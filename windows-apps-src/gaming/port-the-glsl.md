---
title: Portieren des GLSL-Codes
description: Nachdem Sie sich um den Code gekümmert haben, mit dem die Puffer und Shaderobjekte erstellt und konfiguriert werden, muss der in diesen Shadern enthaltene Code von der GL Shader Language (GLSL) von OpenGL ES 2.0 in die High-Level Shader Language (HLSL) von Direct3D 11 portiert werden.
ms.assetid: 0de06c51-8a34-dc68-6768-ea9f75dc57ee
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, GLSL, Portieren
ms.localizationpriority: medium
ms.openlocfilehash: 809440f9e77af19c01f4a050eee3b6f8d1c709b7
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8891652"
---
# <a name="port-the-glsl"></a><span data-ttu-id="f8ea1-104">Portieren der GLSL</span><span class="sxs-lookup"><span data-stu-id="f8ea1-104">Port the GLSL</span></span>




**<span data-ttu-id="f8ea1-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="f8ea1-105">Important APIs</span></span>**

-   [<span data-ttu-id="f8ea1-106">HLSL-Semantik</span><span class="sxs-lookup"><span data-stu-id="f8ea1-106">HLSL Semantics</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb205574)
-   [<span data-ttu-id="f8ea1-107">Shaderkonstanten (HLSL)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-107">Shader Constants (HLSL)</span></span>](https://msdn.microsoft.com/library/windows/desktop/bb509581)

<span data-ttu-id="f8ea1-108">Nachdem Sie sich um den Code gekümmert haben, mit dem die Puffer und Shaderobjekte erstellt und konfiguriert werden, muss der in diesen Shadern enthaltene Code von der GL Shader Language (GLSL) von OpenGL ES 2.0 in die High-Level Shader Language (HLSL) von Direct3D 11 portiert werden.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-108">Once you've moved over the code that creates and configures your buffers and shader objects, it's time to port the code inside those shaders from OpenGL ES 2.0's GL Shader Language (GLSL) to Direct3D 11's High-level Shader Language (HLSL).</span></span>

<span data-ttu-id="f8ea1-109">Unter OpenGL ES 2.0 geben Shader Daten nach der Ausführung zurück, indem systeminterne Elemente wie **gl\_Position**, **gl\_FragColor** oder **gl\_FragData\[n\]** verwendet werden (wobei „n“ der Index für ein bestimmtes Renderziel ist).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-109">In OpenGL ES 2.0, shaders return data after execution using intrinsics such as **gl\_Position**, **gl\_FragColor**, or **gl\_FragData\[n\]** (where n is the index for a specific render target).</span></span> <span data-ttu-id="f8ea1-110">In Direct3D sind keine speziellen systeminternen Funktionen vorhanden. Von den Shadern werden Daten als Rückgabetyp ihrer jeweiligen main()-Funktionen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-110">In Direct3D, there are no specific intrinsics, and the shaders return data as the return type of their respective main() functions.</span></span>

<span data-ttu-id="f8ea1-111">Daten, die zwischen Shaderphasen interpoliert werden sollen, z. B. Vertexposition oder Normale, werden mithilfe der **varying**-Deklaration behandelt.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-111">Data that you want interpolated between shader stages, such as the vertex position or normal, is handled through the use of the **varying** declaration.</span></span> <span data-ttu-id="f8ea1-112">Direct3D verfügt jedoch nicht über diese Deklaration. Alle Daten, die zwischen Shaderphasen übertragen werden sollen, müssen daher per [HLSL-Semantik](https://msdn.microsoft.com/library/windows/desktop/bb205574) markiert werden.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-112">However, Direct3D doesn't have this declaration; rather, any data that you want passed between shader stages must be marked with an [HLSL semantic](https://msdn.microsoft.com/library/windows/desktop/bb205574).</span></span> <span data-ttu-id="f8ea1-113">Mit der jeweils gewählten Semantik wird der Zweck für die Daten angegeben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-113">The specific semantic chosen indicates the purpose of the data, and is.</span></span> <span data-ttu-id="f8ea1-114">Vertexdaten, die zwischen Fragmentshadern interpoliert werden sollen, werden beispielsweise wie folgt deklariert:</span><span class="sxs-lookup"><span data-stu-id="f8ea1-114">For example, you'd declare vertex data that you want interpolated between the fragment shader as:</span></span>

`float4 vertPos : POSITION;`

<span data-ttu-id="f8ea1-115">oder</span><span class="sxs-lookup"><span data-stu-id="f8ea1-115">or</span></span>

`float4 vertColor : COLOR;`

<span data-ttu-id="f8ea1-116">POSITION steht hierbei für die Semantik, die zum Angeben der Vertexpositionsdaten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-116">Where POSITION is the semantic used to indicate vertex position data.</span></span> <span data-ttu-id="f8ea1-117">POSITION stellt außerdem einen Sonderfall dar, da vom Pixelshader nach der Interpolation darauf nicht zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-117">POSITION is also a special case, since after interpolation, it cannot be accessed by the pixel shader.</span></span> <span data-ttu-id="f8ea1-118">Daher müssen Sie Eingaben für den Pixelshader mithilfe von SV\_POSITION angeben. Die interpolierten Vertexdaten werden dann in diese Variable eingefügt.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-118">Therefore, you must specify input to the pixel shader with SV\_POSITION and the interpolated vertex data will be placed in that variable.</span></span>

`float4 position : SV_POSITION;`

<span data-ttu-id="f8ea1-119">Die Semantik kann für die body-Methoden (main) von Shadern deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-119">Semantics can be declared on the body (main) methods of shaders.</span></span> <span data-ttu-id="f8ea1-120">Für Pixelshader ist für die body-Methode SV\_TARGET\[n\] erforderlich. Damit wird ein Renderziel angegeben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-120">For pixel shaders, SV\_TARGET\[n\], which indicates a render target, is required on the body method.</span></span> <span data-ttu-id="f8ea1-121">(SV\_TARGET ohne numerisches Suffix ergibt standardmäßig den Renderzielindex 0.)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-121">(SV\_TARGET without a numeric suffix defaults to render target index 0.)</span></span>

<span data-ttu-id="f8ea1-122">Beachten Sie auch, dass Vertex-Shader erforderlich sind, um die SV\_POSITION-Systemwertsemantik auszugeben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-122">Also note that vertex shaders are required to output the SV\_POSITION system value semantic.</span></span> <span data-ttu-id="f8ea1-123">Mit dieser Semantik werden die Vertexpositionsdaten zu Koordinatenwerten aufgelöst, wobei "x" zwischen -1 und 1 und "y" zwischen -1 und 1 liegt. "z" wird durch den ursprünglichen homogenen Koordinatenwert "w" dividiert (z/w), und "w" ist 1 dividiert durch den Originalwert "w" (1/w).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-123">This semantic resolves the vertex position data to coordinate values where x is between -1 and 1, y is between -1 and 1, z is divided by the original homogeneous coordinate w value (z/w), and w is 1 divided by the original w value (1/w).</span></span> <span data-ttu-id="f8ea1-124">Für Pixelshader wird die SV\_POSITION-Systemwertsemantik zum Abrufen der Pixelposition auf dem Bildschirm verwendet, wobei "x" zwischen 0 und der Breite des Renderziels und "y" zwischen 0 und der Höhe des Renderziels liegt (jeweils um den Wert 0,5 versetzt).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-124">Pixel shaders use the SV\_POSITION system value semantic to retrieve the pixel location on the screen, where x is between 0 and the render target width and y is between 0 and the render target height (each offset by 0.5).</span></span> <span data-ttu-id="f8ea1-125">Pixelshader der Featureebene 9\_x können nicht aus dem SV\_POSITION-Wert auslesen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-125">Feature level 9\_x pixel shaders cannot read from the SV\_POSITION value.</span></span>

<span data-ttu-id="f8ea1-126">Konstantenpuffer müssen mit **cbuffer** deklariert und mit einem speziellen Startregister für die Suche versehen werden.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-126">Constant buffers must be declared with **cbuffer** and be associated with a specific starting register for lookup.</span></span>

<span data-ttu-id="f8ea1-127">Direct3D11: Deklaration eines HLSL-Konstantenpuffers</span><span class="sxs-lookup"><span data-stu-id="f8ea1-127">Direct3D 11: An HLSL constant buffer declaration</span></span>

``` syntax
cbuffer ModelViewProjectionConstantBuffer : register(b0)
{
  matrix mvp;
};
```

<span data-ttu-id="f8ea1-128">Hier wird vom Konstantenpuffer das Register „b0“ für den gepackten Puffer verwendet.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-128">Here, the constant buffer uses register b0 to hold the packed buffer.</span></span> <span data-ttu-id="f8ea1-129">In der Form "b\#" wird auf alle Register verwiesen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-129">All registers are referred to in the form b\#.</span></span> <span data-ttu-id="f8ea1-130">Weitere Informationen zur HLSL-Implementierung von Konstantenpuffern, Registern und Datenpaketen finden Sie unter [Shaderkonstanten (HLSL)](https://msdn.microsoft.com/library/windows/desktop/bb509581).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-130">For more information on the HLSL implementation of constant buffers, registers, and data packing, read [Shader Constants (HLSL)](https://msdn.microsoft.com/library/windows/desktop/bb509581).</span></span>

<a name="instructions"></a><span data-ttu-id="f8ea1-131">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="f8ea1-131">Instructions</span></span>
------------
### <a name="step-1-port-the-vertex-shader"></a><span data-ttu-id="f8ea1-132">Schritt 1: Portieren des Vertex-Shaders</span><span class="sxs-lookup"><span data-stu-id="f8ea1-132">Step 1: Port the vertex shader</span></span>

<span data-ttu-id="f8ea1-133">In diesem einfachen OpenGL ES 2.0-Beispiel verfügt der Vertex-Shader über drei Eingaben: eine konstante Modell-Ansicht-Projektion-4x4-Matrix und zwei Vektoren mit vier Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-133">In our simple OpenGL ES 2.0 example, the vertex shader has three inputs: a constant model-view-projection 4x4 matrix, and two 4-coordinate vectors.</span></span> <span data-ttu-id="f8ea1-134">Diese beiden Vektoren enthalten die Vertexposition und ihre Farbe.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-134">These two vectors contain the vertex position and its color.</span></span> <span data-ttu-id="f8ea1-135">Der Shader wandelt den Positionsvektor in Perspektivenkoordinaten um und weist ihn der systeminternen gl\_Position-Funktion zur Rasterung zu.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-135">The shader transforms the position vector to perspective coordinates and assigns it to the gl\_Position intrinsic for rasterization.</span></span> <span data-ttu-id="f8ea1-136">Außerdem wird die Vertexfarbe zur Interpolation während der Rasterung in eine abweichende Variable kopiert.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-136">The vertex color is copied to a varying variable for interpolation during rasterization, as well.</span></span>

<span data-ttu-id="f8ea1-137">OpenGLES2.0: Vertex-Shader für das Würfelobjekt (GLSL)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-137">OpenGL ES 2.0: Vertex shader for the cube object (GLSL)</span></span>

``` syntax
uniform mat4 u_mvpMatrix; 
attribute vec4 a_position;
attribute vec4 a_color;
varying vec4 destColor;

void main()
{           
  gl_Position = u_mvpMatrix * a_position;
  destColor = a_color;
}
```

<span data-ttu-id="f8ea1-138">In Direct3D ist die konstante Modell-Ansicht-Projektion-Matrix in einem Konstantenpuffer enthalten, der unter Registerb0 verpackt ist, und die Vertexposition und -farbe sind speziell mit der jeweils geeigneten HLSL-Semantik gekennzeichnet: POSITION und COLOR.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-138">Now, in Direct3D, the constant model-view-projection matrix is contained in a constant buffer packed at register b0, and the vertex position and color are specifically marked with the appropriate respective HLSL semantics: POSITION and COLOR.</span></span> <span data-ttu-id="f8ea1-139">Da das Eingabelayout eine bestimmte Anordnung dieser beiden Vertexwerte vorgibt, erstellen Sie dafür eine Struktur und deklarieren diese als Typ für den Eingabeparameter der body-Shaderfunktion (main).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-139">Since our input layout indicates a specific arrangement of these two vertex values, you create a struct to hold them and declare it as the type for the input parameter on the shader body function (main).</span></span> <span data-ttu-id="f8ea1-140">(Sie können die Werte auch als zwei einzelne Parameter angeben, was mitunter jedoch umständlich ist.) Außerdem geben Sie einen Ausgabetyp für diese Phase an, der die interpolierte Position und Farbe enthält, und deklarieren ihn als Rückgabewert für die body-Funktion des Vertex-Shaders.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-140">(You could also specify them as two individual parameters, but that could get cumbersome.) You also specify an output type for this stage, which contains the interpolated position and color, and declare it as the return value for the body function of the vertex shader.</span></span>

<span data-ttu-id="f8ea1-141">Direct3D11: Vertex-Shader für das Würfelobjekt (HLSL)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-141">Direct3D 11: Vertex shader for the cube object (HLSL)</span></span>

``` syntax
cbuffer ModelViewProjectionConstantBuffer : register(b0)
{
  matrix mvp;
};

// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
  float3 pos : POSITION;
  float3 color : COLOR;
};

// Per-vertex color data passed through the pixel shader.
struct PixelShaderInput
{
  float3 pos : SV_POSITION;
  float3 color : COLOR;
};

PixelShaderInput main(VertexShaderInput input)
{
  PixelShaderInput output;
  float4 pos = float4(input.pos, 1.0f); // add the w-coordinate

  pos = mul(mvp, projection);
  output.pos = pos;

  output.color = input.color;

  return output;
}
```

<span data-ttu-id="f8ea1-142">Der Ausgabedatentyp „PixelShaderInput“ wird während der Rasterung aufgefüllt und für den Fragmentshader (Pixelshader) bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-142">The output data type, PixelShaderInput, is populated during rasterization and provided to the fragment (pixel) shader.</span></span>

### <a name="step-2-port-the-fragment-shader"></a><span data-ttu-id="f8ea1-143">Schritt 2: Portieren des Fragmentshaders</span><span class="sxs-lookup"><span data-stu-id="f8ea1-143">Step 2: Port the fragment shader</span></span>

<span data-ttu-id="f8ea1-144">Der Fragmentshader in GLSL im Beispiel ist sehr einfach gestaltet: Der interpolierte Farbwert wird für die systeminterne gl\_FragColor-Funktion bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-144">Our example fragment shader in GLSL is extremely simple: provide the gl\_FragColor intrinsic with the interpolated color value.</span></span> <span data-ttu-id="f8ea1-145">Von OpenGL ES 2.0 wird er in das standardmäßige Renderziel geschrieben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-145">OpenGL ES 2.0 will write it to the default render target.</span></span>

<span data-ttu-id="f8ea1-146">OpenGLES2.0: Fragmentshader für das Würfelobjekt (GLSL)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-146">OpenGL ES 2.0: Fragment shader for the cube object (GLSL)</span></span>

``` syntax
varying vec4 destColor;

void main()
{
  gl_FragColor = destColor;
} 
```

<span data-ttu-id="f8ea1-147">Für Direct3D ist der Aufbau nahezu genauso einfach.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-147">Direct3D is almost as simple.</span></span> <span data-ttu-id="f8ea1-148">Der einzige zu beachtende Unterschied besteht darin, dass die body-Funktion des Pixelshaders einen Wert zurückgeben muss.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-148">The only significant difference is that the body function of the pixel shader must return a value.</span></span> <span data-ttu-id="f8ea1-149">Da es sich bei der Farbe um einen Gleitkommawert mit vier Koordinaten (RGBA) handelt, geben Sie float4 als Rückgabetyp an. Geben Sie anschließend das standardmäßige Renderziel als SV\_TARGET-Systemwertsemantik an.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-149">Since the color is a 4-coordinate (RGBA) float value, you indicate float4 as the return type, and then specify the default render target as the SV\_TARGET system value semantic.</span></span>

<span data-ttu-id="f8ea1-150">Direct3D 11: Pixelshader für das Würfelobjekt (HLSL)</span><span class="sxs-lookup"><span data-stu-id="f8ea1-150">Direct3D 11: Pixel shader for the cube object (HLSL)</span></span>

``` syntax
struct PixelShaderInput
{
  float4 pos : SV_POSITION;
  float3 color : COLOR;
};


float4 main(PixelShaderInput input) : SV_TARGET
{
  return float4(input.color, 1.0f);
}
```

<span data-ttu-id="f8ea1-151">Die Farbe für das Pixel an der Position wird in das Renderziel geschrieben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-151">The color for the pixel at the position is written to the render target.</span></span> <span data-ttu-id="f8ea1-152">Das Anzeigen der Inhalte dieses Renderziels als nächster Schritt wird unter [Zeichnen auf den Bildschirm](draw-to-the-screen.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-152">Now, let's see how to display the contents of that render target in [Draw to the screen](draw-to-the-screen.md)!</span></span>

## <a name="previous-step"></a><span data-ttu-id="f8ea1-153">Vorheriger Schritt</span><span class="sxs-lookup"><span data-stu-id="f8ea1-153">Previous step</span></span>


<span data-ttu-id="f8ea1-154">[Portieren der Vertexpuffer und -daten](port-the-vertex-buffers-and-data-config.md) Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="f8ea1-154">[Port the vertex buffers and data](port-the-vertex-buffers-and-data-config.md) Next step</span></span>
---------
<span data-ttu-id="f8ea1-155">[Zeichnen auf den Bildschirm](draw-to-the-screen.md) Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="f8ea1-155">[Draw to the screen](draw-to-the-screen.md) Remarks</span></span>
-------
<span data-ttu-id="f8ea1-156">Wenn Sie mit der HLSL-Semantik und dem Packen von Konstantenpuffern vertraut sind, können Sie einigen Debugaufwand vermeiden und Möglichkeiten zur Optimierung schaffen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-156">Understanding HLSL semantics and the packing of constant buffers can save you a bit of a debugging headache, as well as provide optimization opportunities.</span></span> <span data-ttu-id="f8ea1-157">Lesen Sie sich nach Möglichkeit die Themen [Variablensyntax (HLSL)](https://msdn.microsoft.com/library/windows/desktop/bb509706), [Einführung in Puffer in Direct3D11](https://msdn.microsoft.com/library/windows/desktop/ff476898) und [Erstellen eines Konstantenpuffers](https://msdn.microsoft.com/library/windows/desktop/ff476896) durch.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-157">If you get a chance, read through [Variable Syntax (HLSL)](https://msdn.microsoft.com/library/windows/desktop/bb509706), [Introduction to Buffers in Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476898), and [How to: Create a Constant Buffer](https://msdn.microsoft.com/library/windows/desktop/ff476896).</span></span> <span data-ttu-id="f8ea1-158">Hier sind als Anfang schon einmal einige Tipps aufgeführt, die in Verbindung mit der Semantik und Konstantenpuffern zu beachten sind:</span><span class="sxs-lookup"><span data-stu-id="f8ea1-158">If not, though, here's a few starting tips to keep in mind about semantics and constant buffers:</span></span>

-   <span data-ttu-id="f8ea1-159">Überprüfen Sie stets den Direct3D-Konfigurationscode des Renderers, um sicherzustellen, dass die Strukturen für die Konstantenpuffer mit den cbuffer-Strukturdeklarationen der HLSL übereinstimmen und dass die Komponentenskalartypen für beide Deklarationen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-159">Always double check your renderer's Direct3D configuration code to make sure that the structures for your constant buffers match the cbuffer struct declarations in your HLSL, and that the component scalar types match across both declarations.</span></span>
-   <span data-ttu-id="f8ea1-160">Verwenden Sie im C++-Code des Renderers [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833)-Typen in den Konstantenpufferdeklarationen, um für die richtige Verpackung der Daten zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-160">In your renderer's C++ code, use [DirectXMath](https://msdn.microsoft.com/library/windows/desktop/hh437833) types in your constant buffer declarations to ensure proper data packing.</span></span>
-   <span data-ttu-id="f8ea1-161">Die beste Möglichkeit zur effizienten Nutzung von Konstantenpuffern ist die Organisation von Shadervariablen in Konstantenpuffern anhand der Updatehäufigkeit.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-161">The best way to efficiently use constant buffers is to organize shader variables into constant buffers based on their frequency of update.</span></span> <span data-ttu-id="f8ea1-162">Wenn Sie beispielsweise über uniform-Daten verfügen, die einmal pro Frame aktualisiert werden, sowie über andere uniform-Daten, die nur bei Kamerabewegungen aktualisiert werden, empfiehlt sich das Aufteilen der Daten auf zwei separate Konstantenpuffer.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-162">For example, if you have some uniform data that is updated once per frame, and other uniform data that is updated only when the camera moves, consider separating that data into two separate constant buffers.</span></span>
-   <span data-ttu-id="f8ea1-163">Semantik, deren Anwendung Sie vergessen oder die Sie auf fehlerhafte Weise angewendet haben, ist die wichtigste Ursache für Fehler der Shaderkompilierung (FXC).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-163">Semantics that you have forgotten to apply or which you have applied incorrectly will be your earliest source of shader compilation (FXC) errors.</span></span> <span data-ttu-id="f8ea1-164">Deshalb sollten Sie die Semantik auf jeden Fall noch einmal überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-164">Double-check them!</span></span> <span data-ttu-id="f8ea1-165">Die Dokumente können etwas verwirrend erscheinen, da viele ältere Seiten und Beispiele noch auf andere Versionen der HLSL-Semantik des Stands vor Direct3D11 verweisen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-165">The docs can be a bit confusing, as many older pages and samples refer to different versions of HLSL semantics prior to Direct3D 11.</span></span>
-   <span data-ttu-id="f8ea1-166">Stellen Sie sicher, dass Sie wissen, auf welche Direct3D-Featureebene Sie für einen Shader jeweils abzielen.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-166">Make sure you know which Direct3D feature level you are targeting for each shader.</span></span> <span data-ttu-id="f8ea1-167">Die Semantik für Featureebene "9\_\*" unterscheidet sich von der Semantik für 11\_1.</span><span class="sxs-lookup"><span data-stu-id="f8ea1-167">The semantics for feature level 9\_\* are different from those for 11\_1.</span></span>
-   <span data-ttu-id="f8ea1-168">Mit der SV\_POSITION-Semantik werden die zugeordneten Daten für die Position nach der Interpolation zu Koordinatenwerten aufgelöst, wobei „x“ zwischen 0 und der Breite des Renderziels und „y“ zwischen 0 und der Höhe des Renderziels liegt. „z“ wird durch den ursprünglichen homogenen Koordinatenwert „w“ dividiert (z/w). „w“ ist 1 dividiert durch den Originalwert „w“ (1/w).</span><span class="sxs-lookup"><span data-stu-id="f8ea1-168">The SV\_POSITION semantic resolves the associated post-interpolation position data to coordinate values where x is between 0 and the render target width, y is between 0 and the render target height, z is divided by the original homogeneous coordinate w value (z/w), and w is 1 divided by the original w value (1/w).</span></span>

## <a name="related-topics"></a><span data-ttu-id="f8ea1-169">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f8ea1-169">Related topics</span></span>


[<span data-ttu-id="f8ea1-170">Portieren eines einfachen OpenGL ES 2.0-Renderers zu Direct3D 11</span><span class="sxs-lookup"><span data-stu-id="f8ea1-170">How to: port a simple OpenGL ES 2.0 renderer to Direct3D 11</span></span>](port-a-simple-opengl-es-2-0-renderer-to-directx-11-1.md)

[<span data-ttu-id="f8ea1-171">Portieren der Shaderobjekte</span><span class="sxs-lookup"><span data-stu-id="f8ea1-171">Port the shader objects</span></span>](port-the-shader-config.md)

[<span data-ttu-id="f8ea1-172">Portieren der Vertexpuffer und Daten</span><span class="sxs-lookup"><span data-stu-id="f8ea1-172">Port the vertex buffers and data</span></span>](port-the-vertex-buffers-and-data-config.md)

[<span data-ttu-id="f8ea1-173">Zeichnen auf den Bildschirm</span><span class="sxs-lookup"><span data-stu-id="f8ea1-173">Draw to the screen</span></span>](draw-to-the-screen.md)

 

 




