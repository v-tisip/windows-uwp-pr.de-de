---
title: Kameraraumtransformationen
description: Scheitelpunkte im Kameraraum werden berechnet, indem die Scheitelpunkte des Objekts mit der globalen Ansichtsmatrix transformiert werden.
ms.assetid: 86EDEB95-8348-4FAA-897F-25251B32B076
keywords:
- Kameraraumtransformationen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9de6759fb15aef4b32a5e9022a27cab09af300f8
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5710369"
---
# <a name="camera-space-transformations"></a><span data-ttu-id="8b388-104">Kameraraumtransformationen</span><span class="sxs-lookup"><span data-stu-id="8b388-104">Camera space transformations</span></span>


<span data-ttu-id="8b388-105">Scheitelpunkte im Kameraraum werden berechnet, indem die Scheitelpunkte des Objekts mit der globalen Ansichtsmatrix transformiert werden.</span><span class="sxs-lookup"><span data-stu-id="8b388-105">Vertices in the camera space are computed by transforming the object vertices with the world view matrix.</span></span>

<span data-ttu-id="8b388-106">V = V \* wvMatrix</span><span class="sxs-lookup"><span data-stu-id="8b388-106">V = V \* wvMatrix</span></span>

<span data-ttu-id="8b388-107">Vertexspezifische Normalen im Kameraraum werden berechnet, indem die Normalen des Objekts mit der inversen Umsetzung der globalen Ansichtsmatrix transformiert werden.</span><span class="sxs-lookup"><span data-stu-id="8b388-107">Vertex normals, in camera space, are computed by transforming the object normals with the inverse transpose of the world view matrix.</span></span> <span data-ttu-id="8b388-108">Eine globale Ansichtsmatrix kann entweder orthogonal sein oder nicht.</span><span class="sxs-lookup"><span data-stu-id="8b388-108">The world view matrix may or may not be orthogonal.</span></span>

<span data-ttu-id="8b388-109">N = N \* (wvMatrix⁻¹)<sup>T</sup></span><span class="sxs-lookup"><span data-stu-id="8b388-109">N = N \* (wvMatrix⁻¹)<sup>T</sup></span></span>

<span data-ttu-id="8b388-110">Die Matrixinversion und der Matrixaustausch werden auf einer 4x4-Matrix ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8b388-110">The matrix inversion and matrix transpose operate on a 4x4 matrix.</span></span> <span data-ttu-id="8b388-111">Die Multiplikation kombiniert den normalen Teil mit dem 3x3-Teil der resultierenden 4x4-Matrix.</span><span class="sxs-lookup"><span data-stu-id="8b388-111">The multiply combines the normal with the 3x3 portion of the resulting 4x4 matrix.</span></span>

<span data-ttu-id="8b388-112">Wenn der Renderstatus so festgelegt ist, dass die Normalen normalisiert werden, werden Scheitelnormalenvektoren wie folgt nach der Transformation auf den Kameraraum normalisiert:</span><span class="sxs-lookup"><span data-stu-id="8b388-112">If the render state is set to normalize normals, vertex normal vectors are normalized after transformation to camera space as follows:</span></span>

<span data-ttu-id="8b388-113">N = norm(N)</span><span class="sxs-lookup"><span data-stu-id="8b388-113">N = norm(N)</span></span>

<span data-ttu-id="8b388-114">Die Beleuchtungsposition im Kameraraum wird durch die Transformation der Position der Lichtquelle mit der Ansichtsmatrix berechnet.</span><span class="sxs-lookup"><span data-stu-id="8b388-114">Light position in camera space is computed by transforming the light source position with the view matrix.</span></span>

<span data-ttu-id="8b388-115">Lₚ = Lₚ \* vMatrix</span><span class="sxs-lookup"><span data-stu-id="8b388-115">Lₚ = Lₚ \* vMatrix</span></span>

<span data-ttu-id="8b388-116">Die Richtung des Lichts im Kameraraum für gerichtetes Licht wird durch die Multiplikation der Richtung der Lichtquellen mit der Ansichtsmatrix berechnet, normalisiert und das Resultat wird negiert.</span><span class="sxs-lookup"><span data-stu-id="8b388-116">The direction to the light in camera space for a directional light is computed by multiplying the light source direction by the view matrix, normalizing, and negating the result.</span></span>

<span data-ttu-id="8b388-117">L<sub>dir</sub> = -norm(L<sub>dir</sub> \* wvMatrix)</span><span class="sxs-lookup"><span data-stu-id="8b388-117">L<sub>dir</sub> = -norm(L<sub>dir</sub> \* wvMatrix)</span></span>

<span data-ttu-id="8b388-118">Für ein punktuelles Licht und ein Spotlight wird die Richtung der Lichtquelle wie folgt berechnet:</span><span class="sxs-lookup"><span data-stu-id="8b388-118">For a point light and a spotlight, the direction to light is computed as follows:</span></span>

