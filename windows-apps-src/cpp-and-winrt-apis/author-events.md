---
author: stevewhims
description: Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse enthält, die Ereignisse auslöst. Es zeigt außerdem eine App, die die Komponente nutzt und die Ereignisse verarbeitet.
title: Erstellen von Ereignissen mit C++/WinRT
ms.author: stwhi
ms.date: 07/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, erstellen, ereignis
ms.localizationpriority: medium
ms.openlocfilehash: 82239436acfe82bf99cd1e665cca14592bbcef74
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4430890"
---
# <a name="author-events-in-cwinrt"></a>Erstellen von Ereignissen mit C++/WinRT

Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät. Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.

> [!NOTE]
> Informationen zur Installation und Verwendung der [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) Visual Studio Extension (VSIX) (bietet projektvorlagenunterstützung sowie C++ / WinRT MSBuild-Eigenschaften und-Ziele) finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a>Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)

Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie eine **Visual C++** > **Universelle Windows-** > **Komponente für Windows-Runtime (C++ / WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für "Bankkonto Komponente für Windows-Runtime").

Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`. Benennen Sie diese Datei `BankAccount.idl` (Umbenennen der `.idl` Datei benennt automatisch der abhängigen `.h` und `.cpp` Dateien zu). Ersetzen Sie den Inhalt des `BankAccount.idl` mit den folgenden Eintrag.

```idl
// BankAccountWRC.idl
namespace BankAccountWRC
{
    runtimeclass BankAccount
    {
        BankAccount();
        event Windows.Foundation.EventHandler<Single> AccountIsInDebit;
        void AdjustBalance(Single value);
    };
}
```

Speichern Sie die Datei. Erstellen des Projekts wird nicht bis zum Abschluss im Moment, aber nun erstellen ist hilfreich, etwas zu tun, da er die Quellcodedateien generiert, in denen Sie die Laufzeitklasse **BankAccount** implementieren. So einfach, und erstellen Sie jetzt (die Buildfehler zu erwarten, dass in dieser Phase finden Sie unter müssen mit `Class.h` und `Class.g.h` nicht gefunden wird). Während des Buildprozesses die `midl.exe` -Tool ausgeführt, um Ihre Komponente Windows-Runtime-Metadaten-Datei erstellen (also `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`). Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen. Diese Dateien enthalten Stubs, um die erste Schritte zum Implementieren der **BankAccount** -Runtime-Klasse, die Sie in Ihrer IDL deklariert haben. Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.

Kopieren Sie die Stub-Dateien im Datei-Explorer `BankAccount.h` und `BankAccount.cpp` aus dem Ordner `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` in den Ordner, die Ihre Projektdateien enthält, ist die `\BankAccountWRC\BankAccountWRC\`, und Ersetzen Sie die Dateien in das Ziel. Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse. Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

    private:
        winrt::event<Windows::Foundation::EventHandler<float>> m_accountIsInDebitEvent;
        float m_balance{ 0.f };
    };
}
...
```

Wie oben zu sehen ist, wird das Ereignis hinsichtlich der strukturvorlage [**winrt::event**](/uwp/cpp-ref-for-winrt/event) , indem eines bestimmten Delegattyps parametrisiert implementiert.

Implementieren Sie in `BankAccount.cpp` die Funktionen wie im folgenden Codebeispiel gezeigt. In C++/WinRT wird ein IDL-deklariertes Ereignis als ein Set überladener Funktionen implementiert (ähnlich wie eine Eigenschaft als ein Paar von überladenen Get- und Set-Funktionen implementiert wird). Eine Überladung übernimmt einen zu registrierenden Delegaten und gibt einen Token zurück. Die andere übernimmt einen Token und widerruft die Registrierung des zugeordneten Delegats.

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    winrt::event_token BankAccount::AccountIsInDebit(Windows::Foundation::EventHandler<float> const& handler)
    {
        return m_accountIsInDebitEvent.add(handler);
    }

    void BankAccount::AccountIsInDebit(winrt::event_token const& token)
    {
        m_accountIsInDebitEvent.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        m_balance += value;
        if (m_balance < 0.f) m_accountIsInDebitEvent(*this, m_balance);
    }
}
```

Sie müssen nicht die Überladung für den Ereignis-Revoker implementieren (weitere Informationen siehe [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate))– dies übernimmt die C++/WinRT-Projektion für Sie. Die anderen Überladungen sind nicht in die Projektion integriert, um Ihnen die Flexibilität zu geben, sie für Ihr Szenario optimal zu implementieren. Ein derartiger Aufruf von [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) und [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) ist eine effiziente und parallele/threadsichere Standardmethode. Wenn Sie jedoch über eine große Anzahl von Ereignissen verfügen, möchten Sie möglicherweise nicht für jedes ein Ereignisfeld, sondern vielmehr eine Implementierung mit geringer Dichte.

Sie sehen oben, dass die Implementierung der Funktion **AdjustBalance** das Ereignis **AccountIsInDebit** auslöst, wenn der Saldo negativ wird.

Wenn alle Warnungen der Erstellung hindern, dann lösen sie oder legen Sie die Projekteigenschaft **C/C++** > **Allgemeine** > **Warnungen als Fehler behandeln** **Nein (/ WX-)**, und erstellen Sie das Projekt erneut.

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a>Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime

Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen). Erstellen Sie eine **Visual C++** > **Universelle Windows-** > **Core App (C++ / WinRT)** Projekt und nennen Sie es *BankAccountCoreApp*.

Fügen Sie einen Verweis hinzu, und navigieren Sie zu `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder fügen Sie einen Projekt-zu-Projekt-Verweis hinzu, wenn die beiden Projekte in der gleichen Projektmappe befinden). Klicken Sie auf **Hinzufügen** und dann auf **OK**. Erstellen Sie jetzt BankAccountCoreApp. Im unwahrscheinlichen Fall, dass ein Fehler angezeigt, die die Payload-Datei `readme.txt` nicht existiert, schließen Sie diese Datei aus dem Komponente für Windows-Runtime-Projekt, erstellen Sie Sie neu, und erstellen Sie bankaccountcoreapp neu.

