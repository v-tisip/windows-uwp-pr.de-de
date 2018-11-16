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
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6835601"
---
# <a name="ambient-lighting"></a><span data-ttu-id="dd9fc-104">Umgebungslicht</span><span class="sxs-lookup"><span data-stu-id="dd9fc-104">Ambient lighting</span></span>


<span data-ttu-id="dd9fc-105">Umgebungsbeleuchtung bietet konstante Beleuchtung für eine Szene.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-105">Ambient lighting provides constant lighting for a scene.</span></span> <span data-ttu-id="dd9fc-106">Sie leuchtet alle Objekteckpunkte gleich aus, da sie nicht von anderen Beleuchtungsfaktoren abhängig ist, wie der Eckpunktnormalen, der Richtung des Lichts, der Position der Lichtquelle, der Reichweite oder Abschwächung des Lichts.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-106">It lights all object vertices the same because it is not dependent on any other lighting factors such as vertex normals, light direction, light position, range, or attenuation.</span></span> <span data-ttu-id="dd9fc-107">Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-107">Ambient lighting is constant in all directions and it colors all pixels of an object the same.</span></span> <span data-ttu-id="dd9fc-108">Obwohl die Berechnung schnell ist, sehen die Objekte flach und unrealistisch aus.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-108">It is fast to calculate but leaves objects looking flat and unrealistic.</span></span>

<span data-ttu-id="dd9fc-109">Das Umgebungslicht ist zwar der schnellste Beleuchtungstyp, es erzeugt allerdings die unrealistischsten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-109">Ambient lighting is the fastest type of lighting but it produces the least realistic results.</span></span> <span data-ttu-id="dd9fc-110">Direct3D enthält eine einzige globale Umgebungslichteigenschaft, die Sie ohne Erstellen des Lichts verwenden können.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-110">Direct3D contains a single global ambient light property that you can use without creating any light.</span></span> <span data-ttu-id="dd9fc-111">Alternativ können Sie jede Lichtquellen als Umgebungslicht festlegen.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-111">Alternatively, you can set any light object to provide ambient lighting.</span></span>

<span data-ttu-id="dd9fc-112">Das Umgebungslicht für eine Szene wird durch die folgende Gleichung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-112">The ambient lighting for a scene is described by the following equation.</span></span>

<span data-ttu-id="dd9fc-113">Umgebungslicht = Cₐ\*\[Gₐ + sum(Atten<sub>i</sub>\*Spot<sub>i</sub>\*L<sub>ai</sub>)\]</span><span class="sxs-lookup"><span data-stu-id="dd9fc-113">Ambient Lighting = Cₐ\*\[Gₐ + sum(Atten<sub>i</sub>\*Spot<sub>i</sub>\*L<sub>ai</sub>)\]</span></span>

<span data-ttu-id="dd9fc-114">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="dd9fc-114">Where:</span></span>

