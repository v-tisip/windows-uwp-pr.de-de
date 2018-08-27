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
keywords: Windows 10, systemeigene Abbild Compiler
ms.localizationpriority: medium
ms.openlocfilehash: d98b576fb51a8f9507802796ab359d0d00d21998
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2855274"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a>Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder

> [!NOTE]
> Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Sie können die Startzeit der .NET Framework-Anwendung verbessern, indem Sie vor dem Kompilieren der Binärdateien. Sie können diese Technologie auf große Applikationen verwenden, die Sie packen und verteilen Sie über den Windows Store. In einigen Fällen haben wir eine leistungsverbesserung von 20 % beobachtet. Erfahren Sie mehr über diese Technologie in der [technischen Überblick](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).

Wir haben eine Preview-Version des Compilers systemeigene Bild als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht. Sie können dieses Paket auf einer beliebigen .NET Framework-Anwendung, die auf .NET Framework, Version 4.6.2 abzielt anwenden oder höher. Dieses Paket Fügt einen Post Buildschritt, der eine systemeigene Nutzlast die Binärdateien, die für die von der Anwendung verwendeten enthält. Diese optimierte Nutzlast wird beim Ausführen der Anwendung in .NET 4.7.2 und höher während Vorgängerversionen MSIL-Code noch geladen werden geladen.

Das [.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) ist in der [Windows-10 April 2018 aktualisieren](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)enthalten. Sie können auch diese Version von .NET Framework auf PCs installieren, auf denen Windows 7 + und Windows Server 2008 R2 oder höher ausgeführt.

> [!IMPORTANT]
> Wenn Sie systemeigene Abbilder für Ihre Anwendung mithilfe der Windows-Anwendung packprojekt gepackt erstellen möchten, stellen Sie sicher, dass Sie die Ziel-Plattform mindestens Version des Projekts auf die Windows-Updates im Unternehmen festgelegt.

## <a name="how-to-produce-native-images"></a>Wie systemeigene Abbilder erzeugt.

Befolgen Sie diese Anweisungen zum Konfigurieren von Projekten.

1. Konfigurieren Sie das Zielframework als 4.6.2 oder höher

2. Konfigurieren der Zielplattform als X86 oder x64 

3. Fügen Sie die NuGet-Pakete.

4. Erstellen Sie einen Versionsbuild.

## <a name="configure-the-target-framework-as-462-or-above"></a>Konfigurieren Sie das Zielframework als 4.6.2 oder höher

So konfigurieren Sie Ihr Projekt .NET Framework 4.6.2 Ziel benötigen Sie die .NET Framework 4.6.2 Entwicklungstools oder höher. Diese Tools sind als optionale Komponenten unter den desktop Entwicklungsaufwand .NET über die Visual Studio-Installer verfügbar:

![Installieren von .NET 4.6.2 Entwicklungswerkzeuge (engl.)](images/desktop-to-uwp/install-4.6.2-devpack.png)

Alternativ können Sie die .NET Developer Packs aus abrufen:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)

## <a name="configure-the-target-platform-as-x86-or-x64"></a>Konfigurieren der Zielplattform als X86 oder x64

Der systemeigene Abbild Compiler optimiert den Code für eine bestimmte Plattform. Um es zu verwenden, müssen Sie die Anwendung für eine bestimmte wie X86 oder X64 Zielplattform konfigurieren.

Wenn Sie mehrere Projekte in der Projektmappe verfügen, muss nur das Eintrag Punkt Projekt (wahrscheinlich das Projekt, das eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden. Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden, auch wenn sie als AnyCPU kompiliert werden mit der Architektur, die in die Hauptassembly des Projekts, angegebenen verarbeitet.

So konfigurieren Sie Ihr Projekt:

1. Maustaste auf die Projektmappe, und wählen Sie dann auf **Konfigurations-Manager**.

2. Wählen Sie **< neu. >** im Dropdownmenü **Plattform** neben dem Namen des Projekts, das die ausführbare Datei erzeugt.

3. Klicken Sie im Dialogfeld **Neues Projektplattform** sicher, dass die Dropdownliste für **Copy Settings from** auf **Any CPU**festgelegt ist.

![Konfigurieren von x86](images/desktop-to-uwp/configure-x86.png)

Wiederholen Sie diesen Schritt für `Release/x64` Wenn X64 erzeugen soll Binärdateien.

>[!IMPORTANT]
> AnyCPU-Konfiguration wird vom Compiler systemeigene Abbild nicht unterstützt.

## <a name="add-the-nuget-packages"></a>Hinzufügen von NuGet-Pakete

Systemeigene Abbild Compiler wird als ein NuGet-Paket bereitgestellt, die Visual Studio-Projekt hinzuzufügen, die ausführbare Datei erstellt. Dies ist üblicherweise das Windows Forms oder WPF-Projekt. Verwenden Sie diesen Befehl PowerShell, dafür.

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> Die Preview-Pakete werden als nicht aufgeführte in NuGet.org veröffentlicht. Diese werden nicht durch Durchsuchen NuGet.org oder mithilfe der Paket-Manager-UI in Visual Studio finden. Sie können jedoch installieren sie die Paket-Manager-Konsole und wann Sie von einem anderen Computer wiederherstellen. Wir stellen die Pakete vollständig zugänglich beim Veröffentlichen der ersten nicht-Preview-Version.

## <a name="create-a-release-build"></a>Erstellen eines Builds Version

NuGet-Paket konfiguriert das Projekt, um ein zusätzliches Tool für Version Builds ausführen. Dieses Tool hinzugefügt dieselben Binärdateien systemeigenen Code.
Um sicherzustellen, dass das Tool, die Binärdateien verarbeitet wurden können Sie den Ausgabe, um sicherzustellen, dass sie eine Nachricht wie diesen enthält Build überprüfen:

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a>Häufig gestellte Fragen

**Q. Funktionieren die neuen Binärdateien auf Computern ohne .NET Framework 4.7.2?**

A. Optimierte Binärdateien profitieren von der Verbesserungen bei der Ausführung mit .NET Framework 4.7.2. Clients, auf denen frühere Versionen von .NET Framework ausgeführt werden nicht optimiert MSIL-Code aus der Binärdatei geladen.

**Q. Wie kann ich melden Probleme oder Feedback senden?**

A. Melden Sie ein Problem mit dem Feedback-Tool in Visual Studio 2017. [Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

**Q. Was ist die Auswirkung des Hinzufügens des systemeigenen Abbilds zu vorhandenen Binärdateien?**

A. Optimierten Binärdateien enthalten verwalteten und systemeigenen Code, damit die endgültigen Dateien größer.

**Q. Kann mithilfe dieser Technologie Binärdateien werden freigegeben?**

A. Diese Version umfasst eine Go Live-Lizenz, die Sie heute verwenden können.
