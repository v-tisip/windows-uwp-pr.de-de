---
author: normesta
Description: "Führen Sie Desktop App Converter zum verpacken einer Windows-Desktopanwendung (z.B. Win32, WPF und Windows Forms) aus."
Search.Product: eADQiWindows 10XVcnh
title: "Verpacken einer App mit dem Desktop App Converter (Desktop-Brücke)"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 74c84eb6-4714-4e12-a658-09cb92b576e3
ms.openlocfilehash: 6aa469d0080412f48de511315684d365d4e90c99
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="package-an-app-using-the-desktop-app-converter-desktop-bridge"></a><span data-ttu-id="3df44-104">Verpacken einer App mit dem Desktop App Converter (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="3df44-104">Package an app using the Desktop App Converter (Desktop Bridge)</span></span>

[<span data-ttu-id="3df44-105">Laden Sie Desktop App Converter herunter</span><span class="sxs-lookup"><span data-stu-id="3df44-105">Get the Desktop App Converter</span></span>](https://aka.ms/converter)

<span data-ttu-id="3df44-106">Sie könnten den Desktop App Converter (DAC) verwenden, um Ihre Desktop-Apps auf die Universelle Windows-Plattform (UWP) umzustellen.</span><span class="sxs-lookup"><span data-stu-id="3df44-106">You can use the Desktop App Converter (DAC) to bring your desktop apps to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="3df44-107">Dazu zählen Win32-Apps und Apps, die Sie mithilfe von .NET 4.6.1 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="3df44-107">This includes Win32 apps and apps that you've created by using .NET 4.6.1.</span></span>

<div style="float: left; padding: 10px">
    ![DAC-Symbol](images/desktop-to-uwp/dac.png)
</div>

<span data-ttu-id="3df44-109">Obwohl der Begriff „Konverter“ im Namen dieses Tool auftaucht, wird nicht tatsächlich konvertiert.</span><span class="sxs-lookup"><span data-stu-id="3df44-109">While the term "Converter" appears in the name of this tool, it doesn't actually convert your app.</span></span> <span data-ttu-id="3df44-110">Ihre App bleibt unverändert.</span><span class="sxs-lookup"><span data-stu-id="3df44-110">Your app remains unchanged.</span></span> <span data-ttu-id="3df44-111">Das Tool generiert jedoch ein Windows-App-Paket mit eine Paketidentität. Es bietet die Möglichkeit, viele WinRT-APIs aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="3df44-111">However, this tool generates a Windows app package with a package identity and the ability to call a vast range of WinRT APIs.</span></span>

<span data-ttu-id="3df44-112">Sie können dieses Paket mithilfe des Add-AppxPackage-PowerShell-Cmdlets auf Ihrem Entwicklungscomputer installieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-112">You can install that package by using the Add-AppxPackage PowerShell cmdlet on your development machine.</span></span>

<span data-ttu-id="3df44-113">Der Konverter führt den Desktop-Installer in einer isolierten Windows-Umgebung mit einem sauberen Basisimage als Teil des Konverterdownloads aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-113">The converter runs the desktop installer in an isolated Windows environment by using a clean base image provided as part of the converter download.</span></span> <span data-ttu-id="3df44-114">Es werden alle Registrierungs- und Dateisystem-E/A des Desktop-Installers erfasst und als Teil der Ausgabe gepackt.</span><span class="sxs-lookup"><span data-stu-id="3df44-114">It captures any registry and file system I/O made by the desktop installer and packages it as part of the output.</span></span>

> [!NOTE]
> <span data-ttu-id="3df44-115">Sehen Sie sich <a href="https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373?l=oZG0B1WhD_8406218965/">diese Reihe</a> von kurzen Videos an, die von der Microsoft Virtual Academy veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="3df44-115">Checkout <a href="https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373?l=oZG0B1WhD_8406218965/">this series</a> of short videos published by the Microsoft Virtual Academy.</span></span> <span data-ttu-id="3df44-116">Diese Videos erläutern einige gängige Verwendungsmethoden des Desktop App Converters.</span><span class="sxs-lookup"><span data-stu-id="3df44-116">These videos walk you through some common ways to use the Desktop App Converter.</span></span>

## <a name="the-dac-does-more-than-just-generate-a-package-for-you"></a><span data-ttu-id="3df44-117">Das DAC macht mehr als nur ein Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-117">The DAC does more than just generate a package for you</span></span>

<span data-ttu-id="3df44-118">Hier sind einige zusätzliche Aufgaben, die er für Sie erledigen kann.</span><span class="sxs-lookup"><span data-stu-id="3df44-118">Here's a few extra things it can do for you.</span></span>

**<span data-ttu-id="3df44-119">Windows10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="3df44-119">Windows 10 Creators Update</span></span>**

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

<span data-ttu-id="3df44-121">Automatisches Registrieren Ihrer Preview-Handler, Miniaturansichthandler, Eigenschaftenhandler, Firewall-Regeln, URL-Kennzeichen.</span><span class="sxs-lookup"><span data-stu-id="3df44-121">Automatically register your preview handlers, thumbnail handlers, property handlers, firewall rules, URL flags.</span></span>

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

<span data-ttu-id="3df44-123">Automatisches Registrieren Ihrer Dateizuordnungen, mit denen Benutzer Dateien mithilfe der **Art**-Spalte im Datei-Explorer gruppieren können.</span><span class="sxs-lookup"><span data-stu-id="3df44-123">Automatically register file type mappings that enable users to group files by using the **Kind** column in File Explorer.</span></span>

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

<span data-ttu-id="3df44-125">Registrieren Ihrer öffentlichen COM-Server.</span><span class="sxs-lookup"><span data-stu-id="3df44-125">Register your public COM servers.</span></span>

**<span data-ttu-id="3df44-126">Windows 10 Anniversary Update oder höher</span><span class="sxs-lookup"><span data-stu-id="3df44-126">Windows 10 Anniversary Update or later</span></span>**

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

<span data-ttu-id="3df44-128">Automatisches Signieren Ihres Pakets, damit Sie Ihre App testen können.</span><span class="sxs-lookup"><span data-stu-id="3df44-128">Automatically sign your package so that you can test your app.</span></span>

<div style="float: left; ">
    ![Überprüfen](images/desktop-to-uwp/check.png)
</div>

<span data-ttu-id="3df44-130">Überprüfen Ihrer App für Desktop-Brücke- und Windows Store-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="3df44-130">Validate your app against Desktop Bridge and Windows Store requirements.</span></span>

<span data-ttu-id="3df44-131">Eine vollständige Liste der Optionen finden Sie unter dem Abschnitt [Parameter](#command-reference) dieses Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="3df44-131">To find a complete list of options, see the [Parameters](#command-reference) section of this guide.</span></span>

<span data-ttu-id="3df44-132">Wenn Sie für die Erstellung des Pakets bereit sind, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="3df44-132">If you're ready to create your package, let's start.</span></span>

## <a name="first-consider-how-youll-distribute-your-app"></a><span data-ttu-id="3df44-133">Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.</span><span class="sxs-lookup"><span data-stu-id="3df44-133">First, consider how you'll distribute your app</span></span>
<span data-ttu-id="3df44-134">Wenn Sie Ihre App im [Windows Store-](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="3df44-134">If you plan to publish your app to the [Windows Store](https://www.microsoft.com/store/apps), start by filling out [this form](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge).</span></span> <span data-ttu-id="3df44-135">Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess.</span><span class="sxs-lookup"><span data-stu-id="3df44-135">Microsoft will contact you to start the onboarding process.</span></span> <span data-ttu-id="3df44-136">Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="3df44-136">As part of this process, you'll reserve a name in the store, and obtain information that you'll need to package your app.</span></span>

## <a name="make-sure-that-your-system-can-run-the-converter"></a><span data-ttu-id="3df44-137">Stellen Sie sicher, dass das System den Konverter ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="3df44-137">Make sure that your system can run the converter</span></span>

<span data-ttu-id="3df44-138">Stellen Sie sicher, dass das System die folgenden Anforderungen erfüllt:</span><span class="sxs-lookup"><span data-stu-id="3df44-138">Make sure that your system meets the following requirements:</span></span>

* <span data-ttu-id="3df44-139">Windows 10 Anniversary Update (10.0.14393.0 und höher) Pro oder Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="3df44-139">Windows 10 Anniversary Update (10.0.14393.0 and later) Pro or Enterprise edition.</span></span>
* <span data-ttu-id="3df44-140">64-Bit (x64)-Prozessor</span><span class="sxs-lookup"><span data-stu-id="3df44-140">64 bit (x64) processor</span></span>
* <span data-ttu-id="3df44-141">Hardwareunterstützte Virtualisierung</span><span class="sxs-lookup"><span data-stu-id="3df44-141">Hardware-assisted virtualization</span></span>
* <span data-ttu-id="3df44-142">Adressübersetzung der zweiten Ebene (Second Level Address Translation, SLAT)</span><span class="sxs-lookup"><span data-stu-id="3df44-142">Second Level Address Translation (SLAT)</span></span>
* <span data-ttu-id="3df44-143">[Windows Software Development Kit (SDK) für Windows10](https://go.microsoft.com/fwlink/?linkid=821375).</span><span class="sxs-lookup"><span data-stu-id="3df44-143">[Windows Software Development Kit (SDK) for Windows 10](https://go.microsoft.com/fwlink/?linkid=821375).</span></span>


## <a name="start-the-desktop-app-converter"></a><span data-ttu-id="3df44-144">Starten Sie den Desktop App Converter.</span><span class="sxs-lookup"><span data-stu-id="3df44-144">Start the Desktop App Converter</span></span>

1. <span data-ttu-id="3df44-145">Laden und Installieren Sie den [Desktop App Converter](https://aka.ms/converter).</span><span class="sxs-lookup"><span data-stu-id="3df44-145">Download and install the [Desktop App Converter](https://aka.ms/converter).</span></span>

2. <span data-ttu-id="3df44-146">Führen Sie den Desktop App Converter als Administrator aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-146">Run the Desktop App Converter as an administrator.</span></span>

    ![Führen Sie DAC als Administrator aus.](images/desktop-to-uwp/run-converter.png)

   <span data-ttu-id="3df44-148">Ein Konsolenfenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3df44-148">A console window appears.</span></span> <span data-ttu-id="3df44-149">Sie werden dieses Konsolenfenster verwenden, um Befehle auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3df44-149">You'll use that console window to run commands.</span></span>

## <a name="set-a-few-things-up-apps-with-installers-only"></a><span data-ttu-id="3df44-150">Richten Sie ein paar Dinge ein (nur Apps mit Installer)</span><span class="sxs-lookup"><span data-stu-id="3df44-150">Set a few things up (apps with installers only)</span></span>

<span data-ttu-id="3df44-151">Sie können diesen Abschnittüberspringen, falls Ihre App über kein Installationsprogramm verfügt.</span><span class="sxs-lookup"><span data-stu-id="3df44-151">You can skip ahead to the next section if your app doesn't have an installer.</span></span>

1. <span data-ttu-id="3df44-152">Identifizieren Sie die Version Ihres Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="3df44-152">Identify the version number of your operating system.</span></span>

   <span data-ttu-id="3df44-153">Öffnen Sie dazu die **Systeminformationen-App** auf Ihrem Computer, und suchen Sie dann die Versionsnummer des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="3df44-153">You can do that by opening the **System Information app** on your computer and then finding the version number of your operating system.</span></span>

    ![Betriebssystemversion in der App Systeminformationen](images/desktop-to-uwp/os-version.png)

2. <span data-ttu-id="3df44-155">Laden Sie das entsprechende [Desktop-App-Konverter-Basisimage](https://aka.ms/converterimages).</span><span class="sxs-lookup"><span data-stu-id="3df44-155">Download the appropriate [Desktop app Converter base image](https://aka.ms/converterimages).</span></span>

   <span data-ttu-id="3df44-156">Stellen Sie sicher, dass die Versionsnummer, die im Namen der Datei angezeigt wird, der Versionsnummer des Windows-Builds entspricht.</span><span class="sxs-lookup"><span data-stu-id="3df44-156">Make sure that the version number that appears in the name of the file matches the version number of your Windows build.</span></span>

   ![Entsprechende Basisimage-Version](images/desktop-to-uwp/base-image-version.png)

   <span data-ttu-id="3df44-158">Platzieren Sie die heruntergeladene Datei an einem beliebigen Speicherort auf Ihrem Computer, wo Sie sie später wieder finden werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-158">Place the downloaded file anywhere on your computer where you'll be able to find it later.</span></span>

3. <span data-ttu-id="3df44-159">Führen Sie im Konsolenfenster, das beim Starten des Desktop App Converters angezeigt wird, folgenden Befehl aus: ```Set-ExecutionPolicy bypass```.</span><span class="sxs-lookup"><span data-stu-id="3df44-159">In the console window that appeared when you started the Desktop App Converter, run this command: ```Set-ExecutionPolicy bypass```.</span></span>
4.  <span data-ttu-id="3df44-160">Richten Sie den Konverter durch Ausführen dieses Befehls ein: ```DesktopAppConverter.exe -Setup -BaseImage .\BaseImage-1XXXX.wim -Verbose```.</span><span class="sxs-lookup"><span data-stu-id="3df44-160">Set up the converter by running  this command: ```DesktopAppConverter.exe -Setup -BaseImage .\BaseImage-1XXXX.wim -Verbose```.</span></span>
5.  <span data-ttu-id="3df44-161">Starten Sie den Computer neu, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-161">Restart your computer if you're prompted to do so.</span></span>

    <span data-ttu-id="3df44-162">Statusbenachrichtigungen werden beim Erweitern des Basisimage durch den Konverter im Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3df44-162">Status messages appear in the console window as the converter expands the base image.</span></span> <span data-ttu-id="3df44-163">Wenn Ihnen keine Statusbenachrichtigungen angezeigt werden, drücken Sie eine beliebige Taste.</span><span class="sxs-lookup"><span data-stu-id="3df44-163">If you don't see any status messages, press any key.</span></span> <span data-ttu-id="3df44-164">Dadurch kann der Inhalt des Konsolenfensters aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-164">This can cause the contents of the console window to refresh.</span></span>

    ![Statusbenachrichtigungen in der Konsole](images/desktop-to-uwp/bas-image-setup.png)

    <span data-ttu-id="3df44-166">Wenn das Basisimage vollständig erweitert wurde, fahren Sie mit dem nächsten Abschnitt fort.</span><span class="sxs-lookup"><span data-stu-id="3df44-166">When the base image is fully expanded, move to the next section.</span></span>

## <a name="package-an-app"></a><span data-ttu-id="3df44-167">Verpacken einer App</span><span class="sxs-lookup"><span data-stu-id="3df44-167">Package an app</span></span>

<span data-ttu-id="3df44-168">Um Ihre App zu verpacken, führen Sie den ``DesktopAppConverter.exe``-Befehl im Konsolenfenster aus, das beim Starten des Desktop App Converters geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-168">To Package your app, run the ``DesktopAppConverter.exe`` command in the console window that opened when you started the Desktop App Converter.</span></span>  

<span data-ttu-id="3df44-169">Sie geben den Paketnamen, Herausgeber und Versionsnummer der App anhand der Parameter an.</span><span class="sxs-lookup"><span data-stu-id="3df44-169">You'll specify the package name, publisher and version number of the app by using parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="3df44-170">Wenn Sie den Namen Ihrer App im Windows Store reserviert haben, können Sie die Namen des Pakets und des Herausgebers mit dem Windows Dev Center-Dashboard abrufen.</span><span class="sxs-lookup"><span data-stu-id="3df44-170">If you've reserved your app name in the Windows store, you can obtain the package and publisher names by using the Windows Dev Center dashboard.</span></span> <span data-ttu-id="3df44-171">Wenn Sie Ihre App auf andere Systeme querladen möchten, können Sie für diese Ihre eigenen Namen bereitstellen, sofern der von Ihnen gewählte Name des Herausgebers mit dem Namen des Zertifikats übereinstimmt, das Sie zum Signieren Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="3df44-171">If you plan to sideload your app onto other systems, you can provide your own names for these as long as the publisher name that you choose matches the name on the certificate you use to sign your app.</span></span>

### <a name="a-quick-look-at-command-parameters"></a><span data-ttu-id="3df44-172">Ein kurzer Überblick der Befehlsparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-172">A quick look at command parameters</span></span>

<span data-ttu-id="3df44-173">Hier sind die benötigten Parameter.</span><span class="sxs-lookup"><span data-stu-id="3df44-173">Here are the required parameters.</span></span>

```CMD
DesktopAppConverter.exe
-Installer <String>
-Destination <String>
-PackageName <String>
-Publisher <String>
-Version <Version>
```
<span data-ttu-id="3df44-174">Sie erhalten Informationen über jeden Parameter [hier](#command-reference).</span><span class="sxs-lookup"><span data-stu-id="3df44-174">You can read about each one [here](#command-reference).</span></span>

### <a name="examples"></a><span data-ttu-id="3df44-175">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3df44-175">Examples</span></span>

<span data-ttu-id="3df44-176">Nachfolgend finden Sie einige gängige Methoden zum Verpacken Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="3df44-176">Here's a few common ways to package your app.</span></span>

* [<span data-ttu-id="3df44-177">Verpacken einer App mit einer (.msi) Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="3df44-177">Package an app that has an installer (.msi) file</span></span>](#installer-conversion)
* [<span data-ttu-id="3df44-178">Verpacken einer App, die eine ausführbare Setup-Datei hat</span><span class="sxs-lookup"><span data-stu-id="3df44-178">Package an app that has a setup executable file</span></span>](#setup-conversion)
* [<span data-ttu-id="3df44-179">Verpacken einer App, die kein Installationsprogramm besitzt</span><span class="sxs-lookup"><span data-stu-id="3df44-179">Package an app that doesn't have an installer</span></span>](#no-installer-conversion)
* [<span data-ttu-id="3df44-180">Verpacken einer App, Signieren der App, und Vorbereiten der App für die Übermittlung an den Store.</span><span class="sxs-lookup"><span data-stu-id="3df44-180">Package an app, sign the app, and prepare it for store submission</span></span>](#optional-parameters)

<span id="installer-conversion" />
#### <a name="package-an-app-that-has-an-installer-msi-file"></a><span data-ttu-id="3df44-181">Verpacken einer App mit einer (.msi) Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="3df44-181">Package an app that has an installer (.msi) file</span></span>

<span data-ttu-id="3df44-182">Weisen Sie auf die Installer-Datei mithilfe der ``Installer``-Parameter.</span><span class="sxs-lookup"><span data-stu-id="3df44-182">Point to the installer file by using the ``Installer`` parameter.</span></span>

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.msi -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

> [!NOTE]
> <span data-ttu-id="3df44-183">Stellen Sie sicher, dass sich das Installationsprogramm in einem unabhängigen Ordner befindet und nur mit dem Installer verbundene Dateien im selben Ordner sind.</span><span class="sxs-lookup"><span data-stu-id="3df44-183">Make sure that your installer is located in an independent folder and that only files related to that installer are in the same folder.</span></span> <span data-ttu-id="3df44-184">Der Konverter kopiert den Inhalt dieses Ordners in die isolierte Windows-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="3df44-184">The converter copies all of the contents of that folder to the isolated Windows environment.</span></span>

**<span data-ttu-id="3df44-185">Video</span><span class="sxs-lookup"><span data-stu-id="3df44-185">Video</span></span>**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-an-Application-That-Has-an-MSI-Installer-Kh1UU2WhD_7106218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="setup-conversion" />
#### <span data-ttu-id="3df44-186">Verpacken einer App, die eine ausführbare Setup-Datei hat</span><span class="sxs-lookup"><span data-stu-id="3df44-186">Package an app that has a setup executable file</span></span>

<span data-ttu-id="3df44-187">Weisen Sie auf die ausführbare Setup-Datei mithilfe der ``Installer``-Parameter.</span><span class="sxs-lookup"><span data-stu-id="3df44-187">Point to the setup executable by using the ``Installer`` parameter.</span></span>

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.exe -InstallerArguments "/S" -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

<span data-ttu-id="3df44-188">Die ``InstallerArguments``-Parameter ist optional.</span><span class="sxs-lookup"><span data-stu-id="3df44-188">The ``InstallerArguments`` parameter is an optional parameter.</span></span> <span data-ttu-id="3df44-189">Da der Desktop App Converter jedoch Ihren Installer benötigt, um im unbeaufsichtigten Modus ausgeführt zu werden, müssen Sie ihn verwenden, wenn Ihre App automatische Flags benötigt, um im Hintergrund ausgeführt zu werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-189">However, because the Desktop App Converter needs your installer to run in unattended mode, you might have to use it if your app needs silent flags to run silently.</span></span> <span data-ttu-id="3df44-190">Die ``/S``-Flag ist eine sehr häufig verwendetes automatisches Kennzeichen. Das von Ihnen verwendete Kennzeichen unterscheidet sich jedoch möglicherweise je nach welcher Installer-Technologie Sie beim Erstellen der Setup-Datei verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="3df44-190">The ``/S`` flag is a very common silent flag, but the flag that you use might be different depending on which installer technology you used to create the setup file.</span></span>

**<span data-ttu-id="3df44-191">Video</span><span class="sxs-lookup"><span data-stu-id="3df44-191">Video</span></span>**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-an-Application-That-Has-a-Setup-exe-Installer-amWit2WhD_5306218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="no-installer-conversion" />
#### <span data-ttu-id="3df44-192">Verpacken einer App, die kein Installationsprogramm besitzt</span><span class="sxs-lookup"><span data-stu-id="3df44-192">Package an app that doesn't have an installer</span></span>

<span data-ttu-id="3df44-193">Verwenden Sie in diesem Beispiel den ``Installer``-Parameter, um auf den Stammordner Ihrer App-Dateien zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="3df44-193">In this example, use the ``Installer`` parameter to point to the root folder of your app files.</span></span>

<span data-ttu-id="3df44-194">Verwenden Sie den `AppExecutable`-Parameter, um auf die ausführbare Datei Ihrer Apps zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="3df44-194">Use the `AppExecutable` parameter to point to your apps executable file.</span></span>

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyApp\ -AppExecutable MyApp.exe -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1
```

**<span data-ttu-id="3df44-195">Video</span><span class="sxs-lookup"><span data-stu-id="3df44-195">Video</span></span>**

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Convert-a-No-Installer-Application-agAXF2WhD_3506218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

<span id="optional-parameters" />
#### <span data-ttu-id="3df44-196">Verpacken einer App, Signieren Sie die App und Ausführen von Validierungstests für das Paket</span><span class="sxs-lookup"><span data-stu-id="3df44-196">Package an app, sign the app, and run validation checks on the package</span></span>

<span data-ttu-id="3df44-197">Dieses Beispiel ähnelt dem vorherigen, da es zeigt, wie Sie Ihre App für das lokale Testen signieren und Ihre App hinsichtlich der Desktop-Brücke- und Windows Store-Anforderungen überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="3df44-197">This example is similar to first one except it shows how you can sign your app for local testing, and then validate your app against Desktop Bridge and Windows Store requirements.</span></span>

```cmd
DesktopAppConverter.exe -Installer C:\Installer\MyAppSetup.exe -InstallerArguments "/S" -Destination C:\Output\MyApp -PackageName "MyApp" -Publisher "CN=MyPublisher" -Version 0.0.0.1 -MakeAppx -Sign -Verbose -Verify
```

<span data-ttu-id="3df44-198">Der ``Sign``-Parameter generiert ein Zertifikat, mit dem dann Ihre App signiert wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-198">The ``Sign`` parameter generates a certificate and then signs your app with it.</span></span> <span data-ttu-id="3df44-199">Sie müssen das erstellte Zertifikat installieren, um Ihre App ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="3df44-199">To run your app, you'll have to install that generated certificate.</span></span> <span data-ttu-id="3df44-200">Weitere Informationen hierzu finden Sie unter dem Abschnitt [Ausführung der verpackten App](#run-app) dieses Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="3df44-200">To learn how, see the [Run the packaged app](#run-app) section of this guide.</span></span>

<span data-ttu-id="3df44-201">Sie können Ihre App anhand der ``Verify``-Parameter überprüfen.</span><span class="sxs-lookup"><span data-stu-id="3df44-201">You can validate you app by using the ``Verify`` parameter.</span></span>

### <a name="a-quick-look-at-optional-parameters"></a><span data-ttu-id="3df44-202">Einen kurzen Überblick über optionale Parameter</span><span class="sxs-lookup"><span data-stu-id="3df44-202">A quick look at optional parameters</span></span>

<span data-ttu-id="3df44-203">Die ``Sign``- und ``Verify``-Parameter sind optional.</span><span class="sxs-lookup"><span data-stu-id="3df44-203">The ``Sign`` and ``Verify`` parameters are optional.</span></span> <span data-ttu-id="3df44-204">Es gibt viele weitere optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="3df44-204">There are many more optional parameters.</span></span>  <span data-ttu-id="3df44-205">Hier sind einige der am häufigsten verwendeten optionalen Parameter.</span><span class="sxs-lookup"><span data-stu-id="3df44-205">Here are some of the more commonly used optional parameters.</span></span>

```CMD
[-ExpandedBaseImage <String>]
[-AppExecutable <String>]
[-AppFileTypes <String>]
[-AppId <String>]
[-AppDisplayName <String>]
[-AppDescription <String>]
[-PackageDisplayName <String>]
[-PackagePublisherDisplayName <String>]
[-MakeAppx]
[-LogFile <String>]
[<CommonParameters>]
```
<span data-ttu-id="3df44-206">Sie können mehr über all diese Parameter in den nächsten Abschnitterfahren.</span><span class="sxs-lookup"><span data-stu-id="3df44-206">You can read about all of them in the next section.</span></span>

<span id="command-reference" />
### <a name="parameter-reference"></a><span data-ttu-id="3df44-207">Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="3df44-207">Parameter Reference</span></span>

<span data-ttu-id="3df44-208">Hier ist die vollständige Liste der Parameter (nach Kategorie sortiert), die Sie beim Ausführen des Desktop App Converters verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3df44-208">Here's the complete list of parameters (organized by category) that you can use when you run the Desktop App Converter.</span></span>

* [<span data-ttu-id="3df44-209">Setup</span><span class="sxs-lookup"><span data-stu-id="3df44-209">Setup</span></span>](#setup-params)
* [<span data-ttu-id="3df44-210">Konvertierung</span><span class="sxs-lookup"><span data-stu-id="3df44-210">Conversion</span></span>](#conversion-params)
* [<span data-ttu-id="3df44-211">Paketidentität</span><span class="sxs-lookup"><span data-stu-id="3df44-211">Package identity</span></span>](#identity-params)
* [<span data-ttu-id="3df44-212">Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="3df44-212">Package manifest</span></span>](#manifest-params)
* [<span data-ttu-id="3df44-213">Bereinigen</span><span class="sxs-lookup"><span data-stu-id="3df44-213">Cleanup</span></span>](#cleanup-params)
* [<span data-ttu-id="3df44-214">Architektur</span><span class="sxs-lookup"><span data-stu-id="3df44-214">Architecture</span></span>](#architecture-params)
* [<span data-ttu-id="3df44-215">Verschiedenes</span><span class="sxs-lookup"><span data-stu-id="3df44-215">Miscellaneous</span></span>](#other-params)

<span data-ttu-id="3df44-216">Sie können auch die gesamte Liste anzeigen, indem Sie den ``Get-Help``-Befehl in der Konsolenfenster-App ausführen.</span><span class="sxs-lookup"><span data-stu-id="3df44-216">You can also view the entire list by running the ``Get-Help`` command in the app console window.</span></span>   

||||
|-------------|-----------|-------------|
|<span id="setup-params" /> <strong><span data-ttu-id="3df44-217">Setupparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-217">Setup parameters</span></span></strong>  ||
|<span data-ttu-id="3df44-218">-Setup [&lt;SwitchParameter&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-218">-Setup [&lt;SwitchParameter&gt;]</span></span> |<span data-ttu-id="3df44-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-219">Required</span></span> |<span data-ttu-id="3df44-220">Führt DesktopAppConverter im Setupmodus aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-220">Runs DesktopAppConverter in setup mode.</span></span> <span data-ttu-id="3df44-221">Setupmodus unterstützt die Erweiterung eines bereitgestellten Basisimages.</span><span class="sxs-lookup"><span data-stu-id="3df44-221">Setup mode supports expanding a provided base image.</span></span>|
|<span data-ttu-id="3df44-222">-BaseImage &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-222">-BaseImage &lt;String&gt;</span></span> | <span data-ttu-id="3df44-223">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-223">Required</span></span> |<span data-ttu-id="3df44-224">Vollständiger Pfad zu einem nicht erweiterten Basisimage.</span><span class="sxs-lookup"><span data-stu-id="3df44-224">Full path to an unexpanded base image.</span></span> <span data-ttu-id="3df44-225">Dieser Parameter ist erforderlich, wenn -Setup angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="3df44-225">This parameter is required if -Setup is specified.</span></span>|
| <span data-ttu-id="3df44-226">-LogFile &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-226">-LogFile &lt;String&gt;</span></span> |<span data-ttu-id="3df44-227">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-227">Optional</span></span> |<span data-ttu-id="3df44-228">Gibt eine Protokolldatei an.</span><span class="sxs-lookup"><span data-stu-id="3df44-228">Specifies a log file.</span></span> <span data-ttu-id="3df44-229">Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="3df44-229">If omitted, a log file temporary location will be created.</span></span>|
|<span data-ttu-id="3df44-230">-NatSubnetPrefix &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-230">-NatSubnetPrefix &lt;String&gt;</span></span> |<span data-ttu-id="3df44-231">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-231">Optional</span></span> |<span data-ttu-id="3df44-232">Präfixwert, der für die Nat-Instanz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-232">Prefix value to be used for the Nat instance.</span></span> <span data-ttu-id="3df44-233">In der Regel möchten Sie diesen nur ändern, wenn der Hostcomputer an den gleichen Subnetzbereich wie NetNat des Konverters angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="3df44-233">Typically, you would want to change this only if your host machine is attached to the same subnet range as the converter's NetNat.</span></span> <span data-ttu-id="3df44-234">Sie können die aktuelle NetNat-Konfiguration des Konverters mithilfe des **Get-NetNat**-Cmdlets abrufen.</span><span class="sxs-lookup"><span data-stu-id="3df44-234">You can query the current converter NetNat config by using the **Get-NetNat** cmdlet.</span></span> |
|<span data-ttu-id="3df44-235">-NoRestart [&lt;SwitchParameter&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-235">-NoRestart [&lt;SwitchParameter&gt;]</span></span> |<span data-ttu-id="3df44-236">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-236">Required</span></span> |<span data-ttu-id="3df44-237">Keine Aufforderung zum Neustart, wenn Sie das Setupprogramm ausführen (Neustart ist erforderlich, um das Container-Feature zu aktivieren).</span><span class="sxs-lookup"><span data-stu-id="3df44-237">Don't prompt for reboot when running setup (reboot is required to enable the container feature).</span></span> |
|<span id="conversion-params" /> <strong><span data-ttu-id="3df44-238">Konvertierungsparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-238">Conversion parameters</span></span></strong>|||
|<span data-ttu-id="3df44-239">-AppInstallPath &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-239">-AppInstallPath &lt;String&gt;</span></span>  |<span data-ttu-id="3df44-240">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-240">Optional</span></span> |<span data-ttu-id="3df44-241">Der vollständige Pfad zum Stammordner Ihrer Anwendung für die installierten Dateien, wenn sie installiert wurde (z.B. „C:\Programme (x86) \MyApp“).</span><span class="sxs-lookup"><span data-stu-id="3df44-241">The full path to your application's root folder for the installed files if it were installed (e.g., "C:\Program Files (x86)\MyApp").</span></span>|
|<span data-ttu-id="3df44-242">-Destination &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-242">-Destination &lt;String&gt;</span></span> |<span data-ttu-id="3df44-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-243">Required</span></span> |<span data-ttu-id="3df44-244">Das gewünschte Ziel für die APPX-Ausgabe des Konverters. DesktopAppConverter kann diesen Speicherort erstellen, wenn er nicht bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3df44-244">The desired destination for the converter's appx output - DesktopAppConverter can create this location if it doesn't already exist.</span></span>|
|<span data-ttu-id="3df44-245">-Installer &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-245">-Installer &lt;String&gt;</span></span> |<span data-ttu-id="3df44-246">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-246">Required</span></span> |<span data-ttu-id="3df44-247">Der Pfad zum Installationsprogramm für Ihre Anwendung. Muss im unbeaufsichtigten Modus bzw. automatisch ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="3df44-247">The path to the installer for your application - must be able to run unattended/silently.</span></span> <span data-ttu-id="3df44-248">Bei der Konvertierung ohne Installationsprogramm ist dies der Pfad zum Stammverzeichnis der App-Dateien.</span><span class="sxs-lookup"><span data-stu-id="3df44-248">No-installer conversion, this is the path to the root directory of your app files.</span></span> |
|<span data-ttu-id="3df44-249">-InstallerArguments &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-249">-InstallerArguments &lt;String&gt;</span></span> |<span data-ttu-id="3df44-250">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-250">Optional</span></span> |<span data-ttu-id="3df44-251">Eine durch Trennzeichen getrennte Liste oder Zeichenfolge mit Argumenten, die das unbeaufsichtigte bzw. automatische Ausführen des Installers erzwingen.</span><span class="sxs-lookup"><span data-stu-id="3df44-251">A comma-separated list or string of arguments to force your installer to run unattended/silently.</span></span> <span data-ttu-id="3df44-252">Dieser Parameter ist optional, wenn der Installer eine MSI-Datei ist.</span><span class="sxs-lookup"><span data-stu-id="3df44-252">This parameter is optional if your installer is an msi.</span></span> <span data-ttu-id="3df44-253">Geben Sie zum Abrufen eines Protokolls vom Installer hier das Argument für die Protokollierung an, und verwenden Sie den Pfad &lt;log_folder&gt;, ein Token, das vom Konverter mit dem entsprechenden Pfad ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-253">To get a log from your installer, supply the logging argument for the installer here and use the path &lt;log_folder&gt;, which is a token that the converter replaces with the appropriate path.</span></span> <br><br><span data-ttu-id="3df44-254">**Hinweis**: Unbeaufsichtigte/automatische Flags und Protokollargumente können bei den verschiedenen Installationstechnologien variieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-254">**NOTE**: The unattended/silent flags and log arguments will vary between installer technologies.</span></span> <br><br><span data-ttu-id="3df44-255">Ein Verwendungsbeispiel für diesen Parameter: -InstallerArguments "/silent /log &lt;log_folder&gt;\install.log" Ein weiteres Beispiel, in dem keine Protokolldatei generiert wird, kann wie folgt aussehen: ```-InstallerArguments "/quiet", "/norestart"``` Alle Protokolle müssen auf den Tokenpfad &lt;log_folder&gt; verweisen, wenn der Konverter diese erfassen und im endgültigen Protokollordner speichern soll.</span><span class="sxs-lookup"><span data-stu-id="3df44-255">An example usage for this parameter: -InstallerArguments "/silent /log &lt;log_folder&gt;\install.log" Another example that doesn't produce a log file may look like: ```-InstallerArguments "/quiet", "/norestart"``` Again, you must literally direct any logs to the token path &lt;log_folder&gt; if you want the converter to capture it and put it in the final log folder.</span></span>|
|<span data-ttu-id="3df44-256">-InstallerValidExitCodes &lt;Int32&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-256">-InstallerValidExitCodes &lt;Int32&gt;</span></span> |<span data-ttu-id="3df44-257">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-257">Optional</span></span> |<span data-ttu-id="3df44-258">Eine durch Trennzeichen getrennte Liste mit Exitcodes, die angeben, das der Installer erfolgreich ausgeführt wurde (z. B.: 0, 1234, 5678).</span><span class="sxs-lookup"><span data-stu-id="3df44-258">A comma-separated list of exit codes that indicate your installer ran successfully (for example: 0, 1234, 5678).</span></span>  <span data-ttu-id="3df44-259">Standardmäßig ist dieser 0 für Nicht-MSI-Dateien und 0, 1641, 3010 für MSI-Dateien.</span><span class="sxs-lookup"><span data-stu-id="3df44-259">By default this is 0 for non-msi, and 0, 1641, 3010 for msi.</span></span>|
|<span id="identity-params" /><strong><span data-ttu-id="3df44-260">Paket-Identitätsparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-260">Package identity parameters</span></span></strong>||
|<span data-ttu-id="3df44-261">-PackageName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-261">-PackageName &lt;String&gt;</span></span> |<span data-ttu-id="3df44-262">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-262">Required</span></span> |<span data-ttu-id="3df44-263">Der Name des Universellen Windows-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="3df44-263">The name of your Universal Windows App package</span></span> |
|<span data-ttu-id="3df44-264">-Publisher &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-264">-Publisher &lt;String&gt;</span></span> |<span data-ttu-id="3df44-265">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-265">Required</span></span> |<span data-ttu-id="3df44-266">Der Herausgeber des Universellen Windows-App-Pakets</span><span class="sxs-lookup"><span data-stu-id="3df44-266">The publisher of your Universal Windows App package</span></span> |
|<span data-ttu-id="3df44-267">-Version &lt;Version&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-267">-Version &lt;Version&gt;</span></span> |<span data-ttu-id="3df44-268">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-268">Required</span></span> |<span data-ttu-id="3df44-269">Die Versionsnummer für das Universelles Windows-App-Paket</span><span class="sxs-lookup"><span data-stu-id="3df44-269">The version number for your Universal Windows App package</span></span> |
|<span id="manifest-params" /><strong><span data-ttu-id="3df44-270">Paketmanifest-Parameter</span><span class="sxs-lookup"><span data-stu-id="3df44-270">Package manifest parameters</span></span></strong>||
|<span data-ttu-id="3df44-271">-AppExecutable &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-271">-AppExecutable &lt;String&gt;</span></span> |<span data-ttu-id="3df44-272">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-272">Optional</span></span> |<span data-ttu-id="3df44-273">Der Name der ausführbaren Hauptdatei Ihrer Anwendung (z.B. „MyApp.exe“).</span><span class="sxs-lookup"><span data-stu-id="3df44-273">The name of your application's main executable (eg "MyApp.exe").</span></span> <span data-ttu-id="3df44-274">Dieser Parameter ist bei der Konvertierung ohne Installationsprogramm erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3df44-274">This parameter is required for a no-installer conversion.</span></span> |
|<span data-ttu-id="3df44-275">-AppFileTypes &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-275">-AppFileTypes &lt;String&gt;</span></span>|<span data-ttu-id="3df44-276">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-276">Optional</span></span> |<span data-ttu-id="3df44-277">Eine durch Trennzeichen getrennte Liste von Dateitypen, denen die Anwendung zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-277">A comma-separated list of file types which the application will be associated with.</span></span> <span data-ttu-id="3df44-278">Beispiel: -AppFileTypes „'.md', '.markdown'“.</span><span class="sxs-lookup"><span data-stu-id="3df44-278">Example usage: -AppFileTypes "'.md', '.markdown'".</span></span>|
|<span data-ttu-id="3df44-279">-AppId &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-279">-AppId &lt;String&gt;</span></span> |<span data-ttu-id="3df44-280">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-280">Optional</span></span> |<span data-ttu-id="3df44-281">Legt einen Wert fest, auf den die Anwendungs-ID im Windows-App-Paket-Manifest festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-281">Specifies a value to set Application Id to in the Windows app package manifest.</span></span> <span data-ttu-id="3df44-282">Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3df44-282">If it is not specified, it will be set to the value passed in for *PackageName*.</span></span>|
|<span data-ttu-id="3df44-283">-AppDisplayName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-283">-AppDisplayName &lt;String&gt;</span></span>  |<span data-ttu-id="3df44-284">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-284">Optional</span></span> |<span data-ttu-id="3df44-285">Legt einen Wert fest, auf den der Anzeigename der Anwendung im Windows-App-Paket-Manifest festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-285">Specifies a value to set Application Display Name to in the Windows app package manifest.</span></span> <span data-ttu-id="3df44-286">Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3df44-286">If it is not specified, it will be set to the value passed in for *PackageName*.</span></span> |
|<span data-ttu-id="3df44-287">-AppDescription &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-287">-AppDescription &lt;String&gt;</span></span> |<span data-ttu-id="3df44-288">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-288">Optional</span></span> |<span data-ttu-id="3df44-289">Legt einen Wert fest, auf den die Anwendungsbeschreibung im Windows-App-Paket-Manifest festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-289">Specifies a value to set Application Description to in the Windows app package manifest.</span></span> <span data-ttu-id="3df44-290">Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3df44-290">If it is not specified, it will be set to the value passed in for *PackageName*.</span></span>|
|<span data-ttu-id="3df44-291">-PackageDisplayName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-291">-PackageDisplayName &lt;String&gt;</span></span> |<span data-ttu-id="3df44-292">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-292">Optional</span></span> |<span data-ttu-id="3df44-293">Legt einen Wert fest, auf den der Anzeigename des Pakets im Windows-App-Paket-Manifest festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-293">Specifies a value to set Package Display Name to in the Windows app package manifest.</span></span> <span data-ttu-id="3df44-294">Wird kein Wert angegeben, wird diese auf den für *PackageName* übergebenen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3df44-294">If it is not specified, it will be set to the value passed in for *PackageName*.</span></span> |
|<span data-ttu-id="3df44-295">-PackagePublisherDisplayName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-295">-PackagePublisherDisplayName &lt;String&gt;</span></span> |<span data-ttu-id="3df44-296">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-296">Optional</span></span> |<span data-ttu-id="3df44-297">Legt einen Wert fest, auf den der Anzeigename des Paketherausgebers im Windows-App-Paket-Manifest festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-297">Specifies a value to set Package Publisher Display Name to in the Windows app package manifest.</span></span> <span data-ttu-id="3df44-298">Wird kein Wert angegeben, wird dieser auf den für *Publisher* übergebenen Wert festgelegt.</span><span class="sxs-lookup"><span data-stu-id="3df44-298">If it is not specified, it will be set to the value passed in for *Publisher*.</span></span> |
|<span id="cleanup-params" /><strong><span data-ttu-id="3df44-299">Bereinigungsparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-299">Cleanup parameters</span></span></strong>|||
|<span data-ttu-id="3df44-300">-Bereinigung [&lt;Option&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-300">-Cleanup [&lt;Option&gt;]</span></span> |<span data-ttu-id="3df44-301">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-301">Required</span></span> |<span data-ttu-id="3df44-302">Führt Bereinigung für die DesktopAppConverter-Artefakte aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-302">Runs cleanup for the DesktopAppConverter artifacts.</span></span> <span data-ttu-id="3df44-303">Es gibt 3 gültige Optionen für den Bereinigungsmodus.</span><span class="sxs-lookup"><span data-stu-id="3df44-303">There are 3 valid options for the Cleanup mode.</span></span> |
|<span data-ttu-id="3df44-304">-Alle Bereinigung</span><span class="sxs-lookup"><span data-stu-id="3df44-304">-Cleanup All</span></span> | |<span data-ttu-id="3df44-305">Löscht alle erweiterten Basisimages, entfernt alle temporären Konverterdateien, entfernt das Containernetzwerk und deaktiviert die optionale Windows-Funktion.</span><span class="sxs-lookup"><span data-stu-id="3df44-305">Deletes all expanded base images, removes any temporary converter files, removes the container network, and disables the optional Windows feature, Containers.</span></span> |
|<span data-ttu-id="3df44-306">-WorkDirectory Bereinigung</span><span class="sxs-lookup"><span data-stu-id="3df44-306">-Cleanup WorkDirectory</span></span> |<span data-ttu-id="3df44-307">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-307">Required</span></span> |<span data-ttu-id="3df44-308">Entfernt alle temporären Konverterdateien.</span><span class="sxs-lookup"><span data-stu-id="3df44-308">Removes all the temporary converter files.</span></span> |
|<span data-ttu-id="3df44-309">-ExpandedImage Bereinigung</span><span class="sxs-lookup"><span data-stu-id="3df44-309">-Cleanup ExpandedImage</span></span> |<span data-ttu-id="3df44-310">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-310">Required</span></span> |<span data-ttu-id="3df44-311">Löscht alle erweiterten Basisimages, die auf dem Hostcomputer installiert sind.</span><span class="sxs-lookup"><span data-stu-id="3df44-311">Deletes all the expanded base images installed on your host machine.</span></span> |
|<span id="architecture-params" /><strong><span data-ttu-id="3df44-312">Paketarchitekturparameter</span><span class="sxs-lookup"><span data-stu-id="3df44-312">Package architecture parameters</span></span></strong>|||
|<span data-ttu-id="3df44-313">-PackageArch &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-313">-PackageArch &lt;String&gt;</span></span> |<span data-ttu-id="3df44-314">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-314">Required</span></span> |<span data-ttu-id="3df44-315">Generiert ein Paket mit der angegebenen Architektur.</span><span class="sxs-lookup"><span data-stu-id="3df44-315">Generates a package with the specified architecture.</span></span> <span data-ttu-id="3df44-316">Gültige Optionen sind „x86“ und „x64“ (Beispiel: -PackageArch x86).</span><span class="sxs-lookup"><span data-stu-id="3df44-316">Valid options are 'x86' or 'x64'; for example, -PackageArch x86.</span></span> <span data-ttu-id="3df44-317">Dieser Parameter ist optional.</span><span class="sxs-lookup"><span data-stu-id="3df44-317">This parameter is optional.</span></span> <span data-ttu-id="3df44-318">Falls nicht angegeben, versucht der DesktopAppConverter die Paketarchitektur automatisch zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="3df44-318">If unspecified, the DesktopAppConverter will try to auto-detect package architecture.</span></span> <span data-ttu-id="3df44-319">Wenn die automatische Erkennung fehlschlägt, wird standardmäßig ein x64-Paket erstellt.</span><span class="sxs-lookup"><span data-stu-id="3df44-319">If auto-detection fails, it will default to x64 package.</span></span> |
|<span id="other-params" /><strong><span data-ttu-id="3df44-320">Sonstige Parameter</span><span class="sxs-lookup"><span data-stu-id="3df44-320">Miscellaneous parameters</span></span></strong>|||
|<span data-ttu-id="3df44-321">-ExpandedBaseImage &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-321">-ExpandedBaseImage &lt;String&gt;</span></span>  |<span data-ttu-id="3df44-322">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-322">Optional</span></span> |<span data-ttu-id="3df44-323">Vollständige Pfad zu einem bereits erweiterten Basisimage.</span><span class="sxs-lookup"><span data-stu-id="3df44-323">Full path to an already expanded base image.</span></span>|
|<span data-ttu-id="3df44-324">-MakeAppx [&lt;SwitchParameter&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-324">-MakeAppx [&lt;SwitchParameter&gt;]</span></span>  |<span data-ttu-id="3df44-325">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-325">Optional</span></span> |<span data-ttu-id="3df44-326">Ein Switch, mit dem, falls vorhanden, dieses Skript zum Aufrufen von MakeAppx für die Ausgabe angewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-326">A switch that, when present, tells this script to call MakeAppx on the output.</span></span> |
|<span data-ttu-id="3df44-327">-LogFile &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-327">-LogFile &lt;String&gt;</span></span>  |<span data-ttu-id="3df44-328">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-328">Optional</span></span> |<span data-ttu-id="3df44-329">Gibt eine Protokolldatei an.</span><span class="sxs-lookup"><span data-stu-id="3df44-329">Specifies a log file.</span></span> <span data-ttu-id="3df44-330">Wird dieser nicht angegeben, wird ein temporärer Speicherort für eine Protokolldatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="3df44-330">If omitted, a log file temporary location will be created.</span></span> |
| <span data-ttu-id="3df44-331">– Zeichen [&lt;SwitchParameter&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-331">-Sign [&lt;SwitchParameter&gt;]</span></span> |<span data-ttu-id="3df44-332">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-332">Optional</span></span> |<span data-ttu-id="3df44-333">Weisen Sie diesen Skript an, das ausgehende Windows-App-Paket mit einem generierten Zertifikat für Testzwecke zu signieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-333">Tells this script to sign the output Windows app package by using a generated certificate for testing purposes.</span></span> <span data-ttu-id="3df44-334">Dieser Switch sollte ebenso vorhanden sein, wie der Switch ```-MakeAppx```.</span><span class="sxs-lookup"><span data-stu-id="3df44-334">This switch should be present alongside the switch ```-MakeAppx```.</span></span> |
|<span data-ttu-id="3df44-335">&lt;Allgemeine Parameter&gt;</span><span class="sxs-lookup"><span data-stu-id="3df44-335">&lt;Common parameters&gt;</span></span> |<span data-ttu-id="3df44-336">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3df44-336">Required</span></span> |<span data-ttu-id="3df44-337">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: *Verbose*, *Debug*, *ErrorAction*, *ErrorVariable*, *WarningAction*, *WarningVariable*, *OutBuffer*, *PipelineVariable* und *OutVariable*.</span><span class="sxs-lookup"><span data-stu-id="3df44-337">This cmdlet supports the common parameters: *Verbose*, *Debug*, *ErrorAction*, *ErrorVariable*, *WarningAction*, *WarningVariable*, *OutBuffer*, *PipelineVariable*, and *OutVariable*.</span></span> <span data-ttu-id="3df44-338">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3df44-338">For more info, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span> |
| <span data-ttu-id="3df44-339">-Überprüfen [&lt;SwitchParameter&gt;]</span><span class="sxs-lookup"><span data-stu-id="3df44-339">-Verify [&lt;SwitchParameter&gt;]</span></span> |<span data-ttu-id="3df44-340">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-340">Optional</span></span> |<span data-ttu-id="3df44-341">Ein Switch, mit dem DAC angewiesen wird, das verpackte App-Paket auf Anforderungen von Desktop-Brücke und Windows Store zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="3df44-341">A switch that, when present, tells the DAC to validate the app package against Desktop Bridge and Windows Store requirements.</span></span> <span data-ttu-id="3df44-342">Das Ergebnis ist ein Überprüfungsbericht „VerifyReport.xml“, der am besten in einem Browser angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3df44-342">The result is a validation report "VerifyReport.xml", which is best visualized in a browser.</span></span> <span data-ttu-id="3df44-343">Dieser Switch sollte ebenso vorhanden sein, wie der Switch `-MakeAppx`.</span><span class="sxs-lookup"><span data-stu-id="3df44-343">This switch should be present alongside the switch `-MakeAppx`.</span></span> |
|<span data-ttu-id="3df44-344">-PublishComRegistrations</span><span class="sxs-lookup"><span data-stu-id="3df44-344">-PublishComRegistrations</span></span>| <span data-ttu-id="3df44-345">Optional</span><span class="sxs-lookup"><span data-stu-id="3df44-345">Optional</span></span>| <span data-ttu-id="3df44-346">Scant alle Öffentlichen COM-Registrierungen, die von Ihrem Installer erstellt wurden, und veröffentlicht die gültigen in Ihrem Manifest.</span><span class="sxs-lookup"><span data-stu-id="3df44-346">Scans all public COM registrations made by your installer and publishes the valid ones in your manifest.</span></span> <span data-ttu-id="3df44-347">Verwenden Sie dieses Flag nur dann, wenn Sie diese Registrierungen für andere Anwendungen verfügbar machen möchten.</span><span class="sxs-lookup"><span data-stu-id="3df44-347">Use this flag only if you want to make these registrations available to other applications.</span></span> <span data-ttu-id="3df44-348">Sie müssen dieses Flag verwenden, wenn diese Registrierungen nur von Ihrer Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-348">You don't need to use this flag if these registrations will be used only by your application.</span></span> <br><br><span data-ttu-id="3df44-349">Lesen Sie [diesen Artikel](https://blogs.windows.com/buildingapps/2017/04/13/com-server-ole-document-support-desktop-bridge/#lDg5gSFxJ2TDlpC6.97), um sicherzustellen, dass die COM-Registrierungen nach der Verpackung Ihrer App erwartungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-349">Review [this article](https://blogs.windows.com/buildingapps/2017/04/13/com-server-ole-document-support-desktop-bridge/#lDg5gSFxJ2TDlpC6.97) to make sure that your COM registrations behave as you expect after you package your app.</span></span>

<span id="run-app" />
## <a name="run-the-packaged-app"></a><span data-ttu-id="3df44-350">Ausführung der verpackten App</span><span class="sxs-lookup"><span data-stu-id="3df44-350">Run the packaged app</span></span>

<span data-ttu-id="3df44-351">Es gibt zwei Möglichkeiten, Ihre App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3df44-351">There's two ways to run your app.</span></span>

<span data-ttu-id="3df44-352">Eine Möglichkeit besteht darin, eine PowerShell-Eingabeaufforderung zu öffnen, und den folgenden Befehl einzugeben: ```Add-AppxPackage –Register AppxManifest.xml```.</span><span class="sxs-lookup"><span data-stu-id="3df44-352">One way is to open a PowerShell command prompt, and then type this command: ```Add-AppxPackage –Register AppxManifest.xml```.</span></span> <span data-ttu-id="3df44-353">Es ist wahrscheinlich die einfachste Möglichkeit, Ihre App auszuführen, da Sie sie nicht signieren müssen.</span><span class="sxs-lookup"><span data-stu-id="3df44-353">It's probably the easiest way to run your app because you don't have to sign it.</span></span>

<span data-ttu-id="3df44-354">Eine weitere Möglichkeit ist das Signieren Ihrer App mit einem Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="3df44-354">Another way is to sign your app with a certificate.</span></span> <span data-ttu-id="3df44-355">Wenn Sie den ```sign```-Parameter verwenden, generiert der Desktop App Converter eines für Sie und signiert mit diesem anschließend Ihre App.</span><span class="sxs-lookup"><span data-stu-id="3df44-355">If you use the ```sign``` parameter, the Desktop App Converter will generate one for you, and then sign your app with it.</span></span> <span data-ttu-id="3df44-356">Diese Datei heißt **auto-generated.cer**; Sie finden sie im Stammordner der verpackten App.</span><span class="sxs-lookup"><span data-stu-id="3df44-356">That file is named **auto-generated.cer**, and you can find it in the root folder of your packaged app.</span></span>

<span data-ttu-id="3df44-357">Führen Sie die folgenden Schritte aus, um das generierte Zertifikat zu installieren, und führen Sie anschließend Ihre App aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-357">Follow these steps to install the generated certificate, and then run your app.</span></span>

1. <span data-ttu-id="3df44-358">Doppelklicken Sie auf die Datei **auto-generated.cer**, um das Zertifikat zu installieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-358">Double-click the **auto-generated.cer** file to install the certificate.</span></span>

   ![Datei mit generiertem Zertifikat](images/desktop-to-uwp/generated-cert-file.png)

   > [!NOTE]
   > <span data-ttu-id="3df44-360">Wenn Sie zur Eingabe eines Kennworts aufgefordert werden, verwenden Sie das Standardkennwort „123456”.</span><span class="sxs-lookup"><span data-stu-id="3df44-360">If you're prompted for a password, use the default password "123456".</span></span>

2. <span data-ttu-id="3df44-361">Wählen Sie im Dialogfeld **Zertifikat** die Schaltfläche **Zertifikat installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="3df44-361">In the **Certificate** dialog box, choose the **Install Certificate** button.</span></span>
3. <span data-ttu-id="3df44-362">Installieren Sie das Zertifikat im **Zertifikatimport-Assistenten** auf dem **lokalen Computer**, und legen Sie das Zertifikat im Zertifikatspeicher **Vertrauenswürdige Personen** ab.</span><span class="sxs-lookup"><span data-stu-id="3df44-362">In the **Certificate Import Wizard**, install the certificate onto the **Local Machine**, and place the certificate into the **Trusted People** certificate store.</span></span>

   ![Speicher für vertrauenswürdige Personen](images/desktop-to-uwp/trusted-people-store.png)

5. <span data-ttu-id="3df44-364">Doppelklicken Sie im Stammordner der verpackten App auf die Windows-App-Paketdatei.</span><span class="sxs-lookup"><span data-stu-id="3df44-364">In root folder of your packaged app, double click the Windows app package file.</span></span>

   ![Windows-App-Paketdatei](images/desktop-to-uwp/windows-app-package.png)

6. <span data-ttu-id="3df44-366">Installieren Sie die App, indem Sie die Schaltfläche **Installieren** auswählen.</span><span class="sxs-lookup"><span data-stu-id="3df44-366">Install the app, by choosing the **Install** button.</span></span>

   ![Schaltfläche „Installieren”](images/desktop-to-uwp/install.png)


## <a name="modify-the-packaged-app"></a><span data-ttu-id="3df44-368">Ändern der verpackten App</span><span class="sxs-lookup"><span data-stu-id="3df44-368">Modify the packaged app</span></span>

<span data-ttu-id="3df44-369">Sie werden wahrscheinlich Änderungen an der verpackten App vornehmen, um Fehler zu beheben, visuelle Ressourcen hinzuzufügen oder die App durch moderne Funktionen wie Live-Kacheln zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="3df44-369">You'll likely make changes to your packaged app to address bugs, add visual assets, or enhance your app with modern experiences such as live tiles.</span></span>

<span data-ttu-id="3df44-370">Wenn Sie die Änderungen vorgenommen haben, müssen Sie den Konverter nicht erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="3df44-370">After you make your changes, you don't need to run the converter again.</span></span> <span data-ttu-id="3df44-371">Sie können Ihre App mithilfe des Tools MakeAppx und der Datei appxmanifest.xml, die der DAC für Ihre App generiert, umpacken.</span><span class="sxs-lookup"><span data-stu-id="3df44-371">You can repackage your app by using the MakeAppx tool and the appxmanifest.xml file the DAC generates for your app.</span></span> <span data-ttu-id="3df44-372">Weitere Informationen erhalten Sie unter [Erstellen eines Windows-App-Pakets](desktop-to-uwp-manual-conversion.md#make-appx).</span><span class="sxs-lookup"><span data-stu-id="3df44-372">See [Generate a Windows app package](desktop-to-uwp-manual-conversion.md#make-appx).</span></span>

> [!NOTE]
> <span data-ttu-id="3df44-373">Wenn Sie Änderungen an Registrierungseinstellungen vornehmen, die das Installationsprogramm festgelegt hat, müssen Sie den Desktop App Converter erneut ausführen, um diese Änderungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="3df44-373">If you make changes to registry settings that your installer makes, you will have to run the Desktop App Converter again to pick up those changes.</span></span>

**<span data-ttu-id="3df44-374">Videos</span><span class="sxs-lookup"><span data-stu-id="3df44-374">Videos</span></span>**

|<span data-ttu-id="3df44-375">Ändern und Umpacken der Ausgabe</span><span class="sxs-lookup"><span data-stu-id="3df44-375">Modify and repackage output</span></span> |<span data-ttu-id="3df44-376">Demo: Ändern und Umpacken der Ausgabe</span><span class="sxs-lookup"><span data-stu-id="3df44-376">Demo: Modify and repackage output</span></span>|
|---|---|
|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Video-Modifying-and-Repackaging-Output-from-Desktop-App-Converter-OwpAJ3WhD_6706218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Modify-Output-from-Desktop-App-Converter-gEnsa3WhD_8606218965" width="426" height="472" allowFullScreen frameBorder="0"></iframe>|

<span data-ttu-id="3df44-377">In den folgenden zwei Abschnitten werden verschiedene optionale Fixups für die verpackte App beschrieben, die Sie in Erwägung ziehen können.</span><span class="sxs-lookup"><span data-stu-id="3df44-377">The following two sections describe a couple of optional fix-ups to the packaged app that you might consider.</span></span>

### <a name="delete-unnecessary-files-and-registry-keys"></a><span data-ttu-id="3df44-378">Löschen nicht benötigter Dateien und Registrierungsschlüssel</span><span class="sxs-lookup"><span data-stu-id="3df44-378">Delete unnecessary files and registry keys</span></span>

<span data-ttu-id="3df44-379">Desktop App Converter verfolgt beim Herausfiltern von Dateien und Systemstörungen im Container einen sehr konservativen Ansatz.</span><span class="sxs-lookup"><span data-stu-id="3df44-379">The desktop App Converter takes a very conservative approach to filtering out files and system noise in the container.</span></span>

<span data-ttu-id="3df44-380">Wenn Sie möchten, können Sie den VFS-Ordner überprüfen und alle Dateien löschen, die der Installer nicht benötigt.</span><span class="sxs-lookup"><span data-stu-id="3df44-380">If you want, you can review the VFS folder and delete any files that your installer doesn't need.</span></span>  <span data-ttu-id="3df44-381">Sie können auch den Inhalt von „Reg.dat“ überprüfen und alle Schlüssel löschen, die nicht von der App installiert/benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-381">You can also review the contents of Reg.dat and delete any keys that are not installed/needed by the app.</span></span>

### <a name="fix-corrupted-pe-headers"></a><span data-ttu-id="3df44-382">Korrigieren fehlerhafter PE-Header</span><span class="sxs-lookup"><span data-stu-id="3df44-382">Fix corrupted PE headers</span></span>

<span data-ttu-id="3df44-383">Beim Konvertieren führt DesktopAppConverter automatisch PEHeaderCertFixTool aus, um alle beschädigten PE-Header zu korrigieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-383">During the conversion process, the DesktopAppConverter automatically runs the PEHeaderCertFixTool to fixup any corrupted PE headers.</span></span> <span data-ttu-id="3df44-384">Sie können PEHeaderCertFixTool jedoch auch für ein UWP-Windows-App-Paket, lose Dateien oder eine bestimmte Binärdatei ausführen.</span><span class="sxs-lookup"><span data-stu-id="3df44-384">However, you can also run the PEHeaderCertFixTool on a UWP Windows app package, loose files, or a specific binary.</span></span> <span data-ttu-id="3df44-385">Hier sehen Sie ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="3df44-385">Here's an example.</span></span>

```CMD
PEHeaderCertFixTool.exe <binary file>|<.appx package>|&lt;folder> [/c] [/v]
 /c   -- check for corrupted certificate but do not fix (optional)
 /v   -- verbose (optional)
example1: PEHeaderCertFixTool app.exe
example2: PEHeaderCertFixTool c:\package.appx /c
example3: PEHeaderCertFixTool c:\myapp /c /v
```

## <a name="known-issues-and-disclosures"></a><span data-ttu-id="3df44-386">Bekannte Probleme und offenzulegende Informationen</span><span class="sxs-lookup"><span data-stu-id="3df44-386">Known issues and disclosures</span></span>

### <a name="known-issues-and-workarounds"></a><span data-ttu-id="3df44-387">Bekannte Probleme und Umgehungen</span><span class="sxs-lookup"><span data-stu-id="3df44-387">Known issues and workarounds</span></span>

<span data-ttu-id="3df44-388">Hier erfahren Sie mehr über einige bekannte Probleme und einige Maßnahmen, durch die diese sich möglicherweise beheben lassen.</span><span class="sxs-lookup"><span data-stu-id="3df44-388">Here's some known issues and some things you can try to resolve them.</span></span>

#### <a name="ecreatingisolatedenvfailed-an-estartingisolatedenvfailed-errors"></a><span data-ttu-id="3df44-389">Fehler E_CREATING_ISOLATED_ENV_FAILED und E_STARTING_ISOLATED_ENV_FAILED</span><span class="sxs-lookup"><span data-stu-id="3df44-389">E_CREATING_ISOLATED_ENV_FAILED an E_STARTING_ISOLATED_ENV_FAILED errors</span></span>    

<span data-ttu-id="3df44-390">Wenn Sie eine dieser Fehlermeldungen erhalten, stellen Sie sicher, dass Sie ein gültiges Basisimage aus dem [Download Center](https://aka.ms/converterimages) verwenden.</span><span class="sxs-lookup"><span data-stu-id="3df44-390">If you receive either of these errors, make sure that you're using a valid base image from the [download center](https://aka.ms/converterimages).</span></span>
<span data-ttu-id="3df44-391">Wenn Sie ein gültiges Basisimage verwenden, versuchen Sie, ``-Cleanup All`` in Ihrem Befehl zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3df44-391">If you’re using a valid base image, try using ``-Cleanup All`` in your command.</span></span>
<span data-ttu-id="3df44-392">Wenn dies nicht funktioniert, senden Sie uns unter converter@microsoft.com bitte Ihre Protokolle, damit wir den Vorgang untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="3df44-392">If that does not work, please send us your logs at converter@microsoft.com to help us investigate.</span></span>

#### <a name="new-containernetwork-the-object-already-exists-error"></a><span data-ttu-id="3df44-393">New-ContainerNetwork: Fehler „Das Objekt ist bereits vorhanden.”</span><span class="sxs-lookup"><span data-stu-id="3df44-393">New-ContainerNetwork: The object already exists error</span></span>

<span data-ttu-id="3df44-394">Dieser Fehler kann angezeigt werden, wenn Sie ein neues Basisimage einrichten.</span><span class="sxs-lookup"><span data-stu-id="3df44-394">You might receive this error when you setup a new base image.</span></span> <span data-ttu-id="3df44-395">Dies kann passieren, wenn Sie ein Windows-Insider-Test-Flight auf einem Entwicklercomputer erhalten, auf dem zuvor Desktop App Converter installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="3df44-395">This can happen if you have a Windows Insider flight on a developer machine that previously had the Desktop App Converter installed.</span></span>

<span data-ttu-id="3df44-396">Um dieses Problem zu beheben, versuchen Sie, den Befehl `Netsh int ipv4 reset` über eine Eingabeaufforderung mit erhöhten Rechten auszuführen, und starten Sie den Computer dann neu.</span><span class="sxs-lookup"><span data-stu-id="3df44-396">To resolve this issue, try running the command `Netsh int ipv4 reset` from an elevated command prompt, and then reboot your machine.</span></span>

#### <a name="your-net-app-is-compiled-with-the-anycpu-build-option-and-fails-to-install"></a><span data-ttu-id="3df44-397">Ihre .NET-App wurde mit der Buildoption „AnyCPU” kompiliert und lässt sich nicht installieren</span><span class="sxs-lookup"><span data-stu-id="3df44-397">Your .NET app is compiled with the "AnyCPU" build option and fails to install</span></span>

<span data-ttu-id="3df44-398">Dies kann vorkommen, wenn die ausführbare Hauptdatei oder eine Abhängigkeitsdatei in der Ordnerhierarchie **Programmdateien** oder **Windows\System32** abgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="3df44-398">This can happen if the main executable or any of the dependencies were placed anywhere in the **Program Files** or **Windows\System32** folder hierarchy.</span></span>

<span data-ttu-id="3df44-399">Um dieses Problem zu beheben, versuchen Sie, mithilfe Ihres architekturspezifischen Desktop-Installers (32 Bit oder 64 Bit) ein Windows-App-Paket zu generieren.</span><span class="sxs-lookup"><span data-stu-id="3df44-399">To resolve this issue, try using your architecture-specific desktop installer (32 bit or 64 bit) to generate a Windows app package.</span></span>

#### <a name="publishing-public-side-by-side-fusion-assemblies-wont-work"></a><span data-ttu-id="3df44-400">Die Veröffentlichung von öffentlichen parallelen Fusion-Assemblys ist nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="3df44-400">Publishing public side-by-side Fusion assemblies won't work</span></span>

 <span data-ttu-id="3df44-401">Während der Installation kann eine Anwendung öffentliche parallele Fusion-Assemblys veröffentlichen, auf die von jedem anderen Prozess zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="3df44-401">During install, an application can publish public side-by-side Fusion assemblies, accessible to any other process.</span></span> <span data-ttu-id="3df44-402">Während der Erstellung des Prozessaktivierungskontexts werden diese Assemblys von einem Systemprozess mit dem Namen CSRSS.exe abgerufen.</span><span class="sxs-lookup"><span data-stu-id="3df44-402">During process activation context creation, these assemblies are retrieved by a system process named CSRSS.exe.</span></span> <span data-ttu-id="3df44-403">Wenn dies für einen konvertierten Prozess erfolgt, tritt beim Erstellen des Aktivierungskontexts sowie beim Laden des Moduls dieser Assemblys ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="3df44-403">When this is done for a converted process, activation context creation and module loading of these assemblies will fail.</span></span> <span data-ttu-id="3df44-404">Die parallelen Fusion-Assemblys werden an folgenden Orten registriert:</span><span class="sxs-lookup"><span data-stu-id="3df44-404">The side-by-side Fusion assemblies are registered in the following locations:</span></span>
  + <span data-ttu-id="3df44-405">Registrierung:</span><span class="sxs-lookup"><span data-stu-id="3df44-405">Registry:</span></span> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\SideBySide\Winners`
  + <span data-ttu-id="3df44-406">Dateisystem: %windir%\\SideBySide</span><span class="sxs-lookup"><span data-stu-id="3df44-406">File System: %windir%\\SideBySide</span></span>

<span data-ttu-id="3df44-407">Dies ist eine bekannte Einschränkung, und derzeit sind keine Umgehungen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="3df44-407">This is a known limitation and no workaround currently exists.</span></span> <span data-ttu-id="3df44-408">Integrierte Assemblys wie z.B. ComCtl sind jedoch Teil des Betriebssystems, sodass entsprechende Abhängigkeiten sicher sind.</span><span class="sxs-lookup"><span data-stu-id="3df44-408">That said, Inbox assemblies, like ComCtl, are shipped with the OS, so taking a dependency on them is safe.</span></span>

#### <a name="error-found-in-xml-the-executable-attribute-is-invalid---the-value-myappexe-is-invalid-according-to-its-datatype"></a><span data-ttu-id="3df44-409">Fehler in XML gefunden.</span><span class="sxs-lookup"><span data-stu-id="3df44-409">Error found in XML.</span></span> <span data-ttu-id="3df44-410">Das Attribut „Ausführbare Datei” ist ungültig. – Der Wert MyApp.EXE ist gemäß dem Datentyp ungültig.</span><span class="sxs-lookup"><span data-stu-id="3df44-410">The 'Executable' attribute is invalid - The value 'MyApp.EXE' is invalid according to its datatype</span></span>

<span data-ttu-id="3df44-411">Dies kann vorkommen, wenn die ausführbaren Dateien in Ihrer Anwendung die Erweiterung **. EXE** in Großbuchstaben aufweisen.</span><span class="sxs-lookup"><span data-stu-id="3df44-411">This can happen if the executables in your application have a capitalized **.EXE** extension.</span></span> <span data-ttu-id="3df44-412">Obwohl die Groß-/Kleinschreibung dieser Erweiterung keine Auswirkungen auf die Ausführung Ihrer App haben sollte, kann dies dazu führen, dass der DAC diesen Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="3df44-412">Although, the casing of this extension shouldn't affect whether your app runs, this can cause the DAC to generate this error.</span></span>

<span data-ttu-id="3df44-413">Um dieses Problem zu beheben, versuchen Sie, das **-AppExecutable**-Kennzeichen beim Verpacken festzulegen, und verwenden Sie als Erweiterung Ihrer wichtigsten ausführbaren Datei „.exe” in Kleinbuchstaben (z.B.: MYAPP.exe).</span><span class="sxs-lookup"><span data-stu-id="3df44-413">To resolve this issue, try specifying the **-AppExecutable** flag when you package, and use the lower case ".exe" as the extension of your main executable (For example: MYAPP.exe).</span></span>    <span data-ttu-id="3df44-414">Alternativ können Sie die Schreibweise für alle ausführbaren Dateien in Ihrer App von Großbuchstaben zu Kleinbuchstaben ändern (z.B.: von .EXE zu .exe).</span><span class="sxs-lookup"><span data-stu-id="3df44-414">Alternately you can change the casing for all executables in your app from lowercase to uppercase (For example: from .EXE to .exe).</span></span>


### <a name="telemetry-from-desktop-app-converter"></a><span data-ttu-id="3df44-415">Telemetriedaten aus Desktop App Converter</span><span class="sxs-lookup"><span data-stu-id="3df44-415">Telemetry from Desktop App Converter</span></span>

<span data-ttu-id="3df44-416">Desktop-App-Konverter erfasst ggf. Informationen über Sie und die Verwendung der Software, und sendet diese Informationen an Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3df44-416">Desktop App Converter may collect information about you and your use of the software and send this info to Microsoft.</span></span> <span data-ttu-id="3df44-417">Weitere Informationen zur Sammlung von Daten und deren Verwendung von Microsoft finden Sie in der Produktdokumentation und in den [Datenschutzbestimmungen von Microsoft](http://go.microsoft.com/fwlink/?LinkId=521839).</span><span class="sxs-lookup"><span data-stu-id="3df44-417">You can learn more about Microsoft's data collection and use in the product documentation and in the [Microsoft Privacy Statement](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> <span data-ttu-id="3df44-418">Sie stimmen der Einhaltung aller geltenden Vorschriften der Datenschutzbestimmungen von Microsoft zu.</span><span class="sxs-lookup"><span data-stu-id="3df44-418">You agree to comply with all applicable provisions of the Microsoft Privacy Statement.</span></span>

<span data-ttu-id="3df44-419">Standardmäßig ist Telemetrie für den Desktop-App-Konverter aktiviert.</span><span class="sxs-lookup"><span data-stu-id="3df44-419">By default, telemetry will be enabled for the Desktop App Converter.</span></span> <span data-ttu-id="3df44-420">Fügen Sie den folgenden Registrierungsschlüssel hinzu, um Telemetrie entsprechend zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="3df44-420">Add the following registry key to configure telemetry to a desired setting:</span></span>  

```cmd
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DesktopAppConverter
```
+ <span data-ttu-id="3df44-421">Fügen Sie den *DisableTelemetry*-Wert hinzu, oder bearbeiten Sie diesen, indem Sie DWORD auf 1 festlegen.</span><span class="sxs-lookup"><span data-stu-id="3df44-421">Add or edit the *DisableTelemetry* value by using a DWORD set to 1.</span></span>
+ <span data-ttu-id="3df44-422">Entfernen Sie zum Aktivieren von Telemetrie den Schlüssel, oder legen Sie den Wert auf 0 fest.</span><span class="sxs-lookup"><span data-stu-id="3df44-422">To enable telemetry, remove the key or set the value to 0.</span></span>

### <a name="language-support"></a><span data-ttu-id="3df44-423">Sprachunterstützung</span><span class="sxs-lookup"><span data-stu-id="3df44-423">Language support</span></span>

<span data-ttu-id="3df44-424">Desktop App Converter unterstützt Unicode nicht. Daher können keine chinesischen Zeichen oder Nicht-ASCII-Zeichen mit dem Tool verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3df44-424">The Desktop App Converter does not support Unicode; thus, no Chinese characters or non-ASCII characters can be used with the tool.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3df44-425">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3df44-425">Next steps</span></span>

**<span data-ttu-id="3df44-426">Ausführer Ihrer App/Suchen und Beheben von Problemen</span><span class="sxs-lookup"><span data-stu-id="3df44-426">Run your app / find and fix issues</span></span>**

<span data-ttu-id="3df44-427">Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)</span><span class="sxs-lookup"><span data-stu-id="3df44-427">See [Run, debug, and test a packaged desktop app (Desktop Bridge)](desktop-to-uwp-debug.md)</span></span>

**<span data-ttu-id="3df44-428">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="3df44-428">Distribute your app</span></span>**

<span data-ttu-id="3df44-429">Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)</span><span class="sxs-lookup"><span data-stu-id="3df44-429">See [Distribute a packaged desktop app (Desktop Bridge)](desktop-to-uwp-distribute.md)</span></span>

**<span data-ttu-id="3df44-430">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="3df44-430">Find answers to specific questions</span></span>**

<span data-ttu-id="3df44-431">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="3df44-431">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="3df44-432">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="3df44-432">Give feedback about this article</span></span>**

<span data-ttu-id="3df44-433">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="3df44-433">Use the comments section below.</span></span>
