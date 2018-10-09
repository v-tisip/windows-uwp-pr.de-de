---
author: laurenhughes
ms.assetid: 3a59ff5e-f491-491c-81b1-6aff15886aad
title: Optionale Pakete und die Erstellung zugehöriger Sets
description: Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, optionale Pakete, zusammengehörig, Paket-Erweiterung, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: 4864bdaa1f32b980c5c8b159ca71bb6a56da4ec5
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4461807"
---
# <a name="optional-packages-and-related-set-authoring"></a><span data-ttu-id="78138-105">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="78138-105">Optional packages and related set authoring</span></span>
<span data-ttu-id="78138-106">Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können.</span><span class="sxs-lookup"><span data-stu-id="78138-106">Optional packages contain content that can be integrated with a main package.</span></span> <span data-ttu-id="78138-107">Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf größenbeschränkungen, oder auch zusätzliche Inhalte getrennt von der ursprünglichen app.</span><span class="sxs-lookup"><span data-stu-id="78138-107">These are useful for downloadable content (DLC), dividing a large app for size restraints, or for shipping any additional content separate from your original app.</span></span>

<span data-ttu-id="78138-108">Zugehörige Gruppen sind eine Erweiterung der optionalen Pakete – können Sie strenger Versionen über Haupt- und optionale Pakete zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="78138-108">Related sets are an extension of optional packages -- they allow you to enforce a strict set of versions across main and optional packages.</span></span> <span data-ttu-id="78138-109">Außerdem können Sie auch systemeigenen Code (C++) von optionalen Paketen laden.</span><span class="sxs-lookup"><span data-stu-id="78138-109">They also let you load native code (C++) from optional packages.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="78138-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="78138-110">Prerequisites</span></span>

- <span data-ttu-id="78138-111">Visual Studio 2017 Version 15.1</span><span class="sxs-lookup"><span data-stu-id="78138-111">Visual Studio 2017, version 15.1</span></span>
- <span data-ttu-id="78138-112">Windows10, Version1703</span><span class="sxs-lookup"><span data-stu-id="78138-112">Windows 10, version 1703</span></span>
- <span data-ttu-id="78138-113">Windows 10, Version 1703 SDK</span><span class="sxs-lookup"><span data-stu-id="78138-113">Windows 10, version 1703 SDK</span></span>

