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
# <a name="arcade-stick"></a>Arcade-Joystick

Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Arcade-Joysticks mittels [Windows.Gaming.Input.ArcadeStick][arcadestick] und verwandter APIs für die universelle Windows-Plattform (UWP) beschrieben.

Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:
* Erstellen einer Liste der verbundenen Arcade-Joysticks und ihrer Benutzer
* Ermitteln, ob ein Arcade-Joystick hinzugefügt oder entfernt wurde
* Lesen der Eingabe von einem oder mehreren Arcade-Joysticks
* Verhalten von Arcade-Joysticks als Navigationsgerät


## <a name="arcade-stick-overview"></a>Übersicht über Arcade-Joysticks

Bei Arcade-Joysticks handelt es sich um Eingabegeräte, die den Eindruck klassischer Arcade-Automaten vermitteln und aufgrund ihrer äußerst präzisen digitalen Steuerelemente geschätzt werden. Arcade-Joysticks sind das ideale Eingabegerät für Kampfspiele und andere Spiele im Arcade-Stil und eignen sich für alle Spiele mit komplett digitaler Steuerung. Arcade-Joysticks werden in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input][] unterstützt.

Xbox One-Arcade-Joysticks sind mit einem digitalen 8-Wege-Joystick, sechs **Aktionstasten** und zwei **Sondertasten** ausgestattet. Es handelt sich bei ihnen um vollständig digitale Eingabegeräte, die keine analoge Steuerung oder Vibration unterstützen. Xbox One-Arcade-Joysticks verfügen außerdem über Tasten für **Ansicht** und **Menü**, um die Benutzeroberflächennavigation zu unterstützen. Diese Tasten sind jedoch nicht für die Unterstützung von Befehlen im Spiel vorgesehen und können nicht direkt als Joystick-Tasten verwendet werden.

### <a name="ui-navigation"></a>Benutzeroberflächennavigation

Um den Aufwand für die Unterstützung vieler unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden. Der Benutzeroberflächen-Navigationscontroller stellt über verschiedene Eingabegeräte hinweg ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle bereit.

