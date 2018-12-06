---
title: Konvertieren des Renderingframeworks
description: Hier wird veranschaulicht, wie Sie ein einfaches Renderingframework von Direct3D9 in Direct3D11 konvertieren. Sie erfahren, wie Sie Geometriepuffer portieren, HLSL-Shaderprogramme kompilieren und laden und die Renderkette in Direct3D11 implementieren.
ms.assetid: f6ca1147-9bb8-719a-9a2c-b7ee3e34bd18
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Renderingframeworks, konvertieren, Direct3D 9, Direct3D 11
ms.localizationpriority: medium
ms.openlocfilehash: aba723a5ee2443664d6d640adc124b991ff0da7e
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8744776"
---
# <a name="convert-the-rendering-framework"></a><span data-ttu-id="0b4d0-104">Konvertieren des Renderingframeworks</span><span class="sxs-lookup"><span data-stu-id="0b4d0-104">Convert the rendering framework</span></span>



**<span data-ttu-id="0b4d0-105">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="0b4d0-105">Summary</span></span>**

-   [<span data-ttu-id="0b4d0-106">Teil 1: Initialisieren von Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="0b4d0-106">Part 1: Initialize Direct3D 11</span></span>](simple-port-from-direct3d-9-to-11-1-part-1--initializing-direct3d.md)
-   <span data-ttu-id="0b4d0-107">Teil 2: Konvertieren des Renderingframeworks</span><span class="sxs-lookup"><span data-stu-id="0b4d0-107">Part 2: Convert the rendering framework</span></span>
-   [<span data-ttu-id="0b4d0-108">Teil 3: Portieren der Spielschleife</span><span class="sxs-lookup"><span data-stu-id="0b4d0-108">Part 3: Port the game loop</span></span>](simple-port-from-direct3d-9-to-11-1-part-3--viewport-and-game-loop.md)


<span data-ttu-id="0b4d0-109">Hier wird veranschaulicht, wie Sie ein einfaches Renderingframework von Direct3D9 in Direct3D11 konvertieren. Sie erfahren, wie Sie Geometriepuffer portieren, HLSL-Shaderprogramme kompilieren und laden und die Renderkette in Direct3D11 implementieren.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-109">Shows how to convert a simple rendering framework from Direct3D 9 to Direct3D 11, including how to port geometry buffers, how to compile and load HLSL shader programs, and how to implement the rendering chain in Direct3D 11.</span></span> <span data-ttu-id="0b4d0-110">Teil2 der exemplarischen Vorgehensweise [Portieren einer einfachen Direct3D9-App zu DirectX11 und UWP (Universelle Windows-Plattform)](walkthrough--simple-port-from-direct3d-9-to-11-1.md).</span><span class="sxs-lookup"><span data-stu-id="0b4d0-110">Part 2 of the [Port a simple Direct3D 9 app to DirectX 11 and Universal Windows Platform (UWP)](walkthrough--simple-port-from-direct3d-9-to-11-1.md) walkthrough.</span></span>

## <a name="convert-effects-to-hlsl-shaders"></a><span data-ttu-id="0b4d0-111">Konvertieren der Effekte in HLSL-Shader</span><span class="sxs-lookup"><span data-stu-id="0b4d0-111">Convert effects to HLSL shaders</span></span>


<span data-ttu-id="0b4d0-112">Das folgende Beispiel ist ein einfaches D3DX-Verfahren, das für die ältere Effekt-API, die Hardware-Vertextransformation und Pass-Through-Farbdaten geschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-112">The following example is a simple D3DX technique, written for the legacy Effects API, for hardware vertex transformation and pass-through color data.</span></span>

<span data-ttu-id="0b4d0-113">Direct3D9-Shadercode</span><span class="sxs-lookup"><span data-stu-id="0b4d0-113">Direct3D 9 shader code</span></span>

