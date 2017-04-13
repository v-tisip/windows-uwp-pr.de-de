---
author: normesta
Description: Zeigt, wie Sie eine Windows-Desktopanwendung (z. B. Win32, WPF und Windows Forms) manuell in eine UWP-App (Universelle Windows-Plattform) konvertieren.
Search.Product: eADQiWindows 10XVcnh
title: "Manuelle Konvertierung der Desktop-zu-UWP-Brücke"
ms.author: normesta
ms.date: 03/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: e8c2a803-9803-47c5-b117-73c4af52c5b6
ms.openlocfilehash: 8d09a0349620e071f5c4d680df18f716e3b10a8e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="desktop-to-uwp-bridge-manual-conversion"></a>Manuelle Konvertierung der Desktop-zu-UWP-Brücke

Die Verwendung des [Desktop App Converter (DAC)](desktop-to-uwp-run-desktop-app-converter.md) ist praktisch und automatisiert den Vorgang. Die Anwendung ist außerdem dann nützlich, wenn nicht klar ist, was Ihr Installer macht. Wenn Ihre App jedoch mithilfe von xcopy installiert wurde, oder wenn Sie mit den Änderungen vertraut sind, die das Installationsprogramm Ihrer App am System vornimmt, können Sie ein App-Paket und -Manifest manuell erstellen. Dieser Artikel beschreibt die ersten Schritte hierfür. Es wird außerdem beschrieben, wie Sie nicht angepasste Ressourcen zu Ihrer App hinzufügen (dies wird nicht vom DAC abgedeckt).

So beginnen Sie mit der manuellen Konvertierung. Alternativ können Sie bei einer .NET-App auch Visual Studio nutzen (siehe [Handbuch zur Desktop-Brücke-Verpackung von .NET Desktop-Apps mit Visual Studio](desktop-to-uwp-packaging-dot-net.md)).  

## <a name="create-a-manifest-by-hand"></a>Manuelles Erstellen eines Manifests

Ihre _appxmanifest.xml_-Datei muss (mindestens) den folgenden Inhalt aufweisen. Ändern Sie Platzhalter, die \*\*\*SO\*\*\* formatiert sind, in tatsächliche Werte für Ihre Anwendung.

```XML
    <?xml version="1.0" encoding="utf-8"?>
    <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities">
      <Identity Name="***YOUR_PACKAGE_NAME_HERE***"
        ProcessorArchitecture="x64"
        Publisher="CN=***COMPANY_NAME***, O=***ORGANIZATION_NAME***, L=***CITY***, S=***STATE***, C=***COUNTRY***"
        Version="***YOUR_PACKAGE_VERSION_HERE***" />
      <Properties>
        <DisplayName>***YOUR_PACKAGE_DISPLAY_NAME_HERE***</DisplayName>
        <PublisherDisplayName>Reserved</PublisherDisplayName>
        <Description>No description entered</Description>
        <Logo>***YOUR_PACKAGE_RELATIVE_DISPLAY_LOGO_PATH_HERE***</Logo>
      </Properties>
      <Resources>
        <Resource Language="en-us" />
      </Resources>
      <Dependencies>
        <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14316.0" MaxVersionTested="10.0.14316.0" />
      </Dependencies>
      <Capabilities>
        <rescap:Capability Name="runFullTrust"/>
      </Capabilities>
      <Applications>
        <Application Id="***YOUR_PRAID_HERE***" Executable="***YOUR_PACKAGE_RELATIVE_EXE_PATH_HERE***" EntryPoint="Windows.FullTrustApplication">
          <uap:VisualElements
           BackgroundColor="#464646"
           DisplayName="***YOUR_APP_DISPLAY_NAME_HERE***"
           Square150x150Logo="***YOUR_PACKAGE_RELATIVE_PNG_PATH_HERE***"
           Square44x44Logo="***YOUR_PACKAGE_RELATIVE_PNG_PATH_HERE***"
           Description="***YOUR_APP_DESCRIPTION_HERE***" />
        </Application>
      </Applications>
    </Package>
```

