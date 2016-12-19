---
author: awkoren
Description: Zeigt, wie Sie eine Windows-Desktopanwendung (z. B. Win32, WPF und Windows Forms) manuell in eine UWP-App (Universelle Windows-Plattform) konvertieren.
Search.Product: eADQiWindows 10XVcnh
title: Manuelles Konvertieren einer Windows-Desktopanwendung in eine UWP-App (Universelle Windows-Plattform)
translationtype: Human Translation
ms.sourcegitcommit: ee697323af75f13c0d36914f65ba70f544d046ff
ms.openlocfilehash: f55f3bd6479cdf076c51cf574b07bfb5ce3a805c

---

# <a name="manually-convert-your-app-to-uwp-using-the-desktop-bridge"></a>Manuelles Konvertieren Ihrer App zu UWP mithilfe der Desktop-Brücke

Die Verwendung von [Desktop App Converter (DAC)](desktop-to-uwp-run-desktop-app-converter.md) ist praktisch und automatisch und darüber hinaus nützlich, wenn Unsicherheiten hinsichtlich der Aktivitäten des Installationsprogramms bestehen. Wenn Ihre App jedoch mithilfe von xcopy installiert wurde, oder wenn Sie mit den Änderungen vertraut sind, die das Installationsprogramm Ihrer App am System vornimmt, können Sie ein App-Paket und -Manifest manuell erstellen. Dieser Artikel beschreibt die ersten Schritte hierfür. Hier wird auch erklärt, wie Sie Ihrer App unbeschichtete Ressourcen hinzufügen, die vom DAC nicht erfasst werden. 

Dies sind die ersten Schritte:

## <a name="create-a-manifest-by-hand"></a>Erstellen Sie manuell ein Manifest.

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

## <a name="add-unplated-assets"></a>Hinzufügen von unbeschichteten Ressourcen

Hier erfahren Sie, wie Sie die 44x44-Ressourcen für Ihre App konfigurieren, die auf der Taskleiste angezeigt werden.

1. Rufen Sie die richtigen 44x44-Bilder ab, und kopieren Sie sie in den Ordner, der Ihre Bilder (d. h. Ressourcen) enthält.

2. Erstellen Sie für jedes 44x44-Bild eine Kopie im selben Ordner, und hängen Sie *.targetsize-44_altform-unplated* an den Dateinamen an. Sie sollten zwei Kopien von jedem Symbol haben, jeweils spezifisch benannt. Nach Abschluss des Vorgangs könnte Ihr Ressourcenordner beispielsweise *MYAPP_44x44.png* und *MYAPP_44x44.targetsize-44_altform-unplated.png* enthalten. (Hinweis: Das erste Symbol ist das Symbol, auf das in der appxmanifest-Datei unter dem VisualElements-Attribut *Square44x44Logo* verwiesen wird.) 

3.  Legen Sie in der Appxmanifest-Datei die Hintergrundfarbe für jedes von Ihnen bearbeitete Symbol auf „Transparent“ fest. Sie finden dieses Attribut unter VisualElements für die einzelnen Anwendungen.

4.  Öffnen Sie CMD, ändern Sie das Verzeichnis in den Stammordner des Pakets, und erstellen Sie mit dem Befehl ```makepri createconfig /cf priconfig.xml /dq en-US``` eine priconfig.xml-Datei.

5.  Bleiben Sie im Stammordner des Pakets, und erstellen Sie mit CMD mittels des Befehls ```makepri new /pr <PHYSICAL_PATH_TO_FOLDER> /cf <PHYSICAL_PATH_TO_FOLDER>\priconfig.xml``` die resources.pri-Datei(en). Der Befehl für Ihre App könnte beispielsweise wie folgt aussehen: ```makepri new /pr c:\MYAPP /cf c:\MYAPP\priconfig.xml```. 

6.  Verpacken Sie Ihre AppX-Datei mithilfe der Anweisungen im nächsten Schritt, um die Ergebnisse anzuzeigen.

## <a name="run-the-makeappx-tool"></a>Ausführen des MakeAppX-Tools

Verwenden Sie den [App-Packager (MakeAppx.exe)](https://msdn.microsoft.com/library/windows/desktop/hh446767(v=vs.85).aspx), um ein AppX-Paket für Ihr Projekt zu generieren. MakeAppx.exe ist in der Windows 10 SDK enthalten. 

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

Das Add-AppxPackage-Cmdlet erfordert, dass das bereitgestellte Anwendungspaket (.appx) signiert ist. Verwenden Sie zum Signieren des Appx-Pakets [SignTool.exe](https://msdn.microsoft.com/library/windows/desktop/aa387764(v=vs.85).aspx), die im Lieferumfang des Microsoft Windows 10 SDK enthalten ist.

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




<!--HONumber=Dec16_HO1-->


