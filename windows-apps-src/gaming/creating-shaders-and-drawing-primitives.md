---
title: Erstellen von Shadern und Zeichnen von Grundtypen
description: Im Folgenden wird das Kompilieren und Erstellen von Shadern mit HLSL-Quelldateien veranschaulicht, die zum Zeichnen von Grundtypen auf dem Bildschirm verwendet werden.
ms.assetid: 91113bbe-96c9-4ef9-6482-39f1ff1a70f4
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Shader, Grundtypen, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: 5173adc26e0730ccb80f93fe0c12af286b0c1a49
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8923470"
---
# <a name="create-shaders-and-drawing-primitives"></a><span data-ttu-id="3774c-104">Erstellen von Shadern und Zeichnen von Grundtypen</span><span class="sxs-lookup"><span data-stu-id="3774c-104">Create shaders and drawing primitives</span></span>



<span data-ttu-id="3774c-105">Im Folgenden wird das Kompilieren und Erstellen von Shadern mit HLSL-Quelldateien veranschaulicht, die zum Zeichnen von Grundtypen auf dem Bildschirm verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3774c-105">Here, we show you how to use HLSL source files to compile and create shaders that you can then use to draw primitives on the display.</span></span>

<span data-ttu-id="3774c-106">Ein gelbes Dreieck wird mit Vertex- und Pixelshadern erstellt.</span><span class="sxs-lookup"><span data-stu-id="3774c-106">We create and draw a yellow triangle by using vertex and pixel shaders.</span></span> <span data-ttu-id="3774c-107">Nach dem Erstellen des Direct3D-Geräts, der Swapchain und der Renderingzielansicht werden Daten aus Binärshaderobjektdateien auf dem Datenträger gelesen.</span><span class="sxs-lookup"><span data-stu-id="3774c-107">After we create the Direct3D device, the swap chain, and the render-target view, we read data from binary shader object files on the disk.</span></span>

<span data-ttu-id="3774c-108">**Ziel:** Shader erstellen und Grundtypen zeichnen.</span><span class="sxs-lookup"><span data-stu-id="3774c-108">**Objective:** To create shaders and to draw primitives.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3774c-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3774c-109">Prerequisites</span></span>


<span data-ttu-id="3774c-110">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="3774c-110">We assume that you are familiar with C++.</span></span> <span data-ttu-id="3774c-111">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="3774c-111">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="3774c-112">Ferner wird davon ausgegangen, dass Sie sich mit dem Dokument [Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen eines Bilds](setting-up-directx-resources.md) vertraut gemacht haben.</span><span class="sxs-lookup"><span data-stu-id="3774c-112">We also assume that you went through [Quickstart: setting up DirectX resources and displaying an image](setting-up-directx-resources.md).</span></span>

<span data-ttu-id="3774c-113">**Zeitaufwand:** 20Minuten.</span><span class="sxs-lookup"><span data-stu-id="3774c-113">**Time to complete:** 20 minutes.</span></span>

## <a name="instructions"></a><span data-ttu-id="3774c-114">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3774c-114">Instructions</span></span>

### <a name="1-compiling-hlsl-source-files"></a><span data-ttu-id="3774c-115">1. Kompilieren von HLSL-Quelldateien</span><span class="sxs-lookup"><span data-stu-id="3774c-115">1. Compiling HLSL source files</span></span>

