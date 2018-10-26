---
title: Projektionstransformation
description: Ein Projektionstransformation steuert die internen Elemente der Kamera, z.B. die Auswahl einer Linse für eine Kamera. Dies ist der komplizierteste der drei Transformationstypen.
ms.assetid: 378F205D-3800-4477-9820-5EBE6528B14A
keywords:
- Projektionstransformation
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 01a410e0e2759dcdfd6adff9c25238447fe4138b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5566191"
---
# <a name="projection-transform"></a><span data-ttu-id="ab95e-105">Projektionstransformation</span><span class="sxs-lookup"><span data-stu-id="ab95e-105">Projection transform</span></span>


<span data-ttu-id="ab95e-106">Eine *Projektionstransformation* steuert die internen Elemente der Kamera, z.B. die Auswahl eines Objektivs für eine Kamera.</span><span class="sxs-lookup"><span data-stu-id="ab95e-106">A *projection transformation* controls the camera's internals, like choosing a lens for a camera.</span></span> <span data-ttu-id="ab95e-107">Dies ist der komplizierteste der drei Transformationstypen.</span><span class="sxs-lookup"><span data-stu-id="ab95e-107">This is the most complicated of the three transformation types.</span></span>

<span data-ttu-id="ab95e-108">Die Projektionsmatrix ist in der Regel eine Skalierung und perspektivische Projektion.</span><span class="sxs-lookup"><span data-stu-id="ab95e-108">The projection matrix is typically a scale and perspective projection.</span></span> <span data-ttu-id="ab95e-109">Die Projektionstransformation konvertiert das Ansichtsfrustum in eine Quaderform.</span><span class="sxs-lookup"><span data-stu-id="ab95e-109">The projection transformation converts the viewing frustum into a cuboid shape.</span></span> <span data-ttu-id="ab95e-110">Da das nähergelegene Ende des Ansichtsfrustrums kleiner als das weiter entfernt liegende Ende, hat dies die Wirkung, dass näher bei der Kamera liegende Objekte erweitert werden. So wird Perspektive auf die Szene angewandt.</span><span class="sxs-lookup"><span data-stu-id="ab95e-110">Because the near end of the viewing frustum is smaller than the far end, this has the effect of expanding objects that are near to the camera; this is how perspective is applied to the scene.</span></span>

<span data-ttu-id="ab95e-111">Im [Anzeigefrustrum](viewports-and-clipping.md) ist der Abstand zwischen der Kamera und dem Ursprung des Ansichtstransformationsbereichs beliebig als D definiert. Daher sieht die Projektionsmatrix so aus wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab95e-111">In [the viewing frustum](viewports-and-clipping.md), the distance between the camera and the origin of the viewing transform space is defined arbitrarily as D, so the projection matrix looks like the following illustration.</span></span>

![Abbildung der Projektionsmatrix](images/projmat1.png)

<span data-ttu-id="ab95e-113">Die Ansichtsmatrix verschiebt die Kamera an den Ursprung, indem um -D in die z-Richtung verschoben wird. Die Verschiebungsmatrix entspricht der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="ab95e-113">The viewing matrix translates the camera to the origin by translating in the z direction by - D. The translation matrix is like the following illustration.</span></span>

![Abbildung der Verschiebungsmatrix](images/projmat2.png)

<span data-ttu-id="ab95e-115">Wenn die Verschiebungsmatrix mit der Projektionsmatrix multipliziert wird (T\*P), ergibt dies die zusammengesetzte Projektionsmatrix, wie in der folgenden Abbildungdargestellt.</span><span class="sxs-lookup"><span data-stu-id="ab95e-115">Multiplying the translation matrix by the projection matrix (T\*P) gives the composite projection matrix, as shown in the following illustration.</span></span>

![Abbildung der zusammengesetzten Projektionsmatrix](images/projmat3.png)

<span data-ttu-id="ab95e-117">Die perspektivische Transformation konvertiert ein Ansichtsfrustum in einen neuen Koordinatenbereich.</span><span class="sxs-lookup"><span data-stu-id="ab95e-117">The perspective transform converts a viewing frustum into a new coordinate space.</span></span> <span data-ttu-id="ab95e-118">Beachten Sie, dass das Frustum Quaderform annimmt und dass sich der Ursprung von der oberen rechten Ecke der Szene zur Mitte verschiebt, wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ab95e-118">Notice that the frustum becomes cuboid and also that the origin moves from the upper-right corner of the scene to the center, as shown in the following diagram.</span></span>

![Diagramm, das zeigt, wie die perspektivische Transformation das Ansichtsfrustrum in einen neuen Koordinatenbereich ändert](images/cuboid.png)

