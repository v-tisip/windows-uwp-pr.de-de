---
author: mtoepke
title: Unterstützen der Bildschirmausrichtung (DirectX und C++)
description: Hier erläutern wir bewährte Methoden für die Behandlung von Drehung des Bildschirms in Ihrer UWP-DirectX-app, damit das Windows 10-Gerät Grafikhardware werden effizienter und effektiver verwendet.
ms.assetid: f23818a6-e372-735d-912b-89cabeddb6d4
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Bildschirmausrichtung, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: 4ed8739f8ba7b2049af154d458ccaa831b8526a5
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5920818"
---
# <a name="supporting-screen-orientation-directx-and-c"></a><span data-ttu-id="a1c51-104">Unterstützen der Bildschirmausrichtung (DirectX und C++)</span><span class="sxs-lookup"><span data-stu-id="a1c51-104">Supporting screen orientation (DirectX and C++)</span></span>



<span data-ttu-id="a1c51-105">Ihre App für die universelle Windows-Plattform (UWP) kann beim Behandeln des [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)-Ereignisses mehrere Bildschirmausrichtungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-105">Your Universal Windows Platform (UWP) app can support multiple screen orientations when you handle the [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) event.</span></span> <span data-ttu-id="a1c51-106">Hier erläutern wir bewährte Methoden für die Behandlung von Drehung des Bildschirms in Ihrer UWP-DirectX-app, damit das Windows 10-Gerät Grafikhardware werden effizienter und effektiver verwendet.</span><span class="sxs-lookup"><span data-stu-id="a1c51-106">Here, we'll discuss best practices for handling screen rotation in your UWP DirectX app, so that the Windows10 device's graphics hardware are used efficiently and effectively.</span></span>

<span data-ttu-id="a1c51-107">Beachten Sie vor Beginn, dass Grafikhardware grundsätzlich auf irgendeine Art und Weise Pixeldaten ausgibt und dass die Ausrichtung des Geräts dabei keine Rolle spielt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-107">Before you start, remember that graphics hardware always outputs pixel data in the same way, regardless of the orientation of the device.</span></span> <span data-ttu-id="a1c51-108">Windows 10-Geräte können ihre aktuelle anzeigeausrichtung bestimmen, (mit einigen Sortierung des Sensors oder einer softwareumschaltung) und Benutzern das Ändern der Anzeigeeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-108">Windows10 devices can determine their current display orientation (with some sort of sensor, or with a software toggle) and allow users to change the display settings.</span></span> <span data-ttu-id="a1c51-109">Aufgrund dieser, Windows 10 selbst übernimmt die Drehung der Bilder um sicherzustellen, dass sie sind "aufrecht angezeigt", basierend auf der Ausrichtung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="a1c51-109">Because of this, Windows10 itself handles the rotation of the images to ensure they are "upright" based on the orientation of the device.</span></span> <span data-ttu-id="a1c51-110">Standardmäßig empfangen Apps eine Benachrichtigung mit dem Hinweis, dass bezüglich der Ausrichtung eine Änderung vorgenommen wurde (beispielsweise eine Änderung der Fenstergröße).</span><span class="sxs-lookup"><span data-stu-id="a1c51-110">By default, your app receives the notification that something has changed in orientation, for example, a window size.</span></span> <span data-ttu-id="a1c51-111">Wenn dieser Fall eintritt, dreht Windows 10 das Bild für die endgültige Anzeige sofort.</span><span class="sxs-lookup"><span data-stu-id="a1c51-111">When this happens, Windows10 immediately rotates the image for final display.</span></span> <span data-ttu-id="a1c51-112">Für drei der vier speziellen bildschirmausrichtungen (finden Sie weiter unten) verwendet Windows 10 zusätzliche Grafikressourcen und Berechnungen, um das endgültige Bild anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-112">For three of the four specific screen orientations (discussed later), Windows10 uses additional graphic resources and computation to display the final image.</span></span>

