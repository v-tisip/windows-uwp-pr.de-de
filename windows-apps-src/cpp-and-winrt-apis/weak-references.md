---
author: stevewhims
description: Windows-Runtime ist ein System Verweis gezählt. und in einem solchen System es ist wichtig, dass Sie über die Bedeutung von und den Unterschied zwischen, wissen starke und schwache Referenzen.
title: Schwache Referenzen in C++/WinRT
ms.author: stwhi
ms.date: 10/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, standard, c++, Cpp, Winrt, Projektion, eine sichere, schwache, Referenz
ms.localizationpriority: medium
ms.openlocfilehash: 414a73c8df31e4547b8bd154945a8e9960529320
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4748769"
---
# <a name="strong-and-weak-references-in-cwinrt"></a>Starke und schwache Referenzen in C++ / WinRT

Windows-Runtime ist ein System Verweis gezählt. und in ein solches System ist es wichtig für die starke über die Bedeutung der und die Unterscheidung zwischen, wissen Sie, und schwache Referenzen (und Verweise, die keiner, z. B. den impliziten *diesem* Zeiger sind). Wie Sie in diesem Thema werden feststellen, kann zu wissen, wie Sie diese Verweise korrekt verwalten ausschlaggebend ein zuverlässiges System, das problemlos ausgeführt werden kann, und, die möglicherweise nicht ordnungsgemäß stürzt ab. Durch die Bereitstellung Hilfsfunktionen, die eine umfassende Unterstützung in der Programmiersprache verfügen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Sie in der Mitte bei Ihrer Arbeit der Erstellung komplexer Systeme einfach und korrekt erfüllt.

## <a name="safely-accessing-the-this-pointer-in-a-class-member-coroutine"></a>Problemlos den Zugriff auf das *diesem* Zeiger in einer Coroutine Klassenmember

Der untenstehenden codeauflistung zeigt ein typisches Beispiel für eine Coroutine, die eine Member-Funktion einer Klasse ist.

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;
using namespace std::chrono_literals;

struct MyClass : winrt::implements<MyClass, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    IAsyncOperation<winrt::hstring> RetrieveValueAsync()
    {
        co_await 5s;
        co_return m_value;
    }
};

