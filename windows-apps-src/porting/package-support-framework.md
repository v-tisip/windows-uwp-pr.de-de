---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben Sie, der Desktop-Anwendung ausführen in einem Container MSIX verhindern
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2815512"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a><span data-ttu-id="93a20-103">Wenden Sie Runtime-Updates mithilfe der Support-Paket MSIX Paket an</span><span class="sxs-lookup"><span data-stu-id="93a20-103">Apply runtime fixes to an MSIX package by using the Package Support Framework</span></span>

<span data-ttu-id="93a20-104">Der Support-Paket ist eine open-Source-Kit, das Anwenden von Updates der vorhandene Win32-Anwendung beim Zugriff auf den Quellcode haben, damit sie in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-104">The Package Support Framework is an open source kit that helps you apply fixes to your existing win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="93a20-105">Der Support-Paket kann eine Anwendung die optimalen Vorgehensweisen von moderne Runtime Environment.</span><span class="sxs-lookup"><span data-stu-id="93a20-105">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

<span data-ttu-id="93a20-106">Erstellen Sie das Paket Förderkonzept nutzten wir [Umwege](https://www.microsoft.com/en-us/research/project/detours) -Technologie ist ein open-Source-Framework entwickelt von Microsoft Research (MSR) und API-Umleitung und verknüpfen kann.</span><span class="sxs-lookup"><span data-stu-id="93a20-106">To create the Package Support Framework, we leveraged the [Detours](https://www.microsoft.com/en-us/research/project/detours) technology which is an open source framework developed by Microsoft Research (MSR) and helps with API redirection and hooking.</span></span>

<span data-ttu-id="93a20-107">Dieses Framework ist leicht, open Source und können diese Anwendung Probleme schnell.</span><span class="sxs-lookup"><span data-stu-id="93a20-107">This framework is open source, lightweight, and you can use it to address application issues quickly.</span></span> <span data-ttu-id="93a20-108">Es gibt Ihnen außerdem die Möglichkeit mit der Gemeinschaft weltweit und auf die Investitionen von anderen aufbauen.</span><span class="sxs-lookup"><span data-stu-id="93a20-108">It also gives you the opportunity to consult with the community around the globe, and to build on top of the investments of others.</span></span>

## <a name="a-quick-look-inside-of-the-package-support-framework"></a><span data-ttu-id="93a20-109">Ein kurzer Blick in der Support-Paket</span><span class="sxs-lookup"><span data-stu-id="93a20-109">A quick look inside of the Package Support Framework</span></span>

<span data-ttu-id="93a20-110">Der Support-Paket enthält eine ausführbare Datei, Laufzeit-Manager-DLL und eine Reihe von Common Language Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="93a20-110">The Package Support Framework contains an executable, a runtime manager  DLL, and a set of runtime fixes.</span></span>

![Paket Rahmen](images/desktop-to-uwp/package-support-framework.png)

<span data-ttu-id="93a20-112">So funktioniert’s.</span><span class="sxs-lookup"><span data-stu-id="93a20-112">Here's how it works.</span></span> <span data-ttu-id="93a20-113">Sie erstellen eine Konfigurationsdatei, die die Fix(s) angibt, die auf die Anwendung angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="93a20-113">You'll create a configuration file that specifies the fix(s) that you want to apply to your application.</span></span> <span data-ttu-id="93a20-114">Anschließend wird das Paket auf die Shim-Start ausführbare Datei ändern.</span><span class="sxs-lookup"><span data-stu-id="93a20-114">Then, you'll modify your package to point to the shim launcher executable file.</span></span>

<span data-ttu-id="93a20-115">Wenn Benutzer die Anwendung starten, ist das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-115">When users start your application, the shim launcher is the first executable that runs.</span></span> <span data-ttu-id="93a20-116">Liest die Konfigurationsdatei und fügt Fix(s) Runtime und den Laufzeit-Manager DLL in den Anwendungsprozess.</span><span class="sxs-lookup"><span data-stu-id="93a20-116">It reads your configuration file, and injects the runtime fix(s) and the runtime manager  DLL into the application process.</span></span>

![Paket Support Framework DLL-Injektion](images/desktop-to-uwp/package-support-framework-2.png)

<span data-ttu-id="93a20-118">Laufzeit-Manager gilt das Update bei Bedarf von der Anwendung in einem MSIX-Container ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="93a20-118">The runtime manager applies the fix when it's needed by the application to run inside of an MSIX container.</span></span>

<span data-ttu-id="93a20-119">Dieses Handbuch hilft Ihnen beim Identifizieren von Problemen mit der Anwendungskompatibilität und zu finden, anwenden und erweitern Runtime behebt, die sie behandeln.</span><span class="sxs-lookup"><span data-stu-id="93a20-119">This guide will help you to identify application compatibility issues, and to find, apply, and extend runtime fixes that address them.</span></span>

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a><span data-ttu-id="93a20-120">Gepackte Anwendungskompatibilitätsprobleme identifizieren</span><span class="sxs-lookup"><span data-stu-id="93a20-120">Identify packaged application compatibility issues</span></span>

<span data-ttu-id="93a20-121">Erstellen Sie zunächst ein Paket für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-121">First, create a package for your application.</span></span> <span data-ttu-id="93a20-122">Anschließend installieren, ausführen und beobachten.</span><span class="sxs-lookup"><span data-stu-id="93a20-122">Then, install it, run it, and observe its behavior.</span></span> <span data-ttu-id="93a20-123">Sie möglicherweise Fehlermeldungen, die ein Kompatibilitätsproblem erleichtern.</span><span class="sxs-lookup"><span data-stu-id="93a20-123">You might receive error messages that can help you identify a compatibility issue.</span></span> <span data-ttu-id="93a20-124">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) können Sie Probleme identifizieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-124">You can also use [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) to identify issues.</span></span>  <span data-ttu-id="93a20-125">Probleme beziehen sich auf Anwendung Annahmen bezüglich arbeiten Berechtigungen für die Verzeichnisse und Programm-Pfad.</span><span class="sxs-lookup"><span data-stu-id="93a20-125">Common issues relate to application assumptions regarding the working directory and program path permissions.</span></span>

### <a name="using-process-monitor-to-identify-an-issue"></a><span data-ttu-id="93a20-126">Mithilfe von Process Monitor ein Problem identifizieren</span><span class="sxs-lookup"><span data-stu-id="93a20-126">Using Process Monitor to identify an issue</span></span>

<span data-ttu-id="93a20-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm eine app-Datei und Registrierungsvorgängen, und ihre Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="93a20-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) is a powerful utility for observing an app's file and registry operations, and their results.</span></span>  <span data-ttu-id="93a20-128">Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="93a20-128">This can help you to understand application compatibility issues.</span></span>  <span data-ttu-id="93a20-129">Process Monitor öffnen, fügen Sie einen Filter (Filter > Filter...) auf nur Ereignisse von ausführbaren Datei der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-129">After opening Process Monitor, add a filter (Filter > Filter…) to include only events from the application executable.</span></span>

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

<span data-ttu-id="93a20-131">Eine Liste der Ereignisse wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a20-131">A list of events will appear.</span></span> <span data-ttu-id="93a20-132">Für viele dieser Ereignisse wird das Wort **Erfolg** in **der Ergebnisspalte** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a20-132">For many of these events, the word **SUCCESS** will appear in the **Result** column.</span></span>

![ProcMon Ereignisse](images/desktop-to-uwp/procmon_events.png)

<span data-ttu-id="93a20-134">Optional können Sie Ereignisse, um nur Fehler nur filtern.</span><span class="sxs-lookup"><span data-stu-id="93a20-134">Optionally, you can filter events to only show only failures.</span></span>

![Erfolgreiche ProcMon ausschließen](images/desktop-to-uwp/procmon_exclude_success.png)

<span data-ttu-id="93a20-136">Wenn einen Dateisystem Zugriffsfehler vermuten, fehlgeschlagenen Ereignisse System32/SysWOW64 oder Paketdateipfad suchen.</span><span class="sxs-lookup"><span data-stu-id="93a20-136">If you suspect a filesystem access failure, search for failed events that are under either the System32/SysWOW64 or the package file path.</span></span> <span data-ttu-id="93a20-137">Filter können auch hier zu helfen.</span><span class="sxs-lookup"><span data-stu-id="93a20-137">Filters can also help here, too.</span></span> <span data-ttu-id="93a20-138">Am Ende dieser Liste starten, und führen Sie einen Bildlauf nach oben.</span><span class="sxs-lookup"><span data-stu-id="93a20-138">Start at the bottom of this list and scroll upwards.</span></span> <span data-ttu-id="93a20-139">Fehler am Ende dieser Liste erscheinen zuletzt aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="93a20-139">Failures that appear at the bottom of this list have occurred most recently.</span></span> <span data-ttu-id="93a20-140">Die meisten achten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" und "Pfad/Name nicht gefunden" und was verdächtig nicht ignorieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-140">Pay most attention to errors that contain strings such as "access denied," and "path/name not found", and ignore things that don't look suspicious.</span></span> <span data-ttu-id="93a20-141">[PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme.</span><span class="sxs-lookup"><span data-stu-id="93a20-141">The [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) has two issues.</span></span> <span data-ttu-id="93a20-142">Diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a20-142">You can see those issues in the list that appears in the following image.</span></span>

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