Während des Buildprozesses wird das `cppwinrt.exe`-Tool ausgeführt, um die referenzierte `.winmd`-Datei in Quellcodedateien zu verarbeiten, die projizierte Typen enthalten, um Sie bei der Verwendung Ihrer Komponente zu unterstützen. Der Header für die projizierten Typen für die Laufzeitklassen Ihrer Komponente (mit dem Namen `BankAccountWRC.h`) wird im Ordner `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\` generiert.

Fügen Sie diesen Header in `App.cpp` ein.

```cppwinrt
#include <winrt/BankAccountWRC.h>
```

Fügen Sie in `App.cpp` ebenfalls den folgenden Code ein, um ein BankAccount zu instanziieren (unter Verwendung des Standardkonstruktors des projizierten Typs), registrieren Sie einen Ereignis-Handler und sorgen Sie dann dafür, dass das Konto ins Minus geht.

```cppwinrt
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount m_bankAccount;
    winrt::event_token m_eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        m_eventToken = m_bankAccount.AccountIsInDebit([](const auto &, float balance)
        {
            WINRT_ASSERT(balance < 0.f);
        });
    }
    ...

    void Uninitialize()
    {
        m_bankAccount.AccountIsInDebit(m_eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        m_bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab. Um zu zeigen, dass das Ereignis wie erwartet ausgelöst wird, setzen Sie einen Haltepunkt in der Lambda-Ausdruck, der das Ereignis **AccountIsInDebit** verarbeitet, führen Sie die app und innerhalb des Fensters auf.

## <a name="parameterized-delegates-and-simple-signals-across-an-abi"></a>Parametrisierten Delegaten und einfache Signale über eine ABI

Wenn das Ereignis über eine Application binary Interface (ABI) verfügbar sein muss&mdash;z. B. zwischen einer Komponente und verwendenden dargestellte&mdash;und dann das Ereignis einen Windows-Runtime-Delegattyp verwenden muss. Im obigen Beispiel verwendet die [**Windows::Foundation::EventHandler\ < T\ >**](/uwp/api/windows.foundation.eventhandler) Windows-Runtime-Delegattyp. [**TypedEventHandler\ < TSender, TResult\ >**](/uwp/api/windows.foundation.eventhandler) ist ein weiteres Beispiel für ein Windows-Runtime-Delegattyp.

Die Typparameter für diese zwei Delegattypen müssen die ABI überschreiten, damit die Typparameter zu Windows-Runtime-Typen sein müssen. Erst- und Drittanbieter Laufzeitklassen sowie primitive Typen wie z. B. Zahlen und Zeichenfolgen enthält. Der Compiler hilft Ihnen mit dem Fehler "*WinRT-Typ*", wenn Sie diese Einschränkung vergessen.

Wenn Sie keine Parameter oder Argumente mit dem Ereignis übergeben müssen, können Sie Ihre eigene einfache Windows-Runtime-Delegattyp definieren. Das folgende Beispiel zeigt eine einfachere Version der Laufzeitklasse **BankAccount** . Delegattyp **SignalDelegate** deklariert und verwendet, die ein Ereignis Signal-Typ anstelle eines Ereignisses mit einem Parameter auslösen.

```idl
// BankAccountWRC.idl
namespace BankAccountWRC
{
    delegate void SignalDelegate();

    runtimeclass BankAccount
    {
        BankAccount();
        event BankAccountWRC.SignalDelegate SignalAccountIsInDebit;
        void AdjustBalance(Single value);
    };
}
```

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

        winrt::event_token SignalAccountIsInDebit(BankAccountWRC::SignalDelegate const& handler);
        void SignalAccountIsInDebit(winrt::event_token const& token);
        void AdjustBalance(float value);

    private:
        winrt::event<BankAccountWRC::SignalDelegate> m_signal;
        float m_balance{ 0.f };
    };
}
```

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    winrt::event_token BankAccount::SignalAccountIsInDebit(BankAccountWRC::SignalDelegate const& handler)
    {
        return m_signal.add(handler);
    }

    void BankAccount::SignalAccountIsInDebit(winrt::event_token const& token)
    {
        m_signal.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        m_balance += value;
        if (m_balance < 0.f)
        {
            m_signal();
        }
    }
}
```