Als Benutzeroberflächen-Navigationscontroller weisen Arcade-Joysticks den [erforderlichen Satz](ui-navigation-controller.md#required-set) mit Navigationsbefehlen dem Joystick und den Tasten **Ansicht**, **Menü**, **Aktion 1** und **Aktion 2** zu.

| Navigationsbefehl | Eingabe des Arcade-Joysticks  |
| ------------------:| ------------------- |
|                 Nach oben | Joystick nach oben            |
|               Nach unten | Joystick nach unten          |
|               Nach links | Joystick nach links          |
|              Nach rechts | Joystick nach rechts         |
|               Ansicht | Ansicht-Taste         |
|               Menü | Menü-Taste         |
|             Annehmen | Taste für Aktion1     |
|             Abbrechen | Taste für Aktion2     |

Arcade-Joysticks ordnen keines der [optionalen Sätze](ui-navigation-controller.md#optional-set) mit Navigationsbefehlen zu.


## <a name="detect-and-track-arcade-sticks"></a>Ermitteln und Nachverfolgen von Arcade-Joysticks

Arcade-Joysticks werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren. Das System stellt eine Liste der verbundenen Arcade-Joysticks und Ereignisse bereit, um Sie zu benachrichtigen, wenn ein Arcade-Joystick hinzugefügt oder entfernt wird.

### <a name="the-arcade-sticks-list"></a>Liste mit Arcade-Joysticks

Die [ArcadeStick][]-Klasse stellt die statische Eigenschaft [ArcadeSticks][] bereit. Dabei handelt es sich um eine schreibgeschützte Liste mit derzeit verbundenen Arcade-Joysticks. Da Sie möglicherweise nur an einigen der verbundenen Arcade-Joysticks interessiert sind, wird empfohlen, dass Sie eine eigene Sammlung verwalten, statt über die Eigenschaft `ArcadeSticks` auf diese zuzugreifen.

Im folgenden Beispiel werden alle verbundenen Arcade-Joysticks in eine neue Sammlung kopiert.
```cpp
auto myArcadeSticks = ref new Vector<ArcadeStick^>();

for (auto arcadestick : ArcadeStick::ArcadeSticks)
{
    // This code assumes that you're interested in all arcade sticks.
    myArcadeSticks->Append(arcadestick);
}
```

### <a name="adding-and-removing-arcade-sticks"></a>Hinzufügen und Entfernen von Arcade-Joysticks

Wenn ein Arcade-Joystick hinzugefügt oder entfernt wird, werden die Ereignisse [ArcadeStickAdded][] und [ArcadeStickRemoved][] ausgelöst. Sie können Handler für diese Ereignisse registrieren, um die zurzeit verbundenen Arcade-Joysticks nachzuverfolgen.

Im folgenden Beispiel wird die Nachverfolgung eines hinzugefügten Arcade-Joysticks gestartet.
```cpp
ArcadeStick::ArcadeStickAdded += ref new EventHandler<ArcadeStick^>(Platform::Object^, ArcadeStick^ args)
{
    // This code assumes that you're interested in all new arcade sticks.
    myArcadeSticks->Append(args);
}
```

Im folgenden Beispiel wird die Nachverfolgung eines entfernen Arcade-Joysticks beendet.
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

### <a name="users-and-headsets"></a>Benutzer und Headsets

Jedes Arcade-Joystick kann mit einem Benutzerkonto verknüpft werden, um die Identität des Benutzers mit dem Spiel zu verknüpfen, und mit einem Headset verbunden werden, um Sprachchats oder Features im Spiel zu unterstützen. Weitere Informationen zu Benutzern und Headsets finden Sie unter [Nachverfolgen von Benutzern und ihren Geräte](input-practices-for-games.md#tracking-users-and-their-devices) und [Headsets](headset.md).


## <a name="reading-the-arcade-stick"></a>Lesen des Arcade-Joysticks

Nachdem Sie den Arcade-Joystick identifiziert haben, für den Sie sich interessieren, können Sie Eingaben von ihm erfassen. Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Arcade-Joysticks Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit. Stattdessen müssen Sie regelmäßig ihren aktuellen Status lesen, indem Sie sie _abfragen_.

### <a name="polling-the-arcade-stick"></a>Abfragen des Arcade-Joysticks

Beim Abfragen wird ein Snapshot des Arcade-Joysticks zu einem bestimmten Zeitpunkt erstellt. Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.

Sie fragen einen Arcade-Joystick ab, indem Sie [GetCurrentReading][] aufrufen. Diese Funktion gibt ein [ArcadeStickReading][]-Element zurück, das den Zustand des Arcade-Joysticks enthält.

Im folgenden Beispiel wird der aktuelle Zustand eines Arcade-Joysticks abgefragt.
```cpp
auto arcadestick = myArcadeSticks[0];

ArcadeStickReading reading = arcadestick->GetCurrentReading();
```

Zusätzlich zum Zustand des Arcade-Joysticks enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde. Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Werte oder zum Zeitpunkt der Spielsimulation herzustellen.

### <a name="reading-the-buttons"></a>Lesen der Tasten

Jede Taste des Arcade-Joysticks (die vier Richtungen des Joysticks, sechs **Aktionstasten** und zwei **Sondertasten**) stellt einen digitalen Ablesewert bereit, der angibt, ob sie gedrückt (unten) oder nicht gedrückt (oben) ist. Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte dargestellt, sondern in einem einzelnen Bitfeld zusammengefasst, das durch die Enumeration [ArcadeStickButtons][] dargestellt wird.

> **Hinweis**    Arcade-Joysticks besitzen zusätzliche Tasten für die Benutzeroberflächennavigation, beispielsweise die **Ansicht**- und **Menü**-Taste. Diese Tasten sind nicht in der Enumeration `ArcadeStickButtons` enthalten und können nur gelesen werden, wenn auf den Arcade-Joystick als Benutzeroberflächen-Navigationsgerät zugegriffen wird. Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationsgerät](ui-navigation-controller.md).

Die Schaltflächenwerte werden von der `Buttons`-Eigenschaft der [ArcadeStickReading][]-Struktur gelesen. Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind. Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).

Im folgenden Beispiel wird ermittelt, ob die Taste für Aktion 1 gedrückt ist.
```cpp
if (ArcadeStickButtons::Action1 == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is pressed
}
```

Im folgenden Beispiel wird ermittelt, ob die Taste für Aktion 1 losgelassen wurde.
```cpp
if (ArcadeStickButtons::None == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is released (not pressed)
}
```

In einigen Fällen möchten Sie möglicherweise ermitteln, ob eine Taste von „Gedrückt“ zu „Losgelassen“ oder von „Losgelassen“ zu „Gedrückt“ wechselt, ob mehrere Tasten gedrückt oder losgelassen werden, oder ob verschiedene Tasten in einer bestimmten Weise angeordnet sind – einige gedrückt, andere nicht. Weitere Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) und [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).

## <a name="run-the-inputinterfacing-sample"></a>Ausführen des InputInterfacing-Beispiels

Das [InputInterfacingUWP-Beispiel _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) veranschaulicht, wie Arcade-Joysticks und verschiedene Arten von Eingabegeräten zusammen verwendet werden und wie diese Eingabegeräte sich bei der Verwendung als Benutzeroberflächen-Navigationcontrollern verhalten.


## <a name="see-also"></a>Weitere Informationen
[Windows.Gaming.Input.UINavigationController][]
[Windows.Gaming.Input.IGameController][]

[Windows.Gaming.Input]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[Windows.Gaming.Input.IGameController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[Windows.Gaming.Input.UINavigationController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[arcadestick]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.aspx
[arcadesticks]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadesticks.aspx
[arcadestickadded]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickadded.aspx
[arcadestickremoved]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickremoved.aspx
[getcurrentreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.getcurrentreading.aspx
[arcadestickreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickreading.aspx
[arcadestickbuttons]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickbuttons.aspx
