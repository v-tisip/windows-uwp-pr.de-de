---
author: laurenhughes
title: Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“
description: MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln.
ms.author: lahugh
ms.date: 06/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, uwp, verpackung
ms.assetid: 7c1c3355-8bf7-4c9f-b13b-2b9874b7c63c
ms.localizationpriority: medium
ms.openlocfilehash: dbde8f2f11276ded6ad0994a1cd52f7f12de229e
ms.sourcegitcommit: 4b97117d3aff38db89d560502a3c372f12bb6ed5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "5441058"
---
# <a name="create-an-app-package-with-the-makeappxexe-tool"></a><span data-ttu-id="6f887-104">Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“</span><span class="sxs-lookup"><span data-stu-id="6f887-104">Create an app package with the MakeAppx.exe tool</span></span>


<span data-ttu-id="6f887-105">**MakeAppx.exe** erstellt sowohl App-Pakete als auch App-Bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-105">**MakeAppx.exe** creates both app packages and app package bundles.</span></span> <span data-ttu-id="6f887-106">**MakeAppx.exe** extrahiert darüber hinaus Dateien aus einem App-Paket oder -Bündel und verschlüsselt und entschlüsselt App-Pakete und App-Bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-106">**MakeAppx.exe** also extracts files from an app package or bundle and encrypts or decrypts app packages and bundles.</span></span> <span data-ttu-id="6f887-107">Dieses Tool ist im Windows10 SDK enthalten und kann über eine Eingabeaufforderung oder eine Skriptdatei verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f887-107">This tool is included in the Windows 10 SDK and can be used from a command prompt or a script file.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="6f887-108">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="6f887-108">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to create your app package.</span></span> <span data-ttu-id="6f887-109">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="6f887-109">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

