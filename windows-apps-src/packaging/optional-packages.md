---
author: laurenhughes
ms.assetid: 3a59ff5e-f491-491c-81b1-6aff15886aad
title: Optionale Pakete und die Erstellung zugehöriger Sets
description: Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern.
ms.author: lahugh
ms.date: 04/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, optional Pakete, ähnliche, Paket-Erweiterung, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: d66a511211396190393e31bfd553149a1e89fad0
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "406083"
---
# <a name="optional-packages-and-related-set-authoring"></a><span data-ttu-id="d49cb-105">Optionale Pakete und die Erstellung zugehöriger Sets</span><span class="sxs-lookup"><span data-stu-id="d49cb-105">Optional packages and related set authoring</span></span>
<span data-ttu-id="d49cb-106">Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können.</span><span class="sxs-lookup"><span data-stu-id="d49cb-106">Optional packages contain content that can be integrated with a main package.</span></span> <span data-ttu-id="d49cb-107">Diese eignen sich für eine große-app für Größe Beschränkungen, Division Bücher (DLC), oder für den Versand alle zusätzlichen Inhalte aus Ihrer ursprünglichen app zu trennen.</span><span class="sxs-lookup"><span data-stu-id="d49cb-107">These are useful for downloadable content (DLC), dividing a large app for size restraints, or for shipping any additional content separate from your original app.</span></span>

<span data-ttu-id="d49cb-108">Verwandte sind eine Erweiterung der optionale Pakete – können Sie strenge Versionen für Haupt- und optional Pakete zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="d49cb-108">Related sets are an extension of optional packages -- they allow you to enforce a strict set of versions across main and optional packages.</span></span> <span data-ttu-id="d49cb-109">Außerdem können Sie auch systemeigenen Code (C++) aus optionale Pakete zu laden.</span><span class="sxs-lookup"><span data-stu-id="d49cb-109">They also let you load native code (C++) from optional packages.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d49cb-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d49cb-110">Prerequisites</span></span>

- <span data-ttu-id="d49cb-111">Visual Studio 2017, Version 15.1.</span><span class="sxs-lookup"><span data-stu-id="d49cb-111">Visual Studio 2017, version 15.1</span></span>
- <span data-ttu-id="d49cb-112">Windows10, Version1703</span><span class="sxs-lookup"><span data-stu-id="d49cb-112">Windows 10, version 1703</span></span>
- <span data-ttu-id="d49cb-113">Windows-10, Version 1703 SDK (engl.)</span><span class="sxs-lookup"><span data-stu-id="d49cb-113">Windows 10, version 1703 SDK</span></span>

