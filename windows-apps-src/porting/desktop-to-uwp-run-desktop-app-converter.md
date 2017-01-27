---
author: awkoren
Description: "Führen Sie Desktop App Converter zum Konvertieren einer Windows-Desktopanwendung (z. B. Win32, WPF und Windows Forms) in eine UWP-App (Universelle Windows-Plattform) aus."
Search.Product: eADQiWindows 10XVcnh
title: Desktop App Converter
translationtype: Human Translation
ms.sourcegitcommit: bf6da2f4d780774819fe7a4abf6367345304767c
ms.openlocfilehash: 3ffd664892fe5ee589d3bf5704e2eeed178bf5f3

---

# <a name="desktop-app-converter"></a>Desktop App Converter

[Laden Sie Desktop App Converter herunter](https://aka.ms/converter)

Desktop App Converter (DAC) ist ein Tool, mit dem Sie vorhandene, für .NET 4.6.1 oder Win32 geschriebene Desktop-Apps für die universelle Windows-Plattform (UWP) konvertieren können. Sie können Ihre Desktop-Installer über den Konverter im unbeaufsichtigten Modus (automatisch) ausführen und ein APPX-Paket abrufen, das Sie mithilfe des Add-AppxPackage-PowerShell-Cmdlets auf Ihrem Entwicklungscomputer installieren können.

Desktop App Converter ist jetzt im [Windows Store](https://aka.ms/converter) erhältlich.

Der Konverter führt den Desktop-Installer in einer isolierten Windows-Umgebung mit einem sauberen Basisimage als Teil des Konverterdownloads aus. Es werden alle Registrierungs- und Dateisystem-E/A des Desktop-Installers erfasst und als Teil der Ausgabe gepackt. Der Konverter gibt ein AppX-Paket mit Paketidentität und der Möglichkeit aus, eine breite Palette von WinRT-APIs aufzurufen.

## <a name="whats-new"></a>Das ist neu:

In diesem Abschnitt werden die Änderungen zwischen den verschiedenen Desktop App Converter-Versionen beschrieben. 

### <a name="12142016-v104"></a>14.12.2016 (v1.0.4)

* Verbesserte Basisimageüberprüfung zur Suche nach ungültigen WIM-Dateien. 
* Programmfehlerbehebung für Sonderzeichen im```-Publisher```-Parameter. 
* Aktualisierte Ressourcen.

### <a name="1122016-v101"></a>02.11.2016 (v1.0.1)

* Verbesserung der Überprüfung des Manifestschemas. 
* Verbesserung der Fehlernachrichten. 
* Hinzufügung der Überprüfung der unterstützten Windows-Versionen. 
* Fehlerkorrekturen für Registrierungsfiltertests.

### <a name="9142016-v10"></a>14.09.2016 (v1.0)

* Desktop App Converter kann jetzt aus dem [Windows Store](https://aka.ms/converter) heruntergeladen werden. 
* Laden Sie die neuesten Windows 10-Basisimages (.wim) für DAC im [Download Center](https://aka.ms/converterimages) herunter.
* Dank der Store-App können Sie jetzt den neuen Einstiegspunkt *DesktopAppConverter.exe <arguments>* zum Ausführen des Konverters von einer beliebigen Stelle einer Eingabeaufforderung mit erhöhten Rechten oder im PowerShell-Fenster verwenden.  


### <a name="922016-v0125"></a>02.09.2016 (v0.1.25)

* Integration des neuesten DotNet-Computervirtualisierungs-NuGet-Pakets.
* Neu eingeführte Abhängigkeiten für common.dll hinzugefügt.
* Mehrere Fehlerbehebungen.

### <a name="842016-v0124"></a>04.08.2016 (v0.1.24)

* Unterstützung für das automatische Signieren der mit DAC konvertierten Apps zu Testzwecken. Versuchen Sie es einmal mit dem Flag ```–Sign```. 
* Warnungen für den Fall, dass eine der COM-Registrierungen in der virtuellen Registrierungsstruktur vom APPX-Paket nicht unterstützt werden.  
* Unterstützung für das automatische Erkennen der App-Abhängigkeiten in VC++-Bibliotheken sowie das anschließende Konvertieren in APPX-Manifestabhängigkeiten. Beachten Sie, dass Sie zum Querladen und Testen von Apps mit der VC++-Laufzeit die VCLib-Frameworkpakete herunterladen müssen. Weitere Informationen hierzu finden Sie im Blogbeitrag [Using Visual C++ Runtime in a Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (in englischer Sprache). Navigieren Sie auf Ihrem Computer zu den Paketen im Ordner ```Program Files (x86)\Microsoft SDKs\Windows Kits\10\ExtensionSDKs\Microsoft.VCLibs.Desktop``` und anschließend zur erforderlichen Version (z. B. 11.0, 12.0, 14.0), und doppelklicken Sie auf das entsprechende Architekturpaket (X64, X86), um es zu installieren.
* Manifestschema wurde für das Windows 10 Anniversary Update (10.0.14393.0) aktualisiert. 
* Mehrere Fehlerbehebungen und verbessertes Ausgabelayout. 

### <a name="772016-v0122"></a>07.07.2016 (v0.1.22)

* Unterstützung für die automatische Erkennung von Shellerweiterungen in Ihrer Desktopanwendung und für die Deklaration der Erweiterungen in der APPXMANIFEST-Datei Ihres UWP-Pakets wurde hinzugefügt. Weitere Informationen zu den Desktoperweiterungen finden Sie unter [**Erweiterungen für konvertierte Desktop-Apps**](desktop-to-uwp-extensions.md). 
* Die AppExecutable-Erkennung bei einer großen Menge von Apps wurde verbessert. 

### <a name="6162016-v0120"></a>16.06.2016 (v0.1.20)

* Probleme beim Konvertieren für die neuesten Windows 10 Insider Preview-Builds wurden behoben. 
* ```–CreateX86Package``` wurde durch ```–PackageArch``` ersetzt. Dies ermöglicht das Angeben der Architektur für das generierte Paket. 

### <a name="682016"></a>08.06.2016

* Unterstützung für die Generierung von x86-appx-Paketen auf AMD64-Hostrechnern hinzugefügt, auf denen der Konverter ausgeführt wird.
* Speicherplatzverwendung durch Entfernen aller zuvor erweiterter Basisimages reduziert.
* Unterstützung für das Bereinigen temporärer Dateien und aller unnötigen Basisimages hinzugefügt.
* Unterstützung für das Erkennen von Dateityp- und Protokollzuordnungen verbessert.
* Logik zum Ermitteln der AppExecutable-Eigenschaft für eine große Anzahl von Apps verbessert.
* Unterstützung für die Bereitstellung zusätzlicher –InstallerArguments für MSI-basierte Installationsprogramme hinzugefügt.
* Fehlerkorrekturen für alle PathTooLongException-Fehler während der Konvertierung.

### <a name="5122016"></a>12.05.2016

- Unterstützung für Pro-Edition von Windows wiederhergestellt. 
- Konverter-```-Setup```-Markierung aktiviert nun Windows-Container-Feature und verarbeitet Basisimage-Erweiterung. Führen Sie Folgendes an einer PowerShell-Eingabeaufforderung mit erhöhten Rechten für die einmalige Einrichtung aus: ```PS C:\> .\DesktopAppConverter.ps1 -Setup -BaseImage BaseImage-12345.wim -Verbose```
- Automatische Erkennung des App-Installationspfads hinzugefügt und Anwendungsstamm außerhalb von VFS verschoben, um alle nicht benötigten Dateisystemumleitungen zur Laufzeit zu verringern.
- Automatische Erkennung des erweiterten Basisimage als Teil des Konvertierungsprozesses hinzugefügt.
- Automatische Erkennung für Dateitypzuordnungen und Protokolle hinzugefügt.
- Logik zum Erkennen der Startmenüverknüpfung verbessert.
- Dateisystemfilter zum Beibehalten der von der App installierten MUI-Dateien verbessert.
- Die unterstützte Desktop-Mindestversion (10.0.14342.0) wurde im Manifest aktualisiert.

## <a name="system-requirements"></a>Systemanforderungen

### <a name="operating-system"></a>Betriebssystem

+ Windows 10 Anniversary Update (10.0.14393.0 und höher) Pro oder Enterprise Edition.

### <a name="hardware-configuration"></a>Hardwarekonfiguration

+ 64-Bit (x64)-Prozessor
+ Hardwareunterstützte Virtualisierung
+ Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)

### <a name="required-resources"></a>Erforderliche Ressourcen

+ [Windows Software Development Kit (SDK) für Windows 10](https://go.microsoft.com/fwlink/?linkid=821375)

## <a name="set-up-the-desktop-app-converter"></a>Einrichten von Desktop App Converter

Desktop App Converter basiert auf den neuesten Windows 10-Features. Stellen Sie sicher, dass Sie Windows 10 Anniversary Update (14393.0) oder spätere Builds verwenden.

1.  Laden Sie [DesktopAppConverter aus dem Windows Store](https://aka.ms/converter) herunter sowie die [WIM-Basisimage-Datei, die dem Build entspricht](https://aka.ms/converterimages).  
2.  Führen Sie DesktopAppConverter als Administrator aus. Klicken Sie dazu im Startmenü mit der rechten Maustaste auf die Kachel, und wählen Sie unter *More* die Option *Als Administrator ausführen* aus, oder klicken Sie in der Taskleiste mit der rechten Maustaste auf die Kachel, klicken Sie ein zweites Mal mit der rechten Maustaste auf den angezeigten App-Namen, und wählen Sie anschließend *Als Administrator ausführen*.
3.  Führen Sie im Konsolenfenster der App ```Set-ExecutionPolicy bypass``` aus.
4.  Richten Sie den Konverter ein, indem Sie im Konsolenfenster der App ```DesktopAppConverter.exe -Setup -BaseImage .\BaseImage-1XXXX.wim -Verbose``` ausführen.
5.  Wenn Sie beim Ausführen des vorherigen Befehls zum Neustart aufgefordert werden, starten Sie den Computer neu.

## <a name="run-the-desktop-app-converter"></a>Ausführen von Desktop App Converter

+ **Herunterladen aus dem Store**: Verwenden Sie ```DesktopAppConverter.exe``` zum Ausführen des Konverters.

### <a name="usage"></a>Verwendungszweck

```CMD
DesktopAppConverter.exe
-Installer <String> [-InstallerArguments <String>] [-InstallerValidExitCodes <Int32>]
-Destination <String>
-PackageName <String>
-Publisher <String>
-Version <Version>
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

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht, wie eine Desktop-App mit dem Namen *MyApp* von *&lt;Herausgebername&gt;* in ein UWP-Paket (APPX) konvertiert wird.

```CMD
DesktopAppConverter.exe -Installer C:\Installer\MyApp.exe 
-InstallerArguments "/S" -Destination C:\Output\MyApp -PackageName "MyApp" 
-Publisher "CN=<publisher_name>" -Version 0.0.0.1 -MakeAppx -Verbose
```

## <a name="deploy-your-converted-appx"></a>Bereitstellen des konvertierten APPX-Pakets

Verwenden Sie das [Add-AppxPackage](https://technet.microsoft.com/library/hh856048.aspx)-Cmdlet in PowerShell zum Bereitstellen eines signierten App-Pakets (.appx) für ein Benutzerkonto. 

Sie können Ihre konvertierte App mit dem Flag ```-Sign``` in Desktop App Converter (v0.1.24) automatisch signieren. Unter [Signieren der konvertierten Desktop-App](desktop-to-uwp-signing.md) erfahren Sie zudem, wie Sie selbstsignierende APPX-Pakete erstellen können.

Sie können auch den ```-Register```-Parameter des PowerShell-Cmdlets Add-AppXPackage verwenden, um eine Installation von einem Ordner mit nicht gepackten Dateien während des Entwicklungsprozesses vorzunehmen. 

Weitere Informationen zum Bereitstellen und Debuggen der konvertierten App finden Sie unter [Bereitstellen und Debuggen der konvertierten UWP-App](desktop-to-uwp-deploy-and-debug.md). 

## <a name="sign-your-appx-package"></a>Signieren des APPX-Pakets

Das Add-AppxPackage-Cmdlet erfordert, dass das bereitgestellte Anwendungspaket (.appx) signiert ist. Verwenden Sie das Flag ```-Sign``` als Teil der Konverter-Befehlszeile oder von SignTool.exe (im Microsoft Windows 10 SDK enthalten), um das APPX-Paket zu signieren.

Weitere Informationen zum Signieren des APPX-Pakets finden Sie unter [Signieren der konvertierten Desktop-App](desktop-to-uwp-signing.md). 

Hinweis: Wenn Sie versuchen, ein Paket mit dem automatisch generierten Zertifikat zu signieren, müssen Sie das Standardkennwort „123456“ verwenden.

## <a name="modify-vfs-folder-and-registry-hive-optional"></a>Ändern des VFS-Ordners und der Registrierungsstruktur (optional)

Desktop App Converter verfolgt beim Herausfiltern von Dateien und Systemstörungen im Container einen sehr konservativen Ansatz.  Nach der Konvertierung können Sie folgende Aktionen ausführen (dies ist jedoch nicht erforderlich):

1. Überprüfen Sie den VFS-Ordner, und löschen Sie alle Dateien, die vom Installationsprogramm nicht benötigt werden.
2. Überprüfen Sie den Inhalt von „Reg.dat“, und löschen Sie alle Schlüssel, die nicht von der App installiert werden/erforderlich sind.

Wenn Sie an der konvertierten App Änderungen vornehmen (einschließlich der oben genannten), müssen Sie den Konverter nicht erneut ausführen. Sie können für Ihre App mit dem MakeAppx-Tool und der von DAC generierten Datei „appxmanifest.xml“ manuell ein neues Paket für Ihre App erstellen. Hilfe hierzu finden Sie unter [Manuelles Konvertieren Ihrer App zu UWP mithilfe der Desktop-Brücke](desktop-to-uwp-manual-conversion.md).

## <a name="caveats"></a>Einschränkungen

1. Der Windows 10-Build auf dem Hostcomputer muss mit dem Basisimage übereinstimmen, das Sie im Rahmen des Desktop App Converter-Downloads erhalten haben.  
2. Stellen Sie sicher, dass sich der Desktop-Installer in einem unabhängigen Verzeichnis befindet, da der Konverter alle Verzeichnisinhalte in eine isolierte Windows-Umgebung kopiert.  
3. Der Desktop-App-Konverter unterstützt den Konvertierungsprozess derzeit nur unter 64-Bit-Versionen des Betriebssystems. Sie können die konvertierten Appx-Pakete nur für 64-Bit-Versionen (x64) des Betriebssystems bereitstellen.  
4. Für den Desktop-App-Konverter muss der Desktop-Installer im unbeaufsichtigten Modus ausgeführt werden. Stellen Sie sicher, dass Sie das automatische Kennzeichen an den Installer für den Konverter mithilfe des *-InstallerArguments*-Parameters übergeben.
5. Die Veröffentlichung von öffentlichen SxS Fusion-Assemblys ist nicht möglich. Während der Installation kann eine Anwendung öffentliche parallele Fusion-Assemblys veröffentlichen, auf die von jedem anderen Prozess zugegriffen werden kann. Während der Erstellung des Prozessaktivierungskontexts werden diese Assemblys von einem Systemprozess mit dem Namen CSRSS.exe abgerufen. Wenn dies für einen konvertierten Prozess erfolgt, tritt beim Erstellen des Aktivierungskontexts sowie beim Laden des Moduls dieser Assemblys ein Fehler auf. Integrierte Assemblys wie z. B. ComCtl sind Teil des Betriebssystems, sodass entsprechende Abhängigkeiten sicher sind. Die SxS Fusion-Assemblys werden an folgenden Orten registriert:
  + Registrierung: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners`
  + Dateisystem: %windir%\\SideBySide

## <a name="known-issues"></a>Bekannte Probleme

* Momentan untersuchen wir die folgenden Fehler, die bei einigen OS-Builds auftreten:
    
    * ```E_CREATTING_ISOLATED_ENV_FAILED```
    * ```E_STARTING_ISOLATED_ENV_FAILED```
    
    Falls bei Ihnen einer dieser Fehler auftritt, stellen Sie sicher, dass Sie ein gültiges Basisimage aus dem [Download Center](https://aka.ms/converterimages) verwenden. Wenn Sie eine gültige WIM-Datei verwenden, senden Sie Ihre Protokolle an „converter@microsoft.com“, damit wir dieses Problem lösen können. 

* Wenn Sie ein Windows-Insider-Test-Flight auf einem Entwicklercomputer erhalten, auf dem zuvor Desktop App Converter installiert war, erhalten Sie bei der Einrichtung des neuen Basisimages möglicherweise den Fehler `New-ContainerNetwork: The object already exists`. Um dieses Problem zu umgehen, führen Sie den Befehl `Netsh int ipv4 reset` an einer Eingabeaufforderung mit erhöhten Rechten aus, und starten Sie den Computer dann neu. 

* Die Installation einer mit der Buildoption „AnyCPU“ kompilierten .NET-App schlägt fehl, wenn die ausführbare Hauptdatei oder eine Abhängigkeit unter „Programme“ oder „Windows\System32“ abgelegt wurden. Um dieses Problem zu umgehen, verwenden Sie das Desktop-Installationsprogramm für Ihre Architektur (32-Bit oder 64-Bit), um ein AppX-Paket erfolgreich zu generieren.

## <a name="telemetry-from-desktop-app-converter"></a>Telemetriedaten aus Desktop-App-Konverter

Desktop-App-Konverter erfasst ggf. Informationen über Sie und die Verwendung der Software, und sendet diese Informationen an Microsoft. Weitere Informationen zur Sammlung von Daten und deren Verwendung von Microsoft finden Sie in der Produktdokumentation und in den [Datenschutzbestimmungen von Microsoft](http://go.microsoft.com/fwlink/?LinkId=521839). Sie stimmen der Einhaltung aller geltenden Vorschriften der Datenschutzbestimmungen von Microsoft zu.

Standardmäßig ist Telemetrie für den Desktop-App-Konverter aktiviert. Fügen Sie den folgenden Registrierungsschlüssel hinzu, um Telemetrie entsprechend zu konfigurieren:  

```cmd
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DesktopAppConverter
```
+ Fügen Sie den *DisableTelemetry*-Wert hinzu, oder bearbeiten Sie diesen, indem Sie DWORD auf 1 festlegen.
+ Entfernen Sie zum Aktivieren von Telemetrie den Schlüssel, oder legen Sie den Wert auf 0 fest.

## <a name="desktop-app-converter-usage"></a>Nutzung des Desktop-App-Konverters

Im Folgenden finden Sie eine Liste der Parameter für Desktop App Converter. Sie können diese Liste auch anzeigen, indem Sie Folgendes ausführen:   

```CMD
Get-Help DesktopAppConverter.exe -detailed
```

### <a name="setup-parameters"></a>Setupparameter  

|Parameter|Beschreibung|
|---------|-----------|
|```-Setup [<SwitchParameter>]``` | Führt DesktopAppConverter im Setupmodus aus. Setupmodus unterstützt die Erweiterung eines bereitgestellten Basisimages.|
|```-BaseImage <String>``` | Vollständiger Pfad zu einem nicht erweiterten Basisimage. Dieser Parameter ist erforderlich, wenn -Setup angegeben wurde.|
|```-LogFile <String>``` [optional] | Gibt eine Protokolldatei an. Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt.|
|```-NatSubnetPrefix <String>``` [optional] | Präfixwert, der für die Nat-Instanz verwendet wird. In der Regel möchten Sie diesen nur ändern, wenn der Hostcomputer an den gleichen Subnetzbereich wie NetNat des Konverters angefügt ist. Sie können die aktuelle NetNat-Konfiguration des Konverters mithilfe des **Get-NetNat**-Cmdlets abrufen. |
|```-NoRestart [<SwitchParameter>]``` | Keine Aufforderung zum Neustart, wenn Sie das Setupprogramm ausführen (Neustart ist erforderlich, um das Container-Feature zu aktivieren). |

### <a name="conversion-parameters"></a>Konvertierungsparameter  

|Parameter|Beschreibung|
|---------|-----------|
|```-AppInstallPath <String> [optional]``` | Der vollständige Pfad zum Stammordner Ihrer Anwendung für die installierten Dateien, wenn sie installiert wurde (z. B. „C:\Programme (x86) \MyApp“).| 
|```-Destination <String>``` | Das gewünschte Ziel für die APPX-Ausgabe des Konverters. DesktopAppConverter kann diesen Speicherort erstellen, wenn er nicht bereits vorhanden ist.|
|```-Installer <String>``` | Der Pfad zum Installer für Ihre Anwendung. Muss im unbeaufsichtigten Modus bzw. automatisch ausgeführt werden können.|
|```-InstallerArguments <String>``` [optional] | Eine durch Trennzeichen getrennte Liste oder Zeichenfolge mit Argumenten, die das unbeaufsichtigte bzw. automatische Ausführen des Installers erzwingen. Dieser Parameter ist optional, wenn der Installer eine MSI-Datei ist. Geben Sie zum Abrufen eines Protokolls vom Installer hier das Argument für die Protokollierung an, und verwenden Sie den Pfad ```<log_folder>```, ein Token, das vom Konverter mit dem entsprechenden Pfad ersetzt wird. <br><br>**Hinweis: Unbeaufsichtigte/automatische Flags und Protokollargumente können bei den verschiedenen Installationstechnologien variieren.** <br><br>Ein Verwendungsbeispiel für diesen Parameter: ```-InstallerArguments "/silent /log <log_folder>\install.log"``` Ein weiteres Beispiel, in dem keine Protokolldatei generiert wird, kann wie folgt aussehen: ```-InstallerArguments "/quiet", "/norestart"``` Alle Protokolle müssen auf den Tokenpfad ```<log_folder>``` verweisen, wenn der Konverter diese erfassen und im endgültigen Protokollordner speichern soll.|
|```-InstallerValidExitCodes <Int32>``` [optional] | Eine durch Trennzeichen getrennte Liste mit Exitcodes, die angeben, das der Installer erfolgreich ausgeführt wurde (z. B.: 0, 1234, 5678).  Standardmäßig ist dieser 0 für Nicht-MSI-Dateien und 0, 1641, 3010 für MSI-Dateien.|

### <a name="appx-identity-parameters"></a>APPX-Identitätsparameter  

|Parameter|Beschreibung|
|---------|-----------|
|```-PackageName <String>``` | Der Name des UWP-Pakets
|```-Publisher <String>``` | Der Herausgeber des UWP-Pakets
|```-Version <Version>``` | Die Versionsnummer für das UWP-Paket

### <a name="optional-appx-manifest-parameters"></a>Optionale APPX-Manifestparameter  

|Parameter|Beschreibung|
|---------|-----------|
|```-AppExecutable <String> [optional]``` [optional] | Der Name der ausführbaren Hauptdatei Ihrer Anwendung (z. B. „MyApp.exe“). |
|```-AppFileTypes <String>``` [optional] | Eine durch Trennzeichen getrennte Liste von Dateitypen, denen die Anwendung zugeordnet wird (z. B. „txt, .doc“, ohne die Anführungszeichen).|
|```-AppId <String>``` [optional] | Gibt einen Wert fest, auf den die Anwendungs-ID im appx-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.|
|```-AppDisplayName <String>``` [optional] | Gibt einen Wert fest, auf den der Anzeigename der Anwendung im appx-Manifest festgelegt wird. Wird kein Wert angegeben, wird dieser auf den für *PackageName* übergebenen Wert festgelegt. |
|```-AppDescription <String>``` [optional] | Gibt einen Wert fest, auf den die Anwendungsbeschreibung im appx-Manifest festgelegt wird. Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.|
|```-PackageDisplayName <String>``` [optional] | Gibt einen Wert fest, auf den der Anzeigename des Pakets im appx-Manifest festgelegt wird. Wird kein Wert angegeben, wird dieser auf den für *PackageName* übergebenen Wert festgelegt. |
|```-PackagePublisherDisplayName <String>``` [optional] | Gibt einen Wert fest, auf den der Anzeigename des Paketherausgebers im appx-Manifest festgelegt wird. Wird kein Wert angegeben, wird dieser auf den für *Publisher* übergebenen Wert festgelegt. |

### <a name="other-conversion-parameters"></a>Weitere Konvertierungsparameter  

|Parameter|Beschreibung|
|---------|-----------|
|```-ExpandedBaseImage <String>``` [optional] | Vollständige Pfad zu einem bereits erweiterten Basisimage.|
|```-MakeAppx [<SwitchParameter>]``` [optional] | Ein Switch, mit dem, falls vorhanden, dieses Skript zum Aufrufen von MakeAppx für die Ausgabe angewiesen wird. |
|```-LogFile <String>``` [optional] | Gibt eine Protokolldatei an. Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt. |
| ```Sign [<SwitchParameter>] [optional]``` | Weist dieses Skript zum Signieren der APPX-Ausgabe an. Dieser Switch sollte ebenso vorhanden sein, wie der Switch ```-MakeAppx```. 
|```<Common parameters>``` | Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: *Verbose*, *Debug*, *ErrorAction*, *ErrorVariable*, *WarningAction*, *WarningVariable*, *OutBuffer*, *PipelineVariable* und *OutVariable*. Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216). |

### <a name="cleanup-parameters"></a>BereinigungsParameter

|Parameter|Beschreibung|
|---------|-----------|
|```Cleanup [<Option>]``` | Führt Bereinigung für die DesktopAppConverter-Artefakte aus. Es gibt 3 gültige Optionen für den Bereinigungsmodus. |
|```Cleanup All``` | Löscht alle erweiterten Basisimages, entfernt alle temporären Konverterdateien, entfernt das Containernetzwerk und deaktiviert die optionale Windows-Funktion. |
|```Cleanup WorkDirectory``` | Entfernt alle temporären Konverterdateien. |
|```Cleanup ExpandedImage``` | Löscht alle erweiterten Basisimages, die auf dem Hostcomputer installiert sind. |

### <a name="package-architecture"></a>Paketarchitektur

Desktop App Converter unterstützt jetzt das Erstellen von x86- und x64-App-Paketen, die Sie auf x86- und amd64-Computern ausführen können. Beachten Sie, dass der Desktop-App-Konverter weiterhin auf einem AMD64-Computer ausgeführt werden muss, um eine erfolgreiche Konvertierung durchzuführen.

|Parameter|Beschreibung|
|---------|-----------|
|```-PackageArch <String>``` | Generiert ein Paket mit der angegebenen Architektur. Gültige Optionen sind „x86“ und „x64“ (Beispiel: -PackageArch x86). Dieser Parameter ist optional. Falls nicht angegeben, versucht der DesktopAppConverter die Paketarchitektur automatisch zu erkennen. Wenn die automatische Erkennung fehlschlägt, wird standardmäßig ein x64-Paket erstellt. 

### <a name="running-the-peheadercertfixtool"></a>Ausführen von PEHeaderCertFixTool

Beim Konvertieren führt DesktopAppConverter automatisch PEHeaderCertFixTool aus, um alle beschädigten PE-Header zu korrigieren. Sie können PEHeaderCertFixTool jedoch auch für UWP-APPX, lose Dateien oder eine bestimmte Binärdatei ausführen. Beispielanwendung: 

```CMD
PEHeaderCertFixTool.exe <binary file>|<.appx package>|<folder> [/c] [/v]
 /c   -- check for corrupted certificate but do not fix (optional)
 /v   -- verbose (optional)
example1: PEHeaderCertFixTool app.exe
example2: PEHeaderCertFixTool c:\package.appx /c
example3: PEHeaderCertFixTool c:\myapp /c /v
```

## <a name="language-support"></a>Sprachunterstützung

Desktop App Converter unterstützt Unicode nicht. Daher können keine chinesischen Zeichen oder Nicht-ASCII-Zeichen mit dem Tool verwendet werden.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

+ [Migrieren von Desktop-Apps zur universellen Windows-Plattform mit Desktop App Converter](https://channel9.msdn.com/events/Build/2016/P504)
+ [Project Centennial: Migrieren vorhandener Desktopanwendungen zur universellen Windows-Plattform](https://channel9.msdn.com/events/Build/2016/B829)  


<!--HONumber=Dec16_HO3-->


