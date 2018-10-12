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
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4566838"
---
# <a name="apply-runtime-fixes-to-an-msix-package-by-using-the-package-support-framework"></a><span data-ttu-id="aa28c-103">Wenden Sie-Runtime-Updates zu einem MSIX-Paket mit dem Paket Support-Framework</span><span class="sxs-lookup"><span data-stu-id="aa28c-103">Apply runtime fixes to an MSIX package by using the Package Support Framework</span></span>

<span data-ttu-id="aa28c-104">Das Paket Support-Framework ist ein open-Source-Kit, das hilft Ihnen, wenden Sie Updates für Ihre vorhandenen win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode, haben, damit sie in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="aa28c-104">The Package Support Framework is an open source kit that helps you apply fixes to your existing win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="aa28c-105">Das Paket Support-Framework hilft Ihrer Anwendung, führen Sie die bewährten Methoden der modernen Common Language Runtime-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-105">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

<span data-ttu-id="aa28c-106">Weitere Informationen hierzu finden Sie unter [Paket Support-Framework](https://docs.microsoft.com/windows/msix/package-support-framework-overview).</span><span class="sxs-lookup"><span data-stu-id="aa28c-106">To learn more, see [Package Support Framework](https://docs.microsoft.com/windows/msix/package-support-framework-overview).</span></span>

<span data-ttu-id="aa28c-107">Dieses Handbuch hilft Ihnen, Probleme mit der Anwendungskompatibilität zu identifizieren und zum Suchen, anwenden und erweitern Common Language Runtime behebt, die diese zu beheben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-107">This guide will help you to identify application compatibility issues, and to find, apply, and extend runtime fixes that address them.</span></span>

<a id="identify" />

## <a name="identify-packaged-application-compatibility-issues"></a><span data-ttu-id="aa28c-108">Identifizieren Sie verpackte Probleme mit der Anwendungskompatibilität</span><span class="sxs-lookup"><span data-stu-id="aa28c-108">Identify packaged application compatibility issues</span></span>

<span data-ttu-id="aa28c-109">Erstellen Sie zunächst ein Paket für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-109">First, create a package for your application.</span></span> <span data-ttu-id="aa28c-110">Installieren Sie es dann, und beobachten Sie, führen Sie es.</span><span class="sxs-lookup"><span data-stu-id="aa28c-110">Then, install it, run it, and observe its behavior.</span></span> <span data-ttu-id="aa28c-111">Sie erhalten möglicherweise Fehlermeldungen, die eine Kompatibilitätsprobleme erleichtern.</span><span class="sxs-lookup"><span data-stu-id="aa28c-111">You might receive error messages that can help you identify a compatibility issue.</span></span> <span data-ttu-id="aa28c-112">Sie können auch [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) verwenden, um Probleme zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-112">You can also use [Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) to identify issues.</span></span>  <span data-ttu-id="aa28c-113">Allgemeine Probleme beziehen sich auf Anwendung Annahmen in Bezug auf die Berechtigungen arbeiten Verzeichnis und Programm Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa28c-113">Common issues relate to application assumptions regarding the working directory and program path permissions.</span></span>

### <a name="using-process-monitor-to-identify-an-issue"></a><span data-ttu-id="aa28c-114">Mithilfe von Process Monitor ein Problems identifizieren</span><span class="sxs-lookup"><span data-stu-id="aa28c-114">Using Process Monitor to identify an issue</span></span>

<span data-ttu-id="aa28c-115">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) ist ein leistungsfähiges Dienstprogramm ermöglicht Ihnen, eine app-Datei und Registrierungsvorgänge und die Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="aa28c-115">[Process Monitor](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon) is a powerful utility for observing an app's file and registry operations, and their results.</span></span>  <span data-ttu-id="aa28c-116">Dies hilft Ihnen, Probleme mit der Anwendungskompatibilität zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-116">This can help you to understand application compatibility issues.</span></span>  <span data-ttu-id="aa28c-117">Fügen Sie nach dem Öffnen Process Monitor, einen Filter (Filter > Filter...) nur Ereignisse für die Anwendung ausführbare einschließen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-117">After opening Process Monitor, add a filter (Filter > Filter…) to include only events from the application executable.</span></span>

![ProcMon App Filter](images/desktop-to-uwp/procmon_app_filter.png)

<span data-ttu-id="aa28c-119">Eine Liste der Ereignisse wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-119">A list of events will appear.</span></span> <span data-ttu-id="aa28c-120">Für viele dieser Ereignisse wird das Wort **Erfolg** in der Spalte **Ergebnis** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-120">For many of these events, the word **SUCCESS** will appear in the **Result** column.</span></span>

![ProcMon-Ereignisse](images/desktop-to-uwp/procmon_events.png)

<span data-ttu-id="aa28c-122">Optional können Sie Ereignisse, um nur angezeigt werden nur Fehler filtern.</span><span class="sxs-lookup"><span data-stu-id="aa28c-122">Optionally, you can filter events to only show only failures.</span></span>

![ProcMon ausschließen Erfolg](images/desktop-to-uwp/procmon_exclude_success.png)

<span data-ttu-id="aa28c-124">Wenn Sie einen Dateisystem Zugriff Fehler vermuten, suchen Sie nach fehlgeschlagenen Ereignisse, die unter dem System32/SysWOW64 oder der Paketdateipfad sind.</span><span class="sxs-lookup"><span data-stu-id="aa28c-124">If you suspect a filesystem access failure, search for failed events that are under either the System32/SysWOW64 or the package file path.</span></span> <span data-ttu-id="aa28c-125">Filter können auch hier zu helfen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-125">Filters can also help here, too.</span></span> <span data-ttu-id="aa28c-126">Starten Sie am unteren Rand der Liste, und führen Sie einen Bildlauf nach oben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-126">Start at the bottom of this list and scroll upwards.</span></span> <span data-ttu-id="aa28c-127">Fehler, die am unteren Rand der Liste angezeigt werden, sind zuletzt aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-127">Failures that appear at the bottom of this list have occurred most recently.</span></span> <span data-ttu-id="aa28c-128">Die meisten geachtet werden, Fehler, die Zeichenfolgen wie "Zugriff verweigert" enthalten, und "Pfad/Name nicht gefunden", und Dinge, die nicht verdächtige aussehen zu ignorieren.</span><span class="sxs-lookup"><span data-stu-id="aa28c-128">Pay most attention to errors that contain strings such as "access denied," and "path/name not found", and ignore things that don't look suspicious.</span></span> <span data-ttu-id="aa28c-129">Die [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) gibt es zwei Probleme.</span><span class="sxs-lookup"><span data-stu-id="aa28c-129">The [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/) has two issues.</span></span> <span data-ttu-id="aa28c-130">Sie können diese Probleme in der Liste sehen, die in der folgenden Abbildung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-130">You can see those issues in the list that appears in the following image.</span></span>

![ProcMon Config.txt](images/desktop-to-uwp/procmon_config_txt.png)

<span data-ttu-id="aa28c-132">In der ersten Ausgabe, die in diesem Bild angezeigt wird, wird die Anwendung fehlschlägt, zum Lesen aus der Datei "Config.txt", die im Pfad "C:\Windows\SysWOW64" befindet.</span><span class="sxs-lookup"><span data-stu-id="aa28c-132">In the first issue that appears in this image, the application is failing to read from the "Config.txt" file that is located in the "C:\Windows\SysWOW64" path.</span></span> <span data-ttu-id="aa28c-133">Es ist unwahrscheinlich, dass die Anwendung versucht, diesen Pfad direkt zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-133">It's unlikely that the application is trying to reference that path directly.</span></span> <span data-ttu-id="aa28c-134">In den meisten Fällen versucht, ein relativer Pfad mit aus der Datei gelesen und in der Standardeinstellung ist "System32/SysWOW64" Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-134">Most likely, it's trying to read from that file by using a relative path, and by default, "System32/SysWOW64" is the application's working directory.</span></span> <span data-ttu-id="aa28c-135">Dies impliziert, dass die Anwendung die aktuelle Arbeitsverzeichnis, das an einer beliebigen Stelle im Paket festgelegt werden, um erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-135">This suggests that the application is expecting its current working directory to be set to somewhere in the package.</span></span> <span data-ttu-id="aa28c-136">Suchen in der Appx, sehen Sie, dass die Datei in demselben Verzeichnis wie die ausführbare Datei vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="aa28c-136">Looking inside of the appx, we can see that the file exists in the same directory as the executable.</span></span>

![App-Config.txt](images/desktop-to-uwp/psfsampleapp_config_txt.png)

<span data-ttu-id="aa28c-138">Das zweite Problem wird in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-138">The second issue appears in the following image.</span></span>

![ProcMon Protokolldatei](images/desktop-to-uwp/procmon_logfile.png)

<span data-ttu-id="aa28c-140">In diesem Problem fällt die Anwendung eine log-Datei in der Paketpfad zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-140">In this issue, the application is failing to write a .log file to its package path.</span></span> <span data-ttu-id="aa28c-141">Dies würde wird empfohlen, eine Datei Umleitung Korrektur hilfreich ist.</span><span class="sxs-lookup"><span data-stu-id="aa28c-141">This would suggest that a file redirection fixup might help.</span></span>

