---
author: mtoepke
title: Verwenden von Tiefen und Effekten in Primitiven
description: Hier zeigen wir Ihnen die Verwendung von Tiefen, Perspektiven, Farben und anderen Effekten in Grundtypen.
ms.assetid: 71ef34c5-b4a3-adae-5266-f86ba257482a
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Tiefe, Effekte, Grundtypen; directx
ms.localizationpriority: medium
ms.openlocfilehash: f81c441910cd0d0205641a119c243cb22d0b695e
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5569463"
---
# <a name="use-depth-and-effects-on-primitives"></a><span data-ttu-id="63c88-104">Verwenden von Tiefen und Effekten in Grundtypen</span><span class="sxs-lookup"><span data-stu-id="63c88-104">Use depth and effects on primitives</span></span>



<span data-ttu-id="63c88-105">Hier zeigen wir Ihnen die Verwendung von Tiefen, Perspektiven, Farben und anderen Effekten in Primitiven.</span><span class="sxs-lookup"><span data-stu-id="63c88-105">Here, we show you how to use depth, perspective, color, and other effects on primitives.</span></span>

<span data-ttu-id="63c88-106">**Ziel:** Ein 3D-Objekt zu erstellen und einfache Vertexbeleuchtung und -färbung darauf anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="63c88-106">**Objective:** To create a 3D object and apply basic vertex lighting and coloring to it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63c88-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="63c88-107">Prerequisites</span></span>


<span data-ttu-id="63c88-108">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="63c88-108">We assume that you are familiar with C++.</span></span> <span data-ttu-id="63c88-109">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="63c88-109">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="63c88-110">Des Weiteren gehen wir davon aus, dass Sie die Themen [Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen von Bildern](setting-up-directx-resources.md) sowie [Erstellen von Shadern und Zeichnen von Primitiven](creating-shaders-and-drawing-primitives.md) bearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="63c88-110">We also assume that you went through [Quickstart: setting up DirectX resources and displaying an image](setting-up-directx-resources.md) and [Creating shaders and drawing primitives](creating-shaders-and-drawing-primitives.md).</span></span>

<span data-ttu-id="63c88-111">**Zeitaufwand:** 20Minuten.</span><span class="sxs-lookup"><span data-stu-id="63c88-111">**Time to complete:** 20 minutes.</span></span>

<a name="instructions"></a><span data-ttu-id="63c88-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="63c88-112">Instructions</span></span>
------------

### <a name="1-defining-cube-variables"></a><span data-ttu-id="63c88-113">1. Definieren von Würfelvariablen</span><span class="sxs-lookup"><span data-stu-id="63c88-113">1. Defining cube variables</span></span>

