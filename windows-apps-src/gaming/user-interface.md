---
author: mtoepke
title: DirectX-Spielprojektvorlagen
description: Hier erhalten Sie Informationen zu den Vorlagen zum Erstellen eines DirectX-Spiels für die Universelle Windows-Plattform (UWP).
ms.assetid: 41b6cd76-5c9a-e2b7-ef6f-bfbf6ef7331d
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Directx, Vorlagen
ms.localizationpriority: medium
ms.openlocfilehash: d27e4bb0d643b859958f887133a128572ca31225
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5981622"
---
# <a name="directx-game-project-templates"></a><span data-ttu-id="b55a6-104">DirectX-Spielprojektvorlagen</span><span class="sxs-lookup"><span data-stu-id="b55a6-104">DirectX game project templates</span></span>



<span data-ttu-id="b55a6-105">Mit Vorlagen für DirectX und die universelle Windows-Plattform (UWP) können Sie schnell ein Projekt als Ausgangspunkt für Ihr Spiel erstellen.</span><span class="sxs-lookup"><span data-stu-id="b55a6-105">The DirectX and Universal Windows Platform (UWP) templates allow you to quickly create a project as a starting point for your game.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b55a6-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b55a6-106">Prerequisites</span></span>


<span data-ttu-id="b55a6-107">Gehen Sie wie folgt vor, um das Projekt zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b55a6-107">To create the project you need to:</span></span>

