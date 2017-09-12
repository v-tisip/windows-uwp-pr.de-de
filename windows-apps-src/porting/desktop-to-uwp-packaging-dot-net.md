---
author: normesta
Description: "In diesem Handbuch wird erläutert, wie Sie Ihre Visual Studio-Lösung zum Bearbeiten, Debuggen und Packen Ihrer konvertierten Desktop-App für die Desktop-Brücke konfigurieren."
Search.Product: eADQiWindows 10XVcnh
title: "Verpacken einer App mit Visual Studio (Desktop-Brücke)"
ms.author: normesta
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.openlocfilehash: d8919448b965f18ff7f8fdaeda325889e495ef85
ms.sourcegitcommit: f6dd9568eafa10ee5cb2b849c0d82d84a1c5fb93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2017
---
# <a name="package-an-app-by-using-visual-studio-desktop-bridge"></a>Verpacken einer App mit Visual Studio (Desktop-Brücke)

Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren. Anschließend können Sie das Paket im Windows Store veröffentlichen oder es auf einem oder mehreren PCs querladen.

Dieser Anleitung zeigt, wie Sie Ihre Lösung einrichten und ein Paket für Ihre Desktopanwendung generieren.

## <a name="first-consider-how-youll-distribute-your-app"></a>Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.

Wenn Sie Ihre App im [Windows Store-](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge). Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess. Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.

## <a name="add-a-packaging-project-to-your-solution"></a>Hinzufügen eines Verpackungsprojekts zur Lösung

1. Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.

2. Fügen Sie der Projektmappe eine JavaScript **Leere App (Universal Windows)**-Projekt hinzu.

   Sie müssen keinen Code hinzufügen. Es dient nur, um ein Paket zu generieren. Wir nennen das Projekt „packaging project“.

   ![JavaScript-UWP-Projekt](images/desktop-to-uwp/javascript-uwp-project.png)

   >[!IMPORTANT]
   >Im Allgemeinen sollten Sie die JavaScript-Version des Projekts verwenden.  Die C#-, VB.NET- und C++ Versionen haben einige Probleme. Wenn Sie diese verwenden wollen, lesen Sie vorher [Bekannte Probleme](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor).

## <a name="add-the-desktop-application-binaries-to-the-packaging-project"></a>Hinzufügen von Desktopanwendungs-Binärdateien zum Verpackungsprojekt

Hinzufügen von Binärdateien direkt zum Verpackungsprojekt.

1. In **Projektmappen-Explorer** erweitern Sie den Verpacken-Projektordner, erstellen einen Unterordner und benennen ihn beliebig (z.B.: **win32**).

2. Klicken Sie jetzt mit der rechten Maustaste auf den Unterordner und wählen Sie **Vorhandenes Elemente hinzufügen** aus.

3. Im **Vorhandenes Element hinzufügen** Dialogfeld suchen Sie die Dateien aus Ihrem Desktopanwendung-Ausgabeordner und fügen diese hinzu. Dazu umfasst nicht nur die ausführbaren Dateien, sondern auch alle DLLs oder config-Dateien, die sich in diesem Ordner befinden.

   ![Ausführbare Referenzdatei](images/desktop-to-uwp/cpp-exe-reference.png)

   Jedes Mal, wenn Sie an Ihrem Desktopanwendung-Projekt Änderungen vornehmen, müssen Sie eine neue Version dieser Dateien in das Verpacken-Projekt kopieren. Sie können dies automatisieren, indem Sie der Projektdatei des Verpackung-Projekts ein Postbuildereignis hinzufügen. Beispiel:

   ```XML
   <Target Name="PostBuildEvent">
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.exe"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.exe.config"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.pdb"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyBusinessLogicLibrary.dll"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyBusinessLogicLibrary.pdb"
       DestinationFolder="win32" />
   </Target>
   ```

## <a name="modify-the-package-manifest"></a>Bearbeiten des Paketmanifests

Das Paketprojekt enthält eine Datei, die die Einstellungen des Pakets beschreibt. Standardmäßig beschreibt diese Datei eine UWP-App. Sie müssen sie so anpassen, dass das System weiß, dass das Paket eine Desktopanwendung enthält, die in voller Vertrauenswürdigkeit ausgeführt wird.  

1. Erweitern Sie im **Lösungs-Explorer** das Verpacken-Projekt, klicken Sie mit Rechts auf die **package.appxmanifest** Datei und wählen Sie **Code anzeigen** aus.

   ![Referenz-Dotnet-Projekt](images/desktop-to-uwp/reference-dotnet-project.png)

