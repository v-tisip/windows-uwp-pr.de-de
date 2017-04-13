---
author: mithom
title: "Eingabemethoden für Spiele"
description: "Erfahren Sie mehr über Muster und Verfahren zur effizienten Verwendung von Eingabegeräten."
ms.assetid: CBAD3345-3333-4924-B6D8-705279F52676
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Spiele, Eingabe
ms.openlocfilehash: 15d56a27ad914b258bb19b80b3498510d01105cd
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="input-practices-for-games"></a>Eingabemethoden für Spiele

Auf dieser Seite werden Muster und Verfahren zur effizienten Verwendung von Eingabegeräten in Spielen für die universelle Windows-Plattform (UWP) beschrieben.

Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:
* Nachverfolgen von Spielern und den von ihnen aktuell verwendeten Eingabe- und Navigationsgeräten
* Erkennen von Tastenübergängen (von „Gedrückt“ zu „Losgelassen“ oder von „Losgelassen“ zu „Gedrückt“)
* Erkennen komplexer Tastenanordnungen mit einem einzelnen Test

## <a name="tracking-users-and-their-devices"></a>Nachverfolgen von Benutzern und ihren Geräten

Alle Eingabegeräte sind einem [Benutzer][Windows.System.User] zugeordnet, damit seine Identität mit seinem Spiel, seinen Erfolgen, geänderten Einstellungen und anderen Aktivitäten verknüpft werden kann. Benutzer können sich nach Belieben anmelden oder abmelden. Es ist nicht ungewöhnlich, dass sich ein anderer Benutzer mit einem Eingabegerät anmeldet, das weiterhin mit dem System verbunden ist, nachdem sich der vorherige Benutzer abgemeldet hat. Wenn sich ein Benutzer an- oder abmeldet, wird das [IGameController.UserChanged][]-Ereignis ausgelöst. Sie können einen Ereignishandler für dieses Ereignis registrieren, um Spieler und die von ihnen verwendeten Geräte nachzuverfolgen.

Die Benutzeridentität dient auch dazu, ein Eingabegerät dem entsprechenden Benutzeroberflächen-Navigationscontroller zuzuordnen.

Aus diesen Gründen sollte die Spielereingabe mithilfe der [User][igamecontroller.user]-Eigenschaft der Geräteklasse (von der [IGameController][]-Schnittstelle geerbt) nachverfolgt und korreliert werden.

Das [UserGamepadPairingUWP _(github)_](
https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/UserGamepadPairingUWP)-Beispiel veranschaulicht, wie Benutzer und die von ihnen verwendeten Geräte nachverfolgt werden können.

## <a name="detecting-button-transitions"></a>Erkennen von Tastenübergängen

In einigen Fällen möchten Sie wissen, wann eine Taste zuerst gedrückt oder losgelassen wird, also genau, wann der Zustand der Taste von „Losgelassen“ in „Gedrückt“ oder von „Gedrückt“ in „Losgelassen“ übergegangen ist. Um dies zu ermitteln und herauszufinden, was sich geändert hat, müssen Sie den vorherigen Geräte-Ablesewert beibehalten und mit dem aktuellen Ablesewert vergleichen.

Im Folgenden wird anhand eines allgemeinen Beispiels erläutert, wie der vorherige Ablesewert beibehalten werden kann. Zwar werden in diesem Fall Gamepads verwendet, dasselbe Prinzip lässt sich aber auch auf Arcade-Joysticks, Rennlenkräder und Navigationstasten für die Benutzeroberfläche anwenden.

```cpp
GamepadReading newReading();
GamepadReading oldReading();

// Game::Loop represents one iteration of a typical game loop
void Game::Loop()
{
    // move previous newReading into oldReading before getting next newReading
    oldReading = newReading, newReading = gamepad.CurrentReading();

    // process device readings using buttonJustPressed/buttonJustReleased
}
```

Als Erstes verschiebt `Game::Loop` den vorhandenen Wert von `newReading` (den Gamepad-Ablesewert aus der vorherigen Schleifeniteration) in `oldReading` und fügt dann einen neuen Gamepad-Ablesewert für die aktuelle Iteration in `newReading` ein. Mithilfe dieser Informationen können Sie den Übergang von Tasten erkennen.

Das folgende Beispiel zeigt eine einfache Möglichkeit, Tastenübergänge zu erkennen.

```cpp
bool buttonJustPressed(const gamepadButtons selection)
{
    bool newSelectionPressed = (selection == (newReading.Buttons & selection));
    bool oldSelectionPressed = (selection == (oldReading.Buttons & selection));

    return newSelectionPressed && !oldSelectionPressed;
}

bool buttonJustReleased(gamepadButtons selection)
{
    bool newSelectionReleased = (gamepadButtons.None == (newReading.Buttons & selection));
    bool oldSelectionReleased = (gamepadButtons.None == (oldReading.Buttons & selection));

    return newSelectionReleased && !oldSelectionReleased;
}
```

