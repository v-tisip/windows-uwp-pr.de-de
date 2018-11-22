---
author: laurenhughes
title: Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“
description: MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln.
ms.author: lahugh
ms.date: 06/21/2018
ms.topic: article
keywords: windows10, uwp, verpackung
ms.assetid: 7c1c3355-8bf7-4c9f-b13b-2b9874b7c63c
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: aad7244d90b9025dbbec37013edfb31b068a8abc
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7563043"
---
# <a name="create-an-app-package-with-the-makeappxexe-tool"></a>Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“


**MakeAppx.exe** erstellt sowohl App-Pakete als auch App-Bündel. **MakeAppx.exe** extrahiert darüber hinaus Dateien aus einem App-Paket oder -Bündel und verschlüsselt und entschlüsselt App-Pakete und App-Bündel. Dieses Tool ist im Windows10 SDK enthalten und kann über eine Eingabeaufforderung oder eine Skriptdatei verwendet werden.

> [!IMPORTANT] 
> Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen des App-Pakets verwenden. Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).

Beachten Sie, dass **MakeAppx.exe** keine APPXUPLOAD-Datei erstellt. Die appxupload-Datei wird als Teil des Visual Studio-verpackungsvorgangs erstellt und enthält zwei weitere Dateien: .msix oder AppX- und appxsym. Die appxsym-Datei ist eine komprimierte PDB-Datei enthält öffentliche Symbole Ihrer App für den [Absturz Analytics](../publish/health-report.md) im Partner Center verwendet. Eine reguläre APPX-Datei kann ebenfalls übermittelt werden. In diesem Fall sind jedoch keine Absturzanalysen oder Informationen zum Debuggen verfügbar. Weitere Informationen zum Übermitteln von Paketen an den Store finden Sie unter [Hochladen von App-Paketen](../publish/upload-app-packages.md). 

 Updates für das Tool in der neuesten Version von Windows 10 haben keinen Einfluss auf die Nutzung der AppX-Paket. Sie können auch weiterhin mit diesem Tool mit AppX-Paketen oder verwenden Sie das Tool mit Unterstützung für .msix Pakete wie unten beschrieben.

So erstellen Sie manuell eine APPXUPLOAD-Datei:
- Platzieren Sie die .msix und die appxsym-Datei in einem Ordner
- Zippen Sie den Ordner.
- Ändern Sie den Namen der Erweiterung des komprimierten Ordners von ZIP in APPXUPLOAD.

## <a name="using-makeappxexe"></a>Verwenden der MakeAppx.exe

Abhängig vom Installationspfad des SDK befindet sich **MakeAppx.exe** an folgenden Speicherorten auf Ihrem Windows10-PC:
- X86: C:\Program Files (x86) \Windows Kits\10\bin\\&lt;build-Nummer&gt;\x86\makeappx.exe
- X64: C:\Program Files (x86) \Windows Kits\10\bin\\&lt;build-Nummer&gt;\x64\makeappx.exe

Es gibt keine ARM-Version dieses Tools.

### <a name="makeappxexe-syntax-and-options"></a>MakeAppx.exe-Syntax und -Optionen

Allgemeine **MakeAppx.exe**-Syntax:

``` Usage
MakeAppx <command> [options]      
```

Die folgende Tabelle enthält die Befehle für **MakeAppx.exe**.

| **Befehl**   | **Beschreibung**                       |
|---------------|---------------------------------------|
| pack          | Erstellt ein Paket.                    |
| unpack        | Extrahiert alle Dateien im angegebenen Paket in das angegebene Ausgabeverzeichnis. |
| bundle        | Erstellt ein Bündel.                     |
| unbundle      | Entpacken alle Pakete in ein Unterverzeichnis am angegebenen Ausgabepfad, der nach dem vollständigen Namen des Bündels benannt ist. |
| encrypt       | Erstellt ein verschlüsseltes App-Paket oder -Bündel aus dem Eingabepaket/-bündel am angegebenen Ausgabepaket/-bündel. |
| decrypt       | Erstellt ein entschlüsseltes App-Paket oder -Bündel aus dem Eingabe-App-Paket/-Bündel am angegebenen Ausgabepaket/-bündel. |


