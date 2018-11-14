---
title: Dämpfungs- und Spotlight-Faktor
description: Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben.
ms.assetid: F61D4ACB-09AB-4087-9E2D-224E472D6196
keywords:
- Dämpfungs- und Spotlight-Faktor
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 65b9f6700ddd11c41193820a5247a90c2382c98b
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6164453"
---
# <a name="attenuation-and-spotlight-factor"></a><span data-ttu-id="cd97e-104">Dämpfungs- und Spotlight-Faktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-104">Attenuation and spotlight factor</span></span>


<span data-ttu-id="cd97e-105">Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben.</span><span class="sxs-lookup"><span data-stu-id="cd97e-105">The diffuse and specular lighting components of the global illumination equation contain terms that describe light attenuation and the spotlight cone.</span></span> <span data-ttu-id="cd97e-106">Diese Begriffe werden nachfolgend beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cd97e-106">These terms are described below.</span></span>

## <a name="span-idattenuationspanspan-idattenuationspanspan-idattenuationspanattenuation"></a><span data-ttu-id="cd97e-107"><span id="Attenuation"></span><span id="attenuation"></span><span id="ATTENUATION"></span>Dämpfung</span><span class="sxs-lookup"><span data-stu-id="cd97e-107"><span id="Attenuation"></span><span id="attenuation"></span><span id="ATTENUATION"></span>Attenuation</span></span>


<span data-ttu-id="cd97e-108">Die Lichtdämpfung hängt vom Typ des Lichts und dem Abstand zwischen dem Licht und der Vertexposition ab.</span><span class="sxs-lookup"><span data-stu-id="cd97e-108">The attenuation of a light depends on the type of light and the distance between the light and the vertex position.</span></span> <span data-ttu-id="cd97e-109">Verwenden Sie eine der folgenden Formeln, um die Dämpfung zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="cd97e-109">To calculate attenuation, use one of the following equations.</span></span>

<span data-ttu-id="cd97e-110">Atten = 1/( att0<sub>i</sub> + att1<sub>i</sub> \* d + att2<sub>i</sub> \* d²)</span><span class="sxs-lookup"><span data-stu-id="cd97e-110">Atten = 1/( att0<sub>i</sub> + att1<sub>i</sub> \* d + att2<sub>i</sub> \* d²)</span></span>

<span data-ttu-id="cd97e-111">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="cd97e-111">Where:</span></span>

| <span data-ttu-id="cd97e-112">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd97e-112">Parameter</span></span>        | <span data-ttu-id="cd97e-113">Standardwert</span><span class="sxs-lookup"><span data-stu-id="cd97e-113">Default value</span></span> | <span data-ttu-id="cd97e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="cd97e-114">Type</span></span>           | <span data-ttu-id="cd97e-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd97e-115">Description</span></span>                                     | <span data-ttu-id="cd97e-116">Bereich</span><span class="sxs-lookup"><span data-stu-id="cd97e-116">Range</span></span>          |
|------------------|---------------|----------------|-------------------------------------------------|----------------|
| <span data-ttu-id="cd97e-117">att0<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-117">att0<sub>i</sub></span></span> | <span data-ttu-id="cd97e-118">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-118">0.0</span></span>           | <span data-ttu-id="cd97e-119">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-119">Floating point</span></span> | <span data-ttu-id="cd97e-120">Konstanter Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-120">Constant attenuation factor</span></span>                     | <span data-ttu-id="cd97e-121">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="cd97e-121">0 to +infinity</span></span> |
| <span data-ttu-id="cd97e-122">att1<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-122">att1<sub>i</sub></span></span> | <span data-ttu-id="cd97e-123">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-123">0.0</span></span>           | <span data-ttu-id="cd97e-124">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-124">Floating point</span></span> | <span data-ttu-id="cd97e-125">Linearer Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-125">Linear attenuation factor</span></span>                       | <span data-ttu-id="cd97e-126">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="cd97e-126">0 to +infinity</span></span> |
| <span data-ttu-id="cd97e-127">att2<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-127">att2<sub>i</sub></span></span> | <span data-ttu-id="cd97e-128">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-128">0.0</span></span>           | <span data-ttu-id="cd97e-129">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-129">Floating point</span></span> | <span data-ttu-id="cd97e-130">Quadratischer Dämpfungsfaktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-130">Quadratic attenuation factor</span></span>                    | <span data-ttu-id="cd97e-131">0 bis +unendlich</span><span class="sxs-lookup"><span data-stu-id="cd97e-131">0 to +infinity</span></span> |
| <span data-ttu-id="cd97e-132">d</span><span class="sxs-lookup"><span data-stu-id="cd97e-132">d</span></span>                | <span data-ttu-id="cd97e-133">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-133">N/A</span></span>           | <span data-ttu-id="cd97e-134">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-134">Floating point</span></span> | <span data-ttu-id="cd97e-135">Abstand zwischen Vertexposition und Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="cd97e-135">Distance from vertex position to light position</span></span> | <span data-ttu-id="cd97e-136">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-136">N/A</span></span>            |

 

