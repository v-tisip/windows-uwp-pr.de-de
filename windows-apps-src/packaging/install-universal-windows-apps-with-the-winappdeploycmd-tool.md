---
author: laurenhughes
ms.assetid: 6AA037C0-35ED-4B9C-80A3-5E144D7EE94B
title: Installieren von Apps mit dem Tool „WinAppDeployCmd.exe“
description: Windows-Anwendungsbereitstellung (WinAppDeployCmd.exe) ist ein Befehlszeilentool, mit denen eine app (universelle Windows Plattform) von einem Windows 10-PC auf einem Gerät mit Windows 10 bereitstellen.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 13468ce3b74992c026d94223b5e67aea99d79991
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6044080"
---
# <a name="install-apps-with-the-winappdeploycmdexe-tool"></a><span data-ttu-id="16c9b-104">Installieren von Apps mit dem Tool „WinAppDeployCmd.exe“</span><span class="sxs-lookup"><span data-stu-id="16c9b-104">Install apps with the WinAppDeployCmd.exe tool</span></span>


<span data-ttu-id="16c9b-105">Windows-Anwendungsbereitstellung (WinAppDeployCmd.exe) ist ein Befehlszeilentool, mit denen eine app (universelle Windows Plattform) von einem Windows 10-PC auf einem Gerät mit Windows 10 bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-105">Windows Application Deployment (WinAppDeployCmd.exe) is a command line tool that can use to deploy a Universal Windows Platform (UWP) app from a Windows10 PC to any Windows10 device.</span></span> <span data-ttu-id="16c9b-106">Sie können dieses Tool verwenden, um ein app-Paket bereitzustellen, wenn das Windows 10-Gerät über USB verbunden ist oder sich im gleichen Subnetz verfügbar ist, ohne Microsoft Visual Studio oder die Projektmappe für diese app.</span><span class="sxs-lookup"><span data-stu-id="16c9b-106">You can use this tool to deploy an app package when the Windows10 device is connected by USB or available on the same subnet without needing Microsoft Visual Studio or the solution for that app.</span></span> <span data-ttu-id="16c9b-107">Sie können die App auch bereitstellen, ohne sie zuerst zu einem Remote-PC oder zu Xbox One zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="16c9b-107">You can also deploy the app without packaging first to a remote PC or Xbox One.</span></span> <span data-ttu-id="16c9b-108">Dieser Artikel beschreibt, wie UWP-Apps mit diesem Tool installiert werden.</span><span class="sxs-lookup"><span data-stu-id="16c9b-108">This article describes how to install UWP apps using this tool.</span></span>

<span data-ttu-id="16c9b-109">Sie benötigen nur das Windows 10 SDK installiert sein, damit das Tool WinAppDeployCmd über eine Eingabeaufforderung oder eine Skriptdatei ausführen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-109">You just need the Windows10 SDK installed to run the WinAppDeployCmd tool from a command prompt or a script file.</span></span> <span data-ttu-id="16c9b-110">Wenn Sie eine app mit WinAppDeployCmd.exe installieren, verwendet diese die.appx/.msix Datei oder AppxManifest (für lose Dateien) zu Ihrer app auf einem Windows 10-Gerät querzuladen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-110">When you install an app with WinAppDeployCmd.exe, this uses the .appx/.msix file or AppxManifest(for loose files) to side-load your app onto a Windows10 device.</span></span> <span data-ttu-id="16c9b-111">Mit diesem Befehl wird nicht das für Ihre App erforderliche Zertifikat installiert.</span><span class="sxs-lookup"><span data-stu-id="16c9b-111">This command does not install the certificate required for your app.</span></span> <span data-ttu-id="16c9b-112">Zum Ausführen der app muss das Windows 10-Gerät im Entwicklermodus werden oder bereits das Zertifikat installiert haben.</span><span class="sxs-lookup"><span data-stu-id="16c9b-112">To run the app, the Windows10 device must be in developer mode or already have the certificate installed.</span></span>

