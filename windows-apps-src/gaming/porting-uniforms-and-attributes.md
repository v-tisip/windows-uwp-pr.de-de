---
author: mtoepke
title: Portieren von OpenGLES2.0-Puffern, -uniform-Elementen und -Scheitelpunkten zu Direct3D
description: Während des Portierens zu Direct3D 11 aus OpenGL ES 2.0 müssen Sie die Syntax und das API-Verhalten zum Übergeben von Daten zwischen der App und den Shaderprogrammen ändern.
ms.assetid: 9b215874-6549-80c5-cc70-c97b571c74fe
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, OpenGL, Direct3D, Puffer, uniform-Variablen, Vertexattribute
ms.localizationpriority: medium
ms.openlocfilehash: bc0192eb4b89ef91bc895a96e46cd39524f24c44
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7566481"
---
# <a name="compare-opengl-es-20-buffers-uniforms-and-vertex-attributes-to-direct3d"></a><span data-ttu-id="21a89-104">Vergleichen von OpenGLES2.0-Puffern, uniform-Variablen und Vertexattributen mit Direct3D</span><span class="sxs-lookup"><span data-stu-id="21a89-104">Compare OpenGL ES 2.0 buffers, uniforms, and vertex attributes to Direct3D</span></span>




**<span data-ttu-id="21a89-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="21a89-105">Important APIs</span></span>**

