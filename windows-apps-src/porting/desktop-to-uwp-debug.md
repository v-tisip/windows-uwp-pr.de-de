---
author: normesta
Description: "Führen Sie Ihre verpackte App aus und prüfen Sie, wie sie aussieht, ohne sie zu signieren. Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen. Wenn Sie bereit sind, Ihre App in einer Produktionsumgebung zu testen, signieren Sie Ihre App und installieren Sie sie."
Search.Product: eADQiWindows 10XVcnh
title: "Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)"
ms.author: normesta
ms.date: 06/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: f45d8b14-02d1-42e1-98df-6c03ce397fd3
ms.openlocfilehash: c160fecc530a6366de48f4f2ecc24df2463c0469
ms.sourcegitcommit: 77bbd060f9253f2b03f0b9d74954c187bceb4a30
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2017
---
# <a name="run-debug-and-test-a-packaged-desktop-app-desktop-bridge"></a>Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)

Führen Sie Ihre verpackte App aus und prüfen Sie, wie sie aussieht, ohne sie zu signieren. Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen. Wenn Sie bereit sind, Ihre App in einer Produktionsumgebung zu testen, signieren Sie Ihre App und installieren Sie sie. In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.

<span id="run-app" />
## <a name="run-your-app"></a>Ausführen der App

Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen.

Wenn Sie Ihr Paket mit einem UWP-Projekt in Visual Studio erstellt haben, legen Sie das Verpackungsprojekt als Startprojekt fest und drücken Sie dann STRG+F5, um Ihre App zu starten.

Wenn Sie den Desktop App Converter verwendet oder Ihre App manuell verpackt haben, öffnen Sie eine Windows PowerShell-Befehlsaufforderung, und führen Sie dieses Cmdlet vom **PacakgeFiles**-Unterordner des Ausgabeordners aus:

```
Add-AppxPackage –Register AppxManifest.xml
```
Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.

