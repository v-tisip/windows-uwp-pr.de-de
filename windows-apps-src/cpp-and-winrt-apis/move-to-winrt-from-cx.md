---
author: stevewhims
description: In diesem Thema wird gezeigt, wie Sie C++/CX-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von C++/CX
ms.author: stwhi
ms.date: 07/20/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: ac7affb044c6b60a249b154cc62379c7517161b0
ms.sourcegitcommit: 1e5590dd10d606a910da6deb67b6a98f33235959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "3228105"
---
# <a name="move-to-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-from-ccx"></a>Wechsel zu [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) von C++/CX
In diesem Thema wird gezeigt, wie Sie [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)-Code zum entsprechenden Äquivalent in C++/WinRT portieren.

> [!IMPORTANT]
> Wenn Sie nach und nach portieren möchten Ihre [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) Code in C++ / WinRT, können Sie. C++ / CX- und C++ / WinRT-Code kann im selben Projekt, mit Ausnahme von XAML-Compiler-Unterstützung und Windows-Runtime-Komponenten vorhanden sein. Für diese Ausnahmen, müssen Sie in der Zielgruppe entweder C++ / CX oder C++ / WinRT im selben Projekt. Aber Sie können einer Komponente für Windows-Runtime-Faktor-Code aus Ihrer XAML-app verwenden, wie Sie es portieren. Entweder bewegen Sie so viel C++ / CX-code können Sie in einer Komponente, und klicken Sie dann das XAML-Projekt in C++ / WinRT. Oder andere lassen die XAML-Projekt als C++ / CX, erstellen Sie eine neue C++ / WinRT-Komponente, und beginnen Sie Portieren von C++ / CX-Code aus dem XAML-Projekt und in der Komponente. Sie haben können auch eine C++ / CX-Komponentenprojekt zusammen mit C++ / WinRT-Komponentenprojekt innerhalb der gleichen Projektmappe verweisen auf beide aus Ihrem Anwendungsprojekt und schrittweise aus einer anderen port.

> [!NOTE]
> Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx) als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**. Ein Windows-Typ, der in C++/WinRT projiziert wird, verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace. Diese unterschiedlichen Namespaces ermöglichen die Portierung von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.

Unter Berücksichtigung der oben genannten Ausnahmen, die erste Schritt beim Portieren eines Projekts zu C++ / WinRT ist C++ manuell hinzufügen / WinRT-Unterstützung (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)). Bearbeiten Sie dazu Ihre `.vcxproj`-Datei, suchen Sie nach `<PropertyGroup Label="Globals">`, und definieren Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`. Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird. Es ist sinnvoll, lassen Sie Unterstützung deaktiviert, so dass Build Nachrichten Sie suchen (und Port) unterstützen alle Ihre Abhängigkeiten von C++ / CX, oder Sie können Unterstützung wieder aktivieren (in den Projekteigenschaften, **C/C++-** \> **Allgemeine** \> **verbrauchen Windows-Runtime Erweiterung** \> **Ja (/ Zw)**), und nach und nach portieren.

Definieren Sie die Projekteigenschaft **Allgemein** \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) oder höher.

Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.

```cppwinrt
#include <winrt/base.h>
```

Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie so nicht explizit `winrt/base.h` einschließen, da dies automatisch erfolgt.

Wenn Ihr Projekt zudem Typen der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) verwendet, lesen Sie bitte [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md).

## <a name="parameter-passing"></a>Parameterübergabe
Beim Schreiben von C++/CX-Quellcode übergeben Sie C++/CX-Typen als Funktionsparameter wie Hütchenverweise (\^).

```cpp
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

```cpp
IVectorView<User^>^ userList = User::Users;

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList->Size; ++iUser)
    ...
```

Beim Portieren in den entsprechenden C++ / WinRT-Code Sie die hütchen entfernt und ändern Sie den Pfeiloperator (-&gt;) in den Punktoperator (.), da C++ / WinRT-projizierte Typen Werte und keine Zeiger sind.

```cppwinrt
IVectorView<User> userList = User::Users();

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList.Size(); ++iUser)
    ...
```

## <a name="properties"></a>Eigenschaften
Die C++/CX-Spracherweiterungen beinhalten das Konzept von Eigenschaften. Beim Schreiben von C++/CX-Quellcode können Sie auf eine Eigenschaft zugreifen, als wäre sie ein Feld. Der C++-Standardcode verfügt nicht über das Konzept einer Eigenschaft, folglich rufen Sie in C++/WinRT Get- und Set-Funktionen auf.

In den folgenden Beispielen sind **XboxUserId**, **UserState**, **PresenceDeviceRecords** und **Größe** alles Eigenschaften.

### <a name="retrieving-a-value-from-a-property"></a>Abrufen eines Werts aus einer Eigenschaft
So erhalten Sie einen Eigenschaftswert in C++/CX.

```cpp
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

```cpp
record->UserState = newValue;
```

Um das Äquivalent in C++/WinRT zu tun, rufen Sie eine Funktion mit dem gleichen Namen wie die Eigenschaft auf und übergeben ein Argument.

```cppwinrt
record.UserState(newValue);
```

## <a name="creating-an-instance-of-a-class"></a>Erstellen einer Instanz einer Klasse
Sie arbeiten mit einem C++/ CX-Objekt über einen Handle dafür (Hütchenverweis (\^)). Sie erstellen ein neues Objekt über das Schlüsselwort `ref new`, das wiederum [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) aufruft, um eine neue Instanz der Laufzeitklasse zu aktivieren.

```cpp
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

