---
author: normesta
Description: Run your packaged app and see how it looks without having to sign it. Then, set breakpoints and step through code. When you're ready to test your app in a production environment, sign your app and then install it.
Search.Product: eADQiWindows 10XVcnh
title: Ausführen, Debuggen und Testen einer verpackten Desktop-App (Desktop-Brücke)
ms.author: normesta
ms.date: 08/31/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: f45d8b14-02d1-42e1-98df-6c03ce397fd3
ms.localizationpriority: medium
ms.openlocfilehash: 0f8d443bc201d0e60387673edb7f9b73e2e47490
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1662680"
---
# <a name="run-debug-and-test-a-packaged-desktop-app-desktop-bridge"></a>Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)

Führen Sie Ihre verpackte App aus und prüfen Sie, wie sie aussieht, ohne sie zu signieren. Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen. Wenn Sie bereit sind, Ihre App in einer Produktionsumgebung zu testen, signieren Sie Ihre App und installieren Sie sie. In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.

<a id="run-app" />

## <a name="run-your-app"></a>Ausführen der App

Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen. Wie Sie die App ausführen, hängt von dem Tool ab, das Sie beim Erstellen des Pakets verwendet haben.

### <a name="you-created-the-package-by-using-visual-studio"></a>Erstellen des Pakets mit Visual Studio

Legen Sie das Paketerstellungsprojekt als Startprojekt fest, und drücken Sie anschließend Strg+F5, um Ihre App zu starten.

### <a name="you-created-the-package-manually-or-by-using-the-desktop-app-converter"></a>Erstellen des Pakets manuell oder mithilfe des Desktop App Converter

Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie dieses Cmdlet aus dem Unterordner **PackageFiles** Ihres Ausgabeordners aus:

```
Add-AppxPackage –Register AppxManifest.xml
```
Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.

![Verpackte App im Startmenü.](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.

## <a name="debug-your-app"></a>Debuggen Sie Ihre App

Wie Sie die App debuggen, hängt von dem Tool ab, das Sie beim Erstellen des Pakets verwendet haben.

Wenn Sie Ihr Paket mithilfe des in Version 15.4 von Visual Studio 2017 verfügbaren [neuen Paketerstellungsprojekts](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) erstellt haben, legen Sie das Paketerstellungsprojekt als Startprojekt fest und drücken Sie F5, um Ihre App zu debuggen.

Wenn Sie Ihr Paket mit einem anderen Tool erstellt haben, gehen Sie folgendermaßen vor.

1. Stellen Sie sicher, dass Sie Ihr App-Paket mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.

   Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.

2. Starten Sie Visual Studio.

   Wenn Sie Ihre App mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio anhand der Option **als Administrator ausführen**.

3. Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.

4. In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.

#### <a name="modify-your-app-in-between-debug-sessions"></a>Ändern Sie Ihre App zwischen Debugsitzungen

Wenn Sie an Ihrer App Änderungen vornehmen, um Fehlern zu beheben, wechseln Sie sie anhand des MakeAppx-Tools aus. Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).

### <a name="debug-the-entire-app-lifecycle"></a>Debuggen des gesamten App-Lebenszyklus

In einigen Fällen empfiehlt sich eine differenziertere Steuerung des Debugging-Vorgangs, wenn z.B. das Debuggen erfolgen soll, bevor die App gestartet wird.

Sie können [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) verwenden, um volle Kontrolle über den App-Lebenszyklus zu erhalten, einschließlich über das Anhalten, Fortsetzen und Beenden.

[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.

## <a name="test-your-app"></a>Testen der App

Um Ihre App vor der Verteilung in einer realistischen Umgebung zu testen, empfiehlt es sich, Ihre App zu signieren und sie anschließend zu installieren.

### <a name="test-an-app-that-you-packaged-by-using-visual-studio"></a>Testen einer mit Visual Studio verpackten App

Visual Studio signiert Ihre App mit einem Testzertifikat. Sie finden dieses Zertifikat im Ausgabeordner, den der Assistent **App-Pakete erstellen** generiert. Die Zertifikatsdatei hat die Erweiterung *.cer*, und Sie müssen dieses Zertifikat im Speicher für **Vertrauenswürdige Stammzertifizierungsstellen** auf dem PC installieren, auf dem Sie Ihre App testen möchten. Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).

### <a name="test-an-app-that-you-packaged-by-using-the-desktop-app-converter-dac"></a>Testen einer mit dem Desktop App Converter (DAC) verpackten App

Wenn Sie Ihre App mithilfe des Desktop App Converters verpackt haben, können Sie die ``sign``-Parameter verwenden, um Ihre App automatisch mit einem generierten Zertifikat zu signieren. Sie müssen das Zertifikat und anschließend die App installieren. Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).   


### <a name="manually-sign-apps-optional"></a>Manuelles signieren von Apps (Optional)

Sie können Ihre App auch manuell signieren. So geht’s

1. Erstellen eines Zertifikats. Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).

2. Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.

3. Signieren Sie Ihre App anhand des Zertifikats. Weiter Informationen finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).

  > [!IMPORTANT]
  > Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

    **Verwandte Beispiele**

    [SigningCerts](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-app-for-windows-10-s"></a>Testen Sie Ihre App für Windows 10 S.

Bevor Sie Ihre App veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Wenn Sie Ihre App im Microsoft Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist. Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert.

Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).

### <a name="run-another-process-inside-the-full-trust-container"></a>Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container

Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen. Dies kann nützlich sein, um Szenarien zu testen (z.B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten). Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```:

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
