---
author: laurenhughes
title: Einrichten automatisierter Builds für UWP-Apps
description: Erfahren Sie, wie Sie automatisierte Builds konfigurieren, um Pakete zum Querladen oder zum Übermitteln an den Store zu erzeugen.
ms.author: hickeys
ms.date: 09/30/2018
ms.topic: article
keywords: Windows10, UWP
ms.assetid: f9b0d6bd-af12-4237-bc66-0c218859d2fd
ms.localizationpriority: medium
ms.openlocfilehash: 775e780be823b6e7b80eda9f488d69fe4fc29edf
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7149590"
---
# <a name="set-up-automated-builds-for-your-uwp-app"></a><span data-ttu-id="663e8-104">Einrichten automatisierter Builds für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="663e8-104">Set up automated builds for your UWP app</span></span>

<span data-ttu-id="663e8-105">Mithilfe von Visual Studio Team Services (VSTS) können Sie automatisierte Builds für UWP-Projekte erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-105">You can use Visual Studio Team Services (VSTS) to create automated builds for UWP projects.</span></span>
<span data-ttu-id="663e8-106">In diesem Artikel werden verschiedene Erstellungsmöglichkeiten erläutert.</span><span class="sxs-lookup"><span data-stu-id="663e8-106">In this article, we’ll look at different ways to do that.</span></span>  <span data-ttu-id="663e8-107">Außerdem wird erläutert, wie Sie diese Aufgaben über die Befehlszeile ausführen, um die Integration in andere Buildsysteme, z.B. AppVeyor, zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="663e8-107">We’ll also show you how to perform these tasks by using the command line so that you can integrate with other build systems such as AppVeyor.</span></span>

## <a name="select-the-right-type-of-build-agent"></a><span data-ttu-id="663e8-108">Die Wahl des richtigen Build-Agents</span><span class="sxs-lookup"><span data-stu-id="663e8-108">Select the right type of build agent</span></span>

