---
author: laurenhughes
title: Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“
description: MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln.
ms.author: lahugh
ms.date: 03/07/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, uwp, verpackung
ms.assetid: 7c1c3355-8bf7-4c9f-b13b-2b9874b7c63c
ms.localizationpriority: medium
ms.openlocfilehash: 94972915e5fc80a477d8d647212ab3b91e0aa384
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817791"
---
# <a name="create-an-app-package-with-the-makeappxexe-tool"></a><span data-ttu-id="bf924-104">Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“</span><span class="sxs-lookup"><span data-stu-id="bf924-104">Create an app package with the MakeAppx.exe tool</span></span>


<span data-ttu-id="bf924-105">**MakeAppx.exe** erstellt sowohl App-Pakete als auch App-Bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-105">**MakeAppx.exe** creates both app packages and app package bundles.</span></span> <span data-ttu-id="bf924-106">**MakeAppx.exe** extrahiert darüber hinaus Dateien aus einem App-Paket oder -Bündel und verschlüsselt und entschlüsselt App-Pakete und App-Bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-106">**MakeAppx.exe** also extracts files from an app package or bundle and encrypts or decrypts app packages and bundles.</span></span> <span data-ttu-id="bf924-107">Dieses Tool ist im Windows10 SDK enthalten und kann über eine Eingabeaufforderung oder eine Skriptdatei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf924-107">This tool is included in the Windows 10 SDK and can be used from a command prompt or a script file.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="bf924-108">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf924-108">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to create your app package.</span></span> <span data-ttu-id="bf924-109">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="bf924-109">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

