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
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4358924"
---
# <a name="run-debug-and-test-a-packaged-desktop-application"></a><span data-ttu-id="fbf39-103">Führen Sie aus, Debuggen Sie und Testen Sie eine verpackte desktop-Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbf39-103">Run, debug, and test a packaged desktop application</span></span>

<span data-ttu-id="fbf39-104">Führen Sie Ihre verpackte Anwendung, und sehen Sie, wie sie aussieht, ohne zu signieren.</span><span class="sxs-lookup"><span data-stu-id="fbf39-104">Run your packaged application and see how it looks without having to sign it.</span></span> <span data-ttu-id="fbf39-105">Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-105">Then, set breakpoints and step through code.</span></span> <span data-ttu-id="fbf39-106">Wenn Sie bereit sind, Ihre Anwendung in einer produktiven Umgebung testen, Signieren Sie Ihre Anwendung, und installieren Sie es dann.</span><span class="sxs-lookup"><span data-stu-id="fbf39-106">When you're ready to test your application in a production environment, sign your application and then install it.</span></span> <span data-ttu-id="fbf39-107">In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-107">This topic shows you how to do each of these things.</span></span>

<a id="run-app" />

## <a name="run-your-application"></a><span data-ttu-id="fbf39-108">Führen Sie Ihre Anwendung</span><span class="sxs-lookup"><span data-stu-id="fbf39-108">Run your application</span></span>

<span data-ttu-id="fbf39-109">Sie können Ihre Anwendung zu testen, lokal ohne Erwerb eines Zertifikats und signieren Sie es ausführen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-109">You can run your application to test it out locally without having to obtain a certificate and sign it.</span></span> <span data-ttu-id="fbf39-110">Wie Sie die Anwendung ausführen, hängt tool verwendet, um das Paket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-110">How you run the application depends on what tool you used to create the package.</span></span>

### <a name="you-created-the-package-by-using-visual-studio"></a><span data-ttu-id="fbf39-111">Erstellen des Pakets mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fbf39-111">You created the package by using Visual Studio</span></span>

<span data-ttu-id="fbf39-112">Legen Sie das Paketerstellungsprojekt als Startprojekt fest, und drücken Sie anschließend Strg+F5, um Ihre App zu starten.</span><span class="sxs-lookup"><span data-stu-id="fbf39-112">Set the packaging project as the startup project, and then press CTRL+F5 to start your app.</span></span>

### <a name="you-created-the-package-manually-or-by-using-the-desktop-app-converter"></a><span data-ttu-id="fbf39-113">Erstellen des Pakets manuell oder mithilfe des Desktop App Converter</span><span class="sxs-lookup"><span data-stu-id="fbf39-113">You created the package manually or by using the Desktop App Converter</span></span>

<span data-ttu-id="fbf39-114">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie dieses Cmdlet aus dem Unterordner **PackageFiles** Ihres Ausgabeordners aus:</span><span class="sxs-lookup"><span data-stu-id="fbf39-114">Open a Windows PowerShell command prompt, and from the **PackageFiles** subfolder of your output folder, run this cmdlet:</span></span>

```
Add-AppxPackage –Register AppxManifest.xml
```
<span data-ttu-id="fbf39-115">Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-115">To start your app, find it in the Windows Start menu.</span></span>

