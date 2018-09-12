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
keywords: Windows 10 systemeigene Abbilder Compiler
ms.localizationpriority: medium
ms.openlocfilehash: d98b576fb51a8f9507802796ab359d0d00d21998
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3931120"
---
# <a name="optimize-your-net-desktop-apps-with-native-images"></a><span data-ttu-id="ab760-103">Optimieren Sie Ihre .NET Desktop-apps für systemeigene Abbilder</span><span class="sxs-lookup"><span data-stu-id="ab760-103">Optimize your .NET Desktop apps with native images</span></span>

> [!NOTE]
> <span data-ttu-id="ab760-104">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="ab760-104">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="ab760-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="ab760-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="ab760-106">Die Startzeit der.NET Framework-Anwendung können Sie die Binärdateien vorkompiliert verbessern.</span><span class="sxs-lookup"><span data-stu-id="ab760-106">You can improve the startup time of your .NET Framework application by pre-compiling your binaries.</span></span> <span data-ttu-id="ab760-107">Diese Technologie können für große Applikationen, die Sie packen und verteilen Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ab760-107">You can use this technology on large applications that you package and distribute through the Windows Store.</span></span> <span data-ttu-id="ab760-108">In einigen Fällen haben wir eine Leistungssteigerung von 20 % beobachtet.</span><span class="sxs-lookup"><span data-stu-id="ab760-108">In some cases, we've observed a 20% performance improvement.</span></span> <span data-ttu-id="ab760-109">Sie können diese Technologie in der [technischen Übersicht](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md)erfahren.</span><span class="sxs-lookup"><span data-stu-id="ab760-109">You can learn more about this technology in the [technical overview](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/readytorun-overview.md).</span></span>

<span data-ttu-id="ab760-110">Wir haben eine Vorschauversion des systemeigenen Abbilds Compiler als [NuGet-Paket](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler)veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="ab760-110">We've released a preview version of the native image compiler as a [NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.Framework.NativeImageCompiler).</span></span> <span data-ttu-id="ab760-111">Alle.NET Framework-Anwendung für.NET Framework Version 4.6.2 dieses Paket zuweisen oder höher.</span><span class="sxs-lookup"><span data-stu-id="ab760-111">You can apply this package to any .NET Framework application that targets the .NET Framework version 4.6.2 or later.</span></span> <span data-ttu-id="ab760-112">Dieses Paket fügt Buildschritt Post, der systemeigene Nutzlast, die von der Anwendung verwendeten Binärdateien enthält.</span><span class="sxs-lookup"><span data-stu-id="ab760-112">This package adds a post build step that includes a native payload to all the binaries used by your application.</span></span> <span data-ttu-id="ab760-113">Diese optimierte Nutzlast wird beim Ausführen der Anwendung in .NET 4.7.2 und höher Vorgängerversionen den MSIL-Code noch geladen werden geladen.</span><span class="sxs-lookup"><span data-stu-id="ab760-113">This optimized payload will be loaded when the application runs in .NET 4.7.2 and above while previous versions will still load the MSIL code.</span></span>

