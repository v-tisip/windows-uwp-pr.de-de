---
title: Umgebungslicht
description: Das Umgebungslicht bietet konstante Beleuchtung für eine Szene.
ms.assetid: C34FA65A-3634-4A4B-B183-4CDA89F4DC95
keywords:
- Umgebungslicht
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 87b5c72ef99e3802a348ddfd28951bc2865891e5
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7172371"
---
# <a name="ambient-lighting"></a><span data-ttu-id="a7db5-104">Umgebungslicht</span><span class="sxs-lookup"><span data-stu-id="a7db5-104">Ambient lighting</span></span>


<span data-ttu-id="a7db5-105">Umgebungsbeleuchtung bietet konstante Beleuchtung für eine Szene.</span><span class="sxs-lookup"><span data-stu-id="a7db5-105">Ambient lighting provides constant lighting for a scene.</span></span> <span data-ttu-id="a7db5-106">Sie leuchtet alle Objekteckpunkte gleich aus, da sie nicht von anderen Beleuchtungsfaktoren abhängig ist, wie der Eckpunktnormalen, der Richtung des Lichts, der Position der Lichtquelle, der Reichweite oder Abschwächung des Lichts.</span><span class="sxs-lookup"><span data-stu-id="a7db5-106">It lights all object vertices the same because it is not dependent on any other lighting factors such as vertex normals, light direction, light position, range, or attenuation.</span></span> <span data-ttu-id="a7db5-107">Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch.</span><span class="sxs-lookup"><span data-stu-id="a7db5-107">Ambient lighting is constant in all directions and it colors all pixels of an object the same.</span></span> <span data-ttu-id="a7db5-108">Obwohl die Berechnung schnell ist, sehen die Objekte flach und unrealistisch aus.</span><span class="sxs-lookup"><span data-stu-id="a7db5-108">It is fast to calculate but leaves objects looking flat and unrealistic.</span></span>

<span data-ttu-id="a7db5-109">Das Umgebungslicht ist zwar der schnellste Beleuchtungstyp, es erzeugt allerdings die unrealistischsten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="a7db5-109">Ambient lighting is the fastest type of lighting but it produces the least realistic results.</span></span> <span data-ttu-id="a7db5-110">Direct3D enthält eine einzige globale Umgebungslichteigenschaft, die Sie ohne Erstellen des Lichts verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a7db5-110">Direct3D contains a single global ambient light property that you can use without creating any light.</span></span> <span data-ttu-id="a7db5-111">Alternativ können Sie jede Lichtquellen als Umgebungslicht festlegen.</span><span class="sxs-lookup"><span data-stu-id="a7db5-111">Alternatively, you can set any light object to provide ambient lighting.</span></span>

<span data-ttu-id="a7db5-112">Das Umgebungslicht für eine Szene wird durch die folgende Gleichung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a7db5-112">The ambient lighting for a scene is described by the following equation.</span></span>

<span data-ttu-id="a7db5-113">Umgebungslicht = Cₐ\*\[Gₐ + sum(Atten<sub>i</sub>\*Spot<sub>i</sub>\*L<sub>ai</sub>)\]</span><span class="sxs-lookup"><span data-stu-id="a7db5-113">Ambient Lighting = Cₐ\*\[Gₐ + sum(Atten<sub>i</sub>\*Spot<sub>i</sub>\*L<sub>ai</sub>)\]</span></span>

<span data-ttu-id="a7db5-114">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="a7db5-114">Where:</span></span>