-   [**<span data-ttu-id="21a89-106">ID3D11Device1::CreateBuffer</span><span class="sxs-lookup"><span data-stu-id="21a89-106">ID3D11Device1::CreateBuffer</span></span>**](https://msdn.microsoft.com/library/windows/desktop/hh404575)
-   [**<span data-ttu-id="21a89-107">ID3D11Device1::CreateInputLayout</span><span class="sxs-lookup"><span data-stu-id="21a89-107">ID3D11Device1::CreateInputLayout</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476512)
-   [**<span data-ttu-id="21a89-108">ID3D11DeviceContext1::IASetInputLayout</span><span class="sxs-lookup"><span data-stu-id="21a89-108">ID3D11DeviceContext1::IASetInputLayout</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476454)

<span data-ttu-id="21a89-109">Während des Portierens zu Direct3D 11 aus OpenGL ES 2.0 müssen Sie die Syntax und das API-Verhalten zum Übergeben von Daten zwischen der App und den Shaderprogrammen ändern.</span><span class="sxs-lookup"><span data-stu-id="21a89-109">During the process of porting to Direct3D 11 from OpenGL ES 2.0, you must change the syntax and API behavior for passing data between the app and the shader programs.</span></span>

<span data-ttu-id="21a89-110">In OpenGLES2.0 werden Daten an und von Shaderprogrammen auf die folgenden Arten übergeben: als uniform-Elemente für Konstantendaten, als Attribute für Vertexdaten und als Pufferobjekte für andere Ressourcendaten (z.B. Texturen).</span><span class="sxs-lookup"><span data-stu-id="21a89-110">In OpenGL ES 2.0, data is passed to and from shader programs in four ways: as uniforms for constant data, as attributes for vertex data, as buffer objects for other resource data (such as textures).</span></span> <span data-ttu-id="21a89-111">In Direct3D11 entsprechen diese Elemente grob Konstantenpuffern, Vertexpuffern und Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="21a89-111">In Direct3D 11, these roughly map to constant buffers, vertex buffers, and subresources.</span></span> <span data-ttu-id="21a89-112">Obwohl auf den ersten Blick Ähnlichkeiten bestehen, unterscheiden sich diese Elemente in der Nutzung jedoch relativ stark.</span><span class="sxs-lookup"><span data-stu-id="21a89-112">Despite the superficial commonality, they are handled quite different in usage.</span></span>

<span data-ttu-id="21a89-113">Unten ist die grundlegende Zuordnung angegeben.</span><span class="sxs-lookup"><span data-stu-id="21a89-113">Here's the basic mapping.</span></span>

| <span data-ttu-id="21a89-114">OpenGL ES 2.0</span><span class="sxs-lookup"><span data-stu-id="21a89-114">OpenGL ES 2.0</span></span>             | <span data-ttu-id="21a89-115">Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="21a89-115">Direct3D 11</span></span>                                                                                                                                                                         |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="21a89-116">uniform-Variable</span><span class="sxs-lookup"><span data-stu-id="21a89-116">uniform</span></span>                   | <span data-ttu-id="21a89-117">Konstantenpufferfeld (**cbuffer**)</span><span class="sxs-lookup"><span data-stu-id="21a89-117">constant buffer (**cbuffer**) field.</span></span>                                                                                                                                                |
| <span data-ttu-id="21a89-118">Attribut</span><span class="sxs-lookup"><span data-stu-id="21a89-118">attribute</span></span>                 | <span data-ttu-id="21a89-119">Vertexpufferelement-Feld mit Eingabelayout und Kennzeichnung durch spezielle HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="21a89-119">vertex buffer element field, designated by an input layout and marked with a specific HLSL semantic.</span></span>                                                                                |
| <span data-ttu-id="21a89-120">buffer-Objekt</span><span class="sxs-lookup"><span data-stu-id="21a89-120">buffer object</span></span>             | <span data-ttu-id="21a89-121">Puffer; allgemeine Pufferdefinitionen unter [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) und [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)</span><span class="sxs-lookup"><span data-stu-id="21a89-121">buffer; See [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) and [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) and for a general-use buffer definitions.</span></span> |
| <span data-ttu-id="21a89-122">Framepufferobjekt (Frame Buffer Object, FBO)</span><span class="sxs-lookup"><span data-stu-id="21a89-122">frame buffer object (FBO)</span></span> | <span data-ttu-id="21a89-123">Renderziel(e); siehe [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582) mit [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)</span><span class="sxs-lookup"><span data-stu-id="21a89-123">render target(s); See [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582) with [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635).</span></span>                                       |
| <span data-ttu-id="21a89-124">Hintergrundpuffer</span><span class="sxs-lookup"><span data-stu-id="21a89-124">back buffer</span></span>               | <span data-ttu-id="21a89-125">Swapchain mit „Hintergrundpuffer“-Oberfläche; siehe [**IDXGISwapChain1**](https://msdn.microsoft.com/library/windows/desktop/hh404631) mit [**IDXGISurface1**](https://msdn.microsoft.com/library/windows/desktop/ff471343) als Anhang</span><span class="sxs-lookup"><span data-stu-id="21a89-125">swap chain with "back buffer" surface; See [**IDXGISwapChain1**](https://msdn.microsoft.com/library/windows/desktop/hh404631) with attached [**IDXGISurface1**](https://msdn.microsoft.com/library/windows/desktop/ff471343).</span></span>                       |

 

## <a name="port-buffers"></a><span data-ttu-id="21a89-126">Portieren von Puffern</span><span class="sxs-lookup"><span data-stu-id="21a89-126">Port buffers</span></span>


<span data-ttu-id="21a89-127">In OpenGL ES 2.0 wird zum Erstellen und Binden jeglicher Arten von Puffern in der Regel das folgende Muster verwendet:</span><span class="sxs-lookup"><span data-stu-id="21a89-127">In OpenGL ES 2.0, the process for creating and binding any kind of buffer generally follows this pattern</span></span>

-   <span data-ttu-id="21a89-128">Aufrufen von glGenBuffers, um einen oder mehrere Puffer zu erzeugen und dafür Handles zurückzugeben</span><span class="sxs-lookup"><span data-stu-id="21a89-128">Call glGenBuffers to generate one or more buffers and return the handles to them.</span></span>
-   <span data-ttu-id="21a89-129">Aufrufen von „glBindBuffer“, um das Layout eines Puffers zu definieren, z. B. GL\_ELEMENT\_ARRAY\_BUFFER</span><span class="sxs-lookup"><span data-stu-id="21a89-129">Call glBindBuffer to define the layout of a buffer, such as GL\_ELEMENT\_ARRAY\_BUFFER.</span></span>
-   <span data-ttu-id="21a89-130">Aufrufen von „glBufferData“, um den Puffer mit speziellen Daten (z. B. Vertexstrukturen, Indexdaten oder Farbdaten) in einem speziellen Layout aufzufüllen</span><span class="sxs-lookup"><span data-stu-id="21a89-130">Call glBufferData to populate the buffer with specific data (such as vertex structures, index data, or color data) in a specific layout.</span></span>

<span data-ttu-id="21a89-131">Der am häufigsten verwendete Puffer ist der Vertexpuffer, der jeweils mindestens die Positionen der Scheitelpunkte (Vertices) in einem Koordinatensystem enthält.</span><span class="sxs-lookup"><span data-stu-id="21a89-131">The most common kind of buffer is the vertex buffer, which minimally contains the positions of the vertices in some coordinate system.</span></span> <span data-ttu-id="21a89-132">Normalerweise wird ein Vertex mithilfe einer Struktur dargestellt, in der die Positionskoordinaten, ein Normalenvektor zur Vertexposition, ein Tangentenvektor zur Vertexposition und Koordinaten für die Textursuche (uv) enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="21a89-132">In typical use, a vertex is represented by a structure that contains the position coordinates, a normal vector to the vertex position, a tangent vector to the vertex position, and texture lookup (uv) coordinates.</span></span> <span data-ttu-id="21a89-133">Der Puffer enthält eine zusammenhängende Liste dieser Scheitelpunkte in einer bestimmten Reihenfolge (z.B. Dreiecksliste, kettenförmig oder fächerförmig), von denen zusammen die sichtbaren Polygone der Szene dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-133">The buffer contains a contiguous list of these vertices, in some order (like a triangle list, or strip, or fan), and which collectively represent the visible polygons in your scene.</span></span> <span data-ttu-id="21a89-134">(In Direct3D11 und in OpenGLES2.0 ist es ineffizient, mehrere Vertexpuffer pro Draw-Aufruf zu verwenden.)</span><span class="sxs-lookup"><span data-stu-id="21a89-134">(In Direct3D 11 as well as OpenGL ES 2.0 it is inefficient to have multiple vertex buffers per draw call.)</span></span>

<span data-ttu-id="21a89-135">Dies ist ein Beispiel für einen Vertexpuffer und einen Indexpuffer, die mit OpenGLES2.0 erstellt wurden:</span><span class="sxs-lookup"><span data-stu-id="21a89-135">Here's an example a vertex buffer and an index buffer created with OpenGL ES 2.0:</span></span>

<span data-ttu-id="21a89-136">OpenGLES2.0: Erstellen und Auffüllen eines Vertexpuffers und eines Indexpuffers</span><span class="sxs-lookup"><span data-stu-id="21a89-136">OpenGL ES 2.0: Creating and populating a vertex buffer and an index buffer.</span></span>

``` syntax
glGenBuffers(1, &renderer->vertexBuffer);
glBindBuffer(GL_ARRAY_BUFFER, renderer->vertexBuffer);
glBufferData(GL_ARRAY_BUFFER, sizeof(Vertex) * CUBE_VERTICES, renderer->vertices, GL_STATIC_DRAW);

glGenBuffers(1, &renderer->indexBuffer);
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, renderer->indexBuffer);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(int) * CUBE_INDICES, renderer->vertexIndices, GL_STATIC_DRAW);
```

<span data-ttu-id="21a89-137">Weitere Puffer sind Pixelpuffer und Zuordnungen, z.B. Texturen</span><span class="sxs-lookup"><span data-stu-id="21a89-137">Other buffers include pixel buffers and maps, like textures.</span></span> <span data-ttu-id="21a89-138">Für die Shaderpipeline ist das Rendern in Texturpuffer (pixmaps) oder das Rendern von Pufferobjekten zur Verwendung in nachfolgenden Shaderdurchläufen möglich.</span><span class="sxs-lookup"><span data-stu-id="21a89-138">The shader pipeline can render into texture buffers (pixmaps) or render buffer objects and use those buffers in future shader passes.</span></span> <span data-ttu-id="21a89-139">Im einfachsten Fall lautet der Fluss für den Aufruf wie folgt:</span><span class="sxs-lookup"><span data-stu-id="21a89-139">In the simplest case, the call flow is:</span></span>

-   <span data-ttu-id="21a89-140">Aufrufen von glGenFramebuffers zum Erzeugen eines Framepufferobjekts</span><span class="sxs-lookup"><span data-stu-id="21a89-140">Call glGenFramebuffers to generate a frame buffer object.</span></span>
-   <span data-ttu-id="21a89-141">Aufrufen von glBindFramebuffer zum Binden des Framepufferobjekts für Schreibvorgänge</span><span class="sxs-lookup"><span data-stu-id="21a89-141">Call glBindFramebuffer to bind the frame buffer object for writing.</span></span>
-   <span data-ttu-id="21a89-142">Aufrufen von glFramebufferTexture2D zum Zeichnen in eine angegebene Texturmap</span><span class="sxs-lookup"><span data-stu-id="21a89-142">Call glFramebufferTexture2D to draw into a specified texture map.</span></span>

<span data-ttu-id="21a89-143">In Direct3D 11 werden Pufferdatenelemente als „Unterressourcen“ angesehen und können von einzelnen Vertexdatenelementen bis hin zu MIP-Map-Texturen reichen.</span><span class="sxs-lookup"><span data-stu-id="21a89-143">In Direct3D 11, buffer data elements are considered "subresources," and can range from individual vertex data elements to MIP-map textures.</span></span>

-   <span data-ttu-id="21a89-144">Auffüllen einer [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur mit der Konfiguration für ein Pufferdatenelement</span><span class="sxs-lookup"><span data-stu-id="21a89-144">Populate a [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structure with the configuration for a buffer data element.</span></span>
-   <span data-ttu-id="21a89-145">Auffüllen einer [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)-Struktur mit der Größe der einzelnen Elemente im Puffer und mit dem Puffertyp</span><span class="sxs-lookup"><span data-stu-id="21a89-145">Populate a [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) structure with the size of the individual elements in the buffer as well as the buffer type.</span></span>
-   <span data-ttu-id="21a89-146">Aufrufen von [**ID3D11Device1::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/hh404575) mit diesen beiden Strukturen</span><span class="sxs-lookup"><span data-stu-id="21a89-146">Call [**ID3D11Device1::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/hh404575) with these two structures.</span></span>

<span data-ttu-id="21a89-147">Direct3D 11: Erstellen und Auffüllen eines Vertexpuffers und eines Indexpuffers</span><span class="sxs-lookup"><span data-stu-id="21a89-147">Direct3D 11: Creating and populating a vertex buffer and an index buffer.</span></span>

``` syntax
D3D11_SUBRESOURCE_DATA vertexBufferData = {0};
vertexBufferData.pSysMem = cubeVertices;
vertexBufferData.SysMemPitch = 0;
vertexBufferData.SysMemSlicePitch = 0;
CD3D11_BUFFER_DESC vertexBufferDesc(sizeof(cubeVertices), D3D11_BIND_VERTEX_BUFFER);

m_d3dDevice->CreateBuffer(
  &vertexBufferDesc,
  &vertexBufferData,
  &m_vertexBuffer);

m_indexCount = ARRAYSIZE(cubeIndices);

D3D11_SUBRESOURCE_DATA indexBufferData = {0};
indexBufferData.pSysMem = cubeIndices;
indexBufferData.SysMemPitch = 0;
indexBufferData.SysMemSlicePitch = 0;
CD3D11_BUFFER_DESC indexBufferDesc(sizeof(cubeIndices), D3D11_BIND_INDEX_BUFFER);

m_d3dDevice->CreateBuffer(
  &indexBufferDesc,
  &indexBufferData,
  &m_indexBuffer);
    
```

<span data-ttu-id="21a89-148">Beschreibbare Pixelpuffer oder Maps, z. B. ein Framepuffer, können als [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635)-Objekte erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-148">Writable pixel buffers or maps, such as a frame buffer, can be created as [**ID3D11Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff476635) objects.</span></span> <span data-ttu-id="21a89-149">Diese können als Ressourcen an eine [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582)- oder [**ID3D11ShaderResourceView**](https://msdn.microsoft.com/library/windows/desktop/ff476628)-Schnittstelle gebunden werden und nach dem Zeichnen mit der zugeordneten Swapchain angezeigt oder an einen Shader übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-149">These can be bound as resources to an [**ID3D11RenderTargetView**](https://msdn.microsoft.com/library/windows/desktop/ff476582) or [**ID3D11ShaderResourceView**](https://msdn.microsoft.com/library/windows/desktop/ff476628), which, once drawn into, can be displayed with the associated swap chain or passed to a shader, respectively.</span></span>

<span data-ttu-id="21a89-150">Direct3D11: Erstellen eines Framepufferobjekts</span><span class="sxs-lookup"><span data-stu-id="21a89-150">Direct3D 11: Creating a frame buffer object.</span></span>

``` syntax
ComPtr<ID3D11RenderTargetView> m_d3dRenderTargetViewWin;
// ...
ComPtr<ID3D11Texture2D> frameBuffer;

m_swapChainCoreWindow->GetBuffer(0, IID_PPV_ARGS(&frameBuffer));
m_d3dDevice->CreateRenderTargetView(
  frameBuffer.Get(),
  nullptr,
  &m_d3dRenderTargetViewWin);
```

## <a name="change-uniforms-and-uniform-buffer-objects-to-direct3d-constant-buffers"></a><span data-ttu-id="21a89-151">Ändern von uniform-Elementen und uniform-Pufferobjekten in Direct3D-Konstantenpuffer</span><span class="sxs-lookup"><span data-stu-id="21a89-151">Change uniforms and uniform buffer objects to Direct3D constant buffers</span></span>


<span data-ttu-id="21a89-152">In OpenGLES2.0 sind uniform-Elemente der Mechanismus zum Bereitstellen von Konstantendaten für einzelne Shaderprogramme.</span><span class="sxs-lookup"><span data-stu-id="21a89-152">In Open GL ES 2.0, uniforms are the mechanism to supply constant data to individual shader programs.</span></span> <span data-ttu-id="21a89-153">Diese Daten können von den Shadern nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-153">This data cannot be altered by the shaders.</span></span>

<span data-ttu-id="21a89-154">Zum Festlegen eines „uniform“-Elements werden normalerweise eine der „glUniform\*“-Methoden mit dem GPU-Speicherbereich für den Upload sowie ein Zeiger auf die Daten im App-Speicher angegeben.</span><span class="sxs-lookup"><span data-stu-id="21a89-154">Setting a uniform typically involves providing one of the glUniform\* methods with the upload location in the GPU along with a pointer to the data in app memory.</span></span> <span data-ttu-id="21a89-155">Nach dem Ausführen der „glUniform\*“-Methode befinden sich die „uniform“-Daten im GPU-Speicher. Von den Shadern, die dieses „uniform“-Element deklariert haben, kann darauf zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-155">After ithe glUniform\* method executes, the uniform data is in the GPU memory and accessible by the shaders that have declared that uniform.</span></span> <span data-ttu-id="21a89-156">Sie müssen sicherstellen, dass die Daten so verpackt sind, dass sie vom Shader basierend auf der uniform-Deklaration im Shader (mithilfe kompatibler Typen) interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="21a89-156">You are expected to ensure that the data is packed in such a way that the shader can interpret it based on the uniform declaration in the shader (by using compatible types).</span></span>

<span data-ttu-id="21a89-157">OpenGLES2.0: Erstellen eines uniform-Elements und Durchführen von Uploads in das Element</span><span class="sxs-lookup"><span data-stu-id="21a89-157">OpenGL ES 2.0 Creating a uniform and uploading data to it</span></span>

``` syntax
renderer->mvpLoc = glGetUniformLocation(renderer->programObject, "u_mvpMatrix");

// ...

glUniformMatrix4fv(renderer->mvpLoc, 1, GL_FALSE, (GLfloat*) &renderer->mvpMatrix.m[0][0]);
```

<span data-ttu-id="21a89-158">Im GLSL-Code eines Shaders sieht die entsprechende uniform-Deklaration wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="21a89-158">In a shader's GLSL, the corresponding uniform declaration looks like this:</span></span>

<span data-ttu-id="21a89-159">OpenGLES2.0: uniform-Deklaration für GLSL</span><span class="sxs-lookup"><span data-stu-id="21a89-159">Open GL ES 2.0: GLSL uniform declaration</span></span>

``` syntax
uniform mat4 u_mvpMatrix;
```

<span data-ttu-id="21a89-160">Unter Direct3D werden uniform-Daten als "Konstantenpuffer" bezeichnet, die – wie uniform-Elemente auch – für die einzelnen Shader bereitgestellte Konstantendaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="21a89-160">Direct3D designates uniform data as "constant buffers," which, like uniforms, contain constant data provided to individual shaders.</span></span> <span data-ttu-id="21a89-161">Genauso wie bei uniform-Puffern ist es wichtig, die Konstantenpufferdaten exakt so im Speicher zu verpacken, wie sie vom Shader für die Interpretation erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="21a89-161">As with uniform buffers, it is important to pack the constant buffer data in memory identically to the way the shader expects to interpret it.</span></span> <span data-ttu-id="21a89-162">Bei Verwendung von DirectXMath-Typen (wie [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608)) anstelle von Plattformtypen (wie **float\*** oder **float\[4\]**) ist die richtige Ausrichtung von Datenelementen sichergestellt.</span><span class="sxs-lookup"><span data-stu-id="21a89-162">Using DirectXMath types (such as [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608)) instead of platform types (such as **float\*** or **float\[4\]**) guarantees proper data element alignment.</span></span>

<span data-ttu-id="21a89-163">Konstantenpuffer müssen über ein zugeordnetes GPU-Register verfügen, mit dem für die GPU auf diese Daten verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="21a89-163">Constant buffers must have an associated GPU register used to reference that data on the GPU.</span></span> <span data-ttu-id="21a89-164">Die Daten werden im Registerbereich so verpackt, wie dies vom Layout des Puffers vorgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="21a89-164">The data is packed into the register location as indicated by the layout of the buffer.</span></span>

<span data-ttu-id="21a89-165">Direct3D11: Erstellen eines Konstantenpuffers und Durchführen des Datenuploads in den Puffer</span><span class="sxs-lookup"><span data-stu-id="21a89-165">Direct3D 11: Creating a constant buffer and uploading data to it</span></span>

``` syntax
struct ModelViewProjectionConstantBuffer
{
     DirectX::XMFLOAT4X4 mvp;
};

// ...

ModelViewProjectionConstantBuffer   m_constantBufferData;

// ...

XMStoreFloat4x4(&m_constantBufferData.mvp, mvpMatrix);

CD3D11_BUFFER_DESC constantBufferDesc(sizeof(ModelViewProjectionConstantBuffer), D3D11_BIND_CONSTANT_BUFFER);
m_d3dDevice->CreateBuffer(
  &constantBufferDesc,
  nullptr,
  &m_constantBuffer);
```

<span data-ttu-id="21a89-166">Im HLSL-Code eines Shaders sieht die entsprechende Konstantenpufferdeklaration wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="21a89-166">In a shader's HLSL, the corresponding constant buffer declaration looks like this:</span></span>

<span data-ttu-id="21a89-167">Direct3D11: Deklaration des Konstantenpuffers für HLSL</span><span class="sxs-lookup"><span data-stu-id="21a89-167">Direct3D 11: Constant buffer HLSL declaration</span></span>

``` syntax
cbuffer ModelViewProjectionConstantBuffer : register(b0)
{
  matrix mvp;
};
```

<span data-ttu-id="21a89-168">Beachten Sie, dass für jeden Konstantenpuffer ein Register deklariert werden muss.</span><span class="sxs-lookup"><span data-stu-id="21a89-168">Note that a register must be declared for each constant buffer.</span></span> <span data-ttu-id="21a89-169">Unterschiedliche Direct3D-Featureebenen verfügen über unterschiedliche Höchstgrenzen für maximal verfügbare Register. Achten Sie daher darauf, dass Sie die Höchstzahl für die niedrigste von Ihnen genutzte Featureebene einhalten.</span><span class="sxs-lookup"><span data-stu-id="21a89-169">Different Direct3D feature levels have different maximum available registers, so do not exceed the maximum number for the lowest feature level you are targeting.</span></span>

## <a name="port-vertex-attributes-to-a-direct3d-input-layouts-and-hlsl-semantics"></a><span data-ttu-id="21a89-170">Portieren von Vertexattributen zu einem Direct3D-Eingabelayout und zur HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="21a89-170">Port vertex attributes to a Direct3D input layouts and HLSL semantics</span></span>


<span data-ttu-id="21a89-171">Da Vertexdaten von der Shaderpipeline geändert werden können, müssen sie unter OpenGLES2.0 als "Attribute" angegeben werden, anstatt als "uniform-Elemente".</span><span class="sxs-lookup"><span data-stu-id="21a89-171">Since vertex data can be modified by the shader pipeline, OpenGL ES 2.0 requires that you specify them as "attributes" instead of "uniforms".</span></span> <span data-ttu-id="21a89-172">(Dies wurde in neueren Versionen von OpenGL und GLSL geändert.) Vertexspezifische Daten wie die Vertexposition, Normalen, Tangenten und Farbwerte werden für Shader als Attributwerte bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="21a89-172">(This has changed in later versions of OpenGL and GLSL.) Vertex-specific data such the vertex position, normals, tangents, and color values are supplied to the shaders as attribute values.</span></span> <span data-ttu-id="21a89-173">Diese Attributwerte entsprechen speziellen Versatzwerten für die einzelnen Elemente in den Vertexdaten. Beispielsweise kann das erste Attribut auf die Positionskomponente eines einzelnen Vertex zeigen, das zweite Attribut auf die Normale usw.</span><span class="sxs-lookup"><span data-stu-id="21a89-173">These attribute values correspond to specific offsets for each element in the vertex data; for example, the first attribute could point to the position component of an individual vertex, and the second to the normal, and so on.</span></span>

<span data-ttu-id="21a89-174">Der grundlegende Prozess zum Verschieben der Vertexpufferdaten aus dem Hauptspeicher in die GPU lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="21a89-174">The basic process for moving the vertex buffer data from main memory to the GPU looks like this:</span></span>

-   <span data-ttu-id="21a89-175">Hochladen der Vertexdaten mit glBindBuffer</span><span class="sxs-lookup"><span data-stu-id="21a89-175">Upload the vertex data with glBindBuffer.</span></span>
-   <span data-ttu-id="21a89-176">Abrufen des Bereichs der Attribute in der GPU mit „glGetAttribLocation“</span><span class="sxs-lookup"><span data-stu-id="21a89-176">Get the location of the attributes on the GPU with glGetAttribLocation.</span></span> <span data-ttu-id="21a89-177">Aufrufen für jedes Attribut im Vertexdatenelement</span><span class="sxs-lookup"><span data-stu-id="21a89-177">Call it for each attribute in the vertex data element.</span></span>
-   <span data-ttu-id="21a89-178">Aufrufen von glVertexAttribPointer zum Festlegen der richtigen Attributgröße und des Versatzes innerhalb eines einzelnen Vertexdatenelements;</span><span class="sxs-lookup"><span data-stu-id="21a89-178">Call glVertexAttribPointer to provide set the correct attribute size and offset inside an individual vertex data element.</span></span> <span data-ttu-id="21a89-179">Durchführen dieses Schritts für jedes Attribut</span><span class="sxs-lookup"><span data-stu-id="21a89-179">Do this for each attribute.</span></span>
-   <span data-ttu-id="21a89-180">Aktivieren der Informationen zum Vertexdatenlayout mit glEnableVertexAttribArray</span><span class="sxs-lookup"><span data-stu-id="21a89-180">Enable the vertex data layout information with glEnableVertexAttribArray.</span></span>

<span data-ttu-id="21a89-181">OpenGLES2.0: Hochladen von Vertexpufferdaten in das Shaderattribut</span><span class="sxs-lookup"><span data-stu-id="21a89-181">OpenGL ES 2.0: Uploading vertex buffer data to the shader attribute</span></span>

``` syntax
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, renderer->vertexBuffer);
loc = glGetAttribLocation(renderer->programObject, "a_position");

glVertexAttribPointer(loc, 3, GL_FLOAT, GL_FALSE, 
  sizeof(Vertex), 0);
loc = glGetAttribLocation(renderer->programObject, "a_color");
glEnableVertexAttribArray(loc);

glVertexAttribPointer(loc, 4, GL_FLOAT, GL_FALSE, 
  sizeof(Vertex), (GLvoid*) (sizeof(float) * 3));
glEnableVertexAttribArray(loc);
```

<span data-ttu-id="21a89-182">Im Vertex-Shader deklarieren Sie Attribute unter den gleichen Namen, die Sie im Aufruf von glGetAttribLocation deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="21a89-182">Now, in your vertex shader, you declare attributes with the same names you defined in your call to glGetAttribLocation.</span></span>

<span data-ttu-id="21a89-183">OpenGLES2.0: Deklarieren eines Attributs in GLSL</span><span class="sxs-lookup"><span data-stu-id="21a89-183">OpenGL ES 2.0: Declaring an attribute in GLSL</span></span>

``` syntax
attribute vec4 a_position;
attribute vec4 a_color;                     
```

<span data-ttu-id="21a89-184">Teilweise gilt für Direct3D der gleiche Prozess.</span><span class="sxs-lookup"><span data-stu-id="21a89-184">In some ways, the same process holds for Direct3D.</span></span> <span data-ttu-id="21a89-185">Anstelle von Attributen werden Vertexdaten in Eingabepuffern bereitgestellt. Dazu gehören auch Vertexpuffer und die entsprechenden Indexpuffer.</span><span class="sxs-lookup"><span data-stu-id="21a89-185">Instead of a attributes, vertex data is provided in input buffers, which include vertex buffers and the corresponding index buffers.</span></span> <span data-ttu-id="21a89-186">Da Direct3D nicht über die "Attributdeklaration" verfügt, müssen Sie ein Eingabelayout angeben. Damit werden die individuelle Komponente der Datenelemente im Vertexpuffer und die HLSL-Semantik deklariert, mit der angegeben wird, wo und wie diese Komponenten vom Vertex-Shader interpretiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="21a89-186">However, since Direct3D does not have the "attribute" declaration, you must specify an input layout which declares the individual component of the data elements in the vertex buffer and the HLSL semantics that indicate where and how those components are to be interpreted by the vertex shader.</span></span> <span data-ttu-id="21a89-187">Für die HLSL-Semantik ist es erforderlich, die Nutzung der einzelnen Komponenten mit einer speziellen Zeichenfolge zu definieren, über die das Shadermodul über ihren Zweck informiert wird.</span><span class="sxs-lookup"><span data-stu-id="21a89-187">HLSL semantics require that you define the usage of each component with a specific string that informs the shader engine as to its purpose.</span></span> <span data-ttu-id="21a89-188">Beispielsweise werden Vertexpositionsdaten als POSITION, Normalendaten als NORMAL und Vertexfarbdaten als COLOR gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="21a89-188">For example, vertex position data is marked as POSITION, normal data is marked as NORMAL, and vertex color data is marked as COLOR.</span></span> <span data-ttu-id="21a89-189">(Andere Shaderphasen erfordern auch jeweils eine spezielle Semantik. Diese Semantiken verfügen basierend auf der Shaderphase über unterschiedliche Interpretationen.). Weitere Informationen zur HLSL-Semantik finden Sie unter [Portieren der Shaderpipeline](change-your-shader-loading-code.md) und [HLSL-Semantik](https://msdn.microsoft.com/library/windows/desktop/bb205574).</span><span class="sxs-lookup"><span data-stu-id="21a89-189">(Other shader stages also require specific semantics, and those semantics have different interpretations based on the shader stage.) For more info on HLSL semantics, read [Port your shader pipeline](change-your-shader-loading-code.md) and [HLSL Semantics](https://msdn.microsoft.com/library/windows/desktop/bb205574).</span></span>

<span data-ttu-id="21a89-190">Der Prozess zum Festlegen der Vertex- und Indexpuffer und das Festlegen des Eingabelayouts wird zusammenfassend als "Eingabeassembly"-Phase (Input Assembly, IA) der Direct3D-Grafikpipeline bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="21a89-190">Collectively, the process of setting the vertex and index buffers, and setting the input layout is called the "Input Assembly" (IA) stage of the Direct3D graphics pipeline.</span></span>

<span data-ttu-id="21a89-191">Direct3D11: Konfigurieren der Eingabeassembly-Phase</span><span class="sxs-lookup"><span data-stu-id="21a89-191">Direct3D 11: Configuring the input assembly stage</span></span>

``` syntax
// Set up the IA stage corresponding to the current draw operation.
UINT stride = sizeof(VertexPositionColor);
UINT offset = 0;
m_d3dContext->IASetVertexBuffers(
        0,
        1,
        m_vertexBuffer.GetAddressOf(),
        &stride,
        &offset);

m_d3dContext->IASetIndexBuffer(
        m_indexBuffer.Get(),
        DXGI_FORMAT_R16_UINT,
        0);

m_d3dContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
m_d3dContext->IASetInputLayout(m_inputLayout.Get());
```

<span data-ttu-id="21a89-192">Ein Eingabelayout wird deklariert, und es wird ein Vertex-Shader zugeordnet, indem das Format des Vertexdatenelements und die für die einzelnen Komponenten zu verwendende Semantik deklariert wird.</span><span class="sxs-lookup"><span data-stu-id="21a89-192">An input layout is declared and associated with a vertex shader by declaring the format of the vertex data element and the semantic used for each component.</span></span> <span data-ttu-id="21a89-193">Das von Ihnen erstellte Vertexelement-Datenlayout, das unter D3D11\_INPUT\_ELEMENT\_DESC beschrieben wird, muss dem Layout der jeweiligen Struktur entsprechen.</span><span class="sxs-lookup"><span data-stu-id="21a89-193">The vertex element data layout described in the D3D11\_INPUT\_ELEMENT\_DESC you create must correspond to the layout of the corresponding structure.</span></span> <span data-ttu-id="21a89-194">Hier erstellen Sie ein Layout für Vertexdaten, die über zwei Komponenten verfügen:</span><span class="sxs-lookup"><span data-stu-id="21a89-194">Here, you create a layout for vertex data that has two components:</span></span>

-   <span data-ttu-id="21a89-195">Eine Vertexpositionskoordinate, die im Hauptspeicher als XMFLOAT3 dargestellt wird und bei der es sich um ein ausgerichtetes Array mit drei 32-Bit-Gleitkommawerten für die Koordinaten (x, y, z) handelt.</span><span class="sxs-lookup"><span data-stu-id="21a89-195">A vertex position coordinate, represented in main memory as an XMFLOAT3, which is an aligned array of 3 32-bit floating point values for the (x, y, z) coordinates.</span></span>
-   <span data-ttu-id="21a89-196">Ein Vertexfarbwert, der als XMFLOAT4 dargestellt wird und bei dem es sich um ein ausgerichtetes Array mit vier 32-Bit-Gleitkommawerten für die Farbe (RGBA) handelt.</span><span class="sxs-lookup"><span data-stu-id="21a89-196">A vertex color value, represented as an XMFLOAT4, which is an aligned array of 4 32-bit floating point values for the color (RGBA).</span></span>

<span data-ttu-id="21a89-197">Sie weisen jeweils eine Semantik und einen Formattyp zu.</span><span class="sxs-lookup"><span data-stu-id="21a89-197">You assign a semantic for each one, as well as a format type.</span></span> <span data-ttu-id="21a89-198">Anschließend übergeben Sie die Beschreibung an [**ID3D11Device1::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512).</span><span class="sxs-lookup"><span data-stu-id="21a89-198">You then pass the description to [**ID3D11Device1::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512).</span></span> <span data-ttu-id="21a89-199">Das Eingabelayout wird beim Aufrufen von [**ID3D11DeviceContext1::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) verwendet, wenn Sie während der Rendermethode die Eingabeassembly einrichten.</span><span class="sxs-lookup"><span data-stu-id="21a89-199">The input layout is used when we call [**ID3D11DeviceContext1::IASetInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476454) when you set up the input assembly during our render method.</span></span>

<span data-ttu-id="21a89-200">Direct3D11: Beschreiben eines Eingabelayouts mit spezieller Semantik</span><span class="sxs-lookup"><span data-stu-id="21a89-200">Direct3D 11: Describing an input layout with specific semantics</span></span>

``` syntax
ComPtr<ID3D11InputLayout> m_inputLayout;

// ...

const D3D11_INPUT_ELEMENT_DESC vertexDesc[] = 
{
  { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 0,  D3D11_INPUT_PER_VERTEX_DATA, 0 },
  { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};

m_d3dDevice->CreateInputLayout(
  vertexDesc,
  ARRAYSIZE(vertexDesc),
  fileData->Data,
  fileData->Length,
  &m_inputLayout);

// ...
// When we start the drawing process...

m_d3dContext->IASetInputLayout(m_inputLayout.Get());
```

<span data-ttu-id="21a89-201">Stellen Sie im letzten Schritt sicher, dass die Eingabedaten vom Shader verstanden werden, indem Sie die Eingabe deklarieren.</span><span class="sxs-lookup"><span data-stu-id="21a89-201">Finally, you make sure that the shader can understand the input data by declaring the input.</span></span> <span data-ttu-id="21a89-202">Die im Layout zugewiesene Semantik wird verwendet, um im GPU-Speicher die richtigen Bereiche auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="21a89-202">The semantics you assigned in the layout are used to select the correct locations in GPU memory.</span></span>

<span data-ttu-id="21a89-203">Direct3D11: Deklarieren von Daten für die Shadereingabe mit HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="21a89-203">Direct3D 11: Declaring shader input data with HLSL semantics</span></span>

``` syntax
struct VertexShaderInput
{
  float3 pos : POSITION;
  float3 color : COLOR;
};
```

 

 




