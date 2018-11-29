---
title: Beleuchtungsmathematik
description: Das Direct3D-Beleuchtungsmodell deckt Umgebungs-, diffuse, spiegelnde und ausstrahlende Beleuchtung ab. Dies bietet eine ausreichende Flexibilität zum Lösen einer breiten Palette an Beleuchtungssituationen. Die Gesamtmenge an Licht in einer Szene wird als globale Beleuchtung bezeichnet.
ms.assetid: D0521F56-050D-4EDF-9BD1-34748E94B873
keywords:
- Beleuchtungsmathematik
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 38a65a3532fe401f31fbf0da656aff1a141fa71a
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8191587"
---
# <a name="mathematics-of-lighting"></a><span data-ttu-id="deaf0-106">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="deaf0-106">Mathematics of lighting</span></span>


<span data-ttu-id="deaf0-107">Das Direct3D-Beleuchtungsmodell deckt Umgebungs-, diffuse, spiegelnde und ausstrahlende Beleuchtung ab.</span><span class="sxs-lookup"><span data-stu-id="deaf0-107">The Direct3D Light Model covers ambient, diffuse, specular, and emissive lighting.</span></span> <span data-ttu-id="deaf0-108">Dies bietet eine ausreichende Flexibilität zum Lösen einer breiten Palette an Beleuchtungssituationen.</span><span class="sxs-lookup"><span data-stu-id="deaf0-108">This is enough flexibility to solve a wide range of lighting situations.</span></span> <span data-ttu-id="deaf0-109">Die Gesamtmenge an Licht in einer Szene wird als *globale Beleuchtung* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="deaf0-109">The total amount of light in a scene is called the *global illumination*.</span></span>

<span data-ttu-id="deaf0-110">Die globale Beleuchtung wird wie folgt berechnet:</span><span class="sxs-lookup"><span data-stu-id="deaf0-110">The global illumination is computed as follows:</span></span>

```
Global Illumination = Ambient Light + Diffuse Light + Specular Light + Emissive Light 
```

<span data-ttu-id="deaf0-111">[Umgebungsbeleuchtung](ambient-lighting.md) ist konstante Beleuchtung.</span><span class="sxs-lookup"><span data-stu-id="deaf0-111">[Ambient lighting](ambient-lighting.md) is constant lighting.</span></span> <span data-ttu-id="deaf0-112">Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch.</span><span class="sxs-lookup"><span data-stu-id="deaf0-112">Ambient lighting is constant in all directions and it colors all pixels of an object the same.</span></span> <span data-ttu-id="deaf0-113">Sie lässt sich schnell berechnen, bewirkt jedoch, dass Objekte flach und unrealistisch aussehen.</span><span class="sxs-lookup"><span data-stu-id="deaf0-113">It is fast to calculate but leaves objects looking flat and unrealistic.</span></span>

<span data-ttu-id="deaf0-114">[Diffuse Beleuchtung](diffuse-lighting.md) hängt sowohl von der Richtung des Lichts als auch von der Flächennormalen des Objektes ab.</span><span class="sxs-lookup"><span data-stu-id="deaf0-114">[Diffuse lighting](diffuse-lighting.md) depends on both the light direction and the object surface normal.</span></span> <span data-ttu-id="deaf0-115">Diffuse Beleuchtung ist auf der Oberfläche eines Objekts durch die Änderung der Richtung des Lichts und den sich ändernden Oberflächenzahlvektor unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="deaf0-115">Diffuse lighting varies across the surface of an object as a result of the changing light direction and the changing surface numeral vector.</span></span> <span data-ttu-id="deaf0-116">Es dauert länger, diffuse Beleuchtung zu berechnen, da sie sich für jeden Eckpunkt des Objektes ändert; der Vorteil der Verwendung liegt jedoch darin, dass sie Objekten einen Schatten und eine dreidimensionale (3D) Tiefe verleiht.</span><span class="sxs-lookup"><span data-stu-id="deaf0-116">It takes longer to calculate diffuse lighting because it changes for each object vertex, however the benefit of using it is that it shades objects and gives them three-dimensional (3D) depth.</span></span>