<span data-ttu-id="16c9b-113">Um eine Bereitstellung auf mobilen Geräten auszuführen, müssen Sie zunächst ein Paket erstellen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-113">To deploy to mobile devices, you must first create a package.</span></span> <span data-ttu-id="16c9b-114">Weitere Informationen finden Sie [hier](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="16c9b-114">For more information, see [here](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

<span data-ttu-id="16c9b-115">Das **WinAppDeployCmd.exe** Tool befindet sich hier auf Ihrem Windows 10-PC: **C:\\Program Files (x86) \\Windows Kits\\10\\bin\\<SDK Version>\\x86\\WinAppDeployCmd.exe** (abhängig vom Installationspfad für das SDK).</span><span class="sxs-lookup"><span data-stu-id="16c9b-115">The **WinAppDeployCmd.exe** tool is located here on your Windows10 PC: **C:\\Program Files (x86)\\Windows Kits\\10\\bin\\<SDK Version>\\x86\\WinAppDeployCmd.exe** (based on your installation path for the SDK).</span></span> 
> [!NOTE]
> <span data-ttu-id="16c9b-116">In Version 15063 und höher des SDK ist das SDK nebeneinander in versionsspezifischen Ordnern installiert.</span><span class="sxs-lookup"><span data-stu-id="16c9b-116">In version 15063 and later of the SDK, the SDK is installed side by side within version-specific folders.</span></span>  <span data-ttu-id="16c9b-117">Frühere SDKs (vor und einschließlich 14393) werden direkt in den übergeordneten Ordner geschrieben.</span><span class="sxs-lookup"><span data-stu-id="16c9b-117">Previous SDKs (prior to and including 14393) are written directly to the parent folder.</span></span>

<span data-ttu-id="16c9b-118">Zunächst verbinden Sie das Windows 10-Gerät mit dem gleichen Subnetz oder Verbinden Sie ihn direkt mit Ihrem Windows 10-Computer über eine USB-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="16c9b-118">First, connect your Windows10 device to the same subnet or connect it directly to your Windows10 machine with a USB connection.</span></span> <span data-ttu-id="16c9b-119">Verwenden Sie anschließend die folgende Syntax und die Beispiele zu diesem Befehl weiter unten in diesem Artikel, um die UWP-App bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="16c9b-119">Then use the following syntax and examples of this command later in this article to deploy your UWP app:</span></span>

## <a name="winappdeploycmd-syntax-and-options"></a><span data-ttu-id="16c9b-120">Syntax und Optionen für WinAppDeployCmd</span><span class="sxs-lookup"><span data-stu-id="16c9b-120">WinAppDeployCmd syntax and options</span></span>

<span data-ttu-id="16c9b-121">Dies ist die allgemeine, für **WinAppDeployCmd.exe** verwendete Syntax:</span><span class="sxs-lookup"><span data-stu-id="16c9b-121">This is the general syntax used for **WinAppDeployCmd.exe**:</span></span>
```syntax
WinAppDeployCmd command -option <argument>
```

<span data-ttu-id="16c9b-122">Hier finden Sie einige zusätzliche Syntaxbeispiele für die Verwendung verschiedener Befehle:</span><span class="sxs-lookup"><span data-stu-id="16c9b-122">Here are some additional syntax examples for using various commands:</span></span>
```syntax
WinAppDeployCmd devices
WinAppDeployCmd devices <x>
WinAppDeployCmd install -file <path> -ip <address>
WinAppDeployCmd install -file <path> -guid <address> -pin <p>
WinAppDeployCmd install -file <path> -ip <address> -dependency <a> <b> 
WinAppDeployCmd install -file <path> -guid <address> -dependency <a> <b>
WinAppDeployCmd uninstall -file <path>
WinAppDeployCmd uninstall -package <name>
WinAppDeployCmd update -file <path>
WinAppDeployCmd list -ip <address>
WinAppDeployCmd list -guid <address>
WinAppDeployCmd deployfiles -file <path> -remotedeploydir <remoterelativepath> -ip <address>
WinAppDeployCmd registerfiles -remotedeploydir <remoterelativepath> -ip <address>
WinAppDeployCmd addcreds -credserver <server> -credusername <username> -credpassword <password> -ip <address>
WinAppDeployCmd getcreds -credserver <server> -ip <address>
WinAppDeployCmd deletecreds -credserver <server> -ip <address>
```

