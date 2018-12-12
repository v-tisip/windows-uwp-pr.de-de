---
title: Dämpfungs- und Spotlight-Faktor
description: Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben.
ms.assetid: F61D4ACB-09AB-4087-9E2D-224E472D6196
keywords:
- Dämpfungs- und Spotlight-Faktor
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 8126ac8fa738a2b8a9680d215179fe23f77c5d44
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8937844"
---
# <a name="attenuation-and-spotlight-factor"></a><span data-ttu-id="5f058-104">Dämpfungs- und Spotlight-Faktor</span><span class="sxs-lookup"><span data-stu-id="5f058-104">Attenuation and spotlight factor</span></span>


<span data-ttu-id="5f058-105">Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben.</span><span class="sxs-lookup"><span data-stu-id="5f058-105">The diffuse and specular lighting components of the global illumination equation contain terms that describe light attenuation and the spotlight cone.</span></span> <span data-ttu-id="5f058-106">Diese Begriffe werden nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5f058-106">These terms are described below.</span></span>

## <a name="span-idattenuationspanspan-idattenuationspanspan-idattenuationspanattenuation"></a><span data-ttu-id="5f058-107"><span id="Attenuation"></span><span id="attenuation"></span><span id="ATTENUATION"></span>Dämpfung</span><span class="sxs-lookup"><span data-stu-id="5f058-107"><span id="Attenuation"></span><span id="attenuation"></span><span id="ATTENUATION"></span>Attenuation</span></span>


<span data-ttu-id="5f058-108">Die Lichtdämpfung hängt vom Typ des Lichts und dem Abstand zwischen dem Licht und der Vertexposition ab.</span><span class="sxs-lookup"><span data-stu-id="5f058-108">The attenuation of a light depends on the type of light and the distance between the light and the vertex position.</span></span> <span data-ttu-id="5f058-109">Verwenden Sie eine der folgenden Formeln, um die Dämpfung zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="5f058-109">To calculate attenuation, use one of the following equations.</span></span>

<span data-ttu-id="5f058-110">Atten = 1/( att0<sub>i</sub> + att1<sub>i</sub> \* d + att2<sub>i</sub> \* d²)</span><span class="sxs-lookup"><span data-stu-id="5f058-110">Atten = 1/( att0<sub>i</sub> + att1<sub>i</sub> \* d + att2<sub>i</sub> \* d²)</span></span>

<span data-ttu-id="5f058-111">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="5f058-111">Where:</span></span>

| <span data-ttu-id="5f058-112">Parameter</span><span class="sxs-lookup"><span data-stu-id="5f058-112">Parameter</span></span>        | <span data-ttu-id="5f058-113">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f058-113">Default value</span></span> | <span data-ttu-id="5f058-114">Typ</span><span class="sxs-lookup"><span data-stu-id="5f058-114">Type</span></span>           | <span data-ttu-id="5f058-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f058-115">Description</span></span>                                     | <span data-ttu-id="5f058-116">Bereich</span><span class="sxs-lookup"><span data-stu-id="5f058-116">Range</span></span>          |
|------------------|---------------|----------------|-------------------------------------------------|----------------|
| <span data-ttu-id="5f058-117">att0<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-117">att0<sub>i</sub></span></span> | <span data-ttu-id="5f058-118">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-118">0.0</span></span>           | <span data-ttu-id="5f058-119">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-119">Floating point</span></span> | <span data-ttu-id="5f058-120">Konstanter Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="5f058-120">Constant attenuation factor</span></span>                     | <span data-ttu-id="5f058-121">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="5f058-121">0 to +infinity</span></span> |
| <span data-ttu-id="5f058-122">att1<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-122">att1<sub>i</sub></span></span> | <span data-ttu-id="5f058-123">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-123">0.0</span></span>           | <span data-ttu-id="5f058-124">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-124">Floating point</span></span> | <span data-ttu-id="5f058-125">Linearer Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="5f058-125">Linear attenuation factor</span></span>                       | <span data-ttu-id="5f058-126">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="5f058-126">0 to +infinity</span></span> |
| <span data-ttu-id="5f058-127">att2<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-127">att2<sub>i</sub></span></span> | <span data-ttu-id="5f058-128">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-128">0.0</span></span>           | <span data-ttu-id="5f058-129">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-129">Floating point</span></span> | <span data-ttu-id="5f058-130">Quadratischer Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="5f058-130">Quadratic attenuation factor</span></span>                    | <span data-ttu-id="5f058-131">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="5f058-131">0 to +infinity</span></span> |
| <span data-ttu-id="5f058-132">d</span><span class="sxs-lookup"><span data-stu-id="5f058-132">d</span></span>                | <span data-ttu-id="5f058-133">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-133">N/A</span></span>           | <span data-ttu-id="5f058-134">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-134">Floating point</span></span> | <span data-ttu-id="5f058-135">Abstand zwischen Vertexposition und Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="5f058-135">Distance from vertex position to light position</span></span> | <span data-ttu-id="5f058-136">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-136">N/A</span></span>            |

 