<span data-ttu-id="63c88-114">Zunächst müssen wir die **SimpleCubeVertex**-Struktur und die **ConstantBuffer**-Struktur für den Würfel definieren.</span><span class="sxs-lookup"><span data-stu-id="63c88-114">First, we need to define the **SimpleCubeVertex** and **ConstantBuffer** structures for the cube.</span></span> <span data-ttu-id="63c88-115">In diesen Strukturen werden die Vertexpositionen und -farben für den Würfel sowie die Darstellung des Würfels angegeben.</span><span class="sxs-lookup"><span data-stu-id="63c88-115">These structures specify the vertex positions and colors for the cube and how the cube will be viewed.</span></span> <span data-ttu-id="63c88-116">Wir deklarieren [**ID3D11DepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476377) und [**ID3D11Buffer**](https://msdn.microsoft.com/library/windows/desktop/ff476351) mit [**ComPtr**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx) und eine Instanz von **ConstantBuffer**.</span><span class="sxs-lookup"><span data-stu-id="63c88-116">We declare [**ID3D11DepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476377) and [**ID3D11Buffer**](https://msdn.microsoft.com/library/windows/desktop/ff476351) with [**ComPtr**](https://msdn.microsoft.com/library/windows/apps/br244983.aspx) and declare an instance of **ConstantBuffer**.</span></span>

```cpp
struct SimpleCubeVertex
{
    DirectX::XMFLOAT3 pos;   // Position
    DirectX::XMFLOAT3 color; // Color
};

struct ConstantBuffer
{
    DirectX::XMFLOAT4X4 model;
    DirectX::XMFLOAT4X4 view;
    DirectX::XMFLOAT4X4 projection;
};

// This class defines the application as a whole.
ref class Direct3DTutorialFrameworkView : public IFrameworkView
{
private:
    Platform::Agile<CoreWindow> m_window;
    ComPtr<IDXGISwapChain1> m_swapChain;
    ComPtr<ID3D11Device1> m_d3dDevice;
    ComPtr<ID3D11DeviceContext1> m_d3dDeviceContext;
    ComPtr<ID3D11RenderTargetView> m_renderTargetView;
    ComPtr<ID3D11DepthStencilView> m_depthStencilView;
    ComPtr<ID3D11Buffer> m_constantBuffer;
    ConstantBuffer m_constantBufferData;
```

### <a name="2-creating-a-depth-stencil-view"></a><span data-ttu-id="63c88-117">2. Erstellen einer Tiefenschablonenansicht</span><span class="sxs-lookup"><span data-stu-id="63c88-117">2. Creating a depth stencil view</span></span>

<span data-ttu-id="63c88-118">Zusätzlich zu der Renderzielansicht erstellen wir eine Tiefenschablonenansicht.</span><span class="sxs-lookup"><span data-stu-id="63c88-118">In addition to creating the render-target view, we also create a depth-stencil view.</span></span> <span data-ttu-id="63c88-119">Die Tiefenschablonenansicht ermöglicht Direct3D das effiziente Rendern von sich näher an der Kamera befindlichen Objekten vor Objekten, die sich weiter weg von der Kamera befinden.</span><span class="sxs-lookup"><span data-stu-id="63c88-119">The depth-stencil view enables Direct3D to efficiently render objects closer to the camera in front of objects further from the camera.</span></span> <span data-ttu-id="63c88-120">Bevor wir eine Ansicht für einen Tiefenschablonenpuffer erstellen können, müssen wir den Tiefenschablonenpuffer erstellen.</span><span class="sxs-lookup"><span data-stu-id="63c88-120">Before we can create a view to a depth-stencil buffer, we must create the depth-stencil buffer.</span></span> <span data-ttu-id="63c88-121">Dazu füllen wir eine [**D3D11\_TEXTURE2D\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476253) zur Beschreibung des Tiefenschablonenpuffers auf und rufen anschließend [**ID3D11Device::CreateTexture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476521) zum Erstellen des Tiefenschablonenpuffers auf.</span><span class="sxs-lookup"><span data-stu-id="63c88-121">We populate a [**D3D11\_TEXTURE2D\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476253) to describe the depth-stencil buffer and then call [**ID3D11Device::CreateTexture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476521) to create the depth-stencil buffer.</span></span> <span data-ttu-id="63c88-122">Zum Erstellen der Tiefenschablonenansicht füllen wir eine [**D3D11\_DEPTH\_STENCIL\_VIEW\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476112) zur Beschreibung der Tiefenschablonenansicht auf und übergeben diese Beschreibung zusammen mit dem Tiefenschablonenpuffer an [**ID3D11Device::CreateDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476507).</span><span class="sxs-lookup"><span data-stu-id="63c88-122">To create the depth-stencil view, we populate a [**D3D11\_DEPTH\_STENCIL\_VIEW\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476112) to describe the depth-stencil view and pass the depth-stencil view description and the depth-stencil buffer to [**ID3D11Device::CreateDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476507).</span></span>

```cpp
        // Once the render target view is created, create a depth stencil view.  This
        // allows Direct3D to efficiently render objects closer to the camera in front
        // of objects further from the camera.

        D3D11_TEXTURE2D_DESC backBufferDesc = {0};
        backBuffer->GetDesc(&backBufferDesc);

        D3D11_TEXTURE2D_DESC depthStencilDesc;
        depthStencilDesc.Width = backBufferDesc.Width;
        depthStencilDesc.Height = backBufferDesc.Height;
        depthStencilDesc.MipLevels = 1;
        depthStencilDesc.ArraySize = 1;
        depthStencilDesc.Format = DXGI_FORMAT_D24_UNORM_S8_UINT;
        depthStencilDesc.SampleDesc.Count = 1;
        depthStencilDesc.SampleDesc.Quality = 0;
        depthStencilDesc.Usage = D3D11_USAGE_DEFAULT;
        depthStencilDesc.BindFlags = D3D11_BIND_DEPTH_STENCIL;
        depthStencilDesc.CPUAccessFlags = 0;
        depthStencilDesc.MiscFlags = 0;
        ComPtr<ID3D11Texture2D> depthStencil;
        DX::ThrowIfFailed(
            m_d3dDevice->CreateTexture2D(
                &depthStencilDesc,
                nullptr,
                &depthStencil
                )
            );

        D3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc;
        depthStencilViewDesc.Format = depthStencilDesc.Format;
        depthStencilViewDesc.ViewDimension = D3D11_DSV_DIMENSION_TEXTURE2D;
        depthStencilViewDesc.Flags = 0;
        depthStencilViewDesc.Texture2D.MipSlice = 0;
        DX::ThrowIfFailed(
            m_d3dDevice->CreateDepthStencilView(
                depthStencil.Get(),
                &depthStencilViewDesc,
                &m_depthStencilView
                )
            );
```

### <a name="3-updating-perspective-with-the-window"></a><span data-ttu-id="63c88-123">3. Aktualisieren der Perspektive mit dem Fenster</span><span class="sxs-lookup"><span data-stu-id="63c88-123">3. Updating perspective with the window</span></span>

<span data-ttu-id="63c88-124">Wir aktualisieren die Perspektivenprojektionsparameter für den Konstantenpuffer gemäß Fensterabmessungen.</span><span class="sxs-lookup"><span data-stu-id="63c88-124">We update the perspective projection parameters for the constant buffer depending on the window dimensions.</span></span> <span data-ttu-id="63c88-125">Wir fixieren die Parameter auf ein 70-Grad-Sichtfeld mit einem Tiefenbereich von 0,01 bis 100.</span><span class="sxs-lookup"><span data-stu-id="63c88-125">We fix the parameters to a 70-degree field of view with a depth range of 0.01 to 100.</span></span>

```cpp
        // Finally, update the constant buffer perspective projection parameters
        // to account for the size of the application window.  In this sample,
        // the parameters are fixed to a 70-degree field of view, with a depth
        // range of 0.01 to 100.  For a generalized camera class, see Lesson 5.

        float xScale = 1.42814801f;
        float yScale = 1.42814801f;
        if (backBufferDesc.Width > backBufferDesc.Height)
        {
            xScale = yScale *
                static_cast<float>(backBufferDesc.Height) /
                static_cast<float>(backBufferDesc.Width);
        }
        else
        {
            yScale = xScale *
                static_cast<float>(backBufferDesc.Width) /
                static_cast<float>(backBufferDesc.Height);
        }

        m_constantBufferData.projection = DirectX::XMFLOAT4X4(
            xScale, 0.0f,    0.0f,  0.0f,
            0.0f,   yScale,  0.0f,  0.0f,
            0.0f,   0.0f,   -1.0f, -0.01f,
            0.0f,   0.0f,   -1.0f,  0.0f
            );
```

### <a name="4-creating-vertex-and-pixel-shaders-with-color-elements"></a><span data-ttu-id="63c88-126">4. Erstellen von Vertex- und Pixelshadern mit Farbelementen</span><span class="sxs-lookup"><span data-stu-id="63c88-126">4. Creating vertex and pixel shaders with color elements</span></span>

<span data-ttu-id="63c88-127">In dieser App erstellen wir Vertex- und Pixelshader, die im Vergleich zu der Beschreibung im vorherigen Lernprogramm [Erstellen von Shadern und Zeichnen von Primitiven](creating-shaders-and-drawing-primitives.md) einen höheren Komplexitätsgrad aufweisen.</span><span class="sxs-lookup"><span data-stu-id="63c88-127">In this app, we create more complex vertex and pixel shaders than what we described in the previous tutorial, [Creating shaders and drawing primitives](creating-shaders-and-drawing-primitives.md).</span></span> <span data-ttu-id="63c88-128">Der Vertexshader der App transformiert die Position der einzelnen Vertizes in den Projektionsbereich und übergibt die Vertexfarbe an den Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="63c88-128">The app's vertex shader transforms each vertex position into projection space and passes the vertex color through to the pixel shader.</span></span>

<span data-ttu-id="63c88-129">Das App-Array der [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180)-Strukturen zur Beschreibung des Layouts des Vertexshadercodes enthält zwei Layoutelemente: Ein Element definiert die Vertexposition, und das andere Element definiert die Farbe.</span><span class="sxs-lookup"><span data-stu-id="63c88-129">The app's array of [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180) structures that describe the layout of the vertex shader code has two layout elements: one element defines the vertex position and the other element defines the color.</span></span>

<span data-ttu-id="63c88-130">Wir erstellen Vertex-, Index- und Konstantenpuffer, um einen kreisenden Würfel zu definieren.</span><span class="sxs-lookup"><span data-stu-id="63c88-130">We create vertex, index, and constant buffers to define an orbiting cube.</span></span>

**<span data-ttu-id="63c88-131">So definieren Sie einen kreisenden Würfel</span><span class="sxs-lookup"><span data-stu-id="63c88-131">To define an orbiting cube</span></span>**

1.  <span data-ttu-id="63c88-132">Zunächst definieren wir den Würfel.</span><span class="sxs-lookup"><span data-stu-id="63c88-132">First, we define the cube.</span></span> <span data-ttu-id="63c88-133">Wir weisen jedem Vertex neben einer Position auch eine Farbe zu.</span><span class="sxs-lookup"><span data-stu-id="63c88-133">We assign each vertex a color in addition to a position.</span></span> <span data-ttu-id="63c88-134">Dies ermöglicht dem Pixelshader eine unterschiedliche Farbgebung der einzelnen Flächen, sodass sie unterschieden werden können.</span><span class="sxs-lookup"><span data-stu-id="63c88-134">This allows the pixel shader to color each face differently so the face can be distinguished.</span></span>
2.  <span data-ttu-id="63c88-135">Als Nächstes beschreiben wir mithilfe der Würfeldefinition die Vertex- und Indexpuffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) und [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)).</span><span class="sxs-lookup"><span data-stu-id="63c88-135">Next, we describe the vertex and index buffers ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) and [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)) using the cube definition.</span></span> <span data-ttu-id="63c88-136">Wir rufen [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) einmal für jeden Puffer auf.</span><span class="sxs-lookup"><span data-stu-id="63c88-136">We call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) once for each buffer.</span></span>
3.  <span data-ttu-id="63c88-137">Nun erstellen wir einen Konstantenpuffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)) zum Übergeben der Modell-, Ansichts- und Projektionsmatrizen an den Vertexshader.</span><span class="sxs-lookup"><span data-stu-id="63c88-137">Next, we create a constant buffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)) for passing model, view, and projection matrices to the vertex shader.</span></span> <span data-ttu-id="63c88-138">Später können wir den Konstantenpuffer zum Drehen des Würfels und zum Anwenden einer Perspektivenprojektion auf den Würfel verwenden.</span><span class="sxs-lookup"><span data-stu-id="63c88-138">We can later use the constant buffer to rotate the cube and apply a perspective projection to it.</span></span> <span data-ttu-id="63c88-139">Wir rufen [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) auf, um den Konstantenpuffer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="63c88-139">We call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) to create the constant buffer.</span></span>
4.  <span data-ttu-id="63c88-140">Als Nächstes geben wir die Ansichtstransformation an, die einer Kameraposition mit X = 0, Y = 1, Z = 2 entspricht.</span><span class="sxs-lookup"><span data-stu-id="63c88-140">Next, we specify the view transform that corresponds to a camera position of X = 0, Y = 1, Z = 2.</span></span>
5.  <span data-ttu-id="63c88-141">Zum Schluss deklarieren wir eine *degree*-Variable, mit deren Hilfe wir den Würfel animieren werden, indem er in jedem Frame gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="63c88-141">Finally, we declare a *degree* variable that we will use to animate the cube by rotating it every frame.</span></span>

