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
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4532555"
---
# <a name="gamepad-and-vibration"></a>Gamepad und Vibration

Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Gamepads mittels [Windows.Gaming.Input.Gamepad][gamepad] und verwandter APIs für die universelle Windows-Plattform (UWP) beschrieben.

Auf dieser Seite erfahren Sie:

* Wie Sie eine Liste mit verbundenen Gamepads und deren Benutzern erstellen
* Wie Sie ermitteln, ob ein Gamepad hinzugefügt oder entfernt wurde
* Wie Sie Eingaben von Gamepads lesen
* Wie Sie Vibrations- und Impulsbefehle senden
* wie sich Gamepads als Benutzeroberflächen-Navigationsgeräte Verhalten

## <a name="gamepad-overview"></a>Gamepadübersicht

Gamepads wie der Xbox Wireless Controller und der Xbox Wireless ControllerS sind allgemeine Eingabegeräte für Spiele. Sie sind die Standardeingabegeräte für Xbox One und werden auch häufig von Windows-Spielern als Alternative zur Tastatur und Maus genutzt. Gamepads werden in Windows10- und UWP-Apps für Xbox durch den [Windows.Gaming.Input][]-Namespace unterstützt.

Xbox One-Gamepads sind mit einem direktionalen Pad (oder -D-Pad) ausgestattet. **A**, **B**, **X**, **Y**, **Ansichts-** und **Menüschaltflächen** ; linken und rechten Ministick, Bumper und Trigger; und insgesamt vier vibrationsmotoren. Beide Ministicks liefern jeweils zwei analoge Werte für die X- und die Y-Achse und können auch gedrückt und somit als Taste verwendet werden. Jeder Trigger gibt mit einem analogen Wert, der darstellt, wie weit es wieder gezogen wird.

<!-- > [!NOTE]
> The Xbox Elite Wireless Controller is equipped with four additional **Paddle** buttons on its underside. These can be used to provide redundant access to game commands that are difficult to use together (such as the right thumbstick together with any of the **A**, **B**, **X**, or **Y** buttons) or to provide dedicated access to additional commands. -->

> [!NOTE]
> `Windows.Gaming.Input.Gamepad` unterstützt auch Xbox 360-Gamepads, die das gleiche Steuerungslayout wie standardmäßige Xbox One-Gamepads verfügen.

### <a name="vibration-and-impulse-triggers"></a>Vibration und Impulse Triggers

Xbox One-Gamepads verfügen über zwei unabhängige Motoren für starke und dezente Gamepadvibrationen sowie über zwei dedizierte Motoren für kurze intensive Vibrationen an den einzelnen Triggern. (Aufgrund dieses einzigartigen Features werden die Trigger des Xbox One-Gamepads als _Impulse Triggers_ bezeichnet.)

> [!NOTE]
> Xbox 360-Gamepads sind nicht mit _Impulse Triggers_ausgestattet.

