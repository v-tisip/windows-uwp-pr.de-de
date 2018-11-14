---
author: stevewhims
description: Eine Einführung in C++/WinRT – einer Standard C++ Sprachprojektion für Windows-Runtime-APIs.
title: Einführung in C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
keywords: Windows 10, UWP, Standard, C++, CPP, WinRT, Projizierung, Einführung
ms.localizationpriority: medium
ms.openlocfilehash: 8b88eac972cd65b771827d7e3125476265cf671e
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6208560"
---
# <a name="introduction-to-cwinrt"></a>Einführung in C++/WinRT
&nbsp;
> [!VIDEO https://www.youtube.com/embed/nOFNc2uTmGs]

C++/WinRT ist eine vollständig standardisierte, moderne C++17-Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet. Mit C++/WinRT können Sie Windows-Runtime-APIs mit jedem standardkonformen C++17-Compiler erstellen und verwenden. Das in Version 10.0.17134.0 (Windows 10, Version 1803) eingeführte Windows SDK enthält C++/WinRT.

C++ / WinRT ist von Microsoft empfohlene Ersatz für die [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx?branch=live) sprachprojektion und der [Windows-Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl?branch=live). Die vollständige Liste der [Themen zu C++ / WinRT](index.md#topics-about-cwinrt) enthält Informationen zu Interoperabilität mit sowohl Portieren von, C++ / CX und WRL.

> [!IMPORTANT]
> Zwei der wichtigsten zu beachtenden Teile von C++/WinRT sind in den Abschnitten [SDK-Unterstützung für C++/WinRT](#sdk-support-for-cwinrt) und [Visual Studio-Unterstützung für C++/WinRT und VSIX](#visual-studio-support-for-cwinrt-and-the-vsix) beschrieben.

## <a name="language-projections"></a>Sprachprojektionen
Die Windows-Runtime basiert auf COM-APIs (Component Object Model) und ist für den Zugriff über *Sprachprojektionen* konzipiert. Eine Projektion verbirgt die COM-Details und bietet eine natürlichere Programmiererfahrung für eine bestimmte Sprache.

### <a name="the-cwinrt-language-projection-in-the-windows-uwp-api-reference-content"></a>Die C++/WinRT-Sprachprojektion in der Windows UWP-API-Referenz
Wenn Sie [Windows UWP-APIs](https://docs.microsoft.com/uwp/api/) anzeigen, klicken Sie auf das Kombinationsfeld **Sprache** oben rechts und wählen Sie **C++/WinRT** aus, um API-Syntaxblöcke so anzuzeigen, wie sie in der C++/WinRT-Sprachprojektion erscheinen.

## <a name="sdk-support-for-cwinrt"></a>SDK-Unterstützung für C++/WinRT
Ab Version 10.0.17134.0 (Windows10, Version 1803) enthält das Windows SDK eine headerbasierte Standard-C++-Bibliothek für die Verwendung von Erstanbieter-Windows-APIs (Windows-Runtime-APIs in Windows-Namespaces). C++/WinRT enthält außerdem das `cppwinrt.exe`-Tool, mit dem Sie auf eine Windows-Runtime-Metadatendatei (`.winmd`) verweisen können, um eine headerbasierte C++-Standardbibliothek zu erstellen, die die in den Metadaten beschriebenen APIs zur Verwendung über den C++/WinRT-Code *projiziert*. Windows-Runtime-Metadaten-Dateien (`.winmd`) bieten eine kanonische Möglichkeit, eine Windows-Runtime-API-Oberfläche zu beschreiben. Durch Verweisen von `cppwinrt.exe` auf Metadaten können Sie eine Bibliothek zur Verwendung mit einer beliebigen, in einer Zweit- oder Drittanbieter-Komponente für Windows-Runtime oder in Ihrer eigenen Anwendung implementierten Runtime-Klasse generieren. Weitere Informationen finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).

Mit C++/WinRT können Sie auch eigene Runtime-Klassen mithilfe von C++-Standardcode implementieren, ohne auf eine Programmierung im COM-Format zurückgreifen zu müssen. Für eine Runtime-Klasse beschreiben Sie einfach Ihre Typen in einer IDL-Datei, `midl.exe` und `cppwinrt.exe` generieren die Quellcodedateien mit den Implementierungstextbausteinen für Sie. Alternativ können Sie einfach Schnittstellen durch eine Ableitung von einer C++/WinRT-Basisklasse implementieren. Weitere Informationen finden Sie unter [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="visual-studio-support-for-cwinrt-and-the-vsix"></a>Visual Studio-Unterstützung für C++/WinRT und VSIX
Für C++/WinRT-Projektvorlagen in Visual Studio, sowie C++/WinRT MSBuild-Eigenschaften und -Ziele. Laden Sie die [C++/WinRT Visual Studio-Erweiterung (VSIX)](https://aka.ms/cppwinrt/vsix) im [Visual Studio Marketplace](https://marketplace.visualstudio.com/) herunter und installieren Sie sie.

> [!NOTE]
> Mit Version 1.0.181002.2 (oder höher) des VSIX installiert haben, erstellen eine neue C++ / WinRT-Projekt installiert automatisch das [Microsoft.Windows.CppWinRT NuGet-Paket](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/) für das Projekt. Das Microsoft.Windows.CppWinRT NuGet-Paket bietet verbesserte C++ / WinRT-Projekt Build-Unterstützung, erstellen Ihr Projekt tragbaren zwischen einem Entwicklungscomputer und einen Build-Agent (auf dem die NuGet-Paket und nicht VSIX, installiert ist).
>
> Für ein vorhandenes Projekt&mdash;nach der Installation von Version 1.0.181002.2 (oder höher) des VSIX&mdash;es wird empfohlen, dass Sie das Projekt in Visual Studio öffnen, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder einfügen **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen, und dann auf **Installieren** , um das Paket für das Projekt zu installieren.

Sie benötigen Visual Studio 2017 (Sie müssen mindestens Version 15.6, aber wir empfehlen mindestens 15.7), und Windows SDK-Version 10.0.17134.0 (Windows 10, Version 1803). Wenn Sie es bereits installiert haben, müssen Sie die Option **C++ universelle Windows-Plattform-Tools** von innerhalb der Visual Studio-Installationsprogramm installieren. Und in Windows- **Einstellungen** > **Update \ & Security** > **für Entwickler**, wählen Sie die Option **Querladen von apps** , anstatt die Option **Entwicklermodus** .

Sie sehen dann möglicherweise erstellen und zu erstellen oder zu öffnen, eine C++ / WinRT Projekts in Visual Studio, und es bereitzustellen. Alternativ können Sie ein vorhandenes Projekt konvertieren, durch Hinzufügen der `<CppWinRTEnabled>true</CppWinRTEnabled>` -Eigenschaft verwenden, um seine `.vcxproj` Datei.

```xml
<Project ...>
    <PropertyGroup Label="Globals">
        <CppWinRTEnabled>true</CppWinRTEnabled>
...
```

Sobald Sie diese Eigenschaft hinzugefügt haben, steht Ihnen die C++/WinRT MSBuild-Unterstützung für das Projekt zur Verfügung, einschließlich des Aufrufs des `cppwinrt.exe`-Tools.

Da C++ / WinRT Features aus dem C ++ 17-Standard verwendet, benötigt Eigenschaft **C/C++-** Projekt > **Sprache** > **C++ Sprache Standard** > **ISO C ++ 17 Standard (/ Std: c ++ 17)**. Sie können außerdem **Konformitätsmodus: Ja (/permissive-)** festlegen, was Ihren Code für die Standardkonformität weiter einschränkt.

Eine weitere zu beachtende Projekteigenschaft ist **C/C++** > **Allgemein** > **Warnungen als Fehler behandeln**. Legen Sie diese auf **Ja (/WX)** oder **Nein (/WX-)** fest. Manchmal generieren vom `cppwinrt.exe`-Tool erzeugte Quelldateien Warnungen, bis Sie Ihre Implementierung hinzufügen.

Mit VSIX erhalten Sie außerdem eine systemeigene Visual Studio-Visualisierung (natvis) von projizierten C++/WinRT-Typen, die eine Erfahrung wie beim C#-Debuggen bereitstellt. Natvis ist für Debugbuilds automatisch. Sie können es für Releasebuilds verwenden, indem Sie das Symbol WINRT_NATVIS definieren.

Hier sind die Visual Studio-Projektvorlagen, die von VSIX bereitgestellt werden.

### <a name="windows-console-application-cwinrt"></a>Windows Console Application (C++/WinRT)
Eine Projektvorlage für eine C++/WinRT-Client-Anwendung für Windows Desktop, mit einer Konsolen-Benutzeroberfläche.

### <a name="blank-app-cwinrt"></a>Blank App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die über eine XAML-Benutzeroberfläche verfügt.

Visual Studio bietet XAML-Compiler-Unterstützung, um Implementierungs- und Header-Stubs aus der IDL-Datei (`.idl`) (Interface Definition Language) zu generieren, die sich hinter jeder XAML-Markup-Datei befindet. Definieren Sie in einer IDL-Datei alle lokalen Laufzeitklassen, auf die Sie in den XAML-Seiten Ihrer Anwendung verweisen möchten, und erstellen Sie das Projekt einmal, um Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um Ihre lokalen Laufzeitklassen zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

### <a name="core-app-cwinrt"></a>Core App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die keine XAML-Benutzeroberfläche verwendet.

Stattdessen wird der C++/WinRT-Windows-Namespace-Header für den Windows.ApplicationModel.Core-Namespace verwendet. Nach dem Erstellen und Ausführen klicken Sie auf ein leeres Feld, um ein farbiges Quadrat hinzuzufügen; klicken Sie dann auf ein farbiges Quadrat, um es zu ziehen.

### <a name="windows-runtime-component-cwinrt"></a>Komponente für Windows-Runtime (C++/WinRT)
Eine Projektvorlage für eine Komponente; typischerweise für die Nutzung in einer UWP-App (Universelle Windows-Plattform).

Dieses Template demonstriert die `midl.exe` > `cppwinrt.exe`-Toolchain, in der Windows-Runtime-Metadaten (`.winmd`) aus IDL generiert werden, und dann die Implementierung und Header-Stubs aus den Windows-Runtime-Metadaten generiert werden.

Definieren Sie in einer IDL-Datei die Laufzeitklassen in Ihrer Komponenten, deren Standardschnittstelle und alle anderen Schnittstellen, die sie implementieren. Erstellen Sie das Projekt einmalig, um `module.g.cpp`, `module.h.cpp`, Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um die Laufzeitklassen in Ihrer Komponente zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

Packen Sie die erstellte Binärdatei für die Komponente für Windows-Runtime und deren `.winmd` mit der UWP-App, die diese nutzt.

## <a name="custom-types-in-the-cwinrt-projection"></a>Benutzerdefinierte Typen in der C++/WinRT-Projektion
In Ihrer C++ / WinRT-Programmierung können Sie Standard-c++-Sprachfunktionen und [Standard C++ Datentypen und C++ / WinRT](std-cpp-data-types.md)&mdash;sowie einige Standard-c++-Datentypen. Sie werden aber auch einige benutzerdefinierte Datentypen in der Projektion bemerken und können diese verwenden. Beispielsweise verwenden wir [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) im Schnellstart-Codebeispiel in [Erste Schritte mit C++/WinRT](get-started.md).

[**winrt::com_array**](/uwp/cpp-ref-for-winrt/com-array) ist ein weiterer Typ, den Sie wahrscheinlich irgendwann verwenden werden. Es ist jedoch weniger wahrscheinlich, dass Sie direkt einen Typ wie [**winrt::array_view**](/uwp/cpp-ref-for-winrt/array-view) verwenden. Möglicherweise werden Sie die Typen auch nicht verwenden, sodass Sie keinen Code ändern müssen wenn ein entsprechender Typ in der C++ Standardbibliothek verfügbar ist.

> [!WARNING]
> Es gibt außerdem Typen, die Sie bei genauerer Betrachtung des C++/WinRT-Windows-Namespace-Headers entdecken. Ein Beispiel ist **winrt::param::hstring**, es stehen jedoch auch Beispiele für die Sammlung zur Verfügung. Diese dienen ausschließlich der Optimierung der Bindung von Eingabeparametern, erzielen hohe Leistungsverbesserungen und sorgen dafür, dass die meisten aufrufenden Muster für verwandte C++-Standardtypen und -container „einfach funktionieren“. Diese Typen werden von der Projektion immer nur in Fällen verwendet, in denen sie den größten Wert hinzufügen. Sie sind umfassend optimiert und nicht für die allgemeine Verwendung vorgesehen. Geben Sie nicht der Versuchung nach, sie selbst zu nutzen. Sie sollten auch nichts aus dem `winrt::impl` -Namespace verwenden, da es sich dabei um Implementierungstypen handelt, die Änderungen unterliegen. Sie sollten weiterhin Standardtypen oder Typen aus dem [WinRT-Namespace](/uwp/cpp-ref-for-winrt/winrt) verwenden.

## <a name="important-apis"></a>Wichtige APIs
* [winrt::hstring struct](/uwp/cpp-ref-for-winrt/hstring)
* [winrt-Namespace](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a>Verwandte Themen
* [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)
* [C++/WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix)
* [Erste Schritte mit C++/WinRT](get-started.md)
* [C++-Standarddatentypen und C++/WinRT](std-cpp-data-types.md)
* [Zeichenkettenverarbeitung in C++/WinRT](strings.md)
* [Windows UWP-APIs](https://docs.microsoft.com/uwp/api/)