<span data-ttu-id="6f887-110">Beachten Sie, dass **MakeAppx.exe** keine APPXUPLOAD-Datei erstellt.</span><span class="sxs-lookup"><span data-stu-id="6f887-110">Note that **MakeAppx.exe** does not create an .appxupload file.</span></span> <span data-ttu-id="6f887-111">Die appxupload-Datei wird als Teil des Visual Studio-verpackungsvorgangs erstellt und enthält zwei weitere Dateien: .msix oder AppX- und appxsym.</span><span class="sxs-lookup"><span data-stu-id="6f887-111">The .appxupload file is created as part of the Visual Studio packaging process and contains two other files: .msix or .appx and .appxsym.</span></span> <span data-ttu-id="6f887-112">Die APPXSYM-Datei ist eine komprimierte PDB-Datei und enthält öffentliche Symbole Ihrer App, die für [Absturzanalysen](https://blogs.windows.com/buildingapps/2015/07/13/crash-analysis-in-the-unified-dev-center/) im Windows Dev Center verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6f887-112">The .appxsym file is a compressed .pdb file containing public symbols of your app used for [crash analytics](https://blogs.windows.com/buildingapps/2015/07/13/crash-analysis-in-the-unified-dev-center/) in the Windows Dev Center.</span></span> <span data-ttu-id="6f887-113">Eine reguläre APPX-Datei kann ebenfalls übermittelt werden. In diesem Fall sind jedoch keine Absturzanalysen oder Informationen zum Debuggen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6f887-113">A regular .appx file can be submitted as well, but there will be no crash analytic or debugging information available.</span></span> <span data-ttu-id="6f887-114">Weitere Informationen zum Übermitteln von Paketen an den Store finden Sie unter [Hochladen von App-Paketen](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages).</span><span class="sxs-lookup"><span data-stu-id="6f887-114">For more information on submitting packages to the store, see [Upload app packages](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages).</span></span> 

 <span data-ttu-id="6f887-115">Updates für dieses Tool in der neuesten Version von Windows 10 haben keinen Einfluss auf die AppX-Paket-Nutzung.</span><span class="sxs-lookup"><span data-stu-id="6f887-115">Updates to this tool in the most recent version of Windows 10 do not affect .appx package usage.</span></span> <span data-ttu-id="6f887-116">Sie können auch weiterhin mit diesem Tool mit AppX-Paketen oder verwenden Sie das Tool mit Unterstützung für .msix Pakete wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6f887-116">You can continue using this tool with .appx packages, or use the tool with support for .msix packages as described below.</span></span>

<span data-ttu-id="6f887-117">So erstellen Sie manuell eine APPXUPLOAD-Datei:</span><span class="sxs-lookup"><span data-stu-id="6f887-117">To manually create an .appxupload file:</span></span>
- <span data-ttu-id="6f887-118">Platzieren Sie die .msix und die appxsym-Datei in einem Ordner</span><span class="sxs-lookup"><span data-stu-id="6f887-118">Place the .msix and the .appxsym in a folder</span></span>
- <span data-ttu-id="6f887-119">Zippen Sie den Ordner.</span><span class="sxs-lookup"><span data-stu-id="6f887-119">Zip the folder</span></span>
- <span data-ttu-id="6f887-120">Ändern Sie den Namen der Erweiterung des komprimierten Ordners von ZIP in APPXUPLOAD.</span><span class="sxs-lookup"><span data-stu-id="6f887-120">Change the zipped folder extension name from .zip to .appxupload</span></span>

## <a name="using-makeappxexe"></a><span data-ttu-id="6f887-121">Verwenden der MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="6f887-121">Using MakeAppx.exe</span></span>

<span data-ttu-id="6f887-122">Abhängig vom Installationspfad des SDK befindet sich **MakeAppx.exe** an folgenden Speicherorten auf Ihrem Windows10-PC:</span><span class="sxs-lookup"><span data-stu-id="6f887-122">Based on your installation path of the SDK, this is where **MakeAppx.exe** is on your Windows 10 PC:</span></span>
- <span data-ttu-id="6f887-123">x86: C:\Programme (x86)\Windows Kits\10\bin\x86\makeappx.exe</span><span class="sxs-lookup"><span data-stu-id="6f887-123">x86: C:\Program Files (x86)\Windows Kits\10\bin\x86\makeappx.exe</span></span>
- <span data-ttu-id="6f887-124">x64: C:\Programme (x86)\Windows Kits\10\bin\x64\makeappx.exe</span><span class="sxs-lookup"><span data-stu-id="6f887-124">x64: C:\Program Files (x86)\Windows Kits\10\bin\x64\makeappx.exe</span></span>

<span data-ttu-id="6f887-125">Es gibt keine ARM-Version dieses Tools.</span><span class="sxs-lookup"><span data-stu-id="6f887-125">There is no ARM version of this tool.</span></span>

### <a name="makeappxexe-syntax-and-options"></a><span data-ttu-id="6f887-126">MakeAppx.exe-Syntax und -Optionen</span><span class="sxs-lookup"><span data-stu-id="6f887-126">MakeAppx.exe syntax and options</span></span>

<span data-ttu-id="6f887-127">Allgemeine **MakeAppx.exe**-Syntax:</span><span class="sxs-lookup"><span data-stu-id="6f887-127">General **MakeAppx.exe** syntax:</span></span>

``` Usage
MakeAppx <command> [options]      
```

<span data-ttu-id="6f887-128">Die folgende Tabelle enthält die Befehle für **MakeAppx.exe**.</span><span class="sxs-lookup"><span data-stu-id="6f887-128">The following table describes the commands for **MakeAppx.exe**.</span></span>

| **<span data-ttu-id="6f887-129">Befehl</span><span class="sxs-lookup"><span data-stu-id="6f887-129">Command</span></span>**   | **<span data-ttu-id="6f887-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-130">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-131">pack</span><span class="sxs-lookup"><span data-stu-id="6f887-131">pack</span></span>          | <span data-ttu-id="6f887-132">Erstellt ein Paket.</span><span class="sxs-lookup"><span data-stu-id="6f887-132">Creates a package.</span></span>                    |
| <span data-ttu-id="6f887-133">unpack</span><span class="sxs-lookup"><span data-stu-id="6f887-133">unpack</span></span>        | <span data-ttu-id="6f887-134">Extrahiert alle Dateien im angegebenen Paket in das angegebene Ausgabeverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="6f887-134">Extracts all files in the specified package to the specified output directory.</span></span> |
| <span data-ttu-id="6f887-135">bundle</span><span class="sxs-lookup"><span data-stu-id="6f887-135">bundle</span></span>        | <span data-ttu-id="6f887-136">Erstellt ein Bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-136">Creates a bundle.</span></span>                     |
| <span data-ttu-id="6f887-137">unbundle</span><span class="sxs-lookup"><span data-stu-id="6f887-137">unbundle</span></span>      | <span data-ttu-id="6f887-138">Entpacken alle Pakete in ein Unterverzeichnis am angegebenen Ausgabepfad, der nach dem vollständigen Namen des Bündels benannt ist.</span><span class="sxs-lookup"><span data-stu-id="6f887-138">Unpacks all packages to a subdirectory under the specified output path named after the bundle full name.</span></span> |
| <span data-ttu-id="6f887-139">encrypt</span><span class="sxs-lookup"><span data-stu-id="6f887-139">encrypt</span></span>       | <span data-ttu-id="6f887-140">Erstellt ein verschlüsseltes App-Paket oder -Bündel aus dem Eingabepaket/-bündel am angegebenen Ausgabepaket/-bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-140">Creates an encrypted app package or bundle from the input package/bundle at the specified output package/bundle.</span></span> |
| <span data-ttu-id="6f887-141">decrypt</span><span class="sxs-lookup"><span data-stu-id="6f887-141">decrypt</span></span>       | <span data-ttu-id="6f887-142">Erstellt ein entschlüsseltes App-Paket oder -Bündel aus dem Eingabe-App-Paket/-Bündel am angegebenen Ausgabepaket/-bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-142">Creates an decrypted app package or bundle from the input app package/bundle at the specified output package/bundle.</span></span> |


<span data-ttu-id="6f887-143">Die folgende Liste von Optionen gilt für alle Befehle:</span><span class="sxs-lookup"><span data-stu-id="6f887-143">This list of options applies to all commands:</span></span>

| **<span data-ttu-id="6f887-144">Option</span><span class="sxs-lookup"><span data-stu-id="6f887-144">Option</span></span>**    | **<span data-ttu-id="6f887-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-145">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-146">/d</span><span class="sxs-lookup"><span data-stu-id="6f887-146">/d</span></span>            | <span data-ttu-id="6f887-147">Gibt das Eingabe-, Ausgabe- oder Inhaltsverzeichnis an.</span><span class="sxs-lookup"><span data-stu-id="6f887-147">Specifies the input, output, or content directory.</span></span> |
| <span data-ttu-id="6f887-148">/l</span><span class="sxs-lookup"><span data-stu-id="6f887-148">/l</span></span>            | <span data-ttu-id="6f887-149">Wird für lokalisierte Pakete verwendet.</span><span class="sxs-lookup"><span data-stu-id="6f887-149">Used for localized packages.</span></span> <span data-ttu-id="6f887-150">Die Standardüberprüfung wird durch lokalisierte Pakete ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="6f887-150">The default validation trips on localized packages.</span></span> <span data-ttu-id="6f887-151">Diese Option deaktiviert nur diese spezifische Überprüfung, ohne dass die gesamte Überprüfung deaktiviert werden muss.</span><span class="sxs-lookup"><span data-stu-id="6f887-151">This options disables only that specific validation, without requiring that all validation be disabled.</span></span> |
| <span data-ttu-id="6f887-152">/kf</span><span class="sxs-lookup"><span data-stu-id="6f887-152">/kf</span></span>           | <span data-ttu-id="6f887-153">Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des Schlüssels aus der angegebenen Schlüsseldatei.</span><span class="sxs-lookup"><span data-stu-id="6f887-153">Encrypts or decrypts the package or bundle using the key from the specified key file.</span></span> <span data-ttu-id="6f887-154">Diese Option kann nicht mit /kt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f887-154">This can't be used with /kt.</span></span> |
| <span data-ttu-id="6f887-155">/kt</span><span class="sxs-lookup"><span data-stu-id="6f887-155">/kt</span></span>           | <span data-ttu-id="6f887-156">Verschlüsselt oder entschlüsselt das Paket oder Bündel mithilfe des globalen Testschlüssels.</span><span class="sxs-lookup"><span data-stu-id="6f887-156">Encrypts the or decrypts package or bundle using the global test key.</span></span> <span data-ttu-id="6f887-157">Diese Option kann nicht mit /kf verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f887-157">This can't be used with /kf.</span></span> |
| <span data-ttu-id="6f887-158">/no</span><span class="sxs-lookup"><span data-stu-id="6f887-158">/no</span></span>           | <span data-ttu-id="6f887-159">Verhindert ein Überschreiben der Ausgabedatei, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="6f887-159">Prevents an overwrite of the output file if it exists.</span></span> <span data-ttu-id="6f887-160">Wenn Sie diese Option oder die Option /o nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="6f887-160">If you don't specify this option or the /o option, the user is asked whether they want to overwrite the file.</span></span> |
| <span data-ttu-id="6f887-161">/nv</span><span class="sxs-lookup"><span data-stu-id="6f887-161">/nv</span></span>           | <span data-ttu-id="6f887-162">Überspringt die semantische Überprüfung.</span><span class="sxs-lookup"><span data-stu-id="6f887-162">Skips semantic validation.</span></span> <span data-ttu-id="6f887-163">Wenn Sie diese Option nicht angeben, führt das Tool eine vollständige Überprüfung des Pakets aus.</span><span class="sxs-lookup"><span data-stu-id="6f887-163">If you don't specify this option, the tool performs a full validation of the package.</span></span> |
| <span data-ttu-id="6f887-164">/o</span><span class="sxs-lookup"><span data-stu-id="6f887-164">/o</span></span>            | <span data-ttu-id="6f887-165">Überschreibt die Ausgabedatei, wenn vorhanden.</span><span class="sxs-lookup"><span data-stu-id="6f887-165">Overwrites the output file if it exists.</span></span> <span data-ttu-id="6f887-166">Wenn Sie diese Option oder die Option /no nicht angeben, werden Benutzer gefragt, ob sie die Datei überschreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="6f887-166">If you don't specify this option or the /no option, the user is asked whether they want to overwrite the file.</span></span> |
| <span data-ttu-id="6f887-167">/p</span><span class="sxs-lookup"><span data-stu-id="6f887-167">/p</span></span>            | <span data-ttu-id="6f887-168">Gibt das App-Paket oder -Bündel an.</span><span class="sxs-lookup"><span data-stu-id="6f887-168">Specifies the app package or bundle.</span></span>  |
| <span data-ttu-id="6f887-169">/v</span><span class="sxs-lookup"><span data-stu-id="6f887-169">/v</span></span>            | <span data-ttu-id="6f887-170">Aktiviert die ausführliche Protokollierungsausgabe an die Konsole.</span><span class="sxs-lookup"><span data-stu-id="6f887-170">Enables verbose logging output to the console.</span></span> |
| <span data-ttu-id="6f887-171">/?</span><span class="sxs-lookup"><span data-stu-id="6f887-171">/?</span></span>            | <span data-ttu-id="6f887-172">Zeigt Hilfetext an.</span><span class="sxs-lookup"><span data-stu-id="6f887-172">Displays help text.</span></span>                   |


<span data-ttu-id="6f887-173">Die folgende Liste enthält mögliche Argumente:</span><span class="sxs-lookup"><span data-stu-id="6f887-173">The following list contains possible arguments:</span></span>

| **<span data-ttu-id="6f887-174">Argument</span><span class="sxs-lookup"><span data-stu-id="6f887-174">Argument</span></span>**                          | **<span data-ttu-id="6f887-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-175">Description</span></span>**                       |
|---------------------------------------|---------------------------------------|
| <span data-ttu-id="6f887-176">&lt;output package name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-176">&lt;output package name&gt;</span></span>           | <span data-ttu-id="6f887-177">Der Name des erstellten Pakets.</span><span class="sxs-lookup"><span data-stu-id="6f887-177">The name of the package created.</span></span> <span data-ttu-id="6f887-178">Dies ist der Dateiname mit .msix oder AppX angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-178">This is the file name appended with .msix or .appx.</span></span> |
| <span data-ttu-id="6f887-179">&lt;encrypted output package name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-179">&lt;encrypted output package name&gt;</span></span> | <span data-ttu-id="6f887-180">Der Name des erstellten verschlüsselten Pakets.</span><span class="sxs-lookup"><span data-stu-id="6f887-180">The name of the encrypted package created.</span></span> <span data-ttu-id="6f887-181">Dies ist der Dateiname mit .emsix oder eappx angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-181">This is the file name appended with .emsix or .eappx.</span></span> |
| <span data-ttu-id="6f887-182">&lt;input package name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-182">&lt;input package name&gt;</span></span>            | <span data-ttu-id="6f887-183">Der Name des Pakets.</span><span class="sxs-lookup"><span data-stu-id="6f887-183">The name of the package.</span></span> <span data-ttu-id="6f887-184">Dies ist der Dateiname mit .msix oder AppX angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-184">This is the file name appended with .msix or .appx.</span></span> |
| <span data-ttu-id="6f887-185">&lt;encrypted input package name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-185">&lt;encrypted input package name&gt;</span></span>  | <span data-ttu-id="6f887-186">Der Name des verschlüsselten Pakets.</span><span class="sxs-lookup"><span data-stu-id="6f887-186">The name of the encrypted package.</span></span> <span data-ttu-id="6f887-187">Dies ist der Dateiname mit .emsix oder eappx angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-187">This is the file name appended with .emsix or .eappx.</span></span> |
| <span data-ttu-id="6f887-188">&lt;output bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-188">&lt;output bundle name&gt;</span></span>            | <span data-ttu-id="6f887-189">Der Name des erstellten Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-189">The name of the bundle created.</span></span> <span data-ttu-id="6f887-190">Dies ist der Dateiname mit .msixbundle oder .appxbundle angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-190">This is the file name appended with .msixbundle or .appxbundle.</span></span> |
| <span data-ttu-id="6f887-191">&lt;encrypted output bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-191">&lt;encrypted output bundle name&gt;</span></span>  | <span data-ttu-id="6f887-192">Der Name des erstellten verschlüsselten Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-192">The name of the encrypted bundle created.</span></span> <span data-ttu-id="6f887-193">Dies ist der Dateiname mit .emsixbundle oder eappxbundle angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-193">This is the file name appended with .emsixbundle or .eappxbundle.</span></span> |
| <span data-ttu-id="6f887-194">&lt;input bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-194">&lt;input bundle name&gt;</span></span>             | <span data-ttu-id="6f887-195">Der Name des Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-195">The name of the bundle.</span></span> <span data-ttu-id="6f887-196">Dies ist der Dateiname mit .msixbundle oder .appxbundle angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-196">This is the file name appended with .msixbundle or .appxbundle.</span></span> |
| <span data-ttu-id="6f887-197">&lt;encrypted input bundle name&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-197">&lt;encrypted input bundle name&gt;</span></span>   | <span data-ttu-id="6f887-198">Der Name des verschlüsselten Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-198">The name of the encrypted bundle.</span></span> <span data-ttu-id="6f887-199">Dies ist der Dateiname mit .emsixbundle oder eappxbundle angefügt.</span><span class="sxs-lookup"><span data-stu-id="6f887-199">This is the file name appended with .emsixbundle or .eappxbundle.</span></span> |
| <span data-ttu-id="6f887-200">&lt;content directory&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-200">&lt;content directory&gt;</span></span>             | <span data-ttu-id="6f887-201">Der Pfad für den Inhalt des App-Pakets oder -Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-201">Path for the app package or bundle content.</span></span> |
| <span data-ttu-id="6f887-202">&lt;mapping file&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-202">&lt;mapping file&gt;</span></span>                  | <span data-ttu-id="6f887-203">Der Name der Datei, der Paketquelle und -ziel angibt.</span><span class="sxs-lookup"><span data-stu-id="6f887-203">File name that specifies the package source and destination.</span></span> |
| <span data-ttu-id="6f887-204">&lt;output directory&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-204">&lt;output directory&gt;</span></span>              | <span data-ttu-id="6f887-205">Der Pfad zum Verzeichnis für Ausgabepakete und -bündel.</span><span class="sxs-lookup"><span data-stu-id="6f887-205">Path to the directory for output packages and bundles.</span></span> |
| <span data-ttu-id="6f887-206">&lt;key file&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-206">&lt;key file&gt;</span></span>                      | <span data-ttu-id="6f887-207">Der Name der Datei mit einem Schlüssel für die Verschlüsselung oder Entschlüsselung.</span><span class="sxs-lookup"><span data-stu-id="6f887-207">Name of the file containing a key for encryption or decryption.</span></span> |
| <span data-ttu-id="6f887-208">&lt;algorithm ID&gt;</span><span class="sxs-lookup"><span data-stu-id="6f887-208">&lt;algorithm ID&gt;</span></span>                  | <span data-ttu-id="6f887-209">Die beim Erstellen einer Blockzuordnung verwendeten Algorithmen.</span><span class="sxs-lookup"><span data-stu-id="6f887-209">Algorithms used when creating a block map.</span></span> <span data-ttu-id="6f887-210">Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512.</span><span class="sxs-lookup"><span data-stu-id="6f887-210">Valid algorithms include: SHA256 (default), SHA384, SHA512.</span></span> |


### <a name="create-an-app-package"></a><span data-ttu-id="6f887-211">Erstellen eines App-Pakets</span><span class="sxs-lookup"><span data-stu-id="6f887-211">Create an app package</span></span>

<span data-ttu-id="6f887-212">Ein app-Paket ist ein vollständiger Satz von app Dateien, verpackt in einer .msix oder AppX-Paketdatei.</span><span class="sxs-lookup"><span data-stu-id="6f887-212">An app package is a complete set of the app's files packaged in to a .msix or .appx package file.</span></span> <span data-ttu-id="6f887-213">Um ein App-Paket mit dem Befehl **pack** zu erstellen, müssen Sie entweder ein Inhaltsverzeichnis oder eine Zuordnungsdati für den Speicherort des Pakets angeben.</span><span class="sxs-lookup"><span data-stu-id="6f887-213">To create an app package using the **pack** command, you must provide either a content directory or a mapping file for the location of the package.</span></span> <span data-ttu-id="6f887-214">Sie können ein Paket auch während des Erstellens verschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="6f887-214">You can also encrypt a package while creating it.</span></span> <span data-ttu-id="6f887-215">Wenn Sie das Paket verschlüsseln möchten, müssen Sie /ep verwenden und angeben, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="6f887-215">If you want to encrypt the package, you must use /ep and specify if you are using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="6f887-216">Weitere Informationen zum Erstellen eines verschlüsselten Pakets finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="6f887-216">For more information on creating an encrypted package, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="6f887-217">Optionen, die für den Befehl **pack** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="6f887-217">Options specific to the **pack** command:</span></span>

| **<span data-ttu-id="6f887-218">Option</span><span class="sxs-lookup"><span data-stu-id="6f887-218">Option</span></span>**    | **<span data-ttu-id="6f887-219">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-219">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-220">/f</span><span class="sxs-lookup"><span data-stu-id="6f887-220">/f</span></span>            | <span data-ttu-id="6f887-221">Gibt die Zuordnungsdatei an.</span><span class="sxs-lookup"><span data-stu-id="6f887-221">Specifies the mapping file.</span></span>           |
| <span data-ttu-id="6f887-222">/h</span><span class="sxs-lookup"><span data-stu-id="6f887-222">/h</span></span>            | <span data-ttu-id="6f887-223">Gibt den Hashalgorithmus an, der beim Erstellen der Blockzuordnung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6f887-223">Specifies the hash algorithm to use when creating the block map.</span></span> <span data-ttu-id="6f887-224">Diese Option kann nur mit den pack-Befehl verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f887-224">This can only be used with the pack command.</span></span> <span data-ttu-id="6f887-225">Gültige Algorithmen sind: SHA256 (Standard), SHA384 und SHA512.</span><span class="sxs-lookup"><span data-stu-id="6f887-225">Valid algorithms include: SHA256 (default), SHA384, SHA512.</span></span> |
| <span data-ttu-id="6f887-226">/m</span><span class="sxs-lookup"><span data-stu-id="6f887-226">/m</span></span>            | <span data-ttu-id="6f887-227">Gibt den Pfad zu einem Eingabe App-Manifest an, das als Grundlage für das Generieren des Ausgabe-App-Pakets oder des Manifests des Ressourcenpakets verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6f887-227">Specifies the path to an input app manifest which will be used as the basis for generating the output app package or resource package's manifest.</span></span>  <span data-ttu-id="6f887-228">Wenn Sie diese Option verwenden, müssen Sie auch /f verwenden und einen [ResourceMetadata]-Abschnitt in die Zuordnungsdatei einfügen, um die Ressourcendimensionen anzugeben, die im generierten Manifest enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="6f887-228">When you use this option, you must also use /f and include a [ResourceMetadata] section in the mapping file to specify the resource dimensions to be included in the generated manifest.</span></span>|
| <span data-ttu-id="6f887-229">/nc</span><span class="sxs-lookup"><span data-stu-id="6f887-229">/nc</span></span>           | <span data-ttu-id="6f887-230">Verhindert die Komprimierung der Paketdateien.</span><span class="sxs-lookup"><span data-stu-id="6f887-230">Prevents compression of the package files.</span></span> <span data-ttu-id="6f887-231">Standardmäßig werden Dateien basierend auf dem erkannten Dateityp komprimiert.</span><span class="sxs-lookup"><span data-stu-id="6f887-231">By default, files are compressed based on detected file type.</span></span> |
| <span data-ttu-id="6f887-232">/r</span><span class="sxs-lookup"><span data-stu-id="6f887-232">/r</span></span>            | <span data-ttu-id="6f887-233">Erstellt ein Ressourcenpaket.</span><span class="sxs-lookup"><span data-stu-id="6f887-233">Builds a resource package.</span></span> <span data-ttu-id="6f887-234">Diese Option muss mit /m verwendet werden und impliziert die Verwendung der Option /l.</span><span class="sxs-lookup"><span data-stu-id="6f887-234">This must be used with /m and implies the use of the /l option.</span></span> |  


<span data-ttu-id="6f887-235">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **pack**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="6f887-235">The following usage examples show some possible syntax options for the **pack** command:</span></span>

``` syntax 
MakeAppx pack [options] /d <content directory> /p <output package name>
MakeAppx pack [options] /f <mapping file> /p <output package name>
MakeAppx pack [options] /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /r /m <app package manifest> /f <mapping file> /p <output package name>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kf <key file>
MakeAppx pack [options] /d <content directory> /ep <encrypted output package name> /kt

```
<span data-ttu-id="6f887-236">Im Folgenden finden Sie Befehlszeilenbeispiele für den **pack**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="6f887-236">The following shows command line examples for the **pack** command:</span></span>

``` examples
MakeAppx pack /v /h SHA256 /d "C:\My Files" /p MyPackage.msix
MakeAppx pack /v /o /f MyMapping.txt /p MyPackage.msix
MakeAppx pack /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p AppPackage.msix
MakeAppx pack /r /m "MyApp\AppxManifest.xml" /f MyMapping.txt /p ResourcePackage.msix
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.emsix /kf MyKeyFile.txt
MakeAppx pack /v /h SHA256 /d "C:\My Files" /ep MyPackage.emsix /kt
```

### <a name="create-an-app-bundle"></a><span data-ttu-id="6f887-237">Erstellen eines App-Bündels</span><span class="sxs-lookup"><span data-stu-id="6f887-237">Create an app bundle</span></span>

<span data-ttu-id="6f887-238">Ein App-Bündel ist einem App-Paket vergleichbar. Ein Bündel kann jedoch die Größe der App reduzieren, die Benutzer herunterladen.</span><span class="sxs-lookup"><span data-stu-id="6f887-238">An app bundle is similar to an app package, but a bundle can reduce the size of the app that users download.</span></span> <span data-ttu-id="6f887-239">App-Bündel sind beispielsweise für sprachspezifische Ressourcen, Ressourcen mit unterschiedlichen Imagegrößen oder Ressourcen nützlich, die für spezifische Versionen von Microsoft DirectX gelten.</span><span class="sxs-lookup"><span data-stu-id="6f887-239">App bundles are helpful for language-specific assets, varying image-scale assets, or resources that apply to specific versions of Microsoft DirectX, for example.</span></span> <span data-ttu-id="6f887-240">Wie beim Erstellen verschlüsselter App-Pakete, können Sie auch App-Bündel beim Bündeln verschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="6f887-240">Similar to creating an encrypted app package, you can also encrypt the app bundle while bundling it.</span></span> <span data-ttu-id="6f887-241">Um das App-Bündel zu verschlüsseln, verwenden Sie die Option /ep und geben an, ob Sie eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="6f887-241">To encrypt the app bundle, use the /ep option and specify if you are using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="6f887-242">Weitere Informationen zum Erstellen eines verschlüsselten Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln von Paketen oder Bündeln](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="6f887-242">For more information on creating an encrypted bundle, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="6f887-243">Optionen, die für den **bundle**-Befehl spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="6f887-243">Options specific to the **bundle** command:</span></span>

| **<span data-ttu-id="6f887-244">Option</span><span class="sxs-lookup"><span data-stu-id="6f887-244">Option</span></span>**    | **<span data-ttu-id="6f887-245">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-245">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-246">/bv</span><span class="sxs-lookup"><span data-stu-id="6f887-246">/bv</span></span>           | <span data-ttu-id="6f887-247">Gibt die Versionsnummer des Bündels an.</span><span class="sxs-lookup"><span data-stu-id="6f887-247">Specifies the version number of the bundle.</span></span> <span data-ttu-id="6f887-248">Die Versionsnummer muss aus vier Teilen bestehen, getrennt durch Punkte: &lt;Hauptversion&gt;.&lt;Unterversion&gt;.&lt;Build&gt;.&lt;Überarbeitung&gt;.</span><span class="sxs-lookup"><span data-stu-id="6f887-248">The version number must be in four parts separated by periods in the form: &lt;Major&gt;.&lt;Minor&gt;.&lt;Build&gt;.&lt;Revision&gt;.</span></span> |
| <span data-ttu-id="6f887-249">/f</span><span class="sxs-lookup"><span data-stu-id="6f887-249">/f</span></span>            | <span data-ttu-id="6f887-250">Gibt die Zuordnungsdatei an.</span><span class="sxs-lookup"><span data-stu-id="6f887-250">Specifies the mapping file.</span></span>           |

<span data-ttu-id="6f887-251">Beachten Sie, dass die Bündelversion mit dem aktuellen Datum und der aktuellen Uhrzeit erstellt wird, wenn die Bündelversion nicht angegeben oder auf „0.0.0.0“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="6f887-251">Note that if the bundle version is not specified or if it is set to "0.0.0.0" the bundle is created using the current date-time.</span></span>

<span data-ttu-id="6f887-252">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für den **bundle**-Befehl:</span><span class="sxs-lookup"><span data-stu-id="6f887-252">The following usage examples show some possible syntax options for the **bundle** command:</span></span>

``` syntax
MakeAppx bundle [options] /d <content directory> /p <output bundle name>
MakeAppx bundle [options] /f <mapping file> /p <output bundle name>
MakeAppx bundle [options] /d <content directory> /ep <encrypted output bundle name> /kf MyKeyFile.txt
MakeAppx bundle [options] /f <mapping file> /ep <encrypted output bundle name> /kt
```
<span data-ttu-id="6f887-253">Der folgende Block enthält Beispiele für den **bundle** Befehl:</span><span class="sxs-lookup"><span data-stu-id="6f887-253">The following block contains examples for the **bundle** command:</span></span>

``` examples
MakeAppx bundle /v /d "C:\My Files" /p MyBundle.msixbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /p MyBundle.msixbundle
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.emsixbundle /kf MyKeyFile.txt
MakeAppx bundle /v /o /bv 1.0.1.2096 /f MyMapping.txt /ep MyBundle.emsixbundle /kt
```

### <a name="extract-files-from-a-package-or-bundle"></a><span data-ttu-id="6f887-254">Extrahieren von Dateien aus einem Paket oder Bündel</span><span class="sxs-lookup"><span data-stu-id="6f887-254">Extract files from a package or bundle</span></span>

<span data-ttu-id="6f887-255">Zusätzlich zum Packen und Bündeln von Apps kann **MakeAppx.exe** vorhandene Pakete entpacken oder entbündeln.</span><span class="sxs-lookup"><span data-stu-id="6f887-255">In addition to packaging and bundling apps, **MakeAppx.exe** can also unpack or unbundle existing packages.</span></span> <span data-ttu-id="6f887-256">Sie müssen als Ziel für die extrahierten Dateien das Inhaltsverzeichnis angeben.</span><span class="sxs-lookup"><span data-stu-id="6f887-256">You must provide the content directory as a destination for the extracted files.</span></span> <span data-ttu-id="6f887-257">Wenn Sie versuchen, Dateien aus einem verschlüsselten Paket oder Bündel zu extrahieren, können Sie die Dateien gleichzeitig entschlüsseln und extrahieren, indem Sie die Option /ep verwenden und angeben, ob sie mit einer Schlüsseldatei (/kf) oder dem globalen Testschlüssel (/kt) entschlüsselt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6f887-257">If you are trying to extract files from an encrypted package or bundle, you can decrypt and extract the files at the same time using the /ep option and specifying whether it should be decrypted using a key file (/kf) or the global test key (/kt).</span></span> <span data-ttu-id="6f887-258">Weitere Informationen zum Entschlüsseln eines Pakets oder Bündels finden Sie unter [Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels](#encrypt-or-decrypt-a-package-or-bundle).</span><span class="sxs-lookup"><span data-stu-id="6f887-258">For more information on decrypting a package or bundle, see [Encrypt or decrypt a package or bundle](#encrypt-or-decrypt-a-package-or-bundle).</span></span>

<span data-ttu-id="6f887-259">Optionen, die für die Befehle **unpack** und **unbundle** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="6f887-259">Options specific to **unpack** and **unbundle** commands:</span></span>

| **<span data-ttu-id="6f887-260">Option</span><span class="sxs-lookup"><span data-stu-id="6f887-260">Option</span></span>**    | **<span data-ttu-id="6f887-261">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-261">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-262">/nd</span><span class="sxs-lookup"><span data-stu-id="6f887-262">/nd</span></span>           | <span data-ttu-id="6f887-263">Führt beim Entpacken oder Entbündeln des Pakets/Bündels keine Entschlüsselung aus.</span><span class="sxs-lookup"><span data-stu-id="6f887-263">Does not perform decryption when unpacking or unbundling the package/bundle.</span></span> |
| <span data-ttu-id="6f887-264">/pfn</span><span class="sxs-lookup"><span data-stu-id="6f887-264">/pfn</span></span>          | <span data-ttu-id="6f887-265">Entpackt/entbündelt alle Dateien in ein Unterverzeichnis am angegebenen Ausgabepfad, benannt nach dem vollständigen Namen des Pakets oder Bündels.</span><span class="sxs-lookup"><span data-stu-id="6f887-265">Unpacks/unbundles all files to a subdirectory under the specified output path, named after the package or bundle full name</span></span> |

<span data-ttu-id="6f887-266">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **unpack** und **unbundle**:</span><span class="sxs-lookup"><span data-stu-id="6f887-266">The following usage examples show some possible syntax options for the **unpack** and **unbundle** commands:</span></span>

``` syntax
MakeAppx unpack [options] /p <input package name> /d <output directory>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kf <key file>
MakeAppx unpack [options] /ep <encrypted input package name> /d <output directory> /kt

MakeAppx unbundle [options] /p <input bundle name> /d <output directory>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kf <key file>
MakeAppx unbundle [options] /ep <encrypted input bundle name> /d <output directory> /kt
```

<span data-ttu-id="6f887-267">Der folgende Block enthält Beispiele für die Verwendung der Befehle **unpack** und **unbundle**:</span><span class="sxs-lookup"><span data-stu-id="6f887-267">The following block contains examples for using the **unpack** and **unbundle** commands:</span></span>

``` examples
MakeAppx unpack /v /p MyPackage.msix /d "C:\My Files"
MakeAppx unpack /v /ep MyPackage.emsix /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unpack /v /ep MyPackage.emsix /d "C:\My Files" /kt

MakeAppx unbundle /v /p MyBundle.msixbundle /d "C:\My Files"
MakeAppx unbundle /v /ep MyBundle.emsixbundle /d "C:\My Files" /kf MyKeyFile.txt
MakeAppx unbundle /v /ep MyBundle.emsixbundle /d "C:\My Files" /kt
```

### <a name="encrypt-or-decrypt-a-package-or-bundle"></a><span data-ttu-id="6f887-268">Verschlüsseln oder Entschlüsseln eines Pakets oder Bündels</span><span class="sxs-lookup"><span data-stu-id="6f887-268">Encrypt or decrypt a package or bundle</span></span>

<span data-ttu-id="6f887-269">Das **MakeAppx.exe**-Tool kann ein vorhandenes Paket oder Bündel auch verschlüsseln oder entschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="6f887-269">The **MakeAppx.exe** tool can also encrypt or decrypt an existing package or bundle.</span></span> <span data-ttu-id="6f887-270">Sie müssen lediglich den Paketnamen und den Ausgabepaketnamen angeben und ob die Verschlüsselung oder Entschlüsselung eine Schlüsseldatei (/kf) oder den globalen Testschlüssel (/kt) verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="6f887-270">You must simply provide the package name, the output package name, and whether encryption or decryption should use a key file (/kf) or the global test key (/kt).</span></span>

<span data-ttu-id="6f887-271">Verschlüsselung und Entschlüsselung sind nicht über den Verpackungs-Assistenten von Visual Studio verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6f887-271">Encryption and decryption are not available through the Visual Studio packaging wizard.</span></span> 

<span data-ttu-id="6f887-272">Optionen, die für die Befehle **encrypt** und **decrypt** spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="6f887-272">Options specific to **encrypt** and **decrypt** commands:</span></span>

| **<span data-ttu-id="6f887-273">Option</span><span class="sxs-lookup"><span data-stu-id="6f887-273">Option</span></span>**    | **<span data-ttu-id="6f887-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f887-274">Description</span></span>**                       |
|---------------|---------------------------------------|
| <span data-ttu-id="6f887-275">/ep</span><span class="sxs-lookup"><span data-stu-id="6f887-275">/ep</span></span>           | <span data-ttu-id="6f887-276">Gibt ein verschlüsseltes App-Paket oder -Bündel an.</span><span class="sxs-lookup"><span data-stu-id="6f887-276">Specifies an encrypted app package or bundle.</span></span> |

<span data-ttu-id="6f887-277">Die folgenden Verwendungsbeispiele zeigen einige mögliche Syntaxoptionen für die Befehle **encrypt** und **decrypt**:</span><span class="sxs-lookup"><span data-stu-id="6f887-277">The following usage examples show some possible syntax options for the **encrypt** and **decrypt** commands:</span></span>

``` syntax
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kf <key file>
MakeAppx encrypt [options] /p <package name> /ep <output package name> /kt

MakeAppx decrypt [options] /ep <package name> /p <output package name> /kf <key file>
MakeAppx decrypt [options] /ep <package name> /p <output package name> /kt
```

<span data-ttu-id="6f887-278">Der folgende Block enthält Beispiele für die Verwendung der Befehle **encrypt** und **decrypt**:</span><span class="sxs-lookup"><span data-stu-id="6f887-278">The following block contains examples for using the **encrypt** and **decrypt** commands:</span></span>

``` examples
MakeAppx.exe encrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kt
MakeAppx.exe encrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kf MyKeyFile.txt

MakeAppx.exe decrypt /p MyPackage.msix /ep MyEncryptedPackage.emsix /kt
MakeAppx.exe decrypt p MyPackage.msix /ep MyEncryptedPackage.emsix /kf MyKeyFile.txt
```

## <a name="key-files"></a><span data-ttu-id="6f887-279">Schlüsseldateien</span><span class="sxs-lookup"><span data-stu-id="6f887-279">Key files</span></span>

<span data-ttu-id="6f887-280">Schlüsseldateien müssen mit einer Zeile beginnen, die die Zeichenfolge „[Keys]“ enthält, gefolgt von Zeilen, die die Schlüssel beschreiben, mit denen die einzelnen Pakete verschlüsselt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6f887-280">Key files must begin with a line containing the string "[Keys]" followed by lines describing the keys to encrypt each package with.</span></span> <span data-ttu-id="6f887-281">Jeder Schlüssel wird durch ein Paar von Zeichenfolgen in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, dargestellt.</span><span class="sxs-lookup"><span data-stu-id="6f887-281">Each key is represented by a pair of strings in quotation marks, separated by either spaces or tabs.</span></span> <span data-ttu-id="6f887-282">Die erste Zeichenfolge stellt die base64-codierte 32-Byte-Schlüssel-ID dar. Die zweite Zeichenfolge stellt den base64-codierten 32-Byte-Verschlüsselungsschlüssel dar.</span><span class="sxs-lookup"><span data-stu-id="6f887-282">The first string represents the base64 encoded 32-byte key ID and the second represents the base64 encoded 32-byte encryption key.</span></span> <span data-ttu-id="6f887-283">Eine Schlüsseldatei sollte eine einfache Textdatei sein.</span><span class="sxs-lookup"><span data-stu-id="6f887-283">A key file should be a simple text file.</span></span>

<span data-ttu-id="6f887-284">Beispiel für eine Schlüsseldatei:</span><span class="sxs-lookup"><span data-stu-id="6f887-284">Example of a key file:</span></span>

``` Example
[Keys]
"OWVwSzliRGY1VWt1ODk4N1Q4R2Vqc04zMzIzNnlUREU="    "MjNFTlFhZGRGZEY2YnVxMTBocjd6THdOdk9pZkpvelc="
```

## <a name="mapping-files"></a><span data-ttu-id="6f887-285">Zuordnungsdateien</span><span class="sxs-lookup"><span data-stu-id="6f887-285">Mapping files</span></span>
<span data-ttu-id="6f887-286">Zuordnungsdateien müssen mit einer Zeile beginnen, die Zeichenfolge „[Files]“ enthält, gefolgt von Zeilen, die die Dateien beschreiben, die dem Paket hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6f887-286">Mapping files must begin with a line containing the string "[Files]" followed by lines describing the files to add to the package.</span></span> <span data-ttu-id="6f887-287">Jede Datei wird durch ein Paar von Pfaden in Anführungszeichen, getrennt durch Leerzeichen oder Tabulatoren, beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6f887-287">Each file is described by a pair of paths in quotation marks, separated by either spaces or tabs.</span></span> <span data-ttu-id="6f887-288">Jede Datei stellt Quelle (auf der Festplatte) und Ziel (im Paket) dar.</span><span class="sxs-lookup"><span data-stu-id="6f887-288">Each file represents its source (on disk) and destination (in the package).</span></span> <span data-ttu-id="6f887-289">Eine Zuordnungsdatei sollte eine einfache Textdatei sein.</span><span class="sxs-lookup"><span data-stu-id="6f887-289">A mapping file should be a simple text file.</span></span>

<span data-ttu-id="6f887-290">Beispiel für eine Zuordnungsdatei (ohne Option /m):</span><span class="sxs-lookup"><span data-stu-id="6f887-290">Example of a mapping file (without the /m option):</span></span>

``` Example
[Files]
"C:\MyApp\StartPage.html"               "default.html"
"C:\Program Files (x86)\example.txt"    "misc\example.txt"
"\\MyServer\path\icon.png"              "icon.png"
"my app files\readme.txt"               "my app files\readme.txt"
"CustomManifest.xml"                    "AppxManifest.xml"
``` 

<span data-ttu-id="6f887-291">Wenn Sie eine Zuordnungsdatei verwenden, können Sie wählen, ob Sie die Option /m verwenden möchten oder nicht.</span><span class="sxs-lookup"><span data-stu-id="6f887-291">When using a mapping file, you can choose whether you would like to use the /m option.</span></span> <span data-ttu-id="6f887-292">Mithilfe der Option /m können Benutzer die Ressourcenmetadaten in der Zuordnungsdatei angeben, die im generierten Manifest eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6f887-292">The /m option allows the user to specify the resource metadata in the mapping file to be included in the generated manifest.</span></span> <span data-ttu-id="6f887-293">Wenn Sie die Option /m verwenden, muss die Zuordnungsdatei einen Abschnittenthalten, der mit der Zeile „[ResourceMetadata]“ beginnt, gefolgt von Zeilen, die „ResourceDimensions“ und „ResourceId“ angeben.</span><span class="sxs-lookup"><span data-stu-id="6f887-293">If you use the /m option, the mapping file must contain a section that begins with the line "[ResourceMetadata]", followed by lines that specify "ResourceDimensions" and "ResourceId."</span></span> <span data-ttu-id="6f887-294">App-Pakete können mehrere „ResourceDimensions“ enthalten kann, jedoch stets nur eine „ResourceId“.</span><span class="sxs-lookup"><span data-stu-id="6f887-294">It is possible for an app package to contain multiple "ResourceDimensions", but there can only ever be one "ResourceId."</span></span>

<span data-ttu-id="6f887-295">Beispiel für eine Zuordnungsdatei (mit Option /m):</span><span class="sxs-lookup"><span data-stu-id="6f887-295">Example of a mapping file (with the /m option):</span></span>

``` Example
[ResourceMetadata]
"ResourceDimensions"                    "language-en-us"
"ResourceId"                            "English"

[Files]
"images\en-us\logo.png"                 "en-us\logo.png"
"en-us.pri"                             "resources.pri"
```

## <a name="semantic-validation-performed-by-makeappxexe"></a><span data-ttu-id="6f887-296">Semantische Überprüfung durch MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="6f887-296">Semantic validation performed by MakeAppx.exe</span></span>

<span data-ttu-id="6f887-297">**MakeAppx.exe** führt eine begrenzte semantische Überprüfung aus, um die häufigsten Bereitstellungsfehler zu erfassen und sicherzustellen, dass das App-Paket gültig ist.</span><span class="sxs-lookup"><span data-stu-id="6f887-297">**MakeAppx.exe** performs limited sematic validation that is designed to catch the most common deployment errors and help ensure that the app package is valid.</span></span> <span data-ttu-id="6f887-298">Verwenden Sie die Option /nv, wenn Sie beim Verwenden von **MakeAppx.exe**  die Überprüfung auslassen möchten.</span><span class="sxs-lookup"><span data-stu-id="6f887-298">See the /nv option if you want to skip validation while using **MakeAppx.exe**.</span></span> 

<span data-ttu-id="6f887-299">Diese Überprüfung stellt Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="6f887-299">This validation ensures that:</span></span>
- <span data-ttu-id="6f887-300">Alle Dateien, auf die im Paketmanifest verwiesen wird, sind im App-Paket enthalten.</span><span class="sxs-lookup"><span data-stu-id="6f887-300">All files referenced in the package manifest are included in the app package.</span></span>
- <span data-ttu-id="6f887-301">Die Anwendung besitzt nicht zwei identische Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="6f887-301">An application does not have two identical keys.</span></span>
- <span data-ttu-id="6f887-302">Die Anwendung registriert sich nicht für ein untersagtes Protokoll aus der folgenden Liste: SMB, FILE, MS-WWA-WEB, MS-WWA.</span><span class="sxs-lookup"><span data-stu-id="6f887-302">An application does not register for a forbidden protocol from this list: SMB, FILE, MS-WWA-WEB, MS-WWA.</span></span> 

<span data-ttu-id="6f887-303">Dies ist keine vollständige semantische Überprüfung, da sie lediglich häufige Fehler erfassen soll.</span><span class="sxs-lookup"><span data-stu-id="6f887-303">This is not a complete semantic validation as it is only designed to catch common errors.</span></span> <span data-ttu-id="6f887-304">Es wird nicht garantiert, dass von **MakeAppx.exe** erstellte Pakete installiert werden können.</span><span class="sxs-lookup"><span data-stu-id="6f887-304">Packages built by **MakeAppx.exe** are not guaranteed to be installable.</span></span>