<span data-ttu-id="deaf0-117">[Spiegelnde Beleuchtung](specular-lighting.md) bezeichnet die hellen spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird.</span><span class="sxs-lookup"><span data-stu-id="deaf0-117">[Specular lighting](specular-lighting.md) identifies the bright specular highlights that occur when light hits an object surface and reflects back toward the camera.</span></span> <span data-ttu-id="deaf0-118">Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab.</span><span class="sxs-lookup"><span data-stu-id="deaf0-118">Specular lighting is more intense than diffuse light and falls off more rapidly across the object surface.</span></span> <span data-ttu-id="deaf0-119">Die Berechnung von spiegelnder Beleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung; der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.</span><span class="sxs-lookup"><span data-stu-id="deaf0-119">It takes longer to calculate specular lighting than diffuse lighting, however the benefit of using it is that it adds significant detail to a surface.</span></span>

<span data-ttu-id="deaf0-120">[Ausstrahlende Beleuchtung](emissive-lighting.md) ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten.</span><span class="sxs-lookup"><span data-stu-id="deaf0-120">[Emissive lighting](emissive-lighting.md) is light that is emitted by an object; for example, a glow.</span></span> <span data-ttu-id="deaf0-121">Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend.</span><span class="sxs-lookup"><span data-stu-id="deaf0-121">Emission makes a rendered object appear to be self-luminous.</span></span> <span data-ttu-id="deaf0-122">Die Ausstrahlung wirkt sich auf die Farbe des Objekts aus und kann beispielsweise ein dunkles Material heller erscheinen lassen und einen Teil der ausgestrahlten Farbe annehmen.</span><span class="sxs-lookup"><span data-stu-id="deaf0-122">Emission affects an object's color and can, for example, make a dark material brighter and take on part of the emitted color.</span></span>

<span data-ttu-id="deaf0-123">Durch die Anwendung jedes dieser Beleuchtungstypen auf einer 3D-Szene kann eine realistische Beleuchtung erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="deaf0-123">Realistic lighting can be accomplished by applying each of these types of lighting to a 3D scene.</span></span> <span data-ttu-id="deaf0-124">Die für Umgebungs-, ausstrahlende und diffuse Komponenten berechneten Werte werden als die diffuse Eckpunktfarbe ausgegeben; der Wert für die spiegelnde Beleuchtungskomponente wird als spiegelnde Eckpunktfarbe ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="deaf0-124">The values calculated for ambient, emissive, and diffuse components are output as the diffuse vertex color; the value for the specular lighting component is output as the specular vertex color.</span></span> <span data-ttu-id="deaf0-125">Werte für Umgebungs-, diffuse und spiegelnde Beleuchtung können durch den Abschwächungs- und Spotlicht-Faktor eines bestimmten Lichts beeinflusst werden.</span><span class="sxs-lookup"><span data-stu-id="deaf0-125">Ambient, diffuse, and specular light values can be affected by a given light's attenuation and spotlight factor.</span></span> <span data-ttu-id="deaf0-126">Siehe [Abschwächungs- und Spotlicht-Faktor](attenuation-and-spotlight-factor.md).</span><span class="sxs-lookup"><span data-stu-id="deaf0-126">See [Attenuation and spotlight factor](attenuation-and-spotlight-factor.md).</span></span>

<span data-ttu-id="deaf0-127">Um einen realistischeren Beleuchtungseffekt zu erzielen, müssen Sie weitere Lampen hinzufügen, woraus jedoch eine längere Wiedergabe der Szene resultiert.</span><span class="sxs-lookup"><span data-stu-id="deaf0-127">To achieve a more realistic lighting effect, you add more lights; however, the scene takes longer to render.</span></span> <span data-ttu-id="deaf0-128">Um alle durch einen Designer angestrebten Effekte zu erzielen, verwenden einige Spiele mehr CPU-Leistung als allgemein verfügbar.</span><span class="sxs-lookup"><span data-stu-id="deaf0-128">To achieve all the effects a designer wants, some games use more CPU power than is commonly available.</span></span> <span data-ttu-id="deaf0-129">In diesem Fall es ist üblich, die Anzahl der Beleuchtungsberechnungen auf ein Minimum zu reduzieren, indem Beleuchtungskarten und Umgebungskarten eingesetzt werden, um eine Szene besser zu beleuchten, während Texturkarten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="deaf0-129">In this case, it is typical to reduce the number of lighting calculations to a minimum by using lighting maps and environment maps to add lighting to a scene while using texture maps.</span></span>

