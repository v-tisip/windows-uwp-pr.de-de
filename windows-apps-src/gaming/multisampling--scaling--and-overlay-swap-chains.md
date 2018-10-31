---
author: mtoepke
title: Swapchainskalierung und Überlagerungen
description: Hier erfahren Sie, wie Sie skalierte Swapchains zum schnelleren Rendern auf mobilen Geräten erstellen und Überlagerungsswapchains (falls verfügbar) verwenden, um die visuelle Qualität zu steigern.
ms.assetid: 3e4d2d19-cac3-eebc-52dd-daa7a7bc30d1
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Swapketten-Skalierung, Einblendungen, directx
ms.localizationpriority: medium
ms.openlocfilehash: 9d159a78412bea528c1a12428288daebe31d1fe1
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5818467"
---
# <a name="swap-chain-scaling-and-overlays"></a><span data-ttu-id="a67db-104">Swapchainskalierung und Überlagerungen</span><span class="sxs-lookup"><span data-stu-id="a67db-104">Swap chain scaling and overlays</span></span>



<span data-ttu-id="a67db-105">Hier erfahren Sie, wie Sie skalierte Swapchains zum schnelleren Rendern auf mobilen Geräten erstellen und Überlagerungsswapchains (falls verfügbar) verwenden, um die visuelle Qualität zu steigern.</span><span class="sxs-lookup"><span data-stu-id="a67db-105">Learn how to create scaled swap chains for faster rendering on mobile devices, and use overlay swap chains (when available) to increase the visual quality.</span></span>

## <a name="swap-chains-in-directx-112"></a><span data-ttu-id="a67db-106">Swapchains unter DirectX11.2</span><span class="sxs-lookup"><span data-stu-id="a67db-106">Swap chains in DirectX 11.2</span></span>


<span data-ttu-id="a67db-107">Unter Direct3D11.2 können Sie UWP-Apps (Universelle Windows-Plattform) mit Swapchains erstellen, die von nicht systemeigenen (reduzierten) Auflösungen skaliert werden, um höhere Füllraten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a67db-107">Direct3D 11.2 allows you to create Universal Windows Platform (UWP) apps with swap chains that are scaled up from non-native (reduced) resolutions, enabling faster fill rates.</span></span> <span data-ttu-id="a67db-108">Außerdem enthält Direct3D11.2 APIs zum Rendern mit Hardwareüberlagerungen, damit Sie eine UI in einer anderen Swapchain mit systemeigener Auflösung darstellen können.</span><span class="sxs-lookup"><span data-stu-id="a67db-108">Direct3D 11.2 also includes APIs for rendering with hardware overlays so that you can present a UI in another swap chain at native resolution.</span></span> <span data-ttu-id="a67db-109">So kann das Spiel die UI mit der höchsten systemeigenen Auflösung zeichnen und gleichzeitig eine hohe Framerate erzielen. Mobile Geräte und Anzeigen mit hohem DPI-Wert (z. B. 3840 x 2160) lassen sich auf diese Weise bestmöglich nutzen.</span><span class="sxs-lookup"><span data-stu-id="a67db-109">This allows your game to draw UI at full native resolution while maintaining a high framerate, thereby making the best use of mobile devices and high DPI displays (such as 3840 by 2160).</span></span> <span data-ttu-id="a67db-110">In diesem Artikel wird erläutert, wie Sie sich überlappende Swapchains verwenden.</span><span class="sxs-lookup"><span data-stu-id="a67db-110">This article explains how to use overlapping swap chains.</span></span>

<span data-ttu-id="a67db-111">Mit Direct3D11.2 wird auch ein neues Feature zur Erzielung einer geringeren Latenz mithilfe von Flipmodell-Swapchains eingeführt.</span><span class="sxs-lookup"><span data-stu-id="a67db-111">Direct3D 11.2 also introduces a new feature for reduced latency with flip model swap chains.</span></span> <span data-ttu-id="a67db-112">Weitere Informationen finden Sie unter [Reduzieren der Latenz mit DXGI1.3-Swapchains](reduce-latency-with-dxgi-1-3-swap-chains.md).</span><span class="sxs-lookup"><span data-stu-id="a67db-112">See [Reduce latency with DXGI 1.3 swap chains](reduce-latency-with-dxgi-1-3-swap-chains.md).</span></span>

