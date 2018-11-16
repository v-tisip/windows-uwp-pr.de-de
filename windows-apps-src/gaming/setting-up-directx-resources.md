---
author: mtoepke
title: Einrichten von DirectX-Ressourcen und Darstellen eines Bilds
description: Hier zeigen wir Ihnen das Erstellen eines Direct3D-Geräts, einer Swapchain und einer Renderzielansicht sowie die Darstellung des gerenderten Bilds auf dem Bildschirm.
ms.assetid: d54d96fe-3522-4acb-35f4-bb11c3a5b064
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, DirectX, Ressourcen, Bilder
ms.localizationpriority: medium
ms.openlocfilehash: 24fd038bdd447491da43e5d5803445d00147ba2d
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6970835"
---
# <a name="set-up-directx-resources-and-display-an-image"></a><span data-ttu-id="d01af-104">Einrichten von DirectX-Ressourcen und Darstellen eines Bilds</span><span class="sxs-lookup"><span data-stu-id="d01af-104">Set up DirectX resources and display an image</span></span>



<span data-ttu-id="d01af-105">Hier zeigen wir Ihnen das Erstellen eines Direct3D-Geräts, einer Swapchain und einer Renderziel-Ansicht sowie die Darstellung des gerenderten Bilds auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="d01af-105">Here, we show you how to create a Direct3D device, swap chain, and render-target view, and how to present the rendered image to the display.</span></span>

<span data-ttu-id="d01af-106">**Ziel:** Sie richten DirectX-Ressourcen in einer UWP-App (Universelle Windows-Plattform) mit C++ ein und zeigen eine Volltonfarbe an.</span><span class="sxs-lookup"><span data-stu-id="d01af-106">**Objective:** To set up DirectX resources in a C++ Universal Windows Platform (UWP) app and to display a solid color.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d01af-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d01af-107">Prerequisites</span></span>


<span data-ttu-id="d01af-108">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="d01af-108">We assume that you are familiar with C++.</span></span> <span data-ttu-id="d01af-109">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="d01af-109">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="d01af-110">**Zeitaufwand:** 20Minuten.</span><span class="sxs-lookup"><span data-stu-id="d01af-110">**Time to complete:** 20 minutes.</span></span>

## <a name="instructions"></a><span data-ttu-id="d01af-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d01af-111">Instructions</span></span>

### <a name="1-declaring-direct3d-interface-variables-with-comptr"></a><span data-ttu-id="d01af-112">1. Deklarieren von Direct3D-Schnittstellenvariablen mit ComPtr</span><span class="sxs-lookup"><span data-stu-id="d01af-112">1. Declaring Direct3D interface variables with ComPtr</span></span>