<span data-ttu-id="deaf0-130">Die Beleuchtung wird im Kameraraum berechnet.</span><span class="sxs-lookup"><span data-stu-id="deaf0-130">Lighting is computed in the camera space.</span></span> <span data-ttu-id="deaf0-131">Siehe [Kameraraumtransformationen](camera-space-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="deaf0-131">See [Camera space transformations](camera-space-transformations.md).</span></span> <span data-ttu-id="deaf0-132">Optimierte Beleuchtung kann in einem Modellraum berechnet werden, in dem spezielle Bedingungen vorherrschen: die Normalvektoren sind bereits normalisiert, Eckpunktvermischung ist nicht erforderlich und Transformationsmatrizen sind orthogonal.</span><span class="sxs-lookup"><span data-stu-id="deaf0-132">Optimized lighting can be computed in model space, when special conditions exist: normal vectors are already normalized, vertex blending is not needed, and transformation matrices are orthogonal.</span></span>

<span data-ttu-id="deaf0-133">Alle Beleuchtungsberechnungen erfolgen im Modellraum durch Ändern von Position und Richtung der Lichtquelle, sowie der Kameraposition, um den Raum unter Verwendung des Gegenteils der Weltmatrix zu modellieren.</span><span class="sxs-lookup"><span data-stu-id="deaf0-133">All lighting computations are made in model space by transforming the light source's position and direction, along with the camera position, to model space using the inverse of the world matrix.</span></span> <span data-ttu-id="deaf0-134">Die resultierende Beleuchtung kann daher, wenn die Welt- oder Ansichtsmatrizen eine ungleichmäßige Skalierung einführen, unter Umständen ungenau sein.</span><span class="sxs-lookup"><span data-stu-id="deaf0-134">As a result, if the world or view matrices introduce non-uniform scaling, the resultant lighting might be inaccurate.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="deaf0-135"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="deaf0-135"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="deaf0-136">Thema</span><span class="sxs-lookup"><span data-stu-id="deaf0-136">Topic</span></span></th>
<th align="left"><span data-ttu-id="deaf0-137">Description</span><span class="sxs-lookup"><span data-stu-id="deaf0-137">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="ambient-lighting.md"><span data-ttu-id="deaf0-138">Umgebungslicht</span><span class="sxs-lookup"><span data-stu-id="deaf0-138">Ambient lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-139">Umgebungsbeleuchtung bietet konstante Beleuchtung für eine Szene.</span><span class="sxs-lookup"><span data-stu-id="deaf0-139">Ambient lighting provides constant lighting for a scene.</span></span> <span data-ttu-id="deaf0-140">Sie leuchtet alle Objekteckpunkte gleich aus, da sie nicht von anderen Beleuchtungsfaktoren abhängig ist, wie der Eckpunktnormalen, der Richtung des Lichts, der Position der Lichtquelle, der Reichweite oder Abschwächung des Lichts.</span><span class="sxs-lookup"><span data-stu-id="deaf0-140">It lights all object vertices the same because it is not dependent on any other lighting factors such as vertex normals, light direction, light position, range, or attenuation.</span></span> <span data-ttu-id="deaf0-141">Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch.</span><span class="sxs-lookup"><span data-stu-id="deaf0-141">Ambient lighting is constant in all directions and it colors all pixels of an object the same.</span></span> <span data-ttu-id="deaf0-142">Sie lässt sich schnell berechnen, bewirkt jedoch, dass Objekte flach und unrealistisch aussehen.</span><span class="sxs-lookup"><span data-stu-id="deaf0-142">It is fast to calculate but leaves objects looking flat and unrealistic.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="diffuse-lighting.md"><span data-ttu-id="deaf0-143">Diffuse Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="deaf0-143">Diffuse lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-144"><em>Diffuse Beleuchtung</em> hängt sowohl von der Richtung des Lichts als auch von der Flächennormalen des Objekts ab.</span><span class="sxs-lookup"><span data-stu-id="deaf0-144"><em>Diffuse lighting</em> depends on both the light direction and the object surface normal.</span></span> <span data-ttu-id="deaf0-145">Diffuse Beleuchtung ist auf der Oberfläche eines Objekts durch die Änderung der Richtung des Lichts und den sich ändernden Oberflächenzahlvektor unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="deaf0-145">Diffuse lighting varies across the surface of an object as a result of the changing light direction and the changing surface numeral vector.</span></span> <span data-ttu-id="deaf0-146">Es dauert länger, diffuse Beleuchtung zu berechnen, da sie sich für jeden Eckpunkt des Objektes ändert; der Vorteil der Verwendung liegt jedoch darin, dass sie Objekten einen Schatten und eine dreidimensionale (3D) Tiefe verleiht.</span><span class="sxs-lookup"><span data-stu-id="deaf0-146">It takes longer to calculate diffuse lighting because it changes for each object vertex, however the benefit of using it is that it shades objects and gives them three-dimensional (3D) depth.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="specular-lighting.md"><span data-ttu-id="deaf0-147">Spiegelnde Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="deaf0-147">Specular lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-148"><em>Spiegelnde Beleuchtung</em> bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird.</span><span class="sxs-lookup"><span data-stu-id="deaf0-148"><em>Specular lighting</em> identifies the bright specular highlights that occur when light hits an object surface and reflects back toward the camera.</span></span> <span data-ttu-id="deaf0-149">Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab.</span><span class="sxs-lookup"><span data-stu-id="deaf0-149">Specular lighting is more intense than diffuse light and falls off more rapidly across the object surface.</span></span> <span data-ttu-id="deaf0-150">Die Berechnung von spiegelnder Beleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung; der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.</span><span class="sxs-lookup"><span data-stu-id="deaf0-150">It takes longer to calculate specular lighting than diffuse lighting, however the benefit of using it is that it adds significant detail to a surface.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="emissive-lighting.md"><span data-ttu-id="deaf0-151">Ausstrahlende Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="deaf0-151">Emissive lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-152"><em>Ausstrahlende Beleuchtung</em> ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten.</span><span class="sxs-lookup"><span data-stu-id="deaf0-152"><em>Emissive lighting</em> is light that is emitted by an object; for example, a glow.</span></span> <span data-ttu-id="deaf0-153">Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend.</span><span class="sxs-lookup"><span data-stu-id="deaf0-153">Emission makes a rendered object appear to be self-luminous.</span></span> <span data-ttu-id="deaf0-154">Die Ausstrahlung wirkt sich auf die Farbe des Objekts aus und kann beispielsweise ein dunkles Material heller erscheinen lassen und einen Teil der ausgestrahlten Farbe annehmen.</span><span class="sxs-lookup"><span data-stu-id="deaf0-154">Emission affects an object's color and can, for example, make a dark material brighter and take on part of the emitted color.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="camera-space-transformations.md"><span data-ttu-id="deaf0-155">Kameraraumtransformationen</span><span class="sxs-lookup"><span data-stu-id="deaf0-155">Camera space transformations</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-156">Eckpunkte im Kameraraum werden durch das Wandeln der Objekteckpunkte mit der Weltansichtsmatrix berechnet.</span><span class="sxs-lookup"><span data-stu-id="deaf0-156">Vertices in the camera space are computed by transforming the object vertices with the world view matrix.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="attenuation-and-spotlight-factor.md"><span data-ttu-id="deaf0-157">Abschwächungs- und Spotlicht-Faktor</span><span class="sxs-lookup"><span data-stu-id="deaf0-157">Attenuation and spotlight factor</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="deaf0-158">Die diffusen und spiegelnden Beleuchtungskomponenten der globalen Beleuchtungsgleichung enthalten Begriffe, die die Abschwächung des Lichts und den Spotlicht-Kegel beschreiben.</span><span class="sxs-lookup"><span data-stu-id="deaf0-158">The diffuse and specular lighting components of the global illumination equation contain terms that describe light attenuation and the spotlight cone.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="deaf0-159"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="deaf0-159"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="deaf0-160">Lampen und Material</span><span class="sxs-lookup"><span data-stu-id="deaf0-160">Lights and materials</span></span>](lights-and-materials.md)

 

 