<span data-ttu-id="a1c51-113">Für UWP-DirectX-Apps stellt das [**DisplayInformation**](https://msdn.microsoft.com/library/windows/apps/dn264258)-Objekt grundlegende Bildschirmausrichtungsdaten bereit, die von der App abgefragt werden können.</span><span class="sxs-lookup"><span data-stu-id="a1c51-113">For UWP DirectX apps, the [**DisplayInformation**](https://msdn.microsoft.com/library/windows/apps/dn264258) object provides basic display orientation data that your app can query.</span></span> <span data-ttu-id="a1c51-114">Die Standardausrichtung lautet *Querformat*, wobei die Pixelbreite der Anzeige größer ist als die Höhe. Die alternative Ausrichtung lautet *Hochformat*, in der die Anzeige um 90Grad in eine Richtung gedreht und die Breite kleiner als die Höhe wird.</span><span class="sxs-lookup"><span data-stu-id="a1c51-114">The default orientation is *landscape*, where the pixel width of the display is greater than the height; the alternative orientation is *portrait*, where the display is rotated 90 degrees in either direction and the width becomes less than the height.</span></span>

<span data-ttu-id="a1c51-115">Windows 10 definiert vier spezielle bildschirmausrichtungsmodi:</span><span class="sxs-lookup"><span data-stu-id="a1c51-115">Windows10 defines four specific display orientation modes:</span></span>

-   <span data-ttu-id="a1c51-116">Querformat – die bildschirmstandardausrichtung für Windows 10, und gilt der Basis- oder identitätswinkel für die Drehung (0 Grad).</span><span class="sxs-lookup"><span data-stu-id="a1c51-116">Landscape—the default display orientation for Windows10, and is considered the base or identity angle for rotation (0 degrees).</span></span>
-   <span data-ttu-id="a1c51-117">Hochformat – die Anzeige wurde um 90 Grad im Uhrzeigersinn gedreht (oder um 270 entgegen dem Uhrzeigersinn).</span><span class="sxs-lookup"><span data-stu-id="a1c51-117">Portrait—the display has been rotated clockwise 90 degrees (or counter-clockwise 270 degrees).</span></span>
-   <span data-ttu-id="a1c51-118">Querformat, gedreht – die Anzeige wurde um 180 Grad gedreht (auf den Kopf gedreht).</span><span class="sxs-lookup"><span data-stu-id="a1c51-118">Landscape, flipped—the display has been rotated 180 degrees (turned upside-down).</span></span>
-   <span data-ttu-id="a1c51-119">Hochformat, gedreht – die Anzeige wurde um 270 Grad im Uhrzeigersinn gedreht (oder um 90 Grad entgegen dem Uhrzeigersinn).</span><span class="sxs-lookup"><span data-stu-id="a1c51-119">Portrait, flipped—the display has been rotated clockwise 270 degrees (or counter-clockwise 90 degrees).</span></span>

<span data-ttu-id="a1c51-120">Wenn die Anzeige von einer Ausrichtung auf eine andere gedreht wird, führt Windows 10 intern einen Drehvorgang um das dargestellte Bild an die neue Ausrichtung anzupassen, und der Benutzer wird ein aufrechtes Bild auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="a1c51-120">When the display rotates from one orientation to another, Windows10 internally performs a rotation operation to align the drawn image with the new orientation, and the user sees an upright image on the screen.</span></span>

<span data-ttu-id="a1c51-121">Zudem zeigt Windows 10 automatische Übergangsanimationen an, um eine flüssige Benutzeroberfläche zu erstellen, wenn von einer Ausrichtung zu einer anderen zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="a1c51-121">Also, Windows10 displays automatic transition animations to create a smooth user experience when shifting from one orientation to another.</span></span> <span data-ttu-id="a1c51-122">Einen Wechsel der Bildschirmausrichtung nimmt der Benutzer mit einer festen Vergrößerung und einer Drehungsanimation des auf dem Bildschirm angezeigten Bilds wahr.</span><span class="sxs-lookup"><span data-stu-id="a1c51-122">As the display orientation shifts, the user sees these shifts as a fixed zoom and rotation animation of the displayed screen image.</span></span> <span data-ttu-id="a1c51-123">Zeit wird von Windows 10 an die app für das Layout in der neuen Ausrichtung zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-123">Time is allocated by Windows10 to the app for layout in the new orientation.</span></span>

<span data-ttu-id="a1c51-124">Im Großen und Ganzen lautet der allgemeine Prozess zum Behandeln von Änderungen bezüglich der Bildschirmausrichtung wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a1c51-124">Overall, this is the general process for handling changes in screen orientation:</span></span>

1.  <span data-ttu-id="a1c51-125">Verwenden Sie eine Kombination aus den Fensterabgrenzungswerten und den Bildschirmausrichtungsdaten, um die Ausrichtung der Swapchain an der systemeigenen Bildschirmausrichtung des Geräts beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="a1c51-125">Use a combination of the window bounds values and the display orientation data to keep the swap chain aligned with the native display orientation of the device.</span></span>
2.  <span data-ttu-id="a1c51-126">Windows 10, der die Ausrichtung der SwapChain mit [**idxgiswapchain1:: SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801)zu benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-126">Notify Windows10 of the orientation of the swap chain using [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801).</span></span>
3.  <span data-ttu-id="a1c51-127">Ändern Sie den Code zum Rendern, um Bilder zu generieren, die an die benutzerdefinierte Ausrichtung des Geräts angepasst sind.</span><span class="sxs-lookup"><span data-stu-id="a1c51-127">Change the rendering code to generate images aligned with the user orientation of the device.</span></span>

## <a name="resizing-the-swap-chain-and-pre-rotating-its-contents"></a><span data-ttu-id="a1c51-128">Ändern der Swapchaingröße und Vorgeben der Bildschirmausrichtung für die Inhalte</span><span class="sxs-lookup"><span data-stu-id="a1c51-128">Resizing the swap chain and pre-rotating its contents</span></span>


<span data-ttu-id="a1c51-129">Wenn Sie eine einfache Änderung der Anzeigegröße in der UWP-DirectX-App ausführen und ihre Inhalte vorab drehen möchten, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="a1c51-129">To perform a basic display resize and pre-rotate its contents in your UWP DirectX app , implement these steps:</span></span>

1.  <span data-ttu-id="a1c51-130">Behandeln Sie das [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="a1c51-130">Handle the [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) event.</span></span>
2.  <span data-ttu-id="a1c51-131">Ändern Sie die Swapchaingröße in die neuen Fensterabmessungen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-131">Resize the swap chain to the new dimensions of the window.</span></span>
3.  <span data-ttu-id="a1c51-132">Rufen Sie [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801) auf, um die Ausrichtung der Swapchain festzulegen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-132">Call [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801) to set the orientation of the swap chain.</span></span>
4.  <span data-ttu-id="a1c51-133">Erstellen Sie die von der Fenstergröße abhängigen Ressourcen neu, beispielsweise die Renderziele und andere Pixeldatenpuffer.</span><span class="sxs-lookup"><span data-stu-id="a1c51-133">Recreate any window size dependent resources, such as your render targets and other pixel data buffers.</span></span>

<span data-ttu-id="a1c51-134">Jetzt wollen wir uns die Schritte etwas genauer ansehen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-134">Now's let's look at those steps in a bit more detail.</span></span>

<span data-ttu-id="a1c51-135">Im ersten Schritt registrieren Sie einen Handler für das [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="a1c51-135">Your first step is to register a handler for the [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) event.</span></span> <span data-ttu-id="a1c51-136">Dieses Ereignis wird immer dann in der App ausgelöst, wenn sich die Bildschirmausrichtung ändert (beispielsweise beim Drehen der Anzeige).</span><span class="sxs-lookup"><span data-stu-id="a1c51-136">This event is raised in your app every time the screen orientation changes, such as when the display is rotated.</span></span>

<span data-ttu-id="a1c51-137">Zum Behandeln des [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)-Ereignisses verbinden Sie den Handler für **DisplayInformation::OrientationChanged** in der erforderlichen [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509)-Methode. Dabei handelt es sich um eine der Methoden der [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478)-Schnittstelle, die vom Ansichtsanbieter implementiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="a1c51-137">To handle the [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) event, you connect your handler for **DisplayInformation::OrientationChanged** in the required [**SetWindow**](https://msdn.microsoft.com/library/windows/apps/hh700509) method, which is one of the methods of the [**IFrameworkView**](https://msdn.microsoft.com/library/windows/apps/hh700478) interface that your view provider must implement.</span></span>

<span data-ttu-id="a1c51-138">In diesem Codebeispiel ist der Ereignishandler für [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) eine Methode namens **OnOrientationChanged**.</span><span class="sxs-lookup"><span data-stu-id="a1c51-138">In this code example, the event handler for [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) is a method called **OnOrientationChanged**.</span></span> <span data-ttu-id="a1c51-139">Beim Auslösen von **DisplayInformation::OrientationChanged** wird wiederum eine Methode mit der Bezeichnung **SetCurrentOrientation** aufgerufen, die dann **CreateWindowSizeDependentResources** aufruft.</span><span class="sxs-lookup"><span data-stu-id="a1c51-139">When **DisplayInformation::OrientationChanged** is raised, it in turn calls a method called **SetCurrentOrientation** which then calls **CreateWindowSizeDependentResources**.</span></span>

```cpp
void App::SetWindow(CoreWindow^ window)
{
  // ... Other UI event handlers assigned here ...
  
    currentDisplayInformation->OrientationChanged +=
        ref new TypedEventHandler<DisplayInformation^, Object^>(this, &App::OnOrientationChanged);

  // ...
}
}
```

```cpp
void App::OnOrientationChanged(DisplayInformation^ sender, Object^ args)
{
    m_deviceResources->SetCurrentOrientation(sender->CurrentOrientation);
    m_main->CreateWindowSizeDependentResources();
}

// This method is called in the event handler for the OrientationChanged event.
void DX::DeviceResources::SetCurrentOrientation(DisplayOrientations currentOrientation)
{
    if (m_currentOrientation != currentOrientation)
    {
        m_currentOrientation = currentOrientation;
        CreateWindowSizeDependentResources();
    }
}
```

<span data-ttu-id="a1c51-140">Anschließend ändern Sie die Swapchaingröße für die neue Bildschirmausrichtung und bereiten sie auf die Drehung der Inhalte der Grafikpipeline vor, wenn das Rendern erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-140">Next, you resize the swap chain for the new screen orientation and prepare it to rotate the contents of the graphic pipeline when the rendering is performed.</span></span> <span data-ttu-id="a1c51-141">In diesem Beispiel ist **DirectXBase::CreateWindowSizeDependentResources** eine Methode, die das Aufrufen von „IDXGISwapChain::ResizeBuffers“ behandelt, eine 3D- und eine 2D-Drehungsmatrix festlegt, „SetRotation“ aufruft und Ihre Ressourcen neu erstellt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-141">In this example, **DirectXBase::CreateWindowSizeDependentResources** is a method that handles calling IDXGISwapChain::ResizeBuffers, setting a 3D and a 2D rotation matrix, calling SetRotation, and recreating your resources.</span></span>

```cpp
void DX::DeviceResources::CreateWindowSizeDependentResources() 
{
    // Clear the previous window size specific context.
    ID3D11RenderTargetView* nullViews[] = {nullptr};
    m_d3dContext->OMSetRenderTargets(ARRAYSIZE(nullViews), nullViews, nullptr);
    m_d3dRenderTargetView = nullptr;
    m_d2dContext->SetTarget(nullptr);
    m_d2dTargetBitmap = nullptr;
    m_d3dDepthStencilView = nullptr;
    m_d3dContext->Flush();

    // Calculate the necessary render target size in pixels.
    m_outputSize.Width = DX::ConvertDipsToPixels(m_logicalSize.Width, m_dpi);
    m_outputSize.Height = DX::ConvertDipsToPixels(m_logicalSize.Height, m_dpi);
    
    // Prevent zero size DirectX content from being created.
    m_outputSize.Width = max(m_outputSize.Width, 1);
    m_outputSize.Height = max(m_outputSize.Height, 1);

    // The width and height of the swap chain must be based on the window's
    // natively-oriented width and height. If the window is not in the native
    // orientation, the dimensions must be reversed.
    DXGI_MODE_ROTATION displayRotation = ComputeDisplayRotation();

    bool swapDimensions = displayRotation == DXGI_MODE_ROTATION_ROTATE90 || displayRotation == DXGI_MODE_ROTATION_ROTATE270;
    m_d3dRenderTargetSize.Width = swapDimensions ? m_outputSize.Height : m_outputSize.Width;
    m_d3dRenderTargetSize.Height = swapDimensions ? m_outputSize.Width : m_outputSize.Height;

    if (m_swapChain != nullptr)
    {
        // If the swap chain already exists, resize it.
        HRESULT hr = m_swapChain->ResizeBuffers(
            2, // Double-buffered swap chain.
            lround(m_d3dRenderTargetSize.Width),
            lround(m_d3dRenderTargetSize.Height),
            DXGI_FORMAT_B8G8R8A8_UNORM,
            0
            );

        if (hr == DXGI_ERROR_DEVICE_REMOVED || hr == DXGI_ERROR_DEVICE_RESET)
        {
            // If the device was removed for any reason, a new device and swap chain will need to be created.
            HandleDeviceLost();

            // Everything is set up now. Do not continue execution of this method. HandleDeviceLost will reenter this method 
            // and correctly set up the new device.
            return;
        }
        else
        {
            DX::ThrowIfFailed(hr);
        }
    }
    else
    {
        // Otherwise, create a new one using the same adapter as the existing Direct3D device.
        DXGI_SWAP_CHAIN_DESC1 swapChainDesc = {0};

        swapChainDesc.Width = lround(m_d3dRenderTargetSize.Width); // Match the size of the window.
        swapChainDesc.Height = lround(m_d3dRenderTargetSize.Height);
        swapChainDesc.Format = DXGI_FORMAT_B8G8R8A8_UNORM; // This is the most common swap chain format.
        swapChainDesc.Stereo = false;
        swapChainDesc.SampleDesc.Count = 1; // Don't use multi-sampling.
        swapChainDesc.SampleDesc.Quality = 0;
        swapChainDesc.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
        swapChainDesc.BufferCount = 2; // Use double-buffering to minimize latency.
        swapChainDesc.SwapEffect = DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL; // All UWP apps must use this SwapEffect.
        swapChainDesc.Flags = 0;    
        swapChainDesc.Scaling = DXGI_SCALING_NONE;
        swapChainDesc.AlphaMode = DXGI_ALPHA_MODE_IGNORE;

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

        DX::ThrowIfFailed(
            dxgiFactory->CreateSwapChainForCoreWindow(
                m_d3dDevice.Get(),
                reinterpret_cast<IUnknown*>(m_window.Get()),
                &swapChainDesc,
                nullptr,
                &m_swapChain
                )
            );

        // Ensure that DXGI does not queue more than one frame at a time. This both reduces latency and
        // ensures that the application will only render after each VSync, minimizing power consumption.
        DX::ThrowIfFailed(
            dxgiDevice->SetMaximumFrameLatency(1)
            );
    }

    // Set the proper orientation for the swap chain, and generate 2D and
    // 3D matrix transformations for rendering to the rotated swap chain.
    // Note the rotation angle for the 2D and 3D transforms are different.
    // This is due to the difference in coordinate spaces.  Additionally,
    // the 3D matrix is specified explicitly to avoid rounding errors.

    switch (displayRotation)
    {
    case DXGI_MODE_ROTATION_IDENTITY:
        m_orientationTransform2D = Matrix3x2F::Identity();
        m_orientationTransform3D = ScreenRotation::Rotation0;
        break;

    case DXGI_MODE_ROTATION_ROTATE90:
        m_orientationTransform2D = 
            Matrix3x2F::Rotation(90.0f) *
            Matrix3x2F::Translation(m_logicalSize.Height, 0.0f);
        m_orientationTransform3D = ScreenRotation::Rotation270;
        break;

    case DXGI_MODE_ROTATION_ROTATE180:
        m_orientationTransform2D = 
            Matrix3x2F::Rotation(180.0f) *
            Matrix3x2F::Translation(m_logicalSize.Width, m_logicalSize.Height);
        m_orientationTransform3D = ScreenRotation::Rotation180;
        break;

    case DXGI_MODE_ROTATION_ROTATE270:
        m_orientationTransform2D = 
            Matrix3x2F::Rotation(270.0f) *
            Matrix3x2F::Translation(0.0f, m_logicalSize.Width);
        m_orientationTransform3D = ScreenRotation::Rotation90;
        break;

    default:
        throw ref new FailureException();
    }


    //SDM: only instance of SetRotation
    DX::ThrowIfFailed(
        m_swapChain->SetRotation(displayRotation)
        );

    // Create a render target view of the swap chain back buffer.
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

    // Create a depth stencil view for use with 3D rendering if needed.
    CD3D11_TEXTURE2D_DESC depthStencilDesc(
        DXGI_FORMAT_D24_UNORM_S8_UINT, 
        lround(m_d3dRenderTargetSize.Width),
        lround(m_d3dRenderTargetSize.Height),
        1, // This depth stencil view has only one texture.
        1, // Use a single mipmap level.
        D3D11_BIND_DEPTH_STENCIL
        );

    ComPtr<ID3D11Texture2D> depthStencil;
    DX::ThrowIfFailed(
        m_d3dDevice->CreateTexture2D(
            &depthStencilDesc,
            nullptr,
            &depthStencil
            )
        );

    CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(D3D11_DSV_DIMENSION_TEXTURE2D);
    DX::ThrowIfFailed(
        m_d3dDevice->CreateDepthStencilView(
            depthStencil.Get(),
            &depthStencilViewDesc,
            &m_d3dDepthStencilView
            )
        );
    
    // Set the 3D rendering viewport to target the entire window.
    m_screenViewport = CD3D11_VIEWPORT(
        0.0f,
        0.0f,
        m_d3dRenderTargetSize.Width,
        m_d3dRenderTargetSize.Height
        );

    m_d3dContext->RSSetViewports(1, &m_screenViewport);

    // Create a Direct2D target bitmap associated with the
    // swap chain back buffer and set it as the current target.
    D2D1_BITMAP_PROPERTIES1 bitmapProperties = 
        D2D1::BitmapProperties1(
            D2D1_BITMAP_OPTIONS_TARGET | D2D1_BITMAP_OPTIONS_CANNOT_DRAW,
            D2D1::PixelFormat(DXGI_FORMAT_B8G8R8A8_UNORM, D2D1_ALPHA_MODE_PREMULTIPLIED),
            m_dpi,
            m_dpi
            );

    ComPtr<IDXGISurface2> dxgiBackBuffer;
    DX::ThrowIfFailed(
        m_swapChain->GetBuffer(0, IID_PPV_ARGS(&dxgiBackBuffer))
        );

    DX::ThrowIfFailed(
        m_d2dContext->CreateBitmapFromDxgiSurface(
            dxgiBackBuffer.Get(),
            &bitmapProperties,
            &m_d2dTargetBitmap
            )
        );

    m_d2dContext->SetTarget(m_d2dTargetBitmap.Get());

    // Grayscale text anti-aliasing is recommended for all UWP apps.
    m_d2dContext->SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE_GRAYSCALE);

}

```

<span data-ttu-id="a1c51-142">Nachdem Sie die aktuellen Höhen- und Breitenwerte des Fensters für den nächsten Aufruf dieser Methode gespeichert haben, konvertieren Sie die DIP (Device Independent Pixel)-Werte für die Bildschirmbegrenzungen in Pixel.</span><span class="sxs-lookup"><span data-stu-id="a1c51-142">After saving the current height and width values of the window for the next time this method is called, convert the device independent pixel (DIP) values for the display bounds to pixels.</span></span> <span data-ttu-id="a1c51-143">In dem Beispiel rufen Sie **ConvertDipsToPixels** auf. Dabei handelt es sich um eine einfache Funktion, die den folgenden Code ausführt:</span><span class="sxs-lookup"><span data-stu-id="a1c51-143">In the sample, you call **ConvertDipsToPixels**, which is a simple function that runs this code:</span></span>

` floor((dips * dpi / 96.0f) + 0.5f);`

<span data-ttu-id="a1c51-144">0.5f wird hinzugefügt, um die Rundung auf den nächsten ganzzahligen Wert sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-144">You add the 0.5f to ensure rounding to the nearest integer value.</span></span>

<span data-ttu-id="a1c51-145">Beachten Sie dabei, dass [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)-Koordinaten immer in DIPs definiert werden.</span><span class="sxs-lookup"><span data-stu-id="a1c51-145">As an aside, [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) coordinates are always defined in DIPs.</span></span> <span data-ttu-id="a1c51-146">Für Windows 10 und früheren Versionen von Windows ist ein DIP als 1/96 Zoll und an die betriebssystemdefinition *auf-* definiert.</span><span class="sxs-lookup"><span data-stu-id="a1c51-146">For Windows10 and earlier versions of Windows, a DIP is defined as 1/96th of an inch, and aligned to the OS's definition of *up*.</span></span> <span data-ttu-id="a1c51-147">Beim Drehen der Bildschirmausrichtung in das Hochformat vertauscht die App die Breite und Höhe von **CoreWindow**, und die Renderzielgröße (Begrenzungen) muss entsprechend geändert werden.</span><span class="sxs-lookup"><span data-stu-id="a1c51-147">When the display orientation rotates to portrait mode, the app flips the width and height of the **CoreWindow**, and the render target size (bounds) must change accordingly.</span></span> <span data-ttu-id="a1c51-148">Da die Direct3D-Koordinaten immer in physischen Pixeln angegeben sind, müssen Sie die DIP-Werte von **CoreWindow** in ganzzahlige Pixelwerte konvertieren, bevor Sie diese Werte zum Einrichten der Swapchain an Direct3D übergeben.</span><span class="sxs-lookup"><span data-stu-id="a1c51-148">Because Direct3D’s coordinates are always in physical pixels, you must convert from **CoreWindow**'s DIP values to integer pixel values before you pass these values to Direct3D to set up the swap chain.</span></span>

<span data-ttu-id="a1c51-149">Für die einzelnen Prozesse ist die Arbeit ein wenig umfangreicher als bei einer einfachen Änderung der Swapchaingröße: Sie drehen die Direct2D- und Direct3D-Komponenten Ihres Bilds, bevor Sie sie für die Darstellung zusammenstellen, und Sie informieren die Swapchain darüber, dass Sie die Ergebnisse in einer neuen Ausrichtung gerendert haben.</span><span class="sxs-lookup"><span data-stu-id="a1c51-149">Process-wise, you're doing a bit more work than you would if you simply resized the swap chain: you're actually rotating the Direct2D and Direct3D components of your image before you composite them for presentation, and you're telling the swap chain that you've rendered the results in a new orientation.</span></span> <span data-ttu-id="a1c51-150">Nachstehend finden Sie etwas mehr Details zu diesem Prozess, wie im Codebeispiel für **DX::DeviceResources::CreateWindowSizeDependentResources** veranschaulicht wird:</span><span class="sxs-lookup"><span data-stu-id="a1c51-150">Here's a little more detail on this process, as shown in the code example for **DX::DeviceResources::CreateWindowSizeDependentResources**:</span></span>

-   <span data-ttu-id="a1c51-151">Bestimmen Sie die neue Ausrichtung der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="a1c51-151">Determine the new orientation of the display.</span></span> <span data-ttu-id="a1c51-152">Wenn die Anzeige vom Querformat in das Hochformat oder umgekehrt geändert wurde, tauschen Sie die Höhen- und Breitenwerte – die natürlich von DIP-Werten in Pixel geändert wurden – für die Bildschirmbegrenzungen aus.</span><span class="sxs-lookup"><span data-stu-id="a1c51-152">If the display has flipped from landscape to portrait, or vice versa, swap the height and width values—changed from DIP values to pixels, of course—for the display bounds.</span></span>

-   <span data-ttu-id="a1c51-153">Überprüfen Sie dann, ob die Swapchain erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a1c51-153">Then, check to see if the swap chain has been created.</span></span> <span data-ttu-id="a1c51-154">Wenn dies nicht der Fall ist, erstellen Sie sie durch Aufrufen von [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559).</span><span class="sxs-lookup"><span data-stu-id="a1c51-154">If it hasn't been created, create it by calling [**IDXGIFactory2::CreateSwapChainForCoreWindow**](https://msdn.microsoft.com/library/windows/desktop/hh404559).</span></span> <span data-ttu-id="a1c51-155">Ändern Sie anderenfalls die Puffergröße der vorhandenen Swapchain in die neuen Anzeigeabmessungen, indem Sie [**IDXGISwapchain:ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-155">Otherwise, resize the existing swap chain's buffers to the new display dimensions by calling [**IDXGISwapchain:ResizeBuffers**](https://msdn.microsoft.com/library/windows/desktop/bb174577).</span></span> <span data-ttu-id="a1c51-156">Obwohl Sie die Größe der Swapchain für das Drehungsereignis nicht ändern müssen – schließlich geben Sie Inhalte aus, die bereits von der Pipeline zum Rendern gedreht wurden –, existieren auch andere Größenänderungsereignisse, beispielsweise Andock- und Füllungsereignisse, für die Größenänderungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a1c51-156">Although you don't need to resize the swap chain for the rotation event—you're outputting the content already rotated by your rendering pipeline, after all—there are other size change events, such as snap and fill events, that require resizing.</span></span>

-   <span data-ttu-id="a1c51-157">Legen Sie danach die entsprechende 2D- oder 3D-Matrixtransformation fest, die beim Rendern in der Swapchain auf die Pixel bzw. Vertizes in der Grafikpipeline angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a1c51-157">After that, set the appropriate 2-D or 3-D matrix transformation to apply to the pixels or the vertices (respectively) in the graphics pipeline when rendering them to the swap chain.</span></span> <span data-ttu-id="a1c51-158">Es existieren vier mögliche Drehungsmatrizen:</span><span class="sxs-lookup"><span data-stu-id="a1c51-158">We have 4 possible rotation matrices:</span></span>

    -   <span data-ttu-id="a1c51-159">Querformat (DXGI\_MODE\_ROTATION\_IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="a1c51-159">landscape (DXGI\_MODE\_ROTATION\_IDENTITY)</span></span>
    -   <span data-ttu-id="a1c51-160">Hochformat (DXGI\_MODE\_ROTATION\_ROTATE270)</span><span class="sxs-lookup"><span data-stu-id="a1c51-160">portrait (DXGI\_MODE\_ROTATION\_ROTATE270)</span></span>
    -   <span data-ttu-id="a1c51-161">Querformat, gedreht (DXGI\_MODE\_ROTATION\_ROTATE180)</span><span class="sxs-lookup"><span data-stu-id="a1c51-161">landscape, flipped (DXGI\_MODE\_ROTATION\_ROTATE180)</span></span>
    -   <span data-ttu-id="a1c51-162">Hochformat, gedreht (DXGI\_MODE\_ROTATION\_ROTATE90)</span><span class="sxs-lookup"><span data-stu-id="a1c51-162">portrait, flipped (DXGI\_MODE\_ROTATION\_ROTATE90)</span></span>

    <span data-ttu-id="a1c51-163">Die richtige Matrix basierend auf den bereitgestellten Windows 10 (z. B. das Ergebnis der [**Displayinformation**](https://msdn.microsoft.com/library/windows/apps/dn264268)) für die Bestimmung der bildschirmausrichtung Daten ausgewählt ist, und es werden durch die Koordinaten der einzelnen Pixel (Direct2D) oder Vertizes multipliziert (Direct3D) in der Szene effektiv gedreht werden sie an die Ausrichtung des Bildschirms ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="a1c51-163">The correct matrix is selected based on the data provided by Windows10 (such as the results of [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)) for determining display orientation, and it will be multiplied by the coordinates of each pixel (Direct2D) or vertex (Direct3D) in the scene, effectively rotating them to align to the orientation of the screen.</span></span> <span data-ttu-id="a1c51-164">(Beachten Sie, dass der Bildschirmursprung in Direct2D als obere linke Ecke und in Direct3D als logische Mitte des Fensters definiert ist.)</span><span class="sxs-lookup"><span data-stu-id="a1c51-164">(Note that in Direct2D, the screen origin is defined as the upper-left corner, while in Direct3D the origin is defined as the logical center of the window.)</span></span>

> <span data-ttu-id="a1c51-165">**Hinweis:**  Weitere Informationen zu den 2-D-Transformationen für Drehung und zu deren Definition finden Sie unter [Definieren von Matrizen für die bildschirmdrehung (2D)](#appendix-a-applying-matrices-for-screen-rotation-2-d).</span><span class="sxs-lookup"><span data-stu-id="a1c51-165">**Note** For more info about the 2-D transformations used for rotation and how to define them, see [Defining matrices for screen rotation (2-D)](#appendix-a-applying-matrices-for-screen-rotation-2-d).</span></span> <span data-ttu-id="a1c51-166">Weitere Informationen zu den für die Drehung verwendeten 3D-Transformationen finden Sie unter [Definieren von Matrizen für die Bildschirmdrehung (3D)](#appendix-b-applying-matrices-for-screen-rotation-3-d).</span><span class="sxs-lookup"><span data-stu-id="a1c51-166">For more info about the 3-D transformations used for rotation, see [Defining matrices for screen rotation (3-D)](#appendix-b-applying-matrices-for-screen-rotation-3-d).</span></span>

 

<span data-ttu-id="a1c51-167">Nun zum wichtigen Teil: rufen Sie [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801) auf, und stellen Sie dafür die aktualisierte Rotationsmatrix bereit – Beispiel:</span><span class="sxs-lookup"><span data-stu-id="a1c51-167">Now, here's the important bit: call [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801) and provide it with your updated rotation matrix, like this:</span></span>

`m_swapChain->SetRotation(rotation);`

<span data-ttu-id="a1c51-168">Die ausgewählte Rotationsmatrix wird auch unter dem Verzeichnis gespeichert, in dem sie von der Rendermethode beim Berechnen der neuen Projektion abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="a1c51-168">You also store the selected rotation matrix where your render method can get it when it computes the new projection.</span></span> <span data-ttu-id="a1c51-169">Sie verwenden diese Matrix beim Rendern der endgültigen 3-D-Projektion oder beim Zusammenstellen des endgültigen 2-D-Layouts.</span><span class="sxs-lookup"><span data-stu-id="a1c51-169">You'll use this matrix when you render your final 3-D projection or composite your final 2-D layout.</span></span> <span data-ttu-id="a1c51-170">(Sie wird nicht automatisch angewendet.)</span><span class="sxs-lookup"><span data-stu-id="a1c51-170">(It doesn't automatically apply it for you.)</span></span>

<span data-ttu-id="a1c51-171">Erstellen Sie nun ein neues Renderziel für die gedrehte 3-D-Ansicht sowie einen neuen Tiefenschablonenpuffer für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="a1c51-171">After that, create a new render target for the rotated 3-D view, as well as a new depth stencil buffer for the view.</span></span> <span data-ttu-id="a1c51-172">Legen Sie den Viewport zum 3D-Rendern für die gedrehte Szene fest, indem Sie [**ID3D11DeviceContext:RSSetViewports**](https://msdn.microsoft.com/library/windows/desktop/ff476480) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-172">Set the 3-D rendering viewport for the rotated scene by calling [**ID3D11DeviceContext:RSSetViewports**](https://msdn.microsoft.com/library/windows/desktop/ff476480).</span></span>

<span data-ttu-id="a1c51-173">Wenn Sie 2D-Bilder drehen oder ein Layout für 2D-Bilder erzeugen müssen, erstellen Sie zuletzt mithilfe von [**ID2D1DeviceContext::CreateBitmapFromDxgiSurface**](https://msdn.microsoft.com/library/windows/desktop/hh404482) ein 2D-Renderziel als beschreibbare Bitmap-Datei für die Swapchain mit geänderter Größe, und stellen Sie das neue Layout für die aktualisierte Ausrichtung zusammen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-173">Lastly, if you have 2-D images to rotate or lay out, create a 2-D render target as a writable bitmap for the resized swap chain using [**ID2D1DeviceContext::CreateBitmapFromDxgiSurface**](https://msdn.microsoft.com/library/windows/desktop/hh404482) and composite your new layout for the updated orientation.</span></span> <span data-ttu-id="a1c51-174">Legen Sie die erforderlichen Eigenschaften für das Renderziel fest, beispielsweise den Antialiasing-Modus (siehe Codebeispiel).</span><span class="sxs-lookup"><span data-stu-id="a1c51-174">Set any properties you need to on the render target, such as the anti-aliasing mode (as seen in the code example).</span></span>

<span data-ttu-id="a1c51-175">Stellen Sie nun die Swapchain dar.</span><span class="sxs-lookup"><span data-stu-id="a1c51-175">Now, present the swap chain.</span></span>

## <a name="reduce-the-rotation-delay-by-using-corewindowresizemanager"></a><span data-ttu-id="a1c51-176">Reduzieren der Rotationsverzögerung mit „CoreWindowResizeManager“</span><span class="sxs-lookup"><span data-stu-id="a1c51-176">Reduce the rotation delay by using CoreWindowResizeManager</span></span>


<span data-ttu-id="a1c51-177">Windows 10 bietet standardmäßig eine kurze aber wahrnehmbares Zeitfenster für jede app, unabhängig von der app-Modell oder der Sprache für die Drehung des Bilds bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-177">By default, Windows10 provides a short but noticeable window of time for any app, regardless of app model or language, to complete the rotation of the image.</span></span> <span data-ttu-id="a1c51-178">Wenn die App die Drehungsberechnung mithilfe einer der hier beschriebenen Techniken ausführt, ist dieser Vorgang möglicherweise bereits abgeschlossen, bevor dieses Zeitfenster abgelaufen ist.</span><span class="sxs-lookup"><span data-stu-id="a1c51-178">However, chances are that when your app performs the rotation calculation using one of the techniques described here, it will be done well before this window of time has closed.</span></span> <span data-ttu-id="a1c51-179">Es wäre doch wünschenswert, diese Zeit zurückzugewinnen und die Drehungsanimation abzuschließen, oder?</span><span class="sxs-lookup"><span data-stu-id="a1c51-179">You'd like to get that time back and complete the rotation animation, right?</span></span> <span data-ttu-id="a1c51-180">An dieser Stelle kommt [**CoreWindowResizeManager**](https://msdn.microsoft.com/library/windows/apps/jj215603) ins Spiel.</span><span class="sxs-lookup"><span data-stu-id="a1c51-180">That's where [**CoreWindowResizeManager**](https://msdn.microsoft.com/library/windows/apps/jj215603) comes in.</span></span>

<span data-ttu-id="a1c51-181">So verwenden Sie [**CoreWindowResizeManager**](https://msdn.microsoft.com/library/windows/apps/jj215603): Beim Auslösen eines [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268)-Ereignisses rufen Sie [**CoreWindowResizeManager::GetForCurrentView**](https://msdn.microsoft.com/library/windows/apps/hh404170) innerhalb des Handlers für das Ereignis auf, um eine Instanz von **CoreWindowResizeManager** zu erhalten. Wenn das Layout für die neue Ausrichtung abgeschlossen ist und dargestellt wird, rufen Sie [**NotifyLayoutCompleted**](https://msdn.microsoft.com/library/windows/apps/jj215605) auf, um Windows darüber zu informieren, dass die Drehungsanimation abgeschlossen und der App-Bildschirm angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a1c51-181">Here's how to use [**CoreWindowResizeManager**](https://msdn.microsoft.com/library/windows/apps/jj215603): when a [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) event is raised, call [**CoreWindowResizeManager::GetForCurrentView**](https://msdn.microsoft.com/library/windows/apps/hh404170) within the handler for the event to obtain an instance of **CoreWindowResizeManager** and, when the layout for the new orientation is complete and presented, call the [**NotifyLayoutCompleted**](https://msdn.microsoft.com/library/windows/apps/jj215605) to let Windows know that it can complete the rotation animation and display the app screen.</span></span>

<span data-ttu-id="a1c51-182">Der Code im Ereignishandler für [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) kann wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="a1c51-182">Here's what the code in your event handler for [**DisplayInformation::OrientationChanged**](https://msdn.microsoft.com/library/windows/apps/dn264268) might look like:</span></span>

```cpp
CoreWindowResizeManager^ resizeManager = Windows::UI::Core::CoreWindowResizeManager::GetForCurrentView();

// ... build the layout for the new display orientation ...

resizeManager->NotifyLayoutCompleted();
```

<span data-ttu-id="a1c51-183">Wenn ein Benutzer die Ausrichtung der Anzeige dreht, zeigt Windows 10 eine Animation unabhängig von der app als Feedback für dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a1c51-183">When a user rotates the orientation of the display, Windows10 shows an animation independent of your app as feedback to the user.</span></span> <span data-ttu-id="a1c51-184">Diese Animation besteht aus drei Teilen, die in der folgenden Reihenfolge ablaufen:</span><span class="sxs-lookup"><span data-stu-id="a1c51-184">There are three parts to that animation that happen in the following order:</span></span>

-   <span data-ttu-id="a1c51-185">Windows 10 verkleinert das ursprüngliche Bild.</span><span class="sxs-lookup"><span data-stu-id="a1c51-185">Windows10 shrinks the original image.</span></span>
-   <span data-ttu-id="a1c51-186">Windows 10 speichert das Bild für die Zeit, die benötigt wird, um das neue Layout neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-186">Windows10 holds the image for the time it takes to rebuild the new layout.</span></span> <span data-ttu-id="a1c51-187">Dies entspricht dem Zeitfenster, das Sie verkürzen möchten, weil die App wahrscheinlich nicht das gesamte Zeitfenster benötigt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-187">This is the window of time that you'd like to reduce, because your app probably doesn't need all of it.</span></span>
-   <span data-ttu-id="a1c51-188">Bei Ablauf des Zeitfensters für das Layout oder beim Empfang einer Benachrichtigung über den Layoutabschluss dreht Windows das Bild, und es erfolgt eine Vergrößerung mit Überblendung in die neue Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="a1c51-188">When the layout window expires, or when a notification of layout completion is received, Windows rotates the image and then cross-fade zooms to new orientation.</span></span>

<span data-ttu-id="a1c51-189">Wie im dritten Punkt vorgeschlagen Wenn eine app [**NotifyLayoutCompleted**](https://msdn.microsoft.com/library/windows/apps/jj215605), ruft Windows 10 beendet das Timeout-Fenster, wird die Drehungsanimation abgeschlossen und gibt die Kontrolle an Ihre app, die nun in der neuen bildschirmausrichtung ausführt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-189">As suggested in the third bullet, when an app calls [**NotifyLayoutCompleted**](https://msdn.microsoft.com/library/windows/apps/jj215605), Windows10 stops the timeout window, completes the rotation animation and returns control to your app, which is now drawing in the new display orientation.</span></span> <span data-ttu-id="a1c51-190">In der Gesamtheit fühlt sich die App nun ein wenig flüssiger und schneller an, und sie arbeitet etwas effizienter!</span><span class="sxs-lookup"><span data-stu-id="a1c51-190">The overall effect is that your app now feels a little bit more fluid and responsive, and works a little more efficiently!</span></span>

## <a name="appendix-a-applying-matrices-for-screen-rotation-2-d"></a><span data-ttu-id="a1c51-191">AnhangA: Anwenden von Matrizen für die automatische Bildschirmausrichtung (2-D)</span><span class="sxs-lookup"><span data-stu-id="a1c51-191">Appendix A: Applying matrices for screen rotation (2-D)</span></span>


<span data-ttu-id="a1c51-192">In dem Beispielcode unter [Ändern der Swapchaingröße und Vorgeben der Bildschirmausrichtung für die Inhalte](#resizing-the-swap-chain-and-pre-rotating-its-contents) (und im [DXGI-Swapchain-Drehungsbeispiel](http://go.microsoft.com/fwlink/p/?linkid=257600)) haben Sie möglicherweise bemerkt, dass wir für die Direct2D- und die Direct3D-Ausgabe separate Drehungsmatrizen verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="a1c51-192">In the example code in [Resizing the swap chain and pre-rotating its contents](#resizing-the-swap-chain-and-pre-rotating-its-contents) (and in the [DXGI swap chain rotation sample](http://go.microsoft.com/fwlink/p/?linkid=257600)), you might have noticed that we had separate rotation matrices for Direct2D output and Direct3D output.</span></span> <span data-ttu-id="a1c51-193">Sehen wir uns zunächst die 2-D-Matrizen an.</span><span class="sxs-lookup"><span data-stu-id="a1c51-193">Let's look at the 2-D matrices, first.</span></span>

<span data-ttu-id="a1c51-194">Es gibt zwei Ursachen dafür, warum wir für Direct2D- und Direct3D-Inhalte nicht dieselben Drehungsmatrizen anwenden können:</span><span class="sxs-lookup"><span data-stu-id="a1c51-194">There are two reasons that we can't apply the same rotation matrices to Direct2D and Direct3D content:</span></span>

-   <span data-ttu-id="a1c51-195">Erstens: Sie verwenden unterschiedliche kartesische Koordinatenmodelle.</span><span class="sxs-lookup"><span data-stu-id="a1c51-195">One, they use different Cartesian coordinate models.</span></span> <span data-ttu-id="a1c51-196">Direct2D verwendet die rechtshändige Regel, wobei der positive Wert der Y-Koordinate vom Ausgangspunkt nach oben hin ansteigt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-196">Direct2D uses the right-handed rule, where the y-coordinate increases in positive value moving upward from the origin.</span></span> <span data-ttu-id="a1c51-197">Für Direct3D wird jedoch die linkshändige Regel verwendet, wobei der positive Wert der Y-Koordinate vom Ausgangspunkt nach rechts hin ansteigt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-197">However, Direct3D uses the left-handed rule, where the y-coordinate increases in positive value rightward from the origin.</span></span> <span data-ttu-id="a1c51-198">Demzufolge befindet sich der Ausgangspunkt für die Bildschirmkoordinaten bei Direct2D oben links, während der Ausgangspunkt für den Bildschirm (Projektionsebene) für Direct3D unten links liegt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-198">The result is the origin for the screen coordinates is located in the upper-left for Direct2D, while the origin for the screen (the projection plane) is in the lower-left for Direct3D.</span></span> <span data-ttu-id="a1c51-199">(Weitere Informationen finden Sie unter [3D-Koordinatensysteme](https://msdn.microsoft.com/library/windows/apps/bb324490.aspx) .)</span><span class="sxs-lookup"><span data-stu-id="a1c51-199">(See [3-D coordinate systems](https://msdn.microsoft.com/library/windows/apps/bb324490.aspx) for more info.)</span></span>

    ![direct3d coordinate system.](images/direct3d-origin.png)![direct2d coordinate system.](images/direct2d-origin.png)

-   <span data-ttu-id="a1c51-202">Zweitens: Die 3D-Drehungsmatrizen müssen explizit angegeben werden, um Rundungsfehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="a1c51-202">Two, the 3-D rotation matrices must be specified explicitly to avoid rounding errors.</span></span>

<span data-ttu-id="a1c51-203">Die Swapchain geht davon aus, dass der Ausgangspunkt unten links liegt. Daher müssen Sie eine Drehung ausführen, um das rechtshändige Direct2D-Koordinatensystem an das von der Swapchain verwendete linkshändige Koordinatensystem anzupassen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-203">The swap chain assumes that the origin is located in the lower-left, so you must perform a rotation to align the right-handed Direct2D coordinate system with the left-handed one used by the swap chain.</span></span> <span data-ttu-id="a1c51-204">Insbesondere ordnen Sie das Bild unter der neuen linkshändigen Ausrichtung neu an, indem Sie die Drehungsmatrix mit einer Übersetzungsmatrix für den Ausgangspunkt des gedrehten Koordinatensystems multiplizieren. Zudem transformieren Sie das Bild aus dem Koordinatenbereich von [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225) in den Koordinatenbereich der Swapchain.</span><span class="sxs-lookup"><span data-stu-id="a1c51-204">Specifically, you reposition the image under the new left-handed orientation by multiplying the rotation matrix with a translation matrix for the rotated coordinate system origin, and transform the image from the [**CoreWindow**](https://msdn.microsoft.com/library/windows/apps/br208225)'s coordinate space to the swap chain's coordinate space.</span></span> <span data-ttu-id="a1c51-205">Die App muss diese Transformation auch konsistent anwenden, wenn das Direct2D-Renderziel mit der Swapchain verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="a1c51-205">Your app also must consistently apply this transform when the Direct2D render target is connected with the swap chain.</span></span> <span data-ttu-id="a1c51-206">Wenn die App jedoch in Zwischenflächen zeichnet, die der Swapchain nicht direkt zugeordnet sind, wenden Sie diese Transformation des Koordinatenbereichs nicht an.</span><span class="sxs-lookup"><span data-stu-id="a1c51-206">However, if your app is drawing to intermediate surfaces that are not associated directly with the swap chain, don't apply this coordinate space transformation.</span></span>

<span data-ttu-id="a1c51-207">Der Code zum Auswählen der richtigen Matrix aus den vier möglichen Drehungen kann beispielsweise wie folgt lauten (beachten Sie die Übersetzung in den neuen Koordinatensystemursprung):</span><span class="sxs-lookup"><span data-stu-id="a1c51-207">Your code to select the correct matrix from the four possible rotations might look like this (be aware of the translation to the new coordinate system origin):</span></span>

```cpp
   
// Set the proper orientation for the swap chain, and generate 2D and
// 3D matrix transformations for rendering to the rotated swap chain.
// Note the rotation angle for the 2D and 3D transforms are different.
// This is due to the difference in coordinate spaces.  Additionally,
// the 3D matrix is specified explicitly to avoid rounding errors.

switch (displayRotation)
{
case DXGI_MODE_ROTATION_IDENTITY:
    m_orientationTransform2D = Matrix3x2F::Identity();
    m_orientationTransform3D = ScreenRotation::Rotation0;
    break;

case DXGI_MODE_ROTATION_ROTATE90:
    m_orientationTransform2D = 
        Matrix3x2F::Rotation(90.0f) *
        Matrix3x2F::Translation(m_logicalSize.Height, 0.0f);
    m_orientationTransform3D = ScreenRotation::Rotation270;
    break;

case DXGI_MODE_ROTATION_ROTATE180:
    m_orientationTransform2D = 
        Matrix3x2F::Rotation(180.0f) *
        Matrix3x2F::Translation(m_logicalSize.Width, m_logicalSize.Height);
    m_orientationTransform3D = ScreenRotation::Rotation180;
    break;

case DXGI_MODE_ROTATION_ROTATE270:
    m_orientationTransform2D = 
        Matrix3x2F::Rotation(270.0f) *
        Matrix3x2F::Translation(0.0f, m_logicalSize.Width);
    m_orientationTransform3D = ScreenRotation::Rotation90;
    break;

default:
    throw ref new FailureException();
}
    
```

<span data-ttu-id="a1c51-208">Nachdem Sie die richtige Drehungsmatrix und den Ursprung für das 2D-Bild ausgewählt haben, legen Sie sie bzw. ihn durch Aufrufen von [**ID2D1DeviceContext::SetTransform**](https://msdn.microsoft.com/library/windows/desktop/dd742857) zwischen den Aufrufen von [**ID2D1DeviceContext::BeginDraw**](https://msdn.microsoft.com/library/windows/desktop/dd371768) und [**ID2D1DeviceContext::EndDraw**](https://msdn.microsoft.com/library/windows/desktop/dd371924) fest.</span><span class="sxs-lookup"><span data-stu-id="a1c51-208">After you have the correct rotation matrix and origin for the 2-D image, set it with a call to [**ID2D1DeviceContext::SetTransform**](https://msdn.microsoft.com/library/windows/desktop/dd742857) between your calls to [**ID2D1DeviceContext::BeginDraw**](https://msdn.microsoft.com/library/windows/desktop/dd371768) and [**ID2D1DeviceContext::EndDraw**](https://msdn.microsoft.com/library/windows/desktop/dd371924).</span></span>

<span data-ttu-id="a1c51-209">**Warnung**  Direct2D nicht hat keinen Transformationsstapel.</span><span class="sxs-lookup"><span data-stu-id="a1c51-209">**Warning** Direct2D doesn't have a transformation stack.</span></span> <span data-ttu-id="a1c51-210">Wenn die App zudem [**ID2D1DeviceContext::SetTransform**](https://msdn.microsoft.com/library/windows/desktop/dd742857) als Teil des zugehörigen Zeichnungscodes verwendet, muss diese Matrix im Nachhinein für alle angewendeten Transformationen multipliziert werden.</span><span class="sxs-lookup"><span data-stu-id="a1c51-210">If your app is also using the [**ID2D1DeviceContext::SetTransform**](https://msdn.microsoft.com/library/windows/desktop/dd742857) as a part of its drawing code, this matrix needs to be post-multiplied to any other transform you have applied.</span></span>

 

```cpp
    ID2D1DeviceContext* context = m_deviceResources->GetD2DDeviceContext();
    Windows::Foundation::Size logicalSize = m_deviceResources->GetLogicalSize();

    context->SaveDrawingState(m_stateBlock.Get());
    context->BeginDraw();

    // Position on the bottom right corner.
    D2D1::Matrix3x2F screenTranslation = D2D1::Matrix3x2F::Translation(
        logicalSize.Width - m_textMetrics.layoutWidth,
        logicalSize.Height - m_textMetrics.height
        );

    context->SetTransform(screenTranslation * m_deviceResources->GetOrientationTransform2D());

    DX::ThrowIfFailed(
        m_textFormat->SetTextAlignment(DWRITE_TEXT_ALIGNMENT_TRAILING)
        );

    context->DrawTextLayout(
        D2D1::Point2F(0.f, 0.f),
        m_textLayout.Get(),
        m_whiteBrush.Get()
        );

    // Ignore D2DERR_RECREATE_TARGET here. This error indicates that the device
    // is lost. It will be handled during the next call to Present.
    HRESULT hr = context->EndDraw();
```

<span data-ttu-id="a1c51-211">Bei der nächsten Darstellung der Swapchain wird das 2D-Bild gedreht, sodass es mit der neuen Bildschirmausrichtung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a1c51-211">The next time you present the swap chain, your 2-D image will be rotated to match the new display orientation.</span></span>

## <a name="appendix-b-applying-matrices-for-screen-rotation-3-d"></a><span data-ttu-id="a1c51-212">AnhangB: Anwenden von Matrizen für die automatische Bildschirmausrichtung (3-D)</span><span class="sxs-lookup"><span data-stu-id="a1c51-212">Appendix B: Applying matrices for screen rotation (3-D)</span></span>


<span data-ttu-id="a1c51-213">In dem Beispielcode unter [Ändern der Swapchaingröße und Vorgeben der Bildschirmausrichtung für die Inhalte](#resizing-the-swap-chain-and-pre-rotating-its-contents) (und im [DXGI-Swapchain-Drehungsbeispiel](http://go.microsoft.com/fwlink/p/?linkid=257600)) haben wir für alle möglichen Bildschirmausrichtungen eine spezielle Transformationsmatrix definiert.</span><span class="sxs-lookup"><span data-stu-id="a1c51-213">In the example code in [Resizing the swap chain and pre-rotating its contents](#resizing-the-swap-chain-and-pre-rotating-its-contents) (and in the [DXGI swap chain rotation sample](http://go.microsoft.com/fwlink/p/?linkid=257600)), we defined a specific transformation matrix for each possible screen orientation.</span></span> <span data-ttu-id="a1c51-214">Nun sehen wir uns die Matrizen zum Drehen von 3-D-Szenen an.</span><span class="sxs-lookup"><span data-stu-id="a1c51-214">Now, let's look at the matrixes for rotating 3-D scenes.</span></span> <span data-ttu-id="a1c51-215">Genau wie zuvor erstellen Sie für jede der vier möglichen Ausrichtungen eine Matrizengruppe.</span><span class="sxs-lookup"><span data-stu-id="a1c51-215">As before, you create a set of matrices for each of the 4 possible orientations.</span></span> <span data-ttu-id="a1c51-216">Zum Vermeiden von Rundungsfehlern und somit von kleineren visuellen Artefakten deklarieren Sie die Matrizen explizit in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="a1c51-216">To prevent rounding errors and thus minor visual artifacts, declare the matrices explicitly in your code.</span></span>

<span data-ttu-id="a1c51-217">Diese 3-D-Rundungsmatrizen werden wie folgt eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="a1c51-217">You set up these 3-D rotation matrices as follows.</span></span> <span data-ttu-id="a1c51-218">Bei den Matrizen im folgenden Codebeispiel handelt es sich um Standarddrehungsmatrizen für Drehungen der Vertizes um 0, 90, 180 und 270 Grad, die im 3D-Szenenraum der Kamera zum Definieren von Punkten dienen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-218">The matrices shown in the following code example are standard rotation matrices for 0, 90, 180, and 270 degree rotations of the vertices that define points in the camera's 3-D scene space.</span></span> <span data-ttu-id="a1c51-219">Beim Berechnen der 2D-Projektion für die Szene werden die Koordinatenwerte \[x, y, z\] aller Vertizes in der Szene mit dieser Drehungsmatrix multipliziert.</span><span class="sxs-lookup"><span data-stu-id="a1c51-219">Each vertex's \[x, y, z\] coordinate value in the scene is multiplied by this rotation matrix when the 2-D projection of the scene is computed.</span></span>

```cpp
   
// 0-degree Z-rotation
static const XMFLOAT4X4 Rotation0( 
    1.0f, 0.0f, 0.0f, 0.0f,
    0.0f, 1.0f, 0.0f, 0.0f,
    0.0f, 0.0f, 1.0f, 0.0f,
    0.0f, 0.0f, 0.0f, 1.0f
    );

// 90-degree Z-rotation
static const XMFLOAT4X4 Rotation90(
    0.0f, 1.0f, 0.0f, 0.0f,
    -1.0f, 0.0f, 0.0f, 0.0f,
    0.0f, 0.0f, 1.0f, 0.0f,
    0.0f, 0.0f, 0.0f, 1.0f
    );

// 180-degree Z-rotation
static const XMFLOAT4X4 Rotation180(
    -1.0f, 0.0f, 0.0f, 0.0f,
    0.0f, -1.0f, 0.0f, 0.0f,
    0.0f, 0.0f, 1.0f, 0.0f,
    0.0f, 0.0f, 0.0f, 1.0f
    );

// 270-degree Z-rotation
static const XMFLOAT4X4 Rotation270( 
    0.0f, -1.0f, 0.0f, 0.0f,
    1.0f, 0.0f, 0.0f, 0.0f,
    0.0f, 0.0f, 1.0f, 0.0f,
    0.0f, 0.0f, 0.0f, 1.0f
    );            
    }
```

<span data-ttu-id="a1c51-220">Der Drehungstyp wird wie folgt über einen Aufruf von [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801) für die Swapchain festgelegt:</span><span class="sxs-lookup"><span data-stu-id="a1c51-220">You set the rotation type on the swap chain with a call to [**IDXGISwapChain1::SetRotation**](https://msdn.microsoft.com/library/windows/desktop/hh446801), like this:</span></span>

`   m_swapChain->SetRotation(rotation);`

<span data-ttu-id="a1c51-221">Implementieren Sie nun in der Rendermethode einen Code, der dem folgenden Code ähnelt:</span><span class="sxs-lookup"><span data-stu-id="a1c51-221">Now, in your render method, implement some code similar to this:</span></span>

``` syntax
struct ConstantBuffer // This struct is provided for illustration.
{
    // Other constant buffer matrices and data are defined here.

    float4x4 projection; // Current matrix for projection
} ;
ConstantBuffer  m_constantBufferData;          // Constant buffer resource data

// ...

// Rotate the projection matrix as it will be used to render to the rotated swap chain.
m_constantBufferData.projection = mul(m_constantBufferData.projection, m_rotationTransform3D);
```

<span data-ttu-id="a1c51-222">Wenn Sie nun die Rendermethode aufrufen, wird die aktuelle Drehungsmatrix (gemäß Angabe durch die Klassenvariable **m\_orientationTransform3D**) mit der aktuellen Projektionsmatrix multipliziert, und die Ergebnisse dieses Vorgangs werden als neue Projektionsmatrix für den Renderer zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="a1c51-222">Now, when you call your render method, it multiplies the current rotation matrix (as specified by the class variable **m\_orientationTransform3D**) with the current projection matrix, and assigns the results of that operation as the new projection matrix for your renderer.</span></span> <span data-ttu-id="a1c51-223">Stellen Sie die Swapchain dar, um die Szene in der aktualisierten Bildschirmausrichtung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a1c51-223">Present the swap chain to see the scene in the updated display orientation.</span></span>

 

 