-   <span data-ttu-id="cd97e-137">Dämpfung = 1, wenn das Licht ein gerichtetes Licht ist.</span><span class="sxs-lookup"><span data-stu-id="cd97e-137">Atten = 1, if the light is a directional light.</span></span>
-   <span data-ttu-id="cd97e-138">Dämpfung = 0, wenn der Abstand zwischen Licht und Vertex die Reichweite des Lichts überschreitet.</span><span class="sxs-lookup"><span data-stu-id="cd97e-138">Atten = 0, if the distance between the light and the vertex exceeds the light's range.</span></span>

<span data-ttu-id="cd97e-139">Der Abstand zwischen Lichtquelle und Vertexposition ist immer positiv.</span><span class="sxs-lookup"><span data-stu-id="cd97e-139">The distance between the light and the vertex position is always positive.</span></span>

<span data-ttu-id="cd97e-140">d = | L<sub>dir</sub> |</span><span class="sxs-lookup"><span data-stu-id="cd97e-140">d = | L<sub>dir</sub> |</span></span>

<span data-ttu-id="cd97e-141">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="cd97e-141">Where:</span></span>

| <span data-ttu-id="cd97e-142">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd97e-142">Parameter</span></span>       | <span data-ttu-id="cd97e-143">Standardwert</span><span class="sxs-lookup"><span data-stu-id="cd97e-143">Default value</span></span> | <span data-ttu-id="cd97e-144">Typ</span><span class="sxs-lookup"><span data-stu-id="cd97e-144">Type</span></span>                                             | <span data-ttu-id="cd97e-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd97e-145">Description</span></span>                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="cd97e-146">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-146">L<sub>dir</sub></span></span> | <span data-ttu-id="cd97e-147">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-147">N/A</span></span>           | <span data-ttu-id="cd97e-148">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="cd97e-148">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="cd97e-149">Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="cd97e-149">Direction vector from vertex position to the light position</span></span> |

 

<span data-ttu-id="cd97e-150">Wenn d größer als die Reichweite des Lichts ist, nimmt Direct3D keine weiteren abnehmenden Berechnungen vor und wendet keine Effekte von der Lichtquelle bis zum Vertex an.</span><span class="sxs-lookup"><span data-stu-id="cd97e-150">If d is greater than the light's range, Direct3D makes no further attenuation calculations and applies no effects from the light to the vertex.</span></span>

<span data-ttu-id="cd97e-151">Die Dämpfungskonstanten fungieren in der Formel als Koeffizient – Sie können eine Vielzahl von Dämpfungskurven erstellen, indem Sie diese einfach anpassen.</span><span class="sxs-lookup"><span data-stu-id="cd97e-151">The attenuation constants act as coefficients in the formula - you can produce a variety of attenuation curves by making simple adjustments to them.</span></span> <span data-ttu-id="cd97e-152">Sie können Dämpfung1 auf 1,0 einstellen, um ein Licht zu erstellen, das sich nicht dämpfen lässt aber trotzdem von der Reichweite begrenzt ist. Sie können ebenfalls mit verschiedenen Werten experimentieren, um verschiedene Dämpfungseffekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="cd97e-152">You can set Attenuation1 to 1.0 to create a light that doesn't attenuate but is still limited by range, or you can experiment with different values to achieve various attenuation effects.</span></span>