Weitere Informationen finden Sie in der [Übersicht über Vibration und Impulse Triggers](#vibration-and-impulse-triggers-overview).

### <a name="thumbstick-deadzones"></a>Inaktive Ministick-Bereiche

Ein Ministick, der sich in der Mittelstellung (und damit im Ruhezustand) befindet, liefert im Idealfall immer den gleichen neutralen Wert für die X- und die Y-Achse. Aufgrund von mechanischen Kräften und der Empfindlichkeit des Ministicks handelt es sich bei den tatsächlichen Werten in der Mittelposition jedoch lediglich um (ggf. schwankende) Näherungswerte für den idealen neutralen Wert. Aus diesem Grund müssen Sie immer verwenden eine kleine _inaktiven_&mdash;einen Bereich von Wertebereich nahe der idealen Mittelposition&mdash;herstellungsbedingte abweichungen, mechanische Abnutzung und andere gamepadeffekte zu kompensieren.

Durch größere inaktive Bereiche lassen sich ganz einfach beabsichtigte Eingaben von unbeabsichtigten Eingaben unterscheiden.

Weitere Informationen finden Sie unter [Lesen der Ministicks](#reading-the-thumbsticks).

### <a name="ui-navigation"></a>Benutzeroberflächennavigation

Um den Aufwand für die Unterstützung unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden. Der Benutzeroberflächen-Navigationscontroller stellt ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle über verschiedene Eingabegeräte hinweg bereit.

Als Benutzeroberflächen-navigationscontroller ordnen Gamepads den [erforderlichen Satz](ui-navigation-controller.md#required-set) von Navigationsbefehlen auf der linken Ministick, dem Steuerkreuz, **Ansicht**, **Menü**, **A**und **B** Schaltflächen.

| Navigationsbefehl | Gamepadeingabe                       |
| ------------------:| ----------------------------------- |
|                 Nach oben | Linker Ministick nach oben/Steuerkreuz nach oben       |
|               Nach unten | Linker Ministick nach unten/Steuerkreuz nach unten   |
|               Nach links | Linker Ministick nach links/Steuerkreuz nach links   |
|              Nach rechts | Linker Ministick nach rechts/Steuerkreuz nach rechts |
|               Ansicht | Ansicht-Taste                         |
|               Menü | Menü-Taste                         |
|             Annehmen | A-Taste                            |
|             Abbrechen | B-Taste                            |

Darüber hinaus ordnen Gamepads den gesamten [optionalen Satz](ui-navigation-controller.md#optional-set) der Navigationsbefehle den restlichen Eingaben zu.

| Navigationsbefehl | Gamepadeingabe          |
| ------------------:| ---------------------- |
|            Seite nach oben | Linker Trigger           |
|          Seite nach unten | Rechter Trigger          |
|          Seite nach links | Linker Bumper            |
|         Seite nach rechts | Rechter Bumper           |
|          Bildlauf nach oben | Rechter Ministick nach oben    |
|        Bildlauf nach unten | Rechter Ministick nach unten  |
|        Bildlauf nach links | Rechter Ministick nach links  |
|       Bildlauf nach rechts | Rechter Ministick nach rechts |
|          Kontext 1 | X-Taste               |
|          Kontext 2 | Y-Taste               |
|          Kontext 3 | Linken Ministick drücken  |
|          Kontext 4 | Rechten Ministick drücken |

## <a name="detect-and-track-gamepads"></a>Erkennen und Nachverfolgen von Gamepads

Gamepads werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren. Das System stellt eine Liste mit verbundenen Gamepads sowie Ereignisse bereit, um Sie zu benachrichtigen, wenn ein Gamepad hinzugefügt oder entfernt wird.

### <a name="the-gamepads-list"></a>Die Gamepadliste

Die [Gamepad][]-Klasse stellt die statische Eigenschaft [Gamepads][] bereit. Hierbei handelt es sich um eine schreibgeschützte Liste mit derzeit verbundenen Gamepads. Da Sie möglicherweise nur an einigen der verbundenen Gamepads interessiert sind, wird empfohlen, dass Sie anstelle von Zugriff auf diese über eine eigene Sammlung Verwalten der `Gamepads` Eigenschaft.

Im folgenden Beispiel werden alle verbundenen Gamepads in eine neue Sammlung kopiert. Beachten Sie, da andere Threads im Hintergrund dieser Sammlung (in den Ereignissen [GamepadAdded][] und [GamepadRemoved][] ) zugreifen, müssen Sie eine Lock keinen Code zu platzieren, das liest oder die Sammlung aktualisiert.

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

### <a name="adding-and-removing-gamepads"></a>Hinzufügen und Entfernen von Gamepads

Wenn ein Gamepad hinzugefügt oder entfernt wird, werden die [GamepadAdded][] und [GamepadRemoved][] -Ereignisse ausgelöst. Sie können Handler für diese Ereignisse registrieren, um die derzeit verbundenen Gamepads nachzuverfolgen.

Im folgenden Beispiel wird mit der Nachverfolgung eines hinzugefügten Gamepads begonnen.

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

Im folgende Beispiel wird die nachverfolgung eines Gamepads, das entfernt wurden beendet. Sie müssen auch behandeln, was mit Gamepads geschieht, die Sie nachverfolgen können, wenn sie entfernt werden. Beispielsweise wird dieser Code nur verfolgt Eingaben von einem Gamepad und legt es einfach auf `nullptr` entfernt wird. Sie müssen überprüfen Sie jedes Frame, falls Ihre Gamepad aktiv ist und aktualisieren die Gamepad Sie Eingaben von sammeln sind Wenn Domänencontroller verbunden und getrennt sind.

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

Weitere Informationen finden Sie in der [Eingabe-Methoden für Spiele](input-practices-for-games.md) .

### <a name="users-and-headsets"></a>Benutzer und Headsets

Jedes Gamepad kann mit einem Benutzerkonto verknüpft werden, um die Identität des Benutzers mit dem Spiel zu verknüpfen, und mit einem Headset verbunden werden, um Sprachchats oder Features im Spiel zu unterstützen. Weitere Informationen zu Benutzern und Headsets finden Sie unter [Nachverfolgen von Benutzern und ihren Geräten](input-practices-for-games.md#tracking-users-and-their-devices) sowie unter [Headsets](headset.md).

## <a name="reading-the-gamepad"></a>Lesen des Gamepads

Nachdem Sie das Gamepad identifiziert haben, für das Sie sich interessieren, können Sie Eingaben davon erfassen. Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Gamepads Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit. Stattdessen müssen Sie regelmäßig ihren aktuellen Zustand lesen, indem Sie sie _abfragen_.

### <a name="polling-the-gamepad"></a>Abfragen des Gamepads

Beim Abfragen wird eine Momentaufnahme des Navigationsgeräts zu einem bestimmten Zeitpunkt erfasst. Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.

Gamepads werden durch Aufrufen von [GetCurrentReading][] abgefragt. Diese Funktion gibt einen [GamepadReading][]-Wert mit dem Zustand des Gamepads zurück.

Im folgenden Beispiel wird der aktuelle Zustand eines Gamepads abgefragt.

```cpp
auto gamepad = myGamepads[0];

GamepadReading reading = gamepad->GetCurrentReading();
```

```cs
Gamepad gamepad = myGamepads[0];

GamepadReading reading = gamepad.GetCurrentReading();
```

Zusätzlich zum Zustand des Gamepads enthält jeder Wert einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde. Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Werte oder zum Zeitpunkt der Spielsimulation herzustellen.

### <a name="reading-the-thumbsticks"></a>Lesen der Ministicks

Jeder Ministick liefert einen analogen Wert zwischen -1,0 und +1,0 auf der X- und der Y-Achse. Auf der X-Achse entspricht der Wert -1,0 der äußerst linken Ministickposition und der Wert +1,0 der äußerst rechten Position. Auf der Y-Achse entspricht der Wert -1,0 der niedrigsten Ministickposition und der Wert +1,0 der höchsten Position. Auf beiden Achsen ist der Wert ungefähr 0,0, wenn der Stick in die Mittelstellung zurückkehrt, aber normalerwiese weicht der genaue Wert ab, sogar in aufeinanderfolgenden Messwerten; Strategien zur Minimierung dieser Abweichung werden weiter unten in diesem Abschnitt behandelt.

Der X-Achsenwert des linken Ministicks wird aus der `LeftThumbstickX`-Eigenschaft der [GamepadReading][]-Struktur gelesen. Der Y-Achsenwert stammt aus der `LeftThumbstickY`-Eigenschaft. Der X-Achsenwert des rechten Ministicks wird aus der `RightThumbstickX`-Eigenschaft gelesen. Der Y-Achsenwert stammt aus der `RightThumbstickY`-Eigenschaft.

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

Sie werden feststellen, dass die gelesenen Ministickwerte nicht zuverlässig einen neutralen 0,0-Wert liefern, wenn sich der Ministick in der Mittelstellung (und damit im Ruhezustand) befindet. Stattdessen erhalten Sie verschiedene Näherungswerte für 0,0, wann immer der Ministicks bewegt wurde und wieder in die Mittelstellung zurückkehrt. Zur Kompensierung dieser Abweichungen können Sie einen kleinen _inaktiven Bereich_ implementieren (also einen zu ignorierenden Wertebereich nahe der idealen Mittelposition). Zur Implementierung eines inaktiven Bereichs können Sie beispielsweise ermitteln, wie weit sich der Ministick von der Mittelposition entfernt hat, und dabei die Werte ignorieren, die eine bestimmte, von Ihnen gewählte Entfernung unterschreiten. Sie können grobe Entfernung&mdash;es ist nicht exakt, da die ministickwerte im Grunde polar und nicht planar sind&mdash;mit dem Satz des Pythagoras. Dadurch entsteht ein radialer inaktiver Bereich.

Das folgende Beispiel veranschaulicht einen einfachen radialen inaktiven Bereich unter Verwendung des Satzes des Pythagoras.

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

Jeder Ministick kann auch gedrückt werden und somit als Taste fungieren. Weitere Informationen zum Lesen dieser Eingabe finden Sie unter [Lesen der Tasten](#reading-the-buttons).

### <a name="reading-the-triggers"></a>Lesen der Trigger

Die Trigger werden als Gleitkommawerte zwischen 0,0 (vollständig losgelassen) und 1,0 (vollständig gedrückt) dargestellt. Der Wert des linken Triggers wird aus der `LeftTrigger`-Eigenschaft der [GamepadReading][]-Struktur gelesen. Der Wert des rechten Triggers stammt aus der `RightTrigger`-Eigenschaft.

```cpp
float leftTrigger  = reading.LeftTrigger;  // returns a value between 0.0 and 1.0
float rightTrigger = reading.RightTrigger; // returns a value between 0.0 and 1.0
```

```cs
double leftTrigger = reading.LeftTrigger;  // returns a value between 0.0 and 1.0
double rightTrigger = reading.RightTrigger; // returns a value between 0.0 and 1.0
```

### <a name="reading-the-buttons"></a>Lesen der Tasten

Jede der gamepadtasten&mdash;die vier Richtungen des das Steuerkreuz, linke und Rechte Bumper, linken und rechten Ministick drücken, **A**, **B**, **X**, **Y**, **Ansichts-** und **Menü**&mdash;bietet lesen, digitale Gibt an, ob sie gedrückt (unten) oder freigegeben (oben). Aus Effizienzgründen werden nicht Effizienzgründen als einzelne boolesche Werte dargestellt. In diesem Fall werden alle in einem einzelnen Bitfeld Effizienzgründen, die von der [GamepadButtons][] -Enumeration dargestellt wird.

<!-- > [!NOTE]
> The Xbox Elite Wireless Controller is equipped with four additional **paddle** buttons on its underside. These buttons are also represented in the `GamepadButtons` enumeration and their values are read in the same way as the standard gamepad buttons. -->

Die Tastenwerte werden aus der `Buttons`-Eigenschaft der [GamepadReading][]-Struktur gelesen. Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind, Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).

Im folgenden Beispiel wird ermittelt, ob die A-Taste gedrückt ist.

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

Im folgenden Beispiel wird ermittelt, ob die A-Taste losgelassen wurde.

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

In einigen Fällen empfiehlt um zu bestimmen, wann eine Schaltfläche von übergeht zu freigegebenen gedrückt oder losgelassen zu gedrückt, ob mehrere Tasten gedrückt oder losgelassen werden, oder wenn eine Reihe von Schaltflächen in einer bestimmten Weise angeordnet sind&mdash;einige sind gedrückt, andere nicht. Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) sowie unter [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).

## <a name="run-the-gamepad-input-sample"></a>Ausführen des Gamepad-Eingabebeispiels

Im [GamepadUWP-Beispiel _(GitHub)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadUWP) wird veranschaulicht, wie Sie eine Verbindung mit einem Gamepad herstellen und dessen Zustand lesen.

## <a name="vibration-and-impulse-triggers-overview"></a>Übersicht über Vibration und Impulse Triggers

Die Vibrationsmotoren in einem Gamepad erzeugen fühlbares Feedback für den Benutzer. Dies wird in Spielen verwendet, um die Immersion zu verbessern, Statusinformationen (wie etwa eine Beschädigung) zu vermitteln, auf wichtige, in der Nähe befindliche Objekte hinzuweisen oder für andere kreative Zwecke.

Xbox One-Gamepads sind mit insgesamt vier unabhängigen Vibrationsmotoren ausgestattet. Zwei sind große Motoren im gamepadgehäuse befindet. der linke Motor bietet Gehäuse Vibrationen, während der Rechte Motor sanftere, subtilere Vibrationen. Die anderen beiden Motoren sind klein, befinden sich in den Triggern und erzeugen kurze, intensive Vibrationen direkt an den Triggerfingern des Benutzers. Aufgrund dieses einzigartigen Features des Xbox One-Gamepads werden die Trigger dieses Gamepads als _Impulse Triggers_ bezeichnet. Gemeinsam lässt sich mithilfe dieser Motoren eine Vielzahl von Tastempfindungen erzeugen.

## <a name="using-vibration-and-impulse"></a>Verwenden von Vibrationen und Impulsen

Gamepadvibrationen werden über die [Vibration][]-Eigenschaft der [Gamepad][]-Klasse gesteuert. `Vibration` ist eine Instanz der [GamepadVibration][]-Struktur, die sich aus vier Gleitkommawerten zusammensetzt, welche jeweils für die Intensität eines der Motoren stehen.

Obwohl die Mitglieder der der `Gamepad.Vibration` Eigenschaft kann direkt geändert werden, es wird empfohlen, dass Sie eine Separate initialisieren `GamepadVibration` -Instanz, die gewünschten Werte ein, und kopieren Sie ihn in, die `Gamepad.Vibration` Eigenschaft motorintensitäten gleichzeitig zu ändern.

Im folgenden Beispiel wird das gleichzeitige Ändern aller Motorintensitäten veranschaulicht.

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

### <a name="using-the-vibration-motors"></a>Verwenden der Vibrationsmotoren

Der linke und der rechte Vibrationsmotor akzeptieren Gleitkommawerte zwischen 0,0 (keine Vibration) und 1,0 (stärkste Vibration). Die Intensität des linken Motors wird durch die `LeftMotor`-Eigenschaft der [GamepadVibration][]-Struktur festgelegt. Die Intensität des rechten Motors wird durch die `RightMotor`-Eigenschaft festgelegt.

Im folgenden Beispiel wird die Intensität beider Vibrationsmotoren festgelegt und die Gamepadvibration aktiviert.

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

Vergessen Sie nicht, dass diese beiden Motoren nicht identisch sind. Wenn Sie die Eigenschaften also auf den gleichen Wert festlegen, werden in den beiden Motoren nicht die gleichen Vibrationen erzeugt. Für einen beliebigen Wert, der linke Motor erzeugt eine stärkere Vibration mit einer niedrigeren Frequenz als der Rechte motor die&mdash;für den gleichen Wert&mdash;eine sanftere Vibration mit höherer Frequenz erzeugt. Selbst bei Verwendung des Maximalwerts erreicht der linke Motor nicht die hohen Frequenzen des rechten Motors, und mit dem rechten Motor lassen sich nicht die gleichen hohen Kräfte erzeugen wie mit dem linken Motor. Da die Motoren allerdings fest mit dem Gamepadgehäuse verbunden sind, nehmen Spieler die Vibrationen nicht vollständig unabhängig voneinander wahr, obwohl die Motoren unterschiedliche Eigenschaften haben und mit unterschiedlicher Intensität vibrieren können. Dadurch lässt sich eine größere, ausdrucksstärkere Bandbreite von Empfindungen vermitteln als mit zwei identischen Motoren.

### <a name="using-the-impulse-triggers"></a>Verwenden der Impulse Triggers

Jeder Impulse Trigger-Motor akzeptiert einen Gleitkommawert zwischen 0,0 (keine Vibration) und 1,0 (stärkste Vibration). Die Intensität des linken Triggermotors wird durch die `LeftTrigger`-Eigenschaft der [GamepadVibration][]-Struktur festgelegt. Die Intensität des rechten Triggers wird durch die `RightTrigger`-Eigenschaft festgelegt.

Das folgende Beispiel legt die Intensität der beiden Impulse Triggers fest und aktiviert sie.

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

Im Gegensatz zu den anderen Motoren sind die beiden Vibrationsmotoren innerhalb der Trigger identisch und erzeugen bei Verwendung des gleichen Werts jeweils die gleiche Vibration. Da diese Motoren jedoch nicht fest verbunden sind, nehmen die Spieler die Vibrationen unabhängig voneinander wahr. Dank dieses Designs können über beide Trigger gleichzeitig vollständig unabhängige Empfindungen erzeugt werden, um spezifischere Informationen zu vermitteln als mit den Motoren im Gamepadgehäuse möglich wäre.

## <a name="run-the-gamepad-vibration-sample"></a>Ausführen des Gamepad-Vibrationsbeispiels

Das [GamepadVibrationUWP-Beispiel _(GitHub)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/UWPSamples/System/GamepadVibrationUWP) veranschaulicht, wie mithilfe der Gamepad-Vibrationsmotoren und der Impulse Triggers eine Reihe von Effekten erzeugt wird.

## <a name="see-also"></a>Weitere Informationen

* [Windows.Gaming.Input.UINavigationController][]
* [Windows.Gaming.Input.IGameController][]
* [Eingabemethoden für Spiele](input-practices-for-games.md)

[Windows.Gaming.Input]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[Windows.Gaming.Input.UINavigationController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[Windows.Gaming.Input.IGameController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[gamepad]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.aspx
[gamepads]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepads.aspx
[gamepadadded]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepadadded.aspx
[gamepadremoved]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.gamepadremoved.aspx
[getcurrentreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.getcurrentreading.aspx
[vibration]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepad.vibration.aspx
[gamepadreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadreading.aspx
[gamepadbuttons]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadbuttons.aspx
[gamepadvibration]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadvibration.aspx
