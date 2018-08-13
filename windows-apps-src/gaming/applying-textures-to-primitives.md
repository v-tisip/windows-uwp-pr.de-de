---
author: mtoepke
title: Anwenden von Texturen auf Grundtypen
description: Wir laden an dieser Stelle unformatierte Texturdaten und wenden diese auf einen 3D-Grundtyp an. Dazu verwenden wir den Würfel, den wir in „Verwenden von Tiefe und Effekten für Grundtypen“ erstellt haben.
ms.assetid: aeed09e3-c47a-4dd9-d0e8-d1b8bdd7e9b4
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Texturen, DirectX
ms.openlocfilehash: cc25d7bcc5809dd10b43418ccd42f78c10d1336e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233837"
---
# <a name="apply-textures-to-primitives"></a><span data-ttu-id="eae34-104">Anwenden von Texturen auf Grundtypen</span><span class="sxs-lookup"><span data-stu-id="eae34-104">Apply textures to primitives</span></span>


<span data-ttu-id="eae34-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="eae34-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="eae34-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="eae34-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="eae34-107">Wir laden an dieser Stelle unformatierte Texturdaten und wenden diese auf einen 3D-Grundtyp an. Dazu verwenden wir den Würfel, den wir unter [Verwenden von Tiefe und Effekten auf Grundtypen](using-depth-and-effects-on-primitives.md) erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="eae34-107">Here, we load raw texture data and apply that data to a 3D primitive by using the cube that we created in [Using depth and effects on primitives](using-depth-and-effects-on-primitives.md).</span></span> <span data-ttu-id="eae34-108">Außerdem stellen wir ein einfaches Skalarprodukt-Lichtmodell vor. Die Oberflächen des Würfels im Modell sind, je nach Entfernung von der und Winkel zur Lichtquelle, heller oder dunkler.</span><span class="sxs-lookup"><span data-stu-id="eae34-108">We also introduce a simple dot-product lighting model, where the cube surfaces are lighter or darker based on their distance and angle relative to a light source.</span></span>

<span data-ttu-id="eae34-109">**Lernziel**: Texturen auf Grundtypen anwenden.</span><span class="sxs-lookup"><span data-stu-id="eae34-109">**Objective:** To apply textures to primitives.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eae34-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="eae34-110">Prerequisites</span></span>


<span data-ttu-id="eae34-111">Es wird davon ausgegangen, dass Sie mit C+ vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="eae34-111">We assume that you are familiar with C++.</span></span> <span data-ttu-id="eae34-112">Sie müssen außerdem mit den grundlegenden Konzepten der Grafikprogrammierung vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="eae34-112">You also need basic experience with graphics programming concepts.</span></span>