![Verpackte Anwendung im Menü "Start"](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> <span data-ttu-id="fbf39-117">Eine Anwendung immer als interaktiver Benutzer ausgeführt wird, und jedes Laufwerk durch die Installation Ihres Anwendungspakets unter muss auf NTFS-Format formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="fbf39-117">A packaged application always runs as an interactive user, and any drive that you install your packaged application on to must be formatted to NTFS format.</span></span>

## <a name="debug-your-app"></a><span data-ttu-id="fbf39-118">Debuggen Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="fbf39-118">Debug your app</span></span>

<span data-ttu-id="fbf39-119">Wie Sie die Anwendung debuggen, hängt von tool verwendet, um das Paket zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-119">How you debug the application depends on what tool you used to create the package.</span></span>

<span data-ttu-id="fbf39-120">Wenn Sie Ihr Paket mithilfe des in Version 15.4 von Visual Studio 2017 verfügbaren [neuen Paketerstellungsprojekts](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) erstellt haben, legen Sie das Paketerstellungsprojekt als Startprojekt fest und drücken Sie F5, um Ihre App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-120">If you created your package by using the [new packaging project](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) available in the 15.4 release of Visual Studio 2017, Just set the packaging project as the startup project, and then press F5 to debug your app.</span></span>

<span data-ttu-id="fbf39-121">Wenn Sie Ihr Paket mit einem anderen Tool erstellt haben, gehen Sie folgendermaßen vor.</span><span class="sxs-lookup"><span data-stu-id="fbf39-121">If you created your package by using any other tool, follow these steps.</span></span>

1. <span data-ttu-id="fbf39-122">Stellen Sie sicher, dass Sie die verpackte Anwendung mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fbf39-122">Make sure that you start your packaged application at least one time so that it's installed on your local machine.</span></span>

   <span data-ttu-id="fbf39-123">Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.</span><span class="sxs-lookup"><span data-stu-id="fbf39-123">See the [Run your app](#run-app) section above.</span></span>

2. <span data-ttu-id="fbf39-124">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fbf39-124">Start Visual Studio.</span></span>

   <span data-ttu-id="fbf39-125">Wenn Sie die Anwendung mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio mithilfe der Option " **als Administrator ausführen** ".</span><span class="sxs-lookup"><span data-stu-id="fbf39-125">If you want to debug your application with elevated permissions, start Visual Studio by using the **Run as Administrator** option.</span></span>

3. <span data-ttu-id="fbf39-126">Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.</span><span class="sxs-lookup"><span data-stu-id="fbf39-126">In Visual Studio, choose **Debug**->**Other Debug Targets**->**Debug Installed App Package**.</span></span>

4. <span data-ttu-id="fbf39-127">In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="fbf39-127">In the **Installed App Packages** list, select your app package, and then choose the **Attach** button.</span></span>

#### <a name="modify-your-application-in-between-debug-sessions"></a><span data-ttu-id="fbf39-128">Ändern Sie Ihre Anwendung zwischen Debugsitzungen</span><span class="sxs-lookup"><span data-stu-id="fbf39-128">Modify your application in between debug sessions</span></span>

<span data-ttu-id="fbf39-129">Wenn Sie Ihre Änderungen an Ihrer Anwendung zum Beheben von Fehlern, wechseln Sie sie mithilfe des MakeAppx-Tools.</span><span class="sxs-lookup"><span data-stu-id="fbf39-129">If you make your changes to your application to fix bugs, repackage it by using the MakeAppx tool.</span></span> <span data-ttu-id="fbf39-130">Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).</span><span class="sxs-lookup"><span data-stu-id="fbf39-130">See [Run the MakeAppx tool](desktop-to-uwp-manual-conversion.md#make-appx).</span></span>

### <a name="debug-the-entire-application-lifecycle"></a><span data-ttu-id="fbf39-131">Debuggen des gesamten Anwendungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fbf39-131">Debug the entire application lifecycle</span></span>

<span data-ttu-id="fbf39-132">In einigen Fällen sollten Sie eine differenziertere Steuerung des debugging-Vorgangs, einschließlich der Möglichkeit zum Debuggen Ihrer Anwendung, bevor er beginnt.</span><span class="sxs-lookup"><span data-stu-id="fbf39-132">In some cases, you might want finer-grained control over the debugging process, including the ability to debug your application before it starts.</span></span>

<span data-ttu-id="fbf39-133">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) können Sie die vollständige Kontrolle über den Anwendungslebenszyklus, einschließlich anhalten, fortsetzen und beenden erhalten.</span><span class="sxs-lookup"><span data-stu-id="fbf39-133">You can use [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) to get full control over application lifecycle including suspending, resuming, and termination.</span></span>

<span data-ttu-id="fbf39-134">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="fbf39-134">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) is included with the Windows SDK.</span></span>

