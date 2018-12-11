---
title: Beleuchtung
description: Lichter werden verwendet, um Objekte in einer Szene zu beleuchten. Die Farbe eines Objekt-Vertex basiert auf der aktuellen Texturmap, Vertexfarben und Lichtquellen.
ms.assetid: AB16CF5B-47CE-455C-A8BD-36305E54BEA9
keywords:
- Beleuchtung
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 012b0bae7c0abdacba352a3e8f60bcfd0aa1dd54
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8894877"
---
# <a name="lighting"></a><span data-ttu-id="b1210-105">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="b1210-105">Lighting</span></span>


<span data-ttu-id="b1210-106">Lichter werden verwendet, um Objekte in einer Szene zu beleuchten.</span><span class="sxs-lookup"><span data-stu-id="b1210-106">Lights are used to illuminate objects in a scene.</span></span> <span data-ttu-id="b1210-107">Die Farbe jedes Objektscheitelpunkts basiert auf der aktuellen Texturzuordnung, Scheitelpunktfarben und Lichtquellen.</span><span class="sxs-lookup"><span data-stu-id="b1210-107">The color of each object vertex is based on the current texture map, vertex colors, and light sources.</span></span>

<span data-ttu-id="b1210-108">**Hinweis:**  dieser Abschnitt gilt nur für die Pipeline mit fester Funktion.</span><span class="sxs-lookup"><span data-stu-id="b1210-108">**Note** This section is only for the fixed-function pipeline.</span></span> <span data-ttu-id="b1210-109">Programmierbare Shader führen jede Beleuchtung explizit aus.</span><span class="sxs-lookup"><span data-stu-id="b1210-109">Programmable shaders perform all lighting explicitly.</span></span>

 

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="b1210-110"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="b1210-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="b1210-111">Thema</span><span class="sxs-lookup"><span data-stu-id="b1210-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="b1210-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b1210-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="lighting-overview.md"><span data-ttu-id="b1210-113">Übersicht über die Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="b1210-113">Lighting overview</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="b1210-114">Wenn Sie Direct3D-Beleuchtung verwenden, erlauben Sie es Direct3D, die Details der Beleuchtung für Sie zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="b1210-114">When you use Direct3D lighting, you allow Direct3D to handle the details of illumination for you.</span></span> <span data-ttu-id="b1210-115">Fortgeschrittene Benutzer können die Beleuchtung bei Bedarf selbst ausführen.</span><span class="sxs-lookup"><span data-stu-id="b1210-115">Advanced users can perform lighting on their own, if desired.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="light-types.md"><span data-ttu-id="b1210-116">Lichttypen</span><span class="sxs-lookup"><span data-stu-id="b1210-116">Light types</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="b1210-117">Die Lichttyp-Eigenschaft bestimmt, welche Art von Lichtquelle Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="b1210-117">The light type property defines which type of light source you're using.</span></span> <span data-ttu-id="b1210-118">Es gibt drei Arten von Licht in Direct3D: Punktlicht, Scheinwerferlicht und gerichtetes Licht.</span><span class="sxs-lookup"><span data-stu-id="b1210-118">There are three types of lights in Direct3D - point lights, spotlights, and directional lights.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="light-properties.md"><span data-ttu-id="b1210-119">Lichteigenschaften</span><span class="sxs-lookup"><span data-stu-id="b1210-119">Light properties</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="b1210-120">Lichteigenschaften beschreiben den Typ einer Lichtquelle (punktuelles, gerichtetes oder Scheinwerferlicht), Dämpfung, Farbe, Richtung, Position und Reichweite.</span><span class="sxs-lookup"><span data-stu-id="b1210-120">Light properties describe a light source's type (point, directional, spotlight), attenuation, color, direction, position, and range.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="mathematics-of-lighting.md"><span data-ttu-id="b1210-121">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="b1210-121">Mathematics of lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="b1210-122">Das Direct3D-Beleuchtungsmodell deckt Umgebungs-, diffuse, spiegelnde und ausstrahlende Beleuchtung ab.</span><span class="sxs-lookup"><span data-stu-id="b1210-122">The Direct3D Light Model covers ambient, diffuse, specular, and emissive lighting.</span></span> <span data-ttu-id="b1210-123">Dies bietet eine ausreichende Flexibilität zum Lösen einer breiten Palette an Beleuchtungssituationen.</span><span class="sxs-lookup"><span data-stu-id="b1210-123">This is enough flexibility to solve a wide range of lighting situations.</span></span> <span data-ttu-id="b1210-124">Die Gesamtmenge an Licht in einer Szene wird als <em>globale Beleuchtung</em> bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b1210-124">The total amount of light in a scene is called the <em>global illumination</em>.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="b1210-125"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b1210-125"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="b1210-126">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="b1210-126">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




