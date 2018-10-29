---
author: normesta
Description: This article contains known issues with the Desktop Bridge.
Search.Product: eADQiWindows 10XVcnh
title: Bekannte Probleme (Desktop-Brücke)
ms.author: normesta
ms.date: 06/20/2018
ms.topic: article
keywords: windows10, UWP
ms.assetid: 71f8ffcb-8a99-4214-ae83-2d4b718a750e
ms.localizationpriority: medium
ms.openlocfilehash: 61803e3a4a18dee260b78468c7970a875d8aff73
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5748168"
---
# <a name="known-issues-with-packaged-desktop-applications"></a>Bekannte Probleme mit verpackten desktop-Apps

Dieser Artikel enthält bekannte Probleme, die auftreten können, wenn Sie ein Windows-app-Paket für Ihre desktop-Anwendung erstellen.

<a id="app-converter" />

## <a name="known-issues-with-the-desktop-app-converter"></a>Bekannte Probleme mit dem Desktop App Converter

### <a name="ecreatingisolatedenvfailed-an-estartingisolatedenvfailed-errors"></a>E_CREATING_ISOLATED_ENV_FAILED- und E_STARTING_ISOLATED_ENV_FAILED-Fehler    

Wenn Sie eine dieser Fehlermeldungen erhalten, stellen Sie sicher, dass Sie ein gültiges Basisimage aus dem [Download Center](https://aka.ms/converterimages) verwenden.
Wenn Sie ein gültiges Basisimage verwenden, versuchen Sie, ``-Cleanup All`` in Ihrem Befehl zu verwenden.
Wenn dies nicht funktioniert, senden Sie uns unter converter@microsoft.com bitte Ihre Protokolle, damit wir den Vorgang untersuchen können.

### <a name="new-containernetwork-the-object-already-exists-error"></a>New-ContainerNetwork: Fehler „Das Objekt ist bereits vorhanden.”

Dieser Fehler kann angezeigt werden, wenn Sie ein neues Basisimage einrichten. Dies kann passieren, wenn Sie ein Windows-Insider-Test-Flight auf einem Entwicklercomputer erhalten, auf dem zuvor Desktop App Converter installiert wurde.

Um dieses Problem zu beheben, versuchen Sie, den Befehl `Netsh int ipv4 reset` über eine Eingabeaufforderung mit erhöhten Rechten auszuführen, und starten Sie den Computer dann neu.

### <a name="your-net-application-is-compiled-with-the-anycpu-build-option-and-fails-to-install"></a>Ihre Anwendung .NET wird mit der Buildoption "AnyCPU" kompiliert und Fehler bei der Installation

Dies kann vorkommen, wenn die ausführbare Hauptdatei oder eine Abhängigkeitsdatei in der Ordnerhierarchie **Programmdateien** oder **Windows\System32** abgelegt wurde.

Um dieses Problem zu beheben, versuchen Sie, mithilfe Ihres architekturspezifischen Desktop-Installers (32 Bit oder 64 Bit) ein Windows-App-Paket zu generieren.

### <a name="publishing-public-side-by-side-fusion-assemblies-wont-work"></a>Die Veröffentlichung von öffentlichen parallelen Fusion-Assemblys ist nicht möglich.

 Während der Installation kann eine Anwendung öffentliche parallele Fusion-Assemblys veröffentlichen, auf die von jedem anderen Prozess zugegriffen werden kann. Während der Erstellung des Prozessaktivierungskontexts werden diese Assemblys von einem Systemprozess mit dem Namen CSRSS.exe abgerufen. Wenn dies für einen konvertierten Prozess erfolgt, tritt beim Erstellen des Aktivierungskontexts sowie beim Laden des Moduls dieser Assemblys ein Fehler auf. Die parallelen Fusion-Assemblys werden an folgenden Orten registriert:
  + Registrierung: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners`
  + Dateisystem: %windir%\\SideBySide

Dies ist eine bekannte Einschränkung, und derzeit sind keine Umgehungen vorhanden. Integrierte Assemblys wie z.B. ComCtl sind jedoch Teil des Betriebssystems, sodass entsprechende Abhängigkeiten sicher sind.

### <a name="error-found-in-xml-the-executable-attribute-is-invalid---the-value-myappexe-is-invalid-according-to-its-datatype"></a>Fehler in XML gefunden. Das Attribut „Ausführbare Datei” ist ungültig. – Der Wert MyApp.EXE ist gemäß dem Datentyp ungültig.

Dies kann vorkommen, wenn die ausführbaren Dateien in Ihrer Anwendung die Erweiterung **. EXE** in Großbuchstaben aufweisen. Obwohl die Groß-/Kleinschreibung dieser Erweiterung keine Auswirkungen auf haben, ob die Anwendung ausgeführt wird, kann den DAC diesen Fehler generiert verursachen.

Um dieses Problem zu beheben, versuchen Sie, das **-AppExecutable**-Kennzeichen beim Verpacken festzulegen, und verwenden Sie als Erweiterung Ihrer wichtigsten ausführbaren Datei „.exe” in Kleinbuchstaben (z.B.: MYAPP.exe).    Alternativ können Sie die Groß-/Kleinschreibung für alle ausführbaren Dateien in Ihrer Anwendung aus Kleinbuchstaben in Großbuchstaben ändern (z. B.: aus. EXE .exe).

### <a name="corrupted-or-malformed-authenticode-signatures"></a>Beschädigte oder falsch formatierte Authenticode-Signaturen

Dieser Abschnitt enthält ausführliche Informationen zum Identifizieren von Problemen mit übertragbaren ausführbaren Dateien in Ihrem Windows-App-Paket, die möglicherweise beschädigte oder falsch formatierte Authenticode-Signaturen enthalten. Ungültige Authenticode-Signaturen auf Ihren übertragbaren ausführbaren Dateien, die ein beliebiges binäres Format (z. B. .exe, .dll, chm usw.) aufweisen können, verhindern, dass Ihr Paket ordnungsgemäß signiert wird und aus einem Windows-App-Paket bereitgestellt werden kann.

Die Position der Authenticode-Signatur einer übertragbaren ausführbaren Datei wird durch den Zertifikat-Tabelleneintrag in den optionalen Kopfzeilen-Datenverzeichnissen und der zugehörigen Attributzertifikatstabelle angegeben. Während der Überprüfung der Signatur dienen die Angaben in diesen Strukturen dazu, die Signatur in einer übertragbaren ausführbaren Datei zu suchen. Wenn diese Werte beschädigt werden, kann es so aussehen, als ob eine Datei ungültig signiert wurde.

Damit die Authenticode-Signatur korrekt ist, muss für die Authenticode-Signatur Folgendes gelten:

- Der Anfang des **WIN_CERTIFICATE**-Eintrags in der übertragbaren ausführbaren Datei kann nicht über das Ende der ausführbaren Datei hinausgehen.
- Der **WIN_CERTIFCATE**-Eintrag sollte sich am Ende des Bilds befinden
- Die Größe des **WIN_CERTIFICATE**-Eintrags muss positiv sein
- Der **WIN_CERTIFICATE**-Eintrag muss bei ausführbaren 32-Bit-Dateien nach der **IMAGE_NT_HEADERS32**-Struktur und bei ausführbaren 64-Bit-Dateien nach der IMAGE_NT_HEADERS64-Struktur beginnen.

Weitere Informationen finden Sie in der [Spezifikation zu übertragbaren ausführbaren Authenticode-Dateien](http://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Authenticode_PE.docx) und der [Spezifikation zum Format übertragbarer ausführbarer Dateien](https://msdn.microsoft.com/windows/hardware/gg463119.aspx).

Beachten Sie, dass SignTool.exe eine Liste der beschädigten oder falsch formatierten Binärdateien ausgeben kann, wenn Sie versuchen, ein Windows-App-Paket zu signieren. Aktivieren Sie dazu ausführliche Protokollierung , indem Sie die Umgebungsvariable APPXSIP_LOG auf 1 (z. B. ```set APPXSIP_LOG=1```) festlegen und SignTool.exe erneut ausführen.

Um diese falsch formatierten Binärdateien zu korrigieren, stellen Sie sicher, dass sie den oben angegebenen Anforderungen entsprechen.

## <a name="you-receive-the-error----msb4018-the-generateresource-task-failed-unexpectedly"></a>Sie erhalten die Fehlermeldung: MSB4018 „GenerateResource“ unerwarteter Taskfehler

Dies kann passieren, wenn Sie versuchen, Satellitenassemblys in Paketressourcendateien (Package Resource Index, PRI) zu konvertiert.

Wir kennen das Problem und arbeiten an einer Lösung. Um dieses Problem temporäre zu umgehen, können Sie den Ressourcen-Generator durch Hinzufügen dieser XML-Zeile zum ersten PropertyGroup-Element in der Projektdatei deaktivieren:

``<AppxGeneratePrisForPortableLibrariesEnabled>false</AppxGeneratePrisForPortableLibrariesEnabled>``

## <a name="blue-screen-with-error-code-0x139-kernelsecuritycheckfailure"></a>Blauer Bildschirm mit dem Fehlercode 0x139 (KERNEL_SECURITY_CHECK_FAILURE)

Nach dem Installieren oder Starten bestimmter Apps aus dem Microsoft Store wird Ihr Computer unter Umständen unerwartet mit folgendem Fehler neu gestartet: **0x139 (KERNEL\_SECURITY\_CHECK\_ FAILURE)**.

Bekannte betroffene Apps: Kodi, JT2Go, Ear Trumpet, Teslagrad usw.

Am 27.10.2016 wurde ein [Windows-Update (Version 14393.351 - KB3197954)](https://support.microsoft.com/kb/3197954) veröffentlich, das wichtige Fehlerbehebungen für dieses Problem enthält. Falls bei Ihnen dieses Problem auftritt, aktualisieren Sie Ihren Computer. Falls Sie Ihren PC nicht aktualisieren können, weil er neu gestartet wird, bevor Sie sich anmelden können, müssen Sie die Systemwiederherstellung verwenden, um für Ihr System einen Zeitpunkt herzustellen, der vor der Installation einer der betroffenen Apps liegt. Informationen zur Systemwiederherstellung finden Sie unter [Wiederherstellungsoptionen unter Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).

Falls das Problem durch das Update nicht behoben werden kann oder Sie nicht sicher sind, wie Sie die Wiederherstellung für den PC ausführen, wenden Sie sich an den [Microsoft-Support](https://support.microsoft.com/contactus/).

Wenn Sie Entwickler sind, möchten Sie die Installation Ihres Anwendungspakets unter Versionen von Windows vielleicht verhindern, die dieses Update nicht enthalten. Beachten Sie, dass Ihre Anwendung dadurch nicht für Benutzer verfügbar ist, die das Update noch nicht installiert haben. Um die Verfügbarkeit der Anwendung, um Benutzer zu beschränken, die dieses Update installiert haben, ändern Sie die Datei "appxmanifest.xml" wie folgt:

```<TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.351" MaxVersionTested="10.0.14393.351"/>```

Details zum Windows Update finden Sie hier:
* https://support.microsoft.com/kb/3197954
* https://support.microsoft.com/help/12387/windows-10-update-history

## <a name="common-errors-that-can-appear-when-you-sign-your-app"></a>Häufige Fehler, die beim Signieren Ihrer App angezeigt werden können

### <a name="publisher-and-cert-mismatch-causes-signtool-error-error-signersign-failed--21470248850x8007000b"></a>Nichtübereinstimmung von Herausgeber und Zertifikat führt zum Signtool-Fehler „Fehler: SignerSign() fehlgeschlagen“ (-2147024885/0x8007000b)

Der Herausgeber-Eintrag im Windows-App-Paket-Manifest muss dem Betreff des Zertifikats entsprechen, mit dem signiert wird.  Mit eine der folgenden Methoden können Sie den Betreff des Zertifikats anzeigen.

**Option1: PowerShell**

Führen Sie folgenden PowerShell-Befehl aus. Als Zertifikatdateien können CER- oder PFX-Dateien verwendet werden, da sie über identische Herausgeberinformationen verfügen.

```ps
(Get-PfxCertificate <cert_file>).Subject
```

**Option2: Datei-Explorer**

Doppelklicken Sie im Datei-Explorer auf das Zertifikat, wählen Sie die Registerkarte *Details* aus, und klicken Sie dann in der Liste auf das Feld *Betreff*. Anschließend können Sie die Inhalte kopieren.

**Option3: CertUtil**

Führen Sie **Certutil** auf die PFX-Datei über die Befehlszeile aus, und kopieren Sie das Feld *Betreff* der Ausgabe.

```cmd
certutil -dump <cert_file.pfx>
```

<a id="bad-pe-cert" />

### <a name="bad-pe-certificate-0x800700c1"></a>Ungültiges PE-Zertifikat (0x800700C1)

Dies kann passieren, wenn Ihr Paket eine Binärdatei mit ein beschädigtes Zertifikat enthalten ist. Hier sehen Sie einige Gründe, warum dies geschieht:

* Beginn des Zertifikats ist nicht am Ende eines Bilds.  

* Die Größe des Zertifikats ist nicht positiv.

* Der Zertifikat Start wird nicht nach der `IMAGE_NT_HEADERS32` Struktur für eine 32-Bit-ausführbare Datei oder nach dem die `IMAGE_NT_HEADERS64` Struktur für eine 64-Bit-ausführbare Datei.

* Der Zertifikat-Zeiger ist nicht ordnungsgemäß für eine Struktur WIN_CERTIFICATE ausgerichtet.

Zum Auffinden von Dateien, die eine ungültige PE-Zertifikat enthalten, öffnen Sie ein **Eingabeaufforderungsfenster**, und legen Sie die Umgebungsvariable `APPXSIP_LOG` auf einen Wert von 1.

```
set APPXSIP_LOG=1
```

Signieren Sie dann über die **Befehlszeile**, Ihre Anwendung erneut aus. Beispiel:

```
signtool.exe sign /a /v /fd SHA256 /f APPX_TEST_0.pfx C:\Users\Contoso\Desktop\pe\VLC.appx
```

Informationen zu Dateien, die eine ungültige PE-Zertifikat enthalten, werden im **Konsolenfenster**angezeigt. Beispiel:

```
...

ERROR: [AppxSipCustomLoggerCallback] File has malformed certificate: uninstall.exe

...   
```
## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