```cppwinrt
// App.cpp
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount m_bankAccount;
    winrt::event_token m_eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        m_eventToken = m_bankAccount.SignalAccountIsInDebit([] { /* ... */ });
    }
    ...

    void Uninitialize()
    {
        m_bankAccount.SignalAccountIsInDebit(m_eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        m_bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

## <a name="parameterized-delegates-simple-signals-and-callbacks-within-a-project"></a>Parametrisierten Delegaten, einfachen Signale und Rückrufe innerhalb eines Projekts

Wenn das Ereignis nur intern verwendet wird, in Ihrer C++ / WinRT projizieren (nicht über Binärdateien), und Sie weiterhin die strukturvorlage [**winrt::event**](/uwp/cpp-ref-for-winrt/event) verwenden, aber Sie parametrisieren es mit C++ / WinRT nicht-Windows-Runtime- [**WinRT:: Delegate&lt;… T&gt; **](/uwp/cpp-ref-for-winrt/delegate) strukturvorlage, die eine effiziente und Referenz-gezählt Delegat ist. Es unterstützt eine beliebige Anzahl von Parametern und sind nicht für Windows-Runtime-Typen beschränkt.

Das folgende Beispiel zeigt einen Delegaten zuerst, Signatur, die keine Parameter (im Wesentlichen eine einfache Signal) und dann ein, die eine Zeichenfolge übernimmt.

```cppwinrt
winrt::event<winrt::delegate<>> signal;
signal.add([] { std::wcout << L"Hello, "; });
signal.add([] { std::wcout << L"World!" << std::endl; });
signal();

winrt::event<winrt::delegate<std::wstring>> log;
log.add([](std::wstring const& message) { std::wcout << message.c_str() << std::endl; });
log.add([](std::wstring const& message) { Persist(message); });
log(L"Hello, World!");
```

Beachten Sie, wie Sie das Ereignis hinzufügen können beliebig viele abonnierende Delegaten wie gewünscht. Es gibt jedoch Mehraufwand ein Ereignis zugeordnet. Wenn Sie benötigen lediglich einen einfachen Rückruf mit nur einem einzelnen abonnierenden Delegaten, können Sie [**WinRT:: Delegate&lt;… T&gt; **](/uwp/cpp-ref-for-winrt/delegate) eigenständig.

```cppwinrt
winrt::delegate<> signalCallback;
signalCallback = [] { std::wcout << L"Hello, World!" << std::endl; };
signalCallback();

winrt::delegate<std::wstring> logCallback;
logCallback = [](std::wstring const& message) { std::wcout << message.c_str() << std::endl; }f;
logCallback(L"Hello, World!");
```

Wenn Sie von einer C++ Portieren / CX-Codebasis, wo Ereignisse und Delegate intern innerhalb eines Projekts verwendet werden, und klicken Sie dann **WinRT:: Delegate** hilft Ihnen beim Replizieren dieses Musters in C++ / WinRT.

## <a name="design-guidelines"></a>Entwurfsrichtlinien

Es wird empfohlen, dass Sie Ereignisse und nicht Delegaten als Funktionsparameter übergeben. Die **add** -Funktion des [**winrt::event**](/uwp/cpp-ref-for-winrt/event) ist die einzige Ausnahme, da Sie einen Delegaten in diesem Fall übergeben müssen. Der Grund für diese Richtlinie ist, Delegaten unterschiedliche Formen, in anderen Windows-Runtime-Sprachen annehmen können (hinsichtlich der gibt an, ob sie eine Clientregistrierung oder mehrere unterstützen). Ereignisse, mit deren Modell mit mehreren Abonnenten bilden eine sehr viel besser vorhersehbare und einheitliche Option.

Die Signatur für den Ereignishandlerdelegaten sollten bestehen aus zwei Parameter: *Absender* (**IInspectable**) und *Args* (einige Ereignisargumenttyp, z. B. [**RoutedEventArgs**](/uwp/api/windows.ui.xaml.routedeventargs)).

Beachten Sie, dass diese Richtlinien nicht unbedingt angewendet werden, wenn Sie eine interne API entwerfen. Obwohl interne APIs häufig im Laufe der Zeit veröffentlicht.

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von APIs mit C++/WinRT](author-apis.md)
* [Verwenden von APIs mit C++/WinRT](consume-apis.md)
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
