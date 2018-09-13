---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben von Problemen, die Ihre desktop-Anwendung ausgeführt wird, in einem Container MSIX verhindern
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: c8f6866100a4b38fdda8394ea185b02d7af66411
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "3957500"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a><span data-ttu-id="b4724-103">Wenden Sie-Runtime-Updates zu einem MSIX-Paket mit dem Paket-Support-Framework</span><span class="sxs-lookup"><span data-stu-id="b4724-103">Apply runtime fixes to an MSIX package by using the Package Support Framework</span></span>

<span data-ttu-id="b4724-104">Das Paket-Support-Framework ist ein open-Source-Kit, mit dem Sie die Updates auf Anwenden der vorhandenen win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode, haben, damit sie in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4724-104">The Package Support Framework is an open source kit that helps you apply fixes to your existing win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="b4724-105">Das Paket Support-Framework können Ihre Anwendung, führen Sie die bewährten Methoden der modernen-Runtime-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="b4724-105">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

<span data-ttu-id="b4724-106">Um das Paket Support-Framework zu erstellen, nutzten wir die [abweichen müssen](https://www.microsoft.com/en-us/research/project/detours) -Technologie ist ein open-Source-Framework von Microsoft Research (MSR) entwickelt und hilft bei der API-Umleitung und verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="b4724-106">To create the Package Support Framework, we leveraged the [Detours](https://www.microsoft.com/en-us/research/project/detours) technology which is an open source framework developed by Microsoft Research (MSR) and helps with API redirection and hooking.</span></span>

<span data-ttu-id="b4724-107">Dieses Framework ist open-Source, leichter zu, und können Sie sie zur Behandlung von Anwendung schnell.</span><span class="sxs-lookup"><span data-stu-id="b4724-107">This framework is open source, lightweight, and you can use it to address application issues quickly.</span></span> <span data-ttu-id="b4724-108">Es gibt Ihnen außerdem die Möglichkeit, mit der Community auf der ganzen Welt finden Sie in, und auf die Investitionen von anderen aufzubauen.</span><span class="sxs-lookup"><span data-stu-id="b4724-108">It also gives you the opportunity to consult with the community around the globe, and to build on top of the investments of others.</span></span>

## <a name="a-quick-look-inside-of-the-package-support-framework"></a><span data-ttu-id="b4724-109">Einen kurzen innerhalb der Paket-Support-Framework</span><span class="sxs-lookup"><span data-stu-id="b4724-109">A quick look inside of the Package Support Framework</span></span>

<span data-ttu-id="b4724-110">Das Paket Support-Framework enthält eine ausführbare Datei, ein Laufzeit-Manager DLL-Datei und eine Reihe von Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="b4724-110">The Package Support Framework contains an executable, a runtime manager  DLL, and a set of runtime fixes.</span></span>

![Paket-Support-Framework](images/desktop-to-uwp/package-support-framework.png)

<span data-ttu-id="b4724-112">So funktioniert’s.</span><span class="sxs-lookup"><span data-stu-id="b4724-112">Here's how it works.</span></span> <span data-ttu-id="b4724-113">Erstellen Sie eine Konfigurationsdatei, die die Fix(s) angibt, die Sie für Ihre Anwendung anwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-113">You'll create a configuration file that specifies the fix(s) that you want to apply to your application.</span></span> <span data-ttu-id="b4724-114">Anschließend können Sie das Paket auf die Shim Startprogramm ausführbare Datei verweisen ändern.</span><span class="sxs-lookup"><span data-stu-id="b4724-114">Then, you'll modify your package to point to the shim launcher executable file.</span></span>

<span data-ttu-id="b4724-115">Wenn Benutzer Ihre Anwendung starten, wird das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-115">When users start your application, the shim launcher is the first executable that runs.</span></span> <span data-ttu-id="b4724-116">Ihrer Konfigurationsdatei liest, und fügen der Runtime Fix(s) und den Laufzeit-Manager DLL in den Anwendungsprozess.</span><span class="sxs-lookup"><span data-stu-id="b4724-116">It reads your configuration file, and injects the runtime fix(s) and the runtime manager  DLL into the application process.</span></span>

![Paket-Unterstützung Framework DLL-Injection](images/desktop-to-uwp/package-support-framework-2.png)

<span data-ttu-id="b4724-118">Der Laufzeit-Manager gilt das Update, wenn sie von der Anwendung auf einem MSIX-Container Ausführen benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-118">The runtime manager applies the fix when it's needed by the application to run inside of an MSIX container.</span></span>

<span data-ttu-id="b4724-119">Dieses Handbuch hilft Ihnen, Probleme mit der Anwendungskompatibilität zu identifizieren und um suchen, anwenden und erweitern die Runtime behebt, die sie beheben.</span><span class="sxs-lookup"><span data-stu-id="b4724-119">This guide will help you to identify application compatibility issues, and to find, apply, and extend runtime fixes that address them.</span></span>

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a><span data-ttu-id="b4724-120">Anwendungspakets Kompatibilitätsprobleme identifiziert</span><span class="sxs-lookup"><span data-stu-id="b4724-120">Identify packaged application compatibility issues</span></span>

<span data-ttu-id="b4724-121">Erstellen Sie zunächst ein Paket für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-121">First, create a package for your application.</span></span> <span data-ttu-id="b4724-122">Installieren Sie es dann, und beobachten Sie, führen Sie es.</span><span class="sxs-lookup"><span data-stu-id="b4724-122">Then, install it, run it, and observe its behavior.</span></span> <span data-ttu-id="b4724-123">Sie erhalten möglicherweise Fehlermeldungen, mit denen Sie eine Kompatibilitätsprobleme identifizieren können.</span><span class="sxs-lookup"><span data-stu-id="b4724-123">You might receive error messages that can help you identify a compatibility issue.</span></span> <span data-ttu-id="b4724-124">Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="b4724-124">You can also use [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) to identify issues.</span></span>  <span data-ttu-id="b4724-125">Allgemeine Probleme beziehen sich auf die Anwendung Annahmen in Bezug auf die Berechtigungen zum Arbeiten-Verzeichnis und Programm Pfad.</span><span class="sxs-lookup"><span data-stu-id="b4724-125">Common issues relate to application assumptions regarding the working directory and program path permissions.</span></span>

### <a name="using-process-monitor-to-identify-an-issue"></a><span data-ttu-id="b4724-126">Process Monitor verwenden, um ein Problem zu identifizieren</span><span class="sxs-lookup"><span data-stu-id="b4724-126">Using Process Monitor to identify an issue</span></span>

<span data-ttu-id="b4724-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm ermöglicht Ihnen, eine app-Datei und Registrierungsvorgänge und die Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="b4724-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) is a powerful utility for observing an app's file and registry operations, and their results.</span></span>  <span data-ttu-id="b4724-128">Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="b4724-128">This can help you to understand application compatibility issues.</span></span>  <span data-ttu-id="b4724-129">Fügen Sie nach dem Öffnen Process Monitor, einen Filter (Filter > Filter...) nur Ereignisse für die Anwendung ausführbare einschließen.</span><span class="sxs-lookup"><span data-stu-id="b4724-129">After opening Process Monitor, add a filter (Filter > Filter…) to include only events from the application executable.</span></span>

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

<span data-ttu-id="b4724-131">Eine Liste der Ereignisse wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4724-131">A list of events will appear.</span></span> <span data-ttu-id="b4724-132">Für viele dieser Ereignisse wird das Wort **Erfolg** in der Spalte **Ergebnis** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4724-132">For many of these events, the word **SUCCESS** will appear in the **Result** column.</span></span>

![ProcMon-Ereignisse](images/desktop-to-uwp/procmon_events.png)

<span data-ttu-id="b4724-134">Optional können Sie Ereignisse, um nur Fehler nur anzeigen filtern.</span><span class="sxs-lookup"><span data-stu-id="b4724-134">Optionally, you can filter events to only show only failures.</span></span>