<span data-ttu-id="cd97e-153">Die Dämpfung bei maximaler Reichweite des Lichts ist 0,0.</span><span class="sxs-lookup"><span data-stu-id="cd97e-153">The attenuation at the maximum range of the light is not 0.0.</span></span> <span data-ttu-id="cd97e-154">Um zu verhindern, dass Lichter plötzlich angezeigt werden, wenn sie sich in Reichweite des Lichts befinden, kann eine Anwendung die Reichweite des Lichts erhöhen.</span><span class="sxs-lookup"><span data-stu-id="cd97e-154">To prevent lights from suddenly appearing when they are at the light range, an application can increase the light range.</span></span> <span data-ttu-id="cd97e-155">Die Anwendung kann ebenfalls Dämpfungskonstanten so einrichten, dass der Dämpfungsfaktor nahe an der Reichweite 0,0 des Lichts liegt.</span><span class="sxs-lookup"><span data-stu-id="cd97e-155">Or, the application can set up attenuation constants so that the attenuation factor is close to 0.0 at the light range.</span></span> <span data-ttu-id="cd97e-156">Der Dämpfungswert wird mit den roten, grünen und blauen Komponenten der Farbe des Lichts multipliziert, um die Intensität des Lichts als Faktor der Distanz zu skalieren, die das Licht bis zum Vertex zurücklegt.</span><span class="sxs-lookup"><span data-stu-id="cd97e-156">The attenuation value is multiplied by the red, green, and blue components of the light's color to scale the light's intensity as a factor of the distance light travels to a vertex.</span></span>

## <a name="span-idspotlight-factorspanspan-idspotlight-factorspanspan-idspotlight-factorspanspotlight-factor"></a><span data-ttu-id="cd97e-157"><span id="Spotlight-Factor"></span><span id="spotlight-factor"></span><span id="SPOTLIGHT-FACTOR"></span>Spotlight-Faktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-157"><span id="Spotlight-Factor"></span><span id="spotlight-factor"></span><span id="SPOTLIGHT-FACTOR"></span>Spotlight Factor</span></span>


<span data-ttu-id="cd97e-158">Die folgende Gleichung legt den Spotlight-Faktor fest.</span><span class="sxs-lookup"><span data-stu-id="cd97e-158">The following equation specifies the spotlight factor.</span></span>

![Gleichung für den Spotlight-Faktor](images/dx8light9.png)

| <span data-ttu-id="cd97e-160">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd97e-160">Parameter</span></span>         | <span data-ttu-id="cd97e-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="cd97e-161">Default value</span></span> | <span data-ttu-id="cd97e-162">Typ</span><span class="sxs-lookup"><span data-stu-id="cd97e-162">Type</span></span>           | <span data-ttu-id="cd97e-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd97e-163">Description</span></span>                              | <span data-ttu-id="cd97e-164">Bereich</span><span class="sxs-lookup"><span data-stu-id="cd97e-164">Range</span></span>                    |
|-------------------|---------------|----------------|------------------------------------------|--------------------------|
| <span data-ttu-id="cd97e-165">rho<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-165">rho<sub>i</sub></span></span>   | <span data-ttu-id="cd97e-166">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-166">N/A</span></span>           | <span data-ttu-id="cd97e-167">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-167">Floating point</span></span> | <span data-ttu-id="cd97e-168">Kosinus(Winkel) für Spotlight i</span><span class="sxs-lookup"><span data-stu-id="cd97e-168">cosine(angle) for spotlight i</span></span>            | <span data-ttu-id="cd97e-169">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-169">N/A</span></span>                      |
| <span data-ttu-id="cd97e-170">phi<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-170">phi<sub>i</sub></span></span>   | <span data-ttu-id="cd97e-171">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-171">0.0</span></span>           | <span data-ttu-id="cd97e-172">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-172">Floating point</span></span> | <span data-ttu-id="cd97e-173">Halbschatten-Winkel für Spotlight i nach Bogenmaß</span><span class="sxs-lookup"><span data-stu-id="cd97e-173">Penumbra angle of spotlight i in radians</span></span> | <span data-ttu-id="cd97e-174">\[theta<sub>i</sub>, pi)</span><span class="sxs-lookup"><span data-stu-id="cd97e-174">\[theta<sub>i</sub>, pi)</span></span> |
| <span data-ttu-id="cd97e-175">theta<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-175">theta<sub>i</sub></span></span> | <span data-ttu-id="cd97e-176">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-176">0.0</span></span>           | <span data-ttu-id="cd97e-177">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-177">Floating point</span></span> | <span data-ttu-id="cd97e-178">Kernschatten-Winkel für Spotlight i nach Bogenmaß</span><span class="sxs-lookup"><span data-stu-id="cd97e-178">Umbra angle of spotlight i in radians</span></span>    | <span data-ttu-id="cd97e-179">\[0, pi)</span><span class="sxs-lookup"><span data-stu-id="cd97e-179">\[0, pi)</span></span>                 |
| <span data-ttu-id="cd97e-180">Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="cd97e-180">falloff</span></span>           | <span data-ttu-id="cd97e-181">0,0</span><span class="sxs-lookup"><span data-stu-id="cd97e-181">0.0</span></span>           | <span data-ttu-id="cd97e-182">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="cd97e-182">Floating point</span></span> | <span data-ttu-id="cd97e-183">Farbverlaufsfaktor</span><span class="sxs-lookup"><span data-stu-id="cd97e-183">Falloff factor</span></span>                           | <span data-ttu-id="cd97e-184">(-unendlich +unendlich)</span><span class="sxs-lookup"><span data-stu-id="cd97e-184">(-infinity, +infinity)</span></span>   |

 

