---
author: stevewhims
description: Damit Sie C++/WinRT schneller verwenden können, werden Ihnen in diesem Thema einige einfache Codebeispiele vorgestellt.
title: Erste Schritte mit C++/WinRT
ms.author: stwhi
ms.date: 10/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, erste schritte
ms.localizationpriority: medium
ms.openlocfilehash: b8f8425fa602c844803cc632f523949b8b04d551
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5403100"
---
# <a name="get-started-with-cwinrt"></a>Erste Schritte mit C++/WinRT

Um Sie bei der Verwendung von Beschleunigung erhalten [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), in diesem Thema führt Sie durch ein einfaches Codebeispiel basierend auf einem neuen **Windows Console Application (C++ / WinRT)** Projekt. Dieses Thema zeigt auch, wie Sie [Hinzufügen C++ / WinRT-Unterstützung zu einem Windows-Desktop-Anwendung-Projekt](#modify-a-windows-desktop-application-project-to-add-cwinrt-support).

> [!IMPORTANT]
> Wenn Sie Visual Studio 2017 verwenden (Version 15.8.0 oder höher), und für das Windows SDK Version 10.0.17134.0 (Windows 10, Version 1803), klicken Sie dann eine neu erstellte C++ / WinRT-Projekt wird möglicherweise mit dem Fehler kompilieren "*Fehler C3861: 'From_abi': Bezeichner nicht gefunden*", und mit anderen Fehlern mit Ursprung in *base.h*. Die Lösung besteht darin, entweder Ziel höher (Weitere konform) Version des Windows SDK oder der Set-Projekteigenschaft **C/C++-** > **Sprache** > **Konformitätsmodus: Nein** (auch, wenn **/ PERMISSIVE--** erscheint in Projekteigenschaft ** C/C++** > **Sprache** > **Befehlszeile** unter **Zusätzliche Optionen**, löschen Sie ihn).

## <a name="a-cwinrt-quick-start"></a>Schnelleinstieg zu C++/WinRT

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

Erstellen Sie ein neues **Windows Console Application (C++/WinRT)**-Projekt.

Bearbeiten Sie `pch.h` und `main.cpp` folgendermaßen.

```cppwinrt
// pch.h
...
#include <iostream>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
...
```

```cppwinrt
// main.cpp
#include "pch.h"

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

int main()
{
    winrt::init_apartment();

    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
    for (const SyndicationItem syndicationItem : syndicationFeed.Items())
    {
        winrt::hstring titleAsHstring = syndicationItem.Title().Text();
        std::wcout << titleAsHstring.c_str() << std::endl;
    }
}
```

Wir nehmen uns das kurze Codebeispiel oben Stück für Stück vor und erläutern, was in jedem Teil passiert.

```cppwinrt
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
```

Die enthaltenen Header sind Teil des SDKs und befinden sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt`. Visual Studio bezieht diesen Pfad in sein *IncludePath*-Makro ein. Die Header enthalten Windows-APIs, die in C++/WinRT projiziert werden. Anders ausgedrückt: Für jeden einzelnen Windows-Typ definiert C++/WinRT ein C++-freundliches Äquivalent (wird als *projizierter Typ* bezeichnet). Ein projizierter Typ verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace. Wenn Sie diese in Ihrem vorkompilierten Header platzieren, werden die inkrementellen Buildzeiten reduziert.

> [!IMPORTANT]
> Wann immer Sie einen Typ aus einem Windows-Namespace verwenden möchten, schließen Sie die entsprechende C++/WinRT-Windows-Namespace-Headerdatei wie gezeigt ein. Der *zugehörige* Header ist derjenige mit dem gleichen Namen wie der Namespace des Typs. Um z.B. die C++/WinRT-Projektion für die Laufzeitklasse [**Windows::Foundation::Collections::PropertySet**](/uwp/api/windows.foundation.collections.propertyset) zu verwenden, fügen Sie Folgendes ein: `#include <winrt/Windows.Foundation.Collections.h>`.

```cppwinrt
using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;
```

Die `using namespace`-Direktiven sind optional, aber praktisch. Das oben gezeigte Muster für diese Richtlinien (was die Suche nach unqualifizierten Namen für alles im**Winrt**-Namespace ermöglicht) eignet sich, wenn Sie ein neues Projekt beginnen und C++/WinRT die einzige Sprachprojektion ist, die Sie innerhalb dieses Projekts verwenden. Wenn Sie andererseits C++/WinRT-Code mit [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) und/oder SDK-ABI-Code (Application Binary Interface) kombinieren (Sie davon entweder portieren oder interagieren, eines oder beide dieser Modelle), dann lesen Sie die Themen [Interoperabilität zwischen C++/WinRT und C++/CX](interop-winrt-cx.md), [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md) und [Interoperabilität zwischen C++/WinRT und der ABI](interop-winrt-abi.md).

```cppwinrt
winrt::init_apartment();
```

Der Aufruf von **winrt::init_apartment** initialisiert COM; standardmäßig in einem Multithread-Apartment.

```cppwinrt
Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
SyndicationClient syndicationClient;
```

Weisen Sie zwei Objekte mit Stapelzuordnung zu: Sie stellen den URI des Windows-Blogs dar, und einen Syndication-Client. Wir erstellen den URI mit einem einfachen Wide-String-Literal (unter [String-Verarbeitung in C++/WinRT](strings.md) finden Sie weitere Möglichkeiten zum Arbeiten mit Zeichenfolgen).

```cppwinrt
SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
```

[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) ist ein Beispiel für eine asynchrone Windows-Runtime-Funktion. Das Codebeispiel erhält von **RetrieveFeedAsync** ein Objekt für einen asynchronen Vorgang. Es ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren und auf das Ergebnis zu warten (in diesem Fall einen Syndication-Feed). Weitere Informationen über Parallelität und Non-Blocking-Techniken finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).

