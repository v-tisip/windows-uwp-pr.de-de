---
author: mtoepke
title: Unterstützen von Schattenmaps für unterschiedliche Hardware
description: Rendern Sie Schatten in noch besserer Qualität auf schnelleren Geräten und schnellere Schatten auf weniger leistungsfähigen Geräten.
ms.assetid: d97c0544-44f2-4e29-5e02-54c45e0dff4e
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Schattenmaps, DirectX
ms.localizationpriority: medium
ms.openlocfilehash: a9c53578fc67c13aafa1c8e39ad1d2910981081d
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6651811"
---
# <a name="support-shadow-maps-on-a-range-of-hardware"></a><span data-ttu-id="7f38a-104">Unterstützen von Schattenmaps für unterschiedliche Hardware</span><span class="sxs-lookup"><span data-stu-id="7f38a-104">Support shadow maps on a range of hardware</span></span>




<span data-ttu-id="7f38a-105">Rendern Sie Schatten in noch besserer Qualität auf schnelleren Geräten und schnellere Schatten auf weniger leistungsfähigen Geräten.</span><span class="sxs-lookup"><span data-stu-id="7f38a-105">Render higher-fidelity shadows on faster devices and faster shadows on less powerful devices.</span></span> <span data-ttu-id="7f38a-106">Teil4 von [Exemplarische Vorgehensweise: Implementieren von Schattenvolumes mithilfe von Tiefenpuffern in Direct3D11](implementing-depth-buffers-for-shadow-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="7f38a-106">Part 4 of [Walkthrough: Implement shadow volumes using depth buffers in Direct3D 11](implementing-depth-buffers-for-shadow-mapping.md).</span></span>

## <a name="comparison-filter-types"></a><span data-ttu-id="7f38a-107">Arten von Vergleichsfiltern</span><span class="sxs-lookup"><span data-stu-id="7f38a-107">Comparison filter types</span></span>


<span data-ttu-id="7f38a-108">Verwenden Sie die lineare Filterung nur, wenn das Gerät die Leistungseinbußen verkraften kann.</span><span class="sxs-lookup"><span data-stu-id="7f38a-108">Only use linear filtering if the device can afford the performance penalty.</span></span> <span data-ttu-id="7f38a-109">Im Allgemeinen verfügen Geräte mit Direct3D-Featureebene9\_1 nicht über eine ausreichende Leistung, um einen Teil davon für die lineare Filterung von Schatten bereitstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="7f38a-109">Generally, Direct3D feature level 9\_1 devices don't have enough power to spare for linear filtering on shadows.</span></span> <span data-ttu-id="7f38a-110">Nutzen Sie auf diesen Geräten stattdessen die Punktfilterung.</span><span class="sxs-lookup"><span data-stu-id="7f38a-110">Use point filtering instead on these devices.</span></span> <span data-ttu-id="7f38a-111">Passen Sie beim Verwenden der linearen Filterung den Pixelshader so an, dass die Schattenkanten ineinander verlaufen.</span><span class="sxs-lookup"><span data-stu-id="7f38a-111">When you use linear filtering, adjust the pixel shader so that it blends the shadow edges.</span></span>

<span data-ttu-id="7f38a-112">Erstellen Sie den Vergleichssampler für die Punktfilterung:</span><span class="sxs-lookup"><span data-stu-id="7f38a-112">Create the comparison sampler for point filtering:</span></span>

```cpp
D3D11_SAMPLER_DESC comparisonSamplerDesc;
ZeroMemory(&comparisonSamplerDesc, sizeof(D3D11_SAMPLER_DESC));
comparisonSamplerDesc.AddressU = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.AddressV = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.AddressW = D3D11_TEXTURE_ADDRESS_BORDER;
comparisonSamplerDesc.BorderColor[0] = 1.0f;
comparisonSamplerDesc.BorderColor[1] = 1.0f;
comparisonSamplerDesc.BorderColor[2] = 1.0f;
comparisonSamplerDesc.BorderColor[3] = 1.0f;
comparisonSamplerDesc.MinLOD = 0.f;
comparisonSamplerDesc.MaxLOD = D3D11_FLOAT32_MAX;
comparisonSamplerDesc.MipLODBias = 0.f;
comparisonSamplerDesc.MaxAnisotropy = 0;
comparisonSamplerDesc.ComparisonFunc = D3D11_COMPARISON_LESS_EQUAL;
comparisonSamplerDesc.Filter = D3D11_FILTER_COMPARISON_MIN_MAG_MIP_POINT;

// Point filtered shadows can be faster, and may be a good choice when
// rendering on hardware with lower feature levels. This sample has a
// UI option to enable/disable filtering so you can see the difference
// in quality and speed.

DX::ThrowIfFailed(
    pD3DDevice->CreateSamplerState(
        &comparisonSamplerDesc,
        &m_comparisonSampler_point
        )
    );
```

<span data-ttu-id="7f38a-113">Erstellen Sie anschließend einen Sampler für die lineare Filterung:</span><span class="sxs-lookup"><span data-stu-id="7f38a-113">Then create a sampler for linear filtering:</span></span>

```cpp
comparisonSamplerDesc.Filter = D3D11_FILTER_COMPARISON_MIN_MAG_MIP_LINEAR;
DX::ThrowIfFailed(
    pD3DDevice->CreateSamplerState(
        &comparisonSamplerDesc,
        &m_comparisonSampler_linear
        )
    );
```

<span data-ttu-id="7f38a-114">Wählen Sie einen Sampler aus:</span><span class="sxs-lookup"><span data-stu-id="7f38a-114">Choose a sampler:</span></span>

```cpp
ID3D11PixelShader* pixelShader;
ID3D11SamplerState** comparisonSampler;
if (m_useLinear)
{
    pixelShader = m_shadowPixelShader_linear.Get();
    comparisonSampler = m_comparisonSampler_linear.GetAddressOf();
}
else
{
    pixelShader = m_shadowPixelShader_point.Get();
    comparisonSampler = m_comparisonSampler_point.GetAddressOf();
}

// Attach our pixel shader.
context->PSSetShader(
    pixelShader,
    nullptr,
    0
    );

context->PSSetSamplers(0, 1, comparisonSampler);
context->PSSetShaderResources(0, 1, m_shadowResourceView.GetAddressOf());
```

<span data-ttu-id="7f38a-115">Schattenkanten mit linearer Filterung vermischen:</span><span class="sxs-lookup"><span data-stu-id="7f38a-115">Blend shadow edges with linear filtering:</span></span>

```cpp
// Blends the shadow area into the lit area.
float3 light = lighting * (ambient + DplusS(N, L, NdotL, input.view));
float3 shadow = (1.0f - lighting) * ambient;
return float4(input.color * (light + shadow), 1.f);
```

## <a name="shadow-buffer-size"></a><span data-ttu-id="7f38a-116">Schattenpuffergröße</span><span class="sxs-lookup"><span data-stu-id="7f38a-116">Shadow buffer size</span></span>


<span data-ttu-id="7f38a-117">Größere Schattenmaps sehen weniger "eckig" aus, aber sie nehmen mehr Speicherplatz im Grafikspeicher ein.</span><span class="sxs-lookup"><span data-stu-id="7f38a-117">Larger shadow maps won't look as blocky but they take up more space in graphics memory.</span></span> <span data-ttu-id="7f38a-118">Experimentieren Sie im Spiel mit unterschiedlichen Größen von Schattenmaps, und beobachten Sie, welche Ergebnisse Sie für unterschiedliche Arten von Geräten und unterschiedliche Anzeigegrößen erzielen.</span><span class="sxs-lookup"><span data-stu-id="7f38a-118">Experiment with different shadow map sizes in your game and observe the results in different types of devices and different display sizes.</span></span> <span data-ttu-id="7f38a-119">Erwägen Sie eine Optimierung, z.B. mithilfe von kaskadierenden Schattenmaps, um bessere Ergebnisse mit geringerem Grafikspeicheraufwand zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7f38a-119">Consider an optimization like cascaded shadow maps to get better results with less graphics memory.</span></span> <span data-ttu-id="7f38a-120">Weitere Informationen finden Sie unter [Häufig verwendete Methoden zur Verbesserung von Tiefenmaps für Schatten](https://msdn.microsoft.com/library/windows/desktop/ee416324).</span><span class="sxs-lookup"><span data-stu-id="7f38a-120">See [Common Techniques to Improve Shadow Depth Maps](https://msdn.microsoft.com/library/windows/desktop/ee416324).</span></span>

## <a name="shadow-buffer-depth"></a><span data-ttu-id="7f38a-121">Schattenpuffertiefe</span><span class="sxs-lookup"><span data-stu-id="7f38a-121">Shadow buffer depth</span></span>


<span data-ttu-id="7f38a-122">Eine höhere Präzision im Schattenpuffer führt zu genaueren Ergebnissen bei Tiefentests. Dies trägt zur Verhinderung von Problemen bei, z.B. von Z-Bufferkonflikten.</span><span class="sxs-lookup"><span data-stu-id="7f38a-122">Greater precision in the shadow buffer will give more accurate depth test results, which helps avoid issues like z-buffer fighting.</span></span> <span data-ttu-id="7f38a-123">Wie bei größeren Schattenmaps auch wird bei einer höheren Präzision mehr Speicher belegt.</span><span class="sxs-lookup"><span data-stu-id="7f38a-123">But like larger shadow maps, greater precision takes up more memory.</span></span> <span data-ttu-id="7f38a-124">Experimentieren Sie mit unterschiedlichen Arten von Tiefenpräzision (DXGI\_FORMAT\_R24G8\_TYPELESS im Gegensatz zu DXGI\_FORMAT\_R16\_TYPELESS), und beobachten Sie die Geschwindigkeit und Qualität auf unterschiedlichen Featureebenen.</span><span class="sxs-lookup"><span data-stu-id="7f38a-124">Experiment with different depth precision types in your game - DXGI\_FORMAT\_R24G8\_TYPELESS versus DXGI\_FORMAT\_R16\_TYPELESS - and observe the speed and quality on different feature levels.</span></span>

## <a name="optimizing-precompiled-shaders"></a><span data-ttu-id="7f38a-125">Optimieren vorkompilierter Shader</span><span class="sxs-lookup"><span data-stu-id="7f38a-125">Optimizing precompiled shaders</span></span>


<span data-ttu-id="7f38a-126">UWP-Apps (Universelle Windows-Plattform) können eine dynamische Shaderkompilierung nutzen, die Verwendung einer dynamischen Shaderverknüpfung ist jedoch schneller.</span><span class="sxs-lookup"><span data-stu-id="7f38a-126">Universal Windows Platform (UWP) apps can use dynamic shader compilation, but it's faster to use dynamic shader linking.</span></span> <span data-ttu-id="7f38a-127">Sie können auch Compilerdirektiven und `#ifdef`-Blöcke verwenden, um unterschiedliche Versionen von Shadern zu laden.</span><span class="sxs-lookup"><span data-stu-id="7f38a-127">You can also use compiler directives and `#ifdef` blocks to create different versions of shaders.</span></span> <span data-ttu-id="7f38a-128">Dazu wird die VisualStudio-Projektdatei in einem Text-Editor geöffnet, und es werden mehrere `<FxcCompiler>`-Einträge für den HLSL-Code hinzugefügt (jeweils mit den passenden Präprozessordefinitionen).</span><span class="sxs-lookup"><span data-stu-id="7f38a-128">This is done by opening the Visual Studio project file in a text editor and adding multiple `<FxcCompiler>` entries for the HLSL (each with the appropriate preprocessor definitions).</span></span> <span data-ttu-id="7f38a-129">Beachten Sie, dass hierzu unterschiedliche Dateinamen erforderlich sind. In diesem Fall hängt Visual Studio an unterschiedliche Versionen des Shaders „\_point and \_linear“ an.</span><span class="sxs-lookup"><span data-stu-id="7f38a-129">Note that this necessitates different filenames; in this case, Visual Studio appends \_point and \_linear to the different versions of the shader.</span></span>

<span data-ttu-id="7f38a-130">Im Projektdateieintrag für die linear gefilterte Version des Shaders wird LINEAR definiert:</span><span class="sxs-lookup"><span data-stu-id="7f38a-130">The project file entry for the linear filtered version of the shader defines LINEAR:</span></span>

```xml
<FxCompile Include="Content\ShadowPixelShader.hlsl">
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|ARM'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|x64'">Pixel</ShaderType>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">false</DisableOptimizations>
  <EnableDebuggingInformation Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">true</EnableDebuggingInformation>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">false</DisableOptimizations>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">false</DisableOptimizations>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|ARM'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|x64'">$(OutDir)%(Filename)_linear.cso</ObjectFileOutput>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">LINEAR</PreprocessorDefinitions>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Release|ARM'">LINEAR</PreprocessorDefinitions>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">LINEAR</PreprocessorDefinitions>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">LINEAR</PreprocessorDefinitions>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">LINEAR</PreprocessorDefinitions>
  <PreprocessorDefinitions Condition="'$(Configuration)|$(Platform)'=='Release|x64'">LINEAR</PreprocessorDefinitions>
</FxCompile>
```

<span data-ttu-id="7f38a-131">Der Projektdateieintrag für die linear gefilterte Version des Shaders enthält keine Präprozessordefinitionen:</span><span class="sxs-lookup"><span data-stu-id="7f38a-131">The project file entry for the linear filtered version of the shader does not include preprocessor definitions:</span></span>

```xml
<FxCompile Include="Content\ShadowPixelShader.hlsl">
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|ARM'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">Pixel</ShaderType>
  <ShaderType Condition="'$(Configuration)|$(Platform)'=='Release|x64'">Pixel</ShaderType>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">false</DisableOptimizations>
  <EnableDebuggingInformation Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">true</EnableDebuggingInformation>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">false</DisableOptimizations>
  <DisableOptimizations Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">false</DisableOptimizations>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|ARM'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|ARM'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
  <ObjectFileOutput Condition="'$(Configuration)|$(Platform)'=='Release|x64'">$(OutDir)%(Filename)_point.cso</ObjectFileOutput>
</FxCompile>
```

 

 




