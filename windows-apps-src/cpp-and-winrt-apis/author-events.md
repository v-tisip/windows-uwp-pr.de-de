---
author: stevewhims
description: Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse enthält, die Ereignisse auslöst. Es zeigt außerdem eine App, die die Komponente nutzt und die Ereignisse verarbeitet.
title: Erstellen von Ereignissen mit C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, erstellen, ereignis
ms.localizationpriority: medium
ms.openlocfilehash: 192000f937989d7218931ce1465bd96d5d9b71c6
ms.sourcegitcommit: 834992ec14a8a34320c96e2e9b887a2be5477a53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2018
ms.locfileid: "1880881"
---
# <a name="author-events-in-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Erstellen von Ereignissen mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)
Dieses Thema zeigt, wie man eine Komponente für Windows-Runtime erstellt, die eine Laufzeitklasse für ein Bankkonto enthält, die ein Ereignis auslöst, wenn sein Saldo ins Minus gerät. Es demonstriert außerdem eine Core App, die die Bankkonto-Laufzeitklasse nutzt, eine Funktion zur Anpassung des Saldos aufruft und alle daraus resultierenden Ereignisse verarbeitet.

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

> [!IMPORTANT]
> Wichtige Konzepte und Begriffe, die Ihr Verständnis für die Verwendung von Laufzeitklassen mit C++/WinRT unterstützen, finden Sie unter [Verwenden von APIs mit C++/WinRT](consume-apis.md) und [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="windowsfoundationeventhandlerlttgt-and-typedeventhandlerlttgt"></a>Windows::Foundation::EventHandler&lt;T&gt; und TypedEventHandler&lt;T&gt;
Wenn Sie ein Ereignis aus einer in einer Komponente für Windows-Runtime implementierten Laufzeitklasse auslösen möchten, sollten Sie [**Windows::Foundation::EventHandler**](/uwp/api/windows.foundation.eventhandler) oder [**TypedEventHandler**](/uwp/api/windows.foundation.eventhandler) für den Delegattyp Ihres Ereignisses verwenden. Die Typparameter müssen Windows-Runtime-Typen sein. Daher sind primitive Typen und Laufzeitklassen von Drittanbietern zulässig.

Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie diese Einschränkung vergessen.

## <a name="winrtdelegatelt-tgt"></a>winrt::delegate&lt;...T&gt;
Wenn Sie ein Ereignis über einen C++-Typ auslösen wollen (im selben Projekt erstellt und genutzt), können Sie [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) von C++/WinRT für den Delegattyp Ihres Ereignisses nutzen. In diesem Fall müssen die Typ-Parameter des Delegats keine Windows-Runtime-Typen sein. Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen **winrt::delegate** beim Replizieren dieses Musters in C++/WinRT.

## <a name="create-a-windows-runtime-component-bankaccountwrc"></a>Erstellen einer Komponente für Windows-Runtime (BankAccountWRC)
Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio. Erstellen Sie ein **Visual C++ Windows-Runtime Component (C++/WinRT)** Projekt und nennen Sie es *BankAccountWRC* (für „Bankkonto-Komponente für Windows-Runtime”).

Das neu erstellte Projekt enthält eine Datei mit dem Namen `Class.idl`. Benennen Sie diese Datei in `BankAccountWRC.idl` um, so dass beim Erstellen die Windows-Runtime-Metadaten-Datei Ihrer Komponente für die Komponente selbst benannt wird. Definieren Sie in `BankAccountWRC.idl` Ihre Schnittstelle entsprechend dem folgenden Code.

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

Speichern Sie die Datei, und erstellen Sie das Projekt. Die Erstellung funktioniert noch nicht. Aber während des Buildprozesses wird das `midl.exe`-Tool ausgeführt, um die Windows-Runtime-Metadaten-Datei Ihrer Komponente zu erstellen (`\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd`). Dann wird das `cppwinrt.exe`-Tool ausgeführt (mit der Option `-component`), um Quelltextdateien zu erzeugen, die Sie bei der Erstellung Ihrer Komponente unterstützen. Diese Dateien enthalten Stubs, um mit der Implementierung der `BankAccount`-Laufzeitklasse zu beginnen, die Sie in Ihrer IDL deklariert haben. Diese Stubs sind `\BankAccountWRC\BankAccountWRC\Generated Files\sources\BankAccount.h` und `BankAccount.cpp`.

Kopieren Sie die Stub-Dateien `BankAccount.h` und `BankAccount.cpp` von `\BankAccountWRC\BankAccountWRC\Generated Files\sources\` in den Projektordner `\BankAccountWRC\BankAccountWRC\`. Stellen Sie im **Projektmappen-Explorer** sicher, dass **Alle Dateien anzeigen** aktiviert ist. Klicken Sie mit der rechten Maustaste auf die kopierten Stub-Dateien und klicken Sie auf **In Projekt aufnehmen**. Klicken Sie außerdem mit der rechten Maustaste auf `Class.h` und `Class.cpp`, und klicken Sie auf **Aus Projekt ausschließen**.

Nun öffnen wir `BankAccount.h` und `BankAccount.cpp` und implementieren unsere Laufzeitklasse. Fügen Sie in `BankAccount.h` zwei private Mitglieder zur Implementierung von BankAccount hinzu (*nicht* zur Factory-Implementierung).

```cppwinrt
// BankAccount.h
...
namespace winrt::BankAccountWRC::implementation
{
    struct BankAccount : BankAccountT<BankAccount>
    {
        ...

    private:
        winrt::event<Windows::Foundation::EventHandler<float>> accountIsInDebitEvent;
        float balance{ 0.f };
    };
}
...
```

Implementieren Sie in `BankAccount.cpp` die Funktionen wie im folgenden Codebeispiel gezeigt. In C++/WinRT wird ein IDL-deklariertes Ereignis als ein Set überladener Funktionen implementiert (ähnlich wie eine Eigenschaft als ein Paar von überladenen Get- und Set-Funktionen implementiert wird). Eine Überladung übernimmt einen zu registrierenden Delegaten und gibt einen Token zurück. Die andere übernimmt einen Token und widerruft die Registrierung des zugeordneten Delegats.

```cppwinrt
// BankAccount.cpp
...
namespace winrt::BankAccountWRC::implementation
{
    event_token BankAccount::AccountIsInDebit(Windows::Foundation::EventHandler<float> const& handler)
    {
        return accountIsInDebitEvent.add(handler);
    }

    void BankAccount::AccountIsInDebit(event_token const& token)
    {
        accountIsInDebitEvent.remove(token);
    }

    void BankAccount::AdjustBalance(float value)
    {
        balance += value;
        if (balance < 0.f) accountIsInDebitEvent(*this, balance);
    }
}
```

Sie müssen nicht die Überladung für den Ereignis-Revoker implementieren (weitere Informationen siehe [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate))– dies übernimmt die C++/WinRT-Projektion für Sie. Die anderen Überladungen sind nicht in die Projektion integriert, um Ihnen die Flexibilität zu geben, sie für Ihr Szenario optimal zu implementieren. Ein derartiger Aufruf von [**event::add**](/uwp/cpp-ref-for-winrt/event#eventadd-function) und [**event::remove**](/uwp/cpp-ref-for-winrt/event#eventremove-function) ist eine effiziente und parallele/threadsichere Standardmethode. Wenn Sie jedoch über eine große Anzahl von Ereignissen verfügen, möchten Sie möglicherweise nicht für jedes ein Ereignisfeld, sondern vielmehr eine Implementierung mit geringer Dichte.

Sie sehen oben, dass die Implementierung der Funktion **AdjustBalance** das Ereignis **AccountIsInDebit** auslöst, wenn der Saldo negativ wird.

Wenn Sie irgendwelche Warnungen an der Erstellung hindern, dann setzen Sie die Projekteigenschaft** C/C++** > **Allgemein** > **Warnungen als Fehler behandeln** auf **Nein (/WX-)**, und erstellen Sie das Projekt neu.

## <a name="create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component"></a>Erstellen einer Core App (BankAccountCoreApp) zum Testen der Komponente für Windows-Runtime
Erstellen Sie nun ein neues Projekt (entweder in Ihrer `BankAccountWRC`-Lösung oder in einer neuen). Erstellen Sie ein **Visual C++ Core App (C++/WinRT)**-Projekt, und nennen Sie es *BankAccountCoreApp*.

Fügen Sie einen Verweis hinzu, und navigieren Sie zu `\BankAccountWRC\Debug\BankAccountWRC\BankAccountWRC.winmd` (oder fügen Sie einen Projektverweis hinzu, wenn sich die beiden Projekte in der gleichen Projektmappe befinden). Klicken Sie auf **Hinzufügen** und dann auf **OK**. Erstellen Sie jetzt BankAccountCoreApp. Wenn ein Fehler anzeigt, dass die Payload-Datei `readme.txt` nicht existiert, dann schließen Sie diese Datei aus dem „Komponente für Windows-Runtime“-Projekt aus, erstellen Sie sie neu, und erstellen Sie dann BankAccountCoreApp neu.

Während des Buildprozesses wird das `cppwinrt.exe`-Tool ausgeführt, um die referenzierte `.winmd`-Datei in Quellcodedateien zu verarbeiten, die projizierte Typen enthalten, um Sie bei der Verwendung Ihrer Komponente zu unterstützen. Der Header für die projizierten Typen für die Laufzeitklassen Ihrer Komponente (mit dem Namen `BankAccountWRC.h`) wird im Ordner `\BankAccountCoreApp\BankAccountCoreApp\Generated Files\winrt\` generiert.

Fügen Sie diesen Header in `App.cpp` ein.

```cppwinrt
#include <winrt/BankAccountWRC.h>
```

Fügen Sie in `App.cpp` ebenfalls den folgenden Code ein, um ein BankAccount zu instanziieren (unter Verwendung des Standardkonstruktors des projizierten Typs), registrieren Sie einen Ereignis-Handler und sorgen Sie dann dafür, dass das Konto ins Minus geht.

```cppwinrt
struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount bankAccount;
    event_token eventToken;
    ...
    
    void Initialize(CoreApplicationView const &)
    {
        eventToken = bankAccount.AccountIsInDebit([](const auto &, float balance)
        {
            assert(balance < 0.f);
        });
    }
    ...

    void Uninitialize()
    {
        bankAccount.AccountIsInDebit(eventToken);
    }
    ...

    void OnPointerPressed(IInspectable const &, PointerEventArgs const & args)
    {
        bankAccount.AdjustBalance(-1.f);
        ...
    }
    ...
};
```

Jedes Mal, wenn Sie auf das Fenster klicken, ziehen Sie 1 vom Kontostand ab. Um zu demonstrieren, dass das Ereignis wie erwartet ausgelöst wird, setzen Sie einen Haltepunkt in den Lambda-Ausdruck, starten Sie die App und klicken Sie in das Fenster.

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von APIs mit C++/WinRT](author-apis.md)
* [Verwenden von APIs mit C++/WinRT](consume-apis.md)
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
