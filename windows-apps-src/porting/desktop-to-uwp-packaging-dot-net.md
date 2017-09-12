---
author: normesta
Description: "In diesem Handbuch wird erläutert, wie Sie Ihre Visual Studio-Lösung zum Bearbeiten, Debuggen und Packen Ihrer konvertierten Desktop-App für die Desktop-Brücke konfigurieren."
Search.Product: eADQiWindows 10XVcnh
title: "Verpacken einer App mit Visual Studio (Desktop-Brücke)"
ms.author: normesta
ms.date: 07/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.openlocfilehash: d8919448b965f18ff7f8fdaeda325889e495ef85
ms.sourcegitcommit: f6dd9568eafa10ee5cb2b849c0d82d84a1c5fb93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2017
---
# <a name="package-an-app-by-using-visual-studio-desktop-bridge"></a><span data-ttu-id="e57a9-104">Verpacken einer App mit Visual Studio (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="e57a9-104">Package an app by using Visual Studio (Desktop Bridge)</span></span>

<span data-ttu-id="e57a9-105">Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="e57a9-105">You can use Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="e57a9-106">Anschließend können Sie das Paket im Windows Store veröffentlichen oder es auf einem oder mehreren PCs querladen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-106">Then, you can publish that package to the Windows store or sideload it onto one or more PCs.</span></span>

<span data-ttu-id="e57a9-107">Dieser Anleitung zeigt, wie Sie Ihre Lösung einrichten und ein Paket für Ihre Desktopanwendung generieren.</span><span class="sxs-lookup"><span data-stu-id="e57a9-107">This guide shows you how to set up your solution and then generate a package for your desktop application.</span></span>

## <a name="first-consider-how-youll-distribute-your-app"></a><span data-ttu-id="e57a9-108">Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="e57a9-108">First, consider how you'll distribute your app</span></span>

