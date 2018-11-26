---
title: Rendern der Schattenmap zum Tiefenpuffer
description: Führen Sie das Rendern aus dem Blickwinkel durch, aus dem das Licht kommt, um eine zweidimensionale Tiefenkarte zu erstellen, mit der das Schattenvolumen dargestellt wird.
ms.assetid: 7f3d0208-c379-8871-cc48-027047c6c2d0
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Rendern, Schattenkarte, Tiefenpuffer, Direct3D
ms.localizationpriority: medium
ms.openlocfilehash: 27cd535dc51a330937c345acf352677a42c652eb
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7692268"
---
# <a name="render-the-shadow-map-to-the-depth-buffer"></a><span data-ttu-id="a809f-104">Rendern der Schattenmap zum Tiefenpuffer</span><span class="sxs-lookup"><span data-stu-id="a809f-104">Render the shadow map to the depth buffer</span></span>




<span data-ttu-id="a809f-105">Führen Sie das Rendern aus dem Blickwinkel durch, aus dem das Licht kommt, um eine zweidimensionale Tiefenkarte zu erstellen, mit der das Schattenvolumen dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="a809f-105">Render from the point of view of the light to create a two-dimensional depth map representing the shadow volume.</span></span> <span data-ttu-id="a809f-106">Mithilfe der Tiefenmap wird eine Maske für den Raum erstellt, der im Schatten gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="a809f-106">The depth map masks the space that will be rendered in shadow.</span></span> <span data-ttu-id="a809f-107">Teil2 von [Exemplarische Vorgehensweise: Implementieren von Schattenvolumes mithilfe von Tiefenpuffern in Direct3D11](implementing-depth-buffers-for-shadow-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="a809f-107">Part 2 of [Walkthrough: Implement shadow volumes using depth buffers in Direct3D 11](implementing-depth-buffers-for-shadow-mapping.md).</span></span>

## <a name="clear-the-depth-buffer"></a><span data-ttu-id="a809f-108">Löschen des Tiefenpuffers</span><span class="sxs-lookup"><span data-stu-id="a809f-108">Clear the depth buffer</span></span>


<span data-ttu-id="a809f-109">Löschen Sie den Tiefenpuffer stets, bevor Sie in den Puffer rendern.</span><span class="sxs-lookup"><span data-stu-id="a809f-109">Always clear the depth buffer before rendering to it.</span></span>

```cpp
context->ClearRenderTargetView(m_deviceResources->GetBackBufferRenderTargetView(), DirectX::Colors::CornflowerBlue);
context->ClearDepthStencilView(m_shadowDepthView.Get(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

## <a name="render-the-shadow-map-to-the-depth-buffer"></a><span data-ttu-id="a809f-110">Rendern der Schattenmap zum Tiefenpuffer</span><span class="sxs-lookup"><span data-stu-id="a809f-110">Render the shadow map to the depth buffer</span></span>


<span data-ttu-id="a809f-111">Geben Sie für den Schattenrenderdurchlauf einen Tiefenpuffer an, aber geben Sie kein Renderziel an.</span><span class="sxs-lookup"><span data-stu-id="a809f-111">For the shadow rendering pass, specify a depth buffer but do not specify a render target.</span></span>

<span data-ttu-id="a809f-112">Geben Sie den Viewport für das Licht und einen Vertex-Shader an, und legen Sie die Konstantenpuffer für den Lichtraum fest.</span><span class="sxs-lookup"><span data-stu-id="a809f-112">Specify the light viewport, a vertex shader, and set the light space constant buffers.</span></span> <span data-ttu-id="a809f-113">Verwenden Sie für diesen Durchlauf das Vorderseiten-Culling, um die in den Schattenpuffer eingefügten Tiefenwerte zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="a809f-113">Use front face culling for this pass to optimize the depth values placed in the shadow buffer.</span></span>

<span data-ttu-id="a809f-114">Beachten Sie, dass Sie auf den meisten Geräten "nullptr" für den Pixelshader angeben können (oder die Angabe eines Pixelshaders ganz weglassen können).</span><span class="sxs-lookup"><span data-stu-id="a809f-114">Note that on most devices, you can specify nullptr for the pixel shader (or skip specifying a pixel shader entirely).</span></span> <span data-ttu-id="a809f-115">Für einige Treiber wird jedoch möglicherweise eine Ausnahme ausgelöst, wenn Sie auf dem Direct3D-Gerät einen Draw-Aufruf durchführen, während ein Null-Pixelshader festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a809f-115">But some drivers may throw an exception when you call draw on the Direct3D device with a null pixel shader set.</span></span> <span data-ttu-id="a809f-116">Sie können einen minimalen Pixel-Shader für den Schattenrenderdurchlauf festlegen, um diese Ausnahme zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="a809f-116">To avoid this exception, you can set a minimal pixel shader for the shadow rendering pass.</span></span> <span data-ttu-id="a809f-117">Die Ausgabe dieses Shaders wird nicht aufbewahrt. Für jedes Pixel kann [**discard**](https://msdn.microsoft.com/library/windows/desktop/bb943995) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a809f-117">The output of this shader is thrown away; it can call [**discard**](https://msdn.microsoft.com/library/windows/desktop/bb943995) on every pixel.</span></span>

<span data-ttu-id="a809f-118">Rendern Sie die Objekte, die Schatten werfen können. Um Geometrieelemente, die keinen Schatten werfen können, brauchen Sie sich jedoch nicht zu kümmern (z. B. ein Boden in einem Raum oder Objekte, die zum Zweck der Optimierung aus dem Schattendurchlauf entfernt werden).</span><span class="sxs-lookup"><span data-stu-id="a809f-118">Render the objects that can cast shadows, but don't bother rendering geometry that can't cast a shadow (like a floor in a room, or objects removed from the shadow pass for optimization reasons).</span></span>

```cpp
void ShadowSceneRenderer::RenderShadowMap()
{
    auto context = m_deviceResources->GetD3DDeviceContext();

    // Render all the objects in the scene that can cast shadows onto themselves or onto other objects.

    // Only bind the ID3D11DepthStencilView for output.
    context->OMSetRenderTargets(
        0,
        nullptr,
        m_shadowDepthView.Get()
        );

    // Note that starting with the second frame, the previous call will display
    // warnings in VS debug output about forcing an unbind of the pixel shader
    // resource. This warning can be safely ignored when using shadow buffers
    // as demonstrated in this sample.

    // Set rendering state.
    context->RSSetState(m_shadowRenderState.Get());
    context->RSSetViewports(1, &m_shadowViewport);

    // Each vertex is one instance of the VertexPositionTexNormColor struct.
    UINT stride = sizeof(VertexPositionTexNormColor);
    UINT offset = 0;
    context->IASetVertexBuffers(
        0,
        1,
        m_vertexBuffer.GetAddressOf(),
        &stride,
        &offset
        );

    context->IASetIndexBuffer(
        m_indexBuffer.Get(),
        DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
        0
        );

    context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
    context->IASetInputLayout(m_inputLayout.Get());

    // Attach our vertex shader.
    context->VSSetShader(
        m_simpleVertexShader.Get(),
        nullptr,
        0
        );

    // Send the constant buffers to the Graphics device.
    context->VSSetConstantBuffers(
        0,
        1,
        m_lightViewProjectionBuffer.GetAddressOf()
        );

    context->VSSetConstantBuffers(
        1,
        1,
        m_rotatedModelBuffer.GetAddressOf()
        );

    // In some configurations, it's possible to avoid setting a pixel shader
    // (or set PS to nullptr). Not all drivers are tolerant of this, so to be
    // safe set a minimal shader here.
    //
    // Direct3D will discard output from this shader because the render target
    // view is unbound.
    context->PSSetShader(
        m_textureShader.Get(),
        nullptr,
        0
        );

    // Draw the objects.
    context->DrawIndexed(
        m_indexCountCube,
        0,
        0
        );
}
```

<span data-ttu-id="a809f-119">**Optimieren des Ansichts-Frustums:**  Stellen Sie sicher, dass in Ihrer Implementierung ein exaktes Ansichts-Frustum berechnet wird, damit Sie mit dem Tiefenpuffer die größtmögliche Präzision erzielen.</span><span class="sxs-lookup"><span data-stu-id="a809f-119">**Optimize the view frustum:**  Make sure your implementation computes a tight view frustum so that you get the most precision out of your depth buffer.</span></span> <span data-ttu-id="a809f-120">Weitere Tipps zu Schattenmethoden finden Sie unter [Häufig verwendete Methoden zur Verbesserung von Tiefenmaps für Schatten](https://msdn.microsoft.com/library/windows/desktop/ee416324).</span><span class="sxs-lookup"><span data-stu-id="a809f-120">See [Common Techniques to Improve Shadow Depth Maps](https://msdn.microsoft.com/library/windows/desktop/ee416324) for more tips on shadow technique.</span></span>

## <a name="vertex-shader-for-shadow-pass"></a><span data-ttu-id="a809f-121">Vertex-Shader für Schattendurchlauf</span><span class="sxs-lookup"><span data-stu-id="a809f-121">Vertex shader for shadow pass</span></span>


<span data-ttu-id="a809f-122">Verwenden Sie eine vereinfachte Version Ihres Vertex-Shaders, um nur die Vertexposition im Lichtraum zu rendern.</span><span class="sxs-lookup"><span data-stu-id="a809f-122">Use a simplified version of your vertex shader to render just the vertex position in light space.</span></span> <span data-ttu-id="a809f-123">Beziehen Sie keine Beleuchtungsnormalen, sekundären Transformationen usw. ein.</span><span class="sxs-lookup"><span data-stu-id="a809f-123">Don't include any lighting normals, secondary transformations, and so on.</span></span>

```cpp
PixelShaderInput main(VertexShaderInput input)
{
    PixelShaderInput output;
    float4 pos = float4(input.pos, 1.0f);

    // Transform the vertex position into projected space.
    pos = mul(pos, model);
    pos = mul(pos, view);
    pos = mul(pos, projection);
    output.pos = pos;

    return output;
}
```

<span data-ttu-id="a809f-124">Im nächsten Teil dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie Schatten hinzufügen, indem Sie [mithilfe des Tiefentests rendern](render-the-scene-with-depth-testing.md).</span><span class="sxs-lookup"><span data-stu-id="a809f-124">In the next part of this walkthrough, learn how to add shadows by [rendering with depth testing](render-the-scene-with-depth-testing.md).</span></span>

 

 




