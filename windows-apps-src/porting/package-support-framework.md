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
ms.openlocfilehash: d4b4cae2e135f7a66cd68192faabeffdb309a909
ms.sourcegitcommit: 232543fba1fb30bb1489b053310ed6bd4b8f15d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "4174853"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a><span data-ttu-id="b7cfe-103">Wenden Sie-Runtime-Updates zu einem MSIX-Paket mit dem Paket Support-Framework</span><span class="sxs-lookup"><span data-stu-id="b7cfe-103">Apply runtime fixes to an MSIX package by using the Package Support Framework</span></span>

<span data-ttu-id="b7cfe-104">Das Paket Support-Framework ist ein open-Source-Kit, das hilft Ihnen, wenden Sie Updates für Ihre vorhandenen Win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode, haben, damit sie in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-104">The Package Support Framework is an open source kit that helps you apply fixes to your existing win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="b7cfe-105">Das Paket Support-Framework hilft Ihrer Anwendung, führen Sie die bewährten Methoden der modernen-Runtime-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-105">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

<span data-ttu-id="b7cfe-106">Weitere Informationen hierzu finden Sie unter [Paket Unterstützung Framework](https://docs.microsoft.com/windows/msix/package-support-framework-overview).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-106">To learn more, see [Package Support Framework](https://docs.microsoft.com/windows/msix/package-support-framework-overview).</span></span>

<span data-ttu-id="b7cfe-107">Dieses Handbuch hilft Ihnen, Probleme mit der Anwendungskompatibilität zu identifizieren und zum Suchen, anwenden und erweitern Runtime behebt, die sie beheben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-107">This guide will help you to identify application compatibility issues, and to find, apply, and extend runtime fixes that address them.</span></span>

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a><span data-ttu-id="b7cfe-108">Identifizieren Sie verpackte Probleme mit der Anwendungskompatibilität</span><span class="sxs-lookup"><span data-stu-id="b7cfe-108">Identify packaged application compatibility issues</span></span>

<span data-ttu-id="b7cfe-109">Erstellen Sie zunächst ein Paket für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-109">First, create a package for your application.</span></span> <span data-ttu-id="b7cfe-110">Installieren Sie es dann, und beobachten Sie, führen Sie es.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-110">Then, install it, run it, and observe its behavior.</span></span> <span data-ttu-id="b7cfe-111">Sie erhalten möglicherweise Fehlermeldungen, mit denen Sie eine Kompatibilitätsprobleme identifizieren können.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-111">You might receive error messages that can help you identify a compatibility issue.</span></span> <span data-ttu-id="b7cfe-112">Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-112">You can also use [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) to identify issues.</span></span>  <span data-ttu-id="b7cfe-113">Allgemeine Probleme beziehen sich auf Anwendung Annahmen in Bezug auf die Berechtigungen arbeiten Verzeichnis und Programm Pfad.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-113">Common issues relate to application assumptions regarding the working directory and program path permissions.</span></span>

### <a name="using-process-monitor-to-identify-an-issue"></a><span data-ttu-id="b7cfe-114">Verwenden Process Monitor zum Identifizieren der ein Problem</span><span class="sxs-lookup"><span data-stu-id="b7cfe-114">Using Process Monitor to identify an issue</span></span>

<span data-ttu-id="b7cfe-115">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm ermöglicht Ihnen, eine app Datei- und Registrierungsvorgänge und die Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-115">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) is a powerful utility for observing an app's file and registry operations, and their results.</span></span>  <span data-ttu-id="b7cfe-116">Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-116">This can help you to understand application compatibility issues.</span></span>  <span data-ttu-id="b7cfe-117">Fügen Sie nach dem Öffnen Prozess überwachen, einen Filter hinzu (Filter > Filter...) nur Ereignisse für die Anwendung ausführbare enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-117">After opening Process Monitor, add a filter (Filter > Filter…) to include only events from the application executable.</span></span>

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

<span data-ttu-id="b7cfe-119">Eine Liste der Ereignisse wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-119">A list of events will appear.</span></span> <span data-ttu-id="b7cfe-120">Für viele dieser Ereignisse wird das Wort **Erfolg** in der Spalte **Ergebnis** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-120">For many of these events, the word **SUCCESS** will appear in the **Result** column.</span></span>

![ProcMon-Ereignisse](images/desktop-to-uwp/procmon_events.png)

<span data-ttu-id="b7cfe-122">Optional können Sie Ereignisse, um nur Fehler nur anzeigen filtern.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-122">Optionally, you can filter events to only show only failures.</span></span>

![ProcMon ausschließen Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

<span data-ttu-id="b7cfe-124">Wenn Sie einen Dateisystem Zugriff Fehler vermuten, suchen Sie nach fehlgeschlagenen Ereignisse, die unter der System32/SysWOW64 oder der Paketpfad Datei sind.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-124">If you suspect a filesystem access failure, search for failed events that are under either the System32/SysWOW64 or the package file path.</span></span> <span data-ttu-id="b7cfe-125">Filter können auch hier zu helfen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-125">Filters can also help here, too.</span></span> <span data-ttu-id="b7cfe-126">Starten Sie am unteren Rand der Liste, und führen Sie einen Bildlauf nach oben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-126">Start at the bottom of this list and scroll upwards.</span></span> <span data-ttu-id="b7cfe-127">Fehler, die am unteren Rand der Liste angezeigt werden, sind die zuletzt aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-127">Failures that appear at the bottom of this list have occurred most recently.</span></span> <span data-ttu-id="b7cfe-128">Die meisten geachtet werden, Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten und "Pfad/Name nicht gefunden", und Dinge, die nicht verdächtige aussehen zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-128">Pay most attention to errors that contain strings such as "access denied," and "path/name not found", and ignore things that don't look suspicious.</span></span> <span data-ttu-id="b7cfe-129">Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-129">The [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) has two issues.</span></span> <span data-ttu-id="b7cfe-130">Sie können diese Probleme in der Liste angezeigt, die in der folgenden Abbildung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-130">You can see those issues in the list that appears in the following image.</span></span>

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

<span data-ttu-id="b7cfe-132">In der ersten Ausgabe, die in diesem Bild angezeigt wird, wird die Anwendung nicht aus der Datei "Config.txt" gelesen, die im Pfad "C:\Windows\SysWOW64" befindet.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-132">In the first issue that appears in this image, the application is failing to read from the "Config.txt" file that is located in the "C:\Windows\SysWOW64" path.</span></span> <span data-ttu-id="b7cfe-133">Es ist unwahrscheinlich, dass die Anwendung versucht, diesen Pfad direkt referenzieren.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-133">It's unlikely that the application is trying to reference that path directly.</span></span> <span data-ttu-id="b7cfe-134">In den meisten Fällen versucht, einen relativen Pfad mit aus der Datei gelesen, und "System32/SysWOW64" wird standardmäßig Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-134">Most likely, it's trying to read from that file by using a relative path, and by default, "System32/SysWOW64" is the application's working directory.</span></span> <span data-ttu-id="b7cfe-135">Dies zeigt, dass die Anwendung die aktuelle Arbeitsverzeichnis, das an einer beliebigen Stelle im Paket festgelegt werden, um erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-135">This suggests that the application is expecting its current working directory to be set to somewhere in the package.</span></span> <span data-ttu-id="b7cfe-136">Suchen innerhalb der Appx, sehen Sie, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-136">Looking inside of the appx, we can see that the file exists in the same directory as the executable.</span></span>

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

<span data-ttu-id="b7cfe-138">Das zweite Problem wird in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-138">The second issue appears in the following image.</span></span>

![ProcMon Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

<span data-ttu-id="b7cfe-140">In diesem Problem ist die Anwendung keine log-Datei in der Paketpfad zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-140">In this issue, the application is failing to write a .log file to its package path.</span></span> <span data-ttu-id="b7cfe-141">Dies würde wird empfohlen, eine Datei Umleitung Korrektur hilfreich ist.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-141">This would suggest that a file redirection fixup might help.</span></span>

<a id="find" />

## <a name="find-a-runtime-fix"></a><span data-ttu-id="b7cfe-142">Suchen nach einer Runtime-Lösung</span><span class="sxs-lookup"><span data-stu-id="b7cfe-142">Find a runtime fix</span></span>

<span data-ttu-id="b7cfe-143">Die PSF enthält-Runtime-Updates, die Sie jetzt, wie z. B. die Datei Umleitung Korrektur verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-143">The PSF contains runtime fixes that you can use right now, such as the file redirection fixup.</span></span>

### <a name="file-redirection-fixup"></a><span data-ttu-id="b7cfe-144">Datei Umleitung Korrektur</span><span class="sxs-lookup"><span data-stu-id="b7cfe-144">File Redirection Fixup</span></span>

<span data-ttu-id="b7cfe-145">Die [Datei Umleitung Korrektur](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten initiierten schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung zugänglich ist, die in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-145">You can use the [File Redirection Fixup](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to redirect attempts to write or read data in a directory that isn't accessible from an application that runs in an MSIX container.</span></span>

<span data-ttu-id="b7cfe-146">Z. B. wenn die Anwendung in eine Protokolldatei, der in demselben Verzeichnis wie die ausführbaren Anwendungen ist schreibt, können klicken Sie dann die [Datei Umleitung Korrektur](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie um die Protokolldatei in einen anderen Speicherort, z. B. den lokalen app-Datenspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-146">For example, if your application writes to a log file that is in the same directory as your applications executable, then you can use the [File Redirection Fixup](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to create that log file in another location, such as the local app data store.</span></span>

### <a name="runtime-fixes-from-the-community"></a><span data-ttu-id="b7cfe-147">Runtime-Updates aus der community</span><span class="sxs-lookup"><span data-stu-id="b7cfe-147">Runtime fixes from the community</span></span>

<span data-ttu-id="b7cfe-148">Achten Sie darauf, dass Sie die Community Beiträge zu unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) -Seite zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-148">Make sure to review the community contributions to our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) page.</span></span> <span data-ttu-id="b7cfe-149">Es ist möglich, dass andere Entwickler haben eine ähnliche und Ihrem Problem gelöst ist und ein Laufzeit-Update freigegeben haben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-149">It's possible that other developers have resolved an issue similar to yours and have shared a runtime fix.</span></span>

## <a name="apply-a-runtime-fix"></a><span data-ttu-id="b7cfe-150">Wenden Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b7cfe-150">Apply a runtime fix</span></span>

<span data-ttu-id="b7cfe-151">Sie können eine vorhandene-Runtime-Update mit einigen einfachen Tools aus dem Windows SDK, und wie folgt anwenden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-151">You can apply an existing runtime fix with a few simple tools from the Windows SDK, and by following these steps.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b7cfe-152">Erstellen Sie ein Layout Paketordner</span><span class="sxs-lookup"><span data-stu-id="b7cfe-152">Create a package layout folder</span></span>
> * <span data-ttu-id="b7cfe-153">Die Paket-Unterstützung Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="b7cfe-153">Get the Package Support Framework files</span></span>
> * <span data-ttu-id="b7cfe-154">Fügen Sie zu Ihrem Paket hinzu</span><span class="sxs-lookup"><span data-stu-id="b7cfe-154">Add them to your package</span></span>
> * <span data-ttu-id="b7cfe-155">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="b7cfe-155">Modify the package manifest</span></span>
> * <span data-ttu-id="b7cfe-156">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b7cfe-156">Create a configuration file</span></span>

<span data-ttu-id="b7cfe-157">Lassen Sie uns über jede Aufgabe geleitet werden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-157">Let's go through each task.</span></span>

### <a name="create-the-package-layout-folder"></a><span data-ttu-id="b7cfe-158">Erstellen Sie den Layout Paketordner</span><span class="sxs-lookup"><span data-stu-id="b7cfe-158">Create the package layout folder</span></span>

<span data-ttu-id="b7cfe-159">Wenn Sie bereits über eine Datei .msix (oder AppX) verfügen, können Sie den Inhalt in einem Layoutordner entpacken, die als die Staging-Bereich für Ihr Paket dient.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-159">If you have a .msix (or .appx) file already, you can unpack its contents into a layout folder that will serve as the staging area for your package.</span></span>  <span data-ttu-id="b7cfe-160">Sie erreichen dies über eine **X64 systemeigenen Tools Eingabeaufforderung für VS 2017**, oder manuell mit dem SDK Bin Pfad in der ausführbaren Pfad.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-160">You can do this from an **x64 Native Tools Command Prompt for VS 2017**, or manually with the SDK bin path in the executable search path.</span></span>

```
makemsix unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.msix /d PackageContents

```

<span data-ttu-id="b7cfe-161">Dadurch erhalten etwas Sie, die wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-161">This will give you something that looks like the following.</span></span>

![Paketlayout](images/desktop-to-uwp/package_contents.png)

<span data-ttu-id="b7cfe-163">Wenn Sie eine Datei .msix (oder AppX) zu besitzen, können Sie die Paketordner und Dateien von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-163">If you don't have a .msix (or .appx) file to start with, you can create the package folder and files from scratch.</span></span>

### <a name="get-the-package-support-framework-files"></a><span data-ttu-id="b7cfe-164">Die Paket-Unterstützung Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="b7cfe-164">Get the Package Support Framework files</span></span>

<span data-ttu-id="b7cfe-165">Sie können das PSF Nuget-Paket abrufen, mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-165">You can get the PSF Nuget package by using Visual Studio.</span></span> <span data-ttu-id="b7cfe-166">Mithilfe des eigenständigen Nuget-Befehlszeilentools können sie auch abrufen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-166">You can also get it by using the standalone Nuget command line tool.</span></span>

#### <a name="get-the-package-by-using-visual-studio"></a><span data-ttu-id="b7cfe-167">Rufen Sie das Paket mithilfe von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b7cfe-167">Get the package by using Visual Studio</span></span>

<span data-ttu-id="b7cfe-168">In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-168">In Visual Studio, right-click your solution or project node and pick one of the Manage Nuget Packages commands.</span></span>  <span data-ttu-id="b7cfe-169">Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , um das Paket unter "NuGet.org" suchen. Anschließend installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-169">Search for **Microsoft.PackageSupportFramework** or **PSF** to find the package on Nuget.org. Then, install it.</span></span>

#### <a name="get-the-package-by-using-the-command-line-tool"></a><span data-ttu-id="b7cfe-170">Rufen Sie das Paket mithilfe des Befehlszeilentools</span><span class="sxs-lookup"><span data-stu-id="b7cfe-170">Get the package by using the command line tool</span></span>

<span data-ttu-id="b7cfe-171">Installieren des Nuget-Befehlszeilentools von diesem Speicherort: https://www.nuget.org/downloads.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-171">Install the Nuget command line tool from this location: https://www.nuget.org/downloads.</span></span> <span data-ttu-id="b7cfe-172">Führen Sie dann über die Befehlszeile Nuget diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b7cfe-172">Then, from the Nuget command line, run this command:</span></span>

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a><span data-ttu-id="b7cfe-173">Fügen Sie die Paket-Support-Framework-Dateien zu Ihrem Paket</span><span class="sxs-lookup"><span data-stu-id="b7cfe-173">Add the Package Support Framework files to your package</span></span>

<span data-ttu-id="b7cfe-174">Erforderliche 32-Bit und 64-Bit-PSF DLL-Dateien und ausführbaren Dateien in das Paketverzeichnis hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-174">Add the required 32-bit and 64-bit PSF  DLLs and executable files to the package directory.</span></span> <span data-ttu-id="b7cfe-175">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-175">Use the following table as a guide.</span></span> <span data-ttu-id="b7cfe-176">Sie sollten auch alle Updates Runtime enthalten, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-176">You'll also want to include any runtime fixes that you need.</span></span> <span data-ttu-id="b7cfe-177">In unserem Beispiel benötigen wir der Datei Umleitung Runtime beheben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-177">In our example, we need the file redirection runtime fix.</span></span>

| <span data-ttu-id="b7cfe-178">Die ausführbare Datei Anwendung ist x64</span><span class="sxs-lookup"><span data-stu-id="b7cfe-178">Application executable is x64</span></span> | <span data-ttu-id="b7cfe-179">Die ausführbare Datei Anwendung ist x86</span><span class="sxs-lookup"><span data-stu-id="b7cfe-179">Application executable is x86</span></span> |
|-------------------------------|-----------|
| [<span data-ttu-id="b7cfe-180">PSFLauncher64.exe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-180">PSFLauncher64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [<span data-ttu-id="b7cfe-181">PSFLauncher32.exe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-181">PSFLauncher32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [<span data-ttu-id="b7cfe-182">PSFRuntime64.dll</span><span class="sxs-lookup"><span data-stu-id="b7cfe-182">PSFRuntime64.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [<span data-ttu-id="b7cfe-183">PSFRuntime32.dll</span><span class="sxs-lookup"><span data-stu-id="b7cfe-183">PSFRuntime32.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [<span data-ttu-id="b7cfe-184">PSFRunDll64.exe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-184">PSFRunDll64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [<span data-ttu-id="b7cfe-185">PSFRunDll32.exe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-185">PSFRunDll32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

<span data-ttu-id="b7cfe-186">Der Inhalt sollte jetzt wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-186">Your package content should now look something like this.</span></span>

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a><span data-ttu-id="b7cfe-188">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="b7cfe-188">Modify the package manifest</span></span>

<span data-ttu-id="b7cfe-189">Ihr Paketmanifest in einem Text-Editor öffnen, und legen Sie die `Executable` -Attribut der `Application` Element auf den Namen der ausführbaren Datei PSF Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-189">Open your package manifest in a text editor, and then set the `Executable` attribute of the `Application` element to the name of the PSF launcher executable file.</span></span>  <span data-ttu-id="b7cfe-190">Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die korrekte Version, PSFLauncher32.exe oder PSFLauncher64.exe.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-190">If you know the architecture of your target application, select the appropriate version, PSFLauncher32.exe or PSFLauncher64.exe.</span></span>  <span data-ttu-id="b7cfe-191">Wenn dies nicht der Fall ist, PSFLauncher32.exe in allen Fällen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-191">If not, PSFLauncher32.exe will work in all cases.</span></span>  <span data-ttu-id="b7cfe-192">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b7cfe-192">Here's an example.</span></span>

```xml
<Package ...>
  ...
  <Applications>
    <Application Id="PSFSample"
                 Executable="PSFLauncher32.exe"
                 EntryPoint="Windows.FullTrustApplication">
      ...
    </Application>
  </Applications>
</Package>
```

### <a name="create-a-configuration-file"></a><span data-ttu-id="b7cfe-193">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b7cfe-193">Create a configuration file</span></span>

<span data-ttu-id="b7cfe-194">Erstellen Sie einen Dateinamen ``config.json``, und speichern Sie diese Datei in den Stammordner des Pakets.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-194">Create a file name ``config.json``, and save that file to the root folder of your package.</span></span> <span data-ttu-id="b7cfe-195">Ändern Sie die deklarierten app-ID der Datei config.json auf die ausführbare Datei verweisen, den Sie gerade ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-195">Modify the declared app ID of the config.json file to point to the executable that you just replaced.</span></span> <span data-ttu-id="b7cfe-196">Verwenden das wissen, das vom Process Monitor mit resultieren, können Sie auch das Arbeitsverzeichnis sowie verwenden Sie die Datei Umleitung Korrektur Lese-und Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" relativen umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-196">Using the knowledge that you gained from using Process Monitor, you can also set the working directory as well as use the file redirection fixup to redirect reads/writes to .log files under the package-relative "PSFSampleApp" directory.</span></span>

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
            "fixups": [
                {
                    "dll": "FileRedirectionFixup.dll",
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
<span data-ttu-id="b7cfe-197">Im folgenden finden eine Anleitung für das Schema config.json:</span><span class="sxs-lookup"><span data-stu-id="b7cfe-197">Following is a guide for the config.json schema:</span></span>

| <span data-ttu-id="b7cfe-198">Array</span><span class="sxs-lookup"><span data-stu-id="b7cfe-198">Array</span></span> | <span data-ttu-id="b7cfe-199">key</span><span class="sxs-lookup"><span data-stu-id="b7cfe-199">key</span></span> | <span data-ttu-id="b7cfe-200">Wert</span><span class="sxs-lookup"><span data-stu-id="b7cfe-200">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="b7cfe-201">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-201">applications</span></span> | <span data-ttu-id="b7cfe-202">id</span><span class="sxs-lookup"><span data-stu-id="b7cfe-202">id</span></span> |  <span data-ttu-id="b7cfe-203">Verwenden Sie den Wert von der `Id` -Attribut der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-203">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="b7cfe-204">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-204">applications</span></span> | <span data-ttu-id="b7cfe-205">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b7cfe-205">executable</span></span> | <span data-ttu-id="b7cfe-206">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-206">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="b7cfe-207">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-207">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="b7cfe-208">Es ist der Wert von der `Executable` -Attribut der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-208">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="b7cfe-209">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-209">applications</span></span> | <span data-ttu-id="b7cfe-210">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="b7cfe-210">workingDirectory</span></span> | <span data-ttu-id="b7cfe-211">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-211">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="b7cfe-212">Wenn Sie diesen Wert nicht festlegen, der vom Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-212">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="b7cfe-213">Prozesse</span><span class="sxs-lookup"><span data-stu-id="b7cfe-213">processes</span></span> | <span data-ttu-id="b7cfe-214">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b7cfe-214">executable</span></span> | <span data-ttu-id="b7cfe-215">In den meisten Fällen, dies ist der Name des, die `executable` konfigurierten oben mit der Pfad und Dateiname Erweiterung entfernt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-215">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="b7cfe-216">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-216">fixups</span></span> | <span data-ttu-id="b7cfe-217">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="b7cfe-217">dll</span></span> | <span data-ttu-id="b7cfe-218">Relativen Pfad zu der Korrektur.msix/.appx geladen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-218">Package-relative path to the fixup, .msix/.appx  to load.</span></span> |
| <span data-ttu-id="b7cfe-219">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-219">fixups</span></span> | <span data-ttu-id="b7cfe-220">config</span><span class="sxs-lookup"><span data-stu-id="b7cfe-220">config</span></span> | <span data-ttu-id="b7cfe-221">(Optional) Steuert, wie die Korrektur Verteilerliste verhält.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-221">(Optional) Controls how the fixup dl behaves.</span></span> <span data-ttu-id="b7cfe-222">Das genaue Format dieses Werts ist jeweils Korrektur von Korrektur wie jeder Korrektur dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-222">The exact format of this value varies on a fixup-by-fixup basis as each fixup can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="b7cfe-223">Die `applications`, `processes`, und `fixups` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-223">The `applications`, `processes`, and `fixups` keys are arrays.</span></span> <span data-ttu-id="b7cfe-224">Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Korrektur DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-224">That means that you can use the config.json file to specify more than one application, process, and fixup DLL.</span></span>


### <a name="package-and-test-the-app"></a><span data-ttu-id="b7cfe-225">Paket und Testen der App</span><span class="sxs-lookup"><span data-stu-id="b7cfe-225">Package and Test the App</span></span>

<span data-ttu-id="b7cfe-226">Als Nächstes erstellen Sie ein Paket.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-226">Next, create a package.</span></span>

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.msix
```

<span data-ttu-id="b7cfe-227">Signieren Sie es dann.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-227">Then, sign it.</span></span>

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.msix
```

<span data-ttu-id="b7cfe-228">Weitere Informationen finden Sie [Informationen zum Erstellen eines Signaturzertifikats Pakets](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie Sie ein Pakets mit signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span><span class="sxs-lookup"><span data-stu-id="b7cfe-228">For more information, see [how to create a package signing certificate](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) and [how to sign a package using signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span></span>

<span data-ttu-id="b7cfe-229">Mithilfe von PowerShell, installieren Sie das Paket.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-229">Using PowerShell, install the package.</span></span>

>[!NOTE]
> <span data-ttu-id="b7cfe-230">Denken Sie daran, das Paket zuerst deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-230">Remember to uninstall the package first.</span></span>

```
powershell Add-MSIXPackage .\PSFSamplePackageFixup.msix
```

<span data-ttu-id="b7cfe-231">Führen Sie die Anwendung, und beobachten Sie das Verhalten Runtime Update angewendet.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-231">Run the application and observe the behavior with runtime fix applied.</span></span>  <span data-ttu-id="b7cfe-232">Wiederholen Sie die Diagnose- und Verpacken Schritte nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-232">Repeat the diagnostic and packaging steps as necessary.</span></span>

### <a name="use-the-trace-fixup"></a><span data-ttu-id="b7cfe-233">Verwenden Sie die Korrektur Trace</span><span class="sxs-lookup"><span data-stu-id="b7cfe-233">Use the Trace Fixup</span></span>

<span data-ttu-id="b7cfe-234">Ein alternatives Verfahren zu diagnostizieren verpackte Probleme mit der Anwendungskompatibilität ist die Korrektur Trace verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-234">An alternative technique to diagnosing packaged application compatibility issues is to use the Trace Fixup.</span></span> <span data-ttu-id="b7cfe-235">Diese DLL ist in der PSF enthalten und bietet eine detaillierte Ansicht der app Verhalten, ähnlich wie Process Monitor diagnostische.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-235">This DLL is included with the PSF and provides a detailed diagnostic view of the app's behavior, similar to Process Monitor.</span></span>  <span data-ttu-id="b7cfe-236">Es ist speziell auf Probleme mit der Anwendungskompatibilität "einblenden".</span><span class="sxs-lookup"><span data-stu-id="b7cfe-236">It is specially designed to reveal application compatibility issues.</span></span>  <span data-ttu-id="b7cfe-237">Verwenden Sie die Korrektur Trace, die DLL für das Paket hinzufügen Ihrer config.json die folgende Fragment-Komponente hinzufügen und dann Verpacken und installieren Sie die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-237">To use the Trace Fixup, add the DLL to the package, add the following fragment to your config.json, and then package and install your application.</span></span>

```json
{
    "dll": "TraceFixup.dll",
    "config": {
        "traceLevels": {
            "filesystem": "allFailures"
        }
    }
}
```

<span data-ttu-id="b7cfe-238">Standardmäßig filtert die Korrektur Trace Fehler, die berücksichtigt werden möglicherweise "erwartet".</span><span class="sxs-lookup"><span data-stu-id="b7cfe-238">By default, the Trace Fixup filters out failures that might be considered "expected".</span></span>  <span data-ttu-id="b7cfe-239">Beispielsweise Versuch Anwendungen bedingungslos Löschen einer Datei ohne Überprüfung, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-239">For example, applications might try to unconditionally delete a file without checking to see if it already exists, ignoring the result.</span></span> <span data-ttu-id="b7cfe-240">Dies hat die leider folgen, die einige unerwartete Fehler, gefiltert erhalten möglicherweise so melden Sie sich im obigen Beispiel wir an, um alle Fehler von Dateisystem-Funktionen zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-240">This has the unfortunate consequence that some unexpected failures might get filtered out, so in the above example, we opt to receive all failures from filesystem functions.</span></span> <span data-ttu-id="b7cfe-241">Wir tun, da wir von vor, die das Lesen aus der Datei Config.txt fehlschlägt wissen mit "die Nachricht Datei nicht gefunden".</span><span class="sxs-lookup"><span data-stu-id="b7cfe-241">We do this because we know from before that the attempt to read from the Config.txt file fails with the message "file not found".</span></span> <span data-ttu-id="b7cfe-242">Dies ist ein Fehler, der häufig beobachtet und nicht in der Regel davon ausgegangen, dass unerwartet ist.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-242">This is a failure that is frequently observed and not generally assumed to be unexpected.</span></span> <span data-ttu-id="b7cfe-243">In der Praxis ist es wahrscheinlich am besten, beginnen Sie mit dem Filterung nur für unerwartete Fehler, und klicken Sie dann zurückgreifen auf alle Fehler liegt ein Problem, das noch nicht zu erkennen sind.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-243">In practice it's likely best to start out filtering only to unexpected failures, and then falling back to all failures if there's an issue that still can't be identified.</span></span>

<span data-ttu-id="b7cfe-244">Standardmäßig wird die Ausgabe die Korrektur Trace an den Debugger angefügte gesendet.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-244">By default, the output from the Trace Fixup gets sent to the attached debugger.</span></span> <span data-ttu-id="b7cfe-245">In diesem Beispiel stellen wir sind nicht zu debuggen, und wird stattdessen mit dem [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals können Sie die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-245">For this example, we aren't going to attach a debugger, and will instead use the [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) program from SysInternals to view its output.</span></span> <span data-ttu-id="b7cfe-246">Nach dem Ausführen der app, sehen der gleiche Fehler wie zuvor, Sie die würden uns für die gleichen Runtime Updates angeben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-246">After running the app, we can see the same failures as before, which would point us towards the same runtime fixes.</span></span>

![TraceShim Datei nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a><span data-ttu-id="b7cfe-249">Debuggen Sie, erweitern Sie oder erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b7cfe-249">Debug, extend, or create a runtime fix</span></span>

<span data-ttu-id="b7cfe-250">Sie können Visual Studio Debuggen ein Laufzeit-Update, erweitern ein Laufzeit-Update oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-250">You can use Visual Studio to debug a runtime fix, extend a runtime fix, or create one from scratch.</span></span> <span data-ttu-id="b7cfe-251">Sie müssen für diese Vorgänge erfolgreich ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-251">You'll need to do these things to be successful.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b7cfe-252">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="b7cfe-252">Add a packaging project</span></span>
> * <span data-ttu-id="b7cfe-253">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b7cfe-253">Add project for the runtime fix</span></span>
> * <span data-ttu-id="b7cfe-254">Fügen Sie ein Projekt, das die-Startprogramms PSF startet</span><span class="sxs-lookup"><span data-stu-id="b7cfe-254">Add a project that starts the PSF Launcher executable</span></span>
> * <span data-ttu-id="b7cfe-255">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="b7cfe-255">Configure the packaging project</span></span>

<span data-ttu-id="b7cfe-256">Wenn Sie fertig sind, wird die Projektmappe wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-256">When you're done, your solution will look something like this.</span></span>

![Abgeschlossenen Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

<span data-ttu-id="b7cfe-258">Sehen wir uns auf jedes Projekt in diesem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-258">Let's look at each project in this example.</span></span>

| <span data-ttu-id="b7cfe-259">Projekt</span><span class="sxs-lookup"><span data-stu-id="b7cfe-259">Project</span></span> | <span data-ttu-id="b7cfe-260">Zweck</span><span class="sxs-lookup"><span data-stu-id="b7cfe-260">Purpose</span></span> |
|-------|-----------|
| <span data-ttu-id="b7cfe-261">DesktopApplicationPackage</span><span class="sxs-lookup"><span data-stu-id="b7cfe-261">DesktopApplicationPackage</span></span> | <span data-ttu-id="b7cfe-262">Dieses Projekt basiert auf dem [Windows Application Packaging Project](desktop-to-uwp-packaging-dot-net.md) und es gibt die das Paket MSIX.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-262">This project is based on the [Windows Application Packaging project](desktop-to-uwp-packaging-dot-net.md) and it outputs the the MSIX package.</span></span> |
| <span data-ttu-id="b7cfe-263">Runtimefix</span><span class="sxs-lookup"><span data-stu-id="b7cfe-263">Runtimefix</span></span> | <span data-ttu-id="b7cfe-264">Dies ist ein C++ Dynamic-Linked Klassenbibliotheksprojekt hinzu, die eine oder mehrere Ersatzfunktionen enthält, die als die Common Language Runtime-Problembehandlung dienen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-264">This is a C++ Dynamic-Linked Library project that contains one or more replacement functions that serve as the runtime fix.</span></span> |
| <span data-ttu-id="b7cfe-265">PSFLauncher</span><span class="sxs-lookup"><span data-stu-id="b7cfe-265">PSFLauncher</span></span> | <span data-ttu-id="b7cfe-266">Dies ist leeres C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-266">This is C++ Empty Project.</span></span> <span data-ttu-id="b7cfe-267">Dieses Projekt ist ein Ort zum Sammeln von der Runtime verteilbaren Dateien des Pakets Support-Frameworks.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-267">This project is a place to collect the runtime distributable files of the Package Support Framework.</span></span> <span data-ttu-id="b7cfe-268">Es gibt eine ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-268">It outputs an executable file.</span></span> <span data-ttu-id="b7cfe-269">Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe zu starten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-269">That executable is the first thing that runs when you start the solution.</span></span> |
| <span data-ttu-id="b7cfe-270">WinFormsDesktopApplication</span><span class="sxs-lookup"><span data-stu-id="b7cfe-270">WinFormsDesktopApplication</span></span> | <span data-ttu-id="b7cfe-271">Dieses Projekt enthält den Quellcode für eine desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-271">This project contains the source code of a desktop application.</span></span> |

<span data-ttu-id="b7cfe-272">Um ein vollständiges Beispiel betrachten, die alle diese Arten von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-272">To look at a complete sample that contains all of these types of projects, see [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span></span>

<span data-ttu-id="b7cfe-273">Betrachten Sie die Schritte zum Erstellen und Konfigurieren jedes dieser Projekte in Ihrer Projektmappe aus.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-273">Let's walk through the steps to create and configure each of these projects in your solution.</span></span>


### <a name="create-a-package-solution"></a><span data-ttu-id="b7cfe-274">Erstellen Sie eine Flight-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-274">Create a package solution</span></span>

<span data-ttu-id="b7cfe-275">Wenn Sie bereits über eine Lösung für Ihre desktop-Anwendung besitzen, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-275">If you don't already have a solution for your desktop application, create a new **Blank Solution** in Visual Studio.</span></span>

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

<span data-ttu-id="b7cfe-277">Sie sollten auch alle Anwendungsprojekte hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-277">You may also want to add any application projects you have.</span></span>

### <a name="add-a-packaging-project"></a><span data-ttu-id="b7cfe-278">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="b7cfe-278">Add a packaging project</span></span>

<span data-ttu-id="b7cfe-279">Wenn Sie bereits über ein **Windows Application Packaging Project**besitzen, erstellen und sie der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-279">If you don't already have a **Windows Application Packaging Project**, create one and add it to your solution.</span></span>

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

<span data-ttu-id="b7cfe-281">Weitere Informationen zu Windows Application Packaging Project finden Sie unter [Paket Ihrer Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-281">For more information on Windows Application Packaging project, see [Package your application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

<span data-ttu-id="b7cfe-282">Im **Projektmappen-Explorer**mit der rechten Maustaste des Verpacken-Projekts, wählen Sie **Bearbeiten**und dann am unteren Rand der Projektdatei hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="b7cfe-282">In **Solution Explorer**, right-click the packaging project, select **Edit**, and then add this to the bottom of the project file:</span></span>

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

### <a name="add-project-for-the-runtime-fix"></a><span data-ttu-id="b7cfe-283">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="b7cfe-283">Add project for the runtime fix</span></span>

<span data-ttu-id="b7cfe-284">Ein C++- **Dll-Bibliothek (DLL)** -Projekt der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-284">Add a C++ **Dynamic-Link Library (DLL)** project to the solution.</span></span>

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

<span data-ttu-id="b7cfe-286">Der rechten Maustaste auf das Projekt, und wählen Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-286">Right-click the that project, and then choose **Properties**.</span></span>

<span data-ttu-id="b7cfe-287">Auf den Eigenschaftenseiten suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld, das **ISO C ++ 17 Standard (/ Std: c ++ 17)** Option.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-287">In the property pages, find the **C++ Language Standard** field, and then in the drop-down list next to that field, select the **ISO C++17 Standard (/std:c++17)** option.</span></span>

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

<span data-ttu-id="b7cfe-289">Mit der rechten Maustaste in des Projekts, und wählen Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** .</span><span class="sxs-lookup"><span data-stu-id="b7cfe-289">Right-click that project, and then in the context menu, choose the **Manage Nuget Packages** option.</span></span> <span data-ttu-id="b7cfe-290">Stellen Sie sicher, dass die **Paketquelle** Option für **Alle** oder **"NuGet.org"** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-290">Ensure that the **Package source** option is set to **All** or **nuget.org**.</span></span>

<span data-ttu-id="b7cfe-291">Klicken Sie auf dem Symbol "Einstellungen" neben dem Feld.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-291">Click the settings icon next that field.</span></span>

<span data-ttu-id="b7cfe-292">Suchen Sie nach der *PSF*\* Nuget Paket, und installieren Sie es für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-292">Search for the *PSF*\* Nuget package, and then install it for this project.</span></span>

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

<span data-ttu-id="b7cfe-294">Wenn Sie Debuggen oder einen vorhandenen Runtime Fix erweitern möchten, fügen Sie die Runtime Update-Dateien, die Sie mithilfe der Anleitung im Abschnitt [Suchen nach einer Lösung Runtime](#find) dieses Handbuchs abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-294">If you want to debug or extend an existing runtime fix, add the runtime fix files that you obtained by using the guidance described in the [Find a runtime fix](#find) section of this guide.</span></span>

<span data-ttu-id="b7cfe-295">Wenn Sie beabsichtigen, ein völlig neues Update zu erstellen, fügen Sie nicht nichts dieses Projekt noch.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-295">If you intend to create a brand new fix, don't add anything to this project just yet.</span></span> <span data-ttu-id="b7cfe-296">Wir helfen Ihnen, die richtigen Dateien in dieses Projekt weiter unten in diesem Handbuch hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-296">We'll help you add the right files to this project later in this guide.</span></span> <span data-ttu-id="b7cfe-297">Für den Moment fahren wir Einrichten Ihrer Projektmappe fort.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-297">For now, we'll continue setting up your solution.</span></span>

### <a name="add-a-project-that-starts-the-psf-launcher-executable"></a><span data-ttu-id="b7cfe-298">Fügen Sie ein Projekt, das die-Startprogramms PSF startet</span><span class="sxs-lookup"><span data-stu-id="b7cfe-298">Add a project that starts the PSF Launcher executable</span></span>

<span data-ttu-id="b7cfe-299">Fügen Sie der Projektmappe ein **Leeres Projekt** für C++-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-299">Add a C++ **Empty Project** project to the solution.</span></span>

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

<span data-ttu-id="b7cfe-301">Hinzufügen des **PSF** Nuget-Pakets dieses Projekt mit der gleichen Anleitung im vorherigen Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-301">Add the **PSF** Nuget package to this project by using the same guidance described in the previous section.</span></span>

<span data-ttu-id="b7cfe-302">Öffnen die Eigenschaftenseiten für das Projekt, und in die **Allgemeine** Seite "Einstellungen", setzen Sie die **Zielnamen** -Eigenschaft auf ``PSFLauncher32`` oder ``PSFLauncher64`` abhängig von der Architektur der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-302">Open the property pages for the project, and in the **General** settings page, set the **Target Name** property to ``PSFLauncher32`` or ``PSFLauncher64`` depending on the architecture of your application.</span></span>

![PSF Startprogramm Referenz](images/desktop-to-uwp/shim-exe-reference.png)

<span data-ttu-id="b7cfe-304">Fügen Sie einen Projektverweis auf die Runtime Update-Projekt in Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-304">Add a project reference to the runtime fix project in your solution.</span></span>

![-Runtime-Fix-Referenz](images/desktop-to-uwp/reference-fix.png)

<span data-ttu-id="b7cfe-306">Mit der rechten Maustaste in der Referenz, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-306">Right-click the reference, and then in the **Properties** window, apply these values.</span></span>

| <span data-ttu-id="b7cfe-307">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b7cfe-307">Property</span></span> | <span data-ttu-id="b7cfe-308">Wert</span><span class="sxs-lookup"><span data-stu-id="b7cfe-308">Value</span></span> |
|-------|-----------|
| <span data-ttu-id="b7cfe-309">Kopieren Sie lokale</span><span class="sxs-lookup"><span data-stu-id="b7cfe-309">Copy local</span></span> | <span data-ttu-id="b7cfe-310">Wahr</span><span class="sxs-lookup"><span data-stu-id="b7cfe-310">True</span></span> |
| <span data-ttu-id="b7cfe-311">Lokale Satellitenassemblys kopieren</span><span class="sxs-lookup"><span data-stu-id="b7cfe-311">Copy Local Satellite Assemblies</span></span> | <span data-ttu-id="b7cfe-312">Wahr</span><span class="sxs-lookup"><span data-stu-id="b7cfe-312">True</span></span> |
| <span data-ttu-id="b7cfe-313">Referenz-Assembly-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="b7cfe-313">Reference Assembly Output</span></span> | <span data-ttu-id="b7cfe-314">Wahr</span><span class="sxs-lookup"><span data-stu-id="b7cfe-314">True</span></span> |
| <span data-ttu-id="b7cfe-315">Link-Bibliothek Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="b7cfe-315">Link Library Dependencies</span></span> | <span data-ttu-id="b7cfe-316">False</span><span class="sxs-lookup"><span data-stu-id="b7cfe-316">False</span></span> |
| <span data-ttu-id="b7cfe-317">Link-Bibliothek Abhängigkeitseigenschaften Eingaben</span><span class="sxs-lookup"><span data-stu-id="b7cfe-317">Link Library Dependency Inputs</span></span> | <span data-ttu-id="b7cfe-318">False</span><span class="sxs-lookup"><span data-stu-id="b7cfe-318">False</span></span> |

### <a name="configure-the-packaging-project"></a><span data-ttu-id="b7cfe-319">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="b7cfe-319">Configure the packaging project</span></span>

<span data-ttu-id="b7cfe-320">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-320">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

<span data-ttu-id="b7cfe-322">Wählen Sie das Projekt PSF Launcher und Ihrem desktopanwendungsprojekt, und wählen Sie dann auf die Schaltfläche " **OK** ".</span><span class="sxs-lookup"><span data-stu-id="b7cfe-322">Choose the PSF launcher project and your desktop application project, and then choose the **OK** button.</span></span>

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> <span data-ttu-id="b7cfe-324">Wenn Sie den Quellcode für Ihre Anwendung besitzen, wählen Sie einfach das PSF Startprogramm Projekt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-324">If you don't have the source code to your application, just choose the PSF launcher project.</span></span> <span data-ttu-id="b7cfe-325">Wir zeigen Ihnen wie die ausführbare Datei verweisen, wenn Sie eine Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-325">We'll show you how to reference your executable when you create a configuration file.</span></span>

<span data-ttu-id="b7cfe-326">Klicken Sie im Knoten " **Anwendungen** " mit der rechten Maustaste die PSF startanwendung, und wählen Sie dann **als Einstiegspunkt festlegen**.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-326">In the **Applications** node, right-click the PSF launcher application, and then choose **Set as Entry Point**.</span></span>

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

<span data-ttu-id="b7cfe-328">Fügen Sie eine Datei mit dem Namen ``config.json`` verpackungs-Projekts, klicken Sie dann kopieren und fügen Sie den folgenden Json-Text in die Datei.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-328">Add a file named ``config.json`` to your packaging project, then, copy and paste the following json text into the file.</span></span> <span data-ttu-id="b7cfe-329">Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalte**.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-329">Set the **Package Action** property to **Content**.</span></span>

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
            "fixups": [
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
<span data-ttu-id="b7cfe-330">Geben Sie einen Wert für jeden Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-330">Provide a value for each key.</span></span> <span data-ttu-id="b7cfe-331">Orientieren Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-331">Use this table as a guide.</span></span>

| <span data-ttu-id="b7cfe-332">Array</span><span class="sxs-lookup"><span data-stu-id="b7cfe-332">Array</span></span> | <span data-ttu-id="b7cfe-333">key</span><span class="sxs-lookup"><span data-stu-id="b7cfe-333">key</span></span> | <span data-ttu-id="b7cfe-334">Wert</span><span class="sxs-lookup"><span data-stu-id="b7cfe-334">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="b7cfe-335">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-335">applications</span></span> | <span data-ttu-id="b7cfe-336">id</span><span class="sxs-lookup"><span data-stu-id="b7cfe-336">id</span></span> |  <span data-ttu-id="b7cfe-337">Verwenden Sie den Wert von der `Id` -Attribut der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-337">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="b7cfe-338">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-338">applications</span></span> | <span data-ttu-id="b7cfe-339">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b7cfe-339">executable</span></span> | <span data-ttu-id="b7cfe-340">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-340">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="b7cfe-341">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-341">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="b7cfe-342">Es ist der Wert von der `Executable` -Attribut der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-342">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="b7cfe-343">applications</span><span class="sxs-lookup"><span data-stu-id="b7cfe-343">applications</span></span> | <span data-ttu-id="b7cfe-344">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="b7cfe-344">workingDirectory</span></span> | <span data-ttu-id="b7cfe-345">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-345">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="b7cfe-346">Wenn Sie diesen Wert nicht festlegen, der vom Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-346">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="b7cfe-347">Prozesse</span><span class="sxs-lookup"><span data-stu-id="b7cfe-347">processes</span></span> | <span data-ttu-id="b7cfe-348">ausführbare</span><span class="sxs-lookup"><span data-stu-id="b7cfe-348">executable</span></span> | <span data-ttu-id="b7cfe-349">In den meisten Fällen, dies ist der Name des, die `executable` konfigurierten oben mit der Pfad und Dateiname Erweiterung entfernt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-349">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="b7cfe-350">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-350">fixups</span></span> | <span data-ttu-id="b7cfe-351">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="b7cfe-351">dll</span></span> | <span data-ttu-id="b7cfe-352">Relativen Pfad die Korrektur DLL zu laden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-352">Package-relative path to the fixup DLL to load.</span></span> |
| <span data-ttu-id="b7cfe-353">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-353">fixups</span></span> | <span data-ttu-id="b7cfe-354">config</span><span class="sxs-lookup"><span data-stu-id="b7cfe-354">config</span></span> | <span data-ttu-id="b7cfe-355">(Optional) Steuert, wie die Korrektur DLL verhält.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-355">(Optional) Controls how the fixup DLL behaves.</span></span> <span data-ttu-id="b7cfe-356">Das genaue Format dieses Werts ist jeweils Korrektur von Korrektur wie jeder Korrektur dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-356">The exact format of this value varies on a fixup-by-fixup basis as each fixup can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="b7cfe-357">Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-357">When you're done, your ``config.json`` file will look something like this.</span></span>

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
      "fixups": [ { "dll": "RuntimeFix.dll" } ]
    }
  ]
}

```

>[!NOTE]
> <span data-ttu-id="b7cfe-358">Die `applications`, `processes`, und `fixups` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-358">The `applications`, `processes`, and `fixups` keys are arrays.</span></span> <span data-ttu-id="b7cfe-359">Das bedeutet, dass Sie die Datei config.json verwenden können, um mehr als eine Anwendung, Prozessen und Korrektur DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-359">That means that you can use the config.json file to specify more than one application, process, and fixup DLL.</span></span>

### <a name="debug-a-runtime-fix"></a><span data-ttu-id="b7cfe-360">Debuggen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b7cfe-360">Debug a runtime fix</span></span>

<span data-ttu-id="b7cfe-361">Drücken Sie in Visual Studio F5, um den Debugger zu starten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-361">In Visual Studio, press F5 to start the debugger.</span></span>  <span data-ttu-id="b7cfe-362">Der erste Schritt, der beginnt ist der startanwendung PSF, die wiederum die Ziel-desktop-Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-362">The first thing that starts is the PSF launcher application, which in turn, starts your target desktop application.</span></span>  <span data-ttu-id="b7cfe-363">Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell für den desktop-Anwendungsprozess anhängen, indem Sie **Debuggen**auswählen->**an den Prozess anhängen**, auswählen und dann den bewerbungsprozess.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-363">To debug the target desktop application, you'll have to manually attach to the desktop application process by choosing **Debug**->**Attach to Process**, and then selecting the application process.</span></span> <span data-ttu-id="b7cfe-364">Um das Debuggen einer .NET-Anwendung mit einer systemeigenen Runtime Update DLL zu ermöglichen, wählen Sie verwalteten und systemeigenen Code (im gemischten Modus Debuggen).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-364">To permit the debugging of a .NET application with a native runtime fix DLL, select managed and native code types (mixed mode debugging).</span></span>  

<span data-ttu-id="b7cfe-365">Nachdem Sie dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und die Runtime Update Projekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-365">Once you've set this up, you can set break points next to lines of code in the desktop application code and the runtime fix project.</span></span> <span data-ttu-id="b7cfe-366">Wenn Sie den Quellcode für Ihre Anwendung besitzen, müssen Sie legen Sie Haltepunkte nur neben Codezeilen in Ihrem Projekt der Runtime beheben können.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-366">If you don't have the source code to your application, you'll be able to set break points only next to lines of code in your runtime fix project.</span></span>

>[!NOTE]
> <span data-ttu-id="b7cfe-367">Visual Studio bietet Ihnen die einfachste Entwicklung Debuggen, es gibt einige Einschränkungen, dies später in diesem Handbuch erläutern wir, andere debugging Techniken, die Sie anwenden können.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-367">While Visual Studio gives you the simplest development and debugging experience, there are some limitations, so later in this guide, we'll discuss other debugging techniques that you can apply.</span></span>

## <a name="create-a-runtime-fix"></a><span data-ttu-id="b7cfe-368">Erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="b7cfe-368">Create a runtime fix</span></span>

<span data-ttu-id="b7cfe-369">Wenn es keine noch eine Laufzeit für das Problem beheben, aufgelöst, können Sie erstellen ein neues Runtime Update schreiben Ersatzfunktionen und einschließlich aller Konfigurationsdaten ist, die sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-369">If there isn't yet a runtime fix for the issue that you want to resolve, you can create a new runtime fix by writing replacement functions and including any configuration data that makes sense.</span></span> <span data-ttu-id="b7cfe-370">Sehen wir uns auf jedem Teil.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-370">Let's look at each part.</span></span>

### <a name="replacement-functions"></a><span data-ttu-id="b7cfe-371">Ersatzfunktionen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-371">Replacement functions</span></span>

<span data-ttu-id="b7cfe-372">Zunächst ermitteln Sie welche Funktion ruft fehl, wenn die Anwendung in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-372">First, identify which function calls fail when your application runs in an MSIX container.</span></span> <span data-ttu-id="b7cfe-373">Anschließend können Sie Ersatzfunktionen erstellen, die Sie den Laufzeit-Manager stattdessen aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-373">Then, you can create replacement functions that you'd like the runtime manager to call instead.</span></span> <span data-ttu-id="b7cfe-374">Dies bietet Ihnen die Möglichkeit, die Implementierung einer Funktion mit Verhalten zu ersetzen, die den Regeln der modernen-Runtime-Umgebung entspricht.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-374">This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.</span></span>

<span data-ttu-id="b7cfe-375">Öffnen Sie das Runtime beheben Sie weiter oben in diesem Handbuch erstellte Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-375">In Visual Studio, open the runtime fix project that you created earlier in this guide.</span></span>

<span data-ttu-id="b7cfe-376">Deklarieren Sie die ``FIXUP_DEFINE_EXPORTS`` Makro und fügen dann eine Include-Anweisung für die `fixup_framework.h` am Anfang jedes. CPP-Datei für die Funktionen der Common Language Runtime-Updates hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-376">Declare the ``FIXUP_DEFINE_EXPORTS`` macro and then add a include statement for the `fixup_framework.h` at the top of each .CPP file where you intend to add the functions of your runtime fix.</span></span>

```c++
#define FIXUP_DEFINE_EXPORTS
#include <fixup_framework.h>
```
>[!IMPORTANT]
><span data-ttu-id="b7cfe-377">Stellen Sie sicher, dass die `FIXUP_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-377">Make sure that the `FIXUP_DEFINE_EXPORTS` macro appears before the include statement.</span></span>

<span data-ttu-id="b7cfe-378">Erstellen Sie eine Funktion, die dieselbe Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-378">Create a function that has the same signature of the function who's behavior you want to modify.</span></span> <span data-ttu-id="b7cfe-379">Hier ist eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-379">Here's an example function that replaces the `MessageBoxW` function.</span></span>

```c++
auto MessageBoxWImpl = &::MessageBoxW;
int WINAPI MessageBoxWFixup(
    _In_opt_ HWND hwnd,
    _In_opt_ LPCWSTR,
    _In_opt_ LPCWSTR caption,
    _In_ UINT type)
{
    return MessageBoxWImpl(hwnd, L"SUCCESS: This worked", caption, type);
}

DECLARE_FIXUP(MessageBoxWImpl, MessageBoxWFixup);
```

<span data-ttu-id="b7cfe-380">Der Aufruf von `DECLARE_FIXUP` ordnet die `MessageBoxW` in Ihrer neuen-Funktion als Ersatz.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-380">The call to `DECLARE_FIXUP` maps the `MessageBoxW` function to your new replacement function.</span></span> <span data-ttu-id="b7cfe-381">Wenn Ihre Anwendung versucht, rufen Sie die `MessageBoxW` Funktion es Ruft die Ersatz-Funktion stattdessen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-381">When your application attempts to call the `MessageBoxW` function, it will call the replacement function instead.</span></span>

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a><span data-ttu-id="b7cfe-382">Schutz vor rekursiven Aufrufe von Funktionen in-Runtime-Updates</span><span class="sxs-lookup"><span data-stu-id="b7cfe-382">Protect against recursive calls to functions in runtime fixes</span></span>

<span data-ttu-id="b7cfe-383">Sie können optional Anwenden der `reentrancy_guard` Typ, der Ihrer Funktionen, die Schutz gegen rekursiven Aufrufe von Funktionen in Runtime Patches.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-383">You can optionally apply the `reentrancy_guard` type to your functions that protect against recursive calls to functions in runtime fixes.</span></span>

<span data-ttu-id="b7cfe-384">Sie können z. B. eine Funktion Ersatz für führen die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-384">For example, you might produce a replacement function for the `CreateFile` function.</span></span> <span data-ttu-id="b7cfe-385">Die Implementierung aufrufen kann die `CopyFile` -Funktion, aber die Implementierung der `CopyFile` Funktionsaufruf möglicherweise die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-385">Your implementation might call the `CopyFile` function, but the implementation of the `CopyFile` function might call the `CreateFile` function.</span></span> <span data-ttu-id="b7cfe-386">Dies kann dazu führen, dass einer unendlichen rekursiven Zyklus von Aufrufen an die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-386">This may lead to an infinite recursive cycle of calls to the `CreateFile` function.</span></span>

<span data-ttu-id="b7cfe-387">Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span><span class="sxs-lookup"><span data-stu-id="b7cfe-387">For more information on `reentrancy_guard` see [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span></span>

### <a name="configuration-data"></a><span data-ttu-id="b7cfe-388">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="b7cfe-388">Configuration data</span></span>

<span data-ttu-id="b7cfe-389">Wenn Sie Ihre Update-Runtime-Konfigurationsdaten hinzufügen möchten, in Betracht ziehen, um die ``config.json``.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-389">If you want to add configuration data to your runtime fix, consider adding it to the ``config.json``.</span></span> <span data-ttu-id="b7cfe-390">Auf diese Weise können Sie die `FixupQueryCurrentDllConfig` einfach diese Daten analysiert.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-390">That way, you can use the `FixupQueryCurrentDllConfig` to easily parse that data.</span></span> <span data-ttu-id="b7cfe-391">In diesem Beispiel wird einen booleschen Wert und Zeichenfolge Wert aus der Konfigurationsdatei analysiert.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-391">This example parses a boolean and string value from that configuration file.</span></span>

```c++
if (auto configRoot = ::FixupQueryCurrentDllConfig())
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

## <a name="other-debugging-techniques"></a><span data-ttu-id="b7cfe-392">Andere debugging-Techniken</span><span class="sxs-lookup"><span data-stu-id="b7cfe-392">Other debugging techniques</span></span>

<span data-ttu-id="b7cfe-393">Während Visual Studio die einfachste Entwicklung und das debugging Erfahrung Ihnen bietet, gibt es einige Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-393">While Visual Studio gives you the simplest development and debugging experience, there are some limitations.</span></span>

<span data-ttu-id="b7cfe-394">Erstens Debuggens mit F5 führt die Anwendung durch die Bereitstellung von losen Dateien aus dem Paket Layout Ordnerpfad, installieren, sondern von einer .msix / AppX-Pakets.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-394">First, F5 debugging runs the application by deploying loose files from the package layout folder path, rather than installing from a .msix / .appx package.</span></span>  <span data-ttu-id="b7cfe-395">Die Layoutordner verfügt in der Regel nicht dieselben sicherheitseinschränkungen, die als eine installierte Paketordner.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-395">The layout folder typically does not have the same security restrictions as an installed package folder.</span></span> <span data-ttu-id="b7cfe-396">Folglich kann es nicht Paket Pfad Denial Zugriffsfehler vor der Anwendung ein Laufzeit-Updates reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-396">As a result, it may not be possible to reproduce package path access denial errors prior to applying a runtime fix.</span></span>

<span data-ttu-id="b7cfe-397">Um dieses Problem zu beheben, verwenden Sie .msix / Bereitstellung des AppX-Pakets statt F5 lose Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-397">To address this issue, use .msix / .appx package deployment rather than F5 loose file deployment.</span></span>  <span data-ttu-id="b7cfe-398">Erstellen Sie eine .msix / AppX-Paket-Datei, das Dienstprogramm [MakeMSIX](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) aus dem Windows SDK verwenden, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-398">To create a .msix / .appx package file, use the [MakeMSIX](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) utility from the Windows SDK, as described above.</span></span> <span data-ttu-id="b7cfe-399">Oder in Visual Studio Maustaste auf den Projektknoten Anwendung und wählen **Store**->**App-Pakete erstellen**.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-399">Or, from within Visual Studio, right-click your application project node and select **Store**->**Create App Packages**.</span></span>

<span data-ttu-id="b7cfe-400">Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung für die Verbindung vom Debugger gestartet untergeordnete Prozesse enthält.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-400">Another issue with Visual Studio is that it does not have built-in support for attaching to any child processes launched by the debugger.</span></span>   <span data-ttu-id="b7cfe-401">Dies erschwert es zum Debuggen Logik im Startpfad der Zielanwendung, die nach dem Start von Visual Studio manuell angefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-401">This makes it difficult to debug logic in the startup path of the target application, which must be manually attached by Visual Studio after launch.</span></span>

<span data-ttu-id="b7cfe-402">Um dieses Problem zu beheben, verwenden Sie einen Debugger, untergeordneter Prozess anhängen, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-402">To address this issue, use a debugger that supports child process attach.</span></span>  <span data-ttu-id="b7cfe-403">Beachten Sie, dass es in der Regel nicht möglich, Just-in-Time (JIT) der Zielanwendung Debuggen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-403">Note that it is generally not possible to attach a just-in-time (JIT) debugger to the target application.</span></span>  <span data-ttu-id="b7cfe-404">Grund dafür ist die meisten JIT-Techniken des Debuggers anstelle der Ziel-app, über den Registrierungsschlüssel ImageFileExecutionOptions.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-404">This is because most JIT techniques involve launching the debugger in place of the target app, via the ImageFileExecutionOptions registry key.</span></span>  <span data-ttu-id="b7cfe-405">Dies "vereitelt" wird den detouring Mechanismus zur Bestimmung von PSFLauncher.exe FixupRuntime.dll in die Ziel-app einzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-405">This defeats the detouring mechanism used by PSFLauncher.exe to inject FixupRuntime.dll into the target app.</span></span>  <span data-ttu-id="b7cfe-406">WinDbg, in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)abgerufenen, unterstützt untergeordneter Prozess anfügen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-406">WinDbg, included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index), and obtained from the [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), supports child process attach.</span></span>  <span data-ttu-id="b7cfe-407">Unterstützt jetzt auch direkt [Starten und Debuggen einer UWP-Apps](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-407">It also now supports directly [launching and debugging a UWP app](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span></span>

<span data-ttu-id="b7cfe-408">Informationen zum Debuggen Ziel Anwendungsstart als untergeordneter Prozess starten ``WinDbg``.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-408">To debug target application startup as a child process, start ``WinDbg``.</span></span>

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

<span data-ttu-id="b7cfe-409">Bei der ``WinDbg`` auffordern, untergeordnete Debuggen aktivieren und entsprechende Haltepunkte festlegen.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-409">At the ``WinDbg`` prompt, enable child debugging and set appropriate breakpoints.</span></span>

```
.childdbg 1
g
```
<span data-ttu-id="b7cfe-410">(ausgeführt wird, bis der Zielanwendung beginnt und in den Debugger unterbricht)</span><span class="sxs-lookup"><span data-stu-id="b7cfe-410">(execute until target application starts and breaks into the debugger)</span></span>

```
sxe ld fixup.dll
g
```
<span data-ttu-id="b7cfe-411">(erst ausgeführt, wenn die Korrektur laden DLL-Datei)</span><span class="sxs-lookup"><span data-stu-id="b7cfe-411">(execute until the fixup DLL is loaded)</span></span>

```
bp ...
```

>[!NOTE]
> <span data-ttu-id="b7cfe-412">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) kann auch zum Debuggen einer app beim Start verwendet werden, und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-412">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) can be also used to attach a debugger to an app upon launch, and is also included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index).</span></span>  <span data-ttu-id="b7cfe-413">Allerdings ist es komplexer als das direkte unterstützt jetzt WinDbg verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-413">However, it is more complex to use than the direct support now provided by WinDbg.</span></span>

## <a name="support-and-feedback"></a><span data-ttu-id="b7cfe-414">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="b7cfe-414">Support and feedback</span></span>

**<span data-ttu-id="b7cfe-415">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="b7cfe-415">Find answers to your questions</span></span>**

<span data-ttu-id="b7cfe-416">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="b7cfe-416">Have questions?</span></span> <span data-ttu-id="b7cfe-417">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="b7cfe-417">Ask us on Stack Overflow.</span></span> <span data-ttu-id="b7cfe-418">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-418">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="b7cfe-419">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="b7cfe-419">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