<span data-ttu-id="3774c-116">Microsoft Visual Studio verwendet den HLSL-Codecompiler [fxc.exe](https://msdn.microsoft.com/library/windows/desktop/bb232919), um die HLSL-Quelldateien („SimpleVertexShader.hlsl“ und „SimplePixelShader.hlsl“) in CSO-Binärshaderobjektdateien („SimpleVertexShader.cso“ und „SimplePixelShader.cso“) zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="3774c-116">Microsoft Visual Studio uses the [fxc.exe](https://msdn.microsoft.com/library/windows/desktop/bb232919) HLSL code compiler to compile the .hlsl source files (SimpleVertexShader.hlsl and SimplePixelShader.hlsl) into .cso binary shader object files (SimpleVertexShader.cso and SimplePixelShader.cso).</span></span> <span data-ttu-id="3774c-117">Weitere Infos über den HLSL-Codecompiler finden Sie im Effektcompiler-Tool.</span><span class="sxs-lookup"><span data-stu-id="3774c-117">For more info about the HLSL code compiler, see Effect-Compiler Tool.</span></span> <span data-ttu-id="3774c-118">Weitere Infos über das Kompilieren von Shadercode finden unter [Kompilieren von Shadern](https://msdn.microsoft.com/library/windows/desktop/bb509633).</span><span class="sxs-lookup"><span data-stu-id="3774c-118">For more info about compiling shader code, see [Compiling Shaders](https://msdn.microsoft.com/library/windows/desktop/bb509633).</span></span>

<span data-ttu-id="3774c-119">Nachfolgend finden Sie den Code in der Datei „SimpleVertexShader.hlsl“:</span><span class="sxs-lookup"><span data-stu-id="3774c-119">Here is the code in SimpleVertexShader.hlsl:</span></span>

```hlsl
struct VertexShaderInput
{
    DirectX::XMFLOAT2 pos : POSITION;
};

struct PixelShaderInput
{
    float4 pos : SV_POSITION;
};

PixelShaderInput SimpleVertexShader(VertexShaderInput input)
{
    PixelShaderInput vertexShaderOutput;

    // For this lesson, set the vertex depth value to 0.5, so it is guaranteed to be drawn.
    vertexShaderOutput.pos = float4(input.pos, 0.5f, 1.0f);

    return vertexShaderOutput;
}
```

<span data-ttu-id="3774c-120">Nachfolgend finden Sie den Code in der Datei „SimplePixelShader.hlsl“:</span><span class="sxs-lookup"><span data-stu-id="3774c-120">Here is the code in SimplePixelShader.hlsl:</span></span>

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
};

