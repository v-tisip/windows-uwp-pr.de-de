---
author: mtoepke
title: Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11
description: Bei der ersten Portierungsübung beginnen wir mit den Grundlagen - Umstellen eines einfachen Renderers für einen sich drehenden Würfel mit Vertexschattierungen von OpenGLES2.0 auf Direct3D, damit er der Vorlage DirectX 11-App (Universelle Windows-App) aus Visual Studio2015 entspricht.
ms.assetid: e7f6fa41-ab05-8a1e-a154-704834e72e6d
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Opengl, Direct3D 11, Portieren
ms.localizationpriority: medium
ms.openlocfilehash: e7541a8f54f64197c17acea5f1737e36b0e6f670
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6986488"
---
# <a name="port-a-simple-opengl-es-20-renderer-to-direct3d-11"></a><span data-ttu-id="91218-104">Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="91218-104">Port a simple OpenGL ES 2.0 renderer to Direct3D 11</span></span>



<span data-ttu-id="91218-105">In dieser Portierungsübung beginnen wir mit den Grundlagen: Umstellen eines einfachen Renderers für einen sich drehenden Würfel mit Vertexschattierungen von OpenGLES2.0 auf Direct3D, damit er der Vorlage „DirectX11-App (Universelle Windows-App)“ aus Visual Studio2015 entspricht.</span><span class="sxs-lookup"><span data-stu-id="91218-105">For this porting exercise, we'll start with the basics: bringing a simple renderer for a spinning, vertex-shaded cube from OpenGL ES 2.0 into Direct3D, such that it matches the DirectX 11 App (Universal Windows) template from Visual Studio 2015.</span></span> <span data-ttu-id="91218-106">Beim Durcharbeiten dieses Portierungsprozesses lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="91218-106">As we walk through this port process, you will learn the following:</span></span>

-   <span data-ttu-id="91218-107">Portieren einer einfachen Gruppe von Vertexpuffern zu Direct3D-Eingabepuffern</span><span class="sxs-lookup"><span data-stu-id="91218-107">How to port a simple set of vertex buffers to Direct3D input buffers</span></span>
-   <span data-ttu-id="91218-108">Portieren von uniform-Elementen und Attributen zu Konstantenpuffern</span><span class="sxs-lookup"><span data-stu-id="91218-108">How to port uniforms and attributes to constant buffers</span></span>
-   <span data-ttu-id="91218-109">Konfigurieren von Direct3D-Shaderobjekten</span><span class="sxs-lookup"><span data-stu-id="91218-109">How to configure Direct3D shader objects</span></span>
-   <span data-ttu-id="91218-110">Verwenden von HLSL-Semantik bei der Entwicklung von Direct3D-Shadern</span><span class="sxs-lookup"><span data-stu-id="91218-110">How basic HLSL semantics are used in Direct3D shader development</span></span>
-   <span data-ttu-id="91218-111">Portieren einfacher GLSL zu HLSL</span><span class="sxs-lookup"><span data-stu-id="91218-111">How to port very simple GLSL to HLSL</span></span>