<a id="find" />

## <a name="find-a-runtime-fix"></a><span data-ttu-id="aa28c-142">Suchen nach einer Runtime-Lösung</span><span class="sxs-lookup"><span data-stu-id="aa28c-142">Find a runtime fix</span></span>

<span data-ttu-id="aa28c-143">Die PSF enthält Common Language Runtime-Updates, die Sie jetzt, wie z. B. die Datei Umleitung Korrektur verwenden können.</span><span class="sxs-lookup"><span data-stu-id="aa28c-143">The PSF contains runtime fixes that you can use right now, such as the file redirection fixup.</span></span>

### <a name="file-redirection-fixup"></a><span data-ttu-id="aa28c-144">Datei Umleitung Korrektur</span><span class="sxs-lookup"><span data-stu-id="aa28c-144">File Redirection Fixup</span></span>

<span data-ttu-id="aa28c-145">Die [Datei Umleitung Korrektur](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) können umleiten Versuche zum Schreiben oder Lesen von Daten in einem Verzeichnis, das von einer Anwendung zugänglich ist, die in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-145">You can use the [File Redirection Fixup](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to redirect attempts to write or read data in a directory that isn't accessible from an application that runs in an MSIX container.</span></span>

<span data-ttu-id="aa28c-146">Z. B. wenn die Anwendung in eine Protokolldatei, der in demselben Verzeichnis wie die ausführbare Anwendung ist schreibt, können klicken Sie dann die [Datei Umleitung Korrektur](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) Sie um die Protokolldatei in einen anderen Speicherort, z. B. den lokalen app-Datenspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-146">For example, if your application writes to a log file that is in the same directory as your applications executable, then you can use the [File Redirection Fixup](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop/FileRedirectionShim) to create that log file in another location, such as the local app data store.</span></span>

### <a name="runtime-fixes-from-the-community"></a><span data-ttu-id="aa28c-147">Runtime-Updates von der community</span><span class="sxs-lookup"><span data-stu-id="aa28c-147">Runtime fixes from the community</span></span>

<span data-ttu-id="aa28c-148">Achten Sie darauf, dass Sie die Community Beiträge unserer [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) -Seite zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-148">Make sure to review the community contributions to our [GitHub](https://github.com/Microsoft/MSIX-PackageSupportFramework/tree/develop) page.</span></span> <span data-ttu-id="aa28c-149">Es ist möglich, dass andere Entwickler eine ähnlich wie Ihr Problem gelöst haben und ein Laufzeit-Update freigegeben haben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-149">It's possible that other developers have resolved an issue similar to yours and have shared a runtime fix.</span></span>

## <a name="apply-a-runtime-fix"></a><span data-ttu-id="aa28c-150">Wenden Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="aa28c-150">Apply a runtime fix</span></span>

<span data-ttu-id="aa28c-151">Sie können eine vorhandene-Runtime-Update mit einigen einfachen Tools aus dem Windows SDK, und wie folgt anwenden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-151">You can apply an existing runtime fix with a few simple tools from the Windows SDK, and by following these steps.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="aa28c-152">Erstellen Sie ein Layout Paketordner</span><span class="sxs-lookup"><span data-stu-id="aa28c-152">Create a package layout folder</span></span>
> * <span data-ttu-id="aa28c-153">Die Paket-Support-Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="aa28c-153">Get the Package Support Framework files</span></span>
> * <span data-ttu-id="aa28c-154">Fügen Sie zu Ihrem Paket hinzu</span><span class="sxs-lookup"><span data-stu-id="aa28c-154">Add them to your package</span></span>
> * <span data-ttu-id="aa28c-155">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="aa28c-155">Modify the package manifest</span></span>
> * <span data-ttu-id="aa28c-156">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="aa28c-156">Create a configuration file</span></span>

<span data-ttu-id="aa28c-157">Lassen Sie uns über jede Aufgabe geleitet werden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-157">Let's go through each task.</span></span>

### <a name="create-the-package-layout-folder"></a><span data-ttu-id="aa28c-158">Erstellen Sie den Layout Paketordner</span><span class="sxs-lookup"><span data-stu-id="aa28c-158">Create the package layout folder</span></span>

<span data-ttu-id="aa28c-159">Wenn Sie bereits über eine Datei .msix (oder AppX) verfügen, können Sie den Inhalt in einem Layoutordner entpacken, die als die Staging-Bereich für Ihr Paket dient.</span><span class="sxs-lookup"><span data-stu-id="aa28c-159">If you have a .msix (or .appx) file already, you can unpack its contents into a layout folder that will serve as the staging area for your package.</span></span>  <span data-ttu-id="aa28c-160">Sie erreichen dies über eine **X64 Native Tools-Eingabeaufforderung für VS 2017**, oder manuell mit dem SDK Bin-Pfad in der ausführbaren Pfad.</span><span class="sxs-lookup"><span data-stu-id="aa28c-160">You can do this from an **x64 Native Tools Command Prompt for VS 2017**, or manually with the SDK bin path in the executable search path.</span></span>

```
makemsix unpack /p PSFSamplePackage_1.0.60.0_AnyCPU_Debug.msix /d PackageContents

```

<span data-ttu-id="aa28c-161">Dadurch erhalten etwas Sie, die wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="aa28c-161">This will give you something that looks like the following.</span></span>

![Paketlayout](images/desktop-to-uwp/package_contents.png)

<span data-ttu-id="aa28c-163">Wenn Sie eine Datei .msix (oder AppX) zu besitzen, können Sie die Paketordner und Dateien von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-163">If you don't have a .msix (or .appx) file to start with, you can create the package folder and files from scratch.</span></span>

### <a name="get-the-package-support-framework-files"></a><span data-ttu-id="aa28c-164">Die Paket-Support-Framework-Dateien zu erhalten</span><span class="sxs-lookup"><span data-stu-id="aa28c-164">Get the Package Support Framework files</span></span>

<span data-ttu-id="aa28c-165">Sie können das PSF Nuget-Paket abrufen, mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa28c-165">You can get the PSF Nuget package by using Visual Studio.</span></span> <span data-ttu-id="aa28c-166">Mithilfe der eigenständigen Nuget-Befehlszeilentool können sie auch abrufen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-166">You can also get it by using the standalone Nuget command line tool.</span></span>

#### <a name="get-the-package-by-using-visual-studio"></a><span data-ttu-id="aa28c-167">Rufen Sie das Paket mithilfe von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aa28c-167">Get the package by using Visual Studio</span></span>

<span data-ttu-id="aa28c-168">In Visual Studio mit der rechten Maustaste Ihrer Lösung oder Projektknoten, und wählen Sie einen der Befehle Nuget-Pakete verwalten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-168">In Visual Studio, right-click your solution or project node and pick one of the Manage Nuget Packages commands.</span></span>  <span data-ttu-id="aa28c-169">Suchen Sie nach **Microsoft.PackageSupportFramework** oder **PSF** , um das Paket unter "NuGet.org" suchen. Anschließend installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="aa28c-169">Search for **Microsoft.PackageSupportFramework** or **PSF** to find the package on Nuget.org. Then, install it.</span></span>

#### <a name="get-the-package-by-using-the-command-line-tool"></a><span data-ttu-id="aa28c-170">Rufen Sie das Paket mithilfe des Befehlszeilentools</span><span class="sxs-lookup"><span data-stu-id="aa28c-170">Get the package by using the command line tool</span></span>

<span data-ttu-id="aa28c-171">Installieren des Nuget-Befehlszeilentools von diesem Speicherort: https://www.nuget.org/downloads.</span><span class="sxs-lookup"><span data-stu-id="aa28c-171">Install the Nuget command line tool from this location: https://www.nuget.org/downloads.</span></span> <span data-ttu-id="aa28c-172">Führen Sie dann über die Befehlszeile Nuget diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="aa28c-172">Then, from the Nuget command line, run this command:</span></span>

```
nuget install Microsoft.PackageSupportFramework
```

### <a name="add-the-package-support-framework-files-to-your-package"></a><span data-ttu-id="aa28c-173">Fügen Sie die Support-Framework-Paket-Dateien zu Ihrem Paket</span><span class="sxs-lookup"><span data-stu-id="aa28c-173">Add the Package Support Framework files to your package</span></span>

<span data-ttu-id="aa28c-174">Erforderliche 32-Bit- und 64-Bit-PSF DLL-Dateien und ausführbaren Dateien in das Paketverzeichnis hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-174">Add the required 32-bit and 64-bit PSF  DLLs and executable files to the package directory.</span></span> <span data-ttu-id="aa28c-175">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="aa28c-175">Use the following table as a guide.</span></span> <span data-ttu-id="aa28c-176">Sie sollten auch alle Runtime Fixes enthalten, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-176">You'll also want to include any runtime fixes that you need.</span></span> <span data-ttu-id="aa28c-177">In unserem Beispiel benötigen wir die Datei Umleitung-Runtime-Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-177">In our example, we need the file redirection runtime fix.</span></span>

