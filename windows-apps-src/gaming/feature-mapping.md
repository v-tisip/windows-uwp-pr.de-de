---
author: mtoepke
title: Zuordnung von DirectX9-Funktionen zu DirectX11-APIs
description: Erfahren Sie, wie Sie die Features Ihres Direct3D9-Spiels mit Direct3D11 und der Universellen Windows-Plattform (UWP) verwenden können.
ms.assetid: 3aa8a114-4e47-ae0a-9447-88ba324377b8
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX 9, DirectX 11, Portierung
ms.localizationpriority: medium
ms.openlocfilehash: 8dcf1749f1e7db4d514466d6a753d6f8cace5713
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6968846"
---
# <a name="map-directx-9-features-to-directx-11-apis"></a><span data-ttu-id="893c6-104">Zuordnung von DirectX9-Funktionen zu DirectX11-APIs</span><span class="sxs-lookup"><span data-stu-id="893c6-104">Map DirectX 9 features to DirectX 11 APIs</span></span>



**<span data-ttu-id="893c6-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="893c6-105">Summary</span></span>**

-   [<span data-ttu-id="893c6-106">Planen der DirectX-Portierung</span><span class="sxs-lookup"><span data-stu-id="893c6-106">Plan your DirectX port</span></span>](plan-your-directx-port.md)
-   [<span data-ttu-id="893c6-107">Wichtige Änderungen beim Wechsel von Direct3D9 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="893c6-107">Important changes from Direct3D 9 to Direct3D 11</span></span>](understand-direct3d-11-1-concepts.md)
-   <span data-ttu-id="893c6-108">Featurezuordnung</span><span class="sxs-lookup"><span data-stu-id="893c6-108">Feature mapping</span></span>


<span data-ttu-id="893c6-109">Erfahren Sie, wie die Features Ihres Direct3D9-Spiels zu Direct3D11 und zur Universellen Windows-Plattform (UWP) zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-109">Understand how the features your Direct3D 9 game uses will translate to Direct3D 11 and the Universal Windows Platform (UWP).</span></span>

## <a name="mapping-direct3d-9-to-directx-11-apis"></a><span data-ttu-id="893c6-110">Zuordnen von Direct3D9-Features zu DirectX11-APIs</span><span class="sxs-lookup"><span data-stu-id="893c6-110">Mapping Direct3D 9 to DirectX 11 APIs</span></span>


<span data-ttu-id="893c6-111">[Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) ist nach wie vor die Grundlage von DirectX-Grafiken, die API wurde seit DirectX 9 jedoch geändert:</span><span class="sxs-lookup"><span data-stu-id="893c6-111">[Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) is still the foundation of DirectX graphics, but the API has changed since DirectX 9:</span></span>

