---
title: Spiegelbeleuchtung
description: Spiegelbeleuchtung bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird.
ms.assetid: 71F87137-B00F-48CE-8E6A-F98A139A742A
keywords:
- Spiegelbeleuchtung
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7f28f1f46cfd34ee1aab614c57dc99019dbd6111
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8691784"
---
# <a name="specular-lighting"></a><span data-ttu-id="d26b8-104">Spiegelbeleuchtung</span><span class="sxs-lookup"><span data-stu-id="d26b8-104">Specular lighting</span></span>


<span data-ttu-id="d26b8-105">*Spiegelnde Beleuchtung* bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird.</span><span class="sxs-lookup"><span data-stu-id="d26b8-105">*Specular lighting* identifies the bright specular highlights that occur when light hits an object surface and reflects back toward the camera.</span></span> <span data-ttu-id="d26b8-106">Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab.</span><span class="sxs-lookup"><span data-stu-id="d26b8-106">Specular lighting is more intense than diffuse light and falls off more rapidly across the object surface.</span></span> <span data-ttu-id="d26b8-107">Die Berechnung der Spiegelbeleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung. Der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.</span><span class="sxs-lookup"><span data-stu-id="d26b8-107">It takes longer to calculate specular lighting than diffuse lighting, however the benefit of using it is that it adds significant detail to a surface.</span></span>

<span data-ttu-id="d26b8-108">Für das Modellieren einer spiegelnden Reflektion muss dem System die Bewegungsrichtung des Lichts und der Blickwinkel des Betrachters bekannt sein.</span><span class="sxs-lookup"><span data-stu-id="d26b8-108">Modeling specular reflection requires that the system know in what direction light is traveling and the direction to the viewer's eye.</span></span> <span data-ttu-id="d26b8-109">Das System verwendet eine vereinfachte Version des Phong-Beleuchtungsmodells, das mit einer Winkelhalbierenden die Intensität der spiegelnden Reflektion angleicht.</span><span class="sxs-lookup"><span data-stu-id="d26b8-109">The system uses a simplified version of the Phong specular-reflection model, which employs a halfway vector to approximate the intensity of specular reflection.</span></span>

<span data-ttu-id="d26b8-110">Für den Standardzustand der Beleuchtung werden keine Glanzlichter berechnet.</span><span class="sxs-lookup"><span data-stu-id="d26b8-110">The default lighting state does not calculate specular highlights.</span></span>

## <a name="span-idspecularlightingequationspanspan-idspecularlightingequationspanspan-idspecularlightingequationspanspecular-lighting-equation"></a><span data-ttu-id="d26b8-111"><span id="Specular_Lighting_Equation"></span><span id="specular_lighting_equation"></span><span id="SPECULAR_LIGHTING_EQUATION"></span>Formel der Spiegelbeleuchtung</span><span class="sxs-lookup"><span data-stu-id="d26b8-111"><span id="Specular_Lighting_Equation"></span><span id="specular_lighting_equation"></span><span id="SPECULAR_LIGHTING_EQUATION"></span>Specular Lighting Equation</span></span>


<span data-ttu-id="d26b8-112">Spiegelbeleuchtung wird durch die folgende Formel beschrieben:</span><span class="sxs-lookup"><span data-stu-id="d26b8-112">Specular Lighting is described by the following equation.</span></span>

|                                                                             |
|-----------------------------------------------------------------------------|
| <span data-ttu-id="d26b8-113">Spiegelbeleuchtung = Cₛ \* Summe\[Lₛ \* (N · H)<sup>P</sup> \* Dämpfung \* Spotlight\]</span><span class="sxs-lookup"><span data-stu-id="d26b8-113">Specular Lighting = Cₛ \* sum\[Lₛ \* (N · H)<sup>P</sup> \* Atten \* Spot\]</span></span> |

 

<span data-ttu-id="d26b8-114">Variablen, Typen und Bereiche:</span><span class="sxs-lookup"><span data-stu-id="d26b8-114">The variables, their types, and their ranges are as follows:</span></span>