![ProcMon Exclude Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

<span data-ttu-id="b4724-136">Wenn Sie einen Dateisystem Zugriff Fehler vermuten, suchen Sie nach fehlgeschlagenen Ereignisse, die unter der System32/SysWOW64 oder der Paketdateipfad sind.</span><span class="sxs-lookup"><span data-stu-id="b4724-136">If you suspect a filesystem access failure, search for failed events that are under either the System32/SysWOW64 or the package file path.</span></span> <span data-ttu-id="b4724-137">Filter können auch hier zu helfen.</span><span class="sxs-lookup"><span data-stu-id="b4724-137">Filters can also help here, too.</span></span> <span data-ttu-id="b4724-138">Starten Sie am unteren Rand der Liste, und führen Sie einen Bildlauf nach oben.</span><span class="sxs-lookup"><span data-stu-id="b4724-138">Start at the bottom of this list and scroll upwards.</span></span> <span data-ttu-id="b4724-139">Fehler, die am unteren Rand der Liste angezeigt werden, sind die zuletzt aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="b4724-139">Failures that appear at the bottom of this list have occurred most recently.</span></span> <span data-ttu-id="b4724-140">Achten Sie die meisten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten, und "Pfad/Name nicht gefunden", und ignorieren Sie Dinge, die nicht verdächtige aussehen.</span><span class="sxs-lookup"><span data-stu-id="b4724-140">Pay most attention to errors that contain strings such as "access denied," and "path/name not found", and ignore things that don't look suspicious.</span></span> <span data-ttu-id="b4724-141">Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme.</span><span class="sxs-lookup"><span data-stu-id="b4724-141">The [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) has two issues.</span></span> <span data-ttu-id="b4724-142">Sie können diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-142">You can see those issues in the list that appears in the following image.</span></span>

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

<span data-ttu-id="b4724-144">In der ersten Ausgabe, die in diesem Bild angezeigt wird, wird die Anwendung nicht aus der Datei "Config.txt" zu lesen, die im Pfad "C:\Windows\SysWOW64" befindet.</span><span class="sxs-lookup"><span data-stu-id="b4724-144">In the first issue that appears in this image, the application is failing to read from the "Config.txt" file that is located in the "C:\Windows\SysWOW64" path.</span></span> <span data-ttu-id="b4724-145">Es ist unwahrscheinlich, dass die Anwendung versucht, diesen Pfad direkt zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="b4724-145">It's unlikely that the application is trying to reference that path directly.</span></span> <span data-ttu-id="b4724-146">In den meisten Fällen versucht, einen relativen Pfad mit aus der Datei gelesen und in der Standardeinstellung ist "System32/SysWOW64" Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-146">Most likely, it's trying to read from that file by using a relative path, and by default, "System32/SysWOW64" is the application's working directory.</span></span> <span data-ttu-id="b4724-147">Dies zeigt, dass die Anwendung die aktuelle Arbeitsverzeichnis, das an einer beliebigen Stelle im Paket festgelegt werden, um erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-147">This suggests that the application is expecting its current working directory to be set to somewhere in the package.</span></span> <span data-ttu-id="b4724-148">Suchen innerhalb der Appx, sehen Sie, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b4724-148">Looking inside of the appx, we can see that the file exists in the same directory as the executable.</span></span>

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

<span data-ttu-id="b4724-150">Das zweite Problem wird in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4724-150">The second issue appears in the following image.</span></span>

![ProcMon Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

<span data-ttu-id="b4724-152">In diesem Problem ist die Anwendung keine log-Datei in ihrem Paketpfad zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="b4724-152">In this issue, the application is failing to write a .log file to its package path.</span></span> <span data-ttu-id="b4724-153">Dies würde empfehlen, dass ein Datei Umleitung Shim hilfreich ist.</span><span class="sxs-lookup"><span data-stu-id="b4724-153">This would suggest that a file redirection shim might help.</span></span>

<a id="find" />

## <a name="find-a-runtime-fix"></a><span data-ttu-id="b4724-154">Suchen nach einer Runtime-Lösung</span><span class="sxs-lookup"><span data-stu-id="b4724-154">Find a runtime fix</span></span>

<span data-ttu-id="b4724-155">Die PSF enthält Runtime-Updates, die Sie jetzt, wie z. B. die Datei Umleitung Shim verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b4724-155">The PSF contains runtime fixes that you can use right now, such as the file redirection shim.</span></span>

### <a name="file-redirection-shim"></a><span data-ttu-id="b4724-156">Datei Umleitung Shim</span><span class="sxs-lookup"><span data-stu-id="b4724-156">File Redirection Shim</span></span>

<span data-ttu-id="b4724-157">Die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten initiierten schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung ist, die in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-157">You can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to redirect attempts to write or read data in a directory that isn't accessible from an application that runs in an MSIX container.</span></span>

<span data-ttu-id="b4724-158">Z. B. wenn die Anwendung in eine Protokolldatei, die in demselben Verzeichnis wie die ausführbare Anwendung ist schreibt, können klicken Sie dann die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie um die Protokolldatei in einen anderen Speicherort, z. B. den lokalen app-Datenspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4724-158">For example, if your application writes to a log file that is in the same directory as your applications executable, then you can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to create that log file in another location, such as the local app data store.</span></span>

### <a name="runtime-fixes-from-the-community"></a><span data-ttu-id="b4724-159">Runtime-Updates von der community</span><span class="sxs-lookup"><span data-stu-id="b4724-159">Runtime fixes from the community</span></span>

<span data-ttu-id="b4724-160">Achten Sie darauf, dass Sie die Community Beiträge unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) -Seite zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b4724-160">Make sure to review the community contributions to our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) page.</span></span> <span data-ttu-id="b4724-161">Es ist möglich, dass andere Entwickler eine ähnliche und Ihrem Problem gelöst haben und ein Laufzeit-Update freigegeben haben.</span><span class="sxs-lookup"><span data-stu-id="b4724-161">It's possible that other developers have resolved an issue similar to yours and have shared a runtime fix.</span></span>

## <a name="apply-a-runtime-fix"></a><span data-ttu-id="b4724-162">Wenden Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b4724-162">Apply a runtime fix</span></span>

<span data-ttu-id="b4724-163">Sie können eine vorhandene Runtime Korrektur mit einige einfache Tools aus dem Windows SDK, und wie folgt anwenden.</span><span class="sxs-lookup"><span data-stu-id="b4724-163">You can apply an existing runtime fix with a few simple tools from the Windows SDK, and by following these steps.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b4724-164">Erstellen Sie einen Ordner des Pakets layout</span><span class="sxs-lookup"><span data-stu-id="b4724-164">Create a package layout folder</span></span>
> * <span data-ttu-id="b4724-165">Die Paket-Support-Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="b4724-165">Get the Package Support Framework files</span></span>
> * <span data-ttu-id="b4724-166">Fügen Sie zu Ihrem Paket hinzu</span><span class="sxs-lookup"><span data-stu-id="b4724-166">Add them to your package</span></span>
> * <span data-ttu-id="b4724-167">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="b4724-167">Modify the package manifest</span></span>
> * <span data-ttu-id="b4724-168">Erstellen Sie eine Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b4724-168">Create a configuration file</span></span>

<span data-ttu-id="b4724-169">Gehen Sie wir durch einzelnen Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="b4724-169">Let's go through each task.</span></span>

### <a name="create-the-package-layout-folder"></a><span data-ttu-id="b4724-170">Erstellen Sie den Ordner der Paket-layout</span><span class="sxs-lookup"><span data-stu-id="b4724-170">Create the package layout folder</span></span>

<span data-ttu-id="b4724-171">Wenn Sie bereits über eine AppX-Datei verfügen, können Sie den Inhalt in einem Layoutordner entpacken, die als die Staging-Bereich für Ihr Paket verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-171">If you have a .appx file already, you can unpack its contents into a layout folder that will serve as the staging area for your package.</span></span>  <span data-ttu-id="b4724-172">Können Sie tun dies auf ein **X64 systemeigenen Tools-Eingabeaufforderung für VS 2017**, oder manuell mit dem SDK Bin-Pfad in den Suchpfad der ausführbaren.</span><span class="sxs-lookup"><span data-stu-id="b4724-172">You can do this from an **x64 Native Tools Command Prompt for VS 2017**, or manually with the SDK bin path in the executable search path.</span></span>

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

<span data-ttu-id="b4724-173">Dadurch wird eine Aktion angezeigt, die wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="b4724-173">This will give you something that looks like the following.</span></span>

![Paketlayout](images/desktop-to-uwp/package_contents.png)

<span data-ttu-id="b4724-175">Wenn Sie eine AppX-Datei zu haben, können Sie die Paketordner und Dateien von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4724-175">If you don't have a .appx file to start with, you can create the package folder and files from scratch.</span></span>

### <a name="get-the-package-support-framework-files"></a><span data-ttu-id="b4724-176">Die Paket-Support-Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="b4724-176">Get the Package Support Framework files</span></span>

<span data-ttu-id="b4724-177">Sie können das PSF Nuget-Paket abrufen, mit Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4724-177">You can get the PSF Nuget package by using Visual Studio.</span></span> <span data-ttu-id="b4724-178">Sie können es auch abrufen, mit dem eigenständigen Nuget-Befehlszeile-Tool.</span><span class="sxs-lookup"><span data-stu-id="b4724-178">You can also get it by using the standalone Nuget command line tool.</span></span>

#### <a name="get-the-package-by-using-visual-studio"></a><span data-ttu-id="b4724-179">Rufen Sie das Paket mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4724-179">Get the package by using Visual Studio</span></span>

<span data-ttu-id="b4724-180">In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.</span><span class="sxs-lookup"><span data-stu-id="b4724-180">In Visual Studio, right-click your solution or project node and pick one of the Manage Nuget Packages commands.</span></span>  <span data-ttu-id="b4724-181">Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , das Paket "NuGet.org" gefunden. Anschließend installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="b4724-181">Search for **Microsoft.PackageSupportFramework** or **PSF** to find the package on Nuget.org. Then, install it.</span></span>

#### <a name="get-the-package-by-using-the-command-line-tool"></a><span data-ttu-id="b4724-182">Rufen Sie das Paket mit dem Tool für die Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="b4724-182">Get the package by using the command line tool</span></span>

<span data-ttu-id="b4724-183">Installieren Sie das Nuget-Befehlszeilentool von diesem Speicherort: https://www.nuget.org/downloads.</span><span class="sxs-lookup"><span data-stu-id="b4724-183">Install the Nuget command line tool from this location: https://www.nuget.org/downloads.</span></span> <span data-ttu-id="b4724-184">Führen Sie dann über die Befehlszeile Nuget diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b4724-184">Then, from the Nuget command line, run this command:</span></span>

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a><span data-ttu-id="b4724-185">Hinzufügen der Paket-Support-Framework-Dateien zu Ihrem Paket</span><span class="sxs-lookup"><span data-stu-id="b4724-185">Add the Package Support Framework files to your package</span></span>

<span data-ttu-id="b4724-186">Erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbaren Dateien in das Paketverzeichnis hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b4724-186">Add the required 32-bit and 64-bit PSF  DLLs and executable files to the package directory.</span></span> <span data-ttu-id="b4724-187">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b4724-187">Use the following table as a guide.</span></span> <span data-ttu-id="b4724-188">Sie sollten auch alle-Runtime-Updates enthalten, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="b4724-188">You'll also want to include any runtime fixes that you need.</span></span> <span data-ttu-id="b4724-189">In unserem Beispiel benötigen wir die Datei Umleitung-Runtime-Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="b4724-189">In our example, we need the file redirection runtime fix.</span></span>

| <span data-ttu-id="b4724-190">Die ausführbare Datei Anwendung ist x64</span><span class="sxs-lookup"><span data-stu-id="b4724-190">Application executable is x64</span></span> | <span data-ttu-id="b4724-191">Die ausführbare Datei Anwendung ist x86</span><span class="sxs-lookup"><span data-stu-id="b4724-191">Application executable is x86</span></span> |
|-------------------------------|-----------|
| [<span data-ttu-id="b4724-192">ShimLauncher64.exe</span><span class="sxs-lookup"><span data-stu-id="b4724-192">ShimLauncher64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [<span data-ttu-id="b4724-193">ShimLauncher32.exe</span><span class="sxs-lookup"><span data-stu-id="b4724-193">ShimLauncher32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [<span data-ttu-id="b4724-194">ShimRuntime64.dll</span><span class="sxs-lookup"><span data-stu-id="b4724-194">ShimRuntime64.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [<span data-ttu-id="b4724-195">ShimRuntime32.dll</span><span class="sxs-lookup"><span data-stu-id="b4724-195">ShimRuntime32.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [<span data-ttu-id="b4724-196">ShimRunDll64.exe</span><span class="sxs-lookup"><span data-stu-id="b4724-196">ShimRunDll64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [<span data-ttu-id="b4724-197">ShimRunDll32.exe</span><span class="sxs-lookup"><span data-stu-id="b4724-197">ShimRunDll32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

<span data-ttu-id="b4724-198">Der Inhalt sollte nun in etwa wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="b4724-198">Your package content should now look something like this.</span></span>

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a><span data-ttu-id="b4724-200">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="b4724-200">Modify the package manifest</span></span>

<span data-ttu-id="b4724-201">Öffnen Sie Ihr Paketmanifest in einem Text-Editor, und legen Sie die `Executable` -Attribut des der `Application` Element auf den Namen der ausführbaren Datei Shim Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="b4724-201">Open your package manifest in a text editor, and then set the `Executable` attribute of the `Application` element to the name of the shim launcher executable file.</span></span>  <span data-ttu-id="b4724-202">Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die korrekte Version, ShimLauncher32.exe oder ShimLauncher64.exe.</span><span class="sxs-lookup"><span data-stu-id="b4724-202">If you know the architecture of your target application, select the appropriate version, ShimLauncher32.exe or ShimLauncher64.exe.</span></span>  <span data-ttu-id="b4724-203">Wenn dies nicht der Fall ist, ShimLauncher32.exe in allen Fällen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b4724-203">If not, ShimLauncher32.exe will work in all cases.</span></span>  <span data-ttu-id="b4724-204">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b4724-204">Here's an example.</span></span>

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

### <a name="create-a-configuration-file"></a><span data-ttu-id="b4724-205">Erstellen Sie eine Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b4724-205">Create a configuration file</span></span>

<span data-ttu-id="b4724-206">Erstellen Sie einen Dateinamen ``config.json``, und speichern Sie diese Datei in den Stammordner des Pakets.</span><span class="sxs-lookup"><span data-stu-id="b4724-206">Create a file name ``config.json``, and save that file to the root folder of your package.</span></span> <span data-ttu-id="b4724-207">Ändern Sie die ID der config.json-Datei deklarierten app aus, um auf die ausführbare Datei verweisen, die Sie gerade ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b4724-207">Modify the declared app ID of the config.json file to point to the executable that you just replaced.</span></span> <span data-ttu-id="b4724-208">Verwenden das wissen, das Sie an der Verwendung von Process Monitor erlangt, können Sie auch das Arbeitsverzeichnis sowie verwenden das Datei Umleitung Shim Lese-/Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" relativen umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="b4724-208">Using the knowledge that you gained from using Process Monitor, you can also set the working directory as well as use the file redirection shim to redirect reads/writes to .log files under the package-relative "PSFSampleApp" directory.</span></span>

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
<span data-ttu-id="b4724-209">Es folgt eine Anleitung für das Schema config.json:</span><span class="sxs-lookup"><span data-stu-id="b4724-209">Following is a guide for the config.json schema:</span></span>

| <span data-ttu-id="b4724-210">Array</span><span class="sxs-lookup"><span data-stu-id="b4724-210">Array</span></span> | <span data-ttu-id="b4724-211">key</span><span class="sxs-lookup"><span data-stu-id="b4724-211">key</span></span> | <span data-ttu-id="b4724-212">Wert</span><span class="sxs-lookup"><span data-stu-id="b4724-212">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="b4724-213">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-213">applications</span></span> | <span data-ttu-id="b4724-214">id</span><span class="sxs-lookup"><span data-stu-id="b4724-214">id</span></span> |  <span data-ttu-id="b4724-215">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="b4724-215">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="b4724-216">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-216">applications</span></span> | <span data-ttu-id="b4724-217">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b4724-217">executable</span></span> | <span data-ttu-id="b4724-218">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-218">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="b4724-219">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern.</span><span class="sxs-lookup"><span data-stu-id="b4724-219">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="b4724-220">Es ist der Wert von der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="b4724-220">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="b4724-221">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-221">applications</span></span> | <span data-ttu-id="b4724-222">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="b4724-222">workingDirectory</span></span> | <span data-ttu-id="b4724-223">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-223">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="b4724-224">Wenn Sie diesen Wert nicht festlegen, wird das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-224">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="b4724-225">Prozesse</span><span class="sxs-lookup"><span data-stu-id="b4724-225">processes</span></span> | <span data-ttu-id="b4724-226">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b4724-226">executable</span></span> | <span data-ttu-id="b4724-227">Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="b4724-227">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="b4724-228">Shims</span><span class="sxs-lookup"><span data-stu-id="b4724-228">shims</span></span> | <span data-ttu-id="b4724-229">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="b4724-229">dll</span></span> | <span data-ttu-id="b4724-230">Relativen Pfad zu der Shim AppX geladen.</span><span class="sxs-lookup"><span data-stu-id="b4724-230">Package-relative path to the shim  .appx  to load.</span></span> |
| <span data-ttu-id="b4724-231">Shims</span><span class="sxs-lookup"><span data-stu-id="b4724-231">shims</span></span> | <span data-ttu-id="b4724-232">config</span><span class="sxs-lookup"><span data-stu-id="b4724-232">config</span></span> | <span data-ttu-id="b4724-233">(Optional) Steuert, wie die Shim Verteilerliste verhält.</span><span class="sxs-lookup"><span data-stu-id="b4724-233">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="b4724-234">Das genaue Format dieses Werts variiert Shim durch Shim regelmäßig, wie jedes Shim dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="b4724-234">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="b4724-235">Die `applications`, `processes`, und `shims` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="b4724-235">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="b4724-236">Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Shim-DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b4724-236">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>


### <a name="package-and-test-the-app"></a><span data-ttu-id="b4724-237">Paket und Testen der App</span><span class="sxs-lookup"><span data-stu-id="b4724-237">Package and Test the App</span></span>

<span data-ttu-id="b4724-238">Als Nächstes erstellen Sie ein Paket.</span><span class="sxs-lookup"><span data-stu-id="b4724-238">Next, create a package.</span></span>

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

<span data-ttu-id="b4724-239">Signieren Sie es dann.</span><span class="sxs-lookup"><span data-stu-id="b4724-239">Then, sign it.</span></span>

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

<span data-ttu-id="b4724-240">Weitere Informationen finden Sie unter [wie ein Signaturzertifikat Paket erstellen](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie Sie ein Pakets mit signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span><span class="sxs-lookup"><span data-stu-id="b4724-240">For more information, see [how to create a package signing certificate](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) and [how to sign a package using signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span></span>

<span data-ttu-id="b4724-241">Mithilfe von PowerShell, installieren Sie das Paket.</span><span class="sxs-lookup"><span data-stu-id="b4724-241">Using PowerShell, install the package.</span></span>

>[!NOTE]
> <span data-ttu-id="b4724-242">Denken Sie daran, das Paket zuerst deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="b4724-242">Remember to uninstall the package first.</span></span>

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

<span data-ttu-id="b4724-243">Führen Sie die Anwendung, und beobachten Sie das Verhalten Runtime Update angewendet.</span><span class="sxs-lookup"><span data-stu-id="b4724-243">Run the application and observe the behavior with runtime fix applied.</span></span>  <span data-ttu-id="b4724-244">Wiederholen Sie die Diagnose- und Verpacken Schritte nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="b4724-244">Repeat the diagnostic and packaging steps as necessary.</span></span>

### <a name="use-the-trace-shim"></a><span data-ttu-id="b4724-245">Verwenden Sie das Trace-Shim</span><span class="sxs-lookup"><span data-stu-id="b4724-245">Use the Trace Shim</span></span>

<span data-ttu-id="b4724-246">Ein alternatives Verfahren für die Diagnose von Kompatibilitätsproblemen verpackten Anwendung ist die Verwendung der Trace-Shim.</span><span class="sxs-lookup"><span data-stu-id="b4724-246">An alternative technique to diagnosing packaged application compatibility issues is to use the Trace Shim.</span></span> <span data-ttu-id="b4724-247">Diese DLL ist in der PSF enthalten und bietet eine detaillierte Ansicht der app Verhalten, ähnlich wie Process Monitor diagnostische.</span><span class="sxs-lookup"><span data-stu-id="b4724-247">This DLL is included with the PSF and provides a detailed diagnostic view of the app's behavior, similar to Process Monitor.</span></span>  <span data-ttu-id="b4724-248">Es ist speziell auf Probleme mit der Anwendungskompatibilität "einblenden".</span><span class="sxs-lookup"><span data-stu-id="b4724-248">It is specially designed to reveal application compatibility issues.</span></span>  <span data-ttu-id="b4724-249">Verwenden Sie die Trace-Shim, die DLL für das Paket hinzufügen Ihrer config.json die folgende Fragment-Komponente hinzufügen und dann Verpacken und Installieren Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-249">To use the Trace Shim, add the DLL to the package, add the following fragment to your config.json, and then package and install your application.</span></span>

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

<span data-ttu-id="b4724-250">Standardmäßig filtert die Trace Shim Fehler, die berücksichtigt werden möglicherweise "erwartet".</span><span class="sxs-lookup"><span data-stu-id="b4724-250">By default, the Trace Shim filters out failures that might be considered "expected".</span></span>  <span data-ttu-id="b4724-251">Beispielsweise Versuch Anwendungen bedingungslos Löschen einer Datei ohne zu überprüfen, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b4724-251">For example, applications might try to unconditionally delete a file without checking to see if it already exists, ignoring the result.</span></span> <span data-ttu-id="b4724-252">Dies hat die unerwünschten Folgen, die einige unerwartete Fehler, gefiltert erhalten möglicherweise so melden Sie sich im obigen Beispiel wir an, um alle Fehler von Dateisystem-Funktionen zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="b4724-252">This has the unfortunate consequence that some unexpected failures might get filtered out, so in the above example, we opt to receive all failures from filesystem functions.</span></span> <span data-ttu-id="b4724-253">Wir tun, da wir von vor, die das Lesen aus der Datei Config.txt fehlschlägt wissen mit "die Meldung Datei nicht gefunden".</span><span class="sxs-lookup"><span data-stu-id="b4724-253">We do this because we know from before that the attempt to read from the Config.txt file fails with the message "file not found".</span></span> <span data-ttu-id="b4724-254">Dies ist ein Fehler, der häufig beobachtet und nicht in der Regel davon ausgegangen, dass unerwartet ist.</span><span class="sxs-lookup"><span data-stu-id="b4724-254">This is a failure that is frequently observed and not generally assumed to be unexpected.</span></span> <span data-ttu-id="b4724-255">In der Praxis ist es wahrscheinlich am besten, beginnen Sie mit dem Filterung nur für unerwartete Fehler, und klicken Sie dann auf die zurückfallen alle Fehler liegt ein Problem, das weiterhin identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4724-255">In practice it's likely best to start out filtering only to unexpected failures, and then falling back to all failures if there's an issue that still can't be identified.</span></span>

<span data-ttu-id="b4724-256">Standardmäßig wird die Ausgabe der Trace-Shim an den Debugger angefügte gesendet.</span><span class="sxs-lookup"><span data-stu-id="b4724-256">By default, the output from the Trace Shim gets sent to the attached debugger.</span></span> <span data-ttu-id="b4724-257">In diesem Beispiel stellen wir sind nicht zu debuggen, und wird die Anwendung [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals stattdessen verwenden, um die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b4724-257">For this example, we aren't going to attach a debugger, and will instead use the [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) program from SysInternals to view its output.</span></span> <span data-ttu-id="b4724-258">Nach dem Ausführen der app, sehen die gleichen Fehler wie zuvor, Sie die würden uns für die gleichen Runtime Updates zeigen.</span><span class="sxs-lookup"><span data-stu-id="b4724-258">After running the app, we can see the same failures as before, which would point us towards the same runtime fixes.</span></span>

![TraceShim Datei nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a><span data-ttu-id="b4724-261">Debuggen Sie, erweitern Sie oder erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b4724-261">Debug, extend, or create a runtime fix</span></span>

<span data-ttu-id="b4724-262">Visual Studio können Sie ein Laufzeit-Update Debuggen, erweitern ein Laufzeit-Update oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4724-262">You can use Visual Studio to debug a runtime fix, extend a runtime fix, or create one from scratch.</span></span> <span data-ttu-id="b4724-263">Sie müssen für diese Vorgänge erfolgreich ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b4724-263">You'll need to do these things to be successful.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b4724-264">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="b4724-264">Add a packaging project</span></span>
> * <span data-ttu-id="b4724-265">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b4724-265">Add project for the runtime fix</span></span>
> * <span data-ttu-id="b4724-266">Fügen Sie ein Projekt, die Shim-Startprogramms gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-266">Add a project that starts the Shim Launcher executable</span></span>
> * <span data-ttu-id="b4724-267">Konfigurieren Sie das Verpacken-Projekt</span><span class="sxs-lookup"><span data-stu-id="b4724-267">Configure the packaging project</span></span>

<span data-ttu-id="b4724-268">Wenn Sie fertig sind, wird die Projektmappe etwa wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="b4724-268">When you're done, your solution will look something like this.</span></span>

![Fertigen Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

<span data-ttu-id="b4724-270">Sehen wir uns auf jedes Projekt in diesem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="b4724-270">Let's look at each project in this example.</span></span>

| <span data-ttu-id="b4724-271">Projekt</span><span class="sxs-lookup"><span data-stu-id="b4724-271">Project</span></span> | <span data-ttu-id="b4724-272">Zweck</span><span class="sxs-lookup"><span data-stu-id="b4724-272">Purpose</span></span> |
|-------|-----------|
| <span data-ttu-id="b4724-273">DesktopApplicationPackage</span><span class="sxs-lookup"><span data-stu-id="b4724-273">DesktopApplicationPackage</span></span> | <span data-ttu-id="b4724-274">Dieses Projekt basiert auf dem [Windows Application Packaging-Projekt](desktop-to-uwp-packaging-dot-net.md) , und es gibt die das Paket MSIX.</span><span class="sxs-lookup"><span data-stu-id="b4724-274">This project is based on the [Windows Application Packaging project](desktop-to-uwp-packaging-dot-net.md) and it outputs the the MSIX package.</span></span> |
| <span data-ttu-id="b4724-275">Runtimefix</span><span class="sxs-lookup"><span data-stu-id="b4724-275">Runtimefix</span></span> | <span data-ttu-id="b4724-276">Dies ist eine Bibliothek Dynamic-Linked-Projekt mit einer oder mehreren Ersatzfunktionen, die als die Runtime-Problembehandlung dienen.</span><span class="sxs-lookup"><span data-stu-id="b4724-276">This is a C++ Dynamic-Linked Library project that contains one or more replacement functions that serve as the runtime fix.</span></span> |
| <span data-ttu-id="b4724-277">ShimLauncher</span><span class="sxs-lookup"><span data-stu-id="b4724-277">ShimLauncher</span></span> | <span data-ttu-id="b4724-278">Dies ist leeres C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b4724-278">This is C++ Empty Project.</span></span> <span data-ttu-id="b4724-279">Dieses Projekt ist ein Ort zum Abrufen der Runtime verteilbaren Dateien des Pakets Support-Frameworks.</span><span class="sxs-lookup"><span data-stu-id="b4724-279">This project is a place to collect the runtime distributable files of the Package Support Framework.</span></span> <span data-ttu-id="b4724-280">Es gibt eine ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="b4724-280">It outputs an executable file.</span></span> <span data-ttu-id="b4724-281">Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe zu starten.</span><span class="sxs-lookup"><span data-stu-id="b4724-281">That executable is the first thing that runs when you start the solution.</span></span> |
| <span data-ttu-id="b4724-282">WinFormsDesktopApplication</span><span class="sxs-lookup"><span data-stu-id="b4724-282">WinFormsDesktopApplication</span></span> | <span data-ttu-id="b4724-283">Dieses Projekt enthält den Quellcode einer desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-283">This project contains the source code of a desktop application.</span></span> |

<span data-ttu-id="b4724-284">Um ein vollständiges Beispiel betrachten, die alle diese Arten von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span><span class="sxs-lookup"><span data-stu-id="b4724-284">To look at a complete sample that contains all of these types of projects, see [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span></span>

<span data-ttu-id="b4724-285">Betrachten Sie die Schritte zum Erstellen und Konfigurieren jedes dieser Projekte in Ihrer Projektmappe aus.</span><span class="sxs-lookup"><span data-stu-id="b4724-285">Let's walk through the steps to create and configure each of these projects in your solution.</span></span>


### <a name="create-a-package-solution"></a><span data-ttu-id="b4724-286">Erstellen Sie eine Paket-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="b4724-286">Create a package solution</span></span>

<span data-ttu-id="b4724-287">Wenn Sie bereits über eine Lösung für Ihre desktop-Anwendung besitzen, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4724-287">If you don't already have a solution for your desktop application, create a new **Blank Solution** in Visual Studio.</span></span>

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

<span data-ttu-id="b4724-289">Sie sollten auch alle Anwendungsprojekte, die hinzufügen, die Sie haben.</span><span class="sxs-lookup"><span data-stu-id="b4724-289">You may also want to add any application projects you have.</span></span>

### <a name="add-a-packaging-project"></a><span data-ttu-id="b4724-290">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="b4724-290">Add a packaging project</span></span>

<span data-ttu-id="b4724-291">Wenn Sie bereits über ein **Windows Application Packaging Project**besitzen, erstellen Sie eine, und fügen sie Sie Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="b4724-291">If you don't already have a **Windows Application Packaging Project**, create one and add it to your solution.</span></span>

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

<span data-ttu-id="b4724-293">Weitere Informationen zu Windows Application Packaging Project finden Sie im [Paket Ihrer Anwendung mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="b4724-293">For more information on Windows Application Packaging project, see [Package your application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

<span data-ttu-id="b4724-294">Im **Projektmappen-Explorer**mit der rechten Maustaste in des Verpacken-Projekts, wählen Sie **Bearbeiten**und fügen Sie diese an das Ende der Datei:</span><span class="sxs-lookup"><span data-stu-id="b4724-294">In **Solution Explorer**, right-click the packaging project, select **Edit**, and then add this to the bottom of the project file:</span></span>

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

### <a name="add-project-for-the-runtime-fix"></a><span data-ttu-id="b4724-295">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b4724-295">Add project for the runtime fix</span></span>

<span data-ttu-id="b4724-296">Fügen Sie der Projektmappe ein C++- **Dll-Bibliothek (DLL)** -Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b4724-296">Add a C++ **Dynamic-Link Library (DLL)** project to the solution.</span></span>

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

<span data-ttu-id="b4724-298">Der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="b4724-298">Right-click the that project, and then choose **Properties**.</span></span>

<span data-ttu-id="b4724-299">Auf den Eigenschaftenseiten suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld der **ISO C ++ 17 Standard (/ Std: c ++ 17)** Option.</span><span class="sxs-lookup"><span data-stu-id="b4724-299">In the property pages, find the **C++ Language Standard** field, and then in the drop-down list next to that field, select the **ISO C++17 Standard (/std:c++17)** option.</span></span>

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

<span data-ttu-id="b4724-301">Mit der rechten Maustaste in des Projekts, und wählen Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** .</span><span class="sxs-lookup"><span data-stu-id="b4724-301">Right-click that project, and then in the context menu, choose the **Manage Nuget Packages** option.</span></span> <span data-ttu-id="b4724-302">Stellen Sie sicher, dass die **Paketquelle** Option für **Alle** oder **"NuGet.org"** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b4724-302">Ensure that the **Package source** option is set to **All** or **nuget.org**.</span></span>

<span data-ttu-id="b4724-303">Klicken Sie auf dem Symbol "Einstellungen" neben dem Feld.</span><span class="sxs-lookup"><span data-stu-id="b4724-303">Click the settings icon next that field.</span></span>

<span data-ttu-id="b4724-304">Suchen Sie nach der *PSF*\* Nuget Paket, und installieren Sie es für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="b4724-304">Search for the *PSF*\* Nuget package, and then install it for this project.</span></span>

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

<span data-ttu-id="b4724-306">Wenn Sie Debuggen oder einen vorhandenen Runtime Fix erweitern möchten, fügen Sie die Runtime-Fix-Dateien, die Sie abgerufen, indem Sie die Anleitung im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="b4724-306">If you want to debug or extend an existing runtime fix, add the runtime fix files that you obtained by using the guidance described in the [Find a runtime fix](#find) section of this guide.</span></span>

<span data-ttu-id="b4724-307">Wenn Sie beabsichtigen, ein völlig neues Update zu erstellen, fügen Sie nicht alles dieses Projekt noch.</span><span class="sxs-lookup"><span data-stu-id="b4724-307">If you intend to create a brand new fix, don't add anything to this project just yet.</span></span> <span data-ttu-id="b4724-308">Wir helfen Ihnen, die richtigen Dateien diesem Projekt weiter unten in diesem Handbuch hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b4724-308">We'll help you add the right files to this project later in this guide.</span></span> <span data-ttu-id="b4724-309">Für den Moment fahren wir Einrichten Ihrer Projektmappe fort.</span><span class="sxs-lookup"><span data-stu-id="b4724-309">For now, we'll continue setting up your solution.</span></span>

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a><span data-ttu-id="b4724-310">Fügen Sie ein Projekt, die Shim-Startprogramms gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-310">Add a project that starts the Shim Launcher executable</span></span>

<span data-ttu-id="b4724-311">Fügen Sie der Projektmappe ein **Leeres Projekt** für C++-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b4724-311">Add a C++ **Empty Project** project to the solution.</span></span>

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

<span data-ttu-id="b4724-313">Fügen Sie das **PSF** Nuget-Paket auf dieses Projekt mithilfe von die gleichen Anleitung im vorherigen Abschnitt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b4724-313">Add the **PSF** Nuget package to this project by using the same guidance described in the previous section.</span></span>

<span data-ttu-id="b4724-314">Öffnen die Eigenschaftenseiten für das Projekt, und klicken Sie auf der Seite **Allgemein** Einstellungen setzen Sie den **Zielnamen** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` abhängig von der Architektur der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-314">Open the property pages for the project, and in the **General** settings page, set the **Target Name** property to ``ShimLauncher32`` or ``ShimLauncher64`` depending on the architecture of your application.</span></span>

![Shim Startprogramm-Referenz](images/desktop-to-uwp/shim-exe-reference.png)

<span data-ttu-id="b4724-316">Fügen Sie einen Projektverweis auf das Projekt der Runtime Update in Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="b4724-316">Add a project reference to the runtime fix project in your solution.</span></span>

![-Runtime-Fix-Referenz](images/desktop-to-uwp/reference-fix.png)

<span data-ttu-id="b4724-318">Mit der rechten Maustaste in der Referenz, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.</span><span class="sxs-lookup"><span data-stu-id="b4724-318">Right-click the reference, and then in the **Properties** window, apply these values.</span></span>

| <span data-ttu-id="b4724-319">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b4724-319">Property</span></span> | <span data-ttu-id="b4724-320">Wert</span><span class="sxs-lookup"><span data-stu-id="b4724-320">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="b4724-321">Kopieren Sie lokale</span><span class="sxs-lookup"><span data-stu-id="b4724-321">Copy local</span></span> | <span data-ttu-id="b4724-322">Wahr</span><span class="sxs-lookup"><span data-stu-id="b4724-322">True</span></span> |
| <span data-ttu-id="b4724-323">Lokale Satellitenassemblys kopieren</span><span class="sxs-lookup"><span data-stu-id="b4724-323">Copy Local Satellite Assemblies</span></span> | <span data-ttu-id="b4724-324">Wahr</span><span class="sxs-lookup"><span data-stu-id="b4724-324">True</span></span> |
| <span data-ttu-id="b4724-325">Referenz-Assembly-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="b4724-325">Reference Assembly Output</span></span> | <span data-ttu-id="b4724-326">Wahr</span><span class="sxs-lookup"><span data-stu-id="b4724-326">True</span></span> |
| <span data-ttu-id="b4724-327">Link-Bibliothek Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="b4724-327">Link Library Dependencies</span></span> | <span data-ttu-id="b4724-328">False</span><span class="sxs-lookup"><span data-stu-id="b4724-328">False</span></span> |
| <span data-ttu-id="b4724-329">Link-Bibliothek Abhängigkeit Eingaben</span><span class="sxs-lookup"><span data-stu-id="b4724-329">Link Library Dependency Inputs</span></span> | <span data-ttu-id="b4724-330">False</span><span class="sxs-lookup"><span data-stu-id="b4724-330">False</span></span> |

### <a name="configure-the-packaging-project"></a><span data-ttu-id="b4724-331">Konfigurieren Sie das Verpacken-Projekt</span><span class="sxs-lookup"><span data-stu-id="b4724-331">Configure the packaging project</span></span>

<span data-ttu-id="b4724-332">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="b4724-332">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

<span data-ttu-id="b4724-334">Wählen Sie die Shim-Startprogramm Projekt und Ihre desktop-Anwendung, und wählen Sie dann auf die Schaltfläche " **OK** ".</span><span class="sxs-lookup"><span data-stu-id="b4724-334">Choose the shim launcher project and your desktop application project, and then choose the **OK** button.</span></span>

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> <span data-ttu-id="b4724-336">Wenn Sie den Quellcode für Ihre Anwendung besitzen, wählen Sie einfach das Shim Startprogramm-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b4724-336">If you don't have the source code to your application, just choose the shim launcher project.</span></span> <span data-ttu-id="b4724-337">Wir zeigen Ihnen wie die ausführbare Datei verweisen, wenn Sie eine Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="b4724-337">We'll show you how to reference your executable when you create a configuration file.</span></span>

<span data-ttu-id="b4724-338">Klicken Sie im Knoten " **Anwendungen** " mit der rechten Maustaste in der startanwendung Shim, und wählen Sie dann **als Einstiegspunkt festlegen**.</span><span class="sxs-lookup"><span data-stu-id="b4724-338">In the **Applications** node, right-click the shim launcher application, and then choose **Set as Entry Point**.</span></span>

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

<span data-ttu-id="b4724-340">Fügen Sie eine Datei mit dem Namen ``config.json`` dem Verpacken-Projekt, klicken Sie dann, kopieren und fügen Sie den folgenden Json-Text in die Datei.</span><span class="sxs-lookup"><span data-stu-id="b4724-340">Add a file named ``config.json`` to your packaging project, then, copy and paste the following json text into the file.</span></span> <span data-ttu-id="b4724-341">Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalte**.</span><span class="sxs-lookup"><span data-stu-id="b4724-341">Set the **Package Action** property to **Content**.</span></span>

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
<span data-ttu-id="b4724-342">Geben Sie einen Wert für jeden Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="b4724-342">Provide a value for each key.</span></span> <span data-ttu-id="b4724-343">Orientieren Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b4724-343">Use this table as a guide.</span></span>

| <span data-ttu-id="b4724-344">Array</span><span class="sxs-lookup"><span data-stu-id="b4724-344">Array</span></span> | <span data-ttu-id="b4724-345">key</span><span class="sxs-lookup"><span data-stu-id="b4724-345">key</span></span> | <span data-ttu-id="b4724-346">Wert</span><span class="sxs-lookup"><span data-stu-id="b4724-346">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="b4724-347">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-347">applications</span></span> | <span data-ttu-id="b4724-348">id</span><span class="sxs-lookup"><span data-stu-id="b4724-348">id</span></span> |  <span data-ttu-id="b4724-349">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="b4724-349">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="b4724-350">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-350">applications</span></span> | <span data-ttu-id="b4724-351">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b4724-351">executable</span></span> | <span data-ttu-id="b4724-352">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-352">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="b4724-353">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern.</span><span class="sxs-lookup"><span data-stu-id="b4724-353">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="b4724-354">Es ist der Wert von der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="b4724-354">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="b4724-355">applications</span><span class="sxs-lookup"><span data-stu-id="b4724-355">applications</span></span> | <span data-ttu-id="b4724-356">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="b4724-356">workingDirectory</span></span> | <span data-ttu-id="b4724-357">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-357">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="b4724-358">Wenn Sie diesen Wert nicht festlegen, wird das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b4724-358">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="b4724-359">Prozesse</span><span class="sxs-lookup"><span data-stu-id="b4724-359">processes</span></span> | <span data-ttu-id="b4724-360">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b4724-360">executable</span></span> | <span data-ttu-id="b4724-361">Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="b4724-361">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="b4724-362">Shims</span><span class="sxs-lookup"><span data-stu-id="b4724-362">shims</span></span> | <span data-ttu-id="b4724-363">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="b4724-363">dll</span></span> | <span data-ttu-id="b4724-364">Relativen Pfad zu der Shim-DLL zu laden.</span><span class="sxs-lookup"><span data-stu-id="b4724-364">Package-relative path to the shim DLL to load.</span></span> |
| <span data-ttu-id="b4724-365">Shims</span><span class="sxs-lookup"><span data-stu-id="b4724-365">shims</span></span> | <span data-ttu-id="b4724-366">config</span><span class="sxs-lookup"><span data-stu-id="b4724-366">config</span></span> | <span data-ttu-id="b4724-367">(Optional) Steuert, wie die Shim Verteilerliste verhält.</span><span class="sxs-lookup"><span data-stu-id="b4724-367">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="b4724-368">Das genaue Format dieses Werts variiert Shim durch Shim regelmäßig, wie jedes Shim dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="b4724-368">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="b4724-369">Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="b4724-369">When you're done, your ``config.json`` file will look something like this.</span></span>

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
> <span data-ttu-id="b4724-370">Die `applications`, `processes`, und `shims` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="b4724-370">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="b4724-371">Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Shim-DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b4724-371">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>

### <a name="debug-a-runtime-fix"></a><span data-ttu-id="b4724-372">Debuggen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b4724-372">Debug a runtime fix</span></span>

<span data-ttu-id="b4724-373">Drücken Sie in Visual Studio F5, um den Debugger zu starten.</span><span class="sxs-lookup"><span data-stu-id="b4724-373">In Visual Studio, press F5 to start the debugger.</span></span>  <span data-ttu-id="b4724-374">Müssen Sie zunächst, die gestartet wird, ist der startanwendung Shim, die wiederum die Ziel-desktop-Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-374">The first thing that starts is the shim launcher application, which in turn, starts your target desktop application.</span></span>  <span data-ttu-id="b4724-375">Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell für den desktop-Anwendungsprozess anhängen, indem Sie **Debuggen**auswählen->**an den Prozess anhängen**, und wählen Sie dann den bewerbungsprozess.</span><span class="sxs-lookup"><span data-stu-id="b4724-375">To debug the target desktop application, you'll have to manually attach to the desktop application process by choosing **Debug**->**Attach to Process**, and then selecting the application process.</span></span> <span data-ttu-id="b4724-376">Um das Debuggen einer .NET-Anwendung mit einen systemeigenen Runtime Hotfix DLL zu ermöglichen, wählen Sie verwalteten und systemeigenen Code (im gemischten Modus Debuggen).</span><span class="sxs-lookup"><span data-stu-id="b4724-376">To permit the debugging of a .NET application with a native runtime fix DLL, select managed and native code types (mixed mode debugging).</span></span>  

<span data-ttu-id="b4724-377">Nachdem Sie dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und das Projekt der Runtime Update festlegen.</span><span class="sxs-lookup"><span data-stu-id="b4724-377">Once you've set this up, you can set break points next to lines of code in the desktop application code and the runtime fix project.</span></span> <span data-ttu-id="b4724-378">Wenn Sie den Quellcode für Ihre Anwendung besitzen, werden Sie Haltepunkte nur neben Codezeilen in Ihrem Projekt der Runtime Update festlegen.</span><span class="sxs-lookup"><span data-stu-id="b4724-378">If you don't have the source code to your application, you'll be able to set break points only next to lines of code in your runtime fix project.</span></span>

>[!NOTE]
> <span data-ttu-id="b4724-379">Obwohl Visual Studio Ihnen die einfachste Entwicklung bietet und Debuggen, es einige Einschränkungen gibt, dies später in diesem Handbuch erläutern wir, andere debugging Techniken, die Sie anwenden können.</span><span class="sxs-lookup"><span data-stu-id="b4724-379">While Visual Studio gives you the simplest development and debugging experience, there are some limitations, so later in this guide, we'll discuss other debugging techniques that you can apply.</span></span>

## <a name="create-a-runtime-fix"></a><span data-ttu-id="b4724-380">Erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b4724-380">Create a runtime fix</span></span>

<span data-ttu-id="b4724-381">Wenn es keinen noch eine Laufzeit für das Problem beheben, aufgelöst werden soll, können Sie erstellen einen neuen Runtime Hotfix schreiben Ersatzfunktionen und alle Konfigurationsdaten, darunter ist, die sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="b4724-381">If there isn't yet a runtime fix for the issue that you want to resolve, you can create a new runtime fix by writing replacement functions and including any configuration data that makes sense.</span></span> <span data-ttu-id="b4724-382">Sehen wir uns auf jeder Teil.</span><span class="sxs-lookup"><span data-stu-id="b4724-382">Let's look at each part.</span></span>

### <a name="replacement-functions"></a><span data-ttu-id="b4724-383">Ersatzfunktionen</span><span class="sxs-lookup"><span data-stu-id="b4724-383">Replacement functions</span></span>

<span data-ttu-id="b4724-384">Identifizieren Sie zunächst, welche Funktion ruft fehl, wenn die Anwendung in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-384">First, identify which function calls fail when your application runs in an MSIX container.</span></span> <span data-ttu-id="b4724-385">Anschließend können Sie Ersatzfunktionen erstellen, die Sie mit den Laufzeit-Manager stattdessen aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-385">Then, you can create replacement functions that you'd like the runtime manager to call instead.</span></span> <span data-ttu-id="b4724-386">Dies bietet Ihnen die Möglichkeit, die Implementierung einer Funktion mit Verhalten zu ersetzen, die die Regeln der modernen-Runtime-Umgebung entspricht.</span><span class="sxs-lookup"><span data-stu-id="b4724-386">This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.</span></span>

<span data-ttu-id="b4724-387">Öffnen Sie das Projekt der Runtime-Update, das Sie weiter oben in diesem Handbuch erstellt haben, in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4724-387">In Visual Studio, open the runtime fix project that you created earlier in this guide.</span></span>

<span data-ttu-id="b4724-388">Deklarieren Sie die ``SHIM_DEFINE_EXPORTS`` Makro und fügen Sie eine Include-Anweisung für die `shim_framework.h` am Anfang jeder. CPP-Datei für die Funktionen der Ihrer Laufzeit-Update hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-388">Declare the ``SHIM_DEFINE_EXPORTS`` macro and then add a include statement for the `shim_framework.h` at the top of each .CPP file where you intend to add the functions of your runtime fix.</span></span>

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
><span data-ttu-id="b4724-389">Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b4724-389">Make sure that the `SHIM_DEFINE_EXPORTS` macro appears before the include statement.</span></span>

<span data-ttu-id="b4724-390">Erstellen Sie eine Funktion, die dieselbe Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="b4724-390">Create a function that has the same signature of the function who's behavior you want to modify.</span></span> <span data-ttu-id="b4724-391">Dies ist eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b4724-391">Here's an example function that replaces the `MessageBoxW` function.</span></span>

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

<span data-ttu-id="b4724-392">Der Aufruf von `DECLARE_SHIM` ordnet die `MessageBoxW` in Ihrer neuen-Funktion als Ersatz.</span><span class="sxs-lookup"><span data-stu-id="b4724-392">The call to `DECLARE_SHIM` maps the `MessageBoxW` function to your new replacement function.</span></span> <span data-ttu-id="b4724-393">Wenn Ihre Anwendung versucht, rufen Sie die `MessageBoxW` -Funktion es Ruft die Ersatz-Funktion stattdessen.</span><span class="sxs-lookup"><span data-stu-id="b4724-393">When your application attempts to call the `MessageBoxW` function, it will call the replacement function instead.</span></span>

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a><span data-ttu-id="b4724-394">Schutz vor rekursiven-Aufrufe von Funktionen in der Common Language Runtime-Updates</span><span class="sxs-lookup"><span data-stu-id="b4724-394">Protect against recursive calls to functions in runtime fixes</span></span>

<span data-ttu-id="b4724-395">Sie können optional anwenden, die `reentrancy_guard` geben, um Ihre Funktionen, die Schutz gegen rekursiven-Aufrufe von Funktionen in der Common Language Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="b4724-395">You can optionally apply the `reentrancy_guard` type to your functions that protect against recursive calls to functions in runtime fixes.</span></span>

<span data-ttu-id="b4724-396">Sie können z. B. erzeugen, eine Funktion Ersatz für die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b4724-396">For example, you might produce a replacement function for the `CreateFile` function.</span></span> <span data-ttu-id="b4724-397">Die Implementierung aufrufen kann die `CopyFile` -Funktion, aber die Implementierung von der `CopyFile` Funktion kann aufrufen und die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b4724-397">Your implementation might call the `CopyFile` function, but the implementation of the `CopyFile` function might call the `CreateFile` function.</span></span> <span data-ttu-id="b4724-398">Dies kann dazu führen, dass ein unendlichen rekursiven Zyklus der Aufrufe von der `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b4724-398">This may lead to an infinite recursive cycle of calls to the `CreateFile` function.</span></span>

<span data-ttu-id="b4724-399">Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span><span class="sxs-lookup"><span data-stu-id="b4724-399">For more information on `reentrancy_guard` see [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span></span>

### <a name="configuration-data"></a><span data-ttu-id="b4724-400">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="b4724-400">Configuration data</span></span>

<span data-ttu-id="b4724-401">Wenn Sie Ihre Update-Runtime-Konfigurationsdaten hinzufügen möchten, in Betracht ziehen, um die ``config.json``.</span><span class="sxs-lookup"><span data-stu-id="b4724-401">If you want to add configuration data to your runtime fix, consider adding it to the ``config.json``.</span></span> <span data-ttu-id="b4724-402">Auf diese Weise können Sie die `ShimQueryCurrentDllConfig` einfach diese Daten analysiert.</span><span class="sxs-lookup"><span data-stu-id="b4724-402">That way, you can use the `ShimQueryCurrentDllConfig` to easily parse that data.</span></span> <span data-ttu-id="b4724-403">In diesem Beispiel wird einen Boolean und String-Wert aus der Konfigurationsdatei analysiert.</span><span class="sxs-lookup"><span data-stu-id="b4724-403">This example parses a boolean and string value from that configuration file.</span></span>

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

## <a name="other-debugging-techniques"></a><span data-ttu-id="b4724-404">Andere debugging-Techniken</span><span class="sxs-lookup"><span data-stu-id="b4724-404">Other debugging techniques</span></span>

<span data-ttu-id="b4724-405">Während Visual Studio die einfachste Entwicklung und das debugging Erfahrung Ihnen bietet, gibt es einige Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b4724-405">While Visual Studio gives you the simplest development and debugging experience, there are some limitations.</span></span>

<span data-ttu-id="b4724-406">Zuerst wird ein Debuggens mit F5 die Anwendung durch die Bereitstellung von losen Dateien aus dem Paket Layout Ordnerpfad, statt aus einem AppX-Paket installiert.</span><span class="sxs-lookup"><span data-stu-id="b4724-406">First, F5 debugging runs the application by deploying loose files from the package layout folder path, rather than installing from a .appx package.</span></span>  <span data-ttu-id="b4724-407">Der Layoutordner verfügt in der Regel nicht dieselben sicherheitseinschränkungen, die als ein installiere Paket-Ordner.</span><span class="sxs-lookup"><span data-stu-id="b4724-407">The layout folder typically does not have the same security restrictions as an installed package folder.</span></span> <span data-ttu-id="b4724-408">Daher kann es nicht Paket Pfad Denial Zugriffsfehler vor der Anwendung ein Laufzeit-Updates reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="b4724-408">As a result, it may not be possible to reproduce package path access denial errors prior to applying a runtime fix.</span></span>

<span data-ttu-id="b4724-409">Um dieses Problem zu beheben, verwenden Sie Bereitstellung des AppX-Pakets anstelle von F5 loser Datei-Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="b4724-409">To address this issue, use .appx package deployment rather than F5 loose file deployment.</span></span>  <span data-ttu-id="b4724-410">Um eine AppX-Paketdatei zu erstellen, verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b4724-410">To create a .appx package file, use the [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) utility from the Windows SDK, as described above.</span></span> <span data-ttu-id="b4724-411">Oder, in Visual Studio Maustaste auf den Projektknoten Anwendung und wählen **Store**->**App-Pakete erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b4724-411">Or, from within Visual Studio, right-click your application project node and select **Store**->**Create App Packages**.</span></span>

<span data-ttu-id="b4724-412">Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung für die Verbindung vom Debugger gestartet untergeordnete Prozesse enthält.</span><span class="sxs-lookup"><span data-stu-id="b4724-412">Another issue with Visual Studio is that it does not have built-in support for attaching to any child processes launched by the debugger.</span></span>   <span data-ttu-id="b4724-413">Dies erschwert es zum Debuggen Logik im Startpfad der Zielanwendung, die nach der Einführung von Visual Studio manuell angefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b4724-413">This makes it difficult to debug logic in the startup path of the target application, which must be manually attached by Visual Studio after launch.</span></span>

<span data-ttu-id="b4724-414">Um dieses Problem zu beheben, verwenden Sie einen Debugger, untergeordneter Prozess anhängen, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b4724-414">To address this issue, use a debugger that supports child process attach.</span></span>  <span data-ttu-id="b4724-415">Beachten Sie, dass es in der Regel nicht möglich, Just-in-Time (JIT) der Zielanwendung Debuggen.</span><span class="sxs-lookup"><span data-stu-id="b4724-415">Note that it is generally not possible to attach a just-in-time (JIT) debugger to the target application.</span></span>  <span data-ttu-id="b4724-416">Grund dafür ist die meisten JIT-Techniken des Debuggers anstelle der Ziel-app, über den Registrierungsschlüssel ImageFileExecutionOptions.</span><span class="sxs-lookup"><span data-stu-id="b4724-416">This is because most JIT techniques involve launching the debugger in place of the target app, via the ImageFileExecutionOptions registry key.</span></span>  <span data-ttu-id="b4724-417">Den detouring Mechanismus von ShimLauncher.exe verwendet, um ShimRuntime.dll in die Ziel-app einzufügen "vereitelt" wird.</span><span class="sxs-lookup"><span data-stu-id="b4724-417">This defeats the detouring mechanism used by ShimLauncher.exe to inject ShimRuntime.dll into the target app.</span></span>  <span data-ttu-id="b4724-418">WinDbg, in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten, und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), unterstützt untergeordneten Prozess anfügen.</span><span class="sxs-lookup"><span data-stu-id="b4724-418">WinDbg, included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index), and obtained from the [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), supports child process attach.</span></span>  <span data-ttu-id="b4724-419">Unterstützt jetzt auch direkt [Starten und Debuggen einer UWP-Apps](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span><span class="sxs-lookup"><span data-stu-id="b4724-419">It also now supports directly [launching and debugging a UWP app](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span></span>

<span data-ttu-id="b4724-420">Zum Starten der Ziel-Anwendung als untergeordneter Prozess Debuggen starten ``WinDbg``.</span><span class="sxs-lookup"><span data-stu-id="b4724-420">To debug target application startup as a child process, start ``WinDbg``.</span></span>

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

<span data-ttu-id="b4724-421">Bei der ``WinDbg`` auffordern, untergeordnete Debuggen aktivieren und entsprechenden Haltepunkte festlegen.</span><span class="sxs-lookup"><span data-stu-id="b4724-421">At the ``WinDbg`` prompt, enable child debugging and set appropriate breakpoints.</span></span>

```
.childdbg 1
g
```
<span data-ttu-id="b4724-422">(ausgeführt wird, bis die Anwendung startet und unterbricht)</span><span class="sxs-lookup"><span data-stu-id="b4724-422">(execute until target application starts and breaks into the debugger)</span></span>

```
sxe ld fixup.dll
g
```
<span data-ttu-id="b4724-423">(erst ausgeführt, wenn die Korrektur aus die DLL geladen wird)</span><span class="sxs-lookup"><span data-stu-id="b4724-423">(execute until the fixup DLL is loaded)</span></span>

```
bp ...
```

>[!NOTE]
> <span data-ttu-id="b4724-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) können auch verwendet werden, um eine app nach dem Start Debuggen, und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b4724-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) can be also used to attach a debugger to an app upon launch, and is also included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index).</span></span>  <span data-ttu-id="b4724-425">Es ist jedoch komplexer als das direkte unterstützt jetzt WinDbg verwenden.</span><span class="sxs-lookup"><span data-stu-id="b4724-425">However, it is more complex to use than the direct support now provided by WinDbg.</span></span>

## <a name="support-and-feedback"></a><span data-ttu-id="b4724-426">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="b4724-426">Support and feedback</span></span>

**<span data-ttu-id="b4724-427">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="b4724-427">Find answers to your questions</span></span>**

<span data-ttu-id="b4724-428">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="b4724-428">Have questions?</span></span> <span data-ttu-id="b4724-429">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="b4724-429">Ask us on Stack Overflow.</span></span> <span data-ttu-id="b4724-430">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="b4724-430">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="b4724-431">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="b4724-431">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>
