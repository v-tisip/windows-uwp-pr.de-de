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
# <a name="distribute-a-packaged-desktop-app-desktop-bridge"></a><span data-ttu-id="cdf15-104">Verteilen einer verpackten Desktop-App (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="cdf15-104">Distribute a packaged desktop app (Desktop Bridge)</span></span>

<span data-ttu-id="cdf15-105">Veröffentlichen Sie Ihre verpackte Desktop-App auf einem Windows Store oder laden Sie es auf einem oder mehreren Geräten quer.</span><span class="sxs-lookup"><span data-stu-id="cdf15-105">Publish your packaged desktop app to a Windows store or sideload it onto one or more devices.</span></span>  

> [!NOTE]
> <span data-ttu-id="cdf15-106">Haben Sie einen Plan, wie Sie für Benutzer den Übergang auf Ihre verpackte App ermöglichen können?</span><span class="sxs-lookup"><span data-stu-id="cdf15-106">Do you have a plan for how you might transition users to your packaged app?</span></span> <span data-ttu-id="cdf15-107">Schauen Sie sich den Abschnitt [Übergang von Benutzern für Ihre Desktop-Brücke App](#transition-users) dieses Handbuchs an, um eine Vorstellung davon zu bekommen, bevor Sie Ihre App verteilen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-107">Before you distribute your app, see the [Transition users to your desktop bridge app](#transition-users) section of this guide to get some ideas.</span></span>

## <a name="distribute-your-app-by-publishing-it-to-the-windows-store"></a><span data-ttu-id="cdf15-108">Verteilen Sie Ihre App, indem Sie sie im Windows Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-108">Distribute your app by publishing it to the Windows Store</span></span>

<span data-ttu-id="cdf15-109">Der [Windows Store](https://www.microsoft.com/store/apps) ist eine bequeme Möglichkeit für Kunden, Ihre App zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-109">The [Windows Store](https://www.microsoft.com/store/apps) is a convenient way for customers to get your app.</span></span>

<div style="float: left; padding: 10px">
    ![Symbol „Store“](images/desktop-to-uwp/store.png)
</div>
<span data-ttu-id="cdf15-111">Veröffentlichen Sie Ihre App auf diesen Store, um die größtmögliche Zielgruppe zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-111">Publish your app to that store to reach the broadest audience.</span></span> <span data-ttu-id="cdf15-112">Darüber hinaus können Unternehmenskunden Ihre App erwerben und sie intern in ihren Organisationen durch den [Windows Store für Unternehmen](https://www.microsoft.com/business-store) verteilen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-112">Also, Also, organizational customers can acquire your app to distribute internally to their organizations through the [Windows Store for Business](https://www.microsoft.com/business-store).</span></span>

<span data-ttu-id="cdf15-113">Wenn Sie Ihre App auf dem Windows Store veröffentlichen möchten und Sie uns noch nicht kontaktiert haben, füllen Sie [dieses Formular](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge) aus, und Microsoft wird sich bei Ihnen melden, um die Aufnahme zu starten.</span><span class="sxs-lookup"><span data-stu-id="cdf15-113">If you plan to publish to the Windows Store, and you haven't reached out to us yet, please fill out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge), and Microsoft will contact you to start the onboarding process.</span></span>

<span data-ttu-id="cdf15-114">Sie müssen Ihre App nicht signieren, bevor Sie sie an den Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="cdf15-114">You don't have to sign your app before you submit it to the store.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="cdf15-115">Wenn Sie Ihre App im Windows Store veröffentlichen möchten, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Dies ist eine Anforderung für den Store.</span><span class="sxs-lookup"><span data-stu-id="cdf15-115">If you plan to publish your app to the Windows Store, make sure that your app operates correctly on devices that run Windows 10 S. This is a store requirement.</span></span> <span data-ttu-id="cdf15-116">Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).</span><span class="sxs-lookup"><span data-stu-id="cdf15-116">See [Test your Windows app for Windows 10  S](desktop-to-uwp-test-windows-s.md).</span></span>

## <a name="distribute-your-app-without-placing-it-onto-the-windows-store"></a><span data-ttu-id="cdf15-117">Verteilen Sie Ihre App, ohne sie auf dem Windows Store zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-117">Distribute your app without placing it onto the Windows Store</span></span>

<span data-ttu-id="cdf15-118">Wenn Sie Ihre App lieber verteilen, ohne sie auf dem Store zu veröffentlichen, können Sie Apps auf einem oder mehreren Geräten manuell vertreiben.</span><span class="sxs-lookup"><span data-stu-id="cdf15-118">If you'd rather distribute your app without using the store, you can manually distribute apps to one or more devices.</span></span>

<span data-ttu-id="cdf15-119">Dies eignet sich ggf., wenn Sie eine bessere Kontrolle über die Verteilung haben oder sich nicht mit dem Windows Store-Zertifizierungsprozess auseinandersetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="cdf15-119">This might make sense if you want greater control over the distribution experience or you don't want to get involved with the Windows Store certification process.</span></span>

<span data-ttu-id="cdf15-120">Um Ihre App auf anderen Geräten zu verteilen, ohne sie im Store zu veröffentlichen, müssen Sie ein Zertifikat einholen, Ihre App anhand dieses Zertifikats signieren und sie anschließend auf diese Geräte querladen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-120">To distribute your app to other devices without placing it onto the store, you have to obtain a certificate, sign your app by using that certificate, and then sideload your app onto those devices.</span></span>

<span data-ttu-id="cdf15-121">Sie können [ein Zertifikat erstellen](../packaging/create-certificate-package-signing.md) oder eines von einem beliebten Anbieter wie z.B. [Verisign](https://www.verisign.com/) erhalten.</span><span class="sxs-lookup"><span data-stu-id="cdf15-121">You can [create a certificate](../packaging/create-certificate-package-signing.md) or obtain one from a popular vendor such as [Verisign](https://www.verisign.com/).</span></span>

<span data-ttu-id="cdf15-122">Wenn Sie Ihre App auf Geräten mit Windows 10 S verteilen möchten, muss Ihre App vom Windows Store signiert werden. Daher müssen Sie den Prozess für die Store-Übermittlung durchlaufen, bevor Sie Ihre App auf diesen Geräte vertreiben können.</span><span class="sxs-lookup"><span data-stu-id="cdf15-122">If you plan to distribute your app onto devices that run Windows 10 S, your app has to be signed by the Windows Store so you'll have to go through the Store submission process before you can distribute your app onto those devices.</span></span>

<span data-ttu-id="cdf15-123">Wenn Sie ein Zertifikat zu erstellen, müssen Sie es im Zertifikatspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** von jedem Gerät installieren, auf dem Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cdf15-123">If you create a certificate, you have to install it into the **Trusted Root** or **Trusted People** certificate store on each device that runs your app.</span></span> <span data-ttu-id="cdf15-124">Wenn Sie ein Zertifikat von einem beliebten Anbieter erhalten, müssen Sie auf anderen Systemen neben Ihrer App nichts weiteres installieren.</span><span class="sxs-lookup"><span data-stu-id="cdf15-124">If you get a certificate from a popular vendor, you won't have to install anything onto other systems besides your app.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="cdf15-125">Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.</span><span class="sxs-lookup"><span data-stu-id="cdf15-125">Make sure that the publisher name on your certificate matches the publisher name of your app.</span></span>

<span data-ttu-id="cdf15-126">Weitere Informationen zum Signieren Ihrer App anhand des Zertifikats finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).</span><span class="sxs-lookup"><span data-stu-id="cdf15-126">To sign your app by using a certificate, see [Sign an app package using SignTool](../packaging/sign-app-package-using-signtool.md).</span></span>

<span data-ttu-id="cdf15-127">Weitere Informationen zum Querladen Ihrer App auf anderen Geräten finden Sie unter [querladen von Branchen-Apps in Windows10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).</span><span class="sxs-lookup"><span data-stu-id="cdf15-127">To sideload your app onto other devices, see [Sideload LOB apps in Windows 10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).</span></span>

**<span data-ttu-id="cdf15-128">Videos</span><span class="sxs-lookup"><span data-stu-id="cdf15-128">Videos</span></span>**

|<span data-ttu-id="cdf15-129">Veröffentlichen Ihrer App im WindowsStore</span><span class="sxs-lookup"><span data-stu-id="cdf15-129">Publish your app into the Windows Store</span></span> |<span data-ttu-id="cdf15-130">Verteilen Sie eine Unternehmens-App</span><span class="sxs-lookup"><span data-stu-id="cdf15-130">Distribute an enterprise app</span></span>  |
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Windows-Store-Publication-3cWyG5WhD_5506218965"      width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Distribution-for-Enterprise-Apps-XJ5Hd5WhD_1106218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<span id="transition-users" />
## <a name="transition-users-to-your-desktop-bridge-app"></a><span data-ttu-id="cdf15-131">Den Übergang für Benutzer auf Ihre App für die Desktop-Brücke bereitstellen</span><span class="sxs-lookup"><span data-stu-id="cdf15-131">Transition users to your desktop bridge app</span></span>

<span data-ttu-id="cdf15-132">Bevor Sie Ihre App verteilen, sollten Sie, Ihr Paketmanifest, erhalten mit der Brücke für Desktop-App besteht darin, Benutzern zu helfen einige Erweiterungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-132">Before you distribute your app, consider adding a few extensions to your package manifest to help users get into the habit of using your desktop bridge app.</span></span> <span data-ttu-id="cdf15-133">Hier sind einige Dinge, die Sie tun können.</span><span class="sxs-lookup"><span data-stu-id="cdf15-133">Here's a few things you can do.</span></span>

* <span data-ttu-id="cdf15-134">Mit vorhandenen Start-Kacheln und Schaltflächen der Taskleiste auf Ihre Desktop-Brücke-App weisen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-134">Point existing Start tiles and taskbar buttons to your desktop bridge app.</span></span>
* <span data-ttu-id="cdf15-135">Ihre verpackte App einer Gruppe von Dateitypen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-135">Associate your packaged app with a set of file types.</span></span>
* <span data-ttu-id="cdf15-136">Einstellen, dass Ihre Desktop-Brücke-App bestimmte Arten von Dateien standardmäßig öffnet.</span><span class="sxs-lookup"><span data-stu-id="cdf15-136">Make your desktop bridge app open certain types of files by default.</span></span>

<span data-ttu-id="cdf15-137">Eine vollständige Liste der Erweiterungen und die Richtlinien für deren Verwendung finden Sie unter [Übergang für Ihre Benutzer zu Ihrer App](desktop-to-uwp-extensions.md#transition-users-to-your-app).</span><span class="sxs-lookup"><span data-stu-id="cdf15-137">For the complete list of extensions and the guidance for how to use them, see [Transition users to your app](desktop-to-uwp-extensions.md#transition-users-to-your-app).</span></span>

<span data-ttu-id="cdf15-138">Erwägen Sie außerdem das Hinzufügen von Code zu Ihrer Desktop-Brücke-App, der diese Aufgaben erledigt:</span><span class="sxs-lookup"><span data-stu-id="cdf15-138">Also, consider adding code to your desktop bridge app that accomplishes these tasks:</span></span>

* <span data-ttu-id="cdf15-139">Migriert Benutzerdaten, die Ihrer Desktop-App zugeordnet sind, zu den entsprechenden Ordnerspeicherorten Ihrer Desktop-Brücke App.</span><span class="sxs-lookup"><span data-stu-id="cdf15-139">Migrates user data associated with your desktop app to the appropriate folder locations of your desktop bridge app.</span></span>
* <span data-ttu-id="cdf15-140">Gibt Benutzern die Möglichkeit, die Desktop-Version Ihrer App zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="cdf15-140">Gives users the option to uninstall the desktop version of your app.</span></span>

<span data-ttu-id="cdf15-141">Erfahren wir mehr über diese einzelnen Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="cdf15-141">Let's talk about each one of these tasks.</span></span> <span data-ttu-id="cdf15-142">Wir beginnen mit der Migration von Benutzerdaten.</span><span class="sxs-lookup"><span data-stu-id="cdf15-142">We'll start with user data migration.</span></span>

### <a name="migrate-user-data"></a><span data-ttu-id="cdf15-143">Migrieren von Benutzerdaten</span><span class="sxs-lookup"><span data-stu-id="cdf15-143">Migrate user data</span></span>

<span data-ttu-id="cdf15-144">Wenn Sie Code hinzufügen, durch den Benutzerdaten migriert werden, empfiehlt es sich, diesen Code nur dann auszuführen, wenn die App das erste Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="cdf15-144">If you're going to add code that migrates user data, it's best to run that code only when the app is first started.</span></span> <span data-ttu-id="cdf15-145">Bevor Sie die Benutzerdaten migrieren, zeigen Sie dem Benutzer ein Dialogfeld an, das erläutert, was passiert, warum es empfohlen wird und was mit den vorhandenen Daten geschehen wird.</span><span class="sxs-lookup"><span data-stu-id="cdf15-145">Before you migrate the users data, display a dialog box to the user that explains what is happening, why it is recommended, and what's going to happen to their existing data.</span></span>

<span data-ttu-id="cdf15-146">Hier ist ein Beispiel, wie Sie dies in einer NET-basierten Desktop-Brücke-App erreichen können.</span><span class="sxs-lookup"><span data-stu-id="cdf15-146">Here's an example of how you could do this in a .NET-based desktop bridge app.</span></span>

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

### <a name="uninstall-the-desktop-version-of-your-app"></a><span data-ttu-id="cdf15-147">Deinstallieren Sie die Desktop-Version Ihrer App</span><span class="sxs-lookup"><span data-stu-id="cdf15-147">Uninstall the desktop version of your app</span></span>

<span data-ttu-id="cdf15-148">Die Desktop-App des Benutzers sollte nicht deinstalliert werden, ohne nach der Berechtigung zu fragen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-148">It is better not to uninstall the users desktop app without first asking them for permission.</span></span> <span data-ttu-id="cdf15-149">Zeigen Sie ein Dialogfeld an, das den Benutzer nach dieser Berechtigung fragt.</span><span class="sxs-lookup"><span data-stu-id="cdf15-149">Display a dialog box that asks the user for that permission.</span></span> <span data-ttu-id="cdf15-150">Benutzer möchten gegebenenfalls die Desktop-Version Ihrer App nicht deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="cdf15-150">Users might decide not to uninstall the desktop version of your app.</span></span> <span data-ttu-id="cdf15-151">In diesem Fall müssen Sie entscheiden, ob Sie die Nutzung der Desktop-App blockieren oder die parallele Nutzung beider Apps unterstützen wollen.</span><span class="sxs-lookup"><span data-stu-id="cdf15-151">If that happens, you'll have to decide whether you want to block usage of the desktop app or support the side-by-side use of both apps.</span></span>

<span data-ttu-id="cdf15-152">Hier ist ein Beispiel, wie Sie dies in einer NET-basierten Desktop-Brücke-App erreichen können.</span><span class="sxs-lookup"><span data-stu-id="cdf15-152">Here's an example of how you could do this in a .NET-based desktop bridge app.</span></span>

<span data-ttu-id="cdf15-153">Den vollständigen Kontext dieses Codestücks finden Sie in der **MainWindow.cs** Datei des Beispiels [WPF-Bildanzeige Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).</span><span class="sxs-lookup"><span data-stu-id="cdf15-153">To view the complete context of this snippet, see the **MainWindow.cs** file of this sample [WPF picture viewer with transition/migration/uninstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).</span></span>

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

### <a name="video"></a><span data-ttu-id="cdf15-154">Video</span><span class="sxs-lookup"><span data-stu-id="cdf15-154">Video</span></span>

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Transition-Taskbar-Pins-Start-Tiles-File-Type-Associations-and-Protocol-Handlers-MD5mv5WhD_2406218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a><span data-ttu-id="cdf15-155">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="cdf15-155">Next steps</span></span>

**<span data-ttu-id="cdf15-156">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="cdf15-156">Find answers to specific questions</span></span>**

<span data-ttu-id="cdf15-157">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="cdf15-157">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="cdf15-158">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="cdf15-158">Give feedback about this article</span></span>**

<span data-ttu-id="cdf15-159">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="cdf15-159">Use the comments section below.</span></span>
