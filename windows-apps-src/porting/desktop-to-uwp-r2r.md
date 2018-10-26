---
author: rido-min
Description: This guide explains how to configure your Visual Studio Solution to optimize the application binaries with native images.
Search.Product: eADQiWindows 10XVcnh
title: Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder
ms.author: normesta
ms.date: 06/11/2018
ms.topic: article
keywords: Windows 10, systemeigene Abbilder Compiler
ms.localizationpriority: medium
ms.openlocfilehash: 231d5aa895cb4cf63ade01660df61e32424e67c7
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5549114"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a>Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder

> [!NOTE]
> Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Sie können die Startzeit Ihrer .NET Framework-Anwendung verbessern, indem Sie Ihre Binärdateien wird vorkompiliert. Sie können diese Technologie auf große Anwendungen verwenden, die Sie verpacken und über den Windows Store zu verteilen. In einigen Fällen haben wir eine 20 % Leistungssteigerung beobachtet. Erfahren Sie mehr über diese Technologie in die [Technische Übersicht](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).

Wir haben eine Vorschauversion von der Compiler systemeigenes Bild als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht. Sie können dieses Paket auf jede .NET Framework-Anwendung, die das .NET Framework-Version 4.6.2 zielt auf Anwenden oder höher. Dieses Paket Fügt einen Buildschritt Post, der eine systemeigene Nutzlast auf alle Binärdateien, die von der Anwendung verwendeten enthält. -Nutzlast dieser optimierte wird geladen werden, wenn die Anwendung in .NET 4.7.2 und höher ausführt, während frühere Versionen weiterhin den MSIL-Code geladen werden.

Das [.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) ist in der [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)enthalten. Sie können diese Version von .NET Framework auch auf PCs installieren, auf denen Windows 7 + und Windows Server 2008 R2 oder höher ausgeführt.

> [!IMPORTANT]
> Wenn Sie systemeigene Abbilder für Ihre Anwendung verpackt vom Windows Application Packaging-Projekt erstellen möchten, stellen Sie sicher, die Ziel Plattform mindestens erforderliche Version des Projekts auf das Windows Anniversary Update festlegen.

## <a name="how-to-produce-native-images"></a>Wie Sie systemeigene Abbilder zu erzeugen.

Konfigurieren von Projekten, gehen Sie wie folgt vor.

1. Konfigurieren Sie das Ziel-Framework als 4.6.2 oder höher

2. Konfigurieren Sie die Zielplattform als X86 oder x64 

3. Fügen Sie die NuGet-Pakete hinzu.

4. Erstellen Sie einen Versionsbuild.

## <a name="configure-the-target-framework-as-462-or-above"></a>Konfigurieren Sie das Ziel-Framework als 4.6.2 oder höher

Zum Konfigurieren des Projekts .NET Framework 4.6.2 Ziel benötigen Sie die Entwicklungstools für .NET Framework 4.6.2 oder höher. Diese Tools sind als optionale Komponenten unter der .NET Desktopentwicklung Workload durch den Visual Studio Installer verfügbar:

![Installieren Sie .NET 4.6.2 Entwicklungstools](images/desktop-to-uwp/install-4.6.2-devpack.png)

Alternativ können Sie die .NET Developer Packs aus abrufen:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)

## <a name="configure-the-target-platform-as-x86-or-x64"></a>Konfigurieren Sie die Zielplattform als X86 oder x64

Den systemeigenen Images Compiler optimiert den Code für eine bestimmte Plattform. Um es zu verwenden, müssen Sie die Anwendung für eine bestimmte z. B. X86 oder X64 Zielplattform konfigurieren.

Wenn Sie in Ihrer Projektmappe mehrere Projekte verfügen, weist nur das Eintrag Punkt Projekt (wahrscheinlich das Projekt, das eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden. Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden mit der im Hauptprojekt angegebenen Architektur verarbeitet werden, auch wenn sie als "anycpu" kompiliert werden.

So konfigurieren Sie Ihr Projekt:

1. Mit der rechten Maustaste der Projektmappe, und wählen Sie dann **Configuration Manager**.

2. Wählen Sie **< neu. >** im Dropdownmenü **Plattform** neben dem Namen des Projekts, das die ausführbare Datei erstellt.

3. Das Dialogfeld **Neues Projektplattform** stellen Sie sicher, dass die Dropdown-Liste **Copy Settings from** **Any CPU**festgelegt ist.

![Konfigurieren von x86](images/desktop-to-uwp/configure-x86.png)

Wiederholen Sie diesen Schritt für `Release/x64` auf Wunsch X64 erzeugen Binärdateien.

>[!IMPORTANT]
> AnyCPU-Konfiguration wird vom Compiler systemeigene Bild nicht unterstützt.

## <a name="add-the-nuget-packages"></a>Fügen Sie das NuGet-Pakete

Der Compiler systemeigenes Bild wird als NuGet-Paket bereitgestellt, die Sie benötigen Visual Studio-Projekt hinzu, die die ausführbare Datei erstellt. Dies ist in der Regel Ihre Windows Forms- oder WPF-Projekt. Verwenden Sie diese PowerShell-Befehl, dafür.

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> Die Vorschau-Pakete werden in "NuGet.org" als nicht aufgeführten veröffentlicht. Sie wird nicht durch Browsen "NuGet.org" oder mithilfe der UI-Paket-Manager in Visual Studio fündig. Sie können jedoch installieren sie das Paket-Manager-Konsole und wann Sie von einem anderen Computer wiederherstellen. Wir stellen die Pakete vollständig verfügbar wenn wir die erste nicht-Preview-Version veröffentlichen.

## <a name="create-a-release-build"></a>Erstellen eines Releasebuilds

Das NuGet-Paket konfiguriert das Projekt, um ein zusätzliches Tool für Release-Builds ausführen. Dieses Tool hinzugefügt die gleichen Binärdateien systemeigenen Code.
Um sicherzustellen, dass das Tool die Binärdateien verarbeitet hat können Sie überprüfen die Buildausgabe in stellen Sie sicher, dass sie eine Nachricht wie diesen enthält:

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a>Häufig gestellte Fragen

**Q. Funktionieren die neuen Binärdateien auf Computern ohne .NET Framework 4.7.2?**

A. Optimierte Binärdateien profitiert von Verbesserungen bei der Ausführung mit .NET Framework 4.7.2. Clients, auf denen frühere Versionen von .NET Framework ausgeführt werden den nicht optimierten MSIL-Code aus der Binärdatei geladen.

**Q. Wie kann ich Feedback können senden oder melden Probleme?**

A. Melden eines Problems mithilfe der Feedback-Tools in Visual Studio 2017. [Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

**Q. Was ist die Auswirkung der vorhandenen Binärdateien systemeigenen Images hinzugefügt?**

A. Die optimierten Binärdateien enthalten den verwalteten und systemeigenen Code, damit die endgültigen Dateien größer.

**Q. Kann mit dieser Technologie Binärdateien werden freigegeben?**

A. Diese Version enthält eine wechseln Sie Live-Lizenz, die Sie heute verwenden können.