-   <span data-ttu-id="b55a6-108">[Microsoft Visual Studio2015 herunterladen](https://www.visualstudio.com/vs-2015-product-editions).</span><span class="sxs-lookup"><span data-stu-id="b55a6-108">[Download Microsoft Visual Studio2015](https://www.visualstudio.com/vs-2015-product-editions).</span></span> <span data-ttu-id="b55a6-109">Visual Studio2015 enthält Tools für die Grafikprogrammierung, beispielsweise Debugtools.</span><span class="sxs-lookup"><span data-stu-id="b55a6-109">Visual Studio2015 has tools for graphics programming, such as debugging tools.</span></span> <span data-ttu-id="b55a6-110">Eine Übersicht über DirectX-Grafik- und -Spielefeatures/-tools finden Sie unter [VisualStudio-Tools für die Entwicklung von DirectX-Spielen](set-up-visual-studio-for-game-development.md).</span><span class="sxs-lookup"><span data-stu-id="b55a6-110">For an overview of DirectX graphics and gaming features and tools, see [Visual Studio tools for DirectX game development](set-up-visual-studio-for-game-development.md).</span></span>

## <a name="choosing-a-template"></a><span data-ttu-id="b55a6-111">Auswählen einer Vorlage</span><span class="sxs-lookup"><span data-stu-id="b55a6-111">Choosing a template</span></span>


<span data-ttu-id="b55a6-112">Visual Studio2015 umfasst drei Vorlagen für DirectX und UWP:</span><span class="sxs-lookup"><span data-stu-id="b55a6-112">Visual Studio2015 includes three DirectX and UWP templates:</span></span>

-   <span data-ttu-id="b55a6-113">DirectX 11-App (Universelle Windows-App): Mit der Vorlage "DirectX 11-App (Universelle Windows-App)" wird ein UWP-Projekt erstellt, das direkt in einem App-Fenster mit DirectX11 gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="b55a6-113">DirectX 11 App (Universal Windows) - The DirectX 11 App (Universal Windows) template creates a UWP project, which renders directly to an app window using DirectX 11.</span></span>
-   <span data-ttu-id="b55a6-114">DirectX 12-App (Universelle Windows-App): Mit der Vorlage "DirectX 12-App (Universelle Windows-App)" wird ein UWP-Projekt erstellt, das direkt in einem App-Fenster mit DirectX12 gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="b55a6-114">DirectX 12 App (Universal Windows) - The DirectX 12 App (Universal Windows) template creates a project UWP, which renders directly to an app window using DirectX 12.</span></span>
-   <span data-ttu-id="b55a6-115">DirectX11- und XAML-App (Universelle Windows-App): Mit der Vorlage „DirectX11- und XAML-App (Universelle Windows-App)“ wird ein UWP-Projekt erstellt, das direkt in einem XAML-Steuerelement mit DirectX11 gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="b55a6-115">DirectX 11 and XAML App (Universal Windows) - The DirectX 11 and XAML App (Universal Windows) template creates a UWP project, which renders inside a XAML control using DirectX 11.</span></span> <span data-ttu-id="b55a6-116">Diese Vorlage verwendet ein [**SwapChainPanel**](https://msdn.microsoft.com/library/windows/apps/dn252834)-Element und ermöglicht so die Verwendung von XAML-UI-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="b55a6-116">This template uses a [**SwapChainPanel**](https://msdn.microsoft.com/library/windows/apps/dn252834), so you can use XAML UI controls.</span></span> <span data-ttu-id="b55a6-117">Dies kann zwar das Hinzufügen von Benutzeroberflächenelementen vereinfachen, die Verwendung der XAML-Vorlage beeinträchtigt aber unter Umständen die Leistung.</span><span class="sxs-lookup"><span data-stu-id="b55a6-117">This can make adding user interface elements easier, but using the XAML template may result in lower performance.</span></span>

<span data-ttu-id="b55a6-118">Die Entscheidung für eine Vorlage hängt von der Leistung und von den gewünschten Technologien ab.</span><span class="sxs-lookup"><span data-stu-id="b55a6-118">Which template you choose depends on the performance and what technologies you want to use.</span></span>

## <a name="template-structure"></a><span data-ttu-id="b55a6-119">Vorlagenstruktur</span><span class="sxs-lookup"><span data-stu-id="b55a6-119">Template structure</span></span>


<span data-ttu-id="b55a6-120">Die DirectX-UWP-Vorlagen enthalten die folgenden Dateien:</span><span class="sxs-lookup"><span data-stu-id="b55a6-120">The DirectX Universal Windows templates contain the following files:</span></span>

-   <span data-ttu-id="b55a6-121">"pch.h" und "pch.cpp": Unterstützung für vorkompilierte Headerdateien.</span><span class="sxs-lookup"><span data-stu-id="b55a6-121">pch.h and pch.cpp - Precompiled header support.</span></span>
-   <span data-ttu-id="b55a6-122">Package.appxmanifest: Die Eigenschaften des Bereitstellungspakets für die App.</span><span class="sxs-lookup"><span data-stu-id="b55a6-122">Package.appxmanifest - The properties of the deployment package for the app.</span></span>
-   <span data-ttu-id="b55a6-123">\*.pfx: Zertifikate für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b55a6-123">\*.pfx - Certificates for the application.</span></span>
-   <span data-ttu-id="b55a6-124">Externe Abhängigkeiten: Links zu externen Dateien, die vom Projekt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b55a6-124">External Dependencies - Links to external files the project use.s</span></span>
-   <span data-ttu-id="b55a6-125">„\*Main.h“ und „\*Main.cpp“: Methoden zum Verwalten von Anwendungsressourcen, zum Upgrade des Anwendungszustands und zum Rendern des Frames.</span><span class="sxs-lookup"><span data-stu-id="b55a6-125">\*Main.h and \*Main.cpp - Methods for managing application assets, updating application state, and rendering the frame.</span></span>
-   <span data-ttu-id="b55a6-126">"App.h" und "App.cpp": Haupteinstiegspunkt für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b55a6-126">App.h and App.cpp - Main entry point for the application.</span></span> <span data-ttu-id="b55a6-127">Verbindet die App mit der Windows-Shell und behandelt App-Lebenszyklusereignisse.</span><span class="sxs-lookup"><span data-stu-id="b55a6-127">Connects the app with the Windows shell and handles application lifecycle events.</span></span> <span data-ttu-id="b55a6-128">Diese Dateien werden nur in den Vorlagen „DirectX11-App (Universelle Windows-App)“ und „DirectX12-App (Universelle Windows-App)“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b55a6-128">These files only appear in the DirectX 11 App (Universal Windows) and DirectX 12 App (Universal Windows) templates.</span></span>
-   <span data-ttu-id="b55a6-129">"App.Xaml", "App.Xaml.cpp" und "App.Xaml.h": Haupteinstiegspunkt für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b55a6-129">App.xaml, App.xaml.cpp, and App.xaml.h - Main entry point for the application.</span></span> <span data-ttu-id="b55a6-130">Verbindet die App mit der Windows-Shell und behandelt App-Lebenszyklusereignisse.</span><span class="sxs-lookup"><span data-stu-id="b55a6-130">Connects the app with the Windows shell and handles application lifecycle events.</span></span> <span data-ttu-id="b55a6-131">Diese Dateien werden nur in der Vorlage "DirectX 11- und XAML-App (Universelle Windows-App)" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b55a6-131">These files only appear in the DirectX 11 and XAML App (Universal Windows) template.</span></span>
-   <span data-ttu-id="b55a6-132">"DirectXPage.xaml", "DirectXPage.xaml.cpp" und "DirectXPage.xaml.h": Eine Seite, die ein DirectX-SwapChainPanel hostet.</span><span class="sxs-lookup"><span data-stu-id="b55a6-132">DirectXPage.xaml, DirectXPage.xaml.cpp, and DirectXPage.xaml.h - A page that hosts a DirectX SwapChainPanel.</span></span> <span data-ttu-id="b55a6-133">Diese Dateien werden nur in der Vorlage "DirectX 11- und XAML-App (Universelle Windows-App)" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b55a6-133">These files only appear in the DirectX 11 and XAML App (Universal Windows) template.</span></span>
-   <span data-ttu-id="b55a6-134">Inhalt</span><span class="sxs-lookup"><span data-stu-id="b55a6-134">Content</span></span>
    -   <span data-ttu-id="b55a6-135">Sample3DSceneRenderer.h und Sample3DSceneRenderer.cpp – Ein Beispielrenderer, der eine grundlegende Renderingpipeline instanziiert.</span><span class="sxs-lookup"><span data-stu-id="b55a6-135">Sample3DSceneRenderer.h and Sample3DSceneRenderer.cpp - A sample renderer that instantiates a basic rendering pipeline.</span></span>
    -   <span data-ttu-id="b55a6-136">SampleFpsTextRenderer.h und SampleFpsTextRenderer.cpp – Rendert den aktuellen FPS-Wert mit Direct2D und DirectWrite rechts unten auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="b55a6-136">SampleFpsTextRenderer.h and SampleFpsTextRenderer.cpp - Renders the current FPS value in the bottom right corner of the screen using Direct2D and DirectWrite.</span></span> <span data-ttu-id="b55a6-137">Diese Dateien werden nur in den Vorlagen „DirectX11-App (Universelle Windows-App)“ und „DirectX11- und XAML-App (Universelle Windows-App)“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b55a6-137">These files only appear in the DirectX 11 App (Universal Windows) and DirectX 11 and XAML App (Universal Windows) templates.</span></span>
    -   <span data-ttu-id="b55a6-138">SamplePixelShader.hlsl – Ein einfacher Beispiel-Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="b55a6-138">SamplePixelShader.hlsl - A simple example pixel shader.</span></span>
    -   <span data-ttu-id="b55a6-139">SampleVertexShader.hlsl – Ein einfacher Beispiel-Vertex-Shader.</span><span class="sxs-lookup"><span data-stu-id="b55a6-139">SampleVertexShader.hlsl - A simple example vertex shader.</span></span>
    -   <span data-ttu-id="b55a6-140">ShaderStructures.h – Zum Senden von Daten an den Beispiel-Vertex-Shader verwendete Strukturen.</span><span class="sxs-lookup"><span data-stu-id="b55a6-140">ShaderStructures.h - Structures used to send date to the example vertex shader.</span></span>
-   <span data-ttu-id="b55a6-141">Allgemein</span><span class="sxs-lookup"><span data-stu-id="b55a6-141">Common</span></span>
    -   <span data-ttu-id="b55a6-142">StepTimer.h – Eine Hilfsklasse für das Animations- und Simulationstiming.</span><span class="sxs-lookup"><span data-stu-id="b55a6-142">StepTimer.h - A helper class for animation and simulation timing.</span></span>
    -   <span data-ttu-id="b55a6-143">DirectXHelper.h – Verschiedene Hilfsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="b55a6-143">DirectXHelper.h - Misc Helper functions.</span></span>
    -   <span data-ttu-id="b55a6-144">DeviceResources.h und Device Resources.cpp – Stellt eine Schnittstelle für eine Anwendung bereit, die Eigentümer von DeviceResources ist, um benachrichtigt zu werden, wenn das Gerät verloren geht oder erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="b55a6-144">DeviceResources.h and Device Resources.cpp - Provides an interface for an application that owns DeviceResources to be notified of the device being lost or created.</span></span>
    -   <span data-ttu-id="b55a6-145">d3dx12.h – Enthält die D3DX12-Hilfsprogrammbibliothek.</span><span class="sxs-lookup"><span data-stu-id="b55a6-145">d3dx12.h - Contains the D3DX12 utility library.</span></span> <span data-ttu-id="b55a6-146">Diese Datei ist nur in der DirectX 12-App (Universelle Windows-App) vorhanden.</span><span class="sxs-lookup"><span data-stu-id="b55a6-146">This file only appears in the DirectX 12 App (Universal Windows).</span></span>
-   <span data-ttu-id="b55a6-147">Ressourcen: Logo- und Splashscreen-Bilder, die von der Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b55a6-147">Assets - Logo and splashscreen images used by the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b55a6-148">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b55a6-148">Next steps</span></span>


<span data-ttu-id="b55a6-149">Erweitern Sie basierend auf diesen Grundkenntnissen Ihr Wissen im Bereich der Spielentwicklung und speziell die Fähigkeiten für die Entwicklung von MicrosoftStore-Spielen.</span><span class="sxs-lookup"><span data-stu-id="b55a6-149">Now that you have a starting point, add to it to build your game development knowledge and Microsoft Store game development skills.</span></span>

<span data-ttu-id="b55a6-150">Wenn Sie ein vorhandenes Spiel portieren, sind die folgenden Themen hilfreich:</span><span class="sxs-lookup"><span data-stu-id="b55a6-150">If you are porting an existing game, see the following topics.</span></span>

-   [<span data-ttu-id="b55a6-151">Portieren von OpenGL ES 2.0 zu Direct3D 11.1</span><span class="sxs-lookup"><span data-stu-id="b55a6-151">Port from OpenGL ES 2.0 to Direct3D 11.1</span></span>](port-from-opengl-es-2-0-to-directx-11-1.md)
-   [<span data-ttu-id="b55a6-152">Portieren von DirectX9 zur universellen Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="b55a6-152">Port from DirectX 9 to Universal Windows Platform</span></span>](porting-your-directx-9-game-to-windows-store.md)

<span data-ttu-id="b55a6-153">Wenn Sie ein neues DirectX-Spiel erstellen, sind die folgenden Themen hilfreich.</span><span class="sxs-lookup"><span data-stu-id="b55a6-153">If you are creating a new DirectX game, see the following topics.</span></span>

-   [<span data-ttu-id="b55a6-154">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="b55a6-154">Create a simple UWP game with DirectX</span></span>](tutorial--create-your-first-uwp-directx-game.md)
-   [<span data-ttu-id="b55a6-155">Entwickeln von Marble Maze, einem Spiel für die universelle Windows-Plattform in C++ und DirectX</span><span class="sxs-lookup"><span data-stu-id="b55a6-155">Developing Marble Maze, a Universal Windows Platform game in C++ and DirectX</span></span>](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)