<span data-ttu-id="ab95e-120">In der perspektivischen Transformation sind die Grenzen von X- und Y-Richtung -1 und 1.</span><span class="sxs-lookup"><span data-stu-id="ab95e-120">In the perspective transform, the limits of the x- and y-directions are -1 and 1.</span></span> <span data-ttu-id="ab95e-121">Die Grenzen der Z-Richtung sind für 0 die vordere Ebene und 1 für die hintere Ebene.</span><span class="sxs-lookup"><span data-stu-id="ab95e-121">The limits of the z-direction are 0 for the front plane and 1 for the back plane.</span></span>

<span data-ttu-id="ab95e-122">Diese Matrix verschiebt und skaliert Objekte basierend auf einem angegebenen Abstand von der Kamera zur vorderen Clippingebene, berücksichtigt aber nicht das Blickfeld, und die erzeugten Z-Werte für Objekte in der Entfernung können nahezu identisch sein, was Tiefenvergleiche erschwert.</span><span class="sxs-lookup"><span data-stu-id="ab95e-122">This matrix translates and scales objects based on a specified distance from the camera to the near clipping plane, but it doesn't consider the field of view (fov), and the z-values that it produces for objects in the distance can be nearly identical, making depth comparisons difficult.</span></span> <span data-ttu-id="ab95e-123">Die folgende Matrix behebt diese Probleme und passt Scheitelpunkte an, um das Seitenverhältnis des Viewports zu berücksichtigen. Daher ist sie eine gute Wahl für perspektivische Projektion.</span><span class="sxs-lookup"><span data-stu-id="ab95e-123">The following matrix addresses these issues, and it adjusts vertices to account for the aspect ratio of the viewport, making it a good choice for the perspective projection.</span></span>

![Abbildung einer Matrix für die perspektivische Projektion](images/prjmatx1.png)

<span data-ttu-id="ab95e-125">In dieser Matrix ist Zₙ der Z-Wert der vorderen Clippingebene.</span><span class="sxs-lookup"><span data-stu-id="ab95e-125">In this matrix, Zₙ is the z-value of the near clipping plane.</span></span> <span data-ttu-id="ab95e-126">Die Variablen w, h und Q haben folgende Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="ab95e-126">The variables w, h, and Q have the following meanings.</span></span> <span data-ttu-id="ab95e-127">Beachten Sie, dass Blickfeld<sub>w</sub> und Blickfeldₖ die horizontalen und vertikalen Blickfelder im Bogenmaß darstellen.</span><span class="sxs-lookup"><span data-stu-id="ab95e-127">Note that fov<sub>w</sub> and fovₖ represent the viewport's horizontal and vertical fields of view, in radians.</span></span>

![Formeln der Variablenbedeutung](images/prjmatx2.png)

<span data-ttu-id="ab95e-129">Für Ihre Anwendung ist die Verwendung von Blickfeldwinkeln zum Definieren der X- und Y-Skalierungskoeffizienten möglicherweise nicht so günstig wie der Einsatz der horizontalen und vertikalen Abmessungen des Viewports (im Kamerabereich).</span><span class="sxs-lookup"><span data-stu-id="ab95e-129">For your application, using field-of-view angles to define the x- and y-scaling coefficients might not be as convenient as using the viewport's horizontal and vertical dimensions (in camera space).</span></span> <span data-ttu-id="ab95e-130">Mathematisch verwenden die folgenden beiden Gleichungen für w und h die Abmessungen des Viewports und entsprechen den obigen Gleichungen.</span><span class="sxs-lookup"><span data-stu-id="ab95e-130">As the math works out, the following two equations for w and h use the viewport's dimensions, and are equivalent to the preceding equations.</span></span>

![Gleichungen der Variablenbedeutung für w und h](images/prjmatx3.png)

<span data-ttu-id="ab95e-132">In diesen Formeln steht Zₙ für die Position der vorderen Clippingebene, und die Variablen V<sub>w</sub> und Vₕ stellen die Breite und Höhe des Viewports im Kamerabereich dar.</span><span class="sxs-lookup"><span data-stu-id="ab95e-132">In these formulas, Zₙ represents the position of the near clipping plane, and the V<sub>w</sub> and Vₕ variables represent the width and height of the viewport, in camera space.</span></span>

<span data-ttu-id="ab95e-133">Unabhängig von der Formel, für die Sie sich entscheiden, sollten Sie den Zₙ-Wert so groß wie möglich festlegen, da sehr nahe bei der Kamera liegende Z-Werte kaum variieren.</span><span class="sxs-lookup"><span data-stu-id="ab95e-133">Whatever formula you decide to use, be sure to set Zₙ to as large a value as possible, because z-values extremely close to the camera don't vary by much.</span></span> <span data-ttu-id="ab95e-134">Das erschwert Tiefenvergleiche mit 16-Bit-z-Puffern.</span><span class="sxs-lookup"><span data-stu-id="ab95e-134">This makes depth comparisons using 16-bit z-buffers somewhat complicated.</span></span>

