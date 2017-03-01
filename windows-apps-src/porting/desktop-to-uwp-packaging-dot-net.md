---
author: awkoren
Description: "In diesem Handbuch wird erläutert, wie Sie Ihre Visual Studio-Lösung zum Bearbeiten, Debuggen und Packen Ihrer konvertierten Desktop-Brücke-App konfigurieren."
Search.Product: eADQiWindows 10XVcnh
title: "Handbuch zur Desktop-Brücke-Verpackung von .NET Desktop-Apps mit Visual Studio"
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 8aa68312d6ce81c809c79ddcafe7732944a628be
ms.lasthandoff: 02/08/2017

---

# <a name="desktop-bridge-packaging-guide-for-net-desktop-apps-with-visual-studio"></a>Handbuch zur Desktop-Brücke-Verpackung von .NET Desktop-Apps mit Visual Studio

Die Windows 10 Anniversary Update bietet Entwicklern die Option, die Desktop-Brücke zum Packen von vorhandenen Win32-Apps über das neue Paketmodell (.appx), zu nutzen und so das Querladen im Store zu ermöglichen. Dieses Handbuch beschreibt, wie Sie Ihre Visual Studio-Lösung so konfigurieren, dass Sie Ihre App bearbeiten, debuggen und verpacken können. 

Füllen Sie zunächst das Formular unter [Bereitstellen vorhandener Apps und Spiele im Windows Store mithilfe der Desktop-Brücke](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge) aus. Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess. Sobald Ihr Konto für das Einrichten von Desktop-Brücke-Apps freigeschaltet wurde, folgen den Anweisungen in diesem Dokument, um das Appxupload-Paket für den Upload vorzubereiten. 