Die folgende Liste von Optionen gilt für alle Befehle:

| **Option**    | **Beschreibung**                       |
|---------------|---------------------------------------|
| /d            | Gibt das Eingabe-, Ausgabe- oder Inhaltsverzeichnis an. |
| /l            | Wird für lokalisierte Pakete verwendet. Die Standardüberprüfung wird durch lokalisierte Pakete ausgelöst. Diese Option deaktiviert nur diese spezifische Überprüfung, ohne dass die gesamte Überprüfung deaktiviert werden muss. |
| /kf           | Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des Schlüssels aus der angegebenen Schlüsseldatei. Diese Option kann nicht mit /kt verwendet werden. |
| /kt           | Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des globalen Testschlüssels. Diese Option kann nicht mit /kf verwendet werden. |
| /no           | Verhindert ein Überschreiben der Ausgabedatei, wenn vorhanden. Wenn Sie diese Option oder die Option /o nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten. |
| /nv           | Überspringt die semantische Überprüfung. Wenn Sie diese Option nicht angeben, führt das Tool eine vollständige Überprüfung des Pakets aus. |
| /o            | Überschreibt die Ausgabedatei, wenn vorhanden. Wenn Sie diese Option oder die Option /no nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten. |
| /p            | Gibt das App-Paket oder -Bündel an.  |
| /v            | Aktiviert die ausführliche Protokollierungsausgabe an die Konsole. |
| /?            | Zeigt Hilfetext an.                   |


Die folgende Liste enthält mögliche Argumente:

| **Argument**                          | **Beschreibung**                       |
|---------------------------------------|---------------------------------------|
| &lt;output package name&gt;           | Der Name des erstellten Pakets. Dies ist der Dateiname mit .msix oder AppX angefügt. |
| &lt;encrypted output package name&gt; | Der Name des erstellten verschlüsselten Pakets. Dies ist der Dateiname mit .emsix oder eappx angefügt. |
| &lt;input package name&gt;            | Der Name des Pakets. Dies ist der Dateiname mit .msix oder AppX angefügt. |
| &lt;encrypted input package name&gt;  | Der Name des verschlüsselten Pakets. Dies ist der Dateiname mit .emsix oder eappx angefügt. |
| &lt;output bundle name&gt;            | Der Name des erstellten Bündels. Dies ist der Dateiname mit .msixbundle oder .appxbundle angefügt. |
| &lt;encrypted output bundle name&gt;  | Der Name des erstellten verschlüsselten Bündels. Dies ist der Dateiname mit .emsixbundle oder eappxbundle angefügt. |
| &lt;input bundle name&gt;             | Der Name des Bündels. Dies ist der Dateiname mit .msixbundle oder .appxbundle angefügt. |
| &lt;encrypted input bundle name&gt;   | Der Name des verschlüsselten Bündels. Dies ist der Dateiname mit .emsixbundle oder eappxbundle angefügt. |
| &lt;content directory&gt;             | Der Pfad für den Inhalt des App-Pakets oder -Bündels. |
| &lt;mapping file&gt;                  | Der Name der Datei, der Paketquelle und -ziel angibt. |
| &lt;output directory&gt;              | Der Pfad zum Verzeichnis für Ausgabepakete und -bündel. |
| &lt;key file&gt;                      | Der Name der Datei mit einem Schlüssel für die Verschlüsselung oder Entschlüsselung. |
| &lt;algorithm ID&gt;                  | Die beim Erstellen einer Blockzuordnung verwendeten Algorithmen. Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512. |


### <a name="create-an-app-package"></a>Erstellen eines App-Pakets