| <span data-ttu-id="dd9fc-115">Parameter</span><span class="sxs-lookup"><span data-stu-id="dd9fc-115">Parameter</span></span>         | <span data-ttu-id="dd9fc-116">Standardwert</span><span class="sxs-lookup"><span data-stu-id="dd9fc-116">Default value</span></span> | <span data-ttu-id="dd9fc-117">Typ</span><span class="sxs-lookup"><span data-stu-id="dd9fc-117">Type</span></span>          | <span data-ttu-id="dd9fc-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dd9fc-118">Description</span></span>                                                                                                       |
|-------------------|---------------|---------------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dd9fc-119">Cₐ</span><span class="sxs-lookup"><span data-stu-id="dd9fc-119">Cₐ</span></span>                | <span data-ttu-id="dd9fc-120">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="dd9fc-120">(0,0,0,0)</span></span>     | <span data-ttu-id="dd9fc-121">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="dd9fc-121">D3DCOLORVALUE</span></span> | <span data-ttu-id="dd9fc-122">Materielle Umgebungsfarbe</span><span class="sxs-lookup"><span data-stu-id="dd9fc-122">Material ambient color</span></span>                                                                                            |
| <span data-ttu-id="dd9fc-123">Gₐ</span><span class="sxs-lookup"><span data-stu-id="dd9fc-123">Gₐ</span></span>                | <span data-ttu-id="dd9fc-124">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="dd9fc-124">(0,0,0,0)</span></span>     | <span data-ttu-id="dd9fc-125">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="dd9fc-125">D3DCOLORVALUE</span></span> | <span data-ttu-id="dd9fc-126">Globale Umgebungsfarbe</span><span class="sxs-lookup"><span data-stu-id="dd9fc-126">Global ambient color</span></span>                                                                                              |
| <span data-ttu-id="dd9fc-127">Atten<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="dd9fc-127">Atten<sub>i</sub></span></span> | <span data-ttu-id="dd9fc-128">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="dd9fc-128">(0,0,0,0)</span></span>     | <span data-ttu-id="dd9fc-129">D3DCOLORVALUE</span><span class="sxs-lookup"><span data-stu-id="dd9fc-129">D3DCOLORVALUE</span></span> | <span data-ttu-id="dd9fc-130">Dämpfung der ith-Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-130">Light attenuation of the ith light.</span></span> <span data-ttu-id="dd9fc-131">Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).</span><span class="sxs-lookup"><span data-stu-id="dd9fc-131">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span> |
| <span data-ttu-id="dd9fc-132">Spot<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="dd9fc-132">Spot<sub>i</sub></span></span>  | <span data-ttu-id="dd9fc-133">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="dd9fc-133">(0,0,0,0)</span></span>     | <span data-ttu-id="dd9fc-134">D3DVECTOR</span><span class="sxs-lookup"><span data-stu-id="dd9fc-134">D3DVECTOR</span></span>     | <span data-ttu-id="dd9fc-135">Spotlight-Faktor der ith-Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-135">Spotlight factor of the ith light.</span></span> <span data-ttu-id="dd9fc-136">Unter [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).</span><span class="sxs-lookup"><span data-stu-id="dd9fc-136">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span>  |
| <span data-ttu-id="dd9fc-137">Summe</span><span class="sxs-lookup"><span data-stu-id="dd9fc-137">sum</span></span>               | <span data-ttu-id="dd9fc-138">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="dd9fc-138">N/A</span></span>           | <span data-ttu-id="dd9fc-139">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="dd9fc-139">N/A</span></span>           | <span data-ttu-id="dd9fc-140">Summe des Umgebungslichts</span><span class="sxs-lookup"><span data-stu-id="dd9fc-140">Sum of the ambient light</span></span>                                                                                          |
| <span data-ttu-id="dd9fc-141">L<sub>ai</sub></span><span class="sxs-lookup"><span data-stu-id="dd9fc-141">L<sub>ai</sub></span></span>    | <span data-ttu-id="dd9fc-142">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="dd9fc-142">(0,0,0,0)</span></span>     | <span data-ttu-id="dd9fc-143">D3DVECTOR</span><span class="sxs-lookup"><span data-stu-id="dd9fc-143">D3DVECTOR</span></span>     | <span data-ttu-id="dd9fc-144">Helle Umgebungsfarbe der ith-Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="dd9fc-144">Light ambient color of the ith light</span></span>                                                                              |

 

<span data-ttu-id="dd9fc-145">Der Wert für Cₐ ist entweder:</span><span class="sxs-lookup"><span data-stu-id="dd9fc-145">The value for Cₐ is either:</span></span>

-   <span data-ttu-id="dd9fc-146">Vertexfarbe1, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE1 und die erste Vertexfarbe in der Vertex-Deklaration angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-146">vertex color1, if AMBIENTMATERIALSOURCE = D3DMCS\_COLOR1, and the first vertex color is supplied in the vertex declaration.</span></span>
-   <span data-ttu-id="dd9fc-147">Vertexfarbe2, wenn AMBIENTMATERIALSOURCE = D3DMCS\_FARBE2 und die zweite Vertexfarbe in der Vertex-Deklaration angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-147">vertex color2, if AMBIENTMATERIALSOURCE = D3DMCS\_COLOR2, and the second vertex color is supplied in vertex declaration.</span></span>
-   <span data-ttu-id="dd9fc-148">Materielle Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-148">material ambient color.</span></span>

<span data-ttu-id="dd9fc-149">**Hinweis:**  Wenn Option AMBIENTMATERIALSOURCE verwendet wird, und die Vertexfarbe nicht angegeben, wird die materielle Umgebungsfarbe verwendet.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-149">**Note** If either AMBIENTMATERIALSOURCE option is used, and the vertex color is not provided, then the material ambient color is used.</span></span>

 