<span data-ttu-id="663e8-109">Wählen Sie aus, welche Art von Build-Agent VSTS beim Ausführen des Buildprozesses verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="663e8-109">Choose the type of build agent that you want VSTS to use when it executes the build process.</span></span>
<span data-ttu-id="663e8-110">Ein gehosteter Build-Agent wird mit den gängigsten Tools und SDKs bereitgestellt und bietet Unterstützung für die meisten Szenarien. Weitere Informationen finden Sie im Artikel zu [Software auf dem gehosteten Buildserver](https://www.visualstudio.com/docs/build/admin/agents/hosted-pool#software).</span><span class="sxs-lookup"><span data-stu-id="663e8-110">A hosted build agent is deployed with the most common tools and sdks, and it will work for most scenarios, see the [Software on the hosted build server](https://www.visualstudio.com/docs/build/admin/agents/hosted-pool#software) article.</span></span> <span data-ttu-id="663e8-111">Wenn Sie jedoch mehr Kontrolle über die Buildschritte benötigen, können Sie auch einen benutzerdefinierten Build-Agent erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-111">However, you can create a custom build agent if you need more control over the build steps.</span></span> <span data-ttu-id="663e8-112">Die folgende Tabelle soll Sie bei der richtigen Entscheidung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="663e8-112">You can use the following table to help you make that decision.</span></span>

| **<span data-ttu-id="663e8-113">Szenario</span><span class="sxs-lookup"><span data-stu-id="663e8-113">Scenario</span></span>** | **<span data-ttu-id="663e8-114">Benutzerdefinierter Agent</span><span class="sxs-lookup"><span data-stu-id="663e8-114">Custom Agent</span></span>** | **<span data-ttu-id="663e8-115">Gehosteter Build-Agent</span><span class="sxs-lookup"><span data-stu-id="663e8-115">Hosted Build Agent</span></span>** |
|-------------|----------------|----------------------|
| <span data-ttu-id="663e8-116">Grundlegender UWP-Build (einschließlich .NET Native)</span><span class="sxs-lookup"><span data-stu-id="663e8-116">Basic UWP build (including .NET native)</span></span>| <span data-ttu-id="663e8-117">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-117">:white_check_mark:</span></span> | <span data-ttu-id="663e8-118">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-118">:white_check_mark:</span></span> |
| <span data-ttu-id="663e8-119">Generieren von Paketen für das Querladen</span><span class="sxs-lookup"><span data-stu-id="663e8-119">Generate packages for Sideloading</span></span>| <span data-ttu-id="663e8-120">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-120">:white_check_mark:</span></span> | <span data-ttu-id="663e8-121">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-121">:white_check_mark:</span></span> |
| <span data-ttu-id="663e8-122">Generieren von Paketen für die Übermittlung an den Store</span><span class="sxs-lookup"><span data-stu-id="663e8-122">Generate packages for Store submission</span></span>| <span data-ttu-id="663e8-123">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-123">:white_check_mark:</span></span> | <span data-ttu-id="663e8-124">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-124">:white_check_mark:</span></span> |
| <span data-ttu-id="663e8-125">Verwenden benutzerdefinierter Zertifikate</span><span class="sxs-lookup"><span data-stu-id="663e8-125">Use custom certificates</span></span>| <span data-ttu-id="663e8-126">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-126">:white_check_mark:</span></span> | |
| <span data-ttu-id="663e8-127">Spezieller Build für ein benutzerdefiniertes Windows SDK</span><span class="sxs-lookup"><span data-stu-id="663e8-127">Build targeting a custom Windows SDK</span></span>| <span data-ttu-id="663e8-128">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-128">:white_check_mark:</span></span> |  |
| <span data-ttu-id="663e8-129">Ausführen von Komponententests</span><span class="sxs-lookup"><span data-stu-id="663e8-129">Run unit tests</span></span>| <span data-ttu-id="663e8-130">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-130">:white_check_mark:</span></span> |  |
| <span data-ttu-id="663e8-131">Verwenden inkrementeller Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-131">Use incremental builds</span></span>| <span data-ttu-id="663e8-132">:white_check_mark:</span><span class="sxs-lookup"><span data-stu-id="663e8-132">:white_check_mark:</span></span> |  |

#### <a name="create-a-custom-build-agent-optional"></a><span data-ttu-id="663e8-133">Erstellen eines benutzerdefinierten Build-Agents (optional)</span><span class="sxs-lookup"><span data-stu-id="663e8-133">Create a custom build agent (optional)</span></span>

<span data-ttu-id="663e8-134">Wenn Sie einen benutzerdefinierten Build-Agent erstellen möchten, benötigen Sie die Tools für die universelle Windows-Plattform.</span><span class="sxs-lookup"><span data-stu-id="663e8-134">If you choose to create a custom build agent, you’ll need the Universal Windows Platform tools.</span></span> <span data-ttu-id="663e8-135">Diese Tools sind Bestandteil von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="663e8-135">These tools are part of Visual Studio.</span></span> <span data-ttu-id="663e8-136">Sie können Visual Studio Community Edition verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-136">You can use the community edition of Visual Studio.</span></span>

<span data-ttu-id="663e8-137">Weitere Informationen finden Sie unter [Bereitstellen eines Agents unter Windows](https://www.visualstudio.com/docs/build/admin/agents/v2-windows).</span><span class="sxs-lookup"><span data-stu-id="663e8-137">To learn more, see [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/admin/agents/v2-windows).</span></span>

<span data-ttu-id="663e8-138">Zum Ausführen von UWP-Komponententests müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="663e8-138">To run UWP unit tests, you’ll have to do these things:</span></span>

- <span data-ttu-id="663e8-139">Bereitstellen und Starten Ihrer App</span><span class="sxs-lookup"><span data-stu-id="663e8-139">Deploy and start your app</span></span>
- <span data-ttu-id="663e8-140">Ausführen des VSTS-Agents im interaktiven Modus</span><span class="sxs-lookup"><span data-stu-id="663e8-140">Run the VSTS agent in interactive mode</span></span>
- <span data-ttu-id="663e8-141">Konfigurieren des Agents für die automatische Anmeldung nach einem Neustart</span><span class="sxs-lookup"><span data-stu-id="663e8-141">Configure your agent to auto-logon after a reboot</span></span>

## <a name="set-up-an-automated-build"></a><span data-ttu-id="663e8-142">Einrichten eines automatisierten Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-142">Set up an automated build</span></span>

<span data-ttu-id="663e8-143">Wir beginnen mit der standardmäßigen UWP-Builddefinition, die in VSTS verfügbar ist, und erläutern dann, wie Sie diese Definition so konfigurieren, dass erweiterte Buildaufgaben ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="663e8-143">We’ll start with the default UWP build definition that’s available in VSTS and then show you how to configure that definition so that you can accomplish more advanced build tasks.</span></span>

**<span data-ttu-id="663e8-144">Hinzufügen des Projektzertifikats zu einem Quellcoderepository</span><span class="sxs-lookup"><span data-stu-id="663e8-144">Add the certificate of your project to a source code repository</span></span>**

<span data-ttu-id="663e8-145">VSTS unterstützt sowohl TFS- als auch Git-basierte Coderepositorys.</span><span class="sxs-lookup"><span data-stu-id="663e8-145">VSTS works with both TFS and GIT based code repositories.</span></span>
<span data-ttu-id="663e8-146">Bei Verwendung eines Git-Repositorys fügen Sie die Zertifikatdatei Ihres Projekts dem Repository hinzu, damit der Build-Agent das App-Paket signieren kann.</span><span class="sxs-lookup"><span data-stu-id="663e8-146">If you use a Git repository, add the certificate file of your project to the repository so that the build agent can sign the app package.</span></span> <span data-ttu-id="663e8-147">Andernfalls wird die Zertifikatdatei vom Git-Repository ignoriert.</span><span class="sxs-lookup"><span data-stu-id="663e8-147">If you don’t do this, the Git repository will ignore the certificate file.</span></span>
<span data-ttu-id="663e8-148">Zum Hinzufügen der Zertifikatdatei zum Repository klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Zertifikatdatei und wählen dann im Kontextmenü den Befehl „Ignorierte Datei zur Quellcodeverwaltung hinzufügen“ aus.</span><span class="sxs-lookup"><span data-stu-id="663e8-148">To add the certificate file to your repository, right-click the certificate file in Solution Explorer, and then in the shortcut menu, choose the Add Ignored File to Source Control command.</span></span>

![Einschließen eines Zertifikats](images/building-screen1.png)

<span data-ttu-id="663e8-150">Die [erweiterte Zertifikatverwaltung](#certificates-best-practices) wird weiter unten in diesem Leitfaden erläutert.</span><span class="sxs-lookup"><span data-stu-id="663e8-150">We’ll discuss [advanced certificate management](#certificates-best-practices) later in this guide.</span></span>

<span data-ttu-id="663e8-151">Um die erste Builddefinition in VSTS zu erstellen, navigieren Sie zur Registerkarte „Builds“ und wählen dann die Schaltfläche „+“ aus.</span><span class="sxs-lookup"><span data-stu-id="663e8-151">To create your first build definition in VSTS, navigate to the Builds tab, and then select the + button.</span></span>

![Erstellen der Builddefinition](images/building-screen2.png)

<span data-ttu-id="663e8-153">Wählen Sie in der Liste der Builddefinitionsvorlagen die Vorlage *Universelle Windows-Plattform* aus.</span><span class="sxs-lookup"><span data-stu-id="663e8-153">In the list of build definition templates, choose the *Universal Windows Platform* template.</span></span>

![Auswählen des UWP-Builds](images/building-screen3.png)

<span data-ttu-id="663e8-155">Diese Builddefinition enthält die folgenden Buildaufgaben:</span><span class="sxs-lookup"><span data-stu-id="663e8-155">This build definition contains the following build tasks:</span></span>

- <span data-ttu-id="663e8-156">NuGet-Wiederherstellung \*\*\*.sln</span><span class="sxs-lookup"><span data-stu-id="663e8-156">NuGet restore \*\*\*.sln</span></span>
- <span data-ttu-id="663e8-157">Projektmappe erstellen \*\*\*.sln</span><span class="sxs-lookup"><span data-stu-id="663e8-157">Build solution \*\*\*.sln</span></span>
- <span data-ttu-id="663e8-158">Symbole veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="663e8-158">Publish Symbols</span></span>
- <span data-ttu-id="663e8-159">Artefakt veröffentlichen: Drop</span><span class="sxs-lookup"><span data-stu-id="663e8-159">Publish Artifact: drop</span></span>

#### <a name="configure-the-nuget-restore-build-task"></a><span data-ttu-id="663e8-160">Konfigurieren der Buildaufgabe „NuGet-Wiederherstellen“</span><span class="sxs-lookup"><span data-stu-id="663e8-160">Configure the NuGet restore build task</span></span>

<span data-ttu-id="663e8-161">Mit dieser Aufgabe werden die in Ihrem Projekt definierten NuGet-Pakete wiederhergestellt.</span><span class="sxs-lookup"><span data-stu-id="663e8-161">This task restores the NuGet Packages that are defined in your project.</span></span> <span data-ttu-id="663e8-162">Für einige Pakete ist eine benutzerdefinierte Version von „NuGet.exe“ erforderlich.</span><span class="sxs-lookup"><span data-stu-id="663e8-162">Some packages require a custom version of NuGet.exe.</span></span> <span data-ttu-id="663e8-163">Bei Verwendung eines Pakets, das eine benutzerdefinierte Version erfordert, verweisen Sie erst in Ihrem Repository auf die Version von „NuGet.exe“ und dann in der erweiterten Eigenschaft *Pfad zu „NuGet.exe“*.</span><span class="sxs-lookup"><span data-stu-id="663e8-163">If you’re using a package that requires one, refer to that version NuGet.exe in your repo and then reference it in the *Path to NuGet.exe* advanced property.</span></span>

![Standardbuilddefinition](images/building-screen4.png)

#### <a name="configure-the-build-solution-build-task"></a><span data-ttu-id="663e8-165">Konfigurieren der Buildaufgabe „Projektmappe erstellen“</span><span class="sxs-lookup"><span data-stu-id="663e8-165">Configure the Build solution build task</span></span>

<span data-ttu-id="663e8-166">Mit dieser Aufgabe wird jede Lösung, die im Arbeitsordner auf Binärdateien und erzeugt die Ausgabedatei für app-Paket kompiliert.</span><span class="sxs-lookup"><span data-stu-id="663e8-166">This task compiles any solution that’s in the working folder to binaries and produces the output app package file.</span></span>
<span data-ttu-id="663e8-167">In dieser Aufgabe werden MSBuild-Argumente verwendet.</span><span class="sxs-lookup"><span data-stu-id="663e8-167">This task uses MSbuild arguments.</span></span>  <span data-ttu-id="663e8-168">Sie müssen den Wert dieser Argumente angeben.</span><span class="sxs-lookup"><span data-stu-id="663e8-168">You’ll have to specify the value of those arguments.</span></span> <span data-ttu-id="663e8-169">Orientieren Sie sich an der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="663e8-169">Use the following table as a guide.</span></span>

|**<span data-ttu-id="663e8-170">MSBuild-Argument</span><span class="sxs-lookup"><span data-stu-id="663e8-170">MSBuild Argument</span></span>**|**<span data-ttu-id="663e8-171">Wert</span><span class="sxs-lookup"><span data-stu-id="663e8-171">Value</span></span>**|**<span data-ttu-id="663e8-172">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="663e8-172">Description</span></span>**|
|--------------------|---------|---------------|
|<span data-ttu-id="663e8-173">AppxPackageDir</span><span class="sxs-lookup"><span data-stu-id="663e8-173">AppxPackageDir</span></span>|<span data-ttu-id="663e8-174">$(Build.ArtifactStagingDirectory)\AppxPackages</span><span class="sxs-lookup"><span data-stu-id="663e8-174">$(Build.ArtifactStagingDirectory)\AppxPackages</span></span>|<span data-ttu-id="663e8-175">Definiert den Ordner, in dem die generierten Artefakte gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-175">Defines the folder to store the generated artifacts.</span></span>|
|<span data-ttu-id="663e8-176">AppxBundlePlatforms</span><span class="sxs-lookup"><span data-stu-id="663e8-176">AppxBundlePlatforms</span></span>|<span data-ttu-id="663e8-177">$(Build.BuildPlatform)</span><span class="sxs-lookup"><span data-stu-id="663e8-177">$(Build.BuildPlatform)</span></span>|<span data-ttu-id="663e8-178">Sie können festlegen, welche Plattformen im Bündel enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="663e8-178">Allows you to define the platforms to include in the bundle.</span></span>|
|<span data-ttu-id="663e8-179">AppxBundle</span><span class="sxs-lookup"><span data-stu-id="663e8-179">AppxBundle</span></span>|<span data-ttu-id="663e8-180">Always</span><span class="sxs-lookup"><span data-stu-id="663e8-180">Always</span></span>|<span data-ttu-id="663e8-181">Erstellt ein APPX-Bündel mit den APPX-Dateien für die angegebene Plattform.</span><span class="sxs-lookup"><span data-stu-id="663e8-181">Creates an appxbundle with the appx files for the platform specified.</span></span>|
|**<span data-ttu-id="663e8-182">UapAppxPackageBuildMode</span><span class="sxs-lookup"><span data-stu-id="663e8-182">UapAppxPackageBuildMode</span></span>**|<span data-ttu-id="663e8-183">StoreUpload</span><span class="sxs-lookup"><span data-stu-id="663e8-183">StoreUpload</span></span>|<span data-ttu-id="663e8-184">Definiert die Art des zu generierenden App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="663e8-184">Defines the kind of app package to generate.</span></span> <span data-ttu-id="663e8-185">(Standardmäßig nicht enthalten)</span><span class="sxs-lookup"><span data-stu-id="663e8-185">(Not included by default)</span></span>|

<span data-ttu-id="663e8-186">Wenn Sie Ihre Projektmappe über die Befehlszeile oder mit einem anderen Buildsystem erstellen möchten, führen Sie MSBuild mit diesen Argumenten aus.</span><span class="sxs-lookup"><span data-stu-id="663e8-186">If you want to build your solution by using the command line, or by using any other build system, run msbuild with these arguments.</span></span>

```ps
/p:AppxPackageDir="$(Build.ArtifactStagingDirectory)\AppxPackages\\"
/p:UapAppxPackageBuildMode=StoreUpload
/p:AppxBundlePlatforms="$(Build.BuildPlatform)"
/p:AppxBundle=Always
```

<span data-ttu-id="663e8-187">Die mit der $()-Syntax definierten Parameter sind Variablen, die in der Builddefinition definiert sind und sich in anderen Buildsystemen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="663e8-187">The parameters defined with the $() syntax are variables defined in the build definition, and will change in other build systems.</span></span>

![Standardvariablen](images/building-screen5.png)

<span data-ttu-id="663e8-189">Unter [Verwenden von Buildvariablen](https://www.visualstudio.com/docs/build/define/variables) sind alle vordefinierten Variablen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="663e8-189">To view all predefined variables, see [Use build variables.](https://www.visualstudio.com/docs/build/define/variables)</span></span>

#### <a name="configure-the-publish-artifact-build-task"></a><span data-ttu-id="663e8-190">Konfigurieren der Buildaufgabe „Artefakt veröffentlichen“</span><span class="sxs-lookup"><span data-stu-id="663e8-190">Configure the Publish Artifact build task</span></span>

<span data-ttu-id="663e8-191">Mit dieser Aufgabe werden die generierten Artefakte in VSTS gespeichert.</span><span class="sxs-lookup"><span data-stu-id="663e8-191">This task stores the generated artifacts in VSTS.</span></span> <span data-ttu-id="663e8-192">Sie werden auf der Registerkarte „Artefakte“ auf der Seite mit den Buildergebnissen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="663e8-192">You can see them in the Artifacts tab of the build results page.</span></span>
<span data-ttu-id="663e8-193">VSTS verwendet den zuvor definierten Ordner `$(Build.ArtifactStagingDirectory)\AppxPackages`.</span><span class="sxs-lookup"><span data-stu-id="663e8-193">VSTS uses the `$(Build.ArtifactStagingDirectory)\AppxPackages` folder that we previously defined.</span></span>

![Artefakte](images/building-screen6.png)

<span data-ttu-id="663e8-195">Da wir die `UapAppxPackageBuildMode`-Eigenschaft auf `StoreUpload` festlegen, enthält der Artefaktordner das Paket, das für die Übermittlung an den Store empfohlen ist (.appxupload).</span><span class="sxs-lookup"><span data-stu-id="663e8-195">Because we’ve set the `UapAppxPackageBuildMode` property to `StoreUpload`, the artifacts folder includes the package that recommended for submission to the Store (.appxupload).</span></span> <span data-ttu-id="663e8-196">Beachten Sie, dass Sie auch ein normales app-Paket (.appx/.msix) oder ein app-Bündel (.appxbundle/.msixbundle) an den Store übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="663e8-196">Note that you can also submit a regular app pacakge (.appx/.msix) or an app bundle (.appxbundle/.msixbundle) to the Store.</span></span> <span data-ttu-id="663e8-197">Für die Zwecke dieses Artikels verwenden wir die appxupload-Datei.</span><span class="sxs-lookup"><span data-stu-id="663e8-197">For the purposes of this article, we'll use the .appxupload file.</span></span>

>[!NOTE]
> <span data-ttu-id="663e8-198">Der VSTS-Agent behält standardmäßig die letzten generierten App-Pakete bei.</span><span class="sxs-lookup"><span data-stu-id="663e8-198">By default, the VSTS agent maintains the latest generated app packages.</span></span> <span data-ttu-id="663e8-199">Wenn Sie nur die Artefakte des aktuellen Builds speichern möchten, konfigurieren Sie den Build so, dass das Verzeichnis mit Binärdateien bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="663e8-199">If you want to store only the artifacts of the current build, configure the build to clean the binaries directory.</span></span> <span data-ttu-id="663e8-200">Fügen Sie dazu eine Variable namens `Build.Clean` hinzu, und legen Sie sie auf den Wert `all` fest.</span><span class="sxs-lookup"><span data-stu-id="663e8-200">To do that, add a variable named `Build.Clean` and then set it to the value `all`.</span></span> <span data-ttu-id="663e8-201">Weitere Informationen finden Sie unter [Angeben des Repositorys](https://www.visualstudio.com/docs/build/define/repository#how-can-i-clean-the-repository-in-a-different-way).</span><span class="sxs-lookup"><span data-stu-id="663e8-201">To learn more, see [Specify the repository](https://www.visualstudio.com/docs/build/define/repository#how-can-i-clean-the-repository-in-a-different-way).</span></span>

#### <a name="the-types-of-automated-builds"></a><span data-ttu-id="663e8-202">Typen automatisierter Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-202">The types of automated builds</span></span>

<span data-ttu-id="663e8-203">Als Nächstes verwenden Sie die Builddefinition zum Erstellen eines automatisierten Builds.</span><span class="sxs-lookup"><span data-stu-id="663e8-203">Next, you’ll use your build definition to create an automated build.</span></span> <span data-ttu-id="663e8-204">In der folgenden Tabelle werden die einzelnen Typen automatisierter Builds beschrieben, die Sie erstellen können.</span><span class="sxs-lookup"><span data-stu-id="663e8-204">The following table describes each type of automated build that you can create.</span></span>

|**<span data-ttu-id="663e8-205">Buildtyp</span><span class="sxs-lookup"><span data-stu-id="663e8-205">Type of Build</span></span>**|**<span data-ttu-id="663e8-206">Artefakt</span><span class="sxs-lookup"><span data-stu-id="663e8-206">Artifact</span></span>**|**<span data-ttu-id="663e8-207">Empfohlene Häufigkeit</span><span class="sxs-lookup"><span data-stu-id="663e8-207">Recommended Frequency</span></span>**|**<span data-ttu-id="663e8-208">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="663e8-208">Description</span></span>**|
|-----------------|------------|-------------------------|---------------|
|<span data-ttu-id="663e8-209">Continuous Integration</span><span class="sxs-lookup"><span data-stu-id="663e8-209">Continuous Integration</span></span>|<span data-ttu-id="663e8-210">Buildprotokoll, Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="663e8-210">Build Log, Test Results</span></span>|<span data-ttu-id="663e8-211">Jeder Commit</span><span class="sxs-lookup"><span data-stu-id="663e8-211">Each commit</span></span>|<span data-ttu-id="663e8-212">Dieser Buildtyp ist schnell und wird mehrmals täglich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="663e8-212">This type of build is fast and run several times a day.</span></span>|
|<span data-ttu-id="663e8-213">Continuous Deployment-Build zum Querladen</span><span class="sxs-lookup"><span data-stu-id="663e8-213">Continuous Deployment build for sideloading</span></span>|<span data-ttu-id="663e8-214">Bereitstellungspakete</span><span class="sxs-lookup"><span data-stu-id="663e8-214">Deployment Packages</span></span>|<span data-ttu-id="663e8-215">Täglich</span><span class="sxs-lookup"><span data-stu-id="663e8-215">Daily</span></span> |<span data-ttu-id="663e8-216">Dieser Buildtyp kann Komponententests enthalten, dauert jedoch etwas länger.</span><span class="sxs-lookup"><span data-stu-id="663e8-216">This type of build can Include unit tests but it takes a bit longer.</span></span> <span data-ttu-id="663e8-217">Er unterstützt manuelle Tests und kann in andere Tools, wie z.B. HockeyApp, integriert werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-217">It allows manual testing and you can integrate it with other tools such as HockeyApp.</span></span>|
|<span data-ttu-id="663e8-218">Continuous Deployment-Build, durch den ein Paket an den Store übermittelt wird</span><span class="sxs-lookup"><span data-stu-id="663e8-218">Continuous Deployment build that submits a package to the Store</span></span>|<span data-ttu-id="663e8-219">Veröffentlichungspakete</span><span class="sxs-lookup"><span data-stu-id="663e8-219">Publishing Packages</span></span>|<span data-ttu-id="663e8-220">Bedarfsgesteuert</span><span class="sxs-lookup"><span data-stu-id="663e8-220">On demand</span></span>|<span data-ttu-id="663e8-221">Durch diesen Buildtyp wird ein Paket erstellt, das Sie im Store veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="663e8-221">This type of build creates a package that you can publish to the Store.</span></span>|

<span data-ttu-id="663e8-222">Im Folgenden wird die Konfiguration der einzelnen Typen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="663e8-222">Let’s look at how to configure each one.</span></span>

## <a name="set-up-a-continuous-integration-ci-build"></a><span data-ttu-id="663e8-223">Einrichten eines Continuous Integration (CI)-Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-223">Set up a Continuous Integration (CI) build</span></span>

<span data-ttu-id="663e8-224">Dieser Buildtyp ermöglicht die schnelle Diagnose codebezogener Probleme.</span><span class="sxs-lookup"><span data-stu-id="663e8-224">This type of a build helps you to diagnose code related problems quickly.</span></span> <span data-ttu-id="663e8-225">Er wird in der Regel nur für eine Plattform ausgeführt und muss nicht durch die .NET Native-Toolkette verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-225">They’re typically executed for only one platform, and they don’t need to be processed by the .NET native toolchain.</span></span> <span data-ttu-id="663e8-226">Außerdem können Sie mit CI-Builds Komponententests ausführen, durch die ein Bericht mit Testergebnissen erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="663e8-226">Also, with CI builds, you can run unit tests that produce a test results report.</span></span>

<span data-ttu-id="663e8-227">Wenn Sie UWP-Komponententests im Rahmen Ihres CI-Builds ausführen möchten, müssen Sie einen benutzerdefinierten Build-Agent anstelle des gehosteten Build-Agents verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-227">If you want to run UWP unit tests as part of your CI build you’ll need to use a custom build agent instead of the hosted build agent.</span></span>

>[!NOTE]
> <span data-ttu-id="663e8-228">Wenn Sie mehr als eine App in der gleichen Projektmappe bündeln, erhalten Sie möglicherweise eine Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="663e8-228">If you bundle more than one app in the same solution, you might receive an error.</span></span> <span data-ttu-id="663e8-229">Unterstützung beim Beheben dieses Fehlers finden Sie im Thema [Beheben von Fehlern, die beim Bündeln von mehr als einer App in derselben Projektmappe auftreten](#bundle-errors).</span><span class="sxs-lookup"><span data-stu-id="663e8-229">See the following topic for help resolving that error: [Address errors that appear when you bundle more than one app in the same solution.](#bundle-errors)</span></span>

### <a name="configure-a-ci-build-definition"></a><span data-ttu-id="663e8-230">Konfigurieren einer CI-Builddefinition</span><span class="sxs-lookup"><span data-stu-id="663e8-230">Configure a CI build definition</span></span>

<span data-ttu-id="663e8-231">Verwenden Sie die UWP-Standardvorlage, um eine Builddefinition zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-231">Use the default UWP template to create a build definition.</span></span> <span data-ttu-id="663e8-232">Konfigurieren Sie dann den Trigger, der bei jedem Einchecken ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="663e8-232">Then, configure the Trigger to execute on each check in.</span></span>

![CI-Trigger](images/building-screen7.png)

<span data-ttu-id="663e8-234">Da der CI-Build nicht für Benutzer bereitgestellt wird, ist es ratsam, unterschiedliche Versionsnummern zu verwenden, um Verwechslungen mit den CD-Builds zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="663e8-234">Because the CI build won’t be deployed to users, it’s a good idea to maintain different versioning numbers to avoid confusion with the CD builds.</span></span> <span data-ttu-id="663e8-235">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="663e8-235">For example:</span></span>
`$(BuildDefinitionName)_0.0.$(DayOfYear)$(Rev:.r)`

#### <a name="configure-a-custom-build-agent-for-unit-testing"></a><span data-ttu-id="663e8-236">Konfigurieren eines benutzerdefinierten Build-Agents für Komponententests</span><span class="sxs-lookup"><span data-stu-id="663e8-236">Configure a custom build agent for unit testing</span></span>

1. <span data-ttu-id="663e8-237">Aktivieren Sie den Entwicklermodus auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="663e8-237">Enable Developer Mode on your PC.</span></span> <span data-ttu-id="663e8-238">Weitere Infos finden Sie unter [Aktivieren des Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development).</span><span class="sxs-lookup"><span data-stu-id="663e8-238">See [Enable your device for development](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) for more information.</span></span>
2. <span data-ttu-id="663e8-239">Ermöglichen Sie die Ausführung des Diensts als interaktiver Prozess.</span><span class="sxs-lookup"><span data-stu-id="663e8-239">Enable the service to run as an interactive process.</span></span> <span data-ttu-id="663e8-240">Weitere Informationen finden Sie unter [Bereitstellen eines Agents unter Windows](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows).</span><span class="sxs-lookup"><span data-stu-id="663e8-240">To learn more, see [Deploy an agent on Windows](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows).</span></span>
3. <span data-ttu-id="663e8-241">Stellen Sie das Signaturzertifikat für den Agent bereit.</span><span class="sxs-lookup"><span data-stu-id="663e8-241">Deploy the signing certificate to the agent.</span></span>

<span data-ttu-id="663e8-242">Doppelklicken Sie zum Bereitstellen eines Signaturzertifikats auf die `.cer`-Datei, wählen Sie **Lokaler Computer** aus, und wählen Sie dann den **Speicher für vertrauenswürdige Personen** aus.</span><span class="sxs-lookup"><span data-stu-id="663e8-242">To deploy a signing certificate, double-click the `.cer` file, choose **Local Machine**, and then choose **Trusted People Store**.</span></span>

<span id="uwp-unit-tests" />

### <a name="configure-the-build-definition-to-run-uwp-unit-tests"></a><span data-ttu-id="663e8-243">Konfigurieren der Builddefinition für die Ausführung von UWP-Komponententests</span><span class="sxs-lookup"><span data-stu-id="663e8-243">Configure the build definition to run UWP Unit Tests</span></span>

<span data-ttu-id="663e8-244">Verwenden Sie zum Ausführen von Komponententests den Visual Studio Test-Buildschritt.</span><span class="sxs-lookup"><span data-stu-id="663e8-244">To execute a unit test, use the Visual Studio Test build step.</span></span>

![Hinzufügen von Komponententests](images/building-screen8.png)

<span data-ttu-id="663e8-246">Da UWP-Komponententests im Kontext einer bestimmten appxrecipe-Datei ausgeführt werden, ist es nicht möglich, das generierte Bündel zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-246">UWP unit tests are executed in the context of a given appxrecipe file so you can’t use the generated bundle.</span></span> <span data-ttu-id="663e8-247">Außerdem müssen Sie den Pfad zu einer konkreten appxrecipe-Plattformdatei angeben.</span><span class="sxs-lookup"><span data-stu-id="663e8-247">Also, you’ll have to specify the path to a concrete platform appxrecipe file.</span></span> <span data-ttu-id="663e8-248">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="663e8-248">For example:</span></span>

```ps
$(Build.ArtifactStagingDirectory)\AppxPackages\MyUWPApp.UnitTest\x86\MyUWPApp.UnitTest_$(AppxVersion)_x86.appxrecipe
```

<span data-ttu-id="663e8-249">Damit die Tests ausgeführt werden können, muss der vstest.console.exe-Datei ein Konsolenparameter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-249">In order for the tests to run a console parameter will have to be added to vstest.console.exe.</span></span> <span data-ttu-id="663e8-250">Dieser Parameter kann über **Ausführungsoptionen => Andere Konsolenoptionen** bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-250">This parameter can be provide through: **Execution Options => Other console options**.</span></span> <span data-ttu-id="663e8-251">Fügen Sie bitte die folgenden Parameter hinzu:</span><span class="sxs-lookup"><span data-stu-id="663e8-251">Please add following parameter:</span></span>

```ps
/framework:FrameworkUap10
```

>[!NOTE]
> <span data-ttu-id="663e8-252">Verwenden Sie den folgenden Befehl, um die Komponententests lokal über die Befehlszeile auszuführen:</span><span class="sxs-lookup"><span data-stu-id="663e8-252">Use the following command to execute the unit tests locally from the command line:</span></span>
`"%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE\CommonExtensions\Microsoft\TestWindow\vstest.console.exe"`

#### <a name="access-test-results"></a><span data-ttu-id="663e8-253">Zugreifen auf Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="663e8-253">Access test results</span></span>

<span data-ttu-id="663e8-254">In VSTS werden auf der Seite „Buildzusammenfassung“ Testergebnisse für jeden Build angezeigt, der Komponententests ausführt.</span><span class="sxs-lookup"><span data-stu-id="663e8-254">In VSTS, the build summary page shows the test results for each build that executes unit tests.</span></span> <span data-ttu-id="663e8-255">Dort können Sie die Seite **Testergebnisse** öffnen, um weitere Details zu den Testergebnissen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="663e8-255">From there, you can open the **Test Results** page to see more detail about the test results.</span></span>

![Testergebnisse](images/building-screen9.png)

#### <a name="improve-the-speed-of-a-ci-build"></a><span data-ttu-id="663e8-257">Verbessern der Geschwindigkeit eines CI-Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-257">Improve the speed of a CI build</span></span>

<span data-ttu-id="663e8-258">Wenn Sie Ihren CI-Build nur verwenden möchten, um die Qualität der Eincheckvorgänge zu überwachen, können Sie Ihre Buildzeiten verringern.</span><span class="sxs-lookup"><span data-stu-id="663e8-258">If you want to use your CI build only to monitor the quality of your check-ins, you can reduce your build times.</span></span>

#### <a name="to-improve-the-speed-of-a-ci-build"></a><span data-ttu-id="663e8-259">So verbessern Sie die Geschwindigkeit eines CI-Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-259">To improve the speed of a CI build</span></span>

1. <span data-ttu-id="663e8-260">Erstellen Sie den Build nur für eine Plattform.</span><span class="sxs-lookup"><span data-stu-id="663e8-260">Build for only one platform.</span></span>
2. <span data-ttu-id="663e8-261">Bearbeiten Sie die BuildPlatform-Variable, um nur x86 zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-261">Edit the BuildPlatform variable to use only x86.</span></span> ![CI-Konfiguration](images/building-screen10.png)
3. <span data-ttu-id="663e8-263">Fügen Sie im Buildschritt „/p:AppxBundle=Never“ zur Eigenschaft „MSBuild-Argumente“ hinzu, und legen Sie die Eigenschaft „Plattform“ fest.</span><span class="sxs-lookup"><span data-stu-id="663e8-263">In the build step, add /p:AppxBundle=Never to the MSBuild Arguments property, and then set the Platform property.</span></span> ![Konfigurieren der Plattform](images/building-screen11.png)
4. <span data-ttu-id="663e8-265">Deaktivieren Sie im Komponententestprojekt .NET Native.</span><span class="sxs-lookup"><span data-stu-id="663e8-265">In the unit test project, disable .NET Native.</span></span>

<span data-ttu-id="663e8-266">Öffnen Sie dazu die Projektdatei, und legen Sie die `UseDotNetNativeToolchain`-Eigenschaft in den Projekteigenschaften auf `false` fest.</span><span class="sxs-lookup"><span data-stu-id="663e8-266">To do that, open the project file, and in the project properties, set the `UseDotNetNativeToolchain` property to `false`.</span></span>

<span data-ttu-id="663e8-267">Die Verwendung der .NET Native-Toolkette stellt immer noch einen wichtigen Bestandteil des Workflows dar und sollte weiterhin zum Testen von Releasebuilds verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-267">Using the .NET native tool chain is an important part of the workflow and should still be used to test release builds.</span></span>

<span id="bundle-errors" />

#### <a name="address-errors-that-appear-when-you-bundle-more-than-one-app-in-the-same-solution"></a><span data-ttu-id="663e8-268">Beheben von Fehlern, die beim Bündeln von mehr als einer App in derselben Projektmappe auftreten</span><span class="sxs-lookup"><span data-stu-id="663e8-268">Address errors that appear when you bundle more than one app in the same solution</span></span>

<span data-ttu-id="663e8-269">Wenn Sie Ihrer Projektmappe mehr als ein UWP-Projekt hinzufügen und dann versuchen, ein Bündel zu erstellen, erhalten Sie möglicherweise eine mit der folgenden vergleichbare Fehlermeldung:</span><span class="sxs-lookup"><span data-stu-id="663e8-269">If you add more than one UWP project to your solution, and then try to create a bundle, you might receive an error like this one:</span></span>

```ps
MakeAppx(0,0): Error : Error info: error 80080204: The package with file name "AppOne.UnitTests_0.1.2595.0_x86.appx" and package full name "8ef641d1-4557-4e33-957f-6895b122f1e6_0.1.2595.0_x86__scrj5wvaadcy6" is not valid in the bundle because it has a different package family name than other packages in the bundle
```

<span data-ttu-id="663e8-270">Dieser Fehler tritt auf, da auf Projektmappenebene nicht eindeutig ist, welche App im Bündel enthalten sein soll.</span><span class="sxs-lookup"><span data-stu-id="663e8-270">This error appears because at the solution level, it’s not clear which app should appear in the bundle.</span></span>
<span data-ttu-id="663e8-271">Um dieses Problem zu beheben, öffnen Sie jede Projektdatei und fügen am Ende des ersten `<PropertyGroup>`-Elements die folgenden Eigenschaften hinzu:</span><span class="sxs-lookup"><span data-stu-id="663e8-271">To resolve this issue, open each project file and add the following properties at the end of the first `<PropertyGroup>` element:</span></span>

|**<span data-ttu-id="663e8-272">Projekt</span><span class="sxs-lookup"><span data-stu-id="663e8-272">Project</span></span>**|**<span data-ttu-id="663e8-273">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="663e8-273">Properties</span></span>**|
|-------|----------|
|<span data-ttu-id="663e8-274">App</span><span class="sxs-lookup"><span data-stu-id="663e8-274">App</span></span>|`<AppxBundle>Always</AppxBundle>`|
|<span data-ttu-id="663e8-275">UnitTests</span><span class="sxs-lookup"><span data-stu-id="663e8-275">UnitTests</span></span>|`<AppxBundle>Never</AppxBundle>`|

<span data-ttu-id="663e8-276">Entfernen Sie dann das MSBuild-Argument `AppxBundle` aus dem Buildschritt.</span><span class="sxs-lookup"><span data-stu-id="663e8-276">Then, remove the `AppxBundle` msbuild argument from the build step.</span></span>

## <a name="set-up-a-continuous-deployment-build-for-sideloading"></a><span data-ttu-id="663e8-277">Einrichten eines Continuous Deployment-Builds zum Querladen</span><span class="sxs-lookup"><span data-stu-id="663e8-277">Set up a continuous deployment build for sideloading</span></span>

<span data-ttu-id="663e8-278">Wenn dieser Buildtyp abgeschlossen ist, können Benutzer die app-Bundle-Datei aus dem artefaktabschnitt der Seite mit den Buildergebnissen herunterladen.</span><span class="sxs-lookup"><span data-stu-id="663e8-278">When this type of build completes, users can download the app bundle file from the artifacts section of the build results page.</span></span>
<span data-ttu-id="663e8-279">Wenn Sie Betatests für die App durchführen möchten, indem Sie eine komplexere Verteilung erstellen, können Sie den HockeyApp-Dienst verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-279">If you want to beta test the app by creating a more complete distribution, you can use the HockeyApp service.</span></span> <span data-ttu-id="663e8-280">Dieser Dienst bietet erweiterte Funktionen für Betatests, Benutzeranalysen und Absturzdiagnosen.</span><span class="sxs-lookup"><span data-stu-id="663e8-280">This service offers advanced capabilities for beta testing, user analytics and crash diagnostics.</span></span>

### <a name="applying-version-numbers-to-your-builds"></a><span data-ttu-id="663e8-281">Anwenden von Versionsnummern auf Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-281">Applying version numbers to your builds</span></span>

<span data-ttu-id="663e8-282">Die Manifestdatei enthält die Versionsnummer der App.</span><span class="sxs-lookup"><span data-stu-id="663e8-282">The manifest file contains the app version number.</span></span>  <span data-ttu-id="663e8-283">Aktualisieren Sie die Manifestdatei im Repository der Quellcodeverwaltung, um die Versionsnummer zu ändern.</span><span class="sxs-lookup"><span data-stu-id="663e8-283">Update the manifest file in your source control repository to change the version number.</span></span>
<span data-ttu-id="663e8-284">Eine weitere Möglichkeit zum Aktualisieren der Versionsnummer Ihrer App besteht darin, die von VSTS generierte Buildnummer zu verwenden und dann das App-Manifest zu ändern, direkt bevor Sie die App kompilieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-284">Another way to update the version number of your app is to use the build number that is generated by VSTS, and then modify the app manifest just before you compile the app.</span></span> <span data-ttu-id="663e8-285">Sie dürfen diese Änderungen nur nicht im Quellcoderepository committen.</span><span class="sxs-lookup"><span data-stu-id="663e8-285">Just don’t commit those changes to the source code repository.</span></span>

<span data-ttu-id="663e8-286">Sie müssen das Format der Versionsbuildnummer in der Builddefinition definieren und dann mit der resultierenden Versionsnummer das AppxManifest und optional die Dateien „AssemblyInfo.cs“ aktualisieren, bevor Sie kompilieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-286">You’ll have to define your versioning build number format in the build definition, and then use the resulting version number to update the AppxManifest and optionally, the AssemblyInfo.cs files, before you compile.</span></span>

<span data-ttu-id="663e8-287">Definieren Sie das Buildnummernformat auf der Registerkarte *Allgemein* der Builddefinition.</span><span class="sxs-lookup"><span data-stu-id="663e8-287">Define the build number format in the *General* tab of your build definition.</span></span>

![Buildversion](images/building-screen12.png)

<span data-ttu-id="663e8-289">Angenommen, Sie legen das Buildnummernformat auf den folgenden Wert fest:</span><span class="sxs-lookup"><span data-stu-id="663e8-289">For example, if you set the build number format to the following value:</span></span>

```ps
$(BuildDefinitionName)_1.1.$(DayOfYear)$(Rev:r).0
```

<span data-ttu-id="663e8-290">In diesem Fall generiert VSTS eine Versionsnummer wie die Folgende:</span><span class="sxs-lookup"><span data-stu-id="663e8-290">VSTS generates a version number like:</span></span>

```ps
CI_MyUWPApp_1.1.2501.0
```

>[!NOTE]
><span data-ttu-id="663e8-291">Für den Store ist es erforderlich, dass die letzte Zahl in der Versionsangabe 0 lautet.</span><span class="sxs-lookup"><span data-stu-id="663e8-291">The Store will require that the last number in the version to be 0.</span></span>

<span data-ttu-id="663e8-292">Damit Sie die Versionsnummer extrahieren und auf die Manifestdateien und/oder `AssemblyInfo`-Dateien anwenden können, verwenden Sie ein benutzerdefiniertes PowerShell-Skript ([hier](https://go.microsoft.com/fwlink/?prd=12560&pver=14&plcid=0x409&clcid=0x9&ar=DevCenter&sar=docs) verfügbar).</span><span class="sxs-lookup"><span data-stu-id="663e8-292">So that you can extract the version number and apply it to the manifest and/or `AssemblyInfo` files, use a custom PowerShell script (available [here](https://go.microsoft.com/fwlink/?prd=12560&pver=14&plcid=0x409&clcid=0x9&ar=DevCenter&sar=docs)).</span></span> <span data-ttu-id="663e8-293">Das Skript liest die Versionsnummer aus der `BUILD_BUILDNUMBER`-Umgebungsvariablen und ändert dann die AssemblyInfo- und AppxManifest-Dateien.</span><span class="sxs-lookup"><span data-stu-id="663e8-293">That script reads the version number from the environment variable `BUILD_BUILDNUMBER`, and then modifies the AssemblyInfo and AppxManifest files.</span></span> <span data-ttu-id="663e8-294">Sie müssen dieses Skript Ihrem Quellrepository hinzufügen und dann eine PowerShell-Buildaufgabe konfigurieren, wie hier veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="663e8-294">Make sure to add this script to your source repository, and then configure a PowerShell build task as shown here:</span></span>

![Aktualisieren der Version](images/building-screen13.png)

<span data-ttu-id="663e8-296">Die `$(AppxVersion)`-Variable enthält die Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="663e8-296">The `$(AppxVersion)` variable contains the version number.</span></span> <span data-ttu-id="663e8-297">Sie können diese Nummer in anderen Buildschritten verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-297">You can use that number in other build steps.</span></span>

#### <a name="optional-integrate-with-hockeyapp"></a><span data-ttu-id="663e8-298">Optional: Integration in HockeyApp</span><span class="sxs-lookup"><span data-stu-id="663e8-298">Optional: Integrate with HockeyApp</span></span>

<span data-ttu-id="663e8-299">Installieren Sie zuerst die Visual Studio-Erweiterung [HockeyApp](https://marketplace.visualstudio.com/items?itemName=ms.hockeyapp).</span><span class="sxs-lookup"><span data-stu-id="663e8-299">First, install the [HockeyApp](https://marketplace.visualstudio.com/items?itemName=ms.hockeyapp) Visual Studio extension.</span></span> <span data-ttu-id="663e8-300">Sie müssen diese Erweiterung als VSTS-Administrator installieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-300">You will need to install this extension as a VSTS administrator.</span></span>

![HockeyApp](images/building-screen14.png)

<span data-ttu-id="663e8-302">Konfigurieren Sie als Nächstes die HockeyApp-Verbindung mithilfe dieser Anleitung: [How to use HockeyApp with Visual Studio Team Services (VSTS) or Team Foundation Server (TFS)](https://support.hockeyapp.net/kb/third-party-bug-trackers-services-and-webhooks/how-to-use-hockeyapp-with-visual-studio-team-services-vsts-or-team-foundation-server-tfs).</span><span class="sxs-lookup"><span data-stu-id="663e8-302">Next, configure the HockeyApp connection by using this guide: [How to use HockeyApp with Visual Studio Team Services (VSTS) or Team Foundation Server (TFS).](https://support.hockeyapp.net/kb/third-party-bug-trackers-services-and-webhooks/how-to-use-hockeyapp-with-visual-studio-team-services-vsts-or-team-foundation-server-tfs)</span></span>
<span data-ttu-id="663e8-303">Sie können Ihr Microsoft-Konto, ein Social Media-Konto oder einfach eine E-Mail-Adresse verwenden, um Ihr HockeyApp-Konto einzurichten.</span><span class="sxs-lookup"><span data-stu-id="663e8-303">You can use your Microsoft account, social media account or just an email address to set up your HockeyApp account.</span></span> <span data-ttu-id="663e8-304">Der kostenlose Plan umfasst zwei Apps, einen Besitzer und keine Dateneinschränkungen.</span><span class="sxs-lookup"><span data-stu-id="663e8-304">The free plan comes with two apps, one owner, and no data restrictions.</span></span>

<span data-ttu-id="663e8-305">Anschließend können Sie eine HockeyApp-app manuell oder indem Sie eine vorhandene app-Paketdatei hochladen erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-305">Then, you can create a HockeyApp app manually, or by uploading an existing app package file.</span></span> <span data-ttu-id="663e8-306">Weitere Informationen finden Sie unter [Erstellen einer neuen App](https://support.hockeyapp.net/kb/app-management-2/how-to-create-a-new-app).</span><span class="sxs-lookup"><span data-stu-id="663e8-306">To learn more, see [How to create a new app](https://support.hockeyapp.net/kb/app-management-2/how-to-create-a-new-app).</span></span>

<span data-ttu-id="663e8-307">Um eine vorhandene app-Paketdatei zu verwenden, fügen Sie einen Buildschritt hinzu, und legen Sie den Parameter binären Dateipfad des Buildschritts fest.</span><span class="sxs-lookup"><span data-stu-id="663e8-307">To use an existing app package file, add a build step, and set the Binary File Path parameter of the build step.</span></span>

![Konfigurieren von HockeyApp](images/building-screen15.png)

<span data-ttu-id="663e8-309">Um diesen Parameter festzulegen, kombinieren Sie den Namen der App, die AppxVersion-Variable und die unterstützten Plattformen in einer Zeichenfolge wie dieser:</span><span class="sxs-lookup"><span data-stu-id="663e8-309">To set this parameter, combine the app name, the AppxVersion variable and the supported platforms together into one string such as this one:</span></span>

```ps
$(Build.ArtifactStagingDirectory)\AppxPackages\MyUWPApp_$(AppxVersion)_Test\MyUWPApp_$(AppxVersion)_x86_x64_ARM.appxbundle
```

<span data-ttu-id="663e8-310">Obwohl die HockeyApp-Aufgabe den Pfad zur Symboldatei angeben kann, ist es eine bewährte Methode, die Symbole in das Bündel einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="663e8-310">Although the HockeyApp task allows you to specify the path to the symbols file, it’s a best practice to include the symbols with the bundle.</span></span>

## <a name="set-up-a-continuous-deployment-build-that-submits-a-package-to-the-store"></a><span data-ttu-id="663e8-311">Einrichten eines Continuous Deployment-Builds, durch den ein Paket an den Store übermittelt wird</span><span class="sxs-lookup"><span data-stu-id="663e8-311">Set up a continuous deployment build that submits a package to the Store</span></span>

<span data-ttu-id="663e8-312">Um Pakete für die Übermittlung an den Store zu generieren, verknüpfen Sie die App mithilfe des Assistenten für die Store-Verknüpfung in Visual Studio mit dem Store.</span><span class="sxs-lookup"><span data-stu-id="663e8-312">To generate Store submission packages, associate your app with the Store by using the Store Association Wizard in Visual Studio.</span></span>

![Verknüpfen mit dem Store](images/building-screen16.png)

<span data-ttu-id="663e8-314">Der Assistenten für die Store-Verknüpfung generiert eine Datei mit dem Namen „Package.StoreAssociation.xml“, die die Informationen zur Store-Verknüpfung enthält.</span><span class="sxs-lookup"><span data-stu-id="663e8-314">The Store Association Wizard generates a file named Package.StoreAssociation.xml that contains the Store association information.</span></span> <span data-ttu-id="663e8-315">Wenn Sie den Quellcode in einem öffentlichen Repository wie GitHub speichern, enthält diese Datei alle reservierten Namen der App für dieses Konto.</span><span class="sxs-lookup"><span data-stu-id="663e8-315">If you store your source code in a public repository such as GitHub, this file will contain all the app reserved names for that account.</span></span> <span data-ttu-id="663e8-316">Sie können diese Datei vor der Veröffentlichung ausschließen oder löschen.</span><span class="sxs-lookup"><span data-stu-id="663e8-316">You can exclude or delete this file before making it public.</span></span>

<span data-ttu-id="663e8-317">Wenn Sie keinen Zugriff auf das Partner Center-Konto haben, die zum Veröffentlichen der app verwendet wurde, können Sie die Anweisungen in diesem Dokument befolgen: [Erstellen einer app für eine 3rd Party? Wie Sie ihre Store-app zu verpacken](https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/#e35YzR5aRG6uaBqK.97).</span><span class="sxs-lookup"><span data-stu-id="663e8-317">If you don’t have access to the Partner Center account that was used to publish the app, you can follow the instructions in this document: [Building an app for a 3rd party? How to package their Store app](https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/#e35YzR5aRG6uaBqK.97).</span></span>

<span data-ttu-id="663e8-318">Anschließend müssen Sie sicherstellen, dass der Buildschritt den folgenden Parameter enthält:</span><span class="sxs-lookup"><span data-stu-id="663e8-318">Then you need to verify that the build step includes the following parameter:</span></span>

```ps
/p:UapAppxPackageBuildMode=StoreUpload
```

<span data-ttu-id="663e8-319">Dadurch wird eine Upload-Datei generiert, die an den Store übermittelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="663e8-319">This will generate an upload file that can be submitted to the Store.</span></span>

#### <a name="configure-automatic-store-submission"></a><span data-ttu-id="663e8-320">Konfigurieren der automatischen Übermittlung an den Store</span><span class="sxs-lookup"><span data-stu-id="663e8-320">Configure automatic Store submission</span></span>

<span data-ttu-id="663e8-321">Verwenden Sie für die Integration in die Store-API die Visual Studio Team Services-Erweiterung für den Microsoft Store, und senden Sie das App-Paket an den Store.</span><span class="sxs-lookup"><span data-stu-id="663e8-321">Use the Visual Studio Team Services extension for the Microsoft Store to integrate with the Store API, and send your app package to the Store.</span></span>

<span data-ttu-id="663e8-322">Sie müssen Ihr Partner Center-Konto mit Azure Active Directory (AD) verbinden, und erstellen Sie eine app in die Anzeige der Anforderungen zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-322">You need to connect your Partner Center account with Azure Active Directory (AD), and then create an app in your AD to authenticate the requests.</span></span> <span data-ttu-id="663e8-323">Befolgen Sie dazu die Anweisungen auf der Seite der Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="663e8-323">You can follow the guidance in the extension page to accomplish that.</span></span>

<span data-ttu-id="663e8-324">Nachdem Sie die Erweiterung konfiguriert haben, können Sie die Buildaufgabe hinzufügen und mit der app-ID und den Speicherort der Uploaddatei konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-324">Once you’ve configured the extension, you can add the build task, and configure it with your app ID and the location of the upload file.</span></span>

![Konfigurieren Sie das Partnercenter](images/building-screen17.png)

<span data-ttu-id="663e8-326">Der Wert des `Package File`-Parameters lautet dabei:</span><span class="sxs-lookup"><span data-stu-id="663e8-326">Where the value of the `Package File` parameter will be:</span></span>

```ps
$(Build.ArtifactStagingDirectory)\
AppxPackages\MyUWPApp__$(AppxVersion)_x86_x64_ARM_bundle.appxupload
```

<span data-ttu-id="663e8-327">Sie müssen diesen Build manuell aktivieren.</span><span class="sxs-lookup"><span data-stu-id="663e8-327">You have to manually activate this build.</span></span> <span data-ttu-id="663e8-328">Sie können ihn zum Aktualisieren vorhandener Apps verwenden, aber nicht für die erste Übermittlung an den Store.</span><span class="sxs-lookup"><span data-stu-id="663e8-328">You can use it to update existing apps but you can’t use it to for your first submission to the Store.</span></span> <span data-ttu-id="663e8-329">Weitere Informationen finden Sie unter [Erstellen und Verwalten von Store-Übermittlungen mit MicrosoftStore-Diensten](https://msdn.microsoft.com/windows/uwp/monetize/create-and-manage-submissions-using-windows-store-services).</span><span class="sxs-lookup"><span data-stu-id="663e8-329">For more information, see [Create and manage Store submissions by using Microsoft Store Services.](https://msdn.microsoft.com/windows/uwp/monetize/create-and-manage-submissions-using-windows-store-services)</span></span>

## <a name="best-practices"></a><span data-ttu-id="663e8-330">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="663e8-330">Best Practices</span></span>

<span id="sideloading-best-practices"/>

### <a name="best-practices-for-sideloading-apps"></a><span data-ttu-id="663e8-331">Bewährte Methoden für das Querladen von Apps</span><span class="sxs-lookup"><span data-stu-id="663e8-331">Best Practices for Sideloading apps</span></span>

<span data-ttu-id="663e8-332">Wenn Sie Ihre App verteilen möchten, ohne sie im Store zu veröffentlichen, können Sie die App direkt auf Geräte querladen, solange die Geräte das Zertifikat, das zum Signieren des App-Pakets verwendet wurde, als vertrauenswürdig ansehen.</span><span class="sxs-lookup"><span data-stu-id="663e8-332">If you want to distribute your app without publishing it to the Store, you can sideload your app directly to devices as long as those devices trust the certificate that was used to sign the app package.</span></span>

<span data-ttu-id="663e8-333">Verwenden Sie zum Installieren von Apps das PowerShell-Skript `Add-AppDevPackage.ps1`.</span><span class="sxs-lookup"><span data-stu-id="663e8-333">Use the `Add-AppDevPackage.ps1` PowerShell script to install apps.</span></span> <span data-ttu-id="663e8-334">Dieses Skript wird fügt das Zertifikat im Abschnitt vertrauenswürdige Stammzertifizierungsstellen des lokalen Computers hinzu und dann installiert oder aktualisieren die app-Paketdatei.</span><span class="sxs-lookup"><span data-stu-id="663e8-334">This script will add the certificate to the Trusted Root Certification section for the local machine, and will then install or update the app package file.</span></span>

#### <a name="sideloading-your-app-with-the-windows-10-anniversary-update"></a><span data-ttu-id="663e8-335">Querladen einer App mit dem Windows10 Anniversary Update</span><span class="sxs-lookup"><span data-stu-id="663e8-335">Sideloading your app with the Windows 10 Anniversary Update</span></span>

<span data-ttu-id="663e8-336">In der Windows 10 Anniversary Update können Sie doppelklicken Sie auf die app-Paketdatei und Ihre app installieren, indem Sie die Schaltfläche "installieren" in einem Dialogfeld auswählen.</span><span class="sxs-lookup"><span data-stu-id="663e8-336">In the Windows 10 Anniversary Update, you can double-click the app package file and install your app by choosing the Install button in a dialog box.</span></span>

![Querladen in rs1](images/building-screen18.png)

>[!NOTE]
> <span data-ttu-id="663e8-338">Durch diese Methode werden keine Zertifikate oder zugehörigen Abhängigkeiten installiert.</span><span class="sxs-lookup"><span data-stu-id="663e8-338">This method doesn’t install the certificate or the associated dependencies.</span></span>

<span data-ttu-id="663e8-339">Wenn Sie Ihre Windows-app-Pakete von einer Website wie VSTS oder HockeyApp verteilen möchten, müssen Sie diese der Liste vertrauenswürdiger Websites in Ihrem Browser hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="663e8-339">If you want to distribute your Windows app packages from a website such as VSTS or HockeyApp, you’ll need to add that site to the list of trusted sites in your browser.</span></span> <span data-ttu-id="663e8-340">Andernfalls wird die Datei von Windows als gesperrt markiert.</span><span class="sxs-lookup"><span data-stu-id="663e8-340">Otherwise, Windows marks the file as locked.</span></span>

<span id="certificates-best-practices"/>

### <a name="best-practices-for-signing-certificates"></a><span data-ttu-id="663e8-341">Bewährte Methoden für das Signieren von Zertifikaten</span><span class="sxs-lookup"><span data-stu-id="663e8-341">Best Practices for Signing Certificates</span></span>

<span data-ttu-id="663e8-342">Visual Studio generiert ein Zertifikat für jedes Projekt.</span><span class="sxs-lookup"><span data-stu-id="663e8-342">Visual Studio generates a certificate for each project.</span></span> <span data-ttu-id="663e8-343">Dadurch wird es schwierig, eine geordnete Liste gültiger Zertifikate zu führen.</span><span class="sxs-lookup"><span data-stu-id="663e8-343">This makes it difficult to maintain a curated list of valid certificates.</span></span> <span data-ttu-id="663e8-344">Wenn Sie mehrere Apps erstellen möchten, können Sie ein einzelnes Zertifikat zum Signieren aller Apps erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-344">If you plan to create several apps, you can create a single certificate to sign all of your apps.</span></span> <span data-ttu-id="663e8-345">Danach kann jedes Gerät, für das das Zertifikat als vertrauenswürdig gilt, alle Ihre Apps querladen, ohne dass ein weiteres Zertifikat installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="663e8-345">Then, each device that trusts your certificate will be able to sideload any of your apps without installing another certificate.</span></span> <span data-ttu-id="663e8-346">Weitere Informationen finden Sie unter [Erstellen eines Zertifikats zur Paketsignierung](https://docs.microsoft.com/windows/uwp/packaging/create-certificate-package-signing).</span><span class="sxs-lookup"><span data-stu-id="663e8-346">To learn more, see [Create a certificate for package signing](https://docs.microsoft.com/windows/uwp/packaging/create-certificate-package-signing).</span></span>

#### <a name="create-a-signing-certificate"></a><span data-ttu-id="663e8-347">Erstellen eines Signaturzertifikats</span><span class="sxs-lookup"><span data-stu-id="663e8-347">Create a Signing Certificate</span></span>

<span data-ttu-id="663e8-348">Verwenden Sie das [MakeCert.exe](https://msdn.microsoft.com/library/windows/desktop/ff548309.aspx)-Tool, um ein Zertifikat zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="663e8-348">Use the [MakeCert.exe](https://msdn.microsoft.com/library/windows/desktop/ff548309.aspx) tool to create a certificate.</span></span>

<span data-ttu-id="663e8-349">Im folgenden Beispiel wird ein Zertifikat mit dem Tool „MakeCert.exe“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="663e8-349">The following example creates a certificate by using the MakeCert.exe tool.</span></span>

```ps
MakeCert /n publisherName /r /h 0 /eku "1.3.6.1.5.5.7.3.3,1.3.6.1.4.1.311.10.3.13" /e expirationDate /sv MyKey.pvk MyKey.cer
```

<span data-ttu-id="663e8-350">Anschließend können Sie mit dem Tool „Pvk2Pfx“ eine PFX-Datei generieren, die den kennwortgeschützten privaten Schlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="663e8-350">Then you can use Pvk2Pfx tool to generate a PFX file that contains the private key protected with a password.</span></span>

<span data-ttu-id="663e8-351">Stellen Sie diese Zertifikate für jede Computerrolle bereit:</span><span class="sxs-lookup"><span data-stu-id="663e8-351">Provide these certificates to each machine role:</span></span>

|**<span data-ttu-id="663e8-352">Computer</span><span class="sxs-lookup"><span data-stu-id="663e8-352">Machine</span></span>**|**<span data-ttu-id="663e8-353">Verwendungszweck</span><span class="sxs-lookup"><span data-stu-id="663e8-353">Usage</span></span>**|**<span data-ttu-id="663e8-354">Zertifikat</span><span class="sxs-lookup"><span data-stu-id="663e8-354">Certificate</span></span>**|**<span data-ttu-id="663e8-355">Zertifikatspeicher</span><span class="sxs-lookup"><span data-stu-id="663e8-355">Certificate Store</span></span>**|
|-----------|---------|---------------|---------------------|
|<span data-ttu-id="663e8-356">Entwickler/Buildcomputer</span><span class="sxs-lookup"><span data-stu-id="663e8-356">Developer/Build Machine</span></span>|<span data-ttu-id="663e8-357">Signieren von Builds</span><span class="sxs-lookup"><span data-stu-id="663e8-357">Sign Builds</span></span>|<span data-ttu-id="663e8-358">MyCert.PFX</span><span class="sxs-lookup"><span data-stu-id="663e8-358">MyCert.PFX</span></span>|<span data-ttu-id="663e8-359">Aktueller Benutzer/Persönlich</span><span class="sxs-lookup"><span data-stu-id="663e8-359">Current User/Personal</span></span>|
|<span data-ttu-id="663e8-360">Entwickler/Buildcomputer</span><span class="sxs-lookup"><span data-stu-id="663e8-360">Developer/Build Machine</span></span>|<span data-ttu-id="663e8-361">Ausführen</span><span class="sxs-lookup"><span data-stu-id="663e8-361">Run</span></span>|<span data-ttu-id="663e8-362">MyCert.cer</span><span class="sxs-lookup"><span data-stu-id="663e8-362">MyCert.cer</span></span>|<span data-ttu-id="663e8-363">Lokaler Computer/Vertrauenswürdige Personen</span><span class="sxs-lookup"><span data-stu-id="663e8-363">Local Machine/Trusted People</span></span>|
|<span data-ttu-id="663e8-364">Benutzer</span><span class="sxs-lookup"><span data-stu-id="663e8-364">User</span></span>|<span data-ttu-id="663e8-365">Ausführen</span><span class="sxs-lookup"><span data-stu-id="663e8-365">Run</span></span>|<span data-ttu-id="663e8-366">MyCert.cer</span><span class="sxs-lookup"><span data-stu-id="663e8-366">MyCert.cer</span></span>|<span data-ttu-id="663e8-367">Lokaler Computer/Vertrauenswürdige Personen</span><span class="sxs-lookup"><span data-stu-id="663e8-367">Local Machine/Trusted People</span></span>|

><span data-ttu-id="663e8-368">Hinweis: Sie können auch ein Unternehmenszertifikat verwenden, dem Ihre Benutzer bereits vertrauen.</span><span class="sxs-lookup"><span data-stu-id="663e8-368">Note: You can also use an enterprise certificate that is already trusted by your users.</span></span>

#### <a name="sign-your-uwp-app"></a><span data-ttu-id="663e8-369">Signieren der UWP-App</span><span class="sxs-lookup"><span data-stu-id="663e8-369">Sign your UWP app</span></span>

<span data-ttu-id="663e8-370">Visual Studio und MSBuild bieten verschiedene Möglichkeiten zum Verwalten des Zertifikats, das Sie zum Signieren der App verwenden:</span><span class="sxs-lookup"><span data-stu-id="663e8-370">Visual Studio and MSBuild offers different options to manage the certificate that you use to sign the app:</span></span>

<span data-ttu-id="663e8-371">Eine Möglichkeit besteht darin, das Zertifikat mit dem privaten Schlüssel (normalerweise in Form einer PFX-Datei) in Ihre Projektmappe aufzunehmen und dann in der Projektdatei auf die PFX-Datei zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="663e8-371">One option is to include the certificate with the private key (normally in the form of a .PFX file) in your solution, and then reference the pfx in the project file.</span></span> <span data-ttu-id="663e8-372">Zu diesem Zweck können Sie die Registerkarte „Paket“ des Manifest-Editors verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-372">You can manage this by using the Package tab of the manifest editor.</span></span>

![Erstellen eines Zertifikats](images/building-screen19.png)

<span data-ttu-id="663e8-374">Eine weitere Möglichkeit besteht darin, das Zertifikat auf dem Buildcomputer („Current User/Personal“) zu installieren und dann die Option „Aus Zertifikatspeicher auswählen“ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="663e8-374">Another option is to install the certificate onto the build machine (Current User/Personal), and then use the Pick from Certificate store option.</span></span> <span data-ttu-id="663e8-375">Dadurch wird der Fingerabdruck des Zertifikats in der Projektdatei angegeben. Auf diese Weise wird das Zertifikat auf allen Computern installiert, die zum Erstellen des Projekts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="663e8-375">This specifies the Thumbprint of the certificate in the project file so that the certificate should be installed in all the machines that will be used to build the project.</span></span>

#### <a name="trust-the-signing-certificate-in-the-target-devices"></a><span data-ttu-id="663e8-376">Akzeptieren der Vertrauenswürdigkeit des Signaturzertifikats auf den Zielgeräten</span><span class="sxs-lookup"><span data-stu-id="663e8-376">Trust the signing certificate in the target devices</span></span>

<span data-ttu-id="663e8-377">Das Zertifikat muss für ein Zielgerät vertrauenswürdig sein, bevor die App darauf installiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="663e8-377">A target device has to trust the certificate before the app can be installed on it.</span></span>

<span data-ttu-id="663e8-378">Registrieren Sie den öffentlichen Schlüssel des Zertifikats im Zertifikatspeicher des lokalen Computers unter dem Knoten für vertrauenswürdige Personen oder für den vertrauenswürdigen Stamm.</span><span class="sxs-lookup"><span data-stu-id="663e8-378">Register the public key of the certificate in the Trusted People or Trust Root location in the Local Machine certificate store.</span></span>

<span data-ttu-id="663e8-379">Die schnellste Möglichkeit zum Registrieren des Zertifikats besteht darin, in der CER-Datei zu doppelklicken und dann die Schritte im Assistenten auszuführen, um das Zertifikat im Speicher des **Lokalen Computers** und im **Speicher für vertrauenswürdige Personen** zu speichern.</span><span class="sxs-lookup"><span data-stu-id="663e8-379">The quickest way to register the certificate is to double-click in the .cer file, and then follow the steps in the wizard to save the certificate in the **Local Machine** and **Trusted People** store.</span></span>

## <a name="related-topics"></a><span data-ttu-id="663e8-380">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="663e8-380">Related Topics</span></span>

- [<span data-ttu-id="663e8-381">Erstellen einer .NET-App für Windows</span><span class="sxs-lookup"><span data-stu-id="663e8-381">Build your .NET app for Windows</span></span>](https://www.visualstudio.com/docs/build/get-started/dot-net)
- [<span data-ttu-id="663e8-382">Verpacken von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="663e8-382">Packaging UWP apps</span></span>](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)
- [<span data-ttu-id="663e8-383">Querladen von branchenspezifischen Apps in Windows10</span><span class="sxs-lookup"><span data-stu-id="663e8-383">Sideload LOB apps in Windows 10</span></span>](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10)
- [<span data-ttu-id="663e8-384">Erstellen eines Paketsignaturzertifikats</span><span class="sxs-lookup"><span data-stu-id="663e8-384">Create a certificate for package signing</span></span>](https://docs.microsoft.com/windows/uwp/packaging/create-certificate-package-signing)
