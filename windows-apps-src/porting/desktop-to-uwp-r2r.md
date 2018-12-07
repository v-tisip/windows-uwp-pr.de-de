---
Description: This guide explains how to configure your Visual Studio Solution to optimize the application binaries with native images.
Search.Product: eADQiWindows 10XVcnh
title: Optimieren Sie Ihre .NET Desktop-apps mit systemeigene Abbildern
ms.date: 06/11/2018
ms.topic: article
keywords: Windows 10, systemeigenen Images Compiler
ms.localizationpriority: medium
ms.openlocfilehash: 3071b843a1605d765ab5b087d5e1bfb96a220218
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8786548"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a><span data-ttu-id="aa12e-103">Optimieren Sie Ihre .NET Desktop-apps mit systemeigene Abbildern</span><span class="sxs-lookup"><span data-stu-id="aa12e-103">Optimize your .NET Desktop apps with native images</span></span>

> [!NOTE]
> <span data-ttu-id="aa12e-104">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-104">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="aa12e-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="aa12e-106">Sie können die Startzeit Ihrer .NET Framework-Anwendung verbessern, indem Sie die Binärdateien vorkompiliert.</span><span class="sxs-lookup"><span data-stu-id="aa12e-106">You can improve the startup time of your .NET Framework application by pre-compiling your binaries.</span></span> <span data-ttu-id="aa12e-107">Sie können diese Technologie auf großen Anwendungen verwenden, die Sie verpacken und über den Microsoft Store verteilen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-107">You can use this technology on large applications that you package and distribute through the Microsoft Store.</span></span> <span data-ttu-id="aa12e-108">In einigen Fällen haben wir eine 20 % Leistungssteigerung ermittelt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-108">In some cases, we've observed a 20% performance improvement.</span></span> <span data-ttu-id="aa12e-109">Hier erfahren Sie mehr über diese Technologie in die [Technische Übersicht](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aa12e-109">You can learn more about this technology in the [technical overview](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).</span></span>

<span data-ttu-id="aa12e-110">Wir haben eine Vorschauversion von der systemeigenen Images Compiler als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="aa12e-110">We've released a preview version of the native image compiler as a [NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler).</span></span> <span data-ttu-id="aa12e-111">Sie können dieses Paket auf jede .NET Framework-Anwendung, die das .NET Framework-Version 4.6.2 ausgerichtet ist anwenden oder höher.</span><span class="sxs-lookup"><span data-stu-id="aa12e-111">You can apply this package to any .NET Framework application that targets the .NET Framework version 4.6.2 or later.</span></span> <span data-ttu-id="aa12e-112">Dieses Paket Fügt einen Post-Buildschritt, der auf die Binärdateien, die von der Anwendung verwendet eine native Nutzlast enthält.</span><span class="sxs-lookup"><span data-stu-id="aa12e-112">This package adds a post build step that includes a native payload to all the binaries used by your application.</span></span> <span data-ttu-id="aa12e-113">-Nutzlast dieser optimierten wird geladen werden, wenn die Anwendung in .NET 4.7.2 und höher ausführt, während den MSIL-Code weiterhin in frühere Versionen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="aa12e-113">This optimized payload will be loaded when the application runs in .NET 4.7.2 and above while previous versions will still load the MSIL code.</span></span>

<span data-ttu-id="aa12e-114">Das [.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) ist in der [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)enthalten.</span><span class="sxs-lookup"><span data-stu-id="aa12e-114">The [.NET framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) is included in the [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/).</span></span> <span data-ttu-id="aa12e-115">Sie können diese Version von .NET Framework auch auf PCs installieren, auf denen Windows 7 + und Windows Server 2008 R2 oder höher ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-115">You can also install this version of the .NET Framework on PC's that run Windows 7+ and Windows Server 2008 R2+.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa12e-116">Wenn Sie systemeigene Abbilder für Ihre Anwendung verpackt, die Windows Application Packaging-Projekt erstellen möchten, stellen Sie sicher, die Ziel-Plattform mindestens erforderliche Version des Projekts auf das Windows Anniversary Update festlegen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-116">If you want to produce native images for your application packaged by  the Windows Application Packaging project, make sure to set the Target Platform Minimum version of the project to the Windows Anniversary Update.</span></span>

