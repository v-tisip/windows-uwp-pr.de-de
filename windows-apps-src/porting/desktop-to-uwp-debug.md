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
# <a name="run-debug-and-test-a-packaged-desktop-app-desktop-bridge"></a><span data-ttu-id="f8505-103">Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="f8505-103">Run, debug, and test a packaged desktop app (Desktop Bridge)</span></span>

<span data-ttu-id="f8505-104">Führen Sie Ihre verpackte App aus und prüfen Sie, wie sie aussieht, ohne sie zu signieren.</span><span class="sxs-lookup"><span data-stu-id="f8505-104">Run your packaged app and see how it looks without having to sign it.</span></span> <span data-ttu-id="f8505-105">Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f8505-105">Then, set breakpoints and step through code.</span></span> <span data-ttu-id="f8505-106">Wenn Sie bereit sind, Ihre App in einer Produktionsumgebung zu testen, signieren Sie Ihre App und installieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="f8505-106">When you're ready to test your app in a production environment, sign your app and then install it.</span></span> <span data-ttu-id="f8505-107">In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="f8505-107">This topic shows you how to do each of these things.</span></span>

<a id="run-app" />

## <a name="run-your-app"></a><span data-ttu-id="f8505-108">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="f8505-108">Run your app</span></span>

<span data-ttu-id="f8505-109">Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen.</span><span class="sxs-lookup"><span data-stu-id="f8505-109">You can run your app to test it out locally without having to obtain a certificate and sign it.</span></span> <span data-ttu-id="f8505-110">Wie Sie die App ausführen, hängt von dem Tool ab, das Sie beim Erstellen des Pakets verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="f8505-110">How you run the app depends on what tool you used to create the package.</span></span>

### <a name="you-created-the-package-by-using-visual-studio"></a><span data-ttu-id="f8505-111">Erstellen des Pakets mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f8505-111">You created the package by using Visual Studio</span></span>

<span data-ttu-id="f8505-112">Legen Sie das Paketerstellungsprojekt als Startprojekt fest, und drücken Sie anschließend Strg+F5, um Ihre App zu starten.</span><span class="sxs-lookup"><span data-stu-id="f8505-112">Set the packaging project as the startup project, and then press CTRL+F5 to start your app.</span></span>

### <a name="you-created-the-package-manually-or-by-using-the-desktop-app-converter"></a><span data-ttu-id="f8505-113">Erstellen des Pakets manuell oder mithilfe des Desktop App Converter</span><span class="sxs-lookup"><span data-stu-id="f8505-113">You created the package manually or by using the Desktop App Converter</span></span>

<span data-ttu-id="f8505-114">Öffnen Sie eine Windows PowerShell-Eingabeaufforderung, und führen Sie dieses Cmdlet aus dem Unterordner **PackageFiles** Ihres Ausgabeordners aus:</span><span class="sxs-lookup"><span data-stu-id="f8505-114">Open a Windows PowerShell command prompt, and from the **PackageFiles** subfolder of your output folder, run this cmdlet:</span></span>

```
Add-AppxPackage –Register AppxManifest.xml
```
<span data-ttu-id="f8505-115">Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f8505-115">To start your app, find it in the Windows Start menu.</span></span>

