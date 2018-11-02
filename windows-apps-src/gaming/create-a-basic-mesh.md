---
author: mtoepke
title: Erstellen und Anzeigen einfacher Gitter
description: In 3D-Spielen für die Universelle Windows-Plattform (UWP) werden Spielobjekte und Oberflächen in der Regel durch Polygone dargestellt.
ms.assetid: bfe0ed5b-63d8-935b-a25b-378b36982b7d
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Gitter, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: e3ae6416217efa16d70b65b8ff55e36654a11557
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5937233"
---
# <a name="create-and-display-a-basic-mesh"></a><span data-ttu-id="d5c7d-104">Erstellen und Anzeigen einfacher Gitter</span><span class="sxs-lookup"><span data-stu-id="d5c7d-104">Create and display a basic mesh</span></span>



<span data-ttu-id="d5c7d-105">In 3D-Spielen für die universelle Windows-Plattform (UWP) werden Spielobjekte und Oberflächen in der Regel durch Polygone dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-105">3-D Universal Windows Platform (UWP) games typically use polygons to represent objects and surfaces in the game.</span></span> <span data-ttu-id="d5c7d-106">Die Liste der Vertizes, die die Struktur dieser polygonalen Objekte und Oberflächen darstellen, werden als Gitter bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-106">The lists of vertices that comprise the structure of these polygonal objects and surfaces are called meshes.</span></span> <span data-ttu-id="d5c7d-107">Hier erstellen wir ein einfaches Gitter für ein Würfelobjekt und stellen es zum Rendern und Anzeigen für die Shader-Pipeline bereit.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-107">Here, we create a basic mesh for a cube object and provide it to the shader pipeline for rendering and display.</span></span>

