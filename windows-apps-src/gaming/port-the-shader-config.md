---
author: mtoepke
title: Portieren der Shaderobjekte
description: Beim Portieren des einfachen Renderers aus OpenGL ES 2.0 ist der erste Schritt das Einrichten der äquivalenten Vertex- und Fragmentshaderobjekte in Direct3D 11. Stellen Sie außerdem sicher, dass das Hauptprogramm mit den Shaderobjekten kommunizieren kann, nachdem diese kompiliert wurden.
ms.assetid: 0383b774-bc1b-910e-8eb6-cc969b3dcc08
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Portieren, Shader, Direct3D, OpenGL
ms.localizationpriority: medium
ms.openlocfilehash: bbf7e05a93ccce4188d62f9800a5f225be713cc6
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5617537"
---
# <a name="port-the-shader-objects"></a><span data-ttu-id="b8c6b-104">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="b8c6b-104">Port the shader objects</span></span>




**<span data-ttu-id="b8c6b-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="b8c6b-105">Important APIs</span></span>**

-   [**<span data-ttu-id="b8c6b-106">ID3D11Device</span><span class="sxs-lookup"><span data-stu-id="b8c6b-106">ID3D11Device</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476379)
-   [**<span data-ttu-id="b8c6b-107">ID3D11DeviceContext</span><span class="sxs-lookup"><span data-stu-id="b8c6b-107">ID3D11DeviceContext</span></span>**](https://msdn.microsoft.com/library/windows/desktop/ff476385)

<span data-ttu-id="b8c6b-108">Beim Portieren des einfachen Renderers aus OpenGL ES 2.0 ist der erste Schritt das Einrichten der äquivalenten Vertex- und Fragmentshaderobjekte in Direct3D 11. Stellen Sie außerdem sicher, dass das Hauptprogramm mit den Shaderobjekten kommunizieren kann, nachdem diese kompiliert wurden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-108">When porting the simple renderer from OpenGL ES 2.0, the first step is to set up the equivalent vertex and fragment shader objects in Direct3D 11, and to make sure that the main program can communicate with the shader objects after they are compiled.</span></span>

> <span data-ttu-id="b8c6b-109">**Hinweis:**  haben Sie ein neues Direct3D-Projekt erstellt?</span><span class="sxs-lookup"><span data-stu-id="b8c6b-109">**Note** Have you created a new Direct3D project?</span></span> <span data-ttu-id="b8c6b-110">Falls nicht, befolgen Sie die Anleitung unter [Erstellen eines neuen DirectX 11-Projekts für die Universelle Windows-Plattform (UWP)](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-110">If not, follow the instructions in [Create a new DirectX 11 project for Universal Windows Platform (UWP)](user-interface.md).</span></span> <span data-ttu-id="b8c6b-111">Bei dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass Sie die DXGI- und Direct3D-Ressourcen zum Zeichnen auf den Bildschirm erstellt haben, die auch in der Vorlage bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-111">This walkthrough assumes that you have the created the DXGI and Direct3D resources for drawing to the screen, and which are provided in the template.</span></span>

 

<span data-ttu-id="b8c6b-112">Wie unter OpenGLES2.0 auch, müssen die kompilierten Shader in Direct3D einem Kontext für das Zeichnen zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-112">Much like OpenGL ES 2.0, the compiled shaders in Direct3D must be associated with a drawing context.</span></span> <span data-ttu-id="b8c6b-113">Direct3D verfügt jedoch nicht per se über das Konzept eines Shaderprogrammobjekts. Daher weisen Sie die Shader direkt einem [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385) zu.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-113">However, Direct3D does not have the concept of a shader program object per se; instead, you must assign the shaders directly to a [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385).</span></span> <span data-ttu-id="b8c6b-114">Bei diesem Schritt wird der OpenGL ES 2.0-Prozess zum Erstellen und Binden von Shaderobjekten eingehalten, und es werden die entsprechenden API-Verhalten in Direct3D bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-114">This step follows the OpenGL ES 2.0 process for creating and binding shader objects, and provides you with the corresponding API behaviors in Direct3D.</span></span>

<a name="instructions"></a><span data-ttu-id="b8c6b-115">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b8c6b-115">Instructions</span></span>
------------

### <a name="step-1-compile-the-shaders"></a><span data-ttu-id="b8c6b-116">Schritt 1: Kompilieren der Shader</span><span class="sxs-lookup"><span data-stu-id="b8c6b-116">Step 1: Compile the shaders</span></span>

<span data-ttu-id="b8c6b-117">In diesem einfachen OpenGL ES 2.0-Beispiel werden die Shader als Textdateien gespeichert und als Zeichenfolgendaten für die Laufzeitkompilierung geladen.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-117">In this simple OpenGL ES 2.0 sample, the shaders are stored as text files and loaded as string data for run-time compilation.</span></span>

<span data-ttu-id="b8c6b-118">OpenGLES2.0: Kompilieren eines Shaders</span><span class="sxs-lookup"><span data-stu-id="b8c6b-118">OpenGL ES 2.0: Compile a shader</span></span>

``` syntax
GLuint __cdecl CompileShader (GLenum shaderType, const char *shaderSrcStr)
// shaderType can be GL_VERTEX_SHADER or GL_FRAGMENT_SHADER. Returns 0 if compilation fails.
{
  GLuint shaderHandle;
  GLint compiledShaderHandle;
   
  // Create an empty shader object.
  shaderHandle = glCreateShader(shaderType);

  if (shaderHandle == 0)
  return 0;

  // Load the GLSL shader source as a string value. You could obtain it from
  // from reading a text file or hardcoded.
  glShaderSource(shaderHandle, 1, &shaderSrcStr, NULL);
   
  // Compile the shader.
  glCompileShader(shaderHandle);

  // Check the compile status
  glGetShaderiv(shaderHandle, GL_COMPILE_STATUS, &compiledShaderHandle);

  if (!compiledShaderHandle) // error in compilation occurred
  {
    // Handle any errors here.
              
    glDeleteShader(shaderHandle);
    return 0;
  }

  return shaderHandle;

}
```

<span data-ttu-id="b8c6b-119">In Direct3D werden Shader nicht während der Laufzeit kompiliert. Sie werden immer in CSO-Dateien kompiliert, wenn auch die restlichen Daten des Programms kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-119">In Direct3D, shaders are not compiled during run-time; they are always compiled to CSO files when the rest of the program is compiled.</span></span> <span data-ttu-id="b8c6b-120">Wenn Sie die App mit Microsoft Visual Studio kompilieren, werden die HLSL-Dateien in CSO-Dateien (.cso) kompiliert, die von der App geladen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-120">When you compile your app with Microsoft Visual Studio, the HLSL files are compiled to CSO (.cso) files that your app must load.</span></span> <span data-ttu-id="b8c6b-121">Achten Sie darauf, diese CSO-Dateien der App beim Verpacken hinzuzufügen!</span><span class="sxs-lookup"><span data-stu-id="b8c6b-121">Make sure you include these CSO files with your app when you package it!</span></span>

> <span data-ttu-id="b8c6b-122">**Hinweis:**  im folgenden Beispiel wird das Laden und Kompilieren des Shaders asynchron mit Syntax für die **Automatische** Schlüsselwort und Lambda-Funktion.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-122">**Note** The following example performs the shader loading and compilation asynchronously using the **auto** keyword and lambda syntax.</span></span> <span data-ttu-id="b8c6b-123">ReadDataAsync() ist eine für die Vorlage implementierte Methode, mit der eine CSO-Datei als Array mit Bytedaten (fileData) eingelesen wird.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-123">ReadDataAsync() is a method implemented for the template that reads in a CSO file as an array of byte data (fileData).</span></span>

 

<span data-ttu-id="b8c6b-124">Direct3D 11: Kompilieren eines Shaders</span><span class="sxs-lookup"><span data-stu-id="b8c6b-124">Direct3D 11: Compile a shader</span></span>

``` syntax
auto loadVSTask = DX::ReadDataAsync(m_projectDir + "SimpleVertexShader.cso");
auto loadPSTask = DX::ReadDataAsync(m_projectDir + "SimplePixelShader.cso");

auto createVSTask = loadVSTask.then([this](Platform::Array<byte>^ fileData) {

m_d3dDevice->CreateVertexShader(
  fileData->Data,
  fileData->Length,
  nullptr,
  &m_vertexShader);

auto createPSTask = loadPSTask.then([this](Platform::Array<byte>^ fileData) {
  m_d3dDevice->CreatePixelShader(
    fileData->Data,
    fileData->Length,
    nullptr,
    &m_pixelShader;
};
```

### <a name="step-2-create-and-load-the-vertex-and-fragment-pixel-shaders"></a><span data-ttu-id="b8c6b-125">Schritt 2: Erstellen und Laden der Vertex- und Fragmentshader (Pixelshader)</span><span class="sxs-lookup"><span data-stu-id="b8c6b-125">Step 2: Create and load the vertex and fragment (pixel) shaders</span></span>

<span data-ttu-id="b8c6b-126">Unter OpenGL ES 2.0 wird ein so genanntes Shaderprogramm verwendet, das als Schnittstelle zwischen dem Hauptprogramm, das über die CPU ausgeführt wird, und den Shadern fungiert, die über die GPU ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-126">OpenGL ES 2.0 has the notion of a shader "program", which serves as the interface between the main program running on the CPU and the shaders, which are executed on the GPU.</span></span> <span data-ttu-id="b8c6b-127">Shader werden kompiliert (oder aus kompilierten Quellen geladen) und einem Programm zugeordnet, das die Ausführung über die GPU ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-127">Shaders are compiled (or loaded from compiled sources) and associated with a program, which enables execution on the GPU.</span></span>

<span data-ttu-id="b8c6b-128">OpenGLES2.0: Laden der Vertex- und Fragmentshader in ein Schattierungsprogramm</span><span class="sxs-lookup"><span data-stu-id="b8c6b-128">OpenGL ES 2.0: Loading the vertex and fragment shaders into a shading program</span></span>

``` syntax
GLuint __cdecl LoadShaderProgram (const char *vertShaderSrcStr, const char *fragShaderSrcStr)
{
  GLuint programObject, vertexShaderHandle, fragmentShaderHandle;
  GLint linkStatusCode;

  // Load the vertex shader and compile it to an internal executable format.
  vertexShaderHandle = CompileShader(GL_VERTEX_SHADER, vertShaderSrcStr);
  if (vertexShaderHandle == 0)
  {
    glDeleteShader(vertexShaderHandle);
    return 0;
  }

   // Load the fragment/pixel shader and compile it to an internal executable format.
  fragmentShaderHandle = CompileShader(GL_FRAGMENT_SHADER, fragShaderSrcStr);
  if (fragmentShaderHandle == 0)
  {
    glDeleteShader(fragmentShaderHandle);
    return 0;
  }

  // Create the program object proper.
  programObject = glCreateProgram();
   
  if (programObject == 0)    return 0;

  // Attach the compiled shaders
  glAttachShader(programObject, vertexShaderHandle);
  glAttachShader(programObject, fragmentShaderHandle);

  // Compile the shaders into binary executables in memory and link them to the program object..
  glLinkProgram(programObject);

  // Check the project object link status and determine if the program is available.
  glGetProgramiv(programObject, GL_LINK_STATUS, &linkStatusCode);

  if (!linkStatusCode) // if link status <> 0
  {
    // Linking failed; delete the program object and return a failure code (0).

    glDeleteProgram (programObject);
    return 0;
  }

  // Deallocate the unused shader resources. The actual executables are part of the program object.
  glDeleteShader(vertexShaderHandle);
  glDeleteShader(fragmentShaderHandle);

  return programObject;
}

// ...

glUseProgram(renderer->programObject);
```

<span data-ttu-id="b8c6b-129">In Direct3D wird kein Shaderprogrammobjekt verwendet.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-129">Direct3D does not have the concept of a shader program object.</span></span> <span data-ttu-id="b8c6b-130">Stattdessen werden die Shader erstellt, wenn eine der Shadererstellungsmethoden auf der [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379)-Schnittstelle (z. B. [**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524) oder [**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513)) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-130">Rather, the shaders are created when one of the shader creation methods on the [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379) interface (such as [**ID3D11Device::CreateVertexShader**](https://msdn.microsoft.com/library/windows/desktop/ff476524) or [**ID3D11Device::CreatePixelShader**](https://msdn.microsoft.com/library/windows/desktop/ff476513)) is called.</span></span> <span data-ttu-id="b8c6b-131">Um die Shader für den aktuellen Zeichnungskontext festzulegen, werden diese einer entsprechenden [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)-Schnittstelle mit einer SetShader-Methode bereitgestellt, z. B. [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) für den Vertex-Shader oder [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) für den Fragmentshader.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-131">To set the shaders for the current drawing context, we provide them to corresponding [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385) with a set shader method, such as [**ID3D11DeviceContext::VSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476493) for the vertex shader or [**ID3D11DeviceContext::PSSetShader**](https://msdn.microsoft.com/library/windows/desktop/ff476472) for the fragment shader.</span></span>

<span data-ttu-id="b8c6b-132">Direct3D 11: Festlegen der Shader für den Kontext des Grafikgeräts für das Zeichnen</span><span class="sxs-lookup"><span data-stu-id="b8c6b-132">Direct3D 11: Set the shaders for the graphics device drawing context.</span></span>

``` syntax
m_d3dContext->VSSetShader(
  m_vertexShader.Get(),
  nullptr,
  0);

m_d3dContext->PSSetShader(
  m_pixelShader.Get(),
  nullptr,
  0);
```

### <a name="step-3-define-the-data-to-supply-to-the-shaders"></a><span data-ttu-id="b8c6b-133">Schritt 3: Definieren der Daten für die Shader</span><span class="sxs-lookup"><span data-stu-id="b8c6b-133">Step 3: Define the data to supply to the shaders</span></span>

<span data-ttu-id="b8c6b-134">Im OpenGL ES 2.0-Beispiel wird ein **uniform**-Element für die Shaderpipeline deklariert:</span><span class="sxs-lookup"><span data-stu-id="b8c6b-134">In our OpenGL ES 2.0 example, we have one **uniform** to declare for the shader pipeline:</span></span>

-   <span data-ttu-id="b8c6b-135">**u\_mvpMatrix**: Ein 4x4-Array mit Float-Werten, welches die endgültige Modell-Ansicht-Projektion-Transformationsmatrix darstellt, das die Modellkoordinaten für den Würfel verwendet und sie in 2D-Projektionskoordinaten für die Scankonvertierung transformiert.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-135">**u\_mvpMatrix**: a 4x4 array of floats that represents the final model-view-projection transformation matrix that takes the model coordinates for the cube and transforms them into 2D projection coordinates for scan conversion.</span></span>

<span data-ttu-id="b8c6b-136">Zusätzlich zwei **attribute**-Werte für die Vertexdaten:</span><span class="sxs-lookup"><span data-stu-id="b8c6b-136">And two **attribute** values for the vertex data:</span></span>

-   <span data-ttu-id="b8c6b-137">**a\_position**: Ein 4-Float-Vektor für die Modellkoordinaten eines Vertex.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-137">**a\_position**: a 4-float vector for the model coordinates of a vertex.</span></span>
-   <span data-ttu-id="b8c6b-138">**a\_color**: Ein 4-Float-Vektor für den RGBA-Farbwert, der dem Vertex zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-138">**a\_color**: A 4-float vector for the RGBA color value associated with the vertex.</span></span>

<span data-ttu-id="b8c6b-139">OpenGLES2.0: GLSL-Definitionen für die uniform-Elemente und Attribute</span><span class="sxs-lookup"><span data-stu-id="b8c6b-139">Open GL ES 2.0: GLSL definitions for the uniforms and attributes</span></span>

``` syntax
uniform mat4 u_mvpMatrix;
attribute vec4 a_position;
attribute vec4 a_color;
```

<span data-ttu-id="b8c6b-140">Die entsprechenden Variablen des Hauptprogramms werden in diesem Fall als Felder des Rendererobjekts definiert.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-140">The corresponding main program variables are defined as fields on the renderer object, in this case.</span></span> <span data-ttu-id="b8c6b-141">(Weitere Informationen finden Sie unter [So wird's gemacht: Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md).) Danach müssen die Speicherorte im Speicher angegeben werden, an denen das Hauptprogramm diese Werte für die Shaderpipeline bereitstellt. Dies erfolgt normalerweise direkt vor einem Draw-Aufruf:</span><span class="sxs-lookup"><span data-stu-id="b8c6b-141">(Refer to the header in [How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md).) Once we've done that, we need to specify the locations in memory where the main program will supply these values for the shader pipeline, which we typically do right before a draw call:</span></span>

<span data-ttu-id="b8c6b-142">OpenGLES2.0: Kennzeichnen des Speicherorts der uniform- und Attributdaten</span><span class="sxs-lookup"><span data-stu-id="b8c6b-142">OpenGL ES 2.0: Marking the location of the uniform and attribute data</span></span>

``` syntax

// Inform the shader of the attribute locations
loc = glGetAttribLocation(renderer->programObject, "a_position");
glVertexAttribPointer(loc, 3, GL_FLOAT, GL_FALSE, 
    sizeof(Vertex), 0);
glEnableVertexAttribArray(loc);

loc = glGetAttribLocation(renderer->programObject, "a_color");
glVertexAttribPointer(loc, 4, GL_FLOAT, GL_FALSE, 
    sizeof(Vertex), (GLvoid*) (sizeof(float) * 3));
glEnableVertexAttribArray(loc);


// Inform the shader program of the uniform location
renderer->mvpLoc = glGetUniformLocation(renderer->programObject, "u_mvpMatrix");
```

<span data-ttu-id="b8c6b-143">In Direct3D werden "Attribute" oder "uniform-Elemente" in dieser Form nicht verwendet (bzw. wird diese Syntax nicht freigegeben).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-143">Direct3D does not have the concept of an "attribute" or a "uniform" in the same sense (or, at least, it does not share this syntax).</span></span> <span data-ttu-id="b8c6b-144">Stattdessen werden Konstantenpuffer verwendet, die als Direct3D-Unterressourcen dargestellt werden. Diese Ressourcen werden vom Hauptprogramm und den Shaderprogrammen gemeinsam genutzt.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-144">Rather, it has constant buffers, represented as Direct3D subresources -- resources that are shared between the main program and the shader programs.</span></span> <span data-ttu-id="b8c6b-145">Einige dieser Unterressourcen, wie Vertexpositionen und -farben, werden in Form von HLSL-Semantik beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-145">Some of these subresources, such as vertex positions and colors, are described as HLSL semantics.</span></span> <span data-ttu-id="b8c6b-146">Weitere Informationen zu Konstantenpuffern und zur HLSL-Semantik und deren Beziehung zu OpenGLES2.0-Konzepten finden Sie unter [Portieren von Framepufferobjekten, uniform-Elementen und Attributen](porting-uniforms-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-146">For more info on constant buffers and HLSL semantics as they relate to OpenGL ES 2.0 concepts, read [Port frame buffer objects, uniforms, and attributes](porting-uniforms-and-attributes.md).</span></span>

<span data-ttu-id="b8c6b-147">Wenn dieser Prozess unter Direct3D durchgeführt werden soll, wird das „uniform“-Element in einen Direct3D-Konstantenpuffer („cbuffer“) konvertiert und erhält ein Register für die Suche per **register**-HLSL-Semantik.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-147">When moving this process to Direct3D, we convert the uniform to a Direct3D constant buffer (cbuffer) and assign it a register for lookup with the **register** HLSL semantic.</span></span> <span data-ttu-id="b8c6b-148">Die beiden Vertexattribute werden als Eingabeelemente für die Shaderpipelinephasen behandelt und ebenfalls mit [HLSL-Semantik](https://msdn.microsoft.com/library/windows/desktop/bb205574) (POSITION und COLOR0) zum Informieren der Shader versehen.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-148">The two vertex attributes are handled as input elements to the shader pipeline stages, and are also assigned [HLSL semantics](https://msdn.microsoft.com/library/windows/desktop/bb205574) (POSITION and COLOR0) that inform the shaders.</span></span> <span data-ttu-id="b8c6b-149">Vom Pixelshader wird ein SV\_POSITION-Element verwendet, wobei mit dem Präfix „SV\_“ angegeben wird, dass es sich um einen von der GPU erzeugten Systemwert handelt.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-149">The pixel shader takes an SV\_POSITION, with the SV\_ prefix indicating that it is a system value generated by the GPU.</span></span> <span data-ttu-id="b8c6b-150">(In diesem Fall ist dies eine Pixelposition, die während der Scankonvertierung erzeugt wurde.) Die Elemente VertexShaderInput und PixelShaderInput werden nicht als Konstantenpuffer deklariert, weil VertexShaderInput zum Definieren des Vertexpuffers verwendet wird (siehe [Portieren der Vertexpuffer und -daten](port-the-vertex-buffers-and-data-config.md)). Die Daten für PixelShaderInput werden als Folge einer vorherigen Phase der Pipeline erzeugt. In diesem Fall ist dies der Vertex-Shader.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-150">(In this case, it is a pixel position generated during scan conversion.) VertexShaderInput and PixelShaderInput are not declared as constant buffers because the former will be used to define the vertex buffer (see [Port the vertex buffers and data](port-the-vertex-buffers-and-data-config.md)), and the data for the latter is generated as the result of a previous stage in the pipeline, which in this case is the vertex shader.</span></span>

<span data-ttu-id="b8c6b-151">Direct3D: HLSL-Definitionen für die Konstantenpuffer und Vertexdaten</span><span class="sxs-lookup"><span data-stu-id="b8c6b-151">Direct3D: HLSL definitions for the constant buffers and vertex data</span></span>

``` syntax
cbuffer ModelViewProjectionConstantBuffer : register(b0)
{
  matrix mvp;
};

// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
  float4 pos : POSITION;
  float4 color : COLOR0;
};

// Per-vertex color data passed through the pixel shader.
struct PixelShaderInput
{
  float4 pos : SV_POSITION;
  float3 color : COLOR0;
};
```

<span data-ttu-id="b8c6b-152">Weitere Informationen zur Portierung zu Konstantenpuffern und zur Anwendung der HLSL-Semantik finden Sie unter [Portieren von Framepufferobjekten, uniform-Elementen und Attributen](porting-uniforms-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-152">For more info on porting to constant buffers and the application of HLSL semantics, read [Port frame buffer objects, uniforms, and attributes](porting-uniforms-and-attributes.md).</span></span>

<span data-ttu-id="b8c6b-153">Dies sind die Strukturen für das Layout der Daten, die mit einem Konstanten- oder Vertexpuffer an die Shaderpipeline übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-153">Here are the structures for the layout of the data passed to the shader pipeline with a constant or vertex buffer.</span></span>

<span data-ttu-id="b8c6b-154">Direct3D 11: Deklarieren des Layouts für Konstanten- und Vertexpuffer</span><span class="sxs-lookup"><span data-stu-id="b8c6b-154">Direct3D 11: Declaring the constant and vertex buffers layout</span></span>

``` syntax
// Constant buffer used to send MVP matrices to the vertex shader.
struct ModelViewProjectionConstantBuffer
{
  DirectX::XMFLOAT4X4 modelViewProjection;
};

// Used to send per-vertex data to the vertex shader.
struct VertexPositionColor
{
  DirectX::XMFLOAT4 pos;
  DirectX::XMFLOAT4 color;
};
```

<span data-ttu-id="b8c6b-155">Verwenden Sie die DirectXMath-Typen „XM\*“ für die Konstantenpufferelemente, da sie eine gute Verpackung und Ausrichtung der Inhalte ermöglichen, wenn diese an die Shaderpipeline gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-155">Use the DirectXMath XM\* types for your constant buffer elements, since they provide proper packing and alignment for the contents when they are sent to the shader pipeline.</span></span> <span data-ttu-id="b8c6b-156">Wenn Sie standardmäßige Gleitkommatypen und Arrays der Windows-Plattform verwenden, müssen Sie die Verpackung und Ausrichtung selbst durchführen.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-156">If you use standard Windows platform float types and arrays, you must perform the packing and alignment yourself.</span></span>

<span data-ttu-id="b8c6b-157">Erstellen Sie zum Binden eines Konstantenpuffers eine Layoutbeschreibung als [**CD3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/jj151620)-Struktur, und übergeben Sie diese an [**ID3DDevice::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-157">To bind a constant buffer, create a layout description as a [**CD3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/jj151620) structure, and pass it to [**ID3DDevice::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501).</span></span> <span data-ttu-id="b8c6b-158">Übergeben Sie den Konstantenpuffer in der Rendermethode dann vor dem Zeichnen an [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486).</span><span class="sxs-lookup"><span data-stu-id="b8c6b-158">Then, in your render method, pass the constant buffer to [**ID3D11DeviceContext::UpdateSubresource**](https://msdn.microsoft.com/library/windows/desktop/ff476486) before drawing.</span></span>

<span data-ttu-id="b8c6b-159">Direct3D 11: Binden des Konstantenpuffers</span><span class="sxs-lookup"><span data-stu-id="b8c6b-159">Direct3D 11: Bind the constant buffer</span></span>

``` syntax
CD3D11_BUFFER_DESC constantBufferDesc(sizeof(ModelViewProjectionConstantBuffer), D3D11_BIND_CONSTANT_BUFFER);

m_d3dDevice->CreateBuffer(
  &constantBufferDesc,
  nullptr,
  &m_constantBuffer);

// ...

// Only update shader resources that have changed since the last frame.
m_d3dContext->UpdateSubresource(
  m_constantBuffer.Get(),
  0,
  NULL,
  &m_constantBufferData,
  0,
  0);
```

<span data-ttu-id="b8c6b-160">Der Vertexpuffer wird auf ähnliche Weise erstellt und aktualisiert. Dies ist im nächsten Schritt, [Portieren der Vertexpuffer und -daten](port-the-vertex-buffers-and-data-config.md), beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8c6b-160">The vertex buffer is created and updated similarly, and is discussed in the next step, [Port the vertex buffers and data](port-the-vertex-buffers-and-data-config.md).</span></span>

<a name="next-step"></a><span data-ttu-id="b8c6b-161">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="b8c6b-161">Next step</span></span>
---------

[<span data-ttu-id="b8c6b-162">Portieren der Vertexpuffer und -daten</span><span class="sxs-lookup"><span data-stu-id="b8c6b-162">Port the vertex buffers and data</span></span>](port-the-vertex-buffers-and-data-config.md)
## <a name="related-topics"></a><span data-ttu-id="b8c6b-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b8c6b-163">Related topics</span></span>


[<span data-ttu-id="b8c6b-164">Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="b8c6b-164">How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11</span></span>](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md)

[<span data-ttu-id="b8c6b-165">Portieren der Vertexpuffer und -daten</span><span class="sxs-lookup"><span data-stu-id="b8c6b-165">Port the vertex buffers and data</span></span>](port-the-vertex-buffers-and-data-config.md)

[<span data-ttu-id="b8c6b-166">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="b8c6b-166">Port the GLSL</span></span>](port-the-glsl.md)

[<span data-ttu-id="b8c6b-167">Zeichnen auf den Bildschirm</span><span class="sxs-lookup"><span data-stu-id="b8c6b-167">Draw to the screen</span></span>](draw-to-the-screen.md)

 

 




