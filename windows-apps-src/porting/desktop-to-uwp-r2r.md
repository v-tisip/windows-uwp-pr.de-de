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
keywords: Windows 10, systemeigene Abbilder Compiler
ms.localizationpriority: medium
ms.openlocfilehash: d98b576fb51a8f9507802796ab359d0d00d21998
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4059042"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a>Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder

> [!NOTE]
> Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Sie können die Startzeit Ihrer .NET Framework-Anwendung verbessern, indem Sie die Binärdateien vorkompiliert. Sie können diese Technologie auf großen Anwendungen verwenden, die Sie verpacken und über den Windows Store zu verteilen. In einigen Fällen haben wir eine 20 % Leistungssteigerung beobachtet. Hier erfahren Sie mehr über diese Technologie in die [Technische Übersicht](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).

Wir haben eine Vorschauversion von der Compiler systemeigenes Bild als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht. Sie können dieses Paket auf jede .NET Framework-Anwendung, die das .NET Framework-Version 4.6.2 zielt auf Anwenden oder höher. Dieses Paket Fügt einen Post-Buildschritt, der eine systemeigene Nutzlast auf alle Binärdateien, die von der Anwendung verwendeten enthält. -Nutzlast dieser optimierten wird geladen werden, wenn die Anwendung in .NET 4.7.2 und höher ausführt, während der vorherige Versionen den MSIL-Code noch geladen werden.

Das [.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) ist in der [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)enthalten. Sie können diese Version von .NET Framework auch auf PCs installieren, auf denen Windows 7 + und Windows Server 2008 R2 oder höher ausgeführt.

> [!IMPORTANT]
> Wenn Sie systemeigene Abbilder für Ihre Anwendung verpackt, die Windows Application Packaging-Projekt erstellen möchten, stellen Sie sicher, die Ziel-Plattform mindestens erforderliche Version des Projekts auf das Windows Anniversary Update festlegen.

## <a name="how-to-produce-native-images"></a>Erläutert, wie diese systemeigenen Images erstellt.

Konfigurieren von Projekten, gehen Sie wie folgt vor.

1. Konfigurieren Sie das Zielframework als 4.6.2 oder höher

2. Konfigurieren Sie die Zielplattform als X86 oder x64 

3. Fügen Sie die NuGet-Pakete hinzu.

4. Erstellen Sie einen Versionsbuild.

## <a name="configure-the-target-framework-as-462-or-above"></a>Konfigurieren Sie das Zielframework als 4.6.2 oder höher

Zum Konfigurieren des Projekts .NET Framework 4.6.2 Ziel benötigen Sie die Entwicklungstools für .NET Framework 4.6.2 oder höher. Diese Tools sind als optionale Komponenten unter der .NET desktop-Entwicklung Workload durch den Visual Studio-Installer verfügbar:

![Installieren Sie .NET 4.6.2 Entwicklungstools](images/desktop-to-uwp/install-4.6.2-devpack.png)

Alternativ können Sie die .NET Developer Packs aus abrufen:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)

## <a name="configure-the-target-platform-as-x86-or-x64"></a>Konfigurieren Sie die Zielplattform als X86 oder x64

Der systemeigene Bild-Compiler optimiert den Code für eine bestimmte Plattform. Um es zu verwenden, müssen Sie Ihre Anwendung an eine bestimmte Plattform z. B. X86 oder X64 konfigurieren.

Wenn Sie in Ihrer Projektmappe mehrere Projekte verfügen, muss nur das Eintrag Punkt Projekt (wahrscheinlich das Projekt, das eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden. Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden, auch wenn sie als "anycpu" kompiliert werden mit der im Hauptprojekt angegebenen Architektur verarbeitet.

So konfigurieren Sie Ihr Projekt:

1. Mit der rechten Maustaste in der Projektmappe, und wählen Sie dann die **Configuration Manager**.

2. Wählen Sie **< neu. >** im Dropdownmenü **Plattform** neben dem Namen des Projekts, das die ausführbare Datei erstellt.

3. Stellen Sie sicher, dass die **Kopie Einstellungen aus** Dropdown-Liste auf **Any CPU**festgelegt ist Schritte aus, klicken Sie im Dialogfeld **Neues Projekt-Plattform** .

![Konfigurieren von x86](images/desktop-to-uwp/configure-x86.png)

Wiederholen Sie diesen Schritt für `Release/x64` Wunsch X64 erzeugen Binärdateien.

>[!IMPORTANT]
> AnyCPU-Konfiguration wird vom Compiler systemeigene Bild nicht unterstützt.

## <a name="add-the-nuget-packages"></a>Fügen Sie das NuGet-Pakete

Der Compiler systemeigenes Bild wird als NuGet-Paket bereitgestellt, die Sie benötigen Visual Studio-Projekt hinzu, die die ausführbare Datei erstellt. Dies ist in der Regel Ihre Windows Forms- oder WPF-Projekt. Verwenden Sie diesen PowerShell-Befehl, dafür.

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> Die Vorschau-Pakete werden in "NuGet.org" als nicht aufgeführten veröffentlicht. Sie wird nicht diese Durchsuchen "NuGet.org" oder mithilfe der UI-Paket-Manager in Visual Studio finden. Sie können jedoch installieren sie das Paket-Manager-Konsole und wann Sie von einem anderen Computer wiederherstellen. Wir verwenden die Pakete vollständig erstellen, wenn wir die erste nicht-Preview-Version veröffentlichen.

## <a name="create-a-release-build"></a>Erstellen eines Releasebuilds

Das NuGet-Paket konfiguriert das Projekt, um ein zusätzliches Tool für Release-Builds ausführen. Dieses Tool hinzugefügt die gleichen Binärdateien systemeigenen Code.
Um sicherzustellen, dass das Tool die Binärdateien verarbeitet hat können Sie überprüfen, um sicherzustellen, dass sie eine Nachricht wie diesen enthält die Buildausgabe:

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a>Häufig gestellte Fragen

**Q. Funktionieren die neuen Binärdateien auf Computern ohne .NET Framework 4.7.2?**

A. Optimierte Binärdateien werden von Verbesserungen profitieren, wenn mit .NET Framework 4.7.2 ausgeführt. Clients, die vorherige .NET Framework-Versionen ausgeführt werden den nicht optimierten MSIL-Code aus der Binärdatei geladen.

**Q. Wie kann ich Feedback können senden oder melden Probleme?**

A. Melden eines Problems mit dem Feedback-Tool in Visual Studio 2017. [Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

**Q. Was ist die Auswirkung der vorhandenen Binärdateien systemeigenen Images hinzugefügt?**

A. Die optimierten Binärdateien enthalten den verwalteten und systemeigenen Code, damit die endgültigen Dateien größer.

**Q. Kann ich Binärdateien, die mit dieser Technologie freigegeben?**

A. Diese Version enthält eine wechseln Sie Live-Lizenz, mit denen Sie noch heute.
