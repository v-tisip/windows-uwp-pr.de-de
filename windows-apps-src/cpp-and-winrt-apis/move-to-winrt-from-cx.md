---
description: In diesem Thema wird gezeigt, wie Sie C++/CX-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von C++/CX
ms.date: 01/17/2019
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: fe988bffbf024308fb5d43da7ed538e5330b58de
ms.sourcegitcommit: ff131135248c85a8a2542fc55437099d549cfaa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9117640"
---
# <a name="move-to-cwinrt-from-ccx"></a>C++/CX zu C++/WinRT wechseln

Dieses Thema zeigt, wie Sie den Code im Anschluss eine [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) Projekt zum entsprechenden Äquivalent in [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="porting-strategies"></a>Portieren von Strategien

Wenn Sie Ihre C++ nach und nach portieren möchten / CX-Code in C++ / WinRT, können Sie. C++ / CX- und C++ / WinRT-Code kann im selben Projekt, mit Ausnahme der XAML-Compiler-Unterstützung und der Windows-Runtime-Komponenten vorhanden sein. Für diese zwei Ausnahmen, müssen Sie in der Zielgruppe entweder C++ / CX oder C++ / WinRT im selben Projekt.

> [!IMPORTANT]
> Wenn Ihr Projekt eine XAML-Anwendung erstellt wird, dann einen Workflow, die wir empfehlen wird zuerst ein neues Projekt in Visual Studio mithilfe eines C++ erstellen / WinRT-Projektvorlagen (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)). Starten Sie anschließend das Kopieren Source Code und Markup über von C++ / CX-Projekt. Sie können neue XAML-Seiten mit **Projekt**hinzufügen \> **Neues Element hinzufügen**  \>  **Visual C++** > **leere Seite (C++ / WinRT)**.
>
> Alternativ können Sie eine Komponente für Windows-Runtime-Faktor-Code aus dem XAML-C++ / CX projizieren, wie Sie es portieren. Entweder bewegen Sie so viele C++ / CX-code können Sie in einer Komponente, und klicken Sie dann das XAML-Projekt in C++ / WinRT. Oder lassen Sie andernfalls das XAML-Projekt als C++ / CX, erstellen Sie eine neue C++ / WinRT-Komponente, und beginnen Sie Portieren von C++ / CX-Code aus dem XAML-Projekt und in der Komponente. Sie haben können auch eine C++ / CX-Komponentenprojekt zusammen mit C++ / WinRT-Komponentenprojekt in der gleichen Projektmappe, verweisen auf beide aus Ihrem Anwendungsprojekt und nach und nach auf einem anderen port. Finden Sie unter [Interoperabilität zwischen C++ / WinRT und C++ / CX](interop-winrt-cx.md) für Weitere Informationen zur Verwendung die beiden sprachprojektionen im selben Projekt.

> [!NOTE]
> Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx) als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**. Ein Windows-Typ, der in C++/WinRT projiziert wird, verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace. Diese unterschiedlichen Namespaces ermöglichen die Portierung von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.

Angesichts der oben genannten Ausnahmen, das erste Schritt beim Portieren eine C++ / CX-Projekts zu C++ / WinRT ist C++ manuell hinzufügen / WinRT-Unterstützung es (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)). Installieren Sie dazu das [Microsoft.Windows.CppWinRT NuGet-Paket](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/) in Ihr Projekt ein. Öffnen des Projekts in Visual Studio, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder fügen Sie **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen übergehen, und dann auf **Installieren** , um das Paket für das Projekt zu installieren. Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird. Es ist sinnvoll, lassen Sie Unterstützung deaktiviert, so dass Build Nachrichten Sie suchen (und Port) unterstützen alle Ihre Abhängigkeiten von C++ / CX, oder Sie können Unterstützung wieder aktivieren (in den Projekteigenschaften, **C/C++-** \> **Allgemeine** \> **verbrauchen Windows-Runtime Erweiterung** \> **Ja (/ Zw)**), und nach und nach portieren.

Stellen Sie sicher, **Allgemeine**Projekteigenschaft \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) festgelegt ist oder größer.

Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.

```cppwinrt
#include <winrt/base.h>
```

Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie so nicht explizit `winrt/base.h` einschließen, da dies automatisch erfolgt.

