---
title: Unity – Versionskontrolle für Ihr UWP-Projekt
description: Versionsverwaltung für Ihr Unity-UWP.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: 064eaf42fe7d664be273cd7e2222fa5d90be1a11
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8873105"
---
# <a name="unity-version-control-your-uwp-project"></a><span data-ttu-id="8009f-103">Unity: Versionskontrolle für Ihr UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="8009f-103">Unity: Version control your UWP project</span></span>

<span data-ttu-id="8009f-104">Sie haben Ihr Unity-Spiel für Xbox noch immer nicht in die universelle Windows-Plattform (UWP) portiert?</span><span class="sxs-lookup"><span data-stu-id="8009f-104">Still haven't built your Unity game for Xbox using the Universal Windows Platform (UWP)?</span></span>  <span data-ttu-id="8009f-105">Lesen Sie zunächst [Portieren von Unity-Spielen für Xbox auf die UWP](development-lanes-unity.md).</span><span class="sxs-lookup"><span data-stu-id="8009f-105">First see [Bringing Unity games to UWP on Xbox](development-lanes-unity.md).</span></span>

<span data-ttu-id="8009f-106">Es gibt verschiedene Gründe dafür, Teile Ihres generierten UWP-Verzeichnisses der Versionskontrolle hinzuzufügen. Hierzu zählt unter anderem das Hinzufügen von Abhängigkeiten (z.B. Xbox Live SDK).</span><span class="sxs-lookup"><span data-stu-id="8009f-106">There are a few different reasons why you would want to add parts of your generated UWP directory to version control, one of which is adding dependencies (for example,Xbox Live SDK).</span></span>  <span data-ttu-id="8009f-107">Dieses Szenario wird in diesem Lernprogramm als Beispiel herangezogen und hilft Ihnen hoffentlich dabei, die individuellen Anforderungen Ihres Projekts zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="8009f-107">We'll use this scenario as an example for this tutorial, and hopefully it will help you solve your project's individual needs.</span></span>

***<span data-ttu-id="8009f-108">Hinweis: Wir verwenden Git als Versionskontrolllösung.</span><span class="sxs-lookup"><span data-stu-id="8009f-108">Disclaimer: We'll be using Git as our version control solution.</span></span>  <span data-ttu-id="8009f-109">Die Konzepte sind jedoch üblicherweise auf andere Lösungen übertragbar.</span><span class="sxs-lookup"><span data-stu-id="8009f-109">If yours differs, the concepts should still translate.</span></span>***

<span data-ttu-id="8009f-110">Zur Erinnerung: Das Verzeichnis für unser Spiel ***ScrapyardPhoenix*** sieht aktuell wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8009f-110">To refresh your memory, this is what the directory for our game, ***ScrapyardPhoenix***, looks like currently:</span></span>

![Build-Zielordner](images/build-destination.png)

<span data-ttu-id="8009f-112">Und unser UWP-Verzeichnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8009f-112">And this is what our UWP directory looks like:</span></span>

![UWP-VS-Lösung](images/uwp-vs-solution.png)

<span data-ttu-id="8009f-114">In diesem Verzeichnis interessiert uns nur der Ordner ***ScrapyardPhoenix*** (Name Ihres Spiels).</span><span class="sxs-lookup"><span data-stu-id="8009f-114">In this directory, we're only concerned about one folder, the ***ScrapyardPhoenix*** (insert your game's name here) folder.</span></span>  <span data-ttu-id="8009f-115">Alles andere ist für unsere Versionskontrolle nicht relevant.</span><span class="sxs-lookup"><span data-stu-id="8009f-115">Everything else can be ignored in our version control.</span></span>

