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
ms.openlocfilehash: b5110eebde087593f07704e89c2e4708b2fcbb8b
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4501466"
---
# <a name="run-debug-and-test-a-packaged-desktop-application"></a>Führen Sie aus, Debuggen Sie und Testen Sie eine verpackte desktop-Anwendung

Führen Sie Ihre verpackte Anwendung, und sehen Sie, wie sie aussieht, ohne zu signieren. Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen. Wenn Sie bereit sind, Ihre Anwendung in einer produktiven Umgebung testen, Signieren Sie Ihre Anwendung, und installieren Sie es. In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.

<a id="run-app" />

## <a name="run-your-application"></a>Führen Sie Ihre Anwendung

Sie können Ihre Anwendung zu testen, lokal ohne Erwerb eines Zertifikats und signieren Sie es ausführen. Die Ausführung der Anwendungs richtet sich nach tool verwendet, um das Paket zu erstellen.

### <a name="you-created-the-package-by-using-visual-studio"></a>Erstellen des Pakets mit Visual Studio

Legen Sie das Paketerstellungsprojekt als Startprojekt fest, und drücken Sie anschließend Strg+F5, um Ihre App zu starten.

### <a name="you-created-the-package-manually-or-by-using-the-desktop-app-converter"></a>Erstellen des Pakets manuell oder mithilfe des Desktop App Converter

Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie dieses Cmdlet aus dem Unterordner **PackageFiles** Ihres Ausgabeordners aus:

```
Add-AppxPackage –Register AppxManifest.xml
```
Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.

![Anwendungspaket im Menü "Start"](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> Eine Anwendung immer als interaktiver Benutzer ausgeführt wird, und jedes Laufwerk durch die Installation Ihres Anwendungspakets zu muss auf NTFS-Format formatiert sein.

## <a name="debug-your-app"></a>Debuggen Sie Ihre App

Wie Sie die Anwendung debuggen, hängt von tool verwendet, um das Paket zu erstellen.

Wenn Sie Ihr Paket mithilfe des in Version 15.4 von Visual Studio 2017 verfügbaren [neuen Paketerstellungsprojekts](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) erstellt haben, legen Sie das Paketerstellungsprojekt als Startprojekt fest und drücken Sie F5, um Ihre App zu debuggen.

Wenn Sie Ihr Paket mit einem anderen Tool erstellt haben, gehen Sie folgendermaßen vor.

1. Stellen Sie sicher, dass Sie die verpackte Anwendung mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.

   Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.

2. Starten Sie Visual Studio.

   Wenn Sie die Anwendung mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio mithilfe der Option " **als Administrator ausführen** ".

3. Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.

4. In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.

#### <a name="modify-your-application-in-between-debug-sessions"></a>Ändern Sie Ihre Anwendung zwischen Debugsitzungen

Wenn Sie Ihre Änderungen an Ihrer Anwendung um Fehlern zu beheben, wechseln Sie sie mithilfe des MakeAppx-Tools. Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).

### <a name="debug-the-entire-application-lifecycle"></a>Debuggen des gesamten Anwendungslebenszyklus

In einigen Fällen sollten Sie eine differenziertere Steuerung des debugging-Vorgangs, einschließlich der Möglichkeit zum Debuggen Ihrer Anwendung, bevor er beginnt.

[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) können Sie die vollständige Kontrolle über den Anwendungslebenszyklus einschließlich anhalten, fortsetzen und beenden erhalten.

[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.

## <a name="test-your-app"></a>Testen der App

Zum Testen Ihrer Anwendung in einer realistischen, wie Sie vor der Verteilung, empfiehlt es sich zum Signieren Ihrer Anwendungs, und installieren Sie es.

### <a name="test-an-application-that-you-packaged-by-using-visual-studio"></a>Testen Sie eine Anwendung, die mit Visual Studio verpackten

Visual Studio signiert Ihre Anwendung mit einem Testzertifikat. Sie finden dieses Zertifikat im Ausgabeordner, den der Assistent **App-Pakete erstellen** generiert. Die Zertifikatsdatei hat die *CER* -Erweiterung, und Sie müssen das Zertifikat im Speicher **Vertrauenswürdige Stammzertifizierungsstellen** auf dem PC installieren, die Sie Ihre Anwendung auf testen möchten. Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).

### <a name="test-an-application-that-you-packaged-by-using-the-desktop-app-converter-dac"></a>Testen Sie eine Anwendung, die mit der Desktop App Converter (DAC) verpackten

Wenn Sie Ihre Anwendung mithilfe der Desktop App Converter Verpacken, können Sie mithilfe der ``sign`` Parameter, um Ihre Anwendung automatisch mit einem generierten Zertifikat zu signieren. Sie müssen das Zertifikat und anschließend die App installieren. Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).   


### <a name="manually-sign-apps-optional"></a>Manuelles signieren von Apps (Optional)

Sie können die Anwendung auch manuell signieren. So geht’s

1. Erstellen eines Zertifikats. Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).

2. Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.

3. Signieren Sie Ihre Anwendung mithilfe dieses Zertifikat, finden Sie unter [Signieren eines app-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).

  > [!IMPORTANT]
  > Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

    **Verwandte Beispiele**

    [SigningCerts](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-application-for-windows-10-s"></a>Testen Sie Ihre Anwendung für Windows 10 S

Bevor Sie Ihre app veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten, auf denen Windows 10 s ausgeführt Tatsächlich, wenn Sie Ihre Anwendung an den Microsoft Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist. Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert.

[Test der Windows-Anwendung für Windows 10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s)angezeigt.

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
