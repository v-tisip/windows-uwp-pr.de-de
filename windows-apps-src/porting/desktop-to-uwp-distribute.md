---
author: normesta
Description: Distribute a packaged desktop app (Desktop Bridge)
Search.Product: eADQiWindows 10XVcnh
title: Veröffentlichen Sie Ihre verpackte Desktop-App auf einem Windows Store oder laden Sie es auf einem oder mehreren Geräten quer.
ms.author: normesta
ms.date: 05/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: edff3787-cecb-4054-9a2d-1fbefa79efc4
ms.localizationpriority: medium
ms.openlocfilehash: fe36fec72645558c539dd8270fd15d35d92b66b5
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4060180"
---
# <a name="distribute-a-packaged-desktop-app-desktop-bridge"></a>Verteilen einer verpackten Desktop-App (Desktop-Brücke)

Veröffentlichen Sie Ihre verpackte Desktop-App auf einem Windows Store oder laden Sie es auf einem oder mehreren Geräten quer.  

> [!NOTE]
> Haben Sie einen Plan, wie Sie für Benutzer den Übergang auf Ihre verpackte App ermöglichen können? Schauen Sie sich den Abschnitt [Umstellung von Benutzern auf Ihre verpackte App](#transition-users) dieses Handbuchs an, um eine Vorstellung davon zu bekommen, bevor Sie Ihre App verteilen.

## <a name="distribute-your-app-by-publishing-it-to-the-microsoft-store"></a>Verteilen Ihrer App durch Veröffentlichung im Microsoft Store

Der [Microsoft Store](https://www.microsoft.com/store/apps) ist eine bequeme Möglichkeit für Kunden, Ihre App zu beziehen.

Veröffentlichen Sie Ihre App in diesem Store, um die größtmögliche Zielgruppe zu erreichen. Außerdem können Unternehmenskunden Ihre App erwerben und sie intern in ihren Organisationen über den [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) verteilen.

Wenn Sie eine Veröffentlichung im Microsoft Store planen, werden Ihnen als Teil des Übermittlungsprozesses einige zusätzliche Fragen gestellt. Der Grund dafür ist, dass Ihr Paketmanifest eine eingeschränkte Funktion mit dem Namen **runFullTrust** deklariert und wir die Verwendung dieser Funktion durch Ihre Anwendung genehmigen müssen. Weitere Informationen zu dieser Anforderung finden Sie hier: [Eingeschränkte Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#restricted-capabilities).

Sie müssen Ihre App nicht signieren, bevor Sie sie an den Store übermitteln.

>[!IMPORTANT]
> Wenn Sie Ihre App im Microsoft Store veröffentlichen möchten, stellen Sie sicher, dass Ihre App auf Geräten, auf denen Windows10 S ausgeführt wird, ordnungsgemäß ausgeführt wird. Dies ist eine Store-Anforderung. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

<a id="side-load" />

## <a name="distribute-your-app-without-placing-it-onto-the-microsoft-store"></a>Verteilen Sie Ihre App, ohne sie auf dem Microsoft Store zu veröffentlichen.

Wenn Sie Ihre App lieber verteilen, ohne sie auf dem Store zu veröffentlichen, können Sie Apps auf einem oder mehreren Geräten manuell vertreiben.

Dies eignet sich ggf., wenn Sie eine bessere Kontrolle über die Verteilung haben oder sich nicht mit dem Microsoft Store-Zertifizierungsprozess auseinandersetzen möchten.

Um Ihre App auf anderen Geräten zu verteilen, ohne sie im Store zu veröffentlichen, müssen Sie ein Zertifikat einholen, Ihre App anhand dieses Zertifikats signieren und sie anschließend auf diese Geräte querladen.

Sie können [ein Zertifikat erstellen](../packaging/create-certificate-package-signing.md) oder eines von einem beliebten Anbieter wie z.B. [Verisign](https://www.verisign.com/) erhalten.

Wenn Sie Ihre App auf Geräten mit Windows 10 S verteilen möchten, muss Ihre App vom Microsoft Store signiert werden. Daher müssen Sie den Prozess für die Store-Übermittlung durchlaufen, bevor Sie Ihre App auf diesen Geräte vertreiben können.

Wenn Sie ein Zertifikat zu erstellen, müssen Sie es im Zertifikatspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** von jedem Gerät installieren, auf dem Ihre App ausgeführt wird. Wenn Sie ein Zertifikat von einem beliebten Anbieter erhalten, müssen Sie auf anderen Systemen neben Ihrer App nichts weiteres installieren.  

> [!IMPORTANT]
> Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

Weitere Informationen zum Signieren Ihrer App anhand des Zertifikats finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).

Weitere Informationen zum Querladen Ihrer App auf anderen Geräten finden Sie unter [querladen von Branchen-Apps in Windows10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).

**Videos**

|Veröffentlichen Ihrer App im MicrosoftStore |Verteilen einer Unternehmens-App  |
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Windows-Store-Publication-3cWyG5WhD_5506218965"      width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Distribution-for-Enterprise-Apps-XJ5Hd5WhD_1106218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<a id="transition-users" />

## <a name="transition-users-to-your-packaged-app"></a>Umstellung von Benutzern auf Ihre verpackte App

Bevor Sie Ihre App verteilen, sollten Sie das Hinzufügen einiger Erweiterungen zu Ihrem Paketmanifest in Betracht ziehen, damit sich Benutzer daran gewöhnen, Ihre verpackte App zu verwenden. Hier sind einige Dinge, die Sie tun können.

* Verweisen Sie mit vorhandenen Startkacheln und Taskleistenschaltflächen auf Ihre verpackte App.
* Ordnen Sie Ihre verpackte App einer Gruppe von Dateitypen zu.
* Sorgen Sie dafür, dass Ihre verpackte App bestimmte Dateitypen standardmäßig öffnet.

Eine vollständige Liste der Erweiterungen und die Richtlinien für deren Verwendung finden Sie unter [Umstellung von Benutzern auf Ihre App](desktop-to-uwp-extensions.md#transition-users-to-your-app).

Erwägen Sie außerdem das Hinzufügen von Code zu Ihrer verpackten App, der die folgenden Aufgaben erledigt:

* Migration von Benutzerdaten, die Ihrer Desktop-App zugeordnet sind, zu den entsprechenden Ordnerspeicherorten Ihrer verpackten App
* Bereitstellung der Option für Benutzer, die Desktopversion Ihrer App zu deinstallieren

Erfahren wir mehr über diese einzelnen Aufgaben. Wir beginnen mit der Migration von Benutzerdaten.

### <a name="migrate-user-data"></a>Migrieren von Benutzerdaten

Wenn Sie Code hinzufügen, durch den Benutzerdaten migriert werden, empfiehlt es sich, diesen Code nur dann auszuführen, wenn die App das erste Mal gestartet wird. Bevor Sie die Benutzerdaten migrieren, zeigen Sie dem Benutzer ein Dialogfeld an, das erläutert, was passiert, warum es empfohlen wird und was mit den vorhandenen Daten geschehen wird.

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

Die Desktop-App des Benutzers sollte nicht deinstalliert werden, ohne nach der Berechtigung zu fragen. Zeigen Sie ein Dialogfeld an, das den Benutzer nach dieser Berechtigung fragt. Benutzer möchten gegebenenfalls die Desktop-Version Ihrer App nicht deinstallieren. In diesem Fall müssen Sie entscheiden, ob Sie die Nutzung der Desktop-App blockieren oder die parallele Nutzung beider Apps unterstützen wollen.

Hier ist ein Beispiel, wie Sie dies in einer NET-basierten verpackten App erreichen können.

Den vollständigen Kontext dieses Codeausschnitts finden Sie in der **MainWindow.cs**-Datei des Beispiels [WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).

```csharp
private void RemoveDesktopApp()
{              
    //Typically, you can find your uninstall string at this location.
    String uninstallString = (String)Microsoft.Win32.Registry.GetValue
        (@"HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion" +
         @"\Uninstall\{7AD02FB8-B85E-44BC-8998-F4803BA5A0E3}\", "UninstallString", null);

    //Detect if the previous version of the Desktop App is installed.
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
                //Uninstallation was unsuccessful - You can choose to block the app here.
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
