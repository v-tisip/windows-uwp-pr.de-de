---
author: stevewhims
description: Dieses Thema zeigt, wie man selbst implementierte oder von Windows oder von Drittanbietern implementierte C++/WinRT-APIs verwendet.
title: Verwenden von APIs mit C++/WinRT
ms.author: stwhi
ms.date: 04/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projiziert, projektion, implementierung, laufzeitklasse, aktivierung
ms.localizationpriority: medium
ms.openlocfilehash: e777aca8f1d9f3892f67b10c785c056b14c8070c
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832244"
---
# <a name="consume-apis-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Verwenden von APIs mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)
> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Dieses Thema zeigt, wie man selbst implementierte oder von Windows oder von Drittanbietern implementierte C++/WinRT-APIs verwendet.

## <a name="if-the-api-is-in-a-windows-namespace"></a>Wenn sich die API in einem Windows-Namespace befindet
Dies ist der häufigste Fall, bei dem Sie eine Windows-Runtime-API verwenden. Dies ist ein einfaches Codebeispiel.

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    winrt::init_apartment();
    Uri contosoUri{ L"http://www.contoso.com" };
}
```

Der enthaltene Header `winrt/Windows.Foundation.h` ist Teil des SDKs, und befindet sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`. Die Header in diesem Ordner enthalten Windows-APIs, die in C++/WinRT projiziert werden. Wenn Sie einen Typ aus einem Windows-Namespace verwenden möchten, fügen Sie den C++/WinRT-Projektions-Header ein, der diesem Namespace entspricht. Die `using namespace`-Direktiven sind optional, aber praktisch.

In diesem Beispiel enthält `winrt/Windows.Foundation.h` den projizierten Typ für die Laufzeitklasse [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri).

> [!TIP]
> Ein *projizierter Typ* ist ein Wrapper für eine Laufzeitklasse, um deren APIs zu nutzen. Eine *projizierte Schnittstelle* ist ein Wrapper für eine Windows-Runtime-Schnittstelle.

