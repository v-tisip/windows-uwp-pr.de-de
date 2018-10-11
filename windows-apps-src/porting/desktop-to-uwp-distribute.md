---
author: normesta
Description: Distribute a packaged desktop application (Desktop Bridge)
Search.Product: eADQiWindows 10XVcnh
title: Veröffentlichen Sie Ihre verpackte desktop-Anwendung auf einem Windows Store oder querladen es auf einem oder mehreren Geräten.
ms.author: normesta
ms.date: 05/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: edff3787-cecb-4054-9a2d-1fbefa79efc4
ms.localizationpriority: medium
ms.openlocfilehash: c81e8d07efa04e93128089eaec78fb83b822a4b9
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4533501"
---
# <a name="distribute-a-packaged-desktop-application"></a>Verteilen einer verpackten desktop-Anwendungs

Veröffentlichen Sie Ihre verpackte desktop-Anwendung auf einem Windows Store oder querladen es auf einem oder mehreren Geräten.  

> [!NOTE]
> Haben Sie einen Plan wie Sie Benutzern auf Ihre verpackte Anwendung Übergang ermöglichen können? Schauen Sie sich den Abschnitt [Umstellung von Benutzern auf Ihre verpackte App](#transition-users) dieses Handbuchs an, um eine Vorstellung davon zu bekommen, bevor Sie Ihre App verteilen.

## <a name="distribute-your-application-by-publishing-it-to-the-microsoft-store"></a>Verteilen Sie Ihre Anwendung, indem sie an den Microsoft Store veröffentlichen.

Der [Microsoft Store](https://www.microsoft.com/store/apps) ist eine bequeme Möglichkeit für Kunden, Ihre App zu beziehen.

Veröffentlichen Sie Ihre Anwendung in diesem Store, um die größtmögliche Zielgruppe zu erreichen. Darüber hinaus können Unternehmenskunden Ihre Anwendung intern in ihren Organisationen über den [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store)verteilen erwerben.

Wenn Sie eine Veröffentlichung im Microsoft Store planen, werden Ihnen als Teil des Übermittlungsprozesses einige zusätzliche Fragen gestellt. Der Grund dafür ist, dass Ihr Paketmanifest eine eingeschränkte Funktion mit dem Namen **runFullTrust** deklariert und wir die Verwendung dieser Funktion durch Ihre Anwendung genehmigen müssen. Weitere Informationen zu dieser Anforderung finden Sie hier: [Eingeschränkte Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#restricted-capabilities).

Sie müssen Ihre Anwendung zu signieren, bevor Sie sie an den Store übermitteln.

>[!IMPORTANT]
> Wenn Sie Ihre Anwendung an den Microsoft Store veröffentlichen möchten, stellen Sie sicher, dass Ihre Anwendung korrekt auf Geräten unter Windows 10 s ausgeführt Dies ist eine Anforderung des Stores. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

<a id="side-load" />

## <a name="distribute-your-application-without-placing-it-onto-the-microsoft-store"></a>Verteilen Sie Ihre Anwendung ohne sie auf der Microsoft Store

Wenn Sie lieber Ihre Anwendung verteilen würde ohne Verwendung des Stores, können Sie apps auf einem oder mehreren Geräten manuell vertreiben.

Dies eignet sich ggf., wenn Sie eine bessere Kontrolle über die Verteilung haben oder sich nicht mit dem Microsoft Store-Zertifizierungsprozess auseinandersetzen möchten.

Um Ihre Anwendung auf anderen Geräten zu verteilen, ohne sie auf den Store müssen Sie ein Zertifikat benötigen, Signieren Sie Ihre Anwendung mithilfe von das Zertifikat, und klicken Sie dann den querladen Ihrer Anwendung auf diesen Geräten.

Sie können [ein Zertifikat erstellen](../packaging/create-certificate-package-signing.md) oder eines von einem beliebten Anbieter wie z.B. [Verisign](https://www.verisign.com/) erhalten.

Wenn Ihre Anwendung auf Geräten zu verteilen, auf denen Windows 10 S ausgeführt werden soll, muss die Anwendung vom Microsoft Store signiert werden, daher müssen Sie die Store-Übermittlung durchlaufen, bevor Sie Ihre Anwendung auf diesen Geräte vertreiben können.

Wenn Sie ein Zertifikat zu erstellen, müssen Sie es im Zertifikatspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** von jedem Gerät installieren, auf dem Ihre App ausgeführt wird. Wenn Sie ein Zertifikat von einem beliebten Anbieter erhalten, müssen Sie auf anderen Systemen neben Ihrer App nichts weiteres installieren.  

> [!IMPORTANT]
> Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

Um Ihre Anwendung mit einem Zertifikat zu signieren, finden Sie in der [Anmeldung eines Anwendungspakets mithilfe von SignTool](../packaging/sign-app-package-using-signtool.md).

Querladen Ihrer Anwendung auf anderen Geräten finden Sie unter [Querladen von Branchen-apps in Windows 10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).

**Videos**

|Veröffentlichen Sie die Anwendung in der Microsoft Store |Verteilen Sie eine Enterprise-Anwendung  |
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Windows-Store-Publication-3cWyG5WhD_5506218965"      width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Distribution-for-Enterprise-Apps-XJ5Hd5WhD_1106218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<a id="transition-users" />

## <a name="transition-users-to-your-packaged-app"></a>Umstellung von Benutzern auf Ihre verpackte App

Bevor Sie Ihre App verteilen, sollten Sie das Hinzufügen einiger Erweiterungen zu Ihrem Paketmanifest in Betracht ziehen, damit sich Benutzer daran gewöhnen, Ihre verpackte App zu verwenden. Hier sind einige Dinge, die Sie tun können.

* Verweisen Sie mit vorhandenen Startkacheln und Taskleistenschaltflächen auf Ihre verpackte App.
* Ihres Anwendungspakets einer Gruppe von Dateitypen zuordnen.
* Stellen Sie Ihre verpackte Anwendung, die bestimmte Dateitypen standardmäßig öffnet.

Eine vollständige Liste der Erweiterungen und die Richtlinien für deren Verwendung finden Sie unter [Umstellung von Benutzern auf Ihre App](desktop-to-uwp-extensions.md#transition-users-to-your-app).

Erwägen Sie außerdem das Hinzufügen von Code zu Ihrer verpackten Anwendung, die diese Aufgaben erledigt:

* Migrieren von Benutzerdaten, die mit Ihrer desktop-Anwendung auf den entsprechenden Ordnerspeicherorten Ihrer verpackten App verknüpft ist.
* Bereitstellung der Option für Benutzer, die Desktopversion Ihrer App zu deinstallieren

Erfahren wir mehr über diese einzelnen Aufgaben. Wir beginnen mit der Migration von Benutzerdaten.

### <a name="migrate-user-data"></a>Migrieren von Benutzerdaten

Wenn Sie vorhaben, Code hinzufügen, der migriert Benutzerdaten, empfiehlt es sich, diesen Code nur ausgeführt, wenn die Anwendung das erste Mal gestartet wird. Bevor Sie die Benutzerdaten migrieren, zeigen Sie dem Benutzer ein Dialogfeld an, das erläutert, was passiert, warum es empfohlen wird und was mit den vorhandenen Daten geschehen wird.

Hier ist ein Beispiel, wie Sie dies in einer NET-basierten verpackten App erreichen können.

```csharp
private void MigrateUserData()
{
    String sourceDir = Environment.GetFolderPath
        (Environment.SpecialFolder.ApplicationData) + "\\AppName";

    if (sourceDir != null)
    {
        DialogResult migrateResult = MessageBox.Show
            ("Would you like to migrate your data from the previous version of this app?",
             "Data Migration", MessageBoxButtons.YesNo);

        if (migrateResult.Equals(DialogResult.Yes))
        {
            String destinationDir =
                Windows.Storage.ApplicationData.Current.LocalFolder.Path + "\\AppName";

            Process process = new Process();
            process.StartInfo.FileName = "robocopy.exe";
            process.StartInfo.Arguments = "%LOCALAPPDATA%\\AppName " + destinationDir + " /move";
            process.StartInfo.CreateNoWindow = true;
            process.Start();
            process.WaitForExit();

            if (process.ExitCode > 1)
            {
                //Migration was unsuccessful -- you can choose to block/retry/other action
            }
        }
    }
}
```

### <a name="uninstall-the-desktop-version-of-your-app"></a>Deinstallieren Sie die Desktopversion Ihrer App.

Es ist besser, die Benutzer-desktop-Anwendung ohne diese Berechtigung nicht deinstallieren. Zeigen Sie ein Dialogfeld an, das den Benutzer nach dieser Berechtigung fragt. Benutzer möchten gegebenenfalls die Desktop-Version Ihrer App nicht deinstallieren. In diesem Fall müssen Sie entscheiden, ob Sie die Nutzung der desktop-Anwendung blockieren oder die Side-by-Side-Nutzung beider Apps unterstützen möchten.

Hier ist ein Beispiel, wie Sie dies in einer NET-basierten verpackten App erreichen können.

Den vollständigen Kontext dieses Codeausschnitts finden Sie in der **MainWindow.cs**-Datei des Beispiels [WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).

```csharp
private void RemoveDesktopApp()
{              
    //Typically, you can find your uninstall string at this location.
    String uninstallString = (String)Microsoft.Win32.Registry.GetValue
        (@"HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion" +
         @"\Uninstall\{7AD02FB8-B85E-44BC-8998-F4803BA5A0E3}\", "UninstallString", null);

    //Detect if the previous version of the Desktop application is installed.
    if (uninstallString != null)
    {
        DialogResult uninstallResult = MessageBox.Show
            ("To have the best experience, consider uninstalling the "
              + " previous version of this app. Would you like to do that now?",
              "Uninstall the previous version", MessageBoxButtons.YesNo);

        if (uninstallResult.Equals(DialogResult.Yes))
        {
                    string[] uninstallArgs = uninstallString.Split(' ');

            Process process = new Process();
            process.StartInfo.FileName = uninstallArgs[0];
            process.StartInfo.Arguments = uninstallArgs[1];
            process.StartInfo.CreateNoWindow = true;

            process.Start();
            process.WaitForExit();

            if (process.ExitCode != 0)
            {
                //Uninstallation was unsuccessful - You can choose to block the application here.
            }
        }
    }

}
```

### <a name="video"></a>Video

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Transition-Taskbar-Pins-Start-Tiles-File-Type-Associations-and-Protocol-Handlers-MD5mv5WhD_2406218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

Wenn beim Veröffentlichen Ihrer Anwendung an den Store Probleme auftreten, enthält dieser [Blogbeitrag](https://blogs.msdn.microsoft.com/appconsult/2017/09/25/preparing-a-desktop-bridge-application-for-the-store-submission/) einige hilfreiche Tipps.

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
