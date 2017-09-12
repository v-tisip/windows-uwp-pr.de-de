---
author: normesta
Description: "Führen Sie Desktop App Converter zum verpacken einer Windows-Desktopanwendung (z.B. Win32, WPF und Windows Forms) aus."
Search.Product: eADQiWindows 10XVcnh
title: "Verpacken einer App mit dem Desktop App Converter (Desktop-Brücke)"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 74c84eb6-4714-4e12-a658-09cb92b576e3
ms.openlocfilehash: 6aa469d0080412f48de511315684d365d4e90c99
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="package-an-app-using-the-desktop-app-converter-desktop-bridge"></a>Verpacken einer App mit dem Desktop App Converter (Desktop-Brücke)

[Laden Sie Desktop App Converter herunter](https://aka.ms/converter)

Sie könnten den Desktop App Converter (DAC) verwenden, um Ihre Desktop-Apps auf die Universelle Windows-Plattform (UWP) umzustellen. Dazu zählen Win32-Apps und Apps, die Sie mithilfe von .NET 4.6.1 erstellt haben.

<div style="float: left; padding: 10px">
    ![DAC-Symbol](images/desktop-to-uwp/dac.png)
</div>

Obwohl der Begriff „Konverter“ im Namen dieses Tool auftaucht, wird nicht tatsächlich konvertiert. Ihre App bleibt unverändert. Das Tool generiert jedoch ein Windows-App-Paket mit eine Paketidentität. Es bietet die Möglichkeit, viele WinRT-APIs aufzurufen.

Sie können dieses Paket mithilfe des Add-AppxPackage-PowerShell-Cmdlets auf Ihrem Entwicklungscomputer installieren.

Der Konverter führt den Desktop-Installer in einer isolierten Windows-Umgebung mit einem sauberen Basisimage als Teil des Konverterdownloads aus. Es werden alle Registrierungs- und Dateisystem-E/A des Desktop-Installers erfasst und als Teil der Ausgabe gepackt.

> [!NOTE]
> Sehen Sie sich <a href="https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373?l=oZG0B1WhD_8406218965/">diese Reihe</a> von kurzen Videos an, die von der Microsoft Virtual Academy veröffentlicht wurden. Diese Videos erläutern einige gängige Verwendungsmethoden des Desktop App Converters.

## <a name="the-dac-does-more-than-just-generate-a-package-for-you"></a>Das DAC macht mehr als nur ein Paket zu generieren.

Hier sind einige zusätzliche Aufgaben, die er für Sie erledigen kann.

**Windows10 Creators Update**

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

Automatisches Registrieren Ihrer Preview-Handler, Miniaturansichthandler, Eigenschaftenhandler, Firewall-Regeln, URL-Kennzeichen.

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

Automatisches Registrieren Ihrer Dateizuordnungen, mit denen Benutzer Dateien mithilfe der **Art**-Spalte im Datei-Explorer gruppieren können.

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

Registrieren Ihrer öffentlichen COM-Server.

**Windows 10 Anniversary Update oder höher**

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

Automatisches Signieren Ihres Pakets, damit Sie Ihre App testen können.

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

Überprüfen Ihrer App für Desktop-Brücke- und Windows Store-Anforderungen.

Eine vollständige Liste der Optionen finden Sie unter dem Abschnitt [Parameter](#command-reference) dieses Handbuchs.

Wenn Sie für die Erstellung des Pakets bereit sind, lassen Sie uns starten.

## <a name="first-consider-how-youll-distribute-your-app"></a>Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.
Wenn Sie Ihre App im [Windows Store-](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge). Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess. Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.

## <a name="make-sure-that-your-system-can-run-the-converter"></a>Stellen Sie sicher, dass das System den Konverter ausführen kann.

Stellen Sie sicher, dass das System die folgenden Anforderungen erfüllt:

* Windows 10 Anniversary Update (10.0.14393.0 und höher) Pro oder Enterprise Edition.
* 64-Bit (x64)-Prozessor
* Hardwareunterstützte Virtualisierung
* Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)
* [Windows Software Development Kit (SDK) für Windows10](https://go.microsoft.com/fwlink/?linkid=821375).


## <a name="start-the-desktop-app-converter"></a>Starten Sie den Desktop App Converter.

1. Laden und Installieren Sie den [Desktop App Converter](https://aka.ms/converter).

2. Führen Sie den Desktop App Converter als Administrator aus.

    ![Führen Sie DAC als Administrator aus.](images/desktop-to-uwp/run-converter.png)

   Ein Konsolenfenster wird angezeigt. Sie werden dieses Konsolenfenster verwenden, um Befehle auszuführen.

## <a name="set-a-few-things-up-apps-with-installers-only"></a>Richten Sie ein paar Dinge ein (nur Apps mit Installer)

Sie können diesen Abschnittüberspringen, falls Ihre App über kein Installationsprogramm verfügt.

1. Identifizieren Sie die Version Ihres Betriebssystems.

   Öffnen Sie dazu die **Systeminformationen-App** auf Ihrem Computer, und suchen Sie dann die Versionsnummer des Betriebssystems.

    ![Betriebssystemversion in der App Systeminformationen](images/desktop-to-uwp/os-version.png)

2. Laden Sie das entsprechende [Desktop-App-Konverter-Basisimage](https://aka.ms/converterimages).

   Stellen Sie sicher, dass die Versionsnummer, die im Namen der Datei angezeigt wird, der Versionsnummer des Windows-Builds entspricht.

   ![Entsprechende Basisimage-Version](images/desktop-to-uwp/base-image-version.png)

   Platzieren Sie die heruntergeladene Datei an einem beliebigen Speicherort auf Ihrem Computer, wo Sie sie später wieder finden werden.

3. Führen Sie im Konsolenfenster, das beim Starten des Desktop App Converters angezeigt wird, folgenden Befehl aus: ```Set-ExecutionPolicy bypass```.
4.  Richten Sie den Konverter durch Ausführen dieses Befehls ein: ```DesktopAppConverter.exe -Setup -BaseImage .\BaseImage-1XXXX.wim -Verbose```.
5.  Starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.

    Statusbenachrichtigungen werden beim Erweitern des Basisimage durch den Konverter im Konsolenfenster angezeigt. Wenn Ihnen keine Statusbenachrichtigungen angezeigt werden, drücken Sie eine beliebige Taste. Dadurch kann der Inhalt des Konsolenfensters aktualisiert werden.

    ![Statusbenachrichtigungen in der Konsole](images/desktop-to-uwp/bas-image-setup.png)

    Wenn das Basisimage vollständig erweitert wurde, fahren Sie mit dem nächsten Abschnitt fort.

## <a name="package-an-app"></a>Verpacken einer App

Um Ihre App zu verpacken, führen Sie den ``DesktopAppConverter.exe``-Befehl im Konsolenfenster aus, das beim Starten des Desktop App Converters geöffnet wird.  

Sie geben den Paketnamen, Herausgeber und Versionsnummer der App anhand der Parameter an.

> [!NOTE]
> Wenn Sie den Namen Ihrer App im Windows Store reserviert haben, können Sie die Namen des Pakets und des Herausgebers mit dem Windows Dev Center-Dashboard abrufen. Wenn Sie Ihre App auf andere Systeme querladen möchten, können Sie für diese Ihre eigenen Namen bereitstellen, sofern der von Ihnen gewählte Name des Herausgebers mit dem Namen des Zertifikats übereinstimmt, das Sie zum Signieren Ihrer App verwenden.

### <a name="a-quick-look-at-command-parameters"></a>Ein kurzer Überblick der Befehlsparameter

Hier sind die benötigten Parameter.

```CMD
DesktopAppConverter.exe
-Installer <String>
-Destination <String>
-PackageName <String>
-Publisher <String>
-Version <Version>
```
Sie erhalten Informationen über jeden Parameter [hier](#command-reference).

### <a name="examples"></a>Beispiele

Nachfolgend finden Sie einige gängige Methoden zum Verpacken Ihrer App.

* [Verpacken einer App mit einer (.msi) Installer-Datei](#installer-conversion)
* [Verpacken einer App, die eine ausführbare Setup-Datei hat](#setup-conversion)
* [Verpacken einer App, die kein Installationsprogramm besitzt](#no-installer-conversion)
* [Verpacken einer App, Signieren der App, und Vorbereiten der App für die Übermittlung an den Store.](#optional-parameters)

<span id="installer-conversion" />
#### <a name="package-an-app-that-has-an-installer-msi-file"></a>Verpacken einer App mit einer (.msi) Installer-Datei

Weisen Sie auf die Installer-Datei mithilfe der ``Installer``-Parameter.

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.msi -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

> [!NOTE]
> Stellen Sie sicher, dass sich das Installationsprogramm in einem unabhängigen Ordner befindet und nur mit dem Installer verbundene Dateien im selben Ordner sind. Der Konverter kopiert den Inhalt dieses Ordners in die isolierte Windows-Umgebung.

**Video**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-an-Application-That-Has-an-MSI-Installer-Kh1UU2WhD_7106218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="setup-conversion" />
#### Verpacken einer App, die eine ausführbare Setup-Datei hat

Weisen Sie auf die ausführbare Setup-Datei mithilfe der ``Installer``-Parameter.

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.exe -InstallerArguments "/S" -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

Die ``InstallerArguments``-Parameter ist optional. Da der Desktop App Converter jedoch Ihren Installer benötigt, um im unbeaufsichtigten Modus ausgeführt zu werden, müssen Sie ihn verwenden, wenn Ihre App automatische Flags benötigt, um im Hintergrund ausgeführt zu werden. Die ``/S``-Flag ist eine sehr häufig verwendetes automatisches Kennzeichen. Das von Ihnen verwendete Kennzeichen unterscheidet sich jedoch möglicherweise je nach welcher Installer-Technologie Sie beim Erstellen der Setup-Datei verwendet haben.

**Video**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-an-Application-That-Has-a-Setup-exe-Installer-amWit2WhD_5306218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="no-installer-conversion" />
#### Verpacken einer App, die kein Installationsprogramm besitzt

Verwenden Sie in diesem Beispiel den ``Installer``-Parameter, um auf den Stammordner Ihrer App-Dateien zu verweisen.

Verwenden Sie den `AppExecutable`-Parameter, um auf die ausführbare Datei Ihrer Apps zu verweisen.

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyApp\ -AppExecutable MyApp.exe -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

**Video**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-a-No-Installer-Application-agAXF2WhD_3506218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="optional-parameters" />
#### Verpacken einer App, Signieren Sie die App und Ausführen von Validierungstests für das Paket

Dieses Beispiel ähnelt dem vorherigen, da es zeigt, wie Sie Ihre App für das lokale Testen signieren und Ihre App hinsichtlich der Desktop-Brücke- und Windows Store-Anforderungen überprüfen können.

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.exe -InstallerArguments "/S" -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1 -MakeAppx -Sign -Verbose -Verify
```

Der ``Sign``-Parameter generiert ein Zertifikat, mit dem dann Ihre App signiert wird. Sie müssen das erstellte Zertifikat installieren, um Ihre App ausführen zu können. Weitere Informationen hierzu finden Sie unter dem Abschnitt [Ausführung der verpackten App](#run-app) dieses Handbuchs.

Sie können Ihre App anhand der ``Verify``-Parameter überprüfen.

### <a name="a-quick-look-at-optional-parameters"></a>Einen kurzen Überblick über optionale Parameter

Die ``Sign``- und ``Verify``-Parameter sind optional. Es gibt viele weitere optionale Parameter.  Hier sind einige der am häufigsten verwendeten optionalen Parameter.

```CMD
[-ExpandedBaseImage <String>]
[-AppExecutable <String>]
[-AppFileTypes <String>]
[-AppId <String>]
[-AppDisplayName <String>]
[-AppDescription <String>]
[-PackageDisplayName <String>]
[-PackagePublisherDisplayName <String>]
[-MakeAppx]
[-LogFile <String>]
[<CommonParameters>]
```
Sie können mehr über all diese Parameter in den nächsten Abschnitterfahren.

<span id="command-reference" />
### <a name="parameter-reference"></a>Parameterverweis

Hier ist die vollständige Liste der Parameter (nach Kategorie sortiert), die Sie beim Ausführen des Desktop App Converters verwenden können.

* [Setup](#setup-params)
* [Konvertierung](#conversion-params)
* [Paketidentität](#identity-params)
* [Paketmanifest](#manifest-params)
* [Bereinigen](#cleanup-params)
* [Architektur](#architecture-params)
* [Verschiedenes](#other-params)

Sie können auch die gesamte Liste anzeigen, indem Sie den ``Get-Help``-Befehl in der Konsolenfenster-App ausführen.   

||||
|-------------|-----------|-------------|
|<span id="setup-params" /> <strong>Setupparameter</strong>  ||
|-Setup [&lt;SwitchParameter&gt;] |Erforderlich |Führt DesktopAppConverter im Setupmodus aus. Setupmodus unterstützt die Erweiterung eines bereitgestellten Basisimages.|
|-BaseImage &lt;String&gt; | Erforderlich |Vollständiger Pfad zu einem nicht erweiterten Basisimage. Dieser Parameter ist erforderlich, wenn -Setup angegeben wurde.|
| -LogFile &lt;String&gt; |Optional |Gibt eine Protokolldatei an. Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt.|
|-NatSubnetPrefix &lt;String&gt; |Optional |Präfixwert, der für die Nat-Instanz verwendet wird. In der Regel möchten Sie diesen nur ändern, wenn der Hostcomputer an den gleichen Subnetzbereich wie NetNat des Konverters angefügt ist. Sie können die aktuelle NetNat-Konfiguration des Konverters mithilfe des **Get-NetNat**-Cmdlets abrufen. |
|-NoRestart [&lt;SwitchParameter&gt;] |Erforderlich |Keine Aufforderung zum Neustart, wenn Sie das Setupprogramm ausführen (Neustart ist erforderlich, um das Container-Feature zu aktivieren). |
|<span id="conversion-params" /> <strong>Konvertierungsparameter</strong>|||
|-AppInstallPath &lt;String&gt;  |Optional |Der vollständige Pfad zum Stammordner Ihrer Anwendung für die installierten Dateien, wenn sie installiert wurde (z.B. „C:\Programme (x86) \MyApp“).|
|-Destination &lt;String&gt; |Erforderlich |Das gewünschte Ziel für die APPX-Ausgabe des Konverters. DesktopAppConverter kann diesen Speicherort erstellen, wenn er nicht bereits vorhanden ist.|
|-Installer &lt;String&gt; |Erforderlich |Der Pfad zum Installationsprogramm für Ihre Anwendung. Muss im unbeaufsichtigten Modus bzw. automatisch ausgeführt werden können. Bei der Konvertierung ohne Installationsprogramm ist dies der Pfad zum Stammverzeichnis der App-Dateien. |
|-InstallerArguments &lt;String&gt; |Optional |Eine durch Trennzeichen getrennte Liste oder Zeichenfolge mit Argumenten, die das unbeaufsichtigte bzw. automatische Ausführen des Installers erzwingen. Dieser Parameter ist optional, wenn der Installer eine MSI-Datei ist. Geben Sie zum Abrufen eines Protokolls vom Installer hier das Argument für die Protokollierung an, und verwenden Sie den Pfad &lt;log_folder&gt;, ein Token, das vom Konverter mit dem entsprechenden Pfad ersetzt wird. <br><br>**Hinweis**: Unbeaufsichtigte/automatische Flags und Protokollargumente können bei den verschiedenen Installationstechnologien variieren. <br><br>Ein Verwendungsbeispiel für diesen Parameter: -InstallerArguments "/silent /log &lt;log_folder&gt;\install.log" Ein weiteres Beispiel, in dem keine Protokolldatei generiert wird, kann wie folgt aussehen: ```-InstallerArguments "/quiet", "/norestart"``` Alle Protokolle müssen auf den Tokenpfad &lt;log_folder&gt; verweisen, wenn der Konverter diese erfassen und im endgültigen Protokollordner speichern soll.|
|-InstallerValidExitCodes &lt;Int32&gt; |Optional |Eine durch Trennzeichen getrennte Liste mit Exitcodes, die angeben, das der Installer erfolgreich ausgeführt wurde (z. B.: 0, 1234, 5678).  Standardmäßig ist dieser 0 für Nicht-MSI-Dateien und 0, 1641, 3010 für MSI-Dateien.|
|<span id="identity-params" /><strong>Paket-Identitätsparameter</strong>||
|-PackageName &lt;String&gt; |Erforderlich |Der Name des Universellen Windows-App-Pakets |
|-Publisher &lt;String&gt; |Erforderlich |Der Herausgeber des Universellen Windows-App-Pakets |
|-Version &lt;Version&gt; |Erforderlich |Die Versionsnummer für das Universelles Windows-App-Paket |
|<span id="manifest-params" /><strong>Paketmanifest-Parameter</strong>||
|-AppExecutable &lt;String&gt; |Optional |Der Name der ausführbaren Hauptdatei Ihrer Anwendung (z.B. „MyApp.exe“). Dieser Parameter ist bei der Konvertierung ohne Installationsprogramm erforderlich. |
|-AppFileTypes &lt;String&gt;|Optional |Eine durch Trennzeichen getrennte Liste von Dateitypen, denen die Anwendung zugeordnet wird. Beispiel: -AppFileTypes „'.md', '.markdown'“.|
|-AppId &lt;String&gt; |Optional |Legt einen Wert fest, auf den die Anwendungs-ID im Windows-App-Paket-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.|
|-AppDisplayName &lt;String&gt;  |Optional |Legt einen Wert fest, auf den der Anzeigename der Anwendung im Windows-App-Paket-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt. |
|-AppDescription &lt;String&gt; |Optional |Legt einen Wert fest, auf den die Anwendungsbeschreibung im Windows-App-Paket-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.|
|-PackageDisplayName &lt;String&gt; |Optional |Legt einen Wert fest, auf den der Anzeigename des Pakets im Windows-App-Paket-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt. |
|-PackagePublisherDisplayName &lt;String&gt; |Optional |Legt einen Wert fest, auf den der Anzeigename des Paketherausgebers im Windows-App-Paket-Manifest festgelegt wird. Wird kein Wert angegeben, wird dieser auf den für *Publisher* übergebenen Wert festgelegt. |
|<span id="cleanup-params" /><strong>Bereinigungsparameter</strong>|||
|-Bereinigung [&lt;Option&gt;] |Erforderlich |Führt Bereinigung für die DesktopAppConverter-Artefakte aus. Es gibt 3 gültige Optionen für den Bereinigungsmodus. |
|-Alle Bereinigung | |Löscht alle erweiterten Basisimages, entfernt alle temporären Konverterdateien, entfernt das Containernetzwerk und deaktiviert die optionale Windows-Funktion. |
|-WorkDirectory Bereinigung |Erforderlich |Entfernt alle temporären Konverterdateien. |
|-ExpandedImage Bereinigung |Erforderlich |Löscht alle erweiterten Basisimages, die auf dem Hostcomputer installiert sind. |
|<span id="architecture-params" /><strong>Paketarchitekturparameter</strong>|||
|-PackageArch &lt;String&gt; |Erforderlich |Generiert ein Paket mit der angegebenen Architektur. Gültige Optionen sind „x86“ und „x64“ (Beispiel: -PackageArch x86). Dieser Parameter ist optional. Falls nicht angegeben, versucht der DesktopAppConverter die Paketarchitektur automatisch zu erkennen. Wenn die automatische Erkennung fehlschlägt, wird standardmäßig ein x64-Paket erstellt. |
|<span id="other-params" /><strong>Sonstige Parameter</strong>|||
|-ExpandedBaseImage &lt;String&gt;  |Optional |Vollständige Pfad zu einem bereits erweiterten Basisimage.|
|-MakeAppx [&lt;SwitchParameter&gt;]  |Optional |Ein Switch, mit dem, falls vorhanden, dieses Skript zum Aufrufen von MakeAppx für die Ausgabe angewiesen wird. |
|-LogFile &lt;String&gt;  |Optional |Gibt eine Protokolldatei an. Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt. |
| – Zeichen [&lt;SwitchParameter&gt;] |Optional |Weisen Sie diesen Skript an, das ausgehende Windows-App-Paket mit einem generierten Zertifikat für Testzwecke zu signieren. Dieser Switch sollte ebenso vorhanden sein, wie der Switch ```-MakeAppx```. |
|&lt;Allgemeine Parameter&gt; |Erforderlich |Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: *Verbose*, *Debug*, *ErrorAction*, *ErrorVariable*, *WarningAction*, *WarningVariable*, *OutBuffer*, *PipelineVariable* und *OutVariable*. Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216). |
| -Überprüfen [&lt;SwitchParameter&gt;] |Optional |Ein Switch, mit dem DAC angewiesen wird, das verpackte App-Paket auf Anforderungen von Desktop-Brücke und Windows Store zu überprüfen. Das Ergebnis ist ein Überprüfungsbericht „VerifyReport.xml“, der am besten in einem Browser angezeigt wird. Dieser Switch sollte ebenso vorhanden sein, wie der Switch `-MakeAppx`. |
|-PublishComRegistrations| Optional| Scant alle Öffentlichen COM-Registrierungen, die von Ihrem Installer erstellt wurden, und veröffentlicht die gültigen in Ihrem Manifest. Verwenden Sie dieses Flag nur dann, wenn Sie diese Registrierungen für andere Anwendungen verfügbar machen möchten. Sie müssen dieses Flag verwenden, wenn diese Registrierungen nur von Ihrer Anwendung verwendet werden. <br><br>Lesen Sie [diesen Artikel](https://blogs.windows.com/buildingapps/2017/04/13/com-server-ole-document-support-desktop-bridge/#lDg5gSFxJ2TDlpC6.97), um sicherzustellen, dass die COM-Registrierungen nach der Verpackung Ihrer App erwartungsgemäß funktionieren.

<span id="run-app" />
## <a name="run-the-packaged-app"></a>Ausführung der verpackten App

Es gibt zwei Möglichkeiten, Ihre App auszuführen.

Eine Möglichkeit besteht darin, eine PowerShell-Eingabeaufforderung zu öffnen, und den folgenden Befehl einzugeben: ```Add-AppxPackage –Register AppxManifest.xml```. Es ist wahrscheinlich die einfachste Möglichkeit, Ihre App auszuführen, da Sie sie nicht signieren müssen.

Eine weitere Möglichkeit ist das Signieren Ihrer App mit einem Zertifikat. Wenn Sie den ```sign```-Parameter verwenden, generiert der Desktop App Converter eines für Sie und signiert mit diesem anschließend Ihre App. Diese Datei heißt **auto-generated.cer**; Sie finden sie im Stammordner der verpackten App.

Führen Sie die folgenden Schritte aus, um das generierte Zertifikat zu installieren, und führen Sie anschließend Ihre App aus.

1. Doppelklicken Sie auf die Datei **auto-generated.cer**, um das Zertifikat zu installieren.

   ![Datei mit generiertem Zertifikat](images/desktop-to-uwp/generated-cert-file.png)

   > [!NOTE]
   > Wenn Sie zur Eingabe eines Kennworts aufgefordert werden, verwenden Sie das Standardkennwort „123456”.

2. Wählen Sie im Dialogfeld **Zertifikat** die Schaltfläche **Zertifikat installieren** aus.
3. Installieren Sie das Zertifikat im **Zertifikatimport-Assistenten** auf dem **lokalen Computer**, und legen Sie das Zertifikat im Zertifikatspeicher **Vertrauenswürdige Personen** ab.

   ![Speicher für vertrauenswürdige Personen](images/desktop-to-uwp/trusted-people-store.png)

5. Doppelklicken Sie im Stammordner der verpackten App auf die Windows-App-Paketdatei.

   ![Windows-App-Paketdatei](images/desktop-to-uwp/windows-app-package.png)

6. Installieren Sie die App, indem Sie die Schaltfläche **Installieren** auswählen.

   ![Schaltfläche „Installieren”](images/desktop-to-uwp/install.png)


## <a name="modify-the-packaged-app"></a>Ändern der verpackten App

Sie werden wahrscheinlich Änderungen an der verpackten App vornehmen, um Fehler zu beheben, visuelle Ressourcen hinzuzufügen oder die App durch moderne Funktionen wie Live-Kacheln zu verbessern.

Wenn Sie die Änderungen vorgenommen haben, müssen Sie den Konverter nicht erneut ausführen. Sie können Ihre App mithilfe des Tools MakeAppx und der Datei appxmanifest.xml, die der DAC für Ihre App generiert, umpacken. Weitere Informationen erhalten Sie unter [Erstellen eines Windows-App-Pakets](desktop-to-uwp-manual-conversion.md#make-appx).

> [!NOTE]
> Wenn Sie Änderungen an Registrierungseinstellungen vornehmen, die das Installationsprogramm festgelegt hat, müssen Sie den Desktop App Converter erneut ausführen, um diese Änderungen zu übernehmen.

**Videos**

|Ändern und Umpacken der Ausgabe |Demo: Ändern und Umpacken der Ausgabe|
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Modifying-and-Repackaging-Output-from-Desktop-App-Converter-OwpAJ3WhD_6706218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Modify-Output-from-Desktop-App-Converter-gEnsa3WhD_8606218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

In den folgenden zwei Abschnitten werden verschiedene optionale Fixups für die verpackte App beschrieben, die Sie in Erwägung ziehen können.

### <a name="delete-unnecessary-files-and-registry-keys"></a>Löschen nicht benötigter Dateien und Registrierungsschlüssel

Desktop App Converter verfolgt beim Herausfiltern von Dateien und Systemstörungen im Container einen sehr konservativen Ansatz.

Wenn Sie möchten, können Sie den VFS-Ordner überprüfen und alle Dateien löschen, die der Installer nicht benötigt.  Sie können auch den Inhalt von „Reg.dat“ überprüfen und alle Schlüssel löschen, die nicht von der App installiert/benötigt werden.

### <a name="fix-corrupted-pe-headers"></a>Korrigieren fehlerhafter PE-Header

Beim Konvertieren führt DesktopAppConverter automatisch PEHeaderCertFixTool aus, um alle beschädigten PE-Header zu korrigieren. Sie können PEHeaderCertFixTool jedoch auch für ein UWP-Windows-App-Paket, lose Dateien oder eine bestimmte Binärdatei ausführen. Hier sehen Sie ein Beispiel.

```CMD
PEHeaderCertFixTool.exe <binary file>|<.appx package>|&lt;folder> [/c] [/v]
 /c   -- check for corrupted certificate but do not fix (optional)
 /v   -- verbose (optional)
example1: PEHeaderCertFixTool app.exe
example2: PEHeaderCertFixTool c:\package.appx /c
example3: PEHeaderCertFixTool c:\myapp /c /v
```

## <a name="known-issues-and-disclosures"></a>Bekannte Probleme und offenzulegende Informationen

### <a name="known-issues-and-workarounds"></a>Bekannte Probleme und Umgehungen

Hier erfahren Sie mehr über einige bekannte Probleme und einige Maßnahmen, durch die diese sich möglicherweise beheben lassen.

#### <a name="ecreatingisolatedenvfailed-an-estartingisolatedenvfailed-errors"></a>Fehler E_CREATING_ISOLATED_ENV_FAILED und E_STARTING_ISOLATED_ENV_FAILED    

Wenn Sie eine dieser Fehlermeldungen erhalten, stellen Sie sicher, dass Sie ein gültiges Basisimage aus dem [Download Center](https://aka.ms/converterimages) verwenden.
Wenn Sie ein gültiges Basisimage verwenden, versuchen Sie, ``-Cleanup All`` in Ihrem Befehl zu verwenden.
Wenn dies nicht funktioniert, senden Sie uns unter converter@microsoft.com bitte Ihre Protokolle, damit wir den Vorgang untersuchen können.

#### <a name="new-containernetwork-the-object-already-exists-error"></a>New-ContainerNetwork: Fehler „Das Objekt ist bereits vorhanden.”

Dieser Fehler kann angezeigt werden, wenn Sie ein neues Basisimage einrichten. Dies kann passieren, wenn Sie ein Windows-Insider-Test-Flight auf einem Entwicklercomputer erhalten, auf dem zuvor Desktop App Converter installiert wurde.

Um dieses Problem zu beheben, versuchen Sie, den Befehl `Netsh int ipv4 reset` über eine Eingabeaufforderung mit erhöhten Rechten auszuführen, und starten Sie den Computer dann neu.

#### <a name="your-net-app-is-compiled-with-the-anycpu-build-option-and-fails-to-install"></a>Ihre .NET-App wurde mit der Buildoption „AnyCPU” kompiliert und lässt sich nicht installieren

Dies kann vorkommen, wenn die ausführbare Hauptdatei oder eine Abhängigkeitsdatei in der Ordnerhierarchie **Programmdateien** oder **Windows\System32** abgelegt wurde.

Um dieses Problem zu beheben, versuchen Sie, mithilfe Ihres architekturspezifischen Desktop-Installers (32 Bit oder 64 Bit) ein Windows-App-Paket zu generieren.

#### <a name="publishing-public-side-by-side-fusion-assemblies-wont-work"></a>Die Veröffentlichung von öffentlichen parallelen Fusion-Assemblys ist nicht möglich.

 Während der Installation kann eine Anwendung öffentliche parallele Fusion-Assemblys veröffentlichen, auf die von jedem anderen Prozess zugegriffen werden kann. Während der Erstellung des Prozessaktivierungskontexts werden diese Assemblys von einem Systemprozess mit dem Namen CSRSS.exe abgerufen. Wenn dies für einen konvertierten Prozess erfolgt, tritt beim Erstellen des Aktivierungskontexts sowie beim Laden des Moduls dieser Assemblys ein Fehler auf. Die parallelen Fusion-Assemblys werden an folgenden Orten registriert:
  + Registrierung: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners`
  + Dateisystem: %windir%\\SideBySide

Dies ist eine bekannte Einschränkung, und derzeit sind keine Umgehungen vorhanden. Integrierte Assemblys wie z.B. ComCtl sind jedoch Teil des Betriebssystems, sodass entsprechende Abhängigkeiten sicher sind.

#### <a name="error-found-in-xml-the-executable-attribute-is-invalid---the-value-myappexe-is-invalid-according-to-its-datatype"></a>Fehler in XML gefunden. Das Attribut „Ausführbare Datei” ist ungültig. – Der Wert MyApp.EXE ist gemäß dem Datentyp ungültig.

Dies kann vorkommen, wenn die ausführbaren Dateien in Ihrer Anwendung die Erweiterung **. EXE** in Großbuchstaben aufweisen. Obwohl die Groß-/Kleinschreibung dieser Erweiterung keine Auswirkungen auf die Ausführung Ihrer App haben sollte, kann dies dazu führen, dass der DAC diesen Fehler generiert.

Um dieses Problem zu beheben, versuchen Sie, das **-AppExecutable**-Kennzeichen beim Verpacken festzulegen, und verwenden Sie als Erweiterung Ihrer wichtigsten ausführbaren Datei „.exe” in Kleinbuchstaben (z.B.: MYAPP.exe).    Alternativ können Sie die Schreibweise für alle ausführbaren Dateien in Ihrer App von Großbuchstaben zu Kleinbuchstaben ändern (z.B.: von .EXE zu .exe).


### <a name="telemetry-from-desktop-app-converter"></a>Telemetriedaten aus Desktop App Converter

Desktop-App-Konverter erfasst ggf. Informationen über Sie und die Verwendung der Software, und sendet diese Informationen an Microsoft. Weitere Informationen zur Sammlung von Daten und deren Verwendung von Microsoft finden Sie in der Produktdokumentation und in den [Datenschutzbestimmungen von Microsoft](http://go.microsoft.com/fwlink/?LinkId=521839). Sie stimmen der Einhaltung aller geltenden Vorschriften der Datenschutzbestimmungen von Microsoft zu.

Standardmäßig ist Telemetrie für den Desktop-App-Konverter aktiviert. Fügen Sie den folgenden Registrierungsschlüssel hinzu, um Telemetrie entsprechend zu konfigurieren:  

```cmd
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DesktopAppConverter
```
+ Fügen Sie den *DisableTelemetry*-Wert hinzu, oder bearbeiten Sie diesen, indem Sie DWORD auf 1 festlegen.
+ Entfernen Sie zum Aktivieren von Telemetrie den Schlüssel, oder legen Sie den Wert auf 0 fest.

### <a name="language-support"></a>Sprachunterstützung

Desktop App Converter unterstützt Unicode nicht. Daher können keine chinesischen Zeichen oder Nicht-ASCII-Zeichen mit dem Tool verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

**Ausführer Ihrer App/Suchen und Beheben von Problemen**

Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)

**Verteilen Ihrer App**

Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
