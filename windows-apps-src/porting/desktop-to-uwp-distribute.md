---
author: normesta
Description: "Verteilen einer verpackten Desktop-App (Desktop-Brücke)"
Search.Product: eADQiWindows 10XVcnh
title: "Veröffentlichen Sie Ihre verpackte Desktop-App auf einem Windows Store oder laden Sie es auf einem oder mehreren Geräten quer."
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: edff3787-cecb-4054-9a2d-1fbefa79efc4
ms.openlocfilehash: 24a005309271a91d669322787fb8d341e1a6d6ad
ms.sourcegitcommit: 77bbd060f9253f2b03f0b9d74954c187bceb4a30
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2017
---
# <a name="distribute-a-packaged-desktop-app-desktop-bridge"></a>Verteilen einer verpackten Desktop-App (Desktop-Brücke)

Veröffentlichen Sie Ihre verpackte Desktop-App auf einem Windows Store oder laden Sie es auf einem oder mehreren Geräten quer.  

> [!NOTE]
> Haben Sie einen Plan, wie Sie für Benutzer den Übergang auf Ihre verpackte App ermöglichen können? Schauen Sie sich den Abschnitt [Übergang von Benutzern für Ihre Desktop-Brücke App](#transition-users) dieses Handbuchs an, um eine Vorstellung davon zu bekommen, bevor Sie Ihre App verteilen.

## <a name="distribute-your-app-by-publishing-it-to-the-windows-store"></a>Verteilen Sie Ihre App, indem Sie sie im Windows Store veröffentlichen.

Der [Windows Store](https://www.microsoft.com/store/apps) ist eine bequeme Möglichkeit für Kunden, Ihre App zu beziehen.

<div style="float: left; padding: 10px">
    ![Symbol „Store“](images/desktop-to-uwp/store.png)
</div>
Veröffentlichen Sie Ihre App auf diesen Store, um die größtmögliche Zielgruppe zu erreichen. Darüber hinaus können Unternehmenskunden Ihre App erwerben und sie intern in ihren Organisationen durch den [Windows Store für Unternehmen](https://www.microsoft.com/business-store) verteilen.

Wenn Sie Ihre App auf dem Windows Store veröffentlichen möchten und Sie uns noch nicht kontaktiert haben, füllen Sie [dieses Formular](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge) aus, und Microsoft wird sich bei Ihnen melden, um die Aufnahme zu starten.

Sie müssen Ihre App nicht signieren, bevor Sie sie an den Store übermitteln.

>[!IMPORTANT]
> Wenn Sie Ihre App im Windows Store veröffentlichen möchten, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Dies ist eine Anforderung für den Store. Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).

## <a name="distribute-your-app-without-placing-it-onto-the-windows-store"></a>Verteilen Sie Ihre App, ohne sie auf dem Windows Store zu veröffentlichen.

Wenn Sie Ihre App lieber verteilen, ohne sie auf dem Store zu veröffentlichen, können Sie Apps auf einem oder mehreren Geräten manuell vertreiben.

Dies eignet sich ggf., wenn Sie eine bessere Kontrolle über die Verteilung haben oder sich nicht mit dem Windows Store-Zertifizierungsprozess auseinandersetzen möchten.

Um Ihre App auf anderen Geräten zu verteilen, ohne sie im Store zu veröffentlichen, müssen Sie ein Zertifikat einholen, Ihre App anhand dieses Zertifikats signieren und sie anschließend auf diese Geräte querladen.

Sie können [ein Zertifikat erstellen](../packaging/create-certificate-package-signing.md) oder eines von einem beliebten Anbieter wie z.B. [Verisign](https://www.verisign.com/) erhalten.

Wenn Sie Ihre App auf Geräten mit Windows 10 S verteilen möchten, muss Ihre App vom Windows Store signiert werden. Daher müssen Sie den Prozess für die Store-Übermittlung durchlaufen, bevor Sie Ihre App auf diesen Geräte vertreiben können.

Wenn Sie ein Zertifikat zu erstellen, müssen Sie es im Zertifikatspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** von jedem Gerät installieren, auf dem Ihre App ausgeführt wird. Wenn Sie ein Zertifikat von einem beliebten Anbieter erhalten, müssen Sie auf anderen Systemen neben Ihrer App nichts weiteres installieren.  

> [!IMPORTANT]
> Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.

Weitere Informationen zum Signieren Ihrer App anhand des Zertifikats finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).

Weitere Informationen zum Querladen Ihrer App auf anderen Geräten finden Sie unter [querladen von Branchen-Apps in Windows10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).

**Videos**

|Veröffentlichen Ihrer App im WindowsStore |Verteilen Sie eine Unternehmens-App  |
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Windows-Store-Publication-3cWyG5WhD_5506218965"      width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Distribution-for-Enterprise-Apps-XJ5Hd5WhD_1106218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<span id="transition-users" />
## <a name="transition-users-to-your-desktop-bridge-app"></a>Den Übergang für Benutzer auf Ihre App für die Desktop-Brücke bereitstellen

Bevor Sie Ihre App verteilen, sollten Sie, Ihr Paketmanifest, erhalten mit der Brücke für Desktop-App besteht darin, Benutzern zu helfen einige Erweiterungen hinzufügen. Hier sind einige Dinge, die Sie tun können.

* Mit vorhandenen Start-Kacheln und Schaltflächen der Taskleiste auf Ihre Desktop-Brücke-App weisen.
* Ihre verpackte App einer Gruppe von Dateitypen zuordnen.
* Einstellen, dass Ihre Desktop-Brücke-App bestimmte Arten von Dateien standardmäßig öffnet.

Eine vollständige Liste der Erweiterungen und die Richtlinien für deren Verwendung finden Sie unter [Übergang für Ihre Benutzer zu Ihrer App](desktop-to-uwp-extensions.md#transition-users-to-your-app).

Erwägen Sie außerdem das Hinzufügen von Code zu Ihrer Desktop-Brücke-App, der diese Aufgaben erledigt:

* Migriert Benutzerdaten, die Ihrer Desktop-App zugeordnet sind, zu den entsprechenden Ordnerspeicherorten Ihrer Desktop-Brücke App.
* Gibt Benutzern die Möglichkeit, die Desktop-Version Ihrer App zu deinstallieren.

Erfahren wir mehr über diese einzelnen Aufgaben. Wir beginnen mit der Migration von Benutzerdaten.

### <a name="migrate-user-data"></a>Migrieren von Benutzerdaten

Wenn Sie Code hinzufügen, durch den Benutzerdaten migriert werden, empfiehlt es sich, diesen Code nur dann auszuführen, wenn die App das erste Mal gestartet wird. Bevor Sie die Benutzerdaten migrieren, zeigen Sie dem Benutzer ein Dialogfeld an, das erläutert, was passiert, warum es empfohlen wird und was mit den vorhandenen Daten geschehen wird.

Hier ist ein Beispiel, wie Sie dies in einer NET-basierten Desktop-Brücke-App erreichen können.

```csharp
private void MigrateUserData()
{
    String sourceDir = Environment.GetFolderPath
        (Environment.SpecialFolder.ApplicationData) + "\\AppName";

    if (sourceDir != null)
    {
        String migrateMessage =
            "Would you like to migrate your data from the previous version of this app?";

        DialogResult migrateResult = MessageBox.Show
            (migrateMessage, "Data Migration", MessageBoxButtons.YesNo);

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

### <a name="uninstall-the-desktop-version-of-your-app"></a>Deinstallieren Sie die Desktop-Version Ihrer App

Die Desktop-App des Benutzers sollte nicht deinstalliert werden, ohne nach der Berechtigung zu fragen. Zeigen Sie ein Dialogfeld an, das den Benutzer nach dieser Berechtigung fragt. Benutzer möchten gegebenenfalls die Desktop-Version Ihrer App nicht deinstallieren. In diesem Fall müssen Sie entscheiden, ob Sie die Nutzung der Desktop-App blockieren oder die parallele Nutzung beider Apps unterstützen wollen.

Hier ist ein Beispiel, wie Sie dies in einer NET-basierten Desktop-Brücke-App erreichen können.

Den vollständigen Kontext dieses Codestücks finden Sie in der **MainWindow.cs** Datei des Beispiels [WPF-Bildanzeige Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).

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
        String uninstallMessage = "To have the best experience, consider uninstalling the "
            +" previous version of this app. Would you like to do that now?";

        DialogResult uninstallResult = MessageBox.Show
            (uninstallMessage, "Uninstall the previous version", MessageBoxButtons.YesNo);

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

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