-   <span data-ttu-id="5f058-137">Dämpfung = 1, wenn das Licht ein gerichtetes Licht ist.</span><span class="sxs-lookup"><span data-stu-id="5f058-137">Atten = 1, if the light is a directional light.</span></span>
-   <span data-ttu-id="5f058-138">Dämpfung = 0, wenn der Abstand zwischen Licht und Vertex die Reichweite des Lichts überschreitet.</span><span class="sxs-lookup"><span data-stu-id="5f058-138">Atten = 0, if the distance between the light and the vertex exceeds the light's range.</span></span>

<span data-ttu-id="5f058-139">Der Abstand zwischen Lichtquelle und Vertexposition ist immer positiv.</span><span class="sxs-lookup"><span data-stu-id="5f058-139">The distance between the light and the vertex position is always positive.</span></span>

<span data-ttu-id="5f058-140">d = | L<sub>dir</sub> |</span><span class="sxs-lookup"><span data-stu-id="5f058-140">d = | L<sub>dir</sub> |</span></span>

<span data-ttu-id="5f058-141">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="5f058-141">Where:</span></span>

| <span data-ttu-id="5f058-142">Parameter</span><span class="sxs-lookup"><span data-stu-id="5f058-142">Parameter</span></span>       | <span data-ttu-id="5f058-143">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f058-143">Default value</span></span> | <span data-ttu-id="5f058-144">Typ</span><span class="sxs-lookup"><span data-stu-id="5f058-144">Type</span></span>                                             | <span data-ttu-id="5f058-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f058-145">Description</span></span>                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="5f058-146">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-146">L<sub>dir</sub></span></span> | <span data-ttu-id="5f058-147">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-147">N/A</span></span>           | <span data-ttu-id="5f058-148">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="5f058-148">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="5f058-149">Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="5f058-149">Direction vector from vertex position to the light position</span></span> |

 

<span data-ttu-id="5f058-150">Wenn d größer als die Reichweite des Lichts ist, nimmt Direct3D keine weiteren abnehmenden Berechnungen vor und wendet keine Effekte von der Lichtquelle bis zum Vertex an.</span><span class="sxs-lookup"><span data-stu-id="5f058-150">If d is greater than the light's range, Direct3D makes no further attenuation calculations and applies no effects from the light to the vertex.</span></span>

<span data-ttu-id="5f058-151">Die Dämpfungskonstanten fungieren in der Formel als Koeffizient – Sie können eine Vielzahl von Dämpfungskurven erstellen, indem Sie diese einfach anpassen.</span><span class="sxs-lookup"><span data-stu-id="5f058-151">The attenuation constants act as coefficients in the formula - you can produce a variety of attenuation curves by making simple adjustments to them.</span></span> <span data-ttu-id="5f058-152">Sie können Dämpfung1 auf 1,0 einstellen, um ein Licht zu erstellen, das sich nicht dämpfen lässt aber trotzdem von der Reichweite begrenzt ist. Sie können ebenfalls mit verschiedenen Werten experimentieren, um verschiedene Dämpfungseffekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="5f058-152">You can set Attenuation1 to 1.0 to create a light that doesn't attenuate but is still limited by range, or you can experiment with different values to achieve various attenuation effects.</span></span>