| <span data-ttu-id="aa28c-178">Die ausführbare Datei Anwendung ist x64</span><span class="sxs-lookup"><span data-stu-id="aa28c-178">Application executable is x64</span></span> | <span data-ttu-id="aa28c-179">Die ausführbare Datei Anwendung ist x86</span><span class="sxs-lookup"><span data-stu-id="aa28c-179">Application executable is x86</span></span> |
|-------------------------------|-----------|
| [<span data-ttu-id="aa28c-180">PSFLauncher64.exe</span><span class="sxs-lookup"><span data-stu-id="aa28c-180">PSFLauncher64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |  [<span data-ttu-id="aa28c-181">PSFLauncher32.exe</span><span class="sxs-lookup"><span data-stu-id="aa28c-181">PSFLauncher32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimLauncher/readme.md) |
| [<span data-ttu-id="aa28c-182">PSFRuntime64.dll</span><span class="sxs-lookup"><span data-stu-id="aa28c-182">PSFRuntime64.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) | [<span data-ttu-id="aa28c-183">PSFRuntime32.dll</span><span class="sxs-lookup"><span data-stu-id="aa28c-183">PSFRuntime32.dll</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRuntime/readme.md) |
| [<span data-ttu-id="aa28c-184">PSFRunDll64.exe</span><span class="sxs-lookup"><span data-stu-id="aa28c-184">PSFRunDll64.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) | [<span data-ttu-id="aa28c-185">PSFRunDll32.exe</span><span class="sxs-lookup"><span data-stu-id="aa28c-185">PSFRunDll32.exe</span></span>](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/ShimRunDll/readme.md) |

<span data-ttu-id="aa28c-186">Der Inhalt sollte jetzt wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-186">Your package content should now look something like this.</span></span>

![Paket-Binärdateien](images/desktop-to-uwp/package_binaries.png)

### <a name="modify-the-package-manifest"></a><span data-ttu-id="aa28c-188">Bearbeiten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="aa28c-188">Modify the package manifest</span></span>

<span data-ttu-id="aa28c-189">Öffnen Sie Ihr Paketmanifest in einem Text-Editor, und legen Sie die `Executable` -Attribut des der `Application` Element auf den Namen der ausführbaren Datei PSF Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="aa28c-189">Open your package manifest in a text editor, and then set the `Executable` attribute of the `Application` element to the name of the PSF launcher executable file.</span></span>  <span data-ttu-id="aa28c-190">Wenn Sie die Architektur der Zielanwendung kennen, wählen Sie die korrekte Version, PSFLauncher32.exe oder PSFLauncher64.exe.</span><span class="sxs-lookup"><span data-stu-id="aa28c-190">If you know the architecture of your target application, select the appropriate version, PSFLauncher32.exe or PSFLauncher64.exe.</span></span>  <span data-ttu-id="aa28c-191">Wenn dies nicht der Fall ist, PSFLauncher32.exe in allen Fällen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-191">If not, PSFLauncher32.exe will work in all cases.</span></span>  <span data-ttu-id="aa28c-192">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aa28c-192">Here's an example.</span></span>

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

### <a name="create-a-configuration-file"></a><span data-ttu-id="aa28c-193">Erstellen einer Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="aa28c-193">Create a configuration file</span></span>

<span data-ttu-id="aa28c-194">Erstellen Sie einen Dateinamen ``config.json``, und speichern Sie diese Datei in den Stammordner des Pakets.</span><span class="sxs-lookup"><span data-stu-id="aa28c-194">Create a file name ``config.json``, and save that file to the root folder of your package.</span></span> <span data-ttu-id="aa28c-195">Ändern Sie die deklarierte app-ID der Datei config.json auf die ausführbare Datei verweisen, den Sie gerade ersetzt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-195">Modify the declared app ID of the config.json file to point to the executable that you just replaced.</span></span> <span data-ttu-id="aa28c-196">Verwenden das wissen, das Sie an der Verwendung von Process Monitor erlangt, können Sie auch das Arbeitsverzeichnis sowie verwenden Sie die Datei Umleitung Korrektur Lese-/Schreibvorgänge an log-Dateien im Verzeichnis "PSFSampleApp" relativen umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="aa28c-196">Using the knowledge that you gained from using Process Monitor, you can also set the working directory as well as use the file redirection fixup to redirect reads/writes to .log files under the package-relative "PSFSampleApp" directory.</span></span>

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
<span data-ttu-id="aa28c-197">Im folgenden finden eine Anleitung für das Schema config.json:</span><span class="sxs-lookup"><span data-stu-id="aa28c-197">Following is a guide for the config.json schema:</span></span>

| <span data-ttu-id="aa28c-198">Array</span><span class="sxs-lookup"><span data-stu-id="aa28c-198">Array</span></span> | <span data-ttu-id="aa28c-199">key</span><span class="sxs-lookup"><span data-stu-id="aa28c-199">key</span></span> | <span data-ttu-id="aa28c-200">Wert</span><span class="sxs-lookup"><span data-stu-id="aa28c-200">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="aa28c-201">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-201">applications</span></span> | <span data-ttu-id="aa28c-202">id</span><span class="sxs-lookup"><span data-stu-id="aa28c-202">id</span></span> |  <span data-ttu-id="aa28c-203">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="aa28c-203">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="aa28c-204">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-204">applications</span></span> | <span data-ttu-id="aa28c-205">ausführbare</span><span class="sxs-lookup"><span data-stu-id="aa28c-205">executable</span></span> | <span data-ttu-id="aa28c-206">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-206">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="aa28c-207">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern.</span><span class="sxs-lookup"><span data-stu-id="aa28c-207">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="aa28c-208">Es ist der Wert der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="aa28c-208">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="aa28c-209">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-209">applications</span></span> | <span data-ttu-id="aa28c-210">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="aa28c-210">workingDirectory</span></span> | <span data-ttu-id="aa28c-211">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-211">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="aa28c-212">Wenn Sie diesen Wert nicht festlegen, der vom Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-212">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="aa28c-213">Prozesse</span><span class="sxs-lookup"><span data-stu-id="aa28c-213">processes</span></span> | <span data-ttu-id="aa28c-214">ausführbare</span><span class="sxs-lookup"><span data-stu-id="aa28c-214">executable</span></span> | <span data-ttu-id="aa28c-215">Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad- und Dateinamen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-215">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="aa28c-216">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="aa28c-216">fixups</span></span> | <span data-ttu-id="aa28c-217">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="aa28c-217">dll</span></span> | <span data-ttu-id="aa28c-218">Relativen Pfad zu der Korrektur.msix/.appx geladen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-218">Package-relative path to the fixup, .msix/.appx  to load.</span></span> |
| <span data-ttu-id="aa28c-219">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="aa28c-219">fixups</span></span> | <span data-ttu-id="aa28c-220">config</span><span class="sxs-lookup"><span data-stu-id="aa28c-220">config</span></span> | <span data-ttu-id="aa28c-221">(Optional) Steuert, wie die Korrektur Verteilerliste verhält.</span><span class="sxs-lookup"><span data-stu-id="aa28c-221">(Optional) Controls how the fixup dl behaves.</span></span> <span data-ttu-id="aa28c-222">Die genaue Format dieses Werts ist Korrektur von Korrektur regelmäßig wie jeder Korrektur dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="aa28c-222">The exact format of this value varies on a fixup-by-fixup basis as each fixup can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="aa28c-223">Die `applications`, `processes`, und `fixups` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="aa28c-223">The `applications`, `processes`, and `fixups` keys are arrays.</span></span> <span data-ttu-id="aa28c-224">Dies bedeutet, dass Sie die config.json-Datei verwenden können, um mehr als eine Anwendung, Prozessen und Korrektur DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-224">That means that you can use the config.json file to specify more than one application, process, and fixup DLL.</span></span>


### <a name="package-and-test-the-app"></a><span data-ttu-id="aa28c-225">Paket kennen und Testen der App</span><span class="sxs-lookup"><span data-stu-id="aa28c-225">Package and Test the App</span></span>

<span data-ttu-id="aa28c-226">Als Nächstes erstellen Sie ein Paket an.</span><span class="sxs-lookup"><span data-stu-id="aa28c-226">Next, create a package.</span></span>

```
makeappx pack /d PackageContents /p PSFSamplePackageFixup.msix
```

<span data-ttu-id="aa28c-227">Signieren Sie es dann.</span><span class="sxs-lookup"><span data-stu-id="aa28c-227">Then, sign it.</span></span>

```
signtool sign /a /v /fd sha256 /f ExportedSigningCertificate.pfx PSFSamplePackageFixup.msix
```

<span data-ttu-id="aa28c-228">Weitere Informationen finden Sie unter [So erstellen Sie ein Signaturzertifikat Paket](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) und [wie Sie ein Pakets mit signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span><span class="sxs-lookup"><span data-stu-id="aa28c-228">For more information, see [how to create a package signing certificate](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-create-a-package-signing-certificate) and [how to sign a package using signtool](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)</span></span>

<span data-ttu-id="aa28c-229">Mithilfe von PowerShell, installieren Sie das Paket.</span><span class="sxs-lookup"><span data-stu-id="aa28c-229">Using PowerShell, install the package.</span></span>

>[!NOTE]
> <span data-ttu-id="aa28c-230">Denken Sie daran, das Paket zuerst deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="aa28c-230">Remember to uninstall the package first.</span></span>

```
powershell Add-MSIXPackage .\PSFSamplePackageFixup.msix
```

<span data-ttu-id="aa28c-231">Führen Sie die Anwendung, und beobachten Sie das Verhalten mit Common Language Runtime-Updates angewendet.</span><span class="sxs-lookup"><span data-stu-id="aa28c-231">Run the application and observe the behavior with runtime fix applied.</span></span>  <span data-ttu-id="aa28c-232">Wiederholen Sie die Diagnose- und Verpacken Schritte nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="aa28c-232">Repeat the diagnostic and packaging steps as necessary.</span></span>

### <a name="use-the-trace-fixup"></a><span data-ttu-id="aa28c-233">Verwenden Sie die Korrektur Trace</span><span class="sxs-lookup"><span data-stu-id="aa28c-233">Use the Trace Fixup</span></span>

<span data-ttu-id="aa28c-234">Ein alternatives Verfahren zu diagnostizieren verpackte Probleme mit der Anwendungskompatibilität ist die Korrektur Trace verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-234">An alternative technique to diagnosing packaged application compatibility issues is to use the Trace Fixup.</span></span> <span data-ttu-id="aa28c-235">Diese DLL ist in der PSF enthalten und bietet eine detaillierte Ansicht der app Verhalten, ähnlich wie Process Monitor diagnostische.</span><span class="sxs-lookup"><span data-stu-id="aa28c-235">This DLL is included with the PSF and provides a detailed diagnostic view of the app's behavior, similar to Process Monitor.</span></span>  <span data-ttu-id="aa28c-236">Es ist speziell auf Probleme mit der Anwendungskompatibilität "einblenden".</span><span class="sxs-lookup"><span data-stu-id="aa28c-236">It is specially designed to reveal application compatibility issues.</span></span>  <span data-ttu-id="aa28c-237">Verwenden Sie die Korrektur Trace, die DLL für das Paket hinzufügen Ihrer config.json mit dem folgende Fragment hinzufügen und dann Verpacken und Installieren Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-237">To use the Trace Fixup, add the DLL to the package, add the following fragment to your config.json, and then package and install your application.</span></span>

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

<span data-ttu-id="aa28c-238">Standardmäßig filtert die Korrektur Trace Fehler, die berücksichtigt werden möglicherweise "erwartet".</span><span class="sxs-lookup"><span data-stu-id="aa28c-238">By default, the Trace Fixup filters out failures that might be considered "expected".</span></span>  <span data-ttu-id="aa28c-239">Beispielsweise Versuch Anwendungen bedingungslos Löschen einer Datei ohne Überprüfung, um festzustellen, ob sie vorhanden ist, wird das Ergebnis ignoriert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-239">For example, applications might try to unconditionally delete a file without checking to see if it already exists, ignoring the result.</span></span> <span data-ttu-id="aa28c-240">Dies hat die leider folgen, die einige unerwartete Fehler, gefiltert erhalten möglicherweise so melden Sie sich im obigen Beispiel wir an, um alle Fehler von Dateisystem-Funktionen zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-240">This has the unfortunate consequence that some unexpected failures might get filtered out, so in the above example, we opt to receive all failures from filesystem functions.</span></span> <span data-ttu-id="aa28c-241">Wir tun, da wir von vor, die das Lesen aus der Datei Config.txt fehlschlägt wissen mit "die Meldung Datei nicht gefunden".</span><span class="sxs-lookup"><span data-stu-id="aa28c-241">We do this because we know from before that the attempt to read from the Config.txt file fails with the message "file not found".</span></span> <span data-ttu-id="aa28c-242">Hierbei handelt es sich um einen Fehler, der häufig beobachtet und nicht in der Regel davon ausgegangen, dass unerwartet ist.</span><span class="sxs-lookup"><span data-stu-id="aa28c-242">This is a failure that is frequently observed and not generally assumed to be unexpected.</span></span> <span data-ttu-id="aa28c-243">In der Praxis ist es wahrscheinlich am besten, beginnen Sie mit dem Filterung nur für unerwartete Fehler und dann zurückgreifen auf alle Fehler liegt ein Problem, das weiterhin identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="aa28c-243">In practice it's likely best to start out filtering only to unexpected failures, and then falling back to all failures if there's an issue that still can't be identified.</span></span>

<span data-ttu-id="aa28c-244">Standardmäßig wird die Ausgabe die Korrektur Trace an den Debugger angefügte gesendet.</span><span class="sxs-lookup"><span data-stu-id="aa28c-244">By default, the output from the Trace Fixup gets sent to the attached debugger.</span></span> <span data-ttu-id="aa28c-245">In diesem Beispiel stellen wir sind nicht zu debuggen, und wird stattdessen mit dem [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) von SysInternals können Sie die Ausgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-245">For this example, we aren't going to attach a debugger, and will instead use the [DebugView](https://docs.microsoft.com/en-us/sysinternals/downloads/debugview) program from SysInternals to view its output.</span></span> <span data-ttu-id="aa28c-246">Nach dem Ausführen der app, sehen der gleiche Fehler wie zuvor, Sie die würden uns auf die gleichen-Runtime-Updates zeigen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-246">After running the app, we can see the same failures as before, which would point us towards the same runtime fixes.</span></span>

![TraceShim-Datei wurde nicht gefunden.](images/desktop-to-uwp/traceshim_filenotfound.png)

![TraceShim Zugriff verweigert](images/desktop-to-uwp/traceshim_accessdenied.png)

## <a name="debug-extend-or-create-a-runtime-fix"></a><span data-ttu-id="aa28c-249">Debuggen Sie, erweitern Sie oder erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="aa28c-249">Debug, extend, or create a runtime fix</span></span>

<span data-ttu-id="aa28c-250">Sie können Visual Studio Debuggen ein Laufzeit-Update, erweitern ein Laufzeit-Update oder von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-250">You can use Visual Studio to debug a runtime fix, extend a runtime fix, or create one from scratch.</span></span> <span data-ttu-id="aa28c-251">Sie müssen diese durchführen, um erfolgreich zu sein.</span><span class="sxs-lookup"><span data-stu-id="aa28c-251">You'll need to do these things to be successful.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="aa28c-252">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="aa28c-252">Add a packaging project</span></span>
> * <span data-ttu-id="aa28c-253">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="aa28c-253">Add project for the runtime fix</span></span>
> * <span data-ttu-id="aa28c-254">Fügen Sie ein Projekt, das die-Startprogramms PSF startet</span><span class="sxs-lookup"><span data-stu-id="aa28c-254">Add a project that starts the PSF Launcher executable</span></span>
> * <span data-ttu-id="aa28c-255">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="aa28c-255">Configure the packaging project</span></span>

<span data-ttu-id="aa28c-256">Wenn Sie fertig sind, wird die Projektmappe etwa wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-256">When you're done, your solution will look something like this.</span></span>

![Fertigen Lösung](images/desktop-to-uwp/runtime-fix-project-structure.png)

<span data-ttu-id="aa28c-258">Sehen wir uns auf jedes Projekt in diesem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="aa28c-258">Let's look at each project in this example.</span></span>

| <span data-ttu-id="aa28c-259">Projekt</span><span class="sxs-lookup"><span data-stu-id="aa28c-259">Project</span></span> | <span data-ttu-id="aa28c-260">Zweck</span><span class="sxs-lookup"><span data-stu-id="aa28c-260">Purpose</span></span> |
|-------|-----------|
| <span data-ttu-id="aa28c-261">DesktopApplicationPackage</span><span class="sxs-lookup"><span data-stu-id="aa28c-261">DesktopApplicationPackage</span></span> | <span data-ttu-id="aa28c-262">Dieses Projekt basiert auf dem [Windows Application Packaging Project](desktop-to-uwp-packaging-dot-net.md) und es gibt die MSIX-Paket.</span><span class="sxs-lookup"><span data-stu-id="aa28c-262">This project is based on the [Windows Application Packaging project](desktop-to-uwp-packaging-dot-net.md) and it outputs the the MSIX package.</span></span> |
| <span data-ttu-id="aa28c-263">Runtimefix</span><span class="sxs-lookup"><span data-stu-id="aa28c-263">Runtimefix</span></span> | <span data-ttu-id="aa28c-264">Dies ist ein C++ Dynamic-Linked Klassenbibliotheksprojekt hinzu, die eine oder mehrere Ersatzfunktionen enthält, die als die Common Language Runtime-Problembehandlung dienen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-264">This is a C++ Dynamic-Linked Library project that contains one or more replacement functions that serve as the runtime fix.</span></span> |
| <span data-ttu-id="aa28c-265">PSFLauncher</span><span class="sxs-lookup"><span data-stu-id="aa28c-265">PSFLauncher</span></span> | <span data-ttu-id="aa28c-266">Dies ist leeres C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-266">This is C++ Empty Project.</span></span> <span data-ttu-id="aa28c-267">Dieses Projekt ist ein Ort zum Abrufen der Runtime verteilbaren Dateien des Pakets Support-Frameworks.</span><span class="sxs-lookup"><span data-stu-id="aa28c-267">This project is a place to collect the runtime distributable files of the Package Support Framework.</span></span> <span data-ttu-id="aa28c-268">Es gibt eine ausführbare Datei.</span><span class="sxs-lookup"><span data-stu-id="aa28c-268">It outputs an executable file.</span></span> <span data-ttu-id="aa28c-269">Die ausführbare Datei ist der erste Schritt, der ausgeführt wird, wenn Sie die Projektmappe zu starten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-269">That executable is the first thing that runs when you start the solution.</span></span> |
| <span data-ttu-id="aa28c-270">WinFormsDesktopApplication</span><span class="sxs-lookup"><span data-stu-id="aa28c-270">WinFormsDesktopApplication</span></span> | <span data-ttu-id="aa28c-271">Dieses Projekt enthält den Quellcode einer desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-271">This project contains the source code of a desktop application.</span></span> |

<span data-ttu-id="aa28c-272">Um ein vollständiges Beispiel betrachten, die alle diese Arten von Projekten enthält, finden Sie unter [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span><span class="sxs-lookup"><span data-stu-id="aa28c-272">To look at a complete sample that contains all of these types of projects, see [PSFSample](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/samples/PSFSample/).</span></span>

<span data-ttu-id="aa28c-273">Betrachten Sie die Schritte zum Erstellen und Konfigurieren jedes dieser Projekte in Ihrer Projektmappe aus.</span><span class="sxs-lookup"><span data-stu-id="aa28c-273">Let's walk through the steps to create and configure each of these projects in your solution.</span></span>


### <a name="create-a-package-solution"></a><span data-ttu-id="aa28c-274">Erstellen Sie eine Paket-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="aa28c-274">Create a package solution</span></span>

<span data-ttu-id="aa28c-275">Wenn Sie bereits über eine Lösung für Ihre desktop-Anwendung besitzen, erstellen Sie eine neue **Leere Projektmappe** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa28c-275">If you don't already have a solution for your desktop application, create a new **Blank Solution** in Visual Studio.</span></span>

![Leere Projektmappe](images/desktop-to-uwp/blank-solution.png)

<span data-ttu-id="aa28c-277">Sie sollten auch alle Anwendungsprojekte, die hinzufügen, die Sie haben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-277">You may also want to add any application projects you have.</span></span>

### <a name="add-a-packaging-project"></a><span data-ttu-id="aa28c-278">Hinzufügen eines verpackungsprojekts</span><span class="sxs-lookup"><span data-stu-id="aa28c-278">Add a packaging project</span></span>

<span data-ttu-id="aa28c-279">Wenn Sie bereits über ein **Windows Application Packaging Project**besitzen, erstellen und in Ihrer Projektmappe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-279">If you don't already have a **Windows Application Packaging Project**, create one and add it to your solution.</span></span>

![Paket-Projektvorlage](images/desktop-to-uwp/package-project-template.png)

<span data-ttu-id="aa28c-281">Weitere Informationen zu Windows Application Packaging Project finden Sie unter [Paket Ihrer Anwendung mithilfe von Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="aa28c-281">For more information on Windows Application Packaging project, see [Package your application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

<span data-ttu-id="aa28c-282">Im **Projektmappen-Explorer**mit der rechten Maustaste des Verpacken-Projekts, wählen Sie **Bearbeiten**und klicken Sie dann am unteren Rand der Projektdatei hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="aa28c-282">In **Solution Explorer**, right-click the packaging project, select **Edit**, and then add this to the bottom of the project file:</span></span>

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

### <a name="add-project-for-the-runtime-fix"></a><span data-ttu-id="aa28c-283">Fügen Sie Projekt für die Common Language Runtime-Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="aa28c-283">Add project for the runtime fix</span></span>

<span data-ttu-id="aa28c-284">Ein C++- **Dll-Bibliothek (DLL)** -Projekt der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-284">Add a C++ **Dynamic-Link Library (DLL)** project to the solution.</span></span>

![Update-Laufzeitbibliothek](images/desktop-to-uwp/runtime-fix-library.png)

<span data-ttu-id="aa28c-286">Der rechten Maustaste auf das Projekt, und wählen Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="aa28c-286">Right-click the that project, and then choose **Properties**.</span></span>

<span data-ttu-id="aa28c-287">Auf den Eigenschaftenseiten suchen Sie das Feld **C++ Sprache Standard** , und wählen Sie dann in der Dropdownliste neben dem Feld, das **ISO C ++ 17 Standard (/ Std: c ++ 17)** Option.</span><span class="sxs-lookup"><span data-stu-id="aa28c-287">In the property pages, find the **C++ Language Standard** field, and then in the drop-down list next to that field, select the **ISO C++17 Standard (/std:c++17)** option.</span></span>

![ISO 17 Option](images/desktop-to-uwp/iso-option.png)

<span data-ttu-id="aa28c-289">Mit der rechten Maustaste in des Projekts, und klicken Sie dann im Kontextmenü die Option **Nuget-Pakete verwalten** .</span><span class="sxs-lookup"><span data-stu-id="aa28c-289">Right-click that project, and then in the context menu, choose the **Manage Nuget Packages** option.</span></span> <span data-ttu-id="aa28c-290">Stellen Sie sicher, dass die **Paketquelle** Option für **Alle** oder **"NuGet.org"** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="aa28c-290">Ensure that the **Package source** option is set to **All** or **nuget.org**.</span></span>

<span data-ttu-id="aa28c-291">Klicken Sie auf dem Symbol "Einstellungen" neben dem Feld.</span><span class="sxs-lookup"><span data-stu-id="aa28c-291">Click the settings icon next that field.</span></span>

<span data-ttu-id="aa28c-292">Suchen Sie nach der *PSF*\* Nuget Paket, und installieren Sie es für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-292">Search for the *PSF*\* Nuget package, and then install it for this project.</span></span>

![NuGet-Paket](images/desktop-to-uwp/psf-package.png)

<span data-ttu-id="aa28c-294">Wenn Sie Debuggen oder einen vorhandenen Runtime Fix erweitern möchten, fügen Sie die Runtime Update-Dateien, die Sie mithilfe der Anleitung im Abschnitt [Suchen nach einer Lösung für die Laufzeit](#find) dieses Handbuchs abgerufen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-294">If you want to debug or extend an existing runtime fix, add the runtime fix files that you obtained by using the guidance described in the [Find a runtime fix](#find) section of this guide.</span></span>

<span data-ttu-id="aa28c-295">Wenn Sie beabsichtigen, ein völlig neues Update zu erstellen, fügen Sie nicht alles dieses Projekt noch.</span><span class="sxs-lookup"><span data-stu-id="aa28c-295">If you intend to create a brand new fix, don't add anything to this project just yet.</span></span> <span data-ttu-id="aa28c-296">Wir helfen Ihnen, die richtigen Dateien in dieses Projekt weiter unten in diesem Handbuch hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-296">We'll help you add the right files to this project later in this guide.</span></span> <span data-ttu-id="aa28c-297">Für den Moment fahren wir Einrichten Ihrer Projektmappe fort.</span><span class="sxs-lookup"><span data-stu-id="aa28c-297">For now, we'll continue setting up your solution.</span></span>

### <a name="add-a-project-that-starts-the-psf-launcher-executable"></a><span data-ttu-id="aa28c-298">Fügen Sie ein Projekt, das die-Startprogramms PSF startet</span><span class="sxs-lookup"><span data-stu-id="aa28c-298">Add a project that starts the PSF Launcher executable</span></span>

<span data-ttu-id="aa28c-299">Fügen Sie der Projektmappe ein **Leeres Projekt** für C++-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="aa28c-299">Add a C++ **Empty Project** project to the solution.</span></span>

![Leeres Projekt](images/desktop-to-uwp/blank-app.png)

<span data-ttu-id="aa28c-301">Fügen Sie das **PSF** Nuget-Paket für dieses Projekt mithilfe von die gleichen Anleitungen, die im vorherigen Abschnitt beschriebene hinzu.</span><span class="sxs-lookup"><span data-stu-id="aa28c-301">Add the **PSF** Nuget package to this project by using the same guidance described in the previous section.</span></span>

<span data-ttu-id="aa28c-302">Öffnen die Eigenschaftenseiten des Projekts, und in die **Allgemeine** Seite "Einstellungen", setzen Sie den **Zielnamen** -Eigenschaft auf ``PSFLauncher32`` oder ``PSFLauncher64`` abhängig von der Architektur der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-302">Open the property pages for the project, and in the **General** settings page, set the **Target Name** property to ``PSFLauncher32`` or ``PSFLauncher64`` depending on the architecture of your application.</span></span>

![PSF Startprogramm-Referenz](images/desktop-to-uwp/shim-exe-reference.png)

<span data-ttu-id="aa28c-304">Fügen Sie einen Projektverweis auf die Common Language Runtime Update-Projekt in Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="aa28c-304">Add a project reference to the runtime fix project in your solution.</span></span>

![-Runtime-Fix-Referenz](images/desktop-to-uwp/reference-fix.png)

<span data-ttu-id="aa28c-306">Mit der rechten Maustaste in der Referenz, und klicken Sie dann im **Eigenschaftenfenster,** gelten diese Werte.</span><span class="sxs-lookup"><span data-stu-id="aa28c-306">Right-click the reference, and then in the **Properties** window, apply these values.</span></span>

| <span data-ttu-id="aa28c-307">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="aa28c-307">Property</span></span> | <span data-ttu-id="aa28c-308">Wert</span><span class="sxs-lookup"><span data-stu-id="aa28c-308">Value</span></span> |
|-------|-----------|
| <span data-ttu-id="aa28c-309">Kopieren Sie lokale</span><span class="sxs-lookup"><span data-stu-id="aa28c-309">Copy local</span></span> | <span data-ttu-id="aa28c-310">Wahr</span><span class="sxs-lookup"><span data-stu-id="aa28c-310">True</span></span> |
| <span data-ttu-id="aa28c-311">Lokale Satellitenassemblys kopieren</span><span class="sxs-lookup"><span data-stu-id="aa28c-311">Copy Local Satellite Assemblies</span></span> | <span data-ttu-id="aa28c-312">Wahr</span><span class="sxs-lookup"><span data-stu-id="aa28c-312">True</span></span> |
| <span data-ttu-id="aa28c-313">Referenz-Assembly-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="aa28c-313">Reference Assembly Output</span></span> | <span data-ttu-id="aa28c-314">Wahr</span><span class="sxs-lookup"><span data-stu-id="aa28c-314">True</span></span> |
| <span data-ttu-id="aa28c-315">Link-Bibliothek Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="aa28c-315">Link Library Dependencies</span></span> | <span data-ttu-id="aa28c-316">False</span><span class="sxs-lookup"><span data-stu-id="aa28c-316">False</span></span> |
| <span data-ttu-id="aa28c-317">Link-Bibliothek Abhängigkeit Eingaben</span><span class="sxs-lookup"><span data-stu-id="aa28c-317">Link Library Dependency Inputs</span></span> | <span data-ttu-id="aa28c-318">False</span><span class="sxs-lookup"><span data-stu-id="aa28c-318">False</span></span> |

### <a name="configure-the-packaging-project"></a><span data-ttu-id="aa28c-319">Konfigurieren Sie das verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="aa28c-319">Configure the packaging project</span></span>

<span data-ttu-id="aa28c-320">Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="aa28c-320">In the packaging project, right-click the **Applications** folder, and then choose **Add Reference**.</span></span>

![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-reference-packaging-project.png)

<span data-ttu-id="aa28c-322">Wählen Sie die PSF Startprogramm Projekt und Ihre desktop-Anwendung, und wählen Sie dann auf die Schaltfläche " **OK** ".</span><span class="sxs-lookup"><span data-stu-id="aa28c-322">Choose the PSF launcher project and your desktop application project, and then choose the **OK** button.</span></span>

![Desktopprojekt](images/desktop-to-uwp/package-project-references.png)

>[!NOTE]
> <span data-ttu-id="aa28c-324">Wenn Sie den Quellcode für Ihre Anwendung besitzen, wählen Sie einfach das PSF Startprogramm Projekt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-324">If you don't have the source code to your application, just choose the PSF launcher project.</span></span> <span data-ttu-id="aa28c-325">Wir zeigen Ihnen wie die EXE-Datei zu verweisen, wenn Sie eine Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-325">We'll show you how to reference your executable when you create a configuration file.</span></span>

<span data-ttu-id="aa28c-326">Klicken Sie im Knoten " **Anwendungen** " mit der rechten Maustaste die PSF startanwendung, und wählen Sie dann **als Einstiegspunkt festlegen**.</span><span class="sxs-lookup"><span data-stu-id="aa28c-326">In the **Applications** node, right-click the PSF launcher application, and then choose **Set as Entry Point**.</span></span>

![Als Einstiegspunkt festlegen](images/desktop-to-uwp/set-startup-project.png)

<span data-ttu-id="aa28c-328">Fügen Sie eine Datei mit dem Namen ``config.json`` zu Ihrem Projekt verpacken, kopieren und fügen Sie die folgenden Json-Text in die Datei.</span><span class="sxs-lookup"><span data-stu-id="aa28c-328">Add a file named ``config.json`` to your packaging project, then, copy and paste the following json text into the file.</span></span> <span data-ttu-id="aa28c-329">Legen Sie die **Aktion Paket** -Eigenschaft auf **Inhalte**.</span><span class="sxs-lookup"><span data-stu-id="aa28c-329">Set the **Package Action** property to **Content**.</span></span>

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
<span data-ttu-id="aa28c-330">Geben Sie einen Wert für jeden Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="aa28c-330">Provide a value for each key.</span></span> <span data-ttu-id="aa28c-331">Orientieren Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="aa28c-331">Use this table as a guide.</span></span>

| <span data-ttu-id="aa28c-332">Array</span><span class="sxs-lookup"><span data-stu-id="aa28c-332">Array</span></span> | <span data-ttu-id="aa28c-333">key</span><span class="sxs-lookup"><span data-stu-id="aa28c-333">key</span></span> | <span data-ttu-id="aa28c-334">Wert</span><span class="sxs-lookup"><span data-stu-id="aa28c-334">Value</span></span> |
|-------|-----------|-------|
| <span data-ttu-id="aa28c-335">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-335">applications</span></span> | <span data-ttu-id="aa28c-336">id</span><span class="sxs-lookup"><span data-stu-id="aa28c-336">id</span></span> |  <span data-ttu-id="aa28c-337">Verwenden Sie den Wert von der `Id` -Attribut des der `Application` Element im Paketmanifest.</span><span class="sxs-lookup"><span data-stu-id="aa28c-337">Use the value of the `Id` attribute of the `Application` element in the package manifest.</span></span> |
| <span data-ttu-id="aa28c-338">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-338">applications</span></span> | <span data-ttu-id="aa28c-339">ausführbare</span><span class="sxs-lookup"><span data-stu-id="aa28c-339">executable</span></span> | <span data-ttu-id="aa28c-340">Der relativen Pfad der ausführbaren Datei, die Sie starten möchten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-340">The package-relative path to the executable that you want to start.</span></span> <span data-ttu-id="aa28c-341">In den meisten Fällen können Sie diesen Wert aus der Paketmanifestdatei abrufen, bevor Sie diese ändern.</span><span class="sxs-lookup"><span data-stu-id="aa28c-341">In most cases, you can get this value from your package manifest file before you modify it.</span></span> <span data-ttu-id="aa28c-342">Es ist der Wert der `Executable` -Attribut des der `Application` Element.</span><span class="sxs-lookup"><span data-stu-id="aa28c-342">It's the value of the `Executable` attribute of the `Application` element.</span></span> |
| <span data-ttu-id="aa28c-343">applications</span><span class="sxs-lookup"><span data-stu-id="aa28c-343">applications</span></span> | <span data-ttu-id="aa28c-344">workingDirectory</span><span class="sxs-lookup"><span data-stu-id="aa28c-344">workingDirectory</span></span> | <span data-ttu-id="aa28c-345">(Optional) Einen relativen Pfad, als das Arbeitsverzeichnis der Anwendung, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-345">(Optional) A package-relative path to use as the working directory of the application that starts.</span></span> <span data-ttu-id="aa28c-346">Wenn Sie diesen Wert nicht festlegen, der vom Betriebssystem verwendet die `System32` Verzeichnis als Arbeitsverzeichnis der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-346">If you don't set this value, the operating system uses the `System32` directory as the application's working directory.</span></span> |
| <span data-ttu-id="aa28c-347">Prozesse</span><span class="sxs-lookup"><span data-stu-id="aa28c-347">processes</span></span> | <span data-ttu-id="aa28c-348">ausführbare</span><span class="sxs-lookup"><span data-stu-id="aa28c-348">executable</span></span> | <span data-ttu-id="aa28c-349">Dies ist in den meisten Fällen ist der Name des, die `executable` oben mit der Erweiterung Pfad- und Dateinamen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-349">In most cases, this will be the name of the `executable` configured above with the path and file extension removed.</span></span> |
| <span data-ttu-id="aa28c-350">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="aa28c-350">fixups</span></span> | <span data-ttu-id="aa28c-351">DLL-Datei</span><span class="sxs-lookup"><span data-stu-id="aa28c-351">dll</span></span> | <span data-ttu-id="aa28c-352">Relativen Pfad zu der Korrektur DLL zu laden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-352">Package-relative path to the fixup DLL to load.</span></span> |
| <span data-ttu-id="aa28c-353">Korrekturen</span><span class="sxs-lookup"><span data-stu-id="aa28c-353">fixups</span></span> | <span data-ttu-id="aa28c-354">config</span><span class="sxs-lookup"><span data-stu-id="aa28c-354">config</span></span> | <span data-ttu-id="aa28c-355">(Optional) Steuert, wie die Korrektur DLL verhält.</span><span class="sxs-lookup"><span data-stu-id="aa28c-355">(Optional) Controls how the fixup DLL behaves.</span></span> <span data-ttu-id="aa28c-356">Die genaue Format dieses Werts ist Korrektur von Korrektur regelmäßig wie jeder Korrektur dieses "Blob" interpretiert werden kann, wie möglich.</span><span class="sxs-lookup"><span data-stu-id="aa28c-356">The exact format of this value varies on a fixup-by-fixup basis as each fixup can interpret this "blob" as it wants.</span></span> |

<span data-ttu-id="aa28c-357">Wenn Sie fertig sind, Ihre ``config.json`` Datei sieht etwa wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="aa28c-357">When you're done, your ``config.json`` file will look something like this.</span></span>

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
> <span data-ttu-id="aa28c-358">Die `applications`, `processes`, und `fixups` Schlüssel sind Arrays.</span><span class="sxs-lookup"><span data-stu-id="aa28c-358">The `applications`, `processes`, and `fixups` keys are arrays.</span></span> <span data-ttu-id="aa28c-359">Dies bedeutet, dass Sie die config.json-Datei verwenden können, um mehr als eine Anwendung, Prozessen und Korrektur DLL anzugeben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-359">That means that you can use the config.json file to specify more than one application, process, and fixup DLL.</span></span>

### <a name="debug-a-runtime-fix"></a><span data-ttu-id="aa28c-360">Debuggen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="aa28c-360">Debug a runtime fix</span></span>

<span data-ttu-id="aa28c-361">Drücken Sie in Visual Studio F5, um den Debugger zu starten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-361">In Visual Studio, press F5 to start the debugger.</span></span>  <span data-ttu-id="aa28c-362">Der erste Schritt, der beginnt ist der startanwendung PSF, die wiederum die Ziel-desktop-Anwendung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-362">The first thing that starts is the PSF launcher application, which in turn, starts your target desktop application.</span></span>  <span data-ttu-id="aa28c-363">Um die Ziel-desktop-Anwendung zu debuggen, müssen Sie manuell auf den desktop-Anwendungsprozess anhängen, indem Sie **Debuggen**auswählen->**an den Prozess anhängen**, auswählen und dann den bewerbungsprozess.</span><span class="sxs-lookup"><span data-stu-id="aa28c-363">To debug the target desktop application, you'll have to manually attach to the desktop application process by choosing **Debug**->**Attach to Process**, and then selecting the application process.</span></span> <span data-ttu-id="aa28c-364">Um das Debuggen einer .NET-Anwendung mit einer systemeigenen Runtime Update DLL zu ermöglichen, wählen Sie verwalteten und systemeigenen Code (im gemischten Modus Debuggen).</span><span class="sxs-lookup"><span data-stu-id="aa28c-364">To permit the debugging of a .NET application with a native runtime fix DLL, select managed and native code types (mixed mode debugging).</span></span>  

<span data-ttu-id="aa28c-365">Nachdem Sie dies eingerichtet haben, können Sie Haltepunkte neben Codezeilen in der desktop-Anwendungscode und die Runtime Update-Projekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-365">Once you've set this up, you can set break points next to lines of code in the desktop application code and the runtime fix project.</span></span> <span data-ttu-id="aa28c-366">Wenn Sie den Quellcode für Ihre Anwendung besitzen, werden Sie Haltepunkte nur neben Codezeilen in Ihrem Projekt der Runtime Update festlegen können.</span><span class="sxs-lookup"><span data-stu-id="aa28c-366">If you don't have the source code to your application, you'll be able to set break points only next to lines of code in your runtime fix project.</span></span>

>[!NOTE]
> <span data-ttu-id="aa28c-367">Wenn Visual Studio Ihnen die einfachste Entwicklung bietet und Debuggen, es einige Einschränkungen gibt, dies später in diesem Handbuch erläutern wir, andere debugging Techniken, die Sie anwenden können.</span><span class="sxs-lookup"><span data-stu-id="aa28c-367">While Visual Studio gives you the simplest development and debugging experience, there are some limitations, so later in this guide, we'll discuss other debugging techniques that you can apply.</span></span>

## <a name="create-a-runtime-fix"></a><span data-ttu-id="aa28c-368">Erstellen Sie ein Laufzeit-Update</span><span class="sxs-lookup"><span data-stu-id="aa28c-368">Create a runtime fix</span></span>

<span data-ttu-id="aa28c-369">Wenn es keinen noch eine Laufzeit für das Problem beheben, aufgelöst werden soll, können Sie erstellen ein neues Runtime Update schreiben Ersatzfunktionen und alle Konfigurationsdaten, darunter ist, die sinnvoll.</span><span class="sxs-lookup"><span data-stu-id="aa28c-369">If there isn't yet a runtime fix for the issue that you want to resolve, you can create a new runtime fix by writing replacement functions and including any configuration data that makes sense.</span></span> <span data-ttu-id="aa28c-370">Sehen wir uns auf jeder Teil.</span><span class="sxs-lookup"><span data-stu-id="aa28c-370">Let's look at each part.</span></span>

### <a name="replacement-functions"></a><span data-ttu-id="aa28c-371">Ersatzfunktionen</span><span class="sxs-lookup"><span data-stu-id="aa28c-371">Replacement functions</span></span>

<span data-ttu-id="aa28c-372">Identifizieren Sie zunächst, welche Funktion ruft fehl, wenn die Anwendung in einem MSIX-Container ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aa28c-372">First, identify which function calls fail when your application runs in an MSIX container.</span></span> <span data-ttu-id="aa28c-373">Anschließend können Sie Ersatzfunktionen erstellen, die Sie der Runtime-Manager, um stattdessen aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-373">Then, you can create replacement functions that you'd like the runtime manager to call instead.</span></span> <span data-ttu-id="aa28c-374">Dies bietet Ihnen die Möglichkeit, die Implementierung einer Funktion mit dem Verhalten zu ersetzen, die die Regeln für die moderne Runtime-Umgebung entspricht.</span><span class="sxs-lookup"><span data-stu-id="aa28c-374">This gives you an opportunity to replace the implementation of a function with behavior that conforms to the rules of the modern runtime environment.</span></span>

<span data-ttu-id="aa28c-375">Öffnen Sie das Projekt der Runtime-Update, das Sie weiter oben in diesem Handbuch erstellt haben, in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa28c-375">In Visual Studio, open the runtime fix project that you created earlier in this guide.</span></span>

<span data-ttu-id="aa28c-376">Deklarieren Sie die ``FIXUP_DEFINE_EXPORTS`` Makro und fügen Sie eine Include-Anweisung für die `fixup_framework.h` am Anfang jeder. CPP-Datei, in denen Sie die Funktionen der Common Language Runtime-Updates hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-376">Declare the ``FIXUP_DEFINE_EXPORTS`` macro and then add a include statement for the `fixup_framework.h` at the top of each .CPP file where you intend to add the functions of your runtime fix.</span></span>

```c++
#define FIXUP_DEFINE_EXPORTS
#include <fixup_framework.h>
```
>[!IMPORTANT]
><span data-ttu-id="aa28c-377">Stellen Sie sicher, dass die `FIXUP_DEFINE_EXPORTS` Makro wird vor der Include-Anweisung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-377">Make sure that the `FIXUP_DEFINE_EXPORTS` macro appears before the include statement.</span></span>

<span data-ttu-id="aa28c-378">Erstellen Sie eine Funktion, die dieselbe Signatur der Funktion hat, hat Verhalten, die Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="aa28c-378">Create a function that has the same signature of the function who's behavior you want to modify.</span></span> <span data-ttu-id="aa28c-379">Hier ist eine Beispielfunktion, die ersetzt die `MessageBoxW` Funktion.</span><span class="sxs-lookup"><span data-stu-id="aa28c-379">Here's an example function that replaces the `MessageBoxW` function.</span></span>

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

<span data-ttu-id="aa28c-380">Beim Aufruf von `DECLARE_FIXUP` ordnet die `MessageBoxW` in Ihrer neuen-Funktion als Ersatz.</span><span class="sxs-lookup"><span data-stu-id="aa28c-380">The call to `DECLARE_FIXUP` maps the `MessageBoxW` function to your new replacement function.</span></span> <span data-ttu-id="aa28c-381">Wenn Ihre Anwendung versucht, rufen Sie die `MessageBoxW` Funktion es Ruft die Ersatz-Funktion stattdessen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-381">When your application attempts to call the `MessageBoxW` function, it will call the replacement function instead.</span></span>

#### <a name="protect-against-recursive-calls-to-functions-in-runtime-fixes"></a><span data-ttu-id="aa28c-382">Schutz vor rekursiven Aufrufe von Funktionen in Common Language Runtime-Updates</span><span class="sxs-lookup"><span data-stu-id="aa28c-382">Protect against recursive calls to functions in runtime fixes</span></span>

<span data-ttu-id="aa28c-383">Sie können optional anwenden, die `reentrancy_guard` geben, um Ihre Funktionen, die Schutz gegen rekursiven Aufrufe von Funktionen in Common Language Runtime-Updates.</span><span class="sxs-lookup"><span data-stu-id="aa28c-383">You can optionally apply the `reentrancy_guard` type to your functions that protect against recursive calls to functions in runtime fixes.</span></span>

<span data-ttu-id="aa28c-384">Beispielsweise können Sie erzeugen, eine Funktion Ersatz für die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="aa28c-384">For example, you might produce a replacement function for the `CreateFile` function.</span></span> <span data-ttu-id="aa28c-385">Die Implementierung aufrufen kann die `CopyFile` -Funktion, aber die Implementierung von der `CopyFile` Funktionsaufruf möglicherweise die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="aa28c-385">Your implementation might call the `CopyFile` function, but the implementation of the `CopyFile` function might call the `CreateFile` function.</span></span> <span data-ttu-id="aa28c-386">Dies kann dazu führen, dass einer unendlichen rekursiven Zyklus von Aufrufen an die `CreateFile` Funktion.</span><span class="sxs-lookup"><span data-stu-id="aa28c-386">This may lead to an infinite recursive cycle of calls to the `CreateFile` function.</span></span>

<span data-ttu-id="aa28c-387">Weitere Informationen zu `reentrancy_guard` finden Sie unter [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span><span class="sxs-lookup"><span data-stu-id="aa28c-387">For more information on `reentrancy_guard` see [authoring.md](https://github.com/Microsoft/MSIX-PackageSupportFramework/blob/master/Authoring.md)</span></span>

### <a name="configuration-data"></a><span data-ttu-id="aa28c-388">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="aa28c-388">Configuration data</span></span>

<span data-ttu-id="aa28c-389">Wenn Sie Konfigurationsdaten zu Ihrer Laufzeit-Update hinzufügen möchten, in Betracht ziehen, um die ``config.json``.</span><span class="sxs-lookup"><span data-stu-id="aa28c-389">If you want to add configuration data to your runtime fix, consider adding it to the ``config.json``.</span></span> <span data-ttu-id="aa28c-390">Auf diese Weise können Sie die `FixupQueryCurrentDllConfig` einfach diese Daten analysiert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-390">That way, you can use the `FixupQueryCurrentDllConfig` to easily parse that data.</span></span> <span data-ttu-id="aa28c-391">In diesem Beispiel wird einen Boolean und String Wert aus der Konfigurationsdatei analysiert.</span><span class="sxs-lookup"><span data-stu-id="aa28c-391">This example parses a boolean and string value from that configuration file.</span></span>

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

## <a name="other-debugging-techniques"></a><span data-ttu-id="aa28c-392">Andere debugging-Techniken</span><span class="sxs-lookup"><span data-stu-id="aa28c-392">Other debugging techniques</span></span>

<span data-ttu-id="aa28c-393">Während Visual Studio die einfachste Entwicklung und das debugging Erfahrung Ihnen bietet, gibt es einige Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-393">While Visual Studio gives you the simplest development and debugging experience, there are some limitations.</span></span>

<span data-ttu-id="aa28c-394">Erstens Debuggens mit F5 führt die Anwendung durch die Bereitstellung von losen Dateien aus dem Paket Layout Ordnerpfad, installieren, sondern von einer .msix / AppX-Pakets.</span><span class="sxs-lookup"><span data-stu-id="aa28c-394">First, F5 debugging runs the application by deploying loose files from the package layout folder path, rather than installing from a .msix / .appx package.</span></span>  <span data-ttu-id="aa28c-395">Die Layoutordner verfügt in der Regel nicht dieselben sicherheitseinschränkungen, die als eine installierte Paketordner.</span><span class="sxs-lookup"><span data-stu-id="aa28c-395">The layout folder typically does not have the same security restrictions as an installed package folder.</span></span> <span data-ttu-id="aa28c-396">Daher kann es nicht Paket Pfad Denial Zugriffsfehler vor einer Runtime Update reproduziert werden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-396">As a result, it may not be possible to reproduce package path access denial errors prior to applying a runtime fix.</span></span>

<span data-ttu-id="aa28c-397">Um dieses Problem zu beheben, verwenden Sie .msix / Bereitstellung des AppX-Pakets statt F5 lose Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="aa28c-397">To address this issue, use .msix / .appx package deployment rather than F5 loose file deployment.</span></span>  <span data-ttu-id="aa28c-398">Erstellen Sie eine .msix / AppX-Paket-Datei, die [MakeMSIX](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) Utility aus dem Windows SDK verwenden, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="aa28c-398">To create a .msix / .appx package file, use the [MakeMSIX](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-) utility from the Windows SDK, as described above.</span></span> <span data-ttu-id="aa28c-399">Oder in Visual Studio Maustaste auf den Projektknoten Anwendung und wählen **Store**->**App-Pakete erstellen**.</span><span class="sxs-lookup"><span data-stu-id="aa28c-399">Or, from within Visual Studio, right-click your application project node and select **Store**->**Create App Packages**.</span></span>

<span data-ttu-id="aa28c-400">Ein weiteres Problem mit Visual Studio ist, dass es keine integrierten Unterstützung für das Anhängen an untergeordnete Prozesse gestartet, indem Sie den Debugger enthält.</span><span class="sxs-lookup"><span data-stu-id="aa28c-400">Another issue with Visual Studio is that it does not have built-in support for attaching to any child processes launched by the debugger.</span></span>   <span data-ttu-id="aa28c-401">Dies erschwert es so Debuggen Sie Logik im Startpfad der Zielanwendung, die nach der Einführung von Visual Studio manuell angefügt werden muss.</span><span class="sxs-lookup"><span data-stu-id="aa28c-401">This makes it difficult to debug logic in the startup path of the target application, which must be manually attached by Visual Studio after launch.</span></span>

<span data-ttu-id="aa28c-402">Um dieses Problem zu beheben, verwenden Sie einen Debugger untergeordneter Prozess anhängen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aa28c-402">To address this issue, use a debugger that supports child process attach.</span></span>  <span data-ttu-id="aa28c-403">Beachten Sie, dass es in der Regel nicht möglich, Just-in-Time (JIT) der Zielanwendung Debuggen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-403">Note that it is generally not possible to attach a just-in-time (JIT) debugger to the target application.</span></span>  <span data-ttu-id="aa28c-404">Grund dafür ist die meisten JIT-Techniken des Debuggers anstelle der Ziel-app, über den Registrierungsschlüssel ImageFileExecutionOptions.</span><span class="sxs-lookup"><span data-stu-id="aa28c-404">This is because most JIT techniques involve launching the debugger in place of the target app, via the ImageFileExecutionOptions registry key.</span></span>  <span data-ttu-id="aa28c-405">Diese "vereitelt" wird den detouring Mechanismus zur Bestimmung von PSFLauncher.exe FixupRuntime.dll in der Ziel-app einzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-405">This defeats the detouring mechanism used by PSFLauncher.exe to inject FixupRuntime.dll into the target app.</span></span>  <span data-ttu-id="aa28c-406">WinDbg, in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)und aus dem [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk)abgerufenen, unterstützt untergeordneter Prozess anfügen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-406">WinDbg, included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index), and obtained from the [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk), supports child process attach.</span></span>  <span data-ttu-id="aa28c-407">Unterstützt jetzt auch direkt [Starten und Debuggen einer UWP-Apps](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span><span class="sxs-lookup"><span data-stu-id="aa28c-407">It also now supports directly [launching and debugging a UWP app](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-a-uwp-app-using-windbg#span-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanspan-idlaunchinganddebuggingauwpappspanlaunching-and-debugging-a-uwp-app).</span></span>

<span data-ttu-id="aa28c-408">Zum Ziel Anwendungsstart als untergeordneter Prozess Debuggen starten ``WinDbg``.</span><span class="sxs-lookup"><span data-stu-id="aa28c-408">To debug target application startup as a child process, start ``WinDbg``.</span></span>

```
windbg.exe -plmPackage PSFSampleWithFixup_1.0.59.0_x86__7s220nvg1hg3m -plmApp PSFSample
```

<span data-ttu-id="aa28c-409">Bei der ``WinDbg`` auffordern, untergeordnete Debuggen aktivieren und entsprechende Haltepunkte festlegen.</span><span class="sxs-lookup"><span data-stu-id="aa28c-409">At the ``WinDbg`` prompt, enable child debugging and set appropriate breakpoints.</span></span>

```
.childdbg 1
g
```
<span data-ttu-id="aa28c-410">(ausgeführt wird, bis die Anwendung beginnt und in den Debugger unterbricht)</span><span class="sxs-lookup"><span data-stu-id="aa28c-410">(execute until target application starts and breaks into the debugger)</span></span>

```
sxe ld fixup.dll
g
```
<span data-ttu-id="aa28c-411">(erst ausgeführt, wenn die Korrektur aus die DLL geladen wird)</span><span class="sxs-lookup"><span data-stu-id="aa28c-411">(execute until the fixup DLL is loaded)</span></span>

```
bp ...
```

>[!NOTE]
> <span data-ttu-id="aa28c-412">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) können auch verwendet werden, um eine app nach dem Start Debuggen und auch in der [Debugtools für Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index)enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="aa28c-412">[PLMDebug](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/plmdebug) can be also used to attach a debugger to an app upon launch, and is also included in the [Debugging Tools for Windows](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/index).</span></span>  <span data-ttu-id="aa28c-413">Es ist jedoch komplexer als das direkte unterstützt jetzt WinDbg verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa28c-413">However, it is more complex to use than the direct support now provided by WinDbg.</span></span>

## <a name="support-and-feedback"></a><span data-ttu-id="aa28c-414">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="aa28c-414">Support and feedback</span></span>

**<span data-ttu-id="aa28c-415">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="aa28c-415">Find answers to your questions</span></span>**

<span data-ttu-id="aa28c-416">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="aa28c-416">Have questions?</span></span> <span data-ttu-id="aa28c-417">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="aa28c-417">Ask us on Stack Overflow.</span></span> <span data-ttu-id="aa28c-418">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="aa28c-418">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="aa28c-419">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="aa28c-419">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