## <a name="span-idawfriendlyprojectionmatrixspanspan-idawfriendlyprojectionmatrixspanspan-idawfriendlyprojectionmatrixspana-w-friendly-projection-matrix"></a><span data-ttu-id="ab95e-135"><span id="A_W_Friendly_Projection_Matrix"></span><span id="a_w_friendly_projection_matrix"></span><span id="A_W_FRIENDLY_PROJECTION_MATRIX"></span>Für w günstige Projektionsmatrix</span><span class="sxs-lookup"><span data-stu-id="ab95e-135"><span id="A_W_Friendly_Projection_Matrix"></span><span id="a_w_friendly_projection_matrix"></span><span id="A_W_FRIENDLY_PROJECTION_MATRIX"></span>A w-friendly projection matrix</span></span>


<span data-ttu-id="ab95e-136">Direct3D kann die w-Komponente eines Scheitelpunkts, der durch die Welt-, Ansichts- und Projektionsmatrizen umgewandelt wurde, für tiefenbasierte Berechnungen im Tiefenpuffer oder bei Nebeleffekten einsetzen.</span><span class="sxs-lookup"><span data-stu-id="ab95e-136">Direct3D can use the w-component of a vertex that has been transformed by the world, view, and projection matrices to perform depth-based calculations in depth-buffer or fog effects.</span></span> <span data-ttu-id="ab95e-137">Für derartige Berechnungen muss Ihre Projektionsmatrix w so normalisieren, dass es dem Welt-Bereich z entspricht.</span><span class="sxs-lookup"><span data-stu-id="ab95e-137">Computations such as these require that your projection matrix normalize w to be equivalent to world-space z.</span></span> <span data-ttu-id="ab95e-138">Wenn Ihre Projektionsmatrix also einen (3,4)-Koeffizienten enthält, der nicht 1 ist, müssen Sie alle Koeffizienten mit dem umgekehrten Wert des (3,4)-Koeffizienten skalieren, um eine korrekte Matrix zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ab95e-138">In short, if your projection matrix includes a (3,4) coefficient that is not 1, you must scale all the coefficients by the inverse of the (3,4) coefficient to make a proper matrix.</span></span> <span data-ttu-id="ab95e-139">Wenn Sie keine kompatible Matrix bereitstellen, werden Nebeleffekte und Tiefenpufferung nicht ordnungsgemäß angewendet.</span><span class="sxs-lookup"><span data-stu-id="ab95e-139">If you don't provide a compliant matrix, fog effects and depth buffering are not applied correctly.</span></span>

<span data-ttu-id="ab95e-140">Die folgende Abbildungzeigt eine nicht kompatible Projektionsmatrix und die gleiche Matrix so skaliert, dass Nebel im Bezug zum Auge ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="ab95e-140">The following illustration shows a noncompliant projection matrix, and the same matrix scaled so that eye-relative fog will be enabled.</span></span>

![Abbildungen einer nicht kompatiblen Projektionsmatrix und einer Matrix mit Nebel im Bezug zum Auge](images/eyerlmx.png)

<span data-ttu-id="ab95e-142">In den vorangehenden Matrizen wird davon ausgegangen, dass alle Variablen ungleich Null sind.</span><span class="sxs-lookup"><span data-stu-id="ab95e-142">In the preceding matrices, all variables are assumed to be nonzero.</span></span> <span data-ttu-id="ab95e-143">Informationen zur w-basierten Tiefenpufferung finden Sie unter [Tiefenpuffer](depth-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="ab95e-143">For information about w-based depth buffering, see [Depth buffers](depth-buffers.md).</span></span>

<span data-ttu-id="ab95e-144">Direct3D verwendet die derzeit festgelegte Projektionsmatrix in ihren w-basierten Tiefenberechnungen.</span><span class="sxs-lookup"><span data-stu-id="ab95e-144">Direct3D uses the currently set projection matrix in its w-based depth calculations.</span></span> <span data-ttu-id="ab95e-145">Daher müssen Anwendungen eine kompatible Projektionsmatrix festlegen, um die gewünschten w-basierten Funktionen zu erhalten, auch wenn sie Direct3D nicht für Transformationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="ab95e-145">As a result, applications must set a compliant projection matrix to receive the desired w-based features, even if they do not use Direct3D for transforms.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="ab95e-146"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ab95e-146"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="ab95e-147">Transformationen</span><span class="sxs-lookup"><span data-stu-id="ab95e-147">Transforms</span></span>](transforms.md)

 

 




