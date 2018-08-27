---
author: rido-min
Description: This guide explains how to configure your Visual Studio Solution to optimize the application binaries with native images.
Search.Product: eADQiWindows 10XVcnh
title: Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder
ms.author: normesta
ms.date: 06/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, systemeigene Abbild Compiler
ms.localizationpriority: medium
ms.openlocfilehash: d98b576fb51a8f9507802796ab359d0d00d21998
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2855274"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a><span data-ttu-id="6db0a-103">Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder</span><span class="sxs-lookup"><span data-stu-id="6db0a-103">Optimize your .NET Desktop apps with native images</span></span>

> [!NOTE]
> <span data-ttu-id="6db0a-104">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-104">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="6db0a-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="6db0a-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="6db0a-106">Sie können die Startzeit der .NET Framework-Anwendung verbessern, indem Sie vor dem Kompilieren der Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="6db0a-106">You can improve the startup time of your .NET Framework application by pre-compiling your binaries.</span></span> <span data-ttu-id="6db0a-107">Sie können diese Technologie auf große Applikationen verwenden, die Sie packen und verteilen Sie über den Windows Store.</span><span class="sxs-lookup"><span data-stu-id="6db0a-107">You can use this technology on large applications that you package and distribute through the Windows Store.</span></span> <span data-ttu-id="6db0a-108">In einigen Fällen haben wir eine leistungsverbesserung von 20 % beobachtet.</span><span class="sxs-lookup"><span data-stu-id="6db0a-108">In some cases, we've observed a 20% performance improvement.</span></span> <span data-ttu-id="6db0a-109">Erfahren Sie mehr über diese Technologie in der [technischen Überblick](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6db0a-109">You can learn more about this technology in the [technical overview](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).</span></span>

<span data-ttu-id="6db0a-110">Wir haben eine Preview-Version des Compilers systemeigene Bild als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="6db0a-110">We've released a preview version of the native image compiler as a [NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler).</span></span> <span data-ttu-id="6db0a-111">Sie können dieses Paket auf einer beliebigen .NET Framework-Anwendung, die auf .NET Framework, Version 4.6.2 abzielt anwenden oder höher.</span><span class="sxs-lookup"><span data-stu-id="6db0a-111">You can apply this package to any .NET Framework application that targets the .NET Framework version 4.6.2 or later.</span></span> <span data-ttu-id="6db0a-112">Dieses Paket Fügt einen Post Buildschritt, der eine systemeigene Nutzlast die Binärdateien, die für die von der Anwendung verwendeten enthält.</span><span class="sxs-lookup"><span data-stu-id="6db0a-112">This package adds a post build step that includes a native payload to all the binaries used by your application.</span></span> <span data-ttu-id="6db0a-113">Diese optimierte Nutzlast wird beim Ausführen der Anwendung in .NET 4.7.2 und höher während Vorgängerversionen MSIL-Code noch geladen werden geladen.</span><span class="sxs-lookup"><span data-stu-id="6db0a-113">This optimized payload will be loaded when the application runs in .NET 4.7.2 and above while previous versions will still load the MSIL code.</span></span>

<span data-ttu-id="6db0a-114">Das [.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) ist in der [Windows-10 April 2018 aktualisieren](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)enthalten.</span><span class="sxs-lookup"><span data-stu-id="6db0a-114">The [.NET framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) is included in the [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/).</span></span> <span data-ttu-id="6db0a-115">Sie können auch diese Version von .NET Framework auf PCs installieren, auf denen Windows 7 + und Windows Server 2008 R2 oder höher ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-115">You can also install this version of the .NET Framework on PC's that run Windows 7+ and Windows Server 2008 R2+.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6db0a-116">Wenn Sie systemeigene Abbilder für Ihre Anwendung mithilfe der Windows-Anwendung packprojekt gepackt erstellen möchten, stellen Sie sicher, dass Sie die Ziel-Plattform mindestens Version des Projekts auf die Windows-Updates im Unternehmen festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-116">If you want to produce native images for your application packaged by  the Windows Application Packaging project, make sure to set the Target Platform Minimum version of the project to the Windows Anniversary Update.</span></span>

