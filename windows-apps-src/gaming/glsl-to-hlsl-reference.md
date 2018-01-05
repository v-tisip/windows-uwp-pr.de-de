---
author: mtoepke
title: GLSL-zu-HLSL-Referenz
description: "Sie portieren Ihren OpenGL Shader Language (GLSL)-Code zu Microsoft High Level Shader Language (HLSL)-Code, wenn Sie Ihre Grafikarchitektur von OpenGLES2.0 zu Direct3D11 portieren, um ein Spiel für die universelle Windows-Plattform (UWP) zu erstellen."
ms.assetid: 979d19f6-ef0c-64e4-89c2-a31e1c7b7692
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, glsl, hlsl, opengl, directx, Shader
ms.openlocfilehash: f2d5f5a363abf026e865ed07221ba9075a6a67e7
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="glsl-to-hlsl-reference"></a><span data-ttu-id="44dfd-104">GLSL-zu-HLSL-Referenz</span><span class="sxs-lookup"><span data-stu-id="44dfd-104">GLSL-to-HLSL reference</span></span>


<span data-ttu-id="44dfd-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="44dfd-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="44dfd-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="44dfd-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="44dfd-107">Sie portieren Ihren OpenGL Shader Language (GLSL)-Code zu Microsoft High Level Shader Language (HLSL)-Code, wenn Sie Ihre [Grafikarchitektur von OpenGLES2.0 zu Direct3D11 portieren](port-from-opengl-es-2-0-to-directx-11-1.md), um ein Spiel für die universelle Windows-Plattform (UWP) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-107">You port your OpenGL Shader Language (GLSL) code to Microsoft High Level Shader Language (HLSL) code when you [port your graphics architecture from OpenGL ES 2.0 to Direct3D 11](port-from-opengl-es-2-0-to-directx-11-1.md) to create a game for Universal Windows Platform (UWP).</span></span> <span data-ttu-id="44dfd-108">Die hier verwendete GLSL ist kompatibel mit OpenGLES2.0, und die HLSL ist kompatibel mit Direct3D11.</span><span class="sxs-lookup"><span data-stu-id="44dfd-108">The GLSL that is referred to herein is compatible with OpenGL ES 2.0; the HLSL is compatible with Direct3D 11.</span></span> <span data-ttu-id="44dfd-109">Informationen zu den Unterschieden zwischen Direct3D11 und Vorgängerversionen von Direct3D finden Sie unter [Funktionszuordnung](feature-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="44dfd-109">For info about the differences between Direct3D 11 and previous versions of Direct3D, see [Feature mapping](feature-mapping.md).</span></span>

