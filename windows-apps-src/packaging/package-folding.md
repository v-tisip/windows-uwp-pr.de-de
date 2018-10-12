---
author: laurenhughes
title: Entwickeln mit Bestandspaketen und Paketfaltung
description: Hier erfahren Sie, wie Sie Ihre App mit Bestandspaketen und Paketfaltung effizient organisieren.
ms.author: lahugh
ms.date: 04/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, verpackung, paketlayout, bestandspaket
ms.localizationpriority: medium
ms.openlocfilehash: 31c27430c850f861c8b97863521202a6dcab80f7
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4563758"
---
# <a name="developing-with-asset-packages-and-package-folding"></a><span data-ttu-id="835dd-104">Entwickeln mit Bestandspaketen und Paketfaltung</span><span class="sxs-lookup"><span data-stu-id="835dd-104">Developing with asset packages and package folding</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="835dd-105">Wenn Sie Ihre App an den Store übermitteln möchten, müssen Sie sich an den [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support) wenden und eine Genehmigung für die Verwendung von Bestandspaketen und Paketfaltung erhalten.</span><span class="sxs-lookup"><span data-stu-id="835dd-105">If you intend to submit your app to the Store, you need to contact [Windows developer support](https://developer.microsoft.com/windows/support) and get approval to use asset packages and package folding.</span></span>

<span data-ttu-id="835dd-106">Bestandspakete können die Gesamtgröße der Verpackung sowie die Veröffentlichungszeit für Ihre Apps im Store reduzieren.</span><span class="sxs-lookup"><span data-stu-id="835dd-106">Asset packages can decrease the overall packaging size and publishing time for your apps to the Store.</span></span> <span data-ttu-id="835dd-107">Weitere Informationen zu Bestandspaketen und wie sie Ihre Entwicklungsiterationen beschleunigen können, finden Sie unter [Einführung zu Bestandspaketen](asset-packages.md).</span><span class="sxs-lookup"><span data-stu-id="835dd-107">You can learn more about asset packages and how it can speed up your development iterations at [Introduction to asset packages](asset-packages.md).</span></span>

<span data-ttu-id="835dd-108">Wenn Sie die Verwendung von Bestandspaketen für Ihre App in Erwägung ziehen oder bereits wissen, dass Sie sie verwenden möchten, fragen Sie sich wahrscheinlich, wie Bestandspakete Ihren Entwicklungsprozess verändern.</span><span class="sxs-lookup"><span data-stu-id="835dd-108">If you are thinking about using asset packages for your app or already know that you want to use it, then you are probably wondering about how asset packages will change your development process.</span></span> <span data-ttu-id="835dd-109">Kurz gesagt, das Entwickeln von Apps bleibt für Sie dank der Paketfaltung für Bestandspakete unverändert.</span><span class="sxs-lookup"><span data-stu-id="835dd-109">In short, app development for you stays the same - this is possible because of package folding for asset packages.</span></span>

## <a name="file-access-after-splitting-your-app"></a><span data-ttu-id="835dd-110">Dateizugriff nach dem Aufteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="835dd-110">File access after splitting your app</span></span>

<span data-ttu-id="835dd-111">Um zu verstehen, warum die Paketfaltung Ihren Entwicklungsprozesses nicht beeinflusst, müssen wir zunächst etwas weiter ausholen, um zu verstehen, was geschieht, wenn Sie Ihre App in mehrere Pakete (entweder mit Bestandspaketen oder Ressourcenpaketen) aufteilen.</span><span class="sxs-lookup"><span data-stu-id="835dd-111">To understand how package folding doesn’t impact your development process, let’s step back first to understand what happens when you split your app into multiple packages (with either asset packages or resource packages).</span></span> 