<span data-ttu-id="eae34-113">Außerdem wird davon ausgegangen, dass Sie mit folgenden Themen vertraut sind: [Schnellstart: Einrichten von DirectX-Ressourcen und Anzeigen eines Bilds](setting-up-directx-resources.md), [Erstellen von Shadern und Zeichnen von Grundtypen](creating-shaders-and-drawing-primitives.md) und [Verwenden von Tiefe und Effekten für Grundtypen](using-depth-and-effects-on-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="eae34-113">We also assume that you went through [Quickstart: setting up DirectX resources and displaying an image](setting-up-directx-resources.md), [Creating shaders and drawing primitives](creating-shaders-and-drawing-primitives.md), and [Using depth and effects on primitives](using-depth-and-effects-on-primitives.md).</span></span>

<span data-ttu-id="eae34-114">**Zeitaufwand:** 20Minuten.</span><span class="sxs-lookup"><span data-stu-id="eae34-114">**Time to complete:** 20 minutes.</span></span>

<a name="instructions"></a><span data-ttu-id="eae34-115">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="eae34-115">Instructions</span></span>
------------

### <a name="1-defining-variables-for-a-textured-cube"></a><span data-ttu-id="eae34-116">1. Definieren von Variablen für einen Würfel mit Texturen</span><span class="sxs-lookup"><span data-stu-id="eae34-116">1. Defining variables for a textured cube</span></span>

<span data-ttu-id="eae34-117">Zunächst müssen wir die **BasicVertex**-Struktur und die **ConstantBuffer**-Struktur für den Würfel mit Texturen definieren.</span><span class="sxs-lookup"><span data-stu-id="eae34-117">First, we need to define the **BasicVertex** and **ConstantBuffer** structures for the textured cube.</span></span> <span data-ttu-id="eae34-118">Diese Strukturen bestimmen die Vertexpositionen, die Ausrichtungen und die Texturen für den Würfel. Außerdem haben sie Einfluss darauf, wie der Würfel angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="eae34-118">These structures specify the vertex positions, orientations, and textures for the cube and how the cube will be viewed.</span></span> <span data-ttu-id="eae34-119">Weiterhin deklarieren wir Variablen analog zum vorangehenden Lernprogramm [Verwenden von Tiefe und Effekten für Grundtypen](using-depth-and-effects-on-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="eae34-119">Otherwise, we declare variables similarly to the previous tutorial, [Using depth and effects on primitives](using-depth-and-effects-on-primitives.md).</span></span>

```cpp
struct BasicVertex
{
    DirectX::XMFLOAT3 pos;  // Position
    DirectX::XMFLOAT3 norm; // Surface normal vector
    DirectX::XMFLOAT2 tex;  // Texture coordinate
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

### <a name="2-creating-vertex-and-pixel-shaders-with-surface-and-texture-elements"></a><span data-ttu-id="eae34-120">2. Erstellen von Vertex- und Pixelshadern mit Oberflächen- und Texturelementen</span><span class="sxs-lookup"><span data-stu-id="eae34-120">2. Creating vertex and pixel shaders with surface and texture elements</span></span>

<span data-ttu-id="eae34-121">Die an dieser Stelle erstellten Vertex- und Pixelshader sind komplexer als die im vorangehenden Lernprogramm [Verwenden von Tiefe und Effekten für Grundtypen](using-depth-and-effects-on-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="eae34-121">Here, we create more complex vertex and pixel shaders than in the previous tutorial, [Using depth and effects on primitives](using-depth-and-effects-on-primitives.md).</span></span> <span data-ttu-id="eae34-122">Der Vertexshader dieser App wandelt jede Vertexposition in eine Projektionsfläche um und übergibt die Koordinaten der Vertexttextur über den Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="eae34-122">This app's vertex shader transforms each vertex position into projection space and passes the vertex texture coordinate through to the pixel shader.</span></span>

<span data-ttu-id="eae34-123">Das Array von [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180)-Strukturen dieser App, die das Layout des Vertex-Shader-Codes beschreiben, weist drei Layoutelemente auf: Ein Element definiert die Vertexposition, ein Element definiert den normalen Oberflächenvektor (die normale Ausrichtung der Oberfläche), und das dritte Element definiert die Texturkoordinaten.</span><span class="sxs-lookup"><span data-stu-id="eae34-123">The app's array of [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180) structures that describe the layout of the vertex shader code has three layout elements: one element defines the vertex position, another element defines the surface normal vector (the direction that the surface normally faces), and the third element defines the texture coordinates.</span></span>

<span data-ttu-id="eae34-124">Wir erstellen einen Vertex, einen Index sowie konstante Puffer, die einen kreisenden Würfel mit Textur definieren.</span><span class="sxs-lookup"><span data-stu-id="eae34-124">We create vertex, index, and constant buffers that define an orbiting textured cube.</span></span>

**<span data-ttu-id="eae34-125">So erstellen Sie einen kreisenden Würfel mit Textur</span><span class="sxs-lookup"><span data-stu-id="eae34-125">To define an orbiting textured cube</span></span>**

1.  <span data-ttu-id="eae34-126">Zunächst definieren wir den Würfel.</span><span class="sxs-lookup"><span data-stu-id="eae34-126">First, we define the cube.</span></span> <span data-ttu-id="eae34-127">Jedem Vertex werden eine Position, ein normaler Oberflächenvektor sowie Texturkoordinaten zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="eae34-127">Each vertex is assigned a position, a surface normal vector, and texture coordinates.</span></span> <span data-ttu-id="eae34-128">Um für die einzelnen Seiten unterschiedliche normale Vektoren und Texturkoordinaten definieren und verwenden zu können, werden mehrere Scheitelpunkte für jede Ecke definiert.</span><span class="sxs-lookup"><span data-stu-id="eae34-128">We use multiple vertices for each corner to allow different normal vectors and texture coordinates to be defined for each face.</span></span>
2.  <span data-ttu-id="eae34-129">Als Nächstes beschreiben wir mithilfe der Würfeldefinition die Vertex- und Indexpuffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) und [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)).</span><span class="sxs-lookup"><span data-stu-id="eae34-129">Next, we describe the vertex and index buffers ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) and [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)) using the cube definition.</span></span> <span data-ttu-id="eae34-130">Wir rufen [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) einmal für jeden Puffer auf.</span><span class="sxs-lookup"><span data-stu-id="eae34-130">We call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) once for each buffer.</span></span>
3.  <span data-ttu-id="eae34-131">Nun erstellen wir einen Konstantenpuffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)) zum Übergeben der Modell-, Ansichts- und Projektionsmatrizen an den Vertexshader.</span><span class="sxs-lookup"><span data-stu-id="eae34-131">Next, we create a constant buffer ([**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)) for passing model, view, and projection matrices to the vertex shader.</span></span> <span data-ttu-id="eae34-132">Später können wir den Konstantenpuffer zum Drehen des Würfels und zum Anwenden einer Perspektivenprojektion auf den Würfel verwenden.</span><span class="sxs-lookup"><span data-stu-id="eae34-132">We can later use the constant buffer to rotate the cube and apply a perspective projection to it.</span></span> <span data-ttu-id="eae34-133">Wir rufen [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) auf, um den Konstantenpuffer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="eae34-133">We call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) to create the constant buffer.</span></span>
4.  <span data-ttu-id="eae34-134">Abschließend geben wir die Transformation der Ansicht an, die der Kameraposition X = 0, Y = 1, Z = 2 entspricht.</span><span class="sxs-lookup"><span data-stu-id="eae34-134">Finally, we specify the view transform that corresponds to a camera position of X = 0, Y = 1, Z = 2.</span></span>

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
          // These correspond to the elements of the BasicVertex struct defined above.
          const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
          {
              { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0,  0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
              { "NORMAL",   0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
              { "TEXCOORD", 0, DXGI_FORMAT_R32G32_FLOAT,    0, 24, D3D11_INPUT_PER_VERTEX_DATA, 0 },
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
          // multiple vertices are used for each corner to allow different normal vectors and
          // texture coordinates to be defined for each face.
          BasicVertex cubeVertices[] =
          {
              { DirectX::XMFLOAT3(-0.5f, 0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // +Y (top face)
              { DirectX::XMFLOAT3( 0.5f, 0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3( 0.5f, 0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3(-0.5f, 0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },

              { DirectX::XMFLOAT3(-0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, -1.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // -Y (bottom face)
              { DirectX::XMFLOAT3( 0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, -1.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3( 0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, -1.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3(-0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, -1.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },

              { DirectX::XMFLOAT3(0.5f,  0.5f,  0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // +X (right face)
              { DirectX::XMFLOAT3(0.5f,  0.5f, -0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3(0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3(0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },

              { DirectX::XMFLOAT3(-0.5f,  0.5f, -0.5f), DirectX::XMFLOAT3(-1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // -X (left face)
              { DirectX::XMFLOAT3(-0.5f,  0.5f,  0.5f), DirectX::XMFLOAT3(-1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3(-0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(-1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3(-0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(-1.0f, 0.0f, 0.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },

              { DirectX::XMFLOAT3(-0.5f,  0.5f, 0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 1.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // +Z (front face)
              { DirectX::XMFLOAT3( 0.5f,  0.5f, 0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 1.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3( 0.5f, -0.5f, 0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 1.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3(-0.5f, -0.5f, 0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 1.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },

              { DirectX::XMFLOAT3( 0.5f,  0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, -1.0f), DirectX::XMFLOAT2(0.0f, 0.0f) }, // -Z (back face)
              { DirectX::XMFLOAT3(-0.5f,  0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, -1.0f), DirectX::XMFLOAT2(1.0f, 0.0f) },
              { DirectX::XMFLOAT3(-0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, -1.0f), DirectX::XMFLOAT2(1.0f, 1.0f) },
              { DirectX::XMFLOAT3( 0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, -1.0f), DirectX::XMFLOAT2(0.0f, 1.0f) },
          };

          unsigned short cubeIndices[] =
          {
              0, 1, 2,
              0, 2, 3,

              4, 5, 6,
              4, 6, 7,

              8, 9, 10,
              8, 10, 11,

              12, 13, 14,
              12, 14, 15,

              16, 17, 18,
              16, 18, 19,

              20, 21, 22,
              20, 22, 23
          };

          D3D11_BUFFER_DESC vertexBufferDesc = {0};
          vertexBufferDesc.ByteWidth = sizeof(BasicVertex) * ARRAYSIZE(cubeVertices);
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
```

### <a name="3-creating-textures-and-samplers"></a><span data-ttu-id="eae34-135">3. Erstellen von Texturen und Mustern</span><span class="sxs-lookup"><span data-stu-id="eae34-135">3. Creating textures and samplers</span></span>

<span data-ttu-id="eae34-136">Während im vorangehenden Beispiel ([Verwenden von Tiefe und Effekten für Grundtypen](using-depth-and-effects-on-primitives.md)) Farben angewendet wurden, werden hier Texturdaten auf einen Würfel angewendet.</span><span class="sxs-lookup"><span data-stu-id="eae34-136">Here, we apply texture data to a cube rather than applying colors as in the previous tutorial, [Using depth and effects on primitives](using-depth-and-effects-on-primitives.md).</span></span>

<span data-ttu-id="eae34-137">Wir verwenden unformatierte Texturdaten, um die Texturen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="eae34-137">We use raw texture data to create textures.</span></span>

**<span data-ttu-id="eae34-138">Erstellen von Texturen und Mustern</span><span class="sxs-lookup"><span data-stu-id="eae34-138">To create textures and samplers</span></span>**

1.  <span data-ttu-id="eae34-139">Wir beginnen damit, unformatierte Texturdaten aus der Datei „texturedata.bin“ auf dem Datenträger zu lesen.</span><span class="sxs-lookup"><span data-stu-id="eae34-139">First, we read raw texture data from the texturedata.bin file on disk.</span></span>
2.  <span data-ttu-id="eae34-140">Im Anschluss erstellen wir eine [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur, die auf diese unformatierten Texturdaten verweist.</span><span class="sxs-lookup"><span data-stu-id="eae34-140">Next, we construct a [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structure that references that raw texture data.</span></span>
3.  <span data-ttu-id="eae34-141">Danach füllen wir eine [**D3D11\_TEXTURE2D\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476253)-Struktur, um die Textur zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="eae34-141">Then, we populate a [**D3D11\_TEXTURE2D\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476253) structure to describe the texture.</span></span> <span data-ttu-id="eae34-142">Nun übergeben wir die [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur und die **D3D11\_TEXTURE2D\_DESC**-Struktur in einem Aufruf von [**ID3D11Device::CreateTexture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476521), um die Textur zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="eae34-142">We then pass the [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) and **D3D11\_TEXTURE2D\_DESC** structures in a call to [**ID3D11Device::CreateTexture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476521) to create the texture.</span></span>
4.  <span data-ttu-id="eae34-143">Jetzt erstellen wir eine Shaderressourcenansicht der Textur, damit diese von Shadern verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="eae34-143">Next, we create a shader-resource view of the texture so shaders can use the texture.</span></span> <span data-ttu-id="eae34-144">Um die Shaderressourcenansicht zu erstellen, füllen wir eine [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476211) zur Beschreibung der Shaderressourcenansicht und übergeben die Beschreibung der Shaderressourcenansicht sowie die Textur an [**ID3D11Device::CreateShaderResourceView**](https://msdn.microsoft.com/library/windows/desktop/ff476519).</span><span class="sxs-lookup"><span data-stu-id="eae34-144">To create the shader-resource view, we populate a [**D3D11\_SHADER\_RESOURCE\_VIEW\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476211) to describe the shader-resource view and pass the shader-resource view description and the texture to [**ID3D11Device::CreateShaderResourceView**](https://msdn.microsoft.com/library/windows/desktop/ff476519).</span></span> <span data-ttu-id="eae34-145">Die Beschreibung der Ansicht sollte im Allgemeinen der Beschreibung der Textur entsprechen.</span><span class="sxs-lookup"><span data-stu-id="eae34-145">In general, you match the view description with the texture description.</span></span>
5.  <span data-ttu-id="eae34-146">Anschließend erstellen wir einen Musterzustand für die Textur.</span><span class="sxs-lookup"><span data-stu-id="eae34-146">Next, we create sampler state for the texture.</span></span> <span data-ttu-id="eae34-147">Dieser Musterzustand legt anhand der relevanten Texturdaten fest, wie die Farbe für eine bestimmte Texturkoordinate bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="eae34-147">This sampler state uses the relevant texture data to define how the color for a particular texture coordinate is determined.</span></span> <span data-ttu-id="eae34-148">Wir füllen eine [**D3D11\_SAMPLER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476207)-Struktur, um den Musterzustand zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="eae34-148">We populate a [**D3D11\_SAMPLER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476207) structure to describe the sampler state.</span></span> <span data-ttu-id="eae34-149">Nun übergeben wir die **D3D11\_SAMPLER\_DESC**-Struktur in einem Aufruf von [**ID3D11Device::CreateSamplerState**](https://msdn.microsoft.com/library/windows/desktop/ff476518), um den Musterzustand zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="eae34-149">We then pass the **D3D11\_SAMPLER\_DESC** structure in a call to [**ID3D11Device::CreateSamplerState**](https://msdn.microsoft.com/library/windows/desktop/ff476518) to create the sampler state.</span></span>
6.  <span data-ttu-id="eae34-150">Zum Schluss deklarieren wir eine *degree*-Variable, mit deren Hilfe wir den Würfel animieren werden, indem er in jedem Frame gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="eae34-150">Finally, we declare a *degree* variable that we will use to animate the cube by rotating it every frame.</span></span>

```cpp
        
        // Load the raw texture data from disk and construct a subresource description that references it.
        auto loadTDTask = DX::ReadDataAsync(L"texturedata.bin");
          
        auto constructSubresourceTask = loadTDTask.then([this](const std::vector<byte>& vertexShaderBytecode) {  
        
          D3D11_SUBRESOURCE_DATA textureSubresourceData = {0};
          textureSubresourceData.pSysMem = textureData->Data;

          // Specify the size of a row in bytes, known as a priori about the texture data.
          textureSubresourceData.SysMemPitch = 1024;

          // As this is not a texture array or 3D texture, this parameter is ignored.
          textureSubresourceData.SysMemSlicePitch = 0;

          // Create a texture description from information known as a priori about the data.
          // Generalized texture loading code can be found in the Resource Loading sample.
          D3D11_TEXTURE2D_DESC textureDesc = {0};
          textureDesc.Width = 256;
          textureDesc.Height = 256;
          textureDesc.Format = DXGI_FORMAT_R8G8B8A8_UNORM;
          textureDesc.Usage = D3D11_USAGE_DEFAULT;
          textureDesc.CPUAccessFlags = 0;
          textureDesc.MiscFlags = 0;

          // Most textures contain more than one MIP level.  For simplicity, this sample uses only one.
          textureDesc.MipLevels = 1;

          // As this will not be a texture array, this parameter is ignored.
          textureDesc.ArraySize = 1;

          // Don't use multi-sampling.
          textureDesc.SampleDesc.Count = 1;
          textureDesc.SampleDesc.Quality = 0;

          // Allow the texture to be bound as a shader resource.
          textureDesc.BindFlags = D3D11_BIND_SHADER_RESOURCE;

          ComPtr<ID3D11Texture2D> texture;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateTexture2D(
                  &textureDesc,
                  &textureSubresourceData,
                  &texture
                  )
              );

          // Once the texture is created, we must create a shader resource view of it
          // so that shaders may use it.  In general, the view description will match
          // the texture description.
          D3D11_SHADER_RESOURCE_VIEW_DESC textureViewDesc;
          ZeroMemory(&textureViewDesc, sizeof(textureViewDesc));
          textureViewDesc.Format = textureDesc.Format;
          textureViewDesc.ViewDimension = D3D11_SRV_DIMENSION_TEXTURE2D;
          textureViewDesc.Texture2D.MipLevels = textureDesc.MipLevels;
          textureViewDesc.Texture2D.MostDetailedMip = 0;

          ComPtr<ID3D11ShaderResourceView> textureView;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateShaderResourceView(
                  texture.Get(),
                  &textureViewDesc,
                  &textureView
                  )
              );

          // Once the texture view is created, create a sampler.  This defines how the color
          // for a particular texture coordinate is determined using the relevant texture data.
          D3D11_SAMPLER_DESC samplerDesc;
          ZeroMemory(&samplerDesc, sizeof(samplerDesc));

          samplerDesc.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;

          // The sampler does not use anisotropic filtering, so this parameter is ignored.
          samplerDesc.MaxAnisotropy = 0;

          // Specify how texture coordinates outside of the range 0..1 are resolved.
          samplerDesc.AddressU = D3D11_TEXTURE_ADDRESS_WRAP;
          samplerDesc.AddressV = D3D11_TEXTURE_ADDRESS_WRAP;
          samplerDesc.AddressW = D3D11_TEXTURE_ADDRESS_WRAP;

          // Use no special MIP clamping or bias.
          samplerDesc.MipLODBias = 0.0f;
          samplerDesc.MinLOD = 0;
          samplerDesc.MaxLOD = D3D11_FLOAT32_MAX;

          // Don't use a comparison function.
          samplerDesc.ComparisonFunc = D3D11_COMPARISON_NEVER;

          // Border address mode is not used, so this parameter is ignored.
          samplerDesc.BorderColor[0] = 0.0f;
          samplerDesc.BorderColor[1] = 0.0f;
          samplerDesc.BorderColor[2] = 0.0f;
          samplerDesc.BorderColor[3] = 0.0f;

          ComPtr<ID3D11SamplerState> sampler;
          DX::ThrowIfFailed(
              m_d3dDevice->CreateSamplerState(
                  &samplerDesc,
                  &sampler
                  )
              );
        });

        // This value will be used to animate the cube by rotating it every frame;
        float degree = 0.0f;
```

### <a name="4-rotating-and-drawing-the-textured-cube-and-presenting-the-rendered-image"></a><span data-ttu-id="eae34-151">4. Drehen und Zeichnen des Würfels mit Texturen und Darstellen des gerenderten Bilds</span><span class="sxs-lookup"><span data-stu-id="eae34-151">4. Rotating and drawing the textured cube and presenting the rendered image</span></span>

<span data-ttu-id="eae34-152">Um die Szene ohne Unterbrechung zu rendern und anzuzeigen, wird analog zu früheren Beispielen eine Endlosschleife aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="eae34-152">As in the previous tutorials, we enter an endless loop to continually render and display the scene.</span></span> <span data-ttu-id="eae34-153">Wir rufen die **rotationY**-Inlinefunktion (BasicMath.h) mit einer Rotationsmenge auf, um die Werte festzulegen, mit deren Hilfe sich die Modellmatrix des Würfels um die Y-Achse dreht.</span><span class="sxs-lookup"><span data-stu-id="eae34-153">We call the **rotationY** inline function (BasicMath.h) with a rotation amount to set values that will rotate the cube’s model matrix around the Y axis.</span></span> <span data-ttu-id="eae34-154">Anschließend rufen wir [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486) auf, um den Konstantenpuffer zu aktualisieren und das Würfelmodell zu drehen.</span><span class="sxs-lookup"><span data-stu-id="eae34-154">We then call [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486) to update the constant buffer and rotate the cube model.</span></span> <span data-ttu-id="eae34-155">Nun rufen wir [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) auf, um das Renderingziel und die Ansicht für die Tiefe/Schablone anzugeben.</span><span class="sxs-lookup"><span data-stu-id="eae34-155">Next, we call [**ID3D11DeviceContext::OMSetRenderTargets**](https://msdn.microsoft.com/library/windows/desktop/ff476464) to specify the render target and the depth-stencil view.</span></span> <span data-ttu-id="eae34-156">Wir rufen [**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) auf, um das Renderziel in eine blaue Volltonfarbe zu bereinigen. Anschließend rufen wir [**ID3D11DeviceContext::ClearDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476387) auf, um den Tiefenpuffer zu leeren.</span><span class="sxs-lookup"><span data-stu-id="eae34-156">We call [**ID3D11DeviceContext::ClearRenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476388) to clear the render target to a solid blue color and call [**ID3D11DeviceContext::ClearDepthStencilView**](https://msdn.microsoft.com/library/windows/desktop/ff476387) to clear the depth buffer.</span></span>

<span data-ttu-id="eae34-157">In der Endlosschleife zeichnen wir auch den Würfel mit Texturen auf der blauen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="eae34-157">In the endless loop, we also draw the textured cube on the blue surface.</span></span>

**<span data-ttu-id="eae34-158">So zeichnen Sie den Würfel mit Texturen</span><span class="sxs-lookup"><span data-stu-id="eae34-158">To draw the textured cube</span></span>**

1.  <span data-ttu-id="eae34-159">Wir rufen zunächst [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) auf, um das Streamen der Vertexpufferdaten in die Eingabe-Assembly-Phase zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="eae34-159">First, we call [**ID3D11DeviceContext::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) to describe how vertex buffer data is streamed into the input-assembler stage.</span></span>
2.  <span data-ttu-id="eae34-160">Als Nächstes rufen wir [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) und [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) auf, um die Vertex- und Indexpuffer an den Eingabeassemblerzustand zu binden.</span><span class="sxs-lookup"><span data-stu-id="eae34-160">Next, we call [**ID3D11DeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) and [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476453) to bind the vertex and index buffers to the input-assembler stage.</span></span>
3.  <span data-ttu-id="eae34-161">Nun rufen wir [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) mit dem [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP)-Wert auf, um für den Eingabeassemblerzustand anzugeben, dass die Vertexdaten als Dreieckskette interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="eae34-161">Next, we call [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) with the [**D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLESTRIP**](https://msdn.microsoft.com/library/windows/desktop/ff476189#D3D11_PRIMITIVE_TOPOLOGY_TRIANGLESTRIP) value to specify for the input-assembler stage to interpret the vertex data as a triangle strip.</span></span>
4.  <span data-ttu-id="eae34-162">Im nächsten Schritt rufen wir [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) auf, um die Vertexshaderphase mit dem Vertexshadercode zu initialisieren. Zudem rufen wir [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) auf, um die Pixelshaderphase mit dem Pixelshadercode zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="eae34-162">Next, we call [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) to initialize the vertex shader stage with the vertex shader code and [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) to initialize the pixel shader stage with the pixel shader code.</span></span>
5.  <span data-ttu-id="eae34-163">Nun rufen wir [**ID3D11DeviceContext::VSSetConstantBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476491) auf, um den in der Vertex-Shader-Pipelinephase verwendeten Konstantenpuffer festzulegen.</span><span class="sxs-lookup"><span data-stu-id="eae34-163">Next, we call [**ID3D11DeviceContext::VSSetConstantBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476491) to set the constant buffer that is used by the vertex shader pipeline stage.</span></span>
6.  <span data-ttu-id="eae34-164">Danach rufen wir [**PSSetShaderResources**](https://msdn.microsoft.com/library/windows/desktop/ff476473) auf, um die Shaderressourcenansicht der Textur an die Pipelinephase des Pixelshaders zu binden.</span><span class="sxs-lookup"><span data-stu-id="eae34-164">Next, we call [**PSSetShaderResources**](https://msdn.microsoft.com/library/windows/desktop/ff476473) to bind the shader-resource view of the texture to the pixel shader pipeline stage.</span></span>
7.  <span data-ttu-id="eae34-165">Danach rufen wir [**PSSetSamplers**](https://msdn.microsoft.com/library/windows/desktop/ff476471) auf, um den Musterzustand für die Pipelinephase des Pixelshaders festzulegen.</span><span class="sxs-lookup"><span data-stu-id="eae34-165">Next, we call [**PSSetSamplers**](https://msdn.microsoft.com/library/windows/desktop/ff476471) to set the sampler state to the pixel shader pipeline stage.</span></span>
8.  <span data-ttu-id="eae34-166">Schließlich rufen wir [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) auf, um den Würfel zu zeichnen und ihn an die Renderpipeline zu senden.</span><span class="sxs-lookup"><span data-stu-id="eae34-166">Finally, we call [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) to draw the cube and submit it to the rendering pipeline.</span></span>

<span data-ttu-id="eae34-167">Analog zu früheren Lernprogrammen wird mit einem Aufruf von [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) das gerenderte Bild im Fenster dargestellt.</span><span class="sxs-lookup"><span data-stu-id="eae34-167">As in the previous tutorials, we call [**IDXGISwapChain::Present**](https://msdn.microsoft.com/library/windows/desktop/bb174576) to present the rendered image to the window.</span></span>

```cpp
            // Update the constant buffer to rotate the cube model.
            m_constantBufferData.model = DirectX::XMMatrixRotationY(-degree);
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
            UINT stride = sizeof(BasicVertex);
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

            m_d3dDeviceContext->PSSetShaderResources(
                0,
                1,
                textureView.GetAddressOf()
                );

            m_d3dDeviceContext->PSSetSamplers(
                0,
                1,
                sampler.GetAddressOf()
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

## <a name="summary"></a><span data-ttu-id="eae34-168">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="eae34-168">Summary</span></span>


<span data-ttu-id="eae34-169">Wir haben unformatierte Textdaten geladen und diese Daten auf einen 3D-Grundtyp angewendet.</span><span class="sxs-lookup"><span data-stu-id="eae34-169">We loaded raw texture data and applied that data to a 3D primitive.</span></span>

 

 