```cpp
// Global variables
matrix g_mWorld;        // world matrix for object
matrix g_View;          // view matrix
matrix g_Projection;    // projection matrix

// Shader pipeline structures
struct VS_OUTPUT
{
    float4 Position   : POSITION;   // vertex position
    float4 Color      : COLOR0;     // vertex diffuse color
};

struct PS_OUTPUT
{
    float4 RGBColor : COLOR0;  // Pixel color    
};

// Vertex shader
VS_OUTPUT RenderSceneVS(float3 vPos : POSITION, 
                        float3 vColor : COLOR0)
{
    VS_OUTPUT Output;
    
    float4 pos = float4(vPos, 1.0f);

    // Transform the position from object space to homogeneous projection space
    pos = mul(pos, g_mWorld);
    pos = mul(pos, g_View);
    pos = mul(pos, g_Projection);

    Output.Position = pos;
    
    // Just pass through the color data
    Output.Color = float4(vColor, 1.0f);
    
    return Output;
}

// Pixel shader
PS_OUTPUT RenderScenePS(VS_OUTPUT In) 
{ 
    PS_OUTPUT Output;

    Output.RGBColor = In.Color;

    return Output;
}

// Technique
technique RenderSceneSimple
{
    pass P0
    {          
        VertexShader = compile vs_2_0 RenderSceneVS();
        PixelShader  = compile ps_2_0 RenderScenePS(); 
    }
}
```

<span data-ttu-id="0b4d0-114">In Direct3D11 können Sie weiterhin HLSL-Shader verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-114">In Direct3D 11, we can still use our HLSL shaders.</span></span> <span data-ttu-id="0b4d0-115">Jeder Shader wird in eine eigene HLSL-Datei eingefügt, damit diese von Visual Studio in separate Dateien kompiliert werden. Später werden sie dann als separate Direct3D-Ressourcen geladen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-115">We put each shader in its own HLSL file so that Visual Studio compiles them into separate files and later, we'll load them as separate Direct3D resources.</span></span> <span data-ttu-id="0b4d0-116">Wir legen die Zielebene auf [Shadermodell4 Ebene9\_1 (/4\_0\_level\_9\_1)](https://msdn.microsoft.com/library/windows/desktop/ff476876) fest, weil diese Shader für DirectX9.1-GPUs geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-116">We set the target level to [Shader Model 4 Level 9\_1 (/4\_0\_level\_9\_1)](https://msdn.microsoft.com/library/windows/desktop/ff476876) because these shaders are written for DirectX 9.1 GPUs.</span></span>

<span data-ttu-id="0b4d0-117">Beim Definieren des Eingabelayouts haben wir sichergestellt, dass die gleiche Datenstruktur abgebildet wurde, die zum Speichern der Daten pro Vertex im Systemspeicher und im GPU-Speicher verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-117">When we defined the input layout, we made sure it represented the same data structure we use to store per-vertex data in system memory and in GPU memory.</span></span> <span data-ttu-id="0b4d0-118">Ebenso sollte die Ausgabe eines Vertex-Shaders mit der Struktur übereinstimmen, die als Eingabe für den Pixelshader verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-118">Similarly, the output of a vertex shader should match the structure used as input to the pixel shader.</span></span> <span data-ttu-id="0b4d0-119">Die Regeln entsprechen dabei nicht den Regeln zum Übergeben von Daten aus einer Funktion in eine andere unter C++. Sie können nicht verwendete Variablen am Ende der Struktur weglassen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-119">The rules are not the same as passing data from one function to another in C++; you can omit unused variables at the end of the structure.</span></span> <span data-ttu-id="0b4d0-120">Die Reihenfolge kann jedoch nicht erneuert werden, und Sie können Inhalte in der Mitte der Datenstruktur nicht überspringen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-120">But the order can't be rearranged and you can't skip content in the middle of the data structure.</span></span>

> <span data-ttu-id="0b4d0-121">**Hinweis:**  die Regeln in Direct3D 9 zum Binden Vertex-Shadern an PixelShader waren strikt wie die Regeln in Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-121">**Note** The rules in Direct3D 9 for binding vertex shaders to pixel shaders were more relaxed than the rules in Direct3D 11.</span></span> <span data-ttu-id="0b4d0-122">Die Direct3D9-Anordnung war zwar flexibel, aber ineffizient.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-122">The Direct3D 9 arrangement was flexible, but inefficient.</span></span>

 

<span data-ttu-id="0b4d0-123">Es ist möglich, dass von Ihren HLSL-Dateien ältere Syntax für die Shadersemantik verwendet wird, beispielsweise COLOR anstelle von SV\_TARGET.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-123">It's possible that your HLSL files uses older syntax for shader semantics - for example, COLOR instead of SV\_TARGET.</span></span> <span data-ttu-id="0b4d0-124">In diesem Fall müssen Sie den HLSL-Kompatibilitätsmodus (Compileroption "/Gec") aktivieren oder die Shader[semantik](https://msdn.microsoft.com/library/windows/desktop/bb509647) auf die aktuelle Syntax aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-124">If so you'll need to enable HLSL compatibility mode (/Gec compiler option) or update the shader [semantics](https://msdn.microsoft.com/library/windows/desktop/bb509647) to the current syntax.</span></span> <span data-ttu-id="0b4d0-125">Der Vertex-Shader in diesem Beispiel wurde mit der aktuellen Syntax aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-125">The vertex shader in this example has been updated with current syntax.</span></span>

