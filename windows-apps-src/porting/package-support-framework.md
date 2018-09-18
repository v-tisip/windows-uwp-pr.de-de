---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben von Problemen, die Ihre desktop-Anwendung ausgeführt wird, in einem Container MSIX verhindern
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4021520"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a>Wenden Sie-Runtime-Updates zu einem MSIX-Paket mit dem Paket-Support-Framework

Das Paket-Support-Framework ist ein open-Source-Kit, mit dem Sie die Updates auf Anwenden der vorhandenen win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode, haben, damit sie in einem MSIX-Container ausgeführt werden kann. Das Paket Support-Framework können Ihre Anwendung, führen Sie die bewährten Methoden der modernen-Runtime-Umgebung.

Um das Paket Support-Framework zu erstellen, nutzten wir die [abweichen müssen](https://www.microsoft.com/en-us/research/project/detours) -Technologie ist ein open-Source-Framework von Microsoft Research (MSR) entwickelt und hilft bei der API-Umleitung und verknüpfen.

Dieses Framework ist open-Source, leichter zu, und können Sie sie zur Behandlung von Anwendung schnell. Es gibt Ihnen außerdem die Möglichkeit, mit der Community auf der ganzen Welt finden Sie in, und auf die Investitionen von anderen aufzubauen.

## <a name="a-quick-look-inside-of-the-package-support-framework"></a>Einen kurzen innerhalb der Paket-Support-Framework

Das Paket Support-Framework enthält eine ausführbare Datei, ein Laufzeit-Manager DLL-Datei und eine Reihe von Runtime-Updates.

![Paket-Support-Framework](images/desktop-to-uwp/package-support-framework.png)

So funktioniert’s. Erstellen Sie eine Konfigurationsdatei, die die Fix(s) angibt, die Sie für Ihre Anwendung anwenden möchten. Anschließend können Sie das Paket auf die Shim Startprogramm ausführbare Datei verweisen ändern.

Wenn Benutzer Ihre Anwendung starten, wird das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird. Ihrer Konfigurationsdatei liest, und fügen der Runtime Fix(s) und den Laufzeit-Manager DLL in den Anwendungsprozess.

![Paket-Unterstützung Framework DLL-Injection](images/desktop-to-uwp/package-support-framework-2.png)

Der Laufzeit-Manager gilt das Update, wenn sie von der Anwendung auf einem MSIX-Container Ausführen benötigt wird.

Dieses Handbuch hilft Ihnen, Probleme mit der Anwendungskompatibilität zu identifizieren und um suchen, anwenden und erweitern die Runtime behebt, die sie beheben.

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a>Anwendungspakets Kompatibilitätsprobleme identifiziert

Erstellen Sie zunächst ein Paket für Ihre Anwendung. Installieren Sie es dann, und beobachten Sie, führen Sie es. Sie erhalten möglicherweise Fehlermeldungen, mit denen Sie eine Kompatibilitätsprobleme identifizieren können. Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu identifizieren.  Allgemeine Probleme beziehen sich auf die Anwendung Annahmen in Bezug auf die Berechtigungen zum Arbeiten-Verzeichnis und Programm Pfad.

### <a name="using-process-monitor-to-identify-an-issue"></a>Process Monitor verwenden, um ein Problem zu identifizieren

[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm ermöglicht Ihnen, eine app-Datei und Registrierungsvorgänge und die Ergebnisse.  Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.  Fügen Sie nach dem Öffnen Process Monitor, einen Filter (Filter > Filter...) nur Ereignisse für die Anwendung ausführbare einschließen.

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

Eine Liste der Ereignisse wird angezeigt. Für viele dieser Ereignisse wird das Wort **Erfolg** in der Spalte **Ergebnis** angezeigt.

![ProcMon-Ereignisse](images/desktop-to-uwp/procmon_events.png)

Optional können Sie Ereignisse, um nur Fehler nur anzeigen filtern.

![ProcMon Exclude Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

Wenn Sie einen Dateisystem Zugriff Fehler vermuten, suchen Sie nach fehlgeschlagenen Ereignisse, die unter der System32/SysWOW64 oder der Paketdateipfad sind. Filter können auch hier zu helfen. Starten Sie am unteren Rand der Liste, und führen Sie einen Bildlauf nach oben. Fehler, die am unteren Rand der Liste angezeigt werden, sind die zuletzt aufgetreten. Achten Sie die meisten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten, und "Pfad/Name nicht gefunden", und ignorieren Sie Dinge, die nicht verdächtige aussehen. Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme. Sie können diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt wird.

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

In der ersten Ausgabe, die in diesem Bild angezeigt wird, wird die Anwendung nicht aus der Datei "Config.txt" zu lesen, die im Pfad "C:\Windows\SysWOW64" befindet. Es ist unwahrscheinlich, dass die Anwendung versucht, diesen Pfad direkt zu verweisen. In den meisten Fällen versucht, einen relativen Pfad mit aus der Datei gelesen und in der Standardeinstellung ist "System32/SysWOW64" Arbeitsverzeichnis der Anwendung. Dies zeigt, dass die Anwendung die aktuelle Arbeitsverzeichnis, das an einer beliebigen Stelle im Paket festgelegt werden, um erwartet wird. Suchen innerhalb der Appx, sehen Sie, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

Das zweite Problem wird in der folgenden Abbildung angezeigt.

![ProcMon Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

In diesem Problem ist die Anwendung keine log-Datei in ihrem Paketpfad zu schreiben. Dies würde empfehlen, dass ein Datei Umleitung Shim hilfreich ist.

<a id="find" />

## <a name="find-a-runtime-fix"></a>Suchen nach einer Runtime-Lösung

Die PSF enthält Runtime-Updates, die Sie jetzt, wie z. B. die Datei Umleitung Shim verwenden können.

### <a name="file-redirection-shim"></a>Datei Umleitung Shim

Die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten initiierten schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung ist, die in einem MSIX-Container ausgeführt wird.

Z. B. wenn die Anwendung in eine Protokolldatei, die in demselben Verzeichnis wie die ausführbare Anwendung ist schreibt, können klicken Sie dann die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie um die Protokolldatei in einen anderen Speicherort, z. B. den lokalen app-Datenspeicher zu erstellen.

### <a name="runtime-fixes-from-the-community"></a>Runtime-Updates von der community

Achten Sie darauf, dass Sie die Community Beiträge unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) -Seite zu überprüfen. Es ist möglich, dass andere Entwickler eine ähnliche und Ihrem Problem gelöst haben und ein Laufzeit-Update freigegeben haben.

## <a name="apply-a-runtime-fix"></a>Wenden Sie ein Laufzeit-Update

Sie können eine vorhandene Runtime Korrektur mit einige einfache Tools aus dem Windows SDK, und wie folgt anwenden.

> [!div class="checklist"]
> * Erstellen Sie einen Ordner des Pakets layout
> * Die Paket-Support-Framework-Dateien zu erhalten
> * Fügen Sie zu Ihrem Paket hinzu
> * Bearbeiten des Paketmanifests
> * Erstellen Sie eine Konfigurationsdatei

Gehen Sie wir durch einzelnen Aufgaben.

### <a name="create-the-package-layout-folder"></a>Erstellen Sie den Ordner der Paket-layout

Wenn Sie bereits über eine AppX-Datei verfügen, können Sie den Inhalt in einem Layoutordner entpacken, die als die Staging-Bereich für Ihr Paket verwendet wird.  Können Sie tun dies auf ein **X64 systemeigenen Tools-Eingabeaufforderung für VS 2017**, oder manuell mit dem SDK Bin-Pfad in den Suchpfad der ausführbaren.

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

Dadurch wird eine Aktion angezeigt, die wie folgt aussieht.

![Paketlayout](images/desktop-to-uwp/package_contents.png)

Wenn Sie eine AppX-Datei zu haben, können Sie die Paketordner und Dateien von Grund auf neu erstellen.

### <a name="get-the-package-support-framework-files"></a>Die Paket-Support-Framework-Dateien zu erhalten

Sie können das PSF Nuget-Paket abrufen, mit Visual Studio. Sie können es auch abrufen, mit dem eigenständigen Nuget-Befehlszeile-Tool.

#### <a name="get-the-package-by-using-visual-studio"></a>Rufen Sie das Paket mit Visual Studio

In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.  Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , das Paket "NuGet.org" gefunden. Anschließend installieren Sie es.

#### <a name="get-the-package-by-using-the-command-line-tool"></a>Rufen Sie das Paket mit dem Tool für die Befehlszeile

Installieren Sie das Nuget-Befehlszeilentool von diesem Speicherort: https://www.nuget.org/downloads. Führen Sie dann über die Befehlszeile Nuget diesen Befehl aus:

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a>Hinzufügen der Paket-Support-Framework-Dateien zu Ihrem Paket

Erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbaren Dateien in das Paketverzeichnis hinzufügen. Orientieren Sie sich an der folgenden Tabelle. Sie sollten auch alle-Runtime-Updates enthalten, die Sie benötigen. In unserem Beispiel benötigen wir die Datei Umleitung-Runtime-Problembehandlung.

| Die ausführbare Datei Anwendung ist x64 | Die ausführbare Datei Anwendung ist x86 |
|-------------------------------|-----------|
| [ShimLauncher64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [ShimLauncher32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [ShimRuntime64.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [ShimRuntime32.dll](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [ShimRunDll64.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [ShimRunDll32.exe](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

Der Inhalt sollte nun in etwa wie folgt aussehen.

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a>Bearbeiten des Paketmanifests

Öffnen Sie Ihr Paketmanifest in einem Text-Editor, und legen Sie die `Executable` -Attribut des der `Application` Element auf den Namen der ausführbaren Datei Shim Startprogramm.  Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die korrekte Version, ShimLauncher32.exe oder ShimLauncher64.exe.  Wenn dies nicht der Fall ist, ShimLauncher32.exe in allen Fällen funktioniert.  Beispiel:

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

Erstellen Sie einen Dateinamen ``config.json``, und speichern Sie diese Datei in den Stammordner des Pakets. Ändern Sie die ID der config.json-Datei deklarierten app aus, um auf die ausführbare Datei verweisen, die Sie gerade ersetzt. Verwenden das wissen, das Sie an der Verwendung von Process Monitor erlangt, können Sie auch das Arbeitsverzeichnis sowie verwenden das Datei Umleitung Shim Lese-/Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" relativen umgeleitet.

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
| applications | id |  Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest. |
| applications | ausführbare | Der relativen Pfad der ausführbaren Datei, die Sie starten möchten. In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern. Es ist der Wert von der `Executable` -Attribut des der `Application` Element. |
| applications | workingDirectory | (Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird. Wenn Sie diesen Wert nicht festlegen, wird das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare | Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad und konfiguriert. |
| Shims | DLL-Datei | Relativen Pfad zu der Shim AppX geladen. |
| Shims | config | (Optional) Steuert, wie die Shim Verteilerliste verhält. Das genaue Format dieses Werts variiert Shim durch Shim regelmäßig, wie jedes Shim dieses "Blob" interpretiert werden kann, wie möglich. |

Die `applications`, `processes`, und `shims` Schlüssel sind Arrays. Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Shim-DLL anzugeben.


### <a name="package-and-test-the-app"></a>Paket und Testen der App

Als Nächstes erstellen Sie ein Paket.

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

Signieren Sie es dann.

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

Weitere Informationen finden Sie unter [wie ein Signaturzertifikat Paket erstellen](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie Sie ein Pakets mit signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)

Mithilfe von PowerShell, installieren Sie das Paket.

>[!NOTE]
> Denken Sie daran, das Paket zuerst deinstalliert werden soll.

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

Führen Sie die Anwendung, und beobachten Sie das Verhalten Runtime Update angewendet.  Wiederholen Sie die Diagnose- und Verpacken Schritte nach Bedarf.

### <a name="use-the-trace-shim"></a>Verwenden Sie das Trace-Shim

Ein alternatives Verfahren für die Diagnose von Kompatibilitätsproblemen verpackten Anwendung ist die Verwendung der Trace-Shim. Diese DLL ist in der PSF enthalten und bietet eine detaillierte Ansicht der app Verhalten, ähnlich wie Process Monitor diagnostische.  Es ist speziell auf Probleme mit der Anwendungskompatibilität "einblenden".  Verwenden Sie die Trace-Shim, die DLL für das Paket hinzufügen Ihrer config.json die folgende Fragment-Komponente hinzufügen und dann Verpacken und Installieren Ihrer Anwendung.

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

Standardmäßig filtert die Trace Shim Fehler, die berücksichtigt werden möglicherweise "erwartet".  Beispielsweise Versuch Anwendungen bedingungslos Löschen einer Datei ohne zu überprüfen, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert. Dies hat die unerwünschten Folgen, die einige unerwartete Fehler, gefiltert erhalten möglicherweise so melden Sie sich im obigen Beispiel wir an, um alle Fehler von Dateisystem-Funktionen zu empfangen. Wir tun, da wir von vor, die das Lesen aus der Datei Config.txt fehlschlägt wissen mit "die Meldung Datei nicht gefunden". Dies ist ein Fehler, der häufig beobachtet und nicht in der Regel davon ausgegangen, dass unerwartet ist. In der Praxis ist es wahrscheinlich am besten, beginnen Sie mit dem Filterung nur für unerwartete Fehler, und klicken Sie dann auf die zurückfallen alle Fehler liegt ein Problem, das weiterhin identifiziert werden kann.

Standardmäßig wird die Ausgabe der Trace-Shim an den Debugger angefügte gesendet. In diesem Beispiel stellen wir sind nicht zu debuggen, und wird die Anwendung [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals stattdessen verwenden, um die Ausgabe anzuzeigen. Nach dem Ausführen der app, sehen die gleichen Fehler wie zuvor, Sie die würden uns für die gleichen Runtime Updates zeigen.

![TraceShim Datei nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a>Debuggen Sie, erweitern Sie oder erstellen Sie ein Laufzeit-Update

Visual Studio können Sie ein Laufzeit-Update Debuggen, erweitern ein Laufzeit-Update oder ein neues erstellen. Sie müssen für diese Vorgänge erfolgreich ausgeführt werden kann.

> [!div class="checklist"]
> * Hinzufügen eines verpackungsprojekts
> * Fügen Sie Projekt für die Common Language Runtime-Problembehandlung
> * Fügen Sie ein Projekt, die Shim-Startprogramms gestartet wird.
> * Konfigurieren Sie das Verpacken-Projekt

Wenn Sie fertig sind, wird die Projektmappe etwa wie folgt aussehen.

![Fertigen Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

Sehen wir uns auf jedes Projekt in diesem Beispiel.

| Projekt | Zweck |
|-------|-----------|
| DesktopApplicationPackage | Dieses Projekt basiert auf dem [Windows Application Packaging-Projekt](desktop-to-uwp-packaging-dot-net.md) , und es gibt die das Paket MSIX. |
| Runtimefix | Dies ist eine Bibliothek Dynamic-Linked-Projekt mit einer oder mehreren Ersatzfunktionen, die als die Runtime-Problembehandlung dienen. |
| ShimLauncher | Dies ist leeres C++-Projekt. Dieses Projekt ist ein Ort zum Abrufen der Runtime verteilbaren Dateien des Pakets Support-Frameworks. Es gibt eine ausführbare Datei. Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe zu starten. |
| WinFormsDesktopApplication | Dieses Projekt enthält den Quellcode einer desktop-Anwendung. |

Um ein vollständiges Beispiel betrachten, die alle diese Arten von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).

Betrachten Sie die Schritte zum Erstellen und Konfigurieren jedes dieser Projekte in Ihrer Projektmappe aus.


### <a name="create-a-package-solution"></a>Erstellen Sie eine Paket-Projektmappe

Wenn Sie bereits über eine Lösung für Ihre desktop-Anwendung besitzen, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

Sie sollten auch alle Anwendungsprojekte, die hinzufügen, die Sie haben.

### <a name="add-a-packaging-project"></a>Hinzufügen eines verpackungsprojekts

Wenn Sie bereits über ein **Windows Application Packaging Project**besitzen, erstellen Sie eine, und fügen sie Sie Ihrer Projektmappe hinzu.

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

Weitere Informationen zu Windows Application Packaging Project finden Sie im [Paket Ihrer Anwendung mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).

Im **Projektmappen-Explorer**mit der rechten Maustaste in des Verpacken-Projekts, wählen Sie **Bearbeiten**und fügen Sie diese an das Ende der Datei:

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

### <a name="add-project-for-the-runtime-fix"></a>Fügen Sie Projekt für die Common Language Runtime-Problembehandlung

Fügen Sie der Projektmappe ein C++- **Dll-Bibliothek (DLL)** -Projekt hinzu.

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

Der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.

Auf den Eigenschaftenseiten suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld der **ISO C ++ 17 Standard (/ Std: c ++ 17)** Option.

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

Mit der rechten Maustaste in des Projekts, und wählen Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** . Stellen Sie sicher, dass die **Paketquelle** Option für **Alle** oder **"NuGet.org"** festgelegt ist.

Klicken Sie auf dem Symbol "Einstellungen" neben dem Feld.

Suchen Sie nach der *PSF** Nuget Paket, und installieren Sie es für dieses Projekt.

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

Wenn Sie Debuggen oder einen vorhandenen Runtime Fix erweitern möchten, fügen Sie die Runtime-Fix-Dateien, die Sie abgerufen, indem Sie die Anleitung im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs.

Wenn Sie beabsichtigen, ein völlig neues Update zu erstellen, fügen Sie nicht alles dieses Projekt noch. Wir helfen Ihnen, die richtigen Dateien diesem Projekt weiter unten in diesem Handbuch hinzufügen. Für den Moment fahren wir Einrichten Ihrer Projektmappe fort.

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a>Fügen Sie ein Projekt, die Shim-Startprogramms gestartet wird.

Fügen Sie der Projektmappe ein **Leeres Projekt** für C++-Projekt hinzu.

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

Fügen Sie das **PSF** Nuget-Paket auf dieses Projekt mithilfe von die gleichen Anleitung im vorherigen Abschnitt hinzu.

Öffnen die Eigenschaftenseiten für das Projekt, und klicken Sie auf der Seite **Allgemein** Einstellungen setzen Sie den **Zielnamen** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` abhängig von der Architektur der Anwendung.

![Shim Startprogramm-Referenz](images/desktop-to-uwp/shim-exe-reference.png)

Fügen Sie einen Projektverweis auf das Projekt der Runtime Update in Ihrer Projektmappe hinzu.

![-Runtime-Fix-Referenz](images/desktop-to-uwp/reference-fix.png)

Mit der rechten Maustaste in der Referenz, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.

| Eigenschaft | Wert |
|-------|-----------|-------|
| Kopieren Sie lokale | Wahr |
| Lokale Satellitenassemblys kopieren | Wahr |
| Referenz-Assembly-Ausgabe | Wahr |
| Link-Bibliothek Abhängigkeiten | False |
| Link-Bibliothek Abhängigkeit Eingaben | False |

### <a name="configure-the-packaging-project"></a>Konfigurieren Sie das Verpacken-Projekt

Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

Wählen Sie die Shim-Startprogramm Projekt und Ihre desktop-Anwendung, und wählen Sie dann auf die Schaltfläche " **OK** ".

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> Wenn Sie den Quellcode für Ihre Anwendung besitzen, wählen Sie einfach das Shim Startprogramm-Projekt. Wir zeigen Ihnen wie die ausführbare Datei verweisen, wenn Sie eine Konfigurationsdatei erstellen.

Klicken Sie im Knoten " **Anwendungen** " mit der rechten Maustaste in der startanwendung Shim, und wählen Sie dann **als Einstiegspunkt festlegen**.

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

Fügen Sie eine Datei mit dem Namen ``config.json`` dem Verpacken-Projekt, klicken Sie dann, kopieren und fügen Sie den folgenden Json-Text in die Datei. Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalte**.

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
Geben Sie einen Wert für jeden Schlüssel. Orientieren Sie in der folgenden Tabelle.

| Array | key | Wert |
|-------|-----------|-------|
| applications | id |  Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest. |
| applications | ausführbare | Der relativen Pfad der ausführbaren Datei, die Sie starten möchten. In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern. Es ist der Wert von der `Executable` -Attribut des der `Application` Element. |
| applications | workingDirectory | (Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird. Wenn Sie diesen Wert nicht festlegen, wird das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung. |
| Prozesse | ausführbare | Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad und konfiguriert. |
| Shims | DLL-Datei | Relativen Pfad zu der Shim-DLL zu laden. |
| Shims | config | (Optional) Steuert, wie die Shim Verteilerliste verhält. Das genaue Format dieses Werts variiert Shim durch Shim regelmäßig, wie jedes Shim dieses "Blob" interpretiert werden kann, wie möglich. |

Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt aus.

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
> Die `applications`, `processes`, und `shims` Schlüssel sind Arrays. Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Shim-DLL anzugeben.

### <a name="debug-a-runtime-fix"></a>Debuggen Sie ein Laufzeit-Update

Drücken Sie in Visual Studio F5, um den Debugger zu starten.  Müssen Sie zunächst, die gestartet wird, ist der startanwendung Shim, die wiederum die Ziel-desktop-Anwendung gestartet wird.  Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell für den desktop-Anwendungsprozess anhängen, indem Sie **Debuggen**auswählen->**an den Prozess anhängen**, und wählen Sie dann den bewerbungsprozess. Um das Debuggen einer .NET-Anwendung mit einen systemeigenen Runtime Hotfix DLL zu ermöglichen, wählen Sie verwalteten und systemeigenen Code (im gemischten Modus Debuggen).  

Nachdem Sie dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und das Projekt der Runtime Update festlegen. Wenn Sie den Quellcode für Ihre Anwendung besitzen, werden Sie Haltepunkte nur neben Codezeilen in Ihrem Projekt der Runtime Update festlegen.

>[!NOTE]
> Obwohl Visual Studio Ihnen die einfachste Entwicklung bietet und Debuggen, es einige Einschränkungen gibt, dies später in diesem Handbuch erläutern wir, andere debugging Techniken, die Sie anwenden können.

## <a name="create-a-runtime-fix"></a>Erstellen Sie ein Laufzeit-Update

Wenn es keinen noch eine Laufzeit für das Problem beheben, aufgelöst werden soll, können Sie erstellen einen neuen Runtime Hotfix schreiben Ersatzfunktionen und alle Konfigurationsdaten, darunter ist, die sinnvoll. Sehen wir uns auf jeder Teil.

### <a name="replacement-functions"></a>Ersatzfunktionen

Identifizieren Sie zunächst, welche Funktion ruft fehl, wenn die Anwendung in einem MSIX-Container ausgeführt wird. Anschließend können Sie Ersatzfunktionen erstellen, die Sie mit den Laufzeit-Manager stattdessen aufrufen möchten. Dies bietet Ihnen die Möglichkeit, die Implementierung einer Funktion mit Verhalten zu ersetzen, die die Regeln der modernen-Runtime-Umgebung entspricht.

Öffnen Sie das Projekt der Runtime-Update, das Sie weiter oben in diesem Handbuch erstellt haben, in Visual Studio.

Deklarieren Sie die ``SHIM_DEFINE_EXPORTS`` Makro und fügen Sie eine Include-Anweisung für die `shim_framework.h` am Anfang jeder. CPP-Datei für die Funktionen der Ihrer Laufzeit-Update hinzufügen möchten.

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
>Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.

Erstellen Sie eine Funktion, die dieselbe Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten. Dies ist eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.

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

Der Aufruf von `DECLARE_SHIM` ordnet die `MessageBoxW` in Ihrer neuen-Funktion als Ersatz. Wenn Ihre Anwendung versucht, rufen Sie die `MessageBoxW` -Funktion es Ruft die Ersatz-Funktion stattdessen.

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a>Schutz vor rekursiven-Aufrufe von Funktionen in der Common Language Runtime-Updates

Sie können optional anwenden, die `reentrancy_guard` geben, um Ihre Funktionen, die Schutz gegen rekursiven-Aufrufe von Funktionen in der Common Language Runtime-Updates.

Sie können z. B. erzeugen, eine Funktion Ersatz für die `CreateFile` Funktion. Die Implementierung aufrufen kann die `CopyFile` -Funktion, aber die Implementierung von der `CopyFile` Funktion kann aufrufen und die `CreateFile` Funktion. Dies kann dazu führen, dass ein unendlichen rekursiven Zyklus der Aufrufe von der `CreateFile` Funktion.

Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)

### <a name="configuration-data"></a>Konfigurationsdaten

Wenn Sie Ihre Update-Runtime-Konfigurationsdaten hinzufügen möchten, in Betracht ziehen, um die ``config.json``. Auf diese Weise können Sie die `ShimQueryCurrentDllConfig` einfach diese Daten analysiert. In diesem Beispiel wird einen Boolean und String-Wert aus der Konfigurationsdatei analysiert.

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

## <a name="other-debugging-techniques"></a>Andere debugging-Techniken

Während Visual Studio die einfachste Entwicklung und das debugging Erfahrung Ihnen bietet, gibt es einige Einschränkungen.

Zuerst wird ein Debuggens mit F5 die Anwendung durch die Bereitstellung von losen Dateien aus dem Paket Layout Ordnerpfad, statt aus einem AppX-Paket installiert.  Der Layoutordner verfügt in der Regel nicht dieselben sicherheitseinschränkungen, die als ein installiere Paket-Ordner. Daher kann es nicht Paket Pfad Denial Zugriffsfehler vor der Anwendung ein Laufzeit-Updates reproduziert werden.

Um dieses Problem zu beheben, verwenden Sie Bereitstellung des AppX-Pakets anstelle von F5 loser Datei-Bereitstellung.  Um eine AppX-Paketdatei zu erstellen, verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK, wie oben beschrieben. Oder, in Visual Studio Maustaste auf den Projektknoten Anwendung und wählen **Store**->**App-Pakete erstellen**.

Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung für die Verbindung vom Debugger gestartet untergeordnete Prozesse enthält.   Dies erschwert es zum Debuggen Logik im Startpfad der Zielanwendung, die nach der Einführung von Visual Studio manuell angefügt werden muss.

Um dieses Problem zu beheben, verwenden Sie einen Debugger, untergeordneter Prozess anhängen, unterstützt.  Beachten Sie, dass es in der Regel nicht möglich, Just-in-Time (JIT) der Zielanwendung Debuggen.  Grund dafür ist die meisten JIT-Techniken des Debuggers anstelle der Ziel-app, über den Registrierungsschlüssel ImageFileExecutionOptions.  Den detouring Mechanismus von ShimLauncher.exe verwendet, um ShimRuntime.dll in die Ziel-app einzufügen "vereitelt" wird.  WinDbg, in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten, und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), unterstützt untergeordneten Prozess anfügen.  Unterstützt jetzt auch direkt [Starten und Debuggen einer UWP-Apps](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).

Zum Starten der Ziel-Anwendung als untergeordneter Prozess Debuggen starten ``WinDbg``.

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

Bei der ``WinDbg`` auffordern, untergeordnete Debuggen aktivieren und entsprechenden Haltepunkte festlegen.

```
.childdbg 1
g
```
(ausgeführt wird, bis die Anwendung startet und unterbricht)

```
sxe ld fixup.dll
g
```
(erst ausgeführt, wenn die Korrektur aus die DLL geladen wird)

```
bp ...
```

>[!NOTE]
> [PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) können auch verwendet werden, um eine app nach dem Start Debuggen, und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.  Es ist jedoch komplexer als das direkte unterstützt jetzt WinDbg verwenden.

## <a name="support-and-feedback"></a>Support und Feedback

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).