## <a name="how-to-produce-native-images"></a><span data-ttu-id="aa12e-117">Wie Sie systemeigene Abbilder zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-117">How to produce native images</span></span>

<span data-ttu-id="aa12e-118">Konfigurieren von Projekten, gehen Sie wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="aa12e-118">Follow these instructions to configure your projects.</span></span>

1. <span data-ttu-id="aa12e-119">Konfigurieren Sie die Zielframework als 4.6.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="aa12e-119">Configure the target framework as 4.6.2 or above</span></span>

2. <span data-ttu-id="aa12e-120">Konfigurieren Sie die Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="aa12e-120">Configure the target platform as x86 or x64</span></span> 

3. <span data-ttu-id="aa12e-121">Fügen Sie den NuGet-Pakete.</span><span class="sxs-lookup"><span data-stu-id="aa12e-121">Add the NuGet packages.</span></span>

4. <span data-ttu-id="aa12e-122">Erstellen Sie einen Versionsbuild.</span><span class="sxs-lookup"><span data-stu-id="aa12e-122">Create a Release Build.</span></span>

## <a name="configure-the-target-framework-as-462-or-above"></a><span data-ttu-id="aa12e-123">Konfigurieren Sie die Zielframework als 4.6.2 oder höher</span><span class="sxs-lookup"><span data-stu-id="aa12e-123">Configure the target framework as 4.6.2 or above</span></span>

<span data-ttu-id="aa12e-124">Zum Konfigurieren des Projekts .NET Framework 4.6.2 Ziel benötigen Sie die Entwicklungstools für .NET Framework 4.6.2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="aa12e-124">To configure your project to target .NET Framework 4.6.2 you will need the .NET Framework 4.6.2 development tools or newer.</span></span> <span data-ttu-id="aa12e-125">Diese Tools sind als optionale Komponenten unter der .NET desktop-Entwicklung Workload durch den Visual Studio-Installer verfügbar:</span><span class="sxs-lookup"><span data-stu-id="aa12e-125">These tools are available through the Visual Studio installer as optional components under the .NET desktop development workload:</span></span>

![Installieren Sie .NET 4.6.2 Entwicklungstools](images/desktop-to-uwp/install-4.6.2-devpack.png)

