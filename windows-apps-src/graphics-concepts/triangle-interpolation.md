---
title: Dreiecksinterpolation
description: Während des Renderns interpoliert die Pipeline Scheitelpunktdaten über jedes Dreieck hinweg.
ms.assetid: 1A76DD78-CED7-42BE-BA81-B9050CD3AF9B
keywords:
- Dreiecksinterpolation
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 56ce3520248a0fca25230d7ee2a822d827d842a3
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7145481"
---
# <a name="triangle-interpolation"></a><span data-ttu-id="56a1e-104">Dreiecksinterpolation</span><span class="sxs-lookup"><span data-stu-id="56a1e-104">Triangle interpolation</span></span>


<span data-ttu-id="56a1e-105">Während des Renderns interpoliert die Pipeline Vertexdaten bei jedem Dreieck.</span><span class="sxs-lookup"><span data-stu-id="56a1e-105">During rendering, the pipeline interpolates vertex data across each triangle.</span></span> <span data-ttu-id="56a1e-106">Die Scheitelpunktdaten können sehr unterschiedliche Daten sein; dazu können u.a. gehören: diffuse Farbe, Glanzfarbe, diffuser Alphawert (Dreiecksopazität), Glanz-Alphawert und ein Nebelfaktor.</span><span class="sxs-lookup"><span data-stu-id="56a1e-106">Vertex data can be a broad variety of data and can include (but is not limited to): diffuse color, specular color, diffuse alpha (triangle opacity), specular alpha, and a fog factor.</span></span> <span data-ttu-id="56a1e-107">Für die programmierbare Scheitelpunkt-Pipeline wird der Nebelfaktor aus dem Nebelregister übernommen.</span><span class="sxs-lookup"><span data-stu-id="56a1e-107">For the programmable vertex pipeline, the fog factor is taken from the fog register.</span></span> <span data-ttu-id="56a1e-108">Für die Scheitelpunkt-Pipeline mit fester Funktion wird der Nebelfaktor dem Glanz-Alphawert entnommen.</span><span class="sxs-lookup"><span data-stu-id="56a1e-108">For the fixed-function vertex pipeline, the fog factor is taken from specular alpha.</span></span>

<span data-ttu-id="56a1e-109">Bei manchen Scheitelpunktdaten hängt die Interpolation wie folgt vom aktuellen Schattierungsmodus ab:</span><span class="sxs-lookup"><span data-stu-id="56a1e-109">For some vertex data, the interpolation is dependent on the current shading mode, as follows:</span></span>

| <span data-ttu-id="56a1e-110">Schattierungsmodus</span><span class="sxs-lookup"><span data-stu-id="56a1e-110">Shading mode</span></span> | <span data-ttu-id="56a1e-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="56a1e-111">Description</span></span>                                                                                                                                                                 |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="56a1e-112">Flach</span><span class="sxs-lookup"><span data-stu-id="56a1e-112">Flat</span></span>         | <span data-ttu-id="56a1e-113">Im Flach-Schattierungsmodus wird nur der Nebelfaktor interpoliert.</span><span class="sxs-lookup"><span data-stu-id="56a1e-113">Only the fog factor is interpolated in flat shade mode.</span></span> <span data-ttu-id="56a1e-114">Für alle anderen interpolierten Werte wird die Farbe des ersten Scheitelpunkts des Dreiecks über die gesamte Fläche angewendet.</span><span class="sxs-lookup"><span data-stu-id="56a1e-114">For all other interpolated values, the color of the first vertex in the triangle is applied across the entire face.</span></span> |
| <span data-ttu-id="56a1e-115">Gouraud</span><span class="sxs-lookup"><span data-stu-id="56a1e-115">Gouraud</span></span>      | <span data-ttu-id="56a1e-116">Zwischen allen drei Scheitelpunkten wird eine lineare Interpolation durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="56a1e-116">Linear interpolation is performed between all three vertices.</span></span>                                                                                                               |

 

<span data-ttu-id="56a1e-117">Diffus- und Glanzfarbe werden je nach Farbmodell unterschiedlich behandelt.</span><span class="sxs-lookup"><span data-stu-id="56a1e-117">The diffuse color and specular color are treated differently, depending on the color model.</span></span> <span data-ttu-id="56a1e-118">Im RGB-Farbmodell verwendet das System die Farbkomponenten Rot, Grün und Blau in der Interpolation.</span><span class="sxs-lookup"><span data-stu-id="56a1e-118">In the RGB color model, the system uses the red, green, and blue color components in the interpolation.</span></span>

<span data-ttu-id="56a1e-119">Die Alpha-Komponente einer Farbe wird als separater interpolierter Wert behandelt, da Gerätetreiber Transparenz auf zwei unterschiedliche Weisen implementieren können: durch Strukturmischung oder durch Punktierung.</span><span class="sxs-lookup"><span data-stu-id="56a1e-119">The alpha component of a color is treated as a separate interpolated value because device drivers can implement transparency in two different ways: by using texture blending or by using stippling.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="56a1e-120"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="56a1e-120"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="56a1e-121">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="56a1e-121">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




