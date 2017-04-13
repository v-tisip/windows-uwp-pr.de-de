---
author: normesta
Description: "In diesem Artikel wird erläutert, wie Sie eine Desktop-App signieren, die Sie für die universelle Windows-Plattform (UWP) konvertiert haben."
Search.Product: eADQiWindows 10XVcnh
title: "Anmelden der Desktop-zu-UWP-Brücke"
ms.author: normesta
ms.date: 03/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 232c3012-71ff-4f76-a81e-b1758febb596
ms.openlocfilehash: bed23b75a966e3a858d1e34a686fa3ba2730354c
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="desktop-to-uwp-bridge-sign"></a>Anmelden der Desktop-zu-UWP-Brücke

In diesem Artikel wird erläutert, wie Sie eine Desktop-App signieren, die Sie für die universelle Windows-Plattform (UWP) konvertiert haben. Sie müssen Ihr Windows-App-Paket mit einem Zertifikat signieren, bevor Sie es bereitstellen können.

## <a name="automatically-sign-using-the-desktop-app-converter-dac"></a>Automatisches Signieren mit Desktop App Converter (DAC)

Verwenden Sie beim Ausführen von DAC das Flag ```-Sign```, um Ihr Windows-App-Paket automatisch zu signieren. Weitere Informationen finden Sie unter [Vorschau für Desktop App Converter](desktop-to-uwp-run-desktop-app-converter.md).

## <a name="manually-sign-using-signtoolexe"></a>Manuelles Signieren mit „SignTool.exe“

Erstellen Sie zunächst ein Zertifikat mit MakeCert.exe. Wenn Sie zur Eingabe eines Kennworts aufgefordert werden, wählen Sie „None“ aus.

```cmd
C:\> MakeCert.exe -r -h 0 -n "CN=<publisher_name>" -eku 1.3.6.1.5.5.7.3.3 -pe -sv <my.pvk> <my.cer>
```

Kopieren Sie als Nächstes unter Verwendung von „pvk2pfx.exe“ die Informationen für den öffentlichen und privaten Schlüssel in das Zertifikat.

```cmd
C:\> pvk2pfx.exe -pvk <my.pvk> -spc <my.cer> -pfx <my.pfx>
```
Verwenden Sie zum Schluss „SignTool.exe“, um Ihr Windows-App-Paket mit dem Zertifikat zu signieren.

```cmd
C:\> signtool.exe sign -f <my.pfx> -fd SHA256 -v .\<outputAppX>.appx
```

Weitere Informationen finden Sie unter [Signieren eines App-Pakets mit SignTool](https://msdn.microsoft.com/library/windows/desktop/jj835835.aspx).

Alle drei oben aufgeführten Tools sind in der Microsoft Windows 10 SDK enthalten. Um diese direkt aufrufen, rufen Sie das Skript ```C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat``` über eine Befehlszeile auf.

## <a name="common-errors"></a>Häufige Fehler

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

Führen Sie **CertUtil** über die Befehlszeile für die PFX-Datei aus, und kopieren Sie das Feld *Betreff* der Ausgabe.

```cmd
certutil -dump <cert_file.pfx>
```

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

## <a name="see-also"></a>Weitere Informationen

- [SignTool](https://msdn.microsoft.com/library/windows/desktop/aa387764.aspx)
- [SignTool.exe (Signaturtool)](https://msdn.microsoft.com/library/8s9b9yaz.aspx)
- [Signieren eines App-Pakets mithilfe von SignTool](https://msdn.microsoft.com/library/windows/desktop/jj835835.aspx)