```cpp
        
        auto loadVSTask = DX::ReadDataAsync(L"SimpleVertexShader.cso");
        auto loadPSTask = DX::ReadDataAsync(L"SimplePixelShader.cso");
        
        
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
          // For this lesson, this is simply a DirectX::XMFLOAT3 vector defining the vertex position, and
          // a DirectX::XMFLOAT3 vector defining the vertex color.
          const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
          {
              { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0,  0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
              { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
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
        
        
        // Create vertex and index buffers that define a simple unit cube.
        auto createCubeTask = (createPSTask && createVSTask).then([this] () {

          // In the array below, which will be used to initialize the cube vertex buffers,
          // each vertex is assigned a color in addition to a position.  This will allow
          // the pixel shader to color each face differently, enabling them to be distinguished.
          SimpleCubeVertex cubeVertices[] =
          {
              { float3(-0.5f, 0.5f, -0.5f), float3(0.0f, 1.0f, 0.0f) }, // +Y (top face)
              { float3( 0.5f, 0.5f, -0.5f), float3(1.0f, 1.0f, 0.0f) },
              { float3( 0.5f, 0.5f,  0.5f), float3(1.0f, 1.0f, 1.0f) },
              { float3(-0.5f, 0.5f,  0.5f), float3(0.0f, 1.0f, 1.0f) },

              { float3(-0.5f, -0.5f,  0.5f), float3(0.0f, 0.0f, 1.0f) }, // -Y (bottom face)
              { float3( 0.5f, -0.5f,  0.5f), float3(1.0f, 0.0f, 1.0f) },
              { float3( 0.5f, -0.5f, -0.5f), float3(1.0f, 0.0f, 0.0f) },
              { float3(-0.5f, -0.5f, -0.5f), float3(0.0f, 0.0f, 0.0f) },
          };

          unsigned short cubeIndices[] =
          {
              0, 1, 2,
              0, 2, 3,

              4, 5, 6,
              4, 6, 7,

              3, 2, 5,
              3, 5, 4,

              2, 1, 6,
              2, 6, 5,

              1, 7, 6,
              1, 0, 7,

              0, 3, 4,
              0, 4, 7
          };

          D3D11_BUFFER_DESC vertexBufferDesc = {0};
          vertexBufferDesc.ByteWidth = sizeof(SimpleCubeVertex) * ARRAYSIZE(cubeVertices);
          vertexBufferDesc.Usage = D3D11_USAGE_DEFAULT;
          vertexBufferDesc.BindFlags = D3D11_BIND_VERTEX_BUFFER;
          vertexBufferDesc.CPUAccessFlags = 0;
          vertexBufferDesc.MiscFlags = 0;
          vertexBufferDesc.StructureByteStride = 0;

          D3D11_SUBRESOURCE_DATA vertexBufferData;
          vertexBufferData.pSysMem = cubeVertices;
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
          indexBufferDesc.ByteWidth = sizeof(unsigned short) * ARRAYSIZE(cubeIndices);
          indexBufferDesc.Usage = D3D11_USAGE_DEFAULT;
          indexBufferDesc.BindFlags = D3D11_BIND_INDEX_BUFFER;
          indexBufferDesc.CPUAccessFlags = 0;
          indexBufferDesc.MiscFlags = 0;
          indexBufferDesc.StructureByteStride = 0;

          D3D11_SUBRESOURCE_DATA indexBufferData;
          indexBufferData.pSysMem = cubeIndices;
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


          // Create a constant buffer for passing model, view, and projection matrices
          // to the vertex shader.  This will allow us to rotate the cube and apply
          // a perspective projection to it.

          D3D11_BUFFER_DESC constantBufferDesc = {0};
          constantBufferDesc.ByteWidth = sizeof(m_constantBufferData);
          constantBufferDesc.Usage = D3D11_USAGE_DEFAULT;
          constantBufferDesc.BindFlags = D3D11_BIND_CONSTANT_BUFFER;
          constantBufferDesc.CPUAccessFlags = 0;
          constantBufferDesc.MiscFlags = 0;
          constantBufferDesc.StructureByteStride = 0;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateBuffer(
                  &constantBufferDesc,
                  nullptr,
                  &m_constantBuffer
                  )
              );

          // Specify the view transform corresponding to a camera position of
          // X = 0, Y = 1, Z = 2.  For a generalized camera class, see Lesson 5.

          m_constantBufferData.view = DirectX::XMFLOAT4X4(
              -1.00000000f, 0.00000000f,  0.00000000f,  0.00000000f,
               0.00000000f, 0.89442718f,  0.44721359f,  0.00000000f,
               0.00000000f, 0.44721359f, -0.89442718f, -2.23606800f,
               0.00000000f, 0.00000000f,  0.00000000f,  1.00000000f
              );

        });
        
        // This value will be used to animate the cube by rotating it every frame.
        float degree = 0.0f;
        
```