<span data-ttu-id="16c9b-123">Sie können eine App auf dem Zielgerät installieren oder deinstallieren oder eine bereits installierte App aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="16c9b-123">You can install or uninstall an app on the target device, or you can update an app that's already installed.</span></span> <span data-ttu-id="16c9b-124">Um die Daten oder Einstellungen beizubehalten, die von einer bereits installierten App gespeichert wurden, verwenden Sie die **update**-Optionen anstelle der **install**-Optionen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-124">To keep data or settings saved by an app that's already installed, use the **update** options instead of the **install** options.</span></span>

<span data-ttu-id="16c9b-125">Die folgende Tabelle enthält die Befehle für **WinAppDeployCmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="16c9b-125">The following table describes the commands for **WinAppDeployCmd.exe**.</span></span>


| **<span data-ttu-id="16c9b-126">Befehl</span><span class="sxs-lookup"><span data-stu-id="16c9b-126">Command</span></span>**  | **<span data-ttu-id="16c9b-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="16c9b-127">Description</span></span>**                                                     |
|--------------|---------------------------------------------------------------------|
| <span data-ttu-id="16c9b-128">Geräte</span><span class="sxs-lookup"><span data-stu-id="16c9b-128">devices</span></span>      | <span data-ttu-id="16c9b-129">Zeigt die Liste verfügbarer Netzwerkgeräte an.</span><span class="sxs-lookup"><span data-stu-id="16c9b-129">Show the list of available network devices.</span></span>                         |
| <span data-ttu-id="16c9b-130">install</span><span class="sxs-lookup"><span data-stu-id="16c9b-130">install</span></span>      | <span data-ttu-id="16c9b-131">Installiert ein UWP-App-Paket auf dem Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="16c9b-131">Install a UWP app package to the target device.</span></span>                     |
| <span data-ttu-id="16c9b-132">update</span><span class="sxs-lookup"><span data-stu-id="16c9b-132">update</span></span>       | <span data-ttu-id="16c9b-133">Aktualisiert eine UWP-App, die bereits auf dem Zielgerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="16c9b-133">Update a UWP app that is already installed on the target device.</span></span>    |
| <span data-ttu-id="16c9b-134">list</span><span class="sxs-lookup"><span data-stu-id="16c9b-134">list</span></span>         | <span data-ttu-id="16c9b-135">Zeigt die Liste der auf dem angegebenen Zielgerät installierten UWP-Apps an.</span><span class="sxs-lookup"><span data-stu-id="16c9b-135">Show the list of UWP apps installed on the specified target device.</span></span> |
| <span data-ttu-id="16c9b-136">uninstall</span><span class="sxs-lookup"><span data-stu-id="16c9b-136">uninstall</span></span>    | <span data-ttu-id="16c9b-137">Deinstalliert das angegebene App-Paket vom Zielgerät.</span><span class="sxs-lookup"><span data-stu-id="16c9b-137">Uninstall the specified app package from the target device.</span></span>         |
| <span data-ttu-id="16c9b-138">deployfiles</span><span class="sxs-lookup"><span data-stu-id="16c9b-138">deployfiles</span></span>  | <span data-ttu-id="16c9b-139">Kopiert die App mit loser Datei am Zielpfad zum relativen Remotepfad auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="16c9b-139">Copy over loose file app at the target path to the remote relative path on the device.</span></span>|
| <span data-ttu-id="16c9b-140">registerfiles</span><span class="sxs-lookup"><span data-stu-id="16c9b-140">registerfiles</span></span>| <span data-ttu-id="16c9b-141">Registriert die App mit loser Datei am Remotebereitstellungsverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="16c9b-141">Register the loose file app at the remote deploy directory.</span></span>         |
| <span data-ttu-id="16c9b-142">addcreds</span><span class="sxs-lookup"><span data-stu-id="16c9b-142">addcreds</span></span>     | <span data-ttu-id="16c9b-143">Fügt einer Xbox Anmeldeinformationen hinzu, um auf einen Netzwerkspeicherort für die App-Registrierung zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-143">Add credentials to an Xbox to allow it to access a network location for app registration.</span></span>|
| <span data-ttu-id="16c9b-144">getcreds</span><span class="sxs-lookup"><span data-stu-id="16c9b-144">getcreds</span></span>     | <span data-ttu-id="16c9b-145">Ruft Netzwerkanmeldeinformationen ab, die das Ziel beim Ausführen einer Anwendung von einer Netzwerkfreigabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="16c9b-145">Get network credentials for the target uses when running an application from a network share.</span></span>|
| <span data-ttu-id="16c9b-146">deletecreds</span><span class="sxs-lookup"><span data-stu-id="16c9b-146">deletecreds</span></span>  | <span data-ttu-id="16c9b-147">Löscht Netzwerkanmeldeinformationen, die das Ziel beim Ausführen einer Anwendung von einer Netzwerkfreigabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="16c9b-147">Delete network credentials the target uses when running an application from a network share.</span></span>|