<span data-ttu-id="835dd-112">Wenn Sie einige Dateien Ihrer App in andere Pakete (die keine Architekturpakete sind) aufteilen, können Sie nicht direkt von dem Speicherort auf diese Dateien zugreifen, wo Ihr Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="835dd-112">At a high level, when you split some of your app’s files into other packages (that are not architecture packages), you will not be able to access those files directly relative to where your code runs.</span></span> <span data-ttu-id="835dd-113">Der Grund hierfür ist, dass diese Pakete alle in verschiedenen Verzeichnissen als das Architekturpaket installiert sind.</span><span class="sxs-lookup"><span data-stu-id="835dd-113">This is because these packages are all installed into different directories from where your architecture package is installed.</span></span> <span data-ttu-id="835dd-114">Z. B. wenn ein Spiel haben, und Ihr Spiel ist in lokalisiert Französisch und Deutsch und Sie für x X86- und X64 Maschinen erstellt, dann sollten Sie diese app-Paketdateien innerhalb der app-Bündel Ihres Spiels haben:</span><span class="sxs-lookup"><span data-stu-id="835dd-114">For example, if you’re making a game and your game is localized into French and German and you built for both x86 and x64 machines, then you should have these app package files within the app bundle of your game:</span></span>

-   <span data-ttu-id="835dd-115">MyGame_1.0_x86.appx</span><span class="sxs-lookup"><span data-stu-id="835dd-115">MyGame_1.0_x86.appx</span></span>
-   <span data-ttu-id="835dd-116">MyGame_1.0_x64.appx</span><span class="sxs-lookup"><span data-stu-id="835dd-116">MyGame_1.0_x64.appx</span></span>
-   <span data-ttu-id="835dd-117">MyGame_1.0_language-fr.appx</span><span class="sxs-lookup"><span data-stu-id="835dd-117">MyGame_1.0_language-fr.appx</span></span>
-   <span data-ttu-id="835dd-118">MyGame_1.0_language-de.appx</span><span class="sxs-lookup"><span data-stu-id="835dd-118">MyGame_1.0_language-de.appx</span></span>

<span data-ttu-id="835dd-119">Wenn Ihr Spiel auf dem Computer eines Benutzers installiert ist, wird jede app-Paketdatei seinen eigenen Ordner im Verzeichnis **WindowsApps** haben.</span><span class="sxs-lookup"><span data-stu-id="835dd-119">When your game is installed to a user’s machine, each app package file will have its own folder in the **WindowsApps** directory.</span></span> <span data-ttu-id="835dd-120">Für einen französischen Benutzer mit 64-Bit-Windows sieht Ihr Spiel folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="835dd-120">So for a French user running 64-bit Windows, your game will look like this:</span></span>

