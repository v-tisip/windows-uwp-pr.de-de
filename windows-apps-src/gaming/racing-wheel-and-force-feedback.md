---
author: mithom
title: "Rennlenkräder und Kraftrückmeldung"
description: "Verwenden Sie die Windows.Gaming.Input-APIs für Rennlenkräder, um Funktionen zu erkennen und zu ermitteln sowie Kraftrückmeldungsbefehle zu lesen und an Rennlenkräder zu senden."
ms.assetid: 6287D87F-6F2E-4B67-9E82-3D6E51CBAFF9
translationtype: Human Translation
ms.sourcegitcommit: d0cfc41e5ae79844f3948ed2c326bf9913c066a4
ms.openlocfilehash: ea2c1f359424f042b9563e2723c1eb34ee8ddff0

---

# <a name="racing-wheel-and-force-feedback"></a>Rennlenkräder und Kraftrückmeldung

Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Renklenkräder mittels [Windows.Gaming.Input.RacingWheel][Racingwheel] und verwandter APIs für die Universelle Windows-Plattform (UWP) beschrieben.

Auf dieser Seite erfahren Sie:
* Wie Sie eine Liste der verbundenen Rennlenkräder und ihrer Benutzer erstellen
* Wie Sie feststellen, dass ein Rennlenkrad hinzugefügt oder entfernt wurde
* Wie Sie die Eingabe eines oder mehrerer Rennlenkräder lesen
* Wie Sie Kraftrückmeldungsbefehle senden
* Wie sich Rennlenkräder als Navigationsgerät verhalten


## <a name="racing-wheel-overview"></a>Übersicht über Rennlenkräder

Rennlenkräder sind Eingabegeräte, die Benutzern das Gefühl vermitteln, in einem echten Rennwagencockpit zu sitzen. Rennlenkräder sind das ideale Eingabegerät für Rennsportspiele im Arcade- und Simulationsstil, die Autos oder Trucks enthalten. Rennlenkräder werden in Windows 10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input][] unterstützt.

Xbox One-Rennlenkräder werden zu verschiedenen Preisen angeboten. In der Regel verfügen Rennlenkräder über mehr und bessere Eingabe- und Kraftrückmeldungsfunktionen, je höher ihr Preis liegt. Alle Rennlenkräder besitzen ein analoges Lenkrad, analoge Gas- und Bremsensteuerelemente sowie einige Lenkradtasten. Einige Rennlenkräder sind zusätzlich mit analogen Kupplungs- und Handbremsensteuerelementen, einer analogen Gangschaltung sowie Kraftrückmeldungsfunktionen ausgestattet. Nicht alle Rennlenkräder besitzen die gleichen Features. Darüber hinaus unterscheiden sie sich möglicherweise hinsichtlich der Unterstützung für bestimmte Features. Beispielsweise können Lenkräder unterschiedliche Drehbereiche unterstützen, und Gangschaltungen können eine unterschiedliche Zahl von Gängen unterstützen.

### <a name="device-capabilities"></a>Gerätefunktionen

Die verschiedenen Xbox One-Rennlenkräder bieten unterschiedliche optionale Gerätefunktionen und einen unterschiedlichen Grad an Unterstützung für diese Funktionen. Dieser Grad an Abweichungen für ein einzelnes Eingabegerät ist unter den Geräten, die von den [Windows.Gaming.Input][]-APIs unterstützt werden, einzigartig. Darüber hinaus unterstützen die meisten Geräte, denen Sie begegnen werden, zumindest einige optionale Funktionen oder andere Abweichungen. Daher ist es wichtig, die Funktionen der verbundenen Rennlenkräder einzeln zu ermitteln und die gesamte Bandbreite der für Ihr Spiel sinnvollen Funktionen zu unterstützen.