<span data-ttu-id="78138-114">Alle von der aktuellen Entwicklungstools finden Sie [Downloads und Tools für Windows 10](https://developer.microsoft.com/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="78138-114">To get all of the latest development tools, see [Downloads and tools for Windows 10](https://developer.microsoft.com/windows/downloads).</span></span>

> [!NOTE]
> <span data-ttu-id="78138-115">Um eine app übermitteln, die an den Microsoft Store optionale Pakete und/oder zugehörige Gruppen verwendet, benötigen Sie eine Berechtigung.</span><span class="sxs-lookup"><span data-stu-id="78138-115">To submit an app that uses optional packages and/or related sets to the Microsoft Store, you will need permission.</span></span> <span data-ttu-id="78138-116">Optionale Pakete und zugehörige Gruppen können ohne Dev Center-Berechtigung für branchenspezifische oder Unternehmens-Apps verwendet werden, wenn sie nicht an den Store übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="78138-116">Optional packages and related sets can be used for Line of Business (LOB) or enterprise apps without Dev Center permission if they are not submitted to the Store.</span></span> <span data-ttu-id="78138-117">Informationen zum Erhalt einer Berechtigung, eine App zu übermitteln, die optionale Pakete und zugehörige Gruppen verwendet, finden Sie unter [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support).</span><span class="sxs-lookup"><span data-stu-id="78138-117">See [Windows developer support](https://developer.microsoft.com/windows/support) to get permission to submit an app that uses optional packages and related sets.</span></span>

### <a name="code-sample"></a><span data-ttu-id="78138-118">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="78138-118">Code sample</span></span>
<span data-ttu-id="78138-119">Während Sie in diesem Artikel lesen, wird empfohlen, dass Sie folgen Sie das [optionale Paket-Codebeispiel](https://github.com/AppInstaller/OptionalPackageSample) auf GitHub eine praktische zu verstehen und wie optionale Pakete und zugehörige Gruppen Arbeit in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78138-119">While you're reading this article, it's recommended that you follow along with the [optional package code sample](https://github.com/AppInstaller/OptionalPackageSample) on GitHub for a hands-on understanding of how optional packages and related sets work within Visual Studio.</span></span>

## <a name="optional-packages"></a><span data-ttu-id="78138-120">Optionale Pakete</span><span class="sxs-lookup"><span data-stu-id="78138-120">Optional packages</span></span>
<span data-ttu-id="78138-121">Um ein optionales Paket in Visual Studio erstellen, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="78138-121">To create an optional package in Visual Studio, you'll need to:</span></span>
1. <span data-ttu-id="78138-122">Stellen Sie sicher, dass Ihre app **Zielplattformversion Min** auf festgelegt ist: 10.0.15063.0.</span><span class="sxs-lookup"><span data-stu-id="78138-122">Make sure your app's **Target Platform Min Version** is set to: 10.0.15063.0.</span></span>
2. <span data-ttu-id="78138-123">Öffnen Sie in Ihrem Projekt **Hauptpaket** der `Package.appxmanifest` Datei.</span><span class="sxs-lookup"><span data-stu-id="78138-123">From your **main package** project, open the `Package.appxmanifest` file.</span></span> <span data-ttu-id="78138-124">Navigieren Sie zur Registerkarte "Verpacken", und notieren Sie Ihren **paketfamilienname**, das ist alles, was vor dem Zeichen "_".</span><span class="sxs-lookup"><span data-stu-id="78138-124">Navigate to the "Packaging" tab and make a note of your **package family name**, which is everything before the "_" character.</span></span>
3. <span data-ttu-id="78138-125">Aus Ihrem Projekt **optionales Paket** rechten Maustaste klicken Sie auf die `Package.appxmanifest` , und wählen Sie **mit öffnen > XML (Text) Editor**.</span><span class="sxs-lookup"><span data-stu-id="78138-125">From your **optional package** project, right click the `Package.appxmanifest` and select **Open with > XML (Text) Editor**.</span></span>
4. <span data-ttu-id="78138-126">Suchen Sie nach dem `<Dependencies>` Element in der Datei.</span><span class="sxs-lookup"><span data-stu-id="78138-126">Locate the `<Dependencies>` element in the file.</span></span> <span data-ttu-id="78138-127">Fügen Sie Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="78138-127">Add the following:</span></span>

```XML
<uap3:MainPackageDependency Name="[MainPackageDependency]"/>
```

<span data-ttu-id="78138-128">Ersetzen Sie `[MainPackageDependency]` mit der **paketfamilienname** aus Schritt2.</span><span class="sxs-lookup"><span data-stu-id="78138-128">Replace `[MainPackageDependency]` with your **package family name** from Step 2.</span></span> <span data-ttu-id="78138-129">Dies wird angegeben, dass das **optionale Paket** das **Hauptpaket**abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="78138-129">This will specify that your **optional package** is dependent on your **main package**.</span></span>

<span data-ttu-id="78138-130">Wenn Sie die Schritte 1 bis 4, einrichten-Paket-Abhängigkeiten haben, können Sie entwickeln wie gewohnt weiter.</span><span class="sxs-lookup"><span data-stu-id="78138-130">Once you have your package dependencies set up from Steps 1 through 4, you can continue developing as you normally would.</span></span> <span data-ttu-id="78138-131">Wenn Sie Code aus das optionale Paket in das Hauptpaket laden möchten, müssen Sie eine verwandte Gruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="78138-131">If you would like to load code from the optional package into the main package, you will need to build a related set.</span></span> <span data-ttu-id="78138-132">Finden Sie im Abschnitt [verknüpft legt](#related_sets) für weitere Details.</span><span class="sxs-lookup"><span data-stu-id="78138-132">See the [Related sets](#related_sets) section for more details.</span></span>

<span data-ttu-id="78138-133">Visual Studio kann konfiguriert werden, um Ihrem Hauptpaket jedes Mal erneut bereitstellen Sie ein optionales Paket bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="78138-133">Visual Studio can be configured to re-deploy your main package each time you deploy an optional package.</span></span> <span data-ttu-id="78138-134">Um die Buildabhängigkeit in Visual Studio festlegen, sollten Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="78138-134">To set the build dependency in Visual Studio, you should:</span></span>

- <span data-ttu-id="78138-135">Klicken Sie mit der rechten Maustaste auf das optionale Paket-Projekt, und wählen Sie **Abhängigkeiten Build > Projekt Abhängigkeiten...**</span><span class="sxs-lookup"><span data-stu-id="78138-135">Right click the optional package project and select **Build Dependencies > Project Dependencies...**</span></span>
- <span data-ttu-id="78138-136">Überprüfen Sie das Hauptpaket-Projekt, und klicken Sie auf "OK".</span><span class="sxs-lookup"><span data-stu-id="78138-136">Check the main package project and select "OK".</span></span> 

<span data-ttu-id="78138-137">Nun, jedes Mal, wenn Sie F5 oder ein optionales Paket-Projekt erstellen, wird Visual Studio das Hauptpaket Projekt erstellen zuerst.</span><span class="sxs-lookup"><span data-stu-id="78138-137">Now, every time you enter F5 or build an optional package project, Visual Studio will build the main package project first.</span></span> <span data-ttu-id="78138-138">Dadurch wird sichergestellt, dass Ihre Hauptprojekt und optionale Projekte synchronisiert sind.</span><span class="sxs-lookup"><span data-stu-id="78138-138">This will ensure that your main project and optional projects are in sync.</span></span>

## <span data-ttu-id="78138-139">Zugehörige Gruppen<a name="related_sets"></a></span><span class="sxs-lookup"><span data-stu-id="78138-139">Related sets<a name="related_sets"></a></span></span>

<span data-ttu-id="78138-140">Wenn Sie Code über ein optionales Paket in das Hauptpaket laden möchten, müssen Sie eine verwandte Gruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="78138-140">If you want to load code from an optional package into the main package, you will need to build a related set.</span></span> <span data-ttu-id="78138-141">Um eine verwandte Gruppe zu erstellen, müssen die Hauptpaket und optionalen Pakets eng werden.</span><span class="sxs-lookup"><span data-stu-id="78138-141">To build a related set, your main package and optional package must be tightly coupled.</span></span> <span data-ttu-id="78138-142">Die Metadaten für zugehörige Gruppen wird in der Datei .appxbundle oder .msixbundle des Hauptpakets angegeben.</span><span class="sxs-lookup"><span data-stu-id="78138-142">The metadata for related sets is specified in the .appxbundle or .msixbundle file of the main package.</span></span> <span data-ttu-id="78138-143">Visual Studio erleichtert die richtige Metadaten in Ihren Dateien zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="78138-143">Visual Studio helps you get the correct metadata in your files.</span></span> <span data-ttu-id="78138-144">Um Ihre app-Lösung für die zugehörige Gruppen zu konfigurieren, verwenden Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="78138-144">To configure your app's solution for related sets, use the following steps:</span></span>

1. <span data-ttu-id="78138-145">Klicken Sie mit der rechten Maustaste auf das Hauptpaket-Projekt, wählen Sie **Hinzufügen > Neues Element**</span><span class="sxs-lookup"><span data-stu-id="78138-145">Right click the main package project, select **Add > New Item...**</span></span>
2. <span data-ttu-id="78138-146">Klicken Sie im Fenster Suchen Sie die installierten Vorlagen für "txt", und fügen Sie eine neue Textdatei.</span><span class="sxs-lookup"><span data-stu-id="78138-146">From the window, search the Installed Templates for ".txt" and add a new text file.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="78138-147">Die neue Textdatei muss den Namen: `Bundle.Mapping.txt`.</span><span class="sxs-lookup"><span data-stu-id="78138-147">The new text file must be named: `Bundle.Mapping.txt`.</span></span>
3. <span data-ttu-id="78138-148">In der `Bundle.Mapping.txt` Datei, die Sie geben relative Pfade optionales Paket Projekte oder externe Pakete.</span><span class="sxs-lookup"><span data-stu-id="78138-148">In the `Bundle.Mapping.txt` file you'll specify relative paths to any optional package projects or external packages.</span></span> <span data-ttu-id="78138-149">Ein Beispiel für `Bundle.Mapping.txt` Datei sollte etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="78138-149">A sample `Bundle.Mapping.txt` file should look something like this:</span></span>

```syntax
[OptionalProjects]
"..\ActivatableOptionalPackage1\ActivatableOptionalPackage1.vcxproj"
"..\ActivatableOptionalPackage2\ActivatableOptionalPackage2.vcxproj"

[ExternalPackages]
"..\ActivatableOptionalPackage1\x86\Release\ActivatableOptionalPackage3_1.1.1.0\ ActivatableOptionalPackage3_1.1.1.0.appx"
```

<span data-ttu-id="78138-150">Wenn Ihre Lösung auf diese Weise konfiguriert ist, erstellt Visual Studio ein Paketmanifest für das Hauptpaket mit alle erforderlichen Metadaten für zugehörige Gruppen.</span><span class="sxs-lookup"><span data-stu-id="78138-150">When your solution is configured this way, Visual Studio will create a bundle manifest for the main package with all of the required metadata for related sets.</span></span> 

<span data-ttu-id="78138-151">Beachten Sie, die optionale Pakete wie ein `Bundle.Mapping.txt` -Datei für Dateisätze funktioniert nur unter Windows 10, Version 1703.</span><span class="sxs-lookup"><span data-stu-id="78138-151">Note that like optional packages, a `Bundle.Mapping.txt` file for related sets will only work on Windows 10, version 1703.</span></span> <span data-ttu-id="78138-152">Darüber hinaus sollte Ihre app Min Zielplattformversion auf 10.0.15063.0 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="78138-152">Additionally, your app's Target Platform Min Version should be set to 10.0.15063.0.</span></span>

## <span data-ttu-id="78138-153">Bekannte Probleme<a name="known_issues"></a></span><span class="sxs-lookup"><span data-stu-id="78138-153">Known issues<a name="known_issues"></a></span></span>

<span data-ttu-id="78138-154">Debuggen eines optionalen zusammengehörig-Projekts ist derzeit in Visual Studio nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78138-154">Debugging a related set optional project is not currently supported in Visual Studio.</span></span> <span data-ttu-id="78138-155">Um dieses Problem zu umgehen, können Sie bereitstellen und starten die Aktivierung (STRG + F5) und manuell den Debugger an einen Prozess anhängen.</span><span class="sxs-lookup"><span data-stu-id="78138-155">To work around this issue, you can deploy and launch the activation (Ctrl + F5) and manually attach the debugger to a process.</span></span> <span data-ttu-id="78138-156">Um den Debugger, wechseln Sie in Visual Studio im Menü "Debug", wählen Sie "Anhängen zum Prozess...", und hängen Sie den Debugger an der **Haupt-app-Prozess**.</span><span class="sxs-lookup"><span data-stu-id="78138-156">To attach the debugger, go the "Debug" menu in Visual Studio, select "Attach to Process...", and attach the debugger to the **main app process**.</span></span>