---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben Sie, der Desktop-Anwendung ausführen in einem Container MSIX verhindern
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: 9e2c34a5ed3134aeca7eb9490f05b20eb9a3e5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2018
ms.locfileid: "3986367"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a>Wenden Sie Runtime-Updates mithilfe der Support-Paket MSIX Paket an

Der Support-Paket ist eine open-Source-Kit, das Anwenden von Updates der vorhandene Win32-Anwendung beim Zugriff auf den Quellcode haben, damit sie in einem MSIX-Container ausgeführt wird. Der Support-Paket kann eine Anwendung die optimalen Vorgehensweisen von moderne Runtime Environment.

Erstellen Sie das Paket Förderkonzept nutzten wir [Umwege](https://www.microsoft.com/en-us/research/project/detours) -Technologie ist ein open-Source-Framework entwickelt von Microsoft Research (MSR) und API-Umleitung und verknüpfen kann.

Dieses Framework ist leicht, open Source und können diese Anwendung Probleme schnell. Es gibt Ihnen außerdem die Möglichkeit mit der Gemeinschaft weltweit und auf die Investitionen von anderen aufbauen.

## <a name="a-quick-look-inside-of-the-package-support-framework"></a>Ein kurzer Blick in der Support-Paket

Der Support-Paket enthält eine ausführbare Datei, Laufzeit-Manager-DLL und eine Reihe von Common Language Runtime-Updates.

![Paket Rahmen](images/desktop-to-uwp/package-support-framework.png)

So funktioniert’s. Sie erstellen eine Konfigurationsdatei, die die Fix(s) angibt, die auf die Anwendung angewendet werden soll. Anschließend wird das Paket auf die Shim-Start ausführbare Datei ändern.

Wenn Benutzer die Anwendung starten, ist das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird. Liest die Konfigurationsdatei und fügt Fix(s) Runtime und den Laufzeit-Manager DLL in den Anwendungsprozess.

![Paket Support Framework DLL-Injektion](images/desktop-to-uwp/package-support-framework-2.png)

Laufzeit-Manager gilt das Update bei Bedarf von der Anwendung in einem MSIX-Container ausgeführt.

Dieses Handbuch hilft Ihnen beim Identifizieren von Problemen mit der Anwendungskompatibilität und zu finden, anwenden und erweitern Runtime behebt, die sie behandeln.

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a>Gepackte Anwendungskompatibilitätsprobleme identifizieren

Erstellen Sie zunächst ein Paket für die Anwendung. Anschließend installieren, ausführen und beobachten. Sie möglicherweise Fehlermeldungen, die ein Kompatibilitätsproblem erleichtern. [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) können Sie Probleme identifizieren.  Probleme beziehen sich auf Anwendung Annahmen bezüglich arbeiten Berechtigungen für die Verzeichnisse und Programm-Pfad.

### <a name="using-process-monitor-to-identify-an-issue"></a>Mithilfe von Process Monitor ein Problem identifizieren

[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm eine app-Datei und Registrierungsvorgängen, und ihre Ergebnisse.  Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.  Process Monitor öffnen, fügen Sie einen Filter (Filter > Filter...) auf nur Ereignisse von ausführbaren Datei der Anwendung.

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

Eine Liste der Ereignisse wird angezeigt. Für viele dieser Ereignisse wird das Wort **Erfolg** in **der Ergebnisspalte** angezeigt.

![ProcMon Ereignisse](images/desktop-to-uwp/procmon_events.png)

Optional können Sie Ereignisse, um nur Fehler nur filtern.

![Erfolgreiche ProcMon ausschließen](images/desktop-to-uwp/procmon_exclude_success.png)

Wenn einen Dateisystem Zugriffsfehler vermuten, fehlgeschlagenen Ereignisse System32/SysWOW64 oder Paketdateipfad suchen. Filter können auch hier zu helfen. Am Ende dieser Liste starten, und führen Sie einen Bildlauf nach oben. Fehler am Ende dieser Liste erscheinen zuletzt aufgetreten. Die meisten achten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" und "Pfad/Name nicht gefunden" und was verdächtig nicht ignorieren. [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme. Diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt.

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

Das erste Problem, das in diesem Bild angezeigt wird, wird die Anwendung nicht die Datei "config.txt" gelesen, die im Pfad "C:\Windows\SysWOW64" befindet. Es ist unwahrscheinlich, dass die Anwendung diesen Pfad direkt verweisen. Wahrscheinlich versucht, die Datei mithilfe eines relativen Pfads gelesen und "System32/SysWOW64" wird standardmäßig Arbeitsverzeichnis der Anwendung. Dies ist die Anwendung der aktuellen Arbeitsverzeichnis irgendwo im Paket festgelegt werden, erwartet. In der Anlage sehen, wir, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.

![App Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

Das zweite Problem wird in der folgenden Abbildung angezeigt.

![ProcMon-Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

Dieses Problem ist die Anwendung nicht in der Paketpfad eine log-Datei schreiben. Denke, dass ein Datei Umleitung Shim unterstützen kann.

<a id="find" />

## <a name="find-a-runtime-fix"></a>Suchen nach einer Laufzeit-Lösung

Die PSF behebt Laufzeit, mit denen Sie, wie die Datei Umleitung Shim.

### <a name="file-redirection-shim"></a>Umleitung Shim-Datei

[Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten möchte schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung ist, die in einem MSIX-Container ausgeführt wird.

Z. B. wenn die Anwendung in eine Protokolldatei schreibt, die im gleichen Verzeichnis wie die ausführbare Anwendung können dann [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie die Protokolldatei an einem anderen Standort, wie lokale app-Datenspeicher zu erstellen.

### <a name="runtime-fixes-from-the-community"></a>Runtime-Updates aus der community

Überprüfen Sie die Beiträge der Community [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) Seite. Es ist möglich, dass andere Entwickler einen ähnlichen Problem gelöst haben und ein Runtime-Update freigegeben haben.

## <a name="apply-a-runtime-fix"></a>Runtime Hotfix

Sie können eine vorhandene Runtime einige einfache Tools aus dem Windows SDK und folgendermaßen Updates.

> [!div class="checklist"]
> * Erstellen Sie einen Ordner Paket layout
> * Paket Rahmen Dateien
> * Dem Paket hinzufügen
> * Bearbeiten des Paketmanifests
> * Erstellen einer Konfigurationsdatei

Lassen Sie uns jeder Aufgabe.

### <a name="create-the-package-layout-folder"></a>Den Paketordner Layout erstellen

Wenn noch eine .appx-Datei können Sie den Inhalt in einem Layout Ordner entpacken, die als Stagingbereich für das Paket verwendet wird.  Dazu aus einer **X64 systemeigenen Tools Befehlszeile VS 2017**, oder manuell mit den SDK-Bin-Pfad in den Suchpfad für ausführbare.

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

Dies wird Ihnen etwas, das wie folgt aussieht.

![Bildpaket-Layout](images/desktop-to-uwp/package_contents.png)

Haben Sie eine .appx-Datei beginnen, können Sie Paketordner und Dateien von Grund auf neu erstellen.

### <a name="get-the-package-support-framework-files"></a>Paket Rahmen Dateien

PSF Nuget-Paket erhalten mithilfe von Visual Studio. Außerdem erhalten sie mit eigenständigen Nuget-Befehlszeilentool.

#### <a name="get-the-package-by-using-visual-studio"></a>Abrufen des Pakets mit Visual Studio

In Visual Studio mit der rechten Maustaste des Knotens Projektmappe oder ein Projekt und wählen Befehle Nuget-Pakete verwalten.  Suche nach **Microsoft.PackageSupportFramework** oder **PSF** Paket unter "NuGet.org" suchen. Installieren Sie es anschließend.

#### <a name="get-the-package-by-using-the-command-line-tool"></a>Rufen Sie das Paket mit dem Befehlszeilenprogramm ab

Das Nuget-Befehlszeilentool von diesem Speicherort aus installieren: https://www.nuget.org/downloads. Führen Sie dann über die Befehlszeile Nuget Befehl aus:

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a>Rahmen-Paket das Paket hinzufügen

Erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbare Dateien auf dem Verzeichnis hinzufügen. Orientieren Sie sich an der folgenden Tabelle. Sie sollten auch alle Runtime-Updates enthalten, die Sie benötigen. In unserem Beispiel benötigen wir Datei Umleitung Runtime korrigieren.

| Ausführbare Anwendung ist x64 | Ausführbare Anwendung ist x86 |
|-------------------------------|-----------|
| [ShimLauncher64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [ShimLauncher32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [ShimRuntime64.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [ShimRuntime32.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [ShimRunDll64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [ShimRunDll32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

Der Inhalt sollte jetzt wie folgt aussehen.

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a>Bearbeiten des Paketmanifests

Die Paketmanifest in einem Texteditor öffnen, und legen Sie die `Executable` Attribut der `Application` Element auf den Namen der ausführbaren Datei Shim Launcher.  Sollten Sie die Architektur Ihrer Anwendung, wählen Sie die entsprechende Version ShimLauncher32.exe oder ShimLauncher64.exe.  Wenn nicht, ShimLauncher32.exe in allen Fällen verwendet werden.  Beispiel:

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

### <a name="create-a-configuration-file"></a>Erstellen einer Konfigurationsdatei

Erstellen Sie einen Dateinamen ``config.json``, und diese Datei in den Stammordner des Pakets speichern. Ändern Sie die deklarierte app-ID der Datei config.json auf die ausführbare Datei, die gerade ersetzt. Verwenden Sie mit Process Monitor gewonnenen Kenntnisse, können Sie auch das Arbeitsverzeichnis sowie Shim Umleitung Datei umleiten Lese-und Schreibvorgänge auf Log-Dateien im Verzeichnis "PSFSampleApp" Relative Paket verwenden.

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
Es folgt eine Anleitung für das Schema config.json:

| Array | key | Wert |
|-------|-----------|-------|
| applications | id |  Verwenden der `Id` Attribut der `Application` Element im Paketmanifest. |
| applications | ausführbare Datei | Das Paket relativer Pfad zur ausführbaren Datei, die Sie starten möchten. In den meisten Fällen erhalten Sie diesen Wert aus der Paketmanifestdatei bevor Sie sie ändern. Ist der Wert der `Executable` Attribut der `Application` Element. |
| applications | workingDirectory | (Optional) Ein Paket relativer Pfad verwendet das Arbeitsverzeichnis der Anwendung, die gestartet wird. Wenn dieser Wert nicht festgelegt wird, verwendet das Betriebssystem den `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare Datei | In den meisten Fällen werden der Name des dem `executable` über mit dem Pfad und Erweiterung konfiguriert. |
| Shims | DLL | Paket relativer Pfad Shim .appx geladen. |
| Shims | Konfiguration | (Optional) Steuert das Verhalten der Shim dl. Das genaue Format dieses Wertes hängt jeweils Shim Shim wie jede Shim "Blob" interpretieren kann, wie es. |

Die `applications`, `processes`, und `shims` Schlüssel sind Arrays. Das bedeutet, dass Sie config.json Datei können mehr als eine Anwendung, Prozess und Shim-DLL an.


### <a name="package-and-test-the-app"></a>Paket und Testen der Anwendung

Als Nächstes erstellen Sie ein Paket.

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

Anschließend signieren.

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

Weitere Informationen finden Sie unter [Erstellen eines Pakets Signaturzertifikat](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie ein Paket mithilfe von signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)

PowerShell verwenden, um das Paket zu installieren.

>[!NOTE]
> Beachten Sie das Paket zuerst deinstallieren.

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

Führen Sie die Anwendung, und beobachten Sie das Verhalten mit Laufzeit Fix angewendet.  Wiederholen Sie Diagnose und Verpackung Schritte.

### <a name="use-the-trace-shim"></a>Trace-Shim verwenden

Ein alternatives Verfahren zur Diagnose von Kompatibilitätsproblemen Anwendung ist die Verwendung der Trace-Shim. Diese DLL ist im Lieferumfang der PSF und bietet eine detaillierte Diagnose Ansicht der app Verhalten wie Process Monitor.  Es ist speziell Anwendungskompatibilitätsprobleme anzuzeigen.  Trace-Shim verwenden, dem Paket die DLL hinzufügen der config.json das folgende Fragment hinzufügen gepackt und installieren Sie die Anwendung.

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

Standardmäßig filtert der Trace-Shim Fehler, die in Betracht "erwartet".  Z. B. versucht Anwendung unbedingt eine Datei löschen, ohne zu überprüfen, ob sie vorhanden ist, wird das Ergebnis ignoriert. Die bedauerliche folgen einige unerwartete Fehler herausgefiltert abrufen können hat, im obigen Beispiel wir entscheiden, alle Fehler von Dateisystem-Funktionen erhalten Wir tun dies, denn wir wissen aus Lesen aus der Datei Config.txt vor, denen mit "die Meldung Datei nicht gefunden schlägt". Dies ist ein Fehler, der häufig und unerwartet nicht angenommen. In der Praxis ist es wahrscheinlich am besten zu filtern, unerwartete Fehler und dann zurückgreifen auf alle Fehler ist ein Problem, das noch nicht identifiziert werden kann.

In der Standardeinstellung wird die Ausgabe von Trace-Shim angefügten Debugger gesendet. In diesem Beispiel wir sind nicht zu debuggen und verwendet stattdessen [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) Programm von SysInternals um die Ausgabe anzuzeigen. Nach der Ausführung der Anwendung, sehen die gleichen Fehler wie zuvor wir die weisen wir auf die gleiche Laufzeit Updates.

![TraceShim-Datei nicht gefunden](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a>Debuggen Sie, erweitern Sie oder erstellen Sie eine Laufzeit-Korrektur

Sie können Visual Studio debuggen Laufzeit Fix, Runtime Update erweitern oder ein neues erstellen. Sie müssen diese Dinge zu tun.

> [!div class="checklist"]
> * Verpackungsprojekt hinzufügen
> * Projekt für Common Language Runtime-Update
> * Fügen Sie ein Projekt, das die Shim-Startprogramm ausführbare beginnt
> * Konfigurieren Sie das verpackungsprojekt

Wenn Sie fertig sind, wird die Projektmappe wie folgt aussehen.

![Bereits fertig gestellte Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

Jedes Projekt in diesem Beispiel betrachten.

| Projekt | Zweck |
|-------|-----------|
| DesktopApplicationPackage | Dieses Projekt basiert auf [Windows Application Packaging Projekt](desktop-to-uwp-packaging-dot-net.md) und es gibt das MSIX-Paket. |
| Runtimefix | Dies ist ein C++ Dynamic-Linked Bibliotheksprojekt mit mindestens Ersatz-Funktion, die als Update Runtime dienen. |
| ShimLauncher | Dies ist leeres C++-Projekt. Dieses Projekt ist an die Laufzeit verteilbaren Dateien des Paket-Unterstützung. Es gibt eine ausführbare Datei. Die ausführbare Datei ist was ausgeführt wird, wenn die Projektmappe zu starten. |
| WinFormsDesktopApplication | Dieses Projekt enthält den Quellcode einer desktop-Anwendung. |

Um sich ein vollständiges Beispiel, das alle diese Projekte enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).

Gehen Sie durch die Schritte zum Erstellen und Konfigurieren aller Projekte in der Projektmappe.


### <a name="create-a-package-solution"></a>Erstellen Sie eine Lösung

Haben Sie bereits eine Lösung für Ihr desktop-Anwendung, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

Außerdem möchten Sie Anwendungsprojekte hinzufügen.

### <a name="add-a-packaging-project"></a>Verpackungsprojekt hinzufügen

Haben Sie bereits ein **Windows-Anwendungsprojekt Verpackung**erstellt und der Projektmappe hinzufügen.

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

Weitere Informationen über Windows Application Packaging-Projekt finden Sie unter [Package die Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).

Im **Projektmappen-Explorer**Maustaste verpackungsprojekt **Bearbeiten**auswählen und dann am Ende der Projektdatei hinzufügen:

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

### <a name="add-project-for-the-runtime-fix"></a>Projekt für Common Language Runtime-Update

Die Lösung eines C++- **Dynamic Link Library (DLL)** hinzufügen.

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

Auf den Eigenschaftenseiten **C++ Language Standard** Feld und wählen Sie dann in der Dropdown-Liste neben dem Feld der **ISO C++ 17-Standard (/ Std:c-17)** Option.

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

Maustaste auf das Projekt und wählen Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** . Sicherstellen Sie, dass die **Paketquelle** **Alle** oder **nuget.org**gewählt wird.

Klicken Sie auf dem Symbol neben das Feld.

Suche nach *PSF** Nuget-Paket, und installieren Sie sie für dieses Projekt.

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

Wenn Sie Debuggen oder einen vorhandenen Laufzeit Fix erweitern möchten, fügen Sie Runtime Update-Dateien hinzu, die mit der beschriebenen Anleitung im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs erhalten.

Soll eine neue zu erstellen, nicht alles dieses Projekt hinzugefügt noch. Wir helfen Ihnen, die richtigen Dateien für dieses Projekt später hinzufügen. Jetzt werden wir das Einrichten Ihrer Lösung.

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a>Fügen Sie ein Projekt, das die Shim-Startprogramm ausführbare beginnt

Hinzufügen eines C++- **Leeres Projekt** der Projektmappe.

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

Fügen Sie **PSF** Nuget-Paket dieses Projekt mit der gleichen Anleitung im vorherigen Abschnitt beschrieben hinzu.

Öffnen die Eigenschaftenseiten für das Projekt und auf der Seite **Allgemeine** Einstellungen legen Sie **Target Name** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` je nach der Anwendung.

![Shim Launcher Verweis](images/desktop-to-uwp/shim-exe-reference.png)

Fügen Sie einen Projektverweis auf das Projekt Update in der Projektmappe.

![Laufzeit Fix Verweis](images/desktop-to-uwp/reference-fix.png)

Maustaste auf den Verweis und wenden Sie dann diese Werte im **Eigenschaftenfenster** .

| Eigenschaft | Wert |
|-------|-----------|-------|
| Lokale kopieren | Wahr |
| Lokale Satellitenassemblys kopieren | Wahr |
| Verweis Montageausstoß | Wahr |
| Link Library Abhängigkeiten | False |
| Verbindung Bibliothekabhängigkeitseingaben | False |

### <a name="configure-the-packaging-project"></a>Konfigurieren Sie das verpackungsprojekt

Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

Wählen Sie das Shim Launcher Projekt und desktop hinzu und wählen Sie dann auf **OK** .

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> Haben Sie den Quellcode der Anwendung, wählen Sie einfach das Shim Launcher-Projekt. Wir zeigen Ihnen wie die ausführbare Datei verweisen, wenn Sie eine Konfigurationsdatei erstellen.

Im Knoten **Applikationen** Application Launcher Shim Maustaste und wählen **als Einstiegspunkt**.

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

Fügen Sie eine Datei mit dem Namen ``config.json`` dem Projekt packen, kopieren und Json-Text in die Datei einfügen. Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalt**.

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
Geben Sie einen Wert für jeden Schlüssel. Verwenden Sie diese Tabelle als Leitfaden.

| Array | key | Wert |
|-------|-----------|-------|
| applications | id |  Verwenden der `Id` Attribut der `Application` Element im Paketmanifest. |
| applications | ausführbare Datei | Das Paket relativer Pfad zur ausführbaren Datei, die Sie starten möchten. In den meisten Fällen erhalten Sie diesen Wert aus der Paketmanifestdatei bevor Sie sie ändern. Ist der Wert der `Executable` Attribut der `Application` Element. |
| applications | workingDirectory | (Optional) Ein Paket relativer Pfad verwendet das Arbeitsverzeichnis der Anwendung, die gestartet wird. Wenn dieser Wert nicht festgelegt wird, verwendet das Betriebssystem den `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare Datei | In den meisten Fällen werden der Name des dem `executable` über mit dem Pfad und Erweiterung konfiguriert. |
| Shims | DLL | Paket relativer Pfad der Shim-DLL geladen. |
| Shims | Konfiguration | (Optional) Steuert das Verhalten der Shim dl. Das genaue Format dieses Wertes hängt jeweils Shim Shim wie jede Shim "Blob" interpretieren kann, wie es. |

Wenn Sie fertig sind, Ihre ``config.json`` Datei wird aussehen.

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
> Die `applications`, `processes`, und `shims` Schlüssel sind Arrays. Das bedeutet, dass Sie config.json Datei können mehr als eine Anwendung, Prozess und Shim-DLL an.

### <a name="debug-a-runtime-fix"></a>Debuggen Sie eine Laufzeit-Lösung

In Visual Studio Debugger starten F5.  Was startet ist die Shim Launcher Anwendung, Ihre Desktop-Anwendung gestartet wird.  Desktop-Anwendung zu debuggen, müssen Sie manuell Anhängen an den Prozess desktop-Anwendung mit **Debuggen**->**an den Prozess anhängen**und dann den Anwendungsprozess. Um das Debuggen einer Anwendung .NET mit einer einheitlichen Laufzeit DLL zuzulassen, wählen Sie verwaltetem und systemeigenem Code (Debuggen im gemischten Modus).  

Nachdem dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen desktop Anwendungscode und die Korrektur Projekt festlegen. Haben Sie den Quellcode der Anwendung, werden Sie Haltepunkte neben Codezeilen im Projekt Update Laufzeit festgelegt.

>[!NOTE]
> Visual Studio bietet die einfachste Entwicklung und Debuggen, gibt es einige Nachteile, werden später in diesem Handbuch andere Debugverfahren besprochen, die Sie anwenden können.

## <a name="create-a-runtime-fix"></a>Erstellen Sie eine Laufzeit-Korrektur

Wenn es keine Laufzeit beheben das Problem aufgelöst, erstellen eine neue Laufzeit Update ersetzt Funktionen und alle Konfigurationsdaten einschließlich macht Sinn. Betrachten Sie jeden Teil.

### <a name="replacement-functions"></a>Ersatz-Funktionen

Bestimmen Sie zunächst, welche Funktion Aufrufe schlagen fehl, wenn die Anwendung in einem MSIX-Container ausgeführt. Dann können Sie Ersatz-Funktionen erstellen, die den Laufzeit-Manager stattdessen aufrufen möchten. So haben Sie Gelegenheit, die Regeln von moderne Runtime Environment entspricht, Verhalten die Implementierung einer Funktion ersetzen.

Öffnen Sie in Visual Studio das Projekt Update, das in diesem Handbuch erstellt.

Erklären der ``SHIM_DEFINE_EXPORTS`` Makro und fügen Sie eine Include-Anweisung für die `shim_framework.h` am oberen Rand jeder. CPP-Datei für Funktionen der Common Language Runtime-Lösung hinzufügen möchten.

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
>Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung.

Erstellen Sie eine Funktion mit der gleichen Signatur der Funktion, hat Verhalten Sie ändern möchten. Hier ist eine Beispielfunktion ersetzt die `MessageBoxW` Funktion.

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

Der Aufruf `DECLARE_SHIM` ordnet die `MessageBoxW` in Ihre neue-Funktion als Ersatz. Wenn eine Anwendung versucht, rufen Sie die `MessageBoxW` , es wird Funktionsaufruf Ersatz-Funktion stattdessen.

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a>Rekursive Aufrufe von Funktionen in Laufzeit Updates schützen

Können optional gelten die `reentrancy_guard` geben die Funktionen, die rekursive Aufrufe von Funktionen in Laufzeit Updates schützen.

Z. B. können Sie eine Ersatz-Funktion für liefern die `CreateFile` Funktion. Die Implementierung aufrufen kann der `CopyFile` Funktion jedoch die Implementierung der `CopyFile` aufrufen kann der `CreateFile` Funktion. Dies kann auf eine unendliche rekursive Aufrufe der `CreateFile` Funktion.

Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)

### <a name="configuration-data"></a>Konfigurationsdaten

Wenn Sie Konfigurationsdaten der Laufzeit Fix hinzufügen möchten, sollten Sie hinzugefügt die ``config.json``. Auf diese Weise können Sie die `ShimQueryCurrentDllConfig` um diese Daten zu analysieren. In diesem Beispiel analysiert einen Boolean und String Wert aus dieser Konfigurationsdatei.

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

## <a name="other-debugging-techniques"></a>Andere Debugverfahren

Visual Studio Sie einfachste Entwicklung und Debuggen können, sind einige Nachteile.

F5-debugging wird zunächst die Anwendung von losen Dateien aus dem Paket Layout Ordner bereitstellen, sondern aus einem .appx Paket installiert.  Layout-Ordner noch die gleichen Einschränkungen als installierte Paketordner normalerweise nicht. Daher kann es nicht Pakets Denial Fehler vor einer Laufzeit Update Pfad reproduziert werden.

Um dieses Problem zu beheben, verwenden Sie .appx Bereitstellung F5 lose Datei Bereitstellung.  Erstellen Sie eine Paketdatei .appx verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK wie oben beschrieben. Oder in Visual Studio mit der rechten Maustaste des Projektknoten und wählen Sie **Store**->**App-Pakete erstellen**.

Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung zum Anhängen an untergeordnete Prozesse vom Debugger gestartet.   Dies erschwert das Debuggen Logik in den Startpfad Anwendung, die nach dem Start von Visual Studio manuell angefügt werden muss.

Um dieses Problem zu beheben, verwenden Sie einen Debugger, untergeordneten Prozess anfügen, unterstützt.  Beachten Sie, dass es im Allgemeinen nicht möglich, Just-in-Time (JIT) Anwendung debuggen.  Grund dafür ist die meisten JIT-Verfahren des Debuggers anstelle der Ziel-app über den Registrierungsschlüssel "ImageFileExecutionOptions".  Diese Niederlagen detouring Mechanismus zur ShimLauncher.exe ShimRuntime.dll in die Ziel-app einfügen.  WinDbg im [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und erhalten von [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)unterstützt untergeordneten Prozess anfügen.  Unterstützt jetzt auch direkt [Starten und eine UWP app zu debuggen](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).

Ziel beim Start der Anwendung als untergeordneter Prozess Debuggen starten ``WinDbg``.

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

Bei der ``WinDbg`` aufgefordert, Kind Debuggen und entsprechenden Haltepunkte festlegen.

```
.childdbg 1
g
```
(führen Sie bis Anwendung und unterbricht aus)

```
sxe ld fixup.dll
g
```
(führen Sie bis Fixup-DLL geladen ist aus)

```
bp ...
```

>[!NOTE]
> [PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) kann auch zum Debuggen einer Anwendung beim Start und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten.  Es ist jedoch komplexer als die direkte Unterstützung jetzt WinDbg verwenden.

## <a name="support-and-feedback"></a>Support und Feedback

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).