float4 SimplePixelShader(PixelShaderInput input) : SV_TARGET
{
    // Draw the entire triangle yellow.
    return float4(1.0f, 1.0f, 0.0f, 1.0f);
}
```

### <a name="2-reading-data-from-disk"></a><span data-ttu-id="3774c-121">2. Lesen von Daten von einem Datenträger</span><span class="sxs-lookup"><span data-stu-id="3774c-121">2. Reading data from disk</span></span>

<span data-ttu-id="3774c-122">Hier wird die DX::ReadDataAsync-Funktion aus „DirectXHelper.h“ in der DirectX11-App-Vorlage (Universal Windows) verwendet, um asynchron Daten aus einer Datei auf dem Datenträger zu lesen.</span><span class="sxs-lookup"><span data-stu-id="3774c-122">We use the DX::ReadDataAsync function from DirectXHelper.h in the DirectX 11 App (Universal Windows) template to asynchronously read data from a file on the disk.</span></span>

### <a name="3-creating-vertex-and-pixel-shaders"></a><span data-ttu-id="3774c-123">3. Erstellen von Vertex- und Pixelshadern</span><span class="sxs-lookup"><span data-stu-id="3774c-123">3. Creating vertex and pixel shaders</span></span>

<span data-ttu-id="3774c-124">Zunächst werden Daten aus der Datei „SimpleVertexShader.cso“ gelesen. Anschließend werden die Daten dem Bytearray *vertexShaderBytecode* zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="3774c-124">We read data from the SimpleVertexShader.cso file and assign the data to the *vertexShaderBytecode* byte array.</span></span> <span data-ttu-id="3774c-125">[**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524) wird mit dem Bytearray aufgerufen, um den Vertexshader ([**ID3D11VertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476641)) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3774c-125">We call [**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524) with the byte array to create the vertex shader ([**ID3D11VertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476641)).</span></span> <span data-ttu-id="3774c-126">Die Vertextiefe wird in der Quelldatei „SimpleVertexShader.hlsl“ auf den Wert 0,5 festgelegt, um zu garantieren, dass das Dreieck gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="3774c-126">We set the vertex depth value to 0.5 in the SimpleVertexShader.hlsl source to guarantee that our triangle is drawn.</span></span> <span data-ttu-id="3774c-127">Ein Array von [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180)-Strukturen wird gefüllt, um das Layout des Vertexshadercodes zu beschreiben. Im Anschluss wird [**ID3D11Device::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512) aufgerufen, um das Layout zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3774c-127">We populate an array of [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180) structures to describe the layout of the vertex shader code and then call [**ID3D11Device::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512) to create the layout.</span></span> <span data-ttu-id="3774c-128">Das Array verfügt über ein Layoutelement, das die Vertexposition definiert.</span><span class="sxs-lookup"><span data-stu-id="3774c-128">The array has one layout element that defines the vertex position.</span></span> <span data-ttu-id="3774c-129">Zunächst werden Daten aus der Datei „SimplePixelShader.cso“ gelesen. Anschließend werden die Daten dem Bytearray *pixelShaderBytecode* zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="3774c-129">We read data from the SimplePixelShader.cso file and assign the data to the *pixelShaderBytecode* byte array.</span></span> <span data-ttu-id="3774c-130">[**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513) wird mit dem Bytearray aufgerufen, um den Pixelshader ([**ID3D11PixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476576)) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3774c-130">We call [**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513) with the byte array to create the pixel shader ([**ID3D11PixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476576)).</span></span> <span data-ttu-id="3774c-131">Der Pixelwert wird in der Quelldatei „SimplePixelShader.hlsl“ auf (1,1,1,1) festgelegt, damit das Dreieck gelb wird.</span><span class="sxs-lookup"><span data-stu-id="3774c-131">We set the pixel value to (1,1,1,1) in the SimplePixelShader.hlsl source to make our triangle yellow.</span></span> <span data-ttu-id="3774c-132">Wenn Sie die Farbe ändern möchten, können Sie diesen Wert ändern.</span><span class="sxs-lookup"><span data-stu-id="3774c-132">You can change the color by changing this value.</span></span>

<span data-ttu-id="3774c-133">Vertex- und Indexpuffer werden erstellt, um ein einfaches Dreieck zu definieren.</span><span class="sxs-lookup"><span data-stu-id="3774c-133">We create vertex and index buffers that define a simple triangle.</span></span> <span data-ttu-id="3774c-134">Zu diesem Zweck wird zunächst das Dreieck definiert. Anschließend werden die Vertex- und Indexpuffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) und [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)) mithilfe der Dreieckdefinition beschrieben, bevor dann [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) einmal für jeden Puffer aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="3774c-134">To do this, we first define the triangle, next describe the vertex and index buffers ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) and [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)) using the triangle definition, and finally call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) once for each buffer.</span></span>

```cpp
        auto loadVSTask = DX::ReadDataAsync(L"SimpleVertexShader.cso");
        auto loadPSTask = DX::ReadDataAsync(L"SimplePixelShader.cso");
        
        // Load the raw vertex shader bytecode from disk and create a vertex shader with it.
        auto createVSTask = loadVSTask.then([this](const std::vector<byte>& vertexShaderBytecode) {


          ComPtr<ID3D11VertexShader> vertexShader;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateVertexShader(
                  vertexShaderBytecode->Data,
                  vertexShaderBytecode->Length,
                  nullptr,
                  &vertexShader
                  )
              );

          // Create an input layout that matches the layout defined in the vertex shader code.
          // For this lesson, this is simply a DirectX::XMFLOAT2 vector defining the vertex position.
          const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
          {
              { "POSITION", 0, DXGI_FORMAT_R32G32_FLOAT, 0, 0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
          };

          ComPtr<ID3D11InputLayout> inputLayout;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateInputLayout(
                  basicVertexLayoutDesc,
                  ARRAYSIZE(basicVertexLayoutDesc),
                  vertexShaderBytecode->Data,
                  vertexShaderBytecode->Length,
                  &inputLayout
                  )
              );
        });
        
        // Load the raw pixel shader bytecode from disk and create a pixel shader with it.
        auto createPSTask = loadPSTask.then([this](const std::vector<byte>& pixelShaderBytecode) {
          ComPtr<ID3D11PixelShader> pixelShader;
          DX::ThrowIfFailed(
              m_d3dDevice->CreatePixelShader(
                  pixelShaderBytecode->Data,
                  pixelShaderBytecode->Length,
                  nullptr,
                  &pixelShader
                  )
              );
        });

        // Create vertex and index buffers that define a simple triangle.
        auto createTriangleTask = (createPSTask && createVSTask).then([this] () {

          DirectX::XMFLOAT2 triangleVertices[] =
          {
              float2(-0.5f, -0.5f),
              float2( 0.0f,  0.5f),
              float2( 0.5f, -0.5f),
          };

          unsigned short triangleIndices[] =
          {
              0, 1, 2,
          };

          D3D11_BUFFER_DESC vertexBufferDesc = {0};
          vertexBufferDesc.ByteWidth = sizeof(float2) * ARRAYSIZE(triangleVertices);
          vertexBufferDesc.Usage = D3D11_USAGE_DEFAULT;
          vertexBufferDesc.BindFlags = D3D11_BIND_VERTEX_BUFFER;
          vertexBufferDesc.CPUAccessFlags = 0;
          vertexBufferDesc.MiscFlags = 0;
          vertexBufferDesc.StructureByteStride = 0;

          D3D11_SUBRESOURCE_DATA vertexBufferData;
          vertexBufferData.pSysMem = triangleVertices;
          vertexBufferData.SysMemPitch = 0;
          vertexBufferData.SysMemSlicePitch = 0;

          ComPtr<ID3D11Buffer> vertexBuffer;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateBuffer(
                  &vertexBufferDesc,
                  &vertexBufferData,
                  &vertexBuffer
                  )
              );

          D3D11_BUFFER_DESC indexBufferDesc;
          indexBufferDesc.ByteWidth = sizeof(unsigned short) * ARRAYSIZE(triangleIndices);
          indexBufferDesc.Usage = D3D11_USAGE_DEFAULT;
          indexBufferDesc.BindFlags = D3D11_BIND_INDEX_BUFFER;
          indexBufferDesc.CPUAccessFlags = 0;
          indexBufferDesc.MiscFlags = 0;
          indexBufferDesc.StructureByteStride = 0;

          D3D11_SUBRESOURCE_DATA indexBufferData;
          indexBufferData.pSysMem = triangleIndices;
          indexBufferData.SysMemPitch = 0;
          indexBufferData.SysMemSlicePitch = 0;

          ComPtr<ID3D11Buffer> indexBuffer;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateBuffer(
                  &indexBufferDesc,
                  &indexBufferData,
                  &indexBuffer
                  )
              );
        });