<span data-ttu-id="93a20-144">Das erste Problem, das in diesem Bild angezeigt wird, wird die Anwendung nicht die Datei "config.txt" gelesen, die im Pfad "C:\Windows\SysWOW64" befindet.</span><span class="sxs-lookup"><span data-stu-id="93a20-144">In the first issue that appears in this image, the application is failing to read from the "Config.txt" file that is located in the "C:\Windows\SysWOW64" path.</span></span> <span data-ttu-id="93a20-145">Es ist unwahrscheinlich, dass die Anwendung diesen Pfad direkt verweisen.</span><span class="sxs-lookup"><span data-stu-id="93a20-145">It's unlikely that the application is trying to reference that path directly.</span></span> <span data-ttu-id="93a20-146">Wahrscheinlich versucht, die Datei mithilfe eines relativen Pfads gelesen und "System32/SysWOW64" wird standardmäßig Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-146">Most likely, it's trying to read from that file by using a relative path, and by default, "System32/SysWOW64" is the application's working directory.</span></span> <span data-ttu-id="93a20-147">Dies ist die Anwendung der aktuellen Arbeitsverzeichnis irgendwo im Paket festgelegt werden, erwartet.</span><span class="sxs-lookup"><span data-stu-id="93a20-147">This suggests that the application is expecting its current working directory to be set to somewhere in the package.</span></span> <span data-ttu-id="93a20-148">In der Anlage sehen, wir, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="93a20-148">Looking inside of the appx, we can see that the file exists in the same directory as the executable.</span></span>