<span data-ttu-id="5f058-153">Die Dämpfung bei maximaler Reichweite des Lichts ist 0,0.</span><span class="sxs-lookup"><span data-stu-id="5f058-153">The attenuation at the maximum range of the light is not 0.0.</span></span> <span data-ttu-id="5f058-154">Um zu verhindern, dass Lichter plötzlich angezeigt werden, wenn sie sich in Reichweite des Lichts befinden, kann eine Anwendung die Reichweite des Lichts erhöhen.</span><span class="sxs-lookup"><span data-stu-id="5f058-154">To prevent lights from suddenly appearing when they are at the light range, an application can increase the light range.</span></span> <span data-ttu-id="5f058-155">Die Anwendung kann ebenfalls Dämpfungskonstanten so einrichten, dass der Dämpfungsfaktor nahe an der Reichweite 0,0 des Lichts liegt.</span><span class="sxs-lookup"><span data-stu-id="5f058-155">Or, the application can set up attenuation constants so that the attenuation factor is close to 0.0 at the light range.</span></span> <span data-ttu-id="5f058-156">Der Dämpfungswert wird mit den roten, grünen und blauen Komponenten der Farbe des Lichts multipliziert, um die Intensität des Lichts als Faktor der Distanz zu skalieren, die das Licht bis zum Vertex zurücklegt.</span><span class="sxs-lookup"><span data-stu-id="5f058-156">The attenuation value is multiplied by the red, green, and blue components of the light's color to scale the light's intensity as a factor of the distance light travels to a vertex.</span></span>

## <a name="span-idspotlight-factorspanspan-idspotlight-factorspanspan-idspotlight-factorspanspotlight-factor"></a><span data-ttu-id="5f058-157"><span id="Spotlight-Factor"></span><span id="spotlight-factor"></span><span id="SPOTLIGHT-FACTOR"></span>Spotlight-Faktor</span><span class="sxs-lookup"><span data-stu-id="5f058-157"><span id="Spotlight-Factor"></span><span id="spotlight-factor"></span><span id="SPOTLIGHT-FACTOR"></span>Spotlight Factor</span></span>


<span data-ttu-id="5f058-158">Die folgende Gleichung legt den Spotlight-Faktor fest.</span><span class="sxs-lookup"><span data-stu-id="5f058-158">The following equation specifies the spotlight factor.</span></span>

![Gleichung für den Spotlight-Faktor](images/dx8light9.png)

| <span data-ttu-id="5f058-160">Parameter</span><span class="sxs-lookup"><span data-stu-id="5f058-160">Parameter</span></span>         | <span data-ttu-id="5f058-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f058-161">Default value</span></span> | <span data-ttu-id="5f058-162">Typ</span><span class="sxs-lookup"><span data-stu-id="5f058-162">Type</span></span>           | <span data-ttu-id="5f058-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f058-163">Description</span></span>                              | <span data-ttu-id="5f058-164">Bereich</span><span class="sxs-lookup"><span data-stu-id="5f058-164">Range</span></span>                    |
|-------------------|---------------|----------------|------------------------------------------|--------------------------|
| <span data-ttu-id="5f058-165">rho<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-165">rho<sub>i</sub></span></span>   | <span data-ttu-id="5f058-166">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-166">N/A</span></span>           | <span data-ttu-id="5f058-167">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-167">Floating point</span></span> | <span data-ttu-id="5f058-168">Kosinus(Winkel) für Spotlight i</span><span class="sxs-lookup"><span data-stu-id="5f058-168">cosine(angle) for spotlight i</span></span>            | <span data-ttu-id="5f058-169">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-169">N/A</span></span>                      |
| <span data-ttu-id="5f058-170">phi<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-170">phi<sub>i</sub></span></span>   | <span data-ttu-id="5f058-171">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-171">0.0</span></span>           | <span data-ttu-id="5f058-172">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-172">Floating point</span></span> | <span data-ttu-id="5f058-173">Halbschatten-Winkel für Spotlight i nach Bogenmaß</span><span class="sxs-lookup"><span data-stu-id="5f058-173">Penumbra angle of spotlight i in radians</span></span> | <span data-ttu-id="5f058-174">\[theta<sub>i</sub>, pi)</span><span class="sxs-lookup"><span data-stu-id="5f058-174">\[theta<sub>i</sub>, pi)</span></span> |
| <span data-ttu-id="5f058-175">theta<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-175">theta<sub>i</sub></span></span> | <span data-ttu-id="5f058-176">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-176">0.0</span></span>           | <span data-ttu-id="5f058-177">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-177">Floating point</span></span> | <span data-ttu-id="5f058-178">Kernschatten-Winkel für Spotlight i nach Bogenmaß</span><span class="sxs-lookup"><span data-stu-id="5f058-178">Umbra angle of spotlight i in radians</span></span>    | <span data-ttu-id="5f058-179">\[0, pi)</span><span class="sxs-lookup"><span data-stu-id="5f058-179">\[0, pi)</span></span>                 |
| <span data-ttu-id="5f058-180">Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="5f058-180">falloff</span></span>           | <span data-ttu-id="5f058-181">0,0</span><span class="sxs-lookup"><span data-stu-id="5f058-181">0.0</span></span>           | <span data-ttu-id="5f058-182">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="5f058-182">Floating point</span></span> | <span data-ttu-id="5f058-183">Farbverlaufsfaktor</span><span class="sxs-lookup"><span data-stu-id="5f058-183">Falloff factor</span></span>                           | <span data-ttu-id="5f058-184">(-unendlich +unendlich)</span><span class="sxs-lookup"><span data-stu-id="5f058-184">(-infinity, +infinity)</span></span>   |

 