```cpp
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

## <a name="converting-from-a-base-runtime-class-to-a-derived-one"></a>Konvertieren von einer Basisklasse Laufzeitklasse in eine abgeleitete
Es ist üblich, eine Verweis auf Basis verfügen, die Sie wissen, dass auf ein Objekt eines abgeleiteten Typs verweist. In C++ / CX verwenden Sie `dynamic_cast` auf eine *Umwandlung* der Referenz-Basis in eine Referenz-zu-abgeleitet. Die `dynamic_cast` ist wirklich nur ein ausgeblendet Aufruf von [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521). Hier ist ein typisches Beispiel&mdash;Sie sind ein Abhängigkeitseigenschaften geänderter Eigenschaftenänderungsereignis behandeln, und Sie möchten, das von **DependencyObject** zurück in den tatsächlichen Typ umgewandelt, die die Abhängigkeitseigenschaft besitzt.

```cpp
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject^ d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs^ e)
{
    BgLabelControl^ theControl{ dynamic_cast<BgLabelControl^>(d) };

    if (theControl != nullptr)
    {
        // succeeded ...
    }
}
```

Die entsprechende C++ / WinRT-Code ersetzt die `dynamic_cast` mit einem Aufruf an die [**IUnknown:: Try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) Funktion, die **QueryInterface**kapselt. Sie haben auch die Möglichkeit, rufen Sie stattdessen [**IUnknown:: As**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), die eine Ausnahme auslöst, wenn für die erforderliche Schnittstelle (die Standardschnittstelle des Typs, die Sie anfordern) Abfragen nicht zurückgegeben wird. Hier sehen Sie eine C++ / WinRT-Codebeispiel.

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

```cpp
auto token = myButton->Click += ref new RoutedEventHandler([&](Platform::Object^ sender, RoutedEventArgs^ args)
{
    // Handle the event.
});
```

Dies ist das Äquivalent in C++/WinRT.

```cppwinrt
auto token = myButton().Click([&](IInspectable const& sender, RoutedEventArgs const& args)
{
    // Handle the event.
});
```

Anstelle einer Lambda-Funktion können Sie den Delegaten als eine freie Funktion oder als Pointer-to-Member-Funktion implementieren. Weitere Informationen finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md).

Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) beim Replizieren dieses Musters in C++/WinRT. Siehe auch [parametrisiert Delegaten, einfache Signale und Rückrufe innerhalb eines Projekts](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).

## <a name="revoking-a-delegate"></a>Widerrufen eines Delegaten
In C++/CX verwenden Sie den `-=`-Operator, um eine frühere Ereignisregistrierung zu widerrufen.

```cpp
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
| **Platform::Exception\^** | [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) |
| **Platform::InvalidArgumentException\^** | [**winrt::hresult_invalid_argument**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) |
| **Platform::Object\^** | **winrt::Windows::Foundation::IInspectable** |
| **Platform::String\^** | [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) |

### <a name="port-platformagile-to-winrtagileref"></a>Port **Platform:: Agile\ ^** zu **WinRT:: agile_ref**
Die **Platform:: Agile\ ^** Typ in C++ / CX steht für eine Windows-Runtime-Klasse, die von jedem Thread aus zugegriffen werden kann. C++ / WinRT-äquivalent ist [**WinRT:: agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).

In C++/CX.

```cpp
Platform::Agile<Windows::UI::Core::CoreWindow> m_window;
```

In C++/WinRT.

```cppwinrt
winrt::agile_ref<Windows::UI::Core::CoreWindow> m_window;
```

### <a name="port-platformexception-to-winrthresulterror"></a>Portieren von **Platform::Exception\^** nach **winrt::hresult_error**
Der Typ **Platform::Exception\^** wird in C++/CX erzeugt, wenn eine Windows-Runtime-API ein Nicht-S\_OK HRESULT zurückgibt. Für C++/WinRT ist die Entsprechung [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).

Zum Portieren nach C++/WinRT ändern Sie jeglichen Code, der **Platform::Exception\^** verwendet, um stattdessen **winrt::hresult_error** zu nutzen.

In C++/CX.

```cpp
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

```cpp
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

```C++
auto var = titleRecord->TitleName->Data();
```

Um das Gleiche mit C++ / WinRT zu tun, können Sie die Funktion [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) verwenden, um eine auf null beendete Zeichenfolgenversion im C-Stil abzurufen (wie von **std::wstring**).

```C++
auto var = titleRecord.TitleName().c_str();
```

Bei der Implementierung von APIs, die Zeichenfolgen übernehmen oder zurückgeben, ändern Sie in der Regel jeglichen C++/CX-Code, der **Platform::String\^** verwendet, um stattdessen **winrt::hstring** zu nutzen.

Hier ist ein Beispiel für eine C++/CX-API, die eine Zeichenfolge übernimmt.

```cpp
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
* [Microsoft Interface Definition Language3.0– Referenz](/uwp/midl-3)
* [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md)
* [String-Verarbeitung in C++/WinRT](strings.md)
