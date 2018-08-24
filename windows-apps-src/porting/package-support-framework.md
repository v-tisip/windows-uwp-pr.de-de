---
author: normesta
Description: Fix issues that prevent your desktop application from running in an MSIX container
Search.Product: eADQiWindows 10XVcnh
title: Beheben von Problemen, die verhindern, dass der Desktopanwendung in einem MSIX-Container ausgeführt wird
ms.author: normesta
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 46d5705233af9e8254b9ac89a2d6e9891e90701f
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2841362"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a><span data-ttu-id="258d1-103">Anwenden von Runtime Updates zu einem Paket MSIX mithilfe des Paket-Support-Frameworks</span><span class="sxs-lookup"><span data-stu-id="258d1-103">Apply runtime fixes to an MSIX package by using the Package Support Framework</span></span>

<span data-ttu-id="258d1-104">Das Paket Support-Framework ist ein open-Source-Kit, die Dank gelten Korrekturen für Ihre vorhandene Win32-Anwendung, wenn Sie nicht über Zugriff auf den Quellcode verfügen, damit es in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="258d1-104">The Package Support Framework is an open source kit that helps you apply fixes to your existing win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="258d1-105">Das Paket Unterstützung Framework hilft bei der Anwendung führen Sie die bewährten Methoden der moderne Runtime-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="258d1-105">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

