---
title: Zuordnung von DirectX9-Funktionen zu DirectX11-APIs
description: Erfahren Sie, wie Sie die Features Ihres Direct3D9-Spiels mit Direct3D11 und der Universellen Windows-Plattform (UWP) verwenden können.
ms.assetid: 3aa8a114-4e47-ae0a-9447-88ba324377b8
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, DirectX 9, DirectX 11, Portierung
ms.localizationpriority: medium
ms.openlocfilehash: 56bb86706795e773d21e45263f640f9fc0aa596a
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8193162"
---
# <a name="map-directx-9-features-to-directx-11-apis"></a><span data-ttu-id="24fff-104">Zuordnung von DirectX9-Funktionen zu DirectX11-APIs</span><span class="sxs-lookup"><span data-stu-id="24fff-104">Map DirectX 9 features to DirectX 11 APIs</span></span>



**<span data-ttu-id="24fff-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="24fff-105">Summary</span></span>**

-   [<span data-ttu-id="24fff-106">Planen der DirectX-Portierung</span><span class="sxs-lookup"><span data-stu-id="24fff-106">Plan your DirectX port</span></span>](plan-your-directx-port.md)
-   [<span data-ttu-id="24fff-107">Wichtige Änderungen beim Wechsel von Direct3D9 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="24fff-107">Important changes from Direct3D 9 to Direct3D 11</span></span>](understand-direct3d-11-1-concepts.md)
-   <span data-ttu-id="24fff-108">Featurezuordnung</span><span class="sxs-lookup"><span data-stu-id="24fff-108">Feature mapping</span></span>


<span data-ttu-id="24fff-109">Erfahren Sie, wie die Features Ihres Direct3D9-Spiels zu Direct3D11 und zur Universellen Windows-Plattform (UWP) zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-109">Understand how the features your Direct3D 9 game uses will translate to Direct3D 11 and the Universal Windows Platform (UWP).</span></span>

## <a name="mapping-direct3d-9-to-directx-11-apis"></a><span data-ttu-id="24fff-110">Zuordnen von Direct3D9-Features zu DirectX11-APIs</span><span class="sxs-lookup"><span data-stu-id="24fff-110">Mapping Direct3D 9 to DirectX 11 APIs</span></span>