```example
C:\Program Files\WindowsApps\
|-- MyGame_1.0_x64
|   `-- …
|-- MyGame_1.0_language-fr
|   `-- …
`-- …(other apps)
```

<span data-ttu-id="835dd-121">Beachten Sie, dass die app-Paket-Dateien, die nicht für den Benutzer anwendbar sind nicht als (die X86- und deutschen Pakete) installiert.</span><span class="sxs-lookup"><span data-stu-id="835dd-121">Note that the app package files that are not applicable to the user will not be installed (the x86 and German packages).</span></span> 

<span data-ttu-id="835dd-122">Für diesen Benutzer befindet sich die ausführbare Hauptdatei Ihres Spiels innerhalb des **MyGame_1.0_x64**-Ordners und wird von dort aus ausgeführt. In der Regel hat diese Datei nur Zugriff auf die Dateien in diesem Ordner.</span><span class="sxs-lookup"><span data-stu-id="835dd-122">For this user, your game’s main executable will be within the **MyGame_1.0_x64** folder and will run from there, and normally, it will only have access to the files within this folder.</span></span> <span data-ttu-id="835dd-123">Für den Zugriff auf die Dateien im **MyGame_1.0_language-fr**-Ordner müssen Sie entweder die MRT-APIs oder die PackageManager-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="835dd-123">In order to access the files in the **MyGame_1.0_language-fr** folder, you would have to use either the MRT APIs or the PackageManager APIs.</span></span> <span data-ttu-id="835dd-124">Die MRT-APIs automatisch die am besten geeignete Datei aus den installierten Sprachen auswählen können, finden Sie weitere Informationen zu MRT-APIs auf [Windows.ApplicationModel.Resources.Core](https://docs.microsoft.com/uwp/api/windows.applicationmodel.resources.core).</span><span class="sxs-lookup"><span data-stu-id="835dd-124">The MRT APIs can automatically select the most appropriate file from the languages installed, you can find out more about MRT APIs at [Windows.ApplicationModel.Resources.Core](https://docs.microsoft.com/uwp/api/windows.applicationmodel.resources.core).</span></span> <span data-ttu-id="835dd-125">Alternativ finden Sie den Installationsort des französischen Sprachpakets mithilfe der [PackageManager-Klasse](https://docs.microsoft.com/uwp/api/Windows.Management.Deployment.PackageManager).</span><span class="sxs-lookup"><span data-stu-id="835dd-125">Alternatively, you can find the installed location of the French language package using the [PackageManager Class](https://docs.microsoft.com/uwp/api/Windows.Management.Deployment.PackageManager).</span></span> <span data-ttu-id="835dd-126">Sie sollten niemals den Installationsort der Pakete Ihrer App annehmen, da sich dies ändern und zwischen Benutzern variieren kann.</span><span class="sxs-lookup"><span data-stu-id="835dd-126">You should never assume the installed location of the packages of your app since this can change and can vary between users.</span></span> 

## <a name="asset-package-folding"></a><span data-ttu-id="835dd-127">Bestandspaketfaltung</span><span class="sxs-lookup"><span data-stu-id="835dd-127">Asset package folding</span></span>

<span data-ttu-id="835dd-128">Wie also können Sie auf die Dateien in Ihren Bestandspaketen zugreifen?</span><span class="sxs-lookup"><span data-stu-id="835dd-128">So how can you access the files in your asset packages?</span></span> <span data-ttu-id="835dd-129">Sie können weiterhin die Dateizugriff-APIs verwenden, die Sie für den Zugriff auf andere Dateien in Ihrem Architekturpaket verwenden.</span><span class="sxs-lookup"><span data-stu-id="835dd-129">Well, you can continue to use the file access APIs you are using to access any other file in your architecture package.</span></span> <span data-ttu-id="835dd-130">Der Grund hierfür ist, dass Bestandspaketdateien in Ihr Architekturpaket gefaltet werden, wenn es durch den Paketfaltungsprozess installiert wird.</span><span class="sxs-lookup"><span data-stu-id="835dd-130">This is because asset package files will be folded into your architecture package when it is installed through the package folding process.</span></span> <span data-ttu-id="835dd-131">Da Bestandspaketdateien ursprünglich Dateien in Ihren Architekturpaketen sein sollten, bedeutet dies darüber hinaus, dass Sie die API-Nutzung nicht ändern müssten, wenn Sie in Ihrem Entwicklungsprozess von der Bereitstellung von losen Dateien zur verpackten Bereitstellung wechseln.</span><span class="sxs-lookup"><span data-stu-id="835dd-131">Furthermore, since asset package files should originally be files within your architecture packages, this means that you would not have to change API usage when you move from loose files deployment to packaged deployment in your development process.</span></span> 

<span data-ttu-id="835dd-132">Beginnen wir mit einem Beispiel, um mehr darüber zu erfahren, wie Paketfaltung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="835dd-132">To understand more about how package folding works, let’s start with an example.</span></span> <span data-ttu-id="835dd-133">Wenn Sie ein Spielprojekt mit der folgenden Dateistruktur haben:</span><span class="sxs-lookup"><span data-stu-id="835dd-133">If you have a game project with the following file structure:</span></span>

```example
MyGame
|-- Audios
|   |-- Level1
|   |   `-- ...
|   `-- Level2
|       `-- ...
|-- Videos
|   |-- Level1
|   |   `-- ...
|   `-- Level2
|       `-- ...
|-- Engine
|   `-- ...
|-- XboxLive
|   `-- ...
`-- Game.exe
```