| <span data-ttu-id="a7db5-115">Parameter</span><span class="sxs-lookup"><span data-stu-id="a7db5-115">Parameter</span></span>         | <span data-ttu-id="a7db5-116">Standardwert</span><span class="sxs-lookup"><span data-stu-id="a7db5-116">Default value</span></span> | <span data-ttu-id="a7db5-117">Typ</span><span class="sxs-lookup"><span data-stu-id="a7db5-117">Type</span></span>          | <span data-ttu-id="a7db5-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a7db5-118">Description</span></span>                                                                                                       |
|-------------------|---------------|---------------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a7db5-119">Cₐ</span><span class="sxs-lookup"><span data-stu-id="a7db5-119">Cₐ</span></span>                | <span data-ttu-id="a7db5-120">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="a7db5-120">(0,0,0,0)</span></span>     | <span data-ttu-id="a7db5-121">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="a7db5-121">D3DCOLORVALUE</span></span> | <span data-ttu-id="a7db5-122">Materielle Umgebungsfarbe</span><span class="sxs-lookup"><span data-stu-id="a7db5-122">Material ambient color</span></span>                                                                                            |
| <span data-ttu-id="a7db5-123">Gₐ</span><span class="sxs-lookup"><span data-stu-id="a7db5-123">Gₐ</span></span>                | <span data-ttu-id="a7db5-124">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="a7db5-124">(0,0,0,0)</span></span>     | <span data-ttu-id="a7db5-125">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="a7db5-125">D3DCOLORVALUE</span></span> | <span data-ttu-id="a7db5-126">Globale Umgebungsfarbe</span><span class="sxs-lookup"><span data-stu-id="a7db5-126">Global ambient color</span></span>                                                                                              |
| <span data-ttu-id="a7db5-127">Atten<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="a7db5-127">Atten<sub>i</sub></span></span> | <span data-ttu-id="a7db5-128">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="a7db5-128">(0,0,0,0)</span></span>     | <span data-ttu-id="a7db5-129">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="a7db5-129">D3DCOLORVALUE</span></span> | <span data-ttu-id="a7db5-130">Dämpfung der ith-Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="a7db5-130">Light attenuation of the ith light.</span></span> <span data-ttu-id="a7db5-131">Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).</span><span class="sxs-lookup"><span data-stu-id="a7db5-131">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span> |
| <span data-ttu-id="a7db5-132">Spot<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="a7db5-132">Spot<sub>i</sub></span></span>  | <span data-ttu-id="a7db5-133">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="a7db5-133">(0,0,0,0)</span></span>     | <span data-ttu-id="a7db5-134">D3DVECTOR</span><span class="sxs-lookup"><span data-stu-id="a7db5-134">D3DVECTOR</span></span>     | <span data-ttu-id="a7db5-135">Spotlight-Faktor der ith-Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="a7db5-135">Spotlight factor of the ith light.</span></span> <span data-ttu-id="a7db5-136">Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).</span><span class="sxs-lookup"><span data-stu-id="a7db5-136">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span>  |
| <span data-ttu-id="a7db5-137">Summe</span><span class="sxs-lookup"><span data-stu-id="a7db5-137">sum</span></span>               | <span data-ttu-id="a7db5-138">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="a7db5-138">N/A</span></span>           | <span data-ttu-id="a7db5-139">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="a7db5-139">N/A</span></span>           | <span data-ttu-id="a7db5-140">Summe des Umgebungslichts</span><span class="sxs-lookup"><span data-stu-id="a7db5-140">Sum of the ambient light</span></span>                                                                                          |
| <span data-ttu-id="a7db5-141">L<sub>ai</sub></span><span class="sxs-lookup"><span data-stu-id="a7db5-141">L<sub>ai</sub></span></span>    | <span data-ttu-id="a7db5-142">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="a7db5-142">(0,0,0,0)</span></span>     | <span data-ttu-id="a7db5-143">D3DVECTOR</span><span class="sxs-lookup"><span data-stu-id="a7db5-143">D3DVECTOR</span></span>     | <span data-ttu-id="a7db5-144">Helle Umgebungsfarbe der ith-Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="a7db5-144">Light ambient color of the ith light</span></span>                                                                              |

 

<span data-ttu-id="a7db5-145">Der Wert für Cₐ ist entweder:</span><span class="sxs-lookup"><span data-stu-id="a7db5-145">The value for Cₐ is either:</span></span>

-   <span data-ttu-id="a7db5-146">Vertexfarbe1, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE1 und die erste Vertexfarbe in der Vertex-Deklaration angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a7db5-146">vertex color1, if AMBIENTMATERIALSOURCE = D3DMCS\_COLOR1, and the first vertex color is supplied in the vertex declaration.</span></span>
-   <span data-ttu-id="a7db5-147">Vertexfarbe2, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE2 und die zweite Vertexfarbe in der Vertex-Deklaration angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a7db5-147">vertex color2, if AMBIENTMATERIALSOURCE = D3DMCS\_COLOR2, and the second vertex color is supplied in vertex declaration.</span></span>
-   <span data-ttu-id="a7db5-148">Materielle Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="a7db5-148">material ambient color.</span></span>

<span data-ttu-id="a7db5-149">**Hinweis:**  Wenn Option AMBIENTMATERIALSOURCE verwendet wird, und die Vertexfarbe nicht angegeben, wird die materielle Umgebungsfarbe verwendet.</span><span class="sxs-lookup"><span data-stu-id="a7db5-149">**Note** If either AMBIENTMATERIALSOURCE option is used, and the vertex color is not provided, then the material ambient color is used.</span></span>

 

<span data-ttu-id="a7db5-150">Um die materielle Umgebungsfarbe anzuwenden, verwenden Sie „SetMaterial” wie im folgenden Beispielcode dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a7db5-150">To use the material ambient color, use SetMaterial as shown in the example code below.</span></span>