<span data-ttu-id="24fff-111">[Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) ist nach wie vor die Grundlage von DirectX-Grafiken, die API wurde seit DirectX 9 jedoch geändert:</span><span class="sxs-lookup"><span data-stu-id="24fff-111">[Direct3D](https://msdn.microsoft.com/library/windows/desktop/hh309466) is still the foundation of DirectX graphics, but the API has changed since DirectX 9:</span></span>

-   <span data-ttu-id="24fff-112">Zum Einrichten von Grafikadaptern wird die Microsoft DirectX Graphics Infrastructure (DXGI) verwendet.</span><span class="sxs-lookup"><span data-stu-id="24fff-112">Microsoft DirectX Graphics Infrastructure (DXGI) is used to set up graphics adapters.</span></span> <span data-ttu-id="24fff-113">Verwenden Sie [DXGI](https://msdn.microsoft.com/library/windows/desktop/hh404534) zum Auswählen von Pufferformaten, Erstellen von Swapchains, Darstellen von Frames und Erstellen freigegebener Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="24fff-113">Use [DXGI](https://msdn.microsoft.com/library/windows/desktop/hh404534) to select buffer formats, create swap chains, present frames, and create shared resources.</span></span> <span data-ttu-id="24fff-114">Siehe [Übersicht über DXGI](https://msdn.microsoft.com/library/windows/desktop/bb205075).</span><span class="sxs-lookup"><span data-stu-id="24fff-114">See [DXGI Overview](https://msdn.microsoft.com/library/windows/desktop/bb205075).</span></span>
-   <span data-ttu-id="24fff-115">Ein Direct3D-Gerätekontext wird zum Festlegen des Pipelinestatus und Generieren von Renderbefehlen verwendet.</span><span class="sxs-lookup"><span data-stu-id="24fff-115">A Direct3D device context is used to set pipeline state and generate rendering commands.</span></span> <span data-ttu-id="24fff-116">In den meisten unserer Beispiele wird ein unmittelbarer Kontext verwendet, um direkt auf dem Gerät zu rendern. Direct3D11 unterstützt auch das Multithread-Rendering, wobei dann verzögerte Kontexte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-116">Most of our samples use an immediate context to render directly to the device; Direct3D 11 also supports multithreaded rendering, in which case deferred contexts are used.</span></span> <span data-ttu-id="24fff-117">Siehe [Einführung in ein Gerät in Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476880).</span><span class="sxs-lookup"><span data-stu-id="24fff-117">See [Introduction to a Device in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476880).</span></span>
-   <span data-ttu-id="24fff-118">Einige Funktionen sind veraltet und nicht mehr verfügbar. Zu beachten ist insbesondere, dass es die Pipeline mit fester Funktion nicht mehr gibt.</span><span class="sxs-lookup"><span data-stu-id="24fff-118">Some features have been deprecated, most notably the fixed function pipeline.</span></span> <span data-ttu-id="24fff-119">Siehe [Veraltete Funktionen](https://msdn.microsoft.com/library/windows/desktop/cc308047).</span><span class="sxs-lookup"><span data-stu-id="24fff-119">See [Deprecated Features](https://msdn.microsoft.com/library/windows/desktop/cc308047).</span></span>

<span data-ttu-id="24fff-120">Eine vollständige Liste der Direct3D11-Funktionen finden Sie unter [Features von Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476342) und [Features von Direct3D11.1](https://msdn.microsoft.com/library/windows/desktop/hh404562).</span><span class="sxs-lookup"><span data-stu-id="24fff-120">For a full list of Direct3D 11 features, see [Direct3D 11 Features](https://msdn.microsoft.com/library/windows/desktop/ff476342) and [Direct3D 11 Features](https://msdn.microsoft.com/library/windows/desktop/hh404562).</span></span>

## <a name="moving-from-direct2d-9-to-direct2d-11"></a><span data-ttu-id="24fff-121">Umstellung von Direct2D9 auf Direct2D11</span><span class="sxs-lookup"><span data-stu-id="24fff-121">Moving from Direct2D 9 to Direct2D 11</span></span>


<span data-ttu-id="24fff-122">[Direct2D (Windows)](https://msdn.microsoft.com/library/windows/desktop/dd370990) ist weiterhin ein wichtiger Bestandteil von DirectX-Grafiken und Windows.</span><span class="sxs-lookup"><span data-stu-id="24fff-122">[Direct2D (Windows)](https://msdn.microsoft.com/library/windows/desktop/dd370990) is still an important part of DirectX graphics and Windows.</span></span> <span data-ttu-id="24fff-123">Sie können mit Direct2D weiterhin 2D-Spiele und Direct3D-basierte Überlagerungen (HUDs) zeichnen.</span><span class="sxs-lookup"><span data-stu-id="24fff-123">You can still use Direct2D to draw 2D games, and to draw overlays (HUDs) on top of Direct3D.</span></span>

<span data-ttu-id="24fff-124">Direct2D baut auf Direct3D auf. 2D-Spiele können mit beiden APIs implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-124">Direct2D runs on top of Direct3D; 2D games can be implemented using either API.</span></span> <span data-ttu-id="24fff-125">Ein mit Direct3D implementiertes 2D-Spiel kann z.B. die orthografische Projektion verwenden, Z-Werte zum Steuern der Zeichnungsreihenfolge von Grundtypen festlegen und mit Pixelshadern Spezialeffekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="24fff-125">For example, a 2D game implemented using Direct3D can use orthographic projection, set Z-values to control the drawing order of primitives, and use pixel shaders to add special effects.</span></span>

<span data-ttu-id="24fff-126">Da Direct2D auf Direct3D basiert, verwendet es ebenfalls DXGI und Gerätekontexte.</span><span class="sxs-lookup"><span data-stu-id="24fff-126">Since Direct2D is based on Direct3D it also uses DXGI and device contexts.</span></span> <span data-ttu-id="24fff-127">Siehe [Übersicht über die Direct2D-API](https://msdn.microsoft.com/library/windows/desktop/dd317121).</span><span class="sxs-lookup"><span data-stu-id="24fff-127">See [Direct2D API Overview](https://msdn.microsoft.com/library/windows/desktop/dd317121).</span></span>

<span data-ttu-id="24fff-128">Die [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038)-API bietet Unterstützung für formatierten Text mit Direct2D.</span><span class="sxs-lookup"><span data-stu-id="24fff-128">The [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) API adds support for formatted text using Direct2D.</span></span> <span data-ttu-id="24fff-129">Siehe [Einführung in DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd371554).</span><span class="sxs-lookup"><span data-stu-id="24fff-129">See [Introducing DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd371554).</span></span>

## <a name="replace-deprecated-helper-libraries"></a><span data-ttu-id="24fff-130">Ersetzen veralteter Hilfsbibliotheken</span><span class="sxs-lookup"><span data-stu-id="24fff-130">Replace deprecated helper libraries</span></span>


<span data-ttu-id="24fff-131">D3DX und DXUT sind veraltet und können nicht in UWP-Spielen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-131">D3DX and DXUT are deprecated and cannot be used by UWP games.</span></span> <span data-ttu-id="24fff-132">Von diesen Hilfsbibliotheken wurden Ressourcen für Aufgaben wie das Laden von Texturen und Gittern bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="24fff-132">These helper libraries provided resources for tasks such as texture loading and mesh loading.</span></span>

-   <span data-ttu-id="24fff-133">In der exemplarischen Vorgehensweise [Einfache Portierung von Direct3D9 zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) wird gezeigt, wie ein Fenster eingerichtet, Direct3D initialisiert und einfaches 3D-Rendering durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="24fff-133">The [Simple port from Direct3D 9 to UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough demonstrates how to set up a window, initialize Direct3D, and do basic 3D rendering.</span></span>
-   <span data-ttu-id="24fff-134">In der exemplarischen Vorgehensweise [Erstellen eines einfachen UWP-Spiels mit DirectX](tutorial--create-your-first-uwp-directx-game.md) werden allgemeine Aufgaben der Spielprogrammierung erläutert, u.a. Grafiken, Laden von Dateien, UI, Steuerelemente und Sound.</span><span class="sxs-lookup"><span data-stu-id="24fff-134">The [Simple UWP game with DirectX](tutorial--create-your-first-uwp-directx-game.md) walkthrough demonstrates common game programming tasks including graphics, loading files, UI, controls, and sound.</span></span>
-   <span data-ttu-id="24fff-135">Das Communityprojekt [DirectX-Toolkit](http://go.microsoft.com/fwlink/p/?LinkID=248929) bietet Hilfsklassen zur Verwendung mit Direct3D11 und UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="24fff-135">The [DirectX Tool Kit](http://go.microsoft.com/fwlink/p/?LinkID=248929) community project offers helper classes for use with Direct3D 11 and UWP apps.</span></span>

## <a name="move-shader-programs-from-fx-to-hlsl"></a><span data-ttu-id="24fff-136">Umstellung von Shaderprogrammen von FX auf HLSL</span><span class="sxs-lookup"><span data-stu-id="24fff-136">Move shader programs from FX to HLSL</span></span>


<span data-ttu-id="24fff-137">Die D3DX-Hilfsprogrammbibliothek (D3DX9, D3DX10 und D3DX11), einschließlich Effects, ist veraltet und für UWP nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="24fff-137">The D3DX utility library (D3DX 9, D3DX 10, and D3DX 11), including Effects, is deprecated for UWP.</span></span> <span data-ttu-id="24fff-138">Alle DirectX-Spiele für UWP steuern die Grafikpipeline mit [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561) ohne Effects.</span><span class="sxs-lookup"><span data-stu-id="24fff-138">All DirectX games for UWP drive the graphics pipeline using [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561) without Effects.</span></span>

<span data-ttu-id="24fff-139">Visual Studio verwendet FXC weiterhin im Hintergrund zum Kompilieren von Shaderobjekten.</span><span class="sxs-lookup"><span data-stu-id="24fff-139">Visual Studio still uses FXC under the hood to compile shader objects.</span></span> <span data-ttu-id="24fff-140">UWP-Spielshader werden vorab kompiliert.</span><span class="sxs-lookup"><span data-stu-id="24fff-140">UWP game shaders are compiled ahead of time.</span></span> <span data-ttu-id="24fff-141">Der Bytecode wird zur Laufzeit geladen. Anschließend wird jede Shaderressource während des entsprechenden Renderingdurchgangs an die Grafikpipeline gebunden.</span><span class="sxs-lookup"><span data-stu-id="24fff-141">The bytecode is loaded at runtime, then each shader resource is bound to the graphics pipeline during the appropriate rendering pass.</span></span> <span data-ttu-id="24fff-142">Shader sollten in eigene separate HLSL-Dateien verschoben werden, und Renderingtechniken sollten im C++-Code implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-142">Shaders should be moved to their own separate .HLSL files and rendering techniques should be implemented in your C++ code.</span></span>

<span data-ttu-id="24fff-143">Einen kurzen Überblick über das Laden von Shaderressourcen finden Sie unter [Einfache Portierung von Direct3D9 zu UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span><span class="sxs-lookup"><span data-stu-id="24fff-143">For a quick look at loading shader resources see [Simple port from Direct3D 9 to UWP](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span></span>

<span data-ttu-id="24fff-144">In Direct3D11 wurde Shadermodell5 eingeführt, das die Direct3D-Funktionsebene11\_0 (oder höher) erfordert.</span><span class="sxs-lookup"><span data-stu-id="24fff-144">Direct3D 11 introduced Shader Model 5, which requires Direct3D feature level 11\_0 (or above).</span></span> <span data-ttu-id="24fff-145">Siehe [Funktionen von HLSL-Shadermodell5 für Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff471419).</span><span class="sxs-lookup"><span data-stu-id="24fff-145">See [HLSL Shader Model 5 Features for Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff471419).</span></span>

## <a name="replace-xnamath-and-d3dxmath"></a><span data-ttu-id="24fff-146">Ersetzen von XNAMath und D3DXMath</span><span class="sxs-lookup"><span data-stu-id="24fff-146">Replace XNAMath and D3DXMath</span></span>


<span data-ttu-id="24fff-147">Code mit XNAMath (oder D3DXMath) sollte zu [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) migriert werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-147">Code using XNAMath (or D3DXMath) should be migrated to [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833).</span></span> <span data-ttu-id="24fff-148">DirectXMath enthält Typen, die zwischen x86, x64 und ARM portierbar sind.</span><span class="sxs-lookup"><span data-stu-id="24fff-148">DirectXMath includes types that are portable across x86, x64, and ARM.</span></span> <span data-ttu-id="24fff-149">Siehe [Codemigration von der XNAMath-Bibliothek](https://msdn.microsoft.com/library/windows/desktop/ee418730).</span><span class="sxs-lookup"><span data-stu-id="24fff-149">See [Code Migration from the XNA Math Library](https://msdn.microsoft.com/library/windows/desktop/ee418730).</span></span>

<span data-ttu-id="24fff-150">Beachten Sie, dass sich Float-Typen von DirectXMath zur Verwendung mit Shadern eignen.</span><span class="sxs-lookup"><span data-stu-id="24fff-150">Note that DirectXMath float types are convenient for use with shaders.</span></span> <span data-ttu-id="24fff-151">Mit [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) und [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) können z.B. auf einfache Weise Daten für Konstantenpuffer ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-151">For example [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) and [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) conveniently align data for constant buffers.</span></span>

## <a name="replace-directsound-with-xaudio2-and-background-audio"></a><span data-ttu-id="24fff-152">Ersetzen von DirectSound durch XAudio2 (und Hintergrundaudio)</span><span class="sxs-lookup"><span data-stu-id="24fff-152">Replace DirectSound with XAudio2 (and background audio)</span></span>


<span data-ttu-id="24fff-153">DirectSound wird für UWP nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="24fff-153">DirectSound is not supported for UWP:</span></span>

-   <span data-ttu-id="24fff-154">Verwenden Sie [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049), um Ihrem Spiel Soundeffekte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="24fff-154">Use [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049) to add sound effects to your game.</span></span>

##  <a name="replace-directinput-with-xinput-and-uwp-apis"></a><span data-ttu-id="24fff-155">Ersetzen von DirectInput durch XInput und UWP-APIs</span><span class="sxs-lookup"><span data-stu-id="24fff-155">Replace DirectInput with XInput and UWP APIs</span></span>


<span data-ttu-id="24fff-156">DirectInput wird für UWP nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="24fff-156">DirectInput is not supported for UWP:</span></span>

-   <span data-ttu-id="24fff-157">Verwenden Sie [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Eingabeereignisrückrufe für Maus-, Tastatur- und Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="24fff-157">Use [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) input event callbacks for mouse, keyboard, and touch input.</span></span>
-   <span data-ttu-id="24fff-158">Verwenden Sie [XInput](https://msdn.microsoft.com/library/windows/desktop/ee417001)1.4 zur Unterstützung von Gamecontrollern (und Gamecontroller-Headsets).</span><span class="sxs-lookup"><span data-stu-id="24fff-158">Use [XInput](https://msdn.microsoft.com/library/windows/desktop/ee417001) 1.4 for game controller support (and game controller headset support).</span></span> <span data-ttu-id="24fff-159">Wenn Sie eine freigegebene Codebasis für Desktop und UWP verwenden, finden Sie unter [XInput-Versionen](https://msdn.microsoft.com/library/windows/desktop/hh405051) Informationen zur Abwärtskompatibilität.</span><span class="sxs-lookup"><span data-stu-id="24fff-159">If you are using a shared code base for desktop and UWP, see [XInput Versions](https://msdn.microsoft.com/library/windows/desktop/hh405051) for information on backwards compatibility.</span></span>
-   <span data-ttu-id="24fff-160">Registrieren Sie [**EdgeGesture**](https://msdn.microsoft.com/library/windows/apps/hh701600)-Ereignisse, wenn die App-Leiste in Ihrem Spiel verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="24fff-160">Register for [**EdgeGesture**](https://msdn.microsoft.com/library/windows/apps/hh701600) events if your game needs to use the app bar.</span></span>

## <a name="use-microsoft-media-foundation-instead-of-directshow"></a><span data-ttu-id="24fff-161">Verwenden von Microsoft Media Foundation anstelle von DirectShow</span><span class="sxs-lookup"><span data-stu-id="24fff-161">Use Microsoft Media Foundation instead of DirectShow</span></span>


<span data-ttu-id="24fff-162">DirectShow ist nicht mehr in der DirectX-API (oder der Windows-API) enthalten.</span><span class="sxs-lookup"><span data-stu-id="24fff-162">DirectShow is no longer part of the DirectX API (or the Windows API).</span></span> <span data-ttu-id="24fff-163">[Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) stellt Videoinhalte mithilfe von freigegebenen Oberflächen für Direct3D bereit.</span><span class="sxs-lookup"><span data-stu-id="24fff-163">[Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) provides video content to Direct3D using shared surfaces.</span></span> <span data-ttu-id="24fff-164">Siehe [Direct3D11-Video-APIs](https://msdn.microsoft.com/library/windows/desktop/hh447677).</span><span class="sxs-lookup"><span data-stu-id="24fff-164">See [Direct3D 11 Video APIs](https://msdn.microsoft.com/library/windows/desktop/hh447677).</span></span>

## <a name="replace-directplay-with-networking-code"></a><span data-ttu-id="24fff-165">Ersetzen von DirectPlay durch Netzwerkcode</span><span class="sxs-lookup"><span data-stu-id="24fff-165">Replace DirectPlay with networking code</span></span>


<span data-ttu-id="24fff-166">Microsoft DirectPlay ist veraltet und nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="24fff-166">Microsoft DirectPlay has been deprecated.</span></span> <span data-ttu-id="24fff-167">Falls Ihr Spiel Netzwerkdienste verwendet, müssen Sie Netzwerkcode bereitstellen, der den UWP-Anforderungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="24fff-167">If your game uses network services, you need to provide networking code that complies with UWP requirements.</span></span> <span data-ttu-id="24fff-168">Verwenden Sie die folgenden APIs:</span><span class="sxs-lookup"><span data-stu-id="24fff-168">Use the following APIs:</span></span>

-   [<span data-ttu-id="24fff-169">Win32 und COM für UWP-Apps (Netzwerk) (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-169">Win32 and COM for UWP apps (networking) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/br205759)
-   [**<span data-ttu-id="24fff-170">Windows.Networking-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-170">Windows.Networking namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207124)
-   [**<span data-ttu-id="24fff-171">Windows.Networking.Sockets-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-171">Windows.Networking.Sockets namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br226960)
-   [**<span data-ttu-id="24fff-172">Windows.Networking.Connectivity-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-172">Windows.Networking.Connectivity namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br207308)
-   [**<span data-ttu-id="24fff-173">Windows.ApplicationModel.Background-Namespace (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-173">Windows.ApplicationModel.Background namespace (Windows)</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)

<span data-ttu-id="24fff-174">In den folgenden Artikeln finden Sie Informationen zum Hinzufügen von Netzwerkfunktionen und Deklarieren der Netzwerkunterstützung im Paketmanifest Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="24fff-174">The following articles help you add networking features and declare support for networking in your app's package manifest.</span></span>

-   [<span data-ttu-id="24fff-175">Verbinden mit Sockets (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-175">Connecting with sockets (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452976)
-   [<span data-ttu-id="24fff-176">Verbinden mit WebSockets (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-176">Connecting with WebSockets (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh994396)
-   [<span data-ttu-id="24fff-177">Herstellen einer Verbindung mit Webdiensten (UWP-Apps mit C#/VB/C++ und XAML) (Windows)</span><span class="sxs-lookup"><span data-stu-id="24fff-177">Connecting to web services (UWP apps using C#/VB/C++ and XAML) (Windows)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh761504)
-   [<span data-ttu-id="24fff-178">Vernetzungsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="24fff-178">Networking basics</span></span>](https://msdn.microsoft.com/library/windows/apps/mt280233)

<span data-ttu-id="24fff-179">Beachten Sie, dass alle UWP-Apps (einschließlich Spiele) bestimmte Hintergrundaufgaben verwenden, um die Verbindung aufrechtzuerhalten, während die App angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="24fff-179">Note that all UWP apps (including games) use specific types of background tasks to maintain connectivity while the app is suspended.</span></span> <span data-ttu-id="24fff-180">Wenn Ihr Spiel den Verbindungsstatus aufrechterhalten muss, während es angehalten ist, gehen Sie wie unter [Grundlagen zum Netzwerk](https://msdn.microsoft.com/library/windows/apps/mt280233) beschrieben vor.</span><span class="sxs-lookup"><span data-stu-id="24fff-180">If your game needs to maintain connection state while suspended see [Networking basics](https://msdn.microsoft.com/library/windows/apps/mt280233).</span></span>

## <a name="function-mapping"></a><span data-ttu-id="24fff-181">Funktionszuordnung</span><span class="sxs-lookup"><span data-stu-id="24fff-181">Function mapping</span></span>


<span data-ttu-id="24fff-182">Ziehen Sie beim Konvertieren von Code von Direct3D9 in Direct3D11 die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="24fff-182">Use the following table to help convert code from Direct3D 9 to Direct3D 11.</span></span> <span data-ttu-id="24fff-183">Diese Informationen können Ihnen auch die Unterscheidung zwischen Gerät und Gerätekontext erleichtern.</span><span class="sxs-lookup"><span data-stu-id="24fff-183">This can also help distinguish between the device and device context.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="24fff-184">Direct3D9</span><span class="sxs-lookup"><span data-stu-id="24fff-184">Direct3D9</span></span></th>
<th align="left"><span data-ttu-id="24fff-185">Direct3D11-Entsprechung</span><span class="sxs-lookup"><span data-stu-id="24fff-185">Direct3D 11 Equivalent</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174336"><span data-ttu-id="24fff-186">IDirect3DDevice9</span><span class="sxs-lookup"><span data-stu-id="24fff-186">IDirect3DDevice9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280493"><span data-ttu-id="24fff-187">ID3D11Device2</span><span class="sxs-lookup"><span data-stu-id="24fff-187">ID3D11Device2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280498"><span data-ttu-id="24fff-188">ID3D11DeviceContext2</span><span class="sxs-lookup"><span data-stu-id="24fff-188">ID3D11DeviceContext2</span></span></a></p>
<p><span data-ttu-id="24fff-189">Die Grafikpipelinestufen werden unter <a href="https://msdn.microsoft.com/library/windows/desktop/ff476882">Grafikpipeline</a> erläutert.</span><span class="sxs-lookup"><span data-stu-id="24fff-189">The graphics pipeline stages are described in <a href="https://msdn.microsoft.com/library/windows/desktop/ff476882">Graphics Pipeline</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174300"><span data-ttu-id="24fff-190">IDirect3D9</span><span class="sxs-lookup"><span data-stu-id="24fff-190">IDirect3D9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404556"><span data-ttu-id="24fff-191">IDXGIFactory2</span><span class="sxs-lookup"><span data-stu-id="24fff-191">IDXGIFactory2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404537"><span data-ttu-id="24fff-192">IDXGIAdapter2</span><span class="sxs-lookup"><span data-stu-id="24fff-192">IDXGIAdapter2</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/dn280345"><span data-ttu-id="24fff-193">IDXGIDevice3</span><span class="sxs-lookup"><span data-stu-id="24fff-193">IDXGIDevice3</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174423"><span data-ttu-id="24fff-194">IDirect3DDevice9::Present</span><span class="sxs-lookup"><span data-stu-id="24fff-194">IDirect3DDevice9::Present</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797"><span data-ttu-id="24fff-195">IDXGISwapChain1::Present1</span><span class="sxs-lookup"><span data-stu-id="24fff-195">IDXGISwapChain1::Present1</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174472"><span data-ttu-id="24fff-196">IDirect3DDevice9::TestCooperativeLevel</span><span class="sxs-lookup"><span data-stu-id="24fff-196">IDirect3DDevice9::TestCooperativeLevel</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-197">Rufen Sie <a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1:: Present1</a> mit der festgelegten DXGI_PRESENT_TEST-Kennung auf.</span><span class="sxs-lookup"><span data-stu-id="24fff-197">Call <a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> with the DXGI_PRESENT_TEST flag set.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174322"><span data-ttu-id="24fff-198">IDirect3DBaseTexture9</span><span class="sxs-lookup"><span data-stu-id="24fff-198">IDirect3DBaseTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205909"><span data-ttu-id="24fff-199">IDirect3DTexture9</span><span class="sxs-lookup"><span data-stu-id="24fff-199">IDirect3DTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174329"><span data-ttu-id="24fff-200">IDirect3DCubeTexture9</span><span class="sxs-lookup"><span data-stu-id="24fff-200">IDirect3DCubeTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205941"><span data-ttu-id="24fff-201">IDirect3DVolumeTexture9</span><span class="sxs-lookup"><span data-stu-id="24fff-201">IDirect3DVolumeTexture9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205865"><span data-ttu-id="24fff-202">IDirect3DIndexBuffer9</span><span class="sxs-lookup"><span data-stu-id="24fff-202">IDirect3DIndexBuffer9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205915"><span data-ttu-id="24fff-203">IDirect3DVertexBuffer9</span><span class="sxs-lookup"><span data-stu-id="24fff-203">IDirect3DVertexBuffer9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476351"><span data-ttu-id="24fff-204">ID3D11Buffer</span><span class="sxs-lookup"><span data-stu-id="24fff-204">ID3D11Buffer</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476633"><span data-ttu-id="24fff-205">ID3D11Texture1D</span><span class="sxs-lookup"><span data-stu-id="24fff-205">ID3D11Texture1D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476635"><span data-ttu-id="24fff-206">ID3D11Texture2D</span><span class="sxs-lookup"><span data-stu-id="24fff-206">ID3D11Texture2D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476637"><span data-ttu-id="24fff-207">ID3D11Texture3D</span><span class="sxs-lookup"><span data-stu-id="24fff-207">ID3D11Texture3D</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476628"><span data-ttu-id="24fff-208">ID3D11ShaderResourceView</span><span class="sxs-lookup"><span data-stu-id="24fff-208">ID3D11ShaderResourceView</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476582"><span data-ttu-id="24fff-209">ID3D11RenderTargetView</span><span class="sxs-lookup"><span data-stu-id="24fff-209">ID3D11RenderTargetView</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476377"><span data-ttu-id="24fff-210">ID3D11DepthStencilView</span><span class="sxs-lookup"><span data-stu-id="24fff-210">ID3D11DepthStencilView</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205922"><span data-ttu-id="24fff-211">IDirect3DVertexShader9</span><span class="sxs-lookup"><span data-stu-id="24fff-211">IDirect3DVertexShader9</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205869"><span data-ttu-id="24fff-212">IDirect3DPixelShader9</span><span class="sxs-lookup"><span data-stu-id="24fff-212">IDirect3DPixelShader9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476641"><span data-ttu-id="24fff-213">ID3D11VertexShader</span><span class="sxs-lookup"><span data-stu-id="24fff-213">ID3D11VertexShader</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476576"><span data-ttu-id="24fff-214">ID3D11PixelShader</span><span class="sxs-lookup"><span data-stu-id="24fff-214">ID3D11PixelShader</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205919"><span data-ttu-id="24fff-215">IDirect3DVertexDeclaration9</span><span class="sxs-lookup"><span data-stu-id="24fff-215">IDirect3DVertexDeclaration9</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476575"><span data-ttu-id="24fff-216">ID3D11InputLayout</span><span class="sxs-lookup"><span data-stu-id="24fff-216">ID3D11InputLayout</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205805"><span data-ttu-id="24fff-217">IDirect3DDevice9::SetRenderState</span><span class="sxs-lookup"><span data-stu-id="24fff-217">IDirect3DDevice9::SetRenderState</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205806"><span data-ttu-id="24fff-218">IDirect3DDevice9::SetSamplerState</span><span class="sxs-lookup"><span data-stu-id="24fff-218">IDirect3DDevice9::SetSamplerState</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/hh404571"><span data-ttu-id="24fff-219">ID3D11BlendState1</span><span class="sxs-lookup"><span data-stu-id="24fff-219">ID3D11BlendState1</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476375"><span data-ttu-id="24fff-220">ID3D11DepthStencilState</span><span class="sxs-lookup"><span data-stu-id="24fff-220">ID3D11DepthStencilState</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/hh446828"><span data-ttu-id="24fff-221">ID3D11RasterizerState1</span><span class="sxs-lookup"><span data-stu-id="24fff-221">ID3D11RasterizerState1</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476588"><span data-ttu-id="24fff-222">ID3D11SamplerState</span><span class="sxs-lookup"><span data-stu-id="24fff-222">ID3D11SamplerState</span></span></a></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174369"><span data-ttu-id="24fff-223">IDirect3DDevice9::DrawIndexedPrimitive</span><span class="sxs-lookup"><span data-stu-id="24fff-223">IDirect3DDevice9::DrawIndexedPrimitive</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174371"><span data-ttu-id="24fff-224">IDirect3DDevice9::DrawPrimitive</span><span class="sxs-lookup"><span data-stu-id="24fff-224">IDirect3DDevice9::DrawPrimitive</span></span></a></p></td>
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476407"><span data-ttu-id="24fff-225">ID3D11DeviceContext::Draw</span><span class="sxs-lookup"><span data-stu-id="24fff-225">ID3D11DeviceContext::Draw</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/ff476409"><span data-ttu-id="24fff-226">ID3D11DeviceContext::DrawIndexed</span><span class="sxs-lookup"><span data-stu-id="24fff-226">ID3D11DeviceContext::DrawIndexed</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173566"><span data-ttu-id="24fff-227">ID3D11DeviceContext::DrawIndexedInstanced</span><span class="sxs-lookup"><span data-stu-id="24fff-227">ID3D11DeviceContext::DrawIndexedInstanced</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173567"><span data-ttu-id="24fff-228">ID3D11DeviceContext::DrawInstanced</span><span class="sxs-lookup"><span data-stu-id="24fff-228">ID3D11DeviceContext::DrawInstanced</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173590"><span data-ttu-id="24fff-229">ID3D11DeviceContext::IASetPrimitiveTopology</span><span class="sxs-lookup"><span data-stu-id="24fff-229">ID3D11DeviceContext::IASetPrimitiveTopology</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb173564"><span data-ttu-id="24fff-230">ID3D11DeviceContext::DrawAuto</span><span class="sxs-lookup"><span data-stu-id="24fff-230">ID3D11DeviceContext::DrawAuto</span></span></a></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174350"><span data-ttu-id="24fff-231">IDirect3DDevice9::BeginScene</span><span class="sxs-lookup"><span data-stu-id="24fff-231">IDirect3DDevice9::BeginScene</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174375"><span data-ttu-id="24fff-232">IDirect3DDevice9::EndScene</span><span class="sxs-lookup"><span data-stu-id="24fff-232">IDirect3DDevice9::EndScene</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174372"><span data-ttu-id="24fff-233">IDirect3DDevice9::DrawPrimitiveUP</span><span class="sxs-lookup"><span data-stu-id="24fff-233">IDirect3DDevice9::DrawPrimitiveUP</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174370"><span data-ttu-id="24fff-234">IDirect3DDevice9::DrawIndexedPrimitiveUP</span><span class="sxs-lookup"><span data-stu-id="24fff-234">IDirect3DDevice9::DrawIndexedPrimitiveUP</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-235">Kein direktes Äquivalent</span><span class="sxs-lookup"><span data-stu-id="24fff-235">No direct equivalent</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174470"><span data-ttu-id="24fff-236">IDirect3DDevice9::ShowCursor</span><span class="sxs-lookup"><span data-stu-id="24fff-236">IDirect3DDevice9::ShowCursor</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174429"><span data-ttu-id="24fff-237">IDirect3DDevice9::SetCursorPosition</span><span class="sxs-lookup"><span data-stu-id="24fff-237">IDirect3DDevice9::SetCursorPosition</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174430"><span data-ttu-id="24fff-238">IDirect3DDevice9::SetCursorProperties</span><span class="sxs-lookup"><span data-stu-id="24fff-238">IDirect3DDevice9::SetCursorProperties</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-239">Verwenden Sie standardmäßige Cursor-APIs.</span><span class="sxs-lookup"><span data-stu-id="24fff-239">Use standard cursor APIs.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174425"><span data-ttu-id="24fff-240">IDirect3DDevice9::Reset</span><span class="sxs-lookup"><span data-stu-id="24fff-240">IDirect3DDevice9::Reset</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-241">"LOST device" und POOL_MANAGED sind nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="24fff-241">LOST device and POOL_MANAGED no longer exist.</span></span> <span data-ttu-id="24fff-242"><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> kann mit einem <a href="https://msdn.microsoft.com/library/windows/desktop/bb509553">DXGI_ERROR_DEVICE_REMOVED</a> Rückgabewert fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="24fff-242"><a href="https://msdn.microsoft.com/library/windows/desktop/hh446797">IDXGISwapChain1::Present1</a> can fail with a <a href="https://msdn.microsoft.com/library/windows/desktop/bb509553">DXGI_ERROR_DEVICE_REMOVED</a> return value.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174373"><span data-ttu-id="24fff-243">IDirect3DDevice9:DrawRectPatch</span><span class="sxs-lookup"><span data-stu-id="24fff-243">IDirect3DDevice9:DrawRectPatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174374"><span data-ttu-id="24fff-244">IDirect3DDevice9:DrawTriPatch</span><span class="sxs-lookup"><span data-stu-id="24fff-244">IDirect3DDevice9:DrawTriPatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174421"><span data-ttu-id="24fff-245">IDirect3DDevice9:LightEnable</span><span class="sxs-lookup"><span data-stu-id="24fff-245">IDirect3DDevice9:LightEnable</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174422"><span data-ttu-id="24fff-246">IDirect3DDevice9:MultiplyTransform</span><span class="sxs-lookup"><span data-stu-id="24fff-246">IDirect3DDevice9:MultiplyTransform</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205798"><span data-ttu-id="24fff-247">IDirect3DDevice9:SetLight</span><span class="sxs-lookup"><span data-stu-id="24fff-247">IDirect3DDevice9:SetLight</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174437"><span data-ttu-id="24fff-248">IDirect3DDevice9:SetMaterial</span><span class="sxs-lookup"><span data-stu-id="24fff-248">IDirect3DDevice9:SetMaterial</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174438"><span data-ttu-id="24fff-249">IDirect3DDevice9:SetNPatchMode</span><span class="sxs-lookup"><span data-stu-id="24fff-249">IDirect3DDevice9:SetNPatchMode</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174463"><span data-ttu-id="24fff-250">IDirect3DDevice9:SetTransform</span><span class="sxs-lookup"><span data-stu-id="24fff-250">IDirect3DDevice9:SetTransform</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174433"><span data-ttu-id="24fff-251">IDirect3DDevice9:SetFVF</span><span class="sxs-lookup"><span data-stu-id="24fff-251">IDirect3DDevice9:SetFVF</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174462"><span data-ttu-id="24fff-252">IDirect3DDevice9:SetTextureStageState</span><span class="sxs-lookup"><span data-stu-id="24fff-252">IDirect3DDevice9:SetTextureStageState</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-253">Die Pipeline mit fester Funktion ist veraltet und nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="24fff-253">The fixed-function pipeline has been deprecated.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174308"><span data-ttu-id="24fff-254">IDirect3DDevice9:CheckDepthStencilMatch</span><span class="sxs-lookup"><span data-stu-id="24fff-254">IDirect3DDevice9:CheckDepthStencilMatch</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174309"><span data-ttu-id="24fff-255">IDirect3DDevice9:CheckDeviceFormat</span><span class="sxs-lookup"><span data-stu-id="24fff-255">IDirect3DDevice9:CheckDeviceFormat</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb174320"><span data-ttu-id="24fff-256">IDirect3DDevice9:GetDeviceCaps</span><span class="sxs-lookup"><span data-stu-id="24fff-256">IDirect3DDevice9:GetDeviceCaps</span></span></a></p>
<p><a href="https://msdn.microsoft.com/library/windows/desktop/bb205859"><span data-ttu-id="24fff-257">IDirect3DDevice9:ValidateDevice</span><span class="sxs-lookup"><span data-stu-id="24fff-257">IDirect3DDevice9:ValidateDevice</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="24fff-258">Funktionsbits werden durch Funktionsebenen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="24fff-258">Capability bits are replaced with feature levels.</span></span> <span data-ttu-id="24fff-259">Nur einige wenige Format- und Funktionsverwendungsfälle sind für alle Funktionsebenen optional.</span><span class="sxs-lookup"><span data-stu-id="24fff-259">Only a few format and feature usage cases are optional for any given feature level.</span></span> <span data-ttu-id="24fff-260">Diese können mit <a href="https://msdn.microsoft.com/library/windows/desktop/ff476497">ID3D11Device::CheckFeatureSupport</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/bb173536">ID3D11Device::CheckFormatSupport</a> überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-260">These can be checked with <a href="https://msdn.microsoft.com/library/windows/desktop/ff476497">ID3D11Device::CheckFeatureSupport</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/bb173536">ID3D11Device::CheckFormatSupport</a>.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="surface-format-mapping"></a><span data-ttu-id="24fff-261">Oberflächenformatzuordnung</span><span class="sxs-lookup"><span data-stu-id="24fff-261">Surface format mapping</span></span>


<span data-ttu-id="24fff-262">Ziehen Sie beim Konvertieren von Direct3D9-Formaten in DXGI-Formate die folgende Tabelle heran.</span><span class="sxs-lookup"><span data-stu-id="24fff-262">Use the following table to convert Direct3D 9 formats into DXGI formats.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="24fff-263">Direct3D9-Format</span><span class="sxs-lookup"><span data-stu-id="24fff-263">Direct3D 9 Format</span></span></th>
<th align="left"><span data-ttu-id="24fff-264">Direct3D11-Format</span><span class="sxs-lookup"><span data-stu-id="24fff-264">Direct3D 11 Format</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-265">D3DFMT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="24fff-265">D3DFMT_UNKNOWN</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-266">DXGI_FORMAT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="24fff-266">DXGI_FORMAT_UNKNOWN</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-267">D3DFMT_R8G8B8</span><span class="sxs-lookup"><span data-stu-id="24fff-267">D3DFMT_R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-268">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-268">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-269">D3DFMT_A8R8G8B8</span><span class="sxs-lookup"><span data-stu-id="24fff-269">D3DFMT_A8R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-270">DXGI_FORMAT_B8G8R8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-270">DXGI_FORMAT_B8G8R8A8_UNORM</span></span></p>
<p><span data-ttu-id="24fff-271">DXGI_FORMAT_B8G8R8A8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-271">DXGI_FORMAT_B8G8R8A8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-272">D3DFMT_X8R8G8B8</span><span class="sxs-lookup"><span data-stu-id="24fff-272">D3DFMT_X8R8G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-273">DXGI_FORMAT_B8G8R8X8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-273">DXGI_FORMAT_B8G8R8X8_UNORM</span></span></p>
<p><span data-ttu-id="24fff-274">DXGI_FORMAT_B8G8R8X8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-274">DXGI_FORMAT_B8G8R8X8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-275">D3DFMT_R5G6B5</span><span class="sxs-lookup"><span data-stu-id="24fff-275">D3DFMT_R5G6B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-276">DXGI_FORMAT_B5G6R5_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-276">DXGI_FORMAT_B5G6R5_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-277">D3DFMT_X1R5G5B5</span><span class="sxs-lookup"><span data-stu-id="24fff-277">D3DFMT_X1R5G5B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-278">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-278">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-279">D3DFMT_A1R5G5B5</span><span class="sxs-lookup"><span data-stu-id="24fff-279">D3DFMT_A1R5G5B5</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-280">DXGI_FORMAT_B5G5R5A1_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-280">DXGI_FORMAT_B5G5R5A1_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-281">D3DFMT_A4R4G4B4</span><span class="sxs-lookup"><span data-stu-id="24fff-281">D3DFMT_A4R4G4B4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-282">DXGI_FORMAT_B4G4R4A4_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-282">DXGI_FORMAT_B4G4R4A4_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-283">D3DFMT_R3G3B2</span><span class="sxs-lookup"><span data-stu-id="24fff-283">D3DFMT_R3G3B2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-284">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-284">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-285">D3DFMT_A8</span><span class="sxs-lookup"><span data-stu-id="24fff-285">D3DFMT_A8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-286">DXGI_FORMAT_A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-286">DXGI_FORMAT_A8_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-287">D3DFMT_A8R3G3B2</span><span class="sxs-lookup"><span data-stu-id="24fff-287">D3DFMT_A8R3G3B2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-288">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-288">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-289">D3DFMT_X4R4G4B4</span><span class="sxs-lookup"><span data-stu-id="24fff-289">D3DFMT_X4R4G4B4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-290">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-290">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-291">D3DFMT_A2B10G10R10</span><span class="sxs-lookup"><span data-stu-id="24fff-291">D3DFMT_A2B10G10R10</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-292">DXGI_FORMAT_R10G10B10A2</span><span class="sxs-lookup"><span data-stu-id="24fff-292">DXGI_FORMAT_R10G10B10A2</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-293">D3DFMT_A8B8G8R8</span><span class="sxs-lookup"><span data-stu-id="24fff-293">D3DFMT_A8B8G8R8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-294">DXGI_FORMAT_R8G8B8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-294">DXGI_FORMAT_R8G8B8A8_UNORM</span></span></p>
<p><span data-ttu-id="24fff-295">DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-295">DXGI_FORMAT_R8G8B8A8_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-296">D3DFMT_X8B8G8R8</span><span class="sxs-lookup"><span data-stu-id="24fff-296">D3DFMT_X8B8G8R8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-297">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-297">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-298">D3DFMT_G16R16</span><span class="sxs-lookup"><span data-stu-id="24fff-298">D3DFMT_G16R16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-299">DXGI_FORMAT_R16G16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-299">DXGI_FORMAT_R16G16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-300">D3DFMT_A2R10G10B10</span><span class="sxs-lookup"><span data-stu-id="24fff-300">D3DFMT_A2R10G10B10</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-301">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-301">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-302">D3DFMT_A16B16G16R16</span><span class="sxs-lookup"><span data-stu-id="24fff-302">D3DFMT_A16B16G16R16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-303">DXGI_FORMAT_R16G16B16A16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-303">DXGI_FORMAT_R16G16B16A16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-304">D3DFMT_A8P8</span><span class="sxs-lookup"><span data-stu-id="24fff-304">D3DFMT_A8P8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-305">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-305">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-306">D3DFMT_P8</span><span class="sxs-lookup"><span data-stu-id="24fff-306">D3DFMT_P8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-307">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-307">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-308">D3DFMT_L8</span><span class="sxs-lookup"><span data-stu-id="24fff-308">D3DFMT_L8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-309">DXGI_FORMAT_R8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-309">DXGI_FORMAT_R8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-310">
<strong>Hinweis:</strong>  verwenden .r Swizzle im Shader, um Rot für andere Komponenten zu Direct3D 9-Verhaltens duplizieren.</span><span class="sxs-lookup"><span data-stu-id="24fff-310">
<strong>Note</strong> Use .r swizzle in shader to duplicate red to other components to get Direct3D 9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-311">D3DFMT_A8L8</span><span class="sxs-lookup"><span data-stu-id="24fff-311">D3DFMT_A8L8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-312">DXGI_FORMAT_R8G8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-312">DXGI_FORMAT_R8G8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-313">
<strong>Hinweis:</strong>  Swizzle Operator ".rrrg" im Shader verwenden, um Rot zu duplizieren und Grün in die alpha-Komponenten zu Direct3D 9-Verhaltens verschieben.</span><span class="sxs-lookup"><span data-stu-id="24fff-313">
<strong>Note</strong> Use swizzle .rrrg in shader to duplicate red and move green to the alpha components to get Direct3D 9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-314">D3DFMT_A4L4</span><span class="sxs-lookup"><span data-stu-id="24fff-314">D3DFMT_A4L4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-315">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-315">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-316">D3DFMT_V8U8</span><span class="sxs-lookup"><span data-stu-id="24fff-316">D3DFMT_V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-317">DXGI_FORMAT_R8G8_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-317">DXGI_FORMAT_R8G8_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-318">D3DFMT_L6V5U5</span><span class="sxs-lookup"><span data-stu-id="24fff-318">D3DFMT_L6V5U5</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-319">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-319">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-320">D3DFMT_X8L8V8U8</span><span class="sxs-lookup"><span data-stu-id="24fff-320">D3DFMT_X8L8V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-321">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-321">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-322">D3DFMT_Q8W8V8U8</span><span class="sxs-lookup"><span data-stu-id="24fff-322">D3DFMT_Q8W8V8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-323">DXGI_FORMAT_R8G8B8A8_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-323">DXGI_FORMAT_R8G8B8A8_SNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-324">D3DFMT_V16U16</span><span class="sxs-lookup"><span data-stu-id="24fff-324">D3DFMT_V16U16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-325">DXGI_FORMAT_R16G16_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-325">DXGI_FORMAT_R16G16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-326">D3DFMT_W11V11U10</span><span class="sxs-lookup"><span data-stu-id="24fff-326">D3DFMT_W11V11U10</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-327">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-327">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-328">D3DFMT_A2W10V10U10</span><span class="sxs-lookup"><span data-stu-id="24fff-328">D3DFMT_A2W10V10U10</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-329">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-329">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-330">D3DFMT_UYVY</span><span class="sxs-lookup"><span data-stu-id="24fff-330">D3DFMT_UYVY</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-331">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-331">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-332">D3DFMT_R8G8_B8G8</span><span class="sxs-lookup"><span data-stu-id="24fff-332">D3DFMT_R8G8_B8G8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-333">DXGI_FORMAT_G8R8_G8B8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-333">DXGI_FORMAT_G8R8_G8B8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-334">
<strong>Hinweis:</strong>  In Direct3D 9 wurden die Daten von 255.0f vergrößert wurde, aber dies kann im Shader behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-334">
<strong>Note</strong> In Direct3D 9 the data was scaled up by 255.0f, but this can be handled in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-335">D3DFMT_YUY2</span><span class="sxs-lookup"><span data-stu-id="24fff-335">D3DFMT_YUY2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-336">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-336">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-337">D3DFMT_G8R8_G8B8</span><span class="sxs-lookup"><span data-stu-id="24fff-337">D3DFMT_G8R8_G8B8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-338">DXGI_FORMAT_R8G8_B8G8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-338">DXGI_FORMAT_R8G8_B8G8_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-339">
<strong>Hinweis:</strong>  In Direct3D 9 wurden die Daten von 255.0f vergrößert wurde, aber dies kann im Shader behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-339">
<strong>Note</strong> In Direct3D 9 the data was scaled up by 255.0f, but this can be handled in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-340">D3DFMT_DXT1</span><span class="sxs-lookup"><span data-stu-id="24fff-340">D3DFMT_DXT1</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-341">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-341">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-342">D3DFMT_DXT2</span><span class="sxs-lookup"><span data-stu-id="24fff-342">D3DFMT_DXT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-343">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-343">DXGI_FORMAT_BC1_UNORM & DXGI_FORMAT_BC1_UNORM_SRGB</span></span></p>
<div class="alert"><span data-ttu-id="24fff-344">
<strong>Hinweis:</strong>  DXT1 und DXT2 sind aus Sicht der API-Hardware identisch.</span><span class="sxs-lookup"><span data-stu-id="24fff-344">
<strong>Note</strong> DXT1 and DXT2 are the same from an API/hardware perspective.</span></span> <span data-ttu-id="24fff-345">Der einzige Unterschied besteht darin, ob prämultipliziertes Alpha verwendet wird, was von einer App nachverfolgt werden kann und kein separates Format erfordert.</span><span class="sxs-lookup"><span data-stu-id="24fff-345">The only difference is whether premultiplied alpha is used, which can be tracked by an application and doesn't need a separate format.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-346">D3DFMT_DXT3</span><span class="sxs-lookup"><span data-stu-id="24fff-346">D3DFMT_DXT3</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-347">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-347">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-348">D3DFMT_DXT4</span><span class="sxs-lookup"><span data-stu-id="24fff-348">D3DFMT_DXT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-349">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-349">DXGI_FORMAT_BC2_UNORM & DXGI_FORMAT_BC2_UNORM_SRGB</span></span></p>
<div class="alert"><span data-ttu-id="24fff-350">
<strong>Hinweis:</strong>  DXT3 und DXT4 sind aus Sicht der API-Hardware identisch.</span><span class="sxs-lookup"><span data-stu-id="24fff-350">
<strong>Note</strong> DXT3 and DXT4 are the same from an API/hardware perspective.</span></span> <span data-ttu-id="24fff-351">Der einzige Unterschied besteht darin, ob prämultipliziertes Alpha verwendet wird, was von einer App nachverfolgt werden kann und kein separates Format erfordert.</span><span class="sxs-lookup"><span data-stu-id="24fff-351">The only difference is whether premultiplied alpha is used, which can be tracked by an application and doesn't need a separate format.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-352">D3DFMT_DXT5</span><span class="sxs-lookup"><span data-stu-id="24fff-352">D3DFMT_DXT5</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-353">DXGI_FORMAT_BC3_UNORM & DXGI_FORMAT_BC3_UNORM_SRGB</span><span class="sxs-lookup"><span data-stu-id="24fff-353">DXGI_FORMAT_BC3_UNORM & DXGI_FORMAT_BC3_UNORM_SRGB</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-354">D3DFMT_D16 & D3DFMT_D16_LOCKABLE</span><span class="sxs-lookup"><span data-stu-id="24fff-354">D3DFMT_D16 & D3DFMT_D16_LOCKABLE</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-355">DXGI_FORMAT_D16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-355">DXGI_FORMAT_D16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-356">D3DFMT_D32</span><span class="sxs-lookup"><span data-stu-id="24fff-356">D3DFMT_D32</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-357">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-357">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-358">D3DFMT_D15S1</span><span class="sxs-lookup"><span data-stu-id="24fff-358">D3DFMT_D15S1</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-359">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-359">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-360">D3DFMT_D24S8</span><span class="sxs-lookup"><span data-stu-id="24fff-360">D3DFMT_D24S8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-361">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-361">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-362">D3DFMT_D24X8</span><span class="sxs-lookup"><span data-stu-id="24fff-362">D3DFMT_D24X8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-363">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-363">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-364">D3DFMT_D24X4S4</span><span class="sxs-lookup"><span data-stu-id="24fff-364">D3DFMT_D24X4S4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-365">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-365">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-366">D3DFMT_D16</span><span class="sxs-lookup"><span data-stu-id="24fff-366">D3DFMT_D16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-367">DXGI_FORMAT_D16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-367">DXGI_FORMAT_D16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-368">D3DFMT_D32F_LOCKABLE</span><span class="sxs-lookup"><span data-stu-id="24fff-368">D3DFMT_D32F_LOCKABLE</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-369">DXGI_FORMAT_D32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-369">DXGI_FORMAT_D32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-370">D3DFMT_D24FS8</span><span class="sxs-lookup"><span data-stu-id="24fff-370">D3DFMT_D24FS8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-371">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-371">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-372">D3DFMT_S1D15</span><span class="sxs-lookup"><span data-stu-id="24fff-372">D3DFMT_S1D15</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-373">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-373">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-374">D3DFMT_S8D24</span><span class="sxs-lookup"><span data-stu-id="24fff-374">D3DFMT_S8D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-375">DXGI_FORMAT_D24_UNORM_S8_UINT</span><span class="sxs-lookup"><span data-stu-id="24fff-375">DXGI_FORMAT_D24_UNORM_S8_UINT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-376">D3DFMT_X8D24</span><span class="sxs-lookup"><span data-stu-id="24fff-376">D3DFMT_X8D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-377">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-377">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-378">D3DFMT_X4S4D24</span><span class="sxs-lookup"><span data-stu-id="24fff-378">D3DFMT_X4S4D24</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-379">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-379">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-380">D3DFMT_L16</span><span class="sxs-lookup"><span data-stu-id="24fff-380">D3DFMT_L16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-381">DXGI_FORMAT_R16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-381">DXGI_FORMAT_R16_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-382">
<strong>Hinweis:</strong>  verwenden .r Swizzle im Shader, um Rot für andere Komponenten zu D3D9-Verhaltens den swizzle duplizieren.</span><span class="sxs-lookup"><span data-stu-id="24fff-382">
<strong>Note</strong> Use .r swizzle in shader to duplicate red to other components to get D3D9 behavior.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-383">D3DFMT_INDEX16</span><span class="sxs-lookup"><span data-stu-id="24fff-383">D3DFMT_INDEX16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-384">DXGI_FORMAT_R16_UINT</span><span class="sxs-lookup"><span data-stu-id="24fff-384">DXGI_FORMAT_R16_UINT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-385">D3DFMT_INDEX32</span><span class="sxs-lookup"><span data-stu-id="24fff-385">D3DFMT_INDEX32</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-386">DXGI_FORMAT_R32_UINT</span><span class="sxs-lookup"><span data-stu-id="24fff-386">DXGI_FORMAT_R32_UINT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-387">D3DFMT_Q16W16V16U16</span><span class="sxs-lookup"><span data-stu-id="24fff-387">D3DFMT_Q16W16V16U16</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-388">DXGI_FORMAT_R16G16B16A16_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-388">DXGI_FORMAT_R16G16B16A16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-389">D3DFMT_MULTI2_ARGB8</span><span class="sxs-lookup"><span data-stu-id="24fff-389">D3DFMT_MULTI2_ARGB8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-390">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-390">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-391">D3DFMT_R16F</span><span class="sxs-lookup"><span data-stu-id="24fff-391">D3DFMT_R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-392">DXGI_FORMAT_R16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-392">DXGI_FORMAT_R16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-393">D3DFMT_G16R16F</span><span class="sxs-lookup"><span data-stu-id="24fff-393">D3DFMT_G16R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-394">DXGI_FORMAT_R16G16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-394">DXGI_FORMAT_R16G16_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-395">D3DFMT_A16B16G16R16F</span><span class="sxs-lookup"><span data-stu-id="24fff-395">D3DFMT_A16B16G16R16F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-396">DXGI_FORMAT_R16G16B16A16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-396">DXGI_FORMAT_R16G16B16A16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-397">D3DFMT_R32F</span><span class="sxs-lookup"><span data-stu-id="24fff-397">D3DFMT_R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-398">DXGI_FORMAT_R32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-398">DXGI_FORMAT_R32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-399">D3DFMT_G32R32F</span><span class="sxs-lookup"><span data-stu-id="24fff-399">D3DFMT_G32R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-400">DXGI_FORMAT_R32G32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-400">DXGI_FORMAT_R32G32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-401">D3DFMT_A32B32G32R32F</span><span class="sxs-lookup"><span data-stu-id="24fff-401">D3DFMT_A32B32G32R32F</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-402">DXGI_FORMAT_R32G32B32A32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-402">DXGI_FORMAT_R32G32B32A32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-403">D3DFMT_CxV8U8</span><span class="sxs-lookup"><span data-stu-id="24fff-403">D3DFMT_CxV8U8</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-404">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-404">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-405">D3DDECLTYPE_FLOAT1</span><span class="sxs-lookup"><span data-stu-id="24fff-405">D3DDECLTYPE_FLOAT1</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-406">DXGI_FORMAT_R32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-406">DXGI_FORMAT_R32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-407">D3DDECLTYPE_FLOAT2</span><span class="sxs-lookup"><span data-stu-id="24fff-407">D3DDECLTYPE_FLOAT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-408">DXGI_FORMAT_R32G32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-408">DXGI_FORMAT_R32G32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-409">D3DDECLTYPE_FLOAT3</span><span class="sxs-lookup"><span data-stu-id="24fff-409">D3DDECLTYPE_FLOAT3</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-410">DXGI_FORMAT_R32G32B32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-410">DXGI_FORMAT_R32G32B32_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-411">D3DDECLTYPE_FLOAT4</span><span class="sxs-lookup"><span data-stu-id="24fff-411">D3DDECLTYPE_FLOAT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-412">DXGI_FORMAT_R32G32B32A32_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-412">DXGI_FORMAT_R32G32B32A32_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-413">D3DDECLTYPED3DCOLOR</span><span class="sxs-lookup"><span data-stu-id="24fff-413">D3DDECLTYPED3DCOLOR</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-414">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-414">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-415">D3DDECLTYPE_UBYTE4</span><span class="sxs-lookup"><span data-stu-id="24fff-415">D3DDECLTYPE_UBYTE4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-416">DXGI_FORMAT_R8G8B8A8_UINT</span><span class="sxs-lookup"><span data-stu-id="24fff-416">DXGI_FORMAT_R8G8B8A8_UINT</span></span></p>
<div class="alert"><span data-ttu-id="24fff-417">
<strong>Hinweis:</strong>  der Shader ruft UINT-Werte ab, aber wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden (0, 0F, 1, 0F... 255.f), kann UINT im Shader einfach in float32 konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="24fff-417">
<strong>Note</strong> The shader gets UINT values, but if Direct3D 9 style integral floats are needed (0.0f, 1.0f... 255.f), UINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-418">D3DDECLTYPE_SHORT2</span><span class="sxs-lookup"><span data-stu-id="24fff-418">D3DDECLTYPE_SHORT2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-419">DXGI_FORMAT_R16G16_SINT</span><span class="sxs-lookup"><span data-stu-id="24fff-419">DXGI_FORMAT_R16G16_SINT</span></span></p>
<div class="alert"><span data-ttu-id="24fff-420">
<strong>Hinweis:</strong>  der Shader ruft SINT-Werte ab, wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden, kann SINT jedoch nur werden konvertiert einfach in float32 im Shader.</span><span class="sxs-lookup"><span data-stu-id="24fff-420">
<strong>Note</strong> The shader gets SINT values, but if Direct3D 9 style integral floats are needed, SINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-421">D3DDECLTYPE_SHORT4</span><span class="sxs-lookup"><span data-stu-id="24fff-421">D3DDECLTYPE_SHORT4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-422">DXGI_FORMAT_R16G16B16A16_SINT</span><span class="sxs-lookup"><span data-stu-id="24fff-422">DXGI_FORMAT_R16G16B16A16_SINT</span></span></p>
<div class="alert"><span data-ttu-id="24fff-423">
<strong>Hinweis:</strong>  der Shader ruft SINT-Werte ab, wenn ganzzahlige Direct3D 9-Gleitkommawerte benötigt werden, kann SINT jedoch nur werden konvertiert einfach in float32 im Shader.</span><span class="sxs-lookup"><span data-stu-id="24fff-423">
<strong>Note</strong> The shader gets SINT values, but if Direct3D 9 style integral floats are needed, SINT can just be converted to float32 in the shader.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-424">D3DDECLTYPE_UBYTE4N</span><span class="sxs-lookup"><span data-stu-id="24fff-424">D3DDECLTYPE_UBYTE4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-425">DXGI_FORMAT_R8G8B8A8_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-425">DXGI_FORMAT_R8G8B8A8_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-426">D3DDECLTYPE_SHORT2N</span><span class="sxs-lookup"><span data-stu-id="24fff-426">D3DDECLTYPE_SHORT2N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-427">DXGI_FORMAT_R16G16_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-427">DXGI_FORMAT_R16G16_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-428">D3DDECLTYPE_SHORT4N</span><span class="sxs-lookup"><span data-stu-id="24fff-428">D3DDECLTYPE_SHORT4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-429">DXGI_FORMAT_R16G16B16A16_SNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-429">DXGI_FORMAT_R16G16B16A16_SNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-430">D3DDECLTYPE_USHORT2N</span><span class="sxs-lookup"><span data-stu-id="24fff-430">D3DDECLTYPE_USHORT2N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-431">DXGI_FORMAT_R16G16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-431">DXGI_FORMAT_R16G16_UNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-432">D3DDECLTYPE_USHORT4N</span><span class="sxs-lookup"><span data-stu-id="24fff-432">D3DDECLTYPE_USHORT4N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-433">DXGI_FORMAT_R16G16B16A16_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-433">DXGI_FORMAT_R16G16B16A16_UNORM</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-434">D3DDECLTYPE_UDEC3</span><span class="sxs-lookup"><span data-stu-id="24fff-434">D3DDECLTYPE_UDEC3</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-435">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-435">Not available</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-436">D3DDECLTYPE_DEC3N</span><span class="sxs-lookup"><span data-stu-id="24fff-436">D3DDECLTYPE_DEC3N</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-437">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="24fff-437">Not available</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-438">D3DDECLTYPE_FLOAT16_2</span><span class="sxs-lookup"><span data-stu-id="24fff-438">D3DDECLTYPE_FLOAT16_2</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-439">DXGI_FORMAT_R16G16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-439">DXGI_FORMAT_R16G16_FLOAT</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-440">D3DDECLTYPE_FLOAT16_4</span><span class="sxs-lookup"><span data-stu-id="24fff-440">D3DDECLTYPE_FLOAT16_4</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-441">DXGI_FORMAT_R16G16B16A16_FLOAT</span><span class="sxs-lookup"><span data-stu-id="24fff-441">DXGI_FORMAT_R16G16B16A16_FLOAT</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="24fff-442">FourCC 'ATI1'</span><span class="sxs-lookup"><span data-stu-id="24fff-442">FourCC 'ATI1'</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-443">DXGI_FORMAT_BC4_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-443">DXGI_FORMAT_BC4_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-444">
<strong>Hinweis:</strong>  erfordert Funktionsebene 10.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="24fff-444">
<strong>Note</strong> Requires Feature Level 10.0 or later</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="24fff-445">FourCC 'ATI2'</span><span class="sxs-lookup"><span data-stu-id="24fff-445">FourCC 'ATI2'</span></span></p></td>
<td align="left"><p><span data-ttu-id="24fff-446">DXGI_FORMAT_BC5_UNORM</span><span class="sxs-lookup"><span data-stu-id="24fff-446">DXGI_FORMAT_BC5_UNORM</span></span></p>
<div class="alert"><span data-ttu-id="24fff-447">
<strong>Hinweis:</strong>  erfordert Funktionsebene 10.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="24fff-447">
<strong>Note</strong> Requires Feature Level 10.0 or later</span></span>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

 

 