## <a name="use-swap-chain-scaling"></a><span data-ttu-id="a67db-113">Verwenden der Swapchainskalierung</span><span class="sxs-lookup"><span data-stu-id="a67db-113">Use swap chain scaling</span></span>


<span data-ttu-id="a67db-114">Wenn Ihr Spiel nicht auf der neuesten Hardware ausgeführt wird – oder auf Hardware, die für sparsamen Betrieb optimiert ist –, kann es von Vorteil sein, Echtzeitinhalte des Spiels mit einer niedrigeren Auflösung als der Auflösung zu rendern, die das Display standardmäßig leisten kann.</span><span class="sxs-lookup"><span data-stu-id="a67db-114">When your game is running on downlevel hardware - or hardware optimized for power savings - it can be beneficial to render real-time game content at a lower resolution than the display is natively capable of.</span></span> <span data-ttu-id="a67db-115">Dazu muss die zum Rendern der Spielinhalte verwendete Swapchain kleiner als die systemeigene Auflösung sein, oder es muss ein Unterbereich der Swapchain verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a67db-115">To do this, the swap chain that is used for rendering game content must be smaller than the native resolution, or a subregion of the swapchain must be used.</span></span>

1.  <span data-ttu-id="a67db-116">Erstellen Sie zuerst eine Swapchain mit der höchstmöglichen systemeigenen Auflösung.</span><span class="sxs-lookup"><span data-stu-id="a67db-116">First, create a swap chain at full native resolution.</span></span>

    ```cpp
    DXGI_SWAP_CHAIN_DESC1 swapChainDesc = {0};

    swapChainDesc.Width = static_cast<UINT>(m_d3dRenderTargetSize.Width); // Match the size of the window.
    swapChainDesc.Height = static_cast<UINT>(m_d3dRenderTargetSize.Height);
    swapChainDesc.Format = DXGI_FORMAT_B8G8R8A8_UNORM; // This is the most common swap chain format.
    swapChainDesc.Stereo = false;
    swapChainDesc.SampleDesc.Count = 1; // Don't use multi-sampling.
    swapChainDesc.SampleDesc.Quality = 0;
    swapChainDesc.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
    swapChainDesc.BufferCount = 2; // Use double-buffering to minimize latency.
    swapChainDesc.SwapEffect = DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL; // All UWP apps must use this SwapEffect.
    swapChainDesc.Flags = 0;
    swapChainDesc.Scaling = DXGI_SCALING_STRETCH;

    // This sequence obtains the DXGI factory that was used to create the Direct3D device above.
    ComPtr<IDXGIDevice3> dxgiDevice;
    DX::ThrowIfFailed(
        m_d3dDevice.As(&dxgiDevice)
        );

    ComPtr<IDXGIAdapter> dxgiAdapter;
    DX::ThrowIfFailed(
        dxgiDevice->GetAdapter(&dxgiAdapter)
        );

    ComPtr<IDXGIFactory2> dxgiFactory;
    DX::ThrowIfFailed(
        dxgiAdapter->GetParent(IID_PPV_ARGS(&dxgiFactory))
        );

    ComPtr<IDXGISwapChain1> swapChain;
    DX::ThrowIfFailed(
        dxgiFactory->CreateSwapChainForCoreWindow(
            m_d3dDevice.Get(),
            reinterpret_cast<IUnknown*>(m_window.Get()),
            &swapChainDesc,
            nullptr,
            &swapChain
            )
        );

    DX::ThrowIfFailed(
        swapChain.As(&m_swapChain)
        );
    ```

