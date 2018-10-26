---
author: mtoepke
title: GLSL-zu-HLSL-Referenz
description: Sie portieren Ihren OpenGL Shader Language (GLSL)-Code zu Microsoft High Level Shader Language (HLSL)-Code, wenn Sie Ihre Grafikarchitektur von OpenGLES2.0 zu Direct3D11 portieren, um ein Spiel für die universelle Windows-Plattform (UWP) zu erstellen.
ms.assetid: 979d19f6-ef0c-64e4-89c2-a31e1c7b7692
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, glsl, hlsl, opengl, directx, Shader
ms.localizationpriority: medium
ms.openlocfilehash: 30c925f9ebb07d578147dfba373fdeb3baa364fe
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5557129"
---
# <a name="glsl-to-hlsl-reference"></a><span data-ttu-id="18431-104">GLSL-zu-HLSL-Referenz</span><span class="sxs-lookup"><span data-stu-id="18431-104">GLSL-to-HLSL reference</span></span>



<span data-ttu-id="18431-105">Sie portieren Ihren OpenGL Shader Language (GLSL)-Code zu Microsoft High Level Shader Language (HLSL)-Code, wenn Sie Ihre [Grafikarchitektur von OpenGLES2.0 zu Direct3D11 portieren](port-from-opengl-es-2-0-to-directx-11-1.md), um ein Spiel für die universelle Windows-Plattform (UWP) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="18431-105">You port your OpenGL Shader Language (GLSL) code to Microsoft High Level Shader Language (HLSL) code when you [port your graphics architecture from OpenGL ES 2.0 to Direct3D 11](port-from-opengl-es-2-0-to-directx-11-1.md) to create a game for Universal Windows Platform (UWP).</span></span> <span data-ttu-id="18431-106">Die hier verwendete GLSL ist kompatibel mit OpenGLES2.0, und die HLSL ist kompatibel mit Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="18431-106">The GLSL that is referred to herein is compatible with OpenGL ES 2.0; the HLSL is compatible with Direct3D 11.</span></span> <span data-ttu-id="18431-107">Informationen zu den Unterschieden zwischen Direct3D11 und Vorgängerversionen von Direct3D finden Sie unter [Funktionszuordnung](feature-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="18431-107">For info about the differences between Direct3D 11 and previous versions of Direct3D, see [Feature mapping](feature-mapping.md).</span></span>

-   [<span data-ttu-id="18431-108">Vergleich zwischen OpenGLES2.0 und Direct3D11</span><span class="sxs-lookup"><span data-stu-id="18431-108">Comparing OpenGL ES 2.0 with Direct3D 11</span></span>](#comparing-opengl-es-20-with-direct3d-11)
-   [<span data-ttu-id="18431-109">Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-109">Porting GLSL variables to HLSL</span></span>](#porting-glsl-variables-to-hlsl)
-   [<span data-ttu-id="18431-110">Portieren von GLSL-Typen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-110">Porting GLSL types to HLSL</span></span>](#porting-glsl-types-to-hlsl)
-   [<span data-ttu-id="18431-111">Portieren von vordefinierten globalen GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-111">Porting GLSL pre-defined global variables to HLSL</span></span>](#porting-glsl-pre-defined-global-variables-to-hlsl)
-   [<span data-ttu-id="18431-112">Beispiele für das Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-112">Examples of porting GLSL variables to HLSL</span></span>](#examples-of-porting-glsl-variables-to-hlsl)
    -   [<span data-ttu-id="18431-113">Uniform-Variable, Attribut und variierende Variable in GLSL</span><span class="sxs-lookup"><span data-stu-id="18431-113">Uniform, attribute, and varying in GLSL</span></span>](#uniform-attribute-and-varying-in-glsl)
    -   [<span data-ttu-id="18431-114">Konstantenpuffer und Datenübertragungen in HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-114">Constant buffers and data transfers in HLSL</span></span>](#constant-buffers-and-data-transfers-in-hlsl)
-   [<span data-ttu-id="18431-115">Beispiele für das Portieren von OpenGL-Renderingcode zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="18431-115">Examples of porting OpenGL rendering code to Direct3D</span></span>](#examples-of-porting-opengl-rendering-code-to-direct3d)
-   [<span data-ttu-id="18431-116">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="18431-116">Related topics</span></span>](#related-topics)

## <a name="comparing-opengl-es-20-with-direct3d-11"></a><span data-ttu-id="18431-117">Vergleich zwischen OpenGLES2.0 und Direct3D11</span><span class="sxs-lookup"><span data-stu-id="18431-117">Comparing OpenGL ES 2.0 with Direct3D 11</span></span>


<span data-ttu-id="18431-118">OpenGLES2.0 und Direct3D11 sind sich in vielen Bereichen ähnlich.</span><span class="sxs-lookup"><span data-stu-id="18431-118">OpenGL ES 2.0 and Direct3D 11 have many similarities.</span></span> <span data-ttu-id="18431-119">Beide verwenden ähnliche Renderingpipelines und Grafikfunktionen.</span><span class="sxs-lookup"><span data-stu-id="18431-119">They both have similar rendering pipelines and graphics features.</span></span> <span data-ttu-id="18431-120">Bei Direct3D 11 handelt es sich jedoch um eine Renderingimplementierung und API und nicht um eine Spezifikation. OpenGLES2.0 ist dagegen eine Renderingspezifikation und API und keine Implementierung.</span><span class="sxs-lookup"><span data-stu-id="18431-120">But Direct3D 11 is a rendering implementation and API, not a specification; OpenGL ES 2.0 is a rendering specification and API, not an implementation.</span></span> <span data-ttu-id="18431-121">Folgende allgemeine Unterschiede bestehen zwischen Direct3D11 und OpenGLES2.0:</span><span class="sxs-lookup"><span data-stu-id="18431-121">Direct3D 11 and OpenGL ES 2.0 generally differ in these ways:</span></span>

| <span data-ttu-id="18431-122">OpenGL ES2.0</span><span class="sxs-lookup"><span data-stu-id="18431-122">OpenGL ES 2.0</span></span>                                                                                         | <span data-ttu-id="18431-123">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="18431-123">Direct3D 11</span></span>                                                                                                            |
|-------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="18431-124">Hardware- und betriebssystemagnostische Spezifikation mit vom Anbieter bereitgestellten Implementierungen.</span><span class="sxs-lookup"><span data-stu-id="18431-124">Hardware and operating system agnostic specification with vendor provided implementations</span></span>             | <span data-ttu-id="18431-125">Microsoft-Implementierung der Hardwareabstraktion und -zertifizierung auf Windows-Plattformen.</span><span class="sxs-lookup"><span data-stu-id="18431-125">Microsoft implementation of hardware abstraction and certification on Windows platforms</span></span>                                |
| <span data-ttu-id="18431-126">Allgemein gehalten, um unterschiedliche Hardware zu unterstützen. Die meisten Ressourcen werden von der Runtime verwaltet.</span><span class="sxs-lookup"><span data-stu-id="18431-126">Abstracted for hardware diversity, runtime manages most resources</span></span>                                     | <span data-ttu-id="18431-127">Direkter Zugriff auf das Hardwarelayout. Ressourcen und Verarbeitung können von der App verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="18431-127">Direct access to hardware layout; app can manage resources and processing</span></span>                                              |
| <span data-ttu-id="18431-128">Stellt Module auf höherer Ebene über Drittanbieterbibliotheken bereit (z.B. Simple DirectMedia Layer, SDL).</span><span class="sxs-lookup"><span data-stu-id="18431-128">Provides higher-level modules via third-party libraries (for example, Simple DirectMedia Layer (SDL))</span></span> | <span data-ttu-id="18431-129">Module auf höherer Ebene wie Direct2D werden basierend auf Modulen auf niedrigerer Eben erstellt, um die Entwicklung für Windows-Apps zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="18431-129">Higher-level modules, like Direct2D, are built upon lower modules to simplify development for Windows apps</span></span>             |
| <span data-ttu-id="18431-130">Unterscheidung von Hardwareanbietern anhand von Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="18431-130">Hardware vendors differentiate via extensions</span></span>                                                         | <span data-ttu-id="18431-131">Microsoft fügt der API optionale Funktionen in generischer Form hinzu, sodass sie nicht speziell für einen bestimmten Hardwareanbieter gelten.</span><span class="sxs-lookup"><span data-stu-id="18431-131">Microsoft adds optional features to the API in a generic way so they aren't specific to any particular hardware vendor</span></span> |

 

<span data-ttu-id="18431-132">Folgende allgemeine Unterschiede bestehen zwischen GLSL und HLSL:</span><span class="sxs-lookup"><span data-stu-id="18431-132">GLSL and HLSL generally differ in these ways:</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="18431-133">GLSL</span><span class="sxs-lookup"><span data-stu-id="18431-133">GLSL</span></span></th>
<th align="left"><span data-ttu-id="18431-134">HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-134">HLSL</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-135">Prozedural, auf Schritte ausgerichtet (ähnlich wie C)</span><span class="sxs-lookup"><span data-stu-id="18431-135">Procedural, step-centric (C like)</span></span></td>
<td align="left"><span data-ttu-id="18431-136">Objektorientiert, auf Daten ausgerichtet (ähnlich wie C++)</span><span class="sxs-lookup"><span data-stu-id="18431-136">Object oriented, data-centric (C++ like)</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="18431-137">In die Grafik-API integrierte Shaderkompilierung</span><span class="sxs-lookup"><span data-stu-id="18431-137">Shader compilation integrated into the graphics API</span></span></td>
<td align="left"><span data-ttu-id="18431-138">Der HLSL-Compiler <a href="https://msdn.microsoft.com/library/windows/desktop/bb509633">kompiliert den Shader</a> in eine binäre Zwischendarstellung, bevor er von Direct3D an den Treiber übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="18431-138">The HLSL compiler <a href="https://msdn.microsoft.com/library/windows/desktop/bb509633">compiles the shader</a> to an intermediate binary representation before Direct3D passes it to the driver.</span></span>
<div class="alert"><span data-ttu-id="18431-139">
<strong>Hinweis:</strong>diese binäre Darstellung ist hardwareunabhängig.</span><span class="sxs-lookup"><span data-stu-id="18431-139">
<strong>Note</strong>This binary representation is hardware independent.</span></span> <span data-ttu-id="18431-140">Sie wird normalerweise beim Erstellen der App und nicht zur Laufzeit kompiliert.</span><span class="sxs-lookup"><span data-stu-id="18431-140">It's typically compiled at app build time, rather than at app run time.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-141"><a href="#porting-glsl-variables-to-hlsl">Variable</a> Speichermodifizierer</span><span class="sxs-lookup"><span data-stu-id="18431-141"><a href="#porting-glsl-variables-to-hlsl">Variable</a> storage modifiers</span></span></td>
<td align="left"><span data-ttu-id="18431-142">Konstantenpuffer und Datenübertragungen über Eingabelayoutdeklarationen</span><span class="sxs-lookup"><span data-stu-id="18431-142">Constant buffers and data transfers via input layout declarations</span></span></td>
</tr>
<tr class="even">
<td align="left"><p><a href="#porting-glsl-types-to-hlsl"><span data-ttu-id="18431-143">Typen</span><span class="sxs-lookup"><span data-stu-id="18431-143">Types</span></span></a></p>
<p><span data-ttu-id="18431-144">Typischer Vektortyp: vec2/3/4</span><span class="sxs-lookup"><span data-stu-id="18431-144">Typical vector type: vec2/3/4</span></span></p>
<p><span data-ttu-id="18431-145">lowp, mediump, highp</span><span class="sxs-lookup"><span data-stu-id="18431-145">lowp, mediump, highp</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-146">Typischer Vektortyp: float2/3/4</span><span class="sxs-lookup"><span data-stu-id="18431-146">Typical vector type: float2/3/4</span></span></p>
<p><span data-ttu-id="18431-147">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="18431-147">min10float, min16float</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-148">texture2D[Funktion]</span><span class="sxs-lookup"><span data-stu-id="18431-148">texture2D [Function]</span></span></td>
<td align="left"><span data-ttu-id="18431-149"><a href="https://msdn.microsoft.com/library/windows/desktop/bb509695">texture.Sample</a> [Datentyp.Funktion]</span><span class="sxs-lookup"><span data-stu-id="18431-149"><a href="https://msdn.microsoft.com/library/windows/desktop/bb509695">texture.Sample</a> [datatype.Function]</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="18431-150">sampler2D[Datentyp]</span><span class="sxs-lookup"><span data-stu-id="18431-150">sampler2D [datatype]</span></span></td>
<td align="left"><span data-ttu-id="18431-151"><a href="https://msdn.microsoft.com/library/windows/desktop/ff471525">Texture2D</a> [Datentyp]</span><span class="sxs-lookup"><span data-stu-id="18431-151"><a href="https://msdn.microsoft.com/library/windows/desktop/ff471525">Texture2D</a> [datatype]</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-152">Zeilenmatrizen (Standard)</span><span class="sxs-lookup"><span data-stu-id="18431-152">Row-major matrices (default)</span></span></td>
<td align="left"><span data-ttu-id="18431-153">Spaltenmatrizen (Standard)</span><span class="sxs-lookup"><span data-stu-id="18431-153">Column-major matrices (default)</span></span>
<div class="alert"><span data-ttu-id="18431-154">
<strong>Hinweis:</strong>  <strong>Row_major</strong> -Typmodifizierer verwenden, um das Layout für eine Variable zu ändern.</span><span class="sxs-lookup"><span data-stu-id="18431-154">
<strong>Note</strong> Use the <strong>row_major</strong> type-modifier to change the layout for one variable.</span></span> <span data-ttu-id="18431-155">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509706">Variablensyntax</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-155">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509706">Variable Syntax</a>.</span></span> <span data-ttu-id="18431-156">Sie können auch ein Compilerkennzeichen oder ein Pragma angeben, um den globalen Standardwert zu ändern.</span><span class="sxs-lookup"><span data-stu-id="18431-156">You can also specify a compiler flag or a pragma to change the global default.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="18431-157">Fragment-Shader</span><span class="sxs-lookup"><span data-stu-id="18431-157">Fragment shader</span></span></td>
<td align="left"><span data-ttu-id="18431-158">Pixelshader</span><span class="sxs-lookup"><span data-stu-id="18431-158">Pixel shader</span></span></td>
</tr>
</tbody>
</table>

 

> <span data-ttu-id="18431-159">**Hinweis:** HLSL sind Texturen und Sampler zwei separate Objekte.</span><span class="sxs-lookup"><span data-stu-id="18431-159">**Note**HLSL has textures and samplers as two separate objects.</span></span> <span data-ttu-id="18431-160">In GLSL ist die Texturbindung wie bei Direct3D9 Teil des Samplerstatus.</span><span class="sxs-lookup"><span data-stu-id="18431-160">In GLSL, like Direct3D 9, the texture binding is part of the sampler state.</span></span>

 

<span data-ttu-id="18431-161">In GLSL stellen Sie einen Großteil des OpenGL-Status in Form von vordefinierten globalen Variablen dar.</span><span class="sxs-lookup"><span data-stu-id="18431-161">In GLSL, you present much of the OpenGL state as pre-defined global variables.</span></span> <span data-ttu-id="18431-162">Bei GLSL verwenden Sie z.B. die **gl\_Position**-Variable zum Angeben der Vertexposition und die **gl\_FragColor**-Variable zum Angeben der Fragmentfarbe.</span><span class="sxs-lookup"><span data-stu-id="18431-162">For example, with GLSL, you use the **gl\_Position** variable to specify vertex position and the **gl\_FragColor** variable to specify fragment color.</span></span> <span data-ttu-id="18431-163">In HLSL übergeben Sie den Direct3D-Status explizit vom App-Code an den Shader.</span><span class="sxs-lookup"><span data-stu-id="18431-163">In HLSL, you pass Direct3D state explicitly from the app code to the shader.</span></span> <span data-ttu-id="18431-164">Bei Direct3D und HLSL muss die Eingabe für den Vertex-Shader z.B. dem Datumsformat im Scheitelpunktpuffer entsprechen, und die Struktur eines Konstantenpuffers im App-Code muss mit der Struktur eines Konstantenpuffers ([cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581)) im Shadercode übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="18431-164">For example, with Direct3D and HLSL, the input to the vertex shader must match the data format in the vertex buffer, and the structure of a constant buffer in the app code must match the structure of a constant buffer ([cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581)) in shader code.</span></span>

## <a name="porting-glsl-variables-to-hlsl"></a><span data-ttu-id="18431-165">Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-165">Porting GLSL variables to HLSL</span></span>


<span data-ttu-id="18431-166">In GLSL wenden Sie Modifizierer (Qualifizierer) auf eine globale Shadervariablendeklaration an, um in den Shadern ein bestimmtes Verhalten der Variable zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="18431-166">In GLSL, you apply modifiers (qualifiers) to a global shader variable declaration to give that variable a specific behavior in your shaders.</span></span> <span data-ttu-id="18431-167">In HLSL sind diese Modifizierer nicht erforderlich, weil Sie den Shaderfluss mit den Argumenten definieren, die Sie an den Shader übergeben und vom Shader zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="18431-167">In HLSL, you don’t need these modifiers because you define the flow of the shader with the arguments that you pass to your shader and that you return from your shader.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="18431-168">Verhalten von GLSL-Variablen</span><span class="sxs-lookup"><span data-stu-id="18431-168">GLSL variable behavior</span></span></th>
<th align="left"><span data-ttu-id="18431-169">HLSL-Äquivalent</span><span class="sxs-lookup"><span data-stu-id="18431-169">HLSL equivalent</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-170">uniform-Variable</span><span class="sxs-lookup"><span data-stu-id="18431-170">uniform</span></span></strong></p>
<p><span data-ttu-id="18431-171">Sie übergeben eine Uniform-Variable vom App-Code in die Vertex- und/oder Fragment-Shader.</span><span class="sxs-lookup"><span data-stu-id="18431-171">You pass a uniform variable from the app code into either or both vertex and fragment shaders.</span></span> <span data-ttu-id="18431-172">Sie müssen die Werte aller Uniform-Variablen festlegen, bevor Sie Dreiecke mit den Shadern zeichnen, damit ihre Werte gleich bleiben, während ein Dreieckgitter gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="18431-172">You must set the values of all uniforms before you draw any triangles with those shaders so their values stay the same throughout the drawing of a triangle mesh.</span></span> <span data-ttu-id="18431-173">Diese Werte sind einheitlich.</span><span class="sxs-lookup"><span data-stu-id="18431-173">These values are uniform.</span></span> <span data-ttu-id="18431-174">Einige Uniform-Variablen werden für den gesamten Frame festgelegt und andere speziell für ein bestimmtes Vertex-/Pixelshaderpaar.</span><span class="sxs-lookup"><span data-stu-id="18431-174">Some uniforms are set for the entire frame and others uniquely to one particular vertex-pixel shader pair.</span></span></p>
<p><span data-ttu-id="18431-175">Uniform-Variablen sind Variablen, die pro Polygon gelten.</span><span class="sxs-lookup"><span data-stu-id="18431-175">Uniform variables are per-polygon variables.</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-176">Verwenden Sie einen Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="18431-176">Use constant buffer.</span></span></p>
<p><span data-ttu-id="18431-177">Siehe <a href="https://msdn.microsoft.com/library/windows/desktop/ff476896">So wird's gemacht: Erstellen eines Konstantenpuffers</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/bb509581">Shaderkonstanten</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-177">See <a href="https://msdn.microsoft.com/library/windows/desktop/ff476896">How to: Create a Constant Buffer</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/bb509581">Shader Constants</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-178">variierende Variable</span><span class="sxs-lookup"><span data-stu-id="18431-178">varying</span></span></strong></p>
<p><span data-ttu-id="18431-179">Sie initialisieren eine variierende Variable im Vertex-Shader und übergeben sie an eine identisch benannte variierende Variable im Fragment-Shader.</span><span class="sxs-lookup"><span data-stu-id="18431-179">You initialize a varying variable inside the vertex shader and pass it through to an identically named varying variable in the fragment shader.</span></span> <span data-ttu-id="18431-180">Da der Vertex-Shader nur den Wert der variieRendern Variablen an jedem Scheitelpunkt festlegt, werden diese Werte vom Rasterizer (perspektivisch korrekt) interpoliert, um Pro-Fragment-Werte zu generieren, die dann in den Fragment-Shader übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="18431-180">Because the vertex shader only sets the value of the varying variables at each vertex, the rasterizer interpolates those values (in a perspective-correct manner) to generate per fragment values to pass into the fragment shader.</span></span> <span data-ttu-id="18431-181">Diese Variablen sind bei jedem Dreieck unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="18431-181">These variables vary across each triangle.</span></span></p></td>
<td align="left"><span data-ttu-id="18431-182">Verwenden Sie die vom Vertex-Shader zurückgegebene Struktur als Eingabe für den Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="18431-182">Use the structure that you return from your vertex shader as the input to your pixel shader.</span></span> <span data-ttu-id="18431-183">Stellen Sie sicher, dass die Semantikwerte übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="18431-183">Make sure the semantic values match.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-184">Attribut</span><span class="sxs-lookup"><span data-stu-id="18431-184">attribute</span></span></strong></p>
<p><span data-ttu-id="18431-185">Ein Attribut ist Teil der Beschreibung eines Scheitelpunkts, die Sie vom App-Code an den Vertex-Shader übergeben.</span><span class="sxs-lookup"><span data-stu-id="18431-185">An attribute is a part of the description of a vertex that you pass from the app code to the vertex shader alone.</span></span> <span data-ttu-id="18431-186">Anders als bei einer Uniform-Variable legen Sie den Wert jedes Attributs für jeden Scheitelpunkt fest, sodass jeder Scheitelpunkt einen anderen Wert haben kann.</span><span class="sxs-lookup"><span data-stu-id="18431-186">Unlike a uniform, you set each attribute’s value for each vertex, which, in turn, allows each vertex to have a different value.</span></span> <span data-ttu-id="18431-187">Attributvariablen sind Variablen, die pro Scheitelpunkt gelten.</span><span class="sxs-lookup"><span data-stu-id="18431-187">Attribute variables are per-vertex variables.</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-188">Definieren Sie einen Scheitelpunktpuffer in Ihrem Direct3D-App-Code, und passen Sie ihn an die im Vertex-Shader definierte Scheitelpunkteingabe an.</span><span class="sxs-lookup"><span data-stu-id="18431-188">Define a vertex buffer in your Direct3D app code and match it to the vertex input defined in the vertex shader.</span></span> <span data-ttu-id="18431-189">Optional können Sie einen Indexpuffer definieren.</span><span class="sxs-lookup"><span data-stu-id="18431-189">Optionally, define an index buffer.</span></span> <span data-ttu-id="18431-190">Siehe <a href="https://msdn.microsoft.com/library/windows/desktop/ff476899">So wird's gemacht: Erstellen eines Scheitelpunktpuffers</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/ff476897">So wird's gemacht: Erstellen eines Indexpuffers</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-190">See <a href="https://msdn.microsoft.com/library/windows/desktop/ff476899">How to: Create a Vertex Buffer</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/ff476897">How to: Create an Index Buffer</a>.</span></span></p>
<p><span data-ttu-id="18431-191">Erstellen Sie ein Eingabelayout in Ihrem Direct3D-App-Code, und passen Sie die Semantikwerte an die Werte in der Scheitelpunkteingabe an.</span><span class="sxs-lookup"><span data-stu-id="18431-191">Create an input layout in your Direct3D app code and match semantic values with those in the vertex input.</span></span> <span data-ttu-id="18431-192">Siehe <a href="https://msdn.microsoft.com/library/windows/desktop/bb205117#Create_the_Input_Layout">Erstellen des Eingabelayouts</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-192">See <a href="https://msdn.microsoft.com/library/windows/desktop/bb205117#Create_the_Input_Layout">Create the input layout</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-193">const</span><span class="sxs-lookup"><span data-stu-id="18431-193">const</span></span></strong></p>
<p><span data-ttu-id="18431-194">Konstanten werden in den Shader kompiliert und ändern sich nie.</span><span class="sxs-lookup"><span data-stu-id="18431-194">Constants that are compiled into the shader and never change.</span></span></p></td>
<td align="left"><span data-ttu-id="18431-195">Verwenden Sie <strong>static const</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-195">Use a <strong>static const</strong>.</span></span> <span data-ttu-id="18431-196"><strong>static</strong> bedeutet, dass der Wert nicht für Konstantenpuffer verfügbar gemacht wird, und <strong>const</strong> bedeutet, dass der Wert nicht vom Shader geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="18431-196"><strong>static</strong> means the value isn't exposed to constant buffers, <strong>const</strong> means the shader can't change the value.</span></span> <span data-ttu-id="18431-197">Der Wert wird also zur Kompilierzeit anhand seines Initialisierers bekannt gemacht.</span><span class="sxs-lookup"><span data-stu-id="18431-197">So, the value is known at compile time based on its initializer.</span></span></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="18431-198">In GLSL sind Variablen ohne Modifizierer einfach normale globale Variablen, die für jeden Shader privat sind.</span><span class="sxs-lookup"><span data-stu-id="18431-198">In GLSL, variables without modifiers are just ordinary global variables that are private to each shader.</span></span>

<span data-ttu-id="18431-199">Wenn Sie Daten an Texturen ([Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) in HLSL) und ihre zugehörigen Sampler ([SamplerState](https://msdn.microsoft.com/library/windows/desktop/bb509644) in HLSL) übergeben, deklarieren Sie sie in der Regel als globale Variablen im Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="18431-199">When you pass data to textures ([Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) in HLSL) and their associated samplers ([SamplerState](https://msdn.microsoft.com/library/windows/desktop/bb509644) in HLSL), you typically declare them as global variables in the pixel shader.</span></span>

## <a name="porting-glsl-types-to-hlsl"></a><span data-ttu-id="18431-200">Portieren von GLSL-Typen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-200">Porting GLSL types to HLSL</span></span>


<span data-ttu-id="18431-201">Ziehen Sie beim Portieren Ihrer GLSL-Typen zu HLSL die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="18431-201">Use this table to port your GLSL types to HLSL.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="18431-202">GLSL-Typ</span><span class="sxs-lookup"><span data-stu-id="18431-202">GLSL type</span></span></th>
<th align="left"><span data-ttu-id="18431-203">HLSL-Typ</span><span class="sxs-lookup"><span data-stu-id="18431-203">HLSL type</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-204">Skalare Typen: float, int, bool</span><span class="sxs-lookup"><span data-stu-id="18431-204">scalar types: float, int, bool</span></span></td>
<td align="left"><p><span data-ttu-id="18431-205">Skalare Typen: float, int, bool</span><span class="sxs-lookup"><span data-stu-id="18431-205">scalar types: float, int, bool</span></span></p>
<p><span data-ttu-id="18431-206">also,uint, double</span><span class="sxs-lookup"><span data-stu-id="18431-206">also, uint, double</span></span></p>
<p><span data-ttu-id="18431-207">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509646">Skalare Typen</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-207">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509646">Scalar Types</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="18431-208">Vektortyp</span><span class="sxs-lookup"><span data-stu-id="18431-208">vector type</span></span></p>
<ul>
<li><span data-ttu-id="18431-209">Gleitkommavektor: vec2, vec3, vec4</span><span class="sxs-lookup"><span data-stu-id="18431-209">floating-point vector: vec2, vec3, vec4</span></span></li>
<li><span data-ttu-id="18431-210">Boolescher Vektor: bvec2, bvec3, bvec4</span><span class="sxs-lookup"><span data-stu-id="18431-210">Boolean vector: bvec2, bvec3, bvec4</span></span></li>
<li><span data-ttu-id="18431-211">Ganzzahlvektor mit Vorzeichen: ivec2, ivec3, ivec4</span><span class="sxs-lookup"><span data-stu-id="18431-211">signed integer vector: ivec2, ivec3, ivec4</span></span></li>
</ul></td>
<td align="left"><p><span data-ttu-id="18431-212">Vektortyp</span><span class="sxs-lookup"><span data-stu-id="18431-212">vector type</span></span></p>
<ul>
<li><span data-ttu-id="18431-213">float2, float3, float4 und float1</span><span class="sxs-lookup"><span data-stu-id="18431-213">float2, float3, float4, and float1</span></span></li>
<li><span data-ttu-id="18431-214">bool2, bool3, bool4 und bool1</span><span class="sxs-lookup"><span data-stu-id="18431-214">bool2, bool3, bool4, and bool1</span></span></li>
<li><span data-ttu-id="18431-215">int2, int3, int4 und int1</span><span class="sxs-lookup"><span data-stu-id="18431-215">int2, int3, int4, and int1</span></span></li>
<li><p><span data-ttu-id="18431-216">Die folgenden Typen haben zudem Vektorerweiterungen, die "float", "bool" und "int" ähneln:</span><span class="sxs-lookup"><span data-stu-id="18431-216">These types also have vector expansions similar to float, bool, and int:</span></span></p>
<ul>
<li><span data-ttu-id="18431-217">uint</span><span class="sxs-lookup"><span data-stu-id="18431-217">uint</span></span></li>
<li><span data-ttu-id="18431-218">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="18431-218">min10float, min16float</span></span></li>
<li><span data-ttu-id="18431-219">min12int, min16int</span><span class="sxs-lookup"><span data-stu-id="18431-219">min12int, min16int</span></span></li>
<li><span data-ttu-id="18431-220">min16uint</span><span class="sxs-lookup"><span data-stu-id="18431-220">min16uint</span></span></li>
</ul></li>
</ul>
<p><span data-ttu-id="18431-221">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509707">Vektortyp</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/bb509568">Schlüsselwörter</a></span><span class="sxs-lookup"><span data-stu-id="18431-221">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509707">Vector Type</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/bb509568">Keywords</a>.</span></span></p>
<p><span data-ttu-id="18431-222">Der Vektor verfügt auch über eine Typdefinition "float4" (typedef vector &lt;float, 4&gt; vector;).</span><span class="sxs-lookup"><span data-stu-id="18431-222">vector is also type defined as float4 (typedef vector &lt;float, 4&gt; vector;).</span></span> <span data-ttu-id="18431-223">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509702">Benutzerdefinierter Typ</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-223">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509702">User-Defined Type</a>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="18431-224">Matrixtyp</span><span class="sxs-lookup"><span data-stu-id="18431-224">matrix type</span></span></p>
<ul>
<li><span data-ttu-id="18431-225">mat2: 2x2-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="18431-225">mat2: 2x2 float matrix</span></span></li>
<li><span data-ttu-id="18431-226">mat3: 3x3-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="18431-226">mat3: 3x3 float matrix</span></span></li>
<li><span data-ttu-id="18431-227">mat4: 4x4-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="18431-227">mat4: 4x4 float matrix</span></span></li>
</ul></td>
<td align="left"><p><span data-ttu-id="18431-228">Matrixtyp</span><span class="sxs-lookup"><span data-stu-id="18431-228">matrix type</span></span></p>
<ul>
<li><span data-ttu-id="18431-229">float2x2</span><span class="sxs-lookup"><span data-stu-id="18431-229">float2x2</span></span></li>
<li><span data-ttu-id="18431-230">float3x3</span><span class="sxs-lookup"><span data-stu-id="18431-230">float3x3</span></span></li>
<li><span data-ttu-id="18431-231">float4x4</span><span class="sxs-lookup"><span data-stu-id="18431-231">float4x4</span></span></li>
<li><span data-ttu-id="18431-232">Auch: float1x1, float1x2, float1x3, float1x4, float2x1, float2x3, float2x4, float3x1, float3x2, float3x4, float4x1, float4x2, float4x3</span><span class="sxs-lookup"><span data-stu-id="18431-232">also, float1x1, float1x2, float1x3, float1x4, float2x1, float2x3, float2x4, float3x1, float3x2, float3x4, float4x1, float4x2, float4x3</span></span></li>
<li><p><span data-ttu-id="18431-233">Die folgenden Typen haben zudem Matrixerweiterungen, die "float" ähneln:</span><span class="sxs-lookup"><span data-stu-id="18431-233">These types also have matrix expansions similar to float:</span></span></p>
<ul>
<li><span data-ttu-id="18431-234">int, uint, bool</span><span class="sxs-lookup"><span data-stu-id="18431-234">int, uint, bool</span></span></li>
<li><span data-ttu-id="18431-235">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="18431-235">min10float, min16float</span></span></li>
<li><span data-ttu-id="18431-236">min12int, min16int</span><span class="sxs-lookup"><span data-stu-id="18431-236">min12int, min16int</span></span></li>
<li><span data-ttu-id="18431-237">min16uint</span><span class="sxs-lookup"><span data-stu-id="18431-237">min16uint</span></span></li>
</ul></li>
</ul>
<p><span data-ttu-id="18431-238">Sie können auch den <a href="https://msdn.microsoft.com/library/windows/desktop/bb509623">Matrixtyp</a> verwenden, um eine Matrix zu definieren.</span><span class="sxs-lookup"><span data-stu-id="18431-238">You can also use the <a href="https://msdn.microsoft.com/library/windows/desktop/bb509623">matrix type</a> to define a matrix.</span></span></p>
<p><span data-ttu-id="18431-239">Beispiel: matrix &lt;float, 2, 2&gt; fMatrix = {0.0f, 0.1, 2.1f, 2.2f};</span><span class="sxs-lookup"><span data-stu-id="18431-239">For example: matrix &lt;float, 2, 2&gt; fMatrix = {0.0f, 0.1, 2.1f, 2.2f};</span></span></p>
<p><span data-ttu-id="18431-240">Die Matrix verfügt auch über eine Typdefinition "float4x4" (typedef matrix &lt;float, 4, 4&gt; matrix;).</span><span class="sxs-lookup"><span data-stu-id="18431-240">matrix is also type defined as float4x4 (typedef matrix &lt;float, 4, 4&gt; matrix;).</span></span> <span data-ttu-id="18431-241">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509702">Benutzerdefinierter Typ</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-241">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509702">User-Defined Type</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="18431-242">Genauigkeitsqualifizierer für "float", "int" und "sampler"</span><span class="sxs-lookup"><span data-stu-id="18431-242">precision qualifiers for float, int, sampler</span></span></p>
<ul>
<li><p><span data-ttu-id="18431-243">highp</span><span class="sxs-lookup"><span data-stu-id="18431-243">highp</span></span></p>
<p><span data-ttu-id="18431-244">Dieser Qualifizierer dient für minimale Genauigkeitsanforderungen, die größer sind als die Anforderungen von "min16float" und kleiner als ein ganzer 32-Bit-Float-Wert.</span><span class="sxs-lookup"><span data-stu-id="18431-244">This qualifier provides minimum precision requirements that are greater than that provided by min16float and less than a full 32-bit float.</span></span> <span data-ttu-id="18431-245">Äquivalent in HLSL:</span><span class="sxs-lookup"><span data-stu-id="18431-245">Equivalent in HLSL is:</span></span></p>
<p><span data-ttu-id="18431-246">highp float -&gt; float</span><span class="sxs-lookup"><span data-stu-id="18431-246">highp float -&gt; float</span></span></p>
<p><span data-ttu-id="18431-247">highp int -&gt; int</span><span class="sxs-lookup"><span data-stu-id="18431-247">highp int -&gt; int</span></span></p></li>
<li><p><span data-ttu-id="18431-248">mediump</span><span class="sxs-lookup"><span data-stu-id="18431-248">mediump</span></span></p>
<p><span data-ttu-id="18431-249">Dieser auf float und int angewendete Qualifizierer entspricht min16float und min12int in HLSL.</span><span class="sxs-lookup"><span data-stu-id="18431-249">This qualifier applied to float and int is equivalent to min16float and min12int in HLSL.</span></span> <span data-ttu-id="18431-250">Mindestens 10Bits Mantisse (nicht wie "min10float").</span><span class="sxs-lookup"><span data-stu-id="18431-250">Minimum 10 bits of mantissa, not like min10float.</span></span></p></li>
<li><p><span data-ttu-id="18431-251">lowp</span><span class="sxs-lookup"><span data-stu-id="18431-251">lowp</span></span></p>
<p><span data-ttu-id="18431-252">Dieser auf "float" angewendete Qualifizierer bietet einen Gleitkommabereich von -2bis2.</span><span class="sxs-lookup"><span data-stu-id="18431-252">This qualifier applied to float provides a floating point range of -2 to 2.</span></span> <span data-ttu-id="18431-253">Entspricht „min10float“ in HLSL.</span><span class="sxs-lookup"><span data-stu-id="18431-253">Equivalent to min10float in HLSL.</span></span></p></li>
</ul></td>
<td align="left"><p><span data-ttu-id="18431-254">Genauigkeitstypen</span><span class="sxs-lookup"><span data-stu-id="18431-254">precision types</span></span></p>
<ul>
<li><span data-ttu-id="18431-255">min16float: min. 16-Bit-Gleitkommawert</span><span class="sxs-lookup"><span data-stu-id="18431-255">min16float: minimum 16-bit floating point value</span></span></li>
<li><p><span data-ttu-id="18431-256">min10float</span><span class="sxs-lookup"><span data-stu-id="18431-256">min10float</span></span></p>
<p><span data-ttu-id="18431-257">Min. 2.8-Bit-Festpunktwert mit Vorzeichen (2Bits ganze Zahl und 8Bits Nachkommakomponente).</span><span class="sxs-lookup"><span data-stu-id="18431-257">Minimum fixed-point signed 2.8 bit value (2 bits of whole number and 8 bits fractional component).</span></span> <span data-ttu-id="18431-258">Die 8-Bit-Nachkommakomponente kann inklusive1 sein (anstelle von exklusive), um den kompletten Bereich von -2bis2 zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="18431-258">The 8-bit fractional component can be inclusive of 1 instead of exclusive to give it the full inclusive range of -2 to 2.</span></span></p></li>
<li><span data-ttu-id="18431-259">min16int: min. 16-Bit-Ganzzahl mit Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="18431-259">min16int: minimum 16-bit signed integer</span></span></li>
<li><p><span data-ttu-id="18431-260">min12int: min. 12-Bit-Ganzzahl mit Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="18431-260">min12int: minimum 12-bit signed integer</span></span></p>
<p><span data-ttu-id="18431-261">Dieser Typ dient für "10Level9" (<a href="https://msdn.microsoft.com/library/windows/desktop/ff476876">9_x-Funktionsebenen</a>). Ganze Zahlen werden dort durch Gleitkommazahlen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="18431-261">This type is for 10Level9 (<a href="https://msdn.microsoft.com/library/windows/desktop/ff476876">9_x feature levels</a>) in which integers are represented by floating point numbers.</span></span> <span data-ttu-id="18431-262">Dies ist die Genauigkeit, die Sie erhalten, wenn Sie eine ganze Zahl mit einer 16-Bit-Gleitkommazahl emulieren.</span><span class="sxs-lookup"><span data-stu-id="18431-262">This is the precision you can get when you emulate an integer with a 16-bit floating point number.</span></span></p></li>
<li><span data-ttu-id="18431-263">min16uint: min. 16-Bit-Ganzzahl ohne Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="18431-263">min16uint: minimum 16-bit unsigned integer</span></span></li>
</ul>
<p><span data-ttu-id="18431-264">Weitere Informationen finden Sie unter <a href="https://msdn.microsoft.com/library/windows/desktop/bb509646">Skalare Typen</a> und <a href="https://msdn.microsoft.com/library/windows/desktop/hh968108">Verwenden der HLSL-Mindestgenauigkeit</a>.</span><span class="sxs-lookup"><span data-stu-id="18431-264">For more info, see <a href="https://msdn.microsoft.com/library/windows/desktop/bb509646">Scalar Types</a> and <a href="https://msdn.microsoft.com/library/windows/desktop/hh968108">Using HLSL minimum precision</a>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="18431-265">sampler2D</span><span class="sxs-lookup"><span data-stu-id="18431-265">sampler2D</span></span></td>
<td align="left"><a href="https://msdn.microsoft.com/library/windows/desktop/ff471525"><span data-ttu-id="18431-266">Texture2D</span><span class="sxs-lookup"><span data-stu-id="18431-266">Texture2D</span></span></a></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="18431-267">samplerCube</span><span class="sxs-lookup"><span data-stu-id="18431-267">samplerCube</span></span></td>
<td align="left"><a href="https://msdn.microsoft.com/library/windows/desktop/bb509700"><span data-ttu-id="18431-268">TextureCube</span><span class="sxs-lookup"><span data-stu-id="18431-268">TextureCube</span></span></a></td>
</tr>
</tbody>
</table>

 

## <a name="porting-glsl-pre-defined-global-variables-to-hlsl"></a><span data-ttu-id="18431-269">Portieren von vordefinierten globalen GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-269">Porting GLSL pre-defined global variables to HLSL</span></span>


<span data-ttu-id="18431-270">Ziehen Sie beim Portieren von vordefinierten globalen GLSL-Variablen zu HLSL die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="18431-270">Use this table to port GLSL pre-defined global variables to HLSL.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="18431-271">Vordefinierte globale GLSL-Variable</span><span class="sxs-lookup"><span data-stu-id="18431-271">GLSL pre-defined global variable</span></span></th>
<th align="left"><span data-ttu-id="18431-272">HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="18431-272">HLSL semantics</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-273">gl_Position</span><span class="sxs-lookup"><span data-stu-id="18431-273">gl_Position</span></span></strong></p>
<p><span data-ttu-id="18431-274">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-274">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="18431-275">Scheitelpunktposition</span><span class="sxs-lookup"><span data-stu-id="18431-275">Vertex position</span></span></p>
<p><span data-ttu-id="18431-276">Beispiel: - gl_Position = position;</span><span class="sxs-lookup"><span data-stu-id="18431-276">for example - gl_Position = position;</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-277">SV_Position</span><span class="sxs-lookup"><span data-stu-id="18431-277">SV_Position</span></span></p>
<p><span data-ttu-id="18431-278">POSITION in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-278">POSITION in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-279">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-279">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="18431-280">Ausgabe des Vertex-Shaders</span><span class="sxs-lookup"><span data-stu-id="18431-280">Vertex shader output</span></span></p>
<p><span data-ttu-id="18431-281">Scheitelpunktposition</span><span class="sxs-lookup"><span data-stu-id="18431-281">Vertex position</span></span></p>
<p><span data-ttu-id="18431-282">Beispiel: - float4 vPosition : SV_Position;</span><span class="sxs-lookup"><span data-stu-id="18431-282">for example - float4 vPosition : SV_Position;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-283">gl_PointSize</span><span class="sxs-lookup"><span data-stu-id="18431-283">gl_PointSize</span></span></strong></p>
<p><span data-ttu-id="18431-284">Diese Variable ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-284">This variable is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="18431-285">Punktgröße</span><span class="sxs-lookup"><span data-stu-id="18431-285">Point size</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-286">PSIZE</span><span class="sxs-lookup"><span data-stu-id="18431-286">PSIZE</span></span></p>
<p><span data-ttu-id="18431-287">Ohne Bedeutung, sofern nicht Direct3D9 das Ziel ist.</span><span class="sxs-lookup"><span data-stu-id="18431-287">No meaning unless you target Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-288">Diese Semantik ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-288">This semantic is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="18431-289">Ausgabe des Vertex-Shaders</span><span class="sxs-lookup"><span data-stu-id="18431-289">Vertex shader output</span></span></p>
<p><span data-ttu-id="18431-290">Punktgröße</span><span class="sxs-lookup"><span data-stu-id="18431-290">Point size</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-291">gl_FragColor</span><span class="sxs-lookup"><span data-stu-id="18431-291">gl_FragColor</span></span></strong></p>
<p><span data-ttu-id="18431-292">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-292">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="18431-293">Fragmentfarbe</span><span class="sxs-lookup"><span data-stu-id="18431-293">Fragment color</span></span></p>
<p><span data-ttu-id="18431-294">Beispiel: - gl_FragColor = vec4(colorVarying, 1.0);</span><span class="sxs-lookup"><span data-stu-id="18431-294">for example - gl_FragColor = vec4(colorVarying, 1.0);</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-295">SV_Target</span><span class="sxs-lookup"><span data-stu-id="18431-295">SV_Target</span></span></p>
<p><span data-ttu-id="18431-296">COLOR in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-296">COLOR in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-297">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-297">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="18431-298">Ausgabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="18431-298">Pixel shader output</span></span></p>
<p><span data-ttu-id="18431-299">Pixelfarbe</span><span class="sxs-lookup"><span data-stu-id="18431-299">Pixel color</span></span></p>
<p><span data-ttu-id="18431-300">Beispiel: - float4 Color[4] : SV_Target;</span><span class="sxs-lookup"><span data-stu-id="18431-300">for example - float4 Color[4] : SV_Target;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-301">gl_FragData[n]</span><span class="sxs-lookup"><span data-stu-id="18431-301">gl_FragData[n]</span></span></strong></p>
<p><span data-ttu-id="18431-302">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-302">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="18431-303">Fragmentfarbe für die Farbzuordnung „n“</span><span class="sxs-lookup"><span data-stu-id="18431-303">Fragment color for color attachment n</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-304">SV_Target[n]</span><span class="sxs-lookup"><span data-stu-id="18431-304">SV_Target[n]</span></span></p>
<p><span data-ttu-id="18431-305">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-305">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="18431-306">Ausgabewert des Pixelshaders, der im Renderziel "n" gespeichert wird, wobei 0 &lt;= n &lt;= 7.</span><span class="sxs-lookup"><span data-stu-id="18431-306">Pixel shader output value that is stored in n render target, where 0 &lt;= n &lt;= 7.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-307">gl_FragCoord</span><span class="sxs-lookup"><span data-stu-id="18431-307">gl_FragCoord</span></span></strong></p>
<p><span data-ttu-id="18431-308">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-308">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="18431-309">Fragmentposition im Framepuffer</span><span class="sxs-lookup"><span data-stu-id="18431-309">Fragment position within frame buffer</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-310">SV_Position</span><span class="sxs-lookup"><span data-stu-id="18431-310">SV_Position</span></span></p>
<p><span data-ttu-id="18431-311">Nicht verfügbar in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-311">Not available in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-312">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-312">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="18431-313">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="18431-313">Pixel shader input</span></span></p>
<p><span data-ttu-id="18431-314">Koordinaten des Bildschirmbereichs</span><span class="sxs-lookup"><span data-stu-id="18431-314">Screen space coordinates</span></span></p>
<p><span data-ttu-id="18431-315">Beispiel: - float4 screenSpace : SV_Position</span><span class="sxs-lookup"><span data-stu-id="18431-315">for example - float4 screenSpace : SV_Position</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-316">gl_FrontFacing</span><span class="sxs-lookup"><span data-stu-id="18431-316">gl_FrontFacing</span></span></strong></p>
<p><span data-ttu-id="18431-317">Diese Variable ist vom Typ <strong>bool</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-317">This variable is type <strong>bool</strong>.</span></span></p>
<p><span data-ttu-id="18431-318">Bestimmt, ob ein Fragment zu einem Vorderseitengrundtyp gehört.</span><span class="sxs-lookup"><span data-stu-id="18431-318">Determines whether fragment belongs to a front-facing primitive.</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-319">SV_IsFrontFace</span><span class="sxs-lookup"><span data-stu-id="18431-319">SV_IsFrontFace</span></span></p>
<p><span data-ttu-id="18431-320">VFACE in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-320">VFACE in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-321">„SV_IsFrontFace“ ist vom Typ <strong>bool</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-321">SV_IsFrontFace is type <strong>bool</strong>.</span></span></p>
<p><span data-ttu-id="18431-322">VFACE ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-322">VFACE is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="18431-323">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="18431-323">Pixel shader input</span></span></p>
<p><span data-ttu-id="18431-324">Grundtypseite</span><span class="sxs-lookup"><span data-stu-id="18431-324">Primitive facing</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="18431-325">gl_PointCoord</span><span class="sxs-lookup"><span data-stu-id="18431-325">gl_PointCoord</span></span></strong></p>
<p><span data-ttu-id="18431-326">Diese Variable ist vom Typ <strong>vec2</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-326">This variable is type <strong>vec2</strong>.</span></span></p>
<p><span data-ttu-id="18431-327">Fragmentposition innerhalb eines Punkts (nur Punktrasterung)</span><span class="sxs-lookup"><span data-stu-id="18431-327">Fragment position within a point (point rasterization only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-328">SV_Position</span><span class="sxs-lookup"><span data-stu-id="18431-328">SV_Position</span></span></p>
<p><span data-ttu-id="18431-329">VPOS in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-329">VPOS in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-330">„SV_Position“ ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-330">SV_Position is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="18431-331">VPOS ist vom Typ <strong>float2</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-331">VPOS is type <strong>float2</strong>.</span></span></p>
<p><span data-ttu-id="18431-332">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="18431-332">Pixel shader input</span></span></p>
<p><span data-ttu-id="18431-333">Pixel- oder Bildpunktposition im Bildschirmbereich</span><span class="sxs-lookup"><span data-stu-id="18431-333">The pixel or sample position in screen space</span></span></p>
<p><span data-ttu-id="18431-334">Beispiel: - float4 pos : SV_Position</span><span class="sxs-lookup"><span data-stu-id="18431-334">for example - float4 pos : SV_Position</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="18431-335">gl_FragDepth</span><span class="sxs-lookup"><span data-stu-id="18431-335">gl_FragDepth</span></span></strong></p>
<p><span data-ttu-id="18431-336">Diese Variable ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-336">This variable is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="18431-337">Tiefenpufferdaten</span><span class="sxs-lookup"><span data-stu-id="18431-337">Depth buffer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="18431-338">SV_Depth</span><span class="sxs-lookup"><span data-stu-id="18431-338">SV_Depth</span></span></p>
<p><span data-ttu-id="18431-339">DEPTH in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="18431-339">DEPTH in Direct3D 9</span></span></p>
<p><span data-ttu-id="18431-340">„SV_Depth“ ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="18431-340">SV_Depth is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="18431-341">Ausgabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="18431-341">Pixel shader output</span></span></p>
<p><span data-ttu-id="18431-342">Tiefenpufferdaten</span><span class="sxs-lookup"><span data-stu-id="18431-342">Depth buffer data</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="18431-343">Geben Sie die Position, Farbe usw. für die Eingabe des Vertex-Shaders und die Eingabe des Pixelshaders mit Semantikwerten an.</span><span class="sxs-lookup"><span data-stu-id="18431-343">You use semantics to specify position, color, and so on for vertex shader input and pixel shader input.</span></span> <span data-ttu-id="18431-344">Die Semantikwerte im Eingabelayout müssen der Eingabe des Vertex-Shaders entsprechen.</span><span class="sxs-lookup"><span data-stu-id="18431-344">You must match the semantics values in the input layout with the vertex shader input.</span></span> <span data-ttu-id="18431-345">Beispiele finden Sie unter [Beispiele für das Portieren von GLSL-Variablen zu HLSL](#examples-of-porting-glsl-variables-to-hlsl).</span><span class="sxs-lookup"><span data-stu-id="18431-345">For examples, see [Examples of porting GLSL variables to HLSL](#examples-of-porting-glsl-variables-to-hlsl).</span></span> <span data-ttu-id="18431-346">Weitere Informationen zur HLSL-Semantik finden Sie unter [Semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span><span class="sxs-lookup"><span data-stu-id="18431-346">For more info about the HLSL semantics, see [Semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span></span>

## <a name="examples-of-porting-glsl-variables-to-hlsl"></a><span data-ttu-id="18431-347">Beispiele für das Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-347">Examples of porting GLSL variables to HLSL</span></span>


<span data-ttu-id="18431-348">Im Folgenden zeigen wir Ihnen Beispiele für die Verwendung von GLSL-Variablen in OpenGL/GLSL-Code und anschließend das entsprechende Beispiel in Direct3D/HLSL-Code.</span><span class="sxs-lookup"><span data-stu-id="18431-348">Here we show examples of using GLSL variables in OpenGL/GLSL code and then the equivalent example in Direct3D/HLSL code.</span></span>

### <a name="uniform-attribute-and-varying-in-glsl"></a><span data-ttu-id="18431-349">Uniform-Variable, Attribut und variierende Variable in GLSL</span><span class="sxs-lookup"><span data-stu-id="18431-349">Uniform, attribute, and varying in GLSL</span></span>

<span data-ttu-id="18431-350">OpenGL-App-Code</span><span class="sxs-lookup"><span data-stu-id="18431-350">OpenGL app code</span></span>

``` syntax
// Uniform values can be set in app code and then processed in the shader code.
uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

// Incoming position of vertex
attribute vec4 position;
 
// Incoming color for the vertex
attribute vec3 color;
 
// The varying variable tells the shader pipeline to pass it  
// on to the fragment shader.
varying vec3 colorVarying;
```

<span data-ttu-id="18431-351">GLSL-Vertex-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="18431-351">GLSL vertex shader code</span></span>

``` syntax
//The shader entry point is the main method.
void main()
{
colorVarying = color; //Use the varying variable to pass the color to the fragment shader
gl_Position = position; //Copy the position to the gl_Position pre-defined global variable
}
```

<span data-ttu-id="18431-352">GLSL-Fragment-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="18431-352">GLSL fragment shader code</span></span>

``` syntax
void main()
{
//Pad the colorVarying vec3 with a 1.0 for alpha to create a vec4 color
//and assign that color to the gl_FragColor pre-defined global variable
//This color then becomes the fragment's color.
gl_FragColor = vec4(colorVarying, 1.0);
}
```

### <a name="constant-buffers-and-data-transfers-in-hlsl"></a><span data-ttu-id="18431-353">Konstantenpuffer und Datenübertragungen in HLSL</span><span class="sxs-lookup"><span data-stu-id="18431-353">Constant buffers and data transfers in HLSL</span></span>

<span data-ttu-id="18431-354">Das folgende Beispiel zeigt, wie Sie Daten an den HLSL-Vertex-Shader übergeben, die anschließend zum Pixelshader übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="18431-354">Here is an example of how you pass data to the HLSL vertex shader that then flows through to the pixel shader.</span></span> <span data-ttu-id="18431-355">Definieren Sie in Ihrem App-Code einen Scheitelpunkt und einen Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="18431-355">In your app code, define a vertex and a constant buffer.</span></span> <span data-ttu-id="18431-356">Definieren Sie anschließend im Vertex-Shader-Code den Konstantenpuffer als [cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581), und speichern Sie die Daten für einzelne Scheitelpunkte und die Eingabedaten des Pixelshaders.</span><span class="sxs-lookup"><span data-stu-id="18431-356">Then, in your vertex shader code, define the constant buffer as a [cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581) and store the per-vertex data and the pixel shader input data.</span></span> <span data-ttu-id="18431-357">Hier verwenden als **VertexShaderInput** und **PixelShaderInput** bezeichnete Strukturen.</span><span class="sxs-lookup"><span data-stu-id="18431-357">Here we use structures called **VertexShaderInput** and **PixelShaderInput**.</span></span>

<span data-ttu-id="18431-358">Direct3D-App-Code</span><span class="sxs-lookup"><span data-stu-id="18431-358">Direct3D app code</span></span>

```cpp
struct ConstantBuffer
{
    XMFLOAT4X4 model;
    XMFLOAT4X4 view;
    XMFLOAT4X4 projection;
};
struct SimpleCubeVertex
{
    XMFLOAT3 pos;   // position
    XMFLOAT3 color; // color
};

 // Create an input layout that matches the layout defined in the vertex shader code.
 const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
 {
     { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0,  0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
     { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
 };

// Create vertex and index buffers that define a geometry.
```

<span data-ttu-id="18431-359">HLSL-Vertex-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="18431-359">HLSL vertex shader code</span></span>

``` syntax
cbuffer ModelViewProjectionCB : register( b0 )
{
    matrix model; 
    matrix view;
    matrix projection;
};
// The POSITION and COLOR semantics must match the semantics in the input layout Direct3D app code.
struct VertexShaderInput
{
    float3 pos : POSITION; // Incoming position of vertex 
    float3 color : COLOR; // Incoming color for the vertex
};

struct PixelShaderInput
{
    float4 pos : SV_Position; // Copy the vertex position.
    float4 color : COLOR; // Pass the color to the pixel shader.
};

PixelShaderInput main(VertexShaderInput input)
{
    PixelShaderInput vertexShaderOutput;

    // shader source code

    return vertexShaderOutput;
}
```

<span data-ttu-id="18431-360">HLSL-Pixelshader-Code</span><span class="sxs-lookup"><span data-stu-id="18431-360">HLSL pixel shader code</span></span>

``` syntax
// Collect input from the vertex shader. 
// The COLOR semantic must match the semantic in the vertex shader code.
struct PixelShaderInput
{
    float4 pos : SV_Position;
    float4 color : COLOR; // Color for the pixel
};

// Set the pixel color value for the renter target. 
float4 main(PixelShaderInput input) : SV_Target
{
    return input.color;
}
```

## <a name="examples-of-porting-opengl-rendering-code-to-direct3d"></a><span data-ttu-id="18431-361">Beispiele für das Portieren von OpenGL-Renderingcode zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="18431-361">Examples of porting OpenGL rendering code to Direct3D</span></span>


<span data-ttu-id="18431-362">Im Folgenden zeigen wir Ihnen ein Beispiel für das Rendering in OpenGLES2.0-Code und anschließend das entsprechende Beispiel in Direct3D11-Code.</span><span class="sxs-lookup"><span data-stu-id="18431-362">Here we show an example of rendering in OpenGL ES 2.0 code and then the equivalent example in Direct3D 11 code.</span></span>

<span data-ttu-id="18431-363">OpenGL-Renderingcode</span><span class="sxs-lookup"><span data-stu-id="18431-363">OpenGL rendering code</span></span>

``` syntax
// Bind shaders to the pipeline. 
// Both vertex shader and fragment shader are in a program.
glUseProgram(m_shader->getProgram());
 
// Input asssembly 
// Get the position and color attributes of the vertex.

m_positionLocation = glGetAttribLocation(m_shader->getProgram(), "position");
glEnableVertexAttribArray(m_positionLocation);

m_colorLocation = glGetAttribColor(m_shader->getProgram(), "color");
glEnableVertexAttribArray(m_colorLocation);
 
// Bind the vertex buffer object to the input assembler.
glBindBuffer(GL_ARRAY_BUFFER, m_geometryBuffer);
glVertexAttribPointer(m_positionLocation, 4, GL_FLOAT, GL_FALSE, 0, NULL);
glBindBuffer(GL_ARRAY_BUFFER, m_colorBuffer);
glVertexAttribPointer(m_colorLocation, 3, GL_FLOAT, GL_FALSE, 0, NULL);
 
// Draw a triangle with 3 vertices.
glDrawArray(GL_TRIANGLES, 0, 3);
```

<span data-ttu-id="18431-364">Direct3D-Renderingcode</span><span class="sxs-lookup"><span data-stu-id="18431-364">Direct3D rendering code</span></span>

```cpp
// Bind the vertex shader and pixel shader to the pipeline.
m_d3dDeviceContext->VSSetShader(vertexShader.Get(),nullptr,0);
m_d3dDeviceContext->PSSetShader(pixelShader.Get(),nullptr,0);
 
// Declare the inputs that the shaders expect.
m_d3dDeviceContext->IASetInputLayout(inputLayout.Get());
m_d3dDeviceContext->IASetVertexBuffers(0, 1, vertexBuffer.GetAddressOf(), &stride, &offset);

// Set the primitive's topology.
m_d3dDeviceContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);

// Draw a triangle with 3 vertices. triangleVertices is an array of 3 vertices.
m_d3dDeviceContext->Draw(ARRAYSIZE(triangleVertices),0);
```

## <a name="related-topics"></a><span data-ttu-id="18431-365">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="18431-365">Related topics</span></span>


* [<span data-ttu-id="18431-366">Portieren von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="18431-366">Port from OpenGL ES 2.0 to Direct3D 11</span></span>](port-from-opengl-es-2-0-to-directx-11-1.md)

 

 