Wenn Ihr Projekt zudem Typen der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) verwendet, lesen Sie bitte [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md).

## <a name="parameter-passing"></a>Parameterübergabe
Beim Schreiben von C++/CX-Quellcode übergeben Sie C++/CX-Typen als Funktionsparameter wie Hütchenverweise (\^).

```cppcx
void LogPresenceRecord(PresenceRecord^ record);
```

In C++/WinRT sollten Sie für synchrone Funktionen standardmäßig `const&`-Parameter verwenden. Dadurch werden Kopien und unnötiger Zusatzaufwand vermieden. Ihre Coroutinen sollten aber Pass-by-Value verwenden, um sicherzustellen, dass sie nach Wert erfassen, und um Probleme mit der Lebensdauer zu vermeiden (weitere Informationen finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)).

```cppwinrt
void LogPresenceRecord(PresenceRecord const& record);
IASyncAction LogPresenceRecordAsync(PresenceRecord const record);
```

Ein C++/WinRT-Objekt ist im Grunde genommen ein Wert, der einen Schnittstellenzeiger zum zugrunde liegenden Windows-Runtime-Objekt enthält. Beim Kopieren eines C++/WinRT-Objekts kopiert der Compiler den gekapselten Schnittstellenzeiger, wodurch sich sein Verweiszähler erhöht. Eine Zerstörung der Kopie beinhaltet, dass der Verweiszähler verringert wird. Daher wird Aufwand einer Kopie nur bei Bedarf verursacht.

## <a name="variable-and-field-references"></a>Variablen und Feldverweise
Beim Schreiben von C++/CX-Quellcode verwenden Sie Hütchenvariablen (\^) zum Verweisen auf Windows-Runtime-Objekte sowie den Pfeiloperator (-&gt;), um den Verweis einer Hütchenvariable aufzuheben.

```cppcx
IVectorView<User^>^ userList = User::Users;

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList->Size; ++iUser)
    ...
```

Beim Portieren in den entsprechenden C++ / WinRT-Code können Sie enorm abrufen, indem die hütchen entfernt, und ändern den Pfeiloperator (-&gt;) in den Punktoperator (.). C++ / WinRT-projizierte Typen Werte und keine Zeiger sind.

```cppwinrt
IVectorView<User> userList = User::Users();

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList.Size(); ++iUser)
    ...
```

Der Standardkonstruktor für eine C++ / CX Hat Zeiger auf null initialisiert. Nachfolgend finden Sie eine C++ / CX-Codebeispiel in der erstellen wir eine Variable oder ein Feld den richtigen Typ, sondern eines, das nicht initialisiert wurde. Anders ausgedrückt, bezieht es zunächst einen **TextBlock**sich nicht auf; Wir beabsichtigen, einen Verweis später zuweisen.

```cppcx
TextBlock^ textBlock;

class MyClass
{
    TextBlock^ textBlock;
};
```