<span data-ttu-id="dd9fc-150">Um die materielle Umgebungsfarbe anzuwenden, verwenden Sie „SetMaterial” wie im folgenden Beispielcode dargestellt.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-150">To use the material ambient color, use SetMaterial as shown in the example code below.</span></span>

<span data-ttu-id="dd9fc-151">Gₐ ist die globale Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-151">Gₐ is the global ambient color.</span></span> <span data-ttu-id="dd9fc-152">Sie wird mit „SetRenderState(D3DRS\_AMBIENT)” festgelegt.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-152">It is set using SetRenderState(D3DRS\_AMBIENT).</span></span> <span data-ttu-id="dd9fc-153">In einer Direct3D-Szene gibt es eine globale Umgebungsfarbe.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-153">There is one global ambient color in a Direct3D scene.</span></span> <span data-ttu-id="dd9fc-154">Dieser Parameter ist keinem Direct3D-Lichtobjekt zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-154">This parameter is not associated with a Direct3D light object.</span></span>

<span data-ttu-id="dd9fc-155">L<sub>ai</sub> ist die Umgebungsfarbe der ith-Beleuchtung in der Szene.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-155">L<sub>ai</sub> is the ambient color of the ith light in the scene.</span></span> <span data-ttu-id="dd9fc-156">Jedes Direct3D-Licht hat eine Reihe von Eigenschaften, von denen eine die Umgebungsfarbe ist.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-156">Each Direct3D light has a set of properties, one of which is the ambient color.</span></span> <span data-ttu-id="dd9fc-157">Der Begriff „Summe” (L<sub>Ai</sub>) beschreibt die Summe aller Umgebungsfarben in der Szene.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-157">The term, sum(L<sub>ai</sub>) is a sum of all the ambient colors in the scene.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="dd9fc-158"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="dd9fc-158"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="dd9fc-159">In diesem Beispiel wird das Objekt durch die Farbe des Umgebungslichts der Szene und einer materiellen Umgebungsfarbe hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-159">In this example, the object is colored using the scene ambient light and a material ambient color.</span></span>

```
#define GRAY_COLOR  0x00bfbfbf

Ambient.r = 0.75f;
Ambient.g = 0.0f;
Ambient.b = 0.0f;
Ambient.a = 0.0f;
```

<span data-ttu-id="dd9fc-160">Gemäß der Gleichung ist die resultierende Farbe für die Objekt-Scheitelpunkte eine Kombination aus der materiellen Farbe und der Farbe des Lichts.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-160">According to the equation, the resulting color for the object vertices is a combination of the material color and the light color.</span></span>

<span data-ttu-id="dd9fc-161">Die folgenden beiden Abbildungen zeigen die materielle Farbe (in Grau) und die Farbe des Lichts (hellrot).</span><span class="sxs-lookup"><span data-stu-id="dd9fc-161">The following two illustrations show the material color, which is gray, and the light color, which is bright red.</span></span>

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer roten Kugel](images/lightred.jpg)

<span data-ttu-id="dd9fc-164">Die resultierende Szene ist in der folgenden Abbildungdargestellt.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-164">The resulting scene is shown in the following illustration.</span></span> <span data-ttu-id="dd9fc-165">Das einzige Objekt in der Szene ist eine Kugel.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-165">The only object in the scene is a sphere.</span></span> <span data-ttu-id="dd9fc-166">Das Umgebungslicht beleuchtet alle Objekt-Schnittpunkte mit derselben Farbe.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-166">Ambient light lights all object vertices with the same color.</span></span> <span data-ttu-id="dd9fc-167">Es ist nicht von der Vertexnormale oder Lichteinfallsrichtung abhängig.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-167">It is not dependent on the vertex normal or the light direction.</span></span> <span data-ttu-id="dd9fc-168">Die Kugel sieht wie ein 2D-Kreis aus, da es keinen Unterschied in der Schattierung der Oberfläche des Objekts gibt.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-168">As a result, the sphere looks like a 2D circle because there is no difference in shading around the surface of the object.</span></span>

![Abbildung einer Kugel mit Umgebungslicht](images/lighta.jpg)

<span data-ttu-id="dd9fc-170">Verwenden Sie neben dem Umgebungslicht diffuses oder Glanzlicht, um Objekten ein realistischeres Aussehen zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="dd9fc-170">To give objects a more realistic look, apply diffuse or specular lighting in addition to ambient lighting.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="dd9fc-171"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="dd9fc-171"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="dd9fc-172">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="dd9fc-172">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