-   [<span data-ttu-id="44dfd-110">Vergleich zwischen OpenGLES2.0 und Direct3D11</span><span class="sxs-lookup"><span data-stu-id="44dfd-110">Comparing OpenGL ES 2.0 with Direct3D 11</span></span>](#comparing-opengl-es-20-with-direct3d-11)
-   [<span data-ttu-id="44dfd-111">Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-111">Porting GLSL variables to HLSL</span></span>](#porting-glsl-variables-to-hlsl)
-   [<span data-ttu-id="44dfd-112">Portieren von GLSL-Typen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-112">Porting GLSL types to HLSL</span></span>](#porting-glsl-types-to-hlsl)
-   [<span data-ttu-id="44dfd-113">Portieren von vordefinierten globalen GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-113">Porting GLSL pre-defined global variables to HLSL</span></span>](#porting-glsl-pre-defined-global-variables-to-hlsl)
-   [<span data-ttu-id="44dfd-114">Beispiele für das Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-114">Examples of porting GLSL variables to HLSL</span></span>](#examples-of-porting-glsl-variables-to-hlsl)
    -   [<span data-ttu-id="44dfd-115">Uniform-Variable, Attribut und variierende Variable in GLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-115">Uniform, attribute, and varying in GLSL</span></span>](#uniform-attribute-and-varying-in-glsl)
    -   [<span data-ttu-id="44dfd-116">Konstantenpuffer und Datenübertragungen in HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-116">Constant buffers and data transfers in HLSL</span></span>](#constant-buffers-and-data-transfers-in-hlsl)
-   [<span data-ttu-id="44dfd-117">Beispiele für das Portieren von OpenGL-Renderingcode zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="44dfd-117">Examples of porting OpenGL rendering code to Direct3D</span></span>](#examples-of-porting-opengl-rendering-code-to-direct3d)
-   [<span data-ttu-id="44dfd-118">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="44dfd-118">Related topics</span></span>](#related-topics)

## <a name="comparing-opengl-es-20-with-direct3d-11"></a><span data-ttu-id="44dfd-119">Vergleich zwischen OpenGLES2.0 und Direct3D11</span><span class="sxs-lookup"><span data-stu-id="44dfd-119">Comparing OpenGL ES 2.0 with Direct3D 11</span></span>


<span data-ttu-id="44dfd-120">OpenGLES2.0 und Direct3D11 sind sich in vielen Bereichen ähnlich.</span><span class="sxs-lookup"><span data-stu-id="44dfd-120">OpenGL ES 2.0 and Direct3D 11 have many similarities.</span></span> <span data-ttu-id="44dfd-121">Beide verwenden ähnliche Renderingpipelines und Grafikfunktionen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-121">They both have similar rendering pipelines and graphics features.</span></span> <span data-ttu-id="44dfd-122">Bei Direct3D 11 handelt es sich jedoch um eine Renderingimplementierung und API und nicht um eine Spezifikation. OpenGLES2.0 ist dagegen eine Renderingspezifikation und API und keine Implementierung.</span><span class="sxs-lookup"><span data-stu-id="44dfd-122">But Direct3D 11 is a rendering implementation and API, not a specification; OpenGL ES 2.0 is a rendering specification and API, not an implementation.</span></span> <span data-ttu-id="44dfd-123">Folgende allgemeine Unterschiede bestehen zwischen Direct3D11 und OpenGLES2.0:</span><span class="sxs-lookup"><span data-stu-id="44dfd-123">Direct3D 11 and OpenGL ES 2.0 generally differ in these ways:</span></span>

| <span data-ttu-id="44dfd-124">OpenGL ES2.0</span><span class="sxs-lookup"><span data-stu-id="44dfd-124">OpenGL ES 2.0</span></span>                                                                                         | <span data-ttu-id="44dfd-125">Direct3D11</span><span class="sxs-lookup"><span data-stu-id="44dfd-125">Direct3D 11</span></span>                                                                                                            |
|-------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="44dfd-126">Hardware- und betriebssystemagnostische Spezifikation mit vom Anbieter bereitgestellten Implementierungen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-126">Hardware and operating system agnostic specification with vendor provided implementations</span></span>             | <span data-ttu-id="44dfd-127">Microsoft-Implementierung der Hardwareabstraktion und -zertifizierung auf Windows-Plattformen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-127">Microsoft implementation of hardware abstraction and certification on Windows platforms</span></span>                                |
| <span data-ttu-id="44dfd-128">Allgemein gehalten, um unterschiedliche Hardware zu unterstützen. Die meisten Ressourcen werden von der Runtime verwaltet.</span><span class="sxs-lookup"><span data-stu-id="44dfd-128">Abstracted for hardware diversity, runtime manages most resources</span></span>                                     | <span data-ttu-id="44dfd-129">Direkter Zugriff auf das Hardwarelayout. Ressourcen und Verarbeitung können von der App verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="44dfd-129">Direct access to hardware layout; app can manage resources and processing</span></span>                                              |
| <span data-ttu-id="44dfd-130">Stellt Module auf höherer Ebene über Drittanbieterbibliotheken bereit (z.B. Simple DirectMedia Layer, SDL).</span><span class="sxs-lookup"><span data-stu-id="44dfd-130">Provides higher-level modules via third-party libraries (for example, Simple DirectMedia Layer (SDL))</span></span> | <span data-ttu-id="44dfd-131">Module auf höherer Ebene wie Direct2D werden basierend auf Modulen auf niedrigerer Eben erstellt, um die Entwicklung für Windows-Apps zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-131">Higher-level modules, like Direct2D, are built upon lower modules to simplify development for Windows apps</span></span>             |
| <span data-ttu-id="44dfd-132">Unterscheidung von Hardwareanbietern anhand von Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-132">Hardware vendors differentiate via extensions</span></span>                                                         | <span data-ttu-id="44dfd-133">Microsoft fügt der API optionale Funktionen in generischer Form hinzu, sodass sie nicht speziell für einen bestimmten Hardwareanbieter gelten.</span><span class="sxs-lookup"><span data-stu-id="44dfd-133">Microsoft adds optional features to the API in a generic way so they aren't specific to any particular hardware vendor</span></span> |

 

<span data-ttu-id="44dfd-134">Folgende allgemeine Unterschiede bestehen zwischen GLSL und HLSL:</span><span class="sxs-lookup"><span data-stu-id="44dfd-134">GLSL and HLSL generally differ in these ways:</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="44dfd-135">GLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-135">GLSL</span></span></th>
<th align="left"><span data-ttu-id="44dfd-136">HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-136">HLSL</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-137">Prozedural, auf Schritte ausgerichtet (ähnlich wie C)</span><span class="sxs-lookup"><span data-stu-id="44dfd-137">Procedural, step-centric (C like)</span></span></td>
<td align="left"><span data-ttu-id="44dfd-138">Objektorientiert, auf Daten ausgerichtet (ähnlich wie C++)</span><span class="sxs-lookup"><span data-stu-id="44dfd-138">Object oriented, data-centric (C++ like)</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="44dfd-139">In die Grafik-API integrierte Shaderkompilierung</span><span class="sxs-lookup"><span data-stu-id="44dfd-139">Shader compilation integrated into the graphics API</span></span></td>
<td align="left"><span data-ttu-id="44dfd-140">Der HLSL-Compiler [kompiliert den Shader](https://msdn.microsoft.com/library/windows/desktop/bb509633) in eine binäre Zwischendarstellung, bevor er von Direct3D an den Treiber übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="44dfd-140">The HLSL compiler [compiles the shader](https://msdn.microsoft.com/library/windows/desktop/bb509633) to an intermediate binary representation before Direct3D passes it to the driver.</span></span>
<div class="alert"><span data-ttu-id="44dfd-141">
<strong>Hinweis</strong>  Diese binäre Darstellung ist hardwareunabhängig.</span><span class="sxs-lookup"><span data-stu-id="44dfd-141">
<strong>Note</strong>  This binary representation is hardware independent.</span></span> <span data-ttu-id="44dfd-142">Sie wird normalerweise beim Erstellen der App und nicht zur Laufzeit kompiliert.</span><span class="sxs-lookup"><span data-stu-id="44dfd-142">It's typically compiled at app build time, rather than at app run time.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-143">[Variable](#porting-glsl-variables-to-hlsl) Speichermodifizierer</span><span class="sxs-lookup"><span data-stu-id="44dfd-143">[Variable](#porting-glsl-variables-to-hlsl) storage modifiers</span></span></td>
<td align="left"><span data-ttu-id="44dfd-144">Konstantenpuffer und Datenübertragungen über Eingabelayoutdeklarationen</span><span class="sxs-lookup"><span data-stu-id="44dfd-144">Constant buffers and data transfers via input layout declarations</span></span></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="44dfd-145">Typen</span><span class="sxs-lookup"><span data-stu-id="44dfd-145">Types</span></span>](#porting-glsl-types-to-hlsl)</p>
<p><span data-ttu-id="44dfd-146">Typischer Vektortyp: vec2/3/4</span><span class="sxs-lookup"><span data-stu-id="44dfd-146">Typical vector type: vec2/3/4</span></span></p>
<p><span data-ttu-id="44dfd-147">lowp, mediump, highp</span><span class="sxs-lookup"><span data-stu-id="44dfd-147">lowp, mediump, highp</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-148">Typischer Vektortyp: float2/3/4</span><span class="sxs-lookup"><span data-stu-id="44dfd-148">Typical vector type: float2/3/4</span></span></p>
<p><span data-ttu-id="44dfd-149">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="44dfd-149">min10float, min16float</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-150">texture2D[Funktion]</span><span class="sxs-lookup"><span data-stu-id="44dfd-150">texture2D [Function]</span></span></td>
<td align="left"><span data-ttu-id="44dfd-151">[texture.Sample](https://msdn.microsoft.com/library/windows/desktop/bb509695) [Datentyp.Funktion]</span><span class="sxs-lookup"><span data-stu-id="44dfd-151">[texture.Sample](https://msdn.microsoft.com/library/windows/desktop/bb509695) [datatype.Function]</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="44dfd-152">sampler2D[Datentyp]</span><span class="sxs-lookup"><span data-stu-id="44dfd-152">sampler2D [datatype]</span></span></td>
<td align="left"><span data-ttu-id="44dfd-153">[Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) [Datentyp]</span><span class="sxs-lookup"><span data-stu-id="44dfd-153">[Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) [datatype]</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-154">Zeilenmatrizen (Standard)</span><span class="sxs-lookup"><span data-stu-id="44dfd-154">Row-major matrices (default)</span></span></td>
<td align="left"><span data-ttu-id="44dfd-155">Spaltenmatrizen (Standard)</span><span class="sxs-lookup"><span data-stu-id="44dfd-155">Column-major matrices (default)</span></span>
<div class="alert"><span data-ttu-id="44dfd-156">
<strong>Hinweis</strong>   Verwenden Sie den <strong>row_major</strong>-Typmodifizierer, um das Layout für eine Variable zu ändern.</span><span class="sxs-lookup"><span data-stu-id="44dfd-156">
<strong>Note</strong>   Use the <strong>row_major</strong> type-modifier to change the layout for one variable.</span></span> <span data-ttu-id="44dfd-157">Weitere Informationen finden Sie unter [Variablensyntax](https://msdn.microsoft.com/library/windows/desktop/bb509706).</span><span class="sxs-lookup"><span data-stu-id="44dfd-157">For more info, see [Variable Syntax](https://msdn.microsoft.com/library/windows/desktop/bb509706).</span></span> <span data-ttu-id="44dfd-158">Sie können auch ein Compilerkennzeichen oder ein Pragma angeben, um den globalen Standardwert zu ändern.</span><span class="sxs-lookup"><span data-stu-id="44dfd-158">You can also specify a compiler flag or a pragma to change the global default.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="44dfd-159">Fragment-Shader</span><span class="sxs-lookup"><span data-stu-id="44dfd-159">Fragment shader</span></span></td>
<td align="left"><span data-ttu-id="44dfd-160">Pixelshader</span><span class="sxs-lookup"><span data-stu-id="44dfd-160">Pixel shader</span></span></td>
</tr>
</tbody>
</table>

 

> <span data-ttu-id="44dfd-161">**Hinweis**  In HLSL sind Texturen und Sampler zwei separate Objekte.</span><span class="sxs-lookup"><span data-stu-id="44dfd-161">**Note**  HLSL has textures and samplers as two separate objects.</span></span> <span data-ttu-id="44dfd-162">In GLSL ist die Texturbindung wie bei Direct3D9 Teil des Samplerstatus.</span><span class="sxs-lookup"><span data-stu-id="44dfd-162">In GLSL, like Direct3D 9, the texture binding is part of the sampler state.</span></span>

 

<span data-ttu-id="44dfd-163">In GLSL stellen Sie einen Großteil des OpenGL-Status in Form von vordefinierten globalen Variablen dar.</span><span class="sxs-lookup"><span data-stu-id="44dfd-163">In GLSL, you present much of the OpenGL state as pre-defined global variables.</span></span> <span data-ttu-id="44dfd-164">Bei GLSL verwenden Sie z.B. die **gl\_Position**-Variable zum Angeben der Vertexposition und die **gl\_FragColor**-Variable zum Angeben der Fragmentfarbe.</span><span class="sxs-lookup"><span data-stu-id="44dfd-164">For example, with GLSL, you use the **gl\_Position** variable to specify vertex position and the **gl\_FragColor** variable to specify fragment color.</span></span> <span data-ttu-id="44dfd-165">In HLSL übergeben Sie den Direct3D-Status explizit vom App-Code an den Shader.</span><span class="sxs-lookup"><span data-stu-id="44dfd-165">In HLSL, you pass Direct3D state explicitly from the app code to the shader.</span></span> <span data-ttu-id="44dfd-166">Bei Direct3D und HLSL muss die Eingabe für den Vertex-Shader z.B. dem Datumsformat im Scheitelpunktpuffer entsprechen, und die Struktur eines Konstantenpuffers im App-Code muss mit der Struktur eines Konstantenpuffers ([cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581)) im Shadercode übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-166">For example, with Direct3D and HLSL, the input to the vertex shader must match the data format in the vertex buffer, and the structure of a constant buffer in the app code must match the structure of a constant buffer ([cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581)) in shader code.</span></span>

## <a name="porting-glsl-variables-to-hlsl"></a><span data-ttu-id="44dfd-167">Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-167">Porting GLSL variables to HLSL</span></span>


<span data-ttu-id="44dfd-168">In GLSL wenden Sie Modifizierer (Qualifizierer) auf eine globale Shadervariablendeklaration an, um in den Shadern ein bestimmtes Verhalten der Variable zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="44dfd-168">In GLSL, you apply modifiers (qualifiers) to a global shader variable declaration to give that variable a specific behavior in your shaders.</span></span> <span data-ttu-id="44dfd-169">In HLSL sind diese Modifizierer nicht erforderlich, weil Sie den Shaderfluss mit den Argumenten definieren, die Sie an den Shader übergeben und vom Shader zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="44dfd-169">In HLSL, you don’t need these modifiers because you define the flow of the shader with the arguments that you pass to your shader and that you return from your shader.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="44dfd-170">Verhalten von GLSL-Variablen</span><span class="sxs-lookup"><span data-stu-id="44dfd-170">GLSL variable behavior</span></span></th>
<th align="left"><span data-ttu-id="44dfd-171">HLSL-Äquivalent</span><span class="sxs-lookup"><span data-stu-id="44dfd-171">HLSL equivalent</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-172">uniform-Variable</span><span class="sxs-lookup"><span data-stu-id="44dfd-172">uniform</span></span></strong></p>
<p><span data-ttu-id="44dfd-173">Sie übergeben eine Uniform-Variable vom App-Code in die Vertex- und/oder Fragment-Shader.</span><span class="sxs-lookup"><span data-stu-id="44dfd-173">You pass a uniform variable from the app code into either or both vertex and fragment shaders.</span></span> <span data-ttu-id="44dfd-174">Sie müssen die Werte aller Uniform-Variablen festlegen, bevor Sie Dreiecke mit den Shadern zeichnen, damit ihre Werte gleich bleiben, während ein Dreieckgitter gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="44dfd-174">You must set the values of all uniforms before you draw any triangles with those shaders so their values stay the same throughout the drawing of a triangle mesh.</span></span> <span data-ttu-id="44dfd-175">Diese Werte sind einheitlich.</span><span class="sxs-lookup"><span data-stu-id="44dfd-175">These values are uniform.</span></span> <span data-ttu-id="44dfd-176">Einige Uniform-Variablen werden für den gesamten Frame festgelegt und andere speziell für ein bestimmtes Vertex-/Pixelshaderpaar.</span><span class="sxs-lookup"><span data-stu-id="44dfd-176">Some uniforms are set for the entire frame and others uniquely to one particular vertex-pixel shader pair.</span></span></p>
<p><span data-ttu-id="44dfd-177">Uniform-Variablen sind Variablen, die pro Polygon gelten.</span><span class="sxs-lookup"><span data-stu-id="44dfd-177">Uniform variables are per-polygon variables.</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-178">Verwenden Sie einen Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="44dfd-178">Use constant buffer.</span></span></p>
<p><span data-ttu-id="44dfd-179">Siehe [So wird's gemacht: Erstellen eines Konstantenpuffers](https://msdn.microsoft.com/library/windows/desktop/ff476896) und [Shaderkonstanten](https://msdn.microsoft.com/library/windows/desktop/bb509581).</span><span class="sxs-lookup"><span data-stu-id="44dfd-179">See [How to: Create a Constant Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476896) and [Shader Constants](https://msdn.microsoft.com/library/windows/desktop/bb509581).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-180">variierende Variable</span><span class="sxs-lookup"><span data-stu-id="44dfd-180">varying</span></span></strong></p>
<p><span data-ttu-id="44dfd-181">Sie initialisieren eine variierende Variable im Vertex-Shader und übergeben sie an eine identisch benannte variierende Variable im Fragment-Shader.</span><span class="sxs-lookup"><span data-stu-id="44dfd-181">You initialize a varying variable inside the vertex shader and pass it through to an identically named varying variable in the fragment shader.</span></span> <span data-ttu-id="44dfd-182">Da der Vertex-Shader nur den Wert der variierenden Variablen an jedem Scheitelpunkt festlegt, werden diese Werte vom Rasterizer (perspektivisch korrekt) interpoliert, um Pro-Fragment-Werte zu generieren, die dann in den Fragment-Shader übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="44dfd-182">Because the vertex shader only sets the value of the varying variables at each vertex, the rasterizer interpolates those values (in a perspective-correct manner) to generate per fragment values to pass into the fragment shader.</span></span> <span data-ttu-id="44dfd-183">Diese Variablen sind bei jedem Dreieck unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="44dfd-183">These variables vary across each triangle.</span></span></p></td>
<td align="left"><span data-ttu-id="44dfd-184">Verwenden Sie die vom Vertex-Shader zurückgegebene Struktur als Eingabe für den Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="44dfd-184">Use the structure that you return from your vertex shader as the input to your pixel shader.</span></span> <span data-ttu-id="44dfd-185">Stellen Sie sicher, dass die Semantikwerte übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-185">Make sure the semantic values match.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-186">Attribut</span><span class="sxs-lookup"><span data-stu-id="44dfd-186">attribute</span></span></strong></p>
<p><span data-ttu-id="44dfd-187">Ein Attribut ist Teil der Beschreibung eines Scheitelpunkts, die Sie vom App-Code an den Vertex-Shader übergeben.</span><span class="sxs-lookup"><span data-stu-id="44dfd-187">An attribute is a part of the description of a vertex that you pass from the app code to the vertex shader alone.</span></span> <span data-ttu-id="44dfd-188">Anders als bei einer Uniform-Variable legen Sie den Wert jedes Attributs für jeden Scheitelpunkt fest, sodass jeder Scheitelpunkt einen anderen Wert haben kann.</span><span class="sxs-lookup"><span data-stu-id="44dfd-188">Unlike a uniform, you set each attribute’s value for each vertex, which, in turn, allows each vertex to have a different value.</span></span> <span data-ttu-id="44dfd-189">Attributvariablen sind Variablen, die pro Scheitelpunkt gelten.</span><span class="sxs-lookup"><span data-stu-id="44dfd-189">Attribute variables are per-vertex variables.</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-190">Definieren Sie einen Scheitelpunktpuffer in Ihrem Direct3D-App-Code, und passen Sie ihn an die im Vertex-Shader definierte Scheitelpunkteingabe an.</span><span class="sxs-lookup"><span data-stu-id="44dfd-190">Define a vertex buffer in your Direct3D app code and match it to the vertex input defined in the vertex shader.</span></span> <span data-ttu-id="44dfd-191">Optional können Sie einen Indexpuffer definieren.</span><span class="sxs-lookup"><span data-stu-id="44dfd-191">Optionally, define an index buffer.</span></span> <span data-ttu-id="44dfd-192">Siehe [So wird's gemacht: Erstellen eines Scheitelpunktpuffers](https://msdn.microsoft.com/library/windows/desktop/ff476899) und [So wird's gemacht: Erstellen eines Indexpuffers](https://msdn.microsoft.com/library/windows/desktop/ff476897).</span><span class="sxs-lookup"><span data-stu-id="44dfd-192">See [How to: Create a Vertex Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476899) and [How to: Create an Index Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476897).</span></span></p>
<p><span data-ttu-id="44dfd-193">Erstellen Sie ein Eingabelayout in Ihrem Direct3D-App-Code, und passen Sie die Semantikwerte an die Werte in der Scheitelpunkteingabe an.</span><span class="sxs-lookup"><span data-stu-id="44dfd-193">Create an input layout in your Direct3D app code and match semantic values with those in the vertex input.</span></span> <span data-ttu-id="44dfd-194">Siehe [Erstellen des Eingabelayouts](https://msdn.microsoft.com/library/windows/desktop/bb205117#Create_the_Input_Layout).</span><span class="sxs-lookup"><span data-stu-id="44dfd-194">See [Create the input layout](https://msdn.microsoft.com/library/windows/desktop/bb205117#Create_the_Input_Layout).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-195">const</span><span class="sxs-lookup"><span data-stu-id="44dfd-195">const</span></span></strong></p>
<p><span data-ttu-id="44dfd-196">Konstanten werden in den Shader kompiliert und ändern sich nie.</span><span class="sxs-lookup"><span data-stu-id="44dfd-196">Constants that are compiled into the shader and never change.</span></span></p></td>
<td align="left"><span data-ttu-id="44dfd-197">Verwenden Sie <strong>static const</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-197">Use a <strong>static const</strong>.</span></span> <span data-ttu-id="44dfd-198"><strong>static</strong> bedeutet, dass der Wert nicht für Konstantenpuffer verfügbar gemacht wird, und <strong>const</strong> bedeutet, dass der Wert nicht vom Shader geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="44dfd-198"><strong>static</strong> means the value isn't exposed to constant buffers, <strong>const</strong> means the shader can't change the value.</span></span> <span data-ttu-id="44dfd-199">Der Wert wird also zur Kompilierzeit anhand seines Initialisierers bekannt gemacht.</span><span class="sxs-lookup"><span data-stu-id="44dfd-199">So, the value is known at compile time based on its initializer.</span></span></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="44dfd-200">In GLSL sind Variablen ohne Modifizierer einfach normale globale Variablen, die für jeden Shader privat sind.</span><span class="sxs-lookup"><span data-stu-id="44dfd-200">In GLSL, variables without modifiers are just ordinary global variables that are private to each shader.</span></span>

<span data-ttu-id="44dfd-201">Wenn Sie Daten an Texturen ([Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) in HLSL) und ihre zugehörigen Sampler ([SamplerState](https://msdn.microsoft.com/library/windows/desktop/bb509644) in HLSL) übergeben, deklarieren Sie sie in der Regel als globale Variablen im Pixelshader.</span><span class="sxs-lookup"><span data-stu-id="44dfd-201">When you pass data to textures ([Texture2D](https://msdn.microsoft.com/library/windows/desktop/ff471525) in HLSL) and their associated samplers ([SamplerState](https://msdn.microsoft.com/library/windows/desktop/bb509644) in HLSL), you typically declare them as global variables in the pixel shader.</span></span>

## <a name="porting-glsl-types-to-hlsl"></a><span data-ttu-id="44dfd-202">Portieren von GLSL-Typen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-202">Porting GLSL types to HLSL</span></span>


<span data-ttu-id="44dfd-203">Ziehen Sie beim Portieren Ihrer GLSL-Typen zu HLSL die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="44dfd-203">Use this table to port your GLSL types to HLSL.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="44dfd-204">GLSL-Typ</span><span class="sxs-lookup"><span data-stu-id="44dfd-204">GLSL type</span></span></th>
<th align="left"><span data-ttu-id="44dfd-205">HLSL-Typ</span><span class="sxs-lookup"><span data-stu-id="44dfd-205">HLSL type</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-206">Skalare Typen: float, int, bool</span><span class="sxs-lookup"><span data-stu-id="44dfd-206">scalar types: float, int, bool</span></span></td>
<td align="left"><p><span data-ttu-id="44dfd-207">Skalare Typen: float, int, bool</span><span class="sxs-lookup"><span data-stu-id="44dfd-207">scalar types: float, int, bool</span></span></p>
<p><span data-ttu-id="44dfd-208">also,uint, double</span><span class="sxs-lookup"><span data-stu-id="44dfd-208">also, uint, double</span></span></p>
<p><span data-ttu-id="44dfd-209">Weitere Informationen finden Sie unter [Skalare Typen](https://msdn.microsoft.com/library/windows/desktop/bb509646).</span><span class="sxs-lookup"><span data-stu-id="44dfd-209">For more info, see [Scalar Types](https://msdn.microsoft.com/library/windows/desktop/bb509646).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="44dfd-210">Vektortyp</span><span class="sxs-lookup"><span data-stu-id="44dfd-210">vector type</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-211">Gleitkommavektor: vec2, vec3, vec4</span><span class="sxs-lookup"><span data-stu-id="44dfd-211">floating-point vector: vec2, vec3, vec4</span></span></li>
<li><span data-ttu-id="44dfd-212">Boolescher Vektor: bvec2, bvec3, bvec4</span><span class="sxs-lookup"><span data-stu-id="44dfd-212">Boolean vector: bvec2, bvec3, bvec4</span></span></li>
<li><span data-ttu-id="44dfd-213">Ganzzahlvektor mit Vorzeichen: ivec2, ivec3, ivec4</span><span class="sxs-lookup"><span data-stu-id="44dfd-213">signed integer vector: ivec2, ivec3, ivec4</span></span></li>
</ul></td>
<td align="left"><p><span data-ttu-id="44dfd-214">Vektortyp</span><span class="sxs-lookup"><span data-stu-id="44dfd-214">vector type</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-215">float2, float3, float4 und float1</span><span class="sxs-lookup"><span data-stu-id="44dfd-215">float2, float3, float4, and float1</span></span></li>
<li><span data-ttu-id="44dfd-216">bool2, bool3, bool4 und bool1</span><span class="sxs-lookup"><span data-stu-id="44dfd-216">bool2, bool3, bool4, and bool1</span></span></li>
<li><span data-ttu-id="44dfd-217">int2, int3, int4 und int1</span><span class="sxs-lookup"><span data-stu-id="44dfd-217">int2, int3, int4, and int1</span></span></li>
<li><p><span data-ttu-id="44dfd-218">Die folgenden Typen haben zudem Vektorerweiterungen, die "float", "bool" und "int" ähneln:</span><span class="sxs-lookup"><span data-stu-id="44dfd-218">These types also have vector expansions similar to float, bool, and int:</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-219">uint</span><span class="sxs-lookup"><span data-stu-id="44dfd-219">uint</span></span></li>
<li><span data-ttu-id="44dfd-220">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="44dfd-220">min10float, min16float</span></span></li>
<li><span data-ttu-id="44dfd-221">min12int, min16int</span><span class="sxs-lookup"><span data-stu-id="44dfd-221">min12int, min16int</span></span></li>
<li><span data-ttu-id="44dfd-222">min16uint</span><span class="sxs-lookup"><span data-stu-id="44dfd-222">min16uint</span></span></li>
</ul></li>
</ul>
<p><span data-ttu-id="44dfd-223">Weitere Informationen finden Sie unter [Vektortyp](https://msdn.microsoft.com/library/windows/desktop/bb509707) und [Schlüsselwörter](https://msdn.microsoft.com/library/windows/desktop/bb509568)</span><span class="sxs-lookup"><span data-stu-id="44dfd-223">For more info, see [Vector Type](https://msdn.microsoft.com/library/windows/desktop/bb509707) and [Keywords](https://msdn.microsoft.com/library/windows/desktop/bb509568).</span></span></p>
<p><span data-ttu-id="44dfd-224">Der Vektor verfügt auch über eine Typdefinition "float4" (typedef vector &lt;float, 4&gt; vector;).</span><span class="sxs-lookup"><span data-stu-id="44dfd-224">vector is also type defined as float4 (typedef vector &lt;float, 4&gt; vector;).</span></span> <span data-ttu-id="44dfd-225">Weitere Informationen finden Sie unter [Benutzerdefinierter Typ](https://msdn.microsoft.com/library/windows/desktop/bb509702).</span><span class="sxs-lookup"><span data-stu-id="44dfd-225">For more info, see [User-Defined Type](https://msdn.microsoft.com/library/windows/desktop/bb509702).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="44dfd-226">Matrixtyp</span><span class="sxs-lookup"><span data-stu-id="44dfd-226">matrix type</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-227">mat2: 2x2-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="44dfd-227">mat2: 2x2 float matrix</span></span></li>
<li><span data-ttu-id="44dfd-228">mat3: 3x3-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="44dfd-228">mat3: 3x3 float matrix</span></span></li>
<li><span data-ttu-id="44dfd-229">mat4: 4x4-Float-Matrix</span><span class="sxs-lookup"><span data-stu-id="44dfd-229">mat4: 4x4 float matrix</span></span></li>
</ul></td>
<td align="left"><p><span data-ttu-id="44dfd-230">Matrixtyp</span><span class="sxs-lookup"><span data-stu-id="44dfd-230">matrix type</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-231">float2x2</span><span class="sxs-lookup"><span data-stu-id="44dfd-231">float2x2</span></span></li>
<li><span data-ttu-id="44dfd-232">float3x3</span><span class="sxs-lookup"><span data-stu-id="44dfd-232">float3x3</span></span></li>
<li><span data-ttu-id="44dfd-233">float4x4</span><span class="sxs-lookup"><span data-stu-id="44dfd-233">float4x4</span></span></li>
<li><span data-ttu-id="44dfd-234">Auch: float1x1, float1x2, float1x3, float1x4, float2x1, float2x3, float2x4, float3x1, float3x2, float3x4, float4x1, float4x2, float4x3</span><span class="sxs-lookup"><span data-stu-id="44dfd-234">also, float1x1, float1x2, float1x3, float1x4, float2x1, float2x3, float2x4, float3x1, float3x2, float3x4, float4x1, float4x2, float4x3</span></span></li>
<li><p><span data-ttu-id="44dfd-235">Die folgenden Typen haben zudem Matrixerweiterungen, die "float" ähneln:</span><span class="sxs-lookup"><span data-stu-id="44dfd-235">These types also have matrix expansions similar to float:</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-236">int, uint, bool</span><span class="sxs-lookup"><span data-stu-id="44dfd-236">int, uint, bool</span></span></li>
<li><span data-ttu-id="44dfd-237">min10float, min16float</span><span class="sxs-lookup"><span data-stu-id="44dfd-237">min10float, min16float</span></span></li>
<li><span data-ttu-id="44dfd-238">min12int, min16int</span><span class="sxs-lookup"><span data-stu-id="44dfd-238">min12int, min16int</span></span></li>
<li><span data-ttu-id="44dfd-239">min16uint</span><span class="sxs-lookup"><span data-stu-id="44dfd-239">min16uint</span></span></li>
</ul></li>
</ul>
<p><span data-ttu-id="44dfd-240">Sie können auch den [Matrixtyp](https://msdn.microsoft.com/library/windows/desktop/bb509623) verwenden, um eine Matrix zu definieren.</span><span class="sxs-lookup"><span data-stu-id="44dfd-240">You can also use the [matrix type](https://msdn.microsoft.com/library/windows/desktop/bb509623) to define a matrix.</span></span></p>
<p><span data-ttu-id="44dfd-241">Beispiel: matrix &lt;float, 2, 2&gt; fMatrix = {0.0f, 0.1, 2.1f, 2.2f};</span><span class="sxs-lookup"><span data-stu-id="44dfd-241">For example: matrix &lt;float, 2, 2&gt; fMatrix = {0.0f, 0.1, 2.1f, 2.2f};</span></span></p>
<p><span data-ttu-id="44dfd-242">Die Matrix verfügt auch über eine Typdefinition "float4x4" (typedef matrix &lt;float, 4, 4&gt; matrix;).</span><span class="sxs-lookup"><span data-stu-id="44dfd-242">matrix is also type defined as float4x4 (typedef matrix &lt;float, 4, 4&gt; matrix;).</span></span> <span data-ttu-id="44dfd-243">Weitere Informationen finden Sie unter [Benutzerdefinierter Typ](https://msdn.microsoft.com/library/windows/desktop/bb509702).</span><span class="sxs-lookup"><span data-stu-id="44dfd-243">For more info, see [User-Defined Type](https://msdn.microsoft.com/library/windows/desktop/bb509702).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="44dfd-244">Genauigkeitsqualifizierer für "float", "int" und "sampler"</span><span class="sxs-lookup"><span data-stu-id="44dfd-244">precision qualifiers for float, int, sampler</span></span></p>
<ul>
<li><p><span data-ttu-id="44dfd-245">highp</span><span class="sxs-lookup"><span data-stu-id="44dfd-245">highp</span></span></p>
<p><span data-ttu-id="44dfd-246">Dieser Qualifizierer dient für minimale Genauigkeitsanforderungen, die größer sind als die Anforderungen von "min16float" und kleiner als ein ganzer 32-Bit-Float-Wert.</span><span class="sxs-lookup"><span data-stu-id="44dfd-246">This qualifier provides minimum precision requirements that are greater than that provided by min16float and less than a full 32-bit float.</span></span> <span data-ttu-id="44dfd-247">Äquivalent in HLSL:</span><span class="sxs-lookup"><span data-stu-id="44dfd-247">Equivalent in HLSL is:</span></span></p>
<p><span data-ttu-id="44dfd-248">highp float -&gt; float</span><span class="sxs-lookup"><span data-stu-id="44dfd-248">highp float -&gt; float</span></span></p>
<p><span data-ttu-id="44dfd-249">highp int -&gt; int</span><span class="sxs-lookup"><span data-stu-id="44dfd-249">highp int -&gt; int</span></span></p></li>
<li><p><span data-ttu-id="44dfd-250">mediump</span><span class="sxs-lookup"><span data-stu-id="44dfd-250">mediump</span></span></p>
<p><span data-ttu-id="44dfd-251">Dieser auf float und int angewendete Qualifizierer entspricht min16float und min12int in HLSL.</span><span class="sxs-lookup"><span data-stu-id="44dfd-251">This qualifier applied to float and int is equivalent to min16float and min12int in HLSL.</span></span> <span data-ttu-id="44dfd-252">Mindestens 10Bits Mantisse (nicht wie "min10float").</span><span class="sxs-lookup"><span data-stu-id="44dfd-252">Minimum 10 bits of mantissa, not like min10float.</span></span></p></li>
<li><p><span data-ttu-id="44dfd-253">lowp</span><span class="sxs-lookup"><span data-stu-id="44dfd-253">lowp</span></span></p>
<p><span data-ttu-id="44dfd-254">Dieser auf "float" angewendete Qualifizierer bietet einen Gleitkommabereich von -2bis2.</span><span class="sxs-lookup"><span data-stu-id="44dfd-254">This qualifier applied to float provides a floating point range of -2 to 2.</span></span> <span data-ttu-id="44dfd-255">Entspricht „min10float“ in HLSL.</span><span class="sxs-lookup"><span data-stu-id="44dfd-255">Equivalent to min10float in HLSL.</span></span></p></li>
</ul></td>
<td align="left"><p><span data-ttu-id="44dfd-256">Genauigkeitstypen</span><span class="sxs-lookup"><span data-stu-id="44dfd-256">precision types</span></span></p>
<ul>
<li><span data-ttu-id="44dfd-257">min16float: min. 16-Bit-Gleitkommawert</span><span class="sxs-lookup"><span data-stu-id="44dfd-257">min16float: minimum 16-bit floating point value</span></span></li>
<li><p><span data-ttu-id="44dfd-258">min10float</span><span class="sxs-lookup"><span data-stu-id="44dfd-258">min10float</span></span></p>
<p><span data-ttu-id="44dfd-259">Min. 2.8-Bit-Festpunktwert mit Vorzeichen (2Bits ganze Zahl und 8Bits Nachkommakomponente).</span><span class="sxs-lookup"><span data-stu-id="44dfd-259">Minimum fixed-point signed 2.8 bit value (2 bits of whole number and 8 bits fractional component).</span></span> <span data-ttu-id="44dfd-260">Die 8-Bit-Nachkommakomponente kann inklusive1 sein (anstelle von exklusive), um den kompletten Bereich von -2bis2 zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="44dfd-260">The 8-bit fractional component can be inclusive of 1 instead of exclusive to give it the full inclusive range of -2 to 2.</span></span></p></li>
<li><span data-ttu-id="44dfd-261">min16int: min. 16-Bit-Ganzzahl mit Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="44dfd-261">min16int: minimum 16-bit signed integer</span></span></li>
<li><p><span data-ttu-id="44dfd-262">min12int: min. 12-Bit-Ganzzahl mit Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="44dfd-262">min12int: minimum 12-bit signed integer</span></span></p>
<p><span data-ttu-id="44dfd-263">Dieser Typ dient für "10Level9" ([9_x-Funktionsebenen](https://msdn.microsoft.com/library/windows/desktop/ff476876)). Ganze Zahlen werden dort durch Gleitkommazahlen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="44dfd-263">This type is for 10Level9 ([9_x feature levels](https://msdn.microsoft.com/library/windows/desktop/ff476876)) in which integers are represented by floating point numbers.</span></span> <span data-ttu-id="44dfd-264">Dies ist die Genauigkeit, die Sie erhalten, wenn Sie eine ganze Zahl mit einer 16-Bit-Gleitkommazahl emulieren.</span><span class="sxs-lookup"><span data-stu-id="44dfd-264">This is the precision you can get when you emulate an integer with a 16-bit floating point number.</span></span></p></li>
<li><span data-ttu-id="44dfd-265">min16uint: min. 16-Bit-Ganzzahl ohne Vorzeichen</span><span class="sxs-lookup"><span data-stu-id="44dfd-265">min16uint: minimum 16-bit unsigned integer</span></span></li>
</ul>
<p><span data-ttu-id="44dfd-266">Weitere Informationen finden Sie unter [Skalare Typen](https://msdn.microsoft.com/library/windows/desktop/bb509646) und [Verwenden der HLSL-Mindestgenauigkeit](https://msdn.microsoft.com/library/windows/desktop/hh968108).</span><span class="sxs-lookup"><span data-stu-id="44dfd-266">For more info, see [Scalar Types](https://msdn.microsoft.com/library/windows/desktop/bb509646) and [Using HLSL minimum precision](https://msdn.microsoft.com/library/windows/desktop/hh968108).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="44dfd-267">sampler2D</span><span class="sxs-lookup"><span data-stu-id="44dfd-267">sampler2D</span></span></td>
<td align="left">[<span data-ttu-id="44dfd-268">Texture2D</span><span class="sxs-lookup"><span data-stu-id="44dfd-268">Texture2D</span></span>](https://msdn.microsoft.com/library/windows/desktop/ff471525)</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="44dfd-269">samplerCube</span><span class="sxs-lookup"><span data-stu-id="44dfd-269">samplerCube</span></span></td>
<td align="left">[<span data-ttu-id="44dfd-270">TextureCube</span><span class="sxs-lookup"><span data-stu-id="44dfd-270">TextureCube</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb509700)</td>
</tr>
</tbody>
</table>

 

## <a name="porting-glsl-pre-defined-global-variables-to-hlsl"></a><span data-ttu-id="44dfd-271">Portieren von vordefinierten globalen GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-271">Porting GLSL pre-defined global variables to HLSL</span></span>


<span data-ttu-id="44dfd-272">Ziehen Sie beim Portieren von vordefinierten globalen GLSL-Variablen zu HLSL die folgende Tabelle zurate.</span><span class="sxs-lookup"><span data-stu-id="44dfd-272">Use this table to port GLSL pre-defined global variables to HLSL.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="44dfd-273">Vordefinierte globale GLSL-Variable</span><span class="sxs-lookup"><span data-stu-id="44dfd-273">GLSL pre-defined global variable</span></span></th>
<th align="left"><span data-ttu-id="44dfd-274">HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="44dfd-274">HLSL semantics</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-275">gl_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-275">gl_Position</span></span></strong></p>
<p><span data-ttu-id="44dfd-276">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-276">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-277">Scheitelpunktposition</span><span class="sxs-lookup"><span data-stu-id="44dfd-277">Vertex position</span></span></p>
<p><span data-ttu-id="44dfd-278">Beispiel: - gl_Position = position;</span><span class="sxs-lookup"><span data-stu-id="44dfd-278">for example - gl_Position = position;</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-279">SV_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-279">SV_Position</span></span></p>
<p><span data-ttu-id="44dfd-280">POSITION in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-280">POSITION in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-281">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-281">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-282">Ausgabe des Vertex-Shaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-282">Vertex shader output</span></span></p>
<p><span data-ttu-id="44dfd-283">Scheitelpunktposition</span><span class="sxs-lookup"><span data-stu-id="44dfd-283">Vertex position</span></span></p>
<p><span data-ttu-id="44dfd-284">Beispiel: - float4 vPosition : SV_Position;</span><span class="sxs-lookup"><span data-stu-id="44dfd-284">for example - float4 vPosition : SV_Position;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-285">gl_PointSize</span><span class="sxs-lookup"><span data-stu-id="44dfd-285">gl_PointSize</span></span></strong></p>
<p><span data-ttu-id="44dfd-286">Diese Variable ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-286">This variable is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-287">Punktgröße</span><span class="sxs-lookup"><span data-stu-id="44dfd-287">Point size</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-288">PSIZE</span><span class="sxs-lookup"><span data-stu-id="44dfd-288">PSIZE</span></span></p>
<p><span data-ttu-id="44dfd-289">Ohne Bedeutung, sofern nicht Direct3D9 das Ziel ist.</span><span class="sxs-lookup"><span data-stu-id="44dfd-289">No meaning unless you target Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-290">Diese Semantik ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-290">This semantic is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-291">Ausgabe des Vertex-Shaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-291">Vertex shader output</span></span></p>
<p><span data-ttu-id="44dfd-292">Punktgröße</span><span class="sxs-lookup"><span data-stu-id="44dfd-292">Point size</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-293">gl_FragColor</span><span class="sxs-lookup"><span data-stu-id="44dfd-293">gl_FragColor</span></span></strong></p>
<p><span data-ttu-id="44dfd-294">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-294">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-295">Fragmentfarbe</span><span class="sxs-lookup"><span data-stu-id="44dfd-295">Fragment color</span></span></p>
<p><span data-ttu-id="44dfd-296">Beispiel: - gl_FragColor = vec4(colorVarying, 1.0);</span><span class="sxs-lookup"><span data-stu-id="44dfd-296">for example - gl_FragColor = vec4(colorVarying, 1.0);</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-297">SV_Target</span><span class="sxs-lookup"><span data-stu-id="44dfd-297">SV_Target</span></span></p>
<p><span data-ttu-id="44dfd-298">COLOR in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-298">COLOR in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-299">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-299">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-300">Ausgabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-300">Pixel shader output</span></span></p>
<p><span data-ttu-id="44dfd-301">Pixelfarbe</span><span class="sxs-lookup"><span data-stu-id="44dfd-301">Pixel color</span></span></p>
<p><span data-ttu-id="44dfd-302">Beispiel: - float4 Color[4] : SV_Target;</span><span class="sxs-lookup"><span data-stu-id="44dfd-302">for example - float4 Color[4] : SV_Target;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-303">gl_FragData[n]</span><span class="sxs-lookup"><span data-stu-id="44dfd-303">gl_FragData[n]</span></span></strong></p>
<p><span data-ttu-id="44dfd-304">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-304">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-305">Fragmentfarbe für die Farbzuordnung „n“</span><span class="sxs-lookup"><span data-stu-id="44dfd-305">Fragment color for color attachment n</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-306">SV_Target[n]</span><span class="sxs-lookup"><span data-stu-id="44dfd-306">SV_Target[n]</span></span></p>
<p><span data-ttu-id="44dfd-307">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-307">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-308">Ausgabewert des Pixelshaders, der im Renderziel "n" gespeichert wird, wobei 0 &lt;= n &lt;= 7.</span><span class="sxs-lookup"><span data-stu-id="44dfd-308">Pixel shader output value that is stored in n render target, where 0 &lt;= n &lt;= 7.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-309">gl_FragCoord</span><span class="sxs-lookup"><span data-stu-id="44dfd-309">gl_FragCoord</span></span></strong></p>
<p><span data-ttu-id="44dfd-310">Diese Variable ist vom Typ <strong>vec4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-310">This variable is type <strong>vec4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-311">Fragmentposition im Framepuffer</span><span class="sxs-lookup"><span data-stu-id="44dfd-311">Fragment position within frame buffer</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-312">SV_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-312">SV_Position</span></span></p>
<p><span data-ttu-id="44dfd-313">Nicht verfügbar in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-313">Not available in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-314">Diese Semantik ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-314">This semantic is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-315">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-315">Pixel shader input</span></span></p>
<p><span data-ttu-id="44dfd-316">Koordinaten des Bildschirmbereichs</span><span class="sxs-lookup"><span data-stu-id="44dfd-316">Screen space coordinates</span></span></p>
<p><span data-ttu-id="44dfd-317">Beispiel: - float4 screenSpace : SV_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-317">for example - float4 screenSpace : SV_Position</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-318">gl_FrontFacing</span><span class="sxs-lookup"><span data-stu-id="44dfd-318">gl_FrontFacing</span></span></strong></p>
<p><span data-ttu-id="44dfd-319">Diese Variable ist vom Typ <strong>bool</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-319">This variable is type <strong>bool</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-320">Bestimmt, ob ein Fragment zu einem Vorderseitengrundtyp gehört.</span><span class="sxs-lookup"><span data-stu-id="44dfd-320">Determines whether fragment belongs to a front-facing primitive.</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-321">SV_IsFrontFace</span><span class="sxs-lookup"><span data-stu-id="44dfd-321">SV_IsFrontFace</span></span></p>
<p><span data-ttu-id="44dfd-322">VFACE in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-322">VFACE in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-323">„SV_IsFrontFace“ ist vom Typ <strong>bool</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-323">SV_IsFrontFace is type <strong>bool</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-324">VFACE ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-324">VFACE is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-325">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-325">Pixel shader input</span></span></p>
<p><span data-ttu-id="44dfd-326">Grundtypseite</span><span class="sxs-lookup"><span data-stu-id="44dfd-326">Primitive facing</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><span data-ttu-id="44dfd-327">gl_PointCoord</span><span class="sxs-lookup"><span data-stu-id="44dfd-327">gl_PointCoord</span></span></strong></p>
<p><span data-ttu-id="44dfd-328">Diese Variable ist vom Typ <strong>vec2</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-328">This variable is type <strong>vec2</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-329">Fragmentposition innerhalb eines Punkts (nur Punktrasterung)</span><span class="sxs-lookup"><span data-stu-id="44dfd-329">Fragment position within a point (point rasterization only)</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-330">SV_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-330">SV_Position</span></span></p>
<p><span data-ttu-id="44dfd-331">VPOS in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-331">VPOS in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-332">„SV_Position“ ist vom Typ <strong>float4</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-332">SV_Position is type <strong>float4</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-333">VPOS ist vom Typ <strong>float2</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-333">VPOS is type <strong>float2</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-334">Eingabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-334">Pixel shader input</span></span></p>
<p><span data-ttu-id="44dfd-335">Pixel- oder Bildpunktposition im Bildschirmbereich</span><span class="sxs-lookup"><span data-stu-id="44dfd-335">The pixel or sample position in screen space</span></span></p>
<p><span data-ttu-id="44dfd-336">Beispiel: - float4 pos : SV_Position</span><span class="sxs-lookup"><span data-stu-id="44dfd-336">for example - float4 pos : SV_Position</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong><span data-ttu-id="44dfd-337">gl_FragDepth</span><span class="sxs-lookup"><span data-stu-id="44dfd-337">gl_FragDepth</span></span></strong></p>
<p><span data-ttu-id="44dfd-338">Diese Variable ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-338">This variable is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-339">Tiefenpufferdaten</span><span class="sxs-lookup"><span data-stu-id="44dfd-339">Depth buffer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="44dfd-340">SV_Depth</span><span class="sxs-lookup"><span data-stu-id="44dfd-340">SV_Depth</span></span></p>
<p><span data-ttu-id="44dfd-341">DEPTH in Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44dfd-341">DEPTH in Direct3D 9</span></span></p>
<p><span data-ttu-id="44dfd-342">„SV_Depth“ ist vom Typ <strong>float</strong>.</span><span class="sxs-lookup"><span data-stu-id="44dfd-342">SV_Depth is type <strong>float</strong>.</span></span></p>
<p><span data-ttu-id="44dfd-343">Ausgabe des Pixelshaders</span><span class="sxs-lookup"><span data-stu-id="44dfd-343">Pixel shader output</span></span></p>
<p><span data-ttu-id="44dfd-344">Tiefenpufferdaten</span><span class="sxs-lookup"><span data-stu-id="44dfd-344">Depth buffer data</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="44dfd-345">Geben Sie die Position, Farbe usw. für die Eingabe des Vertex-Shaders und die Eingabe des Pixelshaders mit Semantikwerten an.</span><span class="sxs-lookup"><span data-stu-id="44dfd-345">You use semantics to specify position, color, and so on for vertex shader input and pixel shader input.</span></span> <span data-ttu-id="44dfd-346">Die Semantikwerte im Eingabelayout müssen der Eingabe des Vertex-Shaders entsprechen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-346">You must match the semantics values in the input layout with the vertex shader input.</span></span> <span data-ttu-id="44dfd-347">Beispiele finden Sie unter [Beispiele für das Portieren von GLSL-Variablen zu HLSL](#examples-of-porting-glsl-variables-to-hlsl).</span><span class="sxs-lookup"><span data-stu-id="44dfd-347">For examples, see [Examples of porting GLSL variables to HLSL](#examples-of-porting-glsl-variables-to-hlsl).</span></span> <span data-ttu-id="44dfd-348">Weitere Informationen zur HLSL-Semantik finden Sie unter [Semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span><span class="sxs-lookup"><span data-stu-id="44dfd-348">For more info about the HLSL semantics, see [Semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span></span>

## <a name="examples-of-porting-glsl-variables-to-hlsl"></a><span data-ttu-id="44dfd-349">Beispiele für das Portieren von GLSL-Variablen zu HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-349">Examples of porting GLSL variables to HLSL</span></span>


<span data-ttu-id="44dfd-350">Im Folgenden zeigen wir Ihnen Beispiele für die Verwendung von GLSL-Variablen in OpenGL/GLSL-Code und anschließend das entsprechende Beispiel in Direct3D/HLSL-Code.</span><span class="sxs-lookup"><span data-stu-id="44dfd-350">Here we show examples of using GLSL variables in OpenGL/GLSL code and then the equivalent example in Direct3D/HLSL code.</span></span>

### <a name="uniform-attribute-and-varying-in-glsl"></a><span data-ttu-id="44dfd-351">Uniform-Variable, Attribut und variierende Variable in GLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-351">Uniform, attribute, and varying in GLSL</span></span>

<span data-ttu-id="44dfd-352">OpenGL-App-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-352">OpenGL app code</span></span>

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

<span data-ttu-id="44dfd-353">GLSL-Vertex-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-353">GLSL vertex shader code</span></span>

``` syntax
//The shader entry point is the main method.
void main()
{
colorVarying = color; //Use the varying variable to pass the color to the fragment shader
gl_Position = position; //Copy the position to the gl_Position pre-defined global variable
}
```

<span data-ttu-id="44dfd-354">GLSL-Fragment-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-354">GLSL fragment shader code</span></span>

``` syntax
void main()
{
//Pad the colorVarying vec3 with a 1.0 for alpha to create a vec4 color
//and assign that color to the gl_FragColor pre-defined global variable
//This color then becomes the fragment's color.
gl_FragColor = vec4(colorVarying, 1.0);
}
```

### <a name="constant-buffers-and-data-transfers-in-hlsl"></a><span data-ttu-id="44dfd-355">Konstantenpuffer und Datenübertragungen in HLSL</span><span class="sxs-lookup"><span data-stu-id="44dfd-355">Constant buffers and data transfers in HLSL</span></span>

<span data-ttu-id="44dfd-356">Das folgende Beispiel zeigt, wie Sie Daten an den HLSL-Vertex-Shader übergeben, die anschließend zum Pixelshader übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="44dfd-356">Here is an example of how you pass data to the HLSL vertex shader that then flows through to the pixel shader.</span></span> <span data-ttu-id="44dfd-357">Definieren Sie in Ihrem App-Code einen Scheitelpunkt und einen Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="44dfd-357">In your app code, define a vertex and a constant buffer.</span></span> <span data-ttu-id="44dfd-358">Definieren Sie anschließend im Vertex-Shader-Code den Konstantenpuffer als [cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581), und speichern Sie die Daten für einzelne Scheitelpunkte und die Eingabedaten des Pixelshaders.</span><span class="sxs-lookup"><span data-stu-id="44dfd-358">Then, in your vertex shader code, define the constant buffer as a [cbuffer](https://msdn.microsoft.com/library/windows/desktop/bb509581) and store the per-vertex data and the pixel shader input data.</span></span> <span data-ttu-id="44dfd-359">Hier verwenden als **VertexShaderInput** und **PixelShaderInput** bezeichnete Strukturen.</span><span class="sxs-lookup"><span data-stu-id="44dfd-359">Here we use structures called **VertexShaderInput** and **PixelShaderInput**.</span></span>

<span data-ttu-id="44dfd-360">Direct3D-App-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-360">Direct3D app code</span></span>

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

<span data-ttu-id="44dfd-361">HLSL-Vertex-Shader-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-361">HLSL vertex shader code</span></span>

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

<span data-ttu-id="44dfd-362">HLSL-Pixelshader-Code</span><span class="sxs-lookup"><span data-stu-id="44dfd-362">HLSL pixel shader code</span></span>

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

## <a name="examples-of-porting-opengl-rendering-code-to-direct3d"></a><span data-ttu-id="44dfd-363">Beispiele für das Portieren von OpenGL-Renderingcode zu Direct3D</span><span class="sxs-lookup"><span data-stu-id="44dfd-363">Examples of porting OpenGL rendering code to Direct3D</span></span>


<span data-ttu-id="44dfd-364">Im Folgenden zeigen wir Ihnen ein Beispiel für das Rendering in OpenGLES2.0-Code und anschließend das entsprechende Beispiel in Direct3D11-Code.</span><span class="sxs-lookup"><span data-stu-id="44dfd-364">Here we show an example of rendering in OpenGL ES 2.0 code and then the equivalent example in Direct3D 11 code.</span></span>

<span data-ttu-id="44dfd-365">OpenGL-Renderingcode</span><span class="sxs-lookup"><span data-stu-id="44dfd-365">OpenGL rendering code</span></span>

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

<span data-ttu-id="44dfd-366">Direct3D-Renderingcode</span><span class="sxs-lookup"><span data-stu-id="44dfd-366">Direct3D rendering code</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="44dfd-367">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="44dfd-367">Related topics</span></span>


* [<span data-ttu-id="44dfd-368">Portieren von OpenGLES2.0 zu Direct3D11</span><span class="sxs-lookup"><span data-stu-id="44dfd-368">Port from OpenGL ES 2.0 to Direct3D 11</span></span>](port-from-opengl-es-2-0-to-directx-11-1.md)

 

 