```

<span data-ttu-id="3774c-135">Mithilfe der Vertex- und Pixelshader, des Vertexshaderlayouts sowie der Vertex- und Indexpuffer wird dann ein gelbes Dreieck gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3774c-135">We use the vertex and pixel shaders, the vertex shader layout, and the vertex and index buffers to draw a yellow triangle.</span></span>

### <a name="4-drawing-the-triangle-and-presenting-the-rendered-image"></a><span data-ttu-id="3774c-136">4. Zeichnen des Dreiecks und Darstellen des gerenderten Bilds</span><span class="sxs-lookup"><span data-stu-id="3774c-136">4. Drawing the triangle and presenting the rendered image</span></span>

<span data-ttu-id="3774c-137">Wir geben eine endlose Schleife zum fortlaufenden Rendern und Anzeigen der Szene ein.</span><span class="sxs-lookup"><span data-stu-id="3774c-137">We enter an endless loop to continually render and display the scene.</span></span> <span data-ttu-id="3774c-138">Wir rufen [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) auf, um das Renderziel als Ausgabeziel anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3774c-138">We call [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) to specify the render target as the output target.</span></span> <span data-ttu-id="3774c-139">[**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) wird mit dem Wert „{ 0.071f, 0.04f, 0.561f, 1.0f }“ aufgerufen, um das Renderingziel durchgehend blau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3774c-139">We call [**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) with { 0.071f, 0.04f, 0.561f, 1.0f } to clear the render target to a solid blue color.</span></span>

<span data-ttu-id="3774c-140">In der Endlosschleife wird ein gelbes Dreieck auf der blauen Oberfläche gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3774c-140">In the endless loop, we draw a yellow triangle on the blue surface.</span></span>

**<span data-ttu-id="3774c-141">So zeichnen Sie ein gelbes Dreieck</span><span class="sxs-lookup"><span data-stu-id="3774c-141">To draw a yellow triangle</span></span>**

1.  <span data-ttu-id="3774c-142">Wir rufen zunächst [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) auf, um das Streamen der Vertexpufferdaten in die Eingabeassemblerphase zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="3774c-142">First, we call [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) to describe how vertex buffer data is streamed into the input-assembler stage.</span></span>
2.  <span data-ttu-id="3774c-143">Als Nächstes rufen wir [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) und [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) auf, um die Vertex- und Indexpuffer an den Eingabeassemblerzustand zu binden.</span><span class="sxs-lookup"><span data-stu-id="3774c-143">Next, we call [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) and [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) to bind the vertex and index buffers to the input-assembler stage.</span></span>
3.  <span data-ttu-id="3774c-144">Nun rufen wir [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) mit dem [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP)-Wert auf, um für den Eingabeassemblerzustand anzugeben, dass die Vertexdaten als Dreieckskette interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="3774c-144">Next, we call [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) with the [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP) value to specify for the input-assembler stage to interpret the vertex data as a triangle strip.</span></span>
4.  <span data-ttu-id="3774c-145">Im nächsten Schritt rufen wir [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) auf, um die Vertexshaderphase mit dem Vertexshadercode zu initialisieren. Zudem rufen wir [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) auf, um die Pixelshaderphase mit dem Pixelshadercode zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="3774c-145">Next, we call [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) to initialize the vertex shader stage with the vertex shader code and [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) to initialize the pixel shader stage with the pixel shader code.</span></span>
5.  <span data-ttu-id="3774c-146">Abschließend wird [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) aufgerufen, um das Dreieck zu zeichnen und an die Renderingpipeline zu senden.</span><span class="sxs-lookup"><span data-stu-id="3774c-146">Finally, we call [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) to draw the triangle and submit it to the rendering pipeline.</span></span>

<span data-ttu-id="3774c-147">Wir rufen [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) auf, um das gerenderte Bild im Fenster darzustellen.</span><span class="sxs-lookup"><span data-stu-id="3774c-147">We call [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) to present the rendered image to the window.</span></span>

```cpp
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

            m_d3dDeviceContext->IASetInputLayout(inputLayout.Get());

            // Set the vertex and index buffers, and specify the way they define geometry.
            UINT stride = sizeof(float2);
            UINT offset = 0;
            m_d3dDeviceContext->IASetVertexBuffers(
                0,
                1,
                vertexBuffer.GetAddressOf(),
                &stride,
                &offset
                );

            m_d3dDeviceContext->IASetIndexBuffer(
                indexBuffer.Get(),
                DXGI_FORMAT_R16_UINT,
                0
                );

            m_d3dDeviceContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);

            // Set the vertex and pixel shader stage state.
            m_d3dDeviceContext->VSSetShader(
                vertexShader.Get(),
                nullptr,
                0
                );

            m_d3dDeviceContext->PSSetShader(
                pixelShader.Get(),
                nullptr,
                0
                );

            // Draw the cube.
            m_d3dDeviceContext->DrawIndexed(
                ARRAYSIZE(triangleIndices),
                0,
                0
                );

            // Present the rendered image to the window.  Because the maximum frame latency is set to 1,
            // the render loop will generally be throttled to the screen refresh rate, typically around
            // 60 Hz, by sleeping the application on Present until the screen is refreshed.
            DX::ThrowIfFailed(
                m_swapChain->Present(1, 0)
                );
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="3774c-148">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3774c-148">Summary and next steps</span></span>


<span data-ttu-id="3774c-149">In diesem Thema wurde ein gelbes Dreieck mit Vertex- und Pixelshadern erstellt und gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3774c-149">We created and drew a yellow triangle by using vertex and pixel shaders.</span></span>

<span data-ttu-id="3774c-150">Als Nächstes wird ein kreisender 3D-Würfel erstellt, und Lichteffekte werden auf den Würfel angewendet.</span><span class="sxs-lookup"><span data-stu-id="3774c-150">Next, we create an orbiting 3D cube and apply lighting effects to it.</span></span>

[<span data-ttu-id="3774c-151">Verwenden von Tiefe und Effekten auf Grundtypen</span><span class="sxs-lookup"><span data-stu-id="3774c-151">Using depth and effects on primitives</span></span>](using-depth-and-effects-on-primitives.md)

 

 




