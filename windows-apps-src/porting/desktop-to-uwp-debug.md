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
# <a name="run-debug-and-test-a-packaged-desktop-app-desktop-bridge"></a><span data-ttu-id="fd8ec-106">Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="fd8ec-106">Run, debug, and test a packaged desktop app (Desktop Bridge)</span></span>

<span data-ttu-id="fd8ec-107">Führen Sie Ihre verpackte App aus und prüfen Sie, wie sie aussieht, ohne sie zu signieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-107">Run your packaged app and see how it looks without having to sign it.</span></span> <span data-ttu-id="fd8ec-108">Legen Sie anschließend Haltepunkte fest und lassen Sie den Code schrittweise durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-108">Then, set breakpoints and step through code.</span></span> <span data-ttu-id="fd8ec-109">Wenn Sie bereit sind, Ihre App in einer Produktionsumgebung zu testen, signieren Sie Ihre App und installieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-109">When you're ready to test your app in a production environment, sign your app and then install it.</span></span> <span data-ttu-id="fd8ec-110">In diesem Thema erfahren Sie, wie Sie diese einzelnen Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-110">This topic shows you how to do each of these things.</span></span>

<span id="run-app" />
## <a name="run-your-app"></a><span data-ttu-id="fd8ec-111">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="fd8ec-111">Run your app</span></span>

<span data-ttu-id="fd8ec-112">Sie können Ihre App lokal testen, ohne dass Sie ein Zertifikat benötigen und es signieren müssen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-112">You can run your app to test it out locally without having to obtain a certificate and sign it.</span></span>

<span data-ttu-id="fd8ec-113">Wenn Sie Ihr Paket mit einem UWP-Projekt in Visual Studio erstellt haben, legen Sie das Verpackungsprojekt als Startprojekt fest und drücken Sie dann STRG+F5, um Ihre App zu starten.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-113">If you created your package by using a UWP project in Visual Studio, just set the packaging project as the startup project, and then press CTRL+F5 to start your app.</span></span>

<span data-ttu-id="fd8ec-114">Wenn Sie den Desktop App Converter verwendet oder Ihre App manuell verpackt haben, öffnen Sie eine Windows PowerShell-Befehlsaufforderung, und führen Sie dieses Cmdlet vom **PacakgeFiles**-Unterordner des Ausgabeordners aus:</span><span class="sxs-lookup"><span data-stu-id="fd8ec-114">If you used the Desktop App Converter or you package your app manually, open a Windows PowerShell command prompt, and from the **PacakgeFiles** subfolder of your output folder, run this cmdlet:</span></span>

```
Add-AppxPackage –Register AppxManifest.xml
```
<span data-ttu-id="fd8ec-115">Finden Sie Ihre App im Windows-Startmenü, um sie auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-115">To start your app, find it in the Windows Start menu.</span></span>

![Verpackte App im Startmenü.](images/desktop-to-uwp/converted-app-installed.png)

> [!NOTE]
> <span data-ttu-id="fd8ec-117">Eine verpackte App wird immer als ein interaktiver Benutzer ausgeführt, und jedes Laufwerk, auf das Sie die verpackte App installieren, muss auf das NTFS-Format formatiert sein.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-117">A packaged app always runs as an interactive user, and any drive that you install your packaged app on to must be formatted to NTFS format.</span></span>

## <a name="debug-your-app"></a><span data-ttu-id="fd8ec-118">Debuggen Sie Ihre App</span><span class="sxs-lookup"><span data-stu-id="fd8ec-118">Debug your app</span></span>

<span data-ttu-id="fd8ec-119">Wählen Sie Ihr Paket in einem Dialogfeld bei jedem Debuggen Ihrer App oder Installieren einer Erweiterung aus und Debuggen Sie Ihre App ohne jedes Mal Ihr Paket auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-119">Select your package in a dialog box each time that you debug your app or install an extension and debug your app without having to select your package each time that you start the session.</span></span>

