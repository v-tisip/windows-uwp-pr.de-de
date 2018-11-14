---
author: mtoepke
title: Portieren der Vertexpuffer und -daten
description: In diesem Schritt definieren Sie die Vertexpuffer für die Gitter und die Indexpuffer, mit deren Hilfe die Shader die Scheitelpunkte (Vertices) in einer angegebenen Reihenfolge durchlaufen können.
ms.assetid: 9a8138a5-0797-8532-6c00-58b907197a25
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Portieren, Vertexpuffer, Daten, Direct3D
ms.localizationpriority: medium
ms.openlocfilehash: b32747a4e11d258f71d4e55e41b7f54bb5e99246
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6183082"
---
# <a name="port-the-vertex-buffers-and-data"></a><span data-ttu-id="80857-104">Portieren der Vertexpuffer und -Daten</span><span class="sxs-lookup"><span data-stu-id="80857-104">Port the vertex buffers and data</span></span>




**<span data-ttu-id="80857-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="80857-105">Important APIs</span></span>**

-   [**<span data-ttu-id="80857-106">ID3DDevice::CreateBuffer</span><span class="sxs-lookup"><span data-stu-id="80857-106">ID3DDevice::CreateBuffer</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476501)
-   [**<span data-ttu-id="80857-107">ID3DDeviceContext::IASetVertexBuffers</span><span class="sxs-lookup"><span data-stu-id="80857-107">ID3DDeviceContext::IASetVertexBuffers</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476456)
-   [**<span data-ttu-id="80857-108">ID3D11DeviceContext::IASetIndexBuffer</span><span class="sxs-lookup"><span data-stu-id="80857-108">ID3D11DeviceContext::IASetIndexBuffer</span></span>**](https://msdn.microsoft.com/library/windows/desktop/bb173588)

<span data-ttu-id="80857-109">In diesem Schritt definieren Sie die Vertexpuffer für die Gitter und die Indexpuffer, mit deren Hilfe die Shader die Scheitelpunkte (Vertices) in einer angegebenen Reihenfolge durchlaufen können.</span><span class="sxs-lookup"><span data-stu-id="80857-109">In this step, you'll define the vertex buffers that will contain your meshes and the index buffers that allow the shaders to traverse the vertices in a specified order.</span></span>

<span data-ttu-id="80857-110">Zuerst untersuchen wir das hartcodierte Modell für das Würfelgitter, das verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="80857-110">At this point, let's examine the hardcoded model for the cube mesh we are using.</span></span> <span data-ttu-id="80857-111">Für beide Darstellungen wurden die Scheitelpunkte in Form einer Dreiecksliste organisiert (im Gegensatz zu einer Kette oder einem anderen effizienteren Dreieckslayout).</span><span class="sxs-lookup"><span data-stu-id="80857-111">Both representations have the vertices organized as a triangle list (as opposed to a strip or other more efficient triangle layout).</span></span> <span data-ttu-id="80857-112">Alle Scheitelpunkte in beiden Darstellungen verfügen außerdem über zugeordnete Indizes und Farbwerte.</span><span class="sxs-lookup"><span data-stu-id="80857-112">All vertices in both representations also have associated indices and color values.</span></span> <span data-ttu-id="80857-113">Ein Großteil des Direct3D-Codes in diesem Thema bezieht sich auf Variablen und Objekte, die im Direct3D-Projekt definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="80857-113">Much of the Direct3D code in this topic refers to variables and objects defined in the Direct3D project.</span></span>

<span data-ttu-id="80857-114">Dies ist der Würfel für die Verarbeitung mit OpenGLES2.0.</span><span class="sxs-lookup"><span data-stu-id="80857-114">Here's the cube for processing by OpenGL ES 2.0.</span></span> <span data-ttu-id="80857-115">In der Beispielimplementierung besteht jeder Scheitelpunkt (Vertex) aus sieben Gleitkommawerten: drei Positionskoordinaten gefolgt von vier RGBA-Farbwerten.</span><span class="sxs-lookup"><span data-stu-id="80857-115">In the sample implementation, each vertex is 7 float values: 3 position coordinates followed by 4 RGBA color values.</span></span>

```cpp
#define CUBE_INDICES 36
#define CUBE_VERTICES 8

GLfloat cubeVertsAndColors[] = 
{
  -0.5f, -0.5f,  0.5f, 0.0f, 0.0f, 1.0f, 1.0f,
  -0.5f, -0.5f, -0.5f, 0.0f, 0.0f, 0.0f, 1.0f,
  -0.5f,  0.5f,  0.5f, 0.0f, 1.0f, 1.0f, 1.0f,
  -0.5f,  0.5f, -0.5f, 0.0f, 1.0f, 0.0f, 1.0f,
  0.5f, -0.5f,  0.5f, 1.0f, 0.0f, 1.0f, 1.0f,
  0.5f, -0.5f, -0.5f, 1.0f, 0.0f, 0.0f, 1.0f,  
  0.5f,  0.5f,  0.5f, 1.0f, 1.0f, 1.0f, 1.0f,
  0.5f,  0.5f, -0.5f, 1.0f, 1.0f, 0.0f, 1.0f
};

GLuint cubeIndices[] = 
{
  0, 1, 2, // -x
  1, 3, 2,

  4, 6, 5, // +x
  6, 7, 5,

  0, 5, 1, // -y
  5, 6, 1,

  2, 6, 3, // +y
  6, 7, 3,

  0, 4, 2, // +z
  4, 6, 2,

  1, 7, 3, // -z
  5, 7, 1
};
```

<span data-ttu-id="80857-116">Dies ist der gleiche Würfel für die Verarbeitung mit Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="80857-116">And here's the same cube for processing by Direct3D 11.</span></span>

```cpp
VertexPositionColor cubeVerticesAndColors[] = 
// struct format is position, color
{
  {XMFLOAT3(-0.5f, -0.5f, -0.5f), XMFLOAT3(0.0f, 0.0f, 0.0f)},
  {XMFLOAT3(-0.5f, -0.5f,  0.5f), XMFLOAT3(0.0f, 0.0f, 1.0f)},
  {XMFLOAT3(-0.5f,  0.5f, -0.5f), XMFLOAT3(0.0f, 1.0f, 0.0f)},
  {XMFLOAT3(-0.5f,  0.5f,  0.5f), XMFLOAT3(0.0f, 1.0f, 1.0f)},
  {XMFLOAT3( 0.5f, -0.5f, -0.5f), XMFLOAT3(1.0f, 0.0f, 0.0f)},
  {XMFLOAT3( 0.5f, -0.5f,  0.5f), XMFLOAT3(1.0f, 0.0f, 1.0f)},
  {XMFLOAT3( 0.5f,  0.5f, -0.5f), XMFLOAT3(1.0f, 1.0f, 0.0f)},
  {XMFLOAT3( 0.5f,  0.5f,  0.5f), XMFLOAT3(1.0f, 1.0f, 1.0f)},
};
        
unsigned short cubeIndices[] = 
{
  0, 2, 1, // -x
  1, 2, 3,

  4, 5, 6, // +x
  5, 7, 6,

  0, 1, 5, // -y
  0, 5, 4,

  2, 6, 7, // +y
  2, 7, 3,

  0, 4, 6, // -z
  0, 6, 2,

  1, 3, 7, // +z
  1, 7, 5
};
```

<span data-ttu-id="80857-117">Es ist erkennbar, dass der Würfel im OpenGLES2.0-Code in einem "rechtshändigen" Koordinatensystem dargestellt wird, während der Würfel im Direct3D-spezifischen Code in einem "linkshändigen" Koordinatensystem dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="80857-117">Reviewing this code, you notice that the cube in the OpenGL ES 2.0 code is represented in a right-hand coordinate system, whereas the cube in the Direct3D-specific code is represented in a left-hand coordinate system.</span></span> <span data-ttu-id="80857-118">Beim Importieren Ihrer eigenen Gitterdaten müssen Sie die Koordinaten der z-Achse für Ihr Modell umkehren und die Indizes für die einzelnen Gitter entsprechend ändern, um die Dreiecke gemäß der Änderung im Koordinatensystem zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="80857-118">When importing your own mesh data, you must reverse the z-axis coordinates for your model and change the indices for each mesh accordingly to traverse the triangles according to the change in the coordinate system.</span></span>

<span data-ttu-id="80857-119">Wir setzen voraus, dass das Verschieben des Würfelgitters aus dem rechtshändigen OpenGL ES 2.0-Koordinatensystem in das linkshändige Direct3D-Koordinatensystem erfolgreich war. Als Nächstes sehen wir uns an, wie die Würfeldaten für die Verarbeitung in beiden Modellen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="80857-119">Assuming that we have successfully moved the cube mesh from the right-handed OpenGL ES 2.0 coordinate system to the left-handed Direct3D one, let's see how to load the cube data for processing in both models.</span></span>

## <a name="instructions"></a><span data-ttu-id="80857-120">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="80857-120">Instructions</span></span>

### <a name="step-1-create-an-input-layout"></a><span data-ttu-id="80857-121">Schritt 1: Erstellen eines Eingabelayouts</span><span class="sxs-lookup"><span data-stu-id="80857-121">Step 1: Create an input layout</span></span>

<span data-ttu-id="80857-122">In OpenGL ES 2.0 werden die Vertexdaten als Attribute angegeben, die für die Shaderobjekte bereitgestellt und von diesen gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="80857-122">In OpenGL ES 2.0, your vertex data is supplied as attributes that will be supplied to and read by the shader objects.</span></span> <span data-ttu-id="80857-123">Normalerweise geben Sie eine Zeichenfolge, die den im GLSL-Code des Shaders verwendeten Attributnamen enthält, für das Shaderprogrammobjekt an und erhalten einen Speicherbereich zurück, den Sie für den Shader bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="80857-123">You typically provide a string that contains the attribute name used in the shader's GLSL to the shader program object, and get a memory location back that you can supply to the shader.</span></span> <span data-ttu-id="80857-124">In diesem Beispiel enthält ein Vertexpufferobjekt eine Liste mit benutzerdefinierten Vertexstrukturen, die wie folgt definiert und formatiert sind:</span><span class="sxs-lookup"><span data-stu-id="80857-124">In this example, a vertex buffer object contains a list of custom Vertex structures, defined and formatted as follows:</span></span>

<span data-ttu-id="80857-125">OpenGLES2.0: Konfigurieren der Attribute, in denen die Informationen pro Vertex enthalten sind</span><span class="sxs-lookup"><span data-stu-id="80857-125">OpenGL ES 2.0: Configure the attributes that contain the per-vertex information.</span></span>

``` syntax
typedef struct 
{
  GLfloat pos[3];        
  GLfloat rgba[4];
} Vertex;
```

<span data-ttu-id="80857-126">In OpenGL ES 2.0 gelten Eingabelayouts implizit. Sie verwenden eine normale GL\_ELEMENT\_ARRAY\_BUFFER-Struktur und geben die Breite und den Versatz an, damit der Vertex-Shader die Daten nach dem Hochladen interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="80857-126">In OpenGL ES 2.0, input layouts are implicit; you take a general purpose GL\_ELEMENT\_ARRAY\_BUFFER and supply the stride and offset such that the vertex shader can interpret the data after uploading it.</span></span> <span data-ttu-id="80857-127">Sie informieren den Shader mithilfe von **glVertexAttribPointer**, bevor gerendert wird, welche Attribute welchen Teilen der einzelnen Vertexdatenblöcke zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="80857-127">You inform the shader before rendering which attributes map to which portions of each block of vertex data with **glVertexAttribPointer**.</span></span>

<span data-ttu-id="80857-128">In Direct3D müssen Sie beim Erstellen des Puffers ein Eingabelayout angeben, um die Struktur der Vertexdaten im Vertexpuffer zu beschreiben, und nicht vor dem Zeichnen der Geometrie.</span><span class="sxs-lookup"><span data-stu-id="80857-128">In Direct3D, you must provide an input layout to describe the structure of the vertex data in the vertex buffer when you create the buffer, instead of before you draw the geometry.</span></span> <span data-ttu-id="80857-129">Dazu verwenden Sie ein Eingabelayout, das dem Layout der Daten für die einzelnen Scheitelpunkte im Speicher entspricht.</span><span class="sxs-lookup"><span data-stu-id="80857-129">To do this, you use an input layout which corresponds to layout of the data for our individual vertices in memory.</span></span> <span data-ttu-id="80857-130">Es ist sehr wichtig, dies genau anzugeben!</span><span class="sxs-lookup"><span data-stu-id="80857-130">It is very important to specify this accurately!</span></span>

<span data-ttu-id="80857-131">Hier erstellen Sie eine Eingabebeschreibung als Array mit [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180)-Strukturen.</span><span class="sxs-lookup"><span data-stu-id="80857-131">Here, you create an input description as an array of [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180) structures.</span></span>

<span data-ttu-id="80857-132">Direct3D: Definieren der Beschreibung eines Eingabelayouts</span><span class="sxs-lookup"><span data-stu-id="80857-132">Direct3D: Define an input layout description.</span></span>

``` syntax
struct VertexPositionColor
{
  DirectX::XMFLOAT3 pos;
  DirectX::XMFLOAT3 color;
};

// ...

const D3D11_INPUT_ELEMENT_DESC vertexDesc[] = 
{
  { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 0,  D3D11_INPUT_PER_VERTEX_DATA, 0 },
  { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};

```

<span data-ttu-id="80857-133">Mit dieser Eingabebeschreibung wird ein Vertex als ein Vektorpaar mit jeweils dreiKoordinaten definiert: ein 3D-Vektor zum Speichern der Vertexposition in den Modellkoordinaten und ein anderer 3D-Vektor zum Speichern des RGB-Farbwerts, der dem Vertex zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="80857-133">This input description defines a vertex as a pair of 2 3-coordinate vectors: one 3D vector to store the position of the vertex in model coordinates, and another 3D vector to store the RGB color value associated with the vertex.</span></span> <span data-ttu-id="80857-134">In diesem Fall verwenden Sie das 3x32-Bit-Gleitkommaformat. Elemente dieses Typs sind im Code als `XMFLOAT3(X.Xf, X.Xf, X.Xf)` dargestellt.</span><span class="sxs-lookup"><span data-stu-id="80857-134">In this case, you use 3x32 bit floating point format, elements of which we represent in code as `XMFLOAT3(X.Xf, X.Xf, X.Xf)`.</span></span> <span data-ttu-id="80857-135">Sie sollten Typen aus der [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/ee415574)-Bibliothek immer bei der Behandlung von Daten verwenden, die von einem Shader genutzt werden. So wird die richtige Verpackung und Ausrichtung der Daten sichergestellt.</span><span class="sxs-lookup"><span data-stu-id="80857-135">You should use types from the [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/ee415574) library whenever you are handling data that will be used by a shader, as it ensure the proper packing and alignment of that data.</span></span> <span data-ttu-id="80857-136">(Verwenden Sie beispielsweise [**XMFLOAT3**](https://msdn.microsoft.com/library/windows/desktop/ee419475) oder [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) für Vektordaten und [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) für Matrizen.)</span><span class="sxs-lookup"><span data-stu-id="80857-136">(For example, use [**XMFLOAT3**](https://msdn.microsoft.com/library/windows/desktop/ee419475) or [**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) for vector data, and [**XMFLOAT4X4**](https://msdn.microsoft.com/library/windows/desktop/ee419621) for matrices.)</span></span>

<span data-ttu-id="80857-137">Eine Liste aller möglichen Formattypen finden Sie unter [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059).</span><span class="sxs-lookup"><span data-stu-id="80857-137">For a list of all the possible format types, refer to [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059).</span></span>

<span data-ttu-id="80857-138">Nachdem das Layout für die Eingabe pro Vertex definiert wurde, erstellen Sie das Layoutobjekt.</span><span class="sxs-lookup"><span data-stu-id="80857-138">With the per-vertex input layout defined, you create the layout object.</span></span> <span data-ttu-id="80857-139">Im folgenden Code schreiben Sie es in **m\_inputLayout**, eine Variable vom Typ **ComPtr** (die auf ein Objekt vom Typ [**ID3D11InputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476575) verweist).</span><span class="sxs-lookup"><span data-stu-id="80857-139">In the following code, you write it to **m\_inputLayout**, a variable of type **ComPtr** (which points to an object of type [**ID3D11InputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476575)).</span></span> <span data-ttu-id="80857-140">**fileData** enthält das kompilierte Vertexshaderobjekt aus dem vorherigen Schritt [Portieren der Shader](port-the-shader-config.md).</span><span class="sxs-lookup"><span data-stu-id="80857-140">**fileData** contains the compiled vertex shader object from the previous step, [Port the shaders](port-the-shader-config.md).</span></span>

<span data-ttu-id="80857-141">Direct3D: Erstellen des vom Vertexpuffer verwendeten Eingabelayouts</span><span class="sxs-lookup"><span data-stu-id="80857-141">Direct3D: Create the input layout used by the vertex buffer.</span></span>

``` syntax
Microsoft::WRL::ComPtr<ID3D11InputLayout>      m_inputLayout;

// ...

m_d3dDevice->CreateInputLayout(
  vertexDesc,
  ARRAYSIZE(vertexDesc),
  fileData->Data,
  fileShaderData->Length,
  &m_inputLayout
);
```

<span data-ttu-id="80857-142">Wir haben das Eingabelayout definiert.</span><span class="sxs-lookup"><span data-stu-id="80857-142">We've defined the input layout.</span></span> <span data-ttu-id="80857-143">Als Nächstes erstellen wir einen Puffer, der dieses Layout nutzt, und laden die Daten des Würfelgitters in den Puffer.</span><span class="sxs-lookup"><span data-stu-id="80857-143">Now, let's create a buffer that uses this layout and load it with the cube mesh data.</span></span>

### <a name="step-2-create-and-load-the-vertex-buffers"></a><span data-ttu-id="80857-144">Schritt 2: Erstellen und Laden der Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="80857-144">Step 2: Create and load the vertex buffer(s)</span></span>

<span data-ttu-id="80857-145">Erstellen Sie in OpenGL ES 2.0 ein Pufferpaar: einen für die Positionsdaten und einen für die Farbdaten.</span><span class="sxs-lookup"><span data-stu-id="80857-145">In OpenGL ES 2.0, you create a pair of buffers, one for the position data and one for the color data.</span></span> <span data-ttu-id="80857-146">(Sie können auch eine Struktur erstellen, die beide zusammen mit einem einzelnen Puffer enthält.) Binden Sie jeden der Puffer sowie die Schreibposition und die Farbdaten darin ein.</span><span class="sxs-lookup"><span data-stu-id="80857-146">(You could also create a struct that contains both and a single buffer.) You bind each buffer and write position and color data into them.</span></span> <span data-ttu-id="80857-147">Später während der Renderfunktion binden Sie die Puffer erneut und stellen das Format der Daten im Puffer für den Shader bereit, damit diese richtig interpretiert werden können.</span><span class="sxs-lookup"><span data-stu-id="80857-147">Later, during your render function, bind the buffers again and provide the shader with the format of the data in the buffer so it can correctly interpret it.</span></span>

<span data-ttu-id="80857-148">OpenGLES2.0: Binden der Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="80857-148">OpenGL ES 2.0: Bind the vertex buffers</span></span>

``` syntax
// upload the data for the vertex position buffer
glGenBuffers(1, &renderer->vertexBuffer);    
glBindBuffer(GL_ARRAY_BUFFER, renderer->vertexBuffer);
glBufferData(GL_ARRAY_BUFFER, sizeof(VERTEX) * CUBE_VERTICES, renderer->vertices, GL_STATIC_DRAW);   
```

<span data-ttu-id="80857-149">In Direct3D werden von Shadern aufrufbare Puffer als [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Strukturen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="80857-149">In Direct3D, shader-accessible buffers are represented as [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structures.</span></span> <span data-ttu-id="80857-150">Zum Binden dieses Puffers an ein Shaderobjekt erstellen Sie mit [**ID3DDevice::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) eine CD3D11\_BUFFER\_DESC-Struktur für jeden Puffer. Legen Sie anschließend den Puffer des Direct3D-Gerätekontexts fest, indem Sie eine für den Puffertyp spezifische set-Methode wie [**ID3DDeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="80857-150">To bind the location of this buffer to shader object, you need to create a CD3D11\_BUFFER\_DESC structure for each buffer with [**ID3DDevice::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501), and then set the buffer of the Direct3D device context by calling a set method specific to the buffer type, such as [**ID3DDeviceContext::IASetVertexBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff476456).</span></span>

<span data-ttu-id="80857-151">Geben Sie beim Festlegen des Puffers die Breite (die Größe des Datenelements für einen einzelnen Vertex) sowie den Versatz (wo die eigentlichen Vertexdaten beginnen) zum Anfang des Puffers an.</span><span class="sxs-lookup"><span data-stu-id="80857-151">When you set the buffer, you must set the stride (the size of the data element for an individual vertex) as well the offset (where the vertex data array actually starts) from the beginning of the buffer.</span></span>

<span data-ttu-id="80857-152">Beachten Sie, dass der Zeiger auf das **vertexIndices**-Array dem **pSysMem**-Feld der [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="80857-152">Notice that we assign the pointer to the **vertexIndices** array to the **pSysMem** field of the [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structure.</span></span> <span data-ttu-id="80857-153">Wenn dies nicht korrekt angegeben wird, ist das Gitter beschädigt oder leer!</span><span class="sxs-lookup"><span data-stu-id="80857-153">If this isn't correct, your mesh will be corrupt or empty!</span></span>

<span data-ttu-id="80857-154">Direct3D: Erstellen und Festlegen des Vertexpuffers</span><span class="sxs-lookup"><span data-stu-id="80857-154">Direct3D: Create and set the vertex buffer</span></span>

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
        
// ...

UINT stride = sizeof(VertexPositionColor);
UINT offset = 0;
m_d3dContext->IASetVertexBuffers(
  0,
  1,
  m_vertexBuffer.GetAddressOf(),
  &stride,
  &offset);
```

### <a name="step-3-create-and-load-the-index-buffer"></a><span data-ttu-id="80857-155">Schritt 3: Erstellen und Laden des Indexpuffers</span><span class="sxs-lookup"><span data-stu-id="80857-155">Step 3: Create and load the index buffer</span></span>

<span data-ttu-id="80857-156">Indexpuffer stellen eine effiziente Möglichkeit dar, für den Vertex-Shader das Suchen nach einzelnen Scheitelpunkten (Vertices) zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="80857-156">Index buffers are an efficient way to allow the vertex shader to look up individual vertices.</span></span> <span data-ttu-id="80857-157">Obwohl sie nicht zwingend erforderlich sind, werden sie in diesem Beispielrenderer verwendet.</span><span class="sxs-lookup"><span data-stu-id="80857-157">Although they are not required, we use them in this sample renderer.</span></span> <span data-ttu-id="80857-158">Wie bei Vertexpuffern in OpenGLES2.0 auch, wird ein Indexpuffer erstellt und als allgemeiner Puffer gebunden. Anschließend werden die bereits erstellten Indizes in den Puffer kopiert.</span><span class="sxs-lookup"><span data-stu-id="80857-158">As with vertex buffers in OpenGL ES 2.0, an index buffer is created and bound as a general purpose buffer and the vertex indices you created earlier are copied into it.</span></span>

<span data-ttu-id="80857-159">Wenn Sie bereit zum Zeichnen sind, binden Sie sowohl den Vertexpuffer als auch den Indexpuffer erneut und rufen **glDrawElements** auf.</span><span class="sxs-lookup"><span data-stu-id="80857-159">When you're ready to draw, you bind both the vertex and the index buffer again, and call **glDrawElements**.</span></span>

<span data-ttu-id="80857-160">OpenGL ES 2.0: Senden der Indexreihenfolge an den Draw-Aufruf</span><span class="sxs-lookup"><span data-stu-id="80857-160">OpenGL ES 2.0: Send the index order to the draw call.</span></span>

``` syntax
GLuint indexBuffer;

// ...

glGenBuffers(1, &renderer->indexBuffer);    
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, renderer->indexBuffer);   
glBufferData(GL_ELEMENT_ARRAY_BUFFER, 
  sizeof(GLuint) * CUBE_INDICES, 
  renderer->vertexIndices, 
  GL_STATIC_DRAW);

// ...
// Drawing function

// Bind the index buffer
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, renderer->indexBuffer);
glDrawElements (GL_TRIANGLES, renderer->numIndices, GL_UNSIGNED_INT, 0);
```

<span data-ttu-id="80857-161">Für Direct3D ist der Prozess sehr ähnlich, jedoch etwas didaktischer gestaltet.</span><span class="sxs-lookup"><span data-stu-id="80857-161">With Direct3D, it's a bit very similar process, albeit a bit more didactic.</span></span> <span data-ttu-id="80857-162">Stellen Sie den Indexpuffer als Direct3D-Unterressource für die [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)-Schnittstelle bereit, die Sie beim Konfigurieren von Direct3D erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="80857-162">Supply the index buffer as a Direct3D subresource to the [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385) you created when you configured Direct3D.</span></span> <span data-ttu-id="80857-163">Rufen Sie zu diesem Zweck [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/bb173588) mit der konfigurierten Unterressource wie folgt für das Indexarray auf.</span><span class="sxs-lookup"><span data-stu-id="80857-163">You do this by calling [**ID3D11DeviceContext::IASetIndexBuffer**](https://msdn.microsoft.com/library/windows/desktop/bb173588) with the configured subresource for the index array, as follows.</span></span> <span data-ttu-id="80857-164">(Beachten Sie auch hier, dass der Zeiger auf das **cubeIndices**-Array dem **pSysMem**-Feld der [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur zugewiesen wird.)</span><span class="sxs-lookup"><span data-stu-id="80857-164">(Again, notice that you assign the pointer to the **cubeIndices** array to the **pSysMem** field of the [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structure.)</span></span>

<span data-ttu-id="80857-165">Direct3D: Erstellen des Indexpuffers</span><span class="sxs-lookup"><span data-stu-id="80857-165">Direct3D: Create the index buffer.</span></span>

``` syntax
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

// ...

m_d3dContext->IASetIndexBuffer(
  m_indexBuffer.Get(),
  DXGI_FORMAT_R16_UINT,
  0);
```

<span data-ttu-id="80857-166">Später werden Sie die Dreiecke wie folgt mit einem Aufruf von [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) (bzw. [**ID3D11DeviceContext::Draw**](https://msdn.microsoft.com/library/windows/desktop/ff476407) für nicht indizierte Scheitelpunkte) zeichnen.</span><span class="sxs-lookup"><span data-stu-id="80857-166">Later, you will draw the triangles with a call to [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/ff476409) (or [**ID3D11DeviceContext::Draw**](https://msdn.microsoft.com/library/windows/desktop/ff476407) for unindexed vertices), as follows.</span></span> <span data-ttu-id="80857-167">(Ausführlichere Informationen erhalten Sie bereits jetzt unter [Zeichnen auf den Bildschirm](draw-to-the-screen.md).)</span><span class="sxs-lookup"><span data-stu-id="80857-167">(For more details, jump ahead to [Draw to the screen](draw-to-the-screen.md).)</span></span>

<span data-ttu-id="80857-168">Direct3D: Zeichnen der indizierten Scheitelpunkte</span><span class="sxs-lookup"><span data-stu-id="80857-168">Direct3D: Draw the indexed vertices.</span></span>

``` syntax
m_d3dContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
m_d3dContext->IASetInputLayout(m_inputLayout.Get());

// ...

m_d3dContext->DrawIndexed(
  m_indexCount,
  0,
  0);
```

## <a name="previous-step"></a><span data-ttu-id="80857-169">Vorheriger Schritt</span><span class="sxs-lookup"><span data-stu-id="80857-169">Previous step</span></span>


[<span data-ttu-id="80857-170">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="80857-170">Port the shader objects</span></span>](port-the-shader-config.md)

## <a name="next-step"></a><span data-ttu-id="80857-171">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="80857-171">Next step</span></span>

[<span data-ttu-id="80857-172">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="80857-172">Port the GLSL</span></span>](port-the-glsl.md)

## <a name="remarks"></a><span data-ttu-id="80857-173">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="80857-173">Remarks</span></span>

<span data-ttu-id="80857-174">Fügen Sie den Code, mit dem unter [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379) Methoden aufgerufen werden, beim Strukturieren von Direct3D jeweils in eine Methode ein, die aufgerufen wird, wenn die Geräteressourcen neu erstellt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="80857-174">When structuring your Direct3D, separate the code that calls methods on [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379) into a method that is called whenever the device resources need to be recreated.</span></span> <span data-ttu-id="80857-175">(In der Direct3D-Projektvorlage befindet sich dieser Code in den **CreateDeviceResource**-Methoden des Rendererobjekts.</span><span class="sxs-lookup"><span data-stu-id="80857-175">(In the Direct3D project template, this code is in the renderer object's **CreateDeviceResource** methods.</span></span> <span data-ttu-id="80857-176">Der Code zum Aktualisieren des Gerätekontexts ([**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)) wird jedoch in der **Render**-Methode platziert, da dort die Shaderphasen tatsächlich erstellt und die Daten gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="80857-176">The code that updates the device context ([**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)), on the other hand, is placed in the **Render** method, since this is where you actually construct the shader stages and bind the data.</span></span>

## <a name="related-topics"></a><span data-ttu-id="80857-177">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="80857-177">Related topics</span></span>


* [<span data-ttu-id="80857-178">Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="80857-178">How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11</span></span>](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md)
* [<span data-ttu-id="80857-179">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="80857-179">Port the shader objects</span></span>](port-the-shader-config.md)
* [<span data-ttu-id="80857-180">Portieren der Vertexpuffer und -daten</span><span class="sxs-lookup"><span data-stu-id="80857-180">Port the vertex buffers and data</span></span>](port-the-vertex-buffers-and-data-config.md)
* [<span data-ttu-id="80857-181">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="80857-181">Port the GLSL</span></span>](port-the-glsl.md)

 

 