<span data-ttu-id="835dd-134">Wenn Sie Ihr Spiel in 3 Pakete aufteilen möchten – ein x64-Architekturpaket, ein Bestandspaket für Audiodateien und ein Bestandspaket für Videos –, wird Ihr Spiel in diese Pakete unterteilt:</span><span class="sxs-lookup"><span data-stu-id="835dd-134">If you want to split your game into 3 packages: an x64 architecture package, an asset package for audios, and an asset package for videos, your game will be divided into these packages:</span></span>

```example
MyGame_1.0_x64.appx
|-- Engine
|   `-- ...
|-- XboxLive
|   `-- ...
`-- Game.exe
MyGame_1.0_Audios.appx
`-- Audios
    |-- Level1
    |   `-- ...
    `-- Level2
        `-- ...
MyGame_1.0_Videos.appx
`-- Videos
    |-- Level1
    |   `-- ...
    `-- Level2
        `-- ...
```

<span data-ttu-id="835dd-135">Wenn Sie Ihr Spiel installieren, wird das x64-Paket als Erstes bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="835dd-135">When you install your game, the x64 package will be deployed first.</span></span> <span data-ttu-id="835dd-136">Danach werden die beiden Bestandspakete weiterhin in ihren eigenen Ordnern bereitgestellt, genau wie **MyGame_1.0_language-fr** aus unserem vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="835dd-136">Then the two asset packages will still be deployed to their own folders, just like **MyGame_1.0_language-fr** from our previous example.</span></span> <span data-ttu-id="835dd-137">Allerdings werden die Dateien des Bestandspakets aufgrund der Paketfaltung auch in den **MyGame_1.0_x64**-Ordner eingebunden (also selbst wenn die Dateien an zwei Speicherorten angezeigt werden, belegen sie nicht doppelt so viel Speicherplatz).</span><span class="sxs-lookup"><span data-stu-id="835dd-137">However, because of package folding, the asset package files will also be hard linked to appear in the **MyGame_1.0_x64** folder (so even though the files appear in two locations, they do not take up twice the disk space).</span></span> <span data-ttu-id="835dd-138">Der Speicherort, an dem die Bestandspaketdateien angezeigt werden, ist genau jener Speicherort, an dem sie sich relativ zum Stammordner des Pakets befinden.</span><span class="sxs-lookup"><span data-stu-id="835dd-138">The location in which the asset package files will appear in is exactly the location that they are at relative to the root of the package.</span></span> <span data-ttu-id="835dd-139">So sieht nun das fertige Layout des bereitgestellten Spiels aus:</span><span class="sxs-lookup"><span data-stu-id="835dd-139">So here’s what the final layout of the deployed game will look like:</span></span>

```example 
C:\Program Files\WindowsApps\
|-- MyGame_1.0_x64
|   |-- Audios
|   |   |-- Level1
|   |   |   `-- ...
|   |   `-- Level2
|   |       `-- ...
|   |-- Videos
|   |   |-- Level1
|   |   |   `-- ...
|   |   `-- Level2
|   |       `-- ...
|   |-- Engine
|   |   `-- ...
|   |-- XboxLive
|   |   `-- ...
|   `-- Game.exe
|-- MyGame_1.0_Audios
|   `-- Audios
|       |-- Level1
|       |   `-- ...
|       `-- Level2
|           `-- ...
|-- MyGame_1.0_Videos
|   `-- Videos
|       |-- Level1
|       |   `-- ...
|       `-- Level2
|           `-- ...
`-- …(other apps)
```

<span data-ttu-id="835dd-140">Wenn Sie die Paketfaltung für Bestandspakete verwenden, können Sie weiterhin auf die Dateien zugreifen, die Sie in Bestandspakete aufgeteilt haben (beachten Sie, dass der Architekturordner genau die gleiche Struktur wie der ursprüngliche Projektordner hat). Zudem können Sie Bestandspakete hinzufügen oder Dateien zwischen Bestandspaketen verschieben, ohne den Code zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="835dd-140">When using package folding for asset packages, you can still access the files you’ve split into asset packages the same way (notice that the architecture folder has the exact same structure as the original project folder), and you can add asset packages or move files between asset packages without impacting your code.</span></span> 

<span data-ttu-id="835dd-141">Sehen wir uns nun ein Beispiel einer komplizierteren Paketfaltung an.</span><span class="sxs-lookup"><span data-stu-id="835dd-141">Now for a more complicated package folding example.</span></span> <span data-ttu-id="835dd-142">Angenommen, Sie möchten Ihre Dateien stattdessen stufenbasiert aufteilen. Wenn Sie dieselbe Struktur wie die des ursprünglichen Projektordners behalten möchten, sollten Ihre Pakete wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="835dd-142">Let’s say that you want to split your files based on level instead, and if you want to keep the same structure as the original project folder, your packages should look like this:</span></span>

```example
MyGame_1.0_x64.appx
|-- Engine
|   `-- ...
|-- XboxLive
|   `-- ...
`-- Game.exe
MyGame_Level1.appx
|-- Audios
|   `-- Level1
|       `-- ...
`-- Videos
    `-- Level1
        `-- ...