![Verpackte App im Startmenü.](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.

## <a name="debug-your-app"></a>Debuggen Sie Ihre App

Wählen Sie Ihr Paket in einem Dialogfeld bei jedem Debuggen Ihrer App oder Installieren einer Erweiterung aus und Debuggen Sie Ihre App ohne jedes Mal Ihr Paket auszuwählen.

### <a name="debug-your-app-by-selecting-the-package"></a>Debuggen Sie Ihre App, indem Sie das Paket auswählen

Diese Option hat die kürzeste Einrichtungszeit, aber Sie müssen bei der Ausführung jeder Debugsitzung einen zusätzlichen Schritt durchführen.


1. Stellen Sie sicher, dass Sie Ihr App-Paket mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.

   Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.

2. Starten Sie Visual Studio.

   Wenn Sie Ihre App mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio anhand der Option **als Administrator ausführen**.

3. Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.

4. In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.


### <a name="debug-your-app-without-having-to-select-the-package"></a>Debuggen Sie Ihre App ohne das Paket auswählen zu müssen

Diese Option hat die längste Einrichtungszeit, jedoch werden Sie nicht das installiere Paket jedes Mal beim Starten Ihrer App auswählen müssen. Sie müssen [Visual Studio2017](https://www.visualstudio.com/vs/whatsnew/) installieren, um diese Option nutzen zu können.

1. Installieren Sie zunächst die [Desktop-Brücke Debugging Project](http://go.microsoft.com/fwlink/?LinkId=797871).

2. Starten Sie Visual Studio, und öffnen Sie das Projekt für die Desktop-Anwendung.

6. Hinzufügen eines **Debuggen von Desktop-Brücke**-Projekts zur Projektmappe.

   Sie finden die Projektvorlage in der Gruppe **Andere Projekttypen** der installierten Vorlagen.

    ![alt](images/desktop-to-uwp/debug-2.png)

    Das **Debuggen von Desktop-Brücke**-Projekt wird in der Projektmappe angezeigt.

    ![alt](images/desktop-to-uwp/debug-3.png)

7. Öffnen Sie die Eigenschaftenseiten des **Debuggen von Desktop-Brücke**-Projekts.

8. Legen Sie das **Paketlayout**-Feld auf den Speicherort Ihres Manifestdateienpakets (AppxManifest.xml) fest, und wählen Sie die ausführbare Datei Ihrer App aus der Dropdown-Liste **Kachel starten**.

     ![alt](images/desktop-to-uwp/debug-4.png)

8. Öffnen Sie die Datei AppXPackageFileList.xml im Code-Editor.

9. Entfernen Sie Kommentare aus dem XML-Block, und geben Sie die Werte für diese Elemente ein:

   **MyProjectOutputPath**: Der relative Pfad zum Ordner „Debug” von Ihrer Desktop-Anwendung.

   **LayoutFile**: Die ausführbare Datei, die im Ordner „Debug” von Ihrer Desktop-Anwendung ist.

   **PackagePath**: Der vollqualifizierte Name für die ausführbare Datei Ihrer Desktop-Anwendung, die zu Ihrem Windows-App-Paketordner während der Konvertierung kopiert wurde.

    Beispiel:

    ```XML
  <?xml version="1.0" encoding="utf-8"?>
  <Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
     <MyProjectOutputPath>..\MyDesktopApp\bin\Debug</MyProjectOutputPath>
    </PropertyGroup>
    <ItemGroup>
      <LayoutFile Include="$(MyProjectOutputPath)\MyDesktopApp.exe">
        <PackagePath>$(PackageLayout)\MyDesktopApp.exe</PackagePath>
      </LayoutFile>
    </ItemGroup>
  </Project>
    ```

  Wenn Ihre App DLL-Dateien nutzt, die von anderen Projekten in Ihrer Projektmappe generiert werden, und Sie den Code ändern wollen, der in diesen DLL-Dateien enthalten ist, dann fügen Sie für diese DLL-Dateien ein **LayoutFile**-Element ein.

  ```XML
  ...
      <LayoutFile Include="$(MyProjectOutputPath)\MyDesktopApp.Models.dll">
      <PackagePath>$(PackageLayout)\MyDesktopApp.Models.dll</PackagePath>
      </LayoutFile>
  ...
  ```

10. Legen Sie das Paketprojekt als Startprojekt fest.  

    ![alt](images/desktop-to-uwp/debug-5.png)

11. Legen Sie Haltepunkte im Code Ihrer Desktop-Anwendung fest, und starten Sie den Debugger.

  ![Debug-Schaltfläche](images/desktop-to-uwp/debugger-button.png)

  Visual Studio kopiert die ausführbaren und DLL-Dateien, die Sie in der XML-Datei für Ihr Windows-App-Paket angegeben haben, und startet dann den Debugger.

#### <a name="handle-multiple-build-configurations"></a>Mehrere Buildkonfigurationen steuern

Wenn Sie mehrere Buildkonfigurationen definiert haben (z.B.: Veröffentlichen und Debuggen), können Sie die Datei AppXPackageFileList.xml ändern, um nur die Dateien zu kopieren, die der Buildkonfiguration entspricht, die Sie in Visual Studio beim Starten des Debuggers gewählt haben.

Beispiel:

```XML
<PropertyGroup>
    <MyProjectOutputPath Condition="$(Configuration) == 'Debug'">..\MyDesktopApp\bin\Debug</MyProjectOutputPath>
    <MyProjectOutputPath Condition="$(Configuration) == 'Release'"> ..\MyDesktopApp\bin\Release</MyProjectOutputPath>
</PropertyGroup>
```

#### <a name="debug-uwp-enhancements-to-your-app"></a>Debuggen von UWP-Erweiterungen für Ihre App

Sie möchten vielleicht Ihre App mit modernen Funktionen wie Live-Kacheln optimieren. Wenn das der Fall ist, können Sie bedingte Kompilierung verwenden, um Codepfade mit bestimmten Buildkonfigurationen zu aktivieren.

1. Definieren Sie zunächst in Visual Studio eine Buildkonfiguration und geben Sie ihr einen Namen wie „DesktopUWP”.

2. Fügen Sie in der Registerkarte **Build** der Projekteigenschaften Ihres Projekts den Namen im Feld **Symbole für bedingte Kompilierung** hinzu.

     ![alt](images/desktop-to-uwp/debug-8.png)

3. Fügen Sie bedingte Codeblöcke hinzu. Dieser Code wird nur für die **DesktopUWP**-Buildkonfiguration kompiliert.

    ```csharp
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

### <a name="debug-the-entire-app-lifecycle"></a>Debuggen des gesamten App-Lebenszyklus

In einigen Fällen empfiehlt sich eine differenziertere Steuerung des Debugging-Vorgangs, wenn z.B. das Debuggen erfolgen soll, bevor die App gestartet wird.

Sie können [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) verwenden, um volle Kontrolle über den App-Lebenszyklus zu erhalten, einschließlich über das Anhalten, Fortsetzen und Beenden.

[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.


### <a name="modify-your-app-in-between-debug-sessions"></a>Ändern Sie Ihre App zwischen Debugsitzungen

Wenn Sie an Ihrer App Änderungen vornehmen, um Fehlern zu beheben, wechseln Sie sie anhand des MakeAppx-Tools aus. Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).

## <a name="test-your-app"></a>Testen der App

Um Ihre App vor der Verteilung in einer realistischen Umgebung zu testen, empfiehlt es sich, Ihre App zu signieren und sie anschließend zu installieren.

Wenn Sie Ihre App anhand Visual Studio verpackt haben, können Sie ein Skript zum Signieren Ihrer App ausführen und sie anschließend installieren. Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).

Wenn Sie Ihre App mithilfe des Desktop App Converters verpackt haben, können Sie die ``sign``-Parameter verwenden, um Ihre App automatisch mit einem generierten Zertifikat zu signieren. Sie müssen das Zertifikat und anschließend die App installieren. Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).   

Sie können Ihre App auch manuell signieren. So geht’s

1. Erstellen eines Zertifikats. Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).

2. Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.

3. Signieren Sie Ihre App anhand des Zertifikats. Weiter Informationen finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).

  > [!IMPORTANT]
  > Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

### <a name="related-sample"></a>Verwandte Beispiele

[SigningCerts](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-app-for-windows-10-s"></a>Testen Sie Ihre App für Windows 10 S.

Bevor Sie Ihre App veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Wenn Sie Ihre App im Windows Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist. Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert. 

Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).

### <a name="run-another-process-inside-the-full-trust-container"></a>Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container

Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen. Dies kann nützlich sein, um Szenarien zu testen (z.B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten). Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```:

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

## <a name="next-steps"></a>Nächste Schritte

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