### <a name="5-rotating-and-drawing-the-cube-and-presenting-the-rendered-image"></a><span data-ttu-id="63c88-142">5. Drehen und Zeichnen des Würfels und Darstellen des gerenderten Bilds</span><span class="sxs-lookup"><span data-stu-id="63c88-142">5. Rotating and drawing the cube and presenting the rendered image</span></span>

<span data-ttu-id="63c88-143">Wir rufen eine Endlosschleife auf, um die Szene fortlaufend zu rendern und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="63c88-143">We enter an endless loop to continually render and display the scene.</span></span> <span data-ttu-id="63c88-144">Wir rufen die **rotationY**-Inlinefunktion (BasicMath.h) mit einer Rotationsmenge auf, um die Werte festzulegen, mit deren Hilfe sich die Modellmatrix des Würfels um die Y-Achse dreht.</span><span class="sxs-lookup"><span data-stu-id="63c88-144">We call the **rotationY** inline function (BasicMath.h) with a rotation amount to set values that will rotate the cube’s model matrix around the Y axis.</span></span> <span data-ttu-id="63c88-145">Anschließend rufen wir [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486) auf, um den Konstantenpuffer zu aktualisieren und das Würfelmodell zu drehen.</span><span class="sxs-lookup"><span data-stu-id="63c88-145">We then call [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486) to update the constant buffer and rotate the cube model.</span></span> <span data-ttu-id="63c88-146">Wir rufen [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) auf, um das Renderziel aus Ausgabeziel anzugeben.</span><span class="sxs-lookup"><span data-stu-id="63c88-146">We call [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) to specify the render target as the output target.</span></span> <span data-ttu-id="63c88-147">In diesem **OMSetRenderTargets**-Aufruf übergeben wir die Tiefenschablonenansicht.</span><span class="sxs-lookup"><span data-stu-id="63c88-147">In this **OMSetRenderTargets** call, we pass the depth-stencil view.</span></span> <span data-ttu-id="63c88-148">Wir rufen [**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) auf, um das Renderziel in eine blaue Volltonfarbe zu bereinigen. Anschließend rufen wir [**ID3D11DeviceContext::ClearDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476387) auf, um den Tiefenpuffer zu leeren.</span><span class="sxs-lookup"><span data-stu-id="63c88-148">We call [**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) to clear the render target to a solid blue color and call [**ID3D11DeviceContext::ClearDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476387) to clear the depth buffer.</span></span>