| <span data-ttu-id="d26b8-115">Parameter</span><span class="sxs-lookup"><span data-stu-id="d26b8-115">Parameter</span></span>    | <span data-ttu-id="d26b8-116">Standardwert</span><span class="sxs-lookup"><span data-stu-id="d26b8-116">Default value</span></span> | <span data-ttu-id="d26b8-117">Typ</span><span class="sxs-lookup"><span data-stu-id="d26b8-117">Type</span></span>                                                             | <span data-ttu-id="d26b8-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d26b8-118">Description</span></span>                                                                                            |
|--------------|---------------|------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d26b8-119">Cₛ</span><span class="sxs-lookup"><span data-stu-id="d26b8-119">Cₛ</span></span>           | <span data-ttu-id="d26b8-120">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="d26b8-120">(0,0,0,0)</span></span>     | <span data-ttu-id="d26b8-121">Rot, Grün, Blau und Alpha-Transparenz (Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-121">Red, green, blue, and alpha transparency (floating-point values)</span></span> | <span data-ttu-id="d26b8-122">Glanzfarbe</span><span class="sxs-lookup"><span data-stu-id="d26b8-122">Specular color.</span></span>                                                                                        |
| <span data-ttu-id="d26b8-123">Summe</span><span class="sxs-lookup"><span data-stu-id="d26b8-123">sum</span></span>          | <span data-ttu-id="d26b8-124">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d26b8-124">N/A</span></span>           | <span data-ttu-id="d26b8-125">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-125">N/A</span></span>                                                              | <span data-ttu-id="d26b8-126">Summe aller Glanzkomponenten des Lichts</span><span class="sxs-lookup"><span data-stu-id="d26b8-126">Summation of each light's specular component.</span></span>                                                          |
| <span data-ttu-id="d26b8-127">N</span><span class="sxs-lookup"><span data-stu-id="d26b8-127">N</span></span>            | <span data-ttu-id="d26b8-128">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d26b8-128">N/A</span></span>           | <span data-ttu-id="d26b8-129">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-129">3D vector (x, y, and z floating-point values)</span></span>                    | <span data-ttu-id="d26b8-130">Vertexnormale</span><span class="sxs-lookup"><span data-stu-id="d26b8-130">Vertex normal.</span></span>                                                                                         |
| <span data-ttu-id="d26b8-131">H</span><span class="sxs-lookup"><span data-stu-id="d26b8-131">H</span></span>            | <span data-ttu-id="d26b8-132">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-132">N/A</span></span>           | <span data-ttu-id="d26b8-133">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-133">3D vector (x, y, and z floating-point values)</span></span>                    | <span data-ttu-id="d26b8-134">Winkelhalbierende.</span><span class="sxs-lookup"><span data-stu-id="d26b8-134">Half way vector.</span></span> <span data-ttu-id="d26b8-135">Siehe den Abschnitt zur Winkelhalbierenden</span><span class="sxs-lookup"><span data-stu-id="d26b8-135">See the section on the halfway vector.</span></span>                                                |
| <sup><span data-ttu-id="d26b8-136">P</span><span class="sxs-lookup"><span data-stu-id="d26b8-136">P</span></span></sup> | <span data-ttu-id="d26b8-137">0,0</span><span class="sxs-lookup"><span data-stu-id="d26b8-137">0.0</span></span>           | <span data-ttu-id="d26b8-138">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="d26b8-138">Floating point</span></span>                                                   | <span data-ttu-id="d26b8-139">Stärke der spiegelnden Reflektion.</span><span class="sxs-lookup"><span data-stu-id="d26b8-139">Specular reflection power.</span></span> <span data-ttu-id="d26b8-140">Von 0 bis plus unendlich</span><span class="sxs-lookup"><span data-stu-id="d26b8-140">Range is 0 to +infinity</span></span>                                                     |
| <span data-ttu-id="d26b8-141">Lₛ</span><span class="sxs-lookup"><span data-stu-id="d26b8-141">Lₛ</span></span>           | <span data-ttu-id="d26b8-142">(0,0,0,0)</span><span class="sxs-lookup"><span data-stu-id="d26b8-142">(0,0,0,0)</span></span>     | <span data-ttu-id="d26b8-143">Rot, Grün, Blau und Alpha-Transparenz (Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-143">Red, green, blue, and alpha transparency (floating-point values)</span></span> | <span data-ttu-id="d26b8-144">Glanzfarbe des Lichts</span><span class="sxs-lookup"><span data-stu-id="d26b8-144">Light specular color.</span></span>                                                                                  |
| <span data-ttu-id="d26b8-145">Dämpfung</span><span class="sxs-lookup"><span data-stu-id="d26b8-145">Atten</span></span>        | <span data-ttu-id="d26b8-146">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-146">N/A</span></span>           | <span data-ttu-id="d26b8-147">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="d26b8-147">Floating point</span></span>                                                   | <span data-ttu-id="d26b8-148">Lichtdämpfungswert.</span><span class="sxs-lookup"><span data-stu-id="d26b8-148">Light attenuation value.</span></span> <span data-ttu-id="d26b8-149">Siehe [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md)</span><span class="sxs-lookup"><span data-stu-id="d26b8-149">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span> |
| <span data-ttu-id="d26b8-150">Spotlight</span><span class="sxs-lookup"><span data-stu-id="d26b8-150">Spot</span></span>         | <span data-ttu-id="d26b8-151">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-151">N/A</span></span>           | <span data-ttu-id="d26b8-152">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="d26b8-152">Floating point</span></span>                                                   | <span data-ttu-id="d26b8-153">Spotlight-Faktor.</span><span class="sxs-lookup"><span data-stu-id="d26b8-153">Spotlight factor.</span></span> <span data-ttu-id="d26b8-154">Siehe [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md)</span><span class="sxs-lookup"><span data-stu-id="d26b8-154">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span>        |

 

<span data-ttu-id="d26b8-155">Cₛ ist einer der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="d26b8-155">The value for Cₛ is either:</span></span>

-   <span data-ttu-id="d26b8-156">Vertexfarbe1, wenn die Glanzmaterialquelle die diffuse Vertexfarbe ist und die erste Vertexfarbe in der Vertexdeklaration angegeben ist</span><span class="sxs-lookup"><span data-stu-id="d26b8-156">vertex color 1, if the specular material source is the diffuse vertex color, and the first vertex color is supplied in the vertex declaration.</span></span>
-   <span data-ttu-id="d26b8-157">Vertexfarbe2, wenn die Glanzmaterialquelle die Glanzvertexfarbe ist und die zweite Vertexfarbe in der Vertexdeklaration angegeben ist</span><span class="sxs-lookup"><span data-stu-id="d26b8-157">vertex color 2, if specular material source is the specular vertex color, and the second vertex color is supplied in the vertex declaration.</span></span>
-   <span data-ttu-id="d26b8-158">Materialglanzfarbe</span><span class="sxs-lookup"><span data-stu-id="d26b8-158">material specular color</span></span>

<span data-ttu-id="d26b8-159">**Hinweis:**  Wenn Option glanzmaterialquelle verwendet wird und die Vertexfarbe nicht angegeben, wird die materialglanzfarbe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d26b8-159">**Note** If either specular material source option is used and the vertex color is not provided, then the material specular color is used.</span></span>

 

<span data-ttu-id="d26b8-160">Nachdem alle Lichter verarbeitet und getrennt interpoliert wurden, sollten Glanzkomponenten auf Werte zwischen0 bis255 festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="d26b8-160">Specular components are clamped to be from 0 to 255, after all lights are processed and interpolated separately.</span></span>

## <a name="span-idthehalfwayvectorspanspan-idthehalfwayvectorspanspan-idthehalfwayvectorspanthe-halfway-vector"></a><span data-ttu-id="d26b8-161"><span id="The_Halfway_Vector"></span><span id="the_halfway_vector"></span><span id="THE_HALFWAY_VECTOR"></span>Die Winkelhalbierende</span><span class="sxs-lookup"><span data-stu-id="d26b8-161"><span id="The_Halfway_Vector"></span><span id="the_halfway_vector"></span><span id="THE_HALFWAY_VECTOR"></span>The Halfway Vector</span></span>


<span data-ttu-id="d26b8-162">Die Winkelhalbierende (H) befindet sich in der Mitte zwischen zwei Vektoren: dem Vektor von einem Objektvertex zur Lichtquelle und dem Vektor von einem Objektvertex zur Kameraposition.</span><span class="sxs-lookup"><span data-stu-id="d26b8-162">The halfway vector (H) exists midway between two vectors: the vector from an object vertex to the light source, and the vector from an object vertex to the camera position.</span></span> <span data-ttu-id="d26b8-163">Direct3D bietet zwei Möglichkeiten zur Berechnung der Winkelhalbierenden.</span><span class="sxs-lookup"><span data-stu-id="d26b8-163">Direct3D provides two ways to compute the halfway vector.</span></span> <span data-ttu-id="d26b8-164">Wenn Glanzlichter relativ zur Kamera aktiviert sind (anstelle von orthogonalen Glanzlichtern), berechnet das System die Winkelhalbierende anhand der Position der Kamera und der Position des Vertex zusammen mit dem Richtungsvektor des Lichts.</span><span class="sxs-lookup"><span data-stu-id="d26b8-164">When camera-relative specular highlights is enabled (instead of orthogonal specular highlights), the system calculates the halfway vector using the position of the camera and the position of the vertex, along with the light's direction vector.</span></span> <span data-ttu-id="d26b8-165">Die folgende Formel veranschaulicht dies:</span><span class="sxs-lookup"><span data-stu-id="d26b8-165">The following formula illustrates this.</span></span>

|                                           |
|-------------------------------------------|
| <span data-ttu-id="d26b8-166">H = norm(norm(Cₚ - Vₚ) + L<sub>dir</sub>)</span><span class="sxs-lookup"><span data-stu-id="d26b8-166">H = norm(norm(Cₚ - Vₚ) + L<sub>dir</sub>)</span></span> |

 

| <span data-ttu-id="d26b8-167">Parameter</span><span class="sxs-lookup"><span data-stu-id="d26b8-167">Parameter</span></span>       | <span data-ttu-id="d26b8-168">Standardwert</span><span class="sxs-lookup"><span data-stu-id="d26b8-168">Default value</span></span> | <span data-ttu-id="d26b8-169">Typ</span><span class="sxs-lookup"><span data-stu-id="d26b8-169">Type</span></span>                                          | <span data-ttu-id="d26b8-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d26b8-170">Description</span></span>                                                  |
|-----------------|---------------|-----------------------------------------------|--------------------------------------------------------------|
| <span data-ttu-id="d26b8-171">Cₚ</span><span class="sxs-lookup"><span data-stu-id="d26b8-171">Cₚ</span></span>              | <span data-ttu-id="d26b8-172">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-172">N/A</span></span>           | <span data-ttu-id="d26b8-173">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-173">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="d26b8-174">Kameraposition</span><span class="sxs-lookup"><span data-stu-id="d26b8-174">Camera position.</span></span>                                             |
| <span data-ttu-id="d26b8-175">Vₚ</span><span class="sxs-lookup"><span data-stu-id="d26b8-175">Vₚ</span></span>              | <span data-ttu-id="d26b8-176">N/V</span><span class="sxs-lookup"><span data-stu-id="d26b8-176">N/A</span></span>           | <span data-ttu-id="d26b8-177">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-177">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="d26b8-178">Vertexposition</span><span class="sxs-lookup"><span data-stu-id="d26b8-178">Vertex position.</span></span>                                             |
| <span data-ttu-id="d26b8-179">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="d26b8-179">L<sub>dir</sub></span></span> | <span data-ttu-id="d26b8-180">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d26b8-180">N/A</span></span>           | <span data-ttu-id="d26b8-181">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="d26b8-181">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="d26b8-182">Richtungsvektor von der Vertexposition zur Lichtposition</span><span class="sxs-lookup"><span data-stu-id="d26b8-182">Direction vector from vertex position to the light position.</span></span> |

 

<span data-ttu-id="d26b8-183">Die Bestimmung der Winkelhalbierenden auf diese Weise kann rechenintensiv sein.</span><span class="sxs-lookup"><span data-stu-id="d26b8-183">Determining the halfway vector in this manner can be computationally intensive.</span></span> <span data-ttu-id="d26b8-184">Als Alternative wird bei der Verwendung orthogonaler Glanzlichter (anstelle von Glanzlichtern relativ zur Kamera) das System angewiesen, sich so zu verhalten, als ob sich der Blickpunkt unendlich entfernt auf der Z-Achse befinden würde.</span><span class="sxs-lookup"><span data-stu-id="d26b8-184">As an alternative, using orthogonal specular highlights (instead of camera-relative specular highlights) instructs the system to act as though the viewpoint is infinitely distant on the z-axis.</span></span> <span data-ttu-id="d26b8-185">Die Formel für diese Berechnung sieht folgendermaßen aus:</span><span class="sxs-lookup"><span data-stu-id="d26b8-185">This is reflected in the following formula.</span></span>

|                                     |
|-------------------------------------|
| <span data-ttu-id="d26b8-186">H = norm((0,0,1) + L<sub>dir</sub>)</span><span class="sxs-lookup"><span data-stu-id="d26b8-186">H = norm((0,0,1) + L<sub>dir</sub>)</span></span> |

 

<span data-ttu-id="d26b8-187">Diese Einstellung ist weniger rechenintensiv, aber auch viel unpräziser, daher sollte sie am besten in Anwendungen mit orthogonalen Projektion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d26b8-187">This setting is less computationally intensive, but much less accurate, so it is best used by applications that use orthogonal projection.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="d26b8-188"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="d26b8-188"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="d26b8-189">In diesem Beispiel wird ein Objekt mit der Glanzlichtfarbe der Szene und einer Materialglanzfarbe eingefärbt.</span><span class="sxs-lookup"><span data-stu-id="d26b8-189">In this example, the object is colored using the scene specular light color and a material specular color.</span></span>

<span data-ttu-id="d26b8-190">Gemäß der Gleichung ist die resultierende Farbe für die Objektvertices eine Kombination aus der Materialfarbe und der Lichtfarbe.</span><span class="sxs-lookup"><span data-stu-id="d26b8-190">According to the equation, the resulting color for the object vertices is a combination of the material color and the light color.</span></span>

<span data-ttu-id="d26b8-191">Die beiden folgenden Abbildungen zeigen die Glanzmaterialfarbe grau und die Glanzlichtfarbe weiß.</span><span class="sxs-lookup"><span data-stu-id="d26b8-191">The following two illustration show the specular material color, which is gray, and the specular light color, which is white.</span></span>

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer weißen Kugel](images/lightwhite.jpg)

