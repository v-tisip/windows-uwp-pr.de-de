---
author: mtoepke
title: Initialisieren von Direct3D11
description: Hier wird veranschaulicht, wie Sie Direct3D 9-Initialisierungscode in Direct3D 11 konvertieren, und Sie erfahren, wie Sie Handles zum Direct3D-Gerät und zum Gerätekontext abrufen und DXGI zum Einrichten einer Swapchain verwenden.
ms.assetid: 1bd5e8b7-fd9d-065c-9ff3-1a9b1c90da29
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Direct3D 11, Initialisierung, portieren, Direct3D 9
ms.localizationpriority: medium
ms.openlocfilehash: 5f6aa5bca3ecc242e90b42081a0111358afdfa9b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5571921"
---
# <a name="initialize-direct3d-11"></a><span data-ttu-id="6fdf6-104">Initialisieren von Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-104">Initialize Direct3D 11</span></span>



**<span data-ttu-id="6fdf6-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="6fdf6-105">Summary</span></span>**

-   <span data-ttu-id="6fdf6-106">Teil 1: Initialisieren von Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-106">Part 1: Initialize Direct3D 11</span></span>
-   [<span data-ttu-id="6fdf6-107">Teil 2: Konvertieren des Renderingframeworks</span><span class="sxs-lookup"><span data-stu-id="6fdf6-107">Part 2: Convert the rendering framework</span></span>](simple-port-from-direct3d-9-to-11-1-part-2--rendering.md)
-   [<span data-ttu-id="6fdf6-108">Teil 3: Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="6fdf6-108">Part 3: Port the game loop</span></span>](simple-port-from-direct3d-9-to-11-1-part-3--viewport-and-game-loop.md)


<span data-ttu-id="6fdf6-109">Hier wird veranschaulicht, wie Sie Direct3D 9-Initialisierungscode in Direct3D 11 konvertieren, und Sie erfahren, wie Sie Handles zum Direct3D-Gerät und zum Gerätekontext abrufen und DXGI zum Einrichten einer Swapchain verwenden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-109">Shows how to convert Direct3D 9 initialization code to Direct3D 11, including how to get handles to the Direct3D device and the device context and how to use DXGI to set up a swap chain.</span></span> <span data-ttu-id="6fdf6-110">Teil1 der exemplarischen Vorgehensweise [Portieren einer einfachen Direct3D9-App zu DirectX11 und UWP (Universelle Windows-Plattform)](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span><span class="sxs-lookup"><span data-stu-id="6fdf6-110">Part 1 of the [Port a simple Direct3D 9 app to DirectX 11 and Universal Windows Platform (UWP)](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough.</span></span>

## <a name="initialize-the-direct3d-device"></a><span data-ttu-id="6fdf6-111">Initialisieren des Direct3D-Geräts</span><span class="sxs-lookup"><span data-stu-id="6fdf6-111">Initialize the Direct3D device</span></span>


