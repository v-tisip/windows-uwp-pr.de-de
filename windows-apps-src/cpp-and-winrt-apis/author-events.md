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
ms.openlocfilehash: 3b52bf8e33bbf111dd02c695d8c3baf77e1338ac
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2891092"
---
# <a name="author-events-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Erstellen von Ereignissen mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)

Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät. Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a>Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)

Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie ein **Visual C++ Windows-Runtime Component (C++/WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für „Bankkonto-Komponente für Windows-Runtime”).

Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`. Benennen Sie diese Datei `BankAccount.idl` (Umbenennen der `.idl` Datei benennt automatisch der abhängigen `.h` und `.cpp` Dateien zu). Ersetzen Sie den Inhalt der `BankAccount.idl` mit der Liste unten.

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

Speichern Sie die Datei. Erstellen Sie das Projekt wird nicht erfolgreich abgeschlossen, in dem Moment, aber jetzt erstellen, ist ein sinnvoll, da die Quellcodedateien generiert wird, in denen Sie die **BankAccount** Common Language Runtime-Klasse implementieren können. So fahren Sie fort, und erstellen Sie jetzt (die Buildfehler zu erwarten, dass in dieser Phase finden Sie unter mit zu tun haben `Class.h` und `Class.g.h` nicht gefunden wurde). Beim Erstellen die `midl.exe` Tool wird ausgeführt, um die Komponente Windows-Runtime Metadaten-Datei zu erstellen (also `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`). Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen. Diese Dateien enthalten Stubs, um Ihnen den Einstieg Implementieren der **BankAccount** Runtime-Klasse, die Sie in Ihre IDL deklariert zu erhalten. Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.

Kopieren Sie die Stub-Dateien im Datei-Explorer `BankAccount.h` und `BankAccount.cpp` aus dem Ordner `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` in den Ordner, die Ihre Projektdateien enthält, wird die `\BankAccountWRC\BankAccountWRC\`, und Ersetzen Sie die Dateien in das Ziel. Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse. Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).

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

Wie oben zu sehen ist, wird das Ereignis im Hinblick auf die Vorlage [**winrt::event**](/uwp/cpp-ref-for-winrt/event) Struktur, nach einer bestimmten Stellvertretung Typ parametrisiert implementiert.

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

Wenn alle Warnungen Sie zum Erstellen von zu verhindern, klicken Sie dann entweder beheben Sie diese oder legen Sie die Projekteigenschaft **C/C++-** > **Allgemeine** > **Warnungen als Fehler behandeln** , die **No (/ WX-)**, und erstellen Sie das Projekt erneut.

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a>Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime

Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen). Erstellen Sie ein **Visual C++ Core App (C++/WinRT)**-Projekt, und nennen Sie es *BankAccountCoreApp*.

Fügen Sie einen Verweis hinzu, und wechseln Sie zur `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder einen Projekt in Project Verweis hinzufügen, wenn beide Projekte in der gleichen Projektmappe sind). Klicken Sie auf **Hinzufügen** und dann auf **OK**. Erstellen Sie jetzt BankAccountCoreApp. Im unwahrscheinlichen Fall, dass ein Fehler angezeigt, die die Nutzlastdatei `readme.txt` nicht vorhanden, diese Datei aus dem Windows-Laufzeitkomponente Projekt ausschließen, erstellen Sie ihn neu und dann neu erstellen BankAccountCoreApp.

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

Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab. Um zu veranschaulichen, dass das Ereignis ausgelöst wird, wie erwartet, setzen Sie einen Haltepunkt innerhalb der Lambda-Ausdruck, der die **AccountIsInDebit** Ereignisbehandlung, Ausführen der app, und klicken Sie in das Fenster.

## <a name="parameterized-delegates-and-simple-signals-across-an-abi"></a>Parametrisierte Stellvertretungen und einfachen signalisiert, über eine ABI

Wenn das Ereignis über eine binäre Anwendungsschnittstelle (ABI) zugegriffen werden muss&mdash;beispielsweise zwischen einer Komponente und der Dienste in Anspruch nehmenden Anwendung&mdash;und klicken Sie dann das Ereignis einen Typ der Windows-Runtime-Delegaten verwendet werden muss. Im obigen Beispiel verwendet [**Windows::Foundation::EventHandler\ < T\ >**](/uwp/api/windows.foundation.eventhandler) Windows-Runtime-Delegaten. [**TypedEventHandler\ < TSender, TResult\ >**](/uwp/api/windows.foundation.eventhandler) ist ein weiteres Beispiel für einen Typ der Windows-Runtime-Delegaten.