2. Fügen Sie diesen Namespace am Anfang der Datei hinzu und fügen Sie das Namespacepräfix zu Liste der ``IgnorableNamespaces`` hinzu.

   ```XML
   xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
   ```
   Wenn Sie fertig sind, sehen die Namespacedeklarationen wie folgt aus:

   ```XML
   <Package
     xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
     xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
     xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
     xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
     IgnorableNamespaces="uap mp rescap">
   ```

3. Suchen Sie das ``TargetDeviceFamily``-Element und legen das ``Name``-Attribut auf **Windows.Desktop**, das ``MinVersion``-Attribut auf die Mindestversion des Paketprojekts und das ``MaxVersionTested`` auf die Zielversion des Projekts fest.

   ```XML
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.10586.0" MaxVersionTested="10.0.15063.0" />
   ```

   Sie finden die Mindestversion und die Zielversion auf den Eigenschaftenseiten des Verpackung-Projekts.

   ![Einstellungen für Mindest- und Zielversion](images/desktop-to-uwp/min-target-version-settings.png)


4. Entfernen Sie das ``StartPage``-Attribut aus dem ``Application``-Element. Fügen Sie dann die ``Executable``- und ``EntryPoint``-Attribute hinzu.

   Das ``Application``-Ergebnis sieht wie folgt aus.

   ```XML
   <Application Id="App"  Executable=" " EntryPoint=" ">
   ```

5. Legen Sie das ``Executable`` Attribut auf den Namen der ausführbaren Datei für Ihre Desktopanwendung fest. Legen Sie anschließend das ``EntryPoint``-Attribut auf **Windows.FullTrustApplication** fest.

   Das ``Application``-Element sieht etwa wie folgt aus.

   ```XML
   <Application Id="App"  Executable="win32\MyWindowsFormsApplication.exe" EntryPoint="Windows.FullTrustApplication">
   ```
6. Fügen Sie die ``runFullTrust``-Funktion zum ``Capabilities`` Element hinzu.

   ```XML
     <rescap:Capability Name="runFullTrust"/>
   ```
   Blaue Wellenlinien werden möglicherweise unter dieser Deklaration angezeigt, doch sie können problemlos ignoriert werden.

   >[!IMPORTANT]
   Wenn Sie ein Pakets für eine C++-Desktopanwendung erstellen, müssen Sie einige zusätzliche Daten in der Manifestdatei ändern, damit Sie die Visual C++-Laufzeitbibliotheken zusammen mit Ihrer App bereitstellen können. Weitere Informationen finden Sie unter [Visual C++-Laufzeiten in einem Projekt für die Desktop-Brücke nutzen](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).

7. Erstellen Sie das Verpacken-Projekt, um sicherzustellen, dass keine Fehler angezeigt werden.

8. Wenn Sie das Paket testen möchten, lesen Sie [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md).

   Lesen Sie dann den nächsten Abschnitt, um Ihr Paket zu generieren.

## <a name="generate-a-package"></a>Generieren eines Pakets

Um ein Paket für Ihre App zu generieren, befolgen Sie die Anleitung im Thema [Verpacken von UWP-Apps](..\packaging\packaging-uwp-apps.md).

Wenn Sie die Seite **Auswählen und Konfigurieren von Paketen** erreichen, nehmen Sie sich einen Moment Zeit und überlegen Sie, welche Arten von Binärdateien Sie in Ihrem Paket haben möchten.

* Wenn Sie die Desktopanwendung [erweiterten](desktop-to-uwp-extend.md), indem Sie ein C#-, C++ oder VB.NET-basiertes Universellen Windows-Plattform-Projekt der Projektmappe hinzufügen, wählen die **x86**- und **x64**-Kontrollkästchen.  

* Wählen Sie andernfalls das **Neutral**-Kontrollkästchen.

>[!NOTE]
Der Grund für das Auswählen jeder unterstützten Plattform ist, das eine Lösung, die Sie erweitert haben, zwei Arten von Binärdateien enthält. Eine für das UWP-Projekt und eine für das Desktop-Projekt. Da diese Arten von Binärdateien unterschiedlich sind, muss .NET Native explizit systemeigene Binärdateien für jede Plattform erstellen.

Wenn Fehler auftreten, wenn Sie versuchen, das Paket zu generieren, finden Sie unter der [Bekannte Probleme](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor) Hilfen. Wenn Ihr Problem in dieser Liste nicht angezeigt wird, teilen Sie uns das Problem [hier](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge) mit.

## <a name="next-steps"></a>Nächste Schritte

**Ausführer Ihrer App/Suchen und Beheben von Problemen**

Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)

**Verbessern Sie Ihre Desktop-App durch Hinzufügen von UWP-APIs**

Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)

**Erweitern Sie Ihre Desktop-App durch Hinzufügen von UWP-Komponenten**

Siehe [Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten](desktop-to-uwp-extend.md)

**Verteilen Ihrer App**

Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
