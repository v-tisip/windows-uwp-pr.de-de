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
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5476348"
---
# <a name="distribute-a-packaged-desktop-application"></a><span data-ttu-id="d1c99-103">Verteilen einer verpackten desktop-Anwendungs</span><span class="sxs-lookup"><span data-stu-id="d1c99-103">Distribute a packaged desktop application</span></span>

<span data-ttu-id="d1c99-104">Veröffentlichen Sie Ihre verpackte desktop-Anwendung auf einem Windows Store oder querladen es auf einem oder mehreren Geräten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-104">Publish your packaged desktop application to a Windows store or sideload it onto one or more devices.</span></span>  

> [!NOTE]
> <span data-ttu-id="d1c99-105">Haben Sie einen Plan für wie Benutzer auf Ihre verpackte Anwendung übertragen werden kann?</span><span class="sxs-lookup"><span data-stu-id="d1c99-105">Do you have a plan for how you might transition users to your packaged application?</span></span> <span data-ttu-id="d1c99-106">Schauen Sie sich den Abschnitt [Umstellung von Benutzern auf Ihre verpackte App](#transition-users) dieses Handbuchs an, um eine Vorstellung davon zu bekommen, bevor Sie Ihre App verteilen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-106">Before you distribute your app, see the [Transition users to your packaged app](#transition-users) section of this guide to get some ideas.</span></span>

## <a name="distribute-your-application-by-publishing-it-to-the-microsoft-store"></a><span data-ttu-id="d1c99-107">Verteilen Sie Ihre Anwendung, indem sie an den Microsoft Store veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="d1c99-107">Distribute your application by publishing it to the Microsoft Store</span></span>

<span data-ttu-id="d1c99-108">Der [Microsoft Store](https://www.microsoft.com/store/apps) ist eine bequeme Möglichkeit für Kunden, Ihre App zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-108">The [Microsoft Store](https://www.microsoft.com/store/apps) is a convenient way for customers to get your app.</span></span>

<span data-ttu-id="d1c99-109">Veröffentlichen Sie die Anwendung in diesem Store, um die größtmögliche Zielgruppe zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-109">Publish your application to that store to reach the broadest audience.</span></span> <span data-ttu-id="d1c99-110">Darüber hinaus können Unternehmenskunden Ihre Anwendung intern in ihren Organisationen über den [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store)verteilen erwerben.</span><span class="sxs-lookup"><span data-stu-id="d1c99-110">Also, organizational customers can acquire your application to distribute internally to their organizations through the [Microsoft Store for Business](https://www.microsoft.com/business-store).</span></span>

<span data-ttu-id="d1c99-111">Wenn Sie eine Veröffentlichung im Microsoft Store planen, werden Ihnen als Teil des Übermittlungsprozesses einige zusätzliche Fragen gestellt.</span><span class="sxs-lookup"><span data-stu-id="d1c99-111">If you plan to publish to the Microsoft Store, you'll be asked a few extra questions as part of the submission process.</span></span> <span data-ttu-id="d1c99-112">Der Grund dafür ist, dass Ihr Paketmanifest eine eingeschränkte Funktion mit dem Namen **runFullTrust** deklariert und wir die Verwendung dieser Funktion durch Ihre Anwendung genehmigen müssen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-112">That's because your package manifest declares a restricted capability named **runFullTrust**, and we need to approve your application's use of that capability.</span></span> <span data-ttu-id="d1c99-113">Weitere Informationen zu dieser Anforderung finden Sie hier: [Eingeschränkte Funktionen](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#restricted-capabilities).</span><span class="sxs-lookup"><span data-stu-id="d1c99-113">You can read more about this requirement here: [Restricted capabilities](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations#restricted-capabilities).</span></span>

<span data-ttu-id="d1c99-114">Sie müssen Ihre Anwendung zu signieren, bevor Sie sie an den Store übermitteln.</span><span class="sxs-lookup"><span data-stu-id="d1c99-114">You don't have to sign your application before you submit it to the store.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d1c99-115">Wenn Sie Ihre Anwendung an den Microsoft Store veröffentlichen möchten, stellen Sie sicher, dass Ihre Anwendung korrekt auf Geräten unter Windows 10 s ausgeführt Dies ist eine Anforderung des Stores.</span><span class="sxs-lookup"><span data-stu-id="d1c99-115">If you plan to publish your application to the Microsoft Store, make sure that your application operates correctly on devices that run Windows 10 S. This is a store requirement.</span></span> <span data-ttu-id="d1c99-116">Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](desktop-to-uwp-test-windows-s.md).</span><span class="sxs-lookup"><span data-stu-id="d1c99-116">See [Test your Windows app for Windows 10  S](desktop-to-uwp-test-windows-s.md).</span></span>

<a id="side-load" />

## <a name="distribute-your-application-without-placing-it-onto-the-microsoft-store"></a><span data-ttu-id="d1c99-117">Verteilen Sie Ihrer Anwendung ohne zu auf dem Microsoft Store veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-117">Distribute your application without placing it onto the Microsoft Store</span></span>

<span data-ttu-id="d1c99-118">Wenn Sie ohne Verwendung des Stores anstatt Ihrer Anwendung verteilen möchten, können Sie apps auf einem oder mehreren Geräten manuell verteilen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-118">If you'd rather distribute your application without using the store, you can manually distribute apps to one or more devices.</span></span>

<span data-ttu-id="d1c99-119">Dies eignet sich ggf., wenn Sie eine bessere Kontrolle über die Verteilung haben oder sich nicht mit dem Microsoft Store-Zertifizierungsprozess auseinandersetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-119">This might make sense if you want greater control over the distribution experience or you don't want to get involved with the Microsoft Store certification process.</span></span>

<span data-ttu-id="d1c99-120">Um Ihre Anwendung auf anderen Geräten ohne platzieren Sie diese auf den Store zu verteilen, müssen Sie ein Zertifikat erhalten, Signieren Sie Ihre Anwendung mit das Zertifikat, und klicken Sie dann den querladen Ihrer Anwendung auf diesen Geräten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-120">To distribute your application to other devices without placing it onto the store, you have to obtain a certificate, sign your application by using that certificate, and then sideload your application onto those devices.</span></span>

<span data-ttu-id="d1c99-121">Sie können [ein Zertifikat erstellen](../packaging/create-certificate-package-signing.md) oder eines von einem beliebten Anbieter wie z.B. [Verisign](https://www.verisign.com/) erhalten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-121">You can [create a certificate](../packaging/create-certificate-package-signing.md) or obtain one from a popular vendor such as [Verisign](https://www.verisign.com/).</span></span>

<span data-ttu-id="d1c99-122">Wenn Sie beabsichtigen, Ihre Anwendung auf Geräte mit Windows 10 S verteilen möchten, muss die Anwendung vom Microsoft Store signiert werden, daher müssen Sie die Store-Übermittlung durchlaufen, bevor Sie Ihre Anwendung auf diesen Geräte vertreiben können.</span><span class="sxs-lookup"><span data-stu-id="d1c99-122">If you plan to distribute your application onto devices that run Windows 10 S, your application has to be signed by the Microsoft Store so you'll have to go through the Store submission process before you can distribute your application onto those devices.</span></span>

<span data-ttu-id="d1c99-123">Wenn Sie ein Zertifikat zu erstellen, müssen Sie es im Zertifikatspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** von jedem Gerät installieren, auf dem Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d1c99-123">If you create a certificate, you have to install it into the **Trusted Root** or **Trusted People** certificate store on each device that runs your app.</span></span> <span data-ttu-id="d1c99-124">Wenn Sie ein Zertifikat von einem beliebten Anbieter erhalten, müssen Sie auf anderen Systemen neben Ihrer App nichts weiteres installieren.</span><span class="sxs-lookup"><span data-stu-id="d1c99-124">If you get a certificate from a popular vendor, you won't have to install anything onto other systems besides your app.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="d1c99-125">Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.</span><span class="sxs-lookup"><span data-stu-id="d1c99-125">Make sure that the publisher name on your certificate matches the publisher name of your app.</span></span>

<span data-ttu-id="d1c99-126">Um Ihre Anwendung mit einem Zertifikat signieren, finden Sie in der [Anmeldung eines Anwendungspakets mithilfe von SignTool](../packaging/sign-app-package-using-signtool.md).</span><span class="sxs-lookup"><span data-stu-id="d1c99-126">To sign your application by using a certificate, see [Sign an application package using SignTool](../packaging/sign-app-package-using-signtool.md).</span></span>

<span data-ttu-id="d1c99-127">Querladen Ihrer Anwendung auf anderen Geräten finden Sie unter [Querladen von Branchen-apps in Windows 10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).</span><span class="sxs-lookup"><span data-stu-id="d1c99-127">To sideload your application onto other devices, see [Sideload LOB apps in Windows 10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10).</span></span>

**<span data-ttu-id="d1c99-128">Videos</span><span class="sxs-lookup"><span data-stu-id="d1c99-128">Videos</span></span>**

|<span data-ttu-id="d1c99-129">Veröffentlichen Sie die Anwendung in der Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="d1c99-129">Publish your application into the Microsoft Store</span></span> |<span data-ttu-id="d1c99-130">Verteilen Sie eine Enterprise-Anwendung</span><span class="sxs-lookup"><span data-stu-id="d1c99-130">Distribute an enterprise application</span></span>  |
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Windows-Store-Publication-3cWyG5WhD_5506218965"      width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Distribution-for-Enterprise-Apps-XJ5Hd5WhD_1106218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<a id="transition-users" />

## <a name="transition-users-to-your-packaged-app"></a><span data-ttu-id="d1c99-131">Umstellung von Benutzern auf Ihre verpackte App</span><span class="sxs-lookup"><span data-stu-id="d1c99-131">Transition users to your packaged app</span></span>

<span data-ttu-id="d1c99-132">Bevor Sie Ihre App verteilen, sollten Sie das Hinzufügen einiger Erweiterungen zu Ihrem Paketmanifest in Betracht ziehen, damit sich Benutzer daran gewöhnen, Ihre verpackte App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1c99-132">Before you distribute your app, consider adding a few extensions to your package manifest to help users get into the habit of using your packaged app.</span></span> <span data-ttu-id="d1c99-133">Hier sind einige Dinge, die Sie tun können.</span><span class="sxs-lookup"><span data-stu-id="d1c99-133">Here's a few things you can do.</span></span>

* <span data-ttu-id="d1c99-134">Verweisen Sie mit vorhandenen Startkacheln und Taskleistenschaltflächen auf Ihre verpackte App.</span><span class="sxs-lookup"><span data-stu-id="d1c99-134">Point existing Start tiles and taskbar buttons to your packaged app.</span></span>
* <span data-ttu-id="d1c99-135">Ihres Anwendungspakets einer Gruppe von Dateitypen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="d1c99-135">Associate your packaged application with a set of file types.</span></span>
* <span data-ttu-id="d1c99-136">Stellen Sie die verpackte Anwendung, die bestimmte Dateitypen standardmäßig öffnet.</span><span class="sxs-lookup"><span data-stu-id="d1c99-136">Make your packaged application open certain types of files by default.</span></span>

<span data-ttu-id="d1c99-137">Eine vollständige Liste der Erweiterungen und die Richtlinien für deren Verwendung finden Sie unter [Umstellung von Benutzern auf Ihre App](desktop-to-uwp-extensions.md#transition-users-to-your-app).</span><span class="sxs-lookup"><span data-stu-id="d1c99-137">For the complete list of extensions and the guidance for how to use them, see [Transition users to your app](desktop-to-uwp-extensions.md#transition-users-to-your-app).</span></span>

<span data-ttu-id="d1c99-138">Erwägen Sie außerdem das Hinzufügen von Code zu Ihrer verpackten Anwendung, die diese Aufgaben erledigt:</span><span class="sxs-lookup"><span data-stu-id="d1c99-138">Also, consider adding code to your packaged application that accomplishes these tasks:</span></span>

* <span data-ttu-id="d1c99-139">Migrieren von Benutzerdaten, die Ihre desktop-Anwendung auf den entsprechenden Ordnerspeicherorten Ihrer verpackten App zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d1c99-139">Migrates user data associated with your desktop application to the appropriate folder locations of your packaged app.</span></span>
* <span data-ttu-id="d1c99-140">Bereitstellung der Option für Benutzer, die Desktopversion Ihrer App zu deinstallieren</span><span class="sxs-lookup"><span data-stu-id="d1c99-140">Gives users the option to uninstall the desktop version of your app.</span></span>

<span data-ttu-id="d1c99-141">Erfahren wir mehr über diese einzelnen Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="d1c99-141">Let's talk about each one of these tasks.</span></span> <span data-ttu-id="d1c99-142">Wir beginnen mit der Migration von Benutzerdaten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-142">We'll start with user data migration.</span></span>

### <a name="migrate-user-data"></a><span data-ttu-id="d1c99-143">Migrieren von Benutzerdaten</span><span class="sxs-lookup"><span data-stu-id="d1c99-143">Migrate user data</span></span>

<span data-ttu-id="d1c99-144">Wenn Sie vorhaben, Code hinzufügen, der migriert Benutzerdaten, empfiehlt es sich, diesen Code nur ausgeführt, wenn die Anwendung das erste Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d1c99-144">If you're going to add code that migrates user data, it's best to run that code only when the application is first started.</span></span> <span data-ttu-id="d1c99-145">Bevor Sie die Benutzerdaten migrieren, zeigen Sie dem Benutzer ein Dialogfeld an, das erläutert, was passiert, warum es empfohlen wird und was mit den vorhandenen Daten geschehen wird.</span><span class="sxs-lookup"><span data-stu-id="d1c99-145">Before you migrate the users data, display a dialog box to the user that explains what is happening, why it is recommended, and what's going to happen to their existing data.</span></span>

<span data-ttu-id="d1c99-146">Hier ist ein Beispiel, wie Sie dies in einer NET-basierten verpackten App erreichen können.</span><span class="sxs-lookup"><span data-stu-id="d1c99-146">Here's an example of how you could do this in a .NET-based packaged app.</span></span>

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

### <a name="uninstall-the-desktop-version-of-your-app"></a><span data-ttu-id="d1c99-147">Deinstallieren Sie die Desktopversion Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d1c99-147">Uninstall the desktop version of your app</span></span>

<span data-ttu-id="d1c99-148">Es ist besser, die Benutzer-desktop-Anwendung ohne diese Berechtigung nicht deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="d1c99-148">It is better not to uninstall the users desktop application without first asking them for permission.</span></span> <span data-ttu-id="d1c99-149">Zeigen Sie ein Dialogfeld an, das den Benutzer nach dieser Berechtigung fragt.</span><span class="sxs-lookup"><span data-stu-id="d1c99-149">Display a dialog box that asks the user for that permission.</span></span> <span data-ttu-id="d1c99-150">Benutzer möchten gegebenenfalls die Desktop-Version Ihrer App nicht deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="d1c99-150">Users might decide not to uninstall the desktop version of your app.</span></span> <span data-ttu-id="d1c99-151">In diesem Fall müssen Sie entscheiden, ob Sie die Nutzung der desktop-Anwendung blockieren oder die Side-by-Side-Nutzung beider Apps unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="d1c99-151">If that happens, you'll have to decide whether you want to block usage of the desktop application or support the side-by-side use of both apps.</span></span>

<span data-ttu-id="d1c99-152">Hier ist ein Beispiel, wie Sie dies in einer NET-basierten verpackten App erreichen können.</span><span class="sxs-lookup"><span data-stu-id="d1c99-152">Here's an example of how you could do this in a .NET-based packaged app.</span></span>

<span data-ttu-id="d1c99-153">Den vollständigen Kontext dieses Codeausschnitts finden Sie in der **MainWindow.cs**-Datei des Beispiels [WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).</span><span class="sxs-lookup"><span data-stu-id="d1c99-153">To view the complete context of this snippet, see the **MainWindow.cs** file of this sample [WPF picture viewer with transition/migration/uninstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition).</span></span>

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

### <a name="video"></a><span data-ttu-id="d1c99-154">Video</span><span class="sxs-lookup"><span data-stu-id="d1c99-154">Video</span></span>

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Transition-Taskbar-Pins-Start-Tiles-File-Type-Associations-and-Protocol-Handlers-MD5mv5WhD_2406218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a><span data-ttu-id="d1c99-155">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d1c99-155">Next steps</span></span>

**<span data-ttu-id="d1c99-156">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="d1c99-156">Find answers to your questions</span></span>**

<span data-ttu-id="d1c99-157">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="d1c99-157">Have questions?</span></span> <span data-ttu-id="d1c99-158">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="d1c99-158">Ask us on Stack Overflow.</span></span> <span data-ttu-id="d1c99-159">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="d1c99-159">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="d1c99-160">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="d1c99-160">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

<span data-ttu-id="d1c99-161">Wenn beim Veröffentlichen Ihrer Anwendung an den Store Probleme auftreten, enthält dieser [Blogbeitrag](https://blogs.msdn.microsoft.com/appconsult/2017/09/25/preparing-a-desktop-bridge-application-for-the-store-submission/) einige hilfreiche Tipps.</span><span class="sxs-lookup"><span data-stu-id="d1c99-161">If you encounter issues publishing your application to the Store, this [blog post](https://blogs.msdn.microsoft.com/appconsult/2017/09/25/preparing-a-desktop-bridge-application-for-the-store-submission/) contains some useful tips.</span></span>

**<span data-ttu-id="d1c99-162">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="d1c99-162">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="d1c99-163">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="d1c99-163">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
