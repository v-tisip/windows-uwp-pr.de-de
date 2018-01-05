---
title: Pipelinezugriff auf Streamingressourcen
description: "Streamingressourcen können in Shaderressourcenansichten (SRV), Renderzielansichten (RTV), Tiefenschablonenansichten (DSV) und in unsortierten Zugriffsansichten (UAV) sowie in bestimmten Bindungen ohne Ansichten, z.B. Vertex-Pufferbindungen, verwendet werden."
ms.assetid: 18DA5D61-930D-4466-8EFE-0CED566EA4A6
keywords: Pipelinezugriff auf Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 2eabbe1b5b7ffc848243f75237e90bc69d8a43dc
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="pipeline-access-to-streaming-resources"></a><span data-ttu-id="e3db4-104">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e3db4-104">Pipeline access to streaming resources</span></span>


<span data-ttu-id="e3db4-105">Streamingressourcen können in Shaderressourcenansichten (SRV), Renderzielansichten (RTV), Tiefenschablonenansichten (DSV) und in unsortierten Zugriffsansichten (UAV) sowie in bestimmten Bindungen ohne Ansichten, z.B. Vertex-Pufferbindungen, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3db4-105">Streaming resources can be used in shader resource views (SRV), render target views (RTV), depth stencil views (DSV) and unordered access views (UAV), as well as some bind points where views aren't used, such as vertex buffer bindings.</span></span> <span data-ttu-id="e3db4-106">Die Liste der unterstützten Bindungen finden Sie unter [Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e3db4-106">For the list of supported bindings, see [Streaming resource creation parameters](streaming-resource-creation-parameters.md).</span></span> <span data-ttu-id="e3db4-107">Die verschiedenen D3D-Kopiervorgänge funktionieren ebenfalls bei Streamingressourcen.</span><span class="sxs-lookup"><span data-stu-id="e3db4-107">The various D3D Copy operations also work on streaming resources.</span></span>

<span data-ttu-id="e3db4-108">Wenn mehrere Kachelkoordinaten in eine oder mehreren Ansichten an dieselbe Speicheradresse gebunden ist, finden Lese- und Schreibvorgänge aus unterschiedlichen Pfaden in einer nicht deterministischen und nicht wiederholbaren Speicherzugriff-Reihenfolge statt.</span><span class="sxs-lookup"><span data-stu-id="e3db4-108">If multiple tile coordinates in one or more views is bound to the same memory location, reads and writes from different paths to the same memory will occur in a non-deterministic and non-repeatable order of memory accesses.</span></span>

<span data-ttu-id="e3db4-109">Wenn alle Kacheln hinter einem Speicherzugriffsbedarf von einem Shader eindeutigen Kacheln zugeordnet sind, entspricht das Verhalten für alle Implementierungen der Oberfläche dem Verhalten gleicher Speicherinhalte ohne Kacheln.</span><span class="sxs-lookup"><span data-stu-id="e3db4-109">If all tiles behind a memory access footprint from a shader are mapped to unique tiles, behavior is identical on all implementations to the surface having the same memory contents in a non-tiled fashion.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="e3db4-110"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="e3db4-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e3db4-111">Thema</span><span class="sxs-lookup"><span data-stu-id="e3db4-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="e3db4-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3db4-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="e3db4-113">SRV-verhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="e3db4-113">SRV behavior with non-mapped tiles</span></span>](srv-behavior-with-non-mapped-tiles.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-114">Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="e3db4-114">Behavior of shader resource view (SRV) reads that involve non-mapped tiles depends on the level of hardware support.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="e3db4-115">UAV-verhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="e3db4-115">UAV behavior with non-mapped tiles</span></span>](uav-behavior-with-non-mapped-tiles.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-116">Das Verhalten der Lese- und Schreibvorgänge der unsortierten Zugriffsansicht (UAV) hängt von der Ebene der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="e3db4-116">Behavior of unordered access view (UAV) reads and writes depends on the level of hardware support.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="e3db4-117">Rasterizerverhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="e3db4-117">Rasterizer behavior with non-mapped tiles</span></span>](rasterizer-behavior-with-non-mapped-tiles.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-118">Dieser Abschnittbeschreibt Rasterizerverhalten bei nicht zugeordneten Kacheln.</span><span class="sxs-lookup"><span data-stu-id="e3db4-118">This section describes rasterizer behavior with non-mapped tiles.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="e3db4-119">Kachelzugriffseinschränkungen bei doppelten Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="e3db4-119">Tile access limitations with duplicate mappings</span></span>](tile-access-limitations-with-duplicate-mappings.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-120">Bei doppelten Zuordnungen gibt es Kachelzugriffseinschränkungen, wie z.B. beim Kopieren von Streamingressourcen mit Quellen- und Zielüberlappung oder beim Rendern von Kacheln innerhalb des Bereichs Rendern freigegeben.</span><span class="sxs-lookup"><span data-stu-id="e3db4-120">There are limitations on tile access with duplicate mappings, such as when copying streaming resources with overlapping source and destination, or when rendering to tiles shared within the render area.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="e3db4-121">Textursampling-Features für Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e3db4-121">Streaming resources texture sampling features</span></span>](streaming-resources-texture-sampling-features.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-122">Textursampling-Features für Streamingressourcen enthalten: Abrufen von Feedback zum Shaderstatus zugeordneter Bereiche, Überprüfen, ob alle Daten, auf die zugegriffen wird, in der Ressource zugeordnet wurden, Klammerung, damit Shader Bereiche in Mipmap-Streamingressourcen vermeiden, die nicht zugeordnet wurden, und Ermitteln der minimalen Detailtiefe (Level-of-Detail, LOD), die für den gesamten Speicherbedarf einer Texturfilterung vollständig zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e3db4-122">Streaming resources texture sampling features include getting shader status feedback about mapped areas, checking whether all data being accessed was mapped in the resource, clamping to help shaders avoid areas in mipmapped streaming resources that are known to be non-mapped, and discovering what the minimum LOD that is fully mapped for an entire texture filter footprint will be.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="e3db4-123">Belichtung von HLSL-Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e3db4-123">HLSL streaming resources exposure</span></span>](hlsl-streaming-resources-exposure.md)</p></td>
<td align="left"><p><span data-ttu-id="e3db4-124">Eine spezielle Syntax für die Microsoft High LevelShader Language (HLSL) ist für die Unterstützung von Streaming Ressourcen in [Shadermodell 5](https://msdn.microsoft.com/library/windows/desktop/ff471356) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e3db4-124">A specific Microsoft High Level Shader Language (HLSL) syntax is required to support streaming resources in [Shader Model 5](https://msdn.microsoft.com/library/windows/desktop/ff471356).</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e3db4-125"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e3db4-125"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e3db4-126">Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e3db4-126">Streaming resources</span></span>](streaming-resources.md)

 

 