Für das Äquivalent in C++ / WinRT, siehe [verzögerte Initialisierung](consume-apis.md#delayed-initialization).

## <a name="properties"></a>Eigenschaften
Die C++/CX-Spracherweiterungen beinhalten das Konzept von Eigenschaften. Beim Schreiben von C++/CX-Quellcode können Sie auf eine Eigenschaft zugreifen, als wäre sie ein Feld. Der C++-Standardcode verfügt nicht über das Konzept einer Eigenschaft, folglich rufen Sie in C++/WinRT Get- und Set-Funktionen auf.

In den folgenden Beispielen sind **XboxUserId**, **UserState**, **PresenceDeviceRecords** und **Größe** alles Eigenschaften.

### <a name="retrieving-a-value-from-a-property"></a>Abrufen eines Werts aus einer Eigenschaft
So erhalten Sie einen Eigenschaftswert in C++/CX.

```cppcx
void Sample::LogPresenceRecord(PresenceRecord^ record)
{
    auto id = record->XboxUserId;
    auto state = record->UserState;
    auto size = record->PresenceDeviceRecords->Size;
}
```

Der entsprechende C++/WinRT-Quellcode ruft eine Funktion mit dem gleichen Namen wie die Eigenschaft auf, jedoch ohne Parameter.

```cppwinrt
void Sample::LogPresenceRecord(PresenceRecord const& record)
{
    auto id = record.XboxUserId();
    auto state = record.UserState();
    auto size = record.PresenceDeviceRecords().Size();
}
```

Beachten Sie, dass die Funktion **PresenceDeviceRecords** ein Windows-Runtime-Objekt zurückgibt, das über eine **Size**-Funktion verfügt. Da es sich beim zurückgegebenen Objekt ebenfalls um einen C++/WinRT-projizierten Typ handelt, dereferenzieren wir, indem wir den Punktoperator zum Aufrufen von **Size** verwenden.

### <a name="setting-a-property-to-a-new-value"></a>Festlegen einer Eigenschaft auf einen neuen Wert
Beim Festlegen einer Eigenschaft auf einen neuen Wert wird ein ähnliches Muster angewandt. Zuerst in C++/CX.

```cppcx
record->UserState = newValue;
```

Um das Äquivalent in C++/WinRT zu tun, rufen Sie eine Funktion mit dem gleichen Namen wie die Eigenschaft auf und übergeben ein Argument.

```cppwinrt
record.UserState(newValue);
```

## <a name="creating-an-instance-of-a-class"></a>Erstellen einer Instanz einer Klasse
Sie arbeiten mit einem C++/ CX-Objekt über einen Handle dafür (Hütchenverweis (\^)). Sie erstellen ein neues Objekt über das Schlüsselwort `ref new`, das wiederum [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) aufruft, um eine neue Instanz der Laufzeitklasse zu aktivieren.

```cppcx
using namespace Windows::Storage::Streams;

class Sample
{
private:
    Buffer^ m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
};
```

Ein C++/WinRT-Objekt ist ein Wert. Folglich können Sie es auf dem Stapel oder als ein Feld eines Objekts zuweisen. *Niemals* können Sie `ref new` (oder `new`) verwenden, um ein C++/WinRT-Objekt zuzuordnen. Im Hintergrund wird dennoch **RoActivateInstance** aufgerufen.

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
private:
    Buffer m_gamerPicBuffer{ MAX_IMAGE_SIZE };
};
```

Wenn eine Ressource aufwendig zu initialisieren ist, ist es üblich, deren Initialisierung zu verzögern, bis sie tatsächlich benötigt wird.

```cppcx
using namespace Windows::Storage::Streams;

class Sample
{
public:
    void DelayedInit()
    {
        // Allocate the actual buffer.
        m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
    }

private:
    Buffer^ m_gamerPicBuffer;
};
```

Der gleiche Code wird zu C++/WinRT portiert. Beachten Sie die Verwendung des Konstruktors `nullptr`. Weitere Informationen zu diesem Konstruktor finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
    void DelayedInit()
    {
        // Allocate the actual buffer.
        m_gamerPicBuffer = Buffer(MAX_IMAGE_SIZE);
    }

private:
    Buffer m_gamerPicBuffer{ nullptr };
};
```

## <a name="converting-from-a-base-runtime-class-to-a-derived-one"></a>Konvertieren von einer Basisklasse Laufzeitklasse in einen abgeleiteten
Es ist üblich, eine Referenz-zu-Base verfügen, die Sie wissen, dass auf ein Objekt eines abgeleiteten Typs verweist. In C++ / CX verwenden Sie `dynamic_cast` auf eine *Umwandlung* der Referenz-Basis in eine Referenz--abgeleitet. Die `dynamic_cast` ist wirklich nur ein ausgeblendeter Aufruf von [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521). Hier ist ein typisches Beispiel&mdash;Sie ein Abhängigkeit geänderter Eigenschaft-Ereignis behandelt, und Sie **DependencyObject** zurück in den tatsächlichen Typ umgewandelt werden, die die Abhängigkeitseigenschaft besitzt möchten.

```cppcx
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject^ d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs^ e)
{
    BgLabelControl^ theControl{ dynamic_cast<BgLabelControl^>(d) };

    if (theControl != nullptr)
    {
        // succeeded ...
    }
}
```

