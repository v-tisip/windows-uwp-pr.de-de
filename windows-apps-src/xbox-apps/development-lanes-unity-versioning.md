---
author: JordanEllis6809
title: Unity – Versionskontrolle für Ihr UWP-Projekt
description: Versionsverwaltung für Ihr Unity-UWP.
ms.openlocfilehash: 3b796c31e6b284cea628ba68a34799cf9317ee2e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235117"
---
# <a name="unity-version-control-your-uwp-project"></a><span data-ttu-id="ccab8-103">Unity: Versionskontrolle für Ihr UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="ccab8-103">Unity: Version control your UWP project</span></span>

<span data-ttu-id="ccab8-104">Sie haben Ihr Unity-Spiel für Xbox noch immer nicht in die universelle Windows-Plattform (UWP) portiert?</span><span class="sxs-lookup"><span data-stu-id="ccab8-104">Still haven't built your Unity game for Xbox using the Universal Windows Platform (UWP)?</span></span>  <span data-ttu-id="ccab8-105">Lesen Sie zunächst [Portieren von Unity-Spielen für Xbox auf die UWP](development-lanes-unity.md).</span><span class="sxs-lookup"><span data-stu-id="ccab8-105">First see [Bringing Unity games to UWP on Xbox](development-lanes-unity.md).</span></span>

<span data-ttu-id="ccab8-106">Es gibt verschiedene Gründe dafür, Teile Ihres generierten UWP-Verzeichnisses der Versionskontrolle hinzuzufügen. Hierzu zählt unter anderem das Hinzufügen von Abhängigkeiten (z.B. Xbox Live SDK).</span><span class="sxs-lookup"><span data-stu-id="ccab8-106">There are a few different reasons why you would want to add parts of your generated UWP directory to version control, one of which is adding dependencies (for example,Xbox Live SDK).</span></span>  <span data-ttu-id="ccab8-107">Dieses Szenario wird in diesem Lernprogramm als Beispiel herangezogen und hilft Ihnen hoffentlich dabei, die individuellen Anforderungen Ihres Projekts zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="ccab8-107">We'll use this scenario as an example for this tutorial, and hopefully it will help you solve your project's individual needs.</span></span>

***<span data-ttu-id="ccab8-108">Hinweis: Wir verwenden Git als Versionskontrolllösung.</span><span class="sxs-lookup"><span data-stu-id="ccab8-108">Disclaimer: We'll be using Git as our version control solution.</span></span>  <span data-ttu-id="ccab8-109">Die Konzepte sind jedoch üblicherweise auf andere Lösungen übertragbar.</span><span class="sxs-lookup"><span data-stu-id="ccab8-109">If yours differs, the concepts should still translate.</span></span>***

<span data-ttu-id="ccab8-110">Zur Erinnerung: Das Verzeichnis für unser Spiel ***ScrapyardPhoenix*** sieht aktuell wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="ccab8-110">To refresh your memory, this is what the directory for our game, ***ScrapyardPhoenix***, looks like currently:</span></span>

![Build-Zielordner](images/build-destination.png)

<span data-ttu-id="ccab8-112">Und unser UWP-Verzeichnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="ccab8-112">And this is what our UWP directory looks like:</span></span>

![UWP-VS-Lösung](images/uwp-vs-solution.png)

<span data-ttu-id="ccab8-114">In diesem Verzeichnis interessiert uns nur der Ordner ***ScrapyardPhoenix*** (Name Ihres Spiels).</span><span class="sxs-lookup"><span data-stu-id="ccab8-114">In this directory, we're only concerned about one folder, the ***ScrapyardPhoenix*** (insert your game's name here) folder.</span></span>  <span data-ttu-id="ccab8-115">Alles andere ist für unsere Versionskontrolle nicht relevant.</span><span class="sxs-lookup"><span data-stu-id="ccab8-115">Everything else can be ignored in our version control.</span></span>