<span data-ttu-id="0b4d0-126">Unten ist der Vertex-Shader für die Hardwaretransformation in einer eigenen Datei definiert.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-126">Here's our hardware transformation vertex shader, this time defined in its own file.</span></span>

> <span data-ttu-id="0b4d0-127">**Hinweis:** Vertex-Shader sind erforderlich, um die SV\_POSITION-systemwertsemantik auszugeben.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-127">**Note**Vertex shaders are required to output the SV\_POSITION system value semantic.</span></span> <span data-ttu-id="0b4d0-128">Mit dieser Semantik werden die Vertexpositionsdaten zu Koordinatenwerten aufgelöst, wobei "x" zwischen-1 und1 und "y" zwischen-1 und1 liegt. "z" wird durch den ursprünglichen homogenen Koordinatenwert"w" dividiert (z/w), und "w" ist1 dividiert durch den Originalwert"w" (1/w).</span><span class="sxs-lookup"><span data-stu-id="0b4d0-128">This semantic resolves the vertex position data to coordinate values where x is between -1 and 1, y is between -1 and 1, z is divided by the original homogeneous coordinate w value (z/w), and w is 1 divided by the original w value (1/w).</span></span>

 

<span data-ttu-id="0b4d0-129">HLSL-Vertex-Shader (Featureebene9.1)</span><span class="sxs-lookup"><span data-stu-id="0b4d0-129">HLSL vertex shader (feature level 9.1)</span></span>

```cpp
cbuffer ModelViewProjectionConstantBuffer : register(b0)
{
    matrix mWorld;       // world matrix for object
    matrix View;        // view matrix
    matrix Projection;  // projection matrix
};

struct VS_INPUT
{
    float3 vPos   : POSITION;
    float3 vColor : COLOR0;
};

struct VS_OUTPUT
{
    float4 Position : SV_POSITION; // Vertex shaders must output SV_POSITION
    float4 Color    : COLOR0;
};

VS_OUTPUT main(VS_INPUT input) // main is the default function name
{
    VS_OUTPUT Output;

    float4 pos = float4(input.vPos, 1.0f);

    // Transform the position from object space to homogeneous projection space
    pos = mul(pos, mWorld);
    pos = mul(pos, View);
    pos = mul(pos, Projection);
    Output.Position = pos;

    // Just pass through the color data
    Output.Color = float4(input.vColor, 1.0f);

    return Output;
}
```

<span data-ttu-id="0b4d0-130">Dies ist alles, was wir für den Pass-Through-Pixelshader brauchen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-130">This is all we need for our pass-through pixel shader.</span></span> <span data-ttu-id="0b4d0-131">Obwohl die Bezeichnung "Pass-Through" verwendet wird, werden für jedes Pixel jeweils für die Perspektive passende interpolierte Farbdaten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-131">Even though we call it a pass-through, it's actually getting perspective-correct interpolated color data for each pixel.</span></span> <span data-ttu-id="0b4d0-132">Beachten Sie, dass die SV\_TARGET-Systemwertsemantik hier vom Pixelshader auf die Farbwertausgabe angewendet wird, wie dies für die API erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-132">Note that the SV\_TARGET system value semantic is applied to the color value output by our pixel shader as required by the API.</span></span>

> <span data-ttu-id="0b4d0-133">**Hinweis:** PixelShader der Featureebene 9\_x können nicht aus der SV\_POSITION-systemwertsemantik gelesen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-133">**Note**Shader level 9\_x pixel shaders cannot read from the SV\_POSITION system value semantic.</span></span> <span data-ttu-id="0b4d0-134">Für Pixelshader des Modells4.0 (oder höher) kann das SV\_POSITION-Element zum Abrufen der Pixelposition auf dem Bildschirm verwendet werden, wobei "x" zwischen0 und der Breite des Renderziels und "y" zwischen0 und der Höhe des Renderziels liegt (jeweils um den Wert0,5 versetzt).</span><span class="sxs-lookup"><span data-stu-id="0b4d0-134">Model 4.0 (and higher) pixel shaders can use SV\_POSITION to retrieve the pixel location on the screen, where x is between 0 and the render target width and y is between 0 and the render target height (each offset by 0.5).</span></span>

 