<span data-ttu-id="e57a9-109">Wenn Sie Ihre App im [Windows Store-](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="e57a9-109">If you plan to publish your app to the [Windows Store](https://www.microsoft.com/store/apps), start by filling out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span></span> <span data-ttu-id="e57a9-110">Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess.</span><span class="sxs-lookup"><span data-stu-id="e57a9-110">Microsoft will contact you to start the onboarding process.</span></span> <span data-ttu-id="e57a9-111">Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="e57a9-111">As part of this process, you'll reserve a name in the store, and obtain information that you'll need to package your app.</span></span>

## <a name="add-a-packaging-project-to-your-solution"></a><span data-ttu-id="e57a9-112">Hinzufügen eines Verpackungsprojekts zur Lösung</span><span class="sxs-lookup"><span data-stu-id="e57a9-112">Add a packaging project to your solution</span></span>

1. <span data-ttu-id="e57a9-113">Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="e57a9-113">In Visual Studio, open the solution that contains your desktop application project.</span></span>

2. <span data-ttu-id="e57a9-114">Fügen Sie der Projektmappe eine JavaScript **Leere App (Universal Windows)**-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="e57a9-114">Add a JavaScript **Blank App (Universal Windows)** project to your solution.</span></span>

   <span data-ttu-id="e57a9-115">Sie müssen keinen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-115">You won't have to add any code to it.</span></span> <span data-ttu-id="e57a9-116">Es dient nur, um ein Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="e57a9-116">It's just there to generate a package for you.</span></span> <span data-ttu-id="e57a9-117">Wir nennen das Projekt „packaging project“.</span><span class="sxs-lookup"><span data-stu-id="e57a9-117">We'll refer to this project as the "packaging project".</span></span>

   ![JavaScript-UWP-Projekt](images/desktop-to-uwp/javascript-uwp-project.png)

   >[!IMPORTANT]
   ><span data-ttu-id="e57a9-119">Im Allgemeinen sollten Sie die JavaScript-Version des Projekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="e57a9-119">In general, you should use the JavaScript version of this project.</span></span>  <span data-ttu-id="e57a9-120">Die C#-, VB.NET- und C++ Versionen haben einige Probleme. Wenn Sie diese verwenden wollen, lesen Sie vorher [Bekannte Probleme](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor).</span><span class="sxs-lookup"><span data-stu-id="e57a9-120">The C#, VB.NET, and C++ versions have a few issues but if you want to use of those, see the [Known Issues](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor) guide before you do.</span></span>

## <a name="add-the-desktop-application-binaries-to-the-packaging-project"></a><span data-ttu-id="e57a9-121">Hinzufügen von Desktopanwendungs-Binärdateien zum Verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="e57a9-121">Add the desktop application binaries to the packaging project</span></span>

<span data-ttu-id="e57a9-122">Hinzufügen von Binärdateien direkt zum Verpackungsprojekt.</span><span class="sxs-lookup"><span data-stu-id="e57a9-122">Add the binaries directly to the packaging project.</span></span>

1. <span data-ttu-id="e57a9-123">In **Projektmappen-Explorer** erweitern Sie den Verpacken-Projektordner, erstellen einen Unterordner und benennen ihn beliebig (z.B.: **win32**).</span><span class="sxs-lookup"><span data-stu-id="e57a9-123">In **Solution Explorer**, expand the packaging project folder, create a subfolder, and name it whatever you want (For example: **win32**).</span></span>

2. <span data-ttu-id="e57a9-124">Klicken Sie jetzt mit der rechten Maustaste auf den Unterordner und wählen Sie **Vorhandenes Elemente hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="e57a9-124">Right-click the subfolder, and then choose **Add Existing Item**.</span></span>

3. <span data-ttu-id="e57a9-125">Im **Vorhandenes Element hinzufügen** Dialogfeld suchen Sie die Dateien aus Ihrem Desktopanwendung-Ausgabeordner und fügen diese hinzu.</span><span class="sxs-lookup"><span data-stu-id="e57a9-125">In the **Add Existing Item** dialog box, locate and then add the files from your desktop application's output folder.</span></span> <span data-ttu-id="e57a9-126">Dazu umfasst nicht nur die ausführbaren Dateien, sondern auch alle DLLs oder config-Dateien, die sich in diesem Ordner befinden.</span><span class="sxs-lookup"><span data-stu-id="e57a9-126">This includes not just the executable files, but any dlls or .config files that are located in that folder.</span></span>

   ![Ausführbare Referenzdatei](images/desktop-to-uwp/cpp-exe-reference.png)

   <span data-ttu-id="e57a9-128">Jedes Mal, wenn Sie an Ihrem Desktopanwendung-Projekt Änderungen vornehmen, müssen Sie eine neue Version dieser Dateien in das Verpacken-Projekt kopieren.</span><span class="sxs-lookup"><span data-stu-id="e57a9-128">Every time you make a change to your desktop application project, you'll have to copy a new version of those files to the packaging project.</span></span> <span data-ttu-id="e57a9-129">Sie können dies automatisieren, indem Sie der Projektdatei des Verpackung-Projekts ein Postbuildereignis hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-129">You can automate this by adding a post-build event to the project file of the packaging project.</span></span> <span data-ttu-id="e57a9-130">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e57a9-130">Here's an example.</span></span>

   ```XML
   <Target Name="PostBuildEvent">
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.exe"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.exe.config"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyWindowsFormsApplication.pdb"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyBusinessLogicLibrary.dll"
       DestinationFolder="win32" />
     <Copy SourceFiles="..\MyWindowsFormsApplication\bin\Debug\MyBusinessLogicLibrary.pdb"
       DestinationFolder="win32" />
   </Target>
   ```

## <a name="modify-the-package-manifest"></a><span data-ttu-id="e57a9-131">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="e57a9-131">Modify the package manifest</span></span>

<span data-ttu-id="e57a9-132">Das Paketprojekt enthält eine Datei, die die Einstellungen des Pakets beschreibt.</span><span class="sxs-lookup"><span data-stu-id="e57a9-132">The packaging project contains a file that describes the settings of your package.</span></span> <span data-ttu-id="e57a9-133">Standardmäßig beschreibt diese Datei eine UWP-App. Sie müssen sie so anpassen, dass das System weiß, dass das Paket eine Desktopanwendung enthält, die in voller Vertrauenswürdigkeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e57a9-133">By default, this file describes a UWP app, so you'll have to modify it so that the system understands that your package includes a desktop application that runs in full trust.</span></span>  

1. <span data-ttu-id="e57a9-134">Erweitern Sie im **Lösungs-Explorer** das Verpacken-Projekt, klicken Sie mit Rechts auf die **package.appxmanifest** Datei und wählen Sie **Code anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="e57a9-134">In **Solution Explorer**, expand the packaging project, right-click the **package.appxmanifest** file, and then choose **View Code**.</span></span>

   ![Referenz-Dotnet-Projekt](images/desktop-to-uwp/reference-dotnet-project.png)

2. <span data-ttu-id="e57a9-136">Fügen Sie diesen Namespace am Anfang der Datei hinzu und fügen Sie das Namespacepräfix zu Liste der ``IgnorableNamespaces`` hinzu.</span><span class="sxs-lookup"><span data-stu-id="e57a9-136">Add this namespace to the top of the file, and add the namespace prefix to the list of ``IgnorableNamespaces``.</span></span>

   ```XML
   xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
   ```
   <span data-ttu-id="e57a9-137">Wenn Sie fertig sind, sehen die Namespacedeklarationen wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="e57a9-137">When you're done, your namespace declarations will look something like this:</span></span>

   ```XML
   <Package
     xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
     xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
     xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
     xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
     IgnorableNamespaces="uap mp rescap">
   ```

3. <span data-ttu-id="e57a9-138">Suchen Sie das ``TargetDeviceFamily``-Element und legen das ``Name``-Attribut auf **Windows.Desktop**, das ``MinVersion``-Attribut auf die Mindestversion des Paketprojekts und das ``MaxVersionTested`` auf die Zielversion des Projekts fest.</span><span class="sxs-lookup"><span data-stu-id="e57a9-138">Find the ``TargetDeviceFamily`` element, and set the ``Name`` attribute to **Windows.Desktop**, the ``MinVersion`` attribute to the minimum version of the packaging project, and the ``MaxVersionTested`` to the target version of the packaging project.</span></span>

   ```XML
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.10586.0" MaxVersionTested="10.0.15063.0" />
   ```

   <span data-ttu-id="e57a9-139">Sie finden die Mindestversion und die Zielversion auf den Eigenschaftenseiten des Verpackung-Projekts.</span><span class="sxs-lookup"><span data-stu-id="e57a9-139">You can find the minimum version and target version in the property pages of the packaging project.</span></span>

   ![Einstellungen für Mindest- und Zielversion](images/desktop-to-uwp/min-target-version-settings.png)


4. <span data-ttu-id="e57a9-141">Entfernen Sie das ``StartPage``-Attribut aus dem ``Application``-Element.</span><span class="sxs-lookup"><span data-stu-id="e57a9-141">Remove the ``StartPage`` attribute from the ``Application`` element.</span></span> <span data-ttu-id="e57a9-142">Fügen Sie dann die ``Executable``- und ``EntryPoint``-Attribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="e57a9-142">Then, add the``Executable`` and ``EntryPoint`` attributes.</span></span>

   <span data-ttu-id="e57a9-143">Das ``Application``-Ergebnis sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="e57a9-143">The ``Application`` element will look like this.</span></span>

   ```XML
   <Application Id="App"  Executable=" " EntryPoint=" ">
   ```

5. <span data-ttu-id="e57a9-144">Legen Sie das ``Executable`` Attribut auf den Namen der ausführbaren Datei für Ihre Desktopanwendung fest.</span><span class="sxs-lookup"><span data-stu-id="e57a9-144">Set the ``Executable`` attribute to the name of your desktop application's executable file.</span></span> <span data-ttu-id="e57a9-145">Legen Sie anschließend das ``EntryPoint``-Attribut auf **Windows.FullTrustApplication** fest.</span><span class="sxs-lookup"><span data-stu-id="e57a9-145">Then, set the ``EntryPoint`` attribute to **Windows.FullTrustApplication**.</span></span>

   <span data-ttu-id="e57a9-146">Das ``Application``-Element sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="e57a9-146">The ``Application`` element will look similar to this.</span></span>

   ```XML
   <Application Id="App"  Executable="win32\MyWindowsFormsApplication.exe" EntryPoint="Windows.FullTrustApplication">
   ```
6. <span data-ttu-id="e57a9-147">Fügen Sie die ``runFullTrust``-Funktion zum ``Capabilities`` Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="e57a9-147">Add the ``runFullTrust`` capability to the ``Capabilities`` element.</span></span>

   ```XML
     <rescap:Capability Name="runFullTrust"/>
   ```
   <span data-ttu-id="e57a9-148">Blaue Wellenlinien werden möglicherweise unter dieser Deklaration angezeigt, doch sie können problemlos ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="e57a9-148">Blue squiggly marks might appear beneath this declaration, but you can safely ignore them.</span></span>

   >[!IMPORTANT]
   <span data-ttu-id="e57a9-149">Wenn Sie ein Pakets für eine C++-Desktopanwendung erstellen, müssen Sie einige zusätzliche Daten in der Manifestdatei ändern, damit Sie die Visual C++-Laufzeitbibliotheken zusammen mit Ihrer App bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="e57a9-149">If your creating a package for a C++ desktop application, you'll have to make a few extra changes to your manifest file so that you can deploy the Visual C++ runtimes along with your app.</span></span> <span data-ttu-id="e57a9-150">Weitere Informationen finden Sie unter [Visual C++-Laufzeiten in einem Projekt für die Desktop-Brücke nutzen](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).</span><span class="sxs-lookup"><span data-stu-id="e57a9-150">See [Using Visual C++ runtimes in a desktop bridge project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/).</span></span>

7. <span data-ttu-id="e57a9-151">Erstellen Sie das Verpacken-Projekt, um sicherzustellen, dass keine Fehler angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e57a9-151">Build the packaging project to ensure that no errors appear.</span></span>

8. <span data-ttu-id="e57a9-152">Wenn Sie das Paket testen möchten, lesen Sie [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md).</span><span class="sxs-lookup"><span data-stu-id="e57a9-152">If you want to test your package, see [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md).</span></span>

   <span data-ttu-id="e57a9-153">Lesen Sie dann den nächsten Abschnitt, um Ihr Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="e57a9-153">Then, return to this guide, and see the next section to generate your package.</span></span>

## <a name="generate-a-package"></a><span data-ttu-id="e57a9-154">Generieren eines Pakets</span><span class="sxs-lookup"><span data-stu-id="e57a9-154">Generate a package</span></span>

<span data-ttu-id="e57a9-155">Um ein Paket für Ihre App zu generieren, befolgen Sie die Anleitung im Thema [Verpacken von UWP-Apps](..\packaging\packaging-uwp-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e57a9-155">To generate a package your app, follow the guidance described in this topic: [Packaging UWP Apps](..\packaging\packaging-uwp-apps.md).</span></span>

<span data-ttu-id="e57a9-156">Wenn Sie die Seite **Auswählen und Konfigurieren von Paketen** erreichen, nehmen Sie sich einen Moment Zeit und überlegen Sie, welche Arten von Binärdateien Sie in Ihrem Paket haben möchten.</span><span class="sxs-lookup"><span data-stu-id="e57a9-156">When you reach the **Select and Configure Packages** screen, Take a moment to consider what sorts of binaries you're including in your package before you select any of the checkboxes.</span></span>

* <span data-ttu-id="e57a9-157">Wenn Sie die Desktopanwendung [erweiterten](desktop-to-uwp-extend.md), indem Sie ein C#-, C++ oder VB.NET-basiertes Universellen Windows-Plattform-Projekt der Projektmappe hinzufügen, wählen die **x86**- und **x64**-Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-157">If you've [extended](desktop-to-uwp-extend.md) your desktop application by adding a adding a C#, C++, or VB.NET-based Universal Windows Platform project to your solution, select the **x86** and **x64** checkboxes.</span></span>  

* <span data-ttu-id="e57a9-158">Wählen Sie andernfalls das **Neutral**-Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-158">Otherwise, choose the **Neutral** checkbox.</span></span>

>[!NOTE]
<span data-ttu-id="e57a9-159">Der Grund für das Auswählen jeder unterstützten Plattform ist, das eine Lösung, die Sie erweitert haben, zwei Arten von Binärdateien enthält. Eine für das UWP-Projekt und eine für das Desktop-Projekt.</span><span class="sxs-lookup"><span data-stu-id="e57a9-159">The reason that you'd have to explicitly choose each supported platform is because an solution that you've extended contains two types of binaries; one for the UWP project and one for the desktop project.</span></span> <span data-ttu-id="e57a9-160">Da diese Arten von Binärdateien unterschiedlich sind, muss .NET Native explizit systemeigene Binärdateien für jede Plattform erstellen.</span><span class="sxs-lookup"><span data-stu-id="e57a9-160">Because these are different types of binaries, .NET Native needs to explicitly produce native binaries for each platform.</span></span>

<span data-ttu-id="e57a9-161">Wenn Fehler auftreten, wenn Sie versuchen, das Paket zu generieren, finden Sie unter der [Bekannte Probleme](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor) Hilfen. Wenn Ihr Problem in dieser Liste nicht angezeigt wird, teilen Sie uns das Problem [hier](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge) mit.</span><span class="sxs-lookup"><span data-stu-id="e57a9-161">If you receive errors when you attempt to generate your package, see the [Known Issues](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-known-issues#known-issues-anchor) guide and if your issue does not appear in that list, please share the issue with us [here](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e57a9-162">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e57a9-162">Next steps</span></span>

**<span data-ttu-id="e57a9-163">Ausführer Ihrer App/Suchen und Beheben von Problemen</span><span class="sxs-lookup"><span data-stu-id="e57a9-163">Run your app / find and fix issues</span></span>**

<span data-ttu-id="e57a9-164">Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="e57a9-164">See [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="e57a9-165">Verbessern Sie Ihre Desktop-App durch Hinzufügen von UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="e57a9-165">Enhance your desktop app by adding UWP APIs</span></span>**

<span data-ttu-id="e57a9-166">Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)</span><span class="sxs-lookup"><span data-stu-id="e57a9-166">See [Enhance your desktop application for Windows 10](desktop-to-uwp-enhance.md)</span></span>

**<span data-ttu-id="e57a9-167">Erweitern Sie Ihre Desktop-App durch Hinzufügen von UWP-Komponenten</span><span class="sxs-lookup"><span data-stu-id="e57a9-167">Extend your desktop app by adding UWP components</span></span>**

<span data-ttu-id="e57a9-168">Siehe [Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten](desktop-to-uwp-extend.md)</span><span class="sxs-lookup"><span data-stu-id="e57a9-168">See [Extend your desktop application with modern UWP components](desktop-to-uwp-extend.md).</span></span>

**<span data-ttu-id="e57a9-169">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="e57a9-169">Distribute your app</span></span>**

<span data-ttu-id="e57a9-170">Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="e57a9-170">See [Distribute a packaged desktop app (Desktop Bridge)](desktop-to-uwp-distribute.md)</span></span>

**<span data-ttu-id="e57a9-171">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="e57a9-171">Find answers to specific questions</span></span>**

<span data-ttu-id="e57a9-172">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="e57a9-172">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="e57a9-173">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="e57a9-173">Give feedback about this article</span></span>**

<span data-ttu-id="e57a9-174">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="e57a9-174">Use the comments section below.</span></span>