***<span data-ttu-id="ccab8-116">Noch keine Erfahrung mit GITIGNORE-Dateien?</span><span class="sxs-lookup"><span data-stu-id="ccab8-116">Unfamiliar with what a .gitignore file is?</span></span>  <span data-ttu-id="ccab8-117">Siehe [Gitignore](https://git-scm.com/docs/gitignore).</span><span class="sxs-lookup"><span data-stu-id="ccab8-117">See [gitignore](https://git-scm.com/docs/gitignore).</span></span>***

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

<span data-ttu-id="ccab8-118">Wir möchten einige unterschiedliche Dateien und Ordner aus dem Ordner **UWP/ScrapyardPhoenix** auswählen und unserer Versionskontrolle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ccab8-118">We're going to want to select a few different files and folders from within the **UWP/ScrapyardPhoenix** folder to add to our version control.</span></span>  <span data-ttu-id="ccab8-119">Sehen wir uns das Ganze erst einmal im Detail an:</span><span class="sxs-lookup"><span data-stu-id="ccab8-119">First let's look at the full thing in detail:</span></span>

![UWP-Buildverzeichnis](images/uwp-build-directory.png)  

## <a name="folders"></a><span data-ttu-id="ccab8-121">Ordner</span><span class="sxs-lookup"><span data-stu-id="ccab8-121">Folders</span></span>  

`Assets` | <span data-ttu-id="ccab8-122">***Einbeziehen*** | Enthält WindowsStore-Bilder.</span><span class="sxs-lookup"><span data-stu-id="ccab8-122">***Include*** | Contains Windows Store images</span></span>  
`Data`   | <span data-ttu-id="ccab8-123">***Ignorieren*** | Der Ort, an dem Unity Ihr Projekt kompiliert (Szenen, Shader, Skripts, vorgefertigte Elemente usw.).</span><span class="sxs-lookup"><span data-stu-id="ccab8-123">***Ignore*** | Where Unity compiles your project to (Scenes, Shaders, Scripts, Prefabs, etc.)</span></span>  
`Dependencies` | <span data-ttu-id="ccab8-124">***Einbeziehen*** | In diesem von mir erstellten Ordner werden alle UWP-Abhängigkeiten (z.B. XboxLiveSDK.dll) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ccab8-124">***Include*** | This folder is one I created to keep all UWP dependencies in (for example, XboxLiveSDK.dll)</span></span>  
`Properties` | <span data-ttu-id="ccab8-125">***Einbeziehen*** | Enthält erweiterte Einstellungen, die vom Entwickler geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="ccab8-125">***Include*** | Contains more advanced settings that can be modified by the developer</span></span>  
`Unprocessed` | <span data-ttu-id="ccab8-126">***Ignorieren*** | Enthält Unity-Dateien vom Typ `.dll` und `.pdb`</span><span class="sxs-lookup"><span data-stu-id="ccab8-126">***Ignore*** | Contains Unity `.dll` and `.pdb` files</span></span>  

## <a name="files"></a><span data-ttu-id="ccab8-127">Dateien</span><span class="sxs-lookup"><span data-stu-id="ccab8-127">Files</span></span>  

`App.cs` | <span data-ttu-id="ccab8-128">***Einbeziehen*** | Der Einstiegspunkt für Ihre UWP-Anwendung. Dieser kann geändert und mit anderen Quelldateien erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="ccab8-128">***Include*** | Entry point for your UWP application; this can be modified and extended with other source files</span></span>  
`Package.appxmanifest` | <span data-ttu-id="ccab8-129">***Einbeziehen*** | Das Paketmanifest für Ihr AppX-Paket.</span><span class="sxs-lookup"><span data-stu-id="ccab8-129">***Include*** | Package manifest for your AppX</span></span>  
`project.json` | <span data-ttu-id="ccab8-130">***Einbeziehen*** | Beschreibt die NuGet-Pakete, von denen Ihre Datei vom Typ `*.csproj` abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="ccab8-130">***Include*** | Describes the NuGet packages your `*.csproj` depends on</span></span>  
`ScrapyardPhoenix.csproj` | <span data-ttu-id="ccab8-131">***Einbeziehen*** | Beschreibt Ihr UWP-Buildziel. Wenn Sie Ihrem UWP-Projekt zusätzliche Abhängigkeiten hinzufügen, sind die entsprechenden Informationen in dieser Datei vom Typ `*.csproj` enthalten.</span><span class="sxs-lookup"><span data-stu-id="ccab8-131">***Include*** | Describes your UWP build target; if you add additional dependencies to your UWP project, this `*.csproj` file will contain that information</span></span>  
`ScrapyardPhoenix.csproj.user` | <span data-ttu-id="ccab8-132">***Ignorieren*** | Diese Datei enthält lokale Benutzerinformationen.</span><span class="sxs-lookup"><span data-stu-id="ccab8-132">***Ignore*** | This file contains local user information</span></span>

## <a name="resulting-gitignore"></a><span data-ttu-id="ccab8-133">Resultierende GITIGNORE-Datei</span><span class="sxs-lookup"><span data-stu-id="ccab8-133">Resulting .gitignore</span></span>

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

<span data-ttu-id="ccab8-134">Geschafft: Ihre Teammitglieder sind nun mit dem von Ihnen generierten UWP-Projekt synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="ccab8-134">And there you go, now your teammates will be in sync with the UWP project you've generated.</span></span> <span data-ttu-id="ccab8-135">Nun können Sie Ihrem UWP-Projekt problemlos zusätzliche Ressourcen, Quellen und Abhängigkeiten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ccab8-135">Now you can feel free to add additional assets, source, and dependencies to your UWP project.</span></span>

<span data-ttu-id="ccab8-136">Einige weitere Versionsverwaltungsbeispiele für den UWP-Ordner finden Sie [hier](https://bitbucket.org/Unity-Technologies/windowsstoreappssamples/overview).</span><span class="sxs-lookup"><span data-stu-id="ccab8-136">Some more examples of versioning the UWP folder can be found in [these examples](https://bitbucket.org/Unity-Technologies/windowsstoreappssamples/overview).</span></span>

## <a name="adding-dependencies-to-your-uwp-app"></a><span data-ttu-id="ccab8-137">Hinzufügen von Abhängigkeiten zu Ihrer UWP-App</span><span class="sxs-lookup"><span data-stu-id="ccab8-137">Adding dependencies to your UWP app</span></span>

<span data-ttu-id="ccab8-138">Fügen Sie Abhängigkeiten zu DLL- und WINMD-Dateien hinzu, indem Sie diese im Unterordner **Unity Assets** des Ordners **Plug-Ins** ablegen und auswählen. Legen Sie anschließend im Paketprüfungstool die Plattform-Zieleinstellungen fest.</span><span class="sxs-lookup"><span data-stu-id="ccab8-138">Add dependencies to DLLs and WINMDs by putting them in your **Unity Assets** folder under a **Plugins** folder, then select them and set their target platform settings appropriately in the Inspector.</span></span>

![UWP-Lösung](images/uwp-solution.PNG)

<span data-ttu-id="ccab8-140">***ScrapyardPhoenix (Universal Windows)*** ist das Projekt, dem Sie einen Verweis (etwa auf das Xbox Live SDK) hinzufügen würden.</span><span class="sxs-lookup"><span data-stu-id="ccab8-140">***ScrapyardPhoenix (Universal Windows)*** is the project you would add a reference to, for example, the Xbox Live SDK.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccab8-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ccab8-141">See also</span></span>
- [<span data-ttu-id="ccab8-142">Portieren vorhandener Spiele zu Xbox</span><span class="sxs-lookup"><span data-stu-id="ccab8-142">Bringing existing games to Xbox</span></span>](development-lanes-landing.md)
- [<span data-ttu-id="ccab8-143">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="ccab8-143">UWP on Xbox One</span></span>](index.md)
