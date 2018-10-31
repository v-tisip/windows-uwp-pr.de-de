---
author: joannaleecy
title: Einführung in das Rendering
description: Hier erfahren Sie, wie Sie die Renderingpipeline zum Anzeigen von Grafiken zusammenstellen. Einführung in das Rendering.
ms.assetid: 1da3670b-2067-576f-da50-5eba2f88b3e6
ms.author: joanlee
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Rendern
ms.localizationpriority: medium
ms.openlocfilehash: 7e8df200e8e989015834608d38cb8dfb0d36917b
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5827783"
---
# <a name="rendering-framework-i-intro-to-rendering"></a><span data-ttu-id="db217-105">Rendering-Framework I: Einführung in das Rendering</span><span class="sxs-lookup"><span data-stu-id="db217-105">Rendering framework I: Intro to rendering</span></span>

<span data-ttu-id="db217-106">Mittlerweile wissen Sie, wie ein Spiel für die universelle Windows-Plattform (UWP) aufgebaut sein muss, damit es verwendet werden kann, und wie Sie einen Zustandsautomaten zum Behandeln des Spielablaufs definieren.</span><span class="sxs-lookup"><span data-stu-id="db217-106">We've covered how to structure a Universal Windows Platform (UWP) game and how to define a state machine to handle the flow of the game in the earlier topics.</span></span> <span data-ttu-id="db217-107">Jetzt erfahren Sie, wie Sie die Rendering-Framework zusammenstellen.</span><span class="sxs-lookup"><span data-stu-id="db217-107">Now, it's time to learn how to assemble the rendering framework.</span></span> <span data-ttu-id="db217-108">Sehen wir uns an, wie das Beispielspiel die Szene des Spiele mit Direct3D11 (auch bezeichnet als DirectX 11) rendert.</span><span class="sxs-lookup"><span data-stu-id="db217-108">Let's look at how the sample game renders the game scene using Direct3D11 (commonly known as DirectX 11).</span></span>

>[!Note]
><span data-ttu-id="db217-109">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="db217-109">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="db217-110">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="db217-110">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="db217-111">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="db217-111">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

<span data-ttu-id="db217-112">Direct3D11 enthält eine Reihe von APIs, die Zugriff auf die erweiterten Funktionen von High-End-Grafik Hardware bereitstellen, die zum Erstellen von 3D-Grafiken für Grafik-intensive Anwendungen wie z.B. Spiele verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db217-112">Direct3D 11 contains a set of APIs that provide access to the advanced features of high-performance graphic hardware that can be used to create 3D graphics for graphic intensive applications such as games.</span></span>

<span data-ttu-id="db217-113">Das Rendern von Spielegrafiken auf dem Bildschirm ist ein Rendern einer Frame-Sequenz auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="db217-113">Rendering game graphics on-screen is basically rendering a sequence of frames on-screen.</span></span> <span data-ttu-id="db217-114">In jeder einzelnen Frame werden Objekte gerendert, die basierend auf der Ansicht in der Szene angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-114">In each frame, you have to render objects that are visible in the scene, based on the view.</span></span> 

<span data-ttu-id="db217-115">Um ein Frame zu rendern, müssen Sie die für die Szene erforderlichen Informationen an die Hardware übergeben, damit sie auf dem Bildschirm angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="db217-115">In order to render a frame, you have to pass the required scene information to the hardware so that it can be displayed on the screen.</span></span> <span data-ttu-id="db217-116">Wenn etwas auf dem Bildschirm angezeigt werden soll, müssen Sie das Rendering starten, sobald das Spiel startet.</span><span class="sxs-lookup"><span data-stu-id="db217-116">If you want to have anything displayed on screen, you need to start rendering as soon as the game starts running.</span></span>

## <a name="objective"></a><span data-ttu-id="db217-117">Ziel</span><span class="sxs-lookup"><span data-stu-id="db217-117">Objective</span></span>

<span data-ttu-id="db217-118">Um ein einfaches Rendering-Framework einzurichten, und die Grafikausgabe für ein UWP-DirectX-Spiel anzuzeigen können Sie diese lose in drei Schritten gruppieren.</span><span class="sxs-lookup"><span data-stu-id="db217-118">To set up a basic rendering framework to display the graphics output for a UWP DirectX game, you can loosely group them into these three steps.</span></span>

 1. <span data-ttu-id="db217-119">Einrichten einer Verbindung zur Grafikschnittstelle</span><span class="sxs-lookup"><span data-stu-id="db217-119">Establish a connection to the graphics interface</span></span>
 2. <span data-ttu-id="db217-120">Erstellen der Ressourcen, die zum Zeichnen der Grafiken benötigt werden</span><span class="sxs-lookup"><span data-stu-id="db217-120">Create the resources needed to draw the graphics</span></span>
 3. <span data-ttu-id="db217-121">Anzeigen die Grafiken: Rendern des Frames</span><span class="sxs-lookup"><span data-stu-id="db217-121">Display the graphics by rendering the frame</span></span>

<span data-ttu-id="db217-122">In diesem Artikel wird erläutert, wie Grafiken mit Schritt1 bis 3 gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-122">This article explains how graphics are rendered, covering steps 1 and 3.</span></span>

<span data-ttu-id="db217-123">[Rendering-Framework II: Spiel-Rendering](tutorial-game-rendering.md) erklärt Schritt2: wie Rendering-Framework eingerichtet und Daten vorbereitet werden, bevor das Rendering möglich ist.</span><span class="sxs-lookup"><span data-stu-id="db217-123">[Rendering framework II: Game rendering](tutorial-game-rendering.md) covers step 2; how to set up the rendering framework and how data is prepared before rendering can happen.</span></span>

## <a name="get-started"></a><span data-ttu-id="db217-124">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="db217-124">Get started</span></span>