Ein app-Paket ist ein vollständiger Satz von app Dateien, verpackt in einer .msix oder AppX-Paketdatei. Um ein App-Paket mit dem Befehl **pack** zu erstellen, müssen Sie entweder ein Inhaltsverzeichnis oder eine Zuordnungsdati für den Speicherort des Pakets angeben. Sie können ein Paket auch während des Erstellens verschlüsseln. Wenn Sie das Paket verschlüsseln möchten, müssen Sie /ep verwenden und angeben, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden. Weitere Informationen zum Erstellen eines verschlüsselten Pakets finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).

Optionen, die für den Befehl **pack** spezifisch sind:

| **Option**    | **Beschreibung**                       |
|---------------|---------------------------------------|
| /f            | Gibt die Zuordnungsdatei an.           |
| /h            | Gibt den Hashalgorithmus an, der beim Erstellen der Blockzuordnung verwendet wird. Diese Option kann nur mit den pack-Befehl verwendet werden. Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512. |
| /m            | Gibt den Pfad zu einem Eingabe App-Manifest an, das als Grundlage für das Generieren des Ausgabe-App-Pakets oder des Manifests des Ressourcenpakets verwendet wird.  Wenn Sie diese Option verwenden, müssen Sie auch /f verwenden und einen [ResourceMetadata]-Abschnitt in die Zuordnungsdatei einfügen, um die Ressourcendimensionen anzugeben, die im generierten Manifest enthalten sein sollen.|
| /nc           | Verhindert die Komprimierung der Paketdateien. Standardmäßig werden Dateien basierend auf dem erkannten Dateityp komprimiert. |
| /r            | Erstellt ein Ressourcenpaket. Diese Option muss mit /m verwendet werden und impliziert die Verwendung der Option /l. |  


Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **pack**-Befehl:

``` syntax 
MakeAppx pack [options] /d <content directory> /p <output package name>
MakeAppx pack [options] /f <mapping file> /p <output package name>
MakeAppx pack [options] /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /r /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kf <key file>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kt

```
Im Folgenden finden Sie Befehlszeilenbeispiele für den **pack**-Befehl:

``` examples
MakeAppx pack /v /h SHA256 /d "C:\My Files" /p MyPackage.msix
MakeAppx pack /v /o /f MyMapping.txt /p MyPackage.msix
MakeAppx pack /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p AppPackage.msix
MakeAppx pack /r /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p ResourcePackage.msix
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.emsix /kf MyKeyFile.txt
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.emsix /kt
```

### <a name="create-an-app-bundle"></a>Erstellen eines App-Bündels

Ein App-Bündel ist einem App-Paket vergleichbar. Ein Bündel kann jedoch die Größe der App reduzieren, die Benutzer herunterladen. App-Bündel sind beispielsweise für sprachspezifische Ressourcen, Ressourcen mit unterschiedlichen Imagegrößen oder Ressourcen nützlich, die für spezifische Versionen von Microsoft DirectX gelten. Wie beim Erstellen verschlüsselter App-Pakete, können Sie auch App-Bündel beim Bündeln verschlüsseln. Um das App-Bündel zu verschlüsseln, verwenden Sie die Option /ep und geben an, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden. Weitere Informationen zum Erstellen eines verschlüsselten Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).

Optionen, die für den **bundle**-Befehl spezifisch sind:

| **Option**    | **Beschreibung**                       |
|---------------|---------------------------------------|
| /bv           | Gibt die Versionsnummer des Bündels an. Die Versionsnummer muss aus vier Teilen bestehen, getrennt durch Punkte: &lt;Hauptversion&gt;.&lt;Unterversion&gt;.&lt;Build&gt;.&lt;Überarbeitung&gt;. |
| /f            | Gibt die Zuordnungsdatei an.           |

Beachten Sie, dass die Bündelversion mit dem aktuellen Datum und der aktuellen Uhrzeit erstellt wird, wenn die Bündelversion nicht angegeben oder auf „0.0.0.0“ festgelegt ist.

Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **bundle**-Befehl:

``` syntax
MakeAppx bundle [options] /d <content directory> /p <output bundle name>
MakeAppx bundle [options] /f <mapping file> /p <output bundle name>
MakeAppx bundle [options] /d <content directory> /ep <encrypted output bundle name> /kf MyKeyFile.txt
MakeAppx bundle [options] /f <mapping file> /ep <encrypted output bundle name> /kt
```
Der folgende Block enthält Beispiele für den **bundle** Befehl:

``` examples
MakeAppx bundle /v /d "C:\My Files" /p MyBundle.msixbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /p MyBundle.msixbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.emsixbundle /kf MyKeyFile.txt
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.emsixbundle /kt
```

### <a name="extract-files-from-a-package-or-bundle"></a>Extrahieren von Dateien aus einem Paket oder Bündel

Zusätzlich zum Packen und Bündeln von Apps kann **MakeAppx.exe** vorhandene Pakete entpacken oder entbündeln. Sie müssen als Ziel für die extrahierten Dateien das Inhaltsverzeichnis angeben. Wenn Sie versuchen, Dateien aus einem verschlüsselten Paket oder Bündel zu extrahieren, können Sie die Dateien gleichzeitig entschlüsseln und extrahieren, indem Sie die Option /ep verwenden und angeben, ob sie mit einer Schlüsseldatei (/kf) oder dem globalen Testschlüssel (/kt) entschlüsselt werden sollen. Weitere Informationen zum Entschlüsseln eines Pakets oder Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels](#encrypt-or-decrypt-a-package-or-bundle).

Optionen, die für die Befehle **unpack** und **unbundle** spezifisch sind:

| **Option**    | **Beschreibung**                       |
|---------------|---------------------------------------|
| /nd           | Führt beim Entpacken oder Entbündeln des Pakets/Bündels keine Entschlüsselung aus. |
| /pfn          | Entpackt/entbündelt alle Dateien in ein Unterverzeichnis am angegebenen Ausgabepfad, benannt nach dem vollständigen Namen des Pakets oder Bündels. |

Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **unpack** und **unbundle**:

``` syntax
MakeAppx unpack [options] /p <input package name> /d <output directory>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kf <key file>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kt

MakeAppx unbundle [options] /p <input bundle name> /d <output directory>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kf <key file>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kt
```

Der folgende Block enthält Beispiele für die Verwendung der Befehle **unpack** und **unbundle**:

``` examples
MakeAppx unpack /v /p MyPackage.msix /d "C:\My Files"
MakeAppx unpack /v /ep MyPackage.emsix /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unpack /v /ep MyPackage.emsix /d "C:\My Files" /kt

MakeAppx unbundle /v /p MyBundle.msixbundle /d "C:\My Files"
MakeAppx unbundle /v /ep MyBundle.emsixbundle /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unbundle /v /ep MyBundle.emsixbundle /d "C:\My Files" /kt
```

### <a name="encrypt-or-decrypt-a-package-or-bundle"></a>Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels

Das **MakeAppx.exe**-Tool kann ein vorhandenes Paket oder Bündel auch verschlüsseln oder entschlüsseln. Sie müssen lediglich den Paketnamen und den Ausgabepaketnamen angeben und ob die Verschlüsselung oder Entschlüsselung eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden soll.

Verschlüsselung und Entschlüsselung sind nicht über den Verpackungs-Assistenten von Visual Studio verfügbar. 

Optionen, die für die Befehle **encrypt** und **decrypt** spezifisch sind:

| **Option**    | **Beschreibung**                       |
|---------------|---------------------------------------|
| /ep           | Gibt ein verschlüsseltes App-Paket oder -Bündel an. |

Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **encrypt** und **decrypt**:

``` syntax
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kf <key file>
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kt

MakeAppx decrypt [options] /ep <package name> /p <output package name> /kf <key file>
MakeAppx decrypt [options] /ep <package name> /p <output package name> /kt
```

Der folgende Block enthält Beispiele für die Verwendung der Befehle **encrypt** und **decrypt**:

``` examples
MakeAppx.exe encrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kt
MakeAppx.exe encrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kf MyKeyFile.txt

MakeAppx.exe decrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kt
MakeAppx.exe decrypt p MyPackage.msix /ep MyEncryptedPackage.emsix /kf MyKeyFile.txt
```

## <a name="key-files"></a>Schlüsseldateien

Schlüsseldateien müssen mit einer Zeile beginnen, die die Zeichenfolge „[Keys]“ enthält, gefolgt von Zeilen, die die Schlüssel beschreiben, mit denen die einzelnen Pakete verschlüsselt werden sollen. Jeder Schlüssel wird durch ein Paar von Zeichenfolgen in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, dargestellt. Die erste Zeichenfolge stellt die base64-codierte 32-Byte-Schlüssel-ID dar. Die zweite Zeichenfolge stellt den base64-codierten 32-Byte-Verschlüsselungsschlüssel dar. Eine Schlüsseldatei sollte eine einfache Textdatei sein.

Beispiel für eine Schlüsseldatei:

``` Example
[Keys]
"OWVwSzliRGY1VWt1ODk4N1Q4R2Vqc04zMzIzNnlUREU="    "MjNFTlFhZGRGZEY2YnVxMTBocjd6THdOdk9pZkpvelc="
```

## <a name="mapping-files"></a>Zuordnungsdateien
Zuordnungsdateien müssen mit einer Zeile beginnen, die Zeichenfolge „[Files]“ enthält, gefolgt von Zeilen, die die Dateien beschreiben, die dem Paket hinzugefügt werden sollen. Jede Datei wird durch ein Paar von Pfaden in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, beschrieben. Jede Datei stellt Quelle (auf der Festplatte) und Ziel (im Paket) dar. Eine Zuordnungsdatei sollte eine einfache Textdatei sein.

Beispiel für eine Zuordnungsdatei (ohne Option /m):

``` Example
[Files]
"C:\MyApp\StartPage.html"               "default.html"
"C:\Program Files (x86)\example.txt"    "misc\example.txt"
"\\MyServer\path\icon.png"              "icon.png"
"my app files\readme.txt"               "my app files\readme.txt"
"CustomManifest.xml"                    "AppxManifest.xml"
``` 

Wenn Sie eine Zuordnungsdatei verwenden, können Sie wählen, ob Sie die Option /m verwenden möchten oder nicht. Mithilfe der Option /m können Benutzer die Ressourcenmetadaten in der Zuordnungsdatei angeben, die im generierten Manifest eingeschlossen werden sollen. Wenn Sie die Option /m verwenden, muss die Zuordnungsdatei einen Abschnittenthalten, der mit der Zeile „[ResourceMetadata]“ beginnt, gefolgt von Zeilen, die „ResourceDimensions“ und „ResourceId“ angeben. App-Pakete können mehrere „ResourceDimensions“ enthalten kann, jedoch stets nur eine „ResourceId“.

Beispiel für eine Zuordnungsdatei (mit Option /m):

``` Example
[ResourceMetadata]
"ResourceDimensions"                    "language-en-us"
"ResourceId"                            "English"

[Files]
"images\en-us\logo.png"                 "en-us\logo.png"
"en-us.pri"                             "resources.pri"
```

## <a name="semantic-validation-performed-by-makeappxexe"></a>Semantische Überprüfung durch MakeAppx.exe

**MakeAppx.exe** führt eine begrenzte semantische Überprüfung aus, um die häufigsten Bereitstellungsfehler zu erfassen und sicherzustellen, dass das App-Paket gültig ist. Verwenden Sie die Option /nv, wenn Sie beim Verwenden von **MakeAppx.exe**  die Überprüfung auslassen möchten. 

Diese Überprüfung stellt Folgendes sicher:
- Alle Dateien, auf die im Paketmanifest verwiesen wird, sind im App-Paket enthalten.
- Die Anwendung besitzt nicht zwei identische Schlüssel.
- Die Anwendung registriert sich nicht für ein untersagtes Protokoll aus der folgenden Liste: SMB, FILE, MS-WWA-WEB, MS-WWA. 

Dies ist keine vollständige semantische Überprüfung, da sie lediglich häufige Fehler erfassen soll. Es wird nicht garantiert, dass von **MakeAppx.exe** erstellte Pakete installiert werden können.