***<span data-ttu-id="8009f-116">Noch keine Erfahrung mit GITIGNORE-Dateien?</span><span class="sxs-lookup"><span data-stu-id="8009f-116">Unfamiliar with what a .gitignore file is?</span></span>  <span data-ttu-id="8009f-117">Siehe [Gitignore](https://git-scm.com/docs/gitignore).</span><span class="sxs-lookup"><span data-stu-id="8009f-117">See [gitignore](https://git-scm.com/docs/gitignore).</span></span>***

    ##################################################################
    # The original .gitignore file can be found at
    # https://github.com/github/gitignore/blob/master/Unity.gitignore
    ##################################################################

    # standard ignores for a Unity Project
    ...

    # ignore the whole UWP directory
    /UWP/**

    # except we want to keep... (this line will be modified and removed further down)
    !/UWP/ScrapyardPhoenix/

<span data-ttu-id="8009f-118">Wir möchten einige unterschiedliche Dateien und Ordner aus dem Ordner **UWP/ScrapyardPhoenix** auswählen und unserer Versionskontrolle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8009f-118">We're going to want to select a few different files and folders from within the **UWP/ScrapyardPhoenix** folder to add to our version control.</span></span>  <span data-ttu-id="8009f-119">Sehen wir uns das Ganze erst einmal im Detail an:</span><span class="sxs-lookup"><span data-stu-id="8009f-119">First let's look at the full thing in detail:</span></span>

![UWP-Buildverzeichnis](images/uwp-build-directory.png)  

## <a name="folders"></a><span data-ttu-id="8009f-121">Ordner</span><span class="sxs-lookup"><span data-stu-id="8009f-121">Folders</span></span>  

`Assets`<span data-ttu-id="8009f-122"> | **\*Enthalten*** | Microsoft Store-Bilder enthält</span><span class="sxs-lookup"><span data-stu-id="8009f-122"> | **\*Include*** | Contains Microsoft Store images</span></span>  
`Data`<span data-ttu-id="8009f-123">   | \*\*\*Ignorieren Sie*\*\* | In denen kompiliert Unity Ihr Projekt auf (Szenen, Shader, Skripts, Prefabs usw.).</span><span class="sxs-lookup"><span data-stu-id="8009f-123">   | \*\*\*Ignore*\*\* | Where Unity compiles your project to (Scenes, Shaders, Scripts, Prefabs, etc.)</span></span>  
`Dependencies`<span data-ttu-id="8009f-124"> | **\*Enthalten*** | Diese Ordner werden alle UWP-Abhängigkeiten (z. B. xboxlivesdk.dll) gespeichert erstellten</span><span class="sxs-lookup"><span data-stu-id="8009f-124"> | **\*Include*** | This folder is one I created to keep all UWP dependencies in (for example, XboxLiveSDK.dll)</span></span>  
`Properties`<span data-ttu-id="8009f-125"> | **\*Enthalten*** | Enthält erweiterte Einstellungen, die vom Entwickler geändert werden können</span><span class="sxs-lookup"><span data-stu-id="8009f-125"> | **\*Include*** | Contains more advanced settings that can be modified by the developer</span></span>  
`Unprocessed`<span data-ttu-id="8009f-126"> | **\*Ignorieren Sie*** | Enthält Unity `.dll` und `.pdb` Dateien</span><span class="sxs-lookup"><span data-stu-id="8009f-126"> | **\*Ignore*** | Contains Unity `.dll` and `.pdb` files</span></span>  

## <a name="files"></a><span data-ttu-id="8009f-127">Dateien</span><span class="sxs-lookup"><span data-stu-id="8009f-127">Files</span></span>  

`App.cs`<span data-ttu-id="8009f-128"> | **\*Enthalten*** | Der Einstiegspunkt für Ihre UWP-Anwendung; Dies kann geändert und mit anderen Quelldateien erweitert werden</span><span class="sxs-lookup"><span data-stu-id="8009f-128"> | **\*Include*** | Entry point for your UWP application; this can be modified and extended with other source files</span></span>  
`Package.appxmanifest`<span data-ttu-id="8009f-129"> | **\*Enthalten*** | App-Paket manifest Quelldatei für Ihr AppX-Paket</span><span class="sxs-lookup"><span data-stu-id="8009f-129"> | **\*Include*** | App package manifest source file for your AppX</span></span>  
`project.json`<span data-ttu-id="8009f-130"> | **\*Enthalten*** | Beschreibt die NuGet-Pakete Ihre `*.csproj` hängt</span><span class="sxs-lookup"><span data-stu-id="8009f-130"> | **\*Include*** | Describes the NuGet packages your `*.csproj` depends on</span></span>  
`ScrapyardPhoenix.csproj`<span data-ttu-id="8009f-131"> | **\*Enthalten*** | Beschreibt Ihr UWP-Buildziel. Wenn Sie zusätzliche Abhängigkeiten zu Ihrer UWP-Projekt hinzufügen, dies `*.csproj` -Datei, die Informationen enthält</span><span class="sxs-lookup"><span data-stu-id="8009f-131"> | **\*Include*** | Describes your UWP build target; if you add additional dependencies to your UWP project, this `*.csproj` file will contain that information</span></span>  
`ScrapyardPhoenix.csproj.user`<span data-ttu-id="8009f-132"> | **\*Ignorieren Sie*** | Diese Datei enthält lokaler Benutzerinformationen</span><span class="sxs-lookup"><span data-stu-id="8009f-132"> | **\*Ignore*** | This file contains local user information</span></span>

## <a name="resulting-gitignore"></a><span data-ttu-id="8009f-133">Resultierende GITIGNORE-Datei</span><span class="sxs-lookup"><span data-stu-id="8009f-133">Resulting .gitignore</span></span>

    ##################################################################
    # The original .gitignore file can be found at
    # https://github.com/github/gitignore/blob/master/Unity.gitignore
    ##################################################################

    # standard ignores for a Unity Project
    ...

    # ignore the whole UWP directory
    /UWP/**

    # except we want to keep...
    !/UWP/ScrapyardPhoenix/Assets/*
    !/UWP/ScrapyardPhoenix/Dependencies/*
    !/UWP/ScrapyardPhoenix/Properties/*
    !/UWP/ScrapyardPhoenix/App.cs
    !/UWP/ScrapyardPhoenix/Package.appxmanifest
    !/UWP/ScrapyardPhoenix/project.json
    !/UWP/ScrapyardPhoenix/ScrapyardPhoenix.csproj

<span data-ttu-id="8009f-134">Geschafft: Ihre Teammitglieder sind nun mit dem von Ihnen generierten UWP-Projekt synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="8009f-134">And there you go, now your teammates will be in sync with the UWP project you've generated.</span></span> <span data-ttu-id="8009f-135">Nun können Sie Ihrem UWP-Projekt problemlos zusätzliche Ressourcen, Quellen und Abhängigkeiten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8009f-135">Now you can feel free to add additional assets, source, and dependencies to your UWP project.</span></span>

<span data-ttu-id="8009f-136">Einige weitere Versionsverwaltungsbeispiele für den UWP-Ordner finden Sie [hier](https://bitbucket.org/Unity-Technologies/windowsstoreappssamples/overview).</span><span class="sxs-lookup"><span data-stu-id="8009f-136">Some more examples of versioning the UWP folder can be found in [these examples](https://bitbucket.org/Unity-Technologies/windowsstoreappssamples/overview).</span></span>

## <a name="adding-dependencies-to-your-uwp-app"></a><span data-ttu-id="8009f-137">Hinzufügen von Abhängigkeiten zu Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="8009f-137">Adding dependencies to your UWP app</span></span>

<span data-ttu-id="8009f-138">Fügen Sie Abhängigkeiten zu DLL- und WINMD-Dateien hinzu, indem Sie diese im Unterordner **Unity Assets** des Ordners **Plug-Ins** ablegen und auswählen. Legen Sie anschließend im Paketprüfungstool die Plattform-Zieleinstellungen fest.</span><span class="sxs-lookup"><span data-stu-id="8009f-138">Add dependencies to DLLs and WINMDs by putting them in your **Unity Assets** folder under a **Plugins** folder, then select them and set their target platform settings appropriately in the Inspector.</span></span>

![UWP-Lösung](images/uwp-solution.PNG)

<span data-ttu-id="8009f-140">***ScrapyardPhoenix (Universal Windows)*** ist das Projekt, dem Sie einen Verweis (etwa auf das Xbox Live SDK) hinzufügen würden.</span><span class="sxs-lookup"><span data-stu-id="8009f-140">***ScrapyardPhoenix (Universal Windows)*** is the project you would add a reference to, for example, the Xbox Live SDK.</span></span>

## <a name="see-also"></a><span data-ttu-id="8009f-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8009f-141">See also</span></span>
- [<span data-ttu-id="8009f-142">Portieren vorhandener Spiele zu Xbox</span><span class="sxs-lookup"><span data-stu-id="8009f-142">Bringing existing games to Xbox</span></span>](development-lanes-landing.md)
- [<span data-ttu-id="8009f-143">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="8009f-143">UWP on Xbox One</span></span>](index.md)
