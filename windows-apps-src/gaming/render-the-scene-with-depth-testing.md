---
author: mtoepke
title: Rendern der Szene mit Tiefentest
description: Erstellen Sie einen Schatteneffekt, indem Sie Ihrem Vertexshader (bzw. Geometrieshader) und dem Pixelshader einen Tiefentest hinzufügen.
ms.assetid: bf496dfb-d7f5-af6b-d588-501164608560
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Rendern, Szene, Tiefentest, Direct3D, Schatten
ms.localizationpriority: medium
ms.openlocfilehash: dc776a60e771cc8d5961e8c7b9c67eb99fabea3a
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6266845"
---
# <a name="render-the-scene-with-depth-testing"></a><span data-ttu-id="2bc21-104">Rendern der Szene mit Tiefentest</span><span class="sxs-lookup"><span data-stu-id="2bc21-104">Render the scene with depth testing</span></span>




<span data-ttu-id="2bc21-105">Erstellen Sie einen Schatteneffekt, indem Sie dem Vertex-Shader (bzw. Geometry-Shader) und dem Pixel-Shader einen Tiefentest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-105">Create a shadow effect by adding depth testing to your vertex (or geometry) shader and your pixel shader.</span></span> <span data-ttu-id="2bc21-106">Teil3 von [Exemplarische Vorgehensweise: Implementieren von Schattenvolumes mithilfe von Tiefenpuffern in Direct3D11](implementing-depth-buffers-for-shadow-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="2bc21-106">Part 3 of [Walkthrough: Implement shadow volumes using depth buffers in Direct3D 11](implementing-depth-buffers-for-shadow-mapping.md).</span></span>

## <a name="include-transformation-for-light-frustum"></a><span data-ttu-id="2bc21-107">Einfügen der Transformation für Licht-Frustum</span><span class="sxs-lookup"><span data-stu-id="2bc21-107">Include transformation for light frustum</span></span>


<span data-ttu-id="2bc21-108">Ihr Vertex-Shader muss für jeden Scheitelpunkt (Vertex) die transformierte Position im Lichtraum berechnen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-108">Your vertex shader needs to compute the transformed light space position for each vertex.</span></span> <span data-ttu-id="2bc21-109">Geben Sie die Modell-, Ansichts- und Projektionsmatrizen für den Lichtraum mithilfe eines Konstantenpuffers an.</span><span class="sxs-lookup"><span data-stu-id="2bc21-109">Provide the light space model, view, and projection matrices using a constant buffer.</span></span> <span data-ttu-id="2bc21-110">Sie können diesen Konstantenpuffer auch verwenden, um die Lichtposition und Normale für Lichtberechnungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-110">You can also use this constant buffer to provide the light position and normal for lighting calculations.</span></span> <span data-ttu-id="2bc21-111">Die transformierte Position im Lichtraum wird während des Tiefentests verwendet.</span><span class="sxs-lookup"><span data-stu-id="2bc21-111">The transformed position in light space will be used during the depth test.</span></span>

```cpp
PixelShaderInput main(VertexShaderInput input)
{
    PixelShaderInput output;
    float4 pos = float4(input.pos, 1.0f);

    // Transform the vertex position into projected space.
    float4 modelPos = mul(pos, model);
    pos = mul(modelPos, view);
    pos = mul(pos, projection);
    output.pos = pos;

    // Transform the vertex position into projected space from the POV of the light.
    float4 lightSpacePos = mul(modelPos, lView);
    lightSpacePos = mul(lightSpacePos, lProjection);
    output.lightSpacePos = lightSpacePos;

    // Light ray
    float3 lRay = lPos.xyz - modelPos.xyz;
    output.lRay = lRay;
    
    // Camera ray
    output.view = eyePos.xyz - modelPos.xyz;

    // Transform the vertex normal into world space.
    float4 norm = float4(input.norm, 1.0f);
    norm = mul(norm, model);
    output.norm = norm.xyz;
    
    // Pass through the color and texture coordinates without modification.
    output.color = input.color;
    output.tex = input.tex;

    return output;
}
```