## <a name="test-your-app"></a><span data-ttu-id="fbf39-135">Testen der App</span><span class="sxs-lookup"><span data-stu-id="fbf39-135">Test your app</span></span>

<span data-ttu-id="fbf39-136">Zum Testen Ihrer Anwendung in einer realistischen, wie Sie für die Verteilung vorbereiten, empfiehlt es sich, Signieren Sie Ihre Anwendung, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="fbf39-136">To test your application in a realistic setting as you prepare for distribution, it's best to sign your application and then install it.</span></span>

### <a name="test-an-application-that-you-packaged-by-using-visual-studio"></a><span data-ttu-id="fbf39-137">Testen Sie eine Anwendung, die Sie mithilfe von Visual Studio verpackt</span><span class="sxs-lookup"><span data-stu-id="fbf39-137">Test an application that you packaged by using Visual Studio</span></span>

<span data-ttu-id="fbf39-138">Visual Studio signiert Ihre Anwendung mit einem Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="fbf39-138">Visual Studio signs your application by using a test certificate.</span></span> <span data-ttu-id="fbf39-139">Sie finden dieses Zertifikat im Ausgabeordner, den der Assistent **App-Pakete erstellen** generiert.</span><span class="sxs-lookup"><span data-stu-id="fbf39-139">You'll find that certificate in the output folder that the **Create App Packages** wizard generates.</span></span> <span data-ttu-id="fbf39-140">Die Zertifikatsdatei hat die *CER* -Erweiterung, und Sie müssen das Zertifikat im Speicher **Vertrauenswürdige Stammzertifizierungsstellen** auf dem PC installieren, die Sie Ihre Anwendung auf testen möchten.</span><span class="sxs-lookup"><span data-stu-id="fbf39-140">The certificate file has the *.cer* extension and you'll have to install that certificate into the **Trusted Root Certification Authorities** store on the PC that you want to test your application on.</span></span> <span data-ttu-id="fbf39-141">Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span><span class="sxs-lookup"><span data-stu-id="fbf39-141">See [Sideload your package](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span></span>

### <a name="test-an-application-that-you-packaged-by-using-the-desktop-app-converter-dac"></a><span data-ttu-id="fbf39-142">Testen Sie eine Anwendung, die Sie mithilfe der Desktop App Converter (DAC) verpackt</span><span class="sxs-lookup"><span data-stu-id="fbf39-142">Test an application that you packaged by using the Desktop App Converter (DAC)</span></span>

<span data-ttu-id="fbf39-143">Wenn Sie Ihre Anwendung mithilfe der Desktop App Converter Verpacken, können Sie mithilfe der ``sign`` Parameter, um Ihre Anwendung automatisch mit einem generierten Zertifikat zu signieren.</span><span class="sxs-lookup"><span data-stu-id="fbf39-143">If you package your application by using the Desktop App Converter, you can use the ``sign`` parameter to automatically sign your application by using a generated certificate.</span></span> <span data-ttu-id="fbf39-144">Sie müssen das Zertifikat und anschließend die App installieren.</span><span class="sxs-lookup"><span data-stu-id="fbf39-144">You'll have to install that certificate, and then install the app.</span></span> <span data-ttu-id="fbf39-145">Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span><span class="sxs-lookup"><span data-stu-id="fbf39-145">See [Run the packaged app](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span></span>   


### <a name="manually-sign-apps-optional"></a><span data-ttu-id="fbf39-146">Manuelles signieren von Apps (Optional)</span><span class="sxs-lookup"><span data-stu-id="fbf39-146">Manually sign apps (Optional)</span></span>

<span data-ttu-id="fbf39-147">Sie können die Anwendung auch manuell signieren.</span><span class="sxs-lookup"><span data-stu-id="fbf39-147">You can also sign your application manually.</span></span> <span data-ttu-id="fbf39-148">So geht’s</span><span class="sxs-lookup"><span data-stu-id="fbf39-148">Here's how</span></span>

1. <span data-ttu-id="fbf39-149">Erstellen eines Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="fbf39-149">Create a certificate.</span></span> <span data-ttu-id="fbf39-150">Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).</span><span class="sxs-lookup"><span data-stu-id="fbf39-150">See [Create a certificate](../packaging/create-certificate-package-signing.md).</span></span>