<span data-ttu-id="16c9b-148">Die folgende Tabelle enthält die Optionen für **WinAppDeployCmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="16c9b-148">The following table describes the options for **WinAppDeployCmd.exe**.</span></span>


| **<span data-ttu-id="16c9b-149">Befehl</span><span class="sxs-lookup"><span data-stu-id="16c9b-149">Command</span></span>**  | **<span data-ttu-id="16c9b-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="16c9b-150">Description</span></span>**  |
|--------------|------------------|
| <span data-ttu-id="16c9b-151">-h (-help)</span><span class="sxs-lookup"><span data-stu-id="16c9b-151">-h (-help)</span></span>       | <span data-ttu-id="16c9b-152">Zeigt die Befehle, Optionen und Argumente an.</span><span class="sxs-lookup"><span data-stu-id="16c9b-152">Show the commands, options and arguments.</span></span> |
| <span data-ttu-id="16c9b-153">-ip</span><span class="sxs-lookup"><span data-stu-id="16c9b-153">-ip</span></span>              | <span data-ttu-id="16c9b-154">Die IP-Adresse des Zielgeräts.</span><span class="sxs-lookup"><span data-stu-id="16c9b-154">IP address of the target device.</span></span> |
| <span data-ttu-id="16c9b-155">-g (-guid)</span><span class="sxs-lookup"><span data-stu-id="16c9b-155">-g (-guid)</span></span>       | <span data-ttu-id="16c9b-156">Der eindeutige Bezeichner des Zielgeräts.</span><span class="sxs-lookup"><span data-stu-id="16c9b-156">Unique identifier of the target device.</span></span>|
| <span data-ttu-id="16c9b-157">-d (-dependency)</span><span class="sxs-lookup"><span data-stu-id="16c9b-157">-d (-dependency)</span></span> | <span data-ttu-id="16c9b-158">(Optional) Gibt den Abhängigkeitspfad für jede Paketabhängigkeit an.</span><span class="sxs-lookup"><span data-stu-id="16c9b-158">(Optional) Specifies the dependency path for each of the package dependencies.</span></span> <span data-ttu-id="16c9b-159">Wenn kein Pfad angegeben ist, sucht das Tool Abhängigkeiten im Stammverzeichnis des App-Pakets und in den SDK-Verzeichnissen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-159">If no path is specified, the tool searches for dependencies in the root directory for the app package and the SDK directories.</span></span>|
| <span data-ttu-id="16c9b-160">-f (-file)</span><span class="sxs-lookup"><span data-stu-id="16c9b-160">-f (-file)</span></span>       | <span data-ttu-id="16c9b-161">Der Dateipfad für das App-Paket, das installiert, aktualisiert oder deinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="16c9b-161">File path for the app package to install, update or uninstall.</span></span>|
| <span data-ttu-id="16c9b-162">-p (-package)</span><span class="sxs-lookup"><span data-stu-id="16c9b-162">-p (-package)</span></span>    | <span data-ttu-id="16c9b-163">Der vollständige Paketname für das zu deinstallierende App-Paket.</span><span class="sxs-lookup"><span data-stu-id="16c9b-163">The full package name for the app package to uninstall.</span></span> <span data-ttu-id="16c9b-164">(Mit dem „list”-Befehl können Sie den vollständigen Namen von Paketen suchen, die bereits auf dem Gerät installiert sind)</span><span class="sxs-lookup"><span data-stu-id="16c9b-164">(You can use the list command to find the full names for packages already installed on the device)</span></span> |
| <span data-ttu-id="16c9b-165">-pin</span><span class="sxs-lookup"><span data-stu-id="16c9b-165">-pin</span></span>             | <span data-ttu-id="16c9b-166">Eine PIN, falls zum Herstellen einer Verbindung mit dem Zielgerät erforderlich.</span><span class="sxs-lookup"><span data-stu-id="16c9b-166">A pin if it is required to establish a connection with the target device.</span></span> <span data-ttu-id="16c9b-167">(Wenn eine Authentifizierung erforderlich ist, werden Sie aufgefordert, den Versuch mit der Option „-pin” zu wiederholen)</span><span class="sxs-lookup"><span data-stu-id="16c9b-167">(You will be prompted to retry with the -pin option if authentication is required)</span></span> |
| <span data-ttu-id="16c9b-168">-credserver</span><span class="sxs-lookup"><span data-stu-id="16c9b-168">-credserver</span></span>      | <span data-ttu-id="16c9b-169">Der Servername der Netzwerkanmeldeinformationen für die Verwendung durch das Ziel.</span><span class="sxs-lookup"><span data-stu-id="16c9b-169">The server name of the network credentials for use by the target.</span></span> |
| <span data-ttu-id="16c9b-170">-credusername</span><span class="sxs-lookup"><span data-stu-id="16c9b-170">-credusername</span></span>    | <span data-ttu-id="16c9b-171">Der Benutzername der Netzwerkanmeldeinformationen für die Verwendung durch das Ziel.</span><span class="sxs-lookup"><span data-stu-id="16c9b-171">The user name of the network credentials for use by the target.</span></span> |
| <span data-ttu-id="16c9b-172">-credpassword</span><span class="sxs-lookup"><span data-stu-id="16c9b-172">-credpassword</span></span>    | <span data-ttu-id="16c9b-173">Das Kennwort der Netzwerkanmeldeinformationen für die Verwendung durch das Ziel.</span><span class="sxs-lookup"><span data-stu-id="16c9b-173">The password of the network credentials for use by the target.</span></span> |
| <span data-ttu-id="16c9b-174">-connecttimeout</span><span class="sxs-lookup"><span data-stu-id="16c9b-174">-connecttimeout</span></span>  | <span data-ttu-id="16c9b-175">Die Zeitüberschreiung in Sekunden, die bei der Herstellung der Verbindung mit dem Gerät verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="16c9b-175">The timeout in seconds used when connecting to the device.</span></span> |
| <span data-ttu-id="16c9b-176">-remotedeploydir</span><span class="sxs-lookup"><span data-stu-id="16c9b-176">-remotedeploydir</span></span> | <span data-ttu-id="16c9b-177">Relativer Verzeichnispfad/Name zum Kopieren von Dateien auf das Remote-Gerät. Dies ist ein bekannter, automatisch bestimmter Remotebereitstellungsordner.</span><span class="sxs-lookup"><span data-stu-id="16c9b-177">Relative directory path/name to copy files over to on the remote device; This will be a well-known, automatically determined remote deployment folder.</span></span> |
| <span data-ttu-id="16c9b-178">-deleteextrafile</span><span class="sxs-lookup"><span data-stu-id="16c9b-178">-deleteextrafile</span></span> | <span data-ttu-id="16c9b-179">Wechselt, um anzugeben, ob vorhandene Dateien im Remoteverzeichnis gelöscht werden sollen, um mit dem Quellverzeichnis übereinzustimmen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-179">Switch to indicate whether existing files in the remote directory should be purged to match the source directory.</span></span> |