Die entsprechende C++ / WinRT-Code ersetzt die `dynamic_cast` mit einem Aufruf an die [**IUnknown:: Try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) Funktion, die **QueryInterface**kapselt. Sie haben auch die Möglichkeit, rufen Sie stattdessen [**IUnknown:: As**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), die eine Ausnahme auslöst, wenn für die erforderliche Schnittstelle (die Standardschnittstelle des Typs, die Sie anfordern) Abfragen nicht zurückgegeben wird. Nachfolgend finden Sie eine C++ / WinRT-Codebeispiel.

```cppwinrt
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject const& d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const& e)
{
    if (BgLabelControlApp::BgLabelControl theControl{ d.try_as<BgLabelControlApp::BgLabelControl>() })
    {
        // succeeded ...
    }

    try
    {
        BgLabelControlApp::BgLabelControl theControl{ d.as<BgLabelControlApp::BgLabelControl>() };
        // succeeded ...
    }
    catch (winrt::hresult_no_interface const&)
    {
        // failed ...
    }
}
```

## <a name="event-handling-with-a-delegate"></a>Ereignisbehandlung mit einem Delegaten
Hier ist ein typisches Beispiel für die Behandlung eines Ereignisses in C++/CX unter Verwendung einer Lambda-Funktion als Delegaten.

```cppcx
auto token = myButton->Click += ref new RoutedEventHandler([=](Platform::Object^ sender, RoutedEventArgs^ args)
{
    // Handle the event.
    // Note: locals are captured by value, not reference, since this handler is delayed.
});
```

Dies ist das Äquivalent in C++/WinRT.

```cppwinrt
auto token = myButton().Click([=](IInspectable const& sender, RoutedEventArgs const& args)
{
    // Handle the event.
    // Note: locals are captured by value, not reference, since this handler is delayed.
});
```

Anstelle einer Lambda-Funktion können Sie den Delegaten als eine freie Funktion oder als Pointer-to-Member-Funktion implementieren. Weitere Informationen finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md).

Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) beim Replizieren dieses Musters in C++/WinRT. Siehe auch [parametrisiert Delegaten, einfachen Signale und Rückrufe innerhalb eines Projekts](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).

## <a name="revoking-a-delegate"></a>Widerrufen eines Delegaten
In C++/CX verwenden Sie den `-=`-Operator, um eine frühere Ereignisregistrierung zu widerrufen.

```cppcx
myButton->Click -= token;
```

Dies ist das Äquivalent in C++/WinRT.

```cppwinrt
myButton().Click(token);
```

Weitere Informationen und Optionen finden Sie unter [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).

## <a name="mapping-ccx-platform-types-to-cwinrt-types"></a>Zuordnen von C++/CX-**Platform**-Typen zu C++/WinRT-Typen
C++/CX bietet verschiedene Datentypen im **Platform**-Namespace. Diese Typen gehören nicht zum C++-Standard, daher können Sie sie nur verwenden, wenn Sie die Windows-Runtime-Spracherweiterungen aktivieren (Visual Studio-Projekteigenschaft **C/C++** > **Allgemein** > **Windows-Runtime-Erweiterung verwenden** > **Ja (/ZW)**). In der Tabelle unten finden Sie Informationen zum Portieren von **Platform**-Typen in ihre Entsprechungen in C++/WinRT. Nachdem Sie dies erledigt haben, können Sie, da C++/WinRT zum C++-Standard gehört, die Option `/ZW` deaktivieren.

