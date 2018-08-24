---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben von Problemen, die verhindern, dass der Desktopanwendung in einem MSIX-Container ausgeführt wird
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2841362"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a>Anwenden von Runtime Updates zu einem Paket MSIX mithilfe des Paket-Support-Frameworks

Das Paket Support-Framework ist ein open-Source-Kit, die Dank gelten Korrekturen für Ihre vorhandene Win32-Anwendung, wenn Sie nicht über Zugriff auf den Quellcode verfügen, damit es in einem MSIX-Container ausgeführt werden kann. Das Paket Unterstützung Framework hilft bei der Anwendung führen Sie die bewährten Methoden der moderne Runtime-Umgebung.

Um die Support-Framework-Paket zu erstellen, nutzten wir die [abweichen müssen](https://www.microsoft.com/en-us/research/project/detours) -Technologie wird eine open-Source-Framework von Microsoft Research (MSR) entwickelt und unterstützt die API-Umleitung und Integrieren von.

Dieses Frameworks ist leicht, open Source und können Sie sie zum Beheben von Anwendungsproblemen schnell. Darüber hinaus haben Sie die Möglichkeit, mit der Community auf der ganzen Welt zu konsultieren, und klicken Sie auf der Basis der Investitionen in der anderen Teilnehmer zu erstellen.

## <a name="a-quick-look-inside-of-the-package-support-framework"></a>Ein kurzer Blick in dem Paket Support-Framework

Das Paket Support-Framework enthält eine ausführbare Datei, eine Laufzeit-Manager DLL-Datei und eine Reihe von Common Language Runtime-Updates.

![Paket-Support-Framework](images/desktop-to-uwp/package-support-framework.png)

So funktioniert’s. Sie erstellen eine Konfigurationsdatei, die die Fix(s) angibt, die Sie für Ihre Anwendung anwenden möchten. Anschließend können Sie Ihr Paket So zeigen Sie auf die ausführbare Datei aus Shim Launcher ändern.

Wenn Benutzer die Anwendung starten, wird das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird. Liest die Konfigurationsdatei, und fügt die Laufzeit Fix(s) und den Laufzeit-Manager DLL in den Anwendungsprozess.

![Paket Unterstützung Framework-DLL Einfügung](images/desktop-to-uwp/package-support-framework-2.png)

Der Runtime-Manager gilt die Korrektur bei Bedarf die Anwendung ein MSIX Container ausgeführt.

Dieses Handbuch hilft Ihnen, um Probleme mit der Anwendungskompatibilität zu identifizieren, und um finden, anwenden und Erweitern von Common Language Runtime behebt, die deren Behebung.

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a>Identifizieren von Anwendungspaket Kompatibilitätsprobleme

Erstellen Sie zunächst ein Paket für Ihre Anwendung. Installieren Sie es anschließend und beobachten Sie, führen Sie es. Sie erhalten Fehlermeldungen, die ein Kompatibilitätsproblem erleichtern. Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu identifizieren.  Häufige Probleme beziehen sich auf die Anwendung Annahmen bezüglich der Berechtigungen Working Directory und Programmdateien Pfad.

### <a name="using-process-monitor-to-identify-an-issue"></a>Verwenden zum Identifizieren eines Problems Process Monitor

[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm für eine app-Datei und Registrierung Vorgänge und deren Ergebnisse beobachten.  Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.  Nach dem Öffnen Process Monitor, fügen Sie einen Filter (Filter > Filter...), gibt es nur Ereignisse aus der ausführbaren Datei der Anwendung.

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

Eine Liste der Ereignisse wird angezeigt. Für viele dieser Ereignisse wird das Wort in der Spalte **Ergebnis** **Erfolg** angezeigt.

![ProcMon Ereignisse](images/desktop-to-uwp/procmon_events.png)

Optional können Sie Ereignisse, um nur die nur Fehler anzeigen filtern.

![ProcMon ausschließen Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

Wenn Sie einen Fehler beim Filesystem-Zugriff auf annehmen, suchen Sie nach fehlerhafte Ereignisse, die unter der System32/SysWOW64 oder den Paketdateipfad sind. Filter können auch hier zu helfen. Starten Sie am Ende dieser Liste aus, und führen Sie einen Bildlauf nach oben. Fehler, die am Ende dieser Liste angezeigt werden, sind die zuletzt aufgetreten. Achten Sie die meisten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten und "Pfad/Name nicht gefunden", und ignorieren Sie Aufgaben, die nicht verdächtigen aussehen. Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme. Sie können diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt wird.

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

In der ersten Ausgabe, die in dieser Abbildung angezeigt wird, fällt aus die Anwendung zum Lesen aus der Datei "Config.txt", die sich im Pfad "C:\Windows\SysWOW64" befindet. Es ist unwahrscheinlich, dass die Anwendung versucht, auf diesen Pfad direkt zu verweisen. In den meisten Fällen versucht, mit der ein relativer Pfad aus dieser Datei gelesen und in der Standardeinstellung ist "System32/SysWOW64" Arbeitsverzeichnis der Anwendung. Dies impliziert, dass die Anwendung aktuellen Arbeitsverzeichnis irgendwo im Paket festgelegt werden soll, um erwartet. Suchen Sie in der Appx, sehen Sie, dass die Datei im gleichen Verzeichnis befindet wie die ausführbare Datei vorhanden ist.

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

In der folgenden Abbildung wird das zweite Problem angezeigt.

![ProcMon-Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

In dieser Ausgabe ist die Anwendung zum Schreiben einer log-Datei in den Paketpfad fehl. Dies würde empfehlen, dass ein Datei Umleitung Shim hilfreich sein kann.

<a id="find" />

## <a name="find-a-runtime-fix"></a>Suchen nach einer Lösung Common Language runtime

Die PSF enthält Runtime-Updates, die Sie sofort, wie die Datei Umleitung Shim verwenden können.

### <a name="file-redirection-shim"></a>Datei Umleitung Shim

Die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können Sie umleiten Versuche zum Schreiben oder Lesen von Daten in einem Verzeichnis, die von einer Anwendung zugänglich ist, die in einem MSIX-Container ausgeführt wird.

Beispielsweise, wenn die Anwendung in einer Protokolldatei, die im gleichen Verzeichnis befindet wie die ausführbare Anwendung ist schreibt, können klicken Sie dann die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie die Protokolldatei an einem anderen Standort, wie etwa dem Datenspeicher lokalen app erstellen.

### <a name="runtime-fixes-from-the-community"></a>Common Language Runtime Fixes aus der community

Stellen Sie sicher, dass Sie die Community-Beiträge zu unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) Seite zu überprüfen. Es ist möglich, dass andere Entwickler eine ähnliche und Ihrem Problem gelöst haben und ein Update Runtime freigegeben haben.

## <a name="apply-a-runtime-fix"></a>Anwenden eines Fixes Common Language runtime

Sie können einen vorhandene Runtime Fix mit ein paar einfache Tools aus dem Windows-SDK und folgende Schritte anwenden.

> [!div class="checklist"]
> * Erstellen Sie einen Paketordner layout
> * Die Paket Unterstützung Framework Dateien abrufen
> * Fügen sie dem Paket hinzu
> * Bearbeiten des Paketmanifests
> * Erstellen Sie eine Konfigurationsdatei

Nun über jede Aufgabe.

### <a name="create-the-package-layout-folder"></a>Erstellen Sie den Ordner Package layout

Wenn Sie bereits eine Datei .appx verfügen, können Sie den Inhalt in einem Ordner Layout entpacken, die als Bereitstellungsbereich für Ihr Paket dient.  Hierzu können Sie von einer **X64 systemeigenen Tools Command Prompt für VS 2017**, oder manuell mit den SDK-Bin-Pfad in den Suchpfad der ausführbaren.

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

Dadurch erhalten etwas Sie, die wie folgt aussieht.

![Paket-Layout](images/desktop-to-uwp/package_contents.png)

Wenn Sie keine .appx-Datei zu haben, können Sie die Package-Ordner und Dateien von Grund auf neu erstellen.

### <a name="get-the-package-support-framework-files"></a>Die Paket Unterstützung Framework Dateien abrufen

Sie können das PSF Nuget-Paket abrufen, indem Sie mithilfe von Visual Studio. Sie können auch darauf zuzugreifen, mithilfe des eigenständigen Nuget-Befehlszeilentools.

#### <a name="get-the-package-by-using-visual-studio"></a>Abrufen des Pakets mithilfe von Visual Studio

In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.  Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , um das Paket Nuget.org zu suchen. Klicken Sie dann, installieren Sie es.

#### <a name="get-the-package-by-using-the-command-line-tool"></a>Abrufen des Pakets mithilfe des Befehlszeilentools

Installieren Sie das Befehlszeilentool Nuget aus diesem Speicherort: https://www.nuget.org/downloads. Führen Sie dann über die Befehlszeile Nuget mit diesem Befehl ein:

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a>Dem Paket die Paket-Support-Framework-Dateien hinzufügen

Fügen Sie die erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbare Dateien in das Paketverzeichnis. Orientieren Sie sich an der folgenden Tabelle. Sie sollten auch alle Runtime Fixes enthalten, die Sie benötigen. In unserem Beispiel benötigen wir die Datei Umleitung Runtime Korrektur.

| Ausführbare Datei Anwendung ist x64 | Ausführbare Datei Anwendung ist x86 |
|-------------------------------|-----------|
| [ShimLauncher64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [ShimLauncher32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [ShimRuntime64.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [ShimRuntime32.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [ShimRunDll64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [ShimRunDll32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

Ihre Inhalte Paket sollte nun etwa wie folgt aussehen.

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a>Bearbeiten des Paketmanifests

Öffnen Sie Ihr Paketmanifest in einem Text-Editor, und legen Sie dann die `Executable` -Attribut des der `Application` Element auf den Namen der ausführbaren Datei Shim Launcher.  Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die entsprechende Version, ShimLauncher32.exe oder ShimLauncher64.exe.  Wenn dies nicht der Fall ist, ShimLauncher32.exe in allen Fällen verwendet werden.  Beispiel:

```xml
<Package ...>
  ...
  <Applications>
    <Application Id="PSFSample"
                 Executable="ShimLauncher32.exe"
                 EntryPoint="Windows.FullTrustApplication">
      ...
    </Application>
  </Applications>
</Package>
```

### <a name="create-a-configuration-file"></a>Erstellen Sie eine Konfigurationsdatei

Erstellen Sie einen Dateinamen ein ``config.json``, und speichern Sie diese Datei in den Stammordner Ihres Pakets. Ändern Sie die deklarierte app-ID der Datei config.json So zeigen Sie auf die ausführbare Datei, die Sie gerade ersetzt. Verwenden die Kenntnisse, die von der Verwendung von Process Monitor resultieren, können Sie auch Arbeitsverzeichnis festlegen sowie verwenden Sie das Datei Umleitung Shim zur Umleitung von Lese-/Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" Paket relativ.

```json
{
    "applications": [
        {
            "id": "PSFSample",
            "executable": "PSFSampleApp/PSFSample.exe",
            "workingDirectory": "PSFSampleApp/"
        }
    ],
    "processes": [
        {
            "executable": "PSFSample",
            "shims": [
                {
                    "dll": "FileRedirectionShim.dll",
                    "config": {
                        "redirectedPaths": {
                            "packageRelative": [
                                {
                                    "base": "PSFSampleApp/",
                                    "patterns": [
                                        ".*\\.log"
                                    ]
                                }
                            ]
                        }
                    }
                }
            ]
        }
    ]
}
```
Nachfolgend sehen Sie einen Leitfaden für das Schema config.json:

| Array | key | Wert |
|-------|-----------|-------|
| applications | id |  Verwenden Sie den Wert von der `Id` -Attribut des der `Application` -Element im Paketmanifest. |
| applications | ausführbare Datei | Die Paket-Relative Pfad der ausführbaren Datei, die Sie starten möchten. In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern. Es ist der Wert der `Executable` -Attribut des der `Application` Element. |
| applications | workingDirectory | (Optional) Ein Paket relativer Pfad als das Arbeitsverzeichnis der Anwendung verwenden, die beginnt. Wenn Sie diesen Wert nicht festlegen, das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare Datei | In den meisten Fällen wird dies der Name der werden die `executable` konfigurierten oberhalb der Pfad und Dateiname Erweiterung entfernt. |
| Shims | DLL-Datei | Paket-relativer Pfad zu der Shim .appx geladen werden. |
| Shims | config | (Optional) Steuert das Verhalten der Shim dl. Das genaue Format dieses Werts variiert für einzelne Shim-durch-Shim wie jedes Shim wie diesmal dieser "Blob" interpretiert werden kann. |

Die `applications`, `processes`, und `shims` Schlüssel Arrays sind. Dies bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozesse und Shim-DLL anzugeben.


### <a name="package-and-test-the-app"></a>Paket und Testen der App

Im nächsten Schritt erstellen Sie ein Paket.

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

Klicken Sie dann signieren.

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Pakets Signaturzertifikat](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [zum Signieren eines Pakets mithilfe von signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)

Mithilfe von PowerShell, um das Paket zu installieren.

>[!NOTE]
> Denken Sie daran, um das Paket zuerst zu deinstallieren.

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

Führen Sie die Anwendung, und beobachten Sie das Verhalten mit Runtime Fix angewendet.  Wiederholen Sie die Diagnose und Verpackung Schritte nach Bedarf.

### <a name="use-the-trace-shim"></a>Verwenden Sie das Trace-Shim

Ein alternatives Verfahren zum Diagnose von Kompatibilitätsproblemen Anwendungspaket ist die Verwendung der Trace-Shim. Diese DLL gehört zum Lieferumfang der PSF und bietet eine detaillierte Ansicht der app-Verhalten, ähnlich wie Process Monitor diagnostische.  Es wurde speziell entwickelt, um Probleme mit der Anwendungskompatibilität anzuzeigen.  Verwenden Sie die Trace-Shim, die DLL des Pakets hinzufügen hinzufügen das folgende Fragment zu Ihrer config.json und gepackt und installieren Sie die Anwendung.

```json
{
    "dll": "TraceShim.dll",
    "config": {
        "traceLevels": {
            "filesystem": "allFailures"
        }
    }
}
```

Standardmäßig filtert die Trace-Shim Fehlern, die möglicherweise berücksichtigt werden "erwartet".  Beispielsweise Versuch Applications uneingeschränkt Löschen einer Datei ohne zu überprüfen, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert. Die unerwünschten Folgen, die einige unerwarteter Fehler herausgefiltert, abrufen können hat damit im obigen Beispiel wir aufzuheben, um alle Fehler von Filesystem Funktionen empfangen Dies erfolgt, da wir vor, denen der Versuch zum Lesen aus der Datei Config.txt mit "der Nachricht Datei wurde nicht gefunden" fehlschlägt, wissen aus. Hierbei handelt es sich um einen Fehler, der häufig beachtet wird und nicht in der Regel davon ausgegangen, dass unerwartete sein. In der Praxis ist es wahrscheinlich am besten, anfangs nur für unerwarteter Fehler filtern, und klicken Sie dann zurückgreifen auf alle Fehler liegt ein Problem, das noch nicht ermittelt werden kann.

Standardmäßig ruft die Ausgabe vom Shim Trace an den angefügten Debugger gesendet. In diesem Beispiel wir sind nicht auf Debuggen und werden das Programm [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals stattdessen verwenden, um die Ausgabe anzuzeigen. Nach dem Ausführen der app, können wir die gleichen Fehler wie zuvor finden Sie unter dem würden uns verweist die gleichen Runtime Updates zeigen.

![TraceShim Datei wurde nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a>Debuggen Sie, erweitern Sie oder erstellen Sie ein Update der Common Language runtime

Visual Studio können Sie das Debuggen eines Fixes Runtime, erweitern ein Update Runtime oder ein neues erstellen. Sie müssen diese Schritte erfolgreich ausgeführt werden.

> [!div class="checklist"]
> * Fügen Sie ein packprojekt
> * Fügen Sie für die Korrektur Runtime Projekt hinzu
> * Fügen Sie ein Projekt aus, die Shim-Startprogramms beginnt
> * Konfigurieren Sie das packprojekt

Wenn Sie fertig sind, wird Ihre Lösung wie folgt aussehen.

![Abgeschlossene Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

In diesem Beispiel wird jedes Projekt betrachten.

| Projekt | Zweck |
|-------|-----------|
| DesktopApplicationPackage | Dieses Projekt wird basierend auf der [Windows-Anwendungspakete Project](desktop-to-uwp-packaging-dot-net.md) , und es gibt die MSIX-Paket. |
| Runtimefix | Dies ist ein C++ Dynamic-Linked Bibliotheksprojekt, die eine oder mehrere Replacement-Funktionen enthält, die als die Laufzeit Korrektur dienen. |
| ShimLauncher | Dies ist eine leere C++-Projekt. Dieses Projekt ist ein Ort für die Laufzeit verteilbare Dateien von Framework-Support-Paket zu sammeln. Es gibt eine ausführbare Datei aus. Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe starten. |
| WinFormsDesktopApplication | Dieses Projekt enthält den Quellcode der desktop-Anwendung. |

Um ein vollständiges Beispiel betrachten, die alle der folgenden Typen von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).

Lassen Sie uns die Schritte zum Erstellen und konfigurieren Sie jeden dieser Projekte in der Projektmappe durchgehen.


### <a name="create-a-package-solution"></a>Erstellen einer Lösung Paket

Wenn Sie bereits eine Lösung für desktop-Anwendung ist, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

Sie möchten möglicherweise auch alle Anwendungsprojekte hinzufügen, die Ihnen.

### <a name="add-a-packaging-project"></a>Fügen Sie ein packprojekt

Wenn Sie bereits ein **Windows-Anwendungsprojekt Verpackung**ist, erstellen Sie eine und Ihrer Lösung hinzugefügt.

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

Weitere Informationen zu Windows-Anwendung packprojekt finden Sie unter [Package Ihrer Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).

Im **Projektmappen-Explorer**mit der rechten Maustaste in des Projekts Verpacken, wählen Sie **Bearbeiten**, und klicken Sie dann am Ende der Projektdatei hinzufügen:

```
<Target Name="PSFRemoveSourceProject" AfterTargets="ExpandProjectReferences" BeforeTargets="_ConvertItems">
<ItemGroup>
  <FilteredNonWapProjProjectOutput Include="@(_FilteredNonWapProjProjectOutput)">
  <SourceProject Condition="'%(_FilteredNonWapProjProjectOutput.SourceProject)'=='<your runtime fix project name goes here>'" />
  </FilteredNonWapProjProjectOutput>
  <_FilteredNonWapProjProjectOutput Remove="@(_FilteredNonWapProjProjectOutput)" />
  <_FilteredNonWapProjProjectOutput Include="@(FilteredNonWapProjProjectOutput)" />
</ItemGroup>
</Target>
```

### <a name="add-project-for-the-runtime-fix"></a>Fügen Sie für die Korrektur Runtime Projekt hinzu

Fügen Sie ein Projekt C++ **Dynamic-Link Library (DLL)** , zu der Lösung an.

![Fix-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

Mit der rechten Maustaste die, project, und wählen Sie dann auf **Eigenschaften**.

In die Eigenschaftenseiten, suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld der **ISO C ++ 17-Standard (/ Std:c ++ 17)** Option.

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

Maustaste auf das Projekt, und wählen Sie dann im Kontextmenü die Option **Manage Nuget Packages** . Stellen Sie sicher, dass die Option **Paketquelle** auf **Alle** oder **nuget.org**festgelegt ist.

Klicken Sie auf dem einstellungssymbol weiter dieses Feld.

Suchen Sie nach der *PSF** Nuget-Paket, und installieren Sie sie für dieses Projekt.

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

Wenn Sie Debuggen oder beim Erweitern eines vorhandenen Runtime Fix möchten, fügen Sie die Common Language Runtime Fix-Dateien, die Sie mithilfe der Anleitung beschriebenen im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs abgerufen.

Wenn Sie eine völlig neue Lösung erstellen möchten, fügen Sie nicht Suchzeichenfolge diesem Projekt noch hinzu. Wir helfen Ihnen, die richtigen Dateien in diesem Projekt weiter unten in diesem Handbuch hinzuzufügen. Jetzt werden wir Einrichten Ihrer Lösung fortzufahren.

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a>Fügen Sie ein Projekt aus, die Shim-Startprogramms beginnt

Fügen Sie ein Projekt C++ **Leeres Projekt** , zu der Lösung an.

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

Hinzufügen des **PSF** Nuget-Pakets diesem Projekt mit den gleichen Leitfäden, die im vorherigen Abschnitt beschrieben.

Öffnen die Eigenschaftenseiten für das Projekt, und klicken Sie auf der Seite **Allgemein** Einstellungen legen Sie die **Ziel-Name** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` je nach der Architektur der Anwendung.

![Shim Launcher Verweis](images/desktop-to-uwp/shim-exe-reference.png)

Fügen Sie einen Projektverweis auf das Projekt Common Language Runtime Fix in Ihrer Lösung hinzu.

![Common Language Runtime Fix-Verweis](images/desktop-to-uwp/reference-fix.png)

Mit der rechten Maustaste in des Verweis, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.

| Eigenschaft | Wert |
|-------|-----------|-------|
| Kopieren der lokalen | Wahr |
| Lokale Satellitenassemblys kopieren | Wahr |
| Referenz-Assembly-Ausgabe | Wahr |
| Link Library Abhängigkeiten | False |
| Link Library Abhängigkeit Eingaben | False |

### <a name="configure-the-packaging-project"></a>Konfigurieren Sie das packprojekt

Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

Wählen Sie das Shim-Projekt Launcher und Ihrem desktop-Anwendung-Projekt, und wählen Sie dann auf die Schaltfläche **OK** .

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> Wenn Sie den Quellcode für die Anwendung ist, wählen Sie nur das Shim Startprogramm-Projekt. Wir können Ihnen zeigen, wie auf die EXE-Datei zu verweisen, wenn Sie eine Konfigurationsdatei erstellen.

In den Knoten **Applications** Maustaste auf das Startprogramm für die Shim und wählen Sie dann auf **als Einstiegspunkt festgelegt**.

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

Hinzufügen einer Datei mit dem Namen ``config.json`` Sie Ihrem packprojekt Sie dann kopieren und fügen Sie den folgenden Json-Text in die Datei. Legen Sie die **Paket-Action** -Eigenschaft auf **Inhalt**.

```json
{
    "applications": [
        {
            "id": "",
            "executable": "",
            "workingDirectory": ""
        }
    ],
    "processes": [
        {
            "executable": "",
            "shims": [
                {
                    "dll": "",
                    "config": {
                    }
                }
            ]
        }
    ]
}
```
Geben Sie einen Wert für jeden Schlüssel ein. Verwenden Sie die folgende Tabelle als Leitfaden.

| Array | key | Wert |
|-------|-----------|-------|
| applications | id |  Verwenden Sie den Wert von der `Id` -Attribut des der `Application` -Element im Paketmanifest. |
| applications | ausführbare Datei | Die Paket-Relative Pfad der ausführbaren Datei, die Sie starten möchten. In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern. Es ist der Wert der `Executable` -Attribut des der `Application` Element. |
| applications | workingDirectory | (Optional) Ein Paket relativer Pfad als das Arbeitsverzeichnis der Anwendung verwenden, die beginnt. Wenn Sie diesen Wert nicht festlegen, das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare Datei | In den meisten Fällen wird dies der Name der werden die `executable` konfigurierten oberhalb der Pfad und Dateiname Erweiterung entfernt. |
| Shims | DLL-Datei | Paket-relativer Pfad zu der Shim-DLL geladen werden. |
| Shims | config | (Optional) Steuert das Verhalten der Shim dl. Das genaue Format dieses Werts variiert für einzelne Shim-durch-Shim wie jedes Shim wie diesmal dieser "Blob" interpretiert werden kann. |

Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt.

```json
{
  "applications": [
    {
      "id": "DesktopApplication",
      "executable": "DesktopApplication/WinFormsDesktopApplication.exe",
      "workingDirectory": "WinFormsDesktopApplication"
    }
  ],
  "processes": [
    {
      "executable": ".*App.*",
      "shims": [ { "dll": "RuntimeFix.dll" } ]
    }
  ]
}

```

>[!NOTE]
> Die `applications`, `processes`, und `shims` Schlüssel Arrays sind. Dies bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozesse und Shim-DLL anzugeben.

### <a name="debug-a-runtime-fix"></a>Debuggen eines Fixes Common Language runtime

Drücken Sie F5, um den Debugger starten Sie in Visual Studio.  Als erstes, die beginnt ist die Shim-Start-Anwendung, die wiederum die Ziel-desktop-Anwendung gestartet wird.  Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell an den Prozess desktop-Anwendung anfügen, indem Sie auf **Debuggen**->**an den Prozess anhängen**, auswählen und dann auf den Anwendungsprozess. Um das Debuggen einer Anwendung .NET mit einer einheitlichen Runtime Fix DLL zu ermöglichen, wählen Sie verwaltete und systemeigenem Code (Debuggen im gemischten Modus).  

Nachdem Sie diese eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und die Laufzeit Fix-Projekt festlegen. Wenn Sie den Quellcode für die Anwendung ist, können Sie Haltepunkte nur neben Codezeilen im Projekt Common Language Runtime Fix festgelegt sein.

>[!NOTE]
> Während der Visual Studio können Sie die einfachste Entwicklung und Debuggen, sind einige Einschränkungen, also weiter unten in diesem Handbuch besprechen andere Debuggingverfahren wir, die Sie anwenden können.

## <a name="create-a-runtime-fix"></a>Erstellen Sie ein Update der Common Language runtime

Wenn es keine noch eine Laufzeit für das Problem beheben, dass Sie beheben möchten, können Sie eine neue Laufzeit Fix durch Schreiben Replacement-Funktionen und alle Konfigurationsdaten einschließlich erstellen sinnvoll, die zurückgegeben. Betrachten Sie jeden Teil.

### <a name="replacement-functions"></a>Ersatzfunktionen

Bestimmen Sie zunächst, welche Funktion Aufrufe schlagen fehl, wenn die Anwendung in einem Container MSIX ausgeführt wird. Anschließend können Sie Replacement-Funktionen erstellen, die Sie den Laufzeit-Manager stattdessen aufrufen möchten. Dies gibt Ihnen eine Gelegenheit, ersetzen Sie die Implementierung einer Funktion mit Verhalten, das die Regeln für die moderne Laufzeitumgebung entspricht.

Öffnen Sie in Visual Studio das Runtime Fix-Projekt, das Sie weiter oben in diesem Handbuch erstellt haben.

Deklarieren der ``SHIM_DEFINE_EXPORTS`` Makro, und fügen Sie eine Include-Anweisung für die `shim_framework.h` am oberen Rand jeder. CPP-Datei für die Funktionen der Common Language Runtime-Updates hinzufügen möchten.

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
>Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.

Erstellen Sie eine Funktion, die die gleiche Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten. Es folgt eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.

```c++
auto MessageBoxWImpl = &::MessageBoxW;
int WINAPI MessageBoxWShim(
    _In_opt_ HWND hwnd,
    _In_opt_ LPCWSTR,
    _In_opt_ LPCWSTR caption,
    _In_ UINT type)
{
    return MessageBoxWImpl(hwnd, L"SUCCESS: This worked", caption, type);
}

DECLARE_SHIM(MessageBoxWImpl, MessageBoxWShim);
```

Der Aufruf von `DECLARE_SHIM` ordnet die `MessageBoxW` Funktion, um Ihre neue Replacement-Funktion. Wenn die Anwendung versucht, rufen Sie die `MessageBoxW` -Funktion; er ruft die Replacement-Funktion stattdessen.

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a>Schutz vor rekursive Aufrufe von Funktionen in Common Language Runtime-Updates

Optional können Sie anwenden der `reentrancy_guard` Typ auf die Funktionen, die Schutz vor rekursive Aufrufe von Funktionen in Common Language Runtime-Updates.

Sie können beispielsweise eine Funktion Ersatz für erzeugen die `CreateFile` Funktion. Rufen Sie möglicherweise die Implementierung der `CopyFile` -Funktion, aber die Implementierung der der `CopyFile` Funktionsaufruf möglicherweise die `CreateFile` Funktion. Dies kann dazu führen, dass ein unendlichen rekursiven Lebenszyklus von Anrufen an die `CreateFile` Funktion.

Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)

### <a name="configuration-data"></a>Konfigurationsdaten

Wenn Sie Daten zur Konfiguration der Common Language Runtime Fix hinzufügen möchten, sollten Sie es zum Hinzufügen der ``config.json``. Auf diese Weise können die `ShimQueryCurrentDllConfig` , diese Daten auf einfache Weise zu analysieren. In diesem Beispiel wird analysiert einen Boolean und String-Wert aus dieser Konfigurationsdatei.

```c++
if (auto configRoot = ::ShimQueryCurrentDllConfig())
{
    auto& config = configRoot->as_object();

    if (auto enabledValue = config.try_get("enabled"))
    {
        g_enabled = enabledValue->as_boolean().get();
    }

    if (auto logPathValue = config.try_get("logPath"))
    {
        g_logPath = logPathValue->as_string().wstring();
    }
}
```

## <a name="other-debugging-techniques"></a>Andere Debuggingverfahren

Während der Visual Studio Sie die einfachste Entwicklung und Debuggen können, sind einige Einschränkungen.

F5-debugging führt Sie zuerst die Anwendung lose Dateien aus dem Paket Layout Ordnerpfad bereitstellen, anstatt aus einem Paket .appx installiert.  Der Layout-Ordner haben die gleiche sicherheitseinschränkungen als eine installierte Paketordner in der Regel nicht. Daher kann es nicht Paket Pfad Denial-Zugriffsfehlern vor dem Anwenden eines Fixes Runtime reproduziert werden.

Verwenden Sie zur Behebung dieses Problems .appx paketbereitstellung anstelle von F5 lose Datei-Bereitstellung.  Um eine .appx Package-Datei zu erstellen, verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK wie oben beschrieben. Oder, innerhalb von Visual Studio Maustaste auf den Projektknoten für die Anwendung und wählen **Store**->**App-Pakete zu erstellen**.

Ein weiteres Problem mit Visual Studio ist, dass sie nicht über integrierte Unterstützung zum Anfügen an untergeordnete Prozesse, die vom Debugger gestartet besitzt.   Dies erschwert das Debuggen von Geschäftslogik in Startpfad der Zielanwendung, die nach der Einführung von Visual Studio manuell angefügt werden muss.

Um dieses Problem zu beheben, verwenden Sie einen Debugger anfügen untergeordneter Prozess unterstützt.  Beachten Sie, dass es im Allgemeinen nicht Just-in-Time (JUST-in) auf die Zielanwendung Debuggen möglich ist.  Dies ist, da die meisten JIT Techniken umfassen des Debuggers an der Stelle der Ziel-app über den Registrierungsschlüssel ImageFileExecutionOptions.  Detouring ein Mechanismus, mit ShimLauncher.exe ShimRuntime.dll in die Ziel-app einfügen wird dadurch zunichte gemacht.  WinDbg, in der [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)abgerufen unterstützt untergeordneter Prozess anfügen.  Unterstützt jetzt auch direkt [Starten und eine UWP app zu debuggen](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).

Zum Starten der Anwendung Ziel als untergeordneter Prozess Debuggen starten ``WinDbg``.

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

Bei der ``WinDbg`` auffordern, aktivieren Sie untergeordneten Debuggen und entsprechenden Haltepunkte festlegen.

```
.childdbg 1
g
```
(wird ausgeführt, bis Zielanwendung startet und unterbricht)

```
sxe ld fixup.dll
g
```
(führen Sie bis die Korrektur aus die DLL-Datei geladen wird aus)

```
bp ...
```

>[!NOTE]
> [PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) kann auch verwendet werden, um eine app beim Start Debuggen, und auch in der [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.  Es ist jedoch komplexer als das direkte unterstützt jetzt WinDbg verwenden.

## <a name="support-and-feedback"></a>Support und Feedback

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).