<span data-ttu-id="16c9b-180">Die folgende Tabelle enthält die Optionen für **WinAppDeployCmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="16c9b-180">The following table describes the options for **WinAppDeployCmd.exe**.</span></span>

| **<span data-ttu-id="16c9b-181">Argument</span><span class="sxs-lookup"><span data-stu-id="16c9b-181">Argument</span></span>**           | **<span data-ttu-id="16c9b-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="16c9b-182">Description</span></span>**                                                              |
|------------------------|------------------------------------------------------------------------------|
| <span data-ttu-id="16c9b-183">&lt;x&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-183">&lt;x&gt;</span></span>              | <span data-ttu-id="16c9b-184">Zeitüberschreitung in Sekunden.</span><span class="sxs-lookup"><span data-stu-id="16c9b-184">Timeout in seconds.</span></span> <span data-ttu-id="16c9b-185">(Der Standardwert ist 10.)</span><span class="sxs-lookup"><span data-stu-id="16c9b-185">(Default is 10)</span></span>                                          |
| <span data-ttu-id="16c9b-186">&lt;address&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-186">&lt;address&gt;</span></span>        | <span data-ttu-id="16c9b-187">Die IP-Adresse oder der eindeutige Bezeichner des Zielgeräts.</span><span class="sxs-lookup"><span data-stu-id="16c9b-187">IP address or unique identifier of the target device.</span></span>                        |
| <span data-ttu-id="16c9b-188">&lt;a&gt;&lt;b&gt; ...</span><span class="sxs-lookup"><span data-stu-id="16c9b-188">&lt;a&gt;&lt;b&gt; ...</span></span> | <span data-ttu-id="16c9b-189">Der Abhängigkeitspfad für die einzelnen App-Paket-Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="16c9b-189">Dependency path for each of the app package dependencies.</span></span>                    |
| <span data-ttu-id="16c9b-190">&lt;p&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-190">&lt;p&gt;</span></span>              | <span data-ttu-id="16c9b-191">Eine alphanumerische PIN, die in den Geräteeinstellungen angezeigt und zum Herstellen einer Verbindung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="16c9b-191">An alpha-numeric pin shown in the device settings to establish a connection.</span></span> |
| <span data-ttu-id="16c9b-192">&lt;path&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-192">&lt;path&gt;</span></span>           | <span data-ttu-id="16c9b-193">Dateisystempfad.</span><span class="sxs-lookup"><span data-stu-id="16c9b-193">File system path.</span></span>                                                            |
| <span data-ttu-id="16c9b-194">&lt;name&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-194">&lt;name&gt;</span></span>           | <span data-ttu-id="16c9b-195">Vollständiger Paketname für das zu deinstallierende App-Paket.</span><span class="sxs-lookup"><span data-stu-id="16c9b-195">Full package name for the app package to uninstall.</span></span>                          |
| <span data-ttu-id="16c9b-196">&lt;server&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-196">&lt;server&gt;</span></span>         | <span data-ttu-id="16c9b-197">Server im Dateinetzwerk.</span><span class="sxs-lookup"><span data-stu-id="16c9b-197">Server on the file network.</span></span>                                                  |
| <span data-ttu-id="16c9b-198">&lt;username&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-198">&lt;username&gt;</span></span>       | <span data-ttu-id="16c9b-199">Benutzer für die Anmeldeinformationen mit Zugriff auf den Server im Dateinetzwerk.</span><span class="sxs-lookup"><span data-stu-id="16c9b-199">User for the credentials with access to the server on the file network.</span></span>      |
| <span data-ttu-id="16c9b-200">&lt;password&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-200">&lt;password&gt;</span></span>       | <span data-ttu-id="16c9b-201">Kennwort für die Anmeldeinformationen mit Zugriff auf den Server im Dateinetzwerk.</span><span class="sxs-lookup"><span data-stu-id="16c9b-201">Password for the credentials with access to the server on the files network.</span></span> |
| <span data-ttu-id="16c9b-202">&lt;remotedeploydir&gt;</span><span class="sxs-lookup"><span data-stu-id="16c9b-202">&lt;remotedeploydir&gt;</span></span>| <span data-ttu-id="16c9b-203">Verzeichnis auf dem Gerät relativ zum Bereitstellungsspeicherort.</span><span class="sxs-lookup"><span data-stu-id="16c9b-203">Directory on device relative to the deployment location</span></span>                      |

 
## <a name="winappdeploycmdexe-examples"></a><span data-ttu-id="16c9b-204">Beispiele für „WinAppDeployCmd.exe“</span><span class="sxs-lookup"><span data-stu-id="16c9b-204">WinAppDeployCmd.exe examples</span></span>