<span data-ttu-id="cd97e-185">Dabei gilt:</span><span class="sxs-lookup"><span data-stu-id="cd97e-185">Where:</span></span>

<span data-ttu-id="cd97e-186">rho = norm(L<sub>dcs</sub>)<sup>.</sup>norm(L<sub>dir</sub>)</span><span class="sxs-lookup"><span data-stu-id="cd97e-186">rho = norm(L<sub>dcs</sub>)<sup>.</sup>norm(L<sub>dir</sub>)</span></span>

<span data-ttu-id="cd97e-187">und</span><span class="sxs-lookup"><span data-stu-id="cd97e-187">and:</span></span>

| <span data-ttu-id="cd97e-188">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd97e-188">Parameter</span></span>       | <span data-ttu-id="cd97e-189">Standardwert</span><span class="sxs-lookup"><span data-stu-id="cd97e-189">Default value</span></span> | <span data-ttu-id="cd97e-190">Typ</span><span class="sxs-lookup"><span data-stu-id="cd97e-190">Type</span></span>                                             | <span data-ttu-id="cd97e-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cd97e-191">Description</span></span>                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="cd97e-192">L<sub>dcs</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-192">L<sub>dcs</sub></span></span> | <span data-ttu-id="cd97e-193">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-193">N/A</span></span>           | <span data-ttu-id="cd97e-194">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="cd97e-194">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="cd97e-195">Der negativen Wert der Lichteinfallsrichtung im Kamerabereich</span><span class="sxs-lookup"><span data-stu-id="cd97e-195">The negative of the light direction in camera space</span></span>         |
| <span data-ttu-id="cd97e-196">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="cd97e-196">L<sub>dir</sub></span></span> | <span data-ttu-id="cd97e-197">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="cd97e-197">N/A</span></span>           | <span data-ttu-id="cd97e-198">3D-Vektor mit X-, Y- und Z-Gleitkommawerten</span><span class="sxs-lookup"><span data-stu-id="cd97e-198">3D vector with x, y, and z floating-point values</span></span> | <span data-ttu-id="cd97e-199">Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="cd97e-199">Direction vector from vertex position to the light position</span></span> |

 

<span data-ttu-id="cd97e-200">Nach dem Berechnen der Lichtdämpfung berücksichtigt Direct3D auch eventuelle Spotlight-Effekte, den vom Licht von der Oberfläche reflektierten Winkel und den Reflexionsgrad des aktuellen Materials, um die diffusen und Glanzlichtkomponenten für den Vertex zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="cd97e-200">After computing the light attenuation, to calculate the diffuse and specular components for the vertex, Direct3D also considers spotlight effects if applicable, the angle that the light reflects from a surface, and the reflectance of the current material.</span></span> <span data-ttu-id="cd97e-201">Siehe auch Spotlight unter [Lichttypen](light-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd97e-201">In [Light types](light-types.md), see "Spotlight".</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="cd97e-202"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cd97e-202"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="cd97e-203">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="cd97e-203">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