Typparameter für diese zwei Delegattypen haben die ABI schneidet, damit die Typparameter zu Windows-Runtime-Typen werden müssen. Erste und Drittanbieter-Runtime-Klassen als auch Grundtypen wie Zahlen und Zeichenfolgen enthält. Der Compiler können Sie mit einem "*muss WinRT Typ*" Fehler, wenn Sie diese Einschränkung vergessen haben.

Wenn Sie keine Parameter oder Argumente mit dem Ereignis übergeben möchten, können Sie Ihre eigene einfachen Typ der Windows-Runtime-Delegaten definieren. Das folgende Beispiel zeigt eine einfachere Version der Common Language Runtime **BankAccount** -Klasse. Deklariert einen Delegattyp mit dem Namen **SignalDelegate** , und klicken Sie dann verwendet, die ein Signal-Typ-Ereignis anstelle eines Ereignisses mit einem Parameter aus.

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

## <a name="parameterized-delegates-simple-signals-and-callbacks-within-a-project"></a>Parametrisierte Stellvertretungen, einfache Anmelde- und Rückrufe innerhalb eines Projekts

Wenn das Ereignis nur intern verwendet wird in Ihrem C + / WinRT project (nicht über Binärdateien), und klicken Sie dann weiterhin die [**winrt::event**](/uwp/cpp-ref-for-winrt/event) Struct-Vorlage verwendet werden, aber Sie mit C + parametrisieren / WinRTs Windows-Runtime [**winrt::delegate&lt;... T&gt; **](/uwp/cpp-ref-for-winrt/delegate) Struct-Vorlage, die eine effiziente und Verweis gezählt Delegat ist. Eine beliebige Anzahl Parameter unterstützt und sind nicht auf Windows-Runtime Typen beschränkt.

Das folgende Beispiel zeigt eine Stellvertretung zuerst, Signatur, die keine Parameter (im Wesentlichen eine einfache Signal) und dann ein, die eine Zeichenfolge akzeptiert.

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

Beachten Sie, wie Sie das Ereignis hinzufügen können beliebig viele abonnierende Stellvertretungen wie gewünscht. Es ist jedoch Mehraufwand ein Ereignis zugeordnet. Wenn Sie benötigen lediglich einen einfachen Rückruf mit nur einem einzigen abonnierenden Delegaten, können Sie [**winrt::delegate&lt;... T&gt; **](/uwp/cpp-ref-for-winrt/delegate) eigenständig.

```cppwinrt
winrt::delegate<> signalCallback;
signalCallback = [] { std::wcout << L"Hello, World!" << std::endl; };
signalCallback();

winrt::delegate<std::wstring> logCallback;
logCallback = [](std::wstring const& message) { std::wcout << message.c_str() << std::endl; }f;
logCallback(L"Hello, World!");
```

Wenn Sie von C + Portieren sind / CX Codebasis, in dem Ereignisse und Delegaten intern innerhalb eines Projekts verwendet werden, und klicken Sie dann **winrt::delegate** helfen Ihnen beim Replizieren dieses Muster in C + / WinRT.

## <a name="design-guidelines"></a>Entwurfsrichtlinien

Es wird empfohlen, dass Sie Ereignisse und Stellvertretungen nicht angezeigt, als Funktionsparameter übergeben. Die **add** -Funktion [**winrt::event**](/uwp/cpp-ref-for-winrt/event) ist die einzige Ausnahme, da Sie eine Stellvertretung müssen in diesem Fall übergeben. Der Grund für diese Richtlinie ist, da Delegaten in verschiedenen Sprachen von Windows-Runtime (im Hinblick auf gibt an, ob sie eine Client-Registrierung oder mehreren unterstützen) verschiedene Formen annehmen können. Ereignisse, mit deren Modell mit mehreren Abonnenten bilden eine sehr viel vorhersehbare und konsistente aus.

Die Signatur für einen Ereignishandler-Delegaten sollten bestehen aus zwei Parameter: *Absender* (**IInspectable**) und *Args* (einige Argument Ereignistyp, beispielsweise [**"RoutedEventArgs"**](/uwp/api/windows.ui.xaml.routedeventargs)).

Beachten Sie, dass diese Richtlinien nicht unbedingt angewendet werden, wenn Sie eine interne API entwerfen. Obwohl interne APIs Laufe der Zeit häufig öffentliche werden.

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von APIs mit C++/WinRT](author-apis.md)
* [Verwenden von APIs mit C++/WinRT](consume-apis.md)
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