<span data-ttu-id="16c9b-205">Im Folgenden finden Sie einige Beispiele dazu, wie Sie mithilfe der Syntax für **WinAppDeployCmd.exe** eine Bereitstellung über die Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-205">Here are some examples of how to deploy from the command-line using the sytax for **WinAppDeployCmd.exe**.</span></span>

<span data-ttu-id="16c9b-206">Zeigt die für die Bereitstellung verfügbaren Geräte an.</span><span class="sxs-lookup"><span data-stu-id="16c9b-206">Shows the devices that are available for deployment.</span></span> <span data-ttu-id="16c9b-207">Der Befehl verursacht in drei Sekunden ein Timeout.</span><span class="sxs-lookup"><span data-stu-id="16c9b-207">The command times out in 3 seconds.</span></span>

``` syntax
WinAppDeployCmd devices 3
```

<span data-ttu-id="16c9b-208">Installiert die app aus dem Paket "MyApp.AppX", die im Downloadverzeichnis Ihres PCs auf einem Windows 10-Gerät mit der IP-Adresse 192.168.0.1 mit einer PIN A1B2C3, eine Verbindung mit dem Gerät herzustellen.</span><span class="sxs-lookup"><span data-stu-id="16c9b-208">Installs the app from MyApp.appx package that is in your PC's Downloads directory to a Windows10 device with an IP address of 192.168.0.1 with a PIN of A1B2C3 to establish a connection with the device</span></span>