<span data-ttu-id="6fdf6-112">In Direct3D9 wurde ein Handle zum Direct3D-Gerät erstellt, indem [**IDirect3D9::CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/bb174313) aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-112">In Direct3D 9, we created a handle to the Direct3D device by calling [**IDirect3D9::CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/bb174313).</span></span> <span data-ttu-id="6fdf6-113">Zuerst wurde ein Zeiger auf [**IDirect3D9 interface**](https://msdn.microsoft.com/library/windows/desktop/bb174300) abgerufen und eine Anzahl von Parametern angegeben, um die Konfiguration des Direct3D-Geräts und der Swapchain zu steuern.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-113">We started by getting a pointer to [**IDirect3D9 interface**](https://msdn.microsoft.com/library/windows/desktop/bb174300) and we specified a number of parameters to control the configuration of the Direct3D device and the swap chain.</span></span> <span data-ttu-id="6fdf6-114">Vorher wurde [**GetDeviceCaps**](https://msdn.microsoft.com/library/windows/desktop/dd144877) aufgerufen, um sicherzustellen, dass vom Gerät keine unmöglichen Vorgänge verlangt wurden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-114">Before doing this we called [**GetDeviceCaps**](https://msdn.microsoft.com/library/windows/desktop/dd144877) to make sure we weren't asking the device to do something it couldn't do.</span></span>

<span data-ttu-id="6fdf6-115">Direct3D9</span><span class="sxs-lookup"><span data-stu-id="6fdf6-115">Direct3D 9</span></span>

```cpp
UINT32 AdapterOrdinal = 0;
D3DDEVTYPE DeviceType = D3DDEVTYPE_HAL;
D3DCAPS9 caps;
m_pD3D->GetDeviceCaps(AdapterOrdinal, DeviceType, &caps); // caps bits

D3DPRESENT_PARAMETERS params;
ZeroMemory(&params, sizeof(D3DPRESENT_PARAMETERS));

// Swap chain parameters:
params.hDeviceWindow = m_hWnd;
params.AutoDepthStencilFormat = D3DFMT_D24X8;
params.BackBufferFormat = D3DFMT_X8R8G8B8;
params.MultiSampleQuality = D3DMULTISAMPLE_NONE;
params.MultiSampleType = D3DMULTISAMPLE_NONE;
params.SwapEffect = D3DSWAPEFFECT_DISCARD;
params.Windowed = true;
params.PresentationInterval = 0;
params.BackBufferCount = 2;
params.BackBufferWidth = 0;
params.BackBufferHeight = 0;
params.EnableAutoDepthStencil = true;
params.Flags = 2;

m_pD3D->CreateDevice(
    0,
    D3DDEVTYPE_HAL,
    m_hWnd,
    64,
    &params,
    &m_pd3dDevice
    );
```

<span data-ttu-id="6fdf6-116">In Direct3D11 werden der Gerätekontext und die Grafikinfrastruktur als separat vom eigentlichen Gerät angesehen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-116">In Direct3D 11, the device context and graphics infrastructure is considered separate from the device itself.</span></span> <span data-ttu-id="6fdf6-117">Die Initialisierung ist in mehrere Schritte unterteilt.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-117">Initialization is divided into multiple steps.</span></span>

<span data-ttu-id="6fdf6-118">Zuerst wird das Gerät erstellt.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-118">First we create the device.</span></span> <span data-ttu-id="6fdf6-119">Dazu rufen wir eine Liste der Featureebenen ab, die vom Gerät unterstützt werden. Dies sind bereits nahezu alle Informationen, die in Bezug auf die GPU benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-119">We get a list of the feature levels the device supports - this informs most of what we need to know about the GPU.</span></span> <span data-ttu-id="6fdf6-120">Allein für den Zugriff auf Direct3D muss auch keine Schnittstelle erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-120">Also, we don't need to create an interface just to access Direct3D.</span></span> <span data-ttu-id="6fdf6-121">Stattdessen wird die [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082)-Kern-API verwendet.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-121">Instead we use the [**D3D11CreateDevice**](https://msdn.microsoft.com/library/windows/desktop/ff476082) core API.</span></span> <span data-ttu-id="6fdf6-122">So erhalten wir einen Handle zum Gerät und den unmittelbaren Kontext des Geräts.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-122">This gives us a handle to the device and the device's immediate context.</span></span> <span data-ttu-id="6fdf6-123">Der Gerätekontext wird verwendet, um den Pipelinestatus festzulegen und Renderbefehle zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-123">The device context is used to set pipeline state and generate rendering commands.</span></span>

<span data-ttu-id="6fdf6-124">Nach dem Erstellen des Direct3D11-Geräts und -Kontexts kann die COM-Zeigerfunktion zum Abrufen der jeweils aktuellen Version der Schnittstellen verwendet werden, die über zusätzliche Funktionen verfügt. Dies ist stets zu empfehlen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-124">After creating the Direct3D 11 device and context, we can take advantage of COM pointer functionality to get the most recent version of the interfaces, which include additional capability and are always recommended.</span></span>

> <span data-ttu-id="6fdf6-125">**Hinweis:**  D3D\_FEATURE\_LEVEL\_9\_1 (entspricht Shadermodell 2.0) ist die mindestens notwendige Stufe, Ihr Microsoft Store-Spiel erforderlich ist, um zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-125">**Note** D3D\_FEATURE\_LEVEL\_9\_1 (which corresponds to shader model 2.0) is the minimum level your Microsoft Store game is required to support.</span></span> <span data-ttu-id="6fdf6-126">(Die ARM-Pakete des Spiels erhalten keine Zertifizierung, wenn 9\_1 nicht unterstützt wird.) Wenn das Spiel auch einen Renderpfad für die Features von Shadermodell3 enthält, sollten Sie D3D_FEATURE\_LEVEL\_9\_3 in das Array einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-126">(Your game's ARM packages will fail certification if you don't support 9\_1.) If your game also includes a rendering path for shader model 3 features, then you should include D3D\_FEATURE\_LEVEL\_9\_3 in the array.</span></span>

 

<span data-ttu-id="6fdf6-127">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-127">Direct3D 11</span></span>

```cpp
// This flag adds support for surfaces with a different color channel 
// ordering than the API default. It is required for compatibility with
// Direct2D.
UINT creationFlags = D3D11_CREATE_DEVICE_BGRA_SUPPORT;

#if defined(_DEBUG)
// If the project is in a debug build, enable debugging via SDK Layers.
creationFlags |= D3D11_CREATE_DEVICE_DEBUG;
#endif

// This example only uses feature level 9.1.
D3D_FEATURE_LEVEL featureLevels[] = 
{
    D3D_FEATURE_LEVEL_9_1
};

// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;
D3D11CreateDevice(
    nullptr, // Specify nullptr to use the default adapter.
    D3D_DRIVER_TYPE_HARDWARE,
    nullptr,
    creationFlags,
    featureLevels,
    ARRAYSIZE(featureLevels),
    D3D11_SDK_VERSION, // UWP apps must set this to D3D11_SDK_VERSION.
    &device, // Returns the Direct3D device created.
    nullptr,
    &context // Returns the device immediate context.
    );

// Store pointers to the Direct3D 11.2 API device and immediate context.
device.As(&m_d3dDevice);

context.As(&m_d3dContext);
```

## <a name="create-a-swap-chain"></a><span data-ttu-id="6fdf6-128">Erstellen einer Swapchain</span><span class="sxs-lookup"><span data-stu-id="6fdf6-128">Create a swap chain</span></span>


<span data-ttu-id="6fdf6-129">Direct3D 11 enthält eine Geräte-API mit der Bezeichnung DirectX Graphics Infrastructure (DXGI).</span><span class="sxs-lookup"><span data-stu-id="6fdf6-129">Direct3D 11 includes a device API called DirectX graphics infrastructure (DXGI).</span></span> <span data-ttu-id="6fdf6-130">Mithilfe der DXGI-Schnittstelle können Sie (beispielsweise) steuern, wie die Swapchain konfiguriert wird, und freigegebene Geräte einrichten.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-130">The DXGI interface allows us to (for example) control how the swap chain is configured and set up shared devices.</span></span> <span data-ttu-id="6fdf6-131">Bei diesem Schritt der Initialisierung von Direct3D wird DXGI zum Erstellen einer Swapchain verwendet.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-131">At this step in initializing Direct3D, we're going to use DXGI to create a swap chain.</span></span> <span data-ttu-id="6fdf6-132">Seit der Erstellung des Geräts können wir eine Schnittstellenkette zurück zum DXGI-Adapter verfolgen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-132">Since we created the device, we can follow an interface chain back to the DXGI adapter.</span></span>

<span data-ttu-id="6fdf6-133">Vom Direct3D-Gerät wird eine COM-Schnittstelle für DXGI implementiert.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-133">The Direct3D device implements a COM interface for DXGI.</span></span> <span data-ttu-id="6fdf6-134">Zuerst muss diese Schnittstelle abgerufen und verwendet werden, um den DXGI-Adapter anzufordern, mit dem das Gerät gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-134">First we need to get that interface and use it to request the DXGI adapter hosting the device.</span></span> <span data-ttu-id="6fdf6-135">Anschließend wird der DXGI-Adapter zum Erstellen einer DXGI-Factory genutzt.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-135">Then we use the DXGI adapter to create a DXGI factory.</span></span>

> <span data-ttu-id="6fdf6-136">**Hinweis:**  Hierbei handelt es sich um COM-Schnittstellen, sodass Ihre erste Antwort [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521)verwenden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-136">**Note** These are COM interfaces so your first response might be to use [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span> <span data-ttu-id="6fdf6-137">Stattdessen sollten Sie intelligente [**Microsoft::WRL::ComPtr**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx)-Zeiger nutzen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-137">You should use [**Microsoft::WRL::ComPtr**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx) smart pointers instead.</span></span> <span data-ttu-id="6fdf6-138">Rufen Sie anschließend einfach die [**As()**](https://msdn.microsoft.com/library/windows/apps/br230426.aspx)-Methode auf, und stellen Sie einen leeren COM-Zeiger mit dem passenden Schnittstellentyp bereit.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-138">Then just call the [**As()**](https://msdn.microsoft.com/library/windows/apps/br230426.aspx) method, supplying an empty COM pointer of the correct interface type.</span></span>

 

**<span data-ttu-id="6fdf6-139">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-139">Direct3D 11</span></span>**

```cpp
ComPtr<IDXGIDevice2> dxgiDevice;
m_d3dDevice.As(&dxgiDevice);

// Then, the adapter hosting the device;
ComPtr<IDXGIAdapter> dxgiAdapter;
dxgiDevice->GetAdapter(&dxgiAdapter);

// Then, the factory that created the adapter interface:
ComPtr<IDXGIFactory2> dxgiFactory;
dxgiAdapter->GetParent(
    __uuidof(IDXGIFactory2),
    &dxgiFactory
    );
```

<span data-ttu-id="6fdf6-140">Da die DXGI-Factory jetzt vorhanden ist, können wir sie zum Erstellen der Swapchain verwenden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-140">Now that we have the DXGI factory, we can use it to create the swap chain.</span></span> <span data-ttu-id="6fdf6-141">Als Nächstes werden die Parameter der Swapchain definiert.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-141">Let's define the swap chain parameters.</span></span> <span data-ttu-id="6fdf6-142">Das Oberflächenformat muss angegeben werden, und wir wählen [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059), weil es mit Direct2D kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-142">We need to specify the surface format; we'll choose [**DXGI\_FORMAT\_B8G8R8A8\_UNORM**](https://msdn.microsoft.com/library/windows/desktop/bb173059) because it's compatible with Direct2D.</span></span> <span data-ttu-id="6fdf6-143">Die Anzeigeskalierung, Multisampling und das Stereorendering werden deaktiviert, weil diese Funktionen in diesem Beispiel nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-143">We'll turn off display scaling, multisampling, and stereo rendering because they aren't used in this example.</span></span> <span data-ttu-id="6fdf6-144">Da die Ausführung direkt in einem CoreWindow-Objekt erfolgt, können wir die Breite und Höhe auf der Einstellung 0 belassen und automatisch Vollbildwerte erhalten.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-144">Since we are running directly in a CoreWindow we can leave the width and height set to 0 and get full-screen values automatically.</span></span>

> <span data-ttu-id="6fdf6-145">**Hinweis:**  immer den *SDKVersion* -Parameter für UWP-apps auf D3D11\_SDK\_VERSION festlegen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-145">**Note** Always set the *SDKVersion* parameter to D3D11\_SDK\_VERSION for UWP apps.</span></span>

 

**<span data-ttu-id="6fdf6-146">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-146">Direct3D 11</span></span>**

```cpp
ComPtr<IDXGISwapChain1> swapChain;
dxgiFactory->CreateSwapChainForCoreWindow(
    m_d3dDevice.Get(),
    reinterpret_cast<IUnknown*>(window),
    &swapChainDesc,
    nullptr,
    &swapChain
    );
swapChain.As(&m_swapChain);
```

<span data-ttu-id="6fdf6-147">Um sicherzustellen, dass nur so häufig Rendervorgänge ausgeführt werden, wie diese vom Bildschirm auch angezeigt werden können, legen wir die Framelatenz auf1 fest und verwenden [**DXGI\_SWAP\_EFFECT\_FLIP\_SEQUENTIAL**](https://msdn.microsoft.com/library/windows/desktop/bb173077).</span><span class="sxs-lookup"><span data-stu-id="6fdf6-147">To ensure we aren't rendering more often than the screen can actually display, we set frame latency to 1 and use [**DXGI\_SWAP\_EFFECT\_FLIP\_SEQUENTIAL**](https://msdn.microsoft.com/library/windows/desktop/bb173077).</span></span> <span data-ttu-id="6fdf6-148">So kann Energie gespart werden. Außerdem ist dies eine Anforderung für die Store-Zertifizierung. Weitere Informationen zur Darstellung auf dem Bildschirm erhalten Sie in Teil 2 dieser exemplarischen Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-148">This saves power and is a store certification requirement; we'll learn more about presenting to the screen in part 2 of this walkthrough.</span></span>

> <span data-ttu-id="6fdf6-149">**Hinweis:**  können Sie multithreading verwenden (z. B. [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/br229642) Arbeitsaufgaben) um weiterarbeiten während der Renderthread blockiert ist.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-149">**Note** You can use multithreading (for example, [**ThreadPool**](https://msdn.microsoft.com/library/windows/apps/br229642) work items) to continue other work while the rendering thread is blocked.</span></span>

 

**<span data-ttu-id="6fdf6-150">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-150">Direct3D 11</span></span>**

```cpp
dxgiDevice->SetMaximumFrameLatency(1);
```

<span data-ttu-id="6fdf6-151">Als Nächstes können wir den Hintergrundpuffer für das Rendern einrichten.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-151">Now we can set up the back buffer for rendering.</span></span>

## <a name="configure-the-back-buffer-as-a-render-target"></a><span data-ttu-id="6fdf6-152">Konfigurieren des Hintergrundpuffers als Renderziel</span><span class="sxs-lookup"><span data-stu-id="6fdf6-152">Configure the back buffer as a render target</span></span>


<span data-ttu-id="6fdf6-153">Zuerst müssen wir ein Handle zum Hintergrundpuffer abrufen.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-153">First we have to get a handle to the back buffer.</span></span> <span data-ttu-id="6fdf6-154">(Beachten Sie, dass der Hintergrundpuffer im Besitz der DXGI-Swapchain ist, während der Besitzer unter DirectX9 das Direct3D-Gerät war.) Anschließend wird das Direct3D-Gerät angewiesen, es als Renderziel zu verwenden, indem mithilfe des Hintergrundpuffers eine Renderziel*ansicht* erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-154">(Note that the back buffer is owned by the DXGI swap chain, whereas in DirectX 9 it was owned by the Direct3D device.) Then we tell the Direct3D device to use it as the render target by creating a render target *view* using the back buffer.</span></span>

**<span data-ttu-id="6fdf6-155">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-155">Direct3D 11</span></span>**

```cpp
ComPtr<ID3D11Texture2D> backBuffer;
m_swapChain->GetBuffer(
    0,
    __uuidof(ID3D11Texture2D),
    &backBuffer
    );

// Create a render target view on the back buffer.
m_d3dDevice->CreateRenderTargetView(
    backBuffer.Get(),
    nullptr,
    &m_renderTargetView
    );
```

<span data-ttu-id="6fdf6-156">Jetzt kommt der Gerätekontext ins Spiel.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-156">Now the device context comes into play.</span></span> <span data-ttu-id="6fdf6-157">Direct3D wird angewiesen, die neu erstellte Renderzielansicht zu nutzen, indem die Gerätekontextschnittstelle verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-157">We tell Direct3D to use our newly-created render target view by using the device context interface.</span></span> <span data-ttu-id="6fdf6-158">Wir rufen die Breite und Höhe des Hintergrundpuffers ab, damit das gesamte Fenster als Viewport genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-158">We'll retrieve the width and height of the back buffer so that we can target the whole window as our viewport.</span></span> <span data-ttu-id="6fdf6-159">Beachten Sie, dass der Hintergrundpuffer an die Swapchain angefügt ist. Wenn sich also die Fenstergröße ändert (z.B. wenn Benutzer das Spielfenster auf einen anderen Monitor ziehen), müssen die Größe des Hintergrundpuffers geändert und einige Setupschritte ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-159">Note that the back buffer is attached to the swap chain, so if the window size changes (for example, the user drags the game window to another monitor) the back buffer will need to be resized and some setup will need to be redone.</span></span>

**<span data-ttu-id="6fdf6-160">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="6fdf6-160">Direct3D 11</span></span>**

```cpp
D3D11_TEXTURE2D_DESC backBufferDesc = {0};
backBuffer->GetDesc(&backBufferDesc);

CD3D11_VIEWPORT viewport(
    0.0f,
    0.0f,
    static_cast<float>(backBufferDesc.Width),
    static_cast<float>(backBufferDesc.Height)
    );

m_d3dContext->RSSetViewports(1, &viewport);
```

<span data-ttu-id="6fdf6-161">Da wir jetzt über ein Gerätehandle und ein Vollbild-Renderziel verfügen, sind wir bereit zum Laden und Zeichnen der Geometrie.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-161">Now that we have a device handle and a full-screen render target, we are ready to load and draw geometry.</span></span> <span data-ttu-id="6fdf6-162">Fahren Sie mit [Teil2: Rendern](simple-port-from-direct3d-9-to-11-1-part-2--rendering.md) fort.</span><span class="sxs-lookup"><span data-stu-id="6fdf6-162">Continue to [Part 2: Rendering](simple-port-from-direct3d-9-to-11-1-part-2--rendering.md).</span></span>

 

 