Sie haben unbeschichtete Ressourcen, die Sie hinzufügen möchten? Ausführliche Informationen zur Vorgehensweise finden Sie weiter unten in diesem Artikel im Abschnitt [Unbeschichtete Ressourcen](#unplated-assets).

## <a name="run-the-makeappx-tool"></a>Ausführen des MakeAppX-Tools

Verwenden Sie den [App-Packager (MakeAppx.exe)](https://msdn.microsoft.com/library/windows/desktop/hh446767(v=vs.85).aspx), um ein Windows-App-Paket für Ihr Projekt zu generieren. MakeAppx.exe ist in der Windows 10 SDK enthalten.

Um MakeAppx auszuführen, stellen Sie zunächst sicher, dass Sie, wie oben beschrieben, eine Manifestdatei erstellt haben.

Erstellen Sie als Nächstes eine Zuordnungsdatei. Die Datei sollte mit **[Dateien]** beginnen, dann jede der Quelldateien auf dem Datenträger auflisten, gefolgt von deren Zielpfad im Paket. Beispiel:

```
[Files]
"C:\MyApp\StartPage.htm"     "default.html"
"C:\MyApp\readme.txt"        "doc\readme.txt"
"\\MyServer\path\icon.png"   "icon.png"
"MyCustomManifest.xml"       "AppxManifest.xml"
```

Führen Sie abschließend den folgenden Befehl aus:

```cmd
MakeAppx.exe pack /f mapping_filepath /p filepath.appx
```

## <a name="sign-your-appx-package"></a>Signieren des Appx-Pakets

Das Add-AppxPackage-Cmdlet erfordert, dass das bereitgestellte Anwendungspaket (.appx) signiert ist. Verwenden Sie zum Signieren des Windows-App-Pakets [SignTool.exe](https://msdn.microsoft.com/library/windows/desktop/aa387764(v=vs.85).aspx), die im Lieferumfang des Microsoft Windows 10 SDK enthalten ist.

Beispielanwendung:

```cmd
C:\> MakeCert.exe -r -h 0 -n "CN=<publisher_name>" -eku 1.3.6.1.5.5.7.3.3 -pe -sv <my.pvk> <my.cer>
C:\> pvk2pfx.exe -pvk <my.pvk> -spc <my.cer> -pfx <my.pfx>
C:\> signtool.exe sign -f <my.pfx> -fd SHA256 -v .\<outputAppX>.appx
```
Wenn Sie beim Ausführen von MakeCert.exe zum Eingeben eines Kennworts aufgefordert werden, wählen Sie **Kein**. Weitere Informationen zu Zertifikaten und zum Signieren finden Sie unter:

- [Gewusst wie: Erstellen temporärer Zertifikate für die Verwendung während der Entwicklung](https://msdn.microsoft.com/library/ms733813.aspx)
- [SignTool](https://msdn.microsoft.com/library/windows/desktop/aa387764.aspx)
- [SignTool.exe (Signaturtool)](https://msdn.microsoft.com/library/8s9b9yaz.aspx)

<span id="unplated-assets" />
## <a name="add-unplated-assets"></a>Hinzufügen von unbeschichteten Ressourcen

Hier erfahren Sie, wie Sie die 44x44-Ressourcen für Ihre App optional konfigurieren, die auf der Taskleiste angezeigt werden.

1. Rufen Sie die richtigen 44x44-Bilder ab, und kopieren Sie sie in den Ordner, der Ihre Bilder (d.h. Ressourcen) enthält.

2. Erstellen Sie für jedes 44x44-Bild eine Kopie im selben Ordner, und hängen Sie *.targetsize-44_altform-unplated* an den Dateinamen an. Sie sollten zwei Kopien von jedem Symbol haben, jeweils spezifisch benannt. Nach Abschluss des Vorgangs könnte Ihr Ressourcenordner beispielsweise *MYAPP_44x44.png* und *MYAPP_44x44.targetsize-44_altform-unplated.png* enthalten. (Hinweis: Das erste Symbol ist das Symbol, auf das in der appxmanifest-Datei unter dem VisualElements-Attribut *Square44x44Logo* verwiesen wird.)

3.    Legen Sie in der Appxmanifest-Datei die Hintergrundfarbe für jedes von Ihnen bearbeitete Symbol auf „Transparent“ fest. Sie finden dieses Attribut unter VisualElements für die einzelnen Anwendungen.

4.    Öffnen Sie CMD, ändern Sie das Verzeichnis in den Stammordner des Pakets, und erstellen Sie mit dem Befehl ```makepri createconfig /cf priconfig.xml /dq en-US``` eine priconfig.xml-Datei.

5.    Bleiben Sie im Stammordner des Pakets, und erstellen Sie mit CMD mittels des Befehls ```makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``` die resources.pri-Datei(en). Der Befehl für Ihre App könnte beispielsweise wie folgt aussehen: ```makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml```.

6.    Verpacken Sie Ihre Windows-App-Datei mithilfe der Anweisungen im nächsten Schritt, um die Ergebnisse anzuzeigen.