## <a name="how-to-produce-native-images"></a><span data-ttu-id="6db0a-117">Wie systemeigene Abbilder erzeugt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-117">How to produce native images</span></span>

<span data-ttu-id="6db0a-118">Befolgen Sie diese Anweisungen zum Konfigurieren von Projekten.</span><span class="sxs-lookup"><span data-stu-id="6db0a-118">Follow these instructions to configure your projects.</span></span>

1. <span data-ttu-id="6db0a-119">Konfigurieren Sie das Zielframework als 4.6.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="6db0a-119">Configure the target framework as 4.6.2 or above</span></span>

2. <span data-ttu-id="6db0a-120">Konfigurieren der Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="6db0a-120">Configure the target platform as x86 or x64</span></span> 

3. <span data-ttu-id="6db0a-121">Fügen Sie die NuGet-Pakete.</span><span class="sxs-lookup"><span data-stu-id="6db0a-121">Add the NuGet packages.</span></span>

4. <span data-ttu-id="6db0a-122">Erstellen Sie einen Versionsbuild.</span><span class="sxs-lookup"><span data-stu-id="6db0a-122">Create a Release Build.</span></span>

## <a name="configure-the-target-framework-as-462-or-above"></a><span data-ttu-id="6db0a-123">Konfigurieren Sie das Zielframework als 4.6.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="6db0a-123">Configure the target framework as 4.6.2 or above</span></span>

<span data-ttu-id="6db0a-124">So konfigurieren Sie Ihr Projekt .NET Framework 4.6.2 Ziel benötigen Sie die .NET Framework 4.6.2 Entwicklungstools oder höher.</span><span class="sxs-lookup"><span data-stu-id="6db0a-124">To configure your project to target .NET Framework 4.6.2 you will need the .NET Framework 4.6.2 development tools or newer.</span></span> <span data-ttu-id="6db0a-125">Diese Tools sind als optionale Komponenten unter den desktop Entwicklungsaufwand .NET über die Visual Studio-Installer verfügbar:</span><span class="sxs-lookup"><span data-stu-id="6db0a-125">These tools are available through the Visual Studio installer as optional components under the .NET desktop development workload:</span></span>

![Installieren von .NET 4.6.2 Entwicklungswerkzeuge (engl.)](images/desktop-to-uwp/install-4.6.2-devpack.png)

