---
author: stevewhims
description: Eine Einführung in C++/WinRT – einer Standard C++ Sprachprojektion für Windows-Runtime-APIs.
title: Einführung in C++/WinRT
ms.author: stwhi
ms.date: 05/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung
ms.localizationpriority: medium
ms.openlocfilehash: 968afd6fdad1e7bf6b3c38d929ab79eefa71819a
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832324"
---
# <a name="introduction-to-cwinrt"></a>Einführung in C++/WinRT
> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Das in Version 10.0.17134.0 (Windows 10, Version 1803) eingeführte Windows SDK enthält nun C++/WinRT.

> [!IMPORTANT]
> Die wichtigsten zu beachtenden Teile von C++/WinRT sind in den Abschnitten [SDK-Unterstützung für C++/WinRT](#sdk-support-for-cwinrt) und [Visual Studio-Unterstützung für C++/WinRT und VSIX](#visual-studio-support-for-cwinrt-and-the-vsix) beschrieben.

C++/WinRT ist eine vollständig standardisierte, moderne C++17 Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die ausschließlich in Header-Dateien implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet. Mit C++/WinRT können Sie Windows-Runtime-APIs mit jedem standardkonformen C++17-Compiler erstellen und verwenden.

## <a name="language-projections"></a>Sprachprojektionen
Die Windows-Runtime basiert auf COM-APIs (Component Object Model) und ist für den Zugriff über *Sprachprojektionen* konzipiert. Eine Projektion verbirgt die COM-Details und bietet eine natürlichere Programmiererfahrung für eine bestimmte Sprache.

### <a name="the-cwinrt-language-projection-in-the-windows-uwp-api-reference-content"></a>Die C++/WinRT-Sprachprojektion in der Windows UWP-API-Referenz
Wenn Sie [Windows UWP-APIs](https://docs.microsoft.com/uwp/api/) anzeigen, klicken Sie auf das Kombinationsfeld **Sprache** oben rechts und wählen Sie **C++/WinRT** aus, um API-Syntaxblöcke so anzuzeigen, wie sie in der C++/WinRT-Sprachprojektion erscheinen.

## <a name="sdk-support-for-cwinrt"></a>SDK-Unterstützung für C++/WinRT
Ab Version 10.0.17134.0 (Windows 10, Version 1803) enthält das Windows SDK die C++/WinRT-Projektion Windows-Namespace-Header und -Tools. Ein wichtiges Werkzeug ist `cppwinrt.exe`, das aus einem `.winmd` Quelltext Dateien erzeugt, die die Metadaten in C++/WinRT projizieren. Windows-Runtime-Metadaten-Dateien (`.winmd`) bieten eine kanonische Möglichkeit, eine Windows-Runtime-API-Oberfläche zu beschreiben. Aus den Windows-Runtime-Metadaten generiert `cppwinrt.exe` eine Standard-C++ Bibliothek, die die API-Oberfläche vollständig beschreibt (bzw. „projiziert”), unabhängig davon, ob es sich um Windows-APIs oder um APIs für Komponente für Windows-Runtime von Drittanbietern handelt. `Cppwinrt.exe` Spielt eine wichtige Rolle in Ihrem Entwicklungs-Workflow sowohl bei der Verwendung von Microsoft-APIs und von APIs von Drittanbietern als auch bei der Erstellung eigener APIs in Komponenten.

## <a name="visual-studio-support-for-cwinrt-and-the-vsix"></a>Visual Studio-Unterstützung für C++/WinRT und VSIX
Für C++/WinRT-Projektvorlagen in Visual Studio, sowie C++/WinRT MSBuild-Eigenschaften und -Ziele. Laden Sie die [C++/WinRT Visual Studio-Erweiterung (VSIX)](https://aka.ms/cppwinrt/vsix) im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) herunter und installieren Sie sie.

Sie benötigen Visual Studio 2017 Version 15.6 oder höher und die Windows SDK-Version 10.0.17134.0 (Windows 10, Version 1803). Sie können dann ein neues Projekt in Visual Studio erstellen, oder Sie können ein vorhandenes Projekt konvertieren, indem Sie die `<CppWinRTProject>true</CppWinRTProject>`-Eigenschaft in Project > PropertyGroup zu seiner `.vcxproj`-Datei hinzufügen. Sobald Sie diese Eigenschaft hinzugefügt haben, steht Ihnen die C++/WinRT MSBuild-Unterstützung für das Projekt zur Verfügung, einschließlich des Aufrufs des `cppwinrt.exe`-Tools.

Da C++/WinRT Features aus dem C++17-Standard verwendet, benötigt es die Projekteigenschaft **C/C++** > **Language** > **ISO C++17 Standard (/std:c++17)**. Sie können außerdem **Konformitätsmodus: Ja (/permissive-)** festlegen, was Ihren Code für die Standardkonformität weiter einschränkt.

Eine weitere zu beachtende Projekteigenschaft ist **C/C++** > **Allgemein** > **Warnungen als Fehler behandeln**. Legen Sie diese auf **Ja (/WX)** oder **Nein (/WX-)** fest. Manchmal generieren vom `cppwinrt.exe`-Tool erzeugte Quelldateien Warnungen bis Sie Ihre Implementierung hinzufügen.

Dies sind die Visual Studio-Projektvorlagen, die von VSIX bereitgestellt werden.

### <a name="windows-console-application-cwinrt"></a>Windows Console Application (C++/WinRT)
Eine Projektvorlage für eine C++/WinRT-Client-Anwendung für Windows Desktop, mit einer Konsolen-Benutzeroberfläche.

### <a name="blank-app-cwinrt"></a>Blank App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die über eine XAML-Benutzeroberfläche verfügt.

Visual Studio bietet XAML-Compiler-Unterstützung, um Implementierungs- und Header-Stubs aus der IDL-Datei (`.idl`) (Interface Definition Language) zu generieren, die sich hinter jeder XAML-Markup-Datei befindet. Definieren Sie in einer IDL-Datei alle lokalen Laufzeitklassen, auf die Sie in den XAML-Seiten Ihrer Anwendung verweisen möchten, und erstellen Sie das Projekt einmal, um Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um Ihre lokalen Laufzeitklassen zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

### <a name="core-app-cwinrt"></a>Core App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die keine XAML-Benutzeroberfläche verwendet.

Stattdessen wird der C++/WinRT-Projektions-Windows-Namespace-Header für den Windows.ApplicationModel.Core-Namespace verwendet. Nach dem Erstellen und Ausführen klicken Sie auf ein leeres Feld, um ein farbiges Quadrat hinzuzufügen; klicken Sie dann auf ein farbiges Quadrat, um es zu ziehen.

### <a name="windows-runtime-component-cwinrt"></a>Komponente für Windows-Runtime (C++/WinRT)
Eine Projektvorlage für eine Komponente; typischerweise für die Nutzung in einer UWP-App (Universelle Windows-Plattform).

Dieses Template demonstriert die `midl.exe` > `cppwinrt.exe`-Toolchain, in der Windows-Runtime-Metadaten (`.winmd`) aus IDL generiert werden, und dann die Implementierung und Header-Stubs aus den Windows-Runtime-Metadaten generiert werden.

Definieren Sie in einer IDL-Datei die Laufzeitklassen in Ihrer Komponenten, deren Standardschnittstelle und alle anderen Schnittstellen, die sie implementieren. Erstellen Sie das Projekt einmalig, um `module.g.cpp`, `module.h.cpp`, Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um die Laufzeitklassen in Ihrer Komponente zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

Packen Sie die erstellte Komponente für Windows-Runtime-Binärdatei und deren `.winmd` mit der UWP-App, die diese nutzt.

## <a name="a-cwinrt-quick-start"></a>Schnelleinstieg zu C++/WinRT
Erstellen Sie ein neues **Windows Console Application (C++/WinRT)**-Projekt. Bearbeiten Sie `main.cpp` folgendermaßen.

```cppwinrt
// main.cpp

#include "pch.h"
#include <iostream>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>

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
        hstring titleAsHstring = syndicationItem.Title().Text();
        std::wcout << titleAsHstring.c_str() << std::endl;
    }
}
```

Die enthaltenen Header `winrt/Windows.Foundation.h` und `winrt/Windows.Web.Syndication.h` befinden sich im SDK, im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`. Visual Studio bezieht diesen Pfad in sein *IncludePath*-Makro ein. Die Header enthalten Windows-APIs, die in C++/WinRT projiziert werden. Wann immer Sie Typen aus den Windows-Namespaces verwenden wollen, fügen Sie die entsprechenden C++/WinRT-Projektions-Windows-Namespace-Header ein. Die `using namespace`-Direktiven sind optional, aber praktisch.

Alle projizierten Typen befinden sich im C++/WinRT-Root-Namespace **winrt**. Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx)als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**. Diese unterschiedlichen Namespaces ermöglichen die Migration von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.

[**SyndicationClient::RetrieveFeedAsync**](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync) ist ein Beispiel für eine asynchrone Windows-Runtime-Funktion. Das Codebeispiel erhält von **RetrieveFeedAsync** ein Objekt für einen asynchronen Vorgang. Es ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren und auf die Ergebnisse zu warten. Weitere Informationen über Parallelität und non-blocking Techniken finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).

[**SyndicationFeed.Items**](/uwp/api/windows.web.syndication.syndicationfeed.items) ist ein Bereich, der durch die Iteratoren definiert wird, die von den **begin**- und **end**-Funktionen (oder deren constant-, reverse- und constant-reverse-Varianten) zurückgegeben werden. Aus diesem Grund können Sie **Items** entweder mit einer bereichsbasierten `for`-Anweisung oder mit der Template-Funktion **std::for_each** auflisten.

Der Code erhält dann den Titeltext des Feeds als [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) Objekt (siehe [String-Verarbeitung in C++/WinRT](strings.md)). Der **hstring** wird dann über **c_str** ausgegeben (was Ihnen vertraut erscheint, wenn Sie Strings aus der C++ Standard Library verwendet haben).

Wie Sie sehen können, unterstützt C++/WinRT moderne, klassenähnliche C++ Ausdrücke wie `syndicationItem.Title().Text()`. Dies ist ein anderer und saubererer Programmierstil als die traditionelle COM-Programmierung. Sie müssen COM nicht explizit initialisieren (**winrt::init_apartment** macht das für Sie), oder mit COM-Zeigern arbeiten oder HRESULT-Rückgabecodes verarbeiten. Für einen natürlichen und modernen Programmierstil konvertiert C++/WinRT Fehler-HRESULTs in Ausnahmen.

## <a name="custom-types-in-the-cwinrt-projection"></a>Benutzerdefinierte Typen in der C++/WinRT-Projektion
Sie können in Ihrer C++/WinRT-Programmierung Standard-C++ Sprachfunktionen und [Standard-C++ Datentypen und C++/WinRT](std-cpp-data-types.md) (einschließlich einiger C++ Standard-Bibliotheksdatentypen) verwenden. Sie werden aber auch einige benutzerdefinierte Datentypen in der Projektion bemerken und können diese verwenden. Zum Beispiel haben wir [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) oben im Schnelleinstieg verwendet.

[**winrt::com_array**](/uwp/cpp-ref-for-winrt/com-array) ist ein weiterer Typ, den Sie wahrscheinlich irgendwann verwenden werden. Es ist jedoch weniger wahrscheinlich, dass Sie direkt einen Typ wie [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) verwenden. Möglicherweise werden Sie die Typen auch nicht verwenden, sodass Sie keinen Code ändern müssen wenn ein entsprechender Typ in der C++ Standardbibliothek verfügbar ist.

Es gibt außerdem Typen, die Sie bei genauerer Betrachtung des C++/WinRT-Projektion Windows-Namespace-Headers entdecken. Ein Beispiel ist **winrt::param::hstring**. Diese gibt es nur aus Effizienzgründen, und Sie sollten sie nicht in Ihrem Code verwenden.

## <a name="important-apis"></a>Wichtige APIs
* [SyndicationClient::RetrieveFeedAsync](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [SyndicationFeed.Items](/uwp/api/windows.web.syndication.syndicationfeed.items)
* [winrt::hstring-Struktur](/uwp/cpp-ref-for-winrt/hstring)
* [winrt-Namespace](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a>Verwandte Themen
* [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)
* [String-Verarbeitung in C++/WinRT](strings.md)
* [Visual Studio Marketplace](https://marketplace.visualstudio.com/)
* [Windows UWP-APIs](https://docs.microsoft.com/uwp/api/)