```cppwinrt
for (const SyndicationItem syndicationItem : syndicationFeed.Items()) { ... }
```

[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) ist ein Bereich, der durch die Iteratoren definiert wird, die von den **begin**- und **end**-Funktionen (oder deren constant-, reverse- und constant-reverse-Varianten) zurückgegeben werden. Aus diesem Grund können Sie **Items** entweder mit einer bereichsbasierten `for`-Anweisung oder mit der Template-Funktion **std::for_each** auflisten.

```cppwinrt
winrt::hstring titleAsHstring = syndicationItem.Title().Text();
std::wcout << titleAsHstring.c_str() << std::endl;
```

Der Code erhält dann den Titeltext des Feeds als [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring)-Objekt (siehe [String-Verarbeitung in C++/WinRT](strings.md)). **hstring** ist dann die Ausgabe, über die **c_str**-Funktion, die das Muster wiedergibt, das mit C++-Standardbibliothekzeichenfolgen verwendet wird.

Wie Sie sehen können, unterstützt C++/WinRT moderne, klassenähnliche C++ Ausdrücke wie `syndicationItem.Title().Text()`. Dies ist ein anderer und saubererer Programmierstil als die traditionelle COM-Programmierung. Sie müssen COM nicht direkt initialisieren, arbeiten Sie mit COM-Zeigern.

Sie müssen auch keine HRESULT-Rückgabecodes verarbeiten. Für einen natürlichen und modernen Programmierstil konvertiert C++/WinRT Fehler-HRESULTs in Ausnahmen, wie z.B. [**winrt::hresult-error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error). Weitere Informationen zur Fehlerbehandlung sowie Codebeispiele finden Sie unter [Fehlerbehandlung bei C++/WinRT](error-handling.md).

## <a name="modify-a-windows-desktop-application-project-to-add-cwinrt-support"></a>Ändern Sie ein Projekt Windows-Desktop-Anwendung zum Hinzufügen von C++ / WinRT-Unterstützung