<span data-ttu-id="63c88-149">In der Endlosschleife zeichnen wir den Würfel ebenfalls auf der blauen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="63c88-149">In the endless loop, we also draw the cube on the blue surface.</span></span>

**<span data-ttu-id="63c88-150">So zeichnen Sie den Würfel</span><span class="sxs-lookup"><span data-stu-id="63c88-150">To draw the cube</span></span>**

1.  <span data-ttu-id="63c88-151">Wir rufen zunächst [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) auf, um das Streamen der Vertexpufferdaten in den Eingabeassemblerzustand zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="63c88-151">First, we call [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) to describe how vertex buffer data is streamed into the input-assembler stage.</span></span>
2.  <span data-ttu-id="63c88-152">Als Nächstes rufen wir [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) und [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) auf, um die Vertex- und Indexpuffer an den Eingabeassemblerzustand zu binden.</span><span class="sxs-lookup"><span data-stu-id="63c88-152">Next, we call [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) and [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) to bind the vertex and index buffers to the input-assembler stage.</span></span>
3.  <span data-ttu-id="63c88-153">Nun rufen wir [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) mit dem [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP)-Wert auf, um für den Eingabeassemblerzustand anzugeben, dass die Vertexdaten als Dreieckskette interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="63c88-153">Next, we call [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) with the [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP) value to specify for the input-assembler stage to interpret the vertex data as a triangle strip.</span></span>
4.  <span data-ttu-id="63c88-154">Im nächsten Schritt rufen wir [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) auf, um die Vertexshaderphase mit dem Vertexshadercode zu initialisieren. Zudem rufen wir [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) auf, um die Pixelshaderphase mit dem Pixelshadercode zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="63c88-154">Next, we call [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) to initialize the vertex shader stage with the vertex shader code and [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) to initialize the pixel shader stage with the pixel shader code.</span></span>
5.  <span data-ttu-id="63c88-155">Dann rufen wir [**ID3D11DeviceContext::VSSetConstantBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476491) auf, um den im Vertexshader-Pipelinezustand verwendeten Konstantenpuffer festzulegen.</span><span class="sxs-lookup"><span data-stu-id="63c88-155">Next, we call [**ID3D11DeviceContext::VSSetConstantBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476491) to set the constant buffer that is used by the vertex shader pipeline stage.</span></span>
6.  <span data-ttu-id="63c88-156">Schließlich rufen wir [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) auf, um den Würfel zu zeichnen und ihn an die Renderpipeline zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="63c88-156">Finally, we call [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) to draw the cube and submit it to the rendering pipeline.</span></span>