<span data-ttu-id="0b4d0-135">Die meisten Pixelshader sind viel komplexer als ein Pass-Through-Element aufgebaut. Beachten Sie, dass höhere Direct3D-Featureebenen auch eine deutlich größere Anzahl an Berechnungen pro Shaderprogramm ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-135">Most pixel shaders are much more complex than a pass through; note that higher Direct3D feature levels allow a much greater number of calculations per shader program.</span></span>

<span data-ttu-id="0b4d0-136">HLSL-Pixelshader (Featureebene9.1)</span><span class="sxs-lookup"><span data-stu-id="0b4d0-136">HLSL pixel shader (feature level 9.1)</span></span>

```cpp
struct PS_INPUT
{
    float4 Position : SV_POSITION;  // interpolated vertex position (system value)
    float4 Color    : COLOR0;       // interpolated diffuse color
};

struct PS_OUTPUT
{
    float4 RGBColor : SV_TARGET;  // pixel color (your PS computes this system value)
};

PS_OUTPUT main(PS_INPUT In)
{
    PS_OUTPUT Output;

    Output.RGBColor = In.Color;

    return Output;
}
```

## <a name="compile-and-load-shaders"></a><span data-ttu-id="0b4d0-137">Kompilieren und Laden von Shadern</span><span class="sxs-lookup"><span data-stu-id="0b4d0-137">Compile and load shaders</span></span>