2.  <span data-ttu-id="a67db-117">Wählen Sie anschließend einen Unterbereich der Swapchain für die Skalierung aus, indem Sie die Quellgröße auf eine niedrigere Auflösung festlegen.</span><span class="sxs-lookup"><span data-stu-id="a67db-117">Then, choose a subregion of the swap chain to scale up by setting the source size to a reduced resolution.</span></span>

    <span data-ttu-id="a67db-118">Im Beispiel zu DX-Vordergrund-Swapchains wird anhand eines Prozentsatzes eine reduzierte Größe berechnet:</span><span class="sxs-lookup"><span data-stu-id="a67db-118">The DX Foreground Swap Chains sample calculates a reduced size based on a percentage:</span></span>

    ```cpp
    m_d3dRenderSizePercentage = percentage;

    UINT renderWidth = static_cast<UINT>(m_d3dRenderTargetSize.Width * percentage + 0.5f);
    UINT renderHeight = static_cast<UINT>(m_d3dRenderTargetSize.Height * percentage + 0.5f);

    // Change the region of the swap chain that will be presented to the screen.
    DX::ThrowIfFailed(
        m_swapChain->SetSourceSize(
            renderWidth,
            renderHeight
            )
        );
    ```

3.  <span data-ttu-id="a67db-119">Erstellen Sie einen Viewport für den Unterbereich der Swapchain.</span><span class="sxs-lookup"><span data-stu-id="a67db-119">Create a viewport to match the subregion of the swap chain.</span></span>

    ```cpp
    // In Direct3D, change the Viewport to match the region of the swap
    // chain that will now be presented from.
    m_screenViewport = CD3D11_VIEWPORT(
        0.0f,
        0.0f,
        static_cast<float>(renderWidth),
        static_cast<float>(renderHeight)
        );

    m_d3dContext->RSSetViewports(1, &m_screenViewport);
    ```

4.  <span data-ttu-id="a67db-120">Bei Verwendung von Direct2D muss die Drehungstransformation angepasst werden, um die Quellregion entsprechend zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="a67db-120">If Direct2D is being used, the rotation transform needs to be adjusted to compensate for the source region.</span></span>

## <a name="create-a-hardware-overlay-swap-chain-for-ui-elements"></a><span data-ttu-id="a67db-121">Erstellen einer Hardware-ÜberlagerungsSwapchain für UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="a67db-121">Create a hardware overlay swap chain for UI elements</span></span>


<span data-ttu-id="a67db-122">Mit der Verwendung der Swapchainskalierung ist der Nachteil verbunden, dass auch die UI herunterskaliert wird und ggf. verschwimmt und schwieriger zu nutzen ist.</span><span class="sxs-lookup"><span data-stu-id="a67db-122">When using swap chain scaling, there is an inherent disadvantage in that the UI is also scaled down, potentially making it blurry and harder to use.</span></span> <span data-ttu-id="a67db-123">Auf Geräten mit Hardwareunterstützung für Überlagerungsswapchains kann dieses Problem vollständig vermieden werden, indem die UI mit der systemeigenen Auflösung in einer Swapchain gerendert wird, die von den Echtzeitinhalten des Spiels getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="a67db-123">On devices with hardware support for overlay swap chains, this problem is alleviated entirely by rendering the UI at native resolution in a swap chain that's separate from the real-time game content.</span></span> <span data-ttu-id="a67db-124">Beachten Sie, dass dieses Verfahren nur für [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Swapchains gilt und nicht für die XAML-Interoperabilität verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a67db-124">Note that this technique applies only to [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) swap chains - it cannot be used with XAML interop.</span></span>

<span data-ttu-id="a67db-125">Führen Sie die folgenden Schritte aus, um eine Vordergrund-Swapchain zu erstellen, bei der eine Hardwareüberlagerungsfunktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a67db-125">Use the following steps to create a foreground swap chain that uses hardware overlay capability.</span></span> <span data-ttu-id="a67db-126">Diese Schritte werden ausgeführt, nachdem wie oben beschrieben zuerst eine Swapchain für die Echtzeitinhalte des Spiels erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a67db-126">These steps are performed after first creating a swap chain for real-time game content as described above.</span></span>