<span data-ttu-id="a7db5-151">Gₐ ist die globale Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="a7db5-151">Gₐ is the global ambient color.</span></span> <span data-ttu-id="a7db5-152">Sie wird mit „SetRenderState(D3DRS\_AMBIENT)” festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a7db5-152">It is set using SetRenderState(D3DRS\_AMBIENT).</span></span> <span data-ttu-id="a7db5-153">In einer Direct3D-Szene gibt es eine globale Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="a7db5-153">There is one global ambient color in a Direct3D scene.</span></span> <span data-ttu-id="a7db5-154">Dieser Parameter ist keinem Direct3D-Lichtobjekt zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="a7db5-154">This parameter is not associated with a Direct3D light object.</span></span>

<span data-ttu-id="a7db5-155">L<sub>ai</sub> ist die Umgebungsfarbe der ith-Beleuchtung in der Szene.</span><span class="sxs-lookup"><span data-stu-id="a7db5-155">L<sub>ai</sub> is the ambient color of the ith light in the scene.</span></span> <span data-ttu-id="a7db5-156">Jedes Direct3D-Licht hat eine Reihe von Eigenschaften, von denen eine die Umgebungsfarbe ist.</span><span class="sxs-lookup"><span data-stu-id="a7db5-156">Each Direct3D light has a set of properties, one of which is the ambient color.</span></span> <span data-ttu-id="a7db5-157">Der Begriff „Summe” (L<sub>Ai</sub>) beschreibt die Summe aller Umgebungsfarben in der Szene.</span><span class="sxs-lookup"><span data-stu-id="a7db5-157">The term, sum(L<sub>ai</sub>) is a sum of all the ambient colors in the scene.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="a7db5-158"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="a7db5-158"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="a7db5-159">In diesem Beispiel wird das Objekt durch die Farbe des Umgebungslichts der Szene und einer materiellen Umgebungsfarbe hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="a7db5-159">In this example, the object is colored using the scene ambient light and a material ambient color.</span></span>

```
#define GRAY_COLOR  0x00bfbfbf

Ambient.r = 0.75f;
Ambient.g = 0.0f;
Ambient.b = 0.0f;
Ambient.a = 0.0f;
```

<span data-ttu-id="a7db5-160">Gemäß der Gleichung ist die resultierende Farbe für die Objekt-Scheitelpunkte eine Kombination aus der materiellen Farbe und der Farbe des Lichts.</span><span class="sxs-lookup"><span data-stu-id="a7db5-160">According to the equation, the resulting color for the object vertices is a combination of the material color and the light color.</span></span>

<span data-ttu-id="a7db5-161">Die folgenden beiden Abbildungen zeigen die materielle Farbe (in Grau) und die Farbe des Lichts (hellrot).</span><span class="sxs-lookup"><span data-stu-id="a7db5-161">The following two illustrations show the material color, which is gray, and the light color, which is bright red.</span></span>

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer roten Kugel](images/lightred.jpg)

<span data-ttu-id="a7db5-164">Die resultierende Szene ist in der folgenden Abbildungdargestellt.</span><span class="sxs-lookup"><span data-stu-id="a7db5-164">The resulting scene is shown in the following illustration.</span></span> <span data-ttu-id="a7db5-165">Das einzige Objekt in der Szene ist eine Kugel.</span><span class="sxs-lookup"><span data-stu-id="a7db5-165">The only object in the scene is a sphere.</span></span> <span data-ttu-id="a7db5-166">Das Umgebungslicht beleuchtet alle Objekt-Schnittpunkte mit derselben Farbe.</span><span class="sxs-lookup"><span data-stu-id="a7db5-166">Ambient light lights all object vertices with the same color.</span></span> <span data-ttu-id="a7db5-167">Es ist nicht von der Vertexnormale oder Lichteinfallsrichtung abhängig.</span><span class="sxs-lookup"><span data-stu-id="a7db5-167">It is not dependent on the vertex normal or the light direction.</span></span> <span data-ttu-id="a7db5-168">Die Kugel sieht wie ein 2D-Kreis aus, da es keinen Unterschied in der Schattierung der Oberfläche des Objekts gibt.</span><span class="sxs-lookup"><span data-stu-id="a7db5-168">As a result, the sphere looks like a 2D circle because there is no difference in shading around the surface of the object.</span></span>

![Abbildung einer Kugel mit Umgebungslicht](images/lighta.jpg)

<span data-ttu-id="a7db5-170">Verwenden Sie neben dem Umgebungslicht diffuses oder Glanzlicht, um Objekten ein realistischeres Aussehen zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="a7db5-170">To give objects a more realistic look, apply diffuse or specular lighting in addition to ambient lighting.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a7db5-171"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a7db5-171"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a7db5-172">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="a7db5-172">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