``` syntax
WinAppDeployCmd install -file "Downloads\MyApp.appx" -ip 192.168.0.1 -pin A1B2C3
```

<span data-ttu-id="16c9b-209">Deinstalliert das angegebene Paket (unter Verwendung des vollständigen Namens) von einem Windows10-Gerät mit der IP-Adresse 192.168.0.1.</span><span class="sxs-lookup"><span data-stu-id="16c9b-209">Uninstalls the specified package (based on its full name) from a Windows 10 device with an IP address of 192.168.0.1.</span></span> <span data-ttu-id="16c9b-210">Mit dem list-Befehl können Sie die vollständigen Namen aller Pakete anzeigen, die auf einem Gerät installiert sind.</span><span class="sxs-lookup"><span data-stu-id="16c9b-210">You can use the list command to see the full names of any packages that are installed on a device.</span></span>

``` syntax
WinAppDeployCmd uninstall -package Company.MyApp_1.0.0.1_x64__qwertyuiop -ip 192.168.0.1
```

<span data-ttu-id="16c9b-211">Aktualisiert die app, die bereits auf dem Gerät Windows 10 mit der IP-Adresse 192.168.0.1 mit dem angegebenen app-Paket installiert ist.</span><span class="sxs-lookup"><span data-stu-id="16c9b-211">Updates the app that is already installed on the Windows10 device with an IP address of 192.168.0.1 using the specified app package.</span></span>