<span data-ttu-id="6db0a-127">Alternativ können Sie die .NET Developer Packs aus abrufen:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span><span class="sxs-lookup"><span data-stu-id="6db0a-127">Alternatively, you can get the .NET developer packs from: [https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span></span>

## <a name="configure-the-target-platform-as-x86-or-x64"></a><span data-ttu-id="6db0a-128">Konfigurieren der Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="6db0a-128">Configure the target platform as x86 or x64</span></span>

<span data-ttu-id="6db0a-129">Der systemeigene Abbild Compiler optimiert den Code für eine bestimmte Plattform.</span><span class="sxs-lookup"><span data-stu-id="6db0a-129">The native image compiler optimizes the code for a given platform.</span></span> <span data-ttu-id="6db0a-130">Um es zu verwenden, müssen Sie die Anwendung für eine bestimmte wie X86 oder X64 Zielplattform konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="6db0a-130">To use it, you need to configure your application to target one specific platform such as x86 or x64.</span></span>

<span data-ttu-id="6db0a-131">Wenn Sie mehrere Projekte in der Projektmappe verfügen, muss nur das Eintrag Punkt Projekt (wahrscheinlich das Projekt, das eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="6db0a-131">If you have multiple projects in your solution, only the entry point project (most likely the project that produces an executable file) has to be compiled as x86 or x64.</span></span> <span data-ttu-id="6db0a-132">Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden, auch wenn sie als AnyCPU kompiliert werden mit der Architektur, die in die Hauptassembly des Projekts, angegebenen verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="6db0a-132">Additional binaries referenced from the main project will be processed with the architecture specified in the main project, even if they are compiled as AnyCPU.</span></span>

<span data-ttu-id="6db0a-133">So konfigurieren Sie Ihr Projekt:</span><span class="sxs-lookup"><span data-stu-id="6db0a-133">To configure your project:</span></span>

1. <span data-ttu-id="6db0a-134">Maustaste auf die Projektmappe, und wählen Sie dann auf **Konfigurations-Manager**.</span><span class="sxs-lookup"><span data-stu-id="6db0a-134">Right-click your solution, and then select **Configuration Manager**.</span></span>

2. <span data-ttu-id="6db0a-135">Wählen Sie **< neu. >** im Dropdownmenü **Plattform** neben dem Namen des Projekts, das die ausführbare Datei erzeugt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-135">Select **<New ..>** in the **Platform** dropdown menu beside the name of the project that produces your executable file.</span></span>

3. <span data-ttu-id="6db0a-136">Klicken Sie im Dialogfeld **Neues Projektplattform** sicher, dass die Dropdownliste für **Copy Settings from** auf **Any CPU**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="6db0a-136">In the **New Project Platform** dialog box, make sure that the **Copy Settings from** dropdown list is set to **Any CPU**.</span></span>

![Konfigurieren von x86](images/desktop-to-uwp/configure-x86.png)

<span data-ttu-id="6db0a-138">Wiederholen Sie diesen Schritt für `Release/x64` Wenn X64 erzeugen soll Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="6db0a-138">Repeat this step for `Release/x64` if you want produce x64 binaries.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="6db0a-139">AnyCPU-Konfiguration wird vom Compiler systemeigene Abbild nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-139">AnyCPU configuration is not supported by the native image compiler.</span></span>

## <a name="add-the-nuget-packages"></a><span data-ttu-id="6db0a-140">Hinzufügen von NuGet-Pakete</span><span class="sxs-lookup"><span data-stu-id="6db0a-140">Add the NuGet packages</span></span>

<span data-ttu-id="6db0a-141">Systemeigene Abbild Compiler wird als ein NuGet-Paket bereitgestellt, die Visual Studio-Projekt hinzuzufügen, die ausführbare Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-141">The native image compiler is provided as a NuGet package that you need to add to the Visual Studio project that produces the executable file.</span></span> <span data-ttu-id="6db0a-142">Dies ist üblicherweise das Windows Forms oder WPF-Projekt.</span><span class="sxs-lookup"><span data-stu-id="6db0a-142">This is typically your Windows Forms or WPF project.</span></span> <span data-ttu-id="6db0a-143">Verwenden Sie diesen Befehl PowerShell, dafür.</span><span class="sxs-lookup"><span data-stu-id="6db0a-143">Use this PowerShell command to do that.</span></span>

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> <span data-ttu-id="6db0a-144">Die Preview-Pakete werden als nicht aufgeführte in NuGet.org veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="6db0a-144">The preview packages are published in NuGet.org as unlisted.</span></span> <span data-ttu-id="6db0a-145">Diese werden nicht durch Durchsuchen NuGet.org oder mithilfe der Paket-Manager-UI in Visual Studio finden.</span><span class="sxs-lookup"><span data-stu-id="6db0a-145">You won’t find them by browsing NuGet.org or by using the Package Manager UI in Visual Studio.</span></span> <span data-ttu-id="6db0a-146">Sie können jedoch installieren sie die Paket-Manager-Konsole und wann Sie von einem anderen Computer wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="6db0a-146">However, you can install them from the Package Manager Console, and when you restoring from a different machine.</span></span> <span data-ttu-id="6db0a-147">Wir stellen die Pakete vollständig zugänglich beim Veröffentlichen der ersten nicht-Preview-Version.</span><span class="sxs-lookup"><span data-stu-id="6db0a-147">We'll make the packages fully accessible when we publish the first non-preview version.</span></span>

## <a name="create-a-release-build"></a><span data-ttu-id="6db0a-148">Erstellen eines Builds Version</span><span class="sxs-lookup"><span data-stu-id="6db0a-148">Create a Release Build</span></span>

<span data-ttu-id="6db0a-149">NuGet-Paket konfiguriert das Projekt, um ein zusätzliches Tool für Version Builds ausführen.</span><span class="sxs-lookup"><span data-stu-id="6db0a-149">The NuGet package configures the project to run an additional tool for release builds.</span></span> <span data-ttu-id="6db0a-150">Dieses Tool hinzugefügt dieselben Binärdateien systemeigenen Code.</span><span class="sxs-lookup"><span data-stu-id="6db0a-150">This tool adds the native code to the same binaries.</span></span>
<span data-ttu-id="6db0a-151">Um sicherzustellen, dass das Tool, die Binärdateien verarbeitet wurden können Sie den Ausgabe, um sicherzustellen, dass sie eine Nachricht wie diesen enthält Build überprüfen:</span><span class="sxs-lookup"><span data-stu-id="6db0a-151">To verify that the tool has processed the binaries you can review the build output to make sure it includes a message such as this one:</span></span>

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a><span data-ttu-id="6db0a-152">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="6db0a-152">FAQ</span></span>

**<span data-ttu-id="6db0a-153">Q.</span><span class="sxs-lookup"><span data-stu-id="6db0a-153">Q.</span></span> <span data-ttu-id="6db0a-154">Funktionieren die neuen Binärdateien auf Computern ohne .NET Framework 4.7.2?</span><span class="sxs-lookup"><span data-stu-id="6db0a-154">Do the new binaries work on machines without .NET Framework 4.7.2?</span></span>**

<span data-ttu-id="6db0a-155">A.</span><span class="sxs-lookup"><span data-stu-id="6db0a-155">A.</span></span> <span data-ttu-id="6db0a-156">Optimierte Binärdateien profitieren von der Verbesserungen bei der Ausführung mit .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="6db0a-156">Optimized binaries will benefit from the improvements when running with .NET Framework 4.7.2.</span></span> <span data-ttu-id="6db0a-157">Clients, auf denen frühere Versionen von .NET Framework ausgeführt werden nicht optimiert MSIL-Code aus der Binärdatei geladen.</span><span class="sxs-lookup"><span data-stu-id="6db0a-157">Clients that run previous .NET framework versions will load the non-optimized MSIL code from the binary.</span></span>

**<span data-ttu-id="6db0a-158">Q.</span><span class="sxs-lookup"><span data-stu-id="6db0a-158">Q.</span></span> <span data-ttu-id="6db0a-159">Wie kann ich melden Probleme oder Feedback senden?</span><span class="sxs-lookup"><span data-stu-id="6db0a-159">How can I provide feedback or report issues?</span></span>**

<span data-ttu-id="6db0a-160">A.</span><span class="sxs-lookup"><span data-stu-id="6db0a-160">A.</span></span> <span data-ttu-id="6db0a-161">Melden Sie ein Problem mit dem Feedback-Tool in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6db0a-161">Report an issue by using the Feedback tool in Visual Studio 2017.</span></span> <span data-ttu-id="6db0a-162">[Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="6db0a-162">[More information](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span></span>

**<span data-ttu-id="6db0a-163">Q.</span><span class="sxs-lookup"><span data-stu-id="6db0a-163">Q.</span></span> <span data-ttu-id="6db0a-164">Was ist die Auswirkung des Hinzufügens des systemeigenen Abbilds zu vorhandenen Binärdateien?</span><span class="sxs-lookup"><span data-stu-id="6db0a-164">What’s the impact of adding the native image to existing binaries?</span></span>**

<span data-ttu-id="6db0a-165">A.</span><span class="sxs-lookup"><span data-stu-id="6db0a-165">A.</span></span> <span data-ttu-id="6db0a-166">Optimierten Binärdateien enthalten verwalteten und systemeigenen Code, damit die endgültigen Dateien größer.</span><span class="sxs-lookup"><span data-stu-id="6db0a-166">The optimized binaries contain the managed and native code, making the final files greater.</span></span>

**<span data-ttu-id="6db0a-167">Q.</span><span class="sxs-lookup"><span data-stu-id="6db0a-167">Q.</span></span> <span data-ttu-id="6db0a-168">Kann mithilfe dieser Technologie Binärdateien werden freigegeben?</span><span class="sxs-lookup"><span data-stu-id="6db0a-168">Can I release binaries using this technology?</span></span>**

<span data-ttu-id="6db0a-169">A.</span><span class="sxs-lookup"><span data-stu-id="6db0a-169">A.</span></span> <span data-ttu-id="6db0a-170">Diese Version umfasst eine Go Live-Lizenz, die Sie heute verwenden können.</span><span class="sxs-lookup"><span data-stu-id="6db0a-170">This version includes a Go Live license that you can use today.</span></span>