<span data-ttu-id="63c88-157">Wir rufen [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) auf, um das gerenderte Bild im Fenster darzustellen.</span><span class="sxs-lookup"><span data-stu-id="63c88-157">We call [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) to present the rendered image to the window.</span></span>

```cpp
            // Update the constant buffer to rotate the cube model.
            m_constantBufferData.model = XMMatrixRotationY(-degree);
            degree += 1.0f;

            m_d3dDeviceContext->UpdateSubresource(
                m_constantBuffer.Get(),
                0,
                nullptr,
                &m_constantBufferData,
                0,
                0
                );

            // Specify the render target and depth stencil we created as the output target.
            m_d3dDeviceContext->OMSetRenderTargets(
                1,
                m_renderTargetView.GetAddressOf(),
                m_depthStencilView.Get()
                );

            // Clear the render target to a solid color, and reset the depth stencil.
            const float clearColor[4] = { 0.071f, 0.04f, 0.561f, 1.0f };
            m_d3dDeviceContext->ClearRenderTargetView(
                m_renderTargetView.Get(),
                clearColor
                );

            m_d3dDeviceContext->ClearDepthStencilView(
                m_depthStencilView.Get(),
                D3D11_CLEAR_DEPTH,
                1.0f,
                0
                );

            m_d3dDeviceContext->IASetInputLayout(inputLayout.Get());

            // Set the vertex and index buffers, and specify the way they define geometry.
            UINT stride = sizeof(SimpleCubeVertex);
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

            m_d3dDeviceContext->VSSetConstantBuffers(
                0,
                1,
                m_constantBuffer.GetAddressOf()
                );

            m_d3dDeviceContext->PSSetShader(
                pixelShader.Get(),
                nullptr,
                0
                );

            // Draw the cube.
            m_d3dDeviceContext->DrawIndexed(
                ARRAYSIZE(cubeIndices),
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

## <a name="summary-and-next-steps"></a><span data-ttu-id="63c88-158">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="63c88-158">Summary and next steps</span></span>


<span data-ttu-id="63c88-159">Wir haben Tiefen, Perspektiven, Farben und andere Effekte in Primitiven verwendet.</span><span class="sxs-lookup"><span data-stu-id="63c88-159">We used depth, perspective, color, and other effects on primitives.</span></span>

<span data-ttu-id="63c88-160">Als Nächstes wenden wir Texturen auf Primitive an.</span><span class="sxs-lookup"><span data-stu-id="63c88-160">Next, we apply textures to primitives.</span></span>

[<span data-ttu-id="63c88-161">Anwenden von Texturen auf Primitive</span><span class="sxs-lookup"><span data-stu-id="63c88-161">Applying textures to primitives</span></span>](applying-textures-to-primitives.md)

 

 