int main()
{
    winrt::init_apartment();

    auto myclass_instance{ winrt::make_self<MyClass>() };
    auto async{ myclass_instance->RetrieveValueAsync() };

    winrt::hstring result{ async.get() };
    std::wcout << result.c_str() << std::endl;
}
```

**MyClass::RetrieveValueAsync** funktioniert für eine Weile und schließlich wird dann eine Kopie des zurückgegeben der `MyClass::m_value` Datenmember. **RetrieveValueAsync** aufrufen bewirkt, dass ein asynchroner Objekt erstellt werden, und dieses Objekt ist einen impliziten *diesem* Zeiger (über die schließlich `m_value` zugegriffen wird).

Hier ist die vollständige Abfolge von Ereignissen.

1. Im **Hauptmenü**, wird eine Instanz von **MyClass** erstellt (`myclass_instance`).
2. Die `async` Objekt wird erstellt, zeigen (über seine *dieses*) `myclass_instance`.
3. **Winrt::Windows::Foundation::IAsyncAction::get** -Funktion ein paar Sekunden lang blockiert und dann das Ergebnis der **RetrieveValueAsync**zurückgegeben.
4. **RetrieveValueAsync** gibt den Wert der `this->m_value`.

Schritt 4 ist sicherer, solange *diese* gültig ist.

Aber was geschieht, wenn die Klasseninstanz zerstört, bevor der asynchrone Vorgang abgeschlossen ist? Es gibt alle Arten von Methoden, mit denen die Klasseninstanz umgebenden auftreten kann, bevor die asynchrone Methode abgeschlossen wurde. Aber wir können es durch Festlegen der Klasseninstanz zu simulieren `nullptr`.

```cppwinrt
int main()
{
    winrt::init_apartment();

    auto myclass_instance{ winrt::make_self<MyClass>() };
    auto async{ myclass_instance->RetrieveValueAsync() };
    myclass_instance = nullptr; // Simulate the class instance going out of scope.

    winrt::hstring result{ async.get() }; // Behavior is now undefined; crashing is likely.
    std::wcout << result.c_str() << std::endl;
}
```

Nach dem Punkt, in dem wir die Klasseninstanz zerstören, sieht es wie wir direkt darauf erneut verweisen nicht aus. Aber natürlich das asynchrone Objekt verfügt über einen *dieser* Zeiger darauf, und versucht, die zu verwenden, kopieren Sie den Wert in der Klasseninstanz gespeichert. Die Coroutine ist eine Member-Funktion, und es geht davon aus, die *diesen* Zeiger mit verhüten verwenden können.

Aufgrund dieser Änderung an den Code ausgeführt werden wir auf ein Problem in Schritt 4, da die Klasseninstanz zerstört wurde, und *diese* ist nicht mehr gültig. Als das asynchrone Objekt versucht, auf die Variable in der Klasseninstanz zuzugreifen, wird es Absturz (oder Aktionen nicht vollständig definiert).

Die Lösung besteht darin, geben Sie den asynchronen Vorgang&mdash;die Coroutine&mdash;eine eigene starken Verweis auf die Klasseninstanz. Im derzeitigen Zustand enthält die Coroutine effektiv einen unformatierte *diesem* Zeiger auf die Klasseninstanz; aber das ist nicht ausreicht, um eine Instanz der beibehalten werden soll.

Um die Klasseninstanz beizubehalten, ändern Sie die Implementierung von **RetrieveValueAsync** siehe unten.

```cppwinrt
IAsyncOperation<winrt::hstring> RetrieveValueAsync()
{
    auto strong_this{ get_strong() }; // Keep *this* alive.
    co_await 5s;
    co_return m_value;
}
```

Da eine C++ / WinRT-Objekt direkt oder indirekt abgeleitet aus der Vorlage [**WinRT:: Implements**](/uwp/cpp-ref-for-winrt/implements) , C++ / WinRT-Objekt aufrufen seiner [**get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) geschützt-Memberfunktion auf, um einen starken Verweis auf *die Zeiger* abgerufen werden sollen. Beachten Sie, dass keine Notwendigkeit besteht für die eigentliche Verwendung der `strong_this` Variable; nur aufrufen **Get_strong** Ihrer Verweiszähler erhöht und den impliziten *diesem* Zeiger gültig bleibt.

Dies behebt das Problem, das wir zuvor gehabt haben wir mit Schritt 4. Selbst wenn alle anderen Verweise auf die Klasseninstanz ausgeblendet werden, hat die Coroutine übernommen, die Vorsichtsmaßnahme sichergestellt wird, dass dessen Abhängigkeiten stabil sind.

Wenn eine starke Referenz nicht geeignet ist, können Sie stattdessen [**Implements:: get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) rufen Sie einen schwachen Verweis auf *diese*aufrufen. Bestätigen Sie, dass Sie einen starken Verweis abrufen können, bevor Sie auf *diese*zugreifen.

```cppwinrt
IAsyncOperation<winrt::hstring> RetrieveValueAsync()
{
    auto weak_this{ get_weak() }; // Maybe keep *this* alive.

    co_await 5s;

    if (auto strong_this{ weak_this.get() })
    {
        co_return m_value;
    }
    else
    {
        co_return L"";
    }
}
```

Im obigen Beispiel halten nicht der schwache Verweis Sie die Klasseninstanz vom zerstört werden, wenn keine starken Verweise verbleiben. Aber es ist eine Möglichkeit prüfen, ob eine starke Referenz erworben werden kann, bevor Sie den Zugriff auf die Membervariable fest.

## <a name="safely-accessing-the-this-pointer-with-an-event-handling-delegate"></a>Problemlos den Zugriff auf *diesen* Zeiger mit einer Ereignisbehandlung Delegaten

### <a name="the-scenario"></a>Das Szenario

Allgemeine Informationen zur Ereignisbehandlung finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++ / WinRT](handle-events.md).

Im vorherige Abschnitt hervorgehoben potenzielle Probleme mit der Lebensdauer in den Bereichen Coroutinen und Parallelität. Wenn Sie ein Ereignis mit Mitgliedsfunktion eines Objekts oder innerhalb von behandeln müssen eine Lambda-Funktion innerhalb der Mitgliedsfunktion eines Objekts, dann können Sie über die relative Lebensdauer des Ereignisempfängers (das Objekt, das das Ereignis behandelt) und die Ereignisquelle (das Objekt vorstellen jedoch das Ereignis auslöst). Betrachten wir einige Codebeispiele.

Im Codebeispiel unten definiert zuerst eine einfache **Ereignisquelle** -Klasse, die ein allgemeines Ereignis auslöst, das indem Sie alle Delegaten behandelt wird, die sie hinzugefügt wurden. Dieses Beispiel-Ereignis tritt auf, um den Delegattyp [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) verwenden, aber die Probleme und Problembehandlungen hier gelten für alle Delegattypen.

Anschließend stellt die **EventRecipient** -Klasse einen Handler für das Ereignis **EventSource::Event** in Form einer Lambda-Funktion.

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;

struct EventSource
{
    winrt::event<EventHandler<int>> m_event;

    void Event(EventHandler<int> const& handler)
    {
        m_event.add(handler);
    }

    void RaiseEvent()
    {
        m_event(nullptr, 0);
    }
};

struct EventRecipient : winrt::implements<EventRecipient, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    void Register(EventSource& event_source)
    {
        event_source.Event([&](auto&& ...)
        {
            std::wcout << m_value.c_str() << std::endl;
        });
    }
};

int main()
{
    winrt::init_apartment();

    EventSource event_source;
    auto event_recipient{ winrt::make_self<EventRecipient>() };
    event_recipient->Register(event_source);
    event_source.RaiseEvent();
}
```