2. <span data-ttu-id="fbf39-151">Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="fbf39-151">Install that certificate into the **Trusted Root** or **Trusted People** certificate store on your system.</span></span>

3. <span data-ttu-id="fbf39-152">Signieren Sie Ihre Anwendung anhand des Zertifikats, finden Sie unter [Signieren eines app-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).</span><span class="sxs-lookup"><span data-stu-id="fbf39-152">Sign your application by using that certificate, see [Sign an app package using SignTool](../packaging/sign-app-package-using-signtool.md).</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="fbf39-153">Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.</span><span class="sxs-lookup"><span data-stu-id="fbf39-153">Make sure that the publisher name on your certificate matches the publisher name of your app.</span></span>

    **<span data-ttu-id="fbf39-154">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="fbf39-154">Related sample</span></span>**

    [<span data-ttu-id="fbf39-155">SigningCerts</span><span class="sxs-lookup"><span data-stu-id="fbf39-155">SigningCerts</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-application-for-windows-10-s"></a><span data-ttu-id="fbf39-156">Testen Sie Ihre Anwendung für Windows 10 S</span><span class="sxs-lookup"><span data-stu-id="fbf39-156">Test your application for Windows 10 S</span></span>

<span data-ttu-id="fbf39-157">Bevor Sie Ihre app veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten, auf denen Windows 10 s ausgeführt. Tatsächlich, wenn Sie Ihre Anwendung an den Microsoft Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist.</span><span class="sxs-lookup"><span data-stu-id="fbf39-157">Before you publish your app, make sure that it will operate correctly on devices that run Windows 10 S. In fact, if you plan to publish your application to the Microsoft Store, you must do this because it is a store requirement.</span></span> <span data-ttu-id="fbf39-158">Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert.</span><span class="sxs-lookup"><span data-stu-id="fbf39-158">Apps that don't operate correctly on devices that run Windows 10 S won't be certified.</span></span>

<span data-ttu-id="fbf39-159">[Test der Windows-Anwendung für Windows 10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s)angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbf39-159">See [Test your Windows application for Windows 10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).</span></span>

### <a name="run-another-process-inside-the-full-trust-container"></a><span data-ttu-id="fbf39-160">Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container</span><span class="sxs-lookup"><span data-stu-id="fbf39-160">Run another process inside the full trust container</span></span>

<span data-ttu-id="fbf39-161">Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fbf39-161">You can invoke custom processes inside the container of a specified app package.</span></span> <span data-ttu-id="fbf39-162">Dies kann nützlich sein, um Szenarien zu testen (z.B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten).</span><span class="sxs-lookup"><span data-stu-id="fbf39-162">This can be useful for testing scenarios (for example, if you have a custom test harness and want to test output of the app).</span></span> <span data-ttu-id="fbf39-163">Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```:</span><span class="sxs-lookup"><span data-stu-id="fbf39-163">To do so, use the ```Invoke-CommandInDesktopPackage``` PowerShell cmdlet:</span></span>

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

## <a name="next-steps"></a><span data-ttu-id="fbf39-164">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="fbf39-164">Next steps</span></span>

**<span data-ttu-id="fbf39-165">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="fbf39-165">Find answers to your questions</span></span>**

<span data-ttu-id="fbf39-166">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="fbf39-166">Have questions?</span></span> <span data-ttu-id="fbf39-167">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="fbf39-167">Ask us on Stack Overflow.</span></span> <span data-ttu-id="fbf39-168">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="fbf39-168">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="fbf39-169">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="fbf39-169">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="fbf39-170">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="fbf39-170">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="fbf39-171">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="fbf39-171">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