<span data-ttu-id="2bc21-112">Als Nächstes wird vom Pixelshader die vom Vertex-Shader bereitgestellte interpolierte Lichtraumposition verwendet, um zu testen, ob das Pixel im Schatten liegt.</span><span class="sxs-lookup"><span data-stu-id="2bc21-112">Next, the pixel shader will use the interpolated light space position provided by the vertex shader to test whether the pixel is in shadow.</span></span>

## <a name="test-whether-the-position-is-in-the-light-frustum"></a><span data-ttu-id="2bc21-113">Testen, ob sich die Position im Licht-Frustum befindet</span><span class="sxs-lookup"><span data-stu-id="2bc21-113">Test whether the position is in the light frustum</span></span>


<span data-ttu-id="2bc21-114">Prüfen Sie zuerst, ob sich das Pixel im Ansichts-Frustum des Lichts befindet, indem Sie die X- und Y-Koordinaten normalisieren.</span><span class="sxs-lookup"><span data-stu-id="2bc21-114">First, check that the pixel is in the view frustum of the light by normalizing the X and Y coordinates.</span></span> <span data-ttu-id="2bc21-115">Wenn diese beide innerhalb des Bereichs \[0, 1\] liegen, ist es möglich, dass das Pixel im Schatten liegt.</span><span class="sxs-lookup"><span data-stu-id="2bc21-115">If they are both within the range \[0, 1\] then it's possible for the pixel to be in shadow.</span></span> <span data-ttu-id="2bc21-116">Andernfalls können Sie den Tiefentest überspringen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-116">Otherwise you can skip the depth test.</span></span> <span data-ttu-id="2bc21-117">Mit einem Shader kann dies ohne viel Zeitaufwand getestet werden, indem [Saturate](https://msdn.microsoft.com/library/windows/desktop/hh447231) aufgerufen und das Ergebnis mit dem Originalwert verglichen wird.</span><span class="sxs-lookup"><span data-stu-id="2bc21-117">A shader can test for this quickly by calling [Saturate](https://msdn.microsoft.com/library/windows/desktop/hh447231) and comparing the result against the original value.</span></span>

```cpp
// Compute texture coordinates for the current point's location on the shadow map.
float2 shadowTexCoords;
shadowTexCoords.x = 0.5f + (input.lightSpacePos.x / input.lightSpacePos.w * 0.5f);
shadowTexCoords.y = 0.5f - (input.lightSpacePos.y / input.lightSpacePos.w * 0.5f);
float pixelDepth = input.lightSpacePos.z / input.lightSpacePos.w;

float lighting = 1;

// Check if the pixel texture coordinate is in the view frustum of the 
// light before doing any shadow work.
if ((saturate(shadowTexCoords.x) == shadowTexCoords.x) &&
    (saturate(shadowTexCoords.y) == shadowTexCoords.y) &&
    (pixelDepth > 0))
{
```

## <a name="depth-test-against-the-shadow-map"></a><span data-ttu-id="2bc21-118">Tiefentest unter Verwendung der Schattenmap</span><span class="sxs-lookup"><span data-stu-id="2bc21-118">Depth test against the shadow map</span></span>