Das Muster besteht darin, dass Ereignisempfängers einen Ereignishandler Lambda-Funktion mit Abhängigkeiten für die *diesen* Zeiger. Wenn der Ereignis Empfänger die Ereignisquelle überlebt, überlebt es diese Abhängigkeiten. Und in diesen Fällen, die häufig verwendet werden, das Muster eignet sich gut. Einige dieser Fälle sind offensichtlich, z. B. wenn eine UI-Seite ein Ereignis verarbeitet, das von einem Steuerelement ausgelöst wird, das sich auf der Seite befindet. Die Seite "die Schaltfläche überlebt&mdash;also der Handler auch die Schaltfläche überlebt. Dies gilt immer dann, wenn der Empfänger die Quelle besitzt (z. B. als Datenelement), oder wenn der Empfänger und die Quelle gleichgeordnet sind und sich direkt im Besitz eines anderen Objekts befinden. Wenn Sie sicher sind, dass Sie einen Fall haben, in dem der Handler das *this*-Objekt nicht überleben wird, können Sie *this*normal verwenden, ohne Rücksicht auf eine starke oder schwache Lebensdauer zu nehmen.

Aber es gibt immer noch Fälle, in denen *diese* nicht überlebt seine Verwendung in einem Handler (einschließlich Handlern für Completion- und Progress-Ereignisse, die durch asynchrone Aktionen und Vorgänge ausgelöst werden), und es ist wichtig zu wissen, wie Sie mit ihnen arbeiten.

- Wenn Sie eine Coroutine erstellen, um eine asynchrone Methode zu implementieren, dann ist dies möglich.
- In seltenen Fällen mit bestimmten XAML-UI-Framework-Objekten (z. B. [**SwapChainPanel**](/uwp/api/windows.ui.xaml.controls.swapchainpanel)) ist dies möglich wenn der Empfänger finalisiert wird, ohne die Registrierung für die Ereignisquelle aufzuheben.

### <a name="the-issue"></a>Das Problem

Dieses nächste Version der **main** -Funktion simuliert, was geschieht, wenn der Empfänger Ereignis zerstört wird (z. B. es den gültigen Bereich verlässt) während die Ereignisquelle noch Auslösen von Ereignissen ist.

