---
title: Ansichten
description: Der Begriff \ 0034;Ansicht \ 0034; wird für \ 0034;Daten im erforderlichen Format \ 0034; verwendet. Eine Konstantenpufferansicht (CBV) ist beispielweise ein Satz ordnungsgemäß formatierter, konstanter Pufferdaten. Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten.
ms.assetid: 0C7FB99F-7391-472F-BA53-576888DFC171
keywords:
- Ansichten
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 77ac16c55bb4292ea7c5362d007ff9569812954f
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6461277"
---
# <a name="views"></a><span data-ttu-id="66a72-106">Ansichten</span><span class="sxs-lookup"><span data-stu-id="66a72-106">Views</span></span>


<span data-ttu-id="66a72-107">Der Begriff „Ansicht“ wird für „Daten im erforderlichen Format“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="66a72-107">The term "view" is used to mean "data in the required format".</span></span> <span data-ttu-id="66a72-108">Eine Konstantenpufferansicht (CBV) ist beispielweise ein Satz ordnungsgemäß formatierter, konstanter Pufferdaten.</span><span class="sxs-lookup"><span data-stu-id="66a72-108">For example, a Constant Buffer View (CBV) would be constant buffer data correctly formatted.</span></span> <span data-ttu-id="66a72-109">Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten.</span><span class="sxs-lookup"><span data-stu-id="66a72-109">This section describes the most common and useful views.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="66a72-110"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="66a72-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="66a72-111">Thema</span><span class="sxs-lookup"><span data-stu-id="66a72-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="66a72-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66a72-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="constant-buffer-view--cbv-.md"><span data-ttu-id="66a72-113">Konstantenpufferansicht (CBV)</span><span class="sxs-lookup"><span data-stu-id="66a72-113">Constant buffer view (CBV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-114">Konstantenpuffer enthalten Konstantendaten für Shader.</span><span class="sxs-lookup"><span data-stu-id="66a72-114">Constant buffers contain shader constant data.</span></span> <span data-ttu-id="66a72-115">Ihr Nutzen besteht darin, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.</span><span class="sxs-lookup"><span data-stu-id="66a72-115">The value of them is that the data persists, and can be accessed by any GPU shader, until it is necessary to change the data.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="vertex-buffer-view--vbv-.md"><span data-ttu-id="66a72-116">Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)</span><span class="sxs-lookup"><span data-stu-id="66a72-116">Vertex buffer view (VBV) and Index buffer view (IBV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-117">Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.</span><span class="sxs-lookup"><span data-stu-id="66a72-117">A vertex buffer holds data for a list of vertices.</span></span> <span data-ttu-id="66a72-118">Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten.</span><span class="sxs-lookup"><span data-stu-id="66a72-118">The data for each vertex can include position, color, normal vector, texture co-ordinates, and so on.</span></span> <span data-ttu-id="66a72-119">Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.</span><span class="sxs-lookup"><span data-stu-id="66a72-119">An index buffer holds integer indexes (offsets) into a vertex buffer, and is used to define and render an object made up of a subset of the full list of vertices.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="shader-resource-view--srv-.md"><span data-ttu-id="66a72-120">Shaderressourcenansicht (SRV) und Unsortierte Zugriffsansicht (UAV)</span><span class="sxs-lookup"><span data-stu-id="66a72-120">Shader resource view (SRV) and Unordered Access view (UAV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-121">Shaderressourcenansichten verpacken Texturen in der Regel in einem Format, sodass die Shader darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="66a72-121">Shader resource views typically wrap textures in a format that the shaders can access them.</span></span> <span data-ttu-id="66a72-122">Eine unsortierte Zugriffsansicht bietet ähnliche Funktionen, ermöglicht aber das Lesen und Schreiben der Textur (oder einer anderen Ressource) in beliebiger Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="66a72-122">An unordered access view provides similar functionality, but enables the reading and writing to the texture (or other resource) in any order.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="sampler.md"><span data-ttu-id="66a72-123">Sampler</span><span class="sxs-lookup"><span data-stu-id="66a72-123">Sampler</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-124">Mit dem Begriff „Sampling“ wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="66a72-124">Sampling is the process of reading input values from a texture, or other resource.</span></span> <span data-ttu-id="66a72-125">Ein &quot;Sampler&quot; ist ein beliebiges Objekt, das aus Ressourcen liest.</span><span class="sxs-lookup"><span data-stu-id="66a72-125">A &quot;sampler&quot; is any object that reads from resources.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="render-target-view--rtv-.md"><span data-ttu-id="66a72-126">Renderzielansicht (RTV)</span><span class="sxs-lookup"><span data-stu-id="66a72-126">Render target view (RTV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-127">Renderziele ermöglichen das Rendern einer Szene, die auf dem Bildschirm gerendert werden soll, in einem temporären Zwischenpuffer statt im Hintergrundpuffer.</span><span class="sxs-lookup"><span data-stu-id="66a72-127">Render targets enable a scene to be rendered to a temporary intermediate buffer, rather than to the back buffer to be rendered to the screen.</span></span> <span data-ttu-id="66a72-128">Dieses Feature ermöglicht die Verwendung der komplexen Szene, die z.B. als eine Spiegelungstextur oder für andere Zwecke in der Grafikpipeline, oder vielleicht zum Hinzufügen von Pixelshader-Effekten zu der Szene vor dem Rendern gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="66a72-128">This feature enables use of the complex scene that might be rendered, perhaps as a reflection texture or other purpose within the graphics pipeline, or perhaps to add additional pixel shader effects to the scene before rendering.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="depth-stencil-view--dsv-.md"><span data-ttu-id="66a72-129">Tiefenschablonenansicht (Depth Stencil View, DSV)</span><span class="sxs-lookup"><span data-stu-id="66a72-129">Depth stencil view (DSV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-130">Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.</span><span class="sxs-lookup"><span data-stu-id="66a72-130">A depth stencil view provides the format and buffer for holding depth and stencil information.</span></span> <span data-ttu-id="66a72-131">Der Tiefenpuffer dient dazu, das Zeichnen von Pixeln zu vermeiden, die von einem näher liegenden Objekt verdeckt werden und so für den Betrachter nicht sichtbar wären.</span><span class="sxs-lookup"><span data-stu-id="66a72-131">The depth buffer is used to cull the drawing of pixels that would be invisible to the viewer as they are occluded from view by a closer object.</span></span> <span data-ttu-id="66a72-132">Der Schablonenpuffer kann zur Aussortierung aller Zeichnungsaktivitäten außerhalb einer definierten Form genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="66a72-132">The stencil buffer can be used to cull all drawing outside of a defined shape.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="stream-output-view--sov-.md"><span data-ttu-id="66a72-133">Streamausgabeansicht (SOV)</span><span class="sxs-lookup"><span data-stu-id="66a72-133">Stream output view (SOV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-134">Streamausgabeansichten ermöglichen, dass die Scheitelpunktinformationen von den Scheitelpunkt-, Mosaik- und Geometrie-Shadern zur weiteren Verwendung zurück in die Anwendung gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="66a72-134">Stream output views enable the vertex information that the vertex, tessellation and geometry shaders have come up with to be streamed back out to the application for further use.</span></span> <span data-ttu-id="66a72-135">Zum Beispiel könnte ein Objekt, das durch diese Shader verzerrt wurde, in die Anwendung zurückgeschrieben werden, um eine genauere Eingabe für eine Physik- oder eine andere Engine bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="66a72-135">For example, an object that has been distorted by these shaders could be written back to the application to provide more accurate input to a physics or other engine.</span></span> <span data-ttu-id="66a72-136">In der Praxis sind aber Streamausgabeansichten ein selten verwendetes Feature der Grafikpipeline.</span><span class="sxs-lookup"><span data-stu-id="66a72-136">In practice though, stream output views are an infrequently used feature of the graphics pipeline.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="rasterizer-ordered-view--rov-.md"><span data-ttu-id="66a72-137">Rasterizergesteuerte Ansicht (ROV)</span><span class="sxs-lookup"><span data-stu-id="66a72-137">Rasterizer ordered view (ROV)</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="66a72-138">Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.</span><span class="sxs-lookup"><span data-stu-id="66a72-138">Rasterizer ordered views enable some of the limitations of a depth buffer to be addressed, in particular having multiple textures containing transparency all applying to the same pixels.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="66a72-139"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="66a72-139"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="66a72-140">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="66a72-140">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




