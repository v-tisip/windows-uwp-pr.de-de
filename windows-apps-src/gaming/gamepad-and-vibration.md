---
author: eliotcowley
title: Gamepad und Vibration
description: Verwenden Sie die Windows.Gaming.Input-Gamepad-APIs zum Erkennen, Lesen und Senden von Vibrations- und Impulsbefehlen an Gamepads.
ms.assetid: BB03BB8E-255F-4AE8-AC43-1E519CA860FE
ms.author: wdg-dev-content
ms.date: 09/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Gamepad, Vibration
ms.localizationpriority: medium
ms.openlocfilehash: 2bf78b43bb09f97c196858d7cc4fcdb1e71462fc
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5431735"
---
# <a name="gamepad-and-vibration"></a><span data-ttu-id="699ca-104">Gamepad und Vibration</span><span class="sxs-lookup"><span data-stu-id="699ca-104">Gamepad and vibration</span></span>

<span data-ttu-id="699ca-105">Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Gamepads mittels [Windows.Gaming.Input.Gamepad][gamepad] und verwandter APIs für die universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="699ca-105">This page describes the basics of programming for Xbox One gamepads using [Windows.Gaming.Input.Gamepad][gamepad] and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="699ca-106">Auf dieser Seite erfahren Sie:</span><span class="sxs-lookup"><span data-stu-id="699ca-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="699ca-107">Wie Sie eine Liste mit verbundenen Gamepads und deren Benutzern erstellen</span><span class="sxs-lookup"><span data-stu-id="699ca-107">how to gather a list of connected gamepads and their users</span></span>
* <span data-ttu-id="699ca-108">Wie Sie ermitteln, ob ein Gamepad hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="699ca-108">how to detect that a gamepad has been added or removed</span></span>
* <span data-ttu-id="699ca-109">Wie Sie Eingaben von Gamepads lesen</span><span class="sxs-lookup"><span data-stu-id="699ca-109">how to read input from one or more gamepads</span></span>
* <span data-ttu-id="699ca-110">Wie Sie Vibrations- und Impulsbefehle senden</span><span class="sxs-lookup"><span data-stu-id="699ca-110">how to send vibration and impulse commands</span></span>
* <span data-ttu-id="699ca-111">wie sich Gamepads als Benutzeroberflächen-Navigationsgeräte Verhalten</span><span class="sxs-lookup"><span data-stu-id="699ca-111">how gamepads behave as UI navigation devices</span></span>

## <a name="gamepad-overview"></a><span data-ttu-id="699ca-112">Gamepadübersicht</span><span class="sxs-lookup"><span data-stu-id="699ca-112">Gamepad overview</span></span>

<span data-ttu-id="699ca-113">Gamepads wie der Xbox Wireless Controller und der Xbox Wireless ControllerS sind allgemeine Eingabegeräte für Spiele.</span><span class="sxs-lookup"><span data-stu-id="699ca-113">Gamepads like the Xbox Wireless Controller and Xbox Wireless Controller S are general-purpose gaming input devices.</span></span> <span data-ttu-id="699ca-114">Sie sind die Standardeingabegeräte für Xbox One und werden auch häufig von Windows-Spielern als Alternative zur Tastatur und Maus genutzt.</span><span class="sxs-lookup"><span data-stu-id="699ca-114">They're the standard input device on Xbox One and a common choice for Windows gamers when they don't favor a keyboard and mouse.</span></span> <span data-ttu-id="699ca-115">Gamepads werden in Windows10- und UWP-Apps für Xbox durch den [Windows.Gaming.Input][]-Namespace unterstützt.</span><span class="sxs-lookup"><span data-stu-id="699ca-115">Gamepads are supported in Windows 10 and Xbox UWP apps by the [Windows.Gaming.Input][] namespace.</span></span>

<span data-ttu-id="699ca-116">Xbox One-Gamepads sind mit einem direktionalen Pad (oder D-Pad) ausgestattet. **A**, **B**, **X**, **Y**, **Ansichts-** und **Menüschaltflächen** ; linken und rechten Ministick, Bumper und Trigger; und insgesamt vier vibrationsmotoren.</span><span class="sxs-lookup"><span data-stu-id="699ca-116">Xbox One gamepads are equipped with a directional pad (or D-pad); **A**, **B**, **X**, **Y**, **View**, and **Menu** buttons; left and right thumbsticks, bumpers, and triggers; and a total of four vibration motors.</span></span> <span data-ttu-id="699ca-117">Beide Ministicks liefern jeweils zwei analoge Werte für die X- und die Y-Achse und können auch gedrückt und somit als Taste verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="699ca-117">Both thumbsticks provide dual analog readings in the X and Y axes, and also act as a button when pressed inward.</span></span> <span data-ttu-id="699ca-118">Jeder Trigger liefert einen analogen Wert, der darstellt, wie weit es wieder gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="699ca-118">Each trigger provides an analog reading that represents how far it's pulled back.</span></span>

<!-- > [!NOTE]
> The Xbox Elite Wireless Controller is equipped with four additional **Paddle** buttons on its underside. These can be used to provide redundant access to game commands that are difficult to use together (such as the right thumbstick together with any of the **A**, **B**, **X**, or **Y** buttons) or to provide dedicated access to additional commands. -->

> [!NOTE]
> `Windows.Gaming.Input.Gamepad` <span data-ttu-id="699ca-119">unterstützt auch Xbox 360-Gamepads, die das gleiche Steuerungslayout wie standardmäßige Xbox One-Gamepads verfügen.</span><span class="sxs-lookup"><span data-stu-id="699ca-119">also supports Xbox 360 gamepads, which have the same control layout as standard Xbox One gamepads.</span></span>

### <a name="vibration-and-impulse-triggers"></a><span data-ttu-id="699ca-120">Vibration und Impulse Triggers</span><span class="sxs-lookup"><span data-stu-id="699ca-120">Vibration and impulse triggers</span></span>

<span data-ttu-id="699ca-121">Xbox One-Gamepads verfügen über zwei unabhängige Motoren für starke und dezente Gamepadvibrationen sowie über zwei dedizierte Motoren für kurze intensive Vibrationen an den einzelnen Triggern. (Aufgrund dieses einzigartigen Features werden die Trigger des Xbox One-Gamepads als _Impulse Triggers_ bezeichnet.)</span><span class="sxs-lookup"><span data-stu-id="699ca-121">Xbox One gamepads provide two independent motors for strong and subtle gamepad vibration as well as two dedicated motors for providing sharp vibration to each trigger (this unique feature is the reason that Xbox One gamepad triggers are referred to as _impulse triggers_).</span></span>

> [!NOTE]
> <span data-ttu-id="699ca-122">Xbox 360-Gamepads sind nicht mit _Impulse Triggers_ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="699ca-122">Xbox 360 gamepads are not equipped with _impulse triggers_.</span></span>