``` syntax
WinAppDeployCmd update -file "Downloads\MyApp.appx" -ip 192.168.0.1
```

<span data-ttu-id="16c9b-212">Stellt die Dateien einer App auf einem PC oder auf Xbox mit der IP-Adresse 192.168.0.1 im gleichen Ordner wie das AppxManifest im Verzeichnis app1_F5 am Bereitstellungspfad des Geräts bereit.</span><span class="sxs-lookup"><span data-stu-id="16c9b-212">Deploys the files of an app to a PC or Xbox with an IP address of 192.168.0.1 in the same folder as the AppxManifest to the app1_F5 directory under the deployment path of the device.</span></span>

``` syntax
WinAppDeployCmd deployfiles -file "C:\apps\App1\AppxManifest.xml" -remotedeploydir app1_F5 -ip 192.168.0.1
```

<span data-ttu-id="16c9b-213">Registriert die App im Verzeichnis app1_F5 am Bereitstellungspfad des PCs oder der Xbox mit 192.168.0.1.</span><span class="sxs-lookup"><span data-stu-id="16c9b-213">Registers the app at the app1_F5 directory under the deployment path of the PC or Xbox at 192.168.0.1.</span></span>

``` syntax
WinAppDeployCmd registerfiles -file app1_F5 -ip 192.168.0.1
```

## <a name="using-winappdeploycmd-to-set-up-run-from-pc-deployment-on-xbox-one"></a><span data-ttu-id="16c9b-214">Verwenden von WinAppDeployCmd für die Einrichtung von über einen PC ausgeführten Bereitstellungen auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="16c9b-214">Using WinAppDeployCmd to set up Run from PC deployment on Xbox One</span></span>

<span data-ttu-id="16c9b-215">Das Ausführen über einen PC ermöglicht Ihnen die Bereitstellung einer UWP-Anwendung auf einer Xbox One, ohne die Binärdateien zu kopieren. Die Binärdateien werden stattdessen in einer Netzwerkfreigabe im selben Netzwerk wie die Xbox gehostet.</span><span class="sxs-lookup"><span data-stu-id="16c9b-215">Run from PC allows you to deploy a UWP application to an Xbox One without copying the binaries over, instead the binaries are hosted on a network share on the same network as the Xbox.</span></span>  <span data-ttu-id="16c9b-216">Dazu benötigen Sie eine für Entwickler entsperrte Xbox One und eine UWP-Anwendung mit loser Datei in einem Netzlaufwerk, das auf die Xbox zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="16c9b-216">In order to do this, you need a developer unlocked Xbox One, and a loose file UWP application on a network drive that the Xbox can access.</span></span>

<span data-ttu-id="16c9b-217">Führen Sie Folgendes aus, um die App zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="16c9b-217">Run this to register the app:</span></span>
``` syntax
WinAppDeployCmd registerfiles -ip <Xbox One IP> -remotedeploydir <location of app> -username <user for network> -password <password for user>

ex. WinAppDeployCmd register files -ip 192.168.0.1 -remotedeploydir \\driveA\myAppLocation -username admin -password A1B2C3
```