> Sie haben Feedback zur oder Probleme bei der Nutzung der Desktop-Brücke? Die [UserVoice für Windows-Entwickler](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial)-Plattform ist der beste Ort für Featurevorschläge. Teilen Sie Fragen und Problemberichte bitte über die [Entwicklerforen für Universelle Windows-Apps](https://social.msdn.microsoft.com/Forums/home?forum=wpdevelop) mit.

## <a name="default-universal-windows-platform-packages"></a>Standardmäßige Pakete für die universelle Windows-Plattform

Mit Visual Studio können Sie Debug- und Veröffentlichungspakete generieren, die über den Windows Store oder per App-Querladen verteilt werden können. Im Rahmen der Paketerstellung unterstützt Sie Visual Studio beim Erstellen einer Appxupload-Datei, die dann an den Store übermittelt werden kann. Weitere Informationen finden Sie unter [Verpacken von UWP-Apps](..\packaging\packaging-uwp-apps.md).

## <a name="desktop-bridge-packages"></a>Desktop-Brücke-Pakete

Die [Desktop-Brücke](desktop-to-uwp-root.md) ermöglicht verschiedene Konfigurationen zur Integration von Win32-Binärdateien in ein Anwendungspaket (Appx). Die Nutzung der Desktop-Brücke umfasst vier grundsätzliche Schritte. 

- **Schritt 1 – Konvertieren**: Verpacken der vorhandenen Win32-Binärdateien ohne Codeändern oder mit minimalen Codeänderungen.
- **Schritt 2 – Optimieren**: Einbeziehen einiger grundlegender UWP-Features (z. B. eine Live-Kachel) in die vorhandene App mithilfe eines Verweises auf Windows.winmd über den vorhandenen Win32-Code.
- **Schritt 3 – Erweitern**: Einbeziehen von erweiterten UWP-Funktionalitäten (z. B. Hintergrundaufgaben) in die vorhandene App. Wenn Ihre UWP-Apps und Win32-Komponenten über verwalteten Sprachen (z. B. C# oder VB.Net) erstellt wurden, umfasst das erstellte Paket gemischte Binärdateien, die zur Gewährleistung der korrekten .NET Native Verarbeitung sorgfältig verarbeitet werden müssen. 
- **Schritt 4 – Migrieren**: Sie haben die Benutzeroberfläche zu XAML und C#/VB.NET migriert. Es ist jedoch noch immer älterer Win32-Code vorhanden. Der Einstiegspunkt ist nun eine ausführbare UWP-.NET-Dateien. Es gibt im Paket jedoch noch immer Binärdateien, die Win32-APIs verwenden.

In der folgenden Tabelle werden einige der Veränderungen Ihre App in den vier Schritten aufgeführt. 

| Schritt | Binärdateien | EntryPoint | .NET Native | F5-Debuggen |
|---|---|---|---|---|
| 1 (Konvertieren) | Win32 | Win32 | N/V | VS-Erweiterung |
| 2 (Optimieren) | Verweis auf WinMD | Win32 | N/V | VS-Erweiterung |
| 3 (Erweitern) | Win32 + CoreCLR (*) | Win32 | Durch Benutzer (**) | VS-Erweiterung |
| 4 (Migrieren)    | CoreCLR (*) + Win32 | UWP | Durch Benutzer (**) | VS |
| 5 (UWP) | CoreCLR | UWP |Durch Store | VS |

(*) [CoreCLR](https://github.com/dotnet/coreclr) verweist auf die für in einer verwalteten Sprache (C# / VB.NET) geschriebenen UWP-Komponenten erforderliche .NET Core-Laufzeitumgebung. Diese Komponenten erfordern außerdem die .NET Native-Verarbeitung.

(**) In Schritt 3 und 4 muss der Benutzer die CoreCLR-Assemblys verarbeiten, um die.NET Native-Binärdateien und die entsprechenden Symbole vor der Veröffentlichung im Store zu erstellen.

## <a name="configure-your-visual-studio-solution"></a>Konfigurieren der Visual Studio-Lösung

Visual Studio umfasst die zur Konfiguration des Anwendungspaktes erforderlichen Tools (beispielsweise den Manifest-Editor und den Assistenten zum Erstellen von Paketen). Um diese Tools verwenden zu können, benötigen Sie ein UWP-Projekt. Dieses fungiert als Appx-Container für die App. Sie können jedes UWP-Projekt verwenden (einschließlich C#, VB.NET, C++ oder JavaScript). Es gibt jedoch einige bekannte Probleme mit C#, VB.NET und C++ Projekten (weitere Informationen hierzu im Abschnitt [Bekannte Probleme](#known-issues-anchor) weiter unten in diesem Dokument). Daher verwenden wir für dieses Beispiel JavaScript. 

Wenn Sie Ihre App im Kontext des Appx-Anwendungsmodells debuggen möchten, müssen Sie ein weiteres Projekts hinzufügen, mit dem das F5-Appx-Debuggen möglich ist. Weitere Informationen finden Sie im Abschnitt [Debuggen Ihrer Desktop-Brücke App](#debugging-anchor).

Beginnen wir mit Schritt 1.

### <a name="step-1-convert"></a>Schritt 1: Konvertieren

Dieser Schritt veranschaulicht, wie Sie eine Desktop-Brücke-App aus einem vorhandenen Win32-Projekt erstellen. In diesem Beispiel verwenden wir ein einfaches WinForms-Projekt, das Lese- und Schreibvorgänge in der Registrierung durchführt.

![](images/desktop-to-uwp/net-1.png)

#### <a name="add-the-uwp-project"></a>Hinzufügen des UWP-Projekts 

Fügen Sie ein JavaScript-UWP-Projekt zur Lösung hinzu, um das Desktop-Brücke-Paket zu erstellen.

> Hinweis: Wir verwenden zwar eine JavaScript-UWP-Vorlage, werden jedoch keinen JavaScript-Code schreiben. Das nutzen das Projekt nur als Hilfsmittel.

![](images/desktop-to-uwp/net-2.png)

#### <a name="add-the-win32-binaries-to-the-win32-folder"></a>Hinzufügen von Win32-Binärdateien zum Win32-Ordner

Alle Win32-Binärdateien in Ihrem UWP-Projekt werden in einem Ordner namens win32 gespeichert (der Name ist jedoch nicht vorgeschrieben und kann beliebig gewählt werden).

Wenn Sie Visual Studio verwenden, können Sie das Projekt für das Kopieren der Dateien nach jeder Erstellung automatisieren und so den Entwicklungsworkflow optimieren. Um ein AfterBuild-Ziel einzufügen, dass alle Win32-Ausgabedateien in die Win32-Ordner des UWP-Projekts kopiert, bearbeiten Sie Ihre Projektdatei (in diesem Beispiel .csproj) wie folgt: 

```xml
  <Target Name="AfterBuild">
    <PropertyGroup>
      <TargetUWP>..\MyDesktopApp.Package\win32\</TargetUWP>
    </PropertyGroup>
     <ItemGroup>
       <Win32Binaries Include="$(TargetDir)\*" />
     </ItemGroup>
    <Copy SourceFiles="@(Win32Binaries)" DestinationFolder="$(TargetUWP)" />
  </Target>
```

Wenn Sie ein anderes Tool zur Erstellung der Win32-Binärdateien verwenden, kopieren Sie einfach alle erforderlichen Dateien zur Laufzeit in den win32-Ordner. 

#### <a name="edit-the-app-manifest-to-enable-the-desktop-bridge-extensions"></a>Bearbeiten des App-Manifests zur Aktivierung von Desktop-Brücke Erweiterungen

Die Vorlage enthält ein package.appxmanifest, das Sie zum Hinzufügen von Desktop-Brücke Erweiterungen verwenden können. Um diese Datei zu bearbeiten, klicken Sie mit der rechten Maustaste, und wählen Sie "Code anzeigen". Fügen Sie dann die folgenden Elemente ein oder bearbeiten Sie diese: 

- `<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10" xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities" IgnorableNamespaces="uap rescap">`

- `<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.0" MaxVersionTested="10.0.14393.0" />`

- `<rescap:Capability Name="runFullTrust" />`

- `<Application Id="MyDesktopAppStep1" Executable="win32\MyDesktopApp.exe" EntryPoint="Windows.FullTrustApplication">`

Hier ist ein vollständiges Beispiel der Manifestdatei: 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
        xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"

        xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
        xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
        IgnorableNamespaces="uap rescap mp">
  <Identity Name="MyDesktopAppStep1"
            ProcessorArchitecture="x64"
            Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
            Version="1.0.0.5" />
  <mp:PhoneIdentity PhoneProductId="6f6600a4-6da1-4d91-b493-35808d01f8de" PhonePublisherId="00000000-0000-0000-0000-000000000000" />
  <Properties>
    <DisplayName>MyDesktopAppStep1</DisplayName>
    <PublisherDisplayName>CN=Test</PublisherDisplayName>
    <Logo>Assets\SampleAppx.150x150.png</Logo>
  </Properties>
  <Resources>
    <Resource Language="en-us" />
  </Resources>
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Desktop" 
                        MinVersion="10.0.14393.0" 
                        MaxVersionTested="10.0.14393.0" />
  </Dependencies>
  <Capabilities>
    <rescap:Capability Name="runFullTrust" />
  </Capabilities>
  <Applications>
    <Application Id="MyDesktopAppStep1" 
                 Executable="win32\MyDesktopApp.exe" 
                 EntryPoint="Windows.FullTrustApplication">
      <uap:VisualElements DisplayName="MyDesktopAppStep1" 
                          Description="MyDesktopAppStep1" 
                          BackgroundColor="#777777" 
                          Square150x150Logo="Assets\SampleAppx.150x150.png" 
                          Square44x44Logo="Assets\SampleAppx.44x44.png">
      </uap:VisualElements>
    </Application>
  </Applications>
</Package>
```

#### <a name="configure-the-win32-binaries"></a>Konfigurieren der Win32-Binärdateien

Um die für die App erforderlichen Binärdateien in das Ausgabepaket einzubeziehen, wählen Sie alle Dateien in Visual Studio aus. Legen Sie die Eigenschaften auf "Inhalt" fest, und das Buildverhalten auf "Kopieren, wenn neuer". 

![](images/desktop-to-uwp/net-3.png)

Wenn Sie den Commit der Binärdateien für Ihr Quellcode-Repository vermeiden möchten, können Sie die Datei .gitignore nutzen, um die Dateien im Ordner win32 auszuschließen. 

#### <a name="optional-use-wildcards-to-specify-the-files-in-your-win32-folder"></a>Optional: Verwenden Sie Platzhalter, um die Dateien im Ordner win32 angeben.

Wenn die Win32-App mehrere Dateien benötigt, können Sie in der Projektdatei mit Platzhaltern festlegen, welche Dateien als "Inhalt" gekennzeichnet werden sollen. Sie müssen die Datei . jsproj mit einem Texteditor öffnen und die benötigten Dateien wie unten dargestellt einfügen.

```xml
<Content Include="win32\*.dll">
  <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
</Content>
<Content Include="win32\*.exe">
  <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
</Content>
<Content Include="win32\*.config">
  <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
</Content>
<Content Include="win32\*.pdb">
  <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
</Content>
```

### <a name="step-2-enhance"></a>Schritt 2: Optimieren

Wenn Sie die UWP-APIs über Ihren Win32-Code aufrufen möchten, müssen Sie einen Verweis auf `\Program Files (x86)\Windows Kits\10\UnionMetadata\Windows.winmd` hinzufügen. Die vollständige Liste der UWP-APIs für die App ist im Artikel [Unterstützte UWP-APIs für Apps, die mit der Desktop-Brücke konvertiert wurden](desktop-to-uwp-supported-api.md) zu finden.  

Da diese Datei unter Windows 10 nicht erforderlich ist, müssen Sie sie nicht verteilen. Legen Sie in den Verweiseigenschaften die Eigenschaft "Lokal kopieren" auf "Falsch" fest.

![](images/desktop-to-uwp/net-4.png)

Wenn die Win32-Binärdateien hinzufügen möchten, verwenden Sie die gleichen Abläufe wie in Schritt 1. 

### <a name="step-3-extend"></a>Schritt 3: Erweitern 

In diesem Beispiel werden wir eine Win32-App um eine Hintergrundaufgabe erweitern. Dies erfordert das Registrieren der Hintergrundaufgabe im package.appxmanifest der UWP-App. Außerdem müssen Sie einen Verweis auf das Projekt hinzufügen, das der Hintergrundaufgabe implementiert (siehe unten).

```xml
<Extensions>
  <Extension Category="windows.backgroundTasks" 
              EntryPoint="BackgroundTasks.MyBackgroundTask">
    <BackgroundTasks>
      <Task Type="timer" />
    </BackgroundTasks>
  </Extension>
</Extensions>
```

Wenn die Hintergrundaufgabe in C# oder VB.NET implementiert ist, enthält die Ausgabe CoreCLR-Binärdateien, die vor der Übermittlung an den Store durch die .NET Native-Tools verarbeitet werden müssen (wie in Schritt 3 und 4, "Erstellen von Appxupload mit gemischten Binärdateien", beschrieben).

### <a name="step-4-migrate"></a>Schritt 4: Migrieren

In diesem Szenario ist bereits ein C#-UWP-Einstiegspunkt vorhanden. Daher muss kein weiteres UWP-Projekt hinzugefügt werden. Sie müssen allerdings die Aktivitäten aus Schritt 1 durchführen, um die Win32-Binärdateien einzubeziehen und zu konfigurieren.

Verwenden Sie die [**FullTrustProcessLauncher**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.FullTrustProcessLauncher)-APIs, um den Win32-Prozess auszuführen. Sie müssen die Desktop-Erweiterung und die *FullTrustProcess*-Funktionalität zum Manifest der App hinzufügen, um die APIs wie folgt nutzen zu können: 

```xml
..
xmlns:desktop=http://schemas.microsoft.com/appx/manifest/desktop/windows10
..
<desktop:Extension Category="windows.fullTrustProcess" 
                    Executable="win32\MyDesktopApp.exe" />
```

## <a name="generate-packages-for-your-desktop-bridge-app"></a>Generieren von Paketen für die Desktop-Brücke-App

Nachdem Sie die oben genannten Schritte ausgeführt haben, sollten Sie Ihre Pakete mit Visual Studio wie in [Verpacken von UWP-Apps](..\packaging\packaging-uwp-apps.md) beschrieben generieren können. 

### <a name="steps-1-and-2-create-appxupload-with-win32-binaries"></a>Schritt 1 und 2: Erstellen von Appxupload mit Win32-Binärdateien

Um Paketen mit der *FullTrust*-Funktionalität übermitteln zu können, müssen Sie eine Appxupload-Datei generieren, die die Symbole für jede Plattform in einer Appxsym-Datei und ein Paket mit den Plattform Appx-Paketen enthält.

In den Schritten 1 und 2 enthält das Paket keine CoreCLR-Binärdateien. Daher müssen Sie sich nicht um die Auswahl der Plattform kümmern. Wählen Sie "Neutral" und "Release (alle CPUs)", wie in der folgenden Abbildung dargestellt.

![](images/desktop-to-uwp/net-5.png)

Nachdem Sie die Option "Store-Pakete generieren" ausgewählt haben, generiert der Assistent die Appxupload-Datei, die an den Store übermittelt werden kann.

### <a name="step-3-and-4-create-appxupload-with-mixed-binaries"></a>Schritt 3 und 4: Erstellen von Appxupload mit gemischte Binärdateien

Sie sollten auch eine Releaseversion erstellen. In diesem Fall ist es notwendig, die Zielplattformen anzugeben. .NET Native benötigt diese Informationen zur Erstellung der nativen Binärdateien für die einzelnen Plattformen.

![](images/desktop-to-uwp/net-6.png)

Um die neue Appxupload-Datei zu erstellen, erstellen wir ein neues Zip-Archiv. In dieses nehmen wir die generierten Appxsym und Appxbundle aus dem Ordner "_Test" auf.

Erstellen Sie eine neue Zip-Datei, die die Dateien Appxsym und Appxbundle enthält, und ändern Sie die Dateierweiterung in Appxupload.

![](images/desktop-to-uwp/net-7.png)

<span id="debugging-anchor" />
## <a name="debugging-your-desktop-bridge-app"></a>Debuggen der Desktop-Brücke-App

Auch wenn Sie Ihre Projekte in Visual Studio ohne Debuggen (STRG+F5) beginnen können, gibt es ein bekanntes Problem, durch das Visual Studio sich nicht einfach in laufenden Prozesse einhängen kann. Sie können jedoch das Einhängen jedoch später über eine der folgenden Methoden durchführen:

### <a name="attach-to-the-running-app"></a>Einhängen in eine laufende App

#### <a name="attach-to-an-existing-process"></a>Einhängen in einen vorhandene Prozess

Nachdem Sie die App mit STRG+F5 erfolgreich gestartet haben, können Sie sich in den Win32-Prozess einhängen. Sie können jedoch kein Debugging für .NET Native-Module durchführen. 

![](images/desktop-to-uwp/net-8.png)

#### <a name="attach-to-an-installed-app"></a>Einhängen in eine installierte App

Sie können sich auch in eine vorhandenes Appx-Paket einhängen. Verwenden Sie hierzu die Option Debuggen -> Andere Debugziele -> Installiertes App-Paket debuggen.

![](images/desktop-to-uwp/net-9.png)

Dort können Sie den lokalen Computer oder einen Remotecomputer auswählen.

![](images/desktop-to-uwp/net-10.png)

Mit dieser Option sollten Sie in der Lage sein, .NET Native-Code zu debuggen.

### <a name="use-visual-studio-extension-to-debug-your-desktop-bridge-app"></a>Verwenden der Visual Studio-Erweiterung zum Debuggen der Desktop-Brücke-App 

Wenn Sie die App über F5 debuggen möchten, müssen Sie die Visual Studio 2017-Erweiterung [Desktop Bridge Debugging Project](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.DesktoptoUWPPackagingProject) aus der Visual Studio Gallery installieren

Mit diesem Projekt können Sie eine Win32-App debuggen, die mit Visual Studio (wie in diesem Dokument beschrieben) oder über den Desktop App Converter zu UWP migriert wird.

#### <a name="add-the-debugging-project-to-your-solution"></a>Hinzufügen des Debuggen Projekts zur Lösung

Fügen Sie zunächst in der Lösung ein neues Desktop-Brücke-Debugging-Projekt zu Ihrem Projekt hinzu.

![](images/desktop-to-uwp/net-11.png)

Um dieses Projekt zu konfigurieren, müssen Sie die Eigenschaft PackageLayout im Eigenschaftenfenster jeder zu debuggenden Konfiguration/Plattform definieren.
Für Debug/x86 legen wir die Paketlayouteigenschaft auf den Ordner bin\x86\debug des UWP-Projekts fest (mit einem relativen Pfad): `..\MyDesktopApp.Package\bin\x86\Debug`. 

![](images/desktop-to-uwp/net-12.png)

Dann bearbeiten wir die Datei AppXFileLayout.xml, um den Einstiegspunkt anzugeben:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" 
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <MyProjectOutputPath>$(PackageLayout)</MyProjectOutputPath>
  </PropertyGroup>
  <ItemGroup>
    <LayoutFile Include="$(MyProjectOutputPath)\win32\MyDesktopApp.exe">
      <PackagePath>$(PackageLayout)\win32\MyDesktopApp.exe</PackagePath>
    </LayoutFile>
  </ItemGroup>
</Project>
```

Schließlich konfigurieren Sie die Abhängigkeiten der Lösung. So stellen Sie sicher, dass die Projekte in der richtigen Reihenfolge erstellt werden. 

Sehen wir uns als Beispiel die in Schritt 3 erstellte Lösung an.

![](images/desktop-to-uwp/net-13.png)

Um die Buildreihenfolge zu konfigurieren, können Sie die Projektabhängigkeiten-Konfiguration verwenden. Klicken Sie mit der rechten Maustaste auf die Lösung, und wählen Sie die Option "Projektabhängigkeiten" aus. Nachdem Sie die richtigen Abhängigkeiten festgelegt haben, können Sie die Buildreihenfolge überprüfen (siehe unten für Schritt 3):

![](images/desktop-to-uwp/net-14.png)

<span id="known-issues-anchor" />
## <a name="known-issues-with-cvbnet-and-c-uwp-projects"></a>Bekannte Probleme mit C#/VB.NET und C++ UWP-Projekten

Wenn Sie ein C#-Projekt zum Verpacken der App verwenden möchten, müssen Sie die folgenden bekannten Probleme berücksichtigen. 

- **Das Erstellen der App im Debugmodus führt zum Fehler: Microsoft.Net.CoreRuntime.targets(235,5): Fehler: Anwendungen mit benutzerdefinierten Einstiegspunkten für ausführbare Dateien werden nicht unterstützt. Überprüfen Sie das Attribut "Executable" im Application-Elements des Paketmanifests.** Verwenden Sie zur Umgehung des Problems den Releasemodus.

- **Im Stammordner des UWP-Projekts gespeichert gespeicherte Win32-Binärdateien werden in der Relaseversion entfernt**. Wenn Sie keinen Ordner zur Speicherung der Win32-Binärdateien verwenden, entfernt der .NET Native-Compiler diese aus dem fertigen Paket. Dies führt zu einem Manifest-Validierungsfehler, da der Einstiegspunkt für die ausführbare Datei nicht gefunden werden kann.