-   <span data-ttu-id="893c6-112">Zum Einrichten von Grafikadaptern wird die Microsoft DirectX Graphics Infrastructure (DXGI) verwendet.</span><span class="sxs-lookup"><span data-stu-id="893c6-112">Microsoft DirectX Graphics Infrastructure (DXGI) is used to set up graphics adapters.</span></span> <span data-ttu-id="893c6-113">Verwenden Sie [DXGI](https://msdn.microsoft.com/library/windows/desktop/hh404534) zum Auswählen von Pufferformaten, Erstellen von Swapchains, Darstellen von Frames und Erstellen freigegebener Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="893c6-113">Use [DXGI](https://msdn.microsoft.com/library/windows/desktop/hh404534) to select buffer formats, create swap chains, present frames, and create shared resources.</span></span> <span data-ttu-id="893c6-114">Siehe [Übersicht über DXGI](https://msdn.microsoft.com/library/windows/desktop/bb205075).</span><span class="sxs-lookup"><span data-stu-id="893c6-114">See [DXGI Overview](https://msdn.microsoft.com/library/windows/desktop/bb205075).</span></span>
-   <span data-ttu-id="893c6-115">Ein Direct3D-Gerätekontext wird zum Festlegen des Pipelinestatus und Generieren von Renderbefehlen verwendet.</span><span class="sxs-lookup"><span data-stu-id="893c6-115">A Direct3D device context is used to set pipeline state and generate rendering commands.</span></span> <span data-ttu-id="893c6-116">In den meisten unserer Beispiele wird ein unmittelbarer Kontext verwendet, um direkt auf dem Gerät zu rendern. Direct3D11 unterstützt auch das Multithread-Rendering, wobei dann verzögerte Kontexte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-116">Most of our samples use an immediate context to render directly to the device; Direct3D 11 also supports multithreaded rendering, in which case deferred contexts are used.</span></span> <span data-ttu-id="893c6-117">Siehe [Einführung in ein Gerät in Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476880).</span><span class="sxs-lookup"><span data-stu-id="893c6-117">See [Introduction to a Device in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476880).</span></span>
-   <span data-ttu-id="893c6-118">Einige Funktionen sind veraltet und nicht mehr verfügbar. Zu beachten ist insbesondere, dass es die Pipeline mit fester Funktion nicht mehr gibt.</span><span class="sxs-lookup"><span data-stu-id="893c6-118">Some features have been deprecated, most notably the fixed function pipeline.</span></span> <span data-ttu-id="893c6-119">Siehe [Veraltete Funktionen](https://msdn.microsoft.com/library/windows/desktop/cc308047).</span><span class="sxs-lookup"><span data-stu-id="893c6-119">See [Deprecated Features](https://msdn.microsoft.com/library/windows/desktop/cc308047).</span></span>

<span data-ttu-id="893c6-120">Eine vollständige Liste der Direct3D11-Funktionen finden Sie unter [Features von Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476342) und [Features von Direct3D11.1](https://msdn.microsoft.com/library/windows/desktop/hh404562).</span><span class="sxs-lookup"><span data-stu-id="893c6-120">For a full list of Direct3D 11 features, see [Direct3D 11 Features](https://msdn.microsoft.com/library/windows/desktop/ff476342) and [Direct3D 11 Features](https://msdn.microsoft.com/library/windows/desktop/hh404562).</span></span>

## <a name="moving-from-direct2d-9-to-direct2d-11"></a><span data-ttu-id="893c6-121">Umstellung von Direct2D9 auf Direct2D11</span><span class="sxs-lookup"><span data-stu-id="893c6-121">Moving from Direct2D 9 to Direct2D 11</span></span>


<span data-ttu-id="893c6-122">[Direct2D (Windows)](https://msdn.microsoft.com/library/windows/desktop/dd370990) ist weiterhin ein wichtiger Bestandteil von DirectX-Grafiken und Windows.</span><span class="sxs-lookup"><span data-stu-id="893c6-122">[Direct2D (Windows)](https://msdn.microsoft.com/library/windows/desktop/dd370990) is still an important part of DirectX graphics and Windows.</span></span> <span data-ttu-id="893c6-123">Sie können mit Direct2D weiterhin 2D-Spiele und Direct3D-basierte Überlagerungen (HUDs) zeichnen.</span><span class="sxs-lookup"><span data-stu-id="893c6-123">You can still use Direct2D to draw 2D games, and to draw overlays (HUDs) on top of Direct3D.</span></span>

<span data-ttu-id="893c6-124">Direct2D baut auf Direct3D auf. 2D-Spiele können mit beiden APIs implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-124">Direct2D runs on top of Direct3D; 2D games can be implemented using either API.</span></span> <span data-ttu-id="893c6-125">Ein mit Direct3D implementiertes 2D-Spiel kann z.B. die orthografische Projektion verwenden, Z-Werte zum Steuern der Zeichnungsreihenfolge von Grundtypen festlegen und mit Pixelshadern Spezialeffekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="893c6-125">For example, a 2D game implemented using Direct3D can use orthographic projection, set Z-values to control the drawing order of primitives, and use pixel shaders to add special effects.</span></span>

<span data-ttu-id="893c6-126">Da Direct2D auf Direct3D basiert, verwendet es ebenfalls DXGI und Gerätekontexte.</span><span class="sxs-lookup"><span data-stu-id="893c6-126">Since Direct2D is based on Direct3D it also uses DXGI and device contexts.</span></span> <span data-ttu-id="893c6-127">Siehe [Übersicht über die Direct2D-API](https://msdn.microsoft.com/library/windows/desktop/dd317121).</span><span class="sxs-lookup"><span data-stu-id="893c6-127">See [Direct2D API Overview](https://msdn.microsoft.com/library/windows/desktop/dd317121).</span></span>

<span data-ttu-id="893c6-128">Die [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038)-API bietet Unterstützung für formatierten Text mit Direct2D.</span><span class="sxs-lookup"><span data-stu-id="893c6-128">The [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) API adds support for formatted text using Direct2D.</span></span> <span data-ttu-id="893c6-129">Siehe [Einführung in DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd371554).</span><span class="sxs-lookup"><span data-stu-id="893c6-129">See [Introducing DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd371554).</span></span>

## <a name="replace-deprecated-helper-libraries"></a><span data-ttu-id="893c6-130">Ersetzen veralteter Hilfsbibliotheken</span><span class="sxs-lookup"><span data-stu-id="893c6-130">Replace deprecated helper libraries</span></span>


<span data-ttu-id="893c6-131">D3DX und DXUT sind veraltet und können nicht in UWP-Spielen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-131">D3DX and DXUT are deprecated and cannot be used by UWP games.</span></span> <span data-ttu-id="893c6-132">Von diesen Hilfsbibliotheken wurden Ressourcen für Aufgaben wie das Laden von Texturen und Gittern bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="893c6-132">These helper libraries provided resources for tasks such as texture loading and mesh loading.</span></span>

-   <span data-ttu-id="893c6-133">In der exemplarischen Vorgehensweise [Einfache Portierung von Direct3D9 zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) wird gezeigt, wie ein Fenster eingerichtet, Direct3D initialisiert und einfaches 3D-Rendering durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="893c6-133">The [Simple port from Direct3D 9 to UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough demonstrates how to set up a window, initialize Direct3D, and do basic 3D rendering.</span></span>
-   <span data-ttu-id="893c6-134">In der exemplarischen Vorgehensweise [Erstellen eines einfachen UWP-Spiels mit DirectX](tutorial--create-your-first-uwp-directx-game.md) werden allgemeine Aufgaben der Spielprogrammierung erläutert, u.a. Grafiken, Laden von Dateien, UI, Steuerelemente und Sound.</span><span class="sxs-lookup"><span data-stu-id="893c6-134">The [Simple UWP game with DirectX](tutorial--create-your-first-uwp-directx-game.md) walkthrough demonstrates common game programming tasks including graphics, loading files, UI, controls, and sound.</span></span>
-   <span data-ttu-id="893c6-135">Das Communityprojekt [DirectX-Toolkit](http://go.microsoft.com/fwlink/p/?LinkID=248929) bietet Hilfsklassen zur Verwendung mit Direct3D11 und UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="893c6-135">The [DirectX Tool Kit](http://go.microsoft.com/fwlink/p/?LinkID=248929) community project offers helper classes for use with Direct3D 11 and UWP apps.</span></span>

## <a name="move-shader-programs-from-fx-to-hlsl"></a><span data-ttu-id="893c6-136">Umstellung von Shaderprogrammen von FX auf HLSL</span><span class="sxs-lookup"><span data-stu-id="893c6-136">Move shader programs from FX to HLSL</span></span>


<span data-ttu-id="893c6-137">Die D3DX-Hilfsprogrammbibliothek (D3DX9, D3DX10 und D3DX11), einschließlich Effects, ist veraltet und für UWP nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="893c6-137">The D3DX utility library (D3DX 9, D3DX 10, and D3DX 11), including Effects, is deprecated for UWP.</span></span> <span data-ttu-id="893c6-138">Alle DirectX-Spiele für UWP steuern die Grafikpipeline mit [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561) ohne Effects.</span><span class="sxs-lookup"><span data-stu-id="893c6-138">All DirectX games for UWP drive the graphics pipeline using [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561) without Effects.</span></span>

<span data-ttu-id="893c6-139">Visual Studio verwendet FXC weiterhin im Hintergrund zum Kompilieren von Shaderobjekten.</span><span class="sxs-lookup"><span data-stu-id="893c6-139">Visual Studio still uses FXC under the hood to compile shader objects.</span></span> <span data-ttu-id="893c6-140">UWP-Spielshader werden vorab kompiliert.</span><span class="sxs-lookup"><span data-stu-id="893c6-140">UWP game shaders are compiled ahead of time.</span></span> <span data-ttu-id="893c6-141">Der Bytecode wird zur Laufzeit geladen. Anschließend wird jede Shaderressource während des entsprechenden Renderingdurchgangs an die Grafikpipeline gebunden.</span><span class="sxs-lookup"><span data-stu-id="893c6-141">The bytecode is loaded at runtime, then each shader resource is bound to the graphics pipeline during the appropriate rendering pass.</span></span> <span data-ttu-id="893c6-142">Shader sollten in eigene separate HLSL-Dateien verschoben werden, und Renderingtechniken sollten im C++-Code implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-142">Shaders should be moved to their own separate .HLSL files and rendering techniques should be implemented in your C++ code.</span></span>

<span data-ttu-id="893c6-143">Einen kurzen Überblick über das Laden von Shaderressourcen finden Sie unter [Einfache Portierung von Direct3D9 zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span><span class="sxs-lookup"><span data-stu-id="893c6-143">For a quick look at loading shader resources see [Simple port from Direct3D 9 to UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span></span>

<span data-ttu-id="893c6-144">In Direct3D11 wurde Shadermodell5 eingeführt, das die Direct3D-Funktionsebene11\_0 (oder höher) erfordert.</span><span class="sxs-lookup"><span data-stu-id="893c6-144">Direct3D 11 introduced Shader Model 5, which requires Direct3D feature level 11\_0 (or above).</span></span> <span data-ttu-id="893c6-145">Siehe [Funktionen von HLSL-Shadermodell5 für Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff471419).</span><span class="sxs-lookup"><span data-stu-id="893c6-145">See [HLSL Shader Model 5 Features for Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff471419).</span></span>

## <a name="replace-xnamath-and-d3dxmath"></a><span data-ttu-id="893c6-146">Ersetzen von XNAMath und D3DXMath</span><span class="sxs-lookup"><span data-stu-id="893c6-146">Replace XNAMath and D3DXMath</span></span>


<span data-ttu-id="893c6-147">Code mit XNAMath (oder D3DXMath) sollte zu [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) migriert werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-147">Code using XNAMath (or D3DXMath) should be migrated to [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833).</span></span> <span data-ttu-id="893c6-148">DirectXMath enthält Typen, die zwischen x86, x64 und ARM portierbar sind.</span><span class="sxs-lookup"><span data-stu-id="893c6-148">DirectXMath includes types that are portable across x86, x64, and ARM.</span></span> <span data-ttu-id="893c6-149">Siehe [Codemigration von der XNAMath-Bibliothek](https://msdn.microsoft.com/library/windows/desktop/ee418730).</span><span class="sxs-lookup"><span data-stu-id="893c6-149">See [Code Migration from the XNA Math Library](https://msdn.microsoft.com/library/windows/desktop/ee418730).</span></span>

<span data-ttu-id="893c6-150">Beachten Sie, dass sich Float-Typen von DirectXMath zur Verwendung mit Shadern eignen.</span><span class="sxs-lookup"><span data-stu-id="893c6-150">Note that DirectXMath float types are convenient for use with shaders.</span></span> <span data-ttu-id="893c6-151">Mit [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) und [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) können z.B. auf einfache Weise Daten für Konstantenpuffer ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-151">For example [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) and [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) conveniently align data for constant buffers.</span></span>

## <a name="replace-directsound-with-xaudio2-and-background-audio"></a><span data-ttu-id="893c6-152">Ersetzen von DirectSound durch XAudio2 (und Hintergrundaudio)</span><span class="sxs-lookup"><span data-stu-id="893c6-152">Replace DirectSound with XAudio2 (and background audio)</span></span>


<span data-ttu-id="893c6-153">DirectSound wird für UWP nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="893c6-153">DirectSound is not supported for UWP:</span></span>

-   <span data-ttu-id="893c6-154">Verwenden Sie [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049), um Ihrem Spiel Soundeffekte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="893c6-154">Use [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049) to add sound effects to your game.</span></span>

##  <a name="replace-directinput-with-xinput-and-uwp-apis"></a><span data-ttu-id="893c6-155">Ersetzen von DirectInput durch XInput und UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="893c6-155">Replace DirectInput with XInput and UWP APIs</span></span>


<span data-ttu-id="893c6-156">DirectInput wird für UWP nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="893c6-156">DirectInput is not supported for UWP:</span></span>

-   <span data-ttu-id="893c6-157">Verwenden Sie [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Eingabeereignisrückrufe für Maus-, Tastatur- und Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="893c6-157">Use [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) input event callbacks for mouse, keyboard, and touch input.</span></span>
-   <span data-ttu-id="893c6-158">Verwenden Sie [XInput](https://msdn.microsoft.com/library/windows/desktop/ee417001)1.4 zur Unterstützung von Gamecontrollern (und Gamecontroller-Headsets).</span><span class="sxs-lookup"><span data-stu-id="893c6-158">Use [XInput](https://msdn.microsoft.com/library/windows/desktop/ee417001) 1.4 for game controller support (and game controller headset support).</span></span> <span data-ttu-id="893c6-159">Wenn Sie eine freigegebene Codebasis für Desktop und UWP verwenden, finden Sie unter [XInput-Versionen](https://msdn.microsoft.com/library/windows/desktop/hh405051) Informationen zur Abwärtskompatibilität.</span><span class="sxs-lookup"><span data-stu-id="893c6-159">If you are using a shared code base for desktop and UWP, see [XInput Versions](https://msdn.microsoft.com/library/windows/desktop/hh405051) for information on backwards compatibility.</span></span>
-   <span data-ttu-id="893c6-160">Registrieren Sie [**EdgeGesture**](https://msdn.microsoft.com/library/windows/apps/hh701600)-Ereignisse, wenn die App-Leiste in Ihrem Spiel verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="893c6-160">Register for [**EdgeGesture**](https://msdn.microsoft.com/library/windows/apps/hh701600) events if your game needs to use the app bar.</span></span>

## <a name="use-microsoft-media-foundation-instead-of-directshow"></a><span data-ttu-id="893c6-161">Verwenden von Microsoft Media Foundation anstelle von DirectShow</span><span class="sxs-lookup"><span data-stu-id="893c6-161">Use Microsoft Media Foundation instead of DirectShow</span></span>


<span data-ttu-id="893c6-162">DirectShow ist nicht mehr in der DirectX-API (oder der Windows-API) enthalten.</span><span class="sxs-lookup"><span data-stu-id="893c6-162">DirectShow is no longer part of the DirectX API (or the Windows API).</span></span> <span data-ttu-id="893c6-163">[Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) stellt Videoinhalte mithilfe von freigegebenen Oberflächen für Direct3D bereit.</span><span class="sxs-lookup"><span data-stu-id="893c6-163">[Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) provides video content to Direct3D using shared surfaces.</span></span> <span data-ttu-id="893c6-164">Siehe [Direct3D11-Video-APIs](https://msdn.microsoft.com/library/windows/desktop/hh447677).</span><span class="sxs-lookup"><span data-stu-id="893c6-164">See [Direct3D 11 Video APIs](https://msdn.microsoft.com/library/windows/desktop/hh447677).</span></span>

## <a name="replace-directplay-with-networking-code"></a><span data-ttu-id="893c6-165">Ersetzen von DirectPlay durch Netzwerkcode</span><span class="sxs-lookup"><span data-stu-id="893c6-165">Replace DirectPlay with networking code</span></span>


<span data-ttu-id="893c6-166">Microsoft DirectPlay ist veraltet und nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="893c6-166">Microsoft DirectPlay has been deprecated.</span></span> <span data-ttu-id="893c6-167">Falls Ihr Spiel Netzwerkdienste verwendet, müssen Sie Netzwerkcode bereitstellen, der den UWP-Anforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="893c6-167">If your game uses network services, you need to provide networking code that complies with UWP requirements.</span></span> <span data-ttu-id="893c6-168">Verwenden Sie die folgenden APIs:</span><span class="sxs-lookup"><span data-stu-id="893c6-168">Use the following APIs:</span></span>

-   [<span data-ttu-id="893c6-169">Win32 und COM für UWP-Apps (Netzwerk) (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-169">Win32 and COM for UWP apps (networking) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/br205759)
-   [**<span data-ttu-id="893c6-170">Windows.Networking-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-170">Windows.Networking namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207124)
-   [**<span data-ttu-id="893c6-171">Windows.Networking.Sockets-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-171">Windows.Networking.Sockets namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226960)
-   [**<span data-ttu-id="893c6-172">Windows.Networking.Connectivity-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-172">Windows.Networking.Connectivity namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207308)
-   [**<span data-ttu-id="893c6-173">Windows.ApplicationModel.Background-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-173">Windows.ApplicationModel.Background namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)

<span data-ttu-id="893c6-174">In den folgenden Artikeln finden Sie Informationen zum Hinzufügen von Netzwerkfunktionen und Deklarieren der Netzwerkunterstützung im Paketmanifest Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="893c6-174">The following articles help you add networking features and declare support for networking in your app's package manifest.</span></span>

-   [<span data-ttu-id="893c6-175">Verbinden mit Sockets (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-175">Connecting with sockets (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452976)
-   [<span data-ttu-id="893c6-176">Verbinden mit WebSockets (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-176">Connecting with WebSockets (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh994396)
-   [<span data-ttu-id="893c6-177">Herstellen einer Verbindung mit Webdiensten (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="893c6-177">Connecting to web services (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh761504)
-   [<span data-ttu-id="893c6-178">Vernetzungsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="893c6-178">Networking basics</span></span>](https://msdn.microsoft.com/library/windows/apps/mt280233)

<span data-ttu-id="893c6-179">Beachten Sie, dass alle UWP-Apps (einschließlich Spiele) bestimmte Hintergrundaufgaben verwenden, um die Verbindung aufrechtzuerhalten, während die App angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="893c6-179">Note that all UWP apps (including games) use specific types of background tasks to maintain connectivity while the app is suspended.</span></span> <span data-ttu-id="893c6-180">Wenn Ihr Spiel den Verbindungsstatus aufrechterhalten muss, während es angehalten ist, gehen Sie wie unter [Grundlagen zum Netzwerk](https://msdn.microsoft.com/library/windows/apps/mt280233) beschrieben vor.</span><span class="sxs-lookup"><span data-stu-id="893c6-180">If your game needs to maintain connection state while suspended see [Networking basics](https://msdn.microsoft.com/library/windows/apps/mt280233).</span></span>

## <a name="function-mapping"></a><span data-ttu-id="893c6-181">Funktionszuordnung</span><span class="sxs-lookup"><span data-stu-id="893c6-181">Function mapping</span></span>


<span data-ttu-id="893c6-182">Ziehen Sie beim Konvertieren von Code von Direct3D9 in Direct3D11 die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="893c6-182">Use the following table to help convert code from Direct3D 9 to Direct3D 11.</span></span> <span data-ttu-id="893c6-183">Diese Informationen können Ihnen auch die Unterscheidung zwischen Gerät und Gerätekontext erleichtern.</span><span class="sxs-lookup"><span data-stu-id="893c6-183">This can also help distinguish between the device and device context.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="893c6-184">Direct3D9</span><span class="sxs-lookup"><span data-stu-id="893c6-184">Direct3D9</span></span></th>
<th align="left"><span data-ttu-id="893c6-185">Direct3D11-Entsprechung</span><span class="sxs-lookup"><span data-stu-id="893c6-185">Direct3D 11 Equivalent</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174336"><span data-ttu-id="893c6-186">IDirect3DDevice9</span><span class="sxs-lookup"><span data-stu-id="893c6-186">IDirect3DDevice9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280493"><span data-ttu-id="893c6-187">ID3D11Device2</span><span class="sxs-lookup"><span data-stu-id="893c6-187">ID3D11Device2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280498"><span data-ttu-id="893c6-188">ID3D11DeviceContext2</span><span class="sxs-lookup"><span data-stu-id="893c6-188">ID3D11DeviceContext2</span></span></a></p>
<p><span data-ttu-id="893c6-189">Die Grafikpipelinestufen werden unter <a href="https://msdn.microsoft.com/library/windows/desktop/ff476882">Grafikpipeline</a> erläutert.</span><span class="sxs-lookup"><span data-stu-id="893c6-189">The graphics pipeline stages are described in <a href="https://msdn.microsoft.com/library/windows/desktop/ff476882">Graphics Pipeline</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174300"><span data-ttu-id="893c6-190">IDirect3D9</span><span class="sxs-lookup"><span data-stu-id="893c6-190">IDirect3D9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404556"><span data-ttu-id="893c6-191">IDXGIFactory2</span><span class="sxs-lookup"><span data-stu-id="893c6-191">IDXGIFactory2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404537"><span data-ttu-id="893c6-192">IDXGIAdapter2</span><span class="sxs-lookup"><span data-stu-id="893c6-192">IDXGIAdapter2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280345"><span data-ttu-id="893c6-193">IDXGIDevice3</span><span class="sxs-lookup"><span data-stu-id="893c6-193">IDXGIDevice3</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174423"><span data-ttu-id="893c6-194">IDirect3DDevice9::Present</span><span class="sxs-lookup"><span data-stu-id="893c6-194">IDirect3DDevice9::Present</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797"><span data-ttu-id="893c6-195">IDXGISwapChain1::Present1</span><span class="sxs-lookup"><span data-stu-id="893c6-195">IDXGISwapChain1::Present1</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174472"><span data-ttu-id="893c6-196">IDirect3DDevice9::TestCooperativeLevel</span><span class="sxs-lookup"><span data-stu-id="893c6-196">IDirect3DDevice9::TestCooperativeLevel</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-197">Rufen Sie <a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1:: Present1</a> mit der festgelegten DXGI_PRESENT_TEST-Kennung auf.</span><span class="sxs-lookup"><span data-stu-id="893c6-197">Call <a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> with the DXGI_PRESENT_TEST flag set.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174322"><span data-ttu-id="893c6-198">IDirect3DBaseTexture9</span><span class="sxs-lookup"><span data-stu-id="893c6-198">IDirect3DBaseTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205909"><span data-ttu-id="893c6-199">IDirect3DTexture9</span><span class="sxs-lookup"><span data-stu-id="893c6-199">IDirect3DTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174329"><span data-ttu-id="893c6-200">IDirect3DCubeTexture9</span><span class="sxs-lookup"><span data-stu-id="893c6-200">IDirect3DCubeTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205941"><span data-ttu-id="893c6-201">IDirect3DVolumeTexture9</span><span class="sxs-lookup"><span data-stu-id="893c6-201">IDirect3DVolumeTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205865"><span data-ttu-id="893c6-202">IDirect3DIndexBuffer9</span><span class="sxs-lookup"><span data-stu-id="893c6-202">IDirect3DIndexBuffer9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205915"><span data-ttu-id="893c6-203">IDirect3DVertexBuffer9</span><span class="sxs-lookup"><span data-stu-id="893c6-203">IDirect3DVertexBuffer9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476351"><span data-ttu-id="893c6-204">ID3D11Buffer</span><span class="sxs-lookup"><span data-stu-id="893c6-204">ID3D11Buffer</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476633"><span data-ttu-id="893c6-205">ID3D11Texture1D</span><span class="sxs-lookup"><span data-stu-id="893c6-205">ID3D11Texture1D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476635"><span data-ttu-id="893c6-206">ID3D11Texture2D</span><span class="sxs-lookup"><span data-stu-id="893c6-206">ID3D11Texture2D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476637"><span data-ttu-id="893c6-207">ID3D11Texture3D</span><span class="sxs-lookup"><span data-stu-id="893c6-207">ID3D11Texture3D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476628"><span data-ttu-id="893c6-208">ID3D11ShaderResourceView</span><span class="sxs-lookup"><span data-stu-id="893c6-208">ID3D11ShaderResourceView</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476582"><span data-ttu-id="893c6-209">ID3D11RenderTargetView</span><span class="sxs-lookup"><span data-stu-id="893c6-209">ID3D11RenderTargetView</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476377"><span data-ttu-id="893c6-210">ID3D11DepthStencilView</span><span class="sxs-lookup"><span data-stu-id="893c6-210">ID3D11DepthStencilView</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205922"><span data-ttu-id="893c6-211">IDirect3DVertexShader9</span><span class="sxs-lookup"><span data-stu-id="893c6-211">IDirect3DVertexShader9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205869"><span data-ttu-id="893c6-212">IDirect3DPixelShader9</span><span class="sxs-lookup"><span data-stu-id="893c6-212">IDirect3DPixelShader9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476641"><span data-ttu-id="893c6-213">ID3D11VertexShader</span><span class="sxs-lookup"><span data-stu-id="893c6-213">ID3D11VertexShader</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476576"><span data-ttu-id="893c6-214">ID3D11PixelShader</span><span class="sxs-lookup"><span data-stu-id="893c6-214">ID3D11PixelShader</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205919"><span data-ttu-id="893c6-215">IDirect3DVertexDeclaration9</span><span class="sxs-lookup"><span data-stu-id="893c6-215">IDirect3DVertexDeclaration9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476575"><span data-ttu-id="893c6-216">ID3D11InputLayout</span><span class="sxs-lookup"><span data-stu-id="893c6-216">ID3D11InputLayout</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205805"><span data-ttu-id="893c6-217">IDirect3DDevice9::SetRenderState</span><span class="sxs-lookup"><span data-stu-id="893c6-217">IDirect3DDevice9::SetRenderState</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205806"><span data-ttu-id="893c6-218">IDirect3DDevice9::SetSamplerState</span><span class="sxs-lookup"><span data-stu-id="893c6-218">IDirect3DDevice9::SetSamplerState</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404571"><span data-ttu-id="893c6-219">ID3D11BlendState1</span><span class="sxs-lookup"><span data-stu-id="893c6-219">ID3D11BlendState1</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476375"><span data-ttu-id="893c6-220">ID3D11DepthStencilState</span><span class="sxs-lookup"><span data-stu-id="893c6-220">ID3D11DepthStencilState</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/hh446828"><span data-ttu-id="893c6-221">ID3D11RasterizerState1</span><span class="sxs-lookup"><span data-stu-id="893c6-221">ID3D11RasterizerState1</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476588"><span data-ttu-id="893c6-222">ID3D11SamplerState</span><span class="sxs-lookup"><span data-stu-id="893c6-222">ID3D11SamplerState</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174369"><span data-ttu-id="893c6-223">IDirect3DDevice9::DrawIndexedPrimitive</span><span class="sxs-lookup"><span data-stu-id="893c6-223">IDirect3DDevice9::DrawIndexedPrimitive</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174371"><span data-ttu-id="893c6-224">IDirect3DDevice9::DrawPrimitive</span><span class="sxs-lookup"><span data-stu-id="893c6-224">IDirect3DDevice9::DrawPrimitive</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476407"><span data-ttu-id="893c6-225">ID3D11DeviceContext::Draw</span><span class="sxs-lookup"><span data-stu-id="893c6-225">ID3D11DeviceContext::Draw</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476409"><span data-ttu-id="893c6-226">ID3D11DeviceContext::DrawIndexed</span><span class="sxs-lookup"><span data-stu-id="893c6-226">ID3D11DeviceContext::DrawIndexed</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173566"><span data-ttu-id="893c6-227">ID3D11DeviceContext::DrawIndexedInstanced</span><span class="sxs-lookup"><span data-stu-id="893c6-227">ID3D11DeviceContext::DrawIndexedInstanced</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173567"><span data-ttu-id="893c6-228">ID3D11DeviceContext::DrawInstanced</span><span class="sxs-lookup"><span data-stu-id="893c6-228">ID3D11DeviceContext::DrawInstanced</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173590"><span data-ttu-id="893c6-229">ID3D11DeviceContext::IASetPrimitiveTopology</span><span class="sxs-lookup"><span data-stu-id="893c6-229">ID3D11DeviceContext::IASetPrimitiveTopology</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173564"><span data-ttu-id="893c6-230">ID3D11DeviceContext::DrawAuto</span><span class="sxs-lookup"><span data-stu-id="893c6-230">ID3D11DeviceContext::DrawAuto</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174350"><span data-ttu-id="893c6-231">IDirect3DDevice9::BeginScene</span><span class="sxs-lookup"><span data-stu-id="893c6-231">IDirect3DDevice9::BeginScene</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174375"><span data-ttu-id="893c6-232">IDirect3DDevice9::EndScene</span><span class="sxs-lookup"><span data-stu-id="893c6-232">IDirect3DDevice9::EndScene</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174372"><span data-ttu-id="893c6-233">IDirect3DDevice9::DrawPrimitiveUP</span><span class="sxs-lookup"><span data-stu-id="893c6-233">IDirect3DDevice9::DrawPrimitiveUP</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174370"><span data-ttu-id="893c6-234">IDirect3DDevice9::DrawIndexedPrimitiveUP</span><span class="sxs-lookup"><span data-stu-id="893c6-234">IDirect3DDevice9::DrawIndexedPrimitiveUP</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-235">Kein direktes Äquivalent</span><span class="sxs-lookup"><span data-stu-id="893c6-235">No direct equivalent</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174470"><span data-ttu-id="893c6-236">IDirect3DDevice9::ShowCursor</span><span class="sxs-lookup"><span data-stu-id="893c6-236">IDirect3DDevice9::ShowCursor</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174429"><span data-ttu-id="893c6-237">IDirect3DDevice9::SetCursorPosition</span><span class="sxs-lookup"><span data-stu-id="893c6-237">IDirect3DDevice9::SetCursorPosition</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174430"><span data-ttu-id="893c6-238">IDirect3DDevice9::SetCursorProperties</span><span class="sxs-lookup"><span data-stu-id="893c6-238">IDirect3DDevice9::SetCursorProperties</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-239">Verwenden Sie standardmäßige Cursor-APIs.</span><span class="sxs-lookup"><span data-stu-id="893c6-239">Use standard cursor APIs.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174425"><span data-ttu-id="893c6-240">IDirect3DDevice9::Reset</span><span class="sxs-lookup"><span data-stu-id="893c6-240">IDirect3DDevice9::Reset</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-241">"LOST device" und POOL_MANAGED sind nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="893c6-241">LOST device and POOL_MANAGED no longer exist.</span></span> <span data-ttu-id="893c6-242"><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> kann mit einem <a href="https://msdn.microsoft.com/library/windows/desktop/bb509553">DXGI_ERROR_DEVICE_REMOVED</a> Rückgabewert fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="893c6-242"><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> can fail with a <a href="https://msdn.microsoft.com/library/windows/desktop/bb509553">DXGI_ERROR_DEVICE_REMOVED</a> return value.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174373"><span data-ttu-id="893c6-243">IDirect3DDevice9:DrawRectPatch</span><span class="sxs-lookup"><span data-stu-id="893c6-243">IDirect3DDevice9:DrawRectPatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174374"><span data-ttu-id="893c6-244">IDirect3DDevice9:DrawTriPatch</span><span class="sxs-lookup"><span data-stu-id="893c6-244">IDirect3DDevice9:DrawTriPatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174421"><span data-ttu-id="893c6-245">IDirect3DDevice9:LightEnable</span><span class="sxs-lookup"><span data-stu-id="893c6-245">IDirect3DDevice9:LightEnable</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174422"><span data-ttu-id="893c6-246">IDirect3DDevice9:MultiplyTransform</span><span class="sxs-lookup"><span data-stu-id="893c6-246">IDirect3DDevice9:MultiplyTransform</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205798"><span data-ttu-id="893c6-247">IDirect3DDevice9:SetLight</span><span class="sxs-lookup"><span data-stu-id="893c6-247">IDirect3DDevice9:SetLight</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174437"><span data-ttu-id="893c6-248">IDirect3DDevice9:SetMaterial</span><span class="sxs-lookup"><span data-stu-id="893c6-248">IDirect3DDevice9:SetMaterial</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174438"><span data-ttu-id="893c6-249">IDirect3DDevice9:SetNPatchMode</span><span class="sxs-lookup"><span data-stu-id="893c6-249">IDirect3DDevice9:SetNPatchMode</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174463"><span data-ttu-id="893c6-250">IDirect3DDevice9:SetTransform</span><span class="sxs-lookup"><span data-stu-id="893c6-250">IDirect3DDevice9:SetTransform</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174433"><span data-ttu-id="893c6-251">IDirect3DDevice9:SetFVF</span><span class="sxs-lookup"><span data-stu-id="893c6-251">IDirect3DDevice9:SetFVF</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174462"><span data-ttu-id="893c6-252">IDirect3DDevice9:SetTextureStageState</span><span class="sxs-lookup"><span data-stu-id="893c6-252">IDirect3DDevice9:SetTextureStageState</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-253">Die Pipeline mit fester Funktion ist veraltet und nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="893c6-253">The fixed-function pipeline has been deprecated.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174308"><span data-ttu-id="893c6-254">IDirect3DDevice9:CheckDepthStencilMatch</span><span class="sxs-lookup"><span data-stu-id="893c6-254">IDirect3DDevice9:CheckDepthStencilMatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174309"><span data-ttu-id="893c6-255">IDirect3DDevice9:CheckDeviceFormat</span><span class="sxs-lookup"><span data-stu-id="893c6-255">IDirect3DDevice9:CheckDeviceFormat</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174320"><span data-ttu-id="893c6-256">IDirect3DDevice9:GetDeviceCaps</span><span class="sxs-lookup"><span data-stu-id="893c6-256">IDirect3DDevice9:GetDeviceCaps</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205859"><span data-ttu-id="893c6-257">IDirect3DDevice9:ValidateDevice</span><span class="sxs-lookup"><span data-stu-id="893c6-257">IDirect3DDevice9:ValidateDevice</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="893c6-258">Funktionsbits werden durch Funktionsebenen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="893c6-258">Capability bits are replaced with feature levels.</span></span> <span data-ttu-id="893c6-259">Nur einige wenige Format- und Funktionsverwendungsfälle sind für alle Funktionsebenen optional.</span><span class="sxs-lookup"><span data-stu-id="893c6-259">Only a few format and feature usage cases are optional for any given feature level.</span></span> <span data-ttu-id="893c6-260">Diese können mit <a href="https://msdn.microsoft.com/library/windows/desktop/ff476497">ID3D11Device::CheckFeatureSupport</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/bb173536">ID3D11Device::CheckFormatSupport</a> überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-260">These can be checked with <a href="https://msdn.microsoft.com/library/windows/desktop/ff476497">ID3D11Device::CheckFeatureSupport</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/bb173536">ID3D11Device::CheckFormatSupport</a>.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="surface-format-mapping"></a><span data-ttu-id="893c6-261">Oberflächenformatzuordnung</span><span class="sxs-lookup"><span data-stu-id="893c6-261">Surface format mapping</span></span>


<span data-ttu-id="893c6-262">Ziehen Sie beim Konvertieren von Direct3D9-Formaten in DXGI-Formate die folgende Tabelle heran.</span><span class="sxs-lookup"><span data-stu-id="893c6-262">Use the following table to convert Direct3D 9 formats into DXGI formats.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="893c6-263">Direct3D9-Format</span><span class="sxs-lookup"><span data-stu-id="893c6-263">Direct3D 9 Format</span></span></th>
<th align="left"><span data-ttu-id="893c6-264">Direct3D11-Format</span><span class="sxs-lookup"><span data-stu-id="893c6-264">Direct3D 11 Format</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-265">D3DFMT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="893c6-265">D3DFMT_UNKNOWN</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-266">DXGI_FORMAT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="893c6-266">DXGI_FORMAT_UNKNOWN</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-267">D3DFMT_R8G8B8</span><span class="sxs-lookup"><span data-stu-id="893c6-267">D3DFMT_R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-268">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-268">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-269">D3DFMT_A8R8G8B8</span><span class="sxs-lookup"><span data-stu-id="893c6-269">D3DFMT_A8R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-270">DXGI_FORMAT_B8G8R8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-270">DXGI_FORMAT_B8G8R8A8_UNORM</span></span></p>
<p><span data-ttu-id="893c6-271">DXGI_FORMAT_B8G8R8A8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-271">DXGI_FORMAT_B8G8R8A8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-272">D3DFMT_X8R8G8B8</span><span class="sxs-lookup"><span data-stu-id="893c6-272">D3DFMT_X8R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-273">DXGI_FORMAT_B8G8R8X8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-273">DXGI_FORMAT_B8G8R8X8_UNORM</span></span></p>
<p><span data-ttu-id="893c6-274">DXGI_FORMAT_B8G8R8X8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-274">DXGI_FORMAT_B8G8R8X8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-275">D3DFMT_R5G6B5</span><span class="sxs-lookup"><span data-stu-id="893c6-275">D3DFMT_R5G6B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-276">DXGI_FORMAT_B5G6R5_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-276">DXGI_FORMAT_B5G6R5_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-277">D3DFMT_X1R5G5B5</span><span class="sxs-lookup"><span data-stu-id="893c6-277">D3DFMT_X1R5G5B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-278">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-278">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-279">D3DFMT_A1R5G5B5</span><span class="sxs-lookup"><span data-stu-id="893c6-279">D3DFMT_A1R5G5B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-280">DXGI_FORMAT_B5G5R5A1_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-280">DXGI_FORMAT_B5G5R5A1_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-281">D3DFMT_A4R4G4B4</span><span class="sxs-lookup"><span data-stu-id="893c6-281">D3DFMT_A4R4G4B4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-282">DXGI_FORMAT_B4G4R4A4_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-282">DXGI_FORMAT_B4G4R4A4_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-283">D3DFMT_R3G3B2</span><span class="sxs-lookup"><span data-stu-id="893c6-283">D3DFMT_R3G3B2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-284">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-284">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-285">D3DFMT_A8</span><span class="sxs-lookup"><span data-stu-id="893c6-285">D3DFMT_A8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-286">DXGI_FORMAT_A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-286">DXGI_FORMAT_A8_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-287">D3DFMT_A8R3G3B2</span><span class="sxs-lookup"><span data-stu-id="893c6-287">D3DFMT_A8R3G3B2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-288">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-288">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-289">D3DFMT_X4R4G4B4</span><span class="sxs-lookup"><span data-stu-id="893c6-289">D3DFMT_X4R4G4B4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-290">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-290">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-291">D3DFMT_A2B10G10R10</span><span class="sxs-lookup"><span data-stu-id="893c6-291">D3DFMT_A2B10G10R10</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-292">DXGI_FORMAT_R10G10B10A2</span><span class="sxs-lookup"><span data-stu-id="893c6-292">DXGI_FORMAT_R10G10B10A2</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-293">D3DFMT_A8B8G8R8</span><span class="sxs-lookup"><span data-stu-id="893c6-293">D3DFMT_A8B8G8R8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-294">DXGI_FORMAT_R8G8B8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-294">DXGI_FORMAT_R8G8B8A8_UNORM</span></span></p>
<p><span data-ttu-id="893c6-295">DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-295">DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-296">D3DFMT_X8B8G8R8</span><span class="sxs-lookup"><span data-stu-id="893c6-296">D3DFMT_X8B8G8R8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-297">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-297">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-298">D3DFMT_G16R16</span><span class="sxs-lookup"><span data-stu-id="893c6-298">D3DFMT_G16R16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-299">DXGI_FORMAT_R16G16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-299">DXGI_FORMAT_R16G16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-300">D3DFMT_A2R10G10B10</span><span class="sxs-lookup"><span data-stu-id="893c6-300">D3DFMT_A2R10G10B10</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-301">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-301">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-302">D3DFMT_A16B16G16R16</span><span class="sxs-lookup"><span data-stu-id="893c6-302">D3DFMT_A16B16G16R16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-303">DXGI_FORMAT_R16G16B16A16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-303">DXGI_FORMAT_R16G16B16A16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-304">D3DFMT_A8P8</span><span class="sxs-lookup"><span data-stu-id="893c6-304">D3DFMT_A8P8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-305">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-305">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-306">D3DFMT_P8</span><span class="sxs-lookup"><span data-stu-id="893c6-306">D3DFMT_P8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-307">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-307">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-308">D3DFMT_L8</span><span class="sxs-lookup"><span data-stu-id="893c6-308">D3DFMT_L8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-309">DXGI_FORMAT_R8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-309">DXGI_FORMAT_R8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-310">
<strong>Hinweis:</strong>  verwenden .r Swizzle im Shader, um Rot für andere Komponenten zu Direct3D 9-Verhaltens duplizieren.</span><span class="sxs-lookup"><span data-stu-id="893c6-310">
<strong>Note</strong> Use .r swizzle in shader to duplicate red to other components to get Direct3D 9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-311">D3DFMT_A8L8</span><span class="sxs-lookup"><span data-stu-id="893c6-311">D3DFMT_A8L8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-312">DXGI_FORMAT_R8G8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-312">DXGI_FORMAT_R8G8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-313">
<strong>Hinweis:</strong>  Swizzle Operator ".rrrg" im Shader verwenden, um Rot zu duplizieren und Grün in die alpha-Komponenten zu Direct3D 9-Verhaltens verschieben.</span><span class="sxs-lookup"><span data-stu-id="893c6-313">
<strong>Note</strong> Use swizzle .rrrg in shader to duplicate red and move green to the alpha components to get Direct3D 9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-314">D3DFMT_A4L4</span><span class="sxs-lookup"><span data-stu-id="893c6-314">D3DFMT_A4L4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-315">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-315">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-316">D3DFMT_V8U8</span><span class="sxs-lookup"><span data-stu-id="893c6-316">D3DFMT_V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-317">DXGI_FORMAT_R8G8_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-317">DXGI_FORMAT_R8G8_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-318">D3DFMT_L6V5U5</span><span class="sxs-lookup"><span data-stu-id="893c6-318">D3DFMT_L6V5U5</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-319">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-319">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-320">D3DFMT_X8L8V8U8</span><span class="sxs-lookup"><span data-stu-id="893c6-320">D3DFMT_X8L8V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-321">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-321">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-322">D3DFMT_Q8W8V8U8</span><span class="sxs-lookup"><span data-stu-id="893c6-322">D3DFMT_Q8W8V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-323">DXGI_FORMAT_R8G8B8A8_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-323">DXGI_FORMAT_R8G8B8A8_SNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-324">D3DFMT_V16U16</span><span class="sxs-lookup"><span data-stu-id="893c6-324">D3DFMT_V16U16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-325">DXGI_FORMAT_R16G16_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-325">DXGI_FORMAT_R16G16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-326">D3DFMT_W11V11U10</span><span class="sxs-lookup"><span data-stu-id="893c6-326">D3DFMT_W11V11U10</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-327">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-327">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-328">D3DFMT_A2W10V10U10</span><span class="sxs-lookup"><span data-stu-id="893c6-328">D3DFMT_A2W10V10U10</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-329">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-329">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-330">D3DFMT_UYVY</span><span class="sxs-lookup"><span data-stu-id="893c6-330">D3DFMT_UYVY</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-331">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-331">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-332">D3DFMT_R8G8_B8G8</span><span class="sxs-lookup"><span data-stu-id="893c6-332">D3DFMT_R8G8_B8G8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-333">DXGI_FORMAT_G8R8_G8B8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-333">DXGI_FORMAT_G8R8_G8B8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-334">
<strong>Hinweis:</strong>  In Direct3D 9 wurden die Daten vom 255.0f vergrößert wurde, aber dies kann im Shader behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-334">
<strong>Note</strong> In Direct3D 9 the data was scaled up by 255.0f, but this can be handled in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-335">D3DFMT_YUY2</span><span class="sxs-lookup"><span data-stu-id="893c6-335">D3DFMT_YUY2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-336">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-336">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-337">D3DFMT_G8R8_G8B8</span><span class="sxs-lookup"><span data-stu-id="893c6-337">D3DFMT_G8R8_G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-338">DXGI_FORMAT_R8G8_B8G8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-338">DXGI_FORMAT_R8G8_B8G8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-339">
<strong>Hinweis:</strong>  In Direct3D 9 wurden die Daten vom 255.0f vergrößert wurde, aber dies kann im Shader behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-339">
<strong>Note</strong> In Direct3D 9 the data was scaled up by 255.0f, but this can be handled in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-340">D3DFMT_DXT1</span><span class="sxs-lookup"><span data-stu-id="893c6-340">D3DFMT_DXT1</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-341">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-341">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-342">D3DFMT_DXT2</span><span class="sxs-lookup"><span data-stu-id="893c6-342">D3DFMT_DXT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-343">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-343">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span></span></p>
<div class="alert"><span data-ttu-id="893c6-344">
<strong>Hinweis:</strong>  DXT1 und DXT2 sind gleich aus Sicht der API-Hardware.</span><span class="sxs-lookup"><span data-stu-id="893c6-344">
<strong>Note</strong> DXT1 and DXT2 are the same from an API/hardware perspective.</span></span> <span data-ttu-id="893c6-345">Der einzige Unterschied besteht darin, ob prämultipliziertes Alpha verwendet wird, was von einer App nachverfolgt werden kann und kein separates Format erfordert.</span><span class="sxs-lookup"><span data-stu-id="893c6-345">The only difference is whether premultiplied alpha is used, which can be tracked by an application and doesn't need a separate format.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-346">D3DFMT_DXT3</span><span class="sxs-lookup"><span data-stu-id="893c6-346">D3DFMT_DXT3</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-347">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-347">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-348">D3DFMT_DXT4</span><span class="sxs-lookup"><span data-stu-id="893c6-348">D3DFMT_DXT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-349">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-349">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span></span></p>
<div class="alert"><span data-ttu-id="893c6-350">
<strong>Hinweis:</strong>  DXT3 und DXT4 sind gleich aus Sicht der API-Hardware.</span><span class="sxs-lookup"><span data-stu-id="893c6-350">
<strong>Note</strong> DXT3 and DXT4 are the same from an API/hardware perspective.</span></span> <span data-ttu-id="893c6-351">Der einzige Unterschied besteht darin, ob prämultipliziertes Alpha verwendet wird, was von einer App nachverfolgt werden kann und kein separates Format erfordert.</span><span class="sxs-lookup"><span data-stu-id="893c6-351">The only difference is whether premultiplied alpha is used, which can be tracked by an application and doesn't need a separate format.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-352">D3DFMT_DXT5</span><span class="sxs-lookup"><span data-stu-id="893c6-352">D3DFMT_DXT5</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-353">DXGI_FORMAT_BC3_UNORM & DXGI_FORMAT_BC3_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="893c6-353">DXGI_FORMAT_BC3_UNORM & DXGI_FORMAT_BC3_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-354">D3DFMT_D16 & D3DFMT_D16_LOCKABLE</span><span class="sxs-lookup"><span data-stu-id="893c6-354">D3DFMT_D16 & D3DFMT_D16_LOCKABLE</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-355">DXGI_FORMAT_D16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-355">DXGI_FORMAT_D16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-356">D3DFMT_D32</span><span class="sxs-lookup"><span data-stu-id="893c6-356">D3DFMT_D32</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-357">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-357">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-358">D3DFMT_D15S1</span><span class="sxs-lookup"><span data-stu-id="893c6-358">D3DFMT_D15S1</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-359">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-359">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-360">D3DFMT_D24S8</span><span class="sxs-lookup"><span data-stu-id="893c6-360">D3DFMT_D24S8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-361">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-361">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-362">D3DFMT_D24X8</span><span class="sxs-lookup"><span data-stu-id="893c6-362">D3DFMT_D24X8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-363">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-363">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-364">D3DFMT_D24X4S4</span><span class="sxs-lookup"><span data-stu-id="893c6-364">D3DFMT_D24X4S4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-365">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-365">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-366">D3DFMT_D16</span><span class="sxs-lookup"><span data-stu-id="893c6-366">D3DFMT_D16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-367">DXGI_FORMAT_D16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-367">DXGI_FORMAT_D16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-368">D3DFMT_D32F_LOCKABLE</span><span class="sxs-lookup"><span data-stu-id="893c6-368">D3DFMT_D32F_LOCKABLE</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-369">DXGI_FORMAT_D32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-369">DXGI_FORMAT_D32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-370">D3DFMT_D24FS8</span><span class="sxs-lookup"><span data-stu-id="893c6-370">D3DFMT_D24FS8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-371">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-371">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-372">D3DFMT_S1D15</span><span class="sxs-lookup"><span data-stu-id="893c6-372">D3DFMT_S1D15</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-373">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-373">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-374">D3DFMT_S8D24</span><span class="sxs-lookup"><span data-stu-id="893c6-374">D3DFMT_S8D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-375">DXGI_FORMAT_D24_UNORM_S8_UINT</span><span class="sxs-lookup"><span data-stu-id="893c6-375">DXGI_FORMAT_D24_UNORM_S8_UINT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-376">D3DFMT_X8D24</span><span class="sxs-lookup"><span data-stu-id="893c6-376">D3DFMT_X8D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-377">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-377">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-378">D3DFMT_X4S4D24</span><span class="sxs-lookup"><span data-stu-id="893c6-378">D3DFMT_X4S4D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-379">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-379">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-380">D3DFMT_L16</span><span class="sxs-lookup"><span data-stu-id="893c6-380">D3DFMT_L16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-381">DXGI_FORMAT_R16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-381">DXGI_FORMAT_R16_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-382">
<strong>Hinweis:</strong>  verwenden .r Swizzle im Shader, um Rot für andere Komponenten zu D3D9-Verhaltens duplizieren.</span><span class="sxs-lookup"><span data-stu-id="893c6-382">
<strong>Note</strong> Use .r swizzle in shader to duplicate red to other components to get D3D9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-383">D3DFMT_INDEX16</span><span class="sxs-lookup"><span data-stu-id="893c6-383">D3DFMT_INDEX16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-384">DXGI_FORMAT_R16_UINT</span><span class="sxs-lookup"><span data-stu-id="893c6-384">DXGI_FORMAT_R16_UINT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-385">D3DFMT_INDEX32</span><span class="sxs-lookup"><span data-stu-id="893c6-385">D3DFMT_INDEX32</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-386">DXGI_FORMAT_R32_UINT</span><span class="sxs-lookup"><span data-stu-id="893c6-386">DXGI_FORMAT_R32_UINT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-387">D3DFMT_Q16W16V16U16</span><span class="sxs-lookup"><span data-stu-id="893c6-387">D3DFMT_Q16W16V16U16</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-388">DXGI_FORMAT_R16G16B16A16_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-388">DXGI_FORMAT_R16G16B16A16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-389">D3DFMT_MULTI2_ARGB8</span><span class="sxs-lookup"><span data-stu-id="893c6-389">D3DFMT_MULTI2_ARGB8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-390">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-390">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-391">D3DFMT_R16F</span><span class="sxs-lookup"><span data-stu-id="893c6-391">D3DFMT_R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-392">DXGI_FORMAT_R16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-392">DXGI_FORMAT_R16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-393">D3DFMT_G16R16F</span><span class="sxs-lookup"><span data-stu-id="893c6-393">D3DFMT_G16R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-394">DXGI_FORMAT_R16G16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-394">DXGI_FORMAT_R16G16_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-395">D3DFMT_A16B16G16R16F</span><span class="sxs-lookup"><span data-stu-id="893c6-395">D3DFMT_A16B16G16R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-396">DXGI_FORMAT_R16G16B16A16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-396">DXGI_FORMAT_R16G16B16A16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-397">D3DFMT_R32F</span><span class="sxs-lookup"><span data-stu-id="893c6-397">D3DFMT_R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-398">DXGI_FORMAT_R32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-398">DXGI_FORMAT_R32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-399">D3DFMT_G32R32F</span><span class="sxs-lookup"><span data-stu-id="893c6-399">D3DFMT_G32R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-400">DXGI_FORMAT_R32G32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-400">DXGI_FORMAT_R32G32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-401">D3DFMT_A32B32G32R32F</span><span class="sxs-lookup"><span data-stu-id="893c6-401">D3DFMT_A32B32G32R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-402">DXGI_FORMAT_R32G32B32A32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-402">DXGI_FORMAT_R32G32B32A32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-403">D3DFMT_CxV8U8</span><span class="sxs-lookup"><span data-stu-id="893c6-403">D3DFMT_CxV8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-404">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-404">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-405">D3DDECLTYPE_FLOAT1</span><span class="sxs-lookup"><span data-stu-id="893c6-405">D3DDECLTYPE_FLOAT1</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-406">DXGI_FORMAT_R32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-406">DXGI_FORMAT_R32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-407">D3DDECLTYPE_FLOAT2</span><span class="sxs-lookup"><span data-stu-id="893c6-407">D3DDECLTYPE_FLOAT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-408">DXGI_FORMAT_R32G32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-408">DXGI_FORMAT_R32G32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-409">D3DDECLTYPE_FLOAT3</span><span class="sxs-lookup"><span data-stu-id="893c6-409">D3DDECLTYPE_FLOAT3</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-410">DXGI_FORMAT_R32G32B32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-410">DXGI_FORMAT_R32G32B32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-411">D3DDECLTYPE_FLOAT4</span><span class="sxs-lookup"><span data-stu-id="893c6-411">D3DDECLTYPE_FLOAT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-412">DXGI_FORMAT_R32G32B32A32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-412">DXGI_FORMAT_R32G32B32A32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-413">D3DDECLTYPED3DCOLOR</span><span class="sxs-lookup"><span data-stu-id="893c6-413">D3DDECLTYPED3DCOLOR</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-414">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-414">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-415">D3DDECLTYPE_UBYTE4</span><span class="sxs-lookup"><span data-stu-id="893c6-415">D3DDECLTYPE_UBYTE4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-416">DXGI_FORMAT_R8G8B8A8_UINT</span><span class="sxs-lookup"><span data-stu-id="893c6-416">DXGI_FORMAT_R8G8B8A8_UINT</span></span></p>
<div class="alert"><span data-ttu-id="893c6-417">
<strong>Hinweis:</strong>  der Shader ruft UINT-Werte ab, aber wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden (0, 0F, 1, 0F... 255.f), kann UINT im Shader einfach in float32 konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="893c6-417">
<strong>Note</strong> The shader gets UINT values, but if Direct3D 9 style integral floats are needed (0.0f, 1.0f... 255.f), UINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-418">D3DDECLTYPE_SHORT2</span><span class="sxs-lookup"><span data-stu-id="893c6-418">D3DDECLTYPE_SHORT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-419">DXGI_FORMAT_R16G16_SINT</span><span class="sxs-lookup"><span data-stu-id="893c6-419">DXGI_FORMAT_R16G16_SINT</span></span></p>
<div class="alert"><span data-ttu-id="893c6-420">
<strong>Hinweis:</strong>  der Shader ruft SINT-Werte ab, aber wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden, St. gerade konvertiert werden kann einfach in float32 im Shader.</span><span class="sxs-lookup"><span data-stu-id="893c6-420">
<strong>Note</strong> The shader gets SINT values, but if Direct3D 9 style integral floats are needed, SINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-421">D3DDECLTYPE_SHORT4</span><span class="sxs-lookup"><span data-stu-id="893c6-421">D3DDECLTYPE_SHORT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-422">DXGI_FORMAT_R16G16B16A16_SINT</span><span class="sxs-lookup"><span data-stu-id="893c6-422">DXGI_FORMAT_R16G16B16A16_SINT</span></span></p>
<div class="alert"><span data-ttu-id="893c6-423">
<strong>Hinweis:</strong>  der Shader ruft SINT-Werte ab, aber wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden, St. gerade konvertiert werden kann einfach in float32 im Shader.</span><span class="sxs-lookup"><span data-stu-id="893c6-423">
<strong>Note</strong> The shader gets SINT values, but if Direct3D 9 style integral floats are needed, SINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-424">D3DDECLTYPE_UBYTE4N</span><span class="sxs-lookup"><span data-stu-id="893c6-424">D3DDECLTYPE_UBYTE4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-425">DXGI_FORMAT_R8G8B8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-425">DXGI_FORMAT_R8G8B8A8_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-426">D3DDECLTYPE_SHORT2N</span><span class="sxs-lookup"><span data-stu-id="893c6-426">D3DDECLTYPE_SHORT2N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-427">DXGI_FORMAT_R16G16_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-427">DXGI_FORMAT_R16G16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-428">D3DDECLTYPE_SHORT4N</span><span class="sxs-lookup"><span data-stu-id="893c6-428">D3DDECLTYPE_SHORT4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-429">DXGI_FORMAT_R16G16B16A16_SNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-429">DXGI_FORMAT_R16G16B16A16_SNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-430">D3DDECLTYPE_USHORT2N</span><span class="sxs-lookup"><span data-stu-id="893c6-430">D3DDECLTYPE_USHORT2N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-431">DXGI_FORMAT_R16G16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-431">DXGI_FORMAT_R16G16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-432">D3DDECLTYPE_USHORT4N</span><span class="sxs-lookup"><span data-stu-id="893c6-432">D3DDECLTYPE_USHORT4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-433">DXGI_FORMAT_R16G16B16A16_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-433">DXGI_FORMAT_R16G16B16A16_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-434">D3DDECLTYPE_UDEC3</span><span class="sxs-lookup"><span data-stu-id="893c6-434">D3DDECLTYPE_UDEC3</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-435">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-435">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-436">D3DDECLTYPE_DEC3N</span><span class="sxs-lookup"><span data-stu-id="893c6-436">D3DDECLTYPE_DEC3N</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-437">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="893c6-437">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-438">D3DDECLTYPE_FLOAT16_2</span><span class="sxs-lookup"><span data-stu-id="893c6-438">D3DDECLTYPE_FLOAT16_2</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-439">DXGI_FORMAT_R16G16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-439">DXGI_FORMAT_R16G16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-440">D3DDECLTYPE_FLOAT16_4</span><span class="sxs-lookup"><span data-stu-id="893c6-440">D3DDECLTYPE_FLOAT16_4</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-441">DXGI_FORMAT_R16G16B16A16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="893c6-441">DXGI_FORMAT_R16G16B16A16_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="893c6-442">FourCC 'ATI1'</span><span class="sxs-lookup"><span data-stu-id="893c6-442">FourCC 'ATI1'</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-443">DXGI_FORMAT_BC4_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-443">DXGI_FORMAT_BC4_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-444">
<strong>Hinweis:</strong>  erfordert Funktionsebene 10.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="893c6-444">
<strong>Note</strong> Requires Feature Level 10.0 or later</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="893c6-445">FourCC 'ATI2'</span><span class="sxs-lookup"><span data-stu-id="893c6-445">FourCC 'ATI2'</span></span></p></td>
<td align="left"><p><span data-ttu-id="893c6-446">DXGI_FORMAT_BC5_UNORM</span><span class="sxs-lookup"><span data-stu-id="893c6-446">DXGI_FORMAT_BC5_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="893c6-447">
<strong>Hinweis:</strong>  erfordert Funktionsebene 10.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="893c6-447">
<strong>Note</strong> Requires Feature Level 10.0 or later</span></span>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

 

 