<span data-ttu-id="699ca-123">Weitere Informationen finden Sie in der [Übersicht über Vibration und Impulse Triggers](#vibration-and-impulse-triggers-overview).</span><span class="sxs-lookup"><span data-stu-id="699ca-123">For more information, see [Vibration and impulse triggers overview](#vibration-and-impulse-triggers-overview).</span></span>

### <a name="thumbstick-deadzones"></a><span data-ttu-id="699ca-124">Inaktive Ministick-Bereiche</span><span class="sxs-lookup"><span data-stu-id="699ca-124">Thumbstick deadzones</span></span>

<span data-ttu-id="699ca-125">Ein Ministick, der sich in der Mittelstellung (und damit im Ruhezustand) befindet, liefert im Idealfall immer den gleichen neutralen Wert für die X- und die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="699ca-125">A thumbstick at rest in the center position would ideally produce the same, neutral reading in the X and Y axes every time.</span></span> <span data-ttu-id="699ca-126">Aufgrund von mechanischen Kräften und der Empfindlichkeit des Ministicks handelt es sich bei den tatsächlichen Werten in der Mittelposition jedoch lediglich um (ggf. schwankende) Näherungswerte für den idealen neutralen Wert.</span><span class="sxs-lookup"><span data-stu-id="699ca-126">However, due to mechanical forces and the sensitivity of the thumbstick, actual readings in the center position only approximate the ideal neutral value and can vary between subsequent readings.</span></span> <span data-ttu-id="699ca-127">Aus diesem Grund müssen Sie immer verwenden eine kleine _inaktiven_&mdash;einen Bereich von Wertebereich nahe der idealen Mittelposition&mdash;herstellungsbedingte abweichungen, mechanische Abnutzung und andere gamepadeffekte zu kompensieren.</span><span class="sxs-lookup"><span data-stu-id="699ca-127">For this reason, you must always use a small _deadzone_&mdash;a range of values near the ideal center position that are ignored&mdash;to compensate for manufacturing differences, mechanical wear, or other gamepad issues.</span></span>

<span data-ttu-id="699ca-128">Durch größere inaktive Bereiche lassen sich ganz einfach beabsichtigte Eingaben von unbeabsichtigten Eingaben unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="699ca-128">Larger deadzones offer a simple strategy for separating intentional input from unintentional input.</span></span>

<span data-ttu-id="699ca-129">Weitere Informationen finden Sie unter [Lesen der Ministicks](#reading-the-thumbsticks).</span><span class="sxs-lookup"><span data-stu-id="699ca-129">For more information, see [Reading the thumbsticks](#reading-the-thumbsticks).</span></span>

### <a name="ui-navigation"></a><span data-ttu-id="699ca-130">Benutzeroberflächennavigation</span><span class="sxs-lookup"><span data-stu-id="699ca-130">UI navigation</span></span>

<span data-ttu-id="699ca-131">Um den Aufwand für die Unterstützung unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="699ca-131">In order to ease the burden of supporting the different input devices for user interface navigation and to encourage consistency between games and devices, most _physical_ input devices simultaneously act as a separate _logical_ input device called a [UI navigation controller](ui-navigation-controller.md).</span></span> <span data-ttu-id="699ca-132">Der Benutzeroberflächen-Navigationscontroller stellt ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle über verschiedene Eingabegeräte hinweg bereit.</span><span class="sxs-lookup"><span data-stu-id="699ca-132">The UI navigation controller provides a common vocabulary for UI navigation commands across input devices.</span></span>

<span data-ttu-id="699ca-133">Als Benutzeroberflächen-navigationscontroller ordnen Gamepads [Erforderlicher Satz](ui-navigation-controller.md#required-set) von Navigationsbefehlen auf der linken Ministick, dem Steuerkreuz, **Ansicht**, **Menü**, **A**und **B** Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="699ca-133">As a UI navigation controller, gamepads map the [required set](ui-navigation-controller.md#required-set) of navigation commands to the left thumbstick, D-pad, **View**, **Menu**, **A**, and **B** buttons.</span></span>

| <span data-ttu-id="699ca-134">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="699ca-134">Navigation command</span></span> | <span data-ttu-id="699ca-135">Gamepadeingabe</span><span class="sxs-lookup"><span data-stu-id="699ca-135">Gamepad input</span></span>                       |
| ------------------:| ----------------------------------- |
|                 <span data-ttu-id="699ca-136">Nach oben</span><span class="sxs-lookup"><span data-stu-id="699ca-136">Up</span></span> | <span data-ttu-id="699ca-137">Linker Ministick nach oben/Steuerkreuz nach oben</span><span class="sxs-lookup"><span data-stu-id="699ca-137">Left thumbstick up / D-pad up</span></span>       |
|               <span data-ttu-id="699ca-138">Nach unten</span><span class="sxs-lookup"><span data-stu-id="699ca-138">Down</span></span> | <span data-ttu-id="699ca-139">Linker Ministick nach unten/Steuerkreuz nach unten</span><span class="sxs-lookup"><span data-stu-id="699ca-139">Left thumbstick down / D-pad down</span></span>   |
|               <span data-ttu-id="699ca-140">Nach links</span><span class="sxs-lookup"><span data-stu-id="699ca-140">Left</span></span> | <span data-ttu-id="699ca-141">Linker Ministick nach links/Steuerkreuz nach links</span><span class="sxs-lookup"><span data-stu-id="699ca-141">Left thumbstick left / D-pad left</span></span>   |
|              <span data-ttu-id="699ca-142">Nach rechts</span><span class="sxs-lookup"><span data-stu-id="699ca-142">Right</span></span> | <span data-ttu-id="699ca-143">Linker Ministick nach rechts/Steuerkreuz nach rechts</span><span class="sxs-lookup"><span data-stu-id="699ca-143">Left thumbstick right / D-pad right</span></span> |
|               <span data-ttu-id="699ca-144">Ansicht</span><span class="sxs-lookup"><span data-stu-id="699ca-144">View</span></span> | <span data-ttu-id="699ca-145">Ansicht-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-145">View button</span></span>                         |
|               <span data-ttu-id="699ca-146">Menü</span><span class="sxs-lookup"><span data-stu-id="699ca-146">Menu</span></span> | <span data-ttu-id="699ca-147">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-147">Menu button</span></span>                         |
|             <span data-ttu-id="699ca-148">Annehmen</span><span class="sxs-lookup"><span data-stu-id="699ca-148">Accept</span></span> | <span data-ttu-id="699ca-149">A-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-149">A button</span></span>                            |
|             <span data-ttu-id="699ca-150">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="699ca-150">Cancel</span></span> | <span data-ttu-id="699ca-151">B-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-151">B button</span></span>                            |

<span data-ttu-id="699ca-152">Darüber hinaus ordnen Gamepads den gesamten [optionalen Satz](ui-navigation-controller.md#optional-set) der Navigationsbefehle den restlichen Eingaben zu.</span><span class="sxs-lookup"><span data-stu-id="699ca-152">Additionally, gamepads map all of the [optional set](ui-navigation-controller.md#optional-set) of navigation commands to the remaining inputs.</span></span>

| <span data-ttu-id="699ca-153">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="699ca-153">Navigation command</span></span> | <span data-ttu-id="699ca-154">Gamepadeingabe</span><span class="sxs-lookup"><span data-stu-id="699ca-154">Gamepad input</span></span>          |
| ------------------:| ---------------------- |
|            <span data-ttu-id="699ca-155">Seite nach oben</span><span class="sxs-lookup"><span data-stu-id="699ca-155">Page Up</span></span> | <span data-ttu-id="699ca-156">Linker Trigger</span><span class="sxs-lookup"><span data-stu-id="699ca-156">Left trigger</span></span>           |
|          <span data-ttu-id="699ca-157">Seite nach unten</span><span class="sxs-lookup"><span data-stu-id="699ca-157">Page Down</span></span> | <span data-ttu-id="699ca-158">Rechter Trigger</span><span class="sxs-lookup"><span data-stu-id="699ca-158">Right trigger</span></span>          |
|          <span data-ttu-id="699ca-159">Seite nach links</span><span class="sxs-lookup"><span data-stu-id="699ca-159">Page Left</span></span> | <span data-ttu-id="699ca-160">Linker Bumper</span><span class="sxs-lookup"><span data-stu-id="699ca-160">Left bumper</span></span>            |
|         <span data-ttu-id="699ca-161">Seite nach rechts</span><span class="sxs-lookup"><span data-stu-id="699ca-161">Page Right</span></span> | <span data-ttu-id="699ca-162">Rechter Bumper</span><span class="sxs-lookup"><span data-stu-id="699ca-162">Right bumper</span></span>           |
|          <span data-ttu-id="699ca-163">Bildlauf nach oben</span><span class="sxs-lookup"><span data-stu-id="699ca-163">Scroll Up</span></span> | <span data-ttu-id="699ca-164">Rechter Ministick nach oben</span><span class="sxs-lookup"><span data-stu-id="699ca-164">Right thumbstick up</span></span>    |
|        <span data-ttu-id="699ca-165">Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="699ca-165">Scroll Down</span></span> | <span data-ttu-id="699ca-166">Rechter Ministick nach unten</span><span class="sxs-lookup"><span data-stu-id="699ca-166">Right thumbstick down</span></span>  |
|        <span data-ttu-id="699ca-167">Bildlauf nach links</span><span class="sxs-lookup"><span data-stu-id="699ca-167">Scroll Left</span></span> | <span data-ttu-id="699ca-168">Rechter Ministick nach links</span><span class="sxs-lookup"><span data-stu-id="699ca-168">Right thumbstick left</span></span>  |
|       <span data-ttu-id="699ca-169">Bildlauf nach rechts</span><span class="sxs-lookup"><span data-stu-id="699ca-169">Scroll Right</span></span> | <span data-ttu-id="699ca-170">Rechter Ministick nach rechts</span><span class="sxs-lookup"><span data-stu-id="699ca-170">Right thumbstick right</span></span> |
|          <span data-ttu-id="699ca-171">Kontext 1</span><span class="sxs-lookup"><span data-stu-id="699ca-171">Context 1</span></span> | <span data-ttu-id="699ca-172">X-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-172">X Button</span></span>               |
|          <span data-ttu-id="699ca-173">Kontext 2</span><span class="sxs-lookup"><span data-stu-id="699ca-173">Context 2</span></span> | <span data-ttu-id="699ca-174">Y-Taste</span><span class="sxs-lookup"><span data-stu-id="699ca-174">Y Button</span></span>               |
|          <span data-ttu-id="699ca-175">Kontext 3</span><span class="sxs-lookup"><span data-stu-id="699ca-175">Context 3</span></span> | <span data-ttu-id="699ca-176">Linken Ministick drücken</span><span class="sxs-lookup"><span data-stu-id="699ca-176">Left thumbstick press</span></span>  |
|          <span data-ttu-id="699ca-177">Kontext 4</span><span class="sxs-lookup"><span data-stu-id="699ca-177">Context 4</span></span> | <span data-ttu-id="699ca-178">Rechten Ministick drücken</span><span class="sxs-lookup"><span data-stu-id="699ca-178">Right thumbstick press</span></span> |

## <a name="detect-and-track-gamepads"></a><span data-ttu-id="699ca-179">Erkennen und Nachverfolgen von Gamepads</span><span class="sxs-lookup"><span data-stu-id="699ca-179">Detect and track gamepads</span></span>

<span data-ttu-id="699ca-180">Gamepads werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren.</span><span class="sxs-lookup"><span data-stu-id="699ca-180">Gamepads are managed by the system, therefore you don't have to create or initialize them.</span></span> <span data-ttu-id="699ca-181">Das System stellt eine Liste mit verbundenen Gamepads sowie Ereignisse bereit, um Sie zu benachrichtigen, wenn ein Gamepad hinzugefügt oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="699ca-181">The system provides a list of connected gamepads and events to notify you when a gamepad is added or removed.</span></span>

### <a name="the-gamepads-list"></a><span data-ttu-id="699ca-182">Die Gamepadliste</span><span class="sxs-lookup"><span data-stu-id="699ca-182">The gamepads list</span></span>

<span data-ttu-id="699ca-183">Die [Gamepad][]-Klasse stellt die statische Eigenschaft [Gamepads][] bereit. Hierbei handelt es sich um eine schreibgeschützte Liste mit derzeit verbundenen Gamepads.</span><span class="sxs-lookup"><span data-stu-id="699ca-183">The [Gamepad][] class provides a static property, [Gamepads][], which is a read-only list of gamepads that are currently connected.</span></span> <span data-ttu-id="699ca-184">Da Sie möglicherweise nur an einigen der verbundenen Gamepads interessiert sind, wird empfohlen, dass Sie anstelle von Zugriff auf diese über eine eigene Sammlung Verwalten der `Gamepads` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="699ca-184">Because you might only be interested in some of the connected gamepads, it's recommended that you maintain your own collection instead of accessing them through the `Gamepads` property.</span></span>

<span data-ttu-id="699ca-185">Im folgenden Beispiel werden alle verbundenen Gamepads in eine neue Sammlung kopiert.</span><span class="sxs-lookup"><span data-stu-id="699ca-185">The following example copies all connected gamepads into a new collection.</span></span> <span data-ttu-id="699ca-186">Beachten Sie, dass da andere Threads im Hintergrund diese Sammlung (in den Ereignissen [GamepadAdded][] und [GamepadRemoved][] ) zugreifen, müssen Sie eine Sperre sämtlichen Code zu platzieren, das liest oder die Sammlung aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="699ca-186">Note that because other threads in the background will be accessing this collection (in the [GamepadAdded][] and [GamepadRemoved][] events), you need to place a lock around any code that reads or updates the collection.</span></span>

```cpp
auto myGamepads = ref new Vector<Gamepad^>();
critical_section myLock{};

for (auto gamepad : Gamepad::Gamepads)
{
    // Check if the gamepad is already in myGamepads; if it isn't, add it.
    critical_section::scoped_lock lock{ myLock };
    auto it = std::find(begin(myGamepads), end(myGamepads), gamepad);

    if (it == end(myGamepads))
    {
        // This code assumes that you're interested in all gamepads.
        myGamepads->Append(gamepad);
    }
}
```

```cs
private readonly object myLock = new object();
private List<Gamepad> myGamepads = new List<Gamepad>();
private Gamepad mainGamepad;

private void GetGamepads()
{
    lock (myLock)
    {
        foreach (var gamepad in Gamepad.Gamepads)
        {
            // Check if the gamepad is already in myGamepads; if it isn't, add it.
            bool gamepadInList = myGamepads.Contains(gamepad);

            if (!gamepadInList)
            {
                // This code assumes that you're interested in all gamepads.
                myGamepads.Add(gamepad);
            }
        }
    }   
}
```

### <a name="adding-and-removing-gamepads"></a><span data-ttu-id="699ca-187">Hinzufügen und Entfernen von Gamepads</span><span class="sxs-lookup"><span data-stu-id="699ca-187">Adding and removing gamepads</span></span>

<span data-ttu-id="699ca-188">Wenn ein Gamepad hinzugefügt oder entfernt wird, werden die [GamepadAdded][] und [GamepadRemoved][] Ereignisse ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="699ca-188">When a gamepad is added or removed, the [GamepadAdded][] and [GamepadRemoved][] events are raised.</span></span> <span data-ttu-id="699ca-189">Sie können Handler für diese Ereignisse registrieren, um die derzeit verbundenen Gamepads nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="699ca-189">You can register handlers for these events to keep track of the gamepads that are currently connected.</span></span>

<span data-ttu-id="699ca-190">Im folgenden Beispiel wird mit der Nachverfolgung eines hinzugefügten Gamepads begonnen.</span><span class="sxs-lookup"><span data-stu-id="699ca-190">The following example starts tracking a gamepad that's been added.</span></span>

```cpp
Gamepad::GamepadAdded += ref new EventHandler<Gamepad^>(Platform::Object^, Gamepad^ args)
{
    // Check if the just-added gamepad is already in myGamepads; if it isn't, add
    // it.
    critical_section::scoped_lock lock{ myLock };
    auto it = std::find(begin(myGamepads), end(myGamepads), args);

    if (it == end(myGamepads))
    {
        // This code assumes that you're interested in all new gamepads.
        myGamepads->Append(args);
    }
}
```

```cs
Gamepad.GamepadAdded += (object sender, Gamepad e) =>
{
    // Check if the just-added gamepad is already in myGamepads; if it isn't, add
    // it.
    lock (myLock)
    {
        bool gamepadInList = myGamepads.Contains(e);

        if (!gamepadInList)
        {
            myGamepads.Add(e);
        }
    }
};
```

<span data-ttu-id="699ca-191">Im folgende Beispiel wird die nachverfolgung eines Gamepads, das entfernt wurden beendet.</span><span class="sxs-lookup"><span data-stu-id="699ca-191">The following example stops tracking a gamepad that's been removed.</span></span> <span data-ttu-id="699ca-192">Sie müssen auch behandeln, was mit Gamepads geschieht, die Sie nachverfolgen können, wenn sie entfernt werden. Beispielsweise wird dieser Code nur verfolgt Eingaben von einem Gamepad und legt es einfach auf `nullptr` Wenn es entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="699ca-192">You'll also need to handle what happens to the gamepads that you're tracking when they're removed; for example, this code only tracks input from one gamepad, and simply sets it to `nullptr` when it's removed.</span></span> <span data-ttu-id="699ca-193">Sie müssen überprüfen Sie jedes Frame, falls Ihre Gamepad aktiv ist und Update welche Gamepad Sie Eingaben von sammeln sind Wenn Domänencontroller verbunden und getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="699ca-193">You'll need to check every frame if your gamepad is active, and update which gamepad you're gathering input from when controllers are connected and disconnected.</span></span>

```cpp
Gamepad::GamepadRemoved += ref new EventHandler<Gamepad^>(Platform::Object^, Gamepad^ args)
{
    unsigned int indexRemoved;
    critical_section::scoped_lock lock{ myLock };

    if(myGamepads->IndexOf(args, &indexRemoved))
    {
        if (m_gamepad == myGamepads->GetAt(indexRemoved))
        {
            m_gamepad = nullptr;
        }

        myGamepads->RemoveAt(indexRemoved);
    }
}
```

```cs
Gamepad.GamepadRemoved += (object sender, Gamepad e) =>
{
    lock (myLock)
    {
        int indexRemoved = myGamepads.IndexOf(e);

        if (indexRemoved > -1)
        {
            if (mainGamepad == myGamepads[indexRemoved])
            {
                mainGamepad = null;
            }

            myGamepads.RemoveAt(indexRemoved);
        }
    }
};
```

<span data-ttu-id="699ca-194">Weitere Informationen finden Sie in der [Eingabe-Methoden für Spiele](input-practices-for-games.md) .</span><span class="sxs-lookup"><span data-stu-id="699ca-194">See [Input practices for games](input-practices-for-games.md) for more information.</span></span>

### <a name="users-and-headsets"></a><span data-ttu-id="699ca-195">Benutzer und Headsets</span><span class="sxs-lookup"><span data-stu-id="699ca-195">Users and headsets</span></span>

<span data-ttu-id="699ca-196">Jedes Gamepad kann mit einem Benutzerkonto verknüpft werden, um die Identität des Benutzers mit dem Spiel zu verknüpfen, und mit einem Headset verbunden werden, um Sprachchats oder Features im Spiel zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="699ca-196">Each gamepad can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features.</span></span> <span data-ttu-id="699ca-197">Weitere Informationen zu Benutzern und Headsets finden Sie unter [Nachverfolgen von Benutzern und ihren Geräten](input-practices-for-games.md#tracking-users-and-their-devices) sowie unter [Headsets](headset.md).</span><span class="sxs-lookup"><span data-stu-id="699ca-197">To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md).</span></span>

## <a name="reading-the-gamepad"></a><span data-ttu-id="699ca-198">Lesen des Gamepads</span><span class="sxs-lookup"><span data-stu-id="699ca-198">Reading the gamepad</span></span>

<span data-ttu-id="699ca-199">Nachdem Sie das Gamepad identifiziert haben, für das Sie sich interessieren, können Sie Eingaben davon erfassen.</span><span class="sxs-lookup"><span data-stu-id="699ca-199">After you identify the gamepad that you're interested in, you're ready to gather input from it.</span></span> <span data-ttu-id="699ca-200">Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Gamepads Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="699ca-200">However, unlike some other kinds of input that you might be used to, gamepads don't communicate state-change by raising events.</span></span> <span data-ttu-id="699ca-201">Stattdessen müssen Sie regelmäßig ihren aktuellen Zustand lesen, indem Sie sie _abfragen_.</span><span class="sxs-lookup"><span data-stu-id="699ca-201">Instead, you take regular readings of their current state by _polling_ them.</span></span>

### <a name="polling-the-gamepad"></a><span data-ttu-id="699ca-202">Abfragen des Gamepads</span><span class="sxs-lookup"><span data-stu-id="699ca-202">Polling the gamepad</span></span>

<span data-ttu-id="699ca-203">Beim Abfragen wird eine Momentaufnahme des Navigationsgeräts zu einem bestimmten Zeitpunkt erfasst.</span><span class="sxs-lookup"><span data-stu-id="699ca-203">Polling captures a snapshot of the navigation device at a precise point in time.</span></span> <span data-ttu-id="699ca-204">Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="699ca-204">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven; it's also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="699ca-205">Gamepads werden durch Aufrufen von [GetCurrentReading][] abgefragt. Diese Funktion gibt einen [GamepadReading][]-Wert mit dem Zustand des Gamepads zurück.</span><span class="sxs-lookup"><span data-stu-id="699ca-205">You poll a gamepad by calling [GetCurrentReading][]; this function returns a [GamepadReading][] that contains the state of the gamepad.</span></span>

<span data-ttu-id="699ca-206">Im folgenden Beispiel wird der aktuelle Zustand eines Gamepads abgefragt.</span><span class="sxs-lookup"><span data-stu-id="699ca-206">The following example polls a gamepad for its current state.</span></span>

```cpp
auto gamepad = myGamepads[0];

GamepadReading reading = gamepad->GetCurrentReading();
```

```cs
Gamepad gamepad = myGamepads[0];

GamepadReading reading = gamepad.GetCurrentReading();
```

<span data-ttu-id="699ca-207">Zusätzlich zum Zustand des Gamepads enthält jeder Wert einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="699ca-207">In addition to the gamepad state, each reading includes a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="699ca-208">Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Werte oder zum Zeitpunkt der Spielsimulation herzustellen.</span><span class="sxs-lookup"><span data-stu-id="699ca-208">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="reading-the-thumbsticks"></a><span data-ttu-id="699ca-209">Lesen der Ministicks</span><span class="sxs-lookup"><span data-stu-id="699ca-209">Reading the thumbsticks</span></span>

<span data-ttu-id="699ca-210">Jeder Ministick liefert einen analogen Wert zwischen -1,0 und +1,0 auf der X- und der Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="699ca-210">Each thumbstick provides an analog reading between -1.0 and +1.0 in the X and Y axes.</span></span> <span data-ttu-id="699ca-211">Auf der X-Achse entspricht der Wert -1,0 der äußerst linken Ministickposition und der Wert +1,0 der äußerst rechten Position.</span><span class="sxs-lookup"><span data-stu-id="699ca-211">In the X axis, a value of -1.0 corresponds to the left-most thumbstick position; a value of +1.0 corresponds to right-most position.</span></span> <span data-ttu-id="699ca-212">Auf der Y-Achse entspricht der Wert -1,0 der niedrigsten Ministickposition und der Wert +1,0 der höchsten Position.</span><span class="sxs-lookup"><span data-stu-id="699ca-212">In the Y axis, a value of -1.0 corresponds to the bottom-most thumbstick position; a value of +1.0 corresponds to the top-most position.</span></span> <span data-ttu-id="699ca-213">In beiden Achsen ist der Wert ungefähr 0,0, wenn sich der Stick befindet sich in die Mittelstellung zurückkehrt, aber normalerwiese weicht der genaue Wert ab, sogar in aufeinanderfolgenden Messwerten; Strategien zur Minimierung dieser Abweichung werden weiter unten in diesem Abschnitt behandelt.</span><span class="sxs-lookup"><span data-stu-id="699ca-213">In both axes, the value is approximately 0.0 when the stick is in the center position, but it's normal for the precise value to vary, even between subsequent readings; strategies for mitigating this variation are discussed later in this section.</span></span>

<span data-ttu-id="699ca-214">Der X-Achsenwert des linken Ministicks wird aus der `LeftThumbstickX`-Eigenschaft der [GamepadReading][]-Struktur gelesen. Der Y-Achsenwert stammt aus der `LeftThumbstickY`-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="699ca-214">The value of the left thumbstick's X axis is read from the `LeftThumbstickX` property of the [GamepadReading][] structure; the value of the Y axis is read from the `LeftThumbstickY` property.</span></span> <span data-ttu-id="699ca-215">Der X-Achsenwert des rechten Ministicks wird aus der `RightThumbstickX`-Eigenschaft gelesen. Der Y-Achsenwert stammt aus der `RightThumbstickY`-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="699ca-215">The value of the right thumbstick's X axis is read from the `RightThumbstickX` property; the value of the Y axis is read from the `RightThumbstickY` property.</span></span>

```cpp
float leftStickX = reading.LeftThumbstickX;   // returns a value between -1.0 and +1.0
float leftStickY = reading.LeftThumbstickY;   // returns a value between -1.0 and +1.0
float rightStickX = reading.RightThumbstickX; // returns a value between -1.0 and +1.0
float rightStickY = reading.RightThumbstickY; // returns a value between -1.0 and +1.0
```

```cs
double leftStickX = reading.LeftThumbstickX;   // returns a value between -1.0 and +1.0
double leftStickY = reading.LeftThumbstickY;   // returns a value between -1.0 and +1.0
double rightStickX = reading.RightThumbstickX; // returns a value between -1.0 and +1.0
double rightStickY = reading.RightThumbstickY; // returns a value between -1.0 and +1.0
```

<span data-ttu-id="699ca-216">Sie werden feststellen, dass die gelesenen Ministickwerte nicht zuverlässig einen neutralen 0,0-Wert liefern, wenn sich der Ministick in der Mittelstellung (und damit im Ruhezustand) befindet. Stattdessen erhalten Sie verschiedene Näherungswerte für 0,0, wann immer der Ministicks bewegt wurde und wieder in die Mittelstellung zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="699ca-216">When reading the thumbstick values, you'll notice that they don't reliably produce a neutral reading of 0.0 when the thumbstick is at rest in the center position; instead, they'll produce different values near 0.0 each time the thumbstick is moved and returned to the center position.</span></span> <span data-ttu-id="699ca-217">Zur Kompensierung dieser Abweichungen können Sie einen kleinen _inaktiven Bereich_ implementieren (also einen zu ignorierenden Wertebereich nahe der idealen Mittelposition).</span><span class="sxs-lookup"><span data-stu-id="699ca-217">To mitigate these variations, you can implement a small _deadzone_, which is a range of values near the ideal center position that are ignored.</span></span> <span data-ttu-id="699ca-218">Zur Implementierung eines inaktiven Bereichs können Sie beispielsweise ermitteln, wie weit sich der Ministick von der Mittelposition entfernt hat, und dabei die Werte ignorieren, die eine bestimmte, von Ihnen gewählte Entfernung unterschreiten.</span><span class="sxs-lookup"><span data-stu-id="699ca-218">One way to implement a deadzone is to determine how far from center the thumbstick has moved, and ignoring the readings that are nearer than some distance you choose.</span></span> <span data-ttu-id="699ca-219">Sie können grobe Entfernung&mdash;Berechnung ist nicht exakt, da die ministickwerte im Grunde polar und nicht planar sind&mdash;mit dem Satz des Pythagoras.</span><span class="sxs-lookup"><span data-stu-id="699ca-219">You can compute the distance roughly&mdash;it's not exact because thumbstick readings are essentially polar, not planar, values&mdash;just by using the Pythagorean theorem.</span></span> <span data-ttu-id="699ca-220">Dadurch entsteht ein radialer inaktiver Bereich.</span><span class="sxs-lookup"><span data-stu-id="699ca-220">This produces a radial deadzone.</span></span>

<span data-ttu-id="699ca-221">Das folgende Beispiel veranschaulicht einen einfachen radialen inaktiven Bereich unter Verwendung des Satzes des Pythagoras.</span><span class="sxs-lookup"><span data-stu-id="699ca-221">The following example demonstrates a basic radial deadzone using the Pythagorean theorem.</span></span>

```cpp
float leftStickX = reading.LeftThumbstickX;   // returns a value between -1.0 and +1.0
float leftStickY = reading.LeftThumbstickY;   // returns a value between -1.0 and +1.0

// choose a deadzone -- readings inside this radius are ignored.
const float deadzoneRadius = 0.1;
const float deadzoneSquared = deadzoneRadius * deadzoneRadius;

// Pythagorean theorem -- for a right triangle, hypotenuse^2 = (opposite side)^2 + (adjacent side)^2
auto oppositeSquared = leftStickY * leftStickY;
auto adjacentSquared = leftStickX * leftStickX;

// accept and process input if true; otherwise, reject and ignore it.
if ((oppositeSquared + adjacentSquared) > deadzoneSquared)
{
    // input accepted, process it
}
```

```cs
double leftStickX = reading.LeftThumbstickX;   // returns a value between -1.0 and +1.0
double leftStickY = reading.LeftThumbstickY;   // returns a value between -1.0 and +1.0

// choose a deadzone -- readings inside this radius are ignored.
const double deadzoneRadius = 0.1;
const double deadzoneSquared = deadzoneRadius * deadzoneRadius;

// Pythagorean theorem -- for a right triangle, hypotenuse^2 = (opposite side)^2 + (adjacent side)^2
double oppositeSquared = leftStickY * leftStickY;
double adjacentSquared = leftStickX * leftStickX;

// accept and process input if true; otherwise, reject and ignore it.
if ((oppositeSquared + adjacentSquared) > deadzoneSquared)
{
    // input accepted, process it
}
```

<span data-ttu-id="699ca-222">Jeder Ministick kann auch gedrückt werden und somit als Taste fungieren. Weitere Informationen zum Lesen dieser Eingabe finden Sie unter [Lesen der Tasten](#reading-the-buttons).</span><span class="sxs-lookup"><span data-stu-id="699ca-222">Each thumbstick also acts as a button when pressed inward; for more information on reading this input, see [Reading the buttons](#reading-the-buttons).</span></span>

### <a name="reading-the-triggers"></a><span data-ttu-id="699ca-223">Lesen der Trigger</span><span class="sxs-lookup"><span data-stu-id="699ca-223">Reading the triggers</span></span>

<span data-ttu-id="699ca-224">Die Trigger werden als Gleitkommawerte zwischen 0,0 (vollständig losgelassen) und 1,0 (vollständig gedrückt) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="699ca-224">The triggers are represented as floating-point values between 0.0 (fully released) and 1.0 (fully depressed).</span></span> <span data-ttu-id="699ca-225">Der Wert des linken Triggers wird aus der `LeftTrigger`-Eigenschaft der [GamepadReading][]-Struktur gelesen. Der Wert des rechten Triggers stammt aus der `RightTrigger`-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="699ca-225">The value of the left trigger is read from the `LeftTrigger` property of the [GamepadReading][] structure; the value of the right trigger is read from the `RightTrigger` property.</span></span>

```cpp
float leftTrigger  = reading.LeftTrigger;  // returns a value between 0.0 and 1.0
float rightTrigger = reading.RightTrigger; // returns a value between 0.0 and 1.0
```

```cs
double leftTrigger = reading.LeftTrigger;  // returns a value between 0.0 and 1.0
double rightTrigger = reading.RightTrigger; // returns a value between 0.0 and 1.0
```

### <a name="reading-the-buttons"></a><span data-ttu-id="699ca-226">Lesen der Tasten</span><span class="sxs-lookup"><span data-stu-id="699ca-226">Reading the buttons</span></span>

<span data-ttu-id="699ca-227">Jede der gamepadtasten&mdash;die vier Richtungen des Steuerkreuz, linke und Rechte Bumper, linken und rechten Ministick drücken, **A**, **B**, **X**, **Y**, **Ansichts-** und **Menü**&mdash;bietet eine digitale Lesen der Gibt an, ob sie gedrückt (unten) oder freigegeben (oben).</span><span class="sxs-lookup"><span data-stu-id="699ca-227">Each of the gamepad buttons&mdash;the four directions of the D-pad, left and right bumpers, left and right thumbstick press, **A**, **B**, **X**, **Y**, **View**, and **Menu**&mdash;provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="699ca-228">Aus Effizienzgründen werden nicht Effizienzgründen als einzelne boolesche Werte dargestellt. In diesem Fall werden alle in einem einzelnen Bitfeld Effizienzgründen, die von der [GamepadButtons][] -Enumeration dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="699ca-228">For efficiency, button readings aren't represented as individual boolean values; instead, they're all packed into a single bitfield that's represented by the [GamepadButtons][] enumeration.</span></span>

<!-- > [!NOTE]
> The Xbox Elite Wireless Controller is equipped with four additional **paddle** buttons on its underside. These buttons are also represented in the `GamepadButtons` enumeration and their values are read in the same way as the standard gamepad buttons. -->

<span data-ttu-id="699ca-229">Die Tastenwerte werden aus der `Buttons`-Eigenschaft der [GamepadReading][]-Struktur gelesen.</span><span class="sxs-lookup"><span data-stu-id="699ca-229">The button values are read from the `Buttons` property of the [GamepadReading][] structure.</span></span> <span data-ttu-id="699ca-230">Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind,</span><span class="sxs-lookup"><span data-stu-id="699ca-230">Because this property is a bitfield, bitwise masking is used to isolate the value of the button that you're interested in.</span></span> <span data-ttu-id="699ca-231">Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).</span><span class="sxs-lookup"><span data-stu-id="699ca-231">The button is pressed (down) when the corresponding bit is set; otherwise, it's released (up).</span></span>

<span data-ttu-id="699ca-232">Im folgenden Beispiel wird ermittelt, ob die A-Taste gedrückt ist.</span><span class="sxs-lookup"><span data-stu-id="699ca-232">The following example determines whether the A button is pressed.</span></span>

```cpp
if (GamepadButtons::A == (reading.Buttons & GamepadButtons::A))
{
    // button A is pressed
}
```

```cs
if (GamepadButtons.A == (reading.Buttons & GamepadButtons.A))
{
    // button A is pressed
}
```

<span data-ttu-id="699ca-233">Im folgenden Beispiel wird ermittelt, ob die A-Taste losgelassen wurde.</span><span class="sxs-lookup"><span data-stu-id="699ca-233">The following example determines whether the A button is released.</span></span>

```cpp
if (GamepadButtons::None == (reading.Buttons & GamepadButtons::A))
{
    // button A is released
}
```

```cs
if (GamepadButtons.None == (reading.Buttons & GamepadButtons.A))
{
    // button A is released
}
```

<span data-ttu-id="699ca-234">In einigen Fällen empfiehlt um zu bestimmen, wann eine Schaltfläche von übergeht "gedrückt" zu nicht oder losgelassen zu gedrückt, ob mehrere Tasten gedrückt oder losgelassen werden, oder wenn eine Reihe von Schaltflächen in einer bestimmten Weise angeordnet sind&mdash;einige sind gedrückt, andere nicht.</span><span class="sxs-lookup"><span data-stu-id="699ca-234">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons is arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="699ca-235">Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) sowie unter [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="699ca-235">For information on how to detect each of these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

## <a name="run-the-gamepad-input-sample"></a><span data-ttu-id="699ca-236">Ausführen des Gamepad-Eingabebeispiels</span><span class="sxs-lookup"><span data-stu-id="699ca-236">Run the gamepad input sample</span></span>

<span data-ttu-id="699ca-237">Im [GamepadUWP-Beispiel _(GitHub)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadUWP) wird veranschaulicht, wie Sie eine Verbindung mit einem Gamepad herstellen und dessen Zustand lesen.</span><span class="sxs-lookup"><span data-stu-id="699ca-237">The [GamepadUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadUWP) demonstrates how to connect to a gamepad and read its state.</span></span>

## <a name="vibration-and-impulse-triggers-overview"></a><span data-ttu-id="699ca-238">Übersicht über Vibration und Impulse Triggers</span><span class="sxs-lookup"><span data-stu-id="699ca-238">Vibration and impulse triggers overview</span></span>

<span data-ttu-id="699ca-239">Die Vibrationsmotoren in einem Gamepad erzeugen fühlbares Feedback für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="699ca-239">The vibration motors inside a gamepad are for providing tactile feedback to the user.</span></span> <span data-ttu-id="699ca-240">Dies wird in Spielen verwendet, um die Immersion zu verbessern, Statusinformationen (wie etwa eine Beschädigung) zu vermitteln, auf wichtige, in der Nähe befindliche Objekte hinzuweisen oder für andere kreative Zwecke.</span><span class="sxs-lookup"><span data-stu-id="699ca-240">Games use this ability to create a greater sense of immersion, to help communicate status information (such as taking damage), to signal proximity to important objects, or for other creative uses.</span></span>

<span data-ttu-id="699ca-241">Xbox One-Gamepads sind mit insgesamt vier unabhängigen Vibrationsmotoren ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="699ca-241">Xbox One gamepads are equipped with a total of four independent vibration motors.</span></span> <span data-ttu-id="699ca-242">Zwei sind große Motoren im gamepadgehäuse befinden. der linke Motor bietet Gehäuse Vibrationen, während der Rechte Motor sanftere, subtilere Vibrationen.</span><span class="sxs-lookup"><span data-stu-id="699ca-242">Two are large motors located in the gamepad body; the left motor provides rough, high-amplitude vibration, while the right motor provides gentler, more subtle vibration.</span></span> <span data-ttu-id="699ca-243">Die anderen beiden Motoren sind klein, befinden sich in den Triggern und erzeugen kurze, intensive Vibrationen direkt an den Triggerfingern des Benutzers. Aufgrund dieses einzigartigen Features des Xbox One-Gamepads werden die Trigger dieses Gamepads als _Impulse Triggers_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="699ca-243">The other two are small motors, one inside each trigger, that provide sharp bursts of vibration directly to the user's trigger fingers; this unique ability of the Xbox One gamepad is the reason its triggers are referred to as _impulse triggers_.</span></span> <span data-ttu-id="699ca-244">Gemeinsam lässt sich mithilfe dieser Motoren eine Vielzahl von Tastempfindungen erzeugen.</span><span class="sxs-lookup"><span data-stu-id="699ca-244">By orchestrating these motors together, a wide range of tactile sensations can be produced.</span></span>

## <a name="using-vibration-and-impulse"></a><span data-ttu-id="699ca-245">Verwenden von Vibrationen und Impulsen</span><span class="sxs-lookup"><span data-stu-id="699ca-245">Using vibration and impulse</span></span>

<span data-ttu-id="699ca-246">Gamepadvibrationen werden über die [Vibration][]-Eigenschaft der [Gamepad][]-Klasse gesteuert.</span><span class="sxs-lookup"><span data-stu-id="699ca-246">Gamepad vibration is controlled through the [Vibration][] property of the [Gamepad][] class.</span></span> `Vibration` <span data-ttu-id="699ca-247">ist eine Instanz der [GamepadVibration][]-Struktur, die sich aus vier Gleitkommawerten zusammensetzt, welche jeweils für die Intensität eines der Motoren stehen.</span><span class="sxs-lookup"><span data-stu-id="699ca-247">is an instance of the [GamepadVibration][] structure which is made up of four floating point values; each value represents the intensity of one of the motors.</span></span>

<span data-ttu-id="699ca-248">Obwohl die Mitglieder der der `Gamepad.Vibration` Eigenschaft kann direkt geändert werden, es wird empfohlen, dass Sie eine Separate initialisieren `GamepadVibration` -Instanz, die gewünschten Werte, und kopieren Sie ihn in, die `Gamepad.Vibration` -Eigenschaft verwenden, um die motorintensitäten gleichzeitig zu ändern.</span><span class="sxs-lookup"><span data-stu-id="699ca-248">Although the members of the `Gamepad.Vibration` property can be modified directly, it's recommended that you initialize a separate `GamepadVibration` instance to the values you want, and then copy it into the `Gamepad.Vibration` property to change the actual motor intensities all at once.</span></span>

<span data-ttu-id="699ca-249">Im folgenden Beispiel wird das gleichzeitige Ändern aller Motorintensitäten veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="699ca-249">The following example demonstrates how to change the motor intensities all at once.</span></span>

```cpp
// get the first gamepad
Gamepad^ gamepad = Gamepad::Gamepads->GetAt(0);

// create an instance of GamepadVibration
GamepadVibration vibration;

// ... set vibration levels on vibration struct here

// copy the GamepadVibration struct to the gamepad
gamepad.Vibration = vibration;
```

```cs
// get the first gamepad
Gamepad gamepad = Gamepad.Gamepads[0];

// create an instance of GamepadVibration
GamepadVibration vibration = new GamepadVibration();

// ... set vibration levels on vibration struct here

// copy the GamepadVibration struct to the gamepad
gamepad.Vibration = vibration;
```

### <a name="using-the-vibration-motors"></a><span data-ttu-id="699ca-250">Verwenden der Vibrationsmotoren</span><span class="sxs-lookup"><span data-stu-id="699ca-250">Using the vibration motors</span></span>

<span data-ttu-id="699ca-251">Der linke und der rechte Vibrationsmotor akzeptieren Gleitkommawerte zwischen 0,0 (keine Vibration) und 1,0 (stärkste Vibration).</span><span class="sxs-lookup"><span data-stu-id="699ca-251">The left and right vibration motors take floating point values between 0.0 (no vibration) and 1.0 (most intense vibration).</span></span> <span data-ttu-id="699ca-252">Die Intensität des linken Motors wird durch die `LeftMotor`-Eigenschaft der [GamepadVibration][]-Struktur festgelegt. Die Intensität des rechten Motors wird durch die `RightMotor`-Eigenschaft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="699ca-252">The intensity of the left motor is set by the `LeftMotor` property of the [GamepadVibration][] structure; the intensity of the right motor is set by the `RightMotor` property.</span></span>

<span data-ttu-id="699ca-253">Im folgenden Beispiel wird die Intensität beider Vibrationsmotoren festgelegt und die Gamepadvibration aktiviert.</span><span class="sxs-lookup"><span data-stu-id="699ca-253">The following example sets the intensity of both vibration motors and activates gamepad vibration.</span></span>

```cpp
GamepadVibration vibration;
vibration.LeftMotor = 0.80;  // sets the intensity of the left motor to 80%
vibration.RightMotor = 0.25; // sets the intensity of the right motor to 25%
gamepad.Vibration = vibration;
```

```cs
GamepadVibration vibration = new GamepadVibration();
vibration.LeftMotor = 0.80;  // sets the intensity of the left motor to 80%
vibration.RightMotor = 0.25; // sets the intensity of the right motor to 25%
mainGamepad.Vibration = vibration;
```

<span data-ttu-id="699ca-254">Vergessen Sie nicht, dass diese beiden Motoren nicht identisch sind. Wenn Sie die Eigenschaften also auf den gleichen Wert festlegen, werden in den beiden Motoren nicht die gleichen Vibrationen erzeugt.</span><span class="sxs-lookup"><span data-stu-id="699ca-254">Remember that these two motors are not identical so setting these properties to the same value doesn't produce the same vibration in one motor as in the other.</span></span> <span data-ttu-id="699ca-255">Für einen beliebigen Wert, der linke Motor erzeugt eine stärkere Vibration mit einer niedrigeren Frequenz als der Rechte motor die&mdash;für den gleichen Wert&mdash;eine sanftere Vibration mit höherer Frequenz erzeugt.</span><span class="sxs-lookup"><span data-stu-id="699ca-255">For any value, the left motor produces a stronger vibration at a lower frequency than the right motor which&mdash;for the same value&mdash;produces a gentler vibration at a higher frequency.</span></span> <span data-ttu-id="699ca-256">Selbst bei Verwendung des Maximalwerts erreicht der linke Motor nicht die hohen Frequenzen des rechten Motors, und mit dem rechten Motor lassen sich nicht die gleichen hohen Kräfte erzeugen wie mit dem linken Motor.</span><span class="sxs-lookup"><span data-stu-id="699ca-256">Even at the maximum value, the left motor can't produce the high frequencies of the right motor, nor can the right motor produce the high forces of the left motor.</span></span> <span data-ttu-id="699ca-257">Da die Motoren allerdings fest mit dem Gamepadgehäuse verbunden sind, nehmen Spieler die Vibrationen nicht vollständig unabhängig voneinander wahr, obwohl die Motoren unterschiedliche Eigenschaften haben und mit unterschiedlicher Intensität vibrieren können.</span><span class="sxs-lookup"><span data-stu-id="699ca-257">Still, because the motors are rigidly connected by the gamepad body, players don't experience the vibrations fully independently even though the motors have different characteristics and can vibrate with different intensities.</span></span> <span data-ttu-id="699ca-258">Dadurch lässt sich eine größere, ausdrucksstärkere Bandbreite von Empfindungen vermitteln als mit zwei identischen Motoren.</span><span class="sxs-lookup"><span data-stu-id="699ca-258">This arrangement allows for a wider, more expressive range of sensations to be produced than if the motors were identical.</span></span>

### <a name="using-the-impulse-triggers"></a><span data-ttu-id="699ca-259">Verwenden der Impulse Triggers</span><span class="sxs-lookup"><span data-stu-id="699ca-259">Using the impulse triggers</span></span>

<span data-ttu-id="699ca-260">Jeder Impulse Trigger-Motor akzeptiert einen Gleitkommawert zwischen 0,0 (keine Vibration) und 1,0 (stärkste Vibration).</span><span class="sxs-lookup"><span data-stu-id="699ca-260">Each impulse trigger motor takes a floating point value between 0.0 (no vibration) and 1.0 (most intense vibration).</span></span> <span data-ttu-id="699ca-261">Die Intensität des linken Triggermotors wird durch die `LeftTrigger`-Eigenschaft der [GamepadVibration][]-Struktur festgelegt. Die Intensität des rechten Triggers wird durch die `RightTrigger`-Eigenschaft festgelegt.</span><span class="sxs-lookup"><span data-stu-id="699ca-261">The intensity of the left trigger motor is set by the `LeftTrigger` property of the [GamepadVibration][] structure; the intensity of the right trigger is set by the `RightTrigger` property.</span></span>

<span data-ttu-id="699ca-262">Das folgende Beispiel legt die Intensität der beiden Impulse Triggers fest und aktiviert sie.</span><span class="sxs-lookup"><span data-stu-id="699ca-262">The following example sets intensity of both impulse triggers and activates them.</span></span>

```cpp
GamepadVibration vibration;
vibration.LeftTrigger = 0.75;  // sets the intensity of the left trigger to 75%
vibration.RightTrigger = 0.50; // sets the intensity of the right trigger to 50%
gamepad.Vibration = vibration;
```

```cs
GamepadVibration vibration = new GamepadVibration();
vibration.LeftTrigger = 0.75;  // sets the intensity of the left trigger to 75%
vibration.RightTrigger = 0.50; // sets the intensity of the right trigger to 50%
mainGamepad.Vibration = vibration;
```

<span data-ttu-id="699ca-263">Im Gegensatz zu den anderen Motoren sind die beiden Vibrationsmotoren innerhalb der Trigger identisch und erzeugen bei Verwendung des gleichen Werts jeweils die gleiche Vibration.</span><span class="sxs-lookup"><span data-stu-id="699ca-263">Unlike the others, the two vibration motors inside the triggers are identical so they produce the same vibration in either motor for the same value.</span></span> <span data-ttu-id="699ca-264">Da diese Motoren jedoch nicht fest verbunden sind, nehmen die Spieler die Vibrationen unabhängig voneinander wahr.</span><span class="sxs-lookup"><span data-stu-id="699ca-264">However, because these motors are not rigidly connected in any way, players experience the vibrations independently.</span></span> <span data-ttu-id="699ca-265">Dank dieses Designs können über beide Trigger gleichzeitig vollständig unabhängige Empfindungen erzeugt werden, um spezifischere Informationen zu vermitteln als mit den Motoren im Gamepadgehäuse möglich wäre.</span><span class="sxs-lookup"><span data-stu-id="699ca-265">This arrangement allows for fully independent sensations to be directed to both triggers simultaneously, and helps them to convey more specific information than the motors in the gamepad body can.</span></span>

## <a name="run-the-gamepad-vibration-sample"></a><span data-ttu-id="699ca-266">Ausführen des Gamepad-Vibrationsbeispiels</span><span class="sxs-lookup"><span data-stu-id="699ca-266">Run the gamepad vibration sample</span></span>

<span data-ttu-id="699ca-267">Das [GamepadVibrationUWP-Beispiel _(GitHub)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadVibrationUWP) veranschaulicht, wie mithilfe der Gamepad-Vibrationsmotoren und der Impulse Triggers eine Reihe von Effekten erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="699ca-267">The [GamepadVibrationUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadVibrationUWP) demonstrates how the gamepad vibration motors and impulse triggers are used to produce a variety of effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="699ca-268">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="699ca-268">See also</span></span>

* [<span data-ttu-id="699ca-269">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="699ca-269">Windows.Gaming.Input.UINavigationController</span></span>][]
* [<span data-ttu-id="699ca-270">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="699ca-270">Windows.Gaming.Input.IGameController</span></span>][]
* [<span data-ttu-id="699ca-271">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="699ca-271">Input practices for games</span></span>](input-practices-for-games.md)

[<span data-ttu-id="699ca-272">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="699ca-272">Windows.Gaming.Input</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[<span data-ttu-id="699ca-273">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="699ca-273">Windows.Gaming.Input.UINavigationController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[<span data-ttu-id="699ca-274">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="699ca-274">Windows.Gaming.Input.IGameController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[<span data-ttu-id="699ca-275">gamepad</span><span class="sxs-lookup"><span data-stu-id="699ca-275">gamepad</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.aspx
[<span data-ttu-id="699ca-276">gamepads</span><span class="sxs-lookup"><span data-stu-id="699ca-276">gamepads</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepads.aspx
[<span data-ttu-id="699ca-277">gamepadadded</span><span class="sxs-lookup"><span data-stu-id="699ca-277">gamepadadded</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepadadded.aspx
[<span data-ttu-id="699ca-278">gamepadremoved</span><span class="sxs-lookup"><span data-stu-id="699ca-278">gamepadremoved</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepadremoved.aspx
[<span data-ttu-id="699ca-279">getcurrentreading</span><span class="sxs-lookup"><span data-stu-id="699ca-279">getcurrentreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.getcurrentreading.aspx
[<span data-ttu-id="699ca-280">vibration</span><span class="sxs-lookup"><span data-stu-id="699ca-280">vibration</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.vibration.aspx
[<span data-ttu-id="699ca-281">gamepadreading</span><span class="sxs-lookup"><span data-stu-id="699ca-281">gamepadreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadreading.aspx
[<span data-ttu-id="699ca-282">gamepadbuttons</span><span class="sxs-lookup"><span data-stu-id="699ca-282">gamepadbuttons</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadbuttons.aspx
[<span data-ttu-id="699ca-283">gamepadvibration</span><span class="sxs-lookup"><span data-stu-id="699ca-283">gamepadvibration</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadvibration.aspx