<span data-ttu-id="91218-112">Dieses Thema beginnt nach der Erstellung eines neuen DirectX11-Projekts.</span><span class="sxs-lookup"><span data-stu-id="91218-112">This topic starts after you have created a new DirectX 11 project.</span></span> <span data-ttu-id="91218-113">Informationen zum Erstellen eines neuen DirectX 11-Projekts finden Sie unter [Erstellen eines neuen DirectX 11-Projekts für die Universelle Windows-Plattform (UWP)](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="91218-113">To learn how to create a new DirectX 11 project, read [Create a new DirectX 11 project for Universal Windows Platform (UWP)](user-interface.md).</span></span>

<span data-ttu-id="91218-114">Das über einen dieser Links erstellte Projekt verfügt über den gesamten vorbereiteten Code für die [Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff476345)-Infrastruktur. Sie können sofort damit beginnen, den Renderer von OpenGL ES 2.0 zu Direct3D 11 zu portieren.</span><span class="sxs-lookup"><span data-stu-id="91218-114">The project created from either of these links has all the code for the [Direct3D](https://msdn.microsoft.com/library/windows/desktop/ff476345) infrastructure prepared, and you can immediately start into the process of porting your renderer from Open GL ES 2.0 to Direct3D 11.</span></span>

<span data-ttu-id="91218-115">Es werden zwei Codepfade durchgegangen, mit denen jeweils die gleiche grundlegende Grafikaufgabe durchgeführt wird: das Anzeigen eines sich drehenden Würfels mit Vertexschattierung in einem Fenster.</span><span class="sxs-lookup"><span data-stu-id="91218-115">This topic walks two code paths that perform the same basic graphics task: display a rotating vertex-shaded cube in a window.</span></span> <span data-ttu-id="91218-116">In beiden Fällen wird mit dem Code der folgende Prozess abgedeckt:</span><span class="sxs-lookup"><span data-stu-id="91218-116">In both cases, the code covers the following process:</span></span>

1.  <span data-ttu-id="91218-117">Erstellen eines Würfelgitters aus hartcodierten Daten.</span><span class="sxs-lookup"><span data-stu-id="91218-117">Creating a cube mesh from hardcoded data.</span></span> <span data-ttu-id="91218-118">Dieses Gitter wird als Liste mit Scheitelpunkten (Vertices) dargestellt, wobei jeder Scheitelpunkt (Vertex) über eine Position, einen Normalenvektor und einen Farbvektor verfügt.</span><span class="sxs-lookup"><span data-stu-id="91218-118">This mesh is represented as a list of vertices, with each vertex possessing a position, a normal vector, and a color vector.</span></span> <span data-ttu-id="91218-119">Dieses Gitter wird in einen Vertexpuffer eingefügt, der von der Schattierungspipeline verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="91218-119">This mesh is put into a vertex buffer for the shading pipeline to process.</span></span>
2.  <span data-ttu-id="91218-120">Erstellen von Shaderobjekten zum Verarbeiten des Würfelgitters.</span><span class="sxs-lookup"><span data-stu-id="91218-120">Creating shader objects to process the cube mesh.</span></span> <span data-ttu-id="91218-121">Es gibt zwei Arten von Shadern: einen Vertex-Shader, der die Scheitelpunkte für die Rasterung verarbeitet, und einen Fragmentshader (oder Pixelshader), mit dem die einzelnen Pixel des Würfels nach der Rasterung eingefärbt werden.</span><span class="sxs-lookup"><span data-stu-id="91218-121">There are two shaders: a vertex shader that processes the vertices for rasterization, and a fragment (pixel) shader that colors the individual pixels of the cube after rasterization.</span></span> <span data-ttu-id="91218-122">Diese Pixel werden zur Anzeige in ein Renderziel geschrieben.</span><span class="sxs-lookup"><span data-stu-id="91218-122">These pixels are written into a render target for display.</span></span>
3.  <span data-ttu-id="91218-123">Erstellen der Schattierungssprache, die in den Vertex- bzw. Fragmentshadern jeweils für die Vertex- und Pixelverarbeitung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91218-123">Forming the shading language that is used for vertex and pixel processing in the vertex and fragment shaders, respectively.</span></span>
4.  <span data-ttu-id="91218-124">Anzeige des gerenderten Würfels auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="91218-124">Displaying the rendered cube on the screen.</span></span>

![Einfacher OpenGL-Würfel](images/simple-opengl-cube.png)

<span data-ttu-id="91218-126">Nach der Durcharbeitung dieser exemplarischen Vorgehensweise sollten Ihnen die folgenden grundlegenden Unterschiede zwischen OpenGL ES 2.0 und Direct3D 11 bekannt sein:</span><span class="sxs-lookup"><span data-stu-id="91218-126">Upon completing this walkthrough, you should be familiar with the following basic differences between Open GL ES 2.0 and Direct3D 11:</span></span>

-   <span data-ttu-id="91218-127">Darstellung der Vertexpuffer und Vertexdaten</span><span class="sxs-lookup"><span data-stu-id="91218-127">The representation of vertex buffers and vertex data.</span></span>
-   <span data-ttu-id="91218-128">Prozess der Erstellung und Konfiguration von Shadern</span><span class="sxs-lookup"><span data-stu-id="91218-128">The process of creating and configuring shaders.</span></span>
-   <span data-ttu-id="91218-129">Schattierungssprachen und die Ein- und Ausgaben von Shaderobjekten</span><span class="sxs-lookup"><span data-stu-id="91218-129">Shading languages, and the inputs and outputs to shader objects.</span></span>
-   <span data-ttu-id="91218-130">Verhalten beim Zeichnen auf dem Bildschirm</span><span class="sxs-lookup"><span data-stu-id="91218-130">Screen drawing behaviors.</span></span>

<span data-ttu-id="91218-131">In dieser exemplarischen Vorgehensweise wird auf eine einfache und generische OpenGL-Rendererstruktur verwiesen, die wie folgt definiert ist:</span><span class="sxs-lookup"><span data-stu-id="91218-131">In this walkthrough, we refer to an simple and generic OpenGL renderer structure, which is defined like this:</span></span>

``` syntax
typedef struct 
{
    GLfloat pos[3];        
    GLfloat rgba[4];
} Vertex;

typedef struct
{
  // Integer handle to the shader program object.
  GLuint programObject;

  // The vertex and index buffers
  GLuint vertexBuffer;
  GLuint indexBuffer;

  // Handle to the location of model-view-projection matrix uniform
  GLint  mvpLoc; 
   
  // Vertex and index data
  Vertex  *vertices;
  GLuint   *vertexIndices;
  int       numIndices;

  // Rotation angle used for animation
  GLfloat   angle;

  GLfloat  mvpMatrix[4][4]; // the model-view-projection matrix itself
} Renderer;
```

<span data-ttu-id="91218-132">Diese Struktur verfügt über eine Instanz und enthält alle erforderlichen Komponenten zum Rendern eines sehr einfach aufgebauten Gitters mit Vertexschattierung.</span><span class="sxs-lookup"><span data-stu-id="91218-132">This structure has one instance and contains all the necessary components for rendering a very simple vertex-shaded mesh.</span></span>

> <span data-ttu-id="91218-133">**Hinweis:** Any OpenGL ES 2.0-Code in diesem Thema basiert auf der Windows-API-Implementierung von der Khronos Group und Programmiersyntax Windows C verwendet.</span><span class="sxs-lookup"><span data-stu-id="91218-133">**Note**Any OpenGL ES 2.0 code in this topic is based on the Windows API implementation provided by the Khronos Group, and uses Windows C programming syntax.</span></span>

 

## <a name="what-you-need-to-know"></a><span data-ttu-id="91218-134">Wissenswertes</span><span class="sxs-lookup"><span data-stu-id="91218-134">What you need to know</span></span>


### <a name="technologies"></a><span data-ttu-id="91218-135">Technologien</span><span class="sxs-lookup"><span data-stu-id="91218-135">Technologies</span></span>

-   [<span data-ttu-id="91218-136">Microsoft Visual C++</span><span class="sxs-lookup"><span data-stu-id="91218-136">Microsoft Visual C++</span></span>](http://msdn.microsoft.com/library/vstudio/60k1461a.aspx)
-   <span data-ttu-id="91218-137">OpenGL ES 2.0</span><span class="sxs-lookup"><span data-stu-id="91218-137">OpenGL ES 2.0</span></span>

### <a name="prerequisites"></a><span data-ttu-id="91218-138">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="91218-138">Prerequisites</span></span>

-   <span data-ttu-id="91218-139">Optional.</span><span class="sxs-lookup"><span data-stu-id="91218-139">Optional.</span></span> <span data-ttu-id="91218-140">Sehen Sie sich das Thema [Portieren von EGL-Code zu DXGI und Direct3D](moving-from-egl-to-dxgi.md) an.</span><span class="sxs-lookup"><span data-stu-id="91218-140">Review [Port EGL code to DXGI and Direct3D](moving-from-egl-to-dxgi.md).</span></span> <span data-ttu-id="91218-141">Lesen Sie sich die Informationen dieses Themas durch, um ein besseres Verständnis der von DirectX bereitgestellten Grafikschnittstelle zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="91218-141">Read this topic to better understand the graphics interface provided by DirectX.</span></span>

## <a name="span-idkeylinksstepsheadingspansteps"></a><span data-ttu-id="91218-142"><span id="keylinks_steps_heading"></span>Schritte</span><span class="sxs-lookup"><span data-stu-id="91218-142"><span id="keylinks_steps_heading"></span>Steps</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="91218-143">Thema</span><span class="sxs-lookup"><span data-stu-id="91218-143">Topic</span></span></th>
<th align="left"><span data-ttu-id="91218-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91218-144">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="port-the-shader-config.md"><span data-ttu-id="91218-145">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="91218-145">Port the shader objects</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="91218-146">Beim Portieren des einfachen Renderers aus OpenGL ES 2.0 ist der erste Schritt das Einrichten der äquivalenten Vertex- und Fragmentshaderobjekte in Direct3D 11. Stellen Sie außerdem sicher, dass das Hauptprogramm mit den Shaderobjekten kommunizieren kann, nachdem diese kompiliert wurden.</span><span class="sxs-lookup"><span data-stu-id="91218-146">When porting the simple renderer from OpenGL ES 2.0, the first step is to set up the equivalent vertex and fragment shader objects in Direct3D 11, and to make sure that the main program can communicate with the shader objects after they are compiled.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="port-the-vertex-buffers-and-data-config.md"><span data-ttu-id="91218-147">Portieren der Vertexpuffer und -daten</span><span class="sxs-lookup"><span data-stu-id="91218-147">Port the vertex buffers and data</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="91218-148">In diesem Schritt definieren Sie die Vertexpuffer für die Gitter und die Indexpuffer, mit deren Hilfe die Shader die Scheitelpunkte (Vertices) in einer angegebenen Reihenfolge durchlaufen können.</span><span class="sxs-lookup"><span data-stu-id="91218-148">In this step, you'll define the vertex buffers that will contain your meshes and the index buffers that allow the shaders to traverse the vertices in a specified order.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="port-the-glsl.md"><span data-ttu-id="91218-149">Portieren des GLSL-Codes</span><span class="sxs-lookup"><span data-stu-id="91218-149">Port the GLSL</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="91218-150">Nachdem Sie sich um den Code gekümmert haben, mit dem die Puffer und Shaderobjekte erstellt und konfiguriert werden, muss der in diesen Shadern enthaltene Code von der GL Shader Language (GLSL) von OpenGL ES 2.0 in die High-Level Shader Language (HLSL) von Direct3D 11 portiert werden.</span><span class="sxs-lookup"><span data-stu-id="91218-150">Once you've moved over the code that creates and configures your buffers and shader objects, it's time to port the code inside those shaders from OpenGL ES 2.0's GL Shader Language (GLSL) to Direct3D 11's High-level Shader Language (HLSL).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="draw-to-the-screen.md"><span data-ttu-id="91218-151">Zeichnen auf den Bildschirm</span><span class="sxs-lookup"><span data-stu-id="91218-151">Draw to the screen</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="91218-152">Schließlich wird der Code portiert, der den sich drehenden Würfel auf den Bildschirm zeichnet.</span><span class="sxs-lookup"><span data-stu-id="91218-152">Finally, we port the code that draws the spinning cube to the screen.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idadditionalresourcesspanadditional-resources"></a><span data-ttu-id="91218-153"><span id="additional_resources"></span>Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="91218-153"><span id="additional_resources"></span>Additional resources</span></span>


-   [<span data-ttu-id="91218-154">Vorbereiten der Entwicklungsumgebung für die Entwicklung von UWP-DirectX-Spielen</span><span class="sxs-lookup"><span data-stu-id="91218-154">Prepare your dev environment for UWP DirectX game development</span></span>](prepare-your-dev-environment-for-windows-store-directx-game-development.md)
-   [<span data-ttu-id="91218-155">Erstellen eines neuen DirectX11-Projekts für UWP</span><span class="sxs-lookup"><span data-stu-id="91218-155">Create a new DirectX 11 project for UWP</span></span>](user-interface.md)
-   [<span data-ttu-id="91218-156">Zuordnen von OpenGLES2.0-Konzepten und -Infrastruktur zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="91218-156">Map OpenGL ES 2.0 concepts and infrastructure to Direct3D 11</span></span>](map-concepts-and-infrastructure.md)

 

 