<span data-ttu-id="8b388-119">L<sub>dir</sub> = norm(V \* Lₚ). Dabei werden die Parameter in der folgenden Tabelle definiert.</span><span class="sxs-lookup"><span data-stu-id="8b388-119">L<sub>dir</sub> = norm(V \* Lₚ), where the parameters are defined in the following table.</span></span>

| <span data-ttu-id="8b388-120">Parameter</span><span class="sxs-lookup"><span data-stu-id="8b388-120">Parameter</span></span>       | <span data-ttu-id="8b388-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b388-121">Default value</span></span> | <span data-ttu-id="8b388-122">Typ</span><span class="sxs-lookup"><span data-stu-id="8b388-122">Type</span></span>                                          | <span data-ttu-id="8b388-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8b388-123">Description</span></span>                                               |
|-----------------|---------------|-----------------------------------------------|-----------------------------------------------------------|
| <span data-ttu-id="8b388-124">L<sub>dir</sub></span><span class="sxs-lookup"><span data-stu-id="8b388-124">L<sub>dir</sub></span></span> | <span data-ttu-id="8b388-125">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="8b388-125">N/A</span></span>           | <span data-ttu-id="8b388-126">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="8b388-126">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="8b388-127">Richtungsvektor vom Objekt-Vertex bis zur Lichtquelle</span><span class="sxs-lookup"><span data-stu-id="8b388-127">Direction vector from object vertex to the light</span></span>          |
| <span data-ttu-id="8b388-128">V</span><span class="sxs-lookup"><span data-stu-id="8b388-128">V</span></span>               | <span data-ttu-id="8b388-129">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="8b388-129">N/A</span></span>           | <span data-ttu-id="8b388-130">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="8b388-130">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="8b388-131">Vertexposition im Kameraraum</span><span class="sxs-lookup"><span data-stu-id="8b388-131">Vertex position in camera space</span></span>                           |
| <span data-ttu-id="8b388-132">wvMatrix</span><span class="sxs-lookup"><span data-stu-id="8b388-132">wvMatrix</span></span>        | <span data-ttu-id="8b388-133">Identität</span><span class="sxs-lookup"><span data-stu-id="8b388-133">Identity</span></span>      | <span data-ttu-id="8b388-134">4x4-Matrix der Gleitkommawerte</span><span class="sxs-lookup"><span data-stu-id="8b388-134">4x4 matrix of floating-point values</span></span>           | <span data-ttu-id="8b388-135">Zusammengesetzte Matrix mit globaler und Ansichtstransformation</span><span class="sxs-lookup"><span data-stu-id="8b388-135">Composite matrix containing the world and view transforms</span></span> |
| <span data-ttu-id="8b388-136">N</span><span class="sxs-lookup"><span data-stu-id="8b388-136">N</span></span>               | <span data-ttu-id="8b388-137">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="8b388-137">N/A</span></span>           | <span data-ttu-id="8b388-138">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="8b388-138">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="8b388-139">Vertexnormale</span><span class="sxs-lookup"><span data-stu-id="8b388-139">Vertex normal</span></span>                                             |
| <span data-ttu-id="8b388-140">Lₚ</span><span class="sxs-lookup"><span data-stu-id="8b388-140">Lₚ</span></span>              | <span data-ttu-id="8b388-141">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="8b388-141">N/A</span></span>           | <span data-ttu-id="8b388-142">3D-Vektor (X-, Y- und Z-Gleitkommawerte)</span><span class="sxs-lookup"><span data-stu-id="8b388-142">3D vector (x, y, and z floating-point values)</span></span> | <span data-ttu-id="8b388-143">Position der Lichtquelle im Kameraraum</span><span class="sxs-lookup"><span data-stu-id="8b388-143">Light position in camera space</span></span>                            |
| <span data-ttu-id="8b388-144">vMatrix</span><span class="sxs-lookup"><span data-stu-id="8b388-144">vMatrix</span></span>         | <span data-ttu-id="8b388-145">Identität</span><span class="sxs-lookup"><span data-stu-id="8b388-145">Identity</span></span>      | <span data-ttu-id="8b388-146">4x4-Matrix der Gleitkommawerte</span><span class="sxs-lookup"><span data-stu-id="8b388-146">4x4 matrix of floating-point values</span></span>           | <span data-ttu-id="8b388-147">Matrix mit Ansichtstransformation</span><span class="sxs-lookup"><span data-stu-id="8b388-147">Matrix containing the view transform</span></span>                      |

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="8b388-148"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8b388-148"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="8b388-149">Beleuchtungsmathematik</span><span class="sxs-lookup"><span data-stu-id="8b388-149">Mathematics of lighting</span></span>](mathematics-of-lighting.md)

 

 