<span data-ttu-id="258d1-106">Um die Support-Framework-Paket zu erstellen, nutzten wir die [abweichen müssen](https://www.microsoft.com/en-us/research/project/detours) -Technologie wird eine open-Source-Framework von Microsoft Research (MSR) entwickelt und unterstützt die API-Umleitung und Integrieren von.</span><span class="sxs-lookup"><span data-stu-id="258d1-106">To create the Package Support Framework, we leveraged the [Detours](https://www.microsoft.com/en-us/research/project/detours) technology which is an open source framework developed by Microsoft Research (MSR) and helps with API redirection and hooking.</span></span>

<span data-ttu-id="258d1-107">Dieses Frameworks ist leicht, open Source und können Sie sie zum Beheben von Anwendungsproblemen schnell.</span><span class="sxs-lookup"><span data-stu-id="258d1-107">This framework is open source, lightweight, and you can use it to address application issues quickly.</span></span> <span data-ttu-id="258d1-108">Darüber hinaus haben Sie die Möglichkeit, mit der Community auf der ganzen Welt zu konsultieren, und klicken Sie auf der Basis der Investitionen in der anderen Teilnehmer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="258d1-108">It also gives you the opportunity to consult with the community around the globe, and to build on top of the investments of others.</span></span>

## <a name="a-quick-look-inside-of-the-package-support-framework"></a><span data-ttu-id="258d1-109">Ein kurzer Blick in dem Paket Support-Framework</span><span class="sxs-lookup"><span data-stu-id="258d1-109">A quick look inside of the Package Support Framework</span></span>

<span data-ttu-id="258d1-110">Das Paket Support-Framework enthält eine ausführbare Datei, eine Laufzeit-Manager DLL-Datei und eine Reihe von Common Language Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="258d1-110">The Package Support Framework contains an executable, a runtime manager  DLL, and a set of runtime fixes.</span></span>

![Paket-Support-Framework](images/desktop-to-uwp/package-support-framework.png)

<span data-ttu-id="258d1-112">So funktioniert’s.</span><span class="sxs-lookup"><span data-stu-id="258d1-112">Here's how it works.</span></span> <span data-ttu-id="258d1-113">Sie erstellen eine Konfigurationsdatei, die die Fix(s) angibt, die Sie für Ihre Anwendung anwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-113">You'll create a configuration file that specifies the fix(s) that you want to apply to your application.</span></span> <span data-ttu-id="258d1-114">Anschließend können Sie Ihr Paket So zeigen Sie auf die ausführbare Datei aus Shim Launcher ändern.</span><span class="sxs-lookup"><span data-stu-id="258d1-114">Then, you'll modify your package to point to the shim launcher executable file.</span></span>

<span data-ttu-id="258d1-115">Wenn Benutzer die Anwendung starten, wird das Shim Startprogramm für die erste ausführbare Datei, die ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="258d1-115">When users start your application, the shim launcher is the first executable that runs.</span></span> <span data-ttu-id="258d1-116">Liest die Konfigurationsdatei, und fügt die Laufzeit Fix(s) und den Laufzeit-Manager DLL in den Anwendungsprozess.</span><span class="sxs-lookup"><span data-stu-id="258d1-116">It reads your configuration file, and injects the runtime fix(s) and the runtime manager  DLL into the application process.</span></span>

![Paket Unterstützung Framework-DLL Einfügung](images/desktop-to-uwp/package-support-framework-2.png)

<span data-ttu-id="258d1-118">Der Runtime-Manager gilt die Korrektur bei Bedarf die Anwendung ein MSIX Container ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="258d1-118">The runtime manager applies the fix when it's needed by the application to run inside of an MSIX container.</span></span>

<span data-ttu-id="258d1-119">Dieses Handbuch hilft Ihnen, um Probleme mit der Anwendungskompatibilität zu identifizieren, und um finden, anwenden und Erweitern von Common Language Runtime behebt, die deren Behebung.</span><span class="sxs-lookup"><span data-stu-id="258d1-119">This guide will help you to identify application compatibility issues, and to find, apply, and extend runtime fixes that address them.</span></span>

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a><span data-ttu-id="258d1-120">Identifizieren von Anwendungspaket Kompatibilitätsprobleme</span><span class="sxs-lookup"><span data-stu-id="258d1-120">Identify packaged application compatibility issues</span></span>

<span data-ttu-id="258d1-121">Erstellen Sie zunächst ein Paket für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-121">First, create a package for your application.</span></span> <span data-ttu-id="258d1-122">Installieren Sie es anschließend und beobachten Sie, führen Sie es.</span><span class="sxs-lookup"><span data-stu-id="258d1-122">Then, install it, run it, and observe its behavior.</span></span> <span data-ttu-id="258d1-123">Sie erhalten Fehlermeldungen, die ein Kompatibilitätsproblem erleichtern.</span><span class="sxs-lookup"><span data-stu-id="258d1-123">You might receive error messages that can help you identify a compatibility issue.</span></span> <span data-ttu-id="258d1-124">Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="258d1-124">You can also use [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) to identify issues.</span></span>  <span data-ttu-id="258d1-125">Häufige Probleme beziehen sich auf die Anwendung Annahmen bezüglich der Berechtigungen Working Directory und Programmdateien Pfad.</span><span class="sxs-lookup"><span data-stu-id="258d1-125">Common issues relate to application assumptions regarding the working directory and program path permissions.</span></span>

### <a name="using-process-monitor-to-identify-an-issue"></a><span data-ttu-id="258d1-126">Verwenden zum Identifizieren eines Problems Process Monitor</span><span class="sxs-lookup"><span data-stu-id="258d1-126">Using Process Monitor to identify an issue</span></span>

<span data-ttu-id="258d1-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm für eine app-Datei und Registrierung Vorgänge und deren Ergebnisse beobachten.</span><span class="sxs-lookup"><span data-stu-id="258d1-127">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) is a powerful utility for observing an app's file and registry operations, and their results.</span></span>  <span data-ttu-id="258d1-128">Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="258d1-128">This can help you to understand application compatibility issues.</span></span>  <span data-ttu-id="258d1-129">Nach dem Öffnen Process Monitor, fügen Sie einen Filter (Filter > Filter...), gibt es nur Ereignisse aus der ausführbaren Datei der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-129">After opening Process Monitor, add a filter (Filter > Filter…) to include only events from the application executable.</span></span>

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

<span data-ttu-id="258d1-131">Eine Liste der Ereignisse wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="258d1-131">A list of events will appear.</span></span> <span data-ttu-id="258d1-132">Für viele dieser Ereignisse wird das Wort in der Spalte **Ergebnis** **Erfolg** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="258d1-132">For many of these events, the word **SUCCESS** will appear in the **Result** column.</span></span>

![ProcMon Ereignisse](images/desktop-to-uwp/procmon_events.png)

<span data-ttu-id="258d1-134">Optional können Sie Ereignisse, um nur die nur Fehler anzeigen filtern.</span><span class="sxs-lookup"><span data-stu-id="258d1-134">Optionally, you can filter events to only show only failures.</span></span>

![ProcMon ausschließen Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

<span data-ttu-id="258d1-136">Wenn Sie einen Fehler beim Filesystem-Zugriff auf annehmen, suchen Sie nach fehlerhafte Ereignisse, die unter der System32/SysWOW64 oder den Paketdateipfad sind.</span><span class="sxs-lookup"><span data-stu-id="258d1-136">If you suspect a filesystem access failure, search for failed events that are under either the System32/SysWOW64 or the package file path.</span></span> <span data-ttu-id="258d1-137">Filter können auch hier zu helfen.</span><span class="sxs-lookup"><span data-stu-id="258d1-137">Filters can also help here, too.</span></span> <span data-ttu-id="258d1-138">Starten Sie am Ende dieser Liste aus, und führen Sie einen Bildlauf nach oben.</span><span class="sxs-lookup"><span data-stu-id="258d1-138">Start at the bottom of this list and scroll upwards.</span></span> <span data-ttu-id="258d1-139">Fehler, die am Ende dieser Liste angezeigt werden, sind die zuletzt aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="258d1-139">Failures that appear at the bottom of this list have occurred most recently.</span></span> <span data-ttu-id="258d1-140">Achten Sie die meisten auf Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten und "Pfad/Name nicht gefunden", und ignorieren Sie Aufgaben, die nicht verdächtigen aussehen.</span><span class="sxs-lookup"><span data-stu-id="258d1-140">Pay most attention to errors that contain strings such as "access denied," and "path/name not found", and ignore things that don't look suspicious.</span></span> <span data-ttu-id="258d1-141">Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme.</span><span class="sxs-lookup"><span data-stu-id="258d1-141">The [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) has two issues.</span></span> <span data-ttu-id="258d1-142">Sie können diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="258d1-142">You can see those issues in the list that appears in the following image.</span></span>

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

<span data-ttu-id="258d1-144">In der ersten Ausgabe, die in dieser Abbildung angezeigt wird, fällt aus die Anwendung zum Lesen aus der Datei "Config.txt", die sich im Pfad "C:\Windows\SysWOW64" befindet.</span><span class="sxs-lookup"><span data-stu-id="258d1-144">In the first issue that appears in this image, the application is failing to read from the "Config.txt" file that is located in the "C:\Windows\SysWOW64" path.</span></span> <span data-ttu-id="258d1-145">Es ist unwahrscheinlich, dass die Anwendung versucht, auf diesen Pfad direkt zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="258d1-145">It's unlikely that the application is trying to reference that path directly.</span></span> <span data-ttu-id="258d1-146">In den meisten Fällen versucht, mit der ein relativer Pfad aus dieser Datei gelesen und in der Standardeinstellung ist "System32/SysWOW64" Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-146">Most likely, it's trying to read from that file by using a relative path, and by default, "System32/SysWOW64" is the application's working directory.</span></span> <span data-ttu-id="258d1-147">Dies impliziert, dass die Anwendung aktuellen Arbeitsverzeichnis irgendwo im Paket festgelegt werden soll, um erwartet.</span><span class="sxs-lookup"><span data-stu-id="258d1-147">This suggests that the application is expecting its current working directory to be set to somewhere in the package.</span></span> <span data-ttu-id="258d1-148">Suchen Sie in der Appx, sehen Sie, dass die Datei im gleichen Verzeichnis befindet wie die ausführbare Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="258d1-148">Looking inside of the appx, we can see that the file exists in the same directory as the executable.</span></span>

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

<span data-ttu-id="258d1-150">In der folgenden Abbildung wird das zweite Problem angezeigt.</span><span class="sxs-lookup"><span data-stu-id="258d1-150">The second issue appears in the following image.</span></span>

![ProcMon-Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

<span data-ttu-id="258d1-152">In dieser Ausgabe ist die Anwendung zum Schreiben einer log-Datei in den Paketpfad fehl.</span><span class="sxs-lookup"><span data-stu-id="258d1-152">In this issue, the application is failing to write a .log file to its package path.</span></span> <span data-ttu-id="258d1-153">Dies würde empfehlen, dass ein Datei Umleitung Shim hilfreich sein kann.</span><span class="sxs-lookup"><span data-stu-id="258d1-153">This would suggest that a file redirection shim might help.</span></span>

<a id="find" />

## <a name="find-a-runtime-fix"></a><span data-ttu-id="258d1-154">Suchen nach einer Lösung Common Language runtime</span><span class="sxs-lookup"><span data-stu-id="258d1-154">Find a runtime fix</span></span>

<span data-ttu-id="258d1-155">Die PSF enthält Runtime-Updates, die Sie sofort, wie die Datei Umleitung Shim verwenden können.</span><span class="sxs-lookup"><span data-stu-id="258d1-155">The PSF contains runtime fixes that you can use right now, such as the file redirection shim.</span></span>

### <a name="file-redirection-shim"></a><span data-ttu-id="258d1-156">Datei Umleitung Shim</span><span class="sxs-lookup"><span data-stu-id="258d1-156">File Redirection Shim</span></span>

<span data-ttu-id="258d1-157">Die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können Sie umleiten Versuche zum Schreiben oder Lesen von Daten in einem Verzeichnis, die von einer Anwendung zugänglich ist, die in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="258d1-157">You can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to redirect attempts to write or read data in a directory that isn't accessible from an application that runs in an MSIX container.</span></span>

<span data-ttu-id="258d1-158">Beispielsweise, wenn die Anwendung in einer Protokolldatei, die im gleichen Verzeichnis befindet wie die ausführbare Anwendung ist schreibt, können klicken Sie dann die [Datei Umleitung Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie die Protokolldatei an einem anderen Standort, wie etwa dem Datenspeicher lokalen app erstellen.</span><span class="sxs-lookup"><span data-stu-id="258d1-158">For example, if your application writes to a log file that is in the same directory as your applications executable, then you can use the [File Redirection Shim](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to create that log file in another location, such as the local app data store.</span></span>

### <a name="runtime-fixes-from-the-community"></a><span data-ttu-id="258d1-159">Common Language Runtime Fixes aus der community</span><span class="sxs-lookup"><span data-stu-id="258d1-159">Runtime fixes from the community</span></span>

<span data-ttu-id="258d1-160">Stellen Sie sicher, dass Sie die Community-Beiträge zu unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) Seite zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="258d1-160">Make sure to review the community contributions to our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) page.</span></span> <span data-ttu-id="258d1-161">Es ist möglich, dass andere Entwickler eine ähnliche und Ihrem Problem gelöst haben und ein Update Runtime freigegeben haben.</span><span class="sxs-lookup"><span data-stu-id="258d1-161">It's possible that other developers have resolved an issue similar to yours and have shared a runtime fix.</span></span>

## <a name="apply-a-runtime-fix"></a><span data-ttu-id="258d1-162">Anwenden eines Fixes Common Language runtime</span><span class="sxs-lookup"><span data-stu-id="258d1-162">Apply a runtime fix</span></span>

<span data-ttu-id="258d1-163">Sie können einen vorhandene Runtime Fix mit ein paar einfache Tools aus dem Windows-SDK und folgende Schritte anwenden.</span><span class="sxs-lookup"><span data-stu-id="258d1-163">You can apply an existing runtime fix with a few simple tools from the Windows SDK, and by following these steps.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="258d1-164">Erstellen Sie einen Paketordner layout</span><span class="sxs-lookup"><span data-stu-id="258d1-164">Create a package layout folder</span></span>
> * <span data-ttu-id="258d1-165">Die Paket Unterstützung Framework Dateien abrufen</span><span class="sxs-lookup"><span data-stu-id="258d1-165">Get the Package Support Framework files</span></span>
> * <span data-ttu-id="258d1-166">Fügen sie dem Paket hinzu</span><span class="sxs-lookup"><span data-stu-id="258d1-166">Add them to your package</span></span>
> * <span data-ttu-id="258d1-167">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="258d1-167">Modify the package manifest</span></span>
> * <span data-ttu-id="258d1-168">Erstellen Sie eine Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="258d1-168">Create a configuration file</span></span>

<span data-ttu-id="258d1-169">Nun über jede Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="258d1-169">Let's go through each task.</span></span>

### <a name="create-the-package-layout-folder"></a><span data-ttu-id="258d1-170">Erstellen Sie den Ordner Package layout</span><span class="sxs-lookup"><span data-stu-id="258d1-170">Create the package layout folder</span></span>

<span data-ttu-id="258d1-171">Wenn Sie bereits eine Datei .appx verfügen, können Sie den Inhalt in einem Ordner Layout entpacken, die als Bereitstellungsbereich für Ihr Paket dient.</span><span class="sxs-lookup"><span data-stu-id="258d1-171">If you have a .appx file already, you can unpack its contents into a layout folder that will serve as the staging area for your package.</span></span>  <span data-ttu-id="258d1-172">Hierzu können Sie von einer **X64 systemeigenen Tools Command Prompt für VS 2017**, oder manuell mit den SDK-Bin-Pfad in den Suchpfad der ausführbaren.</span><span class="sxs-lookup"><span data-stu-id="258d1-172">You can do this from an **x64 Native Tools Command Prompt for VS 2017**, or manually with the SDK bin path in the executable search path.</span></span>

```
makeappx unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.appx /d PackageContents

```

<span data-ttu-id="258d1-173">Dadurch erhalten etwas Sie, die wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="258d1-173">This will give you something that looks like the following.</span></span>

![Paket-Layout](images/desktop-to-uwp/package_contents.png)

<span data-ttu-id="258d1-175">Wenn Sie keine .appx-Datei zu haben, können Sie die Package-Ordner und Dateien von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="258d1-175">If you don't have a .appx file to start with, you can create the package folder and files from scratch.</span></span>

### <a name="get-the-package-support-framework-files"></a><span data-ttu-id="258d1-176">Die Paket Unterstützung Framework Dateien abrufen</span><span class="sxs-lookup"><span data-stu-id="258d1-176">Get the Package Support Framework files</span></span>

<span data-ttu-id="258d1-177">Sie können das PSF Nuget-Paket abrufen, indem Sie mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="258d1-177">You can get the PSF Nuget package by using Visual Studio.</span></span> <span data-ttu-id="258d1-178">Sie können auch darauf zuzugreifen, mithilfe des eigenständigen Nuget-Befehlszeilentools.</span><span class="sxs-lookup"><span data-stu-id="258d1-178">You can also get it by using the standalone Nuget command line tool.</span></span>

#### <a name="get-the-package-by-using-visual-studio"></a><span data-ttu-id="258d1-179">Abrufen des Pakets mithilfe von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="258d1-179">Get the package by using Visual Studio</span></span>

<span data-ttu-id="258d1-180">In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.</span><span class="sxs-lookup"><span data-stu-id="258d1-180">In Visual Studio, right-click your solution or project node and pick one of the Manage Nuget Packages commands.</span></span>  <span data-ttu-id="258d1-181">Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , um das Paket Nuget.org zu suchen. Klicken Sie dann, installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="258d1-181">Search for **Microsoft.PackageSupportFramework** or **PSF** to find the package on Nuget.org. Then, install it.</span></span>

#### <a name="get-the-package-by-using-the-command-line-tool"></a><span data-ttu-id="258d1-182">Abrufen des Pakets mithilfe des Befehlszeilentools</span><span class="sxs-lookup"><span data-stu-id="258d1-182">Get the package by using the command line tool</span></span>

<span data-ttu-id="258d1-183">Installieren Sie das Befehlszeilentool Nuget aus diesem Speicherort: https://www.nuget.org/downloads.</span><span class="sxs-lookup"><span data-stu-id="258d1-183">Install the Nuget command line tool from this location: https://www.nuget.org/downloads.</span></span> <span data-ttu-id="258d1-184">Führen Sie dann über die Befehlszeile Nuget mit diesem Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="258d1-184">Then, from the Nuget command line, run this command:</span></span>

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a><span data-ttu-id="258d1-185">Dem Paket die Paket-Support-Framework-Dateien hinzufügen</span><span class="sxs-lookup"><span data-stu-id="258d1-185">Add the Package Support Framework files to your package</span></span>

<span data-ttu-id="258d1-186">Fügen Sie die erforderlichen 32-Bit- und 64-Bit-PSF-DLLs und ausführbare Dateien in das Paketverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="258d1-186">Add the required 32-bit and 64-bit PSF  DLLs and executable files to the package directory.</span></span> <span data-ttu-id="258d1-187">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="258d1-187">Use the following table as a guide.</span></span> <span data-ttu-id="258d1-188">Sie sollten auch alle Runtime Fixes enthalten, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="258d1-188">You'll also want to include any runtime fixes that you need.</span></span> <span data-ttu-id="258d1-189">In unserem Beispiel benötigen wir die Datei Umleitung Runtime Korrektur.</span><span class="sxs-lookup"><span data-stu-id="258d1-189">In our example, we need the file redirection runtime fix.</span></span>

| <span data-ttu-id="258d1-190">Ausführbare Datei Anwendung ist x64</span><span class="sxs-lookup"><span data-stu-id="258d1-190">Application executable is x64</span></span> | <span data-ttu-id="258d1-191">Ausführbare Datei Anwendung ist x86</span><span class="sxs-lookup"><span data-stu-id="258d1-191">Application executable is x86</span></span> |
|-------------------------------|-----------|
| [<span data-ttu-id="258d1-192">ShimLauncher64.exe</span><span class="sxs-lookup"><span data-stu-id="258d1-192">ShimLauncher64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [<span data-ttu-id="258d1-193">ShimLauncher32.exe</span><span class="sxs-lookup"><span data-stu-id="258d1-193">ShimLauncher32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [<span data-ttu-id="258d1-194">ShimRuntime64.dll</span><span class="sxs-lookup"><span data-stu-id="258d1-194">ShimRuntime64.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [<span data-ttu-id="258d1-195">ShimRuntime32.dll</span><span class="sxs-lookup"><span data-stu-id="258d1-195">ShimRuntime32.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [<span data-ttu-id="258d1-196">ShimRunDll64.exe</span><span class="sxs-lookup"><span data-stu-id="258d1-196">ShimRunDll64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [<span data-ttu-id="258d1-197">ShimRunDll32.exe</span><span class="sxs-lookup"><span data-stu-id="258d1-197">ShimRunDll32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

<span data-ttu-id="258d1-198">Ihre Inhalte Paket sollte nun etwa wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="258d1-198">Your package content should now look something like this.</span></span>

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a><span data-ttu-id="258d1-200">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="258d1-200">Modify the package manifest</span></span>

<span data-ttu-id="258d1-201">Öffnen Sie Ihr Paketmanifest in einem Text-Editor, und legen Sie dann die `Executable` -Attribut des der `Application` Element auf den Namen der ausführbaren Datei Shim Launcher.</span><span class="sxs-lookup"><span data-stu-id="258d1-201">Open your package manifest in a text editor, and then set the `Executable` attribute of the `Application` element to the name of the shim launcher executable file.</span></span>  <span data-ttu-id="258d1-202">Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die entsprechende Version, ShimLauncher32.exe oder ShimLauncher64.exe.</span><span class="sxs-lookup"><span data-stu-id="258d1-202">If you know the architecture of your target application, select the appropriate version, ShimLauncher32.exe or ShimLauncher64.exe.</span></span>  <span data-ttu-id="258d1-203">Wenn dies nicht der Fall ist, ShimLauncher32.exe in allen Fällen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="258d1-203">If not, ShimLauncher32.exe will work in all cases.</span></span>  <span data-ttu-id="258d1-204">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="258d1-204">Here's an example.</span></span>

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

### <a name="create-a-configuration-file"></a><span data-ttu-id="258d1-205">Erstellen Sie eine Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="258d1-205">Create a configuration file</span></span>

<span data-ttu-id="258d1-206">Erstellen Sie einen Dateinamen ein ``config.json``, und speichern Sie diese Datei in den Stammordner Ihres Pakets.</span><span class="sxs-lookup"><span data-stu-id="258d1-206">Create a file name ``config.json``, and save that file to the root folder of your package.</span></span> <span data-ttu-id="258d1-207">Ändern Sie die deklarierte app-ID der Datei config.json So zeigen Sie auf die ausführbare Datei, die Sie gerade ersetzt.</span><span class="sxs-lookup"><span data-stu-id="258d1-207">Modify the declared app ID of the config.json file to point to the executable that you just replaced.</span></span> <span data-ttu-id="258d1-208">Verwenden die Kenntnisse, die von der Verwendung von Process Monitor resultieren, können Sie auch Arbeitsverzeichnis festlegen sowie verwenden Sie das Datei Umleitung Shim zur Umleitung von Lese-/Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" Paket relativ.</span><span class="sxs-lookup"><span data-stu-id="258d1-208">Using the knowledge that you gained from using Process Monitor, you can also set the working directory as well as use the file redirection shim to redirect reads/writes to .log files under the package-relative "PSFSampleApp" directory.</span></span>

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
<span data-ttu-id="258d1-209">Nachfolgend sehen Sie einen Leitfaden für das Schema config.json:</span><span class="sxs-lookup"><span data-stu-id="258d1-209">Following is a guide for the config.json schema:</span></span>

| <span data-ttu-id="258d1-210">Array</span><span class="sxs-lookup"><span data-stu-id="258d1-210">Array</span></span> | <span data-ttu-id="258d1-211">key</span><span class="sxs-lookup"><span data-stu-id="258d1-211">key</span></span> | <span data-ttu-id="258d1-212">Wert</span><span class="sxs-lookup"><span data-stu-id="258d1-212">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="258d1-213">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-213">applications</span></span> | <span data-ttu-id="258d1-214">id</span><span class="sxs-lookup"><span data-stu-id="258d1-214">id</span></span> |  <span data-ttu-id="258d1-215">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` -Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="258d1-215">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="258d1-216">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-216">applications</span></span> | <span data-ttu-id="258d1-217">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-217">executable</span></span> | <span data-ttu-id="258d1-218">Die Paket-Relative Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-218">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="258d1-219">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="258d1-219">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="258d1-220">Es ist der Wert der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="258d1-220">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="258d1-221">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-221">applications</span></span> | <span data-ttu-id="258d1-222">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="258d1-222">workingDirectory</span></span> | <span data-ttu-id="258d1-223">(Optional) Ein Paket relativer Pfad als das Arbeitsverzeichnis der Anwendung verwenden, die beginnt.</span><span class="sxs-lookup"><span data-stu-id="258d1-223">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="258d1-224">Wenn Sie diesen Wert nicht festlegen, das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-224">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="258d1-225">Prozesse</span><span class="sxs-lookup"><span data-stu-id="258d1-225">processes</span></span> | <span data-ttu-id="258d1-226">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-226">executable</span></span> | <span data-ttu-id="258d1-227">In den meisten Fällen wird dies der Name der werden die `executable` konfigurierten oberhalb der Pfad und Dateiname Erweiterung entfernt.</span><span class="sxs-lookup"><span data-stu-id="258d1-227">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="258d1-228">Shims</span><span class="sxs-lookup"><span data-stu-id="258d1-228">shims</span></span> | <span data-ttu-id="258d1-229">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-229">dll</span></span> | <span data-ttu-id="258d1-230">Paket-relativer Pfad zu der Shim .appx geladen werden.</span><span class="sxs-lookup"><span data-stu-id="258d1-230">Package-relative path to the shim  .appx  to load.</span></span> |
| <span data-ttu-id="258d1-231">Shims</span><span class="sxs-lookup"><span data-stu-id="258d1-231">shims</span></span> | <span data-ttu-id="258d1-232">config</span><span class="sxs-lookup"><span data-stu-id="258d1-232">config</span></span> | <span data-ttu-id="258d1-233">(Optional) Steuert das Verhalten der Shim dl.</span><span class="sxs-lookup"><span data-stu-id="258d1-233">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="258d1-234">Das genaue Format dieses Werts variiert für einzelne Shim-durch-Shim wie jedes Shim wie diesmal dieser "Blob" interpretiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="258d1-234">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="258d1-235">Die `applications`, `processes`, und `shims` Schlüssel Arrays sind.</span><span class="sxs-lookup"><span data-stu-id="258d1-235">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="258d1-236">Dies bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozesse und Shim-DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="258d1-236">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>


### <a name="package-and-test-the-app"></a><span data-ttu-id="258d1-237">Paket und Testen der App</span><span class="sxs-lookup"><span data-stu-id="258d1-237">Package and Test the App</span></span>

<span data-ttu-id="258d1-238">Im nächsten Schritt erstellen Sie ein Paket.</span><span class="sxs-lookup"><span data-stu-id="258d1-238">Next, create a package.</span></span>

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.appx
```

<span data-ttu-id="258d1-239">Klicken Sie dann signieren.</span><span class="sxs-lookup"><span data-stu-id="258d1-239">Then, sign it.</span></span>

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.appx
```

<span data-ttu-id="258d1-240">Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Pakets Signaturzertifikat](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [zum Signieren eines Pakets mithilfe von signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span><span class="sxs-lookup"><span data-stu-id="258d1-240">For more information, see [how to create a package signing certificate](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) and [how to sign a package using signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span></span>

<span data-ttu-id="258d1-241">Mithilfe von PowerShell, um das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="258d1-241">Using PowerShell, install the package.</span></span>

>[!NOTE]
> <span data-ttu-id="258d1-242">Denken Sie daran, um das Paket zuerst zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="258d1-242">Remember to uninstall the package first.</span></span>

```
powershell Add-AppxPackage .\PSFSamplePackageFixup.appx
```

<span data-ttu-id="258d1-243">Führen Sie die Anwendung, und beobachten Sie das Verhalten mit Runtime Fix angewendet.</span><span class="sxs-lookup"><span data-stu-id="258d1-243">Run the application and observe the behavior with runtime fix applied.</span></span>  <span data-ttu-id="258d1-244">Wiederholen Sie die Diagnose und Verpackung Schritte nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="258d1-244">Repeat the diagnostic and packaging steps as necessary.</span></span>

### <a name="use-the-trace-shim"></a><span data-ttu-id="258d1-245">Verwenden Sie das Trace-Shim</span><span class="sxs-lookup"><span data-stu-id="258d1-245">Use the Trace Shim</span></span>

<span data-ttu-id="258d1-246">Ein alternatives Verfahren zum Diagnose von Kompatibilitätsproblemen Anwendungspaket ist die Verwendung der Trace-Shim.</span><span class="sxs-lookup"><span data-stu-id="258d1-246">An alternative technique to diagnosing packaged application compatibility issues is to use the Trace Shim.</span></span> <span data-ttu-id="258d1-247">Diese DLL gehört zum Lieferumfang der PSF und bietet eine detaillierte Ansicht der app-Verhalten, ähnlich wie Process Monitor diagnostische.</span><span class="sxs-lookup"><span data-stu-id="258d1-247">This DLL is included with the PSF and provides a detailed diagnostic view of the app's behavior, similar to Process Monitor.</span></span>  <span data-ttu-id="258d1-248">Es wurde speziell entwickelt, um Probleme mit der Anwendungskompatibilität anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="258d1-248">It is specially designed to reveal application compatibility issues.</span></span>  <span data-ttu-id="258d1-249">Verwenden Sie die Trace-Shim, die DLL des Pakets hinzufügen hinzufügen das folgende Fragment zu Ihrer config.json und gepackt und installieren Sie die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-249">To use the Trace Shim, add the DLL to the package, add the following fragment to your config.json, and then package and install your application.</span></span>

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

<span data-ttu-id="258d1-250">Standardmäßig filtert die Trace-Shim Fehlern, die möglicherweise berücksichtigt werden "erwartet".</span><span class="sxs-lookup"><span data-stu-id="258d1-250">By default, the Trace Shim filters out failures that might be considered "expected".</span></span>  <span data-ttu-id="258d1-251">Beispielsweise Versuch Applications uneingeschränkt Löschen einer Datei ohne zu überprüfen, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert.</span><span class="sxs-lookup"><span data-stu-id="258d1-251">For example, applications might try to unconditionally delete a file without checking to see if it already exists, ignoring the result.</span></span> <span data-ttu-id="258d1-252">Die unerwünschten Folgen, die einige unerwarteter Fehler herausgefiltert, abrufen können hat damit im obigen Beispiel wir aufzuheben, um alle Fehler von Filesystem Funktionen empfangen</span><span class="sxs-lookup"><span data-stu-id="258d1-252">This has the unfortunate consequence that some unexpected failures might get filtered out, so in the above example, we opt to receive all failures from filesystem functions.</span></span> <span data-ttu-id="258d1-253">Dies erfolgt, da wir vor, denen der Versuch zum Lesen aus der Datei Config.txt mit "der Nachricht Datei wurde nicht gefunden" fehlschlägt, wissen aus.</span><span class="sxs-lookup"><span data-stu-id="258d1-253">We do this because we know from before that the attempt to read from the Config.txt file fails with the message "file not found".</span></span> <span data-ttu-id="258d1-254">Hierbei handelt es sich um einen Fehler, der häufig beachtet wird und nicht in der Regel davon ausgegangen, dass unerwartete sein.</span><span class="sxs-lookup"><span data-stu-id="258d1-254">This is a failure that is frequently observed and not generally assumed to be unexpected.</span></span> <span data-ttu-id="258d1-255">In der Praxis ist es wahrscheinlich am besten, anfangs nur für unerwarteter Fehler filtern, und klicken Sie dann zurückgreifen auf alle Fehler liegt ein Problem, das noch nicht ermittelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="258d1-255">In practice it's likely best to start out filtering only to unexpected failures, and then falling back to all failures if there's an issue that still can't be identified.</span></span>

<span data-ttu-id="258d1-256">Standardmäßig ruft die Ausgabe vom Shim Trace an den angefügten Debugger gesendet.</span><span class="sxs-lookup"><span data-stu-id="258d1-256">By default, the output from the Trace Shim gets sent to the attached debugger.</span></span> <span data-ttu-id="258d1-257">In diesem Beispiel wir sind nicht auf Debuggen und werden das Programm [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals stattdessen verwenden, um die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="258d1-257">For this example, we aren't going to attach a debugger, and will instead use the [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) program from SysInternals to view its output.</span></span> <span data-ttu-id="258d1-258">Nach dem Ausführen der app, können wir die gleichen Fehler wie zuvor finden Sie unter dem würden uns verweist die gleichen Runtime Updates zeigen.</span><span class="sxs-lookup"><span data-stu-id="258d1-258">After running the app, we can see the same failures as before, which would point us towards the same runtime fixes.</span></span>

![TraceShim Datei wurde nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a><span data-ttu-id="258d1-261">Debuggen Sie, erweitern Sie oder erstellen Sie ein Update der Common Language runtime</span><span class="sxs-lookup"><span data-stu-id="258d1-261">Debug, extend, or create a runtime fix</span></span>

<span data-ttu-id="258d1-262">Visual Studio können Sie das Debuggen eines Fixes Runtime, erweitern ein Update Runtime oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="258d1-262">You can use Visual Studio to debug a runtime fix, extend a runtime fix, or create one from scratch.</span></span> <span data-ttu-id="258d1-263">Sie müssen diese Schritte erfolgreich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="258d1-263">You'll need to do these things to be successful.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="258d1-264">Fügen Sie ein packprojekt</span><span class="sxs-lookup"><span data-stu-id="258d1-264">Add a packaging project</span></span>
> * <span data-ttu-id="258d1-265">Fügen Sie für die Korrektur Runtime Projekt hinzu</span><span class="sxs-lookup"><span data-stu-id="258d1-265">Add project for the runtime fix</span></span>
> * <span data-ttu-id="258d1-266">Fügen Sie ein Projekt aus, die Shim-Startprogramms beginnt</span><span class="sxs-lookup"><span data-stu-id="258d1-266">Add a project that starts the Shim Launcher executable</span></span>
> * <span data-ttu-id="258d1-267">Konfigurieren Sie das packprojekt</span><span class="sxs-lookup"><span data-stu-id="258d1-267">Configure the packaging project</span></span>

<span data-ttu-id="258d1-268">Wenn Sie fertig sind, wird Ihre Lösung wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="258d1-268">When you're done, your solution will look something like this.</span></span>

![Abgeschlossene Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

<span data-ttu-id="258d1-270">In diesem Beispiel wird jedes Projekt betrachten.</span><span class="sxs-lookup"><span data-stu-id="258d1-270">Let's look at each project in this example.</span></span>

| <span data-ttu-id="258d1-271">Projekt</span><span class="sxs-lookup"><span data-stu-id="258d1-271">Project</span></span> | <span data-ttu-id="258d1-272">Zweck</span><span class="sxs-lookup"><span data-stu-id="258d1-272">Purpose</span></span> |
|-------|-----------|
| <span data-ttu-id="258d1-273">DesktopApplicationPackage</span><span class="sxs-lookup"><span data-stu-id="258d1-273">DesktopApplicationPackage</span></span> | <span data-ttu-id="258d1-274">Dieses Projekt wird basierend auf der [Windows-Anwendungspakete Project](desktop-to-uwp-packaging-dot-net.md) , und es gibt die MSIX-Paket.</span><span class="sxs-lookup"><span data-stu-id="258d1-274">This project is based on the [Windows Application Packaging project](desktop-to-uwp-packaging-dot-net.md) and it outputs the the MSIX package.</span></span> |
| <span data-ttu-id="258d1-275">Runtimefix</span><span class="sxs-lookup"><span data-stu-id="258d1-275">Runtimefix</span></span> | <span data-ttu-id="258d1-276">Dies ist ein C++ Dynamic-Linked Bibliotheksprojekt, die eine oder mehrere Replacement-Funktionen enthält, die als die Laufzeit Korrektur dienen.</span><span class="sxs-lookup"><span data-stu-id="258d1-276">This is a C++ Dynamic-Linked Library project that contains one or more replacement functions that serve as the runtime fix.</span></span> |
| <span data-ttu-id="258d1-277">ShimLauncher</span><span class="sxs-lookup"><span data-stu-id="258d1-277">ShimLauncher</span></span> | <span data-ttu-id="258d1-278">Dies ist eine leere C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="258d1-278">This is C++ Empty Project.</span></span> <span data-ttu-id="258d1-279">Dieses Projekt ist ein Ort für die Laufzeit verteilbare Dateien von Framework-Support-Paket zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="258d1-279">This project is a place to collect the runtime distributable files of the Package Support Framework.</span></span> <span data-ttu-id="258d1-280">Es gibt eine ausführbare Datei aus.</span><span class="sxs-lookup"><span data-stu-id="258d1-280">It outputs an executable file.</span></span> <span data-ttu-id="258d1-281">Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe starten.</span><span class="sxs-lookup"><span data-stu-id="258d1-281">That executable is the first thing that runs when you start the solution.</span></span> |
| <span data-ttu-id="258d1-282">WinFormsDesktopApplication</span><span class="sxs-lookup"><span data-stu-id="258d1-282">WinFormsDesktopApplication</span></span> | <span data-ttu-id="258d1-283">Dieses Projekt enthält den Quellcode der desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-283">This project contains the source code of a desktop application.</span></span> |

<span data-ttu-id="258d1-284">Um ein vollständiges Beispiel betrachten, die alle der folgenden Typen von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span><span class="sxs-lookup"><span data-stu-id="258d1-284">To look at a complete sample that contains all of these types of projects, see [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span></span>

<span data-ttu-id="258d1-285">Lassen Sie uns die Schritte zum Erstellen und konfigurieren Sie jeden dieser Projekte in der Projektmappe durchgehen.</span><span class="sxs-lookup"><span data-stu-id="258d1-285">Let's walk through the steps to create and configure each of these projects in your solution.</span></span>


### <a name="create-a-package-solution"></a><span data-ttu-id="258d1-286">Erstellen einer Lösung Paket</span><span class="sxs-lookup"><span data-stu-id="258d1-286">Create a package solution</span></span>

<span data-ttu-id="258d1-287">Wenn Sie bereits eine Lösung für desktop-Anwendung ist, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="258d1-287">If you don't already have a solution for your desktop application, create a new **Blank Solution** in Visual Studio.</span></span>

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

<span data-ttu-id="258d1-289">Sie möchten möglicherweise auch alle Anwendungsprojekte hinzufügen, die Ihnen.</span><span class="sxs-lookup"><span data-stu-id="258d1-289">You may also want to add any application projects you have.</span></span>

### <a name="add-a-packaging-project"></a><span data-ttu-id="258d1-290">Fügen Sie ein packprojekt</span><span class="sxs-lookup"><span data-stu-id="258d1-290">Add a packaging project</span></span>

<span data-ttu-id="258d1-291">Wenn Sie bereits ein **Windows-Anwendungsprojekt Verpackung**ist, erstellen Sie eine und Ihrer Lösung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="258d1-291">If you don't already have a **Windows Application Packaging Project**, create one and add it to your solution.</span></span>

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

<span data-ttu-id="258d1-293">Weitere Informationen zu Windows-Anwendung packprojekt finden Sie unter [Package Ihrer Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="258d1-293">For more information on Windows Application Packaging project, see [Package your application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

<span data-ttu-id="258d1-294">Im **Projektmappen-Explorer**mit der rechten Maustaste in des Projekts Verpacken, wählen Sie **Bearbeiten**, und klicken Sie dann am Ende der Projektdatei hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="258d1-294">In **Solution Explorer**, right-click the packaging project, select **Edit**, and then add this to the bottom of the project file:</span></span>

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

### <a name="add-project-for-the-runtime-fix"></a><span data-ttu-id="258d1-295">Fügen Sie für die Korrektur Runtime Projekt hinzu</span><span class="sxs-lookup"><span data-stu-id="258d1-295">Add project for the runtime fix</span></span>

<span data-ttu-id="258d1-296">Fügen Sie ein Projekt C++ **Dynamic-Link Library (DLL)** , zu der Lösung an.</span><span class="sxs-lookup"><span data-stu-id="258d1-296">Add a C++ **Dynamic-Link Library (DLL)** project to the solution.</span></span>

![Fix-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

<span data-ttu-id="258d1-298">Mit der rechten Maustaste die, project, und wählen Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="258d1-298">Right-click the that project, and then choose **Properties**.</span></span>

<span data-ttu-id="258d1-299">In die Eigenschaftenseiten, suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld der **ISO C ++ 17-Standard (/ Std:c ++ 17)** Option.</span><span class="sxs-lookup"><span data-stu-id="258d1-299">In the property pages, find the **C++ Language Standard** field, and then in the drop-down list next to that field, select the **ISO C++17 Standard (/std:c++17)** option.</span></span>

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

<span data-ttu-id="258d1-301">Maustaste auf das Projekt, und wählen Sie dann im Kontextmenü die Option **Manage Nuget Packages** .</span><span class="sxs-lookup"><span data-stu-id="258d1-301">Right-click that project, and then in the context menu, choose the **Manage Nuget Packages** option.</span></span> <span data-ttu-id="258d1-302">Stellen Sie sicher, dass die Option **Paketquelle** auf **Alle** oder **nuget.org**festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="258d1-302">Ensure that the **Package source** option is set to **All** or **nuget.org**.</span></span>

<span data-ttu-id="258d1-303">Klicken Sie auf dem einstellungssymbol weiter dieses Feld.</span><span class="sxs-lookup"><span data-stu-id="258d1-303">Click the settings icon next that field.</span></span>

<span data-ttu-id="258d1-304">Suchen Sie nach der *PSF*\* Nuget-Paket, und installieren Sie sie für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="258d1-304">Search for the *PSF*\* Nuget package, and then install it for this project.</span></span>

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

<span data-ttu-id="258d1-306">Wenn Sie Debuggen oder beim Erweitern eines vorhandenen Runtime Fix möchten, fügen Sie die Common Language Runtime Fix-Dateien, die Sie mithilfe der Anleitung beschriebenen im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs abgerufen.</span><span class="sxs-lookup"><span data-stu-id="258d1-306">If you want to debug or extend an existing runtime fix, add the runtime fix files that you obtained by using the guidance described in the [Find a runtime fix](#find) section of this guide.</span></span>

<span data-ttu-id="258d1-307">Wenn Sie eine völlig neue Lösung erstellen möchten, fügen Sie nicht Suchzeichenfolge diesem Projekt noch hinzu.</span><span class="sxs-lookup"><span data-stu-id="258d1-307">If you intend to create a brand new fix, don't add anything to this project just yet.</span></span> <span data-ttu-id="258d1-308">Wir helfen Ihnen, die richtigen Dateien in diesem Projekt weiter unten in diesem Handbuch hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="258d1-308">We'll help you add the right files to this project later in this guide.</span></span> <span data-ttu-id="258d1-309">Jetzt werden wir Einrichten Ihrer Lösung fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="258d1-309">For now, we'll continue setting up your solution.</span></span>

### <a name="add-a-project-that-starts-the-shim-launcher-executable"></a><span data-ttu-id="258d1-310">Fügen Sie ein Projekt aus, die Shim-Startprogramms beginnt</span><span class="sxs-lookup"><span data-stu-id="258d1-310">Add a project that starts the Shim Launcher executable</span></span>

<span data-ttu-id="258d1-311">Fügen Sie ein Projekt C++ **Leeres Projekt** , zu der Lösung an.</span><span class="sxs-lookup"><span data-stu-id="258d1-311">Add a C++ **Empty Project** project to the solution.</span></span>

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

<span data-ttu-id="258d1-313">Hinzufügen des **PSF** Nuget-Pakets diesem Projekt mit den gleichen Leitfäden, die im vorherigen Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="258d1-313">Add the **PSF** Nuget package to this project by using the same guidance described in the previous section.</span></span>

<span data-ttu-id="258d1-314">Öffnen die Eigenschaftenseiten für das Projekt, und klicken Sie auf der Seite **Allgemein** Einstellungen legen Sie die **Ziel-Name** -Eigenschaft auf ``ShimLauncher32`` oder ``ShimLauncher64`` je nach der Architektur der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-314">Open the property pages for the project, and in the **General** settings page, set the **Target Name** property to ``ShimLauncher32`` or ``ShimLauncher64`` depending on the architecture of your application.</span></span>

![Shim Launcher Verweis](images/desktop-to-uwp/shim-exe-reference.png)

<span data-ttu-id="258d1-316">Fügen Sie einen Projektverweis auf das Projekt Common Language Runtime Fix in Ihrer Lösung hinzu.</span><span class="sxs-lookup"><span data-stu-id="258d1-316">Add a project reference to the runtime fix project in your solution.</span></span>

![Common Language Runtime Fix-Verweis](images/desktop-to-uwp/reference-fix.png)

<span data-ttu-id="258d1-318">Mit der rechten Maustaste in des Verweis, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.</span><span class="sxs-lookup"><span data-stu-id="258d1-318">Right-click the reference, and then in the **Properties** window, apply these values.</span></span>

| <span data-ttu-id="258d1-319">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="258d1-319">Property</span></span> | <span data-ttu-id="258d1-320">Wert</span><span class="sxs-lookup"><span data-stu-id="258d1-320">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="258d1-321">Kopieren der lokalen</span><span class="sxs-lookup"><span data-stu-id="258d1-321">Copy local</span></span> | <span data-ttu-id="258d1-322">Wahr</span><span class="sxs-lookup"><span data-stu-id="258d1-322">True</span></span> |
| <span data-ttu-id="258d1-323">Lokale Satellitenassemblys kopieren</span><span class="sxs-lookup"><span data-stu-id="258d1-323">Copy Local Satellite Assemblies</span></span> | <span data-ttu-id="258d1-324">Wahr</span><span class="sxs-lookup"><span data-stu-id="258d1-324">True</span></span> |
| <span data-ttu-id="258d1-325">Referenz-Assembly-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="258d1-325">Reference Assembly Output</span></span> | <span data-ttu-id="258d1-326">Wahr</span><span class="sxs-lookup"><span data-stu-id="258d1-326">True</span></span> |
| <span data-ttu-id="258d1-327">Link Library Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="258d1-327">Link Library Dependencies</span></span> | <span data-ttu-id="258d1-328">False</span><span class="sxs-lookup"><span data-stu-id="258d1-328">False</span></span> |
| <span data-ttu-id="258d1-329">Link Library Abhängigkeit Eingaben</span><span class="sxs-lookup"><span data-stu-id="258d1-329">Link Library Dependency Inputs</span></span> | <span data-ttu-id="258d1-330">False</span><span class="sxs-lookup"><span data-stu-id="258d1-330">False</span></span> |

### <a name="configure-the-packaging-project"></a><span data-ttu-id="258d1-331">Konfigurieren Sie das packprojekt</span><span class="sxs-lookup"><span data-stu-id="258d1-331">Configure the packaging project</span></span>

<span data-ttu-id="258d1-332">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="258d1-332">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

<span data-ttu-id="258d1-334">Wählen Sie das Shim-Projekt Launcher und Ihrem desktop-Anwendung-Projekt, und wählen Sie dann auf die Schaltfläche **OK** .</span><span class="sxs-lookup"><span data-stu-id="258d1-334">Choose the shim launcher project and your desktop application project, and then choose the **OK** button.</span></span>

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> <span data-ttu-id="258d1-336">Wenn Sie den Quellcode für die Anwendung ist, wählen Sie nur das Shim Startprogramm-Projekt.</span><span class="sxs-lookup"><span data-stu-id="258d1-336">If you don't have the source code to your application, just choose the shim launcher project.</span></span> <span data-ttu-id="258d1-337">Wir können Ihnen zeigen, wie auf die EXE-Datei zu verweisen, wenn Sie eine Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="258d1-337">We'll show you how to reference your executable when you create a configuration file.</span></span>

<span data-ttu-id="258d1-338">In den Knoten **Applications** Maustaste auf das Startprogramm für die Shim und wählen Sie dann auf **als Einstiegspunkt festgelegt**.</span><span class="sxs-lookup"><span data-stu-id="258d1-338">In the **Applications** node, right-click the shim launcher application, and then choose **Set as Entry Point**.</span></span>

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

<span data-ttu-id="258d1-340">Hinzufügen einer Datei mit dem Namen ``config.json`` Sie Ihrem packprojekt Sie dann kopieren und fügen Sie den folgenden Json-Text in die Datei.</span><span class="sxs-lookup"><span data-stu-id="258d1-340">Add a file named ``config.json`` to your packaging project, then, copy and paste the following json text into the file.</span></span> <span data-ttu-id="258d1-341">Legen Sie die **Paket-Action** -Eigenschaft auf **Inhalt**.</span><span class="sxs-lookup"><span data-stu-id="258d1-341">Set the **Package Action** property to **Content**.</span></span>

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
<span data-ttu-id="258d1-342">Geben Sie einen Wert für jeden Schlüssel ein.</span><span class="sxs-lookup"><span data-stu-id="258d1-342">Provide a value for each key.</span></span> <span data-ttu-id="258d1-343">Verwenden Sie die folgende Tabelle als Leitfaden.</span><span class="sxs-lookup"><span data-stu-id="258d1-343">Use this table as a guide.</span></span>

| <span data-ttu-id="258d1-344">Array</span><span class="sxs-lookup"><span data-stu-id="258d1-344">Array</span></span> | <span data-ttu-id="258d1-345">key</span><span class="sxs-lookup"><span data-stu-id="258d1-345">key</span></span> | <span data-ttu-id="258d1-346">Wert</span><span class="sxs-lookup"><span data-stu-id="258d1-346">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="258d1-347">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-347">applications</span></span> | <span data-ttu-id="258d1-348">id</span><span class="sxs-lookup"><span data-stu-id="258d1-348">id</span></span> |  <span data-ttu-id="258d1-349">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` -Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="258d1-349">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="258d1-350">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-350">applications</span></span> | <span data-ttu-id="258d1-351">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-351">executable</span></span> | <span data-ttu-id="258d1-352">Die Paket-Relative Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-352">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="258d1-353">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="258d1-353">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="258d1-354">Es ist der Wert der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="258d1-354">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="258d1-355">applications</span><span class="sxs-lookup"><span data-stu-id="258d1-355">applications</span></span> | <span data-ttu-id="258d1-356">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="258d1-356">workingDirectory</span></span> | <span data-ttu-id="258d1-357">(Optional) Ein Paket relativer Pfad als das Arbeitsverzeichnis der Anwendung verwenden, die beginnt.</span><span class="sxs-lookup"><span data-stu-id="258d1-357">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="258d1-358">Wenn Sie diesen Wert nicht festlegen, das Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="258d1-358">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="258d1-359">Prozesse</span><span class="sxs-lookup"><span data-stu-id="258d1-359">processes</span></span> | <span data-ttu-id="258d1-360">ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-360">executable</span></span> | <span data-ttu-id="258d1-361">In den meisten Fällen wird dies der Name der werden die `executable` konfigurierten oberhalb der Pfad und Dateiname Erweiterung entfernt.</span><span class="sxs-lookup"><span data-stu-id="258d1-361">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="258d1-362">Shims</span><span class="sxs-lookup"><span data-stu-id="258d1-362">shims</span></span> | <span data-ttu-id="258d1-363">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="258d1-363">dll</span></span> | <span data-ttu-id="258d1-364">Paket-relativer Pfad zu der Shim-DLL geladen werden.</span><span class="sxs-lookup"><span data-stu-id="258d1-364">Package-relative path to the shim DLL to load.</span></span> |
| <span data-ttu-id="258d1-365">Shims</span><span class="sxs-lookup"><span data-stu-id="258d1-365">shims</span></span> | <span data-ttu-id="258d1-366">config</span><span class="sxs-lookup"><span data-stu-id="258d1-366">config</span></span> | <span data-ttu-id="258d1-367">(Optional) Steuert das Verhalten der Shim dl.</span><span class="sxs-lookup"><span data-stu-id="258d1-367">(Optional) Controls how the shim dl behaves.</span></span> <span data-ttu-id="258d1-368">Das genaue Format dieses Werts variiert für einzelne Shim-durch-Shim wie jedes Shim wie diesmal dieser "Blob" interpretiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="258d1-368">The exact format of this value varies on a shim-by-shim basis as each shim can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="258d1-369">Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt.</span><span class="sxs-lookup"><span data-stu-id="258d1-369">When you're done, your ``config.json`` file will look something like this.</span></span>

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
> <span data-ttu-id="258d1-370">Die `applications`, `processes`, und `shims` Schlüssel Arrays sind.</span><span class="sxs-lookup"><span data-stu-id="258d1-370">The `applications`, `processes`, and `shims` keys are arrays.</span></span> <span data-ttu-id="258d1-371">Dies bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozesse und Shim-DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="258d1-371">That means that you can use the config.json file to specify more than one application, process, and shim DLL.</span></span>

### <a name="debug-a-runtime-fix"></a><span data-ttu-id="258d1-372">Debuggen eines Fixes Common Language runtime</span><span class="sxs-lookup"><span data-stu-id="258d1-372">Debug a runtime fix</span></span>

<span data-ttu-id="258d1-373">Drücken Sie F5, um den Debugger starten Sie in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="258d1-373">In Visual Studio, press F5 to start the debugger.</span></span>  <span data-ttu-id="258d1-374">Als erstes, die beginnt ist die Shim-Start-Anwendung, die wiederum die Ziel-desktop-Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="258d1-374">The first thing that starts is the shim launcher application, which in turn, starts your target desktop application.</span></span>  <span data-ttu-id="258d1-375">Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell an den Prozess desktop-Anwendung anfügen, indem Sie auf **Debuggen**->**an den Prozess anhängen**, auswählen und dann auf den Anwendungsprozess.</span><span class="sxs-lookup"><span data-stu-id="258d1-375">To debug the target desktop application, you'll have to manually attach to the desktop application process by choosing **Debug**->**Attach to Process**, and then selecting the application process.</span></span> <span data-ttu-id="258d1-376">Um das Debuggen einer Anwendung .NET mit einer einheitlichen Runtime Fix DLL zu ermöglichen, wählen Sie verwaltete und systemeigenem Code (Debuggen im gemischten Modus).</span><span class="sxs-lookup"><span data-stu-id="258d1-376">To permit the debugging of a .NET application with a native runtime fix DLL, select managed and native code types (mixed mode debugging).</span></span>  

<span data-ttu-id="258d1-377">Nachdem Sie diese eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und die Laufzeit Fix-Projekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="258d1-377">Once you've set this up, you can set break points next to lines of code in the desktop application code and the runtime fix project.</span></span> <span data-ttu-id="258d1-378">Wenn Sie den Quellcode für die Anwendung ist, können Sie Haltepunkte nur neben Codezeilen im Projekt Common Language Runtime Fix festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="258d1-378">If you don't have the source code to your application, you'll be able to set break points only next to lines of code in your runtime fix project.</span></span>

>[!NOTE]
> <span data-ttu-id="258d1-379">Während der Visual Studio können Sie die einfachste Entwicklung und Debuggen, sind einige Einschränkungen, also weiter unten in diesem Handbuch besprechen andere Debuggingverfahren wir, die Sie anwenden können.</span><span class="sxs-lookup"><span data-stu-id="258d1-379">While Visual Studio gives you the simplest development and debugging experience, there are some limitations, so later in this guide, we'll discuss other debugging techniques that you can apply.</span></span>

## <a name="create-a-runtime-fix"></a><span data-ttu-id="258d1-380">Erstellen Sie ein Update der Common Language runtime</span><span class="sxs-lookup"><span data-stu-id="258d1-380">Create a runtime fix</span></span>

<span data-ttu-id="258d1-381">Wenn es keine noch eine Laufzeit für das Problem beheben, dass Sie beheben möchten, können Sie eine neue Laufzeit Fix durch Schreiben Replacement-Funktionen und alle Konfigurationsdaten einschließlich erstellen sinnvoll, die zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="258d1-381">If there isn't yet a runtime fix for the issue that you want to resolve, you can create a new runtime fix by writing replacement functions and including any configuration data that makes sense.</span></span> <span data-ttu-id="258d1-382">Betrachten Sie jeden Teil.</span><span class="sxs-lookup"><span data-stu-id="258d1-382">Let's look at each part.</span></span>

### <a name="replacement-functions"></a><span data-ttu-id="258d1-383">Ersatzfunktionen</span><span class="sxs-lookup"><span data-stu-id="258d1-383">Replacement functions</span></span>

<span data-ttu-id="258d1-384">Bestimmen Sie zunächst, welche Funktion Aufrufe schlagen fehl, wenn die Anwendung in einem Container MSIX ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="258d1-384">First, identify which function calls fail when your application runs in an MSIX container.</span></span> <span data-ttu-id="258d1-385">Anschließend können Sie Replacement-Funktionen erstellen, die Sie den Laufzeit-Manager stattdessen aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-385">Then, you can create replacement functions that you'd like the runtime manager to call instead.</span></span> <span data-ttu-id="258d1-386">Dies gibt Ihnen eine Gelegenheit, ersetzen Sie die Implementierung einer Funktion mit Verhalten, das die Regeln für die moderne Laufzeitumgebung entspricht.</span><span class="sxs-lookup"><span data-stu-id="258d1-386">This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.</span></span>

<span data-ttu-id="258d1-387">Öffnen Sie in Visual Studio das Runtime Fix-Projekt, das Sie weiter oben in diesem Handbuch erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="258d1-387">In Visual Studio, open the runtime fix project that you created earlier in this guide.</span></span>

<span data-ttu-id="258d1-388">Deklarieren der ``SHIM_DEFINE_EXPORTS`` Makro, und fügen Sie eine Include-Anweisung für die `shim_framework.h` am oberen Rand jeder. CPP-Datei für die Funktionen der Common Language Runtime-Updates hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-388">Declare the ``SHIM_DEFINE_EXPORTS`` macro and then add a include statement for the `shim_framework.h` at the top of each .CPP file where you intend to add the functions of your runtime fix.</span></span>

```c++
#define SHIM_DEFINE_EXPORTS
#include <shim_framework.h>
```
>[!IMPORTANT]
><span data-ttu-id="258d1-389">Stellen Sie sicher, dass die `SHIM_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="258d1-389">Make sure that the `SHIM_DEFINE_EXPORTS` macro appears before the include statement.</span></span>

<span data-ttu-id="258d1-390">Erstellen Sie eine Funktion, die die gleiche Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="258d1-390">Create a function that has the same signature of the function who's behavior you want to modify.</span></span> <span data-ttu-id="258d1-391">Es folgt eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.</span><span class="sxs-lookup"><span data-stu-id="258d1-391">Here's an example function that replaces the `MessageBoxW` function.</span></span>

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

<span data-ttu-id="258d1-392">Der Aufruf von `DECLARE_SHIM` ordnet die `MessageBoxW` Funktion, um Ihre neue Replacement-Funktion.</span><span class="sxs-lookup"><span data-stu-id="258d1-392">The call to `DECLARE_SHIM` maps the `MessageBoxW` function to your new replacement function.</span></span> <span data-ttu-id="258d1-393">Wenn die Anwendung versucht, rufen Sie die `MessageBoxW` -Funktion; er ruft die Replacement-Funktion stattdessen.</span><span class="sxs-lookup"><span data-stu-id="258d1-393">When your application attempts to call the `MessageBoxW` function, it will call the replacement function instead.</span></span>

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a><span data-ttu-id="258d1-394">Schutz vor rekursive Aufrufe von Funktionen in Common Language Runtime-Updates</span><span class="sxs-lookup"><span data-stu-id="258d1-394">Protect against recursive calls to functions in runtime fixes</span></span>

<span data-ttu-id="258d1-395">Optional können Sie anwenden der `reentrancy_guard` Typ auf die Funktionen, die Schutz vor rekursive Aufrufe von Funktionen in Common Language Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="258d1-395">You can optionally apply the `reentrancy_guard` type to your functions that protect against recursive calls to functions in runtime fixes.</span></span>

<span data-ttu-id="258d1-396">Sie können beispielsweise eine Funktion Ersatz für erzeugen die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="258d1-396">For example, you might produce a replacement function for the `CreateFile` function.</span></span> <span data-ttu-id="258d1-397">Rufen Sie möglicherweise die Implementierung der `CopyFile` -Funktion, aber die Implementierung der der `CopyFile` Funktionsaufruf möglicherweise die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="258d1-397">Your implementation might call the `CopyFile` function, but the implementation of the `CopyFile` function might call the `CreateFile` function.</span></span> <span data-ttu-id="258d1-398">Dies kann dazu führen, dass ein unendlichen rekursiven Lebenszyklus von Anrufen an die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="258d1-398">This may lead to an infinite recursive cycle of calls to the `CreateFile` function.</span></span>

<span data-ttu-id="258d1-399">Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span><span class="sxs-lookup"><span data-stu-id="258d1-399">For more information on `reentrancy_guard` see [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span></span>

### <a name="configuration-data"></a><span data-ttu-id="258d1-400">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="258d1-400">Configuration data</span></span>

<span data-ttu-id="258d1-401">Wenn Sie Daten zur Konfiguration der Common Language Runtime Fix hinzufügen möchten, sollten Sie es zum Hinzufügen der ``config.json``.</span><span class="sxs-lookup"><span data-stu-id="258d1-401">If you want to add configuration data to your runtime fix, consider adding it to the ``config.json``.</span></span> <span data-ttu-id="258d1-402">Auf diese Weise können die `ShimQueryCurrentDllConfig` , diese Daten auf einfache Weise zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="258d1-402">That way, you can use the `ShimQueryCurrentDllConfig` to easily parse that data.</span></span> <span data-ttu-id="258d1-403">In diesem Beispiel wird analysiert einen Boolean und String-Wert aus dieser Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="258d1-403">This example parses a boolean and string value from that configuration file.</span></span>

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

## <a name="other-debugging-techniques"></a><span data-ttu-id="258d1-404">Andere Debuggingverfahren</span><span class="sxs-lookup"><span data-stu-id="258d1-404">Other debugging techniques</span></span>

<span data-ttu-id="258d1-405">Während der Visual Studio Sie die einfachste Entwicklung und Debuggen können, sind einige Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="258d1-405">While Visual Studio gives you the simplest development and debugging experience, there are some limitations.</span></span>

<span data-ttu-id="258d1-406">F5-debugging führt Sie zuerst die Anwendung lose Dateien aus dem Paket Layout Ordnerpfad bereitstellen, anstatt aus einem Paket .appx installiert.</span><span class="sxs-lookup"><span data-stu-id="258d1-406">First, F5 debugging runs the application by deploying loose files from the package layout folder path, rather than installing from a .appx package.</span></span>  <span data-ttu-id="258d1-407">Der Layout-Ordner haben die gleiche sicherheitseinschränkungen als eine installierte Paketordner in der Regel nicht.</span><span class="sxs-lookup"><span data-stu-id="258d1-407">The layout folder typically does not have the same security restrictions as an installed package folder.</span></span> <span data-ttu-id="258d1-408">Daher kann es nicht Paket Pfad Denial-Zugriffsfehlern vor dem Anwenden eines Fixes Runtime reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="258d1-408">As a result, it may not be possible to reproduce package path access denial errors prior to applying a runtime fix.</span></span>

<span data-ttu-id="258d1-409">Verwenden Sie zur Behebung dieses Problems .appx paketbereitstellung anstelle von F5 lose Datei-Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="258d1-409">To address this issue, use .appx package deployment rather than F5 loose file deployment.</span></span>  <span data-ttu-id="258d1-410">Um eine .appx Package-Datei zu erstellen, verwenden Sie das Dienstprogramm [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="258d1-410">To create a .appx package file, use the [MakeAppx](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) utility from the Windows SDK, as described above.</span></span> <span data-ttu-id="258d1-411">Oder, innerhalb von Visual Studio Maustaste auf den Projektknoten für die Anwendung und wählen **Store**->**App-Pakete zu erstellen**.</span><span class="sxs-lookup"><span data-stu-id="258d1-411">Or, from within Visual Studio, right-click your application project node and select **Store**->**Create App Packages**.</span></span>

<span data-ttu-id="258d1-412">Ein weiteres Problem mit Visual Studio ist, dass sie nicht über integrierte Unterstützung zum Anfügen an untergeordnete Prozesse, die vom Debugger gestartet besitzt.</span><span class="sxs-lookup"><span data-stu-id="258d1-412">Another issue with Visual Studio is that it does not have built-in support for attaching to any child processes launched by the debugger.</span></span>   <span data-ttu-id="258d1-413">Dies erschwert das Debuggen von Geschäftslogik in Startpfad der Zielanwendung, die nach der Einführung von Visual Studio manuell angefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="258d1-413">This makes it difficult to debug logic in the startup path of the target application, which must be manually attached by Visual Studio after launch.</span></span>

<span data-ttu-id="258d1-414">Um dieses Problem zu beheben, verwenden Sie einen Debugger anfügen untergeordneter Prozess unterstützt.</span><span class="sxs-lookup"><span data-stu-id="258d1-414">To address this issue, use a debugger that supports child process attach.</span></span>  <span data-ttu-id="258d1-415">Beachten Sie, dass es im Allgemeinen nicht Just-in-Time (JUST-in) auf die Zielanwendung Debuggen möglich ist.</span><span class="sxs-lookup"><span data-stu-id="258d1-415">Note that it is generally not possible to attach a just-in-time (JIT) debugger to the target application.</span></span>  <span data-ttu-id="258d1-416">Dies ist, da die meisten JIT Techniken umfassen des Debuggers an der Stelle der Ziel-app über den Registrierungsschlüssel ImageFileExecutionOptions.</span><span class="sxs-lookup"><span data-stu-id="258d1-416">This is because most JIT techniques involve launching the debugger in place of the target app, via the ImageFileExecutionOptions registry key.</span></span>  <span data-ttu-id="258d1-417">Detouring ein Mechanismus, mit ShimLauncher.exe ShimRuntime.dll in die Ziel-app einfügen wird dadurch zunichte gemacht.</span><span class="sxs-lookup"><span data-stu-id="258d1-417">This defeats the detouring mechanism used by ShimLauncher.exe to inject ShimRuntime.dll into the target app.</span></span>  <span data-ttu-id="258d1-418">WinDbg, in der [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)abgerufen unterstützt untergeordneter Prozess anfügen.</span><span class="sxs-lookup"><span data-stu-id="258d1-418">WinDbg, included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index), and obtained from the [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), supports child process attach.</span></span>  <span data-ttu-id="258d1-419">Unterstützt jetzt auch direkt [Starten und eine UWP app zu debuggen](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span><span class="sxs-lookup"><span data-stu-id="258d1-419">It also now supports directly [launching and debugging a UWP app](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span></span>

<span data-ttu-id="258d1-420">Zum Starten der Anwendung Ziel als untergeordneter Prozess Debuggen starten ``WinDbg``.</span><span class="sxs-lookup"><span data-stu-id="258d1-420">To debug target application startup as a child process, start ``WinDbg``.</span></span>

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

<span data-ttu-id="258d1-421">Bei der ``WinDbg`` auffordern, aktivieren Sie untergeordneten Debuggen und entsprechenden Haltepunkte festlegen.</span><span class="sxs-lookup"><span data-stu-id="258d1-421">At the ``WinDbg`` prompt, enable child debugging and set appropriate breakpoints.</span></span>

```
.childdbg 1
g
```
<span data-ttu-id="258d1-422">(wird ausgeführt, bis Zielanwendung startet und unterbricht)</span><span class="sxs-lookup"><span data-stu-id="258d1-422">(execute until target application starts and breaks into the debugger)</span></span>

```
sxe ld fixup.dll
g
```
<span data-ttu-id="258d1-423">(führen Sie bis die Korrektur aus die DLL-Datei geladen wird aus)</span><span class="sxs-lookup"><span data-stu-id="258d1-423">(execute until the fixup DLL is loaded)</span></span>

```
bp ...
```

>[!NOTE]
> <span data-ttu-id="258d1-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) kann auch verwendet werden, um eine app beim Start Debuggen, und auch in der [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="258d1-424">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) can be also used to attach a debugger to an app upon launch, and is also included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index).</span></span>  <span data-ttu-id="258d1-425">Es ist jedoch komplexer als das direkte unterstützt jetzt WinDbg verwenden.</span><span class="sxs-lookup"><span data-stu-id="258d1-425">However, it is more complex to use than the direct support now provided by WinDbg.</span></span>

## <a name="support-and-feedback"></a><span data-ttu-id="258d1-426">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="258d1-426">Support and feedback</span></span>

**<span data-ttu-id="258d1-427">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="258d1-427">Find answers to your questions</span></span>**

<span data-ttu-id="258d1-428">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="258d1-428">Have questions?</span></span> <span data-ttu-id="258d1-429">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="258d1-429">Ask us on Stack Overflow.</span></span> <span data-ttu-id="258d1-430">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="258d1-430">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="258d1-431">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="258d1-431">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>
