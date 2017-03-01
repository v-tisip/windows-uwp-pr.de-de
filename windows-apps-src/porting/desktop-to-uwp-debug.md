---
author: awkoren
Description: "Bereitstellen und Debuggen einer UWP-App (Universelle Windows-Plattform), die mit der Desktop-zu-UWP-Brücke von einer Windows-Desktopanwendung (Win32, WPF und Windows-Forms) konvertiert wurde"
Search.Product: eADQiWindows 10XVcnh
title: "Debuggen von Apps, die mit der Desktop-Brücke konvertiert wurden"
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: f45d8b14-02d1-42e1-98df-6c03ce397fd3
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 9660d14a1ca28929a213d4ed5a59cdcda73ccc39
ms.lasthandoff: 02/08/2017

---

# <a name="debug-apps-converted-with-the-desktop-bridge"></a>Debuggen von Apps, die mit der Desktop-Brücke konvertiert wurden

Dieses Thema enthält Informationen, die Sie beim erfolgreichen Debuggen der App nach der Konvertierung mit der Desktop-zu-UWP-Brücke unterstützen. Sie haben mehrere Optionen zum Debuggen der konvertierten App.

## <a name="attach-to-process"></a>Anhängen an den Prozess

Wenn Sie Microsoft Visual Studio als Administrator ausführen, funktionieren die Befehle *Debuggen starten* und *Start Without* für das konvertierte App-Projekt, doch die gestartete App wird auf einer [Ebene mittlerer Integrität](https://msdn.microsoft.com/library/bb625963) ausgeführt (d. h. ohne erhöhte Rechte). Wenn Sie der gestarteten App Administratorrechte gewähren möchten, müssen Sie sie zunächst über eine Verknüpfung oder eine Kachel „als Administrator“ starten. Wenn die App ausgeführt wird, rufen Sie von einer Microsoft Visual Studio-Instanz, die als Administrator ausgeführt wird, __An Prozess anhängen__ auf, und wählen Sie im Dialogfeld den Prozess der App.

## <a name="f5-debug"></a>Debugging mit F5

Visual Studio unterstützt jetzt ein neues Paketprojekt. Das neue Projekt ermöglicht beim Erstellen der Anwendung das automatische Kopieren von Updates in das APPX-Paket, das vom Konverter für den Installer Ihrer Anwendung erstellt wurde. Nach der Konfiguration des Paketprojekts können Sie F5 verwenden, um das Debuggen direkt im APPX-Paket durchzuführen. 

>Hinweis: Sie können auch die Option zum Debuggen eines vorhandenen APPX-Pakets verwenden, indem Sie Debuggen -> Andere Debugziele -> Installiertes App-Paket debuggen auswählen.

Dies sind die ersten Schritte: 

1. Stellen Sie zunächst sicher, dass Desktop App Converter verwendet werden kann. Eine Anleitung hierzu finden Sie unter [Desktop App Converter](desktop-to-uwp-run-desktop-app-converter.md).

2. Führen Sie den Konverter und dann den Installer für die Win32-Anwendung aus. Der Konverter erfasst das Layout und alle an der Registrierung vorgenommenen Änderungen und gibt ein APPX-Paket mit einem Manifest und die Datei „Registry.dat“ aus, um die Registrierung zu virtualisieren:

![alt](images/desktop-to-uwp/debug-1.png)

3. Installieren und starten Sie [Visual Studio 2017 RC](https://www.visualstudio.com/downloads/#visual-studio-community-2017-rc). 

4. Installieren Sie das VSIX-Projekt „Desktop to UWP Packaging“ aus der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=797871). 

5. Öffnen Sie die entsprechende Win32-Lösung, die in Visual Studio konvertiert wurde.
 
6. Fügen Sie der Projektmappe das neue Paketprojekt hinzu, indem Sie mit der rechten Maustaste auf die Projektmappe klicken und „Neues Projekt hinzufügen“ wählen. Wählen Sie dann unter „Setup und Bereitstellung“ das Paketprojekt „Desktop to UWP Packaging Project“:

    ![alt](images/desktop-to-uwp/debug-2.png)

    Das resultierende Projekt wird der Projektmappe hinzugefügt:

    ![alt](images/desktop-to-uwp/debug-3.png)

    Im Paketprojekt stellt die AppXFileList eine Zuordnung von Dateien im AppX-Layout bereit. Verweise sind zunächst leer, sollten jedoch manuell auf die .exe-Projektdatei für die Buildreihenfolge festgelegt werden. 

7. Das DesktopToUWPPackaging-Projekt verfügt über eine Eigenschaftenseite, auf der Sie den AppX-Paketstamm konfigurieren und die auszuführende Kachel festlegen können:

    ![alt](images/desktop-to-uwp/debug-4.png)

    Legen Sie PackageLayout auf das Stammverzeichnis des AppX-Projekts fest, das vom Konverter (siehe oben) erstellt wurde. Wählen Sie die Kachel, die Sie ausführen möchten.

8.    Öffnen und bearbeiten Sie die Datei „AppXFileList.xml“. Diese Datei definiert, wie die Ausgabe des Win32-Debugbuilds in das vom Konverter erstellte AppX-Layout kopiert wird. Standardmäßig enthält die Datei einen Platzhalter mit einem Beispieltag und einem Kommentar:

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <ItemGroup>
    <!— Use the following syntax to copy debug output to the AppX layout
       <AppxPackagedFile Include="$(outdir)\App.exe">
          <PackagePath>App.exe</PackagePath>
        </AppxPackagedFile> 
        See http://etc...
    -->
      </ItemGroup>
    </Project>
    ```

    Im Folgenden finden Sie ein Beispiel für das Erstellen der Zuordnung. In diesem Fall werden die EXE- und DLL-Dateien vom Win32-Buildspeicherort in den Speicherort des Paketlayouts kopiert. 

    ```XML
    <?xml version="1.0" encoding=utf-8"?>
    <Project ToolsVersion=14.0" xmlns="http://scehmas.microsoft.com/developer/msbuild/2003">
        <PropertyGroup>
            <MyProjectOutputPath>{relativepath}</MyProjectOutputPath>
        </PropertyGroup>
        <ItemGroup>
            <LayoutFile Include="$(MyProjectOutputPath)\ProjectTracker.exe">
                <PackagePath>$(PackageLayout)\VFS\Program Files (x86)\Contoso Software\Project Tracker\ProjectTracker.exe</PackagePath>
            </LayoutFile>
            <LayoutFile Include="$(MyProjectOutputPath)\ProjectTracker.Models.dll">
                <PackagePath>$(PackageLayout)\VFS\Program Files (x86)\Contoso Software\Project Tracker\ProjectTracker.Models.dll</PackagePath>
            </LayoutFile>
        </ItemGroup>
    </Project>
    ```

    Die Datei wird wie folgt definiert: 

    Zunächst wird *MyProjectOutputPath* so definiert, dass es auf den Speicherort zeigt, wo das Win32-Projekt erstellt wird:

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
        <PropertyGroup>
            <MyProjectOutputPath>..\ProjectTracker\bin\DesktopUWP</MyProjectOutputPath>
        </PropertyGroup>
    ```

    Anschließend gibt jede *LayoutFile* eine Datei an, die aus dem Win32-Buildspeicherort in das Appx-Paketlayout kopiert wird. In diesem Fall werden erst eine EXE-Datei und dann eine DLL-Datei kopiert. 

    ```XML
        <ItemGroup>
            <LayoutFile Include="$(MyProjectOutputPath)\ProjectTracker.exe">
                <PackagePath>$(PackageLayout)\VFS\Program Files (x86)\Contoso Software\Project Tracker\ProjectTracker.exe</PackagePath>
            </LayoutFile>
            <LayoutFile Include="$(MyProjectOutputPath)\ProjectTracker.Models.dll">
                <PackagePath>$(PackageLayout)\VFS\Program Files (x86)\Contoso Software\Project Tracker\ProjectTracker.Models.dll</PackagePath>
            </LayoutFile>
        </ItemGroup>
    </Project>
    ```

9. Legen Sie das Paketprojekt als Startprojekt fest. Hierdurch werden die Win32-Dateien in das AppX-Paket kopiert und der Debugger gestartet, wenn das Projekt erstellt und ausgeführt wird.  

    ![alt](images/desktop-to-uwp/debug-5.png)

10.    Schließlich können Sie einen Haltepunkt im Win32-Code festlegen und F5 drücken, um den Debugger zu starten. Alle an der Win32-Anwendung vorgenommenen Änderungen im AppX-Paket werden kopiert. Sie können das Debugging direkt in Visual Studio durchführen.

11.    Wenn Sie Ihre Anwendung aktualisieren, müssen Sie MakeAppX verwenden, um erneut ein App-Paket zu erstellen. Weitere Informationen finden Sie unter [App-Objekt-Manager (MakeAppx.exe)](https://msdn.microsoft.com/library/windows/desktop/hh446767(v=vs.85).aspx). 

Wenn Sie über mehrere Buildkonfigurationen verfügen (z. B. für Version und fürs Debuggen), können Sie der Datei „AppXFileList.xml“ Folgendes hinzufügen, um den Win32-Build aus verschiedenen Speicherorten zu kopieren:

```XML
<PropertyGroup>
    <MyProjectOutputPath Condition="$(Configuration) == 'DesktopUWP'">C:\Users\peterfar\Desktop\ProjectTracker\ProjectTracker\bin\DesktopUWP>
    </MyProjectOutputPath>
    <MyProjectOutputPath Condition="$(Configuration) == 'ReleaseDesktopUWP'"> C:\Users\peterfar\Desktop\ProjectTracker\ProjectTracker\bin\ReleaseDesktopUWP</MyProjectOutputPath>
</PropertyGroup>
```

Sie können auch die bedingte Kompilierung zum Aktivieren bestimmter Codepfade verwenden, wenn Sie Ihre Anwendung für UWP aktualisieren, diese jedoch weiterhin für Win32 erstellen möchten. 

1.    Im folgenden Beispiel werden nur der Code für DesktopUWP kompiliert und eine Kachel mit der WinRT-API dargestellt. 

    ```C#
    [Conditional("DesktopUWP")]
    private void showtile()
    {
        XmlDocument tileXml = TileUpdateManager.GetTemplateContent(TileTemplateType.TileSquare150x150Text01);
        XmlNodeList textNodes = tileXml.GetElementsByTagName("text");
        textNodes[0].InnerText = string.Format("Welcome to DesktopUWP!");
        TileNotification tileNotification = new TileNotification(tileXml);
        TileUpdateManager.CreateTileUpdaterForApplication().Update(tileNotification);
    }
    ```

2.    Sie können den Konfigurations-Manager zum Hinzufügen neuer Buildkonfiguration verwenden:

    ![alt](images/desktop-to-uwp/debug-6.png)

    ![alt](images/desktop-to-uwp/debug-7.png)

3.    Fügen Sie dann in den Projekteigenschaften Unterstützung für Symbole für die bedingte Kompilierung hinzu:

    ![alt](images/desktop-to-uwp/debug-8.png)

4.    Sie können jetzt das Buildziel zu DesktopUWP ändern, wenn Sie für die hinzugefügte UWP-API erstellen möchten.

## <a name="plmdebug"></a>PLMDebug 

In Visual Studio können Sie mit der Taste F5 sowie mithilfe der Option „An den Prozess anhängen“ Ihre App debuggen, während sie ausgeführt wird. In einigen Fällen empfiehlt sich jedoch eine differenziertere Steuerung des Debugging-Vorgangs, wenn z. B. das Debuggen erfolgen soll, bevor die App gestartet wird. Verwenden Sie in diesen komplexeren Szenarien [**PLMDebug**](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx). Mit diesem Tool können Sie die konvertierte App mit dem Windows-Debugger debuggen. Zudem verfügen Sie über die vollständige Steuerung des App-Lebenszyklus, einschließlich Anhalten, Fortsetzen und Beenden. 

PLMDebug ist im Windows SDK enthalten. Weitere Informationen finden Sie unter [**PLMDebug**](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx). 

## <a name="run-another-process-inside-the-full-trust-container"></a>Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container 

Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen. Dies kann nützlich sein, um Szenarien zu testen (z. B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten). Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```: 

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