| C++/CX | C++/WinRT |
| ---- | ---- |
| **Platform:: Agile\ ^** | [**WinRT:: agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref) |
| **Platform:: Array\ ^** | Finden Sie unter [Port **Platform:: Array\ ^** ](#port-platformarray) |
| **Platform::Exception\^** | [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) |
| **Platform::InvalidArgumentException\^** | [**winrt::hresult_invalid_argument**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) |
| **Platform::Object\^** | **winrt::Windows::Foundation::IInspectable** |
| **Platform::String\^** | [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) |

### <a name="port-platformagile-to-winrtagileref"></a>Port **Platform:: Agile\ ^** zu **WinRT:: agile_ref**
Die **Platform:: Agile\ ^** Typ in C++ / CX steht für eine Windows-Runtime-Klasse, die von jedem Thread aus zugegriffen werden kann. C++ / WinRT-äquivalent ist [**WinRT:: agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).

In C++/CX.

```cppcx
Platform::Agile<Windows::UI::Core::CoreWindow> m_window;
```

In C++/WinRT.

```cppwinrt
winrt::agile_ref<Windows::UI::Core::CoreWindow> m_window;
```

### <a name="port-platformarray"></a>Port **Platform:: Array\ ^**
Ihre Optionen umfassen mit einer Initialisierungsliste, eine **Std:: Array**oder eine **Std:: Vector**. Weitere Informationen und Codebeispiele finden Sie unter [aufgeführt, welche standardmäßigen Initialisierung](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-initializer-lists) und [Standard-Arrays und-Vektoren](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-arrays-and-vectors).

### <a name="port-platformexception-to-winrthresulterror"></a>Portieren von **Platform::Exception\^** nach **winrt::hresult_error**
Der Typ **Platform::Exception\^** wird in C++/CX erzeugt, wenn eine Windows-Runtime-API ein Nicht-S\_OK HRESULT zurückgibt. Für C++/WinRT ist die Entsprechung [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).

Zum Portieren nach C++/WinRT ändern Sie jeglichen Code, der **Platform::Exception\^** verwendet, um stattdessen **winrt::hresult_error** zu nutzen.

In C++/CX.

```cppcx
catch (Platform::Exception^ ex)
```

In C++/WinRT.

```cppwinrt
catch (winrt::hresult_error const& ex)
```

C++/WinRT stellt diese Ausnahmeklassen bereit.

| Ausnahmentyp | Basisklasse | HRESULT |
| ---- | ---- | ---- |
| [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) | | Aufrufen von [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function) |
| [**winrt::hresult_access_denied**](/uwp/cpp-ref-for-winrt/error-handling/hresult-access-denied) | **winrt::hresult_error** | E_ACCESSDENIED |
| [**winrt::hresult_canceled**](/uwp/cpp-ref-for-winrt/error-handling/hresult-canceled) | **winrt::hresult_error** | ERROR_CANCELLED |
| [**winrt::hresult_changed_state**](/uwp/cpp-ref-for-winrt/error-handling/hresult-changed-state) | **winrt::hresult_error** | E_CHANGED_STATE |
| [**winrt::hresult_class_not_available**](/uwp/cpp-ref-for-winrt/error-handling/hresult-class-not-available) | **winrt::hresult_error** | CLASS_E_CLASSNOTAVAILABLE |
| [**winrt::hresult_illegal_delegate_assignment**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-delegate-assignment) | **winrt::hresult_error** | E_ILLEGAL_DELEGATE_ASSIGNMENT |
| [**winrt::hresult_illegal_method_call**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-method-call) | **winrt::hresult_error** | E_ILLEGAL_METHOD_CALL |
| [**winrt::hresult_illegal_state_change**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-state-change) | **winrt::hresult_error** | E_ILLEGAL_STATE_CHANGE |
| [**winrt::hresult_invalid_argument**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) | **winrt::hresult_error** | E_INVALIDARG |
| [**winrt::hresult_no_interface**](/uwp/cpp-ref-for-winrt/error-handling/hresult-no-interface) | **winrt::hresult_error** | E_NOINTERFACE |
| [**winrt::hresult_not_implemented**](/uwp/cpp-ref-for-winrt/error-handling/hresult-not-implemented) | **winrt::hresult_error** | E_NOTIMPL |
| [**winrt::hresult_out_of_bounds**](/uwp/cpp-ref-for-winrt/error-handling/hresult-out-of-bounds) | **winrt::hresult_error** | E_BOUNDS |
| [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/error-handling/hresult-wrong-thread) | **winrt::hresult_error** | RPC_E_WRONG_THREAD |

Beachten Sie, dass jede Klasse (über die **hresult_error** -Basisklasse) eine [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)-Funktion bereitstellt, die das HRESULT für den Fehler zurückgibt, sowie eine [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function)-Funktion, die die Darstellung der Zeichenfolge dieses HRESULT zurückgibt.

Hier ist ein Beispiel für das Auslösen einer Ausnahme in C++/CX.

```cppcx
throw ref new Platform::InvalidArgumentException(L"A valid User is required");
```

Und das Äquivalent in C++/WinRT.

```cppwinrt
throw winrt::hresult_invalid_argument{ L"A valid User is required" };
```

### <a name="port-platformobject-to-winrtwindowsfoundationiinspectable"></a>Portieren von **Platform::Object\^** nach **winrt::Windows::Foundation::IInspectable**
Wie alle C++/WinRT-Typen ist **winrt::Windows::Foundation::IInspectable** ein Werttyp. Hier erfahren Sie, wie Sie eine Variable dieses Typs auf null initialisieren.

```cppwinrt
winrt::Windows::Foundation::IInspectable var{ nullptr };
```

### <a name="port-platformstring-to-winrthstring"></a>Portieren von **Platform::String\^** nach **winrt::hstring**
**Platform::String\^** ist das Äquivalent zum Windows-Runtime-HSTRING-ABI-Typ. Für C++/WinRT ist die Entsprechung [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring). Mit C++/WinRT können Sie aber Windows-Runtime-APIs mit Standard-C++ Wide-String-Typen wie **std::wstring** aufrufen und/oder Wide-String-Literale. Weitere Informationen und Codebeispiele finden Sie unter [String-Verarbeitung in C++/WinRT](strings.md).

Mit C++/CX können Sie auf die Eigenschaft [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) zugreifen, um die Zeichenfolge als **const wchar_t\***-Array im C-Stil abzurufen (z.B. zur Übergabe an **std::wcout**).

```cppcx
auto var{ titleRecord->TitleName->Data() };
```

Um das Gleiche mit C++ / WinRT zu tun, können Sie die Funktion [**hstring::c_str**](/uwp/api/windows.foundation.uri.-ctor#Windows_Foundation_Uri__ctor_System_String_) verwenden, um eine auf null beendete Zeichenfolgenversion im C-Stil abzurufen (wie von **std::wstring**).

```cppwinrt
auto var{ titleRecord.TitleName().c_str() };
```

Bei der Implementierung von APIs, die Zeichenfolgen übernehmen oder zurückgeben, ändern Sie in der Regel jeglichen C++/CX-Code, der **Platform::String\^** verwendet, um stattdessen **winrt::hstring** zu nutzen.

Hier ist ein Beispiel für eine C++/CX-API, die eine Zeichenfolge übernimmt.

```cppcx
void LogWrapLine(Platform::String^ str);
```

Für C++/WinRT könnten Sie diese API in [MIDL 3.0](/uwp/midl-3) wie folgt deklarieren.

```idl
// LogType.idl
void LogWrapLine(String str);
```

Die C++/WinRT-Toolkette generiert dann Quellcode für Sie, der wie folgt aussieht.

```cppwinrt
void LogWrapLine(winrt::hstring const& str);
```

#### <a name="tostring"></a>ToString()

C++ / CX bietet die [Object::ToString](/cpp/cppcx/platform-object-class?view=vs-2017#tostring) -Methode.

```cppcx
int i{ 2 };
auto s{ i.ToString() }; // s is a Platform::String^ with value L"2".
```

C++ / WinRT nicht direkt zur Verfügung, diese Funktion, aber Sie können zu alternativen aktivieren.

```cppwinrt
int i{ 2 };
auto s{ std::to_wstring(i) }; // s is a std::wstring with value L"2".
```

## <a name="important-apis"></a>Wichtige APIs
* [winrt::delegate-Strukturvorlage](/uwp/cpp-ref-for-winrt/delegate)
* [winrt::hresult_error-Struktur](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)
* [winrt::hstring-Struktur](/uwp/cpp-ref-for-winrt/hstring)
* [winrt-Namespace](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a>Verwandte Themen
* [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)
* [Erstellen von Ereignissen mit C++/WinRT](author-events.md)
* [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)
* [Verwenden von APIs mit C++/WinRT](consume-apis.md)
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
* [Interoperabilität zwischen C++/WinRT und C++/CX](interop-winrt-cx.md)
* [Microsoft Interface Definition Language3.0– Referenz](/uwp/midl-3)
* [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md)
* [String-Verarbeitung in C++/WinRT](strings.md)