<span data-ttu-id="d26b8-194">Das resultierende Glanzlicht ist in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d26b8-194">The resulting specular highlight is shown in the following illustration.</span></span>

![Abbildung des Glanzlichts](images/lights.jpg)

<span data-ttu-id="d26b8-196">Durch Kombination des Glanzlichts mit der Umgebungs- und diffusen Beleuchtung wird ein Ergebnis wie in der folgenden Abbildung erzeugt.</span><span class="sxs-lookup"><span data-stu-id="d26b8-196">Combining the specular highlight with the ambient and diffuse lighting produces the following illustration.</span></span> <span data-ttu-id="d26b8-197">Die Anwendung aller drei Beleuchtungsarten liefert ein sehr realistisches Objekt.</span><span class="sxs-lookup"><span data-stu-id="d26b8-197">With all three types of lighting applied, this more clearly resembles a realistic object.</span></span>

![Abbildung der Kombination des Glanzlichts, des Umgebungslichts und des diffusen Lichts](images/lightads.jpg)

<span data-ttu-id="d26b8-199">Für die Spiegelbeleuchtung ist eine intensivere Berechnung als für die diffuse Beleuchtung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d26b8-199">Specular lighting is more intensive to calculate than diffuse lighting.</span></span> <span data-ttu-id="d26b8-200">Sie wird normalerweise verwendet, um visuelle Hinweise zu dem Oberflächenmaterial zu geben.</span><span class="sxs-lookup"><span data-stu-id="d26b8-200">It is typically used to provide visual clues about the surface material.</span></span> <span data-ttu-id="d26b8-201">Das Glanzlicht ändert sich in Größe und Farbe entsprechend dem Material der Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="d26b8-201">The specular highlight varies in size and color with the material of the surface.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="d26b8-202"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d26b8-202"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="d26b8-203">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="d26b8-203">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