<span data-ttu-id="5f058-185">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="5f058-185">Where:</span></span>

<span data-ttu-id="5f058-186">rho = norm(L<sub>dcs</sub>)<sup>.</sup>norm(L<sub>dir</sub>)</span><span class="sxs-lookup"><span data-stu-id="5f058-186">rho = norm(L<sub>dcs</sub>)<sup>.</sup>norm(L<sub>dir</sub>)</span></span>

<span data-ttu-id="5f058-187">und</span><span class="sxs-lookup"><span data-stu-id="5f058-187">and:</span></span>

| <span data-ttu-id="5f058-188">Parameter</span><span class="sxs-lookup"><span data-stu-id="5f058-188">Parameter</span></span>       | <span data-ttu-id="5f058-189">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f058-189">Default value</span></span> | <span data-ttu-id="5f058-190">Typ</span><span class="sxs-lookup"><span data-stu-id="5f058-190">Type</span></span>                                             | <span data-ttu-id="5f058-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5f058-191">Description</span></span>                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="5f058-192">L<sub>dcs</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-192">L<sub>dcs</sub></span></span> | <span data-ttu-id="5f058-193">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-193">N/A</span></span>           | <span data-ttu-id="5f058-194">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="5f058-194">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="5f058-195">Der negativen Wert der Lichteinfallsrichtung im Kamerabereich</span><span class="sxs-lookup"><span data-stu-id="5f058-195">The negative of the light direction in camera space</span></span>         |
| <span data-ttu-id="5f058-196">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="5f058-196">L<sub>dir</sub></span></span> | <span data-ttu-id="5f058-197">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="5f058-197">N/A</span></span>           | <span data-ttu-id="5f058-198">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="5f058-198">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="5f058-199">Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="5f058-199">Direction vector from vertex position to the light position</span></span> |

 

<span data-ttu-id="5f058-200">Nach dem Berechnen der Lichtdämpfung berücksichtigt Direct3D auch eventuelle Spotlight-Effekte, den vom Licht von der Oberfläche reflektierten Winkel und den Reflexionsgrad des aktuellen Materials, um die diffusen und Glanzlichtkomponenten für den Vertex zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="5f058-200">After computing the light attenuation, to calculate the diffuse and specular components for the vertex, Direct3D also considers spotlight effects if applicable, the angle that the light reflects from a surface, and the reflectance of the current material.</span></span> <span data-ttu-id="5f058-201">Siehe auch Spotlight unter [Lichttypen](light-types.md).</span><span class="sxs-lookup"><span data-stu-id="5f058-201">In [Light types](light-types.md), see "Spotlight".</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="5f058-202"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5f058-202"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="5f058-203">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="5f058-203">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