<span data-ttu-id="db217-125">Bevor Sie beginnen, sollten Sie sich mit den grundlegenden Grafik- und Rendering-Konzepten vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="db217-125">Before you begin, you should familiarize yourself with the basic graphics and rendering concepts.</span></span> <span data-ttu-id="db217-126">Wenn Sie noch nie mit Direct3D und Rendering gearbeitet haben, finden Sie unter [Begriffe und Konzepte](#terms-and-concepts) eine kurze Beschreibung der Grafik- und Rendering-Terminologie, die in diesem Artikel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db217-126">If you're new to Direct3D and rendering, see [Terms and concepts](#terms-and-concepts) for a brief description of the graphics and rendering terms used in this article.</span></span>

<span data-ttu-id="db217-127">Für dieses Spiel stellt das __GameRenderer__-Klassenobjekt den Renderer für dieses Beispielspiel dar.</span><span class="sxs-lookup"><span data-stu-id="db217-127">For this game, the __GameRenderer__ class object represents the renderer for this sample game.</span></span>  <span data-ttu-id="db217-128">Er ist verantwortlich für das Erstellen und Verwalten alle Direct3D 11- und Direct2D-Objekte, die verwendet, um die visuellen Spielelemente generieren.</span><span class="sxs-lookup"><span data-stu-id="db217-128">It's responsible for creating and maintaining all the Direct3D 11 and Direct2D objects used to generate the game visuals.</span></span>  <span data-ttu-id="db217-129">Er enthält auch einen Verweis auf das __Simple3DGame__-Objekt zum Abrufen einer Liste von Objekten und dem Status des Spiels für die HUD-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="db217-129">It also maintains a reference to the __Simple3DGame__ object used to retrieve the list of objects to render as well as status of the game for the Heads Up Display (HUD).</span></span> 

<span data-ttu-id="db217-130">In diesem Teil des Lernprogramms konzentrieren wir uns auf das Rendering von 3D-Objekten im Spiel.</span><span class="sxs-lookup"><span data-stu-id="db217-130">In this part of the tutorial, we'll focus on rendering 3D objects in the game.</span></span>

## <a name="establish-a-connection-to-the-graphics-interface"></a><span data-ttu-id="db217-131">Einrichten einer Verbindung zur Grafikschnittstelle</span><span class="sxs-lookup"><span data-stu-id="db217-131">Establish a connection to the graphics interface</span></span>

<span data-ttu-id="db217-132">Um auf die Hardware für das Rendern zuzugreifen, finden Sie im UWP-Framework-Artikel unter [__App::Initialize__](tutorial--building-the-games-uwp-app-framework.md#appinitialize-method) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="db217-132">To access to the hardware for rendering, see the UWP framework article under [__App::Initialize__](tutorial--building-the-games-uwp-app-framework.md#appinitialize-method).</span></span>

<span data-ttu-id="db217-133">Die __make\_shared-Funktion__, wie [unten](#appinitialize-method) dargestellt, dient zum Erstellen einer __shared\_ptr__ auf [__DX::DeviceResources__](#dxdeviceresources), die auch Zugriff auf das Gerät ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="db217-133">The __make\_shared function__, as shown [below](#appinitialize-method), is used to create a __shared\_ptr__ to [__DX::DeviceResources__](#dxdeviceresources), which also provides access to the device.</span></span> 

<span data-ttu-id="db217-134">In Direct3D11 dient ein [Gerät](#device) zum Zuordnen und zerstören von Objekten, um Grundtypen zu rendern und mit der Grafikkarte über die Grafiktreiber zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="db217-134">In Direct3D 11, a [device](#device) is used to allocate and destroy objects, render primitives, and communicate with the graphics card through the graphics driver.</span></span>

### <a name="appinitialize-method"></a><span data-ttu-id="db217-135">App::Initialize-Methode</span><span class="sxs-lookup"><span data-stu-id="db217-135">App::Initialize method</span></span>

```cpp
void App::Initialize(
    CoreApplicationView^ applicationView
    )
{
    //...

    // At this point we have access to the device. 
    // We can create the device-dependent resources.
    m_deviceResources = std::make_shared<DX::DeviceResources>();
}
```

## <a name="display-the-graphics-by-rendering-the-frame"></a><span data-ttu-id="db217-136">Anzeigen die Grafiken: Rendern des Frames</span><span class="sxs-lookup"><span data-stu-id="db217-136">Display the graphics by rendering the frame</span></span>

<span data-ttu-id="db217-137">Die Spieleszene muss gerendert werden, wenn das Spiel gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="db217-137">The game scene needs to render when the game is launched.</span></span> <span data-ttu-id="db217-138">Die Anweisungen für das Rendern beginnen in der [__GameMain::Run__](#gameamainrun-method)-Methode, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-138">The instructions for rendering start in the  [__GameMain::Run__](#gameamainrun-method) method, as shown below.</span></span>

<span data-ttu-id="db217-139">Der einfache Fluss ist:</span><span class="sxs-lookup"><span data-stu-id="db217-139">The simple flow is:</span></span>
1. __<span data-ttu-id="db217-140">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="db217-140">Update</span></span>__
2. __<span data-ttu-id="db217-141">Rendern</span><span class="sxs-lookup"><span data-stu-id="db217-141">Render</span></span>__
3. __<span data-ttu-id="db217-142">Darstellen</span><span class="sxs-lookup"><span data-stu-id="db217-142">Present</span></span>__

### <a name="gamemainrun-method"></a><span data-ttu-id="db217-143">GameMain::Run-Methode</span><span class="sxs-lookup"><span data-stu-id="db217-143">GameMain::Run method</span></span>

```cpp
// Comparing this to App::Run() in the DirectX 11 App template
void GameMain::Run()
{
    while (!m_windowClosed)
    {
        if (m_visible) // if the window is visible
        {
            // Added: Switching different game states since this game sample is more complex
            switch (m_updateState) 
            {

                // ...
                CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);
                // 1. Update
                // Also exist in DirectX 11 App template: Update loop to get the latest game changes
                Update();
                
                // 2. Render
                // Present also in DirectX 11 App template: Prepare to render
                m_renderer->Render();
                
                // 3. Present
                // Present also in DirectX 11 App template: Present the 
                // contents of the swap chain to the screen.
                m_deviceResources->Present(); 
                
                // Added: resetting a variable we've added to indicate that 
                // render has been done and no longer needed to render
                m_renderNeeded = false; 
            }
        }
        else
        {   
            // Present also in DirectX 11 App template
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending); 
        }
    }
    m_game->OnSuspending();  // exiting due to window close. Make sure to save state.
}
```

### <a name="update"></a><span data-ttu-id="db217-144">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="db217-144">Update</span></span>

<span data-ttu-id="db217-145">Weitere Informationen über das Aktualisieren der Spielzustände finden Sie im Artikel [Spielablaufverwaltung](tutorial-game-flow-management.md) der [__App:: Update__ und __GameMain::Update__](tutorial-game-flow-management.md#appupdate-method)-Methode.</span><span class="sxs-lookup"><span data-stu-id="db217-145">See the [Game flow management](tutorial-game-flow-management.md) article for more information about how game states are updated in the [__App::Update__ and __GameMain::Update__](tutorial-game-flow-management.md#appupdate-method) method.</span></span>

### <a name="render"></a><span data-ttu-id="db217-146">Rendern</span><span class="sxs-lookup"><span data-stu-id="db217-146">Render</span></span>

<span data-ttu-id="db217-147">Das Rendern wird durch Aufrufen der [__GameRenderer::Render__](#gamerendererrender-method)-Methode im __GameMain::Run__ implementiert.</span><span class="sxs-lookup"><span data-stu-id="db217-147">Rendering is implemented by calling the [__GameRenderer::Render__](#gamerendererrender-method) method in __GameMain::Run__.</span></span>

<span data-ttu-id="db217-148">Wenn [Stereorendering](#stereo-rendering) aktiviert ist, gibt es zwei Renderingdurchgänge: einen für das rechte Auge und einen für das linke Auge.</span><span class="sxs-lookup"><span data-stu-id="db217-148">If [stereo rendering](#stereo-rendering) is enabled, there are two rendering passes: one for the right eye and one for the left eye.</span></span> <span data-ttu-id="db217-149">In jedem Renderingdurchgang binden wir das Renderziel und die [Tiefenschablonen-Ansicht](#depth-stencil-view) für das Gerät.</span><span class="sxs-lookup"><span data-stu-id="db217-149">In each rendering pass, we bind the render target and the [depth-stencil view](#depth-stencil-view) to the device.</span></span> <span data-ttu-id="db217-150">Wir löschen danach die Tiefenschablonen-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="db217-150">We also clear the depth-stencil view afterward.</span></span>

> [!Note]
> <span data-ttu-id="db217-151">Stereorendering kann mit anderen Methoden wie z.B. einem einzigen Stereo-Durchlauf mit Vertex-Instanzerstellung oder Geometry-Shader erzielt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-151">Stereo rendering can be achieved using other methods such as single pass stereo using vertex instancing or geometry shaders.</span></span> <span data-ttu-id="db217-152">Die beiden Renderingdurchgangs-Methoden sind langsamer, aber einfacher zum Stereo-Rendering.</span><span class="sxs-lookup"><span data-stu-id="db217-152">The two rendering pass method is a slower, but more convenient way to achieve stereo rendering.</span></span>

<span data-ttu-id="db217-153">Wenn das Spiel vorhanden ist und Ressourcen geladen werden, aktualisieren Sie die [Projektionsmatrix](#projection-transform-matrix), einmal pro Renderingdurchgang.</span><span class="sxs-lookup"><span data-stu-id="db217-153">Once the game exists and resources are loaded, update the [projection matrix](#projection-transform-matrix), once per rendering pass.</span></span> <span data-ttu-id="db217-154">Objekte sehen in den verschiedenen Ansichten etwas anders aus.</span><span class="sxs-lookup"><span data-stu-id="db217-154">Objects are slightly different from each view.</span></span> <span data-ttu-id="db217-155">Richten Sie nun die [Grafikrenderingpipeline](#rendering-pipeline) ein.</span><span class="sxs-lookup"><span data-stu-id="db217-155">Next, set up the [graphics rendering pipeline](#rendering-pipeline).</span></span> 

> [!Note]
> <span data-ttu-id="db217-156">Weitere Informationen finden Sie unter [Erstellen und Laden von DirectX-Grafikressourcen](tutorial-game-rendering.md#create-and-load-directx-graphic-resources), um zu sehen, wie Ressourcen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="db217-156">See [Create and load DirectX graphic resources](tutorial-game-rendering.md#create-and-load-directx-graphic-resources) for more information on how resources are loaded.</span></span>

<span data-ttu-id="db217-157">In diesem Beispielspiel verwendet der Renderer ein Standard-Vertex-Layout für alle verwendeten Objekte.</span><span class="sxs-lookup"><span data-stu-id="db217-157">In this game sample, the renderer is designed to use a standard vertex layout across all objects.</span></span> <span data-ttu-id="db217-158">Dies vereinfacht das Shader-Design und ermöglicht eine einfache Änderungen zwischen den Shaders, unabhängig von der Objekt-Geometrie.</span><span class="sxs-lookup"><span data-stu-id="db217-158">This simplifies the shader design and allows for easy changes between shaders, independent of the objects' geometry.</span></span>

#### <a name="gamerendererrender-method"></a><span data-ttu-id="db217-159">GameRenderer::Render-Methode</span><span class="sxs-lookup"><span data-stu-id="db217-159">GameRenderer::Render method</span></span>

<span data-ttu-id="db217-160">Legen Sie den Direct3D-Kontext fest, um ein Eingabevertex-Layout zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="db217-160">Set the Direct3D context to use an input vertex layout.</span></span> <span data-ttu-id="db217-161">Eingabevertex-Objekte beschreiben das Streamen der Vertexpufferdaten in die [Renderingpipeline](#rendering-pipeline).</span><span class="sxs-lookup"><span data-stu-id="db217-161">Input-layout objects describe how vertex buffer data is streamed into the [rendering pipeline](#rendering-pipeline).</span></span> 

<span data-ttu-id="db217-162">Als Nächstes legen wir den Direct3D-Kontext mithilfe der [Konstantenpuffer](#constant-buffers) fest, die zuvor definiert wurden und vom [Vertex-Shader](#vertex-shaders-and-pixel-shaders) der Pipeline-Phase und dem [Pixel-Shader](#vertex-shaders-and-pixel-shaders) der Pipeline-Phase verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db217-162">Next, we set the Direct3D context to use the [constant buffers](#constant-buffers) defined earlier, that are used by the [vertex shader](#vertex-shaders-and-pixel-shaders) pipeline stage and the [pixel shader](#vertex-shaders-and-pixel-shaders) pipeline stage.</span></span> 

> [!Note]
> <span data-ttu-id="db217-163">Weitere Informationen zur Definition der Konstantenpuffer finden Sie unter [Rendering-Framework II: Spiel-Rendering](tutorial-game-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="db217-163">See [Rendering framework II: Game rendering](tutorial-game-rendering.md) for more information about definition of the constant buffers.</span></span>

<span data-ttu-id="db217-164">Da das gleiche Eingabelayout und der Satz von Konstantenpuffern für alle Shader in der Pipeline verwendet wird, wird es einmal pro Frame festgelegt.</span><span class="sxs-lookup"><span data-stu-id="db217-164">Because the same input layout and set of constant buffers is used for all shaders that are in the pipeline, it's set up once per frame.</span></span>

```cpp
void GameRenderer::Render()
{
    bool stereoEnabled = m_deviceResources->GetStereoState();

    auto d3dContext = m_deviceResources->GetD3DDeviceContext();
    auto d2dContext = m_deviceResources->GetD2DDeviceContext();

    int renderingPasses = 1;
    if (stereoEnabled)
    {
        renderingPasses = 2;
    }

    for (int i = 0; i < renderingPasses; i++)
    {
        // Iterate through the number of rendering passes to be completed.
        // 2 rendering passes if stereo is enabled
        if (i > 0)
        {
            // Doing the Right Eye View.
            ID3D11RenderTargetView *const targets[1] = { m_deviceResources->GetBackBufferRenderTargetViewRight() };

            // Resets render targets to the screen.
            // OMSetRenderTargets binds 2 things to the device.
            // 1. Binds one render target atomically to the device.
            // 2. Binds the depth-stencil view, as returned by the GetDepthStencilView method, to the device.
            // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476464.aspx

            d3dContext->OMSetRenderTargets(1, targets, m_deviceResources->GetDepthStencilView());
            
            // Clears the depth stencil view.
            // A depth stencil view contains the format and buffer to hold depth and stencil info.
            // For more info about depth stencil view, go to: 
            // https://docs.microsoft.com/windows/uwp/graphics-concepts/depth-stencil-view--dsv-
            // A depth buffer is used to store depth information to control which areas of 
            // polygons are rendered rather than hidden from view. To learn more about a depth buffer,
            // go to: https://docs.microsoft.com/windows/uwp/graphics-concepts/depth-buffers
            // A stencil buffer is used to mask pixels in an image, to produce special effects. 
            // The mask determines whether a pixel is drawn or not,
            // by setting the bit to a 1 or 0. To learn more about a stencil buffer,
            // go to: https://docs.microsoft.com/windows/uwp/graphics-concepts/stencil-buffers

            d3dContext->ClearDepthStencilView(m_deviceResources->GetDepthStencilView(), D3D11_CLEAR_DEPTH, 1.0f, 0);
            
            // d2d -- Discussed later
            d2dContext->SetTarget(m_deviceResources->GetD2DTargetBitmapRight());
        }
        else
        {
            // Doing the Mono or Left Eye View.
            // As compared to the right eye:
            // m_deviceResources->GetBackBufferRenderTargetView instead of GetBackBufferRenderTargetViewRight
            ID3D11RenderTargetView *const targets[1] = { m_deviceResources->GetBackBufferRenderTargetView() }; 
            
            // Same as the Right Eye View.
            d3dContext->OMSetRenderTargets(1, targets, m_deviceResources->GetDepthStencilView());
            d3dContext->ClearDepthStencilView(m_deviceResources->GetDepthStencilView(), D3D11_CLEAR_DEPTH, 1.0f, 0);
            
            // d2d -- Discussed later under Adding UI
            d2dContext->SetTarget(m_deviceResources->GetD2DTargetBitmap()); 
        }

        // Render the scene objects
        if (m_game != nullptr && m_gameResourcesLoaded && m_levelResourcesLoaded)
        {
            // This section is only used after the game state has been initialized and all device
            // resources needed for the game have been created and associated with the game objects.
            if (stereoEnabled)
            {
                // When doing stereo, it is necessary to update the projection matrix once per rendering pass.

                auto orientation = m_deviceResources->GetOrientationTransform3D();

                ConstantBufferChangeOnResize changesOnResize;

                // Apply either a left or right eye projection, which is an offset from the middle
                XMStoreFloat4x4(
                    &changesOnResize.projection,
                    XMMatrixMultiply(
                        XMMatrixTranspose(
                            i == 0 ?
                            m_game->GameCamera()->LeftEyeProjection() :
                            m_game->GameCamera()->RightEyeProjection()
                            ),
                        XMMatrixTranspose(XMLoadFloat4x4(&orientation))
                        )
                    );

                d3dContext->UpdateSubresource(
                    m_constantBufferChangeOnResize.Get(),
                    0,
                    nullptr,
                    &changesOnResize,
                    0,
                    0
                    );
            }

            // Update variables that change once per frame.
            ConstantBufferChangesEveryFrame constantBufferChangesEveryFrame;
            XMStoreFloat4x4(
                &constantBufferChangesEveryFrame.view,
                XMMatrixTranspose(m_game->GameCamera()->View())
                );
            d3dContext->UpdateSubresource(
                m_constantBufferChangesEveryFrame.Get(),
                0,
                nullptr,
                &constantBufferChangesEveryFrame,
                0,
                0
                );

            // Setup the graphics pipeline. This sample uses the same InputLayout and set of
            // constant buffers for all shaders, so they only need to be set once per frame.
            // For more info about the graphics or rendering pipeline, 
            // go to https://msdn.microsoft.com/library/windows/desktop/ff476882.aspx

            // IASetInputLayout binds an input-layout object to the input-assembler (IA) stage. 
            // Input-layout objects describe how vertex buffer data is streamed into the IA pipeline stage.
            // Set up the Direct3D context to use this vertex layout.
            // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476454.aspx
            d3dContext->IASetInputLayout(m_vertexLayout.Get());

            // VSSetConstantBuffers sets the constant buffers used by the vertex shader pipeline stage.
            // Set up the Direct3D context to use these constant buffers.
            // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476491.aspx

            d3dContext->VSSetConstantBuffers(0, 1, m_constantBufferNeverChanges.GetAddressOf());
            d3dContext->VSSetConstantBuffers(1, 1, m_constantBufferChangeOnResize.GetAddressOf());
            d3dContext->VSSetConstantBuffers(2, 1, m_constantBufferChangesEveryFrame.GetAddressOf());
            d3dContext->VSSetConstantBuffers(3, 1, m_constantBufferChangesEveryPrim.GetAddressOf());

            // Sets the constant buffers used by the pixel shader pipeline stage. 
            // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476470.aspx

            d3dContext->PSSetConstantBuffers(2, 1, m_constantBufferChangesEveryFrame.GetAddressOf());
            d3dContext->PSSetConstantBuffers(3, 1, m_constantBufferChangesEveryPrim.GetAddressOf());
            d3dContext->PSSetSamplers(0, 1, m_samplerLinear.GetAddressOf());

            auto objects = m_game->RenderObjects();
            for (auto object = objects.begin(); object != objects.end(); object++)
            {
                // The 3D object render method handles the rendering.
                // For more info, see Primitive rendering below.
                (*object)->Render(d3dContext, m_constantBufferChangesEveryPrim.Get()); /
            }
        }
        else
        {
            const float ClearColor[4] = {0.5f, 0.5f, 0.8f, 1.0f};

            // Only need to clear the background when not rendering the full 3D scene since
            // the 3D world is a fully enclosed box and the dynamics prevents the camera from
            // moving outside this space.
            if (i > 0)
            {
                // Doing the Right Eye View.
                d3dContext->ClearRenderTargetView(m_deviceResources->GetBackBufferRenderTargetViewRight(), ClearColor);
            }
            else
            {
                // Doing the Mono or Left Eye View.
                d3dContext->ClearRenderTargetView(m_deviceResources->GetBackBufferRenderTargetView(), ClearColor);
            }
        }

        // Start of 2D rendering
        d3dContext->BeginEventInt(L"D2D BeginDraw", 1);
        d2dContext->BeginDraw();

        // ...
    }
}
```

### <a name="primitive-rendering"></a><span data-ttu-id="db217-165">Rendern der Grundtypen</span><span class="sxs-lookup"><span data-stu-id="db217-165">Primitive rendering</span></span>

<span data-ttu-id="db217-166">Beim Rendern der Szene durchlaufen Sie alle Objekte, die gerendert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="db217-166">When rendering the scene, you loop through all the objects that need to be rendered.</span></span> <span data-ttu-id="db217-167">Die folgenden Schrittewerden für jedes Objekt (Grundtyp) wiederholt.</span><span class="sxs-lookup"><span data-stu-id="db217-167">The steps below are repeated for each object (primitive).</span></span>

* <span data-ttu-id="db217-168">Aktualisieren Sie die Konstantenpuffer (__m\_constantBufferChangesEveryPrim__) mit der [globalen Transformationsmatrix](#world-transform-matrix) des Modells und den wesentlichen Informationen.</span><span class="sxs-lookup"><span data-stu-id="db217-168">Update the constant buffer(__m\_constantBufferChangesEveryPrim__) with the model's [world transformation matrix](#world-transform-matrix) and material information.</span></span>
* <span data-ttu-id="db217-169">Der __m\_constantBufferChangesEveryPrim__ enthält Parameter für jedes Objekt.</span><span class="sxs-lookup"><span data-stu-id="db217-169">The  __m\_constantBufferChangesEveryPrim__ contains parameters for each object.</span></span>  <span data-ttu-id="db217-170">Beinhaltet das Objekt für die globale Transformationsmatrix sowie die grundlegenden Eigenschaften wie Farbe und Glanzlichterexponenten für die Berechnung der Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="db217-170">It includes the object to world transformation matrix as well as material properties like color and specular exponent for lighting calculations.</span></span>
* <span data-ttu-id="db217-171">Legen Sie den Direct3D-Kontext für das Eingabevertex-Layout für die Gitterobjektdaten fest, das in die Eingabeassemblerphase (IA)-Phase der [Renderingpipeline](#rendering-pipeline) gestreamt werden soll</span><span class="sxs-lookup"><span data-stu-id="db217-171">Set Direct3D context to use the input vertex layout for the mesh object data to be streamed into the input-assembler (IA) stage of the [rendering pipeline](#rendering-pipeline)</span></span>
* <span data-ttu-id="db217-172">Legen Sie den Direct3D-Kontext für den [Indexpuffer](#index-buffer) in der IA-Phase fest.</span><span class="sxs-lookup"><span data-stu-id="db217-172">Set Direct3D context to use an [index buffer](#index-buffer) in the IA stage.</span></span> <span data-ttu-id="db217-173">Geben Sie die Grundtyp-Informationen an: Typ, Datenreihenfolge.</span><span class="sxs-lookup"><span data-stu-id="db217-173">Provide the primitive info: type, data order.</span></span>
* <span data-ttu-id="db217-174">Übermitteln Sie einen Draw-Aufruf zum Zeichnen des indizierten, nicht instanziierten Grundtyps.</span><span class="sxs-lookup"><span data-stu-id="db217-174">Submit a draw call to draw the indexed, non-instanced primitive.</span></span> <span data-ttu-id="db217-175">Die __GameObject::Render__-Methode aktualisiert den [Grundtypkonstantenpuffer](#constant-buffer-or-shader-constant-buffer) mit den spezifischen Daten eines Grundtyps.</span><span class="sxs-lookup"><span data-stu-id="db217-175">The __GameObject::Render__ method updates the primitive [constant buffer](#constant-buffer-or-shader-constant-buffer) with the data specific to a given primitive.</span></span> <span data-ttu-id="db217-176">Dadurch erfolgt ein __DrawIndexed__-Aufruf für den Kontext, um die Geometrie jedes Grundtyps zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="db217-176">This results in a __DrawIndexed__ call on the context to draw the geometry of that each primitive.</span></span> <span data-ttu-id="db217-177">Durch diesen Draw-Aufruf werden Befehle und Daten in die Warteschlange der GPU eingereiht (entsprechend der Parametrisierung durch die Konstantenpufferdaten).</span><span class="sxs-lookup"><span data-stu-id="db217-177">Specifically, this draw call queues commands and data to the graphics processing unit (GPU), as parameterized by the constant buffer data.</span></span> <span data-ttu-id="db217-178">Jeder Draw-Aufruf führt einmal den [Vertexshader](#vertex-shaders-and-pixel-shaders) für jeden Vertex und anschließend einmal den [Pixelshader](#vertex-shaders-and-pixel-shaders) für jedes Pixel der einzelnen Dreiecke im Grundtyp aus.</span><span class="sxs-lookup"><span data-stu-id="db217-178">Each draw call executes the [vertex shader](#vertex-shaders-and-pixel-shaders) one time per vertex, and then the [pixel shader](#vertex-shaders-and-pixel-shaders) one time for every pixel of each triangle in the primitive.</span></span> <span data-ttu-id="db217-179">Die Texturen sind Teil des Zustands, den der Pixelshader für das Rendering verwendet.</span><span class="sxs-lookup"><span data-stu-id="db217-179">The textures are part of the state that the pixel shader uses to do the rendering.</span></span>

<span data-ttu-id="db217-180">Gründe für die Verwendung mehrerer Konstantenpuffer:</span><span class="sxs-lookup"><span data-stu-id="db217-180">Reasons for multiple constant buffers:</span></span>
    * <span data-ttu-id="db217-181">Im Spiel werden mehrere Konstantenpuffer verwendet; diese müssen aber nur einmal pro Grundtyp aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-181">The game uses multiple constant buffers but only needs to update these buffers one time per primitive.</span></span> <span data-ttu-id="db217-182">Sie können sich die Konstantenpuffer als Eingabe für die für jeden Grundtyp ausgeführten Shader vorstellen.</span><span class="sxs-lookup"><span data-stu-id="db217-182">As mentioned earlier, constant buffers are like inputs to the shaders that run for each primitive.</span></span> <span data-ttu-id="db217-183">Einige Daten sind statisch (__m\_constantBufferNeverChanges__), einige Daten (etwa die Position der Kamera) sind innerhalb eines Frames konstant (__m\_constantBufferChangesEveryFrame__), und einige Daten wie Farbe und Texturen gelten speziell für den Grundtyp (__m\_constantBufferChangesEveryPrim__).</span><span class="sxs-lookup"><span data-stu-id="db217-183">Some data is static (__m\_constantBufferNeverChanges__); some data is constant over the frame (__m\_constantBufferChangesEveryFrame__), like the position of the camera; and some data is specific to the primitive, like its color and textures (__m\_constantBufferChangesEveryPrim__)</span></span>
    * <span data-ttu-id="db217-184">Der [Spielrenderer](#renderer) teilt diese Eingaben in verschiedene Konstantenpuffer auf, um die von CPU und GPU verwendete Speicherbandbreite zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="db217-184">The game [renderer](#renderer) separates these inputs into different constant buffers to optimize the memory bandwidth that the CPU and GPU use.</span></span> <span data-ttu-id="db217-185">Durch diesen Ansatz lässt sich auch die Datenmenge minimieren, die von der GPU nachverfolgt werden muss.</span><span class="sxs-lookup"><span data-stu-id="db217-185">This approach also helps to minimize the amount of data the GPU needs to keep track of.</span></span> <span data-ttu-id="db217-186">Die GPU verfügt über eine große Befehlswarteschlange und dieser Befehl bei jedem Aufruf von __Draw__ zusammen mit den dazugehörigen Daten in die Warteschlange eingereiht wird.</span><span class="sxs-lookup"><span data-stu-id="db217-186">The GPU has a big queue of commands, and each time the game calls __Draw__, that command is queued along with the data associated with it.</span></span> <span data-ttu-id="db217-187">Wenn das Spiel den Grundtypkonstantenpuffer aktualisiert und den nächsten __Draw__-Befehl ausgibt, fügt der Grafiktreiber diesen Befehl und die dazugehörigen Daten der Warteschlange hinzu.</span><span class="sxs-lookup"><span data-stu-id="db217-187">When the game updates the primitive constant buffer and issues the next __Draw__ command, the graphics driver adds this next command and the associated data to the queue.</span></span> <span data-ttu-id="db217-188">Zeichnet das Spiel 100Grundtypen, kann die Warteschlange 100Kopien der Konstantenpufferdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="db217-188">If the game draws 100 primitives, it could potentially have 100 copies of the constant buffer data in the queue.</span></span> <span data-ttu-id="db217-189">Um die an die GPU gesendete Datenmenge zu minimieren, wird im Spiel ein separater Grundtypkonstantenpuffer verwendet, der nur die Aktualisierungen für jeden Grundtyp enthält.</span><span class="sxs-lookup"><span data-stu-id="db217-189">To minimize the amount of data the game is sending to the GPU, the game uses a separate primitive constant buffer that only contains the updates for each primitive.</span></span>

#### <a name="gameobjectrender-method"></a><span data-ttu-id="db217-190">GameObject::Render-Methode</span><span class="sxs-lookup"><span data-stu-id="db217-190">GameObject::Render method</span></span>

```cpp
void GameObject::Render(
    _In_ ID3D11DeviceContext *context,
    _In_ ID3D11Buffer *primitiveConstantBuffer
    )
{
    if (!m\_active || (m\_mesh == nullptr) || (m_normalMaterial == nullptr))
    {
        return;
    }

    ConstantBufferChangesEveryPrim constantBuffer;

    // Put the model matrix info into a constant buffer, in world matrix.
    XMStoreFloat4x4(
        &constantBuffer.worldMatrix,
        XMMatrixTranspose(ModelMatrix())
        );

    // Check to see which material to use on the object.
    // If a collision (a hit) is detected, GameObject::Render checks the current context, which 
    // indicates whether the target has been hit by an ammo sphere. If the target has been hit, 
    // this method applies a hit material, which reverses the colors of the rings of the target to 
    // indicate a successful hit to the player. Otherwise, it applies the default material 
    // with the same method. In both cases, it sets the material by calling Material::RenderSetup, 
    // which sets the appropriate constants into the constant buffer. Then, it calls 
    // ID3D11DeviceContext::PSSetShaderResources to set the corresponding texture resource for the 
    // pixel shader, and ID3D11DeviceContext::VSSetShader and ID3D11DeviceContext::PSSetShader 
    // to set the vertex shader and pixel shader objects themselves, respectively.

    if (m_hit && m_hitMaterial != nullptr)
    {
        m_hitMaterial->RenderSetup(context, &constantBuffer);
    }
    else
    {
        m_normalMaterial->RenderSetup(context, &constantBuffer);
    }

    // Update the primitive constant buffer with the object model's info.
    context->UpdateSubresource(primitiveConstantBuffer, 0, nullptr, &constantBuffer, 0, 0);

    // Render the mesh.
    // See MeshObject::Render method below.
    m_mesh->Render(context);
}

#### MeshObject::Render method

void MeshObject::Render(\_In\_ ID3D11DeviceContext *context)
{
    // PNTVertex is a struct. stride provides us the size required for all the mesh data
    // struct PNTVertex
    //{
    //  DirectX::XMFLOAT3 position;
    //  DirectX::XMFLOAT3 normal;
    //  DirectX::XMFLOAT2 textureCoordinate;
    //};
    uint32 stride = sizeof(PNTVertex);
    uint32 offset = 0;

    // Similar to the main render loop.
    // Input-layout objects describe how vertex buffer data is streamed into the IA pipeline stage.
    context->IASetVertexBuffers(0, 1, m_vertexBuffer.GetAddressOf(), &stride, &offset);

    // IASetIndexBuffer binds an index buffer to the input-assembler stage.
    // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476453.aspx
    context->IASetIndexBuffer(m_indexBuffer.Get(), DXGI_FORMAT_R16_UINT, 0);

    // Binds information about the primitive type, and data order that describes input data for the input assembler stage.
    // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476455.aspx
    context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);

    // Draw indexed, non-instanced primitives. A draw API submits work to the rendering pipeline.
    // For more info, go to: https://msdn.microsoft.com/library/windows/desktop/ff476409.aspx
    context->DrawIndexed(m_indexCount, 0, 0);
}
```

### <a name="present"></a><span data-ttu-id="db217-191">Darstellen</span><span class="sxs-lookup"><span data-stu-id="db217-191">Present</span></span>

<span data-ttu-id="db217-192">Wir rufen die __DX::DeviceResources::Present__-Methode auf, um den Inhalt des Puffers zu platzieren und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="db217-192">We call the __DX::DeviceResources::Present__ method to put the contents we've placed in the buffers and display it.</span></span>

<span data-ttu-id="db217-193">Eine Swapchain ist eine Sammlung von Puffern, die zum Anzeigen von Frames für den Benutzer verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db217-193">We use the term swap chain for a collection of buffers that are used for displaying frames to the user.</span></span> <span data-ttu-id="db217-194">Bei jeder Darstellung eines neuen Frames für eine Anzeige durch eine Anwendung wird der erste Puffer der Swapchain zum Anzeigepuffer.</span><span class="sxs-lookup"><span data-stu-id="db217-194">Each time an application presents a new frame for display, the first buffer in the swap chain takes the place of the displayed buffer.</span></span> <span data-ttu-id="db217-195">Dieser Prozess wird Austauschen oder Kippen genannt.</span><span class="sxs-lookup"><span data-stu-id="db217-195">This process is called swapping or flipping.</span></span> <span data-ttu-id="db217-196">Weitere Informationen finden Sie unter [Swapchain](../graphics-concepts/swap-chains.md).</span><span class="sxs-lookup"><span data-stu-id="db217-196">For more information, see [Swap chains](../graphics-concepts/swap-chains.md).</span></span>

* <span data-ttu-id="db217-197">Die in der __IDXGISwapChain1__ Schnittstelle __vorhanden__-Methode weist [DXGI](#dxgi) an, bis zur vertikalen Synchronisierung (VSync) zu blockieren und die Anwendung bis zum nächsten VSYNC-Vorgang in den Standbymodus versetzen.</span><span class="sxs-lookup"><span data-stu-id="db217-197">__IDXGISwapChain1__ interface's __Present__ method the instructs [DXGI](#dxgi) to block until Vertical Synchronization (VSync), putting the application to sleep until the next VSync.</span></span> <span data-ttu-id="db217-198">Dadurch wird sichergestellt, dass Sie kein Durchlaufrendern des Frames vergeuden, das nie auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-198">This ensures you don't waste any cycles rendering frames that will never be displayed to the screen.</span></span>
* <span data-ttu-id="db217-199">Die in der __ID3D11DeviceContext3__ Schnittstelle enthaltene __DiscardView__-Methode verwirft den Inhalt des [Renderziels](#render-target).</span><span class="sxs-lookup"><span data-stu-id="db217-199">__ID3D11DeviceContext3__ interface's __DiscardView__ method discards the contents of the [render target](#render-target).</span></span> <span data-ttu-id="db217-200">Dies ist nur dann ein gültiger Vorgang, wenn der vorhandene Inhalt vollständig überschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="db217-200">This is a valid operation only when the existing contents will be entirely overwritten.</span></span> <span data-ttu-id="db217-201">Wenn verschmutzte oder Bildlauf-Rechtecke verwendet werden, sollte dieser Aufruf entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-201">If dirty or scroll rects are used, this call should be removed.</span></span>
* <span data-ttu-id="db217-202">Mit der gleichen __DiscardView__-Methode, verwerfen Sie den Inhalt der [Tiefenschablonen](#depth-stencil).</span><span class="sxs-lookup"><span data-stu-id="db217-202">Using the same __DiscardView__ method, discard the contents of the [depth-stencil](#depth-stencil).</span></span>
* <span data-ttu-id="db217-203">Die __HandleDeviceLost__-Methode wird verwendet, um das Szenario zu verwalten, wenn das [Gerät](#device) entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="db217-203">__HandleDeviceLost__ method is used to manage the scenario if the [device](#device) is removed.</span></span> <span data-ttu-id="db217-204">Wenn das Gerät entweder durch ein Trennen der Verbindung oder dem Upgrade des Treibers entfernt wurde, müssen Sie alle Geräteressourcen neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="db217-204">If the device was removed either by a disconnection or a driver upgrade, you must recreate all device resources.</span></span> <span data-ttu-id="db217-205">Weitere Informationen finden Sie unter [Behandeln von Szenarien mit entfernten Geräten in Direct3D11](handling-device-lost-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="db217-205">For more information, see [Handle device removed scenarios in Direct3D 11](handling-device-lost-scenarios.md).</span></span>

> [!Tip]
> <span data-ttu-id="db217-206">Um eine reibungslose Framerate zu erreichen, müssen Sie sicherstellen, dass die Menge der zu rendernden Frames in die Zeit zwischen den VSyncs passt.</span><span class="sxs-lookup"><span data-stu-id="db217-206">To achieve a smooth frame rate, you must ensure that the amount of work to render a frame fits the time between VSyncs.</span></span>

```cpp
// Present the contents of the swap chain to the screen.
void DX::DeviceResources::Present()
{
    // The first argument instructs DXGI to block until VSync, putting the application
    // to sleep until the next VSync. This ensures we don't waste any cycles rendering
    // frames that will never be displayed to the screen.
    HRESULT hr = m_swapChain->Present(1, 0);

    // Discard the contents of the render target.
    // This is a valid operation only when the existing contents will be entirely
    // overwritten. If dirty or scroll rects are used, this call should be removed.
    m_d3dContext->DiscardView(m_d3dRenderTargetView.Get());

    // Discard the contents of the depth-stencil.
    m_d3dContext->DiscardView(m_d3dDepthStencilView.Get());

    // If the device was removed either by a disconnection or a driver upgrade, we 
    // must recreate all device resources.
    // For more info about how to handle a device lost scenario, go to:
    // https://docs.microsoft.com/windows/uwp/gaming/handling-device-lost-scenarios
    if (hr == DXGI_ERROR_DEVICE_REMOVED || hr == DXGI_ERROR_DEVICE_RESET)
    {
        HandleDeviceLost();
    }
    else
    {
        DX::ThrowIfFailed(hr);
    }
}
```

## <a name="next-steps"></a><span data-ttu-id="db217-207">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="db217-207">Next steps</span></span>

<span data-ttu-id="db217-208">In diesem Artikel wird erläutert, wie Grafiken auf dem Bildschirm gerendert werden sowie eine kurze Beschreibung für die Rendering-Terminologie.</span><span class="sxs-lookup"><span data-stu-id="db217-208">This article explained how graphics is rendered on the display and provided a short description for some of the rendering terms used.</span></span> <span data-ttu-id="db217-209">Weitere Informationen über das Rendern finden Sie im Artikel [Rendering-Framework II: Spiel-Rendering](tutorial-game-rendering.md). Hier erfahren Sie, wie Sie die Daten vor dem Rendern vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="db217-209">Learn more about rendering in the [Rendering framework II: Game rendering](tutorial-game-rendering.md) article, and learn how to prepare the data needed before rendering.</span></span>

## <a name="terms-and-concepts"></a><span data-ttu-id="db217-210">Begriffe und Konzepte</span><span class="sxs-lookup"><span data-stu-id="db217-210">Terms and concepts</span></span>

### <a name="simple-game-scene"></a><span data-ttu-id="db217-211">Einfache Spielszenen</span><span class="sxs-lookup"><span data-stu-id="db217-211">Simple game scene</span></span>

<span data-ttu-id="db217-212">Eine einfache Spieleszene besteht aus wenigen Objekten mit mehreren Lichtquellen.</span><span class="sxs-lookup"><span data-stu-id="db217-212">A simple game scene is made up of a few objects with several light sources.</span></span>

<span data-ttu-id="db217-213">Ein Objekt wird durch eine Reihe von X-, Y- und Z-Koordinaten im Raum definiert.</span><span class="sxs-lookup"><span data-stu-id="db217-213">An object's shape is defined by a set of X, Y, Z coordinates in space.</span></span> <span data-ttu-id="db217-214">Die tatsächliche Rendering-Position in der Spielwelt kann durch das Anwenden einer Transformationsmatrix mit fester Breite der X, Y, Z-Koordinaten festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-214">The actual render location in the game world can be determined by applying a transformation matrix to the positional X, Y, Z coordinates.</span></span> <span data-ttu-id="db217-215">Sie müssen auch eine Reihe von Texturkoordinaten haben – U und V geben an, wie ein Material auf das Objekt angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="db217-215">It may also have a set of texture coordinates - U and V which specifies how a material is applied to the object.</span></span> <span data-ttu-id="db217-216">Diese definiert die Surface-Eigenschaften des Objekts und gibt Ihnen die Möglichkeit, festzustellen, ob ein Objekt über eine grobe Oberfläche wie ein Tennisball oder eine glatte glänzende Oberfläche wie ein Bowlingball verfügt.</span><span class="sxs-lookup"><span data-stu-id="db217-216">This defines the surface properties of the object and gives you the ability to see if an object has a rough surface like a tennis ball or a smooth glossy surface like a bowling ball.</span></span>

<span data-ttu-id="db217-217">Szenen- und Objekt-Informationen werden von der Rendering-Framework verwendet, um die Szene von Frame zu Frame neu zu erstellen, und sie auf Ihrem Bildschirm lebendig werden zu lassen.</span><span class="sxs-lookup"><span data-stu-id="db217-217">Scene and object info are used by the rendering framework to recreate the scene frame by frame, making it come alive on your display monitor.</span></span>

### <a name="rendering-pipeline"></a><span data-ttu-id="db217-218">Renderingpipeline</span><span class="sxs-lookup"><span data-stu-id="db217-218">Rendering pipeline</span></span>

<span data-ttu-id="db217-219">Im Prozess der Renderingpipeline werden die 3D-Szenen-Informationen zu einem Bild auf dem Bildschirm übersetzt.</span><span class="sxs-lookup"><span data-stu-id="db217-219">The rendering pipeline is the process in which 3D scene info is translated to an image displayed on screen.</span></span> <span data-ttu-id="db217-220">In Direct3D11 ist diese Pipeline programmierbar.</span><span class="sxs-lookup"><span data-stu-id="db217-220">In Direct3D 11, this pipeline is programmable.</span></span> <span data-ttu-id="db217-221">Sie können die Phasen zur Unterstützung der Rendering-Anforderungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="db217-221">You can adapt the stages to support your rendering needs.</span></span> <span data-ttu-id="db217-222">Stufen, die allgemeine Shaderkerne bereitstellen, sind mit der HLSL-Programmiersprache programmierbar.</span><span class="sxs-lookup"><span data-stu-id="db217-222">Stages that feature common shader cores are programmable by using the HLSL programming language.</span></span> <span data-ttu-id="db217-223">Dies ist auch als Grafikrenderingpipeline oder einfach Pipeline bekannt.</span><span class="sxs-lookup"><span data-stu-id="db217-223">It is also known as the graphics rendering pipeline or simply pipeline.</span></span>

<span data-ttu-id="db217-224">Um diese Pipeline erstellen zu können, müssen Sie damit vertraut sein:</span><span class="sxs-lookup"><span data-stu-id="db217-224">To help you create this pipeline, you need to be familiar with:</span></span>
* <span data-ttu-id="db217-225">[HLSL](#HLSL).</span><span class="sxs-lookup"><span data-stu-id="db217-225">[HLSL](#HLSL).</span></span> <span data-ttu-id="db217-226">Wir empfehlen die Verwendung von HLSL-Shader Model 5.1 und höher für UWP-DirectX-Spiele.</span><span class="sxs-lookup"><span data-stu-id="db217-226">We recommend the use of HLSL Shader Model 5.1 and above for UWP DirectX games.</span></span>
* [<span data-ttu-id="db217-227">Shader</span><span class="sxs-lookup"><span data-stu-id="db217-227">Shaders</span></span>](#Shaders)
* [<span data-ttu-id="db217-228">Vertex-Shader sind Pixelshader</span><span class="sxs-lookup"><span data-stu-id="db217-228">Vertex shaders and pixel shaders</span></span>](#vertext-shaders-pixel-shaders)
* [<span data-ttu-id="db217-229">Shaderstufen</span><span class="sxs-lookup"><span data-stu-id="db217-229">Shader stages</span></span>](#shader-stages)
* [<span data-ttu-id="db217-230">Verschiedene Shader-Dateiformate</span><span class="sxs-lookup"><span data-stu-id="db217-230">Various shader file formats</span></span>](#various-shader-file-formats)

<span data-ttu-id="db217-231">Weitere Informationen finden Sie unter [Understand the Direct3D 11 rendering pipeline](https://msdn.microsoft.com/library/windows/desktop/dn643746.aspx) und [Grafik-Pipeline](https://msdn.microsoft.com/library/windows/desktop/ff476882.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-231">For more information, see [Understand the Direct3D 11 rendering pipeline](https://msdn.microsoft.com/library/windows/desktop/dn643746.aspx) and [Graphics pipeline](https://msdn.microsoft.com/library/windows/desktop/ff476882.aspx).</span></span>

#### <a name="hlsl"></a><span data-ttu-id="db217-232">HLSL</span><span class="sxs-lookup"><span data-stu-id="db217-232">HLSL</span></span>

<span data-ttu-id="db217-233">HLSL ist die High LevelShading-Sprache für DirectX.</span><span class="sxs-lookup"><span data-stu-id="db217-233">HLSL is the High Level Shading Language for DirectX.</span></span> <span data-ttu-id="db217-234">Mit HLSL können Sie wie in C-programmierbare Shader für die Direct3D-Pipeline erstellen.</span><span class="sxs-lookup"><span data-stu-id="db217-234">Using HLSL, you can create C like programmable shaders for the Direct3D pipeline.</span></span> <span data-ttu-id="db217-235">Weitere Informationen finden Sie unter [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-235">For more information, see [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561.aspx).</span></span>

#### <a name="shaders"></a><span data-ttu-id="db217-236">Shader</span><span class="sxs-lookup"><span data-stu-id="db217-236">Shaders</span></span>

<span data-ttu-id="db217-237">Shader können als ein Satz von Anweisungen betrachtet werden, die bestimmen, wie die Oberfläche eines Objekts gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="db217-237">Shaders can be thought of as a set of instructions that determine how the surface of an object appears when rendered.</span></span> <span data-ttu-id="db217-238">Diejenigen, die mithilfe von HLSL programmiert werden, werden als HLSL-Shader bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="db217-238">Those that are programmed using HLSL are known as HLSL shaders.</span></span> <span data-ttu-id="db217-239">Quellcodedateien für [HLSL])(#hlsl)-Shader haben die Erweiterung der HLSL-Datei.</span><span class="sxs-lookup"><span data-stu-id="db217-239">Source code files for [HLSL])(#hlsl) shaders have .hlsl file extension.</span></span> <span data-ttu-id="db217-240">Diese Shader können zum Zeitpunkt der Erstellung oder Laufzeit kompiliert werden und zur Laufzeit auf die entsprechende Pipelinephase festgelegt werden; ein kompiliertes Shader-Objekt hat die Dateierweiterung ".cso".</span><span class="sxs-lookup"><span data-stu-id="db217-240">These shaders can be compiled at author-time or at runtime, and set at runtime into the appropriate pipeline stage; a compiled shader object has a .cso file extension.</span></span>

<span data-ttu-id="db217-241">Direct3D9-Shader können mit Shadermodell 1, Shadermodell 2 und Shadermodell 3 entworfen werden. Direct3D10 Shader können nur auf Shadermodell 4 entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="db217-241">Direct3D 9 shaders can be designed using shader model 1, shader model 2 and shader model 3; Direct3D 10 shaders can only be designed on shader model 4.</span></span> <span data-ttu-id="db217-242">Direct3D11-Shader können auf Shadermodell 5 entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="db217-242">Direct3D 11 shaders can be designed on shader model 5.</span></span> <span data-ttu-id="db217-243">Direct3D11.3 und Direct3D12 können auf Shadermodell 5.1 entwickelt werden und Direct3D12 kann auch auf Shadermodell 6 entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="db217-243">Direct3D 11.3 and Direct3D 12 can be designed on shader model 5.1, and Direct3D 12 can also be designed on shader model 6.</span></span>

#### <a name="vertex-shaders-and-pixel-shaders"></a><span data-ttu-id="db217-244">Vertex-Shader sind Pixelshader</span><span class="sxs-lookup"><span data-stu-id="db217-244">Vertex shaders and pixel shaders</span></span>

<span data-ttu-id="db217-245">Daten werden in der Grafikpipeline als einen Stream von Grundtypen und durch verschiedene Shader z.B. den Vertex-Shader und Pixel-Shader verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="db217-245">Data enters the graphics pipeline as a stream of primitives and is processed by various shaders such as the vertex shaders and pixel shaders.</span></span> 

<span data-ttu-id="db217-246">Vertex-Shader verarbeiten Scheitelpunkte und führt dabei in der Regel Vorgänge wie Transformationen, das Anwenden von Skins und Beleuchtung durch.</span><span class="sxs-lookup"><span data-stu-id="db217-246">Vertex shaders processes vertices, typically performing operations such as transformations, skinning, and lighting.</span></span>  <span data-ttu-id="db217-247">Pixelshader aktivieren umfassende Schattierungstechniken wie z.B. Beleuchtung pro Pixel und Nachbearbeitung.</span><span class="sxs-lookup"><span data-stu-id="db217-247">Pixel shaders enables rich shading techniques such as per-pixel lighting and post-processing.</span></span> <span data-ttu-id="db217-248">Diese kombinieren Konstantenvariablen, Texturdaten, interpolierte Vertex-Werte und andere Daten für Pro-Pixel-Ausgaben.</span><span class="sxs-lookup"><span data-stu-id="db217-248">It combines constant variables, texture data, interpolated per-vertex values, and other data to produce per-pixel outputs.</span></span> 

#### <a name="shader-stages"></a><span data-ttu-id="db217-249">Shaderstufen</span><span class="sxs-lookup"><span data-stu-id="db217-249">Shader stages</span></span>

<span data-ttu-id="db217-250">Eine Sequenz dieser verschiedene Shader für die Verarbeitung dieser Grundtypen wird als Shaderstufen in einer Renderingpipeline bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="db217-250">A sequence of these various shaders defined to process this stream of primitives is known as shader stages in a rendering pipeline.</span></span> <span data-ttu-id="db217-251">Die tatsächlichen Phasen hängen von der Version von Direct3D ab, aber in der Regel umfassen sie Vertex-, Geometrie- und Pixel-Phasen.</span><span class="sxs-lookup"><span data-stu-id="db217-251">The actual stages depend on the version of Direct3D, but usually include the vertex, geometry, and pixel stages.</span></span> <span data-ttu-id="db217-252">Es gibt auch andere Phasen, z.B. Geometrie- und Domänen-Shader für Tesselation und Compute-Shader.</span><span class="sxs-lookup"><span data-stu-id="db217-252">There are also other stages, such as the hull and domain shaders for tessellation, and the compute shader.</span></span> <span data-ttu-id="db217-253">Alle diese Stufen sind vollständig programmierbar mithilfe von [HLSL])(#hlsl).</span><span class="sxs-lookup"><span data-stu-id="db217-253">All these stages are completely programmable using the [HLSL])(#hlsl).</span></span> <span data-ttu-id="db217-254">Weitere Informationen finden Sie unter [Grafikpipeline](https://msdn.microsoft.com/library/windows/desktop/ff476882.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-254">For more information, see [Graphics pipeline](https://msdn.microsoft.com/library/windows/desktop/ff476882.aspx).</span></span>

#### <a name="various-shader-file-formats"></a><span data-ttu-id="db217-255">Verschiedene Shader-Dateiformate</span><span class="sxs-lookup"><span data-stu-id="db217-255">Various shader file formats</span></span>

<span data-ttu-id="db217-256">Shader-Code-Dateierweiterungen:</span><span class="sxs-lookup"><span data-stu-id="db217-256">Shader code file extensions:</span></span>
    * <span data-ttu-id="db217-257">Eine Datei mit HLSL-Erweiterung enthält [HLSL])(#hlsl)-Quellcode.</span><span class="sxs-lookup"><span data-stu-id="db217-257">A file with the .hlsl extension holds [HLSL])(#hlsl) source code.</span></span>
    * <span data-ttu-id="db217-258">Eine Datei mit CSO-Erweiterung enthält ein kompiliertes Shader-Objekt.</span><span class="sxs-lookup"><span data-stu-id="db217-258">A file with the .cso extension holds a compiled shader object.</span></span>
    * <span data-ttu-id="db217-259">Eine Datei mit der Erweiterung .h ist eine Headerdatei, aber im Kontext des Shader-Code definiert diese Headerdatei ein Byte-Array, das Shader-Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="db217-259">A file with the .h extension is a header file, but in a shader code context, this header file defines a byte array that holds shader data.</span></span>
    * <span data-ttu-id="db217-260">Eine Datei mit HLSLI-Erweiterung enthält das Format einer HLSLI-Datei: .</span><span class="sxs-lookup"><span data-stu-id="db217-260">A file with the .hlsli extension contains the format of the constant buffers.</span></span> <span data-ttu-id="db217-261">Im Beispielspiel ist es die Datei __Shader__>__ConstantBuffers.hlsli__.</span><span class="sxs-lookup"><span data-stu-id="db217-261">In the game sample, the file is __Shaders__>__ConstantBuffers.hlsli__.</span></span>

> [!Note]
> <span data-ttu-id="db217-262">Sie würden den Shader einbetten, indem Sie entweder eine CSO-Datei zur Laufzeit laden oder die h-Datei in Ihren ausführbaren Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db217-262">You would embed the shader either by loading a .cso file at runtime or adding the .h file in your executable code.</span></span> <span data-ttu-id="db217-263">Jedoch werden nicht beide für den gleichen Shader verwendet.</span><span class="sxs-lookup"><span data-stu-id="db217-263">But you would not use both for the same shader.</span></span>

### <a name="deeper-understanding-of-directx"></a><span data-ttu-id="db217-264">Weitere Kenntnisse über DirectX</span><span class="sxs-lookup"><span data-stu-id="db217-264">Deeper understanding of DirectX</span></span>

<span data-ttu-id="db217-265">Direct3D11 ist eine Reihe von APIs, mit deren Hilfe wir Grafiken für Grafik-intensive Anwendung erstellen, z.B. Spiele, in der wir eine gute Grafikkarte benötigen, um die ressourcenintensive Berechnung verarbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="db217-265">Direct3D 11 is a set of APIs that can help us create graphics for graphics intensive applications like games, where we want to have a good graphics card to process intensive computation.</span></span> <span data-ttu-id="db217-266">In diesem Abschnitt werden die Direct3D11-Grafik-Programmierkonzepte kurz erläutert: Ressource, Unterressource, Gerät und Gerätekontext.</span><span class="sxs-lookup"><span data-stu-id="db217-266">This section briefly explains the Direct3D 11 graphics programming concepts: resource, subresource, device, and device context.</span></span>

#### <a name="resource"></a><span data-ttu-id="db217-267">Ressource</span><span class="sxs-lookup"><span data-stu-id="db217-267">Resource</span></span>

<span data-ttu-id="db217-268">Für diejenigen, die noch nie damit gearbeitet haben, können Sie sich Ressourcen (auch bekannt als Geräteressourcen) als Informationen vorstellen, um ein Objekt wie Textur, Position, Farbe zu rendern.</span><span class="sxs-lookup"><span data-stu-id="db217-268">For those who are new, you can think of resources (also known as device resources) as info on how to render an object like texture, position, color.</span></span> <span data-ttu-id="db217-269">Ressourcen stellen Daten für die Pipeline bereit und definieren, was während der Szene gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="db217-269">Resources provide data to the pipeline and define what is rendered during your scene.</span></span> <span data-ttu-id="db217-270">Ressourcen können von Ihren Spielmedien geladen oder zur Laufzeit dynamisch erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-270">Resources can be loaded from your game media or created dynamically at run time.</span></span>

<span data-ttu-id="db217-271">Eine Ressource ist ein Bereich im Speicher, auf den die Direct3D-[Pipeline](#rendering-pipeline) zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="db217-271">A resource is, in fact, an area in memory that can be accessed by the Direct3D [pipeline](#rendering-pipeline).</span></span> <span data-ttu-id="db217-272">Damit die Pipeline effizient auf den Speicher zugreifen kann, müssen für die Pipeline bereitgestellte Daten (wie z.B. Input-Geometrie, Shader-Ressourcen und Texturen) in einer Ressource gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-272">In order for the pipeline to access memory efficiently, data that is provided to the pipeline (such as input geometry, shader resources, and textures) must be stored in a resource.</span></span> <span data-ttu-id="db217-273">Es gibt zwei Arten von Ressourcen, aus denen alle Direct3D-Ressourcen abgeleitet sind: ein Puffer oder eine Textur.</span><span class="sxs-lookup"><span data-stu-id="db217-273">There are two types of resources from which all Direct3D resources derive: a buffer or a texture.</span></span> <span data-ttu-id="db217-274">Bis zu 128 Ressourcen können für jede Pipeline-Phase aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="db217-274">Up to 128 resources can be active for each pipeline stage.</span></span> <span data-ttu-id="db217-275">Weitere Informationen finden Sie unter [Ressourcen](../graphics-concepts/resources.md).</span><span class="sxs-lookup"><span data-stu-id="db217-275">For more information, see [Resources](../graphics-concepts/resources.md).</span></span>

#### <a name="subresource"></a><span data-ttu-id="db217-276">Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="db217-276">Subresource</span></span>

<span data-ttu-id="db217-277">Der Begriff Unterressource bezieht sich auf die Teilmenge einer Ressource.</span><span class="sxs-lookup"><span data-stu-id="db217-277">The term subresource refers to a subset of a resource.</span></span> <span data-ttu-id="db217-278">Direct3D kann auf eine gesamte Ressource verweisen oder auf die Teilmenge einer Ressource.</span><span class="sxs-lookup"><span data-stu-id="db217-278">Direct3D can reference an entire resource or it can reference subsets of a resource.</span></span> <span data-ttu-id="db217-279">Weitere Informationen finden Sie unter [Unterressource](../graphics-concepts/resource-types.md#subresources).</span><span class="sxs-lookup"><span data-stu-id="db217-279">For more information, see [Subresource](../graphics-concepts/resource-types.md#subresources).</span></span>

#### <a name="depth-stencil"></a><span data-ttu-id="db217-280">Tiefenschablone</span><span class="sxs-lookup"><span data-stu-id="db217-280">Depth-stencil</span></span>

<span data-ttu-id="db217-281">Eine Tiefenschablonenressource stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.</span><span class="sxs-lookup"><span data-stu-id="db217-281">A depth-stencil resource contains the format and buffer to hold depth and stencil information.</span></span> <span data-ttu-id="db217-282">Es wird mit der eine Texturressource erstellt.</span><span class="sxs-lookup"><span data-stu-id="db217-282">It is created using a texture resource.</span></span> <span data-ttu-id="db217-283">Weitere Informationen zum Erstellen einer Tiefenschablonen-Ressource finden Sie unter [Konfigurieren der Tiefenschablonenfunktionalität](https://msdn.microsoft.com/library/windows/desktop/bb205074.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-283">For more information on how to create a depth-stencil resource, see [Configuring Depth-Stencil Functionality](https://msdn.microsoft.com/library/windows/desktop/bb205074.aspx).</span></span> <span data-ttu-id="db217-284">Wir greifen über die implementierte Tiefenschablonenansicht auf die Tiefenschablonenressource zu, mithilfe der [ID3D11DepthStencilView](https://msdn.microsoft.com/library/windows/desktop/ff476377.aspx)-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="db217-284">We access the depth-stencil resource through the depth-stencil view implemented using the [ID3D11DepthStencilView](https://msdn.microsoft.com/library/windows/desktop/ff476377.aspx) interface.</span></span>

<span data-ttu-id="db217-285">Tiefeninformationen steuern, welche Bereiche von Polygonen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="db217-285">Depth info tells us which areas of polygons are rendered rather than hidden from view.</span></span> <span data-ttu-id="db217-286">Schabloneninformationen steuern, welche Pixel maskiert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-286">Stencil info tells us which pixels are masked.</span></span> <span data-ttu-id="db217-287">Es kann verwendet werden, um Spezialeffekte zu erzeugen, da es bestimmt, ob ein Pixel gezeichnet oder nicht gezeichnet wird. Es setzt das Bit auf 1 oder 0.</span><span class="sxs-lookup"><span data-stu-id="db217-287">It can be used to produce special effects since it determines whether a pixel is drawn or not; sets the bit to a 1 or 0.</span></span> 

<span data-ttu-id="db217-288">Weitere Informationen finden Sie unter: [Tiefenschablonenansicht](../graphics-concepts/depth-stencil-view--dsv-.md), [Tiefenpuffer](../graphics-concepts/depth-buffers.md), und [Schablonen-Puffer](../graphics-concepts/stencil-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="db217-288">For more information, see: [Depth-stencil view](../graphics-concepts/depth-stencil-view--dsv-.md), [depth buffer](../graphics-concepts/depth-buffers.md), and [stencil buffer](../graphics-concepts/stencil-buffers.md).</span></span>

#### <a name="render-target"></a><span data-ttu-id="db217-289">Renderziel</span><span class="sxs-lookup"><span data-stu-id="db217-289">Render target</span></span>

<span data-ttu-id="db217-290">Eine Renderziel ist eine Ressource, in die wir am Ende eines Renderingdurchgangs schreiben können.</span><span class="sxs-lookup"><span data-stu-id="db217-290">A render target is a resource that we can write to at the end of a render pass.</span></span> <span data-ttu-id="db217-291">Es wird häufig mit der [ID3D11Device::CreateRenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476517.aspx)-Methode erstellt, mit der Hintergrundpuffer-Swapkette (die auch eine Ressource ist) als Eingabeparameter.</span><span class="sxs-lookup"><span data-stu-id="db217-291">It is commonly created using the [ID3D11Device::CreateRenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476517.aspx) method using the swap chain back buffer (which is also a resource) as the input parameter.</span></span> 

<span data-ttu-id="db217-292">Jedes Renderziel sollte auch eine entsprechende Tiefenschablonenansicht haben, da wir [OMSetRenderTargets](https://msdn.microsoft.com/library/windows/desktop/ff476464.aspx) zum Festlegen des Renderziel vor der Verwendung verwenden, was auch eine Tiefenschablonenansicht erfordert.</span><span class="sxs-lookup"><span data-stu-id="db217-292">Each render target should also have a corresponding depth-stencil view because when we use [OMSetRenderTargets](https://msdn.microsoft.com/library/windows/desktop/ff476464.aspx) to set the render target before using it, it requires also a depth-stencil view.</span></span> <span data-ttu-id="db217-293">Wir greifen auf die Renderzielressource über die implementierte Renderzielansicht mit der [ID3D11RenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476582.aspx)-Schnittstelle zu.</span><span class="sxs-lookup"><span data-stu-id="db217-293">We access the render target resource through the render target view implemented using the [ID3D11RenderTargetView](https://msdn.microsoft.com/library/windows/desktop/ff476582.aspx) interface.</span></span> 

#### <a name="device"></a><span data-ttu-id="db217-294">Gerät</span><span class="sxs-lookup"><span data-stu-id="db217-294">Device</span></span>

<span data-ttu-id="db217-295">Für Benutzer, die mit Direct3D11 nicht vertraut sind, ist dies ein Gerät zum Zuordnen und zerstören von Objekten, um Grundtypen zu rendern und mit der Grafikkarte über die Grafiktreiber zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="db217-295">For those who are new to Direct3D 11, you can imagine a device as a way to allocate and destroy objects, render primitives, and communicate with the graphics card through the graphics driver.</span></span> 

<span data-ttu-id="db217-296">Oder präzise ausgedrückt: Direct3D-Gerät ist die Komponente zum Rendern von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="db217-296">For a more precise explanation, a Direct3D device is the rendering component of Direct3D.</span></span> <span data-ttu-id="db217-297">Ein Gerät kapselt und speichert den Renderstatus, führt Transformationen und Beleuchtungsvorgänge aus, und rastert ein Bild zu einer Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="db217-297">A device encapsulates and stores the rendering state, performs transformations and lighting operations, and rasterizes an image to a surface.</span></span> <span data-ttu-id="db217-298">Weitere Informationen finden Sie unter [Geräte](../graphics-concepts/devices.md)</span><span class="sxs-lookup"><span data-stu-id="db217-298">For more information, see [Devices](../graphics-concepts/devices.md)</span></span>

<span data-ttu-id="db217-299">Ein Gerät wird durch die [ID3D11Device](https://msdn.microsoft.com/library/windows/desktop/ff476379.aspx)-Schnittstelle dargestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-299">A device is represented by the [ID3D11Device](https://msdn.microsoft.com/library/windows/desktop/ff476379.aspx) interface.</span></span> <span data-ttu-id="db217-300">In anderen Worten: die ID3D11Device-Schnittstelle stellt eine virtuelle Grafikkarte dar und wird verwendet, um die Ressourcen zu erstellen, die das Gerät besitzt.</span><span class="sxs-lookup"><span data-stu-id="db217-300">In other words, the ID3D11Device interface represents a virtual display adapter and is used to create resources that are owned by a device.</span></span> 

<span data-ttu-id="db217-301">Beachten Sie, dass es verschiedene Versionen von ID3D11Device gibt, [ID3D11Device5](https://msdn.microsoft.com/library/windows/desktop/mt492478.aspx) ist die neueste Version und fügt neue Informationen zum ID3D11Device4 hinzu.</span><span class="sxs-lookup"><span data-stu-id="db217-301">Note that there are different versions of ID3D11Device, [ID3D11Device5](https://msdn.microsoft.com/library/windows/desktop/mt492478.aspx) is the latest version and adds new methods to those in ID3D11Device4.</span></span> <span data-ttu-id="db217-302">Weitere Informationen zur Kommunikation zwischen Direct3D mit der zugrunde liegenden Hardware finden Sie unter [Windows Device Driver Model (WDDM)-Architektur](https://docs.microsoft.com/windows-hardware/drivers/display/windows-vista-and-later-display-driver-model-architecture).</span><span class="sxs-lookup"><span data-stu-id="db217-302">For more information on how Direct3D communicates with the underlying hardware, see [Windows Device Driver Model (WDDM) architecture](https://docs.microsoft.com/windows-hardware/drivers/display/windows-vista-and-later-display-driver-model-architecture).</span></span>

<span data-ttu-id="db217-303">Jede Anwendung muss mindestens ein Gerät haben, die meisten Apps erstellen nur ein Gerät.</span><span class="sxs-lookup"><span data-stu-id="db217-303">Each application must have at least one device, most applications only create one device.</span></span> <span data-ttu-id="db217-304">Erstellen Sie ein Gerät für die auf Ihrem Computer installierten Hardwaretreiber, durch den Aufruf von __D3D11CreateDevice__ oder __D3D11CreateDeviceAndSwapChain__ und geben Sie den Treiber mit dem Flag D3D\_DRIVER\_TYPE an.</span><span class="sxs-lookup"><span data-stu-id="db217-304">Create a device for one of the hardware drivers installed on your machine by calling __D3D11CreateDevice__ or __D3D11CreateDeviceAndSwapChain__ and specifying the driver type with the D3D\_DRIVER\_TYPE flag.</span></span> <span data-ttu-id="db217-305">Jedes Gerät kann einen oder mehrere Gerätekontexte benutzen, je nach Bedarf der gewünschten Funktion.</span><span class="sxs-lookup"><span data-stu-id="db217-305">Each device can use one or more device contexts, depending on the functionality desired.</span></span> <span data-ttu-id="db217-306">Weitere Informationen finden Sie unter [D3D11CreateDevice-Funktion](https://msdn.microsoft.com/library/windows/desktop/ff476082.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-306">For more information, see [D3D11CreateDevice function](https://msdn.microsoft.com/library/windows/desktop/ff476082.aspx).</span></span>

#### <a name="device-context"></a><span data-ttu-id="db217-307">Gerätekontext</span><span class="sxs-lookup"><span data-stu-id="db217-307">Device context</span></span>

<span data-ttu-id="db217-308">Der Gerätekontext wird verwendet, um den [Pipelinestatus](#rendering-pipeline) festzulegen und Renderbefehle mit [Ressourcen](#resource) eines [Geräts](#device) zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="db217-308">A device context is used to set [pipeline](#rendering-pipeline) state and generate rendering commands using the [resources](#resource) owned by a [device](#device).</span></span> 

<span data-ttu-id="db217-309">Direct3D11 implementiert zwei Arten von Gerätekontexten, eins für das sofortige Rendern und das andere für das verzögerte Rendern. Beide Kontexte werden durch eine [ID3D11DeviceContext](https://msdn.microsoft.com/library/windows/desktop/ff476385.aspx)-Schnittstelle dargestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-309">Direct3D 11 implements two types of device contexts, one for immediate rendering and the other for deferred rendering; both contexts are represented with an [ID3D11DeviceContext](https://msdn.microsoft.com/library/windows/desktop/ff476385.aspx) interface.</span></span>  

<span data-ttu-id="db217-310">Die __ID3D11DeviceContext__-Schnittstellen haben unterschiedliche Versionen; __ID3D11DeviceContext4__ fügt neue Methoden zu __ID3D11DeviceContext3__ hinzu.</span><span class="sxs-lookup"><span data-stu-id="db217-310">The __ID3D11DeviceContext__ interfaces have different versions; __ID3D11DeviceContext4__ adds new methods to those in __ID3D11DeviceContext3__.</span></span>

<span data-ttu-id="db217-311">Hinweis: __ID3D11DeviceContext4__ wird im Windows10 Creators Update eingeführt und ist die neueste Version der __ID3D11DeviceContext__-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="db217-311">Note: __ID3D11DeviceContext4__ is introduced in the Windows 10 Creators Update and is the latest version of the __ID3D11DeviceContext__ interface.</span></span> <span data-ttu-id="db217-312">Anwendungen für das Windows10 Creators Update sollten diese Schnittstelle anstelle von früheren Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="db217-312">Applications targeting Windows 10 Creators Update should use this interface instead of earlier versions.</span></span> <span data-ttu-id="db217-313">Weitere Informationen finden Sie unter [ID3D11DeviceContext4](https://msdn.microsoft.com/library/windows/desktop/mt492481.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-313">For more information, see [ID3D11DeviceContext4](https://msdn.microsoft.com/library/windows/desktop/mt492481.aspx).</span></span>

#### <a name="dxdeviceresources"></a><span data-ttu-id="db217-314">DX::DeviceResources</span><span class="sxs-lookup"><span data-stu-id="db217-314">DX::DeviceResources</span></span>

<span data-ttu-id="db217-315">Die __DX::DeviceResources__-Klasse befindet sich in der __DeviceResources.cpp__/__.h__-Datei und steuert alle Geräteressourcen von DirectX.</span><span class="sxs-lookup"><span data-stu-id="db217-315">The __DX::DeviceResources__ class is in the __DeviceResources.cpp__/__.h__ files and controls all of DirectX device resources.</span></span> <span data-ttu-id="db217-316">In dem Spiele-Beispielprojekt und der DirectX11-App-Projektvorlage, befinden sich diese Dateien im Ordner __Commons__.</span><span class="sxs-lookup"><span data-stu-id="db217-316">In the sample game project and the DirectX 11 App template project, these files are in the __Commons__ folder.</span></span> <span data-ttu-id="db217-317">Sie können auf die neueste Version dieser Dateien zuzugreifen, wenn Sie ein neues DirectX11-App-Vorlageprojekt in Visual Studio2015 oder höher erstellen.</span><span class="sxs-lookup"><span data-stu-id="db217-317">You can grab the latest version of these files when you create a new DirectX 11 App template project in Visual Studio 2015 or later.</span></span>

### <a name="buffer"></a><span data-ttu-id="db217-318">Puffer</span><span class="sxs-lookup"><span data-stu-id="db217-318">Buffer</span></span>

<span data-ttu-id="db217-319">Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-319">A buffer resource is a collection of fully typed data grouped into elements.</span></span> <span data-ttu-id="db217-320">Verwenden Sie Puffer zum Speichern von Daten, wie Positionsvektoren, normale Vektoren, Texturkoordinaten in einem Vertexpuffer, Indexe in einem Indexpuffer oder den Gerätezustand.</span><span class="sxs-lookup"><span data-stu-id="db217-320">You can use buffers to store a wide variety of data, including position vectors, normal vectors, texture coordinates in a vertex buffer, indexes in an index buffer, or device state.</span></span> <span data-ttu-id="db217-321">Pufferelemente können gepackte Datenwerten (wie R8G8B8A8-Oberflächenwerte), einzelne 8-Bit-Ganzahlen oder vier 32-Bit-Gleitkommawerte enthalten.</span><span class="sxs-lookup"><span data-stu-id="db217-321">Buffer elements can include packed data values (like R8G8B8A8 surface values), single 8-bit integers, or four 32-bit floating point values.</span></span>

<span data-ttu-id="db217-322">Es sind drei Arten von Puffern verfügbar: Vertex-Puffer, Indexpuffer und Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="db217-322">There are three types of buffers available: Vertex buffer, index buffer, and constant buffer.</span></span>

#### <a name="vertex-buffer"></a><span data-ttu-id="db217-323">Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="db217-323">Vertex Buffer</span></span>

<span data-ttu-id="db217-324">Enthält Scheitelpunktdaten, die zur Definition Ihrer Geometrie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="db217-324">Contains the vertex data used to define your geometry.</span></span> <span data-ttu-id="db217-325">Zu den Scheitelpunktdaten gehören Positionskoordinaten, Farbdaten, Texturkoordinatendaten, Normale-Daten usw.</span><span class="sxs-lookup"><span data-stu-id="db217-325">Vertex data includes position coordinates, color data, texture coordinate data, normal data, and so on.</span></span> 

#### <a name="index-buffer"></a><span data-ttu-id="db217-326">Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="db217-326">Index Buffer</span></span>

<span data-ttu-id="db217-327">Enthalten Ganzzahl-Offsets in Vertexpuffern und werden zum effizienteren Rendern der Grundtypen verwendet.</span><span class="sxs-lookup"><span data-stu-id="db217-327">Contains integer offsets into vertex buffers and are used to render primitives more efficiently.</span></span> <span data-ttu-id="db217-328">Ein Indexpuffer enthält eine aufeinanderfolgende Reihe von 16-Bit- oder 32-Bit-Indizes; jeder Index wird verwendet, um einen Scheitelpunkt im Vertexpuffer zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="db217-328">An index buffer contains a sequential set of 16-bit or 32-bit indices; each index is used to identify a vertex in a vertex buffer.</span></span>

#### <a name="constant-buffer-or-shader-constant-buffer"></a><span data-ttu-id="db217-329">Konstantenpuffer oder Shader-Konstantenpuffer</span><span class="sxs-lookup"><span data-stu-id="db217-329">Constant Buffer or shader-constant buffer</span></span>

<span data-ttu-id="db217-330">Ermöglicht Ihnen, Shader-Daten effizient an die Pipeline zu liefern.</span><span class="sxs-lookup"><span data-stu-id="db217-330">Allows you to efficiently supply shader data to the pipeline.</span></span> <span data-ttu-id="db217-331">Sie können Konstantenpuffer als Eingabe für die Shader verwenden, die für jeden Grundtyp ausgeführt werden und die Ergebnisse der Stream-Ausgabe-Stufe der Renderingpipeline speichern.</span><span class="sxs-lookup"><span data-stu-id="db217-331">You can use constant buffers as inputs to the shaders that run for each primitive and store results of the stream-output stage of the rendering pipeline.</span></span> <span data-ttu-id="db217-332">Vom Konzept her sieht ein Konstantenpuffer wie ein Vertexpuffer mit einem Element aus.</span><span class="sxs-lookup"><span data-stu-id="db217-332">Conceptually, a constant buffer looks just like a single-element vertex buffer.</span></span>

#### <a name="design-and-implementation-of-buffers"></a><span data-ttu-id="db217-333">Entwurf und -Implementierung der Puffer</span><span class="sxs-lookup"><span data-stu-id="db217-333">Design and implementation of buffers</span></span>

<span data-ttu-id="db217-334">Sie können Puffer basierend auf den Datentypen entwickeln, z.B., wie in unserem Spielbeispiel, wobei ein Puffer für statische Daten erstellt wird, ein weiterer für Daten, die innerhalb eines Frames konstant sind und eine weiterer für Daten, die speziell für einen Grundtyp gelten.</span><span class="sxs-lookup"><span data-stu-id="db217-334">You can design buffers based on the data type, for example, like in our game sample, one buffer is created for static data, another for data that's constant over the frame, and another for data that's specific to a primitive.</span></span>

<span data-ttu-id="db217-335">Alle Puffertypen sind von der __ID3D11Buffer__-Schnittstelle gekapselt, und Sie können eine Pufferressource erstellen, indem Sie __id3d11Device:: CreateBuffer__ aufrufen.</span><span class="sxs-lookup"><span data-stu-id="db217-335">All buffer types are encapsulated by the __ID3D11Buffer__ interface and you can create a buffer resource by calling __ID3D11Device::CreateBuffer__.</span></span> <span data-ttu-id="db217-336">E Puffer muss in der Pipeline gebunden werden, damit darauf zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="db217-336">But a buffer must be bound to the pipeline before it can be accessed.</span></span> <span data-ttu-id="db217-337">Puffer können zum Lesen nicht gleichzeitig mit mehreren Phasen der Pipeline gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="db217-337">Buffers can be bound to multiple pipeline stages simultaneously for reading.</span></span> <span data-ttu-id="db217-338">Ein Puffer kann auch an eine einzelne Pipelinephase zum Schreiben gebunden werden. Allerdings kann nicht der gleiche Puffer zum Lesen und Schreiben gleichzeitig gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="db217-338">A buffer can also be bound to a single pipeline stage for writing; however, the same buffer cannot be bound for reading and writing simultaneously.</span></span>

<span data-ttu-id="db217-339">Binden Sie Puffer an:</span><span class="sxs-lookup"><span data-stu-id="db217-339">Bind buffers to the:</span></span>
    * <span data-ttu-id="db217-340">den Eingabeassemblerzustand durch Aufrufen der __ID3D11DeviceContext__-Methoden, wie __ID3D11DeviceContext::IASetVertexBuffers__ und __ID3D11DeviceContext::IASetIndexBuffer__</span><span class="sxs-lookup"><span data-stu-id="db217-340">Input-assembler stage by calling __ID3D11DeviceContext__ methods like __ID3D11DeviceContext::IASetVertexBuffers__ and __ID3D11DeviceContext::IASetIndexBuffer__</span></span>
    * <span data-ttu-id="db217-341">Die Streamoutputstufe durch Aufrufen von __ID3D11DeviceContext::SOSetTargets__</span><span class="sxs-lookup"><span data-stu-id="db217-341">Stream-output stage by calling __ID3D11DeviceContext::SOSetTargets__</span></span>
    * <span data-ttu-id="db217-342">Die Shader-Stufe durch Aufrufen der Shader-Methoden, wie __id3d11DeviceContext:: VSSetConstantBuffers__</span><span class="sxs-lookup"><span data-stu-id="db217-342">Shader stage by calling shader methods, like __ID3D11DeviceContext::VSSetConstantBuffers__</span></span>

<span data-ttu-id="db217-343">Weitere Informationen zu finden Sie unter [Einführung in Puffer in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-343">For more information, see [Introduction to buffers in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898.aspx).</span></span>

### <a name="dxgi"></a><span data-ttu-id="db217-344">DXGI</span><span class="sxs-lookup"><span data-stu-id="db217-344">DXGI</span></span>

<span data-ttu-id="db217-345">Microsoft DirectX Graphics Infrastructure (DXGI) ist ein neues Subsystem, das mit WindowsVista eingeführt wurde, die Low-Level-Aufgaben umfasst, die von Direct3D 10 benötigt werden 10.1, 11 und 11.1.</span><span class="sxs-lookup"><span data-stu-id="db217-345">Microsoft DirectX Graphics Infrastructure (DXGI) is a new subsystem that was introduced with WindowsVista that encapsulates some of the low-level tasks that are needed by Direct3D 10, 10.1, 11, and 11.1.</span></span> <span data-ttu-id="db217-346">Bei Verwendung von DXGI in einer Multithread-Anwendung ist besondere Vorsicht geboten, um sicherzustellen, dass keine Deadlocks auftreten.</span><span class="sxs-lookup"><span data-stu-id="db217-346">Special care must be taken when using DXGI in a multithreaded application to ensure that deadlocks do not occur.</span></span> <span data-ttu-id="db217-347">Weitere Informationen finden Sie unter [DirectX Graphics Infrastructure (DXGI): Best Practices – Multithreading](https://msdn.microsoft.com/library/windows/desktop/ee417025.aspx#multithreading_and_dxgi)</span><span class="sxs-lookup"><span data-stu-id="db217-347">For more info, see [DirectX Graphics Infrastructure (DXGI): Best Practices- Multithreading](https://msdn.microsoft.com/library/windows/desktop/ee417025.aspx#multithreading_and_dxgi)</span></span>

### <a name="feature-level"></a><span data-ttu-id="db217-348">Featureebene</span><span class="sxs-lookup"><span data-stu-id="db217-348">Feature Level</span></span>

<span data-ttu-id="db217-349">Die Featureebene ist ein Konzept, das in Direct3D11 eingeführt wurde, um die Vielfalt der Grafikkarten in neuen und vorhandenen Computern zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="db217-349">Feature level is a concept introduced in Direct3D 11 to handle the diversity of video cards in new and existing machines.</span></span> <span data-ttu-id="db217-350">Eine Featureebene ist ein klar definierter Satz mit GPU-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="db217-350">A feature level is a well defined set of graphics processing unit (GPU) functionality.</span></span> 

<span data-ttu-id="db217-351">Jede Grafikkarte implementiert eine gewisse DirectX-Funktion, abhängig von den installierten GPUs.</span><span class="sxs-lookup"><span data-stu-id="db217-351">Each video card implements a certain level of DirectX functionality depending on the GPUs installed.</span></span> <span data-ttu-id="db217-352">In früheren Versionen von Microsoft Direct3D konnten Sie die Version der implementierten Direct3D-Grafikkarte sehen und die Anwendung entsprechend programmieren.</span><span class="sxs-lookup"><span data-stu-id="db217-352">In prior versions of Microsoft Direct3D, you could find out the version of Direct3D the video card implemented, and then program your application accordingly.</span></span> 

<span data-ttu-id="db217-353">Mit der Featureebene können Sie bei der Erstellung eines Geräts versuchen, ein Gerät für die Featureebene zu erstellen, die Sie anfordern möchten.</span><span class="sxs-lookup"><span data-stu-id="db217-353">With feature level, when you create a device, you can attempt to create a device for the feature level that you want to request.</span></span> <span data-ttu-id="db217-354">Wenn die Geräteerstellung funktioniert, ist die Featureebene vorhanden, andernfalls wird die Featureebene von der Hardware nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="db217-354">If the device creation works, that feature level exists, if not, the hardware does not support that feature level.</span></span> <span data-ttu-id="db217-355">Sie können entweder versuchen, ein Gerät auf einer niedrigeren Featureebene neu zu erstellen oder Sie können die Anwendung beenden.</span><span class="sxs-lookup"><span data-stu-id="db217-355">You can either try to recreate a device at a lower feature level or you can choose to exit the application.</span></span> <span data-ttu-id="db217-356">Beispielsweise muss die Featureebene 12\_0 Direct3D11.3 oder Direct3D12 und Shadermodell 5.1 ausführen.</span><span class="sxs-lookup"><span data-stu-id="db217-356">For instance, the 12\_0 feature level requires Direct3D 11.3 or Direct3D 12, and shader model 5.1.</span></span> <span data-ttu-id="db217-357">Weitere Informationen finden Sie unter [Direct3D-Featureebenen: Übersicht über jede Featureebene](https://msdn.microsoft.com/library/windows/desktop/ff476876.aspx#Overview).</span><span class="sxs-lookup"><span data-stu-id="db217-357">For more information, see [Direct3D feature levels: Overview for each feature level](https://msdn.microsoft.com/library/windows/desktop/ff476876.aspx#Overview).</span></span>

<span data-ttu-id="db217-358">Mithilfe von featureebenen, können Sie eine Anwendung für Direct3D9 oder Microsoft Direct3D10, Direct3D11 entwickeln und führen Sie diese auf 9, 10 oder 11 Hardware (mit einigen Ausnahmen).</span><span class="sxs-lookup"><span data-stu-id="db217-358">Using feature levels, you can develop an application for Direct3D9, Microsoft Direct3D10, or Direct3D11, and then run it on 9, 10, or 11 hardware (with some exceptions).</span></span> <span data-ttu-id="db217-359">Weitere Informationen finden Sie unter [Direct3D-Featureebenen](https://msdn.microsoft.com/library/windows/desktop/ff476876.aspx).</span><span class="sxs-lookup"><span data-stu-id="db217-359">For more information, see [Direct3D feature levels](https://msdn.microsoft.com/library/windows/desktop/ff476876.aspx).</span></span>

### <a name="stereo-rendering"></a><span data-ttu-id="db217-360">Stereorendering</span><span class="sxs-lookup"><span data-stu-id="db217-360">Stereo rendering</span></span>

<span data-ttu-id="db217-361">Stereorendering wird verwendet, um die Illusion der Tiefe zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="db217-361">Stereo rendering is used to enhance the illusion of depth.</span></span> <span data-ttu-id="db217-362">Er verwendet zwei Bilder, eine vom linken Auge und das andere vom rechten Auge, um eine Szene auf dem Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="db217-362">It uses two images, one from the left eye and the other from the right eye to display a scene on the display screen.</span></span> 

<span data-ttu-id="db217-363">Mathematisch gesehen verwenden wir eine Stereo-Projektionsmatrix, die einen leicht horizontalen Versatz nach rechts und links neben der regulären Mono-Projektionsmatrix hat, um dies zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="db217-363">Mathematically, we apply a stereo projection matrix, which is a slight horizontal offset to the right and to the left, of the regular mono projection matrix to achieve this.</span></span>

<span data-ttu-id="db217-364">Wir haben zwei Renderingdurchgänge, um Stereorendering in diesem Beispielspiel zu erreichen:</span><span class="sxs-lookup"><span data-stu-id="db217-364">We did two rendering passes to achieve stereo rendering in this game sample:</span></span>
* <span data-ttu-id="db217-365">Binden Sie diese an das rechte Renderziel, wenden Sie die rechte Projektion an und Zeichnen Sie das Grundtypobjekt.</span><span class="sxs-lookup"><span data-stu-id="db217-365">Bind to right render target, apply right projection, then draw the primitive object.</span></span>
* <span data-ttu-id="db217-366">Binden Sie diese an das linke Renderziel, wenden Sie die linke Projektion an und Zeichnen Sie das Grundtypobjekt.</span><span class="sxs-lookup"><span data-stu-id="db217-366">Bind to left render target, apply left projection, then draw the primitive object.</span></span>

### <a name="camera-and-coordinate-space"></a><span data-ttu-id="db217-367">Kamera und Koordinatenraum</span><span class="sxs-lookup"><span data-stu-id="db217-367">Camera and coordinate space</span></span>

<span data-ttu-id="db217-368">Das Spiel enthält den erforderlichen Code, um die Spielwelt in seinem eigenen Koordinatensystem (auch als Spielweltbereich oder Szenenbereich bezeichnet) zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="db217-368">The game has the code in place to update the world in its own coordinate system (sometimes called the world space or scene space).</span></span> <span data-ttu-id="db217-369">Alle Objekte, einschließlich der Kamera, werden in diesem Bereich positioniert und ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="db217-369">All objects, including the camera, are positioned and oriented in this space.</span></span> <span data-ttu-id="db217-370">Weitere Informationen zu Standortsystemen finden Sie unter [Koordinatensysteme](../graphics-concepts/coordinate-systems.md)..</span><span class="sxs-lookup"><span data-stu-id="db217-370">For more information, see [Coordinate systems](../graphics-concepts/coordinate-systems.md).</span></span>

<span data-ttu-id="db217-371">Ein Vertexshader übernimmt die schwere Aufgabe, die Modellkoordinaten mit dem folgenden Algorithmus in die Gerätekoordinaten zu konvertieren (wobei V ein Vektor und M eine Matrix ist).</span><span class="sxs-lookup"><span data-stu-id="db217-371">A vertex shader does the heavy lifting of converting from the model coordinates to device coordinates with the following algorithm (where V is a vector and M is a matrix).</span></span>

<span data-ttu-id="db217-372">V(Gerät) = V(Modell) x M(model-to-world) x M(world-to-view) x M(view-to-device).</span><span class="sxs-lookup"><span data-stu-id="db217-372">V(device) = V(model) x M(model-to-world) x M(world-to-view) x M(view-to-device).</span></span>

<span data-ttu-id="db217-373">Dabei gilt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="db217-373">where:</span></span> 
* <span data-ttu-id="db217-374">M(Model-to-World) ist eine Transformationsmatrix für die Modellkoordinaten in Spielweltkoordinaten, auch bekannt als die [World transform matrix](#world-transform-matrix).</span><span class="sxs-lookup"><span data-stu-id="db217-374">M(model-to-world) is a transformation matrix for model coordinates to world coordinates, also known as the [World transform matrix](#world-transform-matrix).</span></span> <span data-ttu-id="db217-375">Diese Matrix wird vom Grundtyp bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-375">This is provided by the primitive.</span></span>
* <span data-ttu-id="db217-376">M(world-to-view) ist eine Transformationsmatrix für die Weltkoordinaten in Spielansichtskoordinaten, auch bekannt als die [Ansichtstransformationsmatrix](#view-transform-matrix).</span><span class="sxs-lookup"><span data-stu-id="db217-376">M(world-to-view) is a transformation matrix for world coordinates to view coordinates, also known as the [View transform matrix](#view-transform-matrix).</span></span>
    * <span data-ttu-id="db217-377">Diese Matrix wird von der Ansichtsmatrix der Kamera bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-377">This is provided by the view matrix of the camera.</span></span> <span data-ttu-id="db217-378">Es wird durch die Position der Kamera und die Blickvektoren definiert (der Vektor "anschauen", der von der Kamera in die Szene weist, und der Vektor "nach oben schauen" senkrecht zur Szene).</span><span class="sxs-lookup"><span data-stu-id="db217-378">It's defined by the camera's position along with the look vectors (the "look at" vector that points directly into the scene from the camera, and the "look up" vector that is upwards perpendicular to it)</span></span>
    * <span data-ttu-id="db217-379">Im Beispielspiel ist __m\_viewMatrix__ die Ansichtstransformationsmatrix und wird mit __Camera::SetViewParams__ berechnet</span><span class="sxs-lookup"><span data-stu-id="db217-379">In the sample game, __m\_viewMatrix__ is the view transformation matrix and is calculated using __Camera::SetViewParams__</span></span> 
* <span data-ttu-id="db217-380">M(view-to-device) ist eine Transformationsmatrix für die Ansichtskoordinaten in Gerätekoordinaten, auch bekannt als die [Projektstransformationsmatrix](#projection-transform-matrix).</span><span class="sxs-lookup"><span data-stu-id="db217-380">M(view-to-device) is a transformation matrix for view coordinates to device coordinates, also known as the [Projection transform matrix](#projection-transform-matrix)</span></span>
    * <span data-ttu-id="db217-381">Diese Matrix wird von der Projektion der Kamera bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="db217-381">This is provided by the projection of the camera.</span></span> <span data-ttu-id="db217-382">Es enthält Informationen darüber, wie dieser Platz tatsächlich in der endgültigen Szene sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="db217-382">It provides info how much of that space is actually visible in the final scene.</span></span> <span data-ttu-id="db217-383">Das Blickfeld (FoV), das Seitenverhältnis und die Clippingebenen definieren die Projektionstransformationsmatrix.</span><span class="sxs-lookup"><span data-stu-id="db217-383">The Field of View (FoV), aspect ratio, and clipping planes define the projection transform matrix.</span></span>
    * <span data-ttu-id="db217-384">Im Beispielspiel definiert __m\_projectionMatrix__ die Transformation der Projektionskoordinaten, berechnet mithilfe von __Camera::SetProjParams__ (für die Stereoprojektion verwenden Sie zwei Projektionsmatrizen: eine für die Ansicht jedes Auges.)</span><span class="sxs-lookup"><span data-stu-id="db217-384">In the sample game, __m\_projectionMatrix__ defines transformation to the projection coordinates, calculated using __Camera::SetProjParams__ (For stereo projection, you use two projection matrices: one for each eye's view.)</span></span> 

<span data-ttu-id="db217-385">Der Shadercode in VertexShader.hlsl wird mit diesen Vektoren und Matrizen aus den Konstantenpuffern geladen und führt diese Transformation für jeden Vertex aus.</span><span class="sxs-lookup"><span data-stu-id="db217-385">The shader code in VertexShader.hlsl is loaded with these vectors and matrices from the constant buffers, and performs this transformation for every vertex.</span></span>

### <a name="coordinate-transformation"></a><span data-ttu-id="db217-386">Koordinatentransformation</span><span class="sxs-lookup"><span data-stu-id="db217-386">Coordinate transformation</span></span>

<span data-ttu-id="db217-387">Direct3D verwendet drei Transformationen, um Ihre 3D-Modell-Koordinaten in Pixelkoordinaten zu verwandeln (Bildschirmbereich).</span><span class="sxs-lookup"><span data-stu-id="db217-387">Direct3D uses three transformations to change your 3D model coordinates into pixel coordinates (screen space).</span></span> <span data-ttu-id="db217-388">Diese Transformationen sind die globale Transformation, die Ansichtstransformation und Projektionstransformation.</span><span class="sxs-lookup"><span data-stu-id="db217-388">These transformations are world transform, view transform, and projection transform.</span></span> <span data-ttu-id="db217-389">Weitere Informationen finden Sie unter [Übersicht über Transformationen](../graphics-concepts/transform-overview.md).</span><span class="sxs-lookup"><span data-stu-id="db217-389">For more info, go to [Transform overview](../graphics-concepts/transform-overview.md).</span></span>

#### <a name="world-transform-matrix"></a><span data-ttu-id="db217-390">Welttransformationsmatrix</span><span class="sxs-lookup"><span data-stu-id="db217-390">World transform matrix</span></span>

<span data-ttu-id="db217-391">Eine Welttransformationsmatrix ändert die Koordinaten des Modellbereichs, in dem Scheitelpunkte definiert werden, die relativ zum lokalen Ursprung des Modells im Weltraum sind, wo Scheitelpunkte relativ zum Ursprung für alle Objekte in einer Szene definiert werden.</span><span class="sxs-lookup"><span data-stu-id="db217-391">A world transform changes coordinates from model space, where vertices are defined relative to a model's local origin, to world space, where vertices are defined relative to an origin common to all the objects in a scene.</span></span> <span data-ttu-id="db217-392">Die Welttransformation platziert ein Modell in der Welt, daher ihr Name.</span><span class="sxs-lookup"><span data-stu-id="db217-392">In essence, the world transform places a model into the world; hence its name.</span></span> <span data-ttu-id="db217-393">Weitere Informationen finden Sie unter [Welttransformationen](../graphics-concepts/world-transform.md).</span><span class="sxs-lookup"><span data-stu-id="db217-393">For more information, see [World transform](../graphics-concepts/world-transform.md).</span></span>

####  <a name="view-transform-matrix"></a><span data-ttu-id="db217-394">Ansichtstransformationsmatrix</span><span class="sxs-lookup"><span data-stu-id="db217-394">View transform matrix</span></span>

<span data-ttu-id="db217-395">Die Ansichtstransformation lokalisiert den Betrachter im Weltbereich und transformiert dazu Scheitelpunkte in den Kamerabereich.</span><span class="sxs-lookup"><span data-stu-id="db217-395">The view transform locates the viewer in world space, transforming vertices into camera space.</span></span> <span data-ttu-id="db217-396">Im Kamerabereich befindet sich die Kamera, bzw. der Betrachter, am Ursprungspunkt und blickt in die positive z-Richtung.</span><span class="sxs-lookup"><span data-stu-id="db217-396">In camera space, the camera, or viewer, is at the origin, looking in the positive z-direction.</span></span> <span data-ttu-id="db217-397">Weitere Informationen finden Sie unter [Ansichtstransformation](../graphics-concepts/view-transform.md).</span><span class="sxs-lookup"><span data-stu-id="db217-397">For more info, go to [View transform](../graphics-concepts/view-transform.md).</span></span>

####  <a name="projection-transform-matrix"></a><span data-ttu-id="db217-398">Projektionstransformationsmatrix</span><span class="sxs-lookup"><span data-stu-id="db217-398">Projection transform matrix</span></span>

<span data-ttu-id="db217-399">Die Projektionstransformation konvertiert das Ansichtsfrustum in eine Quaderform.</span><span class="sxs-lookup"><span data-stu-id="db217-399">The projection transform converts the viewing frustum to a cuboid shape.</span></span> <span data-ttu-id="db217-400">Ein Pyramidenstumpf ist ein 3D-Körper in einer Szene, der relativ zur Viewport-Kamera positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="db217-400">A viewing frustum is a 3D volume in a scene positioned relative to the viewport's camera.</span></span> <span data-ttu-id="db217-401">Ein Viewport ist ein 2D-Rechteck, auf das eine 3D-Szene projiziert wird.</span><span class="sxs-lookup"><span data-stu-id="db217-401">A viewport is a 2D rectangle into which a 3D scene is projected.</span></span> <span data-ttu-id="db217-402">Weitere Informationen finden Sie unter [Viewports und Zuschneiden](../graphics-concepts/viewports-and-clipping.md).</span><span class="sxs-lookup"><span data-stu-id="db217-402">For more information, see [Viewports and clipping](../graphics-concepts/viewports-and-clipping.md)</span></span>

<span data-ttu-id="db217-403">Da das nähergelegene Ende des Ansichtsfrustrums kleiner als das weiter entfernt liegende Ende, hat dies die Wirkung, dass näher bei der Kamera liegende Objekte erweitert werden. So wird Perspektive auf die Szene angewandt.</span><span class="sxs-lookup"><span data-stu-id="db217-403">Because the near end of the viewing frustum is smaller than the far end, this has the effect of expanding objects that are near to the camera; this is how perspective is applied to the scene.</span></span> <span data-ttu-id="db217-404">Daher erscheinen Objekte, die näher am Spieler sind, größer; Objekte, die weiter entfernt sind, werden kleiner angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db217-404">So objects that are closer to the player, appear larger; objects that are further away, appear smaller.</span></span>

<span data-ttu-id="db217-405">Die Projektionstransformation ist mathematisch gesehen eine Matrix, die in der Regel eine Skalierung und Perspektive verwendet.</span><span class="sxs-lookup"><span data-stu-id="db217-405">Mathematically, the projection transform is a matrix that is typically both a scale and perspective projection.</span></span> <span data-ttu-id="db217-406">Sie funktioniert wie die Foto-App einer Kamera.</span><span class="sxs-lookup"><span data-stu-id="db217-406">It functions like the lens of a camera.</span></span> <span data-ttu-id="db217-407">Weitere Informationen finden Sie unter [Projektionstransformationen](../graphics-concepts/projection-transform.md).</span><span class="sxs-lookup"><span data-stu-id="db217-407">For more information, see [Projection transform](../graphics-concepts/projection-transform.md).</span></span>

### <a name="sampler-state"></a><span data-ttu-id="db217-408">Musterzustand</span><span class="sxs-lookup"><span data-stu-id="db217-408">Sampler state</span></span>

<span data-ttu-id="db217-409">Der Musterzustand legt fest, wie Texturdaten verwendet werden mit Textur und deren Modi, Filtern und Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="db217-409">Sampler state determines how texture data is sampled using texture addressing modes, filtering, and level of detail.</span></span> <span data-ttu-id="db217-410">Sampling erfolgt jedes Mal, wenn ein Texturpixel oder Texel aus einer Textur gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="db217-410">Sampling is done each time a texture pixel, or texel, is read from a texture.</span></span>

<span data-ttu-id="db217-411">Eine Textur enthält ein Array von Texel oder Texturpixeln.</span><span class="sxs-lookup"><span data-stu-id="db217-411">A texture contains an array of texels, or texture pixels.</span></span> <span data-ttu-id="db217-412">Die Position des einzelnen Texels wird von (u, v) festgelegt, wobei u die Breite und v ist die Höhe ist und zwischen 0 und 1 zugeordnet ist die Texturbreite und Höhe abhängig.</span><span class="sxs-lookup"><span data-stu-id="db217-412">The position of each texel is denoted by (u,v), where u is the width and v is the height, and is mapped between 0 and 1 based on the texture width and height.</span></span> <span data-ttu-id="db217-413">Die resultierende Texturkoordinaten werden auf einem Texel beim Sampling einer Textur verwendet.</span><span class="sxs-lookup"><span data-stu-id="db217-413">The resulting texture coordinates are used to address a texel when sampling a texture.</span></span>

<span data-ttu-id="db217-414">Wenn Texturkoordinaten unter 0 oder 1 sind, definiert der Textur-Adressmodus wie die Texturkoordinate einen den Ort des Texels festlegt.</span><span class="sxs-lookup"><span data-stu-id="db217-414">When texture coordinates are below 0 or above 1, the texture address mode defines how the texture coordinate addresses a texel location.</span></span> <span data-ttu-id="db217-415">Bei Verwendung __TextureAddressMode.Clamp__ wird eine Koordinate außerhalb des 0-1-Bereichs auf einen Maximalwert von 1 und Mindestwert von 0 vor dem Sampling festgelegt.</span><span class="sxs-lookup"><span data-stu-id="db217-415">For example, when using __TextureAddressMode.Clamp__, any coordinate outside the 0-1 range is clamped to a maximum value of 1, and minimum value of 0 before sampling.</span></span>

<span data-ttu-id="db217-416">Wenn die Textur zu groß oder zu klein für das Polygon ist, wird die Textur gefiltert und dem Abstand angepasst.</span><span class="sxs-lookup"><span data-stu-id="db217-416">If the texture is too large or too small for the polygon, the texture is filtered to fit the space.</span></span> <span data-ttu-id="db217-417">Ein Vergrößerungsfilter vergrößert die Textur, ein Verkleinerungsfilter reduziert die Textur, um ihn einem kleineren Bereich anzupassen.</span><span class="sxs-lookup"><span data-stu-id="db217-417">A magnification filter enlarges a texture, a minification filter reduces the texture to fit into a smaller area.</span></span> <span data-ttu-id="db217-418">Texturvergrößerung wiederholt die Texel-Beispiel für eine oder mehrere Adressen, was ein verschwommenes Image ergibt.</span><span class="sxs-lookup"><span data-stu-id="db217-418">Texture magnification repeats the sample texel for one or more addresses which yields a blurrier image.</span></span> <span data-ttu-id="db217-419">Texturverkleinerung ist komplizierter, da es mehr als einen Texelwert in einen einzelnen Wert kombiniert.</span><span class="sxs-lookup"><span data-stu-id="db217-419">Texture minification is more complicated because it requires combining more than one texel value into a single value.</span></span> <span data-ttu-id="db217-420">Dadurch können Aliasing oder ausgefranste Ränder je nach der Texturdaten entstehen.</span><span class="sxs-lookup"><span data-stu-id="db217-420">This can cause aliasing or jagged edges depending on the texture data.</span></span> <span data-ttu-id="db217-421">Der am häufigsten verwendete Ansatz für die Verkleinerung ist die Verwendung eine Mipmap.</span><span class="sxs-lookup"><span data-stu-id="db217-421">The most popular approach for minification is to use a mipmap.</span></span> <span data-ttu-id="db217-422">Eine Mipmap ist eine Textur mit mehreren Ebenen.</span><span class="sxs-lookup"><span data-stu-id="db217-422">A mipmap is a multi-level texture.</span></span> <span data-ttu-id="db217-423">Die Größe der einzelnen Ebenen ist um eine Zweierpotenz kleiner als die vorherigen Ebenen bis zur Textur 1 x 1.</span><span class="sxs-lookup"><span data-stu-id="db217-423">The size of each level is a power-of-two smaller than the previous level down to a 1x1 texture.</span></span> <span data-ttu-id="db217-424">Wenn die Verkleinerung verwendet wird, wählt ein Spiel die Mipmap-Ebene, die am der Größe des Renderns am nächsten liegt.</span><span class="sxs-lookup"><span data-stu-id="db217-424">When minification is used, a game chooses the mipmap level closest to the size that is needed at render time.</span></span> 

### <a name="basicloader"></a><span data-ttu-id="db217-425">BasicLoader</span><span class="sxs-lookup"><span data-stu-id="db217-425">BasicLoader</span></span>

<span data-ttu-id="db217-426">__BasicLoader__ ist eine einfache Loader-Klasse für die Unterstützung beim Laden von Shader, Textur und Gitter von Dateien auf einem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="db217-426">__BasicLoader__ is a simple loader class that provides support for loading shaders, textures, and meshes from files on disk.</span></span> <span data-ttu-id="db217-427">Sie bietet synchrone und asynchrone Methoden an.</span><span class="sxs-lookup"><span data-stu-id="db217-427">It provides both synchronous and asynchronous methods.</span></span> <span data-ttu-id="db217-428">In diesem Beispielspiel befinden sich die BasicLoader.h/.cpp-Dateien im Ordner __Commons__.</span><span class="sxs-lookup"><span data-stu-id="db217-428">In this game sample, the BasicLoader.h/.cpp files are found in the __Commons__ folder.</span></span>

<span data-ttu-id="db217-429">Weitere Informationen finden Sie unter [Basic Loader](complete-code-for-basicloader.md).</span><span class="sxs-lookup"><span data-stu-id="db217-429">For more information, see [Basic Loader](complete-code-for-basicloader.md).</span></span>