Im obigen Codebeispiel wird nach der Initialisierung von C++/WinRT der projizierte Typ **Uri** über einen seiner öffentlich dokumentierten Konstruktoren (in diesem Beispiel [**Uri(String)**](/uwp/api/windows.foundation.uri#Windows_Foundation_Uri__ctor_System_String_)) konstruiert. Für diesen häufigsten Anwendungsfall müssen Sie nichts weiter tun.

## <a name="if-the-api-is-implemented-in-a-windows-runtime-component"></a>Wenn die API in einer Komponente für Windows-Runtime implementiert ist
Dieser Abschnitt gilt unabhängig davon, ob Sie die Komponente selbst erstellt haben oder ob sie von einem Anbieter stammt.

> [!NOTE]
> Informationen über die aktuelle Verfügbarkeit der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

Verweisen Sie in Ihrem Anwendungsprojekt auf die Windows-Runtime-Metadaten-Datei (`.winmd`) der Komponente für Windows-Runtime und erstellen Sie diese. Während des Builds erzeugt das `cppwinrt.exe`-Tool eine Standard-C++ Bibliothek, die die API-Oberfläche der Komponente vollständig beschreibt (bzw. *projiziert*). Mit anderen Worten, die generierte Bibliothek enthält die projizierten Typen für die Komponente.

Dann fügen Sie wie bei einem Windows-Namespace-Typ einen Header ein und konstruieren den projizierten Typ über einen seiner Konstruktoren. Der Startcode Ihres Anwendungsprojekts registriert die Laufzeitklasse, und der Konstruktor des projizierten Typs ruft [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) auf, um die Laufzeitklasse der referenzierten Komponente zu aktivieren.

```cppwinrt
#include <winrt/BankAccountWRC.h>

struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount bankAccount;
    ...
};
```

Weitere Details, Code und eine exemplarische Vorgehensweise bei der Verwendung von APIs, die in einer Komponente für Windows-Runtime implementiert sind, finden Sie unter [Erstellen von Ereignissen in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).

## <a name="if-the-api-is-implemented-in-the-consuming-project"></a>Wenn die API im verwendenden Projekt implementiert ist
Ein Typ, der vom XAML-UI verwendet wird, muss eine Laufzeitklasse sein (auch, wenn er sich im selben Projekt wie das XAML-UI befindet).

Für dieses Szenario generieren Sie einen projizierten Typ aus den Windows-Runtime-Metadaten der Laufzeitklasse (`.winmd`). Auch hier fügen Sie einen Header ein. Aber diesmal konstruieren Sie den projizierten Typ über seinen `nullptr`-Konstruktor. Dieser Konstruktor führt keine Initialisierung durch. Daher müssen Sie der Instanz über die [**winrt::make**](/uwp/cpp-ref-for-winrt/make)-Helper-Funktion einen Wert zuweisen und alle notwendigen Konstruktorargumente übergeben. Eine Laufzeitklasse, die im selben Projekt wie der verwendende Code implementiert ist, muss weder registriert noch über die Windows-Runtime/COM-Aktivierung instanziiert werden.

```cppwinrt
// MainPage.h
...
struct MainPage : MainPageT<MainPage>
{
    ...
    private:
        Bookstore::BookstoreViewModel m_mainViewModel{ nullptr };
        ...
    };
}
...
// MainPage.cpp
...
#include "BookstoreViewModel.h"

MainPage::MainPage()
{
    m_mainViewModel = make<Bookstore::implementation::BookstoreViewModel>();
    ...
}
```

Weitere Details, Code und eine exemplarische Vorgehensweise für die Nutzung einer im verwendenden Projekt implementierten Laufzeitklasse finden Sie unter [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).

## <a name="instantiating-and-returning-projected-types-and-interfaces"></a>Instanziierung und Rückgabe von projizierten Typen und Schnittstellen
Hier ist ein Beispiel dafür, wie projizierte Typen und Schnittstellen in Ihrem Projekt aussehen könnten.

```cppwinrt
struct MyRuntimeClass : MyProject::IMyRuntimeClass, impl::require<MyRuntimeClass,
    Windows::Foundation::IStringable, Windows::Foundation::IClosable>
```

**MyRuntimeClass** ist ein projizierter Typ. Projizierte Schnittstellen sind **IMyRuntimeClass**, **IStringable** und **IClosable**. Dieses Thema hat die verschiedenen Möglichkeiten gezeigt, über die Sie einen projizierten Typ instanziieren können. Hier ist eine Zusammenfassung, die **MyRuntimeClass** als Beispiel verwendet.

```cppwinrt
// The runtime class is implemented in another compilation unit (it's either a Windows API,
// or it's implemented in a second- or third-party component).
MyProject::MyRuntimeClass myrc1;

// The runtime class is implemented in the same compilation unit.
MyProject::MyRuntimeClass myrc2{ nullptr };
myrc2 = winrt::make<MyProject::implementation::MyRuntimeClass>();
```

- Sie können auf die Mitglieder aller Schnittstellen eines projizierten Typs zugreifen.
- Sie können einen projizierten Typ an einen Aufrufer zurückgeben.
- Projizierte Typen und Schnittstellen sind von [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown) abgeleitet. Sie können [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) für einen projizierten Typ oder eine Interface aufrufen, um nach anderen projizierten Schnittstellen zu suchen, die Sie ebenfalls verwenden oder an einen Aufrufer zurückgeben können. Die **as**Mitgliedsfunktion arbeitet wie [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).

```cppwinrt
void f(MyProject::MyRuntimeClass const& myrc)
{
    myrc.ToString();
    myrc.Close();
    IClosable iclosable = myrc.as<IClosable>();
    iclosable.Close();
}
```

## <a name="important-apis"></a>Wichtige APIs
* [winrt::make Funktionsvorlage](/uwp/cpp-ref-for-winrt/make)
* [winrt::Windows::Foundation::IUnknown::as](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function)

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von Ereignissen mit C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component)
* [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage)