```cppwinrt
int main()
{
    winrt::init_apartment();

    EventSource event_source;
    auto event_recipient{ winrt::make_self<EventRecipient>() };
    event_recipient->Register(event_source);
    event_recipient = nullptr; // Simulate the event recipient going out of scope.
    event_source.RaiseEvent(); // Behavior is now undefined within the lambda event handler; crashing is likely.
}
```

Ereignisempfängers zerstört, aber der Lambda-Ereignishandler darin ist weiterhin für **das Ereignis** abonniert. Wenn das Ereignis ausgelöst wird, versucht der Lambda-Ausdruck, der *diesem* Zeiger zu dereferenzieren, der an diesem Punkt ungültig ist. Dies führt eine zugriffsverletzung durch Code im Ereignishandler (oder in der Fortsetzung einer Coroutine) versucht, es zu verwenden.

> [!IMPORTANT]
> Wenn Sie eine solchen Situation auftreten, müssen Sie über die Lebensdauer des *dieses* Objekt vorstellen. und davon, ob die aufgenommenen *dieses* Objekt die Aufnahme überlebt. Wenn dies nicht der Fall, dann verwenden Sie es mit einer starken oder eine schwache Referenz wie weiter unten unten erläutert.
>
> Oder&mdash;Wenn es für Ihr Szenario sinnvoll ist, und wenn threading-Überlegungen ermöglichen es sogar&mdash;und dann eine andere Möglichkeit besteht darin, den Handler zu widerrufen, nachdem der Empfänger mit dem Ereignis oder in der Destruktor des Empfängers fertig ist. Finden Sie in [einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).

Dies ist wie wir den Ereignishandler registriert werden.