![App Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

<span data-ttu-id="93a20-150">Das zweite Problem wird in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93a20-150">The second issue appears in the following image.</span></span>

![ProcMon-Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

<span data-ttu-id="93a20-152">Dieses Problem ist die Anwendung nicht in der Paketpfad eine log-Datei schreiben.</span><span class="sxs-lookup"><span data-stu-id="93a20-152">In this issue, the application is failing to write a .log file to its package path.</span></span> <span data-ttu-id="93a20-153">Denke, dass ein Datei Umleitung Shim unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="93a20-153">This would suggest that a file redirection shim might help.</span></span>

<a id="find" />

## <a name="find-a-runtime-fix"></a><span data-ttu-id="93a20-154">Suchen nach einer Laufzeit-Lösung</span><span class="sxs-lookup"><span data-stu-id="93a20-154">Find a runtime fix</span></span>

<span data-ttu-id="93a20-155">Die PSF behebt Laufzeit, mit denen Sie, wie die Datei Umleitung Shim.</span><span class="sxs-lookup"><span data-stu-id="93a20-155">The PSF contains runtime fixes that you can use right now, such as the file redirection shim.</span></span>

### <a name="file-redirection-shim"></a><span data-ttu-id="93a20-156">Umleitung Shim-Datei</span><span class="sxs-lookup"><span data-stu-id="93a20-156">File Redirection Shim</span></span>

<span data-ttu-id="93a20-157">[Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten möchte schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung ist, die in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-157">You can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to redirect attempts to write or read data in a directory that isn't accessible from an application that runs in an MSIX container.</span></span>

<span data-ttu-id="93a20-158">Z. B. wenn die Anwendung in eine Protokolldatei schreibt, die im gleichen Verzeichnis wie die ausführbare Anwendung können dann [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie die Protokolldatei an einem anderen Standort, wie lokale app-Datenspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="93a20-158">For example, if your application writes to a log file that is in the same directory as your applications executable, then you can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to create that log file in another location, such as the local app data store.</span></span>

### <a name="runtime-fixes-from-the-community"></a><span data-ttu-id="93a20-159">Runtime-Updates aus der community</span><span class="sxs-lookup"><span data-stu-id="93a20-159">Runtime fixes from the community</span></span>

<span data-ttu-id="93a20-160">Überprüfen Sie die Beiträge der Community [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) Seite.</span><span class="sxs-lookup"><span data-stu-id="93a20-160">Make sure to review the community contributions to our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) page.</span></span> <span data-ttu-id="93a20-161">Es ist möglich, dass andere Entwickler einen ähnlichen Problem gelöst haben und ein Runtime-Update freigegeben haben.</span><span class="sxs-lookup"><span data-stu-id="93a20-161">It's possible that other developers have resolved an issue similar to yours and have shared a runtime fix.</span></span>

## <a name="apply-a-runtime-fix"></a><span data-ttu-id="93a20-162">Runtime Hotfix</span><span class="sxs-lookup"><span data-stu-id="93a20-162">Apply a runtime fix</span></span>

<span data-ttu-id="93a20-163">Sie können eine vorhandene Runtime einige einfache Tools aus dem Windows SDK und folgendermaßen Updates.</span><span class="sxs-lookup"><span data-stu-id="93a20-163">You can apply an existing runtime fix with a few simple tools from the Windows SDK, and by following these steps.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="93a20-164">Erstellen Sie einen Ordner Paket layout</span><span class="sxs-lookup"><span data-stu-id="93a20-164">Create a package layout folder</span></span>
> * <span data-ttu-id="93a20-165">Paket Rahmen Dateien</span><span class="sxs-lookup"><span data-stu-id="93a20-165">Get the Package Support Framework files</span></span>
> * <span data-ttu-id="93a20-166">Dem Paket hinzufügen</span><span class="sxs-lookup"><span data-stu-id="93a20-166">Add them to your package</span></span>
> * <span data-ttu-id="93a20-167">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="93a20-167">Modify the package manifest</span></span>
> * <span data-ttu-id="93a20-168">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="93a20-168">Create a configuration file</span></span>

<span data-ttu-id="93a20-169">Lassen Sie uns jeder Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="93a20-169">Let's go through each task.</span></span>

### <a name="create-the-package-layout-folder"></a><span data-ttu-id="93a20-170">Den Paketordner Layout erstellen</span><span class="sxs-lookup"><span data-stu-id="93a20-170">Create the package layout folder</span></span>

<span data-ttu-id="93a20-171">Wenn noch eine .appx-Datei können Sie den Inhalt in einem Layout Ordner entpacken, die als Stagingbereich für das Paket verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-171">If you have a .appx file already, you can unpack its contents into a layout folder that will serve as the staging area for your package.</span></span>  <span data-ttu-id="93a20-172">Dazu aus einer **X64 systemeigenen Tools Befehlszeile VS 2017**, oder manuell mit den SDK-Bin-Pfad in den Suchpfad für ausführbare.</span><span class="sxs-lookup"><span data-stu-id="93a20-172">You can do this from an **x64 Native Tools Command Prompt for VS 2017**, or manually with the SDK bin path in the executable search path.</span></span>

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

<span data-ttu-id="93a20-173">Dies wird Ihnen etwas, das wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="93a20-173">This will give you something that looks like the following.</span></span>

![Bildpaket-Layout](images/desktop-to-uwp/package_contents.png)

<span data-ttu-id="93a20-175">Haben Sie eine .appx-Datei beginnen, können Sie Paketordner und Dateien von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="93a20-175">If you don't have a .appx file to start with, you can create the package folder and files from scratch.</span></span>

### <a name="get-the-package-support-framework-files"></a><span data-ttu-id="93a20-176">Paket Rahmen Dateien</span><span class="sxs-lookup"><span data-stu-id="93a20-176">Get the Package Support Framework files</span></span>

<span data-ttu-id="93a20-177">PSF Nuget-Paket erhalten mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93a20-177">You can get the PSF Nuget package by using Visual Studio.</span></span> <span data-ttu-id="93a20-178">Außerdem erhalten sie mit eigenständigen Nuget-Befehlszeilentool.</span><span class="sxs-lookup"><span data-stu-id="93a20-178">You can also get it by using the standalone Nuget command line tool.</span></span>

#### <a name="get-the-package-by-using-visual-studio"></a><span data-ttu-id="93a20-179">Abrufen des Pakets mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93a20-179">Get the package by using Visual Studio</span></span>

<span data-ttu-id="93a20-180">In Visual Studio mit der rechten Maustaste des Knotens Projektmappe oder ein Projekt und wählen Befehle Nuget-Pakete verwalten.</span><span class="sxs-lookup"><span data-stu-id="93a20-180">In Visual Studio, right-click your solution or project node and pick one of the Manage Nuget Packages commands.</span></span>  <span data-ttu-id="93a20-181">Suche nach **Microsoft.PackageSupportFramework** oder **PSF** Paket unter "NuGet.org" suchen. Installieren Sie es anschließend.</span><span class="sxs-lookup"><span data-stu-id="93a20-181">Search for **Microsoft.PackageSupportFramework** or **PSF** to find the package on Nuget.org. Then, install it.</span></span>

#### <a name="get-the-package-by-using-the-command-line-tool"></a><span data-ttu-id="93a20-182">Rufen Sie das Paket mit dem Befehlszeilenprogramm ab</span><span class="sxs-lookup"><span data-stu-id="93a20-182">Get the package by using the command line tool</span></span>

<span data-ttu-id="93a20-183">Das Nuget-Befehlszeilentool von diesem Speicherort aus installieren: https://www.nuget.org/downloads.</span><span class="sxs-lookup"><span data-stu-id="93a20-183">Install the Nuget command line tool from this location: https://www.nuget.org/downloads.</span></span> <span data-ttu-id="93a20-184">Führen Sie dann über die Befehlszeile Nuget Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="93a20-184">Then, from the Nuget command line, run this command:</span></span>

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a><span data-ttu-id="93a20-185">Rahmen-Paket das Paket hinzufügen</span><span class="sxs-lookup"><span data-stu-id="93a20-185">Add the Package Support Framework files to your package</span></span>

<span data-ttu-id="93a20-186">Erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbare Dateien auf dem Verzeichnis hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-186">Add the required 32-bit and 64-bit PSF  DLLs and executable files to the package directory.</span></span> <span data-ttu-id="93a20-187">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="93a20-187">Use the following table as a guide.</span></span> <span data-ttu-id="93a20-188">Sie sollten auch alle Runtime-Updates enthalten, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="93a20-188">You'll also want to include any runtime fixes that you need.</span></span> <span data-ttu-id="93a20-189">In unserem Beispiel benötigen wir Datei Umleitung Runtime korrigieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-189">In our example, we need the file redirection runtime fix.</span></span>

| <span data-ttu-id="93a20-190">Ausführbare Anwendung ist x64</span><span class="sxs-lookup"><span data-stu-id="93a20-190">Application executable is x64</span></span> | <span data-ttu-id="93a20-191">Ausführbare Anwendung ist x86</span><span class="sxs-lookup"><span data-stu-id="93a20-191">Application executable is x86</span></span> |
|-------------------------------|-----------|
| [<span data-ttu-id="93a20-192">ShimLauncher64.exe</span><span class="sxs-lookup"><span data-stu-id="93a20-192">ShimLauncher64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [<span data-ttu-id="93a20-193">ShimLauncher32.exe</span><span class="sxs-lookup"><span data-stu-id="93a20-193">ShimLauncher32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [<span data-ttu-id="93a20-194">ShimRuntime64.dll</span><span class="sxs-lookup"><span data-stu-id="93a20-194">ShimRuntime64.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [<span data-ttu-id="93a20-195">ShimRuntime32.dll</span><span class="sxs-lookup"><span data-stu-id="93a20-195">ShimRuntime32.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [<span data-ttu-id="93a20-196">ShimRunDll64.exe</span><span class="sxs-lookup"><span data-stu-id="93a20-196">ShimRunDll64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [<span data-ttu-id="93a20-197">ShimRunDll32.exe</span><span class="sxs-lookup"><span data-stu-id="93a20-197">ShimRunDll32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

<span data-ttu-id="93a20-198">Der Inhalt sollte jetzt wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="93a20-198">Your package content should now look something like this.</span></span>

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a><span data-ttu-id="93a20-200">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="93a20-200">Modify the package manifest</span></span>

<span data-ttu-id="93a20-201">Die Paketmanifest in einem Texteditor öffnen, und legen Sie die `Executable` Attribut der `Application` Element auf den Namen der ausführbaren Datei Shim Launcher.</span><span class="sxs-lookup"><span data-stu-id="93a20-201">Open your package manifest in a text editor, and then set the `Executable` attribute of the `Application` element to the name of the shim launcher executable file.</span></span>  <span data-ttu-id="93a20-202">Sollten Sie die Architektur Ihrer Anwendung, wählen Sie die entsprechende Version ShimLauncher32.exe oder ShimLauncher64.exe.</span><span class="sxs-lookup"><span data-stu-id="93a20-202">If you know the architecture of your target application, select the appropriate version, ShimLauncher32.exe or ShimLauncher64.exe.</span></span>  <span data-ttu-id="93a20-203">Wenn nicht, ShimLauncher32.exe in allen Fällen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="93a20-203">If not, ShimLauncher32.exe will work in all cases.</span></span>  <span data-ttu-id="93a20-204">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="93a20-204">Here's an example.</span></span>

```xml
<Package ...>
  ...
  <Applications>
    <Application Id="PSFSample"
                 Executable="ShimLauncher32.exe"
                 EntryPoint="Windows.FullTrustApplication">
      ...
    </Application>
  </Applications>
</Package>
```

### <a name="create-a-configuration-file"></a><span data-ttu-id="93a20-205">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="93a20-205">Create a configuration file</span></span>

<span data-ttu-id="93a20-206">Erstellen Sie einen Dateinamen ``config.json``, und diese Datei in den Stammordner des Pakets speichern.</span><span class="sxs-lookup"><span data-stu-id="93a20-206">Create a file name ``config.json``, and save that file to the root folder of your package.</span></span> <span data-ttu-id="93a20-207">Ändern Sie die deklarierte app-ID der Datei config.json auf die ausführbare Datei, die gerade ersetzt.</span><span class="sxs-lookup"><span data-stu-id="93a20-207">Modify the declared app ID of the config.json file to point to the executable that you just replaced.</span></span> <span data-ttu-id="93a20-208">Verwenden Sie mit Process Monitor gewonnenen Kenntnisse, können Sie auch das Arbeitsverzeichnis sowie Shim Umleitung Datei umleiten Lese-und Schreibvorgänge auf Log-Dateien im Verzeichnis "PSFSampleApp" Relative Paket verwenden.</span><span class="sxs-lookup"><span data-stu-id="93a20-208">Using the knowledge that you gained from using Process Monitor, you can also set the working directory as well as use the file redirection shim to redirect reads/writes to .log files under the package-relative "PSFSampleApp" directory.</span></span>

```json
{
    "applications": [
        {
            "id": "PSFSample",
            "executable": "PSFSampleApp/PSFSample.exe",
            "workingDirectory": "PSFSampleApp/"
        }
    ],
    "processes": [
        {
            "executable": "PSFSample",
            "shims": [
                {
                    "dll": "FileRedirectionShim.dll",
                    "config": {
                        "redirectedPaths": {
                            "packageRelative": [
                                {
                                    "base": "PSFSampleApp/",
                                    "patterns": [
                                        ".*\\.log"
                                    ]
                                }
                            ]
                        }
                    }
                }
            ]
        }
    ]
}
```
<span data-ttu-id="93a20-209">Es folgt eine Anleitung für das Schema config.json:</span><span class="sxs-lookup"><span data-stu-id="93a20-209">Following is a guide for the config.json schema:</span></span>

| <span data-ttu-id="93a20-210">Array</span><span class="sxs-lookup"><span data-stu-id="93a20-210">Array</span></span> | <span data-ttu-id="93a20-211">key</span><span class="sxs-lookup"><span data-stu-id="93a20-211">key</span></span> | <span data-ttu-id="93a20-212">Wert</span><span class="sxs-lookup"><span data-stu-id="93a20-212">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="93a20-213">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-213">applications</span></span> | <span data-ttu-id="93a20-214">id</span><span class="sxs-lookup"><span data-stu-id="93a20-214">id</span></span> |  <span data-ttu-id="93a20-215">Verwenden der `Id` Attribut der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="93a20-215">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="93a20-216">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-216">applications</span></span> | <span data-ttu-id="93a20-217">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="93a20-217">executable</span></span> | <span data-ttu-id="93a20-218">Das Paket relativer Pfad zur ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="93a20-218">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="93a20-219">In den meisten Fällen erhalten Sie diesen Wert aus der Paketmanifestdatei bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="93a20-219">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="93a20-220">Ist der Wert der `Executable` Attribut der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="93a20-220">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="93a20-221">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-221">applications</span></span> | <span data-ttu-id="93a20-222">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="93a20-222">workingDirectory</span></span> | <span data-ttu-id="93a20-223">(Optional) Ein Paket relativer Pfad verwendet das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-223">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="93a20-224">Wenn dieser Wert nicht festgelegt wird, verwendet das Betriebssystem den `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-224">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="93a20-225">Prozesse</span><span class="sxs-lookup"><span data-stu-id="93a20-225">processes</span></span> | <span data-ttu-id="93a20-226">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="93a20-226">executable</span></span> | <span data-ttu-id="93a20-227">In den meisten Fällen werden der Name des dem `executable` über mit dem Pfad und Erweiterung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="93a20-227">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="93a20-228">Shims</span><span class="sxs-lookup"><span data-stu-id="93a20-228">shims</span></span> | <span data-ttu-id="93a20-229">DLL</span><span class="sxs-lookup"><span data-stu-id="93a20-229">dll</span></span> | <span data-ttu-id="93a20-230">Paket relativer Pfad Shim .appx geladen.</span><span class="sxs-lookup"><span data-stu-id="93a20-230">Package-relative path to the shim  .appx  to load.</span></span> |
| <span data-ttu-id="93a20-231">Shims</span><span class="sxs-lookup"><span data-stu-id="93a20-231">shims</span></span> | <span data-ttu-id="93a20-232">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="93a20-232">config</span></span> | <span data-ttu-id="93a20-233">(Optional) Steuert das Verhalten der Shim dl.</span><span class="sxs-lookup"><span data-stu-id="93a20-233">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="93a20-234">Das genaue Format dieses Wertes hängt jeweils Shim Shim wie jede Shim "Blob" interpretieren kann, wie es.</span><span class="sxs-lookup"><span data-stu-id="93a20-234">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="93a20-235">Die `applications`, `processes`, und `shims` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="93a20-235">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="93a20-236">Das bedeutet, dass Sie config.json Datei können mehr als eine Anwendung, Prozess und Shim-DLL an.</span><span class="sxs-lookup"><span data-stu-id="93a20-236">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>


### <a name="package-and-test-the-app"></a><span data-ttu-id="93a20-237">Paket und Testen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="93a20-237">Package and Test the App</span></span>

<span data-ttu-id="93a20-238">Als Nächstes erstellen Sie ein Paket.</span><span class="sxs-lookup"><span data-stu-id="93a20-238">Next, create a package.</span></span>

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

<span data-ttu-id="93a20-239">Anschließend signieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-239">Then, sign it.</span></span>

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

<span data-ttu-id="93a20-240">Weitere Informationen finden Sie unter [Erstellen eines Pakets Signaturzertifikat](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie ein Paket mithilfe von signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span><span class="sxs-lookup"><span data-stu-id="93a20-240">For more information, see [how to create a package signing certificate](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) and [how to sign a package using signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span></span>

<span data-ttu-id="93a20-241">PowerShell verwenden, um das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-241">Using PowerShell, install the package.</span></span>

>[!NOTE]
> <span data-ttu-id="93a20-242">Beachten Sie das Paket zuerst deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-242">Remember to uninstall the package first.</span></span>

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

<span data-ttu-id="93a20-243">Führen Sie die Anwendung, und beobachten Sie das Verhalten mit Laufzeit Fix angewendet.</span><span class="sxs-lookup"><span data-stu-id="93a20-243">Run the application and observe the behavior with runtime fix applied.</span></span>  <span data-ttu-id="93a20-244">Wiederholen Sie Diagnose und Verpackung Schritte.</span><span class="sxs-lookup"><span data-stu-id="93a20-244">Repeat the diagnostic and packaging steps as necessary.</span></span>

### <a name="use-the-trace-shim"></a><span data-ttu-id="93a20-245">Trace-Shim verwenden</span><span class="sxs-lookup"><span data-stu-id="93a20-245">Use the Trace Shim</span></span>

<span data-ttu-id="93a20-246">Ein alternatives Verfahren zur Diagnose von Kompatibilitätsproblemen Anwendung ist die Verwendung der Trace-Shim.</span><span class="sxs-lookup"><span data-stu-id="93a20-246">An alternative technique to diagnosing packaged application compatibility issues is to use the Trace Shim.</span></span> <span data-ttu-id="93a20-247">Diese DLL ist im Lieferumfang der PSF und bietet eine detaillierte Diagnose Ansicht der app Verhalten wie Process Monitor.</span><span class="sxs-lookup"><span data-stu-id="93a20-247">This DLL is included with the PSF and provides a detailed diagnostic view of the app's behavior, similar to Process Monitor.</span></span>  <span data-ttu-id="93a20-248">Es ist speziell Anwendungskompatibilitätsprobleme anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="93a20-248">It is specially designed to reveal application compatibility issues.</span></span>  <span data-ttu-id="93a20-249">Trace-Shim verwenden, dem Paket die DLL hinzufügen der config.json das folgende Fragment hinzufügen gepackt und installieren Sie die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-249">To use the Trace Shim, add the DLL to the package, add the following fragment to your config.json, and then package and install your application.</span></span>

```json
{
    "dll": "TraceShim.dll",
    "config": {
        "traceLevels": {
            "filesystem": "allFailures"
        }
    }
}
```

<span data-ttu-id="93a20-250">Standardmäßig filtert der Trace-Shim Fehler, die in Betracht "erwartet".</span><span class="sxs-lookup"><span data-stu-id="93a20-250">By default, the Trace Shim filters out failures that might be considered "expected".</span></span>  <span data-ttu-id="93a20-251">Z. B. versucht Anwendung unbedingt eine Datei löschen, ohne zu überprüfen, ob sie vorhanden ist, wird das Ergebnis ignoriert.</span><span class="sxs-lookup"><span data-stu-id="93a20-251">For example, applications might try to unconditionally delete a file without checking to see if it already exists, ignoring the result.</span></span> <span data-ttu-id="93a20-252">Die bedauerliche folgen einige unerwartete Fehler herausgefiltert abrufen können hat, im obigen Beispiel wir entscheiden, alle Fehler von Dateisystem-Funktionen erhalten</span><span class="sxs-lookup"><span data-stu-id="93a20-252">This has the unfortunate consequence that some unexpected failures might get filtered out, so in the above example, we opt to receive all failures from filesystem functions.</span></span> <span data-ttu-id="93a20-253">Wir tun dies, denn wir wissen aus Lesen aus der Datei Config.txt vor, denen mit "die Meldung Datei nicht gefunden schlägt".</span><span class="sxs-lookup"><span data-stu-id="93a20-253">We do this because we know from before that the attempt to read from the Config.txt file fails with the message "file not found".</span></span> <span data-ttu-id="93a20-254">Dies ist ein Fehler, der häufig und unerwartet nicht angenommen.</span><span class="sxs-lookup"><span data-stu-id="93a20-254">This is a failure that is frequently observed and not generally assumed to be unexpected.</span></span> <span data-ttu-id="93a20-255">In der Praxis ist es wahrscheinlich am besten zu filtern, unerwartete Fehler und dann zurückgreifen auf alle Fehler ist ein Problem, das noch nicht identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="93a20-255">In practice it's likely best to start out filtering only to unexpected failures, and then falling back to all failures if there's an issue that still can't be identified.</span></span>

<span data-ttu-id="93a20-256">In der Standardeinstellung wird die Ausgabe von Trace-Shim angefügten Debugger gesendet.</span><span class="sxs-lookup"><span data-stu-id="93a20-256">By default, the output from the Trace Shim gets sent to the attached debugger.</span></span> <span data-ttu-id="93a20-257">In diesem Beispiel wir sind nicht zu debuggen und verwendet stattdessen [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) Programm von SysInternals um die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="93a20-257">For this example, we aren't going to attach a debugger, and will instead use the [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) program from SysInternals to view its output.</span></span> <span data-ttu-id="93a20-258">Nach der Ausführung der Anwendung, sehen die gleichen Fehler wie zuvor wir die weisen wir auf die gleiche Laufzeit Updates.</span><span class="sxs-lookup"><span data-stu-id="93a20-258">After running the app, we can see the same failures as before, which would point us towards the same runtime fixes.</span></span>

![TraceShim-Datei nicht gefunden](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a><span data-ttu-id="93a20-261">Debuggen Sie, erweitern Sie oder erstellen Sie eine Laufzeit-Korrektur</span><span class="sxs-lookup"><span data-stu-id="93a20-261">Debug, extend, or create a runtime fix</span></span>

<span data-ttu-id="93a20-262">Sie können Visual Studio debuggen Laufzeit Fix, Runtime Update erweitern oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="93a20-262">You can use Visual Studio to debug a runtime fix, extend a runtime fix, or create one from scratch.</span></span> <span data-ttu-id="93a20-263">Sie müssen diese Dinge zu tun.</span><span class="sxs-lookup"><span data-stu-id="93a20-263">You'll need to do these things to be successful.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="93a20-264">Verpackungsprojekt hinzufügen</span><span class="sxs-lookup"><span data-stu-id="93a20-264">Add a packaging project</span></span>
> * <span data-ttu-id="93a20-265">Projekt für Common Language Runtime-Update</span><span class="sxs-lookup"><span data-stu-id="93a20-265">Add project for the runtime fix</span></span>
> * <span data-ttu-id="93a20-266">Fügen Sie ein Projekt, das die Shim-Startprogramm ausführbare beginnt</span><span class="sxs-lookup"><span data-stu-id="93a20-266">Add a project that starts the Shim Launcher executable</span></span>
> * <span data-ttu-id="93a20-267">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="93a20-267">Configure the packaging project</span></span>

<span data-ttu-id="93a20-268">Wenn Sie fertig sind, wird die Projektmappe wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="93a20-268">When you're done, your solution will look something like this.</span></span>

![Bereits fertig gestellte Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

<span data-ttu-id="93a20-270">Jedes Projekt in diesem Beispiel betrachten.</span><span class="sxs-lookup"><span data-stu-id="93a20-270">Let's look at each project in this example.</span></span>

| <span data-ttu-id="93a20-271">Projekt</span><span class="sxs-lookup"><span data-stu-id="93a20-271">Project</span></span> | <span data-ttu-id="93a20-272">Zweck</span><span class="sxs-lookup"><span data-stu-id="93a20-272">Purpose</span></span> |
|-------|-----------|
| <span data-ttu-id="93a20-273">DesktopApplicationPackage</span><span class="sxs-lookup"><span data-stu-id="93a20-273">DesktopApplicationPackage</span></span> | <span data-ttu-id="93a20-274">Dieses Projekt basiert auf [Windows Application Packaging Projekt](desktop-to-uwp-packaging-dot-net.md) und es gibt das MSIX-Paket.</span><span class="sxs-lookup"><span data-stu-id="93a20-274">This project is based on the [Windows Application Packaging project](desktop-to-uwp-packaging-dot-net.md) and it outputs the the MSIX package.</span></span> |
| <span data-ttu-id="93a20-275">Runtimefix</span><span class="sxs-lookup"><span data-stu-id="93a20-275">Runtimefix</span></span> | <span data-ttu-id="93a20-276">Dies ist ein C++ Dynamic-Linked Bibliotheksprojekt mit mindestens Ersatz-Funktion, die als Update Runtime dienen.</span><span class="sxs-lookup"><span data-stu-id="93a20-276">This is a C++ Dynamic-Linked Library project that contains one or more replacement functions that serve as the runtime fix.</span></span> |
| <span data-ttu-id="93a20-277">ShimLauncher</span><span class="sxs-lookup"><span data-stu-id="93a20-277">ShimLauncher</span></span> | <span data-ttu-id="93a20-278">Dies ist leeres C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="93a20-278">This is C++ Empty Project.</span></span> <span data-ttu-id="93a20-279">Dieses Projekt ist an die Laufzeit verteilbaren Dateien des Paket-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="93a20-279">This project is a place to collect the runtime distributable files of the Package Support Framework.</span></span> <span data-ttu-id="93a20-280">Es gibt eine ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="93a20-280">It outputs an executable file.</span></span> <span data-ttu-id="93a20-281">Die ausführbare Datei ist was ausgeführt wird, wenn die Projektmappe zu starten.</span><span class="sxs-lookup"><span data-stu-id="93a20-281">That executable is the first thing that runs when you start the solution.</span></span> |
| <span data-ttu-id="93a20-282">WinFormsDesktopApplication</span><span class="sxs-lookup"><span data-stu-id="93a20-282">WinFormsDesktopApplication</span></span> | <span data-ttu-id="93a20-283">Dieses Projekt enthält den Quellcode einer desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-283">This project contains the source code of a desktop application.</span></span> |

<span data-ttu-id="93a20-284">Um sich ein vollständiges Beispiel, das alle diese Projekte enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span><span class="sxs-lookup"><span data-stu-id="93a20-284">To look at a complete sample that contains all of these types of projects, see [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span></span>

<span data-ttu-id="93a20-285">Gehen Sie durch die Schritte zum Erstellen und Konfigurieren aller Projekte in der Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="93a20-285">Let's walk through the steps to create and configure each of these projects in your solution.</span></span>


### <a name="create-a-package-solution"></a><span data-ttu-id="93a20-286">Erstellen Sie eine Lösung</span><span class="sxs-lookup"><span data-stu-id="93a20-286">Create a package solution</span></span>

<span data-ttu-id="93a20-287">Haben Sie bereits eine Lösung für Ihr desktop-Anwendung, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93a20-287">If you don't already have a solution for your desktop application, create a new **Blank Solution** in Visual Studio.</span></span>

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

<span data-ttu-id="93a20-289">Außerdem möchten Sie Anwendungsprojekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-289">You may also want to add any application projects you have.</span></span>

### <a name="add-a-packaging-project"></a><span data-ttu-id="93a20-290">Verpackungsprojekt hinzufügen</span><span class="sxs-lookup"><span data-stu-id="93a20-290">Add a packaging project</span></span>

<span data-ttu-id="93a20-291">Haben Sie bereits ein **Windows-Anwendungsprojekt Verpackung**erstellt und der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-291">If you don't already have a **Windows Application Packaging Project**, create one and add it to your solution.</span></span>

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

<span data-ttu-id="93a20-293">Weitere Informationen über Windows Application Packaging-Projekt finden Sie unter [Package die Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="93a20-293">For more information on Windows Application Packaging project, see [Package your application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

<span data-ttu-id="93a20-294">Im **Projektmappen-Explorer**Maustaste verpackungsprojekt **Bearbeiten**auswählen und dann am Ende der Projektdatei hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="93a20-294">In **Solution Explorer**, right-click the packaging project, select **Edit**, and then add this to the bottom of the project file:</span></span>

```
<Target Name="PSFRemoveSourceProject" AfterTargets="ExpandProjectReferences" BeforeTargets="_ConvertItems">
<ItemGroup>
  <FilteredNonWapProjProjectOutput Include="@(_FilteredNonWapProjProjectOutput)">
  <SourceProject Condition="'%(_FilteredNonWapProjProjectOutput.SourceProject)'=='<your runtime fix project name goes here>'" />
  </FilteredNonWapProjProjectOutput>
  <_FilteredNonWapProjProjectOutput Remove="@(_FilteredNonWapProjProjectOutput)" />
  <_FilteredNonWapProjProjectOutput Include="@(FilteredNonWapProjProjectOutput)" />
</ItemGroup>
</Target>
```

### <a name="add-project-for-the-runtime-fix"></a><span data-ttu-id="93a20-295">Projekt für Common Language Runtime-Update</span><span class="sxs-lookup"><span data-stu-id="93a20-295">Add project for the runtime fix</span></span>

<span data-ttu-id="93a20-296">Die Lösung eines C++- **Dynamic Link Library (DLL)** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-296">Add a C++ **Dynamic-Link Library (DLL)** project to the solution.</span></span>

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

<span data-ttu-id="93a20-298">Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="93a20-298">Right-click the that project, and then choose **Properties**.</span></span>

<span data-ttu-id="93a20-299">Auf den Eigenschaftenseiten **C++ Language Standard** Feld und wählen Sie dann in der Dropdown-Liste neben dem Feld der **ISO C++ 17-Standard (/ Std:c-17)** Option.</span><span class="sxs-lookup"><span data-stu-id="93a20-299">In the property pages, find the **C++ Language Standard** field, and then in the drop-down list next to that field, select the **ISO C++17 Standard (/std:c++17)** option.</span></span>

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

<span data-ttu-id="93a20-301">Maustaste auf das Projekt und wählen Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** .</span><span class="sxs-lookup"><span data-stu-id="93a20-301">Right-click that project, and then in the context menu, choose the **Manage Nuget Packages** option.</span></span> <span data-ttu-id="93a20-302">Sicherstellen Sie, dass die **Paketquelle** **Alle** oder **nuget.org**gewählt wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-302">Ensure that the **Package source** option is set to **All** or **nuget.org**.</span></span>

<span data-ttu-id="93a20-303">Klicken Sie auf dem Symbol neben das Feld.</span><span class="sxs-lookup"><span data-stu-id="93a20-303">Click the settings icon next that field.</span></span>

<span data-ttu-id="93a20-304">Suche nach *PSF*\* Nuget-Paket, und installieren Sie sie für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="93a20-304">Search for the *PSF*\* Nuget package, and then install it for this project.</span></span>

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

<span data-ttu-id="93a20-306">Wenn Sie Debuggen oder einen vorhandenen Laufzeit Fix erweitern möchten, fügen Sie Runtime Update-Dateien hinzu, die mit der beschriebenen Anleitung im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs erhalten.</span><span class="sxs-lookup"><span data-stu-id="93a20-306">If you want to debug or extend an existing runtime fix, add the runtime fix files that you obtained by using the guidance described in the [Find a runtime fix](#find) section of this guide.</span></span>

<span data-ttu-id="93a20-307">Soll eine neue zu erstellen, nicht alles dieses Projekt hinzugefügt noch.</span><span class="sxs-lookup"><span data-stu-id="93a20-307">If you intend to create a brand new fix, don't add anything to this project just yet.</span></span> <span data-ttu-id="93a20-308">Wir helfen Ihnen, die richtigen Dateien für dieses Projekt später hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-308">We'll help you add the right files to this project later in this guide.</span></span> <span data-ttu-id="93a20-309">Jetzt werden wir das Einrichten Ihrer Lösung.</span><span class="sxs-lookup"><span data-stu-id="93a20-309">For now, we'll continue setting up your solution.</span></span>

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a><span data-ttu-id="93a20-310">Fügen Sie ein Projekt, das die Shim-Startprogramm ausführbare beginnt</span><span class="sxs-lookup"><span data-stu-id="93a20-310">Add a project that starts the Shim Launcher executable</span></span>

<span data-ttu-id="93a20-311">Hinzufügen eines C++- **Leeres Projekt** der Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="93a20-311">Add a C++ **Empty Project** project to the solution.</span></span>

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

<span data-ttu-id="93a20-313">Fügen Sie **PSF** Nuget-Paket dieses Projekt mit der gleichen Anleitung im vorherigen Abschnitt beschrieben hinzu.</span><span class="sxs-lookup"><span data-stu-id="93a20-313">Add the **PSF** Nuget package to this project by using the same guidance described in the previous section.</span></span>

<span data-ttu-id="93a20-314">Öffnen die Eigenschaftenseiten für das Projekt und auf der Seite **Allgemeine** Einstellungen legen Sie **Target Name** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` je nach der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-314">Open the property pages for the project, and in the **General** settings page, set the **Target Name** property to ``ShimLauncher32`` or ``ShimLauncher64`` depending on the architecture of your application.</span></span>

![Shim Launcher Verweis](images/desktop-to-uwp/shim-exe-reference.png)

<span data-ttu-id="93a20-316">Fügen Sie einen Projektverweis auf das Projekt Update in der Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="93a20-316">Add a project reference to the runtime fix project in your solution.</span></span>

![Laufzeit Fix Verweis](images/desktop-to-uwp/reference-fix.png)

<span data-ttu-id="93a20-318">Maustaste auf den Verweis und wenden Sie dann diese Werte im **Eigenschaftenfenster** .</span><span class="sxs-lookup"><span data-stu-id="93a20-318">Right-click the reference, and then in the **Properties** window, apply these values.</span></span>

| <span data-ttu-id="93a20-319">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="93a20-319">Property</span></span> | <span data-ttu-id="93a20-320">Wert</span><span class="sxs-lookup"><span data-stu-id="93a20-320">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="93a20-321">Lokale kopieren</span><span class="sxs-lookup"><span data-stu-id="93a20-321">Copy local</span></span> | <span data-ttu-id="93a20-322">Wahr</span><span class="sxs-lookup"><span data-stu-id="93a20-322">True</span></span> |
| <span data-ttu-id="93a20-323">Lokale Satellitenassemblys kopieren</span><span class="sxs-lookup"><span data-stu-id="93a20-323">Copy Local Satellite Assemblies</span></span> | <span data-ttu-id="93a20-324">Wahr</span><span class="sxs-lookup"><span data-stu-id="93a20-324">True</span></span> |
| <span data-ttu-id="93a20-325">Verweis Montageausstoß</span><span class="sxs-lookup"><span data-stu-id="93a20-325">Reference Assembly Output</span></span> | <span data-ttu-id="93a20-326">Wahr</span><span class="sxs-lookup"><span data-stu-id="93a20-326">True</span></span> |
| <span data-ttu-id="93a20-327">Link Library Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="93a20-327">Link Library Dependencies</span></span> | <span data-ttu-id="93a20-328">False</span><span class="sxs-lookup"><span data-stu-id="93a20-328">False</span></span> |
| <span data-ttu-id="93a20-329">Verbindung Bibliothekabhängigkeitseingaben</span><span class="sxs-lookup"><span data-stu-id="93a20-329">Link Library Dependency Inputs</span></span> | <span data-ttu-id="93a20-330">False</span><span class="sxs-lookup"><span data-stu-id="93a20-330">False</span></span> |

### <a name="configure-the-packaging-project"></a><span data-ttu-id="93a20-331">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="93a20-331">Configure the packaging project</span></span>

<span data-ttu-id="93a20-332">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="93a20-332">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

<span data-ttu-id="93a20-334">Wählen Sie das Shim Launcher Projekt und desktop hinzu und wählen Sie dann auf **OK** .</span><span class="sxs-lookup"><span data-stu-id="93a20-334">Choose the shim launcher project and your desktop application project, and then choose the **OK** button.</span></span>

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> <span data-ttu-id="93a20-336">Haben Sie den Quellcode der Anwendung, wählen Sie einfach das Shim Launcher-Projekt.</span><span class="sxs-lookup"><span data-stu-id="93a20-336">If you don't have the source code to your application, just choose the shim launcher project.</span></span> <span data-ttu-id="93a20-337">Wir zeigen Ihnen wie die ausführbare Datei verweisen, wenn Sie eine Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="93a20-337">We'll show you how to reference your executable when you create a configuration file.</span></span>

<span data-ttu-id="93a20-338">Im Knoten **Applikationen** Application Launcher Shim Maustaste und wählen **als Einstiegspunkt**.</span><span class="sxs-lookup"><span data-stu-id="93a20-338">In the **Applications** node, right-click the shim launcher application, and then choose **Set as Entry Point**.</span></span>

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

<span data-ttu-id="93a20-340">Fügen Sie eine Datei mit dem Namen ``config.json`` dem Projekt packen, kopieren und Json-Text in die Datei einfügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-340">Add a file named ``config.json`` to your packaging project, then, copy and paste the following json text into the file.</span></span> <span data-ttu-id="93a20-341">Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalt**.</span><span class="sxs-lookup"><span data-stu-id="93a20-341">Set the **Package Action** property to **Content**.</span></span>

```json
{
    "applications": [
        {
            "id": "",
            "executable": "",
            "workingDirectory": ""
        }
    ],
    "processes": [
        {
            "executable": "",
            "shims": [
                {
                    "dll": "",
                    "config": {
                    }
                }
            ]
        }
    ]
}
```
<span data-ttu-id="93a20-342">Geben Sie einen Wert für jeden Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="93a20-342">Provide a value for each key.</span></span> <span data-ttu-id="93a20-343">Verwenden Sie diese Tabelle als Leitfaden.</span><span class="sxs-lookup"><span data-stu-id="93a20-343">Use this table as a guide.</span></span>

| <span data-ttu-id="93a20-344">Array</span><span class="sxs-lookup"><span data-stu-id="93a20-344">Array</span></span> | <span data-ttu-id="93a20-345">key</span><span class="sxs-lookup"><span data-stu-id="93a20-345">key</span></span> | <span data-ttu-id="93a20-346">Wert</span><span class="sxs-lookup"><span data-stu-id="93a20-346">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="93a20-347">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-347">applications</span></span> | <span data-ttu-id="93a20-348">id</span><span class="sxs-lookup"><span data-stu-id="93a20-348">id</span></span> |  <span data-ttu-id="93a20-349">Verwenden der `Id` Attribut der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="93a20-349">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="93a20-350">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-350">applications</span></span> | <span data-ttu-id="93a20-351">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="93a20-351">executable</span></span> | <span data-ttu-id="93a20-352">Das Paket relativer Pfad zur ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="93a20-352">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="93a20-353">In den meisten Fällen erhalten Sie diesen Wert aus der Paketmanifestdatei bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="93a20-353">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="93a20-354">Ist der Wert der `Executable` Attribut der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="93a20-354">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="93a20-355">applications</span><span class="sxs-lookup"><span data-stu-id="93a20-355">applications</span></span> | <span data-ttu-id="93a20-356">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="93a20-356">workingDirectory</span></span> | <span data-ttu-id="93a20-357">(Optional) Ein Paket relativer Pfad verwendet das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-357">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="93a20-358">Wenn dieser Wert nicht festgelegt wird, verwendet das Betriebssystem den `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="93a20-358">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="93a20-359">Prozesse</span><span class="sxs-lookup"><span data-stu-id="93a20-359">processes</span></span> | <span data-ttu-id="93a20-360">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="93a20-360">executable</span></span> | <span data-ttu-id="93a20-361">In den meisten Fällen werden der Name des dem `executable` über mit dem Pfad und Erweiterung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="93a20-361">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="93a20-362">Shims</span><span class="sxs-lookup"><span data-stu-id="93a20-362">shims</span></span> | <span data-ttu-id="93a20-363">DLL</span><span class="sxs-lookup"><span data-stu-id="93a20-363">dll</span></span> | <span data-ttu-id="93a20-364">Paket relativer Pfad der Shim-DLL geladen.</span><span class="sxs-lookup"><span data-stu-id="93a20-364">Package-relative path to the shim DLL to load.</span></span> |
| <span data-ttu-id="93a20-365">Shims</span><span class="sxs-lookup"><span data-stu-id="93a20-365">shims</span></span> | <span data-ttu-id="93a20-366">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="93a20-366">config</span></span> | <span data-ttu-id="93a20-367">(Optional) Steuert das Verhalten der Shim dl.</span><span class="sxs-lookup"><span data-stu-id="93a20-367">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="93a20-368">Das genaue Format dieses Wertes hängt jeweils Shim Shim wie jede Shim "Blob" interpretieren kann, wie es.</span><span class="sxs-lookup"><span data-stu-id="93a20-368">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="93a20-369">Wenn Sie fertig sind, Ihre ``config.json`` Datei wird aussehen.</span><span class="sxs-lookup"><span data-stu-id="93a20-369">When you're done, your ``config.json`` file will look something like this.</span></span>

```json
{
  "applications": [
    {
      "id": "DesktopApplication",
      "executable": "DesktopApplication/WinFormsDesktopApplication.exe",
      "workingDirectory": "WinFormsDesktopApplication"
    }
  ],
  "processes": [
    {
      "executable": ".*App.*",
      "shims": [ { "dll": "RuntimeFix.dll" } ]
    }
  ]
}

```

>[!NOTE]
> <span data-ttu-id="93a20-370">Die `applications`, `processes`, und `shims` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="93a20-370">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="93a20-371">Das bedeutet, dass Sie config.json Datei können mehr als eine Anwendung, Prozess und Shim-DLL an.</span><span class="sxs-lookup"><span data-stu-id="93a20-371">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>

### <a name="debug-a-runtime-fix"></a><span data-ttu-id="93a20-372">Debuggen Sie eine Laufzeit-Lösung</span><span class="sxs-lookup"><span data-stu-id="93a20-372">Debug a runtime fix</span></span>

<span data-ttu-id="93a20-373">In Visual Studio Debugger starten F5.</span><span class="sxs-lookup"><span data-stu-id="93a20-373">In Visual Studio, press F5 to start the debugger.</span></span>  <span data-ttu-id="93a20-374">Was startet ist die Shim Launcher Anwendung, Ihre Desktop-Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="93a20-374">The first thing that starts is the shim launcher application, which in turn, starts your target desktop application.</span></span>  <span data-ttu-id="93a20-375">Desktop-Anwendung zu debuggen, müssen Sie manuell Anhängen an den Prozess desktop-Anwendung mit **Debuggen**->**an den Prozess anhängen**und dann den Anwendungsprozess.</span><span class="sxs-lookup"><span data-stu-id="93a20-375">To debug the target desktop application, you'll have to manually attach to the desktop application process by choosing **Debug**->**Attach to Process**, and then selecting the application process.</span></span> <span data-ttu-id="93a20-376">Um das Debuggen einer Anwendung .NET mit einer einheitlichen Laufzeit DLL zuzulassen, wählen Sie verwaltetem und systemeigenem Code (Debuggen im gemischten Modus).</span><span class="sxs-lookup"><span data-stu-id="93a20-376">To permit the debugging of a .NET application with a native runtime fix DLL, select managed and native code types (mixed mode debugging).</span></span>  

<span data-ttu-id="93a20-377">Nachdem dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen desktop Anwendungscode und die Korrektur Projekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="93a20-377">Once you've set this up, you can set break points next to lines of code in the desktop application code and the runtime fix project.</span></span> <span data-ttu-id="93a20-378">Haben Sie den Quellcode der Anwendung, werden Sie Haltepunkte neben Codezeilen im Projekt Update Laufzeit festgelegt.</span><span class="sxs-lookup"><span data-stu-id="93a20-378">If you don't have the source code to your application, you'll be able to set break points only next to lines of code in your runtime fix project.</span></span>

>[!NOTE]
> <span data-ttu-id="93a20-379">Visual Studio bietet die einfachste Entwicklung und Debuggen, gibt es einige Nachteile, werden später in diesem Handbuch andere Debugverfahren besprochen, die Sie anwenden können.</span><span class="sxs-lookup"><span data-stu-id="93a20-379">While Visual Studio gives you the simplest development and debugging experience, there are some limitations, so later in this guide, we'll discuss other debugging techniques that you can apply.</span></span>

## <a name="create-a-runtime-fix"></a><span data-ttu-id="93a20-380">Erstellen Sie eine Laufzeit-Korrektur</span><span class="sxs-lookup"><span data-stu-id="93a20-380">Create a runtime fix</span></span>

<span data-ttu-id="93a20-381">Wenn es keine Laufzeit beheben das Problem aufgelöst, erstellen eine neue Laufzeit Update ersetzt Funktionen und alle Konfigurationsdaten einschließlich macht Sinn.</span><span class="sxs-lookup"><span data-stu-id="93a20-381">If there isn't yet a runtime fix for the issue that you want to resolve, you can create a new runtime fix by writing replacement functions and including any configuration data that makes sense.</span></span> <span data-ttu-id="93a20-382">Betrachten Sie jeden Teil.</span><span class="sxs-lookup"><span data-stu-id="93a20-382">Let's look at each part.</span></span>

### <a name="replacement-functions"></a><span data-ttu-id="93a20-383">Ersatz-Funktionen</span><span class="sxs-lookup"><span data-stu-id="93a20-383">Replacement functions</span></span>

<span data-ttu-id="93a20-384">Bestimmen Sie zunächst, welche Funktion Aufrufe schlagen fehl, wenn die Anwendung in einem MSIX-Container ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="93a20-384">First, identify which function calls fail when your application runs in an MSIX container.</span></span> <span data-ttu-id="93a20-385">Dann können Sie Ersatz-Funktionen erstellen, die den Laufzeit-Manager stattdessen aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="93a20-385">Then, you can create replacement functions that you'd like the runtime manager to call instead.</span></span> <span data-ttu-id="93a20-386">So haben Sie Gelegenheit, die Regeln von moderne Runtime Environment entspricht, Verhalten die Implementierung einer Funktion ersetzen.</span><span class="sxs-lookup"><span data-stu-id="93a20-386">This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.</span></span>

<span data-ttu-id="93a20-387">Öffnen Sie in Visual Studio das Projekt Update, das in diesem Handbuch erstellt.</span><span class="sxs-lookup"><span data-stu-id="93a20-387">In Visual Studio, open the runtime fix project that you created earlier in this guide.</span></span>

<span data-ttu-id="93a20-388">Erklären der ``SHIM_DEFINE_EXPORTS`` Makro und fügen Sie eine Include-Anweisung für die `shim_framework.h` am oberen Rand jeder. CPP-Datei für Funktionen der Common Language Runtime-Lösung hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="93a20-388">Declare the ``SHIM_DEFINE_EXPORTS`` macro and then add a include statement for the `shim_framework.h` at the top of each .CPP file where you intend to add the functions of your runtime fix.</span></span>

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
><span data-ttu-id="93a20-389">Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="93a20-389">Make sure that the `SHIM_DEFINE_EXPORTS` macro appears before the include statement.</span></span>

<span data-ttu-id="93a20-390">Erstellen Sie eine Funktion mit der gleichen Signatur der Funktion, hat Verhalten Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="93a20-390">Create a function that has the same signature of the function who's behavior you want to modify.</span></span> <span data-ttu-id="93a20-391">Hier ist eine Beispielfunktion ersetzt die `MessageBoxW` Funktion.</span><span class="sxs-lookup"><span data-stu-id="93a20-391">Here's an example function that replaces the `MessageBoxW` function.</span></span>

```c++
auto MessageBoxWImpl = &::MessageBoxW;
int WINAPI MessageBoxWShim(
    _In_opt_ HWND hwnd,
    _In_opt_ LPCWSTR,
    _In_opt_ LPCWSTR caption,
    _In_ UINT type)
{
    return MessageBoxWImpl(hwnd, L"SUCCESS: This worked", caption, type);
}

DECLARE_SHIM(MessageBoxWImpl, MessageBoxWShim);
```

<span data-ttu-id="93a20-392">Der Aufruf `DECLARE_SHIM` ordnet die `MessageBoxW` in Ihre neue-Funktion als Ersatz.</span><span class="sxs-lookup"><span data-stu-id="93a20-392">The call to `DECLARE_SHIM` maps the `MessageBoxW` function to your new replacement function.</span></span> <span data-ttu-id="93a20-393">Wenn eine Anwendung versucht, rufen Sie die `MessageBoxW` , es wird Funktionsaufruf Ersatz-Funktion stattdessen.</span><span class="sxs-lookup"><span data-stu-id="93a20-393">When your application attempts to call the `MessageBoxW` function, it will call the replacement function instead.</span></span>

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a><span data-ttu-id="93a20-394">Rekursive Aufrufe von Funktionen in Laufzeit Updates schützen</span><span class="sxs-lookup"><span data-stu-id="93a20-394">Protect against recursive calls to functions in runtime fixes</span></span>

<span data-ttu-id="93a20-395">Können optional gelten die `reentrancy_guard` geben die Funktionen, die rekursive Aufrufe von Funktionen in Laufzeit Updates schützen.</span><span class="sxs-lookup"><span data-stu-id="93a20-395">You can optionally apply the `reentrancy_guard` type to your functions that protect against recursive calls to functions in runtime fixes.</span></span>

<span data-ttu-id="93a20-396">Z. B. können Sie eine Ersatz-Funktion für liefern die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="93a20-396">For example, you might produce a replacement function for the `CreateFile` function.</span></span> <span data-ttu-id="93a20-397">Die Implementierung aufrufen kann der `CopyFile` Funktion jedoch die Implementierung der `CopyFile` aufrufen kann der `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="93a20-397">Your implementation might call the `CopyFile` function, but the implementation of the `CopyFile` function might call the `CreateFile` function.</span></span> <span data-ttu-id="93a20-398">Dies kann auf eine unendliche rekursive Aufrufe der `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="93a20-398">This may lead to an infinite recursive cycle of calls to the `CreateFile` function.</span></span>

<span data-ttu-id="93a20-399">Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span><span class="sxs-lookup"><span data-stu-id="93a20-399">For more information on `reentrancy_guard` see [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span></span>

### <a name="configuration-data"></a><span data-ttu-id="93a20-400">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="93a20-400">Configuration data</span></span>

<span data-ttu-id="93a20-401">Wenn Sie Konfigurationsdaten der Laufzeit Fix hinzufügen möchten, sollten Sie hinzugefügt die ``config.json``.</span><span class="sxs-lookup"><span data-stu-id="93a20-401">If you want to add configuration data to your runtime fix, consider adding it to the ``config.json``.</span></span> <span data-ttu-id="93a20-402">Auf diese Weise können Sie die `ShimQueryCurrentDllConfig` um diese Daten zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="93a20-402">That way, you can use the `ShimQueryCurrentDllConfig` to easily parse that data.</span></span> <span data-ttu-id="93a20-403">In diesem Beispiel analysiert einen Boolean und String Wert aus dieser Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="93a20-403">This example parses a boolean and string value from that configuration file.</span></span>

```c++
if (auto configRoot = ::ShimQueryCurrentDllConfig())
{
    auto& config = configRoot->as_object();

    if (auto enabledValue = config.try_get("enabled"))
    {
        g_enabled = enabledValue->as_boolean().get();
    }

    if (auto logPathValue = config.try_get("logPath"))
    {
        g_logPath = logPathValue->as_string().wstring();
    }
}
```

## <a name="other-debugging-techniques"></a><span data-ttu-id="93a20-404">Andere Debugverfahren</span><span class="sxs-lookup"><span data-stu-id="93a20-404">Other debugging techniques</span></span>

<span data-ttu-id="93a20-405">Visual Studio Sie einfachste Entwicklung und Debuggen können, sind einige Nachteile.</span><span class="sxs-lookup"><span data-stu-id="93a20-405">While Visual Studio gives you the simplest development and debugging experience, there are some limitations.</span></span>

<span data-ttu-id="93a20-406">F5-debugging wird zunächst die Anwendung von losen Dateien aus dem Paket Layout Ordner bereitstellen, sondern aus einem .appx Paket installiert.</span><span class="sxs-lookup"><span data-stu-id="93a20-406">First, F5 debugging runs the application by deploying loose files from the package layout folder path, rather than installing from a .appx package.</span></span>  <span data-ttu-id="93a20-407">Layout-Ordner noch die gleichen Einschränkungen als installierte Paketordner normalerweise nicht.</span><span class="sxs-lookup"><span data-stu-id="93a20-407">The layout folder typically does not have the same security restrictions as an installed package folder.</span></span> <span data-ttu-id="93a20-408">Daher kann es nicht Pakets Denial Fehler vor einer Laufzeit Update Pfad reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="93a20-408">As a result, it may not be possible to reproduce package path access denial errors prior to applying a runtime fix.</span></span>

<span data-ttu-id="93a20-409">Um dieses Problem zu beheben, verwenden Sie .appx Bereitstellung F5 lose Datei Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="93a20-409">To address this issue, use .appx package deployment rather than F5 loose file deployment.</span></span>  <span data-ttu-id="93a20-410">Erstellen Sie eine Paketdatei .appx verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="93a20-410">To create a .appx package file, use the [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) utility from the Windows SDK, as described above.</span></span> <span data-ttu-id="93a20-411">Oder in Visual Studio mit der rechten Maustaste des Projektknoten und wählen Sie **Store**->**App-Pakete erstellen**.</span><span class="sxs-lookup"><span data-stu-id="93a20-411">Or, from within Visual Studio, right-click your application project node and select **Store**->**Create App Packages**.</span></span>

<span data-ttu-id="93a20-412">Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung zum Anhängen an untergeordnete Prozesse vom Debugger gestartet.</span><span class="sxs-lookup"><span data-stu-id="93a20-412">Another issue with Visual Studio is that it does not have built-in support for attaching to any child processes launched by the debugger.</span></span>   <span data-ttu-id="93a20-413">Dies erschwert das Debuggen Logik in den Startpfad Anwendung, die nach dem Start von Visual Studio manuell angefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="93a20-413">This makes it difficult to debug logic in the startup path of the target application, which must be manually attached by Visual Studio after launch.</span></span>

<span data-ttu-id="93a20-414">Um dieses Problem zu beheben, verwenden Sie einen Debugger, untergeordneten Prozess anfügen, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="93a20-414">To address this issue, use a debugger that supports child process attach.</span></span>  <span data-ttu-id="93a20-415">Beachten Sie, dass es im Allgemeinen nicht möglich, Just-in-Time (JIT) Anwendung debuggen.</span><span class="sxs-lookup"><span data-stu-id="93a20-415">Note that it is generally not possible to attach a just-in-time (JIT) debugger to the target application.</span></span>  <span data-ttu-id="93a20-416">Grund dafür ist die meisten JIT-Verfahren des Debuggers anstelle der Ziel-app über den Registrierungsschlüssel "ImageFileExecutionOptions".</span><span class="sxs-lookup"><span data-stu-id="93a20-416">This is because most JIT techniques involve launching the debugger in place of the target app, via the ImageFileExecutionOptions registry key.</span></span>  <span data-ttu-id="93a20-417">Diese Niederlagen detouring Mechanismus zur ShimLauncher.exe ShimRuntime.dll in die Ziel-app einfügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-417">This defeats the detouring mechanism used by ShimLauncher.exe to inject ShimRuntime.dll into the target app.</span></span>  <span data-ttu-id="93a20-418">WinDbg im [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und erhalten von [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)unterstützt untergeordneten Prozess anfügen.</span><span class="sxs-lookup"><span data-stu-id="93a20-418">WinDbg, included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index), and obtained from the [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), supports child process attach.</span></span>  <span data-ttu-id="93a20-419">Unterstützt jetzt auch direkt [Starten und eine UWP app zu debuggen](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span><span class="sxs-lookup"><span data-stu-id="93a20-419">It also now supports directly [launching and debugging a UWP app](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span></span>

<span data-ttu-id="93a20-420">Ziel beim Start der Anwendung als untergeordneter Prozess Debuggen starten ``WinDbg``.</span><span class="sxs-lookup"><span data-stu-id="93a20-420">To debug target application startup as a child process, start ``WinDbg``.</span></span>

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

<span data-ttu-id="93a20-421">Bei der ``WinDbg`` aufgefordert, Kind Debuggen und entsprechenden Haltepunkte festlegen.</span><span class="sxs-lookup"><span data-stu-id="93a20-421">At the ``WinDbg`` prompt, enable child debugging and set appropriate breakpoints.</span></span>

```
.childdbg 1
g
```
<span data-ttu-id="93a20-422">(führen Sie bis Anwendung und unterbricht aus)</span><span class="sxs-lookup"><span data-stu-id="93a20-422">(execute until target application starts and breaks into the debugger)</span></span>

```
sxe ld fixup.dll
g
```
<span data-ttu-id="93a20-423">(führen Sie bis Fixup-DLL geladen ist aus)</span><span class="sxs-lookup"><span data-stu-id="93a20-423">(execute until the fixup DLL is loaded)</span></span>

```
bp ...
```

>[!NOTE]
> <span data-ttu-id="93a20-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) kann auch zum Debuggen einer Anwendung beim Start und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten.</span><span class="sxs-lookup"><span data-stu-id="93a20-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) can be also used to attach a debugger to an app upon launch, and is also included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index).</span></span>  <span data-ttu-id="93a20-425">Es ist jedoch komplexer als die direkte Unterstützung jetzt WinDbg verwenden.</span><span class="sxs-lookup"><span data-stu-id="93a20-425">However, it is more complex to use than the direct support now provided by WinDbg.</span></span>

## <a name="support-and-feedback"></a><span data-ttu-id="93a20-426">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="93a20-426">Support and feedback</span></span>

**<span data-ttu-id="93a20-427">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="93a20-427">Find answers to your questions</span></span>**

<span data-ttu-id="93a20-428">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="93a20-428">Have questions?</span></span> <span data-ttu-id="93a20-429">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="93a20-429">Ask us on Stack Overflow.</span></span> <span data-ttu-id="93a20-430">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="93a20-430">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="93a20-431">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="93a20-431">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>