<span data-ttu-id="d49cb-114">So rufen Sie alle der neuesten Entwicklungstools, finden Sie unter [Downloads und Tools für Windows 10](https://developer.microsoft.com/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="d49cb-114">To get all of the latest development tools, see [Downloads and tools for Windows 10](https://developer.microsoft.com/windows/downloads).</span></span>

> [!NOTE]
> <span data-ttu-id="d49cb-115">Wenn Sie eine app übermitteln, die an den Microsoft-Store optionale Pakete und/oder verwandte verwendet, benötigen Sie die Berechtigung.</span><span class="sxs-lookup"><span data-stu-id="d49cb-115">To submit an app that uses optional packages and/or related sets to the Microsoft Store, you will need permission.</span></span> <span data-ttu-id="d49cb-116">Optionale Pakete und zugehörige Gruppen können ohne Dev Center-Berechtigung für branchenspezifische oder Unternehmens-Apps verwendet werden, wenn sie nicht an den Store übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="d49cb-116">Optional packages and related sets can be used for Line of Business (LOB) or enterprise apps without Dev Center permission if they are not submitted to the Store.</span></span> <span data-ttu-id="d49cb-117">Informationen zum Erhalt einer Berechtigung, eine App zu übermitteln, die optionale Pakete und zugehörige Gruppen verwendet, finden Sie unter [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support).</span><span class="sxs-lookup"><span data-stu-id="d49cb-117">See [Windows developer support](https://developer.microsoft.com/windows/support) to get permission to submit an app that uses optional packages and related sets.</span></span>

### <a name="code-sample"></a><span data-ttu-id="d49cb-118">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="d49cb-118">Code sample</span></span>
<span data-ttu-id="d49cb-119">Während Sie in diesem Artikel lesen, wird empfohlen, dass Sie führen Sie eine praktische zu verstehen und wie optionale Pakete auf GitHub sowie die [optionalen Paket Codebeispiel](https://github.com/AppInstaller/OptionalPackageSample) und damit legt Arbeit in Visual Studio verbundene.</span><span class="sxs-lookup"><span data-stu-id="d49cb-119">While you're reading this article, it's recommended that you follow along with the [optional package code sample](https://github.com/AppInstaller/OptionalPackageSample) on GitHub for a hands-on understanding of how optional packages and related sets work within Visual Studio.</span></span>

## <a name="optional-packages"></a><span data-ttu-id="d49cb-120">Optionale Pakete</span><span class="sxs-lookup"><span data-stu-id="d49cb-120">Optional packages</span></span>
<span data-ttu-id="d49cb-121">Um ein optionales Paket in Visual Studio erstellen möchten, benötigen Sie:</span><span class="sxs-lookup"><span data-stu-id="d49cb-121">To create an optional package in Visual Studio, you'll need to:</span></span>
1. <span data-ttu-id="d49cb-122">Stellen Sie sicher, dass Ihre app- **Plattform Min-Zielversion** auf festgelegt ist: 10.0.15063.0.</span><span class="sxs-lookup"><span data-stu-id="d49cb-122">Make sure your app's **Target Platform Min Version** is set to: 10.0.15063.0.</span></span>
2. <span data-ttu-id="d49cb-123">Aus dem Projekt **Hauptfenster Paket** öffnen Sie die `Package.appxmanifest` Datei.</span><span class="sxs-lookup"><span data-stu-id="d49cb-123">From your **main package** project, open the `Package.appxmanifest` file.</span></span> <span data-ttu-id="d49cb-124">Navigieren Sie zur Registerkarte "Packen", und notieren Sie Ihre **Familie Paketname**, ist alles vor dem Zeichen "_".</span><span class="sxs-lookup"><span data-stu-id="d49cb-124">Navigate to the "Packaging" tab and make a note of your **package family name**, which is everything before the "_" character.</span></span>
3. <span data-ttu-id="d49cb-125">Aus dem Projekt **optionales Paket** rechten Maustaste klicken Sie auf die `Package.appxmanifest` und wählen Sie **mit Open > XML (Text) Editor**.</span><span class="sxs-lookup"><span data-stu-id="d49cb-125">From your **optional package** project, right click the `Package.appxmanifest` and select **Open with > XML (Text) Editor**.</span></span>
4. <span data-ttu-id="d49cb-126">Suchen Sie nach der `<Dependencies>` Element in der Datei.</span><span class="sxs-lookup"><span data-stu-id="d49cb-126">Locate the `<Dependencies>` element in the file.</span></span> <span data-ttu-id="d49cb-127">Fügen Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d49cb-127">Add the following:</span></span>

```XML
<uap3:MainPackageDependency Name="[MainPackageDependency]"/>
```

<span data-ttu-id="d49cb-128">Ersetzen Sie `[MainPackageDependency]` Ihre **Familie Paketname** aus Schritt2.</span><span class="sxs-lookup"><span data-stu-id="d49cb-128">Replace `[MainPackageDependency]` with your **package family name** from Step 2.</span></span> <span data-ttu-id="d49cb-129">Dies wird angegeben, dass Ihr **Paket optional** das **Hauptfenster Paket**abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="d49cb-129">This will specify that your **optional package** is dependent on your **main package**.</span></span>

<span data-ttu-id="d49cb-130">Sobald Sie Paket Abhängigkeiten von Schritte 1 bis 4 eingerichtet haben, können Sie die Entwicklung von weiterhin, wie gewohnt verwenden.</span><span class="sxs-lookup"><span data-stu-id="d49cb-130">Once you have your package dependencies set up from Steps 1 through 4, you can continue developing as you normally would.</span></span> <span data-ttu-id="d49cb-131">Wenn Sie Code in das Hauptfenster Paket aus dem optionalen Paket laden möchten, müssen Sie eine zugehörige Gruppe erstellen.</span><span class="sxs-lookup"><span data-stu-id="d49cb-131">If you would like to load code from the optional package into the main package, you will need to build a related set.</span></span> <span data-ttu-id="d49cb-132">Finden Sie weitere Informationen im Abschnitt [verknüpft wird](#related_sets) .</span><span class="sxs-lookup"><span data-stu-id="d49cb-132">See the [Related sets](#related_sets) section for more details.</span></span>

<span data-ttu-id="d49cb-133">Visual Studio kann konfiguriert werden, um das Hauptfenster Paket jedes Mal erneut bereitstellen Sie ein optionales Paket bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d49cb-133">Visual Studio can be configured to re-deploy your main package each time you deploy an optional package.</span></span> <span data-ttu-id="d49cb-134">Wenn die Buildabhängigkeit in Visual Studio festlegen möchten, sollten Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d49cb-134">To set the build dependency in Visual Studio, you should:</span></span>

- <span data-ttu-id="d49cb-135">Klicken Sie mit der rechten Maustaste auf das Projekt optionales Paket, und wählen Sie **Abhängigkeiten Build > Project Dependencies...**</span><span class="sxs-lookup"><span data-stu-id="d49cb-135">Right click the optional package project and select **Build Dependencies > Project Dependencies...**</span></span>
- <span data-ttu-id="d49cb-136">Aktivieren Sie das Hauptfenster Paket-Projekt, und wählen Sie "OK".</span><span class="sxs-lookup"><span data-stu-id="d49cb-136">Check the main package project and select "OK".</span></span> 

<span data-ttu-id="d49cb-137">Nun, jedes Mal, wenn Sie F5 eingeben oder ein optionales Paket-Projekt erstellen, wird Visual Studio Haupt-Paket zuerst erstellen das Projekt.</span><span class="sxs-lookup"><span data-stu-id="d49cb-137">Now, every time you enter F5 or build an optional package project, Visual Studio will build the main package project first.</span></span> <span data-ttu-id="d49cb-138">Dadurch wird sichergestellt, dass Ihre Hauptassembly des Projekts und optional Projekte synchronisiert sind.</span><span class="sxs-lookup"><span data-stu-id="d49cb-138">This will ensure that your main project and optional projects are in sync.</span></span>

## <span data-ttu-id="d49cb-139">Verwandte<a name="related_sets"></a></span><span class="sxs-lookup"><span data-stu-id="d49cb-139">Related sets<a name="related_sets"></a></span></span>

<span data-ttu-id="d49cb-140">Wenn Sie Code in das Hauptfenster Paket aus einem Paket optional laden möchten, müssen Sie eine zugehörige Gruppe erstellen.</span><span class="sxs-lookup"><span data-stu-id="d49cb-140">If you want to load code from an optional package into the main package, you will need to build a related set.</span></span> <span data-ttu-id="d49cb-141">Um ähnliche zu erstellen, müssen Ihre wichtigsten Paket und optional Paket eng verknüpft sein.</span><span class="sxs-lookup"><span data-stu-id="d49cb-141">To build a related set, your main package and optional package must be tightly coupled.</span></span> <span data-ttu-id="d49cb-142">Die Metadaten für verwandte wird angegeben, der `.appxbundle` Datei des Haupt-Pakets.</span><span class="sxs-lookup"><span data-stu-id="d49cb-142">The metadata for related sets is specified in the `.appxbundle` file of the main package.</span></span> <span data-ttu-id="d49cb-143">Visual Studio unterstützt Sie bei die richtige Metadaten in den Dateien.</span><span class="sxs-lookup"><span data-stu-id="d49cb-143">Visual Studio helps you get the correct metadata in your files.</span></span> <span data-ttu-id="d49cb-144">Gehen Sie folgendermaßen vor, um Ihre app-Lösung für verwandte zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="d49cb-144">To configure your app's solution for related sets, use the following steps:</span></span>

1. <span data-ttu-id="d49cb-145">Klicken Sie mit der rechten Maustaste auf das Hauptfenster Paket-Projekt, wählen Sie **Hinzufügen > Neues Element...**</span><span class="sxs-lookup"><span data-stu-id="d49cb-145">Right click the main package project, select **Add > New Item...**</span></span>
2. <span data-ttu-id="d49cb-146">Klicken Sie im Fenster Suchen Sie die installierte Vorlagen für "txt", und fügen Sie eine neue Textdatei.</span><span class="sxs-lookup"><span data-stu-id="d49cb-146">From the window, search the Installed Templates for ".txt" and add a new text file.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="d49cb-147">Muss den Namen der neuen Textdatei: `Bundle.Mapping.txt`.</span><span class="sxs-lookup"><span data-stu-id="d49cb-147">The new text file must be named: `Bundle.Mapping.txt`.</span></span>
3. <span data-ttu-id="d49cb-148">In der `Bundle.Mapping.txt` Datei benötigen Sie relative Pfade an einem beliebigen optionales Paket Projekte oder externe Pakete angeben.</span><span class="sxs-lookup"><span data-stu-id="d49cb-148">In the `Bundle.Mapping.txt` file you'll specify relative paths to any optional package projects or external packages.</span></span> <span data-ttu-id="d49cb-149">Ein Beispiel für `Bundle.Mapping.txt` Datei sollte in etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="d49cb-149">A sample `Bundle.Mapping.txt` file should look something like this:</span></span>

```syntax
[OptionalProjects]
"..\ActivatableOptionalPackage1\ActivatableOptionalPackage1.vcxproj"
"..\ActivatableOptionalPackage2\ActivatableOptionalPackage2.vcxproj"

[ExternalPackages]
"..\ActivatableOptionalPackage1\x86\Release\ActivatableOptionalPackage3_1.1.1.0\ ActivatableOptionalPackage3_1.1.1.0.appx"
```

<span data-ttu-id="d49cb-150">Wenn Ihre Lösung auf diese Weise konfiguriert ist, erstellt Visual Studio ein Manifest Bundle für das Hauptfenster Paket mit alle erforderlichen Metadaten für verwandte.</span><span class="sxs-lookup"><span data-stu-id="d49cb-150">When your solution is configured this way, Visual Studio will create a bundle manifest for the main package with all of the required metadata for related sets.</span></span> 

<span data-ttu-id="d49cb-151">Notiz, die optionale Pakete, wie eine `Bundle.Mapping.txt` -Datei für verwandte funktioniert nur auf Windows-10, Version 1703.</span><span class="sxs-lookup"><span data-stu-id="d49cb-151">Note that like optional packages, a `Bundle.Mapping.txt` file for related sets will only work on Windows 10, version 1703.</span></span> <span data-ttu-id="d49cb-152">Darüber hinaus sollten Ihre app Zielversion Plattform Min auf 10.0.15063.0 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="d49cb-152">Additionally, your app's Target Platform Min Version should be set to 10.0.15063.0.</span></span>

## <span data-ttu-id="d49cb-153">Bekannte Probleme<a name="known_issues"></a></span><span class="sxs-lookup"><span data-stu-id="d49cb-153">Known issues<a name="known_issues"></a></span></span>

<span data-ttu-id="d49cb-154">Debuggen eines optional ähnliche-Projekts wird derzeit in Visual Studio nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d49cb-154">Debugging a related set optional project is not currently supported in Visual Studio.</span></span> <span data-ttu-id="d49cb-155">Dieses Problem zu umgehen, können Sie bereitstellen und manuelles Anfügen des Debuggers an einen Prozess und starten Sie die Aktivierung (STRG + F5).</span><span class="sxs-lookup"><span data-stu-id="d49cb-155">To work around this issue, you can deploy and launch the activation (Ctrl + F5) and manually attach the debugger to a process.</span></span> <span data-ttu-id="d49cb-156">Zum Anfügen des Debuggers wechseln Sie in Visual Studio im Menü "Debuggen", wählen Sie "Anfügen an Prozess..." und fügen Sie des Debuggers an den **Prozess Hauptfenster app an**.</span><span class="sxs-lookup"><span data-stu-id="d49cb-156">To attach the debugger, go the "Debug" menu in Visual Studio, select "Attach to Process...", and attach the debugger to the **main app process**.</span></span>