1.  <span data-ttu-id="a67db-127">Ermitteln Sie zuerst, ob Überlagerungen vom DXGI-Adapter unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="a67db-127">First, determine whether the DXGI adapter supports overlays.</span></span> <span data-ttu-id="a67db-128">Rufen Sie den DXGI-Ausgabeadapter aus der Swapchain ab:</span><span class="sxs-lookup"><span data-stu-id="a67db-128">Get the DXGI output adapter from the swap chain:</span></span>

    ```cpp
    ComPtr<IDXGIAdapter> outputDxgiAdapter;
    DX::ThrowIfFailed(
        dxgiFactory->EnumAdapters(0, &outputDxgiAdapter)
        );

    ComPtr<IDXGIOutput> dxgiOutput;
    DX::ThrowIfFailed(
        outputDxgiAdapter->EnumOutputs(0, &dxgiOutput)
        );

    ComPtr<IDXGIOutput2> dxgiOutput2;
    DX::ThrowIfFailed(
        dxgiOutput.As(&dxgiOutput2)
        );
    ```

    <span data-ttu-id="a67db-129">Überlagerungen werden vom DXGI-Adapter unterstützt, wenn der Ausgabeadapter für [**SupportsOverlays**](https://msdn.microsoft.com/library/windows/desktop/dn280411) "True" zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="a67db-129">The DXGI adapter supports overlays if the output adapter returns True for [**SupportsOverlays**](https://msdn.microsoft.com/library/windows/desktop/dn280411).</span></span>

    ```cpp
    m_overlaySupportExists = dxgiOutput2->SupportsOverlays() ? true : false;
    ```
    
    > <span data-ttu-id="a67db-130">**Hinweis:**  Wenn der DXGI-Adapter Überlagerungen unterstützt, fahren Sie mit dem nächsten Schritt fort.</span><span class="sxs-lookup"><span data-stu-id="a67db-130">**Note** If the DXGI adapter supports overlays, continue to the next step.</span></span> <span data-ttu-id="a67db-131">Wenn das Gerät Überlagerungen nicht unterstützt, ist das Rendern mit mehreren Swapchains nicht effizient.</span><span class="sxs-lookup"><span data-stu-id="a67db-131">If the device does not support overlays, rendering with multiple swap chains will not be efficient.</span></span> <span data-ttu-id="a67db-132">Rendern Sie die UI stattdessen mit reduzierter Auflösung in derselben Swapchain wie die Echtzeitinhalte des Spiels.</span><span class="sxs-lookup"><span data-stu-id="a67db-132">Instead, render the UI at reduced resolution in the same swap chain as real-time game content.</span></span>

     

2.  <span data-ttu-id="a67db-133">Erstellen Sie die Vordergrund-Swapchain mit [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559).</span><span class="sxs-lookup"><span data-stu-id="a67db-133">Create the foreground swap chain with [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559).</span></span> <span data-ttu-id="a67db-134">In der für den *pDesc*-Parameter bereitgestellten [**DXGI\_SWAP\_CHAIN\_DESC1**](https://msdn.microsoft.com/library/windows/desktop/hh404528)-Struktur müssen folgende Optionen festgelegt werden:</span><span class="sxs-lookup"><span data-stu-id="a67db-134">The following options must be set in the [**DXGI\_SWAP\_CHAIN\_DESC1**](https://msdn.microsoft.com/library/windows/desktop/hh404528) supplied to the *pDesc* parameter:</span></span>

    -   <span data-ttu-id="a67db-135">Legen Sie das [**DXGI\_SWAP\_CHAIN\_FLAG\_FOREGROUND\_LAYER**](https://msdn.microsoft.com/library/windows/desktop/bb173076)-Swapchainflag fest, um eine Vordergrund-Swapchain anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a67db-135">Specify the [**DXGI\_SWAP\_CHAIN\_FLAG\_FOREGROUND\_LAYER**](https://msdn.microsoft.com/library/windows/desktop/bb173076) swap chain flag to indicate a foreground swap chain.</span></span>
    -   <span data-ttu-id="a67db-136">Verwenden Sie das [**DXGI\_ALPHA\_MODE\_PREMULTIPLIED**](https://msdn.microsoft.com/library/windows/desktop/hh404496)-Alphamodusflag.</span><span class="sxs-lookup"><span data-stu-id="a67db-136">Use the [**DXGI\_ALPHA\_MODE\_PREMULTIPLIED**](https://msdn.microsoft.com/library/windows/desktop/hh404496) alpha mode flag.</span></span> <span data-ttu-id="a67db-137">Vordergrund-Swapchains sind immer prämultipliziert.</span><span class="sxs-lookup"><span data-stu-id="a67db-137">Foreground swap chains are always premultiplied.</span></span>
    -   <span data-ttu-id="a67db-138">Legen Sie das [**DXGI\_SCALING\_NONE**](https://msdn.microsoft.com/library/windows/desktop/hh404526)-Flag fest.</span><span class="sxs-lookup"><span data-stu-id="a67db-138">Set the [**DXGI\_SCALING\_NONE**](https://msdn.microsoft.com/library/windows/desktop/hh404526) flag.</span></span> <span data-ttu-id="a67db-139">Vordergrund-Swapchains werden immer mit systemeigener Auflösung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a67db-139">Foreground swap chains always run at native resolution.</span></span>

    ```cpp
     foregroundSwapChainDesc.Flags = DXGI_SWAP_CHAIN_FLAG_FOREGROUND_LAYER;
     foregroundSwapChainDesc.Scaling = DXGI_SCALING_NONE;
     foregroundSwapChainDesc.AlphaMode = DXGI_ALPHA_MODE_PREMULTIPLIED; // Foreground swap chain alpha values must be premultiplied.
    ```

    > <span data-ttu-id="a67db-140">**Hinweis:**  die [**DXGI\_SWAP\_CHAIN\_FLAG\_FOREGROUND\_LAYER**](https://msdn.microsoft.com/library/windows/desktop/bb173076) noch einmal festlegen, jedes Mal, wenn die Größe die SwapChain geändert wird.</span><span class="sxs-lookup"><span data-stu-id="a67db-140">**Note** Set the [**DXGI\_SWAP\_CHAIN\_FLAG\_FOREGROUND\_LAYER**](https://msdn.microsoft.com/library/windows/desktop/bb173076) again every time the swap chain is resized.</span></span>

    ```cpp
    HRESULT hr = m_foregroundSwapChain->ResizeBuffers(
        2, // Double-buffered swap chain.
        static_cast<UINT>(m_d3dRenderTargetSize.Width),
        static_cast<UINT>(m_d3dRenderTargetSize.Height),
        DXGI_FORMAT_B8G8R8A8_UNORM,
        DXGI_SWAP_CHAIN_FLAG_FOREGROUND_LAYER // The FOREGROUND_LAYER flag cannot be removed with ResizeBuffers.
        );
    ```

3.  <span data-ttu-id="a67db-141">Erhöhen Sie bei Verwendung von zwei Swapchains die maximale Framelatenz auf 2, damit der DXGI-Adapter genügend Zeit hat, um beide Swapchains gleichzeitig (innerhalb desselben VSync-Intervalls) darzustellen.</span><span class="sxs-lookup"><span data-stu-id="a67db-141">When two swap chains are being used, increase the maximum frame latency to 2 so that the DXGI adapter has time to present both swap chains simultaneously (within the same VSync interval).</span></span>

    ```cpp
    // Create a render target view of the foreground swap chain's back buffer.
    if (m_foregroundSwapChain)
    {
        ComPtr<ID3D11Texture2D> foregroundBackBuffer;
        DX::ThrowIfFailed(
            m_foregroundSwapChain->GetBuffer(0, IID_PPV_ARGS(&foregroundBackBuffer))
            );

        DX::ThrowIfFailed(
            m_d3dDevice->CreateRenderTargetView(
                foregroundBackBuffer.Get(),
                nullptr,
                &m_d3dForegroundRenderTargetView
                )
            );
    }
    ```

4.  <span data-ttu-id="a67db-142">Für Vordergrund-Swapchains wird immer prämultipliziertes Alpha verwendet.</span><span class="sxs-lookup"><span data-stu-id="a67db-142">Foreground swap chains always use premultiplied alpha.</span></span> <span data-ttu-id="a67db-143">Es wird davon ausgegangen, dass die Farbwerte der einzelnen Pixel vor der Darstellung des Frames bereits mit dem Alphawert multipliziert wurden.</span><span class="sxs-lookup"><span data-stu-id="a67db-143">Each pixel's color values are expected to be already multiplied by the alpha value before the frame is presented.</span></span> <span data-ttu-id="a67db-144">Ein BGRA-Pixel mit 100% Weiß und einem Alpha von 50% wird beispielsweise auf (0,5, 0,5, 0,5, 0,5) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a67db-144">For example, a 100% white BGRA pixel at 50% alpha is set to (0.5, 0.5, 0.5, 0.5).</span></span>

    <span data-ttu-id="a67db-145">Der Schritt der Alphaprämultiplikation kann in der Ausgabezusammenführungsphase ausgeführt werden, indem ein App-Blend-Status (siehe [**ID3D11BlendState**](https://msdn.microsoft.com/library/windows/desktop/ff476349)) angewendet wird, bei dem das **SrcBlend**-Feld der [**D3D11\_RENDER\_TARGET\_BLEND\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476200)-Struktur auf **D3D11\_SRC\_ALPHA** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a67db-145">The alpha premultiplication step can be done in the output-merger stage by applying an app blend state (see [**ID3D11BlendState**](https://msdn.microsoft.com/library/windows/desktop/ff476349)) with the [**D3D11\_RENDER\_TARGET\_BLEND\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476200) structure's **SrcBlend** field set to **D3D11\_SRC\_ALPHA**.</span></span> <span data-ttu-id="a67db-146">Es können auch Ressourcen mit prämultiplizierten Alphawerten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a67db-146">Assets with pre-multiplied alpha values can also be used.</span></span>

    <span data-ttu-id="a67db-147">Wenn der Schritt der Alphaprämultiplikation nicht erfolgt, erscheinen Farben für die Vordergrund-Swapchain heller als erwartet.</span><span class="sxs-lookup"><span data-stu-id="a67db-147">If the alpha premultiplication step is not done, colors on the foreground swap chain will be brighter than expected.</span></span>

5.  <span data-ttu-id="a67db-148">Je nachdem, ob die Vordergrund-Swapchain erstellt wurde, muss die Direct2D-Zeichenoberfläche für UI-Elemente möglicherweise der Vordergrund-Swapchain zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="a67db-148">Depending on whether the foreground swap chain was created, the Direct2D drawing surface for UI elements might need be associated with the foreground swap chain.</span></span>

    <span data-ttu-id="a67db-149">Erstellen von Renderzielansichten:</span><span class="sxs-lookup"><span data-stu-id="a67db-149">Creating render target views:</span></span>

    ```cpp
    // Create a render target view of the foreground swap chain's back buffer.
    if (m_foregroundSwapChain)
    {
        ComPtr<ID3D11Texture2D> foregroundBackBuffer;
        DX::ThrowIfFailed(
            m_foregroundSwapChain->GetBuffer(0, IID_PPV_ARGS(&foregroundBackBuffer))
            );

        DX::ThrowIfFailed(
            m_d3dDevice->CreateRenderTargetView(
                foregroundBackBuffer.Get(),
                nullptr,
                &m_d3dForegroundRenderTargetView
                )
            );
    }
    ```

    <span data-ttu-id="a67db-150">Erstellen der Direct2D-Zeichenoberfläche:</span><span class="sxs-lookup"><span data-stu-id="a67db-150">Creating the Direct2D drawing surface:</span></span>

    ```cpp
    if (m_foregroundSwapChain)
    {
        // Create a Direct2D target bitmap for the foreground swap chain.
        ComPtr<IDXGISurface2> dxgiForegroundSwapChainBackBuffer;
        DX::ThrowIfFailed(
            m_foregroundSwapChain->GetBuffer(0, IID_PPV_ARGS(&dxgiForegroundSwapChainBackBuffer))
            );

        DX::ThrowIfFailed(
            m_d2dContext->CreateBitmapFromDxgiSurface(
                dxgiForegroundSwapChainBackBuffer.Get(),
                &bitmapProperties,
                &m_d2dTargetBitmap
                )
            );
    }
    else
    {
        // Create a Direct2D target bitmap for the swap chain.
        ComPtr<IDXGISurface2> dxgiSwapChainBackBuffer;
        DX::ThrowIfFailed(
            m_swapChain->GetBuffer(0, IID_PPV_ARGS(&dxgiSwapChainBackBuffer))
            );

        DX::ThrowIfFailed(
            m_d2dContext->CreateBitmapFromDxgiSurface(
                dxgiSwapChainBackBuffer.Get(),
                &bitmapProperties,
                &m_d2dTargetBitmap
                )
            );
    }

    m_d2dContext->SetTarget(m_d2dTargetBitmap.Get());
    ```

    ```cpp
    // Create a render target view of the swap chain's back buffer.
    ComPtr<ID3D11Texture2D> backBuffer;
    DX::ThrowIfFailed(
        m_swapChain->GetBuffer(0, IID_PPV_ARGS(&backBuffer))
        );

    DX::ThrowIfFailed(
        m_d3dDevice->CreateRenderTargetView(
            backBuffer.Get(),
            nullptr,
            &m_d3dRenderTargetView
            )
        );
    ```

6.  <span data-ttu-id="a67db-151">Stellen Sie die Vordergrund-Swapchain zusammen mit der skalierten Swapchain dar, die für die Echtzeitinhalte des Spiels verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a67db-151">Present the foreground swap chain together with the scaled swap chain used for real-time game content.</span></span> <span data-ttu-id="a67db-152">Da die Framelatenz für beide Swapchains auf 2 festgelegt wurde, können beide von DXGI innerhalb desselben VSync-Intervalls dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a67db-152">Since frame latency was set to 2 for both swap chains, DXGI can present them both within the same VSync interval.</span></span>

    ```cpp
    // Present the contents of the swap chain to the screen.
    void DX::DeviceResources::Present()
    {
        // The first argument instructs DXGI to block until VSync, putting the application
        // to sleep until the next VSync. This ensures that we don't waste any cycles rendering
        // frames that will never be displayed to the screen.
        HRESULT hr = m_swapChain->Present(1, 0);

        if (SUCCEEDED(hr) && m_foregroundSwapChain)
        {
            m_foregroundSwapChain->Present(1, 0);
        }

        // Discard the contents of the render targets.
        // This is a valid operation only when the existing contents will be entirely
        // overwritten. If dirty or scroll rects are used, this call should be removed.
        m_d3dContext->DiscardView(m_d3dRenderTargetView.Get());
        if (m_foregroundSwapChain)
        {
            m_d3dContext->DiscardView(m_d3dForegroundRenderTargetView.Get());
        }

        // Discard the contents of the depth stencil.
        m_d3dContext->DiscardView(m_d3dDepthStencilView.Get());

        // If the device was removed either by a disconnection or a driver upgrade, we
        // must recreate all device resources.
        if (hr == DXGI_ERROR_DEVICE_REMOVED)
        {
            HandleDeviceLost();
        }
        else
        {
            DX::ThrowIfFailed(hr);
        }
    }
    ```

 

 