MyGame_Level2.appx
|-- Audios
|   `-- Level2
|       `-- ...
`-- Videos
    `-- Level2
        `-- ...
```
<span data-ttu-id="835dd-143">Auf diese Weise können die **Level1**-Ordner und -Dateien im **MyGame_Level1**-Paket, und **Level2**-Ordner und -Dateien im **MyGame_Level2**-Paket während der Paketfaltung in den **Audiodateien**- und **Videos**-Ordner zusammengeführt werden.</span><span class="sxs-lookup"><span data-stu-id="835dd-143">This will allow the **Level1** folders and files in the **MyGame_Level1** package and **Level2** folders and files in the **MyGame_Level2** package to be merged into the **Audios** and **Videos** folders during package folding.</span></span> <span data-ttu-id="835dd-144">Es gilt also die allgemeine Regel, dass der für verpackte Dateien in der Zuordnungsdatei bestimmte relative Pfad bzw. das [Verpackungslayout](packaging-layout.md) für MakeAppx.exe der Pfad ist, den Sie für den Zugriff auf diese Dateien nach der Paketfaltung verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="835dd-144">So as a general rule, the relative path designated for packaged files in the mapping file or [packaging layout](packaging-layout.md) for MakeAppx.exe is the path you should use to access them after package folding.</span></span> 

<span data-ttu-id="835dd-145">Wenn sich zwei Dateien in verschiedenen Bestandspaketen befinden, die die gleichen relativen Pfade aufweisen, führt dies schließlich zu einer Kollision während der Paketfaltung.</span><span class="sxs-lookup"><span data-stu-id="835dd-145">Lastly, if there are two files in different asset packages that have the same relative paths, this will cause a collision during package folding.</span></span> <span data-ttu-id="835dd-146">Wenn eine Kollision auftritt, führt die Bereitstellung Ihrer App zu einem Fehler und schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="835dd-146">If a collision occurs, the deployment of your app will result in an error and fail.</span></span> <span data-ttu-id="835dd-147">Zudem können Sie Ihre App bei Verwendung von Bestandspaketen nicht auf Nicht-NTFS-Laufwerken bereitstellen, da die Paketfaltung die Vorteile von festen Links nutzt.</span><span class="sxs-lookup"><span data-stu-id="835dd-147">Also, because package folding takes advantage of hard links, if you do use asset packages, your app will not be able to be deployed to non-NTFS drives.</span></span> <span data-ttu-id="835dd-148">Wenn Sie wissen, dass Ihre App von Ihren Benutzern wahrscheinlich auf Wechseldatenträger verschoben wird, sollten Sie keine Bestandspakete verwenden.</span><span class="sxs-lookup"><span data-stu-id="835dd-148">If you know your app will likely be moved to removable drives by your users, then you should not use asset packages.</span></span> 


