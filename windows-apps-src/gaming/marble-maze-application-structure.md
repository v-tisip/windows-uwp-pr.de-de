---
author: eliotcowley
title: Marble Maze-Anwendungsstruktur
description: Die Struktur einer DirectX-UWP-App unterscheidet sich von der einer herkömmlichen Desktopanwendung.
ms.assetid: 6080f0d3-478a-8bbe-d064-73fd3d432074
ms.author: elcowle
ms.date: 09/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Spiele, Beispiel, Directx, Struktur
ms.localizationpriority: medium
ms.openlocfilehash: c26b547d5cc94f3277d0c898804e65d75e6d17e2
ms.sourcegitcommit: cceaf2206ec53a3e9155f97f44e4795a7b6a1d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
ms.locfileid: "1700876"
---
# <a name="marble-maze-application-structure"></a><span data-ttu-id="97454-104">Anwendungsstruktur von Marble Maze</span><span class="sxs-lookup"><span data-stu-id="97454-104">Marble Maze application structure</span></span>




<span data-ttu-id="97454-105">Die Struktur einer DirectX-UWP-App unterscheidet sich von der einer herkömmlichen Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="97454-105">The structure of a DirectX Universal Windows Platform (UWP) app differs from that of a traditional desktop application.</span></span> <span data-ttu-id="97454-106">Die Windows-Runtime verwendet keine Handletypen wie z.B. [HWND](https://msdn.microsoft.com/library/windows/desktop/aa383751) und keine Funktionen wie z.B. [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679), sondern stellt Schnittstellen, z.B. [Windows::UI::Core::ICoreWindow](https://msdn.microsoft.com/library/windows/apps/br208296) bereit, sodass Sie UWP-Apps auf modernere Weise und mit stärkerer Objektorientierung entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="97454-106">Instead of working with handle types such as [HWND](https://msdn.microsoft.com/library/windows/desktop/aa383751) and functions such as [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679), the Windows Runtime provides interfaces such as [Windows::UI::Core::ICoreWindow](https://msdn.microsoft.com/library/windows/apps/br208296) so that you can develop UWP apps in a more modern, object-oriented manner.</span></span> <span data-ttu-id="97454-107">In diesem Abschnitt der Dokumentation ist dargestellt, wie der App-code von Marble Maze strukturiert ist.</span><span class="sxs-lookup"><span data-stu-id="97454-107">This section of the documentation shows how the Marble Maze app code is structured.</span></span>

> [!NOTE]
> <span data-ttu-id="97454-108">Den Beispielcode für dieses Dokument finden Sie im [DirectX-Beispielspiel Marble Maze](http://go.microsoft.com/fwlink/?LinkId=624011).</span><span class="sxs-lookup"><span data-stu-id="97454-108">The sample code that corresponds to this document is found in the [DirectX Marble Maze game sample](http://go.microsoft.com/fwlink/?LinkId=624011).</span></span>

 
## 
<span data-ttu-id="97454-109">Es folgen einige wichtige Punkte, die in diesem Dokument für das Strukturieren von Spielcode erläutert werden:</span><span class="sxs-lookup"><span data-stu-id="97454-109">Here are some of the key points that this document discusses for when you structure your game code:</span></span>

-   <span data-ttu-id="97454-110">Richten Sie in der Initialisierungsphase Laufzeit- und Bibliothekskomponenten ein, die das Spiel verwendet. Laden Sie auch spielspezifische Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="97454-110">In the initialization phase, set up the runtime and library components that your game uses, and load game-specific resources.</span></span>
-   <span data-ttu-id="97454-111">Bei UWP-Apps muss der Start der Ereignisverarbeitung innerhalb von 5Sekunden nach dem Start der App erfolgen.</span><span class="sxs-lookup"><span data-stu-id="97454-111">UWP apps must start processing events within 5 seconds of launch.</span></span> <span data-ttu-id="97454-112">Laden Sie daher beim Laden Ihrer App nur wichtige Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="97454-112">Therefore, load only essential resources when you load your app.</span></span> <span data-ttu-id="97454-113">Spiele sollten umfangreiche Ressourcen im Hintergrund laden und einen Statusbildschirm anzeigen.</span><span class="sxs-lookup"><span data-stu-id="97454-113">Games should load large resources in the background and display a progress screen.</span></span>
-   <span data-ttu-id="97454-114">In der Spielschleife sollten vier Aktionen ausgeführt werden: Verarbeiten von Windows-Ereignissen, Lesen von Benutzereingaben, Aktualisieren von Szenenobjekten und Rendern der Szene.</span><span class="sxs-lookup"><span data-stu-id="97454-114">In the game loop, respond to Windows events, read user input, update scene objects, and render the scene.</span></span>
-   <span data-ttu-id="97454-115">Reagieren Sie mithilfe von Handlern auf Fensterereignisse.</span><span class="sxs-lookup"><span data-stu-id="97454-115">Use event handlers to respond to window events.</span></span> <span data-ttu-id="97454-116">(Diese ersetzen die Fenstermeldungen in Windows-Desktopanwendungen.)</span><span class="sxs-lookup"><span data-stu-id="97454-116">(These replace the window messages from desktop Windows applications.)</span></span>
-   <span data-ttu-id="97454-117">Verwenden Sie einen Zustandsautomaten, um den Fluss und die Reihenfolge der Spiellogik zu steuern.</span><span class="sxs-lookup"><span data-stu-id="97454-117">Use a state machine to control the flow and order of the game logic.</span></span>

##  <a name="file-organization"></a><span data-ttu-id="97454-118">Dateiorganisation</span><span class="sxs-lookup"><span data-stu-id="97454-118">File organization</span></span>


<span data-ttu-id="97454-119">Einige der Komponenten in Marble Maze können mit geringfügigen oder ohne Änderungen für andere Spiele wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="97454-119">Some of the components in Marble Maze can be reused with any game with little or no modification.</span></span> <span data-ttu-id="97454-120">Sie können die Organisation und die Ideen aus diesen Dateien für Ihr eigenes Spiel anpassen.</span><span class="sxs-lookup"><span data-stu-id="97454-120">For your own game, you can adapt the organization and ideas that these files provide.</span></span> <span data-ttu-id="97454-121">In der folgenden Tabelle sind die wichtigen Quellcodedateien kurz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="97454-121">The following table briefly describes the important source code files.</span></span>

| <span data-ttu-id="97454-122">Dateien</span><span class="sxs-lookup"><span data-stu-id="97454-122">Files</span></span>                                      | <span data-ttu-id="97454-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="97454-123">Description</span></span>                                                                                                                                                                          |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="97454-124">App.h, App.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-124">App.h, App.cpp</span></span>               | <span data-ttu-id="97454-125">Definiert die **App**- und **DirectXApplicationSource**-Klassen, die die Ansicht (Fenster, Thread und Ereignisse) der App kapseln.</span><span class="sxs-lookup"><span data-stu-id="97454-125">Defines the **App** and **DirectXApplicationSource** classes, which encapsulate the view (window, thread, and events) of the app.</span></span>                                                     |
| <span data-ttu-id="97454-126">Audio.h, Audio.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-126">Audio.h, Audio.cpp</span></span>                         | <span data-ttu-id="97454-127">Definiert die **Audio**-Klasse, die Audioressourcen verwaltet.</span><span class="sxs-lookup"><span data-stu-id="97454-127">Defines the **Audio** class, which manages audio resources.</span></span>                                                                                                                          |
| <span data-ttu-id="97454-128">BasicLoader.h, BasicLoader.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-128">BasicLoader.h, BasicLoader.cpp</span></span>             | <span data-ttu-id="97454-129">Definiert die **BasicLoader**-Klasse, die Dienstprogrammmethoden bereitstellt, mit denen Sie Texturen, Gitter und Shader laden können.</span><span class="sxs-lookup"><span data-stu-id="97454-129">Defines the **BasicLoader** class, which provides utility methods that help you load textures, meshes, and shaders.</span></span>                                                                  |
| <span data-ttu-id="97454-130">BasicMath.h</span><span class="sxs-lookup"><span data-stu-id="97454-130">BasicMath.h</span></span>                                | <span data-ttu-id="97454-131">Definiert Strukturen und Funktionen, mit denen Sie Vektor- und Matrixdaten und -berechnungen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="97454-131">Defines structures and functions that help you work with vector and matrix data and computations.</span></span> <span data-ttu-id="97454-132">Viele dieser Funktionen sind mit HLSL-Shadertypen kompatibel.</span><span class="sxs-lookup"><span data-stu-id="97454-132">Many of these functions are compatible with HLSL shader types.</span></span>                     |
| <span data-ttu-id="97454-133">BasicInformationen zu einigen der wichtigsten Vorgehensweisen, die Sie beim Verwenden von visuellen Ressourcen berücksichtigen sollten, finden Sie unter Writer.h, BasicInformationen zu einigen der wichtigsten Vorgehensweisen, die Sie beim Verwenden von visuellen Ressourcen berücksichtigen sollten, finden Sie unter Writer.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-133">BasicReaderWriter.h, BasicReaderWriter.cpp</span></span> | <span data-ttu-id="97454-134">Definiert die **BasicReaderWriter**-Klasse, die die Windows-Runtime zum Lesen und Schreiben von Dateidaten in einer UWP-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="97454-134">Defines the **BasicReaderWriter** class, which uses the Windows Runtime to read and write file data in a UWP app.</span></span>                                                                    |
| <span data-ttu-id="97454-135">BasicShapes.h, BasicShapes.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-135">BasicShapes.h, BasicShapes.cpp</span></span>             | <span data-ttu-id="97454-136">Definiert die **BasicShapes**-Klasse, die Dienstprogrammmethoden zum Erstellen von Grundformen wie Würfeln und Kugeln bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="97454-136">Defines the **BasicShapes** class, which provides utility methods for creating basic shapes such as cubes and spheres.</span></span> <span data-ttu-id="97454-137">(Diese Dateien werden von der Marble Maze-Implementierung nicht verwendet).</span><span class="sxs-lookup"><span data-stu-id="97454-137">(These files are not used by the Marble Maze implementation).</span></span> |                                                                                  |
| <span data-ttu-id="97454-138">Camera.h, Camera.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-138">Camera.h, Camera.cpp</span></span>                       | <span data-ttu-id="97454-139">Definiert die **Camera**-Klasse, die die Position und Ausrichtung einer Kamera bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="97454-139">Defines the **Camera** class, which provides the position and orientation of a camera.</span></span>                                                                                               |
| <span data-ttu-id="97454-140">Collision.h, Collision.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-140">Collision.h, Collision.cpp</span></span>                 | <span data-ttu-id="97454-141">Verwaltet Informationen über das Aufeinandertreffen der Murmel mit anderen Objekten, z. B. dem Labyrinth.</span><span class="sxs-lookup"><span data-stu-id="97454-141">Manages collision info between the marble and other objects, such as the maze.</span></span>                                                                                                       |
| <span data-ttu-id="97454-142">DDSTextureLoader.h, DDSTextureLoader.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-142">DDSTextureLoader.h, DDSTextureLoader.cpp</span></span>   | <span data-ttu-id="97454-143">Definiert die **CreateDDSTextureFromMemory**-Funktion, die Texturen im DDS-Format aus einem Speicherpuffer lädt.</span><span class="sxs-lookup"><span data-stu-id="97454-143">Defines the **CreateDDSTextureFromMemory** function, which loads textures that are in .dds format from a memory buffer.</span></span>                                                              |
| <span data-ttu-id="97454-144">DirectXHelper.h</span><span class="sxs-lookup"><span data-stu-id="97454-144">DirectXHelper.h</span></span>             | <span data-ttu-id="97454-145">Definiert die DirectX-Hilfsfunktionen, die in vielen DirectX-UWP-Apps hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="97454-145">Defines DirectX helper functions that are useful to many DirectX UWP apps.</span></span>                                                                            |
| <span data-ttu-id="97454-146">LoadScreen.h, LoadScreen.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-146">LoadScreen.h, LoadScreen.cpp</span></span>               | <span data-ttu-id="97454-147">Definiert die **LoadScreen**-Klasse, die bei der App-Initialisierung einen Ladebildschirm anzeigt.</span><span class="sxs-lookup"><span data-stu-id="97454-147">Defines the **LoadScreen** class, which displays a loading screen during app initialization.</span></span>                                                                                         |
| <span data-ttu-id="97454-148">MarbleMazeMain.h, MarbleMazeMain.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-148">MarbleMazeMain.h, MarbleMazeMain.cpp</span></span>               | <span data-ttu-id="97454-149">Definiert die **MarbleMazeMain**-Klasse, die spielspezifische Ressourcen verwaltet und den Großteil der Spiellogik definiert.</span><span class="sxs-lookup"><span data-stu-id="97454-149">Defines the **MarbleMazeMain** class, which manages game-specific resources and defines much of the game logic.</span></span>                                                                          |
| <span data-ttu-id="97454-150">MediaStreamer.h, MediaStreamer.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-150">MediaStreamer.h, MediaStreamer.cpp</span></span>         | <span data-ttu-id="97454-151">Definiert die **MediaStreamer**-Klasse, die Media Foundation verwendet, um das Spiel beim Verwalten von Audioressourcen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="97454-151">Defines the **MediaStreamer** class, which uses Media Foundation to help the game manage audio resources.</span></span>                                                                            |
| <span data-ttu-id="97454-152">PersistentState.h, PersistentState.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-152">PersistentState.h, PersistentState.cpp</span></span>     | <span data-ttu-id="97454-153">Definiert die **PersistentState**-Klasse, die primitive Datentypen aus einem Sicherungsspeicher liest und in einen Sicherungsspeicher schreibt.</span><span class="sxs-lookup"><span data-stu-id="97454-153">Defines the **PersistentState** class, which reads and writes primitive data types from and to a backing store.</span></span>                                                                      |
| <span data-ttu-id="97454-154">Physics.h, Physics.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-154">Physics.h, Physics.cpp</span></span>                     | <span data-ttu-id="97454-155">Definiert die **Physics**-Klasse, die die physische Simulation zwischen der Murmel und dem Labyrinth implementiert.</span><span class="sxs-lookup"><span data-stu-id="97454-155">Defines the **Physics** class, which implements the physics simulation between the marble and the maze.</span></span>                                                                              |
| <span data-ttu-id="97454-156">Primitives.h</span><span class="sxs-lookup"><span data-stu-id="97454-156">Primitives.h</span></span>                               | <span data-ttu-id="97454-157">Definiert geometrische Typen, die vom Spiel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="97454-157">Defines geometric types that are used by the game.</span></span>                                                                                                                                   |
| <span data-ttu-id="97454-158">SampleOverlay.h, SampleOverlay.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-158">SampleOverlay.h, SampleOverlay.cpp</span></span>         | <span data-ttu-id="97454-159">Definiert die **SampleOverlay**-Klasse, die allgemeine 2D- und Benutzeroberflächendaten und -vorgänge bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="97454-159">Defines the **SampleOverlay** class, which provides common 2D and user-interface data and operations.</span></span>                                                                               |
| <span data-ttu-id="97454-160">SDKMesh.h, SDKMesh.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-160">SDKMesh.h, SDKMesh.cpp</span></span>                     | <span data-ttu-id="97454-161">Definiert die **SDKMesh**-Klasse, die Gitter lädt und rendert, die im SDK Mesh-Format (.sdkmesh) vorliegen.</span><span class="sxs-lookup"><span data-stu-id="97454-161">Defines the **SDKMesh** class, which loads and renders meshes that are in SDK Mesh (.sdkmesh) format.</span></span>                                                                                |
| <span data-ttu-id="97454-162">StepTimer.h</span><span class="sxs-lookup"><span data-stu-id="97454-162">StepTimer.h</span></span>               | <span data-ttu-id="97454-163">Definiert die **StepTimer**-Klasse, die eine einfache Möglichkeit zum Abrufen von Gesamtzeiten und verstrichenen Zeiten bietet.</span><span class="sxs-lookup"><span data-stu-id="97454-163">Defines the **StepTimer** class, which provides an easy way to get total and elapsed times.</span></span>
| <span data-ttu-id="97454-164">UserInterface.h, UserInterface.cpp</span><span class="sxs-lookup"><span data-stu-id="97454-164">UserInterface.h, UserInterface.cpp</span></span>         | <span data-ttu-id="97454-165">Definiert die Funktionalität, die mit der Benutzeroberfläche (z. B. dem Menüsystem und der Bestenliste) verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="97454-165">Defines functionality that's related to the user interface, such as the menu system and the high score table.</span></span>                                                                        |

 

##  <a name="design-time-versus-run-time-resource-formats"></a><span data-ttu-id="97454-166">Entwurfszeit- und Laufzeitressourcenformate</span><span class="sxs-lookup"><span data-stu-id="97454-166">Design-time versus run-time resource formats</span></span>


<span data-ttu-id="97454-167">Verwenden Sie nach Möglichkeit Laufzeitformate anstelle von Entwurfszeitformaten, um Spielressourcen effizienter zu laden.</span><span class="sxs-lookup"><span data-stu-id="97454-167">When you can, use run-time formats instead of design-time formats to more efficiently load game resources.</span></span>

<span data-ttu-id="97454-168">Ein *Entwurfszeitformat* ist das Format, das Sie verwenden, wenn Sie die Ressource entwerfen.</span><span class="sxs-lookup"><span data-stu-id="97454-168">A *design-time* format is the format you use when you design your resource.</span></span> <span data-ttu-id="97454-169">In der Regel verwenden 3D-Designer Entwurfszeitformate.</span><span class="sxs-lookup"><span data-stu-id="97454-169">Typically, 3D designers work with design-time formats.</span></span> <span data-ttu-id="97454-170">Einige Entwurfszeitformate sind auch textbasiert, um sie in jedem textbasierten Editor ändern zu können.</span><span class="sxs-lookup"><span data-stu-id="97454-170">Some design-time formats are also text-based so that you can modify them in any text-based editor.</span></span> <span data-ttu-id="97454-171">Entwurfszeitformate können sehr ausführlich sein und mehr Informationen enthalten, als das Spiel erfordert.</span><span class="sxs-lookup"><span data-stu-id="97454-171">Design-time formats can be verbose and contain more information than your game requires.</span></span> <span data-ttu-id="97454-172">Ein *Laufzeitformat* ist das Binärformat, das vom Spiel gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="97454-172">A *run-time* format is the binary format that is read by your game.</span></span> <span data-ttu-id="97454-173">Laufzeitformate sind in der Regel kompakter und effizienter zu laden als die entsprechenden Entwurfszeitformate.</span><span class="sxs-lookup"><span data-stu-id="97454-173">Run-time formats are typically more compact and more efficient to load than the corresponding design-time formats.</span></span> <span data-ttu-id="97454-174">Daher verwenden die meisten Spiele zur Laufzeit Laufzeitressourcen.</span><span class="sxs-lookup"><span data-stu-id="97454-174">This is why the majority of games use run-time assets at run time.</span></span>

<span data-ttu-id="97454-175">Auch wenn das Spiel ein Entwurfszeitformat direkt lesen kann, bietet die Verwendung eines separaten Laufzeitformats viele Vorteile.</span><span class="sxs-lookup"><span data-stu-id="97454-175">Although your game can directly read a design-time format, there are several benefits to using a separate run-time format.</span></span> <span data-ttu-id="97454-176">Da Laufzeitformate häufig kompakter sind, benötigen sie weniger Speicherplatz und weniger Zeit für die Übertragung über ein Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="97454-176">Because run-time formats are often more compact, they require less disk space and require less time to transfer over a network.</span></span> <span data-ttu-id="97454-177">Außerdem werden Laufzeitfomate häufig als im Speicher abgebildete Datenstrukturen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="97454-177">Also, run-time formats are often represented as memory-mapped data structures.</span></span> <span data-ttu-id="97454-178">Deshalb können sie viel schneller in den Speicher geladen werden als beispielsweise eine XML-basierte Textdatei.</span><span class="sxs-lookup"><span data-stu-id="97454-178">Therefore, they can be loaded into memory much faster than, for example, an XML-based text file.</span></span> <span data-ttu-id="97454-179">Da separate Laufzeitformate in der Regel binär codiert werden, lassen sich diese vom Endbenutzer letztendlich schwieriger ändern.</span><span class="sxs-lookup"><span data-stu-id="97454-179">Finally, because separate run-time formats are typically binary-encoded, they are more difficult for the end-user to modify.</span></span>

<span data-ttu-id="97454-180">HLSL-Shader sind ein Beispiel für Ressourcen, die verschiedene Entwurfszeit- und Laufzeitformate verwenden.</span><span class="sxs-lookup"><span data-stu-id="97454-180">HLSL shaders are one example of resources that use different design-time and run-time formats.</span></span> <span data-ttu-id="97454-181">Marble Maze verwendet HLSL-Dateien als Entwurfszeitformat und CSO-Dateien als Laufzeitformat.</span><span class="sxs-lookup"><span data-stu-id="97454-181">Marble Maze uses .hlsl as the design-time format, and .cso as the run-time format.</span></span> <span data-ttu-id="97454-182">Eine HLSL-Datei enthält den Shaderquellcode und eine CSO-Datei den entsprechenden Shaderbytecode.</span><span class="sxs-lookup"><span data-stu-id="97454-182">A .hlsl file holds source code for the shader; a .cso file holds the corresponding shader byte code.</span></span> <span data-ttu-id="97454-183">Wenn Sie HLSL-Dateien offline konvertieren und für das Spiel CSO-Dateien bereitstellen, müssen Sie die HLSL-Quelldateien beim Laden des Spiels nicht in Bytecode konvertieren.</span><span class="sxs-lookup"><span data-stu-id="97454-183">When you convert .hlsl files offline and provide .cso files with your game, you avoid the need to convert HLSL source files to byte code when your game loads.</span></span>

<span data-ttu-id="97454-184">Aus anleitungstechnischen Gründen enthält das Marble Maze-Projekt für viele Ressourcen sowohl das Entwurfszeitformat als auch das Laufzeitformat. Für ein eigenes Spiel benötigen Sie jedoch nur die Entwurfszeitformate im Quellprojekt, da Sie diese bei Bedarf in Laufzeitformate konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="97454-184">For instructional reasons, the Marble Maze project includes both the design-time format and the run-time format for many resources, but you only have to maintain the design-time formats in the source project for your own game because you can convert them to run-time formats when you need them.</span></span> <span data-ttu-id="97454-185">In dieser Dokumentation wird gezeigt, wie die Entwurfszeitformate in Laufzeitformate konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="97454-185">This documentation shows how to convert the design-time formats to the run-time formats.</span></span>

##  <a name="application-life-cycle"></a><span data-ttu-id="97454-186">Anwendungslebenszyklus</span><span class="sxs-lookup"><span data-stu-id="97454-186">Application life cycle</span></span>


<span data-ttu-id="97454-187">Marble Maze folgt dem Lebenszyklus einer typischen UWP-App.</span><span class="sxs-lookup"><span data-stu-id="97454-187">Marble Maze follows the life cycle of a typical UWP app.</span></span> <span data-ttu-id="97454-188">Weitere Informationen zum Lebenszyklus von UWP-Apps finden Sie unter [App-Lebenszyklus](https://msdn.microsoft.com/library/windows/apps/mt243287).</span><span class="sxs-lookup"><span data-stu-id="97454-188">For more info about the life cycle of a UWP app, see [App lifecycle](https://msdn.microsoft.com/library/windows/apps/mt243287).</span></span>

<span data-ttu-id="97454-189">Ein UWP-Spiel initialisiert in der Regel Laufzeitkomponenten wie Direct3D, Direct2D und alle von ihm verwendeten Eingabe-, Audio- oder Physikbibliotheken.</span><span class="sxs-lookup"><span data-stu-id="97454-189">When a UWP game initializes, it typically initializes runtime components such as Direct3D, Direct2D, and any input, audio, or physics libraries that it uses.</span></span> <span data-ttu-id="97454-190">Es lädt auch spielspezifische Ressourcen, die vor dem Starten des Spiels erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="97454-190">It also loads game-specific resources that are required before the game begins.</span></span> <span data-ttu-id="97454-191">Diese Initialisierung erfolgt einmalig während einer Spielsitzung.</span><span class="sxs-lookup"><span data-stu-id="97454-191">This initialization occurs one time during a game session.</span></span>

<span data-ttu-id="97454-192">Nach der Initialisierung führen Spiele in der Regel die *Spielschleife* aus.</span><span class="sxs-lookup"><span data-stu-id="97454-192">After initialization, games typically run the *game loop*.</span></span> <span data-ttu-id="97454-193">In dieser Schleife führen Spiele in der Regel vier Aktionen aus: Verarbeiten von Windows-Ereignissen, Sammeln von Eingaben, Aktualisieren von Szenenobjekten und Rendern der Szene.</span><span class="sxs-lookup"><span data-stu-id="97454-193">In this loop, games typically perform four actions: process Windows events, collect input, update scene objects, and render the scene.</span></span> <span data-ttu-id="97454-194">Wenn das Spiel die Szene aktualisiert, kann es den aktuellen Eingabezustand für die Szenenobjekte übernehmen und physische Ereignisse wie das Aufeinandertreffen von Objekten simulieren.</span><span class="sxs-lookup"><span data-stu-id="97454-194">When the game updates the scene, it can apply the current input state to the scene objects and simulate physical events, such as object collisions.</span></span> <span data-ttu-id="97454-195">Das Spiel kann auch andere Aktivitäten wie die Wiedergabe von Soundeffekten oder das Senden von Daten über das Netzwerk ausführen.</span><span class="sxs-lookup"><span data-stu-id="97454-195">The game can also perform other activities such as playing sound effects or sending data over the network.</span></span> <span data-ttu-id="97454-196">Wenn das Spiel die Szene rendert, zeichnet es den aktuellen Zustand der Szene auf und zeichnet es auf das Anzeigegerät.</span><span class="sxs-lookup"><span data-stu-id="97454-196">When the game renders the scene, it captures the current state of the scene and draws it to the display device.</span></span> <span data-ttu-id="97454-197">In den nachfolgenden Abschnitten sind diese Aktivitäten ausführlicher beschrieben.</span><span class="sxs-lookup"><span data-stu-id="97454-197">The following sections describe these activities in greater detail.</span></span>

##  <a name="adding-to-the-template"></a><span data-ttu-id="97454-198">Ergänzen der Vorlage</span><span class="sxs-lookup"><span data-stu-id="97454-198">Adding to the template</span></span>


<span data-ttu-id="97454-199">Die **DirectX 11-App (Universal Windows)** -Vorlage erstellt ein Kernfenster, in dem Sie mit Direct3D rendern können.</span><span class="sxs-lookup"><span data-stu-id="97454-199">The **DirectX 11 App (Universal Windows)** template creates a core window to which you can render with Direct3D.</span></span> <span data-ttu-id="97454-200">Die Vorlage enthält auch die **DeviceResources**-Klasse, die alle zum Rendern von 3D-Inhalten in einer UWP-App erforderlichen Direct3D-Geräteressourcen erstellt.</span><span class="sxs-lookup"><span data-stu-id="97454-200">The template also includes the **DeviceResources** class that creates all of the Direct3D device resources needed for rendering 3D content in a UWP app.</span></span>

<span data-ttu-id="97454-201">Die **App**-Klasse erstellt das **MarbleMazeMain**-Klassenobjekt, startet das Laden von Ressourcen, führt eine Schleife zum Upgrade des Timers aus und ruft die **MarbleMazeMain::Render**-Methode für jeden Frame auf.</span><span class="sxs-lookup"><span data-stu-id="97454-201">The **App** class creates the **MarbleMazeMain** class object, starts the loading of resources, loops to update the timer, and calls the **MarbleMazeMain::Render** method each frame.</span></span> <span data-ttu-id="97454-202">Die **App::OnWindowSizeChanged**, **App::OnDpiChanged** und **App::OnOrientationChanged**-Methoden rufen die **MarbleMazeMain::CreateWindowSizeDependentResources** -Methode auf, und die **Implementierungscode**-Methode ruft die **MarbleMazeMain::Update** und **MarbleMazeMain::Render**-Methoden auf.</span><span class="sxs-lookup"><span data-stu-id="97454-202">The **App::OnWindowSizeChanged**, **App::OnDpiChanged**, and **App::OnOrientationChanged** methods each call the **MarbleMazeMain::CreateWindowSizeDependentResources** method, and the **App::Run** method calls the **MarbleMazeMain::Update** and **MarbleMazeMain::Render** methods.</span></span>

<span data-ttu-id="97454-203">Das folgende Beispiel zeigt, an welcher Stelle der **App::SetWindow**-Methode das **MarbleMazeMain**-Klassenobjekt erstellt.</span><span class="sxs-lookup"><span data-stu-id="97454-203">The following example shows where the **App::SetWindow** method creates the **MarbleMazeMain** class object.</span></span> <span data-ttu-id="97454-204">Die **DeviceResources**-Klasse wird an die Methode übergeben, sodass sie die Direct3D-Objekte zum Rendern verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="97454-204">The **DeviceResources** class is passed to the method so it can use the Direct3D objects for rendering.</span></span>

```cpp
    m_main = std::unique_ptr<MarbleMazeMain>(new MarbleMazeMain(m_deviceResources));
```

<span data-ttu-id="97454-205">Die **App**-Klasse startet auch das Laden der verzögerten Ressourcen für das Spiel.</span><span class="sxs-lookup"><span data-stu-id="97454-205">The **App** class also starts loading the deferred resources for the game.</span></span> <span data-ttu-id="97454-206">Ausführliche Informationen dazu finden Sie im nächsten Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="97454-206">See the next section for more detail.</span></span>

<span data-ttu-id="97454-207">Darüber hinaus richtet die **App**-Klasse die Ereignishandler für die [CoreWindow](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow)-Ereignisse ein.</span><span class="sxs-lookup"><span data-stu-id="97454-207">Additionally, the **App** class sets up the event handlers for the [CoreWindow](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow) events.</span></span> <span data-ttu-id="97454-208">Wenn die Handler für diese Ereignisse aufgerufen werden, übergeben sie die Eingabe an die **MarbleMazeMain**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="97454-208">When the handlers for these events are called, they pass the input to the **MarbleMazeMain** class.</span></span>

## <a name="loading-game-assets-in-the-background"></a><span data-ttu-id="97454-209">Laden von Spielressourcen im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="97454-209">Loading game assets in the background</span></span>


<span data-ttu-id="97454-210">Damit das Spiel innerhalb von 5 Sekunden nach dem Starten auf Fensterereignisse reagieren kann, wird empfohlen, die Spielressourcen asynchron oder im Hintergrund zu laden.</span><span class="sxs-lookup"><span data-stu-id="97454-210">To ensure that your game can respond to window events within 5 seconds after it is launched, we recommend that you load your game assets asynchronously, or in the background.</span></span> <span data-ttu-id="97454-211">Während die Objekte im Hintergrund geladen werden, kann das Spiel auf Fensterereignisse reagieren.</span><span class="sxs-lookup"><span data-stu-id="97454-211">As assets load in the background, your game can respond to window events.</span></span>

> [!NOTE]
> <span data-ttu-id="97454-212">Sie können auch das Hauptmenü anzeigen, wenn es bereit ist, und den übrigen Ressourcen erlauben, den Ladevorgang im Hintergrund fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="97454-212">You can also display the main menu when it is ready, and allow the remaining assets to continue loading in the background.</span></span> <span data-ttu-id="97454-213">Wenn der Benutzer eine Menüoption auswählt, bevor alle Ressourcen geladen wurden, kann beispielsweise durch Anzeigen einer Statusleiste angegeben werden, dass Szenenressourcen weiter geladen werden.</span><span class="sxs-lookup"><span data-stu-id="97454-213">If the user selects an option from the menu before all resources are loaded, you can indicate that scene resources are continuing to load by displaying a progress bar, for example.</span></span>

 

<span data-ttu-id="97454-214">Selbst wenn das Spiel relativ wenige Spielressourcen enthält, empfiehlt es sich aus zwei Gründen, diese asynchron zu laden.</span><span class="sxs-lookup"><span data-stu-id="97454-214">Even if your game contains relatively few game assets, it is good practice to load them asynchronously for two reasons.</span></span> <span data-ttu-id="97454-215">Zum einen ist es schwierig, sicherzustellen, dass alle Ressourcen auf allen Geräten und in allen Konfigurationen schnell geladen werden.</span><span class="sxs-lookup"><span data-stu-id="97454-215">One reason is that it is difficult to guarantee that all of your resources will load quickly on all devices and all configurations.</span></span> <span data-ttu-id="97454-216">Zum anderen ist der Code bei frühzeitiger Integration des asynchronen Ladens zum Skalieren bereit, wenn Sie Funktionalitäten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="97454-216">Also, by incorporating asynchronous loading early, your code is ready to scale as you add functionality.</span></span>

<span data-ttu-id="97454-217">Das asynchrone Laden von Ressourcen beginnt mit der **App::Load**-Methode.</span><span class="sxs-lookup"><span data-stu-id="97454-217">Asynchronous asset loading begins with the **App::Load** method.</span></span> <span data-ttu-id="97454-218">Diese Methode verwendet die [Aufgaben](https://docs.microsoft.com/cpp/parallel/concrt/reference/task-class)-Klasse, um Spielressourcen im Hintergrund zu laden.</span><span class="sxs-lookup"><span data-stu-id="97454-218">This method uses the [task](https://docs.microsoft.com/cpp/parallel/concrt/reference/task-class) class to load game assets in the background.</span></span>

```cpp
    task<void>([=]()
    {
        m_main->LoadDeferredResources(true, false);
    });
```

<span data-ttu-id="97454-219">Die **MarbleMazeMain**-Klasse definiert das *m\_deferredResourcesReady*-Kennzeichen, um anzugeben, dass das asynchrone Laden abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="97454-219">The **MarbleMazeMain** class defines the *m\_deferredResourcesReady* flag to indicate that asynchronous loading is complete.</span></span> <span data-ttu-id="97454-220">Die **MarbleMazeMain::LoadDeferredResources**-Methode lädt die Spielressourcen und legt anschließend dieses Kennzeichen fest.</span><span class="sxs-lookup"><span data-stu-id="97454-220">The **MarbleMazeMain::LoadDeferredResources** method loads the game resources and then sets this flag.</span></span> <span data-ttu-id="97454-221">Während der Aktualisierung(**MarbleMazeMain::Update**) und des Renderns (**MarbleMazeMain::Render**) der App wird dieses Kennzeichen überprüft.</span><span class="sxs-lookup"><span data-stu-id="97454-221">The update (**MarbleMazeMain::Update**) and render (**MarbleMazeMain::Render**) phases of the app check this flag.</span></span> <span data-ttu-id="97454-222">Ist dieses Flag festgelegt, wird das Spiel normal fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="97454-222">When this flag is set, the game continues as normal.</span></span> <span data-ttu-id="97454-223">Wurde das Flag noch nicht festgelegt, zeigt das Spiel den Ladebildschirm an.</span><span class="sxs-lookup"><span data-stu-id="97454-223">If the flag is not yet set, the game shows the loading screen.</span></span>

<span data-ttu-id="97454-224">Weitere Informationen zur asynchronen Programmierung für UWP-Apps finden Sie unter [Asynchrone Programmierung in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span><span class="sxs-lookup"><span data-stu-id="97454-224">For more information about asynchronous programming for UWP apps, see [Asynchronous programming in C++](https://docs.microsoft.com/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).</span></span>

> [!TIP]
> <span data-ttu-id="97454-225">Sollten Sie z.B. einen Spielcode schreiben, der Teil einer Windows-Runtime-C++-Bibliothek (d.h. eine DLL) ist, können Sie im Abschnitt [Erstellen asynchroner Vorgänge in C++ für UWP-Apps](https://docs.microsoft.com/cpp/parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps) lesen, wie asynchrone Vorgänge erstellt werden, die von Apps und anderen Bibliotheken genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="97454-225">If you’re writing game code that is part of a Windows Runtime C++ Library (in other words, a DLL), consider whether to read [Creating Asynchronous Operations in C++ for UWP apps](https://docs.microsoft.com/cpp/parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps) to learn how to create asynchronous operations that can be consumed by apps and other libraries.</span></span>

 

## <a name="the-game-loop"></a><span data-ttu-id="97454-226">Die Spielschleife</span><span class="sxs-lookup"><span data-stu-id="97454-226">The game loop</span></span>


<span data-ttu-id="97454-227">Die **App::Run**-Methode führt die Hauptspielschleife (**MarbleMazeMain::Update**) aus.</span><span class="sxs-lookup"><span data-stu-id="97454-227">The **App::Run** method runs the main game loop (**MarbleMazeMain::Update**).</span></span> <span data-ttu-id="97454-228">Diese Methode wird für jeden Frame aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="97454-228">This method is called every frame.</span></span>

<span data-ttu-id="97454-229">Um den Ansichts- und Fenstercode vom spielspezifischen Code zu trennen, haben wir die **App::Run**-Methode zum Weiterleiten von Aktualisierungs- und Renderaufrufen an das **MarbleMazeMain**-Objekt implementiert.</span><span class="sxs-lookup"><span data-stu-id="97454-229">To help separate view and window code from game-specific code, we implemented the **App::Run** method to forward update and render calls to the **MarbleMazeMain** object.</span></span>

<span data-ttu-id="97454-230">Im folgenden Beispiel ist die **App::Run**-Methode dargestellt, die die Hauptspielschleife enthält.</span><span class="sxs-lookup"><span data-stu-id="97454-230">The following example shows the **App::Run** method, which includes the main game loop.</span></span> <span data-ttu-id="97454-231">Die Spielschleife aktualisiert die Gesamtdauer- und Bilddauervariablen und aktualisiert und rendert anschließend die Szene.</span><span class="sxs-lookup"><span data-stu-id="97454-231">The game loop updates the total time and frame time variables, and then updates and renders the scene.</span></span> <span data-ttu-id="97454-232">Dadurch wird auch sichergestellt, dass Inhalt nur gerendert wird, wenn das Fenster sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="97454-232">This also makes sure that content is only rendered when the window is visible.</span></span>

```cpp
void App::Run()
{
    while (!m_windowClosed)
    {
        if (m_windowVisible)
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->
                ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            m_main->Update();

            if (m_main->Render())
            {
                m_deviceResources->Present();
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->
                ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }

    // The app is exiting so do the same thing as if the app were being suspended.
    m_main->OnSuspending();

#ifdef _DEBUG
    // Dump debug info when exiting.
    DumpD3DDebug();
#endif //_DEGBUG
}
```

## <a name="the-state-machine"></a><span data-ttu-id="97454-233">Der Zustandsautomat</span><span class="sxs-lookup"><span data-stu-id="97454-233">The state machine</span></span>


<span data-ttu-id="97454-234">Spiele enthalten in der Regel einen *Zustandsautomaten* (auch als *finiter Zustandsautomat* oder FSM bezeichnet), um den Fluss und die Reihenfolge der Spiellogik zu steuern.</span><span class="sxs-lookup"><span data-stu-id="97454-234">Games typically contain a *state machine* (also known as a *finite state machine*, or FSM) to control the flow and order of the game logic.</span></span> <span data-ttu-id="97454-235">Ein Zustandsautomat enthält eine bestimmte Anzahl von Zuständen und die Fähigkeit, zwischen diesen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="97454-235">A state machine contains a given number of states and the ability to transition among them.</span></span> <span data-ttu-id="97454-236">Ein Zustandsautomat wird normalerweise von einem *Ausgangszustand* aus gestartet, wechselt zu einem oder mehreren *Zwischenzuständen* und wird möglicherweise in einem *abschließenden Zustand* beendet.</span><span class="sxs-lookup"><span data-stu-id="97454-236">A state machine typically starts from an *initial* state, transitions to one or more *intermediate* states, and possibly ends at a *terminal* state.</span></span>

<span data-ttu-id="97454-237">Eine Spielschleife verwendet häufig einen Zustandsautomaten, damit sie die Logik ausführen kann, die für den aktuellen Spielzustand spezifisch ist.</span><span class="sxs-lookup"><span data-stu-id="97454-237">A game loop often uses a state machine so that it can perform the logic that is specific to the current game state.</span></span> <span data-ttu-id="97454-238">Marble Maze definiert die **GameState**-Enumeration, die jeden möglichen Zustand des Spiels definiert.</span><span class="sxs-lookup"><span data-stu-id="97454-238">Marble Maze defines the **GameState** enumeration, which defines each possible state of the game.</span></span>

```cpp
enum class GameState
{
    Initial,
    MainMenu,
    HighScoreDisplay,
    PreGameCountdown,
    InGameActive,
    InGamePaused,
    PostGameResults,
};
```

<span data-ttu-id="97454-239">Der **MainMenu**-Zustand definiert beispielsweise, dass das Hauptmenü angezeigt wird und das Spiel nicht aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="97454-239">The **MainMenu** state, for example, defines that the main menu appears, and that the game is not active.</span></span> <span data-ttu-id="97454-240">Der **InGameActive**-Zustand definiert dagegen, dass das Spiel aktiv ist und das Menü nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="97454-240">Conversely, the **InGameActive** state defines that the game is active, and that the menu does not appear.</span></span> <span data-ttu-id="97454-241">Die **MarbleMazeMain**-Klasse definiert die **m\_gameState**-Membervariable, um den aktiven Spielzustand beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="97454-241">The **MarbleMazeMain** class defines the **m\_gameState** member variable to hold the active game state.</span></span>

<span data-ttu-id="97454-242">Die Methoden **MarbleMazeMain::Update** und **MarbleMazeMain::Render** verwenden die switch-Anweisung, um die Logik für den aktuellen Zustand auszuführen.</span><span class="sxs-lookup"><span data-stu-id="97454-242">The **MarbleMazeMain::Update** and **MarbleMazeMain::Render** methods use switch statements to perform logic for the current state.</span></span> <span data-ttu-id="97454-243">Das folgende Beispiel zeigt, wie diese switch-Anweisung für die **MarbleMazeMain::Update**-Methode aussehen könnte (zur besseren Veranschaulichung der Struktur wurden Einzelheiten ausgespart).</span><span class="sxs-lookup"><span data-stu-id="97454-243">The following example shows what a switch statement might look like for the **MarbleMazeMain::Update** method (details are removed to illustrate the structure).</span></span>

```cpp
switch (m_gameState)
{
case GameState::MainMenu:
    // Do something with the main menu. 
    break;

case GameState::HighScoreDisplay:
    // Do something with the high-score table. 
    break;

case GameState::PostGameResults:
    // Do something with the game results. 
    break;

case GameState::InGamePaused:
    // Handle the paused state. 
    break;
}
```

<span data-ttu-id="97454-244">Hängt die Spiellogik oder das Rendering von einem bestimmten Spielzustand ab, ist dies in dieser Dokumentation hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="97454-244">When game logic or rendering depends on a specific game state, we emphasize it in this documentation.</span></span>

## <a name="handling-app-and-window-events"></a><span data-ttu-id="97454-245">Behandlung von App- und Fensterereignissen</span><span class="sxs-lookup"><span data-stu-id="97454-245">Handling app and window events</span></span>


<span data-ttu-id="97454-246">Die Windows-Runtime stellt ein objektorientiertes System zur Ereignisbehandlung bereit, damit Sie Windows-Meldungen leichter verwalten können.</span><span class="sxs-lookup"><span data-stu-id="97454-246">The Windows Runtime provides an object-oriented event-handling system so that you can more easily manage Windows messages.</span></span> <span data-ttu-id="97454-247">Sie müssen einen Ereignishandler oder eine Ereignisbehandlungsmethode bereitstellen, die auf das Ereignis reagiert, um ein Ereignis in einer Anwendung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="97454-247">To consume an event in an application, you must provide an event handler, or event-handling method, that responds to the event.</span></span> <span data-ttu-id="97454-248">Sie müssen den Ereignishandler außerdem bei der Ereignisquelle registrieren.</span><span class="sxs-lookup"><span data-stu-id="97454-248">You must also register the event handler with the event source.</span></span> <span data-ttu-id="97454-249">Dieser Prozess wird oft als Ereignisverknüpfung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="97454-249">This process is often referred to as event wiring.</span></span>

### <a name="supporting-suspend-resume-and-restart"></a><span data-ttu-id="97454-250">Unterstützen des Anhaltens, Fortsetzens und Neustartens</span><span class="sxs-lookup"><span data-stu-id="97454-250">Supporting suspend, resume, and restart</span></span>

<span data-ttu-id="97454-251">Marble Maze wird angehalten, wenn der Benutzer aus dem Spiel herauswechselt oder Windows in den Energiesparmodus versetzt wird.</span><span class="sxs-lookup"><span data-stu-id="97454-251">Marble Maze is suspended when the user switches away from it or when Windows enters a low power state.</span></span> <span data-ttu-id="97454-252">Das Spiel wird fortgesetzt, wenn der Benutzer es in den Vordergrund bringt oder der Stromsparmodus für Windows beendet wird.</span><span class="sxs-lookup"><span data-stu-id="97454-252">The game is resumed when the user moves it to the foreground or when Windows comes out of a low power state.</span></span> <span data-ttu-id="97454-253">Im Allgemeinen werden Apps nicht geschlossen.</span><span class="sxs-lookup"><span data-stu-id="97454-253">Generally, you don't close apps.</span></span> <span data-ttu-id="97454-254">Die Apps kann von Windows beendet werden, wenn sich diese im angehaltenen Zustand befindet und Windows die von der App verwendeten Ressourcen (z.B. den Arbeitsspeicher) benötigt.</span><span class="sxs-lookup"><span data-stu-id="97454-254">Windows can terminate the app when it's in the suspended state and Windows requires the resources, such as memory, that the app is using.</span></span> <span data-ttu-id="97454-255">Eine App wird von Windows benachrichtigt, wenn diese gerade angehalten oder fortgesetzt wird, sie wird jedoch nicht benachrichtigt, wenn sie gerade beendet wird.</span><span class="sxs-lookup"><span data-stu-id="97454-255">Windows notifies an app when it is about to be suspended or resumed, but it doesn't notify the app when it's about to be terminated.</span></span> <span data-ttu-id="97454-256">Daher muss die App – ab dem Zeitpunkt, an dem sie von Windows benachrichtigt wird, dass sie gerade angehalten wird – alle Daten speichern können, die erforderlich wären, um den aktuellen Benutzerzustand wiederherzustellen, wenn die App neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="97454-256">Therefore, your app must be able to save—at the point when Windows notifies your app that it is about to be suspended—any data that would be required to restore the current user state when the app is restarted.</span></span> <span data-ttu-id="97454-257">Verfügt die App über einen signifikanten Benutzerzustand, der einen hohen Speicheraufwand erfordert, kann zudem ein regelmäßiges Speichern des Zustands erforderlich sein, noch bevor die App die Anhaltebenachrichtigung empfängt.</span><span class="sxs-lookup"><span data-stu-id="97454-257">If your app has significant user state that is expensive to save, you may also need to save state regularly, even before your app receives the suspend notification.</span></span> <span data-ttu-id="97454-258">Marble Maze reagiert aus zwei Gründen auf Anhalte- und Fortsetzungsbenachrichtigungen:</span><span class="sxs-lookup"><span data-stu-id="97454-258">Marble Maze responds to suspend and resume notifications for two reasons:</span></span>

1.  <span data-ttu-id="97454-259">Wird die App angehalten, speichert das Spiel den aktuellen Spielzustand und hält die Audiowiedergabe an.</span><span class="sxs-lookup"><span data-stu-id="97454-259">When the app is suspended, the game saves the current game state and pauses audio playback.</span></span> <span data-ttu-id="97454-260">Wird die App fortgesetzt, setzt das Spiel die Audiowiedergabe fort.</span><span class="sxs-lookup"><span data-stu-id="97454-260">When the app is resumed, the game resumes audio playback.</span></span>
2.  <span data-ttu-id="97454-261">Wird die App geschlossen und später neu gestartet, wird das Spiel ab dem vorherigen Zustand fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="97454-261">When the app is closed and later restarted, the game resumes from its previous state.</span></span>

<span data-ttu-id="97454-262">Marble Maze führt zum Anhalten und Fortsetzen folgende Aufgaben aus:</span><span class="sxs-lookup"><span data-stu-id="97454-262">Marble Maze performs the following tasks to support suspend and resume:</span></span>

-   <span data-ttu-id="97454-263">An Schlüsselpunkten des Spiels, beispielsweise dann, wenn der Benutzer einen Kontrollpunkt erreicht, speichert es den Zustand im beständigen Speicher.</span><span class="sxs-lookup"><span data-stu-id="97454-263">It saves its state to persistent storage at key points in the game, such as when the user reaches a checkpoint.</span></span>
-   <span data-ttu-id="97454-264">Es reagiert auf Anhaltebenachrichtigungen, indem es seinen Zustand dauerhaft speichert.</span><span class="sxs-lookup"><span data-stu-id="97454-264">It responds to suspend notifications by saving its state to persistent storage.</span></span>
-   <span data-ttu-id="97454-265">Es reagiert auf Fortsetzungsbenachrichtigungen, indem es seinen Zustand aus dem beständigen Speicher lädt.</span><span class="sxs-lookup"><span data-stu-id="97454-265">It responds to resume notifications by loading its state from persistent storage.</span></span> <span data-ttu-id="97454-266">Es lädt den vorherigen Zustand auch während des Starts.</span><span class="sxs-lookup"><span data-stu-id="97454-266">It also loads the previous state during startup.</span></span>

<span data-ttu-id="97454-267">Marble Maze definiert die **PersistentState**-Klasse, um das Anhalten und Fortsetzen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="97454-267">To support suspend and resume, Marble Maze defines the **PersistentState** class.</span></span> <span data-ttu-id="97454-268">(Siehe **PersistentState.h** und **PersistentState.cpp**).</span><span class="sxs-lookup"><span data-stu-id="97454-268">(See **PersistentState.h** and **PersistentState.cpp**).</span></span> <span data-ttu-id="97454-269">Diese Klasse verwendet die [Windows::Foundation::Collections::IPropertySet](https://docs.microsoft.com/uwp/api/Windows.Foundation.Collections.IPropertySet)-Schnittstelle, um Eigenschaften zu lesen und zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="97454-269">This class uses the [Windows::Foundation::Collections::IPropertySet](https://docs.microsoft.com/uwp/api/Windows.Foundation.Collections.IPropertySet) interface to read and write properties.</span></span> <span data-ttu-id="97454-270">Die **PersistentState**-Klasse stellt Methoden bereit, die primitive Datentypen (z. B. **Bool**, **Int**, **Float**, [XMFLOAT3](https://msdn.microsoft.com/library/windows/desktop/ee419475) und [Platform::String](https://docs.microsoft.com/cpp/cppcx/platform-string-class)) aus einem Sicherungsspeicher lesen und in einen Sicherungsspeicher schreiben.</span><span class="sxs-lookup"><span data-stu-id="97454-270">The **PersistentState** class provides methods that read and write primitive data types (such as **bool**, **int**, **float**, [XMFLOAT3](https://msdn.microsoft.com/library/windows/desktop/ee419475), and [Platform::String](https://docs.microsoft.com/cpp/cppcx/platform-string-class)), from and to a backing store.</span></span>

```cpp
ref class PersistentState
{
internal:
    void Initialize(
        _In_ Windows::Foundation::Collections::IPropertySet^ settingsValues,
        _In_ Platform::String^ key
        );

    void SaveBool(Platform::String^ key, bool value);
    void SaveInt32(Platform::String^ key, int value);
    void SaveSingle(Platform::String^ key, float value);
    void SaveXMFLOAT3(Platform::String^ key, DirectX::XMFLOAT3 value);
    void SaveString(Platform::String^ key, Platform::String^ string);

    bool LoadBool(Platform::String^ key, bool defaultValue);
    int  LoadInt32(Platform::String^ key, int defaultValue);
    float LoadSingle(Platform::String^ key, float defaultValue);

    DirectX::XMFLOAT3 LoadXMFLOAT3(
        Platform::String^ key, 
        DirectX::XMFLOAT3 defaultValue);

    Platform::String^ LoadString(
        Platform::String^ key, 
        Platform::String^ defaultValue);

private:
    Platform::String^ m_keyName;
    Windows::Foundation::Collections::IPropertySet^ m_settingsValues;
};
```

<span data-ttu-id="97454-271">Die **MarbleMazeMain**-Klasse enthält ein **PersistentState**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="97454-271">The **MarbleMazeMain** class holds a **PersistentState** object.</span></span> <span data-ttu-id="97454-272">Der **MarbleMazeMain**-Konstruktor initialisiert dieses Objekt und stellt den lokalen Anwendungsdatenspeicher als Sicherungsdatenspeicher bereit.</span><span class="sxs-lookup"><span data-stu-id="97454-272">The **MarbleMazeMain** constructor initializes this object and provides the local application data store as the backing data store.</span></span>

```cpp
m_persistentState = ref new PersistentState();

m_persistentState->Initialize(
    Windows::Storage::ApplicationData::Current->LocalSettings->Values,
    "MarbleMaze");
```

<span data-ttu-id="97454-273">Marble Maze speichert den Zustand, wenn die Murmel einen Prüfpunkt oder das Ziel passiert (in der **MarbleMazeMain::Update**-Methode) und das Fenster den Fokus verliert (in der **MarbleMazeMain::OnFocusChange**-Methode).</span><span class="sxs-lookup"><span data-stu-id="97454-273">Marble Maze saves its state when the marble passes over a checkpoint or the goal (in the **MarbleMazeMain::Update** method), and when the window loses focus (in the **MarbleMazeMain::OnFocusChange** method).</span></span> <span data-ttu-id="97454-274">Enthält das Spiel eine große Menge an Zustandsdaten, empfiehlt es sich, den Zustand auf ähnliche Weise gelegentlich im beständigen Speicher zu speichern, da Sie nur einige Sekunden Zeit haben, um auf die Anhaltebenachrichtigung zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="97454-274">If your game holds a large amount of state data, we recommend that you occasionally save state to persistent storage in a similar manner because you only have a few seconds to respond to the suspend notification.</span></span> <span data-ttu-id="97454-275">Empfängt die App eine Anhaltebenachrichtigung, muss sie daher nur die Zustandsdaten speichern, die geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="97454-275">Therefore, when your app receives a suspend notification, it only has to save the state data that has changed.</span></span>

<span data-ttu-id="97454-276">Zum Reagieren auf Anhalte- und Fortsetzungsbenachrichtigungen definiert die **MarbleMazeMain**-Klasse die **SaveState**- und **LoadState**-Methoden, die beim Anhalten und Fortsetzen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="97454-276">To respond to suspend and resume notifications, the **MarbleMazeMain** class defines the **SaveState** and **LoadState** methods that are called on suspend and resume.</span></span> <span data-ttu-id="97454-277">Die **MarbleMazeMain::OnSuspending**-Methode behandelt das Anhalteereignis und die **MarbleMazeMain::OnResuming**-Methode das Fortsetzungsereignis.</span><span class="sxs-lookup"><span data-stu-id="97454-277">The **MarbleMazeMain::OnSuspending** method handles the suspend event and the **MarbleMazeMain::OnResuming** method handles the resume event.</span></span>

<span data-ttu-id="97454-278">Die **MarbleMazeMain::OnSuspending**-Methode speichert den Spielzustand und hält das Audio an.</span><span class="sxs-lookup"><span data-stu-id="97454-278">The **MarbleMazeMain::OnSuspending** method saves game state and suspends audio.</span></span>

```cpp
void MarbleMazeMain::OnSuspending()
{
    SaveState();
    m_audio.SuspendAudio();
}
```

<span data-ttu-id="97454-279">Die **MarbleMazeMain::SaveState**-Methode speichert Spielzustandswerte wie die aktuelle Position und Geschwindigkeit der Murmel, den letzten Prüfpunkt und die Bestenliste.</span><span class="sxs-lookup"><span data-stu-id="97454-279">The **MarbleMazeMain::SaveState** method saves game state values such as the current position and velocity of the marble, the most recent checkpoint, and the high-score table.</span></span>

```cpp
void MarbleMazeMain::SaveState()
{
    m_persistentState->SaveXMFLOAT3(":Position", m_physics.GetPosition());
    m_persistentState->SaveXMFLOAT3(":Velocity", m_physics.GetVelocity());

    m_persistentState->SaveSingle(
        ":ElapsedTime", 
        m_inGameStopwatchTimer.GetElapsedTime());

    m_persistentState->SaveInt32(":GameState", static_cast<int>(m_gameState));
    m_persistentState->SaveInt32(":Checkpoint", static_cast<int>(m_currentCheckpoint));

    int i = 0;
    HighScoreEntries entries = m_highScoreTable.GetEntries();
    const int bufferLength = 16;
    char16 str[bufferLength];

    m_persistentState->SaveInt32(":ScoreCount", static_cast<int>(entries.size()));

    for (auto iter = entries.begin(); iter != entries.end(); ++iter)
    {
        int len = swprintf_s(str, bufferLength, L"%d", i++);
        Platform::String^ string = ref new Platform::String(str, len);

        m_persistentState->SaveSingle(
            Platform::String::Concat(":ScoreTime", string), 
            iter->elapsedTime);

        m_persistentState->SaveString(
            Platform::String::Concat(":ScoreTag", string), 
            iter->tag);
    }
}
```

<span data-ttu-id="97454-280">Beim Fortsetzen des Spiels muss nur das Audio fortgesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="97454-280">When the game resumes, it only has to resume audio.</span></span> <span data-ttu-id="97454-281">Es ist kein Laden des Zustands aus dem beständigen Speicher erforderlich, da der Zustand bereits im Arbeitsspeicher geladen ist.</span><span class="sxs-lookup"><span data-stu-id="97454-281">It doesn't have to load state from persistent storage because the state is already loaded in memory.</span></span>

<span data-ttu-id="97454-282">Wie das Spiel ein Audio anhält und fortsetzt, wird im Dokument [Hinzufügen von Audio zum Beispielspiel Marble Maze](adding-audio-to-the-marble-maze-sample.md) erläutert.</span><span class="sxs-lookup"><span data-stu-id="97454-282">How the game suspends and resumes audio is explained in the document [Adding audio to the Marble Maze sample](adding-audio-to-the-marble-maze-sample.md).</span></span>

<span data-ttu-id="97454-283">Zur Unterstützung des Neustarts ruft der beim Start aufgerufene **MarbleMazeMain::Initialize**-Konstruktor die **MarbleMazeMain::LoadState**-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="97454-283">To support restart, the **MarbleMazeMain** constructor, which is called during startup, calls the **MarbleMazeMain::LoadState** method.</span></span> <span data-ttu-id="97454-284">Die **MarbleMazeMain::LoadState**-Methode liest den Zustand in den Spielobjekten und übernimmt diesen.</span><span class="sxs-lookup"><span data-stu-id="97454-284">The **MarbleMazeMain::LoadState** method reads and applies the state to the game objects.</span></span> <span data-ttu-id="97454-285">Diese Methode legt außerdem den aktuellen Spielzustand als angehalten fest, wenn das Spiel angehalten wurde oder aktiv war, als es angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="97454-285">This method also sets the current game state to paused if the game was paused or active when it was suspended.</span></span> <span data-ttu-id="97454-286">Das Spiel wird angehalten, sodass der Benutzer nicht von unerwarteten Aktivitäten überrascht wird.</span><span class="sxs-lookup"><span data-stu-id="97454-286">We pause the game so that the user is not surprised by unexpected activity.</span></span> <span data-ttu-id="97454-287">Sie wechselt auch zum Hauptmenü, wenn sich das Spiel nicht in einem Wiedergabezustand befand, als es angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="97454-287">It also moves to the main menu if the game was not in a gameplay state when it was suspended.</span></span>

```cpp
void MarbleMazeMain::LoadState()
{
    XMFLOAT3 position = m_persistentState->LoadXMFLOAT3(
        ":Position", 
        m_physics.GetPosition());

    XMFLOAT3 velocity = m_persistentState->LoadXMFLOAT3(
        ":Velocity", 
        m_physics.GetVelocity());

    float elapsedTime = m_persistentState->LoadSingle(":ElapsedTime", 0.0f);

    int gameState = m_persistentState->LoadInt32(
        ":GameState", 
        static_cast<int>(m_gameState));

    int currentCheckpoint = m_persistentState->LoadInt32(
        ":Checkpoint", 
        static_cast<int>(m_currentCheckpoint));

    switch (static_cast<GameState>(gameState))
    {
    case GameState::Initial:
        break;

    case GameState::MainMenu:
    case GameState::HighScoreDisplay:
    case GameState::PreGameCountdown:
    case GameState::PostGameResults:
        SetGameState(GameState::MainMenu);
        break;

    case GameState::InGameActive:
    case GameState::InGamePaused:
        m_inGameStopwatchTimer.SetVisible(true);
        m_inGameStopwatchTimer.SetElapsedTime(elapsedTime);
        m_physics.SetPosition(position);
        m_physics.SetVelocity(velocity);
        m_currentCheckpoint = currentCheckpoint;
        SetGameState(GameState::InGamePaused);
        break;
    }

    int count = m_persistentState->LoadInt32(":ScoreCount", 0);

    const int bufferLength = 16;
    char16 str[bufferLength];

    for (int i = 0; i < count; i++)
    {
        HighScoreEntry entry;
        int len = swprintf_s(str, bufferLength, L"%d", i);
        Platform::String^ string = ref new Platform::String(str, len);

        entry.elapsedTime = m_persistentState->LoadSingle(
            Platform::String::Concat(":ScoreTime", string), 
            0.0f);

        entry.tag = m_persistentState->LoadString(
            Platform::String::Concat(":ScoreTag", string), 
            L"");

        m_highScoreTable.AddScoreToTable(entry);
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="97454-288">Marble Maze unterscheidet nicht zwischen Kaltstart– d.h. einem erstmaligen Start ohne vorheriges Anhalteereignis– und dem Fortsetzen vom angehaltenen Zustand aus.</span><span class="sxs-lookup"><span data-stu-id="97454-288">Marble Maze doesn't distinguish between cold starting—that is, starting for the first time without a prior suspend event—and resuming from a suspended state.</span></span> <span data-ttu-id="97454-289">Dies ist der empfohlene Entwurf für alle UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="97454-289">This is recommended design for all UWP apps.</span></span>

<span data-ttu-id="97454-290">Weitere Informationen zu Anwendungsdaten finden Sie unter [Speichern und Abrufen von Einstellungen und anderen App-Daten](https://msdn.microsoft.com/library/windows/apps/mt299098).</span><span class="sxs-lookup"><span data-stu-id="97454-290">For more info about application data, see [Store and retrieve settings and other app data](https://msdn.microsoft.com/library/windows/apps/mt299098).</span></span>

##  <a name="next-steps"></a><span data-ttu-id="97454-291">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="97454-291">Next steps</span></span>


<span data-ttu-id="97454-292">Informationen zu einigen der wichtigsten Vorgehensweisen, die Sie beim Verwenden von visuellen Ressourcen berücksichtigen sollten, finden Sie unter [Hinzufügen von visuellem Inhalt zum Beispielspiel Marble Maze](adding-visual-content-to-the-marble-maze-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="97454-292">Read [Adding visual content to the Marble Maze sample](adding-visual-content-to-the-marble-maze-sample.md) for information about some of the key practices to keep in mind when you work with visual resources.</span></span>

## <a name="related-topics"></a><span data-ttu-id="97454-293">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="97454-293">Related topics</span></span>

* [<span data-ttu-id="97454-294">Hinzufügen von visuellen Inhalten zum Marble Maze-Beispiel</span><span class="sxs-lookup"><span data-stu-id="97454-294">Adding visual content to the Marble Maze sample</span></span>](adding-visual-content-to-the-marble-maze-sample.md)
* [<span data-ttu-id="97454-295">Grundlagen am Beispiel von Marble Maze</span><span class="sxs-lookup"><span data-stu-id="97454-295">Marble Maze sample fundamentals</span></span>](marble-maze-sample-fundamentals.md)
* [<span data-ttu-id="97454-296">Entwickeln von Marble Maze, einem UWP-Spiel in C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="97454-296">Developing Marble Maze, a UWP game in C++ and DirectX</span></span>](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)

 

 




