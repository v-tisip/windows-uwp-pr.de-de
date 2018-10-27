---
author: JordanEllis6809
title: Portieren von Unity-Spielen für Xbox auf die UWP
description: UWP-Entwicklung für Unity-Spiele auf Xbox.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: fca3267a-0c0f-4872-8017-90384fb34215
ms.localizationpriority: medium
ms.openlocfilehash: f9851b76b218ed4241ccb617979c127d03f57ee7
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5705974"
---
# <a name="bringing-unity-games-to-uwp-on-xbox"></a><span data-ttu-id="9f3df-104">Portieren von Unity-Spielen für Xbox auf die UWP</span><span class="sxs-lookup"><span data-stu-id="9f3df-104">Bringing Unity games to UWP on Xbox</span></span>


<span data-ttu-id="9f3df-105">In diesem ausführlichen Lernprogramm wird davon ausgegangen, dass Sie bereits über ein Spiel in Unity verfügen, das zum Erstellen und Bereitstellen bereit ist.</span><span class="sxs-lookup"><span data-stu-id="9f3df-105">In this step-by-step tutorial, we assume that you already have a game in Unity, ready to be built and deployed.</span></span>

<span data-ttu-id="9f3df-106">Beachten Sie auch die [Videoversion des Lernprogramms](https://www.youtube.com/watch?v=f0Ptvw7k-CE).</span><span class="sxs-lookup"><span data-stu-id="9f3df-106">See also a [video version of this tutorial](https://www.youtube.com/watch?v=f0Ptvw7k-CE).</span></span>

<span data-ttu-id="9f3df-107">Möchten Sie eine Versionsverwaltung für Ihr Unity-UWP-Projekt verwenden?</span><span class="sxs-lookup"><span data-stu-id="9f3df-107">Looking to version your Unity UWP project?</span></span> <span data-ttu-id="9f3df-108">Siehe [Versionskontrolle für Ihr UWP-Projekt](development-lanes-unity-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="9f3df-108">See [Version control your UWP project](development-lanes-unity-versioning.md).</span></span>

## <a name="step-0-ensure-unity-is-installed-correctly"></a><span data-ttu-id="9f3df-109">Schritt0: Sicherstellen, dass Unity richtig installiert wurde</span><span class="sxs-lookup"><span data-stu-id="9f3df-109">Step 0: Ensure Unity is installed correctly</span></span>

<span data-ttu-id="9f3df-110">Beim Installieren von Unity müssen folgende Komponenten ausgewählt sein:</span><span class="sxs-lookup"><span data-stu-id="9f3df-110">When installing Unity, these components must be selected:</span></span>

![Installationskomponenten von Unity](images/unity-install-components.png)

## <a name="step-1-building-the-uwp-solution"></a><span data-ttu-id="9f3df-112">Schritt 1: Erstellen der UWP-Lösung</span><span class="sxs-lookup"><span data-stu-id="9f3df-112">Step 1: Building the UWP solution</span></span>

<span data-ttu-id="9f3df-113">Öffnen Sie in Ihrem Unity-Spielprojekt das Fenster mit den **Build-Einstellungen** unter **Datei -> Build-Einstellungen**, und wechseln Sie zum Menü mit den Microsoft Store-Optionen.</span><span class="sxs-lookup"><span data-stu-id="9f3df-113">In your Unity game project, open the **Build Settings** windows located at **File -> Build Settings**, and go to the Microsoft Store options menu.</span></span>

![Fenster mit Build-Einstellungen](images/build-settings.png)

<span data-ttu-id="9f3df-115">Stellen Sie sicher, dass die **SDK**-Einstellung auf **Universal10** gesetzt ist, und klicken Sie dann auf die Schaltfläche **Build**. Ein Datei-Explorer-Fenster wird geöffnet, in dem Sie nach einem Zielordner gefragt werden.</span><span class="sxs-lookup"><span data-stu-id="9f3df-115">Make sure the **SDK** setting is set to **Universal 10**, and then select the **Build** button, which will launch a File Explorer window asking for a destination folder.</span></span> <span data-ttu-id="9f3df-116">Erstellen Sie neben dem Verzeichnis **Assets** Ihres Projekts den Ordner **UWP**, und wählen Sie diesen Ordner als Zielordner des Builds aus.</span><span class="sxs-lookup"><span data-stu-id="9f3df-116">Create a folder named **UWP** next to the **Assets** directory of your project, and choose this folder as the destination folder of the build.</span></span>

![Build-Zielordner](images/build-destination.png)

<span data-ttu-id="9f3df-118">Unity hat eine neue Visual Studio-Lösung erstellt, die wir zum Bereitstellen Ihres UWP-Spiels verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f3df-118">Unity has now created a new Visual Studio solution that we will use to deploy your UWP game from.</span></span>

![UWP-VS-Lösung](images/uwp-vs-solution.png)

## <a name="step-2-deploying-your-game"></a><span data-ttu-id="9f3df-120">Schritt 2: Bereitstellen des Spiels</span><span class="sxs-lookup"><span data-stu-id="9f3df-120">Step 2: Deploying your game</span></span>

<span data-ttu-id="9f3df-121">Öffnen Sie die neu erstellte Lösung im Ordner **UWP**, und ändern Sie die Zielplattform zu **x64**.</span><span class="sxs-lookup"><span data-stu-id="9f3df-121">Open the newly generated solution in the **UWP** folder, and then change the target platform to **x64**.</span></span>

![x64-Build-Plattform](images/x64-build-platform.png)

<span data-ttu-id="9f3df-123">Nachdem Sie nun über eine Visual Studio-UWP-Lösung für Ihr Spiel verfügen, [befolgen Sie diese Schritte](getting-started.md), um Ihr Spiel erfolgreich auf Ihrer Xbox One-Konsole für den Einzelhandel bereitzustellen!</span><span class="sxs-lookup"><span data-stu-id="9f3df-123">Now that you have a UWP Visual Studio solution for your game, [following these steps](getting-started.md) will allow you to successfuly deploy your game onto your retail Xbox One!</span></span>

## <a name="step-3-modify-and-rebuild"></a><span data-ttu-id="9f3df-124">Schritt3: Ändern und Neuerstellen</span><span class="sxs-lookup"><span data-stu-id="9f3df-124">Step 3: Modify and rebuild</span></span>

<span data-ttu-id="9f3df-125">Wenn etwas anderes als ein Skript geändert wird, muss das Projekt im Editor neu erstellt werden (siehe __Schritt1__), damit die Änderungen in den UWP-Build Ihres Spiel übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="9f3df-125">If changes are made to anything that isn't a script, for these changes to be shown in your game's UWP build, the project must be rebuilt from within the Editor (as described in __Step 1__).</span></span>

## <a name="versioning-your-uwp-project"></a><span data-ttu-id="9f3df-126">Versionsverwaltung für Ihr UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="9f3df-126">Versioning your UWP project</span></span>

<span data-ttu-id="9f3df-127">In bestimmten Situationen müssen Teile dieses neu generierten UWP-Verzeichnisses der Versionskontrolle hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="9f3df-127">There are a few common situations where adding parts of this newly generated UWP directory to version control becomes necessary.</span></span> <span data-ttu-id="9f3df-128">Dies ist beispielsweise der Fall, wenn Sie dem UWP-Projekt eine neue Abhängigkeit (z.B. das Xbox Live SDK) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9f3df-128">For example, if you're adding a new dependency to the UWP project (for example, the Xbox Live SDK).</span></span>  <span data-ttu-id="9f3df-129">Wir betrachten dieses Beispiel unter [Versionskontrolle für Ihr UWP-Projekt](development-lanes-unity-versioning.md) ausführlich.</span><span class="sxs-lookup"><span data-stu-id="9f3df-129">We go over this example in detail at [Version control your UWP project](development-lanes-unity-versioning.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f3df-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9f3df-130">See also</span></span>
- [<span data-ttu-id="9f3df-131">Portieren vorhandener Spiele zu Xbox</span><span class="sxs-lookup"><span data-stu-id="9f3df-131">Bringing existing games to Xbox</span></span>](development-lanes-landing.md)
- [<span data-ttu-id="9f3df-132">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="9f3df-132">UWP on Xbox One</span></span>](index.md)