<span data-ttu-id="ab760-114">[.NET Framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) [10 April 2018 Windows update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/)gehört.</span><span class="sxs-lookup"><span data-stu-id="ab760-114">The [.NET framework 4.7.2](https://blogs.msdn.microsoft.com/dotnet/2018/04/30/announcing-the-net-framework-4-7-2/) is included in the [Windows 10 April 2018 update](https://blogs.windows.com/windowsexperience/2018/04/30/how-to-get-the-windows-10-april-2018-update/).</span></span> <span data-ttu-id="ab760-115">Sie können auch diese Version von.NET Framework auf PCs, die Windows 7 und Windows Server 2008 R2 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ab760-115">You can also install this version of the .NET Framework on PC's that run Windows 7+ and Windows Server 2008 R2+.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab760-116">Wenn systemeigene Bilder für die Anwendung von Windows Application Packaging-Projekt verpackt werden soll, müssen Sie Windows Jahrestag Update Ziel Plattform minimale Version des Projekts fest.</span><span class="sxs-lookup"><span data-stu-id="ab760-116">If you want to produce native images for your application packaged by  the Windows Application Packaging project, make sure to set the Target Platform Minimum version of the project to the Windows Anniversary Update.</span></span>

## <a name="how-to-produce-native-images"></a><span data-ttu-id="ab760-117">Wie systemeigene Bilder</span><span class="sxs-lookup"><span data-stu-id="ab760-117">How to produce native images</span></span>

<span data-ttu-id="ab760-118">Konfigurieren von Projekten, gehen Sie wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="ab760-118">Follow these instructions to configure your projects.</span></span>

1. <span data-ttu-id="ab760-119">Konfigurieren Sie das Zielframework 4.6.2 oder oben</span><span class="sxs-lookup"><span data-stu-id="ab760-119">Configure the target framework as 4.6.2 or above</span></span>

2. <span data-ttu-id="ab760-120">Konfigurieren Sie die Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="ab760-120">Configure the target platform as x86 or x64</span></span> 

3. <span data-ttu-id="ab760-121">NuGet-Pakete hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ab760-121">Add the NuGet packages.</span></span>

4. <span data-ttu-id="ab760-122">Erstellen Sie einen Versionsbuild.</span><span class="sxs-lookup"><span data-stu-id="ab760-122">Create a Release Build.</span></span>

## <a name="configure-the-target-framework-as-462-or-above"></a><span data-ttu-id="ab760-123">Konfigurieren Sie das Zielframework 4.6.2 oder oben</span><span class="sxs-lookup"><span data-stu-id="ab760-123">Configure the target framework as 4.6.2 or above</span></span>

<span data-ttu-id="ab760-124">Konfigurieren Sie das Projekt auf.NET Framework 4.6.2 benötigen Sie.NET Framework 4.6.2 Entwicklungstools oder höher.</span><span class="sxs-lookup"><span data-stu-id="ab760-124">To configure your project to target .NET Framework 4.6.2 you will need the .NET Framework 4.6.2 development tools or newer.</span></span> <span data-ttu-id="ab760-125">Diese Tools sind als optionale Komponenten Arbeitslast Desktopentwicklung .NET über Visual Studio Installer verfügbar:</span><span class="sxs-lookup"><span data-stu-id="ab760-125">These tools are available through the Visual Studio installer as optional components under the .NET desktop development workload:</span></span>

![Installieren Sie .NET 4.6.2 Entwicklungstools](images/desktop-to-uwp/install-4.6.2-devpack.png)

<span data-ttu-id="ab760-127">Alternativ erhalten Sie .NET Developer Packs aus:[https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span><span class="sxs-lookup"><span data-stu-id="ab760-127">Alternatively, you can get the .NET developer packs from: [https://www.microsoft.com/net/download/visual-studio-sdks](https://www.microsoft.com/net/download/visual-studio-sdks)</span></span>

## <a name="configure-the-target-platform-as-x86-or-x64"></a><span data-ttu-id="ab760-128">Konfigurieren Sie die Zielplattform als X86 oder x64</span><span class="sxs-lookup"><span data-stu-id="ab760-128">Configure the target platform as x86 or x64</span></span>

<span data-ttu-id="ab760-129">Systemeigene Abbilder Compiler optimiert den Code für eine bestimmte Plattform.</span><span class="sxs-lookup"><span data-stu-id="ab760-129">The native image compiler optimizes the code for a given platform.</span></span> <span data-ttu-id="ab760-130">Für die Verwendung müssen Sie Ihre Anwendung auf einer bestimmten Plattform wie X86 oder X64.</span><span class="sxs-lookup"><span data-stu-id="ab760-130">To use it, you need to configure your application to target one specific platform such as x86 or x64.</span></span>

<span data-ttu-id="ab760-131">Mehrere Projekte in der Projektmappe vorhanden sind, ist nur das Eintrag Punkt Projekt (höchstwahrscheinlich die, die eine ausführbare Datei erstellt) als X86 oder X64 kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="ab760-131">If you have multiple projects in your solution, only the entry point project (most likely the project that produces an executable file) has to be compiled as x86 or x64.</span></span> <span data-ttu-id="ab760-132">Zusätzliche Binärdateien aus dem Hauptprojekt verwiesen werden, wenn sie als AnyCPU kompiliert werden in das Hauptprojekt angegebene Architektur verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="ab760-132">Additional binaries referenced from the main project will be processed with the architecture specified in the main project, even if they are compiled as AnyCPU.</span></span>

<span data-ttu-id="ab760-133">So konfigurieren Sie das Projekt</span><span class="sxs-lookup"><span data-stu-id="ab760-133">To configure your project:</span></span>

1. <span data-ttu-id="ab760-134">Maustaste auf die Projektmappe und wählen Sie **Configuration Manager**.</span><span class="sxs-lookup"><span data-stu-id="ab760-134">Right-click your solution, and then select **Configuration Manager**.</span></span>

2. <span data-ttu-id="ab760-135">Wählen Sie **< neu... >** in der **Plattform** -Dropdown-Menü neben dem Namen des Projekts, das die ausführbare Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="ab760-135">Select **<New ..>** in the **Platform** dropdown menu beside the name of the project that produces your executable file.</span></span>

3. <span data-ttu-id="ab760-136">Klicken Sie im Dialogfeld **Neue Projektplattform** sicherstellen Sie, dass die Dropdownliste **Copy Settings from** **Any CPU**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ab760-136">In the **New Project Platform** dialog box, make sure that the **Copy Settings from** dropdown list is set to **Any CPU**.</span></span>

![X86 konfigurieren](images/desktop-to-uwp/configure-x86.png)

<span data-ttu-id="ab760-138">Wiederholen Sie diesen Schritt für `Release/x64` sollten X64 erzeugen Binärdateien.</span><span class="sxs-lookup"><span data-stu-id="ab760-138">Repeat this step for `Release/x64` if you want produce x64 binaries.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ab760-139">AnyCPU-Konfiguration wird vom Compiler systemeigene Abbilder nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ab760-139">AnyCPU configuration is not supported by the native image compiler.</span></span>

## <a name="add-the-nuget-packages"></a><span data-ttu-id="ab760-140">Hinzufügen von NuGet-Paketen</span><span class="sxs-lookup"><span data-stu-id="ab760-140">Add the NuGet packages</span></span>

<span data-ttu-id="ab760-141">Systemeigene Abbilder Compiler wird ein NuGet-Paket bereitgestellt, die Sie dem Visual Studio-Projekt hinzufügen, die ausführbare Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="ab760-141">The native image compiler is provided as a NuGet package that you need to add to the Visual Studio project that produces the executable file.</span></span> <span data-ttu-id="ab760-142">Dies ist in der Regel Windows Forms- oder WPF-Projekt.</span><span class="sxs-lookup"><span data-stu-id="ab760-142">This is typically your Windows Forms or WPF project.</span></span> <span data-ttu-id="ab760-143">Dieser Befehl PowerShell dazu.</span><span class="sxs-lookup"><span data-stu-id="ab760-143">Use this PowerShell command to do that.</span></span>

```PS
PM> Install-Package Microsoft.DotNet.Framework.NativeImageCompiler -Version 0.0.1-prerelease-00002  -PRE
```

> [!NOTE]
> <span data-ttu-id="ab760-144">Vorschau-Pakete werden in NuGet.org als veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="ab760-144">The preview packages are published in NuGet.org as unlisted.</span></span> <span data-ttu-id="ab760-145">Sie wird nicht durchsuchen NuGet.org oder Paket-Manager UI in Visual Studio finden.</span><span class="sxs-lookup"><span data-stu-id="ab760-145">You won’t find them by browsing NuGet.org or by using the Package Manager UI in Visual Studio.</span></span> <span data-ttu-id="ab760-146">Aber Sie können sie von der Konsole Paket-Manager und wenn Sie von einem anderen Computer wiederherstellen.</span><span class="sxs-lookup"><span data-stu-id="ab760-146">However, you can install them from the Package Manager Console, and when you restoring from a different machine.</span></span> <span data-ttu-id="ab760-147">Wir machen die Pakete barrierefrei beim ersten-Preview-Version veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="ab760-147">We'll make the packages fully accessible when we publish the first non-preview version.</span></span>

## <a name="create-a-release-build"></a><span data-ttu-id="ab760-148">Erstellen eines Releasebuilds</span><span class="sxs-lookup"><span data-stu-id="ab760-148">Create a Release Build</span></span>

<span data-ttu-id="ab760-149">NuGet-Paket konfiguriert das Projekt um ein zusätzliches Tool für Releasebuilds auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ab760-149">The NuGet package configures the project to run an additional tool for release builds.</span></span> <span data-ttu-id="ab760-150">Dieses Tool hinzugefügt dieselben Binärdateien systemeigenen Code.</span><span class="sxs-lookup"><span data-stu-id="ab760-150">This tool adds the native code to the same binaries.</span></span>
<span data-ttu-id="ab760-151">Um sicherzustellen, dass das Tool die Binärdateien verarbeitet hat können Sie überprüfen die Buildausgabe um sicherzustellen, dass eine Meldung wie diese enthält:</span><span class="sxs-lookup"><span data-stu-id="ab760-151">To verify that the tool has processed the binaries you can review the build output to make sure it includes a message such as this one:</span></span>

```
Native image obj\x86\Release\\R2R\DesktopApp1.exe generated successfully.
```

## <a name="faq"></a><span data-ttu-id="ab760-152">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="ab760-152">FAQ</span></span>

**<span data-ttu-id="ab760-153">Q.</span><span class="sxs-lookup"><span data-stu-id="ab760-153">Q.</span></span> <span data-ttu-id="ab760-154">Arbeiten die neuen Binärdateien ohne.NET Framework 4.7.2?</span><span class="sxs-lookup"><span data-stu-id="ab760-154">Do the new binaries work on machines without .NET Framework 4.7.2?</span></span>**

<span data-ttu-id="ab760-155">A.</span><span class="sxs-lookup"><span data-stu-id="ab760-155">A.</span></span> <span data-ttu-id="ab760-156">Optimierte Binärdateien Verbesserungen profitieren mit.NET Framework 4.7.2 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ab760-156">Optimized binaries will benefit from the improvements when running with .NET Framework 4.7.2.</span></span> <span data-ttu-id="ab760-157">Clients, die frühere Versionen von .NET Framework lädt nicht optimierten MSIL-Codes aus der Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="ab760-157">Clients that run previous .NET framework versions will load the non-optimized MSIL code from the binary.</span></span>

**<span data-ttu-id="ab760-158">Q.</span><span class="sxs-lookup"><span data-stu-id="ab760-158">Q.</span></span> <span data-ttu-id="ab760-159">Wie kann ich Feedback oder melden Probleme?</span><span class="sxs-lookup"><span data-stu-id="ab760-159">How can I provide feedback or report issues?</span></span>**

<span data-ttu-id="ab760-160">A.</span><span class="sxs-lookup"><span data-stu-id="ab760-160">A.</span></span> <span data-ttu-id="ab760-161">Melden Sie ein Problem mit dem Feedback-Tool in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ab760-161">Report an issue by using the Feedback tool in Visual Studio 2017.</span></span> <span data-ttu-id="ab760-162">[Weitere Informationen](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="ab760-162">[More information](https://docs.microsoft.com/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).</span></span>

**<span data-ttu-id="ab760-163">Q.</span><span class="sxs-lookup"><span data-stu-id="ab760-163">Q.</span></span> <span data-ttu-id="ab760-164">Wie wirkt bestehender Binärdateien des systemeigenen Abbilds hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="ab760-164">What’s the impact of adding the native image to existing binaries?</span></span>**

<span data-ttu-id="ab760-165">A.</span><span class="sxs-lookup"><span data-stu-id="ab760-165">A.</span></span> <span data-ttu-id="ab760-166">Optimierten Binärdateien enthalten den verwalteten und systemeigenen Code, machen die fertigen Dateien größer.</span><span class="sxs-lookup"><span data-stu-id="ab760-166">The optimized binaries contain the managed and native code, making the final files greater.</span></span>

**<span data-ttu-id="ab760-167">Q.</span><span class="sxs-lookup"><span data-stu-id="ab760-167">Q.</span></span> <span data-ttu-id="ab760-168">Können diese Technologie Binärdateien freigeben?</span><span class="sxs-lookup"><span data-stu-id="ab760-168">Can I release binaries using this technology?</span></span>**

<span data-ttu-id="ab760-169">A.</span><span class="sxs-lookup"><span data-stu-id="ab760-169">A.</span></span> <span data-ttu-id="ab760-170">Diese Version enthält eine Go Live Lizenz, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ab760-170">This version includes a Go Live license that you can use today.</span></span>