```cppwinrt
event_source.Event([&](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

Die Lambda-Funktion wird automatisch alle lokalen Variablen durch einen Verweis erfasst. Ja, in diesem Beispiel wir könnten vorigen dies geschrieben haben.

```cppwinrt
event_source.Event([this](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

In beiden Fällen sind wir gerade den unformatierten *dieses* -Zeiger erfassen. Und die keine Auswirkung auf die Referenzzähler, sodass nichts das aktuelle Objekt zerstört wird verhindert.

### <a name="the-solution"></a>Die Lösung

Die Lösung besteht darin einen starken Verweis erfassen. Eine starke Referenz *ist* erhöht die Referenzzähler, und es *wird* die Reaktionsfähigkeit der aktuellen Objekt aktiv. Sie deklarieren Sie eine Variable Aufnahme (aufgerufen `strong_this` in diesem Beispiel), und initialisieren Sie es mit einem Aufruf von [**get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function), die einen starken Verweis auf unser *diesen* Zeiger abruft.

```cppwinrt
event_source.Event([this, strong_this { get_strong()}](auto&& ...)
{
    std::wcout << m_value.c_str() << std::endl;
});
```

Sogar können Sie auslassen der automatische Erfassung des aktuellen Objekts und greifen Sie auf das Datenelement über die Aufnahme Variable anstelle von über den impliziten *diese*.

```cppwinrt
event_source.Event([strong_this { get_strong()}](auto&& ...)
{
    std::wcout << strong_this->m_value.c_str() << std::endl;
});
```

Wenn eine starke Referenz nicht geeignet ist, können Sie stattdessen [**Implements:: get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function) rufen Sie einen schwachen Verweis auf *diese*aufrufen. Bestätigen Sie, dass Sie einen starken Verweis weiterhin daraus abrufen können, bevor Sie den Zugriff auf Member.

```cppwinrt
event_source.Event([weak_this{ get_weak() }](auto&& ...)
{
    if (auto strong_this{ weak_this.get() })
    {
        std::wcout << strong_this->m_value.c_str() << std::endl;
    }
});
```

### <a name="if-you-use-a-member-function-as-a-delegate"></a>Wenn Sie eine Member-Funktion als Delegaten verwenden

Als auch Lambda-Funktionen, diese Grundsätze gelten auch für eine Member-Funktion als den Delegaten verwenden. Die Syntax unterscheidet, also sehen wir uns etwas Code. Hier wird zunächst mithilfe eines unformatierten *dieses* Zeigers potenziell unsichere Member-Funktion-Ereignishandler.

```cppwinrt
struct EventRecipient : winrt::implements<EventRecipient, IInspectable>
{
    winrt::hstring m_value{ L"Hello, World!" };

    void Register(EventSource& event_source)
    {
        event_source.Event({ this, &EventRecipient::OnEvent });
    }

    void OnEvent(IInspectable const& /* sender */, int /* args */)
    {
        std::wcout << m_value.c_str() << std::endl;
    }
};
```

Dies ist der standard, herkömmlichen Möglichkeit zum Verweisen auf ein Objekt und dessen Member-Funktion. Um dies zu sicherer machen, können Sie&mdash;ab Version 10.0.17763.0 (Windows 10, Version 1809) des Windows SDKS&mdash;herstellen eine starke oder schwache Referenz auf den Punkt, in dem der Handler registriert ist. Der Empfänger-Ereignisobjekt bekanntermaßen an diesem Punkt ist immer noch verwendet werden.

Rufen Sie einfach für einen starken Verweis [**Get_strong**](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function) "anstelle von" raw *diesem* Zeiger. C++ / WinRT stellt sicher, dass der resultierende Delegat einen starken Verweis auf das aktuelle Objekt enthält.

```cppwinrt
event_source.Event({ get_strong(), &EventRecipient::OnEvent });
```

Rufen Sie für eine schwache Referenz [**Get_weak**](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function). C++ / WinRT stellt sicher, dass der resultierende Delegat eine schwache Referenz enthält. In letzter Minute, im Hintergrund der Delegat versucht, den schwachen Verweis auf eine starke aufzulösen und nur die Memberfunktion aufruft, wenn dies erfolgreich ist.

```cppwinrt
event_source.Event({ get_weak(), &EventRecipient::OnEvent });
```

### <a name="a-weak-reference-example-using-swapchainpanelcompositionscalechanged"></a>Eine schwache Referenz Beispiel für die Verwendung von **SwapChainPanel::CompositionScaleChanged**

In diesem Beispiel verwenden wir das [**SwapChainPanel::CompositionScaleChanged**](/uwp/api/windows.ui.xaml.controls.swapchainpanel.compositionscalechanged) Ereignis über einen anderen Illustration schwache Referenzen. Der Code registriert einen Ereignis-Handler mit einer Lambda-Funktion, die eine schwache Referenz auf den Empfänger erfasst.

```cppwinrt
winrt::Windows::UI::Xaml::Controls::SwapChainPanel m_swapChainPanel;
winrt::event_token m_compositionScaleChangedEventToken;

void RegisterEventHandler()
{
    m_compositionScaleChangedEventToken = m_swapChainPanel.CompositionScaleChanged([weak_this{ get_weak() }]
        (Windows::UI::Xaml::Controls::SwapChainPanel const& sender,
        Windows::Foundation::IInspectable const& object)
    {
        if (auto strong_this{ weak_this.get() })
        {
            strong_this->OnCompositionScaleChanged(sender, object);
        }
    });
}

void OnCompositionScaleChanged(Windows::UI::Xaml::Controls::SwapChainPanel const& sender,
    Windows::Foundation::IInspectable const& object)
{
    // Here, we know that the "this" object is valid.
}
```

In der Lamba-Bedingung wird eine temporäre Variable erzeugt, die eine schwache Referenz auf *this* darstellt. In der Lambda wird die Funktion **OnCompositionScaleChanged** aufgerufen, wenn eine starke Referenz auf *this* abgerufen werden kann. Auf diese Weise kann *this* innerhalb von **OnCompositionScaleChanged** sicher verwendet werden.

## <a name="weak-references-in-cwinrt"></a>Schwache Referenzen in C++/WinRT

Oben haben wir gesehen, schwache Verweise verwendet wird. Im Allgemeinen sind, ist dies eignet sich gut für zyklische Referenzen unterbrechen. Z. B. für die systemeigene Implementierung des XAML-basierte Benutzeroberflächen-Frameworks&mdash;aufgrund des historischen Designs des Frameworks&mdash;der schwache verweisen in C++ / WinRT ist erforderlich, um zyklische Referenzen zu verarbeiten. Außerhalb von XAML jedoch wahrscheinlich müssen Sie nicht schwache Referenzen verwenden (nicht, dass es nichts gibt grundsätzlich XAML-spezifisches über diese). Anstatt Sie sollten mehr häufig als nicht in der Lage, Entwerfen Sie Ihre eigenen C++ / WinRT-APIs so, dass zyklische Referenzen und schwache Referenzen vermieden. 

Bei einem von Ihnen deklarierten Typ ist es für C++/WinRT nicht sofort ersichtlich, ob oder wann schwache Referenzen benötigt werden. Daher bietet C++/WinRT für die Strukturvorlage [**winrt::implements**](/uwp/cpp-ref-for-winrt/implements) automatisch eine Unterstützung von schwache Referenzen. Von dieser werden Ihre eigenen C++/WinRT-Typen direkt oder indirekt abgeleitet. Dies kostet Sie nichts, es sei denn, Ihr Objekt wird tatsächlich auf [**IWeakReferenceSource**](/windows/desktop/api/weakreference/nn-weakreference-iweakreferencesource) abgefragt. Und Sie können sich explizit [gegen diese Unterstützung](#opting-out-of-weak-reference-support) entscheiden.

### <a name="code-examples"></a>Codebeispiele
Die Strukturvorlage [**winrt::weak_ref**](/uwp/cpp-ref-for-winrt/weak-ref) ist eine Option, um eine schwache Referenz auf eine Klasseninstanz zu erhalten.

```cppwinrt
Class c;
winrt::weak_ref<Class> weak{ c };
```

Oder Sie können die Hilfsfunktion [**winrt::make_weak**](/uwp/cpp-ref-for-winrt/make-weak) verwenden.

```cppwinrt
Class c;
auto weak = winrt::make_weak(c);
```

Die Erstellung einer schwachen Referenz hat keinen Einfluss auf die Anzahl der Referenzen auf das Objekt selbst, sondern bewirkt lediglich die Zuweisung eines Kontrollblocks. Dieser Kontrollblock kümmert sich um die Implementierung der schwachen Referenzsemantik. Sie können dann versuchen, den schwachen Verweis auf einen starken Verweis hochzustufen (und, wenn dies erfolgreich ist, ihn zu verwenden).

```cppwinrt
if (Class strong = weak.get())
{
    // use strong, for example strong.DoWork();
}
```

Sofern noch eine andere starke Referenz existiert, erhöht der Aufruf von [**weak_ref::get**](/uwp/cpp-ref-for-winrt/weak-ref#weakrefget-function) die Referenzanzahl und gibt die starke Referenz an den Aufrufer zurück.

### <a name="opting-out-of-weak-reference-support"></a>Opt-out der Unterstützung von schwachen Referenzen
Die Unterstützung schwacher Referenzen erfolgt automatisch. Sie können diese Unterstützung jedoch explizit deaktivieren, indem Sie die [**winrt::no_weak_ref**](/uwp/cpp-ref-for-winrt/no-weak-ref)-Markerstruktur als template-Argument an Ihre Basisklasse übergeben.

Wenn Sie direkt von **winrt::implements** ableiten.

```cppwinrt
struct MyImplementation: implements<MyImplementation, IStringable, no_weak_ref>
{
    ...
}
```

Wenn Sie eine Laufzeitklasse schreiben.

```cppwinrt
struct MyRuntimeClass: MyRuntimeClassT<MyRuntimeClass, no_weak_ref>
{
    ...
}
```

Dabei spielt es keine Rolle, wo im Variadic-Parameterpaket die Markerstruktur erscheint. Wenn Sie eine schwache Referenz für einen Opted-Out-Typ anfordern, dann hilft Ihnen der Compiler mit der Meldung „*Dies ist nur für die Unterstützung schwacher Referenzen*”.

## <a name="important-apis"></a>Wichtige APIs
* [implements::get_weak Funktion](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [winrt::make_weak Funktionsvorlage](/uwp/cpp-ref-for-winrt/make-weak)
* [winrt::no_weak_ref Markerstruktur](/uwp/cpp-ref-for-winrt/no-weak-ref)
* [winrt::weak_ref Strukturvorlage](/uwp/cpp-ref-for-winrt/weak-ref)