> <span data-ttu-id="d5c7d-108">**Wichtige**  der enthaltene Beispielcode verwendet hier Typen (z. B. DirectX:: Xmfloat3 "und" DirectX:: Xmfloat4x4 ") und Inlinemethoden in DirectXMath.h deklariert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-108">**Important** The example code included here uses types (such as DirectX::XMFLOAT3 and DirectX::XMFLOAT4X4) and inline methods declared in DirectXMath.h.</span></span> <span data-ttu-id="d5c7d-109">Wenn Sie diesen Code ausschneiden und einfügen, nehmen Sie auch &lt;DirectXMath.h&gt; in Ihr Projekt auf.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-109">If you're cutting and pasting this code, \#include &lt;DirectXMath.h&gt; in your project.</span></span>

 

## <a name="what-you-need-to-know"></a><span data-ttu-id="d5c7d-110">Wissenswertes</span><span class="sxs-lookup"><span data-stu-id="d5c7d-110">What you need to know</span></span>


### <a name="technologies"></a><span data-ttu-id="d5c7d-111">Technologien</span><span class="sxs-lookup"><span data-stu-id="d5c7d-111">Technologies</span></span>

-   [<span data-ttu-id="d5c7d-112">Direct3D</span><span class="sxs-lookup"><span data-stu-id="d5c7d-112">Direct3D</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh769064)

### <a name="prerequisites"></a><span data-ttu-id="d5c7d-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-113">Prerequisites</span></span>

-   <span data-ttu-id="d5c7d-114">Grundkenntnisse in linearer Algebra und 3D-Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-114">Basic knowledge of linear algebra and 3-D coordinate systems</span></span>
-   <span data-ttu-id="d5c7d-115">Ein Visual Studio 2015 oder höher Direct3D-Vorlage</span><span class="sxs-lookup"><span data-stu-id="d5c7d-115">A Visual Studio 2015 or later Direct3D template</span></span>

## <a name="instructions"></a><span data-ttu-id="d5c7d-116">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-116">Instructions</span></span>

<span data-ttu-id="d5c7d-117">Diese Schritte verdeutlichen, wie Sie einen einfachen Gitterwürfel erstellen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-117">These steps will show you how to create a basic mesh cube.</span></span> 


<span data-ttu-id="d5c7d-118">Wenn Sie eine gesprochene Erklärung dieser Konzepte bevorzugen, sehen Sie sich dieses Video an.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-118">If you prefer a talked-through explanation of these concepts, check out this video.</span></span>
</br>
</br>
<iframe src="https://channel9.msdn.com/Series/Introduction-to-C-and-DirectX-Game-Development/03/player#time=7m39s:paused" width="600" height="338" allowFullScreen frameBorder="0"></iframe>


### <a name="step-1-construct-the-mesh-for-the-model"></a><span data-ttu-id="d5c7d-119">Schritt1: Konstruieren des Gitters für das Modell</span><span class="sxs-lookup"><span data-stu-id="d5c7d-119">Step 1: Construct the mesh for the model</span></span>

<span data-ttu-id="d5c7d-120">In den meisten Spielen wird das Gitter für ein Spielobjekt aus einer Datei geladen, die die spezifischen Vertexdaten enthält.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-120">In most games, the mesh for a game object is loaded from a file that contains the specific vertex data.</span></span> <span data-ttu-id="d5c7d-121">Die Reihenfolge dieser Vertizes ist App-abhängig, in der Regel werden sie jedoch ketten- oder fächerförmig serialisiert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-121">The ordering of these vertices is app-dependent, but they are usually serialized as strips or fans.</span></span> <span data-ttu-id="d5c7d-122">Vertexdaten können aus einer beliebigen Softwarequelle stammen oder manuell erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-122">Vertex data can come from any software source, or it can be created manually.</span></span> <span data-ttu-id="d5c7d-123">Die Daten müssen vom Spiel so interpretiert werden, dass sie vom Vertex-Shader effektiv verarbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-123">It's up to your game to interpret the data in a way that the vertex shader can effectively process it.</span></span>

<span data-ttu-id="d5c7d-124">In unserem Beispiel verwenden wir ein einfaches Gitter für einen Würfel.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-124">In our example, we use a simple mesh for a cube.</span></span> <span data-ttu-id="d5c7d-125">Der Würfel wird wie alle Objektgitter in diesem Abschnitt der Pipeline mithilfe eines eigenen Koordinatensystems dargestellt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-125">The cube, like any object mesh at this stage in the pipeline, is represented using its own coordinate system.</span></span> <span data-ttu-id="d5c7d-126">Der Vertex-Shader verwendet die Koordinaten und gibt durch Anwendung der bereitgestellten Transformationsmatrizen die endgültige 2D-Anzeigeprojektion in einem homogenen Koordinatensystem zurück.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-126">The vertex shader takes its coordinates and, by applying the transformation matrices you provide, returns the final 2-D view projection in a homogeneous coordinate system.</span></span>

<span data-ttu-id="d5c7d-127">Definieren Sie das Gitter für einen Würfel.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-127">Define the mesh for a cube.</span></span> <span data-ttu-id="d5c7d-128">(Laden Sie es alternativ aus einer Datei.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-128">(Or load it from a file.</span></span> <span data-ttu-id="d5c7d-129">Das bleibt Ihnen überlassen.)</span><span class="sxs-lookup"><span data-stu-id="d5c7d-129">It's your call!)</span></span>

```cpp
SimpleCubeVertex cubeVertices[] =
{
    { DirectX::XMFLOAT3(-0.5f, 0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 0.0f) }, // +Y (top face)
    { DirectX::XMFLOAT3( 0.5f, 0.5f, -0.5f), DirectX::XMFLOAT3(1.0f, 1.0f, 0.0f) },
    { DirectX::XMFLOAT3( 0.5f, 0.5f,  0.5f), DirectX::XMFLOAT3(1.0f, 1.0f, 1.0f) },
    { DirectX::XMFLOAT3(-0.5f, 0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, 1.0f, 1.0f) },

    { DirectX::XMFLOAT3(-0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 1.0f) }, // -Y (bottom face)
    { DirectX::XMFLOAT3( 0.5f, -0.5f,  0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 1.0f) },
    { DirectX::XMFLOAT3( 0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(1.0f, 0.0f, 0.0f) },
    { DirectX::XMFLOAT3(-0.5f, -0.5f, -0.5f), DirectX::XMFLOAT3(0.0f, 0.0f, 0.0f) },
};
```

<span data-ttu-id="d5c7d-130">Das Koordinatensystem des Würfels platziert die Mitte des Würfels am Ursprung. Dabei verläuft die Y-Achse bei Verwendung eines linkshändigen Koordinatensystems von oben nach unten.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-130">The cube's coordinate system places the center of the cube at the origin, with the y-axis running top to bottom using a left-handed coordinate system.</span></span> <span data-ttu-id="d5c7d-131">Die Koordinatenwerte werden als 32-Bit-Gleitkommawerte zwischen -1 und 1 ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-131">Coordinate values are expressed as 32-bit floating values between -1 and 1.</span></span>

<span data-ttu-id="d5c7d-132">Bei jedem in Klammern gesetzten Paar gibt die zweite DirectX::XMFLOAT3-Wertgruppe die dem Vertex zugeordnete Farbe als RGB-Wert an.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-132">In each bracketed pairing, the second DirectX::XMFLOAT3 value group specifies the color associated with the vertex as an RGB value.</span></span> <span data-ttu-id="d5c7d-133">Beispiel: Der erste Vertex bei (-0,5, 0,5, -0,5) hat eine deckende grüne Farbe (für den Wert "G" ist 1,0 festgelegt, für die Werte "R" und "B" ist 0 festgelegt).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-133">For example, the first vertex at (-0.5, 0.5, -0.5) has a full green color (the G value is set to 1.0, and the "R" and "B" values are set to 0).</span></span>

<span data-ttu-id="d5c7d-134">Daraus ergeben sich acht Vertizes mit jeweils einer bestimmten Farbe.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-134">Therefore, you have 8 vertices, each with a specific color.</span></span> <span data-ttu-id="d5c7d-135">Jedes Paar aus Vertex und Farbe stellt die vollständigen Daten für einen Vertex in unserem Beispiel dar.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-135">Each vertex/color pairing is the complete data for a vertex in our example.</span></span> <span data-ttu-id="d5c7d-136">Wenn Sie den Vertexpuffer angeben, müssen Sie dabei dieses spezielle Layout berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-136">When you specify our vertex buffer, you must keep this specific layout in mind.</span></span> <span data-ttu-id="d5c7d-137">Dieses Eingabelayout wird dem Vertex-Shader zur Verfügung gestellt, damit er die Vertexdaten interpretieren kann.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-137">We provide this input layout to the vertex shader so it can understand your vertex data.</span></span>

### <a name="step-2-set-up-the-input-layout"></a><span data-ttu-id="d5c7d-138">Schritt2: Einrichten des Eingabelayouts</span><span class="sxs-lookup"><span data-stu-id="d5c7d-138">Step 2: Set up the input layout</span></span>

<span data-ttu-id="d5c7d-139">Nun befinden sich die Vertizes im Speicher.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-139">Now, you have the vertices in memory.</span></span> <span data-ttu-id="d5c7d-140">Ihr Grafikgerät besitzt jedoch einen eigenen Speicher, auf den Sie mithilfe von Direct3D zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-140">But, your graphics device has its own memory, and you use Direct3D to access it.</span></span> <span data-ttu-id="d5c7d-141">Um die Vertexdaten zur Verarbeitung an das Grafikgerät zu übergeben, müssen Sie den Weg dazu ebnen. Das bedeutet: Sie müssen deklarieren, wie die Vertexdaten angeordnet sind, sodass sie vom Grafikgerät interpretiert werden können, wenn sie vom Spiel an das Gerät übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-141">To get your vertex data into the graphics device for processing, you need to clear the way, as it were: you must declare how the vertex data is laid out so that the graphics device can interpret it when it gets it from your game.</span></span> <span data-ttu-id="d5c7d-142">Verwenden Sie dazu [**ID3D11InputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476575).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-142">To do that, you use [**ID3D11InputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476575).</span></span>

<span data-ttu-id="d5c7d-143">Deklarieren Sie das Eingabelayout für den Vertexpuffer, und legen Sie es fest.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-143">Declare and set the input layout for the vertex buffer.</span></span>

```cpp
const D3D11_INPUT_ELEMENT_DESC basicVertexLayoutDesc[] =
{
    { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0,  0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
    { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};

ComPtr<ID3D11InputLayout> inputLayout;
m_d3dDevice->CreateInputLayout(
                basicVertexLayoutDesc,
                ARRAYSIZE(basicVertexLayoutDesc),
                vertexShaderBytecode->Data,
                vertexShaderBytecode->Length,
                &inputLayout)
);
```

<span data-ttu-id="d5c7d-144">In diesem Code geben Sie ein Layout für die Vertizes an – genauer gesagt: welche Daten die einzelnen Elemente in der Vertexliste enthalten.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-144">In this code, you specify a layout for the vertices, specifically, what data each element in the vertex list contains.</span></span> <span data-ttu-id="d5c7d-145">In **basicVertexLayoutDesc** geben Sie zwei Datenkomponenten an:</span><span class="sxs-lookup"><span data-stu-id="d5c7d-145">Here, in **basicVertexLayoutDesc**, you specify two data components:</span></span>

-   <span data-ttu-id="d5c7d-146">**POSITION**: Eine HLSL-Semantik für Positionsdaten, die für einen Shader bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-146">**POSITION**: This is an HLSL semantic for position data provided to a shader.</span></span> <span data-ttu-id="d5c7d-147">In diesem Code ist dies ein DirectX::XMFLOAT3-Wert, oder genauer ausgedrückt, eine Struktur mit drei 32-Bit-Gleitkommazahlen, die einem 3D-Koordinatensystem (X, Y, Z) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-147">In this code, it's a DirectX::XMFLOAT3, or more specifically, a structure with 3 32-bit floating point values that correspond to a 3D coordinate (x, y, z).</span></span> <span data-ttu-id="d5c7d-148">Sie könnten aber auch einen float4-Wert verwenden, wenn Sie die homogene W-Koordinate angeben. In diesem Fall müssten Sie dann „DXGI\_FORMAT\_R32G32B32A32\_FLOAT“ angeben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-148">You could also use a float4 if you are supplying the homogeneous "w" coordinate, and in that case, you specify DXGI\_FORMAT\_R32G32B32A32\_FLOAT.</span></span> <span data-ttu-id="d5c7d-149">Ob Sie einen DirectX::XMFLOAT3- oder einen float4-Wert verwenden, ist von den speziellen Anforderungen Ihres Spiels abhängig.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-149">Whether you use a DirectX::XMFLOAT3 or a float4 is up to the specific needs of your game.</span></span> <span data-ttu-id="d5c7d-150">Stellen Sie lediglich sicher, dass die Vertexdaten für Ihr Gitter dem verwendeten Format entsprechen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-150">Just make sure that the vertex data for your mesh corresponds correctly to the format you use!</span></span>

    <span data-ttu-id="d5c7d-151">Jeder Koordinatenwert wird als Gleitkommawert zwischen -1 und 1 im Koordinatenbereich des Objekts ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-151">Each coordinate value is expressed as a floating point value between -1 and 1, in the object's coordinate space.</span></span> <span data-ttu-id="d5c7d-152">Nach Abschluss des Vertex-Shaders befindet sich der transformierte Vertex im homogenen (korrigierte Perspektive) Anzeigeprojektionsbereich.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-152">When the vertex shader completes, the transformed vertex is in the homogeneous (perspective corrected) view projection space.</span></span>

    <span data-ttu-id="d5c7d-153">„Aber der Enumerationswert gibt RGB und nicht XYZ an!“,</span><span class="sxs-lookup"><span data-stu-id="d5c7d-153">"But the enumeration value indicates RGB, not XYZ!"</span></span> <span data-ttu-id="d5c7d-154">wie Sie völlig zu Recht bemerkt haben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-154">you smartly note.</span></span> <span data-ttu-id="d5c7d-155">Gut aufgepasst!</span><span class="sxs-lookup"><span data-stu-id="d5c7d-155">Good eye!</span></span> <span data-ttu-id="d5c7d-156">Sowohl für Farbdaten als auch für Koordinatendaten verwenden Sie in der Regel drei oder vier Komponentenwerte. Warum kann also nicht dasselbe Formate für beide verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="d5c7d-156">In both the cases of color data and coordinate data, you typically use 3 or 4 component values, so why not use the same format for both?</span></span> <span data-ttu-id="d5c7d-157">Nicht der Formatname, sondern die HLSL-Semantik gibt an, wie der Shader die Daten behandelt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-157">The HLSL semantic, not the format name, indicates how the shader treats the data.</span></span>

-   <span data-ttu-id="d5c7d-158">**COLOR**: Eine HLSL-Semantik für Farbdaten.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-158">**COLOR**: This is an HLSL semantic for color data.</span></span> <span data-ttu-id="d5c7d-159">Genau wie **POSITION** besteht auch sie aus drei 32-Bit-Gleitkommawerten (DirectX::XMFLOAT3).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-159">Like **POSITION**, it consists of 3 32-bit floating point values (DirectX::XMFLOAT3).</span></span> <span data-ttu-id="d5c7d-160">Jeder Wert enthält eine Farbkomponente: rot (r), blau (b) oder grün (g). Diese werden als Gleitkommazahl zwischen0 und1 ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-160">Each value contains a color component: red (r), blue (b), or green (g), expressed as a floating number between 0 and 1.</span></span>

    <span data-ttu-id="d5c7d-161">**COLOR**-Werte werden in der Regel als RGBA-Wert aus vier Komponenten am Ende der Shader-Pipeline zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-161">**COLOR** values are typically returned as a 4-component RGBA value at the end of the shader pipeline.</span></span> <span data-ttu-id="d5c7d-162">In diesem Beispiel legen Sie in der Shader-Pipeline für alle Pixel den Alpha-Wert „A“ auf „1,0“ (maximale Deckkraft) fest.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-162">For this example, you will be setting the "A" alpha value to 1.0 (maximum opacity) in the shader pipeline for all pixels.</span></span>

<span data-ttu-id="d5c7d-163">Die vollständige Formatliste finden Sie unter [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-163">For a complete list of formats, see [**DXGI\_FORMAT**](https://msdn.microsoft.com/library/windows/desktop/bb173059).</span></span> <span data-ttu-id="d5c7d-164">Die vollständige HLSL-Semantikliste finden Sie unter [Semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-164">For a complete list of HLSL semantics, see [Semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647).</span></span>

<span data-ttu-id="d5c7d-165">Rufen Sie [**ID3D11Device::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512) auf, und erstellen Sie das Eingabelayout auf dem Direct3D-Gerät.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-165">Call [**ID3D11Device::CreateInputLayout**](https://msdn.microsoft.com/library/windows/desktop/ff476512) and create the input layout on the Direct3D device.</span></span> <span data-ttu-id="d5c7d-166">Nun müssen Sie einen Puffer erstellen, der die Daten auch enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-166">Now, you need to create a buffer that can actually hold the data!</span></span>

### <a name="step-3-populate-the-vertex-buffers"></a><span data-ttu-id="d5c7d-167">Schritt3: Füllen des Vertexpuffers</span><span class="sxs-lookup"><span data-stu-id="d5c7d-167">Step 3: Populate the vertex buffers</span></span>

<span data-ttu-id="d5c7d-168">Vertexpuffer enthalten die Liste der Vertizes für alle Dreiecke im Gitter.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-168">Vertex buffers contain the list of vertices for each triangle in the mesh.</span></span> <span data-ttu-id="d5c7d-169">Alle Vertizes müssen in dieser Liste eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-169">Every vertex must be unique in this list.</span></span> <span data-ttu-id="d5c7d-170">In unserem Beispiel sind acht Vertizes für den Würfel vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-170">In our example, you have 8 vertices for the cube.</span></span> <span data-ttu-id="d5c7d-171">Der Vertex-Shader wird auf dem Grafikgerät ausgeführt. Er liest aus dem Vertexpuffer und interpretiert die Daten basierend auf dem im vorherigen Schritt angegebenen Eingabelayout.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-171">The vertex shader runs on the graphics device and reads from the vertex buffer, and it interprets the data based on the input layout you specified in the previous step.</span></span>

<span data-ttu-id="d5c7d-172">Im nächsten Beispiel geben Sie eine Beschreibung und eine Unterressource für den Puffer an. Diese beiden Elemente teilen Direct3D verschiedene Informationen zur physischen Zuordnung der Vertexdaten und zu ihrer Behandlung im Speicher des Grafikgeräts mit.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-172">In the next example, you provide a description and a subresource for the buffer, which tell Direct3D a number of things about the physical mapping of the vertex data and how to treat it in memory on the graphics device.</span></span> <span data-ttu-id="d5c7d-173">Das ist erforderlich, weil Sie einen generischen [**ID3D11Buffer**](https://msdn.microsoft.com/library/windows/desktop/ff476351) verwenden, der alles Mögliche enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-173">This is necessary because you use a generic [**ID3D11Buffer**](https://msdn.microsoft.com/library/windows/desktop/ff476351), which could contain anything!</span></span> <span data-ttu-id="d5c7d-174">Die [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092)- und die [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220)-Struktur werden bereitgestellt, um sicherzustellen, dass Direct3D das Layout des physischen Speichers des Puffers versteht. Hierzu zählen u.a. die Größe der einzelnen Vertexelemente im Puffer sowie die maximale Größe der Vertexliste.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-174">The [**D3D11\_BUFFER\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476092) and [**D3D11\_SUBRESOURCE\_DATA**](https://msdn.microsoft.com/library/windows/desktop/ff476220) structures are supplied to ensure that Direct3D understands the physical memory layout of the buffer, including the size of each vertex element in the buffer as well as the maximum size of the vertex list.</span></span> <span data-ttu-id="d5c7d-175">Darüber hinaus können Sie hier den Zugriff auf den Pufferspeicher und seinen Durchlauf steuern. Dies ist jedoch nicht Teil dieses Lernprogramms.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-175">You can also control access to the buffer memory here and how it is traversed, but that's a bit beyond the scope of this tutorial.</span></span>

<span data-ttu-id="d5c7d-176">Nach dem Konfigurieren des Puffers rufen Sie [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) auf, um ihn zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-176">After you configure the buffer, you call [**ID3D11Device::CreateBuffer**](https://msdn.microsoft.com/library/windows/desktop/ff476501) to actually create it.</span></span> <span data-ttu-id="d5c7d-177">Bei mehreren Objekten müssen Sie natürlich Puffer für jedes einzelne Modell erstellen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-177">Obviously, if you have more than one object, create buffers for each unique model.</span></span>

<span data-ttu-id="d5c7d-178">Deklarieren Sie den Vertexpuffer, und erstellen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-178">Declare and create the vertex buffer.</span></span>

```cpp
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
m_d3dDevice->CreateBuffer(
                &vertexBufferDesc,
                &vertexBufferData,
                &vertexBuffer);
```

<span data-ttu-id="d5c7d-179">Die Vertizes werden geladen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-179">Vertices loaded.</span></span> <span data-ttu-id="d5c7d-180">Aber in welcher Reihenfolge werden diese Vertizes verarbeitet?</span><span class="sxs-lookup"><span data-stu-id="d5c7d-180">But what's the order of processing these vertices?</span></span> <span data-ttu-id="d5c7d-181">Dies wird festgelegt, wenn Sie für die Vertizes eine Liste mit den Indizes angeben. Die Reihenfolge dieser Indizes ist die Reihenfolge, in der sie vom Vertex-Shader verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-181">That's handled when you provide a list of indices to the vertices—the ordering of these indices is the order in which the vertex shader processes them.</span></span>

### <a name="step-4-populate-the-index-buffers"></a><span data-ttu-id="d5c7d-182">Schritt4: Füllen der Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="d5c7d-182">Step 4: Populate the index buffers</span></span>

<span data-ttu-id="d5c7d-183">Nun geben Sie eine Liste mit den Indizes für die einzelnen Vertizes an.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-183">Now, you provide a list of the indices for each of the vertices.</span></span> <span data-ttu-id="d5c7d-184">Diese Indizes entsprechen der Position des Vertex im Vertexpuffer und beginnen mit 0.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-184">These indices correspond to the position of the vertex in the vertex buffer, starting with 0.</span></span> <span data-ttu-id="d5c7d-185">Stellen Sie sich zur besseren Veranschaulichung einfach vor, dass jedem eindeutigen Vertex in Ihrem Gitter eine eindeutige Zahl (wie eine ID) zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-185">To help you visualize this, consider that each unique vertex in your mesh has a unique number assigned to it, like an ID.</span></span> <span data-ttu-id="d5c7d-186">Diese ID ist die ganzzahlige Position des Vertex im Vertexpuffer.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-186">This ID is the integer position of the vertex in the vertex buffer.</span></span>

![Ein Würfel mit acht nummerierten Vertizes](images/cube-mesh-1.png)

<span data-ttu-id="d5c7d-188">Unser Beispielwürfel besitzt acht Vertizes, die wiederum sechs Vierecke für die Seiten bilden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-188">In our example cube, you have 8 vertices, which create 6 quads for the sides.</span></span> <span data-ttu-id="d5c7d-189">Wenn Sie die Vierecke in Dreiecke teilen, entstehen aus den acht Vertizes also insgesamt zwölfDreiecke.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-189">You split the quads into triangles, for a total of 12 triangles that use our 8 vertices.</span></span> <span data-ttu-id="d5c7d-190">Bei drei Vertizes pro Dreieck enthält der Indexpuffer 36Einträge.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-190">At 3 vertices per triangle, you have 36 entries in our index buffer.</span></span> <span data-ttu-id="d5c7d-191">In unserem Beispiel wird dieses Indexmuster als Dreiecksliste bezeichnet. Sie geben sie für Direct3D als **D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLELIST** an, wenn Sie die primitive Topologie festlegen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-191">In our example, this index pattern is known as a triangle list, and you indicate it to Direct3D as a **D3D11\_PRIMITIVE\_TOPOLOGY\_TRIANGLELIST** when you set the primitive topology.</span></span>

<span data-ttu-id="d5c7d-192">Diese Art der Indexauflistung ist besonders ineffizient, da Dreiecke gemeinsame Punkte und Seiten besitzen und es so zu Redundanzen kommt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-192">This is probably the most inefficient way to list indices, as there are many redundancies when triangles share points and sides.</span></span> <span data-ttu-id="d5c7d-193">Teilt sich ein Dreieck also beispielsweise eine Seite mit einer Raute, werden für die vier Vertizes sechs Indizes aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="d5c7d-193">For example, when a triangle shares a side in a rhombus shape, you list 6 indices for the four vertices, like this:</span></span>

![Reihenfolge der Indizes beim Konstruieren einer Raute](images/rhombus-surface-1.png)

-   <span data-ttu-id="d5c7d-195">Dreieck1: \[0, 1, 2\]</span><span class="sxs-lookup"><span data-stu-id="d5c7d-195">Triangle 1: \[0, 1, 2\]</span></span>
-   <span data-ttu-id="d5c7d-196">Dreieck2: \[0, 2, 3\]</span><span class="sxs-lookup"><span data-stu-id="d5c7d-196">Triangle 2: \[0, 2, 3\]</span></span>

<span data-ttu-id="d5c7d-197">In einer ketten- oder fächerförmigen Topologie ordnen Sie die Vertizes so an, dass viele redundante Seiten beim Durchlaufen ausgeschlossen werden (z.B. die Seite von Index0 zu Index2 im Bild). Bei großen Gittern wird dadurch die Anzahl der Ausführungen des Vertex-Shaders deutlich reduziert und die Leistung erheblich gesteigert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-197">In a strip or fan topology, you order the vertices in a way that eliminates many redundant sides during traversal (such as the side from index 0 to index 2 in the image.) For large meshes, this dramatically reduces the number of times the vertex shader is run, and improves performance significantly.</span></span> <span data-ttu-id="d5c7d-198">Wir halten es hier jedoch einfach und verwenden die Dreiecksliste.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-198">However, we'll keep it simple and stick with the triangle list.</span></span>

<span data-ttu-id="d5c7d-199">Deklarieren Sie die Indizes für den Vertexpuffer als eine einfache Dreieckslistentopologie.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-199">Declare the indices for the vertex buffer as a simple triangle list topology.</span></span>

```cpp
unsigned short cubeIndices[] =
{   0, 1, 2,
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
    0, 4, 7 };
```

<span data-ttu-id="d5c7d-200">Bei 36Indexelemente im Puffer für lediglich achtVertizes ergibt sich ein hohes Maß an Redundanz.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-200">Thirty six index elements in the buffer is very redundant when you only have 8 vertices!</span></span> <span data-ttu-id="d5c7d-201">Wenn Sie einige Redundanzen ausschließen und einen anderen Vertexlistentyp (beispielsweise einen ketten- oder fächerförmigen Typ) verwenden möchten, müssen Sie diesen Typ angeben, wenn Sie einen bestimmten [**D3D11\_PRIMITIVE\_TOPOLOGY**](https://msdn.microsoft.com/library/windows/desktop/ff476189)-Wert für die [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455)-Methode angeben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-201">If you choose to eliminate some of the redundancies and use a different vertex list type, such as a strip or a fan, you must specify that type when you provide a specific [**D3D11\_PRIMITIVE\_TOPOLOGY**](https://msdn.microsoft.com/library/windows/desktop/ff476189) value to the [**ID3D11DeviceContext::IASetPrimitiveTopology**](https://msdn.microsoft.com/library/windows/desktop/ff476455) method.</span></span>

<span data-ttu-id="d5c7d-202">Weitere Informationen zu verschiedenen Indexlistentechniken finden Sie unter [Primitive Topologien](https://msdn.microsoft.com/library/windows/desktop/bb205124).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-202">For more information about different index list techniques, see [Primitive Topologies](https://msdn.microsoft.com/library/windows/desktop/bb205124).</span></span>

### <a name="step-5-create-a-constant-buffer-for-your-transformation-matrices"></a><span data-ttu-id="d5c7d-203">Schritt5: Erstellen eines konstanten Puffers für die Transformationsmatrizen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-203">Step 5: Create a constant buffer for your transformation matrices</span></span>

<span data-ttu-id="d5c7d-204">Bevor Sie mit der Verarbeitung von Vertizes beginnen können, müssen Sie die Transformationsmatrizen angeben, die bei der Ausführung auf alle Vertizes angewendet (multipliziert) werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-204">Before you can start processing vertices, you need to provide the transformation matrices that will be applied (multiplied) to each vertex when it runs.</span></span> <span data-ttu-id="d5c7d-205">Die meisten 3D-Spielen enthalten drei Matrizen:</span><span class="sxs-lookup"><span data-stu-id="d5c7d-205">For most 3-D games, there are three of them:</span></span>

-   <span data-ttu-id="d5c7d-206">4x4-Matrix, die eine Transformation vom Koordinatensystem des Objekts (Modell) zum allgemeinen Weltkoordinatensystem ausführt</span><span class="sxs-lookup"><span data-stu-id="d5c7d-206">The 4x4 matrix that transforms from the object (model) coordinate system to the overall world coordinate system.</span></span>
-   <span data-ttu-id="d5c7d-207">4x4-Matrix, die eine Transformation vom Weltkoordinatensystem zum Kamerakoordinatensystem (Ansicht) ausführt</span><span class="sxs-lookup"><span data-stu-id="d5c7d-207">The 4x4 matrix that transforms from the world coordinate system to the camera (view) coordinate system.</span></span>
-   <span data-ttu-id="d5c7d-208">4x4-Matrix, die eine Transformation vom Kamerakoordinatensystem zum Koordinatensystem der 2D-Anzeigeprojektion ausführt</span><span class="sxs-lookup"><span data-stu-id="d5c7d-208">The 4x4 matrix that transforms from the camera coordinate system to the 2-D view projection coordinate system.</span></span>

<span data-ttu-id="d5c7d-209">Diese Matrizen werden in einem *konstanten Puffer* an den Shader übergeben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-209">These matrices are passed to the shader in a *constant buffer*.</span></span> <span data-ttu-id="d5c7d-210">Bei einem Konstantenpuffer handelt es sich um einen Bereich des Speichers, der während des nächsten Schritts der Shader-Pipeline konstant bleibt und auf den von den Shadern aus dem HLSL-Code direkt zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-210">A constant buffer is a region of memory that remains constant throughout the execution of the next pass of the shader pipeline, and which can be directly accessed by the shaders from your HLSL code.</span></span> <span data-ttu-id="d5c7d-211">Sie definieren die einzelnen konstanten Puffer zweimal: zuerst im C++-Code Ihres Spiels und (mindestens) einmal in der C-ähnlichen HLSL-Syntax für den Shadercode.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-211">You define each constant buffer two times: first in your game's C++ code, and (at least) one time in the C-like HLSL syntax for your shader code.</span></span> <span data-ttu-id="d5c7d-212">Die beiden Deklarationen müssen in Bezug auf Typ und Datenausrichtung direkt übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-212">The two declarations must directly correspond in terms of types and data alignment.</span></span> <span data-ttu-id="d5c7d-213">Schwer auffindbare Fehler entstehen schnell, wenn der Shader die HLSL-Deklaration zum Interpretieren von in C++ deklarierten Daten verwendet und die Typen nicht übereinstimmen oder die Ausrichtung der Daten deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-213">It's easy to introduce hard to find errors when the shader uses the HLSL declaration to interpret data declared in C++, and the types don't match or the alignment of data is off!</span></span>

<span data-ttu-id="d5c7d-214">Konstante Puffer werden von der HLSL-Syntax nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-214">Constant buffers don't get changed by the HLSL.</span></span> <span data-ttu-id="d5c7d-215">Sie können sie ändern, wenn vom Spiel bestimmte Daten aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-215">You can change them when your game updates specific data.</span></span> <span data-ttu-id="d5c7d-216">Häufig erstellen Spieleentwickler vier Klassen konstanter Puffer: einen Typ für Updates pro Frame, einen Typ für Updates pro Modell/Objekt, einen Typ für Updates pro Aktualisierung des Spielzustands und einen Typ für Daten, die sich während der Lebensdauer des Spiels nie ändern.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-216">Often, game devs create 4 classes of constant buffers: one type for updates per frame; one type for updates per model/object; one type for updates per game state refresh; and one type for data that never changes through the lifetime of the game.</span></span>

<span data-ttu-id="d5c7d-217">Dieses Beispiel enthält nur eine Art von Daten, die sich nie ändern: die DirectX::XMFLOAT4X4-Daten für die drei Matrizen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-217">In this example, we just have one that never changes: the DirectX::XMFLOAT4X4 data for the three matrices.</span></span>

> <span data-ttu-id="d5c7d-218">**Hinweis:**  der hier dargestellte Beispielcode werden spaltenweise absteigenden Matrizen verwendet.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-218">**Note** The example code presented here uses column-major matrices.</span></span> <span data-ttu-id="d5c7d-219">Sie können stattdessen zeilenweise absteigende Matrizen (row-major) verwenden, indem Sie das **row\_major**-Schlüsselwort in HLSL angeben und sicherstellen, dass die Quellmatrixdaten ebenfalls zeilenweise absteigend angeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-219">You can use row-major matrices instead by using the **row\_major** keyword in HLSL, and ensuring your source matrix data is also row-major.</span></span> <span data-ttu-id="d5c7d-220">„DirectXMath“ verwendet zeilenweise absteigende Matrizen und kann direkt mit HLSL-Matrizen verwendet werden, die mit dem **row\_major**-Schlüsselwort definiert werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-220">DirectXMath uses row-major matrices and can be used directly with HLSL matrices defined with the **row\_major** keyword.</span></span>

 

<span data-ttu-id="d5c7d-221">Deklarieren und erstellen Sie einen Konstantenpuffer für die drei Matrizen, die Sie zum Transformieren der einzelnen Vertizes verwenden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-221">Declare and create a constant buffer for the three matrices you use to transform each vertex.</span></span>

```cpp
struct ConstantBuffer
{
    DirectX::XMFLOAT4X4 model;
    DirectX::XMFLOAT4X4 view;
    DirectX::XMFLOAT4X4 projection;
};
ComPtr<ID3D11Buffer> m_constantBuffer;
ConstantBuffer m_constantBufferData;

// ...

// Create a constant buffer for passing model, view, and projection matrices
// to the vertex shader.  This allows us to rotate the cube and apply
// a perspective projection to it.

D3D11_BUFFER_DESC constantBufferDesc = {0};
constantBufferDesc.ByteWidth = sizeof(m_constantBufferData);
constantBufferDesc.Usage = D3D11_USAGE_DEFAULT;
constantBufferDesc.BindFlags = D3D11_BIND_CONSTANT_BUFFER;
constantBufferDesc.CPUAccessFlags = 0;
constantBufferDesc.MiscFlags = 0;
constantBufferDesc.StructureByteStride = 0;
m_d3dDevice->CreateBuffer(
                &constantBufferDesc,
                nullptr,
                &m_constantBuffer
             );

m_constantBufferData.model = DirectX::XMFLOAT4X4( // Identity matrix, since you are not animating the object
            1.0f, 0.0f, 0.0f, 0.0f,
            0.0f, 1.0f, 0.0f, 0.0f,
            0.0f, 0.0f, 1.0f, 0.0f,
            0.0f, 0.0f, 0.0f, 1.0f);

);
// Specify the view (camera) transform corresponding to a camera position of
// X = 0, Y = 1, Z = 2.  

m_constantBufferData.view = DirectX::XMFLOAT4X4(
            -1.00000000f, 0.00000000f,  0.00000000f,  0.00000000f,
             0.00000000f, 0.89442718f,  0.44721359f,  0.00000000f,
             0.00000000f, 0.44721359f, -0.89442718f, -2.23606800f,
             0.00000000f, 0.00000000f,  0.00000000f,  1.00000000f);
```

> <span data-ttu-id="d5c7d-222">**Hinweis:** Sie in der Regel deklarieren die Projektionsmatrix beim Einrichten Gerätespezifischer Ressourcen, da die Ergebnisse der multiplikationsergebnisse mit die aktuellen 2D Viewport Größenparametern übereinstimmen müssen (die häufig der Pixelhöhe und-Breite der entsprechen den Zeigen Sie).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-222">**Note**You usually declare the projection matrix when you set up device specific resources, because the results of multiplication with it must match the current 2-D viewport size parameters (which often correspond with the pixel height and width of the display).</span></span> <span data-ttu-id="d5c7d-223">Ändern sich diese, müssen Sie die Werte für die X- und die Y-Koordinate entsprechend skalieren.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-223">If those change, you must scale the x- and y-coordinate values accordingly.</span></span>

 

```cpp
// Finally, update the constant buffer perspective projection parameters
// to account for the size of the application window.  In this sample,
// the parameters are fixed to a 70-degree field of view, with a depth
// range of 0.01 to 100.  

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

<span data-ttu-id="d5c7d-224">Wenn Sie schon einmal dabei sind, legen Sie die Vertex- und Indexpuffer für [ID3D11DeviceContext](https://msdn.microsoft.com/library/windows/desktop/ff476149) sowie die verwendete Topologie fest.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-224">While you're here, set the vertex and index buffers on the[ID3D11DeviceContext](https://msdn.microsoft.com/library/windows/desktop/ff476149), plus the topology you're using.</span></span>

```cpp
// Set the vertex and index buffers, and specify the way they define geometry.
UINT stride = sizeof(SimpleCubeVertex);
UINT offset = 0;
m_d3dDeviceContext->IASetVertexBuffers(
                0,
                1,
                vertexBuffer.GetAddressOf(),
                &stride,
                &offset);

m_d3dDeviceContext->IASetIndexBuffer(
                indexBuffer.Get(),
                DXGI_FORMAT_R16_UINT,
                0);

 m_d3dDeviceContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
```

<span data-ttu-id="d5c7d-225">Gut.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-225">All right!</span></span> <span data-ttu-id="d5c7d-226">Das Eingabeassembly ist fertig.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-226">Input assembly complete.</span></span> <span data-ttu-id="d5c7d-227">Nun ist alles bereit für das Rendern.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-227">Everything's in place for rendering.</span></span> <span data-ttu-id="d5c7d-228">Führen wir also den Vertex-Shader aus.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-228">Let's get that vertex shader going.</span></span>

### <a name="step-6-process-the-mesh-with-the-vertex-shader"></a><span data-ttu-id="d5c7d-229">Schritt6: Verarbeiten des Gitters mit dem Vertex-Shader</span><span class="sxs-lookup"><span data-stu-id="d5c7d-229">Step 6: Process the mesh with the vertex shader</span></span>

<span data-ttu-id="d5c7d-230">Sie haben nun einen Vertexpuffer mit den Vertizes, die Ihr Gitter definieren, und den Indexpuffer, der die Reihenfolge für die Verarbeitung der Vertizes festlegt. Senden Sie die beiden Puffer jetzt an den Vertex-Shader.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-230">Now that you have a vertex buffer with the vertices that define your mesh, and the index buffer that defines the order in which the vertices are processed, you send them to the vertex shader.</span></span> <span data-ttu-id="d5c7d-231">Der Vertex-Shader-Code (ausdrückt als kompilierte High-Level Shader Language (HLSL)) wird ein Mal für jeden Vertex im Vertexpuffer ausgeführt. Dadurch wird die Transformation der einzelnen Vertizes ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-231">The vertex shader code, expressed as compiled high-level shader language, runs one time for each vertex in the vertex buffer, allowing you to perform your per-vertex transforms.</span></span> <span data-ttu-id="d5c7d-232">Das Endergebnis ist in der Regel eine 2D-Projektion.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-232">The final result is typically a 2-D projection.</span></span>

<span data-ttu-id="d5c7d-233">(Haben Sie den Vertex-Shader geladen?</span><span class="sxs-lookup"><span data-stu-id="d5c7d-233">(Did you load your vertex shader?</span></span> <span data-ttu-id="d5c7d-234">Falls nicht, lesen Sie [So wird's gemacht: Laden von Ressourcen im DirectX-Spiel](load-a-game-asset.md).)</span><span class="sxs-lookup"><span data-stu-id="d5c7d-234">If not, review [How to load resources in your DirectX game](load-a-game-asset.md).)</span></span>

<span data-ttu-id="d5c7d-235">Hier erstellen Sie den Vertex-Shader...</span><span class="sxs-lookup"><span data-stu-id="d5c7d-235">Here, you create the vertex shader...</span></span>

``` syntax
// Set the vertex and pixel shader stage state.
m_d3dDeviceContext->VSSetShader(
                vertexShader.Get(),
                nullptr,
                0);
```

<span data-ttu-id="d5c7d-236">...und legen die Konstantenpuffer fest.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-236">...and set the constant buffers.</span></span>

``` syntax
m_d3dDeviceContext->VSSetConstantBuffers(
                0,
                1,
                m_constantBuffer.GetAddressOf());
```

<span data-ttu-id="d5c7d-237">Hier sehen Sie den Vertex-Shader-Code, mit dem die Transformation von Objektkoordinaten zu Weltkoordinaten und schließlich zum Koordinatensystem der 2D-Anzeigeprojektion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-237">Here's the vertex shader code that handles the transformation from object coordinates to world coordinates and then to the 2-D view projection coordinate system.</span></span> <span data-ttu-id="d5c7d-238">Darüber hinaus wenden Sie eine einfache Beleuchtung für einzelne Vertizes an, um das Ganze zu verschönern.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-238">You also apply some simple per-vertex lighting to make things pretty.</span></span> <span data-ttu-id="d5c7d-239">Dies wird in der HLSL-Datei des Vertex-Shaders gespeichert (in diesem Beispiel in „SimplerVertexShader.hlsl“).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-239">This goes in your vertex shader's HLSL file (SimplerVertexShader.hlsl, in this example).</span></span>

``` syntax
cbuffer simpleConstantBuffer : register( b0 )
{
    matrix model;
    matrix view;
    matrix projection;
};

struct VertexShaderInput
{
    DirectX::XMFLOAT3 pos : POSITION;
    DirectX::XMFLOAT3 color : COLOR;
};

struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 color : COLOR;
};

PixelShaderInput SimpleVertexShader(VertexShaderInput input)
{
    PixelShaderInput vertexShaderOutput;
    float4 pos = float4(input.pos, 1.0f);

    // Transform the vertex position into projection space.
    pos = mul(pos, model);
    pos = mul(pos, view);
    pos = mul(pos, projection);
    vertexShaderOutput.pos = pos;

    // Pass the vertex color through to the pixel shader.
    vertexShaderOutput.color = float4(input.color, 1.0f);

    return vertexShaderOutput;
}
```

<span data-ttu-id="d5c7d-240">Sehen Sie **cbuffer** ganz oben?</span><span class="sxs-lookup"><span data-stu-id="d5c7d-240">See that **cbuffer** at the top?</span></span> <span data-ttu-id="d5c7d-241">Dieser HLSL-Code entspricht dem Konstantenpuffer, den wir zuvor in unserem C++-Code deklariert haben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-241">That's the HLSL analogue to the same constant buffer we declared in our C++ code previously.</span></span> <span data-ttu-id="d5c7d-242">Und wie sieht es mit **VertexShaderInputstruct** aus?</span><span class="sxs-lookup"><span data-stu-id="d5c7d-242">And the **VertexShaderInputstruct**?</span></span> <span data-ttu-id="d5c7d-243">Das sieht doch ganz nach der Deklaration Ihres Eingabelayouts und der Vertexdaten aus.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-243">Why, that looks just like your input layout and vertex data declaration!</span></span> <span data-ttu-id="d5c7d-244">Die Deklarationen des Konstantenpuffers und der Vertexdaten im C++-Code müssen mit den Deklarationen im HLSL-Code übereinstimmen – einschließlich Vorzeichen, Typen und Datenausrichtung.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-244">It's important that the constant buffer and vertex data declarations in your C++ code match the declarations in your HLSL code—and that includes signs, types, and data alignment.</span></span>

<span data-ttu-id="d5c7d-245">**PixelShaderInput** gibt das Layout der Daten an, die von der Hauptfunktion des Vertex-Shaders zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-245">**PixelShaderInput** specifies the layout of the data that is returned by the vertex shader's main function.</span></span> <span data-ttu-id="d5c7d-246">Nach der Verarbeitung eines Vertex geben Sie eine Vertexposition im 2D-Projektionsbereich und eine für die Beleuchtung der einzelnen Vertizes verwendete Farbe zurück.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-246">When you finish processing a vertex, you'll return a vertex position in the 2-D projection space and a color used for per-vertex lighting.</span></span> <span data-ttu-id="d5c7d-247">Die Grafikkarte verwendet die Datenausgabe des Shaders zum Berechnen der Fragmente (mögliche Pixel), die koloriert werden müssen, wenn der Pixel-Shader im nächsten Abschnitt der Pipeline ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-247">The graphics card uses data output by the shader to calculate the "fragments" (possible pixels) that must be colored when the pixel shader is run in the next stage of the pipeline.</span></span>

### <a name="step-7-passing-the-mesh-through-the-pixel-shader"></a><span data-ttu-id="d5c7d-248">Schritt7: Übergeben des Gitters durch den Pixel-Shader</span><span class="sxs-lookup"><span data-stu-id="d5c7d-248">Step 7: Passing the mesh through the pixel shader</span></span>

<span data-ttu-id="d5c7d-249">In der Regel führen Sie in diesem Abschnitt der Grafikpipeline Aktionen für einzelne Pixel auf den sichtbaren projizierten Oberflächen der Objekte aus.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-249">Typically, at this stage in the graphics pipeline, you perform per-pixel operations on the visible projected surfaces of your objects.</span></span> <span data-ttu-id="d5c7d-250">(Benutzer stehen auf Texturen.) Zu Beispielzwecken wird das Gitter hier jedoch nur direkt übergegeben.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-250">(People like textures.) For the purposes of sample, though, you simply pass it through this stage.</span></span>

<span data-ttu-id="d5c7d-251">Erstellen wir zunächst eine Instanz des Pixel-Shaders.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-251">First, let's create an instance of the pixel shader.</span></span> <span data-ttu-id="d5c7d-252">Der Pixel-Shader wird für jedes Pixel in der 2D-Projektion der Szene ausgeführt und weist dabei dem jeweiligen Pixel eine Farbe zu.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-252">The pixel shader runs for every pixel in the 2-D projection of your scene, assigning a color to that pixel.</span></span> <span data-ttu-id="d5c7d-253">In diesem Fall wird die vom Vertex-Shader für das Pixel zurückgegebene Farbe direkt weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-253">In this case, we pass the color for the pixel returned by the vertex shader straight through.</span></span>

<span data-ttu-id="d5c7d-254">Legen Sie den Pixel-Shader fest.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-254">Set the pixel shader.</span></span>

``` syntax
m_d3dDeviceContext->PSSetShader( pixelShader.Get(), nullptr, 0 );
```

<span data-ttu-id="d5c7d-255">Definieren Sie einen Passthrough-Pixel-Shader in HLSL.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-255">Define a passthrough pixel shader in HLSL.</span></span>

``` syntax
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

<span data-ttu-id="d5c7d-256">Fügen Sie diesen Code getrennt vom Vertex-Shader-HLSL-Code in eine HLSL-Datei (beispielsweise „SimplePixelShader.hlsl“) ein.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-256">Put this code in an HLSL file separate from the vertex shader HLSL (such as SimplePixelShader.hlsl).</span></span> <span data-ttu-id="d5c7d-257">Dieser Code wird einmal für jedes sichtbare Pixel im Viewport (eine speicherinterne Darstellung des Bildschirmbereichs, in dem Sie zeichnen) ausgeführt. In diesem Fall entspricht er dem gesamten Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-257">This code is run one time for every visible pixel in your viewport (an in-memory representation of the portion of the screen you are drawing to), which, in this case, maps to the entire screen.</span></span> <span data-ttu-id="d5c7d-258">Nun ist Ihre Grafikpipeline vollständig definiert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-258">Now, your graphics pipeline is completely defined!</span></span>

### <a name="step-8-rasterizing-and-displaying-the-mesh"></a><span data-ttu-id="d5c7d-259">Schritt8: Rastern und Anzeigen des Gitters</span><span class="sxs-lookup"><span data-stu-id="d5c7d-259">Step 8: Rasterizing and displaying the mesh</span></span>

<span data-ttu-id="d5c7d-260">Führen Sie die Pipeline aus.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-260">Let's run the pipeline.</span></span> <span data-ttu-id="d5c7d-261">Rufen Sie dazu einfach [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/bb173565) auf.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-261">This is easy: call [**ID3D11DeviceContext::DrawIndexed**](https://msdn.microsoft.com/library/windows/desktop/bb173565).</span></span>

<span data-ttu-id="d5c7d-262">Zeichnen Sie den Würfel.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-262">Draw that cube!</span></span>

```cpp
// Draw the cube.
m_d3dDeviceContext->DrawIndexed( ARRAYSIZE(cubeIndices), 0, 0 );
            
```

<span data-ttu-id="d5c7d-263">Von der Grafikkarte wird jeder Vertex in der im Indexpuffer angegebenen Reihenfolge verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-263">Inside the graphics card, each vertex is processed in the order specified in your index buffer.</span></span> <span data-ttu-id="d5c7d-264">Nachdem der Vertex-Shader von Ihrem Code ausgeführt und die 2D-Fragmente definiert wurden, wird der Pixel-Shader aufgerufen, und die Dreiecke werden koloriert.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-264">After your code has executed the vertex shader and the 2-D fragments are defined, the pixel shader is invoked and the triangles colored.</span></span>

<span data-ttu-id="d5c7d-265">Platzieren Sie nun den Würfel auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-265">Now, put the cube on the screen.</span></span>

<span data-ttu-id="d5c7d-266">Stellen Sie den Framepuffer für die Anzeige bereit.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-266">Present that frame buffer to the display.</span></span>

```cpp
// Present the rendered image to the window.  Because the maximum frame latency is set to 1,
// the render loop is generally  throttled to the screen refresh rate, typically around
// 60 Hz, by sleeping the app on Present until the screen is refreshed.

m_swapChain->Present(1, 0);
```

<span data-ttu-id="d5c7d-267">Nun sind Sie fertig.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-267">And you're done!</span></span> <span data-ttu-id="d5c7d-268">Verwenden Sie für eine mit Modellen gefüllte Szene mehrere Vertex- und Indexpuffer. Möglicherweise haben Sie sogar verschiedene Shader für unterschiedliche Modelltypen.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-268">For a scene full of models, use multiple vertex and index buffers, and you might even have different shaders for different model types.</span></span> <span data-ttu-id="d5c7d-269">Bedenken Sie, dass jedes Modell ein eigenes Koordinatensystem besitzt. Sie müssen die Systeme mithilfe der im konstanten Puffer definierten Matrizen in das gemeinsame Weltkoordinatensystem umwandeln.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-269">Remember that each model has its own coordinate system, and you need to transform them to the shared world coordinate system using the matrices you defined in the constant buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5c7d-270">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-270">Remarks</span></span>

<span data-ttu-id="d5c7d-271">In diesem Thema wird das Erstellen und Anzeigen einfacher, selbst erstellter Geometrie behandelt.</span><span class="sxs-lookup"><span data-stu-id="d5c7d-271">This topic covers creating and displaying simple geometry that you create yourself.</span></span> <span data-ttu-id="d5c7d-272">Weitere Informationen zum Laden komplexerer Geometrie aus einer Datei und Konvertieren in das beispielspezifische Vertexpufferobjekt-Format (VBO) finden Sie unter [So wird's gemacht: Laden von Ressourcen im DirectX-Spiel](load-a-game-asset.md).</span><span class="sxs-lookup"><span data-stu-id="d5c7d-272">For more info about loading more complex geometry from a file and converting it to the sample-specific vertex buffer object (.vbo) format, see [How to load resources in your DirectX game](load-a-game-asset.md).</span></span>  

 

## <a name="related-topics"></a><span data-ttu-id="d5c7d-273">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d5c7d-273">Related topics</span></span>


* [<span data-ttu-id="d5c7d-274">So wird's gemacht: Laden von Ressourcen im DirectX-Spiel</span><span class="sxs-lookup"><span data-stu-id="d5c7d-274">How to load resources in your DirectX game</span></span>](load-a-game-asset.md)

 

 




