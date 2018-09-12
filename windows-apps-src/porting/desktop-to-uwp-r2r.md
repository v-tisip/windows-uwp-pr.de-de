---
author: rido-min
Description: This guide explains how to configure your Visual Studio Solution to optimize the application binaries with native images.
Search.Product: eADQiWindows 10XVcnh
title: Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder
ms.author: normesta
ms.date: 06/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 systemeigene Abbilder Compiler
ms.localizationpriority: medium
ms.openlocfilehash: d98b576fb51a8f9507802796ab359d0d00d21998
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3931120"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a>Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder

> [!NOTE]
> Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Die Startzeit der.NET Framework-Anwendung können Sie die Binärdateien vorkompiliert verbessern. Diese Technologie können für große Applikationen, die Sie packen und verteilen Windows Store. In einigen Fällen haben wir eine Leistungssteigerung von 20 % beobachtet. Sie können diese Technologie in der [technischen Übersicht](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md)erfahren.

Wir haben eine Vorschauversion des systemeigenen Abbilds Compiler als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht. Alle.NET Framework-Anwendung für.NET Framework Version 4.6.2 dieses Paket zuweisen oder höher. Dieses Paket fügt Buildschritt Post, der systemeigene Nutzlast, die von der Anwendung verwendeten Binärdateien enthält. Diese optimierte Nutzlast wird beim Ausführen der Anwendung in .NET 4.7.2 und höher Vorgängerversionen den MSIL-Code noch geladen werden geladen.

[.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) [10 April 2018 Windows update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)gehört. Sie können auch diese Version von.NET Framework auf PCs, die Windows 7 und Windows Server 2008 R2 ausgeführt.

> [!IMPORTANT]
> Wenn systemeigene Bilder für die Anwendung von Windows Application Packaging-Projekt verpackt werden soll, müssen Sie Windows Jahrestag Update Ziel Plattform minimale Version des Projekts fest.

## <a name="how-to-produce-native-images"></a>Wie systemeigene Bilder

Konfigurieren von Projekten, gehen Sie wie folgt vor.

1. Konfigurieren Sie das Zielframework 4.6.2 oder oben

2. Konfigurieren Sie die Zielplattform als X86 oder x64 

3. NuGet-Pakete hinzufügen.

4. Erstellen Sie einen Versionsbuild.

## <a name="configure-the-target-framework-as-462-or-above"></a>Konfigurieren Sie das Zielframework 4.6.2 oder oben

Konfigurieren Sie das Projekt auf.NET Framework 4.6.2 benötigen Sie.NET Framework 4.6.2 Entwicklungstools oder höher. Diese Tools sind als optionale Komponenten Arbeitslast Desktopentwicklung .NET über Visual Studio Installer verfügbar:

![Installieren Sie .NET 4.6.2 Entwicklungstools](images/desktop-to-uwp/install-4.6.2-devpack.png)

Alternativ erhalten Sie .NET Developer Packs aus:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)

## <a name="configure-the-target-platform-as-x86-or-x64"></a>Konfigurieren Sie die Zielplattform als X86 oder x64

Systemeigene Abbilder Compiler optimiert den Code für eine bestimmte Plattform. Für die Verwendung müssen Sie Ihre Anwendung auf einer bestimmten Plattform wie X86 oder X64.

Mehrere Projekte in der Projektmappe vorhanden sind, ist nur das Eintrag Punkt Projekt (höchstwahrscheinlich die, die eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden. Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden, wenn sie als AnyCPU kompiliert werden in das Hauptprojekt angegebene Architektur verarbeitet.

So konfigurieren Sie das Projekt

1. Maustaste auf die Projektmappe und wählen Sie **Configuration Manager**.

2. Wählen Sie **< neu... >** in der **Plattform** -Dropdown-Menü neben dem Namen des Projekts, das die ausführbare Datei erstellt.

3. Klicken Sie im Dialogfeld **Neue Projektplattform** sicherstellen Sie, dass die Dropdownliste **Copy Settings from** **Any CPU**festgelegt ist.

![X86 konfigurieren](images/desktop-to-uwp/configure-x86.png)

Wiederholen Sie diesen Schritt für `Release/x64` sollten X64 erzeugen Binärdateien.

>[!IMPORTANT]
> AnyCPU-Konfiguration wird vom Compiler systemeigene Abbilder nicht unterstützt.

## <a name="add-the-nuget-packages"></a>Hinzufügen von NuGet-Paketen

Systemeigene Abbilder Compiler wird ein NuGet-Paket bereitgestellt, die Sie dem Visual Studio-Projekt hinzufügen, die ausführbare Datei erstellt. Dies ist in der Regel Windows Forms- oder WPF-Projekt. Dieser Befehl PowerShell dazu.

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> Vorschau-Pakete werden in NuGet.org als veröffentlicht. Sie wird nicht durchsuchen NuGet.org oder Paket-Manager UI in Visual Studio finden. Aber Sie können sie von der Konsole Paket-Manager und wenn Sie von einem anderen Computer wiederherstellen. Wir machen die Pakete barrierefrei beim ersten-Preview-Version veröffentlichen.

## <a name="create-a-release-build"></a>Erstellen eines Releasebuilds

NuGet-Paket konfiguriert das Projekt um ein zusätzliches Tool für Releasebuilds auszuführen. Dieses Tool hinzugefügt dieselben Binärdateien systemeigenen Code.
Um sicherzustellen, dass das Tool die Binärdateien verarbeitet hat können Sie überprüfen die Buildausgabe um sicherzustellen, dass eine Meldung wie diese enthält:

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a>Häufig gestellte Fragen

**Q. Arbeiten die neuen Binärdateien ohne.NET Framework 4.7.2?**

A. Optimierte Binärdateien Verbesserungen profitieren mit.NET Framework 4.7.2 ausgeführt. Clients, die frühere Versionen von .NET Framework lädt nicht optimierten MSIL-Codes aus der Binärdatei.

**Q. Wie kann ich Feedback oder melden Probleme?**

A. Melden Sie ein Problem mit dem Feedback-Tool in Visual Studio 2017. [Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

**Q. Wie wirkt bestehender Binärdateien des systemeigenen Abbilds hinzufügen?**

A. Optimierten Binärdateien enthalten den verwalteten und systemeigenen Code, machen die fertigen Dateien größer.

**Q. Können diese Technologie Binärdateien freigeben?**

A. Diese Version enthält eine Go Live Lizenz, die Sie verwenden können.
