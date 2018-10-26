---
author: mtoepke
title: Erstellen von Tiefenpuffer-Geräteressourcen
description: Hier erfahren Sie, wie Sie die zum Unterstützen von Tiefentests für Schattenvolumen erforderlichen Direct3D-Geräteressourcen erstellen.
ms.assetid: 86d5791b-1faa-17e4-44a8-bbba07062756
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Direct3D, Tiefenpuffer
ms.localizationpriority: medium
ms.openlocfilehash: 091ac04b2a41c54fbce7294bcf6651f4ad4aafd2
ms.sourcegitcommit: d0e836dfc937ebf7dfa9c424620f93f3c8e0a7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5641917"
---
# <a name="create-depth-buffer-device-resources"></a><span data-ttu-id="09f23-104">Erstellen von Tiefenpuffer-Geräteressourcen</span><span class="sxs-lookup"><span data-stu-id="09f23-104">Create depth buffer device resources</span></span>




<span data-ttu-id="09f23-105">Hier erfahren Sie, wie Sie die zum Unterstützen von Tiefentests für Schattenvolumen erforderlichen Direct3D-Geräteressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="09f23-105">Learn how to create the Direct3D device resources necessary to support depth testing for shadow volumes.</span></span> <span data-ttu-id="09f23-106">Teil 1 von [Exemplarische Vorgehensweise: Implementieren von Schattenvolumen mithilfe von Tiefenpuffern in Direct3D11](implementing-depth-buffers-for-shadow-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="09f23-106">Part 1 of [Walkthrough: Implement shadow volumes using depth buffers in Direct3D 11](implementing-depth-buffers-for-shadow-mapping.md).</span></span>

## <a name="resources-youll-need"></a><span data-ttu-id="09f23-107">Erforderliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="09f23-107">Resources you'll need</span></span>


<span data-ttu-id="09f23-108">Zum Rendern einer Tiefenkarte für Schattenvolumen benötigen Sie die folgenden geräteabhängigen Direct3D-Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="09f23-108">Rendering a depth map for shadow volumes requires the following Direct3D device-dependent resources:</span></span>

-   <span data-ttu-id="09f23-109">Eine Ressource (Puffer) für die Tiefenkarte</span><span class="sxs-lookup"><span data-stu-id="09f23-109">A resource (buffer) for the depth map</span></span>
-   <span data-ttu-id="09f23-110">Eine Tiefenschablonenansicht und eine Shaderressourcenansicht für die Ressource</span><span class="sxs-lookup"><span data-stu-id="09f23-110">A depth stencil view and shader resource view for the resource</span></span>
-   <span data-ttu-id="09f23-111">Ein Vergleichs-Samplerstatusobjekt</span><span class="sxs-lookup"><span data-stu-id="09f23-111">A comparison sampler state object</span></span>
-   <span data-ttu-id="09f23-112">Konstantenpuffer für POV-Beleuchtungsmatrizen</span><span class="sxs-lookup"><span data-stu-id="09f23-112">Constant buffers for light POV matrices</span></span>
-   <span data-ttu-id="09f23-113">Einen Viewport zum Rendern der Schattenkarte (normalerweise ein quadratischer Viewport)</span><span class="sxs-lookup"><span data-stu-id="09f23-113">A viewport for rendering the shadow map (typically a square viewport)</span></span>
-   <span data-ttu-id="09f23-114">Ein Renderstatusobjekt zum Aktivieren von Frontface-Culling</span><span class="sxs-lookup"><span data-stu-id="09f23-114">A rendering state object to enable front face culling</span></span>
-   <span data-ttu-id="09f23-115">Außerdem benötigen Sie ein Renderstatusobjekt, um wieder zum Backface-Culling zu wechseln, falls Sie noch keines verwenden.</span><span class="sxs-lookup"><span data-stu-id="09f23-115">You will also need a rendering state object to switch back to back face culling, if you don't already use one.</span></span>

<span data-ttu-id="09f23-116">Beachten Sie, dass die Erstellung dieser Ressourcen in eine geräteabhängige Ressourcenerstellungsroutine eingebunden werden muss. Auf diese Weise kann Ihr Renderer die Ressourcen neu erstellen, wenn (beispielsweise) ein neuer Gerätetreiber installiert wird oder der Benutzer Ihre App auf einen Monitor verschiebt, der an einen anderen Grafikadapter angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="09f23-116">Note that creation of these resources needs to be included in a device-dependent resource creation routine, that way your renderer can recreate them if (for example) a new device driver is installed, or the user moves your app to a monitor attached to a different graphics adapter.</span></span>

## <a name="check-feature-support"></a><span data-ttu-id="09f23-117">Überprüfen unterstützter Features</span><span class="sxs-lookup"><span data-stu-id="09f23-117">Check feature support</span></span>


<span data-ttu-id="09f23-118">Rufen Sie vor dem Erstellen der Tiefenkarte die [**CheckFeatureSupport**](https://msdn.microsoft.com/library/windows/desktop/ff476497)-Methode für das Direct3D-Gerät auf, fordern Sie **D3D11\_FEATURE\_D3D9\_SHADOW\_SUPPORT** an, und stellen Sie eine [**D3D11\_FEATURE\_DATA\_D3D9\_SHADOW\_SUPPORT**](https://msdn.microsoft.com/library/windows/desktop/jj247569)-Struktur bereit.</span><span class="sxs-lookup"><span data-stu-id="09f23-118">Before creating the depth map, call the [**CheckFeatureSupport**](https://msdn.microsoft.com/library/windows/desktop/ff476497) method on the Direct3D device, request **D3D11\_FEATURE\_D3D9\_SHADOW\_SUPPORT**, and provide a [**D3D11\_FEATURE\_DATA\_D3D9\_SHADOW\_SUPPORT**](https://msdn.microsoft.com/library/windows/desktop/jj247569) structure.</span></span>

```cpp
D3D11_FEATURE_DATA_D3D9_SHADOW_SUPPORT isD3D9ShadowSupported;
ZeroMemory(&isD3D9ShadowSupported, sizeof(isD3D9ShadowSupported));
pD3DDevice->CheckFeatureSupport(
    D3D11_FEATURE_D3D9_SHADOW_SUPPORT,
    &isD3D9ShadowSupported,
    sizeof(D3D11_FEATURE_D3D9_SHADOW_SUPPORT)
    );

if (isD3D9ShadowSupported.SupportsDepthAsTextureWithLessEqualComparisonFilter)
{
    // Init shadow map resources

```

<span data-ttu-id="09f23-119">Wenn dieses Feature nicht unterstützt wird, dürfen Sie nicht versuchen, Shader zu laden, die für das Shadermodell 4 Ebene 9\_x kompiliert wurden, bei dem Samplevergleichsfunktionen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="09f23-119">If this feature is not supported, do not try to load shaders compiled for shader model 4 level 9\_x that call sample comparison functions.</span></span> <span data-ttu-id="09f23-120">Eine fehlende Unterstützung für dieses Feature bedeutet in vielen Fällen, dass es sich bei der GPU um ein älteres Gerät mit einem Treiber handelt, der nicht zur Unterstützung von mindestens WDDM 1.2 aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="09f23-120">In many cases, lack of support for this feature means that the GPU is a legacy device with a driver that isn't updated to support at least WDDM 1.2.</span></span> <span data-ttu-id="09f23-121">Wenn das Gerät mindestens die Featureebene 10\_0 unterstützt, können Sie stattdessen einen Samplevergleichsshader laden, der für das Shadermodell 4\_0 kompiliert ist.</span><span class="sxs-lookup"><span data-stu-id="09f23-121">If the device supports at least feature level 10\_0 then you can load a sample comparison shader compiled for shader model 4\_0 instead.</span></span>

## <a name="create-depth-buffer"></a><span data-ttu-id="09f23-122">Erstellen des Tiefenpuffers</span><span class="sxs-lookup"><span data-stu-id="09f23-122">Create depth buffer</span></span>


<span data-ttu-id="09f23-123">Versuchen Sie als Erstes, die Tiefenkarte in einem Tiefenformat mit einer höheren Genauigkeit zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="09f23-123">First, try creating the depth map with a higher-precision depth format.</span></span> <span data-ttu-id="09f23-124">Richten Sie zuerst die entsprechenden Eigenschaften der Shaderressourcenansicht ein.</span><span class="sxs-lookup"><span data-stu-id="09f23-124">Set up matching shader resource view properties first.</span></span> <span data-ttu-id="09f23-125">Falls die Erstellung der Ressource fehlschlägt (z.B. weil zu wenig Gerätespeicher verfügbar ist oder ein Format von der Hardware nicht unterstützt wird), können Sie es mit einem Format mit geringerer Genauigkeit probieren und die Eigenschaften entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="09f23-125">If the resource creation fails, for example due to low device memory or a format that the hardware doesn't support, try a lower-precision format and change properties to match.</span></span>

<span data-ttu-id="09f23-126">Dieser Schritt ist optional, wenn Sie nur ein Format mit geringerer Genauigkeit benötigen (z.B. wenn Sie auf Geräten mit Direct3D-Funktionsebene9\_1 und mittlerer Auflösung rendern).</span><span class="sxs-lookup"><span data-stu-id="09f23-126">This step is optional if you only need a low-precision depth format, for example when rendering on medium-resolution Direct3D feature level 9\_1 devices.</span></span>

```cpp
D3D11_TEXTURE2D_DESC shadowMapDesc;
ZeroMemory(&shadowMapDesc, sizeof(D3D11_TEXTURE2D_DESC));
shadowMapDesc.Format = DXGI_FORMAT_R24G8_TYPELESS;
shadowMapDesc.MipLevels = 1;
shadowMapDesc.ArraySize = 1;
shadowMapDesc.SampleDesc.Count = 1;
shadowMapDesc.BindFlags = D3D11_BIND_SHADER_RESOURCE | D3D11_BIND_DEPTH_STENCIL;
shadowMapDesc.Height = static_cast<UINT>(m_shadowMapDimension);
shadowMapDesc.Width = static_cast<UINT>(m_shadowMapDimension);

HRESULT hr = pD3DDevice->CreateTexture2D(
    &shadowMapDesc,
    nullptr,
    &m_shadowMap
    );
```

<span data-ttu-id="09f23-127">Erstellen Sie anschließend die Ressourcenansichten.</span><span class="sxs-lookup"><span data-stu-id="09f23-127">Then create the resource views.</span></span> <span data-ttu-id="09f23-128">Legen Sie den Mip-Slice für die Ansicht der Tiefenschablone auf null und die Mip-Ebenen für die Shaderressourcenansicht auf 1 fest.</span><span class="sxs-lookup"><span data-stu-id="09f23-128">Set the mip slice to zero on the depth stencil view and set mip levels to 1 on the shader resource view.</span></span> <span data-ttu-id="09f23-129">Beide haben die Texturdimension TEXTURE2D und müssen ein entsprechendes [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059) verwenden.</span><span class="sxs-lookup"><span data-stu-id="09f23-129">Both have a texture dimension of TEXTURE2D, and both need to use a matching [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059).</span></span>

```cpp
D3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc;
ZeroMemory(&depthStencilViewDesc, sizeof(D3D11_DEPTH_STENCIL_VIEW_DESC));
depthStencilViewDesc.Format = DXGI_FORMAT_D24_UNORM_S8_UINT;
depthStencilViewDesc.ViewDimension = D3D11_DSV_DIMENSION_TEXTURE2D;
depthStencilViewDesc.Texture2D.MipSlice = 0;

D3D11_SHADER_RESOURCE_VIEW_DESC shaderResourceViewDesc;
ZeroMemory(&shaderResourceViewDesc, sizeof(D3D11_SHADER_RESOURCE_VIEW_DESC));
shaderResourceViewDesc.ViewDimension = D3D11_SRV_DIMENSION_TEXTURE2D;
shaderResourceViewDesc.Format = DXGI_FORMAT_R24_UNORM_X8_TYPELESS;
shaderResourceViewDesc.Texture2D.MipLevels = 1;

hr = pD3DDevice->CreateDepthStencilView(
    m_shadowMap.Get(),
    &depthStencilViewDesc,
    &m_shadowDepthView
    );

hr = pD3DDevice->CreateShaderResourceView(
    m_shadowMap.Get(),
    &shaderResourceViewDesc,
    &m_shadowResourceView
    );
```

## <a name="create-comparison-state"></a><span data-ttu-id="09f23-130">Erstellen eines Vergleichsstatus</span><span class="sxs-lookup"><span data-stu-id="09f23-130">Create comparison state</span></span>


<span data-ttu-id="09f23-131">Erstellen Sie jetzt das Vergleichs-Samplerstatusobjekt.</span><span class="sxs-lookup"><span data-stu-id="09f23-131">Now create the comparison sampler state object.</span></span> <span data-ttu-id="09f23-132">Auf Featureebene 9\_1 wird nur D3D11\_COMPARISON\_LESS\_EQUAL unterstützt.</span><span class="sxs-lookup"><span data-stu-id="09f23-132">Feature level 9\_1 only supports D3D11\_COMPARISON\_LESS\_EQUAL.</span></span> <span data-ttu-id="09f23-133">Die Filterungsoptionen werden ausführlicher unter [Unterstützen von Schattenkarten auf unterschiedlicher Hardware](target-a-range-of-hardware.md) erläutert. Oder Sie setzen einfach Punktfilterung ein, um schnellere Schattenkarten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="09f23-133">Filtering choices are explained more in [Supporting shadow maps on a range of hardware](target-a-range-of-hardware.md) - or you can just pick point filtering for faster shadow maps.</span></span>

<span data-ttu-id="09f23-134">Hinweis: Sie können den D3D11\_TEXTURE\_ADDRESS\_BORDER-Adressmodus angeben und auf Geräten mit Funktionsebene9\_1 verwenden.</span><span class="sxs-lookup"><span data-stu-id="09f23-134">Note that you can specify the D3D11\_TEXTURE\_ADDRESS\_BORDER address mode and it will work on feature level 9\_1 devices.</span></span> <span data-ttu-id="09f23-135">Dies gilt für Pixelshader, die vor dem Tiefentest nicht testen, ob sich das Pixel im Ansichtsfrustum der Beleuchtung befindet.</span><span class="sxs-lookup"><span data-stu-id="09f23-135">This applies to pixel shaders that don't test whether the pixel is in the light's view frustum before doing the depth test.</span></span> <span data-ttu-id="09f23-136">Wenn Sie für jeden Rand 0 oder 1 angeben, können Sie steuern, ob Pixel außerhalb des Lichtkegels den Tiefentest bestehen – was bedeutet, ob sie beleuchtet werden oder sich im Schatten befinden.</span><span class="sxs-lookup"><span data-stu-id="09f23-136">By specifying 0 or 1 for each border, you can control whether pixels outside the light's view frustum pass or fail the depth test, and therefore whether they are lit or in shadow.</span></span>

<span data-ttu-id="09f23-137">Auf Funktionsebene9\_1 müssen Sie sicherstellen, dass folgende erforderliche Werte festgelegt sind: **MinLOD** ist auf NULL festgelegt, **MaxLOD** ist auf **D3D11\_FLOAT32\_MAX** festgelegt, und **MaxAnisotropy** ist auf NULL festgelegt.</span><span class="sxs-lookup"><span data-stu-id="09f23-137">On feature level 9\_1, the following required values must be set: **MinLOD** is set to zero, **MaxLOD** is set to **D3D11\_FLOAT32\_MAX**, and **MaxAnisotropy** is set to zero.</span></span>

```cpp
D3D11_SAMPLER_DESC comparisonSamplerDesc;
ZeroMemory(&comparisonSamplerDesc, sizeof(D3D11_SAMPLER_DESC));
comparisonSamplerDesc.AddressU = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.AddressV = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.AddressW = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.BorderColor[0] = 1.0f;
comparisonSamplerDesc.BorderColor[1] = 1.0f;
comparisonSamplerDesc.BorderColor[2] = 1.0f;
comparisonSamplerDesc.BorderColor[3] = 1.0f;
comparisonSamplerDesc.MinLOD = 0.f;
comparisonSamplerDesc.MaxLOD = D3D11_FLOAT32_MAX;
comparisonSamplerDesc.MipLODBias = 0.f;
comparisonSamplerDesc.MaxAnisotropy = 0;
comparisonSamplerDesc.ComparisonFunc = D3D11_COMPARISON_LESS_EQUAL;
comparisonSamplerDesc.Filter = D3D11_FILTER_COMPARISON_MIN_MAG_MIP_POINT;

// Point filtered shadows can be faster, and may be a good choice when
// rendering on hardware with lower feature levels. This sample has a
// UI option to enable/disable filtering so you can see the difference
// in quality and speed.

DX::ThrowIfFailed(
    pD3DDevice->CreateSamplerState(
        &comparisonSamplerDesc,
        &m_comparisonSampler_point
        )
    );
```

## <a name="create-render-states"></a><span data-ttu-id="09f23-138">Erstellen von Renderstatus</span><span class="sxs-lookup"><span data-stu-id="09f23-138">Create render states</span></span>


<span data-ttu-id="09f23-139">Erstellen Sie jetzt einen Renderstatus, den Sie zum Aktivieren von Frontface-Culling verwenden können.</span><span class="sxs-lookup"><span data-stu-id="09f23-139">Now create a render state you can use to enable front face culling.</span></span> <span data-ttu-id="09f23-140">Beachten Sie, dass **DepthClipEnable** bei Geräten mit Funktionsebene9\_1 auf **true** festgelegt werden muss.</span><span class="sxs-lookup"><span data-stu-id="09f23-140">Note that feature level 9\_1 devices require **DepthClipEnable** set to **true**.</span></span>

```cpp
D3D11_RASTERIZER_DESC drawingRenderStateDesc;
ZeroMemory(&drawingRenderStateDesc, sizeof(D3D11_RASTERIZER_DESC));
drawingRenderStateDesc.CullMode = D3D11_CULL_BACK;
drawingRenderStateDesc.FillMode = D3D11_FILL_SOLID;
drawingRenderStateDesc.DepthClipEnable = true; // Feature level 9_1 requires DepthClipEnable == true
DX::ThrowIfFailed(
    pD3DDevice->CreateRasterizerState(
        &drawingRenderStateDesc,
        &m_drawingRenderState
        )
    );
```

<span data-ttu-id="09f23-141">Erstellen Sie einen Renderstatus, den Sie zum Aktivieren von Backface-Culling verwenden können.</span><span class="sxs-lookup"><span data-stu-id="09f23-141">Create a render state you can use to enable back face culling.</span></span> <span data-ttu-id="09f23-142">Falls Ihr Rendercode Backface-Culling bereits aktiviert, können Sie diesen Schritt überspringen.</span><span class="sxs-lookup"><span data-stu-id="09f23-142">If your rendering code already turns on back face culling, then you can skip this step.</span></span>

```cpp
D3D11_RASTERIZER_DESC shadowRenderStateDesc;
ZeroMemory(&shadowRenderStateDesc, sizeof(D3D11_RASTERIZER_DESC));
shadowRenderStateDesc.CullMode = D3D11_CULL_FRONT;
shadowRenderStateDesc.FillMode = D3D11_FILL_SOLID;
shadowRenderStateDesc.DepthClipEnable = true;

DX::ThrowIfFailed(
    pD3DDevice->CreateRasterizerState(
        &shadowRenderStateDesc,
        &m_shadowRenderState
        )
    );
```

## <a name="create-constant-buffers"></a><span data-ttu-id="09f23-143">Erstellen von Konstantenpuffern</span><span class="sxs-lookup"><span data-stu-id="09f23-143">Create constant buffers</span></span>


<span data-ttu-id="09f23-144">Denken Sie daran, einen Konstantenpuffer für das Rendering aus der Perspektive der Beleuchtung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="09f23-144">Don't forget to create a constant buffer for rendering from the light's point of view.</span></span> <span data-ttu-id="09f23-145">Mit diesem Konstantenpuffer können Sie die Beleuchtungsposition für den Shader angeben.</span><span class="sxs-lookup"><span data-stu-id="09f23-145">You can also use this constant buffer to specify the light position to the shader.</span></span> <span data-ttu-id="09f23-146">Verwenden Sie für punktuelles Licht eine perspektivische Matrix und für gerichtetes Licht (z.B. Sonnenlicht) eine orthogonale Matrix.</span><span class="sxs-lookup"><span data-stu-id="09f23-146">Use a perspective matrix for point lights, and use an orthogonal matrix for directional lights (such as sunlight).</span></span>

```cpp
DX::ThrowIfFailed(
    m_deviceResources->GetD3DDevice()->CreateBuffer(
        &viewProjectionConstantBufferDesc,
        nullptr,
        &m_lightViewProjectionBuffer
        )
    );
```

<span data-ttu-id="09f23-147">Füllen Sie den Konstantenpuffer mit Daten.</span><span class="sxs-lookup"><span data-stu-id="09f23-147">Fill the constant buffer data.</span></span> <span data-ttu-id="09f23-148">Aktualisieren Sie den Konstantenpuffer einmal während der Initialisierung und dann noch einmal, wenn sich die Lichtwerte seit dem vorherigen Frame geändert haben.</span><span class="sxs-lookup"><span data-stu-id="09f23-148">Update the constant buffers once during initialization, and again if the light values have changed since the previous frame.</span></span>

```cpp
{
    XMMATRIX lightPerspectiveMatrix = XMMatrixPerspectiveFovRH(
        XM_PIDIV2,
        1.0f,
        12.f,
        50.f
        );

    XMStoreFloat4x4(
        &m_lightViewProjectionBufferData.projection,
        XMMatrixTranspose(lightPerspectiveMatrix)
        );

    // Point light at (20, 15, 20), pointed at the origin. POV up-vector is along the y-axis.
    static const XMVECTORF32 eye = { 20.0f, 15.0f, 20.0f, 0.0f };
    static const XMVECTORF32 at = { 0.0f, 0.0f, 0.0f, 0.0f };
    static const XMVECTORF32 up = { 0.0f, 1.0f, 0.0f, 0.0f };

    XMStoreFloat4x4(
        &m_lightViewProjectionBufferData.view,
        XMMatrixTranspose(XMMatrixLookAtRH(eye, at, up))
        );

    // Store the light position to help calculate the shadow offset.
    XMStoreFloat4(&m_lightViewProjectionBufferData.pos, eye);
}
```

```cpp
context->UpdateSubresource(
    m_lightViewProjectionBuffer.Get(),
    0,
    NULL,
    &m_lightViewProjectionBufferData,
    0,
    0
    );
```

## <a name="create-a-viewport"></a><span data-ttu-id="09f23-149">Erstellen eines Viewports</span><span class="sxs-lookup"><span data-stu-id="09f23-149">Create a viewport</span></span>


<span data-ttu-id="09f23-150">Sie benötigen einen separaten Viewport zum Rendern der Schattenkarte.</span><span class="sxs-lookup"><span data-stu-id="09f23-150">You need a separate viewport to render to the shadow map.</span></span> <span data-ttu-id="09f23-151">Der Viewport ist keine geräteabhängige Ressource. Sie können ihn auch an einer anderen Stelle im Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="09f23-151">The viewport isn't a device-based resource; you're free to create it elsewhere in your code.</span></span> <span data-ttu-id="09f23-152">Wenn Sie den Viewport zusammen mit der Schattenkarte erstellen, ist es einfacher, die Dimensionen von Viewport und Schattenkarte deckungsgleich zu halten.</span><span class="sxs-lookup"><span data-stu-id="09f23-152">Creating the viewport along with the shadow map can help make it more convenient to keep the dimension of the viewport congruent with the shadow map dimension.</span></span>

```cpp
// Init viewport for shadow rendering
ZeroMemory(&m_shadowViewport, sizeof(D3D11_VIEWPORT));
m_shadowViewport.Height = m_shadowMapDimension;
m_shadowViewport.Width = m_shadowMapDimension;
m_shadowViewport.MinDepth = 0.f;
m_shadowViewport.MaxDepth = 1.f;
```

<span data-ttu-id="09f23-153">Im nächsten Teil dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die Schattenkarte durch [Rendern in den Tiefenpuffer](render-the-shadow-map-to-the-depth-buffer.md) erstellen.</span><span class="sxs-lookup"><span data-stu-id="09f23-153">In the next part of this walkthrough, learn how to create the shadow map by [rendering to the depth buffer](render-the-shadow-map-to-the-depth-buffer.md).</span></span>

 

 