<span data-ttu-id="0b4d0-138">In Direct3D 9-Spielen wurde die Effektbibliothek häufig als bequeme Möglichkeit zum Implementieren programmierbarer Pipelines genutzt.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-138">Direct3D 9 games often used the Effects library as a convenient way to implement programmable pipelines.</span></span> <span data-ttu-id="0b4d0-139">Effekte können zur Laufzeit mit der [**D3DXCreateEffectFromFile function**](https://msdn.microsoft.com/library/windows/desktop/bb172768)-Methode kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-139">Effects could be compiled at run-time using the [**D3DXCreateEffectFromFile function**](https://msdn.microsoft.com/library/windows/desktop/bb172768) method.</span></span>

<span data-ttu-id="0b4d0-140">Laden eines Effekts in Direct3D 9</span><span class="sxs-lookup"><span data-stu-id="0b4d0-140">Loading an effect in Direct3D 9</span></span>

```cpp
// Turn off preshader optimization to keep calculations on the GPU
DWORD dwShaderFlags = D3DXSHADER_NO_PRESHADER;

// Only enable debug info when compiling for a debug target
#if defined (DEBUG) || defined (_DEBUG)
dwShaderFlags |= D3DXSHADER_DEBUG;
#endif

D3DXCreateEffectFromFile(
    m_pd3dDevice,
    L"CubeShaders.fx",
    NULL,
    NULL,
    dwShaderFlags,
    NULL,
    &m_pEffect,
    NULL
    );
```

<span data-ttu-id="0b4d0-141">In Direct3D 11 können Shaderprogramme als binäre Ressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-141">Direct3D 11 works with shader programs as binary resources.</span></span> <span data-ttu-id="0b4d0-142">Shader werden kompiliert, wenn das Projekt erstellt wird, und dann als Ressourcen behandelt.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-142">Shaders are compiled when the project is built and then treated as resources.</span></span> <span data-ttu-id="0b4d0-143">In diesem Beispiel wird der Shader-Bytecode in den Systemspeicher geladen, die Direct3D-Geräteschnittstelle zum Erstellen einer Direct3D-Ressource für jeden Shader verwendet und jeweils auf die Direct3D-Shaderressourcen verwiesen, wenn ein Frame eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-143">So our example will load the shader bytecode into system memory, use the Direct3D device interface to create a Direct3D resource for each shader, and point to the Direct3D shader resources when we set up each frame.</span></span>

<span data-ttu-id="0b4d0-144">Laden einer Shaderressource in Direct3D11</span><span class="sxs-lookup"><span data-stu-id="0b4d0-144">Loading a shader resource in Direct3D 11</span></span>

```cpp
// BasicReaderWriter is a tested file loader used in SDK samples.
BasicReaderWriter^ readerWriter = ref new BasicReaderWriter();


// Load vertex shader:
Platform::Array<byte>^ vertexShaderData =
    readerWriter->ReadData("CubeVertexShader.cso");

// This call allocates a device resource, validates the vertex shader 
// with the device feature level, and stores the vertex shader bits in 
// graphics memory.
m_d3dDevice->CreateVertexShader(
    vertexShaderData->Data,
    vertexShaderData->Length,
    nullptr,
    &m_vertexShader
    );
```

<span data-ttu-id="0b4d0-145">Fügen Sie zum Einbinden von Shader-Bytecode in das kompilierte App-Paket dem Visual Studio-Projekt einfach die HLSL-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-145">To include the shader bytecode in your compiled app package, just add the HLSL file to the Visual Studio project.</span></span> <span data-ttu-id="0b4d0-146">In Visual Studio wird das [Effektcompiler-Tool](https://msdn.microsoft.com/library/windows/desktop/bb232919) (FXC) verwendet, um HLSL-Dateien in kompilierte Shaderobjekte (CSO-Dateien) zu kompilieren und in das App-Paket einzubinden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-146">Visual Studio will use the [Effect-Compiler Tool](https://msdn.microsoft.com/library/windows/desktop/bb232919) (FXC) to compile HLSL files into compiled shader objects (.CSO files) and include them in the app package.</span></span>

> <span data-ttu-id="0b4d0-147">**Hinweis:**  müssen Sie die richtige zielfeatureebene für den HLSL-Compiler festlegen: mit der rechten Maustaste der HLSL-Quelldatei in Visual Studio, klicken Sie auf Eigenschaften und ändern Sie die **Shader Model** -Einstellung unter **HLSL-Compiler -&gt; allgemeine**.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-147">**Note** Be sure to set the correct target feature level for the HLSL compiler: right-click the HLSL source file in Visual Studio, select Properties, and change the **Shader Model** setting under **HLSL Compiler -&gt; General**.</span></span> <span data-ttu-id="0b4d0-148">In Direct3D wird diese Eigenschaft anhand der Hardwarefunktionen überprüft, wenn von der App die Direct3D-Shaderressource erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-148">Direct3D checks this property against the hardware capabilities when your app creates the Direct3D shader resource.</span></span>

 

![HLSL-Shadereigenschaften](images/hlslshaderpropertiesmenu.png)![HLSL-Shadertyp](images/hlslshadertypeproperties.png)

<span data-ttu-id="0b4d0-151">Dies ist ein guter Ort zum Erstellen des Eingabelayouts, welches der Deklaration des Vertexstreams in Direct3D 9 entspricht.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-151">This is a good place to create the input layout, which corresponds to the vertex stream declaration in Direct3D 9.</span></span> <span data-ttu-id="0b4d0-152">Die Datenstruktur pro Vertex muss mit der Struktur übereinstimmen, die vom Vertex-Shader verwendet wird. In Direct3D11 ist eine bessere Steuerung des Eingabelayouts möglich. Sie können die Arraygröße und Bitlänge von Gleitkommavektoren definieren und die Semantik für den Vertex-Shader angeben.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-152">The per-vertex data structure needs to match what the vertex shader uses; in Direct3D 11 we have more control over the input layout; we can define the array size and bit length of floating-point vectors and specify semantics for the vertex shader.</span></span> <span data-ttu-id="0b4d0-153">Wir erstellen eine [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180)-Struktur und verwenden sie, um für Direct3D anzugeben, wie die Daten pro Vertex aussehen sollen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-153">We create a [**D3D11\_INPUT\_ELEMENT\_DESC**](https://msdn.microsoft.com/library/windows/desktop/ff476180) structure and use it to inform Direct3D what the per-vertex data will look like.</span></span> <span data-ttu-id="0b4d0-154">Wir haben das Laden des Vertex-Shaders abgewartet, bevor das Eingabelayout definiert wurde. Der Grund ist, dass das Eingabelayout von der API anhand der Vertex-Shaderressource überprüft wird.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-154">We waited until after we loaded the vertex shader to define the input layout because the API validates the input layout against the vertex shader resource.</span></span> <span data-ttu-id="0b4d0-155">Wenn das Eingabelayout nicht kompatibel ist, löst Direct3D eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-155">If the input layout isn't compatible then Direct3D throws an exception.</span></span>

<span data-ttu-id="0b4d0-156">Daten pro Vertex müssen im Systemspeicher in Form von kompatiblen Typen gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-156">Per-vertex data has to be stored in compatible types in system memory.</span></span> <span data-ttu-id="0b4d0-157">Hierbei können DirectXMath-Datentypen hilfreich sein. DXGI\_FORMAT\_R32G32B32\_FLOAT entspricht beispielsweise [**XMFLOAT3**](https://msdn.microsoft.com/library/windows/desktop/ee419475).</span><span class="sxs-lookup"><span data-stu-id="0b4d0-157">DirectXMath data types can help; for example, DXGI\_FORMAT\_R32G32B32\_FLOAT corresponds to [**XMFLOAT3**](https://msdn.microsoft.com/library/windows/desktop/ee419475).</span></span>

> <span data-ttu-id="0b4d0-158">**Hinweis:**  Konstantenpuffer verwendet eine feste festes eingabelayout mit für vier Gleitkommazahlen gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-158">**Note** Constant buffers use a fixed input layout that aligns to four floating-point numbers at a time.</span></span> <span data-ttu-id="0b4d0-159">[**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) (und die Ableitungen) wird für die Daten von Konstantenpuffern empfohlen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-159">[**XMFLOAT4**](https://msdn.microsoft.com/library/windows/desktop/ee419608) (and its derivatives) are recommended for constant buffer data.</span></span>

 

<span data-ttu-id="0b4d0-160">Festlegen des Eingabelayouts in Direct3D11</span><span class="sxs-lookup"><span data-stu-id="0b4d0-160">Setting the input layout in Direct3D 11</span></span>

```cpp
// Create input layout:
const D3D11_INPUT_ELEMENT_DESC vertexDesc[] = 
{
    { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT,
        0, 0,  D3D11_INPUT_PER_VERTEX_DATA, 0 },

    { "COLOR",    0, DXGI_FORMAT_R32G32B32_FLOAT, 
        0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};
```

## <a name="create-geometry-resources"></a><span data-ttu-id="0b4d0-161">Erstellen von Geometrieressourcen</span><span class="sxs-lookup"><span data-stu-id="0b4d0-161">Create geometry resources</span></span>


<span data-ttu-id="0b4d0-162">In Direct3D9 wurden Geometrieressourcen gespeichert, indem Puffer auf dem Direct3D-Gerät erstellt wurden, der Speicher gesperrt wurde und Daten aus dem CPU-Speicher in den GPU-Speicher kopiert wurden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-162">In Direct3D 9 we stored geometry resources by creating buffers on the Direct3D device, locking the memory, and copying data from CPU memory to GPU memory.</span></span>

<span data-ttu-id="0b4d0-163">Direct3D9</span><span class="sxs-lookup"><span data-stu-id="0b4d0-163">Direct3D 9</span></span>

```cpp
// Create vertex buffer:
VOID* pVertices;

// In Direct3D 9 we create the buffer, lock it, and copy the data from 
// system memory to graphics memory.
m_pd3dDevice->CreateVertexBuffer(
    sizeof(CubeVertices),
    0,
    D3DFVF_XYZ | D3DFVF_DIFFUSE,
    D3DPOOL_MANAGED,
    &pVertexBuffer,
    NULL);

pVertexBuffer->Lock(
    0,
    sizeof(CubeVertices),
    &pVertices,
    0);

memcpy(pVertices, CubeVertices, sizeof(CubeVertices));
pVertexBuffer->Unlock();
```

<span data-ttu-id="0b4d0-164">Für DirectX11 wird ein einfacherer Prozess genutzt.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-164">DirectX 11 follows a simpler process.</span></span> <span data-ttu-id="0b4d0-165">Von der API werden die Daten automatisch aus dem Systemspeicher in die GPU kopiert.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-165">The API automatically copies the data from system memory to the GPU.</span></span> <span data-ttu-id="0b4d0-166">Wir können intelligente COM-Zeiger verwenden, um die Programmierung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-166">We can use COM smart pointers to help make programming easier.</span></span>

<span data-ttu-id="0b4d0-167">DirectX11</span><span class="sxs-lookup"><span data-stu-id="0b4d0-167">DirectX 11</span></span>

```cpp
D3D11_SUBRESOURCE_DATA vertexBufferData = {0};
vertexBufferData.pSysMem = CubeVertices;
vertexBufferData.SysMemPitch = 0;
vertexBufferData.SysMemSlicePitch = 0;
CD3D11_BUFFER_DESC vertexBufferDesc(
    sizeof(CubeVertices),
    D3D11_BIND_VERTEX_BUFFER);
  
// This call allocates a device resource for the vertex buffer and copies
// in the data.
m_d3dDevice->CreateBuffer(
    &vertexBufferDesc,
    &vertexBufferData,
    &m_vertexBuffer
    );
```

## <a name="implement-the-rendering-chain"></a><span data-ttu-id="0b4d0-168">Implementieren der Renderkette</span><span class="sxs-lookup"><span data-stu-id="0b4d0-168">Implement the rendering chain</span></span>


<span data-ttu-id="0b4d0-169">Für Direct3D9-Spiele wurde häufig eine auf Effekten basierende Renderkette genutzt.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-169">Direct3D 9 games often used an effect-based rendering chain.</span></span> <span data-ttu-id="0b4d0-170">Mit dieser Art von Renderkette wird das Effektobjekt eingerichtet, die benötigten Ressourcen werden bereitgestellt, und die einzelnen Durchläufe werden gerendert.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-170">This type of rendering chain sets up the effect object, provides it with the resources it needs, and lets it render each pass.</span></span>

<span data-ttu-id="0b4d0-171">Direct3D9-Renderkette</span><span class="sxs-lookup"><span data-stu-id="0b4d0-171">Direct3D 9 rendering chain</span></span>

```cpp
// Clear the render target and the z-buffer.
m_pd3dDevice->Clear(
    0, NULL,
    D3DCLEAR_TARGET | D3DCLEAR_ZBUFFER,
    D3DCOLOR_ARGB(0, 45, 50, 170),
    1.0f, 0
    );

// Set the effect technique
m_pEffect->SetTechnique("RenderSceneSimple");

// Rotate the cube 1 degree per frame.
D3DXMATRIX world;
D3DXMatrixRotationY(&world, D3DXToRadian(m_frameCount++));


// Set the matrices up using traditional functions.
m_pEffect->SetMatrix("g_mWorld", &world);
m_pEffect->SetMatrix("g_View", &m_view);
m_pEffect->SetMatrix("g_Projection", &m_projection);

// Render the scene using the Effects library.
if(SUCCEEDED(m_pd3dDevice->BeginScene()))
{
    // Begin rendering effect passes.
    UINT passes = 0;
    m_pEffect->Begin(&passes, 0);
    
    for (UINT i = 0; i < passes; i++)
    {
        m_pEffect->BeginPass(i);
        
        // Send vertex data to the pipeline.
        m_pd3dDevice->SetFVF(D3DFVF_XYZ | D3DFVF_DIFFUSE);
        m_pd3dDevice->SetStreamSource(
            0, pVertexBuffer,
            0, sizeof(VertexPositionColor)
            );
        m_pd3dDevice->SetIndices(pIndexBuffer);
        
        // Draw the cube.
        m_pd3dDevice->DrawIndexedPrimitive(
            D3DPT_TRIANGLELIST,
            0, 0, 8, 0, 12
            );
        m_pEffect->EndPass();
    }
    m_pEffect->End();
    
    // End drawing.
    m_pd3dDevice->EndScene();
}

// Present frame:
// Show the frame on the primary surface.
m_pd3dDevice->Present(NULL, NULL, NULL, NULL);
```

<span data-ttu-id="0b4d0-172">Mit der DirectX11-Renderkette werden diese Aufgaben auch weiterhin ausgeführt, aber die Renderdurchläufe müssen anders implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-172">The DirectX 11 rendering chain will still do the same tasks, but the rendering passes need to be implemented differently.</span></span> <span data-ttu-id="0b4d0-173">Anstatt die speziellen Angaben in FX-Dateien einzufügen und die Renderverfahren für den C++-Code mehr oder weniger undurchschaubar zu machen, werden alle Rendervorgänge unter C++ eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-173">Instead of putting the specifics in FX files and letting the rendering techniques be more-or-less opaque to our C++ code, we'll set up all our rendering in C++.</span></span>

<span data-ttu-id="0b4d0-174">Unten ist die Renderkette angegeben.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-174">Here's how our rendering chain will look.</span></span> <span data-ttu-id="0b4d0-175">Wir müssen das Eingabelayout angeben, das wir nach dem Laden des Vertex-Shaders erstellt haben, die einzelnen Shaderobjekte bereitstellen und angeben, welche Konstantenpuffer von den einzelnen Shadern verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-175">We need to supply the input layout we created after loading the vertex shader, supply each of the shader objects, and specify the constant buffers for each shader to use.</span></span> <span data-ttu-id="0b4d0-176">Dieses Beispiel enthält nicht mehrere Renderdurchläufe. Wäre dies der Fall, würden wir für jeden Durchlauf eine ähnliche Renderkette erstellen und das Setup jeweils je nach Bedarf ändern.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-176">This example doesn't include multiple rendering passes, but if it did we'd do a similar rendering chain for each pass, changing the setup as needed.</span></span>

<span data-ttu-id="0b4d0-177">Direct3D11-Renderkette</span><span class="sxs-lookup"><span data-stu-id="0b4d0-177">Direct3D 11 rendering chain</span></span>

```cpp
// Clear the back buffer.
const float midnightBlue[] = { 0.098f, 0.098f, 0.439f, 1.000f };
m_d3dContext->ClearRenderTargetView(
    m_renderTargetView.Get(),
    midnightBlue
    );

// Set the render target. This starts the drawing operation.
m_d3dContext->OMSetRenderTargets(
    1,  // number of render target views for this drawing operation.
    m_renderTargetView.GetAddressOf(),
    nullptr
    );


// Rotate the cube 1 degree per frame.
XMStoreFloat4x4(
    &m_constantBufferData.model, 
    XMMatrixTranspose(XMMatrixRotationY(m_frameCount++ * XM_PI / 180.f))
    );

// Copy the updated constant buffer from system memory to video memory.
m_d3dContext->UpdateSubresource(
    m_constantBuffer.Get(),
    0,      // update the 0th subresource
    NULL,   // use the whole destination
    &m_constantBufferData,
    0,      // default pitch
    0       // default pitch
    );


// Send vertex data to the Input Assembler stage.
UINT stride = sizeof(VertexPositionColor);
UINT offset = 0;

m_d3dContext->IASetVertexBuffers(
    0,  // start with the first vertex buffer
    1,  // one vertex buffer
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
    );

m_d3dContext->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT,
    0   // no offset
    );

m_d3dContext->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
m_d3dContext->IASetInputLayout(m_inputLayout.Get());


// Set the vertex shader.
m_d3dContext->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// Set the vertex shader constant buffer data.
m_d3dContext->VSSetConstantBuffers(
    0,  // register 0
    1,  // one constant buffer
    m_constantBuffer.GetAddressOf()
    );


// Set the pixel shader.
m_d3dContext->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
    );


// Draw the cube.
m_d3dContext->DrawIndexed(
    m_indexCount,
    0,  // start with index 0
    0   // start with vertex 0
    );
```

<span data-ttu-id="0b4d0-178">Die Swapchain ist Teil der Grafikinfrastruktur, sodass wir unsere DXGI-Swapchain verwenden, um den fertigen Frame darzustellen.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-178">The swap chain is part of graphics infrastructure, so we use our DXGI swap chain to present the completed frame.</span></span> <span data-ttu-id="0b4d0-179">DXGI blockiert den Aufruf bis zum nächsten vsync-Vorgang. Dann erfolgt die Rückgabe, und die Spielschleife kann mit der nächsten Iteration fortfahren.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-179">DXGI blocks the call until the next vsync; then it returns, and our game loop can continue to the next iteration.</span></span>

<span data-ttu-id="0b4d0-180">Darstellen eines Frames auf dem Bildschirm mithilfe von DirectX11</span><span class="sxs-lookup"><span data-stu-id="0b4d0-180">Presenting a frame to the screen using DirectX 11</span></span>

```cpp
m_swapChain->Present(1, 0);
```

<span data-ttu-id="0b4d0-181">Die gerade erstellte Renderkette wird von einer Spielschleife aufgerufen, die in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-181">The rendering chain we just created will be called from a game loop implemented in the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method.</span></span> <span data-ttu-id="0b4d0-182">Dies wird unter [Teil3: Viewport und Spielschleife](simple-port-from-direct3d-9-to-11-1-part-3--viewport-and-game-loop.md) veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="0b4d0-182">This is shown in [Part 3: Viewport and game loop](simple-port-from-direct3d-9-to-11-1-part-3--viewport-and-game-loop.md).</span></span>

 

 