Die beiden Funktionen leiten zunächst den booleschen Zustand der Tastenauswahl von `newReading` und `oldReading` ab und bestimmen dann anhand boolescher Logik, ob der Übergang in den Zielzustand erfolgt ist. Diese Funktionen geben nur _true_ zurück, wenn der neue Ablesewert den Zielzustand enthält („Gedrückt“ bzw. „Losgelassen“) *und* der alte Ablesewert nicht auch den Zielzustand enthält. Andernfalls geben sie _false_ zurück.


## <a name="detecting-complex-button-arrangements"></a>Erkennen komplexer Tastenanordnungen

Jede Taste eines Eingabegeräts liefert einen digitalen Wert, der angibt, ob sie sich im gedrückten Zustand (unten) oder losgelassenen Zustand (oben) befindet. Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte dargestellt, sondern in Bitfeldern zusammengefasst, die durch gerätespezifische Enumerationen wie [GamepadButtons][] dargestellt werden. Zum Lesen bestimmter Tastenwerte wird eine bitweise Maskierung verwendet, um die für Sie relevanten Werte zu isolieren. Tasten sind gedrückt (unten), wenn ihr entsprechendes Bit festgelegt ist. Andernfalls sind sie losgelassen (oben).

Es wurde bereits erläutert, wie der Zustand einzelner Tasten („Gedrückt“ oder „Losgelassen“) bestimmt wird. Zwar werden in diesem Fall Gamepads verwendet, dasselbe Prinzip lässt sich aber auch auf Arcade-Joysticks, Rennlenkräder und Navigationstasten für die Benutzeroberfläche anwenden.

```cpp
// determines whether gamepad button A is pressed
if (GamepadButtons::A == (reading.Buttons & GamepadButtons::A))
{
    // button A is pressed
}

// determines whether gamepad button A is released
if (GamepadButtons::None == (reading.Buttons & GamepadButtons::A))
{
    // button A is released (not pressed)
}
```

Der Zustand einer einzelnen Taste lässt sich auf einfache Weise bestimmen. In einigen Fällen möchten Sie aber möglicherweise ermitteln, ob mehrere Tasten gedrückt oder losgelassen werden, oder ob verschiedene Tasten in einer bestimmten Weise angeordnet sind – einige sind gedrückt, andere nicht. Es ist komplexer, mehrere Tasten zu testen als einzelne Tasten. Dies gilt insbesondere bei gemischten Tastenzuständen. Allerdings gibt es eine einfache Formel für diese Tests, die sowohl auf einzelne als auch auf mehrere Tasten angewendet werden kann.

Im folgenden Beispiel wird ermittelt, ob die Gamepadtasten A und B beide gedrückt sind.

```cpp
if ((GamepadButtons::A | GamepadButtons::B) == (reading.Buttons & (GamepadButtons::A | GamepadButtons::B))
{
    // buttons A and B are pressed
}
```

Im folgenden Beispiel wird ermittelt, ob die Gamepadtasten A und B beide losgelassen sind.

```cpp
if ((GamepadButtons::None == (reading.Buttons & GamepadButtons::A | GamepadButtons::B))
{
    // buttons A and B are released (not pressed)
}
```

Im folgenden Beispiel wird ermittelt, ob die Gamepadtaste A gedrückt und die Taste B losgelassen ist.

```cpp
if (GamepadButtons::A == (reading.Buttons & (GamepadButtons::A | GamepadButtons::B))
{
    // button A is pressed and button B is released (button B is not pressed)
}
```

Die Formel, die in allen fünf Beispielen verwendet wird, ist wie folgt aufgebaut: Die Anordnung der zu überprüfenden Tasten wird durch den Ausdruck auf der linken Seite des Gleichheitsoperators angegeben, während die Tasten, die berücksichtigt werden sollen, durch den Maskierungsausdruck auf der rechten Seite ausgewählt werden.

Das folgende Beispiel verdeutlicht diese Formel noch besser, da das vorherige Beispiel umgeschrieben wurde.

```cpp
auto buttonArrangement = GamepadButtons::A;
auto buttonSelection = (reading.Buttons & (GamepadButtons::A | GamepadButtons::B));

if (buttonArrangement == buttonSelection)
{
    // button A is pressed and button B is released (button B is not pressed)
}
```

Die Formel kann zum Testen einer beliebigen Anzahl von Tasten in einer beliebigen Anordnung ihrer Zustände verwendet werden.



[Windows.System.User]: https://msdn.microsoft.com/library/windows/apps/windows.system.user.aspx
[igamecontroller]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[igamecontroller.user]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.user.aspx
[igamecontroller.userchanged]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.userchanged.aspx
[gamepadbuttons]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.gamepadbuttons.aspx