<span data-ttu-id="d01af-113">Wir deklarieren Direct3D-Schnittstellenvariablen mit der [intelligenten Zeigervorlage](https://msdn.microsoft.com/library/windows/apps/hh279674.aspx) ComPtr aus der C++-Vorlagenbibliothek für Windows-Runtime (Windows Runtime C++ Template Library, WRL), damit wir die Lebensdauer dieser Variablen ausnahmesicher verwalten können.</span><span class="sxs-lookup"><span data-stu-id="d01af-113">We declare Direct3D interface variables with the ComPtr [smart pointer](https://msdn.microsoft.com/library/windows/apps/hh279674.aspx) template from the Windows Runtime C++ Template Library (WRL), so we can manage the lifetime of those variables in an exception safe manner.</span></span> <span data-ttu-id="d01af-114">Mithilfe dieser Variablen können wir auf die [**ComPtr class**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx) und ihre Member zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d01af-114">We can then use those variables to access the [**ComPtr class**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx) and its members.</span></span> <span data-ttu-id="d01af-115">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d01af-115">For example:</span></span>

```cpp
    ComPtr<ID3D11RenderTargetView> m_renderTargetView;
    m_d3dDeviceContext->OMSetRenderTargets(
        1,
        m_renderTargetView.GetAddressOf(),
        nullptr // Use no depth stencil.
        );
```

<span data-ttu-id="d01af-116">Wenn Sie [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582) mit ComPtr deklarieren, können Sie anschließend die ComPtr-Methode **GetAddressOf** zum Abrufen der Adresse des Zeigers auf **ID3D11RenderTargetView** (\*\*ID3D11RenderTargetView) für die Übergabe an [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) verwenden.</span><span class="sxs-lookup"><span data-stu-id="d01af-116">If you declare [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582) with ComPtr, you can then use ComPtr’s **GetAddressOf** method to get the address of the pointer to **ID3D11RenderTargetView** (\*\*ID3D11RenderTargetView) to pass to [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464).</span></span> <span data-ttu-id="d01af-117">**OMSetRenderTargets** bindet das Renderziel an den [Ausgabezusammenführungsstatus](https://msdn.microsoft.com/library/windows/desktop/bb205120), um das Renderziel als Ausgabeziel anzugeben.</span><span class="sxs-lookup"><span data-stu-id="d01af-117">**OMSetRenderTargets** binds the render target to the [output-merger stage](https://msdn.microsoft.com/library/windows/desktop/bb205120) to specify the render target as the output target.</span></span>

<span data-ttu-id="d01af-118">Nachdem die Beispiel-App gestartet wurde, wird sie initialisiert und geladen. Danach kann sie ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d01af-118">After the sample app is started, it initializes and loads, and is then ready to run.</span></span>

### <a name="2-creating-the-direct3d-device"></a><span data-ttu-id="d01af-119">2. Erstellen des Direct3D-Geräts</span><span class="sxs-lookup"><span data-stu-id="d01af-119">2. Creating the Direct3D device</span></span>

<span data-ttu-id="d01af-120">Für die Verwendung der Direct3D-API zum Rendern einer Szene müssen wir zunächst ein Direct3D-Gerät erstellen, das die Grafikkarte darstellt.</span><span class="sxs-lookup"><span data-stu-id="d01af-120">To use the Direct3D API to render a scene, we must first create a Direct3D device that represents the display adapter.</span></span> <span data-ttu-id="d01af-121">Zum Erstellen des Direct3D-Geräts rufen wir die [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082)-Funktion auf.</span><span class="sxs-lookup"><span data-stu-id="d01af-121">To create the Direct3D device, we call the [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082) function.</span></span> <span data-ttu-id="d01af-122">Im Array der [**D3D\_FEATURE\_LEVEL**](https://msdn.microsoft.com/library/windows/desktop/ff476329)-Werte geben wir die Ebenen 9.1 bis 11.1 an.</span><span class="sxs-lookup"><span data-stu-id="d01af-122">We specify levels 9.1 through 11.1 in the array of [**D3D\_FEATURE\_LEVEL**](https://msdn.microsoft.com/library/windows/desktop/ff476329) values.</span></span> <span data-ttu-id="d01af-123">Direct3D durchläuft das Array der Reihe nach und gibt die höchste Ebene des unterstützten Features zurück.</span><span class="sxs-lookup"><span data-stu-id="d01af-123">Direct3D walks the array in order and returns the highest supported feature level.</span></span> <span data-ttu-id="d01af-124">Zum Abrufen der höchsten verfügbaren Featureebene listen wir also die **D3D\_FEATURE\_LEVEL**-Arrayeinträge vom höchsten zum niedrigsten Eintrag auf.</span><span class="sxs-lookup"><span data-stu-id="d01af-124">So, to get the highest feature level available, we list the **D3D\_FEATURE\_LEVEL** array entries from highest to lowest.</span></span> <span data-ttu-id="d01af-125">Wir übergeben das [**D3D11\_CREATE\_DEVICE\_BGRA\_SUPPORT**](https://msdn.microsoft.com/library/windows/desktop/ff476107#D3D11_CREATE_DEVICE_BGRA_SUPPORT)-Flag an den *Flags*-Parameter, damit Direct3D-Ressourcen mit Direct2D ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="d01af-125">We pass the [**D3D11\_CREATE\_DEVICE\_BGRA\_SUPPORT**](https://msdn.microsoft.com/library/windows/desktop/ff476107#D3D11_CREATE_DEVICE_BGRA_SUPPORT) flag to the *Flags* parameter to make Direct3D resources interoperate with Direct2D.</span></span> <span data-ttu-id="d01af-126">Bei Verwendung der Debugversion übergeben wir zudem das [**D3D11\_CREATE\_DEVICE\_DEBUG**](https://msdn.microsoft.com/library/windows/desktop/ff476107#D3D11_CREATE_DEVICE_DEBUG)-Flag.</span><span class="sxs-lookup"><span data-stu-id="d01af-126">If we use the debug build, we also pass the [**D3D11\_CREATE\_DEVICE\_DEBUG**](https://msdn.microsoft.com/library/windows/desktop/ff476107#D3D11_CREATE_DEVICE_DEBUG) flag.</span></span> <span data-ttu-id="d01af-127">Weitere Informationen zum Debuggen von Apps finden Sie unter [Verwenden der Debugschicht zum Debuggen von Apps](https://msdn.microsoft.com/library/windows/desktop/jj200584).</span><span class="sxs-lookup"><span data-stu-id="d01af-127">For more info about debugging apps, see [Using the debug layer to debug apps](https://msdn.microsoft.com/library/windows/desktop/jj200584).</span></span>

<span data-ttu-id="d01af-128">Wir rufen das Direct3D 11.1-Gerät ([**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575)) und den Gerätekontext ([**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598)) durch Abfragen des Direct3D 11-Geräts und Gerätekontexts ab, die von [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082) zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d01af-128">We obtain the Direct3D 11.1 device ([**ID3D11Device1**](https://msdn.microsoft.com/library/windows/desktop/hh404575)) and device context ([**ID3D11DeviceContext1**](https://msdn.microsoft.com/library/windows/desktop/hh404598)) by querying the Direct3D 11 device and device context that are returned from [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082).</span></span>

```cpp
        // First, create the Direct3D device.

        // This flag is required in order to enable compatibility with Direct2D.
        UINT creationFlags = D3D11_CREATE_DEVICE_BGRA_SUPPORT;

#if defined(_DEBUG)
        // If the project is in a debug build, enable debugging via SDK Layers with this flag.
        creationFlags |= D3D11_CREATE_DEVICE_DEBUG;
#endif

        // This array defines the ordering of feature levels that D3D should attempt to create.
        D3D_FEATURE_LEVEL featureLevels[] =
        {
            D3D_FEATURE_LEVEL_11_1,
            D3D_FEATURE_LEVEL_11_0,
            D3D_FEATURE_LEVEL_10_1,
            D3D_FEATURE_LEVEL_10_0,
            D3D_FEATURE_LEVEL_9_3,
            D3D_FEATURE_LEVEL_9_1
        };

        ComPtr<ID3D11Device> d3dDevice;
        ComPtr<ID3D11DeviceContext> d3dDeviceContext;
        DX::ThrowIfFailed(
            D3D11CreateDevice(
                nullptr,                    // Specify nullptr to use the default adapter.
                D3D_DRIVER_TYPE_HARDWARE,
                nullptr,                    // leave as nullptr if hardware is used
                creationFlags,              // optionally set debug and Direct2D compatibility flags
                featureLevels,
                ARRAYSIZE(featureLevels),
                D3D11_SDK_VERSION,          // always set this to D3D11_SDK_VERSION
                &d3dDevice,
                nullptr,
                &d3dDeviceContext
                )
            );

        // Retrieve the Direct3D 11.1 interfaces.
        DX::ThrowIfFailed(
            d3dDevice.As(&m_d3dDevice)
            );

        DX::ThrowIfFailed(
            d3dDeviceContext.As(&m_d3dDeviceContext)
            );
```

### <a name="3-creating-the-swap-chain"></a><span data-ttu-id="d01af-129">3. Erstellen der Swapchain</span><span class="sxs-lookup"><span data-stu-id="d01af-129">3. Creating the swap chain</span></span>

<span data-ttu-id="d01af-130">Im nächsten Schritt erstellen wir eine Swapchain, die von dem Gerät zum Rendern und für die Anzeige verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d01af-130">Next, we create a swap chain that the device uses for rendering and display.</span></span> <span data-ttu-id="d01af-131">Wir deklarieren und initialisieren eine [**DXGI\_SWAP\_CHAIN\_DESC1**](https://msdn.microsoft.com/library/windows/desktop/hh404528)-Struktur, um die Swapchain zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="d01af-131">We declare and initialize a [**DXGI\_SWAP\_CHAIN\_DESC1**](https://msdn.microsoft.com/library/windows/desktop/hh404528) structure to describe the swap chain.</span></span> <span data-ttu-id="d01af-132">Anschließend richten wir die Swapchain als Flip-Modell ein (d. h. eine Swapchain, für die der [**DXGI\_SWAP\_EFFECT\_FLIP\_SEQUENTIAL**](https://msdn.microsoft.com/library/windows/desktop/bb173077#DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL)-Wert im **SwapEffect**-Member festgelegt ist), und wir legen das **Format**-Member auf [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059#DXGI_FORMAT_B8G8R8A8_UNORM) fest.</span><span class="sxs-lookup"><span data-stu-id="d01af-132">Then, we set up the swap chain as flip-model (that is, a swap chain that has the [**DXGI\_SWAP\_EFFECT\_FLIP\_SEQUENTIAL**](https://msdn.microsoft.com/library/windows/desktop/bb173077#DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL) value set in the **SwapEffect** member) and set the **Format** member to [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059#DXGI_FORMAT_B8G8R8A8_UNORM).</span></span> <span data-ttu-id="d01af-133">Wir legen den **Count**-Member der [**DXGI\_SAMPLE\_DESC**](https://msdn.microsoft.com/library/windows/desktop/bb173072)-Struktur, die vom **SampleDesc**-Member angegeben wird, auf 1 fest. Außerdem legen wir den **Quality**-Member von **DXGI\_SAMPLE\_DESC** auf null fest, da MSAA (Multiple Sample Antialiasing) vom Flip-Modell nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="d01af-133">We set the **Count** member of the [**DXGI\_SAMPLE\_DESC**](https://msdn.microsoft.com/library/windows/desktop/bb173072) structure that the **SampleDesc** member specifies to 1 and the **Quality** member of **DXGI\_SAMPLE\_DESC** to zero because flip-model doesn’t support multiple sample antialiasing (MSAA).</span></span> <span data-ttu-id="d01af-134">Wir legen den **BufferCount**-Member auf 2 fest, sodass die Swapchain für die Darstellung auf dem Anzeigegerät einen Frontpuffer sowie einen Hintergrundpuffer verwenden kann, der als Renderziel dient.</span><span class="sxs-lookup"><span data-stu-id="d01af-134">We set the **BufferCount** member to 2 so the swap chain can use a front buffer to present to the display device and a back buffer that serves as the render target.</span></span>

<span data-ttu-id="d01af-135">Wir rufen das zugrunde liegende DXGI-Gerät durch Abfragen des Direct3D 11.1-Geräts ab.</span><span class="sxs-lookup"><span data-stu-id="d01af-135">We obtain the underlying DXGI device by querying the Direct3D 11.1 device.</span></span> <span data-ttu-id="d01af-136">Zur Minimierung des Stromverbrauchs – einem wichtigen Aspekt für batteriebetriebene Geräte wie Laptops und Tablet-PCs – rufen wir die [**IDXGIDevice1::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/ff471334)-Methode mit dem Wert 1 auf. Dieser Wert ist die maximale Anzahl an Hintergrundpufferframes, die von DXGI in die Warteschlange verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="d01af-136">To minimize power consumption, which is important to do on battery-powered devices such as laptops and tablets, we call the [**IDXGIDevice1::SetMaximumFrameLatency**](https://msdn.microsoft.com/library/windows/desktop/ff471334) method with 1 as the maximum number of back buffer frames that DXGI can queue.</span></span> <span data-ttu-id="d01af-137">Dadurch wird sichergestellt, dass die App erst nach der vertikalen Austastung gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="d01af-137">This ensures that the app is rendered only after the vertical blank.</span></span>

<span data-ttu-id="d01af-138">Für die endgültige Erstellung der Swapchain müssen wir die übergeordnete Factory vom DXGI-Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="d01af-138">To finally create the swap chain, we need to get the parent factory from the DXGI device.</span></span> <span data-ttu-id="d01af-139">Zum Abrufen des Adapters für das Gerät rufen wir [**IDXGIDevice::GetAdapter**](https://msdn.microsoft.com/library/windows/desktop/bb174531) auf. Anschließend rufen wir auf dem Adapter [**IDXGIObject::GetParent**](https://msdn.microsoft.com/library/windows/desktop/bb174542) auf, um die übergeordnete Factory ([**IDXGIFactory2**](https://msdn.microsoft.com/library/windows/desktop/hh404556)) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d01af-139">We call [**IDXGIDevice::GetAdapter**](https://msdn.microsoft.com/library/windows/desktop/bb174531) to get the adapter for the device, and then call [**IDXGIObject::GetParent**](https://msdn.microsoft.com/library/windows/desktop/bb174542) on the adapter to get the parent factory ([**IDXGIFactory2**](https://msdn.microsoft.com/library/windows/desktop/hh404556)).</span></span> <span data-ttu-id="d01af-140">Zum Erstellen der Swapchain rufen wir [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559) mit der Swapchainbeschreibung und dem Kernfenster der App auf.</span><span class="sxs-lookup"><span data-stu-id="d01af-140">To create the swap chain, we call [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559) with the swap-chain descriptor and the app’s core window.</span></span>

```cpp
            // If the swap chain does not exist, create it.
            DXGI_SWAP_CHAIN_DESC1 swapChainDesc = {0};

            swapChainDesc.Stereo = false;
            swapChainDesc.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
            swapChainDesc.Scaling = DXGI_SCALING_NONE;
            swapChainDesc.Flags = 0;

            // Use automatic sizing.
            swapChainDesc.Width = 0;
            swapChainDesc.Height = 0;

            // This is the most common swap chain format.
            swapChainDesc.Format = DXGI_FORMAT_B8G8R8A8_UNORM;

            // Don't use multi-sampling.
            swapChainDesc.SampleDesc.Count = 1;
            swapChainDesc.SampleDesc.Quality = 0;

            // Use two buffers to enable the flip effect.
            swapChainDesc.BufferCount = 2;

            // We recommend using this swap effect for all applications.
            swapChainDesc.SwapEffect = DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL;


            // Once the swap chain description is configured, it must be
            // created on the same adapter as the existing D3D Device.

            // First, retrieve the underlying DXGI Device from the D3D Device.
            ComPtr<IDXGIDevice2> dxgiDevice;
            DX::ThrowIfFailed(
                m_d3dDevice.As(&dxgiDevice)
                );

            // Ensure that DXGI does not queue more than one frame at a time. This both reduces
            // latency and ensures that the application will only render after each VSync, minimizing
            // power consumption.
            DX::ThrowIfFailed(
                dxgiDevice->SetMaximumFrameLatency(1)
                );

            // Next, get the parent factory from the DXGI Device.
            ComPtr<IDXGIAdapter> dxgiAdapter;
            DX::ThrowIfFailed(
                dxgiDevice->GetAdapter(&dxgiAdapter)
                );

            ComPtr<IDXGIFactory2> dxgiFactory;
            DX::ThrowIfFailed(
                dxgiAdapter->GetParent(IID_PPV_ARGS(&dxgiFactory))
                );

            // Finally, create the swap chain.
            CoreWindow^ window = m_window.Get();
            DX::ThrowIfFailed(
                dxgiFactory->CreateSwapChainForCoreWindow(
                    m_d3dDevice.Get(),
                    reinterpret_cast<IUnknown*>(window),
                    &swapChainDesc,
                    nullptr, // Allow on all displays.
                    &m_swapChain
                    )
                );
```

### <a name="4-creating-the-render-target-view"></a><span data-ttu-id="d01af-141">4. Erstellen der Renderziel-Ansicht</span><span class="sxs-lookup"><span data-stu-id="d01af-141">4. Creating the render-target view</span></span>

<span data-ttu-id="d01af-142">Zum Rendern von Grafik in dem Fenster müssen wir eine Renderziel-Ansicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="d01af-142">To render graphics to the window, we need to create a render-target view.</span></span> <span data-ttu-id="d01af-143">Wir rufen [**IDXGISwapChain::GetBuffer**](https://msdn.microsoft.com/library/windows/desktop/bb174570) zum Abrufen des Swapchain-Hintergrundpuffers auf, der beim Erstellen der Renderziel-Ansicht verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d01af-143">We call [**IDXGISwapChain::GetBuffer**](https://msdn.microsoft.com/library/windows/desktop/bb174570) to get the swap chain’s back buffer to use when we create the render-target view.</span></span> <span data-ttu-id="d01af-144">Wir geben den Hintergrundpuffer als 2D-Textur an ([**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)).</span><span class="sxs-lookup"><span data-stu-id="d01af-144">We specify the back buffer as a 2D texture ([**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)).</span></span> <span data-ttu-id="d01af-145">Zum Erstellen der Renderziel-Ansicht rufen wir [**ID3D11Device::CreateRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476517) mit dem Hintergrundpuffer der Swapchain auf.</span><span class="sxs-lookup"><span data-stu-id="d01af-145">To create the render-target view, we call [**ID3D11Device::CreateRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476517) with the swap chain’s back buffer.</span></span> <span data-ttu-id="d01af-146">Wir müssen das Zeichnen im gesamten Kernfenster festlegen, indem wir den Viewport ([**D3D11\_VIEWPORT**](https://msdn.microsoft.com/library/windows/desktop/ff476260)) als vollständige Größe des Swapchain-Hintergrundpuffers angeben.</span><span class="sxs-lookup"><span data-stu-id="d01af-146">We must specify to draw to the entire core window by specifying the view port ([**D3D11\_VIEWPORT**](https://msdn.microsoft.com/library/windows/desktop/ff476260)) as the full size of the swap chain's back buffer.</span></span> <span data-ttu-id="d01af-147">Wir verwenden den Viewport in einem Aufruf von [**ID3D11DeviceContext::RSSetViewports**](https://msdn.microsoft.com/library/windows/desktop/ff476480), um den Viewport an die [Rasterprogrammstufe](https://msdn.microsoft.com/library/windows/desktop/bb205125) der Pipeline zu binden.</span><span class="sxs-lookup"><span data-stu-id="d01af-147">We use the view port in a call to [**ID3D11DeviceContext::RSSetViewports**](https://msdn.microsoft.com/library/windows/desktop/ff476480) to bind the view port to the [rasterizer stage](https://msdn.microsoft.com/library/windows/desktop/bb205125) of the pipeline.</span></span> <span data-ttu-id="d01af-148">In der Rasterprogrammstufe werden Vektorinformationen in ein Rasterbild konvertiert.</span><span class="sxs-lookup"><span data-stu-id="d01af-148">The rasterizer stage converts vector information into a raster image.</span></span> <span data-ttu-id="d01af-149">In diesem Fall ist keine Konvertierung erforderlich, da wir nur eine Volltonfarbe anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d01af-149">In this case, we don't require a conversion because we are just displaying a solid color.</span></span>

```cpp
        // Once the swap chain is created, create a render target view.  This will
        // allow Direct3D to render graphics to the window.

        ComPtr<ID3D11Texture2D> backBuffer;
        DX::ThrowIfFailed(
            m_swapChain->GetBuffer(0, IID_PPV_ARGS(&backBuffer))
            );

        DX::ThrowIfFailed(
            m_d3dDevice->CreateRenderTargetView(
                backBuffer.Get(),
                nullptr,
                &m_renderTargetView
                )
            );


        // After the render target view is created, specify that the viewport,
        // which describes what portion of the window to draw to, should cover
        // the entire window.

        D3D11_TEXTURE2D_DESC backBufferDesc = {0};
        backBuffer->GetDesc(&backBufferDesc);

        D3D11_VIEWPORT viewport;
        viewport.TopLeftX = 0.0f;
        viewport.TopLeftY = 0.0f;
        viewport.Width = static_cast<float>(backBufferDesc.Width);
        viewport.Height = static_cast<float>(backBufferDesc.Height);
        viewport.MinDepth = D3D11_MIN_DEPTH;
        viewport.MaxDepth = D3D11_MAX_DEPTH;

        m_d3dDeviceContext->RSSetViewports(1, &viewport);
```

### <a name="5-presenting-the-rendered-image"></a><span data-ttu-id="d01af-150">5. Darstellen des gerenderten Bilds</span><span class="sxs-lookup"><span data-stu-id="d01af-150">5. Presenting the rendered image</span></span>

<span data-ttu-id="d01af-151">Wir geben eine endlose Schleife zum fortlaufenden Rendern und Anzeigen der Szene ein.</span><span class="sxs-lookup"><span data-stu-id="d01af-151">We enter an endless loop to continually render and display the scene.</span></span>

<span data-ttu-id="d01af-152">In dieser Schleife wird Folgendes aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="d01af-152">In this loop, we call:</span></span>

1.  <span data-ttu-id="d01af-153">[**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464), um das Renderziel als Ausgabeziel anzugeben.</span><span class="sxs-lookup"><span data-stu-id="d01af-153">[**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) to specify the render target as the output target.</span></span>
2.  <span data-ttu-id="d01af-154">[**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388), um das Renderziel mit einer Volltonfarbe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d01af-154">[**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) to clear the render target to a solid color.</span></span>
3.  <span data-ttu-id="d01af-155">[**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576), um das gerenderte Bild im Fenster darzustellen.</span><span class="sxs-lookup"><span data-stu-id="d01af-155">[**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) to present the rendered image to the window.</span></span>

<span data-ttu-id="d01af-156">Da wir zuvor die maximale Framelatenz auf 1 festgelegt haben, reduziert Windows die Geschwindigkeit der Renderschleife generell auf die Bildschirmaktualisierungsrate, die normalerweise etwa 60 Hz beträgt.</span><span class="sxs-lookup"><span data-stu-id="d01af-156">Because we previously set the maximum frame latency to 1, Windows generally slows down the render loop to the screen refresh rate, typically around 60 Hz.</span></span> <span data-ttu-id="d01af-157">Windows reduziert die Geschwindigkeit der Renderschleife, indem die App in den Ruhezustand versetzt wird, wenn sie [**Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) aufruft.</span><span class="sxs-lookup"><span data-stu-id="d01af-157">Windows slows down the render loop by making the app sleep when the app calls [**Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576).</span></span> <span data-ttu-id="d01af-158">Windows versetzt die App so lange in den Ruhezustand, bis die Bildschirmanzeige aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="d01af-158">Windows makes the app sleep until the screen is refreshed.</span></span>

```cpp
        // Enter the render loop.  Note that UWP apps should never exit.
        while (true)
        {
            // Process events incoming to the window.
            m_window->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            // Specify the render target we created as the output target.
            m_d3dDeviceContext->OMSetRenderTargets(
                1,
                m_renderTargetView.GetAddressOf(),
                nullptr // Use no depth stencil.
                );

            // Clear the render target to a solid color.
            const float clearColor[4] = { 0.071f, 0.04f, 0.561f, 1.0f };
            m_d3dDeviceContext->ClearRenderTargetView(
                m_renderTargetView.Get(),
                clearColor
                );

            // Present the rendered image to the window.  Because the maximum frame latency is set to 1,
            // the render loop will generally be throttled to the screen refresh rate, typically around
            // 60 Hz, by sleeping the application on Present until the screen is refreshed.
            DX::ThrowIfFailed(
                m_swapChain->Present(1, 0)
                );
        }
```

### <a name="6-resizing-the-app-window-and-the-swap-chains-buffer"></a><span data-ttu-id="d01af-159">6. Ändern der Größe des App-Fensters und des Swapchainpuffers</span><span class="sxs-lookup"><span data-stu-id="d01af-159">6. Resizing the app window and the swap chain’s buffer</span></span>

<span data-ttu-id="d01af-160">Wenn sich die Größe des App-Fensters ändert, muss die App die Größe der Swapchainpuffer ändern, die Renderziel-Ansicht neu erstellen und anschließend das gerenderte Bild in der geänderten Größe darstellen.</span><span class="sxs-lookup"><span data-stu-id="d01af-160">If the size of the app window changes, the app must resize the swap chain’s buffers, recreate the render-target view, and then present the resized rendered image.</span></span> <span data-ttu-id="d01af-161">Zum Ändern der Größe der Swapchainpuffer rufen wir [**IDXGISwapChain::ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577) auf.</span><span class="sxs-lookup"><span data-stu-id="d01af-161">To resize the swap chain’s buffers, we call [**IDXGISwapChain::ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577).</span></span> <span data-ttu-id="d01af-162">Bei diesem Aufruf lassen wir die Anzahl und das Format der Puffer unverändert (der *BufferCount*-Parameter ist auf den Wert zwei und der *NewFormat*-Parameter ist auf [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059#DXGI_FORMAT_B8G8R8A8_UNORM) festgelegt).</span><span class="sxs-lookup"><span data-stu-id="d01af-162">In this call, we leave the number of buffers and the format of the buffers unchanged (the *BufferCount* parameter to two and the *NewFormat* parameter to [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059#DXGI_FORMAT_B8G8R8A8_UNORM)).</span></span> <span data-ttu-id="d01af-163">Wir legen für die Größe des Swapchain-Hintergrundpuffers denselben Wert wie für das Fenster mit geänderter Größe fest.</span><span class="sxs-lookup"><span data-stu-id="d01af-163">We make the size of the swap chain’s back buffer the same size as the resized window.</span></span> <span data-ttu-id="d01af-164">Nachdem wir die Größe des Swapchainpuffers geändert haben, erstellen wir das neue Renderziel, und wir stellen das neue gerenderte Bild genauso wie beim Initialisieren der App dar.</span><span class="sxs-lookup"><span data-stu-id="d01af-164">After we resize the swap chain’s buffers, we create the new render target and present the new rendered image similarly to when we initialized the app.</span></span>

```cpp
            // If the swap chain already exists, resize it.
            DX::ThrowIfFailed(
                m_swapChain->ResizeBuffers(
                    2,
                    0,
                    0,
                    DXGI_FORMAT_B8G8R8A8_UNORM,
                    0
                    )
                );
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="d01af-165">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d01af-165">Summary and next steps</span></span>


<span data-ttu-id="d01af-166">Wir haben ein Direct3D-Gerät, eine Swapchain und eine Renderziel-Ansicht erstellt und das gerenderte Bild auf dem Bildschirm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d01af-166">We created a Direct3D device, swap chain, and render-target view, and presented the rendered image to the display.</span></span>

<span data-ttu-id="d01af-167">Als Nächstes zeichnen wir ein Dreieck auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="d01af-167">Next, we also draw a triangle on the display.</span></span>

[<span data-ttu-id="d01af-168">Erstellen von Shadern und Zeichnen von Primitiven</span><span class="sxs-lookup"><span data-stu-id="d01af-168">Creating shaders and drawing primitives</span></span>](creating-shaders-and-drawing-primitives.md)

 

 