### <a name="debug-your-app-by-selecting-the-package"></a><span data-ttu-id="fd8ec-120">Debuggen Sie Ihre App, indem Sie das Paket auswählen</span><span class="sxs-lookup"><span data-stu-id="fd8ec-120">Debug your app by selecting the package</span></span>

<span data-ttu-id="fd8ec-121">Diese Option hat die kürzeste Einrichtungszeit, aber Sie müssen bei der Ausführung jeder Debugsitzung einen zusätzlichen Schritt durchführen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-121">This option has the least amount of setup time, but requires you to perform an extra step each time you want to start the debug session.</span></span>


1. <span data-ttu-id="fd8ec-122">Stellen Sie sicher, dass Sie Ihr App-Paket mindestens ein Mal starten, damit es auf dem lokalen Computer installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-122">Make sure that you start your packaged app at least one time so that it's installed on your local machine.</span></span>

   <span data-ttu-id="fd8ec-123">Informationen hierzu finden Sie im Abschnitt [Ausführen Ihrer App](#run-app) weiter oben.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-123">See the [Run your app](#run-app) section above.</span></span>

2. <span data-ttu-id="fd8ec-124">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-124">Start Visual Studio.</span></span>

   <span data-ttu-id="fd8ec-125">Wenn Sie Ihre App mit erhöhten Berechtigungen debuggen möchten, starten Sie Visual Studio anhand der Option **als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-125">If you want to debug your app with elevated permissions, start Visual Studio by using the **Run as Administrator** option.</span></span>

3. <span data-ttu-id="fd8ec-126">Wählen Sie in Visual Studio **Debuggen**->**Andere Debugziele**->**Installiertes App-Paket debuggen**.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-126">In Visual Studio, choose **Debug**->**Other Debug Targets**->**Debug Installed App Package**.</span></span>

4. <span data-ttu-id="fd8ec-127">In der **installierte App-Pakete** Liste, wählen Sie das App-Paket, und wählen Sie dann die **Anhängen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-127">In the **Installed App Packages** list, select your app package, and then choose the **Attach** button.</span></span>


### <a name="debug-your-app-without-having-to-select-the-package"></a><span data-ttu-id="fd8ec-128">Debuggen Sie Ihre App ohne das Paket auswählen zu müssen</span><span class="sxs-lookup"><span data-stu-id="fd8ec-128">Debug your app without having to select the package</span></span>

<span data-ttu-id="fd8ec-129">Diese Option hat die längste Einrichtungszeit, jedoch werden Sie nicht das installiere Paket jedes Mal beim Starten Ihrer App auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-129">This option has the most amount of setup time, but you won't have to select the installed package every time you start your app.</span></span> <span data-ttu-id="fd8ec-130">Sie müssen [Visual Studio2017](https://www.visualstudio.com/vs/whatsnew/) installieren, um diese Option nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-130">You'll need to install [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) to use this approach.</span></span>

1. <span data-ttu-id="fd8ec-131">Installieren Sie zunächst die [Desktop-Brücke Debugging Project](http://go.microsoft.com/fwlink/?LinkId=797871).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-131">First, install the [Desktop Bridge Debugging Project](http://go.microsoft.com/fwlink/?LinkId=797871).</span></span>

2. <span data-ttu-id="fd8ec-132">Starten Sie Visual Studio, und öffnen Sie das Projekt für die Desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-132">Start Visual Studio, and open the desktop application project.</span></span>

6. <span data-ttu-id="fd8ec-133">Hinzufügen eines **Debuggen von Desktop-Brücke**-Projekts zur Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-133">Add a **Desktop Bridge Debugging** project to your solution.</span></span>

   <span data-ttu-id="fd8ec-134">Sie finden die Projektvorlage in der Gruppe **Andere Projekttypen** der installierten Vorlagen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-134">You can find the project template in the **Other Project Types** group of installed templates.</span></span>

    ![alt](images/desktop-to-uwp/debug-2.png)

    <span data-ttu-id="fd8ec-136">Das **Debuggen von Desktop-Brücke**-Projekt wird in der Projektmappe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-136">The **Desktop Bridge Debugging** project will appear in your solution.</span></span>

    ![alt](images/desktop-to-uwp/debug-3.png)

7. <span data-ttu-id="fd8ec-138">Öffnen Sie die Eigenschaftenseiten des **Debuggen von Desktop-Brücke**-Projekts.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-138">Open the property pages of the **Desktop Bridge Debugging** project.</span></span>

8. <span data-ttu-id="fd8ec-139">Legen Sie das **Paketlayout**-Feld auf den Speicherort Ihres Manifestdateienpakets (AppxManifest.xml) fest, und wählen Sie die ausführbare Datei Ihrer App aus der Dropdown-Liste **Kachel starten**.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-139">Set the **Package Layout** field to the location of your package manifest file (AppxManifest.xml), and choose your app's executable file from the **Start Up Tile** drop-down list.</span></span>

     ![alt](images/desktop-to-uwp/debug-4.png)

8. <span data-ttu-id="fd8ec-141">Öffnen Sie die Datei AppXPackageFileList.xml im Code-Editor.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-141">Open the AppXPackageFileList.xml file in the code editor.</span></span>

9. <span data-ttu-id="fd8ec-142">Entfernen Sie Kommentare aus dem XML-Block, und geben Sie die Werte für diese Elemente ein:</span><span class="sxs-lookup"><span data-stu-id="fd8ec-142">Uncomment the block of XML and add values for these elements:</span></span>

   <span data-ttu-id="fd8ec-143">**MyProjectOutputPath**: Der relative Pfad zum Ordner „Debug” von Ihrer Desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-143">**MyProjectOutputPath**: The relative path to debug folder of your desktop application.</span></span>

   <span data-ttu-id="fd8ec-144">**LayoutFile**: Die ausführbare Datei, die im Ordner „Debug” von Ihrer Desktop-Anwendung ist.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-144">**LayoutFile**: The executable that is in the debug folder of your desktop application.</span></span>

   <span data-ttu-id="fd8ec-145">**PackagePath**: Der vollqualifizierte Name für die ausführbare Datei Ihrer Desktop-Anwendung, die zu Ihrem Windows-App-Paketordner während der Konvertierung kopiert wurde.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-145">**PackagePath**: The fully qualified file name of your desktop application's executable that was copied to your Windows app package folder during the conversion process.</span></span>

    <span data-ttu-id="fd8ec-146">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="fd8ec-146">Here's an example:</span></span>

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

  <span data-ttu-id="fd8ec-147">Wenn Ihre App DLL-Dateien nutzt, die von anderen Projekten in Ihrer Projektmappe generiert werden, und Sie den Code ändern wollen, der in diesen DLL-Dateien enthalten ist, dann fügen Sie für diese DLL-Dateien ein **LayoutFile**-Element ein.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-147">If your app consumes dll files that are generated from other projects in your solution, and you want to step into the code that is contained in those dlls, include a **LayoutFile** element for each of those dll files.</span></span>

  ```XML
  ...
      <LayoutFile Include="$(MyProjectOutputPath)\MyDesktopApp.Models.dll">
      <PackagePath>$(PackageLayout)\MyDesktopApp.Models.dll</PackagePath>
      </LayoutFile>
  ...
  ```

10. <span data-ttu-id="fd8ec-148">Legen Sie das Paketprojekt als Startprojekt fest.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-148">Set the packaging project the start-up project.</span></span>  

    ![alt](images/desktop-to-uwp/debug-5.png)

11. <span data-ttu-id="fd8ec-150">Legen Sie Haltepunkte im Code Ihrer Desktop-Anwendung fest, und starten Sie den Debugger.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-150">Set breakpoints in your desktop application code, and then start the debugger.</span></span>

  ![Debug-Schaltfläche](images/desktop-to-uwp/debugger-button.png)

  <span data-ttu-id="fd8ec-152">Visual Studio kopiert die ausführbaren und DLL-Dateien, die Sie in der XML-Datei für Ihr Windows-App-Paket angegeben haben, und startet dann den Debugger.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-152">Visual Studio copies the executables and dll files that you specified in the XML file to your Windows app package and then start the debugger.</span></span>

#### <a name="handle-multiple-build-configurations"></a><span data-ttu-id="fd8ec-153">Mehrere Buildkonfigurationen steuern</span><span class="sxs-lookup"><span data-stu-id="fd8ec-153">Handle multiple build configurations</span></span>

<span data-ttu-id="fd8ec-154">Wenn Sie mehrere Buildkonfigurationen definiert haben (z.B.: Veröffentlichen und Debuggen), können Sie die Datei AppXPackageFileList.xml ändern, um nur die Dateien zu kopieren, die der Buildkonfiguration entspricht, die Sie in Visual Studio beim Starten des Debuggers gewählt haben.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-154">If you've defined multiple build configurations (for example: Release and Debug), you can modify your AppXPackageFileList.xml file to copy only those files that match the build configuration that choose in Visual Studio when you start the debugger.</span></span>

<span data-ttu-id="fd8ec-155">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="fd8ec-155">Here's an example.</span></span>

```XML
<PropertyGroup>
    <MyProjectOutputPath Condition="$(Configuration) == 'Debug'">..\MyDesktopApp\bin\Debug</MyProjectOutputPath>
    <MyProjectOutputPath Condition="$(Configuration) == 'Release'"> ..\MyDesktopApp\bin\Release</MyProjectOutputPath>
</PropertyGroup>
```

#### <a name="debug-uwp-enhancements-to-your-app"></a><span data-ttu-id="fd8ec-156">Debuggen von UWP-Erweiterungen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="fd8ec-156">Debug UWP enhancements to your app</span></span>

<span data-ttu-id="fd8ec-157">Sie möchten vielleicht Ihre App mit modernen Funktionen wie Live-Kacheln optimieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-157">You might want to enhance your app with modern experiences such as live tiles.</span></span> <span data-ttu-id="fd8ec-158">Wenn das der Fall ist, können Sie bedingte Kompilierung verwenden, um Codepfade mit bestimmten Buildkonfigurationen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-158">If you do, you can use conditional compilation to enable code paths with specific build configurations.</span></span>

1. <span data-ttu-id="fd8ec-159">Definieren Sie zunächst in Visual Studio eine Buildkonfiguration und geben Sie ihr einen Namen wie „DesktopUWP”.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-159">First, in Visual Studio, define a build configuration and give it a name like "DesktopUWP".</span></span>

2. <span data-ttu-id="fd8ec-160">Fügen Sie in der Registerkarte **Build** der Projekteigenschaften Ihres Projekts den Namen im Feld **Symbole für bedingte Kompilierung** hinzu.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-160">In the **Build** tab of the project properties of your project, add that name in the **Conditional compilation symbols** field.</span></span>

     ![alt](images/desktop-to-uwp/debug-8.png)

3. <span data-ttu-id="fd8ec-162">Fügen Sie bedingte Codeblöcke hinzu.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-162">Add conditional code blocks.</span></span> <span data-ttu-id="fd8ec-163">Dieser Code wird nur für die **DesktopUWP**-Buildkonfiguration kompiliert.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-163">This code compiles only for the **DesktopUWP** build configuration.</span></span>

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

### <a name="debug-the-entire-app-lifecycle"></a><span data-ttu-id="fd8ec-164">Debuggen des gesamten App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="fd8ec-164">Debug the entire app lifecycle</span></span>

<span data-ttu-id="fd8ec-165">In einigen Fällen empfiehlt sich eine differenziertere Steuerung des Debugging-Vorgangs, wenn z.B. das Debuggen erfolgen soll, bevor die App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-165">In some cases, you might want finer-grained control over the debugging process, including the ability to debug your app before it starts.</span></span>

<span data-ttu-id="fd8ec-166">Sie können [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) verwenden, um volle Kontrolle über den App-Lebenszyklus zu erhalten, einschließlich über das Anhalten, Fortsetzen und Beenden.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-166">You can use [PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) to get full control over app lifecycle including suspending, resuming, and termination.</span></span>

<span data-ttu-id="fd8ec-167">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) ist im Windows SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-167">[PLMDebug](https://msdn.microsoft.com/library/windows/hardware/jj680085(v=vs.85).aspx) is included with the Windows SDK.</span></span>


### <a name="modify-your-app-in-between-debug-sessions"></a><span data-ttu-id="fd8ec-168">Ändern Sie Ihre App zwischen Debugsitzungen</span><span class="sxs-lookup"><span data-stu-id="fd8ec-168">Modify your app in between debug sessions</span></span>

<span data-ttu-id="fd8ec-169">Wenn Sie an Ihrer App Änderungen vornehmen, um Fehlern zu beheben, wechseln Sie sie anhand des MakeAppx-Tools aus.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-169">If you make your changes to your app to fix bugs, repackage it by using the MakeAppx tool.</span></span> <span data-ttu-id="fd8ec-170">Informationen hierzu finden Sie unter [Ausführen des MakeAppx-Tools](desktop-to-uwp-manual-conversion.md#make-appx).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-170">See [Run the MakeAppx tool](desktop-to-uwp-manual-conversion.md#make-appx).</span></span>

## <a name="test-your-app"></a><span data-ttu-id="fd8ec-171">Testen der App</span><span class="sxs-lookup"><span data-stu-id="fd8ec-171">Test your app</span></span>

<span data-ttu-id="fd8ec-172">Um Ihre App vor der Verteilung in einer realistischen Umgebung zu testen, empfiehlt es sich, Ihre App zu signieren und sie anschließend zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-172">To test your app in a realistic setting as you prepare for distribution, it's best to sign your app and then install it.</span></span>

<span data-ttu-id="fd8ec-173">Wenn Sie Ihre App anhand Visual Studio verpackt haben, können Sie ein Skript zum Signieren Ihrer App ausführen und sie anschließend installieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-173">If you packaged you app by using Visual Studio, you can run a script to sign your app and then install it.</span></span> <span data-ttu-id="fd8ec-174">Weitere Informationen finden Sie unter [Querladen des App-Pakets](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-174">See [Sideload your package](../packaging/packaging-uwp-apps.md#sideload-your-app-package).</span></span>

<span data-ttu-id="fd8ec-175">Wenn Sie Ihre App mithilfe des Desktop App Converters verpackt haben, können Sie die ``sign``-Parameter verwenden, um Ihre App automatisch mit einem generierten Zertifikat zu signieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-175">If you package your app by using the Desktop App Converter, you can use the ``sign`` parameter to automatically sign your app by using a generated certificate.</span></span> <span data-ttu-id="fd8ec-176">Sie müssen das Zertifikat und anschließend die App installieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-176">You'll have to install that certificate, and then install the app.</span></span> <span data-ttu-id="fd8ec-177">Weitere Informationen finden Sie unter [Ausführung der verpackten App](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-177">See [Run the packaged app](desktop-to-uwp-run-desktop-app-converter.md#run-app).</span></span>   

<span data-ttu-id="fd8ec-178">Sie können Ihre App auch manuell signieren.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-178">You can also sign your app manually.</span></span> <span data-ttu-id="fd8ec-179">So geht’s</span><span class="sxs-lookup"><span data-stu-id="fd8ec-179">Here's how</span></span>

1. <span data-ttu-id="fd8ec-180">Erstellen eines Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-180">Create a certificate.</span></span> <span data-ttu-id="fd8ec-181">Weitere Informationen finden Sie unter [Erstellen eines Zertifikats](../packaging/create-certificate-package-signing.md).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-181">See [Create a certificate](../packaging/create-certificate-package-signing.md).</span></span>

2. <span data-ttu-id="fd8ec-182">Installieren Sie das Zertifikat im Zertifikatsspeicher **Vertrauenswürdiger Stamm** oder **Vertrauenswürdige Personen** auf Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-182">Install that certificate into the **Trusted Root** or **Trusted People** certificate store on your system.</span></span>

3. <span data-ttu-id="fd8ec-183">Signieren Sie Ihre App anhand des Zertifikats. Weiter Informationen finden Sie unter [Signieren eines App-Pakets mit SignTool](../packaging/sign-app-package-using-signtool.md).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-183">Sign your app by using that certificate, see [Sign an app package using SignTool](../packaging/sign-app-package-using-signtool.md).</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="fd8ec-184">Stellen Sie sicher, dass der Name des Herausgebers auf dem Zertifikat dem Namen des Herausgebers Ihrer App entspricht.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-184">Make sure that the publisher name on your certificate matches the publisher name of your app.</span></span>

### <a name="related-sample"></a><span data-ttu-id="fd8ec-185">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="fd8ec-185">Related sample</span></span>

[<span data-ttu-id="fd8ec-186">SigningCerts</span><span class="sxs-lookup"><span data-stu-id="fd8ec-186">SigningCerts</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SigningCerts)


### <a name="test-your-app-for-windows-10-s"></a><span data-ttu-id="fd8ec-187">Testen Sie Ihre App für Windows 10 S.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-187">Test your app for Windows 10 S</span></span>

<span data-ttu-id="fd8ec-188">Bevor Sie Ihre App veröffentlichen, stellen Sie sicher, dass sie korrekt auf Geräten unter Windows10 S ausgeführt wird. Wenn Sie Ihre App im Windows Store veröffentlichen möchten, müssen Sie dies tun, da es eine Anforderung des Stores ist.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-188">Before you publish your app, make sure that it will operate correctly on devices that run Windows 10 S. In fact, if you plan to publish your app to the Windows Store, you must do this because it is a store requirement.</span></span> <span data-ttu-id="fd8ec-189">Apps, die auf Geräten unter Windows10 S nicht ordnungsgemäß funktionieren, werden nicht zertifiziert.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-189">Apps that don't operate correctly on devices that run Windows 10 S won't be certified.</span></span> 

<span data-ttu-id="fd8ec-190">Weitere Informationen finden Sie unter [Testen Ihrer Windows-App für Windows10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-190">See [Test your Windows app for Windows 10 S](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-test-windows-s).</span></span>

### <a name="run-another-process-inside-the-full-trust-container"></a><span data-ttu-id="fd8ec-191">Ausführen eines anderen Prozesses im vollständig vertrauenswürdigen Container</span><span class="sxs-lookup"><span data-stu-id="fd8ec-191">Run another process inside the full trust container</span></span>

<span data-ttu-id="fd8ec-192">Sie können benutzerdefinierte Prozesse im Container eines angegebenen App-Pakets aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-192">You can invoke custom processes inside the container of a specified app package.</span></span> <span data-ttu-id="fd8ec-193">Dies kann nützlich sein, um Szenarien zu testen (z.B. wenn Sie über eine benutzerdefinierte Testumgebung verfügen und die Ausgabe der App testen möchten).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-193">This can be useful for testing scenarios (for example, if you have a custom test harness and want to test output of the app).</span></span> <span data-ttu-id="fd8ec-194">Verwenden Sie hierzu das PowerShell-Cmdlet ```Invoke-CommandInDesktopPackage```:</span><span class="sxs-lookup"><span data-stu-id="fd8ec-194">To do so, use the ```Invoke-CommandInDesktopPackage``` PowerShell cmdlet:</span></span>

```CMD
Invoke-CommandInDesktopPackage [-PackageFamilyName] <string> [-AppId] <string> [-Command] <string> [[-Args]
    <string>]  [<CommonParameters>]
```

## <a name="next-steps"></a><span data-ttu-id="fd8ec-195">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="fd8ec-195">Next steps</span></span>

**<span data-ttu-id="fd8ec-196">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="fd8ec-196">Find answers to specific questions</span></span>**

<span data-ttu-id="fd8ec-197">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="fd8ec-197">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="fd8ec-198">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="fd8ec-198">Give feedback about this article</span></span>**

<span data-ttu-id="fd8ec-199">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="fd8ec-199">Use the comments section below.</span></span>
