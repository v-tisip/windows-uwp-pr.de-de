---
description: Eine Einführung in C++/WinRT – einer Standard C++ Sprachprojektion für Windows-Runtime-APIs.
title: Einführung in C++/WinRT
ms.date: 01/31/2019
ms.topic: article
keywords: Windows 10, UWP, Standard, C++, CPP, WinRT, Projizierung, Einführung
ms.localizationpriority: medium
ms.openlocfilehash: 5281049aa9ddec58a97283a2ca6ba5d229a49c4e
ms.sourcegitcommit: 038fe813c73804285d5e74d97864ac1a2fb531f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "9042604"
---
# <a name="introduction-to-cwinrt"></a>Einführung in C++/WinRT
&nbsp;
> [!VIDEO https://www.youtube.com/embed/nOFNc2uTmGs]

C++/WinRT ist eine vollständig standardisierte, moderne C++17-Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet. Mit C++/WinRT können Sie Windows-Runtime-APIs mit jedem standardkonformen C++17-Compiler erstellen und verwenden. Das in Version 10.0.17134.0 (Windows 10, Version 1803) eingeführte Windows SDK enthält C++/WinRT.

C++ / WinRT ist von Microsoft empfohlene Ersatz für die [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx?branch=live) Programmiersprache und [C++ für Windows-Runtime-Bibliothek (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl?branch=live). Die vollständige Liste der [Themen für C++ / WinRT](index.md#topics-about-cwinrt) enthält Informationen zu Interoperabilität mit sowohl Portieren von C++ / CX und WRL.

> [!IMPORTANT]
> Zwei der wichtigsten Teile von C++ / WinRT zu beachten sind in den Abschnitten beschriebenen [SDK-Unterstützung für C++ / WinRT](#sdk-support-for-cwinrt) und [Visual Studio-Unterstützung für C++ / WinRT, XAML, die VSIX-Erweiterung und das NuGet-Paket](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package).

## <a name="language-projections"></a>Sprachprojektionen
Die Windows-Runtime basiert auf COM-APIs (Component Object Model) und ist für den Zugriff über *Sprachprojektionen* konzipiert. Eine Projektion verbirgt die COM-Details und bietet eine natürlichere Programmiererfahrung für eine bestimmte Sprache.

### <a name="the-cwinrt-language-projection-in-the-windows-uwp-api-reference-content"></a>Die C++/WinRT-Sprachprojektion in der Windows UWP-API-Referenz
Wenn Sie [Windows UWP-APIs](https://docs.microsoft.com/uwp/api/) anzeigen, klicken Sie auf das Kombinationsfeld **Sprache** oben rechts und wählen Sie **C++/WinRT** aus, um API-Syntaxblöcke so anzuzeigen, wie sie in der C++/WinRT-Sprachprojektion erscheinen.

## <a name="sdk-support-for-cwinrt"></a>SDK-Unterstützung für C++/WinRT
Ab Version 10.0.17134.0 (Windows10, Version 1803) enthält das Windows SDK eine headerbasierte Standard-C++-Bibliothek für die Verwendung von Erstanbieter-Windows-APIs (Windows-Runtime-APIs in Windows-Namespaces). C++/WinRT enthält außerdem das `cppwinrt.exe`-Tool, mit dem Sie auf eine Windows-Runtime-Metadatendatei (`.winmd`) verweisen können, um eine headerbasierte C++-Standardbibliothek zu erstellen, die die in den Metadaten beschriebenen APIs zur Verwendung über den C++/WinRT-Code *projiziert*. Windows-Runtime-Metadaten-Dateien (`.winmd`) bieten eine kanonische Möglichkeit, eine Windows-Runtime-API-Oberfläche zu beschreiben. Durch Verweisen von `cppwinrt.exe` auf Metadaten können Sie eine Bibliothek zur Verwendung mit einer beliebigen, in einer Zweit- oder Drittanbieter-Komponente für Windows-Runtime oder in Ihrer eigenen Anwendung implementierten Runtime-Klasse generieren. Weitere Informationen finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).

Mit C++/WinRT können Sie auch eigene Runtime-Klassen mithilfe von C++-Standardcode implementieren, ohne auf eine Programmierung im COM-Format zurückgreifen zu müssen. Für eine Runtime-Klasse beschreiben Sie einfach Ihre Typen in einer IDL-Datei, `midl.exe` und `cppwinrt.exe` generieren die Quellcodedateien mit den Implementierungstextbausteinen für Sie. Alternativ können Sie einfach Schnittstellen durch eine Ableitung von einer C++/WinRT-Basisklasse implementieren. Weitere Informationen finden Sie unter [Erstellen von APIs mit C++/WinRT](author-apis.md).

## <a name="visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package"></a>Visual Studio-Unterstützung für C++ / WinRT, XAML, die VSIX-Erweiterung und das NuGet-Paket
Für Visual Studio-Unterstützung, zusätzlich zu eine minimale Windows SDK-Zielversion von 10.0.17134.0 (Windows 10, Version 1803), benötigen Sie Visual Studio 2017 (mindestens Version 15,6; mindestens 15.7 empfohlen), oder Visual Studio 2019. Wenn Sie es bereits installiert haben, müssen Sie die Option **C++ universelle Windows-Plattform-Tools** in Visual Studio-Installer installieren. Und in Windows- **Einstellungen** > **Aktualisieren \& Sicherheit** > **für Entwickler**, wählen Sie die Option **Querladen von apps** , anstatt die Option **Entwicklermodus** .

Sie müssen zum Herunterladen und installieren die neueste Version von der [C++ / WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix) über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

- Die Erweiterung VSIX erhalten Sie C++ / WinRT Projekt- und Elementvorlagen in Visual Studio, damit Sie mit C++ beginnen können / WinRT-Entwicklung.
- Darüber hinaus es erhalten Sie Visual Studio systemeigene Visualisierung (Natvis) von C++ / WinRT-projizierten Typen. Bereitstellen von eine Erfahrung wie beim c#-Debuggen. Natvis ist für Debugbuilds automatisch. Sie können es für Releasebuilds verwenden, indem Sie das Symbol WINRT_NATVIS definieren.

Die Visual Studio-Projektvorlagen für C++ / WinRT werden nachstehend beschrieben. Beim Erstellen einer neuen C++ / WinRT-Projekt mit der neuesten Version der VSIX-Erweiterung installiert haben, die neue C++ / WinRT-Projekt das [Microsoft.Windows.CppWinRT NuGet-Paket](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/)automatisch installiert. Das **Microsoft.Windows.CppWinRT** NuGet-Paket bietet C++ / WinRT build-Unterstützung (MSBuild-Eigenschaften und Ziele), indem Ihr Projekt tragbaren zwischen einem Entwicklungscomputer und einen Build-Agent (auf dem nur das NuGet-Paket und nicht die VSIX-Erweiterung, installiert ist).

> [!IMPORTANT]
> Wenn Sie Projekte, die verfügen mit erstellt (oder aktualisiert, um die Arbeit mit wurden) eine Version der VSIX-Erweiterung zuvor als 1.0.190128.4, dann finden Sie unter [früheren Versionen der VSIX-Erweiterung](#earlier-versions-of-the-vsix-extension). Dieser Abschnitt enthält wichtige Informationen über die Konfiguration von Ihren Projekten Sie wissen, aktualisieren, um die neueste Version der VSIX-Erweiterung verwenden müssen.

Da C++ / WinRT Features aus dem C ++ 17-Standard verwendet, benötigt Eigenschaft **C/C++-** Projekt > **Sprache** > **C++ Sprache Standard** > **ISO C ++ 17 Standard (/ Std: c ++ 17)**. Sie können außerdem **Konformitätsmodus: Ja (/permissive-)** festlegen, was Ihren Code für die Standardkonformität weiter einschränkt.

Eine weitere zu beachtende Projekteigenschaft ist **C/C++** > **Allgemein** > **Warnungen als Fehler behandeln**. Legen Sie diese auf **Ja (/WX)** oder **Nein (/WX-)** fest. Manchmal generieren vom `cppwinrt.exe`-Tool erzeugte Quelldateien Warnungen, bis Sie Ihre Implementierung hinzufügen.

Mit dem System bis wie oben beschrieben festgelegt, Sie sehen möglicherweise erstellen und zu erstellen oder zu öffnen, eine C++ / WinRT Projekts in Visual Studio, und es bereitzustellen.

Alternativ können Sie ein vorhandenes Projekt konvertieren, indem Sie das **Microsoft.Windows.CppWinRT** NuGet-Paket manuell installieren. Nach dem Installieren (oder zu aktualisieren) die neueste Version der VSIX-Erweiterung, öffnen Sie das vorhandene Projekt in Visual Studio, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder fügen Sie **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen übergehen, und dann auf **Installieren** , um das Paket für das Projekt zu installieren. Nachdem Sie das Paket hinzugefügt haben, erhalten Sie C++ / WinRT MSBuild-Unterstützung für das Projekt, einschließlich des Aufrufs der `cppwinrt.exe` Tool.

Sie können ein Projekt, C++ verwendet, identifizieren / WinRT MSBuild-Unterstützung durch das Vorhandensein des **Microsoft.Windows.CppWinRT** NuGet-Pakets in das Projekt installiert.

Hier sind die Visual Studio-Projektvorlagen, die von der VSIX-Erweiterung bereitgestellten.

### <a name="windows-console-application-cwinrt"></a>Windows Console Application (C++/WinRT)
Eine Projektvorlage für eine C++/WinRT-Client-Anwendung für Windows Desktop, mit einer Konsolen-Benutzeroberfläche.

### <a name="blank-app-cwinrt"></a>Blank App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die über eine XAML-Benutzeroberfläche verfügt.

Visual Studio bietet XAML-Compiler-Unterstützung, um Implementierungs- und Header-Stubs aus der IDL-Datei (`.idl`) (Interface Definition Language) zu generieren, die sich hinter jeder XAML-Markup-Datei befindet. Definieren Sie in einer IDL-Datei alle lokalen Laufzeitklassen, auf die Sie in den XAML-Seiten Ihrer Anwendung verweisen möchten, und erstellen Sie das Projekt einmal, um Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um Ihre lokalen Laufzeitklassen zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

Visual Studio XAML-Design Surface Unterstützung für C++ / WinRT ist nahe Parität mit c#. Eine Ausnahme ist die Registerkarte " **Ereignisse** " **im Eigenschaftenfenster** . Ein C#-Projekt können Sie die Registerkarte Ereignishandler hinzu. mit einem C++ / WinRT-Projekt, diese Funktion ist nicht vorhanden. Aber finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++ / WinRT](handle-events.md) Informationen zur Verwendung der Code-Ereignishandler hinzu.

### <a name="core-app-cwinrt"></a>Core App (C++/WinRT)
Eine Projektvorlage für eine UWP-App (Universelle Windows-Plattform), die keine XAML-Benutzeroberfläche verwendet.

Stattdessen wird der C++/WinRT-Windows-Namespace-Header für den Windows.ApplicationModel.Core-Namespace verwendet. Nach dem Erstellen und Ausführen klicken Sie auf ein leeres Feld, um ein farbiges Quadrat hinzuzufügen; klicken Sie dann auf ein farbiges Quadrat, um es zu ziehen.

### <a name="windows-runtime-component-cwinrt"></a>Komponente für Windows-Runtime (C++/WinRT)
Eine Projektvorlage für eine Komponente; typischerweise für die Nutzung in einer UWP-App (Universelle Windows-Plattform).

Dieses Template demonstriert die `midl.exe` > `cppwinrt.exe`-Toolchain, in der Windows-Runtime-Metadaten (`.winmd`) aus IDL generiert werden, und dann die Implementierung und Header-Stubs aus den Windows-Runtime-Metadaten generiert werden.

Definieren Sie in einer IDL-Datei die Laufzeitklassen in Ihrer Komponenten, deren Standardschnittstelle und alle anderen Schnittstellen, die sie implementieren. Erstellen Sie das Projekt einmalig, um `module.g.cpp`, `module.h.cpp`, Implementierungsvorlagen in `Generated Files` und Stubtypdefinitionen in `Generated Files\sources` zu generieren. Verwenden Sie dann die Stubtypdefinitionen als Referenz, um die Laufzeitklassen in Ihrer Komponente zu implementieren. Wir empfehlen, jede Laufzeitklasse in einer eigenen IDL-Datei zu deklarieren.

Packen Sie die erstellte Binärdatei für die Komponente für Windows-Runtime und deren `.winmd` mit der UWP-App, die diese nutzt.

## <a name="earlier-versions-of-the-vsix-extension"></a>Frühere Versionen der VSIX-Erweiterung
Es wird empfohlen, dass Sie installieren (oder zu aktualisieren) die neueste Version der [VSIX-Erweiterung](https://aka.ms/cppwinrt/vsix). Aktualisieren Sie selbst standardmäßig konfiguriert ist. Wenn Sie dies tun, und Projekte, die mit einer Version der VSIX-Erweiterung vor 1.0.190128.4, und klicken Sie dann auf in diesem Abschnitt erstellt wurden enthält wichtige Informationen über diese Projekte mit der neuen Version zu aktualisieren. Wenn Sie nicht aktualisieren, klicken Sie dann finden noch die Informationen in diesem Abschnitt nützlich Sie.

Hinsichtlich der unterstützten Windows SDK und Visual Studio und Visual Studio-Konfiguration, die Informationen in der [Visual Studio-Unterstützung für C++ / WinRT, XAML, die VSIX-Erweiterung und das NuGet-Paket](#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package) Abschnitt oben gilt für frühere Versionen von VSIX Erweiterung. Die Informationen unten beschreibt wichtige Unterschiede in Bezug auf das Verhalten und Konfiguration von Projekte (oder Arbeit mit aktualisierten) erstellt wurden, mit früheren Versionen Versionen.

### <a name="created-earlier-than-101810022"></a>Vor 1.0.181002.2 erstellt wurden
Wenn Ihr Projekt, mit einer Version der VSIX-Erweiterung vor 1.0.181002.2 und C++ erstellt wurde / WinRT-Build-Unterstützung wurde in dieser Version der VSIX-Erweiterung integriert. Ihr Projekt verfügt über die `<CppWinRTEnabled>true</CppWinRTEnabled>` Eigenschaftensatz der `.vcxproj` Datei.

```xml
<Project ...>
    <PropertyGroup Label="Globals">
        <CppWinRTEnabled>true</CppWinRTEnabled>
...
```

Sie können Ihr Projekt aktualisieren, indem Sie das **Microsoft.Windows.CppWinRT** NuGet-Paket manuell installieren. Nach dem Installieren (oder ein Upgrade auf) die neueste Version der VSIX-Erweiterung, öffnen Sie das Projekt in Visual Studio, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder fügen Sie **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen übergehen, und dann auf **Installieren** , um das Paket für Ihr Projekt zu installieren.

### <a name="created-with-or-upgraded-to-between-101810022-and-101901283"></a>Mit erstellt (oder aktualisiert) zwischen 1.0.181002.2 und 1.0.190128.3
Wenn Ihr Projekt mit einer Version der VSIX-Erweiterung zwischen 1.0.181002.2 und 1.0.190128.3 erstellt wurde, einschließlich dann das **Microsoft.Windows.CppWinRT** NuGet-Paket im Projekt automatisch der Projektvorlage installiert wurde. Sie können auch eine ältere Projekt für eine Version der VSIX-Erweiterung in diesem Bereich aktualisiert haben. Wenn Sie, klicken Sie dann haben&mdash;seit Buildunterstützung auch weiterhin in Versionen der VSIX-Erweiterung in diesem Bereich&mdash;das aktualisierte Projekt möglicherweise oder möglicherweise nicht das **Microsoft.Windows.CppWinRT** NuGet-Paket installiert.

Um Ihr Projekt aktualisieren, folgen Sie den Anweisungen im vorherigen Abschnitt, und stellen Sie sicher, dass Ihr Projekt das **Microsoft.Windows.CppWinRT** NuGet-Paket installiert verfügt.

### <a name="invalid-upgrade-configurations"></a>Ungültige Upgrade-Konfigurationen
Mit der neuesten Version der VSIX-Erweiterung, es gilt nicht für ein Projekt, haben die `<CppWinRTEnabled>true</CppWinRTEnabled>` Eigenschaft, wenn sie auch das **Microsoft.Windows.CppWinRT** NuGet-Paket installiert verfügt. Ein Projekt mit dieser Konfiguration erzeugt die Fehlermeldung "Build", "C++ / WinRT VSIX nicht mehr unterstützt Projekt erstellen.  Bitte fügen Sie einen Projektverweis auf das Microsoft.Windows.CppWinRT Nuget-Paket. hinzu"

Wie erwähnt oben eine C++ / WinRT-Projekt jetzt muss das NuGet-Paket installiert haben.

Da die `<CppWinRTEnabled>` Element ist veraltet, Sie können optional Bearbeiten Ihrer `.vcxproj`, und löschen Sie das Element. Es ist nicht unbedingt erforderlich, aber es ist eine Option.

## <a name="custom-types-in-the-cwinrt-projection"></a>Benutzerdefinierte Typen in der C++/WinRT-Projektion
In Ihrer C++ / WinRT-Programmierung können Sie Standard-c++-Sprachfunktionen und [Standard C++ Datentypen und C++ / WinRT](std-cpp-data-types.md)&mdash;einschließlich einiger C++ Standard Library-Datentypen. Sie werden aber auch einige benutzerdefinierte Datentypen in der Projektion bemerken und können diese verwenden. Beispielsweise verwenden wir [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring) im Schnellstart-Codebeispiel in [Erste Schritte mit C++/WinRT](get-started.md).

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