<span data-ttu-id="bf924-110">Beachten Sie, dass **MakeAppx.exe** keine APPXUPLOAD-Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="bf924-110">Note that **MakeAppx.exe** does not create an .appxupload file.</span></span> <span data-ttu-id="bf924-111">Die APPXUPLOAD-Datei wird als Teil des Visual Studio-Verpackungsvorgangs erstellt und enthält zwei weitere Dateien: .appX- und .appxsym.</span><span class="sxs-lookup"><span data-stu-id="bf924-111">The .appxupload file is created as part of the Visual Studio packaging process and contains two other files: .appx and .appxsym.</span></span> <span data-ttu-id="bf924-112">Die APPXSYM-Datei ist eine komprimierte PDB-Datei und enthält öffentliche Symbole Ihrer App, die für [Absturzanalysen](https://blogs.windows.com/buildingapps/2015/07/13/crash-analysis-in-the-unified-dev-center/) im Windows Dev Center verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bf924-112">The .appxsym file is a compressed .pdb file containing public symbols of your app used for [crash analytics](https://blogs.windows.com/buildingapps/2015/07/13/crash-analysis-in-the-unified-dev-center/) in the Windows Dev Center.</span></span> <span data-ttu-id="bf924-113">Eine reguläre APPX-Datei kann ebenfalls übermittelt werden. In diesem Fall sind jedoch keine Absturzanalysen oder Informationen zum Debuggen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bf924-113">A regular .appx file can be submitted as well, but there will be no crash analytic or debugging information available.</span></span> <span data-ttu-id="bf924-114">Weitere Informationen zum Übermitteln von Paketen an den Store finden Sie unter [Hochladen von App-Paketen](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages).</span><span class="sxs-lookup"><span data-stu-id="bf924-114">For more information on submitting packages to the store, see [Upload app packages](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages).</span></span> 

<span data-ttu-id="bf924-115">So erstellen Sie manuell eine APPXUPLOAD-Datei:</span><span class="sxs-lookup"><span data-stu-id="bf924-115">To manually create an .appxupload file:</span></span>
- <span data-ttu-id="bf924-116">Speichern Sie die APPX- und die APPXSYM-Datei in einem Ordner.</span><span class="sxs-lookup"><span data-stu-id="bf924-116">Place the .appx and the .appxsym in a folder</span></span>
- <span data-ttu-id="bf924-117">Zippen Sie den Ordner.</span><span class="sxs-lookup"><span data-stu-id="bf924-117">Zip the folder</span></span>
- <span data-ttu-id="bf924-118">Ändern Sie den Namen der Erweiterung des komprimierten Ordners von ZIP in APPXUPLOAD.</span><span class="sxs-lookup"><span data-stu-id="bf924-118">Change the zipped folder extension name from .zip to .appxupload</span></span>

## <a name="using-makeappxexe"></a><span data-ttu-id="bf924-119">Verwenden der MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="bf924-119">Using MakeAppx.exe</span></span>

<span data-ttu-id="bf924-120">Abhängig vom Installationspfad des SDK befindet sich **MakeAppx.exe** an folgenden Speicherorten auf Ihrem Windows10-PC:</span><span class="sxs-lookup"><span data-stu-id="bf924-120">Based on your installation path of the SDK, this is where **MakeAppx.exe** is on your Windows 10 PC:</span></span>
- <span data-ttu-id="bf924-121">x86: C:\Programme (x86)\Windows Kits\10\bin\x86\makeappx.exe</span><span class="sxs-lookup"><span data-stu-id="bf924-121">x86: C:\Program Files (x86)\Windows Kits\10\bin\x86\makeappx.exe</span></span>
- <span data-ttu-id="bf924-122">x64: C:\Programme (x86)\Windows Kits\10\bin\x64\makeappx.exe</span><span class="sxs-lookup"><span data-stu-id="bf924-122">x64: C:\Program Files (x86)\Windows Kits\10\bin\x64\makeappx.exe</span></span>

<span data-ttu-id="bf924-123">Es gibt keine ARM-Version dieses Tools.</span><span class="sxs-lookup"><span data-stu-id="bf924-123">There is no ARM version of this tool.</span></span>

### <a name="makeappxexe-syntax-and-options"></a><span data-ttu-id="bf924-124">MakeAppx.exe-Syntax und -Optionen</span><span class="sxs-lookup"><span data-stu-id="bf924-124">MakeAppx.exe syntax and options</span></span>

<span data-ttu-id="bf924-125">Allgemeine **MakeAppx.exe**-Syntax:</span><span class="sxs-lookup"><span data-stu-id="bf924-125">General **MakeAppx.exe** syntax:</span></span>

``` Usage
MakeAppx <command> [options]      
```

<span data-ttu-id="bf924-126">Die folgende Tabelle enthält die Befehle für **MakeAppx.exe**.</span><span class="sxs-lookup"><span data-stu-id="bf924-126">The following table describes the commands for **MakeAppx.exe**.</span></span>

| **<span data-ttu-id="bf924-127">Befehl</span><span class="sxs-lookup"><span data-stu-id="bf924-127">Command</span></span>**   | **<span data-ttu-id="bf924-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-128">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-129">pack</span><span class="sxs-lookup"><span data-stu-id="bf924-129">pack</span></span>          | <span data-ttu-id="bf924-130">Erstellt ein Paket.</span><span class="sxs-lookup"><span data-stu-id="bf924-130">Creates a package.</span></span>                    |
| <span data-ttu-id="bf924-131">unpack</span><span class="sxs-lookup"><span data-stu-id="bf924-131">unpack</span></span>        | <span data-ttu-id="bf924-132">Extrahiert alle Dateien im angegebenen Paket in das angegebene Ausgabeverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="bf924-132">Extracts all files in the specified package to the specified output directory.</span></span> |
| <span data-ttu-id="bf924-133">bundle</span><span class="sxs-lookup"><span data-stu-id="bf924-133">bundle</span></span>        | <span data-ttu-id="bf924-134">Erstellt ein Bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-134">Creates a bundle.</span></span>                     |
| <span data-ttu-id="bf924-135">unbundle</span><span class="sxs-lookup"><span data-stu-id="bf924-135">unbundle</span></span>      | <span data-ttu-id="bf924-136">Entpacken alle Pakete in ein Unterverzeichnis am angegebenen Ausgabepfad, der nach dem vollständigen Namen des Bündels benannt ist.</span><span class="sxs-lookup"><span data-stu-id="bf924-136">Unpacks all packages to a subdirectory under the specified output path named after the bundle full name.</span></span> |
| <span data-ttu-id="bf924-137">encrypt</span><span class="sxs-lookup"><span data-stu-id="bf924-137">encrypt</span></span>       | <span data-ttu-id="bf924-138">Erstellt ein verschlüsseltes App-Paket oder -Bündel aus dem Eingabepaket/-bündel am angegebenen Ausgabepaket/-bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-138">Creates an encrypted app package or bundle from the input package/bundle at the specified output package/bundle.</span></span> |
| <span data-ttu-id="bf924-139">decrypt</span><span class="sxs-lookup"><span data-stu-id="bf924-139">decrypt</span></span>       | <span data-ttu-id="bf924-140">Erstellt ein entschlüsseltes App-Paket oder -Bündel aus dem Eingabe-App-Paket/-Bündel am angegebenen Ausgabepaket/-bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-140">Creates an decrypted app package or bundle from the input app package/bundle at the specified output package/bundle.</span></span> |
| <span data-ttu-id="bf924-141">build</span><span class="sxs-lookup"><span data-stu-id="bf924-141">build</span></span>         |  |


<span data-ttu-id="bf924-142">Die folgende Liste von Optionen gilt für alle Befehle:</span><span class="sxs-lookup"><span data-stu-id="bf924-142">This list of options applies to all commands:</span></span>

| **<span data-ttu-id="bf924-143">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-143">Option</span></span>**    | **<span data-ttu-id="bf924-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-144">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-145">/d</span><span class="sxs-lookup"><span data-stu-id="bf924-145">/d</span></span>            | <span data-ttu-id="bf924-146">Gibt das Eingabe-, Ausgabe- oder Inhaltsverzeichnis an.</span><span class="sxs-lookup"><span data-stu-id="bf924-146">Specifies the input, output, or content directory.</span></span> |
| <span data-ttu-id="bf924-147">/l</span><span class="sxs-lookup"><span data-stu-id="bf924-147">/l</span></span>            | <span data-ttu-id="bf924-148">Wird für lokalisierte Pakete verwendet.</span><span class="sxs-lookup"><span data-stu-id="bf924-148">Used for localized packages.</span></span> <span data-ttu-id="bf924-149">Die Standardüberprüfung wird durch lokalisierte Pakete ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="bf924-149">The default validation trips on localized packages.</span></span> <span data-ttu-id="bf924-150">Diese Option deaktiviert nur diese spezifische Überprüfung, ohne dass die gesamte Überprüfung deaktiviert werden muss.</span><span class="sxs-lookup"><span data-stu-id="bf924-150">This options disables only that specific validation, without requiring that all validation be disabled.</span></span> |
| <span data-ttu-id="bf924-151">/kf</span><span class="sxs-lookup"><span data-stu-id="bf924-151">/kf</span></span>           | <span data-ttu-id="bf924-152">Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des Schlüssels aus der angegebenen Schlüsseldatei.</span><span class="sxs-lookup"><span data-stu-id="bf924-152">Encrypts or decrypts the package or bundle using the key from the specified key file.</span></span> <span data-ttu-id="bf924-153">Diese Option kann nicht mit /kt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf924-153">This can't be used with /kt.</span></span> |
| <span data-ttu-id="bf924-154">/kt</span><span class="sxs-lookup"><span data-stu-id="bf924-154">/kt</span></span>           | <span data-ttu-id="bf924-155">Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des globalen Testschlüssels.</span><span class="sxs-lookup"><span data-stu-id="bf924-155">Encrypts the or decrypts package or bundle using the global test key.</span></span> <span data-ttu-id="bf924-156">Diese Option kann nicht mit /kf verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf924-156">This can't be used with /kf.</span></span> |
| <span data-ttu-id="bf924-157">/no</span><span class="sxs-lookup"><span data-stu-id="bf924-157">/no</span></span>           | <span data-ttu-id="bf924-158">Verhindert ein Überschreiben der Ausgabedatei, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="bf924-158">Prevents an overwrite of the output file if it exists.</span></span> <span data-ttu-id="bf924-159">Wenn Sie diese Option oder die Option /o nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="bf924-159">If you don't specify this option or the /o option, the user is asked whether they want to overwrite the file.</span></span> |
| <span data-ttu-id="bf924-160">/nv</span><span class="sxs-lookup"><span data-stu-id="bf924-160">/nv</span></span>           | <span data-ttu-id="bf924-161">Überspringt die semantische Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="bf924-161">Skips semantic validation.</span></span> <span data-ttu-id="bf924-162">Wenn Sie diese Option nicht angeben, führt das Tool eine vollständige Überprüfung des Pakets aus.</span><span class="sxs-lookup"><span data-stu-id="bf924-162">If you don't specify this option, the tool performs a full validation of the package.</span></span> |
| <span data-ttu-id="bf924-163">/o</span><span class="sxs-lookup"><span data-stu-id="bf924-163">/o</span></span>            | <span data-ttu-id="bf924-164">Überschreibt die Ausgabedatei, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="bf924-164">Overwrites the output file if it exists.</span></span> <span data-ttu-id="bf924-165">Wenn Sie diese Option oder die Option /no nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="bf924-165">If you don't specify this option or the /no option, the user is asked whether they want to overwrite the file.</span></span> |
| <span data-ttu-id="bf924-166">/p</span><span class="sxs-lookup"><span data-stu-id="bf924-166">/p</span></span>            | <span data-ttu-id="bf924-167">Gibt das App-Paket oder -Bündel an.</span><span class="sxs-lookup"><span data-stu-id="bf924-167">Specifies the app package or bundle.</span></span>  |
| <span data-ttu-id="bf924-168">/v</span><span class="sxs-lookup"><span data-stu-id="bf924-168">/v</span></span>            | <span data-ttu-id="bf924-169">Aktiviert die ausführliche Protokollierungsausgabe an die Konsole.</span><span class="sxs-lookup"><span data-stu-id="bf924-169">Enables verbose logging output to the console.</span></span> |
| <span data-ttu-id="bf924-170">/?</span><span class="sxs-lookup"><span data-stu-id="bf924-170">/?</span></span>            | <span data-ttu-id="bf924-171">Zeigt Hilfetext an.</span><span class="sxs-lookup"><span data-stu-id="bf924-171">Displays help text.</span></span>                   |


<span data-ttu-id="bf924-172">Die folgende Liste enthält mögliche Argumente:</span><span class="sxs-lookup"><span data-stu-id="bf924-172">The following list contains possible arguments:</span></span>

| **<span data-ttu-id="bf924-173">Argument</span><span class="sxs-lookup"><span data-stu-id="bf924-173">Argument</span></span>**                          | **<span data-ttu-id="bf924-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-174">Description</span></span>**                       |
|---------------------------------------|---------------------------------------|
| <span data-ttu-id="bf924-175">&lt;output package name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-175">&lt;output package name&gt;</span></span>           | <span data-ttu-id="bf924-176">Der Name des erstellten Pakets.</span><span class="sxs-lookup"><span data-stu-id="bf924-176">The name of the package created.</span></span> <span data-ttu-id="bf924-177">Dies ist der Dateiname mit der angehängten Erweiterung .appx.</span><span class="sxs-lookup"><span data-stu-id="bf924-177">This is the file name appended with .appx.</span></span> |
| <span data-ttu-id="bf924-178">&lt;encrypted output package name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-178">&lt;encrypted output package name&gt;</span></span> | <span data-ttu-id="bf924-179">Der Name des erstellten verschlüsselten Pakets.</span><span class="sxs-lookup"><span data-stu-id="bf924-179">The name of the encrypted package created.</span></span> <span data-ttu-id="bf924-180">Dies ist der Dateiname mit der angehängten Erweiterung .eappx.</span><span class="sxs-lookup"><span data-stu-id="bf924-180">This is the file name appended with .eappx.</span></span> |
| <span data-ttu-id="bf924-181">&lt;input package name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-181">&lt;input package name&gt;</span></span>            | <span data-ttu-id="bf924-182">Der Name des Pakets.</span><span class="sxs-lookup"><span data-stu-id="bf924-182">The name of the package.</span></span> <span data-ttu-id="bf924-183">Dies ist der Dateiname mit der angehängten Erweiterung .appx.</span><span class="sxs-lookup"><span data-stu-id="bf924-183">This is the file name appended with .appx.</span></span> |
| <span data-ttu-id="bf924-184">&lt;encrypted input package name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-184">&lt;encrypted input package name&gt;</span></span>  | <span data-ttu-id="bf924-185">Der Name des verschlüsselten Pakets.</span><span class="sxs-lookup"><span data-stu-id="bf924-185">The name of the encrypted package.</span></span> <span data-ttu-id="bf924-186">Dies ist der Dateiname mit der angehängten Erweiterung .eappx.</span><span class="sxs-lookup"><span data-stu-id="bf924-186">This is the file name appended with .eappx.</span></span> |
| <span data-ttu-id="bf924-187">&lt;output bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-187">&lt;output bundle name&gt;</span></span>            | <span data-ttu-id="bf924-188">Der Name des erstellten Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-188">The name of the bundle created.</span></span> <span data-ttu-id="bf924-189">Dies ist der Dateiname mit der angehängten Erweiterung .appxbundle.</span><span class="sxs-lookup"><span data-stu-id="bf924-189">This is the file name appended with .appxbundle.</span></span> |
| <span data-ttu-id="bf924-190">&lt;encrypted output bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-190">&lt;encrypted output bundle name&gt;</span></span>  | <span data-ttu-id="bf924-191">Der Name des erstellten verschlüsselten Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-191">The name of the encrypted bundle created.</span></span> <span data-ttu-id="bf924-192">Dies ist der Dateiname mit der angehängten Erweiterung .eappxbundle.</span><span class="sxs-lookup"><span data-stu-id="bf924-192">This is the file name appended with .eappxbundle.</span></span> |
| <span data-ttu-id="bf924-193">&lt;input bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-193">&lt;input bundle name&gt;</span></span>             | <span data-ttu-id="bf924-194">Der Name des Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-194">The name of the bundle.</span></span> <span data-ttu-id="bf924-195">Dies ist der Dateiname mit der angehängten Erweiterung .appxbundle.</span><span class="sxs-lookup"><span data-stu-id="bf924-195">This is the file name appended with .appxbundle.</span></span> |
| <span data-ttu-id="bf924-196">&lt;encrypted input bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-196">&lt;encrypted input bundle name&gt;</span></span>   | <span data-ttu-id="bf924-197">Der Name des verschlüsselten Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-197">The name of the encrypted bundle.</span></span> <span data-ttu-id="bf924-198">Dies ist der Dateiname mit der angehängten Erweiterung .eappxbundle.</span><span class="sxs-lookup"><span data-stu-id="bf924-198">This is the file name appended with .eappxbundle.</span></span> |
| <span data-ttu-id="bf924-199">&lt;content directory&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-199">&lt;content directory&gt;</span></span>             | <span data-ttu-id="bf924-200">Der Pfad für den Inhalt des App-Pakets oder -Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-200">Path for the app package or bundle content.</span></span> |
| <span data-ttu-id="bf924-201">&lt;mapping file&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-201">&lt;mapping file&gt;</span></span>                  | <span data-ttu-id="bf924-202">Der Name der Datei, der Paketquelle und -ziel angibt.</span><span class="sxs-lookup"><span data-stu-id="bf924-202">File name that specifies the package source and destination.</span></span> |
| <span data-ttu-id="bf924-203">&lt;output directory&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-203">&lt;output directory&gt;</span></span>              | <span data-ttu-id="bf924-204">Der Pfad zum Verzeichnis für Ausgabepakete und -bündel.</span><span class="sxs-lookup"><span data-stu-id="bf924-204">Path to the directory for output packages and bundles.</span></span> |
| <span data-ttu-id="bf924-205">&lt;key file&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-205">&lt;key file&gt;</span></span>                      | <span data-ttu-id="bf924-206">Der Name der Datei mit einem Schlüssel für die Verschlüsselung oder Entschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="bf924-206">Name of the file containing a key for encryption or decryption.</span></span> |
| <span data-ttu-id="bf924-207">&lt;algorithm ID&gt;</span><span class="sxs-lookup"><span data-stu-id="bf924-207">&lt;algorithm ID&gt;</span></span>                  | <span data-ttu-id="bf924-208">Die beim Erstellen einer Blockzuordnung verwendeten Algorithmen.</span><span class="sxs-lookup"><span data-stu-id="bf924-208">Algorithms used when creating a block map.</span></span> <span data-ttu-id="bf924-209">Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512.</span><span class="sxs-lookup"><span data-stu-id="bf924-209">Valid algorithms include: SHA256 (default), SHA384, SHA512.</span></span> |


### <a name="create-an-app-package"></a><span data-ttu-id="bf924-210">Erstellen eines App-Pakets</span><span class="sxs-lookup"><span data-stu-id="bf924-210">Create an app package</span></span>

<span data-ttu-id="bf924-211">Ein App-Paket ist ein vollständiger Satz der App-Dateien, verpackt in einer APPX-Paketdatei.</span><span class="sxs-lookup"><span data-stu-id="bf924-211">An app package is a complete set of the app's files packaged in to an .appx package file.</span></span> <span data-ttu-id="bf924-212">Um ein App-Paket mit dem Befehl **pack** zu erstellen, müssen Sie entweder ein Inhaltsverzeichnis oder eine Zuordnungsdati für den Speicherort des Pakets angeben.</span><span class="sxs-lookup"><span data-stu-id="bf924-212">To create an app package using the **pack** command, you must provide either a content directory or a mapping file for the location of the package.</span></span> <span data-ttu-id="bf924-213">Sie können ein Paket auch während des Erstellens verschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="bf924-213">You can also encrypt a package while creating it.</span></span> <span data-ttu-id="bf924-214">Wenn Sie das Paket verschlüsseln möchten, müssen Sie /ep verwenden und angeben, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf924-214">If you want to encrypt the package, you must use /ep and specify if you are using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="bf924-215">Weitere Informationen zum Erstellen eines verschlüsselten Pakets finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="bf924-215">For more information on creating an encrypted package, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="bf924-216">Optionen, die für den Befehl **pack** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bf924-216">Options specific to the **pack** command:</span></span>

| **<span data-ttu-id="bf924-217">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-217">Option</span></span>**    | **<span data-ttu-id="bf924-218">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-218">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-219">/f</span><span class="sxs-lookup"><span data-stu-id="bf924-219">/f</span></span>            | <span data-ttu-id="bf924-220">Gibt die Zuordnungsdatei an.</span><span class="sxs-lookup"><span data-stu-id="bf924-220">Specifies the mapping file.</span></span>           |
| <span data-ttu-id="bf924-221">/h</span><span class="sxs-lookup"><span data-stu-id="bf924-221">/h</span></span>            | <span data-ttu-id="bf924-222">Gibt den Hashalgorithmus an, der beim Erstellen der Blockzuordnung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bf924-222">Specifies the hash algorithm to use when creating the block map.</span></span> <span data-ttu-id="bf924-223">Diese Option kann nur mit den pack-Befehl verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bf924-223">This can only be used with the pack command.</span></span> <span data-ttu-id="bf924-224">Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512.</span><span class="sxs-lookup"><span data-stu-id="bf924-224">Valid algorithms include: SHA256 (default), SHA384, SHA512.</span></span> |
| <span data-ttu-id="bf924-225">/m</span><span class="sxs-lookup"><span data-stu-id="bf924-225">/m</span></span>            | <span data-ttu-id="bf924-226">Gibt den Pfad zu einem Eingabe App-Manifest an, das als Grundlage für das Generieren des Ausgabe-App-Pakets oder des Manifests des Ressourcenpakets verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bf924-226">Specifies the path to an input app manifest which will be used as the basis for generating the output app package or resource package's manifest.</span></span>  <span data-ttu-id="bf924-227">Wenn Sie diese Option verwenden, müssen Sie auch /f verwenden und einen [ResourceMetadata]-Abschnitt in die Zuordnungsdatei einfügen, um die Ressourcendimensionen anzugeben, die im generierten Manifest enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="bf924-227">When you use this option, you must also use /f and include a [ResourceMetadata] section in the mapping file to specify the resource dimensions to be included in the generated manifest.</span></span>|
| <span data-ttu-id="bf924-228">/nc</span><span class="sxs-lookup"><span data-stu-id="bf924-228">/nc</span></span>           | <span data-ttu-id="bf924-229">Verhindert die Komprimierung der Paketdateien.</span><span class="sxs-lookup"><span data-stu-id="bf924-229">Prevents compression of the package files.</span></span> <span data-ttu-id="bf924-230">Standardmäßig werden Dateien basierend auf dem erkannten Dateityp komprimiert.</span><span class="sxs-lookup"><span data-stu-id="bf924-230">By default, files are compressed based on detected file type.</span></span> |
| <span data-ttu-id="bf924-231">/r</span><span class="sxs-lookup"><span data-stu-id="bf924-231">/r</span></span>            | <span data-ttu-id="bf924-232">Erstellt ein Ressourcenpaket.</span><span class="sxs-lookup"><span data-stu-id="bf924-232">Builds a resource package.</span></span> <span data-ttu-id="bf924-233">Diese Option muss mit /m verwendet werden und impliziert die Verwendung der Option /l.</span><span class="sxs-lookup"><span data-stu-id="bf924-233">This must be used with /m and implies the use of the /l option.</span></span> |  


<span data-ttu-id="bf924-234">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **pack**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="bf924-234">The following usage examples show some possible syntax options for the **pack** command:</span></span>

``` syntax 
MakeAppx pack [options] /d <content directory> /p <output package name>
MakeAppx pack [options] /f <mapping file> /p <output package name>
MakeAppx pack [options] /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /r /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kf <key file>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kt

```
<span data-ttu-id="bf924-235">Im Folgenden finden Sie Befehlszeilenbeispiele für den **pack**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="bf924-235">The following shows command line examples for the **pack** command:</span></span>

``` examples
MakeAppx pack /v /h SHA256 /d "C:\My Files" /p MyPackage.appx
MakeAppx pack /v /o /f MyMapping.txt /p MyPackage.appx
MakeAppx pack /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p AppPackage.appx
MakeAppx pack /r /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p ResourcePackage.appx
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.eappx /kf MyKeyFile.txt
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.eappx /kt
```

### <a name="create-an-app-bundle"></a><span data-ttu-id="bf924-236">Erstellen eines App-Bündels</span><span class="sxs-lookup"><span data-stu-id="bf924-236">Create an app bundle</span></span>

<span data-ttu-id="bf924-237">Ein App-Bündel ist einem App-Paket vergleichbar. Ein Bündel kann jedoch die Größe der App reduzieren, die Benutzer herunterladen.</span><span class="sxs-lookup"><span data-stu-id="bf924-237">An app bundle is similar to an app package, but a bundle can reduce the size of the app that users download.</span></span> <span data-ttu-id="bf924-238">App-Bündel sind beispielsweise für sprachspezifische Ressourcen, Ressourcen mit unterschiedlichen Imagegrößen oder Ressourcen nützlich, die für spezifische Versionen von Microsoft DirectX gelten.</span><span class="sxs-lookup"><span data-stu-id="bf924-238">App bundles are helpful for language-specific assets, varying image-scale assets, or resources that apply to specific versions of Microsoft DirectX, for example.</span></span> <span data-ttu-id="bf924-239">Wie beim Erstellen verschlüsselter App-Pakete, können Sie auch App-Bündel beim Bündeln verschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="bf924-239">Similar to creating an encrypted app package, you can also encrypt the app bundle while bundling it.</span></span> <span data-ttu-id="bf924-240">Um das App-Bündel zu verschlüsseln, verwenden Sie die Option /ep und geben an, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf924-240">To encrypt the app bundle, use the /ep option and specify if you are using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="bf924-241">Weitere Informationen zum Erstellen eines verschlüsselten Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="bf924-241">For more information on creating an encrypted bundle, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="bf924-242">Optionen, die für den **bundle**-Befehl spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bf924-242">Options specific to the **bundle** command:</span></span>

| **<span data-ttu-id="bf924-243">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-243">Option</span></span>**    | **<span data-ttu-id="bf924-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-244">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-245">/bv</span><span class="sxs-lookup"><span data-stu-id="bf924-245">/bv</span></span>           | <span data-ttu-id="bf924-246">Gibt die Versionsnummer des Bündels an.</span><span class="sxs-lookup"><span data-stu-id="bf924-246">Specifies the version number of the bundle.</span></span> <span data-ttu-id="bf924-247">Die Versionsnummer muss aus vier Teilen bestehen, getrennt durch Punkte: &lt;Hauptversion&gt;.&lt;Unterversion&gt;.&lt;Build&gt;.&lt;Überarbeitung&gt;.</span><span class="sxs-lookup"><span data-stu-id="bf924-247">The version number must be in four parts separated by periods in the form: &lt;Major&gt;.&lt;Minor&gt;.&lt;Build&gt;.&lt;Revision&gt;.</span></span> |
| <span data-ttu-id="bf924-248">/f</span><span class="sxs-lookup"><span data-stu-id="bf924-248">/f</span></span>            | <span data-ttu-id="bf924-249">Gibt die Zuordnungsdatei an.</span><span class="sxs-lookup"><span data-stu-id="bf924-249">Specifies the mapping file.</span></span>           |

<span data-ttu-id="bf924-250">Beachten Sie, dass die Bündelversion mit dem aktuellen Datum und der aktuellen Uhrzeit erstellt wird, wenn die Bündelversion nicht angegeben oder auf „0.0.0.0“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="bf924-250">Note that if the bundle version is not specified or if it is set to "0.0.0.0" the bundle is created using the current date-time.</span></span>

<span data-ttu-id="bf924-251">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **bundle**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="bf924-251">The following usage examples show some possible syntax options for the **bundle** command:</span></span>

``` syntax
MakeAppx bundle [options] /d <content directory> /p <output bundle name>
MakeAppx bundle [options] /f <mapping file> /p <output bundle name>
MakeAppx bundle [options] /d <content directory> /ep <encrypted output bundle name> /kf MyKeyFile.txt
MakeAppx bundle [options] /f <mapping file> /ep <encrypted output bundle name> /kt
```
<span data-ttu-id="bf924-252">Der folgende Block enthält Beispiele für den **bundle** Befehl:</span><span class="sxs-lookup"><span data-stu-id="bf924-252">The following block contains examples for the **bundle** command:</span></span>

``` examples
MakeAppx bundle /v /d "C:\My Files" /p MyBundle.appxbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /p MyBundle.appxbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.eappxbundle /kf MyKeyFile.txt
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.eappxbundle /kt
```

### <a name="extract-files-from-a-package-or-bundle"></a><span data-ttu-id="bf924-253">Extrahieren von Dateien aus einem Paket oder Bündel</span><span class="sxs-lookup"><span data-stu-id="bf924-253">Extract files from a package or bundle</span></span>

<span data-ttu-id="bf924-254">Zusätzlich zum Packen und Bündeln von Apps kann **MakeAppx.exe** vorhandene Pakete entpacken oder entbündeln.</span><span class="sxs-lookup"><span data-stu-id="bf924-254">In addition to packaging and bundling apps, **MakeAppx.exe** can also unpack or unbundle existing packages.</span></span> <span data-ttu-id="bf924-255">Sie müssen als Ziel für die extrahierten Dateien das Inhaltsverzeichnis angeben.</span><span class="sxs-lookup"><span data-stu-id="bf924-255">You must provide the content directory as a destination for the extracted files.</span></span> <span data-ttu-id="bf924-256">Wenn Sie versuchen, Dateien aus einem verschlüsselten Paket oder Bündel zu extrahieren, können Sie die Dateien gleichzeitig entschlüsseln und extrahieren, indem Sie die Option /ep verwenden und angeben, ob sie mit einer Schlüsseldatei (/kf) oder dem globalen Testschlüssel (/kt) entschlüsselt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bf924-256">If you are trying to extract files from an encrypted package or bundle, you can decrypt and extract the files at the same time using the /ep option and specifying whether it should be decrypted using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="bf924-257">Weitere Informationen zum Entschlüsseln eines Pakets oder Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="bf924-257">For more information on decrypting a package or bundle, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="bf924-258">Optionen, die für die Befehle **unpack** und **unbundle** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bf924-258">Options specific to **unpack** and **unbundle** commands:</span></span>

| **<span data-ttu-id="bf924-259">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-259">Option</span></span>**    | **<span data-ttu-id="bf924-260">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-260">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-261">/nd</span><span class="sxs-lookup"><span data-stu-id="bf924-261">/nd</span></span>           | <span data-ttu-id="bf924-262">Führt beim Entpacken oder Entbündeln des Pakets/Bündels keine Entschlüsselung aus.</span><span class="sxs-lookup"><span data-stu-id="bf924-262">Does not perform decryption when unpacking or unbundling the package/bundle.</span></span> |
| <span data-ttu-id="bf924-263">/pfn</span><span class="sxs-lookup"><span data-stu-id="bf924-263">/pfn</span></span>          | <span data-ttu-id="bf924-264">Entpackt/entbündelt alle Dateien in ein Unterverzeichnis am angegebenen Ausgabepfad, benannt nach dem vollständigen Namen des Pakets oder Bündels.</span><span class="sxs-lookup"><span data-stu-id="bf924-264">Unpacks/unbundles all files to a subdirectory under the specified output path, named after the package or bundle full name</span></span> |

<span data-ttu-id="bf924-265">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **unpack** und **unbundle**:</span><span class="sxs-lookup"><span data-stu-id="bf924-265">The following usage examples show some possible syntax options for the **unpack** and **unbundle** commands:</span></span>

``` syntax
MakeAppx unpack [options] /p <input package name> /d <output directory>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kf <key file>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kt

MakeAppx unbundle [options] /p <input bundle name> /d <output directory>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kf <key file>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kt
```

<span data-ttu-id="bf924-266">Der folgende Block enthält Beispiele für die Verwendung der Befehle **unpack** und **unbundle**:</span><span class="sxs-lookup"><span data-stu-id="bf924-266">The following block contains examples for using the **unpack** and **unbundle** commands:</span></span>

``` examples
MakeAppx unpack /v /p MyPackage.appx /d "C:\My Files"
MakeAppx unpack /v /ep MyPackage.eappx /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unpack /v /ep MyPackage.eappx /d "C:\My Files" /kt

MakeAppx unbundle /v /p MyBundle.appxbundle /d "C:\My Files"
MakeAppx unbundle /v /ep MyBundle.eappxbundle /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unbundle /v /ep MyBundle.eappxbundle /d "C:\My Files" /kt
```

### <a name="encrypt-or-decrypt-a-package-or-bundle"></a><span data-ttu-id="bf924-267">Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels</span><span class="sxs-lookup"><span data-stu-id="bf924-267">Encrypt or decrypt a package or bundle</span></span>

<span data-ttu-id="bf924-268">Das **MakeAppx.exe**-Tool kann ein vorhandenes Paket oder Bündel auch verschlüsseln oder entschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="bf924-268">The **MakeAppx.exe** tool can also encrypt or decrypt an existing package or bundle.</span></span> <span data-ttu-id="bf924-269">Sie müssen lediglich den Paketnamen und den Ausgabepaketnamen angeben und ob die Verschlüsselung oder Entschlüsselung eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="bf924-269">You must simply provide the package name, the output package name, and whether encryption or decryption should use a key file (/kf) or the global test key (/kt).</span></span>

<span data-ttu-id="bf924-270">Verschlüsselung und Entschlüsselung sind nicht über den Verpackungs-Assistenten von Visual Studio verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bf924-270">Encryption and decryption are not available through the Visual Studio packaging wizard.</span></span> 

<span data-ttu-id="bf924-271">Optionen, die für die Befehle **encrypt** und **decrypt** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bf924-271">Options specific to **encrypt** and **decrypt** commands:</span></span>

| **<span data-ttu-id="bf924-272">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-272">Option</span></span>**    | **<span data-ttu-id="bf924-273">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-273">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-274">/ep</span><span class="sxs-lookup"><span data-stu-id="bf924-274">/ep</span></span>           | <span data-ttu-id="bf924-275">Gibt ein verschlüsseltes App-Paket oder -Bündel an.</span><span class="sxs-lookup"><span data-stu-id="bf924-275">Specifies an encrypted app package or bundle.</span></span> |

<span data-ttu-id="bf924-276">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **encrypt** und **decrypt**:</span><span class="sxs-lookup"><span data-stu-id="bf924-276">The following usage examples show some possible syntax options for the **encrypt** and **decrypt** commands:</span></span>

``` syntax
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kf <key file>
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kt

MakeAppx decrypt [options] /ep <package name> /p <output package name> /kf <key file>
MakeAppx decrypt [options] /ep <package name> /p <output package name> /kt
```

<span data-ttu-id="bf924-277">Der folgende Block enthält Beispiele für die Verwendung der Befehle **encrypt** und **decrypt**:</span><span class="sxs-lookup"><span data-stu-id="bf924-277">The following block contains examples for using the **encrypt** and **decrypt** commands:</span></span>

``` examples
MakeAppx.exe encrypt /p MyPackage.appx /ep MyEncryptedPackage.eappx /kt
MakeAppx.exe encrypt /p MyPackage.appx /ep MyEncryptedPackage.eappx /kf MyKeyFile.txt

MakeAppx.exe decrypt /p MyPackage.appx /ep MyEncryptedPackage.eappx /kt
MakeAppx.exe decrypt p MyPackage.appx /ep MyEncryptedPackage.eappx /kf MyKeyFile.txt
```

### <a name="build-an-app-package"></a><span data-ttu-id="bf924-278">Erstellen eines App-Pakets</span><span class="sxs-lookup"><span data-stu-id="bf924-278">Build an app package</span></span> 

<span data-ttu-id="bf924-279">**MakeAppx.exe** kann eine App basierend auf der Paketlayoutdatei der App erstellen.</span><span class="sxs-lookup"><span data-stu-id="bf924-279">**MakeAppx.exe** can build an app based on it's app package layout file.</span></span> <span data-ttu-id="bf924-280">Weitere Informationen zum Erstellen einer Paketlayoutdatei und zum Verwenden von **MakeAppx.exe** zum Erstellen finden Sie unter [Erstellen eines Pakets mit dem Verpackungslayout](packaging-layout.md).</span><span class="sxs-lookup"><span data-stu-id="bf924-280">To learn how to create a package layout file and how to use **MakeAppx.exe** to build it, see [Package creation with the packaging layout](packaging-layout.md).</span></span>  

<span data-ttu-id="bf924-281">Optionen, die für den **build**-Befehl spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bf924-281">Options specific to the **build** command:</span></span>

| **<span data-ttu-id="bf924-282">Option</span><span class="sxs-lookup"><span data-stu-id="bf924-282">Option</span></span>**    | **<span data-ttu-id="bf924-283">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bf924-283">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="bf924-284">/bc</span><span class="sxs-lookup"><span data-stu-id="bf924-284">/bc</span></span>           | <span data-ttu-id="bf924-285">Gibt die untergeordneten Pakete in einer zu erstellenden Paketfamilie an.</span><span class="sxs-lookup"><span data-stu-id="bf924-285">Specifies the sub-packages in a package family to be built.</span></span>  |
| <span data-ttu-id="bf924-286">/id</span><span class="sxs-lookup"><span data-stu-id="bf924-286">/id</span></span>           | <span data-ttu-id="bf924-287">Wird verwendet, um die auf Grundlage des **ID**-Attributs zu erstellenden Pakete auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="bf924-287">Used to select packages to be built based on the package **ID** attribute.</span></span> |
| <span data-ttu-id="bf924-288">/ip</span><span class="sxs-lookup"><span data-stu-id="bf924-288">/ip</span></span>           | <span data-ttu-id="bf924-289">Gibt den Speicherort von früheren Versionen eines App-Pakets an.</span><span class="sxs-lookup"><span data-stu-id="bf924-289">Indicates the location of previous versions of an app package.</span></span> |
| <span data-ttu-id="bf924-290">/iv</span><span class="sxs-lookup"><span data-stu-id="bf924-290">/iv</span></span>           | <span data-ttu-id="bf924-291">Erhöht automatisch die Version der zu erstellenden Pakete.</span><span class="sxs-lookup"><span data-stu-id="bf924-291">Automatically increments the version of the packages being built.</span></span> |
| <span data-ttu-id="bf924-292">/f</span><span class="sxs-lookup"><span data-stu-id="bf924-292">/f</span></span>            | <span data-ttu-id="bf924-293">Gibt die Verpackungslayoutdatei an.</span><span class="sxs-lookup"><span data-stu-id="bf924-293">Specifies the packaging layout file.</span></span> |
| <span data-ttu-id="bf924-294">/nbp</span><span class="sxs-lookup"><span data-stu-id="bf924-294">/nbp</span></span>          | <span data-ttu-id="bf924-295">Gibt an, dass ein App-Paket nicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bf924-295">Indicates that an app package should not be built.</span></span> |
| <span data-ttu-id="bf924-296">/op</span><span class="sxs-lookup"><span data-stu-id="bf924-296">/op</span></span>           | <span data-ttu-id="bf924-297">Das Ziel des Ausgabepakets.</span><span class="sxs-lookup"><span data-stu-id="bf924-297">The output package destination.</span></span> |

## <a name="key-files"></a><span data-ttu-id="bf924-298">Schlüsseldateien</span><span class="sxs-lookup"><span data-stu-id="bf924-298">Key files</span></span>

<span data-ttu-id="bf924-299">Schlüsseldateien müssen mit einer Zeile beginnen, die die Zeichenfolge „[Keys]“ enthält, gefolgt von Zeilen, die die Schlüssel beschreiben, mit denen die einzelnen Pakete verschlüsselt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bf924-299">Key files must begin with a line containing the string "[Keys]" followed by lines describing the keys to encrypt each package with.</span></span> <span data-ttu-id="bf924-300">Jeder Schlüssel wird durch ein Paar von Zeichenfolgen in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, dargestellt.</span><span class="sxs-lookup"><span data-stu-id="bf924-300">Each key is represented by a pair of strings in quotation marks, separated by either spaces or tabs.</span></span> <span data-ttu-id="bf924-301">Die erste Zeichenfolge stellt die base64-codierte 32-Byte-Schlüssel-ID dar. Die zweite Zeichenfolge stellt den base64-codierten 32-Byte-Verschlüsselungsschlüssel dar.</span><span class="sxs-lookup"><span data-stu-id="bf924-301">The first string represents the base64 encoded 32-byte key ID and the second represents the base64 encoded 32-byte encryption key.</span></span> <span data-ttu-id="bf924-302">Eine Schlüsseldatei sollte eine einfache Textdatei sein.</span><span class="sxs-lookup"><span data-stu-id="bf924-302">A key file should be a simple text file.</span></span>

<span data-ttu-id="bf924-303">Beispiel für eine Schlüsseldatei:</span><span class="sxs-lookup"><span data-stu-id="bf924-303">Example of a key file:</span></span>

``` Example
[Keys]
"OWVwSzliRGY1VWt1ODk4N1Q4R2Vqc04zMzIzNnlUREU="    "MjNFTlFhZGRGZEY2YnVxMTBocjd6THdOdk9pZkpvelc="
```

## <a name="mapping-files"></a><span data-ttu-id="bf924-304">Zuordnungsdateien</span><span class="sxs-lookup"><span data-stu-id="bf924-304">Mapping files</span></span>
<span data-ttu-id="bf924-305">Zuordnungsdateien müssen mit einer Zeile beginnen, die Zeichenfolge „[Files]“ enthält, gefolgt von Zeilen, die die Dateien beschreiben, die dem Paket hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bf924-305">Mapping files must begin with a line containing the string "[Files]" followed by lines describing the files to add to the package.</span></span> <span data-ttu-id="bf924-306">Jede Datei wird durch ein Paar von Pfaden in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bf924-306">Each file is described by a pair of paths in quotation marks, separated by either spaces or tabs.</span></span> <span data-ttu-id="bf924-307">Jede Datei stellt Quelle (auf der Festplatte) und Ziel (im Paket) dar.</span><span class="sxs-lookup"><span data-stu-id="bf924-307">Each file represents its source (on disk) and destination (in the package).</span></span> <span data-ttu-id="bf924-308">Eine Zuordnungsdatei sollte eine einfache Textdatei sein.</span><span class="sxs-lookup"><span data-stu-id="bf924-308">A mapping file should be a simple text file.</span></span>

<span data-ttu-id="bf924-309">Beispiel für eine Zuordnungsdatei (ohne Option /m):</span><span class="sxs-lookup"><span data-stu-id="bf924-309">Example of a mapping file (without the /m option):</span></span>

``` Example
[Files]
"C:\MyApp\StartPage.html"               "default.html"
"C:\Program Files (x86)\example.txt"    "misc\example.txt"
"\\MyServer\path\icon.png"              "icon.png"
"my app files\readme.txt"               "my app files\readme.txt"
"CustomManifest.xml"                    "AppxManifest.xml"
``` 

<span data-ttu-id="bf924-310">Wenn Sie eine Zuordnungsdatei verwenden, können Sie wählen, ob Sie die Option /m verwenden möchten oder nicht.</span><span class="sxs-lookup"><span data-stu-id="bf924-310">When using a mapping file, you can choose whether you would like to use the /m option.</span></span> <span data-ttu-id="bf924-311">Mithilfe der Option /m können Benutzer die Ressourcenmetadaten in der Zuordnungsdatei angeben, die im generierten Manifest eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bf924-311">The /m option allows the user to specify the resource metadata in the mapping file to be included in the generated manifest.</span></span> <span data-ttu-id="bf924-312">Wenn Sie die Option /m verwenden, muss die Zuordnungsdatei einen Abschnittenthalten, der mit der Zeile „[ResourceMetadata]“ beginnt, gefolgt von Zeilen, die „ResourceDimensions“ und „ResourceId“ angeben.</span><span class="sxs-lookup"><span data-stu-id="bf924-312">If you use the /m option, the mapping file must contain a section that begins with the line "[ResourceMetadata]", followed by lines that specify "ResourceDimensions" and "ResourceId."</span></span> <span data-ttu-id="bf924-313">App-Pakete können mehrere „ResourceDimensions“ enthalten kann, jedoch stets nur eine „ResourceId“.</span><span class="sxs-lookup"><span data-stu-id="bf924-313">It is possible for an app package to contain multiple "ResourceDimensions", but there can only ever be one "ResourceId."</span></span>

<span data-ttu-id="bf924-314">Beispiel für eine Zuordnungsdatei (mit Option /m):</span><span class="sxs-lookup"><span data-stu-id="bf924-314">Example of a mapping file (with the /m option):</span></span>

``` Example
[ResourceMetadata]
"ResourceDimensions"                    "language-en-us"
"ResourceId"                            "English"

[Files]
"images\en-us\logo.png"                 "en-us\logo.png"
"en-us.pri"                             "resources.pri"
```

## <a name="semantic-validation-performed-by-makeappxexe"></a><span data-ttu-id="bf924-315">Semantische Überprüfung durch MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="bf924-315">Semantic validation performed by MakeAppx.exe</span></span>

<span data-ttu-id="bf924-316">**MakeAppx.exe** führt eine begrenzte semantische Überprüfung aus, um die häufigsten Bereitstellungsfehler zu erfassen und sicherzustellen, dass das App-Paket gültig ist.</span><span class="sxs-lookup"><span data-stu-id="bf924-316">**MakeAppx.exe** performs limited sematic validation that is designed to catch the most common deployment errors and help ensure that the app package is valid.</span></span> <span data-ttu-id="bf924-317">Verwenden Sie die Option /nv, wenn Sie beim Verwenden von **MakeAppx.exe**  die Überprüfung auslassen möchten.</span><span class="sxs-lookup"><span data-stu-id="bf924-317">See the /nv option if you want to skip validation while using **MakeAppx.exe**.</span></span> 

<span data-ttu-id="bf924-318">Diese Überprüfung stellt Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="bf924-318">This validation ensures that:</span></span>
- <span data-ttu-id="bf924-319">Alle Dateien, auf die im Paketmanifest verwiesen wird, sind im App-Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="bf924-319">All files referenced in the package manifest are included in the app package.</span></span>
- <span data-ttu-id="bf924-320">Die Anwendung besitzt nicht zwei identische Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="bf924-320">An application does not have two identical keys.</span></span>
- <span data-ttu-id="bf924-321">Die Anwendung registriert sich nicht für ein untersagtes Protokoll aus der folgenden Liste: SMB, FILE, MS-WWA-WEB, MS-WWA.</span><span class="sxs-lookup"><span data-stu-id="bf924-321">An application does not register for a forbidden protocol from this list: SMB, FILE, MS-WWA-WEB, MS-WWA.</span></span> 

<span data-ttu-id="bf924-322">Dies ist keine vollständige semantische Überprüfung, da sie lediglich häufige Fehler erfassen soll.</span><span class="sxs-lookup"><span data-stu-id="bf924-322">This is not a complete semantic validation as it is only designed to catch common errors.</span></span> <span data-ttu-id="bf924-323">Es wird nicht garantiert, dass von **MakeAppx.exe** erstellte Pakete installiert werden können.</span><span class="sxs-lookup"><span data-stu-id="bf924-323">Packages built by **MakeAppx.exe** are not guaranteed to be installable.</span></span>