![Verpackte App im Startmenü.](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> <span data-ttu-id="f8505-117">Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="f8505-117">A packaged app always runs as an interactive user, and any drive that you install your packaged app on to must be formatted to NTFS format.</span></span>

## <a name="debug-your-app"></a><span data-ttu-id="f8505-118">Debuggen Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="f8505-118">Debug your app</span></span>

<span data-ttu-id="f8505-119">Wie Sie die App debuggen, hängt von dem Tool ab, das Sie beim Erstellen des Pakets verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="f8505-119">How you debug the app depends on what tool you used to create the package.</span></span>

<span data-ttu-id="f8505-120">Wenn Sie Ihr Paket mithilfe des in Version 15.4 von Visual Studio 2017 verfügbaren [neuen Paketerstellungsprojekts](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) erstellt haben, legen Sie das Paketerstellungsprojekt als Startprojekt fest und drücken Sie F5, um Ihre App zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="f8505-120">If you created your package by using the [new packaging project](desktop-to-uwp-packaging-dot-net.md#new-packaging-project) available in the 15.4 release of Visual Studio 2017, Just set the packaging project as the startup project, and then press F5 to debug your app.</span></span>

<span data-ttu-id="f8505-121">Wenn Sie Ihr Paket mit einem anderen Tool erstellt haben, gehen Sie folgendermaßen vor.</span><span class="sxs-lookup"><span data-stu-id="f8505-121">If you created your package by using any other tool, follow these steps.</span></span>

1. <span data-ttu-id="f8505-122">Stellen Sie sicher, dass Sie Ihr App-Paket mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.</span><span class="sxs-lookup"><span data-stu-id="f8505-122">Make sure that you start your packaged app at least one time so that it's installed on your local machine.</span></span>

   <span data-ttu-id="f8505-123">Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.</span><span class="sxs-lookup"><span data-stu-id="f8505-123">See the [Run your app](#run-app) section above.</span></span>

2. <span data-ttu-id="f8505-124">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8505-124">Start Visual Studio.</span></span>

   <span data-ttu-id="f8505-125">Wenn Sie Ihre App mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio anhand der Option **als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="f8505-125">If you want to debug your app with elevated permissions, start Visual Studio by using the **Run as Administrator** option.</span></span>

3. <span data-ttu-id="f8505-126">Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.</span><span class="sxs-lookup"><span data-stu-id="f8505-126">In Visual Studio, choose **Debug**->**Other Debug Targets**->**Debug Installed App Package**.</span></span>

4. <span data-ttu-id="f8505-127">In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f8505-127">In the **Installed App Packages** list, select your app package, and then choose the **Attach** button.</span></span>

#### <a name="modify-your-app-in-between-debug-sessions"></a><span data-ttu-id="f8505-128">Ändern Sie Ihre App zwischen Debugsitzungen</span><span class="sxs-lookup"><span data-stu-id="f8505-128">Modify your app in between debug sessions</span></span>

<span data-ttu-id="f8505-129">Wenn Sie an Ihrer App Änderungen vornehmen, um Fehlern zu beheben, wechseln Sie sie anhand des MakeAppx-Tools aus.</span><span class="sxs-lookup"><span data-stu-id="f8505-129">If you make your changes to your app to fix bugs, repackage it by using the MakeAppx tool.</span></span> <span data-ttu-id="f8505-130">Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).</span><span class="sxs-lookup"><span data-stu-id="f8505-130">See [Run the MakeAppx tool](desktop-to-uwp-manual-conversion.md#make-appx).</span></span>

### <a name="debug-the-entire-app-lifecycle"></a><span data-ttu-id="f8505-131">Debuggen des gesamten App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="f8505-131">Debug the entire app lifecycle</span></span>

<span data-ttu-id="f8505-132">In einigen Fällen empfiehlt sich eine differenziertere Steuerung des Debugging-Vorgangs, wenn z.B. das Debuggen erfolgen soll, bevor die App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f8505-132">In some cases, you might want finer-grained control over the debugging process, including the ability to debug your app before it starts.</span></span>

<span data-ttu-id="f8505-133">Sie können [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) verwenden, um volle Kontrolle über den App-Lebenszyklus zu erhalten, einschließlich über das Anhalten, Fortsetzen und Beenden.</span><span class="sxs-lookup"><span data-stu-id="f8505-133">You can use [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) to get full control over app lifecycle including suspending, resuming, and termination.</span></span>

<span data-ttu-id="f8505-134">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="f8505-134">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) is included with the Windows SDK.</span></span>

## <a name="test-your-app"></a><span data-ttu-id="f8505-135">Testen der App</span><span class="sxs-lookup"><span data-stu-id="f8505-135">Test your app</span></span>

<span data-ttu-id="f8505-136">Um Ihre App vor der Verteilung in einer realistischen Umgebung zu testen, empfiehlt es sich, Ihre App zu signieren und sie anschließend zu installieren.</span><span class="sxs-lookup"><span data-stu-id="f8505-136">To test your app in a realistic setting as you prepare for distribution, it's best to sign your app and then install it.</span></span>

### <a name="test-an-app-that-you-packaged-by-using-visual-studio"></a><span data-ttu-id="f8505-137">Testen einer mit Visual Studio verpackten App</span><span class="sxs-lookup"><span data-stu-id="f8505-137">Test an app that you packaged by using Visual Studio</span></span>

<span data-ttu-id="f8505-138">Visual Studio signiert Ihre App mit einem Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="f8505-138">Visual Studio signs your app by using a test certificate.</span></span> <span data-ttu-id="f8505-139">Sie finden dieses Zertifikat im Ausgabeordner, den der Assistent **App-Pakete erstellen** generiert.</span><span class="sxs-lookup"><span data-stu-id="f8505-139">You'll find that certificate in the output folder that the **Create App Packages** wizard generates.</span></span> <span data-ttu-id="f8505-140">Die Zertifikatsdatei hat die Erweiterung *.cer*, und Sie müssen dieses Zertifikat im Speicher für **Vertrauenswürdige Stammzertifizierungsstellen** auf dem PC installieren, auf dem Sie Ihre App testen möchten.</span><span class="sxs-lookup"><span data-stu-id="f8505-140">The certificate file has the *.cer* extension and you'll have to install that certificate into the **Trusted Root Certification Authorities** store on the PC that you want to test your app on.</span></span> <span data-ttu-id="f8505-141">Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span><span class="sxs-lookup"><span data-stu-id="f8505-141">See [Sideload your package](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span></span>

### <a name="test-an-app-that-you-packaged-by-using-the-desktop-app-converter-dac"></a><span data-ttu-id="f8505-142">Testen einer mit dem Desktop App Converter (DAC) verpackten App</span><span class="sxs-lookup"><span data-stu-id="f8505-142">Test an app that you packaged by using the Desktop App Converter (DAC)</span></span>

<span data-ttu-id="f8505-143">Wenn Sie Ihre App mithilfe des Desktop App Converters verpackt haben, können Sie die ``sign``-Parameter verwenden, um Ihre App automatisch mit einem generierten Zertifikat zu signieren.</span><span class="sxs-lookup"><span data-stu-id="f8505-143">If you package your app by using the Desktop App Converter, you can use the ``sign`` parameter to automatically sign your app by using a generated certificate.</span></span> <span data-ttu-id="f8505-144">Sie müssen das Zertifikat und anschließend die App installieren.</span><span class="sxs-lookup"><span data-stu-id="f8505-144">You'll have to install that certificate, and then install the app.</span></span> <span data-ttu-id="f8505-145">Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span><span class="sxs-lookup"><span data-stu-id="f8505-145">See [Run the packaged app](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span></span>   


### <a name="manually-sign-apps-optional"></a><span data-ttu-id="f8505-146">Manuelles signieren von Apps (Optional)</span><span class="sxs-lookup"><span data-stu-id="f8505-146">Manually sign apps (Optional)</span></span>

<span data-ttu-id="f8505-147">Sie können Ihre App auch manuell signieren.</span><span class="sxs-lookup"><span data-stu-id="f8505-147">You can also sign your app manually.</span></span> <span data-ttu-id="f8505-148">So geht’s</span><span class="sxs-lookup"><span data-stu-id="f8505-148">Here's how</span></span>

1. <span data-ttu-id="f8505-149">Erstellen eines Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="f8505-149">Create a certificate.</span></span> <span data-ttu-id="f8505-150">Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).</span><span class="sxs-lookup"><span data-stu-id="f8505-150">See [Create a certificate](../packaging/create-certificate-package-signing.md).</span></span>

2. <span data-ttu-id="f8505-151">Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="f8505-151">Install that certificate into the **Trusted Root** or **Trusted People** certificate store on your system.</span></span>

3. <span data-ttu-id="f8505-152">Signieren Sie Ihre App anhand des Zertifikats. Weiter Informationen finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).</span><span class="sxs-lookup"><span data-stu-id="f8505-152">Sign your app by using that certificate, see [Sign an app package using SignTool](../packaging/sign-app-package-using-signtool.md).</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f8505-153">Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.</span><span class="sxs-lookup"><span data-stu-id="f8505-153">Make sure that the publisher name on your certificate matches the publisher name of your app.</span></span>

    **<span data-ttu-id="f8505-154">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="f8505-154">Related sample</span></span>**

    [<span data-ttu-id="f8505-155">SigningCerts</span><span class="sxs-lookup"><span data-stu-id="f8505-155">SigningCerts</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-app-for-windows-10-s"></a><span data-ttu-id="f8505-156">Testen Sie Ihre App für Windows 10 S.</span><span class="sxs-lookup"><span data-stu-id="f8505-156">Test your app for Windows 10 S</span></span>

<span data-ttu-id="f8505-157">Bevor Sie Ihre App veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Wenn Sie Ihre App im Microsoft Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist.</span><span class="sxs-lookup"><span data-stu-id="f8505-157">Before you publish your app, make sure that it will operate correctly on devices that run Windows 10 S. In fact, if you plan to publish your app to the Microsoft Store, you must do this because it is a store requirement.</span></span> <span data-ttu-id="f8505-158">Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert.</span><span class="sxs-lookup"><span data-stu-id="f8505-158">Apps that don't operate correctly on devices that run Windows 10 S won't be certified.</span></span>

<span data-ttu-id="f8505-159">Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).</span><span class="sxs-lookup"><span data-stu-id="f8505-159">See [Test your Windows app for Windows 10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).</span></span>

### <a name="run-another-process-inside-the-full-trust-container"></a><span data-ttu-id="f8505-160">Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container</span><span class="sxs-lookup"><span data-stu-id="f8505-160">Run another process inside the full trust container</span></span>

<span data-ttu-id="f8505-161">Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f8505-161">You can invoke custom processes inside the container of a specified app package.</span></span> <span data-ttu-id="f8505-162">Dies kann nützlich sein, um Szenarien zu testen (z.B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten).</span><span class="sxs-lookup"><span data-stu-id="f8505-162">This can be useful for testing scenarios (for example, if you have a custom test harness and want to test output of the app).</span></span> <span data-ttu-id="f8505-163">Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```:</span><span class="sxs-lookup"><span data-stu-id="f8505-163">To do so, use the ```Invoke-CommandInDesktopPackage``` PowerShell cmdlet:</span></span>

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

## <a name="next-steps"></a><span data-ttu-id="f8505-164">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="f8505-164">Next steps</span></span>

**<span data-ttu-id="f8505-165">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="f8505-165">Find answers to your questions</span></span>**

<span data-ttu-id="f8505-166">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="f8505-166">Have questions?</span></span> <span data-ttu-id="f8505-167">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="f8505-167">Ask us on Stack Overflow.</span></span> <span data-ttu-id="f8505-168">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="f8505-168">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="f8505-169">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="f8505-169">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="f8505-170">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="f8505-170">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="f8505-171">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="f8505-171">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