In diesem Abschnitt wird gezeigt, wie Sie C++ hinzufügen können / WinRT-Unterstützung für ein Projekt der Windows-Desktop-Anwendung, die Sie möglicherweise. Wenn Sie ein vorhandenes Projekt der Windows-Desktop-Anwendung besitzen, können Sie zusammen mit diesen Schritten durch Erstellen von ersten folgen. Angenommen, öffnen Sie Visual Studio und erstellen Sie eine **Visual C++** \> **Windows-Desktop** \> Projekt**Windows-Desktop-Anwendung** .

### <a name="set-project-properties"></a>Set-Projekteigenschaften

Navigieren Sie zum Projekt-Eigenschaft, die **Allgemeine** \> **Windows SDK-Version**, und wählen Sie **Alle Konfigurationen** und **Alle Plattformen**. Stellen Sie sicher, dass **Windows SDK-Version** 10.0.17134.0 (Windows 10, Version 1803) festgelegt ist oder größer.

Stellen Sie sicher, dass Sie nicht betroffen sind [Warum nicht Mein neue Projekt kompiliert?](/windows/uwp/cpp-and-winrt-apis/faq).

Da C++ / WinRT Features aus dem C ++ 17-Standard verwendet, legen Sie die Projekteigenschaft **C/C++-** > **Sprache** > **C++ Sprache Standard** in *ISO C ++ 17 Standard (/ Std: c ++ 17)*.

### <a name="the-precompiled-header"></a>Die vorkompilierte Headerdatei

Benennen Sie Ihre `stdafx.h` und `stdafx.cpp` auf `pch.h` und `pch.cpp`bzw.. Setzen Sie die Projekteigenschaft **C/C++-** > **Vorkompilierte Header** > **Vorkompilierte Headerdatei** *pch.h*.

Suchen und Ersetzen Sie den gesamten `#include "stdafx.h"` mit `#include "pch.h"`.

In `pch.h`, gehören `winrt/base.h`.

```cppwinrt
// pch.h
...
#include <winrt/base.h>
```

## <a name="linking"></a>Verknüpfen

C++ / WinRT-sprachprojektion hängt von bestimmten Windows-Runtime-freien (nicht-Mitglieds)-Funktionen und Einstiegspunkten ab, erfordern, die Verknüpfung mit der überbibliothek ["windowsapp.lib"](/uwp/win32-and-com/win32-apis) . Dieser Abschnitt beschreibt die drei Arten von der Linker erfüllen.

Die erste Option ist Ihr Visual Studio hinzu-Projekt alle C++ / WinRT MSBuild-Eigenschaften und-Ziele. Bearbeiten Sie Ihre `.vcxproj` Datei, suchen Sie `<PropertyGroup Label="Globals">` aus, und legen Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.

Alternativ können Sie projektlinkeinstellungen verwenden, um eine explizite Verknüpfung `WindowsApp.lib`.

Alternativ können Sie dies im Quellcode erledigen (in `pch.h`, z. B.) wie folgt aus.

```cppwinrt
#pragma comment(lib, "windowsapp")
```

Können Sie jetzt kompilieren und verknüpfen, und fügen C++ / WinRT-Code zu Ihrem Projekt (z. B. der Code in die [ein c++ / WinRT-Schnellstart-](#a-cwinrt-quick-start) Abschnitt oben beschrieben)

## <a name="important-apis"></a>Wichtige APIs
* [Syndicationclient:: Retrievefeedasync-Methode](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [SyndicationFeed.Items-Eigenschaft](/uwp/api/windows.web.syndication.syndicationfeed.items)
* [winrt::hstring struct](/uwp/cpp-ref-for-winrt/hstring)
* [WinRT:: HRESULT-Error-Struktur](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)

## <a name="related-topics"></a>Verwandte Themen
* [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)
* [Fehlerbehandlung bei C++/WinRT](error-handling.md)
* [Interoperabilität zwischen C++/WinRT und C++/CX](interop-winrt-cx.md)
* [Interoperabilität zwischen C++/WinRT und der ABI](interop-winrt-abi.md)
* [Wechsel zu C++/WinRT von C++/CX](move-to-winrt-from-cx.md)
* [String-Verarbeitung in C++/WinRT](strings.md)