<span data-ttu-id="2bc21-119">Verwenden Sie eine Samplevergleichsfunktion (entweder [SampleCmp](https://msdn.microsoft.com/library/windows/desktop/bb509696) oder [SampleCmpLevelZero](https://msdn.microsoft.com/library/windows/desktop/bb509697)), um die Tiefe des Pixels im Lichtraum unter Verwendung der Tiefenmap zu testen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-119">Use a sample comparison function (either [SampleCmp](https://msdn.microsoft.com/library/windows/desktop/bb509696) or [SampleCmpLevelZero](https://msdn.microsoft.com/library/windows/desktop/bb509697)) to test the pixel's depth in light space against the depth map.</span></span> <span data-ttu-id="2bc21-120">Berechnen Sie den normalisierten Lichtraum-Tiefenwert, für den `z / w` gilt, und übergeben Sie den Wert an die Vergleichsfunktion.</span><span class="sxs-lookup"><span data-stu-id="2bc21-120">Compute the normalized light space depth value, which is `z / w`, and pass the value to the comparison function.</span></span> <span data-ttu-id="2bc21-121">Da wir für den Sampler einen LessOrEqual-Vergleichstest verwenden, wird von der systeminternen Funktion null zurückgegeben, wenn der Vergleichstest bestanden wurde; dies gibt an, dass das Pixel im Schatten liegt.</span><span class="sxs-lookup"><span data-stu-id="2bc21-121">Since we use a LessOrEqual comparison test for the sampler, the intrinsic function returns zero when the comparison test passes; this indicates that the pixel is in shadow.</span></span>

```cpp
// Use an offset value to mitigate shadow artifacts due to imprecise 
// floating-point values (shadow acne).
//
// This is an approximation of epsilon * tan(acos(saturate(NdotL))):
float margin = acos(saturate(NdotL));
#ifdef LINEAR
// The offset can be slightly smaller with smoother shadow edges.
float epsilon = 0.0005 / margin;
#else
float epsilon = 0.001 / margin;
#endif
// Clamp epsilon to a fixed range so it doesn't go overboard.
epsilon = clamp(epsilon, 0, 0.1);

// Use the SampleCmpLevelZero Texture2D method (or SampleCmp) to sample from 
// the shadow map, just as you would with Direct3D feature level 10_0 and
// higher.  Feature level 9_1 only supports LessOrEqual, which returns 0 if
// the pixel is in the shadow.
lighting = float(shadowMap.SampleCmpLevelZero(
    shadowSampler,
    shadowTexCoords,
    pixelDepth + epsilon
    )
    );
```

## <a name="compute-lighting-in-or-out-of-shadow"></a><span data-ttu-id="2bc21-122">Berechnen der Beleuchtung innerhalb und außerhalb des Schattens</span><span class="sxs-lookup"><span data-stu-id="2bc21-122">Compute lighting in or out of shadow</span></span>


<span data-ttu-id="2bc21-123">Wenn das Pixel nicht im Schatten liegt, kann der Pixelshader die direkte Beleuchtung berechnen und dem Pixelwert hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-123">If the pixel is not in shadow, the pixel shader should compute direct lighting and add it to the pixel value.</span></span>

```cpp
return float4(input.color * (ambient + DplusS(N, L, NdotL, input.view)), 1.f);
```

```cpp
float3 DplusS(float3 N, float3 L, float NdotL, float3 view)
{
    const float3 Kdiffuse = float3(.5f, .5f, .4f);
    const float3 Kspecular = float3(.2f, .2f, .3f);
    const float exponent = 3.f;

    // Compute the diffuse coefficient.
    float diffuseConst = saturate(NdotL);

    // Compute the diffuse lighting value.
    float3 diffuse = Kdiffuse * diffuseConst;

    // Compute the specular highlight.
    float3 R = reflect(-L, N);
    float3 V = normalize(view);
    float3 RdotV = dot(R, V);
    float3 specular = Kspecular * pow(saturate(RdotV), exponent);

    return (diffuse + specular);
}
```

<span data-ttu-id="2bc21-124">Andernfalls sollte der Pixelshader den Pixelwert mithilfe des Umgebungslichts berechnen.</span><span class="sxs-lookup"><span data-stu-id="2bc21-124">Otherwise, the pixel shader should compute the pixel value using ambient lighting.</span></span>

```cpp
return float4(input.color * ambient, 1.f);
```

<span data-ttu-id="2bc21-125">Der nächste Teil dieser exemplarischen Vorgehensweise beschäftigt sich mit dem [Unterstützen von Schattenmaps für unterschiedliche Hardware](target-a-range-of-hardware.md).</span><span class="sxs-lookup"><span data-stu-id="2bc21-125">In the next part of this walkthrough, learn how to [Support shadow maps on a range of hardware](target-a-range-of-hardware.md).</span></span>

 

 