Weitere Informationen finden Sie unter [Ermitteln von Rennlenkradfunktionen](#determining-racing-wheel-capabilities).

### <a name="force-feedback"></a>Kraftrückmeldung

Einige Xbox One-Rennlenkräder stellen eine echte Kraftrückmeldung und nicht einfach nur Vibrationen bereit, d. h., sie können echte Kräfte auf eine Steuerungsachse wie das Lenkrad ausüben. Spiele verwenden diese Fähigkeit, um ein besseres Spielerlebnis zu vermitteln (_simulierte Unfallschäden_, _„Gefühl für die Straße“_) und die Anforderungen in Bezug auf gutes Fahren zu erhöhen.

Weitere Informationen finden Sie unter [Übersicht über die Kraftrückmeldung](#force-feedback-overview).

### <a name="ui-navigation"></a>Benutzeroberflächennavigation

Um den Aufwand für die Unterstützung unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden. Der Benutzeroberflächen-Navigationscontroller stellt ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle über verschiedene Eingabegeräte hinweg bereit.

Aufgrund des spezifischen Schwerpunkts auf analogen Steuerungen und des Umfangs der Abweichungen zwischen den verschiedenen Rennlenkrädern verfügen diese in der Regel über ein Steuerkreuz, eine **Ansicht**, ein **Menü** und die Tasten **A**, **B**, **X** und **Y**, die den Tasten eines [Gamepad](gamepad-and-vibration.md) ähnlich sind. Diese Tasten sind jedoch nicht für die Unterstützung von Befehlen im Spiel vorgesehen und können nicht direkt als Rennlenkradtasten verwendet werden.

Als Benutzeroberflächen-Navigationscontroller ordnen Rennlenkräder den [erforderlichen Satz](ui-navigation-controller.md#required-set) von Navigationsbefehlen dem linken Ministick, dem Steuerkreuz, der **Ansicht**, dem **Menü** sowie den Tasten **A** und **B** zu.

| Navigationsbefehl | Rennlenkradeingabe |
| ------------------:| ------------------ |
|                 Nach oben | Steuerkreuz nach oben           |
|               Nach unten | Steuerkreuz nach unten         |
|               Links | Steuerkreuz nach links         |
|              Rechts | Steuerkreuz nach rechts        |
|               Ansicht | Ansicht-Taste        |
|               Menü | Menü-Taste        |
|             Annehmen | A-Taste           |
|             Abbrechen | B-Taste           |

Darüber hinaus ordnen einige Rennlenkräder möglicherweise einige [optionale](ui-navigation-controller.md#optional-set) Navigationsbefehle anderen von ihnen unterstützten Eingaben zu. Die Befehlszuordnungen können sich jedoch von Gerät zu Gerät unterscheiden. Sie sollten die Unterstützung dieser Befehle ebenfalls in Betracht ziehen, dabei jedoch sicherstellen, dass diese Befehle für die Navigation in der Benutzeroberfläche Ihres Spiels nicht notwendig sind.

| Navigationsbefehl | Rennlenkradeingabe    |
| ------------------:| --------------------- |
|            Seite nach oben | _Unterschiedlich_              |
|          Seite nach unten | _Unterschiedlich_              |
|          Seite nach links | _Unterschiedlich_              |
|         Seite nach rechts | _Unterschiedlich_              |
|          Bildlauf nach oben | _Unterschiedlich_              |
|        Bildlauf nach unten | _Unterschiedlich_              |
|        Bildlauf nach links | _Unterschiedlich_              |
|       Bildlauf nach rechts | _Unterschiedlich_              |
|          Kontext 1 | X-Taste (_in der Regel_) |
|          Kontext 2 | Y-Taste (_in der Regel_) |
|          Kontext 3 | _Unterschiedlich_              |
|          Kontext 4 | _Unterschiedlich_              |


## <a name="detect-and-track-racing-wheels"></a>Erkennen und Nachverfolgen von Rennlenkrädern

Rennlenkräder werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren. Das System stellt eine Liste der verbundenen Rennlenkräder sowie der Ereignisse bereit, um Sie zu benachrichtigen, wenn ein Rennlenkrad hinzugefügt oder entfernt wird.

### <a name="the-racing-wheels-list"></a>Die Rennlenkradliste

Die Klasse [RacingWheel][] stellt die statische Eigenschaft [RacingWheels][] bereit. Dies ist eine schreibgeschützte Liste der zurzeit verbundenen Rennlenkräder. Da Sie möglicherweise nur an einigen der verbundenen Rennlenkräder interessiert sind, wird empfohlen, dass Sie eine eigene Sammlung verwalten, statt über die Eigenschaft `RacingWheels` auf diese zuzugreifen.

Im folgenden Beispiel werden alle verbundenen Rennlenkräder in eine neue Sammlung kopiert.
```cpp
auto myRacingWheels = ref new Vector<RacingWheel^>();

for (auto racingwheel : RacingWheel::RacingWheels)
{
    // This code assumes that you're interested in all racing wheels.
    myRacingWheels->Append(racingwheel);
}
```

### <a name="adding-and-removing-racing-wheels"></a>Hinzufügen und Entfernen von Rennlenkrädern

Beim Hinzufügen oder Entfernen eines Rennlenkrads werden die Ereignisse [RacingWheelAdded][] und [RacingWheelRemoved][] ausgelöst. Sie können Handler für diese Ereignisse registrieren, um die zurzeit verbundenen Rennlenkräder nachzuverfolgen.

Im folgenden Beispiel wird die Nachverfolgung eines hinzugefügten Rennlenkrads gestartet.
```cpp
RacingWheel::RacingWheelAdded += ref new EventHandler<RacingWheel^>(Platform::Object^, RacingWheel^ args)
{
    // This code assumes that you're interested in all new racing wheels.
    myRacingWheels->Append(args);
}
```

Im folgenden Beispiel wird die Nachverfolgung eines entfernten Rennlenkrads beendet.
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

### <a name="users-and-headsets"></a>Benutzer und Headsets

Jedes Rennlenkrad kann mit einem Benutzerkonto verknüpft werden, um die Identität des Benutzers mit dem Spiel zu verknüpfen, und mit einem Headset verbunden werden, um Sprachchats oder Features im Spiel zu unterstützen. Weitere Informationen zu Benutzern und Headsets finden Sie unter [Nachverfolgen von Benutzern und ihrer Geräte](input-practices-for-games.md#tracking-users-and-their-devices) und [Headsets](headset.md).

## <a name="reading-the-racing-wheel"></a>Lesen der Rennlenkradwerte

Nachdem Sie die Rennlenkräder identifiziert haben, für die Sie sich interessieren, können Sie Eingaben von diesen erfassen. Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Rennlenkräder Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit. Stattdessen müssen Sie regelmäßig den aktuellen Status lesen, indem Sie ihn _abrufen_.

### <a name="polling-the-racing-wheel"></a>Abrufen von Rennlenkrädern

Durch den Abruf wird eine Momentaufnahme des Rennlenkrads zu einem genau festgelegten Zeitpunkt erfasst. Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik in der Regel in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die zusammen erfasst werden, als anhand zahlreicher Eingaben, die über die Zeit erfasst werden.

Sie rufen ein Rennlenkrad durch Aufruf von [GetCurrentReading][] ab. Diese Funktion gibt einen [RacingWheelReading][]-Wert zurück, der den Zustand des Rennlenkrads enthält.

Im folgenden Beispiel wird der aktuelle Zustand eines Rennlenkrads abgerufen.
```cpp
auto racingwheel = myRacingWheels[0];

RacingWheelReading reading = racingwheel->GetCurrentReading();
```

Zusätzlich zum Zustand des Rennlenkrads enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, an dem der Zustand abgerufen wurde. Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Ablesungen oder zum Zeitpunkt der Spielsimulation herzustellen.

### <a name="determining-racing-wheel-capabilities"></a>Ermitteln der Rennlenkradfunktionalität

Viele Steuerelemente eines Rennlenkrads sind optional oder unterstützen verschiedene Varianten. Da dies auch für erforderliche Steuerelemente gilt, müssen Sie die Funktionalität jedes Rennlenkrads einzeln ermitteln, bevor Sie die Eingaben verarbeiten können, die mit den Ablesungen des Rennlenkrads erfasst wurden.

Optionale Steuerelemente sind Handbremse, Kupplung und Gangschaltung. Sie können ermitteln, ob ein verbundenes Rennlenkrad diese Steuerelemente unterstützt, indem Sie die Eigenschaften [HasHandbrake][], [HasClutch][] bzw. [HasPatternShifter][] des Rennlenkrads lesen. Das Steuerelement wird unterstützt, wenn der Wert der Eigenschaft **true** ist. Andernfalls wird es nicht unterstützt.

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

Die Steuerelemente, deren Funktionalität variieren kann, sind das Lenkrad und die Gangschaltung. Das Lenkrad kann hinsichtlich des Umfangs der physischen Drehung variieren, die durch das tatsächliche Lenkrad unterstützt wird. Die Gangschaltung kann hinsichtlich der Zahl der einzelnen Vorwärtsgänge variieren, die unterstützt werden. Sie können den größten, durch das tatsächliche Lenkrad unterstützten Drehwinkel ermitteln, indem Sie die Eigenschaft `MaxWheelAngle` des Rennlenkrads lesen. Dessen Wert entspricht dem maximal unterstützten physischen Winkel im Uhrzeigersinn, ausgedrückt in Grad (positive Gradangabe). Der gleiche Drehwinkel wird in der dem Uhrzeigersinn entgegengesetzten Richtung unterstützt (negative Gradangabe). Sie können den höchsten, durch die Gangschaltung unterstützten Vorwärtsgang ermitteln, indem Sie die Eigenschaft `MaxPatternShifterGear` des Rennlenkrads lesen. Dessen Wert entspricht dem höchsten unterstützten Vorwärtsgang (einschließlich): Wenn der Wert 4 ist, unterstützt die Gangschaltung einen Rückwärtsgang, einen Leerlaufgang sowie einen ersten, zweiten, dritten und vierten Gang.

```cpp
auto maxWheelDegrees = racingwheel->MaxWheelAngle;
auto maxShifterGears = racingwheel->MaxPatternShifterGear;
```

Schließlich unterstützen einige Rennlenkräder die Kraftrückmeldung über das Lenkrad. Sie können ermitteln, ob ein verbundenes Rennlenkrad die Kraftrückmeldung unterstützt, indem Sie die Eigenschaft [WheelMotor][] des Rennlenkrads lesen. Die Kraftrückmeldung wird unterstützt, wenn `WheelMotor` nicht **null** ist. Andernfalls wird sie nicht unterstützt.

```cpp
if (racingwheel->WheelMotor != nullptr)
{
    // force feedback is supported
}
```

Weitere Informationen dazu, wie Sie die Kraftrückmeldungsfunktion der Rennlenkräder verwenden, die dies unterstützen, finden Sie unter [Übersicht über die Kraftrückmeldung](#force-feedback-overview).

### <a name="reading-the-buttons"></a>Lesen der Tastenwerte

Jede Rennlenkradtaste – die vier Richtungen des Steuerkreuzes, die Tasten **Vorheriger Gang** und **Nächster Gang** und 16 zusätzliche Tasten – stellt eine digitale Ablesewert bereit, der angibt, ob sie gedrückt (unten) oder freigegeben (oben) ist. Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte angezeigt, sondern in einem einzelnen Bitfeld zusammengefasst, dargestellt durch die Enumeration [RacingWheelButtons][].

> **Hinweis**    Rennlenkräder besitzen zusätzliche Tasten für die Benutzeroberflächennavigation, beispielsweise die **Ansicht**- und **Menü**-Taste. Diese Tasten sind nicht in der Enumeration `RacingWheelButtons` enthalten und können nur gelesen werden, wenn auf das Rennlenkrad als Benutzeroberflächen-Navigationsgerät zugegriffen wird. Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationsgerät](ui-navigation-controller.md).

Die Tastenwerte werden aus der Eigenschaft `Buttons` der Struktur [RacingWheelReading][] gelesen. Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind, Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie freigeben (oben).

Im folgenden Beispiel wird ermittelt, ob die Taste **Nächster Gang** gedrückt ist.
```cpp
if (RacingWheelButtons::NextGear == (reading.Buttons & RacingWheelButtons::NextGear))
{
    // Next Gear is pressed
}
```

Im folgenden Beispiel wird ermittelt, ob die Taste „Nächster Gang“ freigegeben ist.
```cpp
if (RacingWheelButtons::None == (reading.Buttons & RacingWheelButtons::NextGear))
{
    // Next Gear is released (not pressed)
}
```

In einigen Fällen möchten Sie möglicherweise ermitteln, ob eine Taste von „Gedrückt“ zu „Freigeben“ oder von „Freigegeben“ zu „Gedrückt“ wechselt, ob mehrere Tasten gedrückt oder freigegeben werden, oder ob eine Reihe von Tasten in einer bestimmten Weise angeordnet ist – einige sind gedrückt, andere nicht. Weitere Informationen dazu, wie Sie diese Bedingungen ermitteln, finden Sie unter [Erkennen von Tastenzustandswechseln](input-practices-for-games.md#detecting-button-transitions) und [Erkennen komplexer Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).

### <a name="reading-the-wheel"></a>Lesen der Lenkradwerte

Das Lenkrad ist ein erforderliches Steuerelement, das einen analogen Ablesewert zwischen -1,0 und +1,0 bereitstellt. Der Wert -1,0 entspricht der äußersten linken Lenkradposition. Der Wert +1,0 entspricht der äußersten rechten Lenkradposition. Der Wert für das Lenkrad wird aus der Eigenschaft `Wheel` der Struktur [RacingWheelReading][] gelesen.

```cpp
float wheel = reading.Wheel;  // returns a value between -1.0 and +1.0.
```

Auch wenn die Lenkradwerte dem Grad der physischen Drehung des tatsächlichen Lenkrads entsprechen, abhängig vom durch das physische Rennlenkrad unterstützten Drehbereich, sollten Sie die Lenkradwerte nicht skalieren. Lenkräder, die einen größeren Drehbereich unterstützen, bieten lediglich eine größere Genauigkeit.

### <a name="reading-the-throttle-and-brake"></a>Lesen der Gas- und Bremsensteuerelementwerte

Die Gas- und Bremsensteuerelemente sind erforderliche Steuerelemente, die jeweils analoge Ablesewerte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) bereitstellen, dargestellt als Gleitkommawerte. Der Wert für das Gassteuerelement wird aus der Eigenschaft `Throttle` der Struktur [RacingWheelReading][] gelesen. Der Wert für das Bremsensteuerelement wird aus der Eigenschaft `Brake` gelesen.

```cpp
float throttle = reading.Throttle;  // returns a value between 0.0 and 1.0
float brake    = reading.Brake;     // returns a value between 0.0 and 1.0
```

### <a name="reading-the-handbrake-and-clutch"></a>Lesen der Handbremsen- und Kupplungswerte

Die Handbremsen- und Kupplungssteuerelemente sind optionale Steuerelemente, die jeweils analoge Ablesewerte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) bereitstellen, dargestellt als Gleitkommawerte. Der Wert für das Handbremsensteuerelement wird aus der Eigenschaft `Handbrake` der Struktur [RacingWheelReading][] gelesen. Der Wert für das Kupplungssteuerelement wird aus der Eigenschaft `Clutch` gelesen.

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

### <a name="reading-the-pattern-shifter"></a>Lesen der Gangschaltungswerte

Die Gangschaltung ist ein optionales Steuerelement, das einen digitalen Wert zwischen -1 und [MaxPatternShifterGear][] bereitstellt, dargestellt als ganze Zahl mit Vorzeichen. Der Wert -1 bzw. 0 entspricht dem _Rückwärtsgang_- bzw. dem _Leerlaufgang_. Aufsteigende positive Werte entsprechen den jeweiligen höheren Vorwärtsgängen bis einschließlich [MaxPatternShifterGear][]. Der Wert für die Gangschaltung wird aus der Eigenschaft `PatternShifterGear` der Struktur [RacingWheelReading][] gelesen.

```cpp
if(racingwheel->HasPatternShifter)
{
    gear = reading.PatternShifterGear
}
```

> **Hinweis**    Wenn unterstützt, ist die Gangschaltung zusätzlich zu den erforderlichen Tasten für den vorherigen und den nächsten Gang vorhanden, die sich ebenfalls auf den aktuellen Gang des Autos des Spielers auswirken. Wenn beides vorhanden ist, besteht eine einfache Strategie für die Zusammenführung dieser Eingaben im Ignorieren von Gangschaltung (und Kupplung), wenn sich ein Spieler für ein Automatikgetriebe entscheidet, und im Ignorieren der Tasten für den vorherigen und den nächsten Gang, wenn sich ein Spieler für ein manuelles Getriebe entscheidet (nur möglich, wenn das Rennlenkrad über ein Gangschaltungssteuerelement verfügt). Wenn dies für Ihr Spiel nicht geeignet ist, können Sie eine andere Strategie für die Zusammenführung implementieren.

## <a name="run-the-inputinterfacing-sample"></a>Ausführen des InputInterfacing-Beispiels

Das [InputInterfacingUWP-Beispiel _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) zeigt, wie Rennlenkräder und verschiedene Arten von Eingabegeräten zusammen verwendet werden und wie sich diese Eingabegeräte bei Verwendung als Benutzeroberflächen-Navigationscontroller verhalten.

## <a name="force-feedback-overview"></a>Übersicht über die Kraftrückmeldung

Viele Rennlenkräder besitzen eine Kraftrückmeldungsfunktion, um ein umfassenderes und stärker herausforderndes Fahrerlebnis bereitzustellen. Rennlenkräder, die die Kraftrückmeldung unterstützen, besitzen in der Regel einen einzelnen Motor, der entlang einer einzelnen Achse (der Achse der Lenkraddrehung) Kraft auf das Lenkrad ausübt. Die Kraftrückmeldung wird in Windows 10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input.ForceFeedback] unterstützt.

> **Hinweis**    Die Kraftrückmeldungs-APIs können mehrere Krafteinwirkungsachsen unterstützen. Xbox One-Rennlenkräder unterstützen zurzeit jedoch nur die Lenkraddrehungsachse als Kraftrückmeldungsachse.

## <a name="using-force-feedback"></a>Verwenden der Kraftrückmeldung

In den folgenden Abschnitten werden die Grundlagen der Programmierung von Kraftrückmeldungseffekten für Xbox One-Rennlenkräder beschrieben. Die Rückmeldung wird mithilfe von Effekten angewendet, die zuerst in das Rückmeldungsgerät geladen und anschließend gestartet, angehalten, fortgesetzt und gestoppt werden können, ähnlich wie Soundeffekte. Sie müssen jedoch zunächst die Rückmeldungsfunktionalität des Rennlenkrads ermitteln.

### <a name="determining-force-feedback-capabilities"></a>Ermitteln der Kraftrückmeldungsfunktionalität

Sie können ermitteln, ob ein verbundenes Rennlenkrad die Kraftrückmeldung unterstützt, indem Sie die Eigenschaft [WheelMotor][] des Rennlenkrads lesen. Die Kraftrückmeldung wird nicht unterstützt, wenn `WheelMotor` **null** ist. Andernfalls wird die Kraftrückmeldung unterstützt, und Sie können mit der Ermittlung der spezifischen Kraftrückmeldungsfunktionalität des Motors fortfahren, beispielsweise der Achsen, auf die Kraft ausgeübt werden kann.

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

### <a name="loading-force-feedback-effects"></a>Laden der Kraftrückmeldungseffekte

Die Kraftrückmeldungseffekte werden in das Rückmeldungsgerät geladen, auf dem sie autonom nach den Regeln Ihres Spiels „gespielt“ werden. Es wird eine Reihe von Basiseffekten bereitgestellt. Benutzerdefinierte Effekte können über eine Klasse erstellt werden, die die [IForceFeedbackEffect][]-Schnittstelle implementiert.

| Effektklasse         | Effektbeschreibung                                                                     |
| -------------------- | -------------------------------------------------------------------------------------- |
| ConditionForceEffect | Ein Effekt, der als Reaktion auf den aktuellen Sensor im Gerät unterschiedliche Kraft anwendet. |
| ConstantForceEffect  | Ein Effekt, der eine konstante Kraft entlang eines Vektors anwendet.                                  |
| PeriodicForceEffect  | Ein Effekt, der entlang eines Vektors unterschiedliche Kraft anwendet, definiert durch eine Waveform.           |
| RampForceEffect      | Ein Effekt, der eine linear zunehmende/abnehmende Kraft entlang eines Vektors anwendet.          |


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

### <a name="using-force-feedback-effects"></a>Verwenden von Kraftrückmeldungseffekten

Nach dem Laden können alle Effekte synchron durch das Aufrufen von Funktionen in der Eigenschaft `WheelMotor` des Rennlenkrads oder einzeln durch das Aufrufen von Funktionen im Rückmeldungseffekt selbst gestartet, angehalten, fortgesetzt und gestoppt werden. In der Regel sollten Sie alle Effekte, die Sie verwenden möchten, vor Beginn des Spiels in das Rückmeldungsgerät laden und anschließend die jeweiligen `SetParameters`-Funktionen verwenden,, um die Effekte im Verlauf des Spiels zu aktualisieren.

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

Sie können das gesamte Kraftrückmeldungssystem auf einem bestimmten Rennlenkrad jederzeit asynchron aktivieren, deaktivieren oder zurücksetzen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Windows.Gaming.Input.UINavigationController][]
[Windows.Gaming.Input.IGameController][]


[Windows.Gaming.Input]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[Windows.Gaming.Input.UINavigationController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[Windows.Gaming.Input.IGameController]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[racingwheel]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.aspx
[racingwheels]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheels.aspx
[racingwheeladded]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheeladded.aspx
[racingwheelremoved]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheelremoved.aspx
[haspatternshifter]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.haspatternshifter.aspx
[hashandbrake]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.hashandbrake.aspx
[hasclutch]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.hasclutch.aspx
[maxpatternshiftergear]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.maxpatternshiftergear.aspx
[maxwheelangle]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.maxwheelangle.aspx
[getcurrentreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.getcurrentreading.aspx
[wheelmotor]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.wheelmotor.aspx
[racingwheelreading]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheelreading.aspx
[racingwheelbuttons]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheelbuttons.aspx



<!--HONumber=Dec16_HO4-->