<span data-ttu-id="aa12e-127">Alternativ können Sie die .NET Entwickler Packs von abrufen:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span><span class="sxs-lookup"><span data-stu-id="aa12e-127">Alternatively, you can get the .NET developer packs from: [https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span></span>

## <a name="configure-the-target-platform-as-x86-or-x64"></a><span data-ttu-id="aa12e-128">Konfigurieren Sie die Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="aa12e-128">Configure the target platform as x86 or x64</span></span>

<span data-ttu-id="aa12e-129">Die systemeigene Bild-Compiler optimiert den Code für eine bestimmte Plattform.</span><span class="sxs-lookup"><span data-stu-id="aa12e-129">The native image compiler optimizes the code for a given platform.</span></span> <span data-ttu-id="aa12e-130">Um es zu verwenden, müssen Sie Ihre Anwendung an eine bestimmte Plattform z. B. X86 oder X64 konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="aa12e-130">To use it, you need to configure your application to target one specific platform such as x86 or x64.</span></span>

<span data-ttu-id="aa12e-131">Wenn Sie die Projektmappe mehrere Projekte enthält, muss nur der Eintrag Punkt Projekt (wahrscheinlich das Projekt, das eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="aa12e-131">If you have multiple projects in your solution, only the entry point project (most likely the project that produces an executable file) has to be compiled as x86 or x64.</span></span> <span data-ttu-id="aa12e-132">Zusätzliche Binärdateien, die von der Haupt-Projekt verwiesen werden mit der im Hauptprojekt angegebenen Architektur verarbeitet werden, auch wenn sie als "anycpu" kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="aa12e-132">Additional binaries referenced from the main project will be processed with the architecture specified in the main project, even if they are compiled as AnyCPU.</span></span>

<span data-ttu-id="aa12e-133">So konfigurieren Sie Ihr Projekt:</span><span class="sxs-lookup"><span data-stu-id="aa12e-133">To configure your project:</span></span>

1. <span data-ttu-id="aa12e-134">Mit der rechten Maustaste in der Projektmappe, und wählen Sie dann die **Configuration Manager**.</span><span class="sxs-lookup"><span data-stu-id="aa12e-134">Right-click your solution, and then select **Configuration Manager**.</span></span>

2. <span data-ttu-id="aa12e-135">Wählen Sie **<New. >** im Dropdownmenü **Plattform** neben dem Namen des Projekts, das die ausführbare Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-135">Select **<New ..>** in the **Platform** dropdown menu beside the name of the project that produces your executable file.</span></span>

3. <span data-ttu-id="aa12e-136">Das Dialogfeld **Neues Projektplattform** stellen Sie sicher, dass die **Kopie Einstellungen aus** Dropdown-Liste auf **Any CPU**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="aa12e-136">In the **New Project Platform** dialog box, make sure that the **Copy Settings from** dropdown list is set to **Any CPU**.</span></span>

![Konfigurieren von x86](images/desktop-to-uwp/configure-x86.png)

<span data-ttu-id="aa12e-138">Wiederholen Sie diesen Schritt für `Release/x64` Wenn Sie X64 erzeugen möchten Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="aa12e-138">Repeat this step for `Release/x64` if you want produce x64 binaries.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="aa12e-139">AnyCPU-Konfiguration wird vom Compiler systemeigene Bild nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-139">AnyCPU configuration is not supported by the native image compiler.</span></span>

## <a name="add-the-nuget-packages"></a><span data-ttu-id="aa12e-140">Fügen Sie das NuGet-Pakete</span><span class="sxs-lookup"><span data-stu-id="aa12e-140">Add the NuGet packages</span></span>

<span data-ttu-id="aa12e-141">Der Compiler systemeigenes Bild wird als NuGet-Paket bereitgestellt, die Sie benötigen Visual Studio-Projekt hinzu, die die ausführbare Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-141">The native image compiler is provided as a NuGet package that you need to add to the Visual Studio project that produces the executable file.</span></span> <span data-ttu-id="aa12e-142">Dies ist in der Regel Ihre Windows Forms- oder WPF-Projekt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-142">This is typically your Windows Forms or WPF project.</span></span> <span data-ttu-id="aa12e-143">Verwenden Sie diese PowerShell-Befehl, dafür.</span><span class="sxs-lookup"><span data-stu-id="aa12e-143">Use this PowerShell command to do that.</span></span>

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> <span data-ttu-id="aa12e-144">Die Vorschau-Pakete werden in "NuGet.org" als nicht aufgeführten veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="aa12e-144">The preview packages are published in NuGet.org as unlisted.</span></span> <span data-ttu-id="aa12e-145">Sie wird nicht durchsuchen "NuGet.org" oder mithilfe der UI-Paket-Manager in Visual Studio finden.</span><span class="sxs-lookup"><span data-stu-id="aa12e-145">You won’t find them by browsing NuGet.org or by using the Package Manager UI in Visual Studio.</span></span> <span data-ttu-id="aa12e-146">Sie können jedoch installieren sie die Paket-Manager-Konsole und wann Sie von einem anderen Computer wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-146">However, you can install them from the Package Manager Console, and when you restoring from a different machine.</span></span> <span data-ttu-id="aa12e-147">Wir verwenden die Pakete vollständig erstellen, wenn wir die erste nicht Preview-Version veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-147">We'll make the packages fully accessible when we publish the first non-preview version.</span></span>

## <a name="create-a-release-build"></a><span data-ttu-id="aa12e-148">Erstellen eines Releasebuilds</span><span class="sxs-lookup"><span data-stu-id="aa12e-148">Create a Release Build</span></span>

<span data-ttu-id="aa12e-149">Das NuGet-Paket konfiguriert das Projekt, um ein zusätzliches Tool für Release-Builds ausführen.</span><span class="sxs-lookup"><span data-stu-id="aa12e-149">The NuGet package configures the project to run an additional tool for release builds.</span></span> <span data-ttu-id="aa12e-150">Dieses Tool hinzugefügt die gleichen Binärdateien systemeigenen Code.</span><span class="sxs-lookup"><span data-stu-id="aa12e-150">This tool adds the native code to the same binaries.</span></span>
<span data-ttu-id="aa12e-151">Um sicherzustellen, dass das Tool die Binärdateien verarbeitet hat können Sie überprüfen, den Build-Ausgabe um sicherzustellen, dass es sich um eine Nachricht wie dieses enthält:</span><span class="sxs-lookup"><span data-stu-id="aa12e-151">To verify that the tool has processed the binaries you can review the build output to make sure it includes a message such as this one:</span></span>

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a><span data-ttu-id="aa12e-152">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="aa12e-152">FAQ</span></span>

**<span data-ttu-id="aa12e-153">Q.</span><span class="sxs-lookup"><span data-stu-id="aa12e-153">Q.</span></span> <span data-ttu-id="aa12e-154">Funktionieren die neuen Binärdateien auf Computern ohne .NET Framework 4.7.2?</span><span class="sxs-lookup"><span data-stu-id="aa12e-154">Do the new binaries work on machines without .NET Framework 4.7.2?</span></span>**

<span data-ttu-id="aa12e-155">A.</span><span class="sxs-lookup"><span data-stu-id="aa12e-155">A.</span></span> <span data-ttu-id="aa12e-156">Optimierte Binärdateien werden von Verbesserungen profitieren, wenn mit .NET Framework 4.7.2 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="aa12e-156">Optimized binaries will benefit from the improvements when running with .NET Framework 4.7.2.</span></span> <span data-ttu-id="aa12e-157">Clients unter früheren Versionen von .NET Framework lädt die MSIL-Code nicht optimierten aus der Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="aa12e-157">Clients that run previous .NET framework versions will load the non-optimized MSIL code from the binary.</span></span>

**<span data-ttu-id="aa12e-158">Q.</span><span class="sxs-lookup"><span data-stu-id="aa12e-158">Q.</span></span> <span data-ttu-id="aa12e-159">Wie kann ich Feedback oder melden Probleme?</span><span class="sxs-lookup"><span data-stu-id="aa12e-159">How can I provide feedback or report issues?</span></span>**

<span data-ttu-id="aa12e-160">A.</span><span class="sxs-lookup"><span data-stu-id="aa12e-160">A.</span></span> <span data-ttu-id="aa12e-161">Melden eines Problems mit dem Feedback-Tool in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="aa12e-161">Report an issue by using the Feedback tool in Visual Studio 2017.</span></span> <span data-ttu-id="aa12e-162">[Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="aa12e-162">[More information](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span></span>

**<span data-ttu-id="aa12e-163">Q.</span><span class="sxs-lookup"><span data-stu-id="aa12e-163">Q.</span></span> <span data-ttu-id="aa12e-164">Was ist die Auswirkung der vorhandenen Binärdateien das systemeigene Bild hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="aa12e-164">What’s the impact of adding the native image to existing binaries?</span></span>**

<span data-ttu-id="aa12e-165">A.</span><span class="sxs-lookup"><span data-stu-id="aa12e-165">A.</span></span> <span data-ttu-id="aa12e-166">Die optimierten Binärdateien enthalten die verwalteten und systemeigenen Code, damit die endgültigen Dateien größer.</span><span class="sxs-lookup"><span data-stu-id="aa12e-166">The optimized binaries contain the managed and native code, making the final files greater.</span></span>

**<span data-ttu-id="aa12e-167">Q.</span><span class="sxs-lookup"><span data-stu-id="aa12e-167">Q.</span></span> <span data-ttu-id="aa12e-168">Kann mit dieser Technologie Binärdateien werden freigegeben?</span><span class="sxs-lookup"><span data-stu-id="aa12e-168">Can I release binaries using this technology?</span></span>**

<span data-ttu-id="aa12e-169">A.</span><span class="sxs-lookup"><span data-stu-id="aa12e-169">A.</span></span> <span data-ttu-id="aa12e-170">Diese Version enthält eine wechseln Sie Live-Lizenz, die Sie heute verwenden können.</span><span class="sxs-lookup"><span data-stu-id="aa12e-170">This version includes a Go Live license that you can use today.</span></span>
