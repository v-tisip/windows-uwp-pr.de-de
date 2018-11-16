---
title: Übersicht über Transformationen
description: Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.
ms.assetid: B5220EE8-2533-4B55-BF58-A3F9F612B977
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 32f55b0a387221b792e37072f129edddf285195b
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6980537"
---
# <a name="transform-overview"></a><span data-ttu-id="39433-104">Übersicht über Transformationen</span><span class="sxs-lookup"><span data-stu-id="39433-104">Transform overview</span></span>


<span data-ttu-id="39433-105">Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="39433-105">Matrix transformations handle a lot of the low level math of 3D graphics.</span></span>

<span data-ttu-id="39433-106">Die Geometrie-Pipeline verwendet Scheitelpunkte als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="39433-106">The geometry pipeline takes vertices as input.</span></span> <span data-ttu-id="39433-107">Die Transform-Engine wendet die Welt-, Ansichts- und Projektionstransformationen auf die Scheitelpunkte an, beschneidet das Ergebnis und übergibt alles an den Rasterizer.</span><span class="sxs-lookup"><span data-stu-id="39433-107">The transform engine applies the world, view, and projection transforms to the vertices, clips the result, and passes everything to the rasterizer.</span></span>

| <span data-ttu-id="39433-108">Transformation und Bereich</span><span class="sxs-lookup"><span data-stu-id="39433-108">Transform and space</span></span>                           | <span data-ttu-id="39433-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39433-109">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="39433-110">Modellkoordinaten im Modellbereich</span><span class="sxs-lookup"><span data-stu-id="39433-110">Model coordinates in model space</span></span>              | <span data-ttu-id="39433-111">Am Anfang der Pipeline werden die Scheitelpunkte eines Modells relativ zu einem lokalen Koordinatensystems deklariert.</span><span class="sxs-lookup"><span data-stu-id="39433-111">At the head of the pipeline, a model's vertices are declared relative to a local coordinate system.</span></span> <span data-ttu-id="39433-112">Dies ist ein lokaler Ursprung und eine Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="39433-112">This is a local origin and an orientation.</span></span> <span data-ttu-id="39433-113">Diese Ausrichtung der Koordinaten wird häufig als *Modellbereich* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="39433-113">This orientation of coordinates is often referred to as *model space*.</span></span> <span data-ttu-id="39433-114">Einzelne Koordinaten werden als *Modellkoordinaten* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="39433-114">Individual coordinates are called *model coordinates*.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="39433-115">Welttransformation in den Weltbereich</span><span class="sxs-lookup"><span data-stu-id="39433-115">World transform into world space</span></span>              | <span data-ttu-id="39433-116">Die erste Phase der Geometrie-Pipeline transformiert die Scheitelpunkte eines Modells aus ihrem lokalen Koordinatensystem in ein Koordinatensystem, das von allen Objekten in einer Szene verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="39433-116">The first stage of the geometry pipeline transforms a model's vertices from their local coordinate system to a coordinate system that is used by all the objects in a scene.</span></span> <span data-ttu-id="39433-117">Der Prozess der Neuorientierung der Scheitelpunkte wird als [Welttransformation](world-transform.md) bezeichnet; dies ist die Konvertierung vom Modellbereich zu einer neuen Orientierung, die als *Weltbereich* bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="39433-117">The process of reorienting the vertices is called the [World transform](world-transform.md), which converts from model space to a new orientation called *world space*.</span></span> <span data-ttu-id="39433-118">Jeder Scheitelpunkt im Weltbereich wird durch *Weltkoordinaten* angegeben.</span><span class="sxs-lookup"><span data-stu-id="39433-118">Each vertex in world space is declared using *world coordinates*.</span></span>                                                                                                                                                                                                                                                                                                                           |
| <span data-ttu-id="39433-119">Ansichtstransformation zum Ansichtsbereich (Kamerabereich)</span><span class="sxs-lookup"><span data-stu-id="39433-119">View transform into view space (camera space)</span></span> | <span data-ttu-id="39433-120">Im nächsten Schrittwerden die Scheitelpunkte, die Ihre 3D-Welt beschreiben, hinsichtlich der Kamera ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="39433-120">In the next stage, the vertices that describe your 3D world are oriented with respect to a camera.</span></span> <span data-ttu-id="39433-121">Dies bedeutet, dass Ihre Anwendung einen Ansichtspunkt für die Szene auswählt, und dass die Weltbereichskoordinaten um die Kameraansicht neu angeordnet und gedreht werden, wodurch der Weltbereich zum *Ansichtsbereich* (bzw. *Kamerabereich*) wird.</span><span class="sxs-lookup"><span data-stu-id="39433-121">That is, your application chooses a point-of-view for the scene, and world space coordinates are relocated and rotated around the camera's view, turning world space into *view space* (also known as *camera space*).</span></span> <span data-ttu-id="39433-122">Dies ist die [Ansichtstransformation](view-transform.md), die Konvertierung vom Ansichtsbereich zum Weltbereich.</span><span class="sxs-lookup"><span data-stu-id="39433-122">This is the [View transform](view-transform.md), which converts from world space to view space.</span></span>                                                                                                                                                                                                                                                                                                                        |
| <span data-ttu-id="39433-123">Transformation der Projektion zum Projektionsbereich</span><span class="sxs-lookup"><span data-stu-id="39433-123">Projection transform into projection space</span></span>    | <span data-ttu-id="39433-124">Der nächste Schrittist die [Projektionstransformation](projection-transform.md), die Konvertierung vom Ansichtsbereich zum Projektionsbereich.</span><span class="sxs-lookup"><span data-stu-id="39433-124">The next stage is the [Projection transform](projection-transform.md), which converts from view space to projection space.</span></span> <span data-ttu-id="39433-125">In diesem Teil der Pipeline werden Objekte in der Regel in Bezug auf ihre Entfernung vom Betrachter skaliert, um einer Szene die Illusion von Tiefe zu geben. Nahe Objekte erscheinen dadurch größer als entfernte Objekte.</span><span class="sxs-lookup"><span data-stu-id="39433-125">In this part of the pipeline, objects are usually scaled with relation to their distance from the viewer in order to give the illusion of depth to a scene; close objects are made to appear larger than distant objects.</span></span> <span data-ttu-id="39433-126">Der Einfachheit halber bezeichnet diese Dokumentation den Bereich mit den Scheitelpunkten nach der Projektionstransformation als *Projektionsbereich*.</span><span class="sxs-lookup"><span data-stu-id="39433-126">For simplicity, this documentation refers to the space in which vertices exist after the projection transform as *projection space*.</span></span> <span data-ttu-id="39433-127">Einige Grafikbücher bezeichnen den Projektionsbereich möglicherweise als *postperspektivischen homogenen Bereich*.</span><span class="sxs-lookup"><span data-stu-id="39433-127">Some graphics books might refer to projection space as *post-perspective homogeneous space*.</span></span> <span data-ttu-id="39433-128">Nicht alle Projektionstransformationen skalieren Objekte in einer Szene nach der Größe.</span><span class="sxs-lookup"><span data-stu-id="39433-128">Not all projection transforms scale the size of objects in a scene.</span></span> <span data-ttu-id="39433-129">Eine solche Projektion wird manchmal als *affine* oder *orthogonale Projektion* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="39433-129">A projection such as this is sometimes called an *affine* or *orthogonal projection*.</span></span> |
| <span data-ttu-id="39433-130">Zuschneiden im Bildschirmbereich</span><span class="sxs-lookup"><span data-stu-id="39433-130">Clipping in screen space</span></span>                      | <span data-ttu-id="39433-131">Im letzten Teil der Pipeline werden alle Scheitelpunkte, die nicht auf dem Bildschirm zu sehen sind, entfernt, so dass der Rasterizer keine Zeit für die Berechnung der Farben und der Schattierungen für Dinge aufwenden muss, die niemals zu sehen sind.</span><span class="sxs-lookup"><span data-stu-id="39433-131">In the final part of the pipeline, any vertices that will not be visible on the screen are removed, so that the rasterizer doesn't take the time to calculate the colors and shading for something that will never be seen.</span></span> <span data-ttu-id="39433-132">Dieser Vorgang wird als *Zuschneiden* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="39433-132">This process is called *clipping*.</span></span> <span data-ttu-id="39433-133">Nach dem Zuschneiden werden die verbleibenden Scheitelpunkte nach den Viewportparametern skaliert und in Bildschirmkoordinaten umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="39433-133">After clipping, the remaining vertices are scaled according to the viewport parameters and converted into screen coordinates.</span></span> <span data-ttu-id="39433-134">Die resultieRendern Scheitelpunkte, die bei der Rasterisierung der Szene auf dem Bildschirm zu sehen sind, befinden sich im *Bildschirmbereich*.</span><span class="sxs-lookup"><span data-stu-id="39433-134">The resulting vertices, seen on the screen when the scene is rasterized, exist in *screen space*.</span></span>                                                                                                                                                                                                                                                    |

 

<span data-ttu-id="39433-135">Transformationen werden verwendet, um die Objektgeometrie von einem Koordinatenbereich zu einem anderen zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="39433-135">Transforms are used to convert object geometry from one coordinate space to another.</span></span> <span data-ttu-id="39433-136">Direct3D verwendet Matrizen für die Durchführung von 3D-Transformationen.</span><span class="sxs-lookup"><span data-stu-id="39433-136">Direct3D uses matrices to perform 3D transforms.</span></span> <span data-ttu-id="39433-137">Matrizen erstellen-3D-Transformationen.</span><span class="sxs-lookup"><span data-stu-id="39433-137">Matrices create 3D transforms.</span></span> <span data-ttu-id="39433-138">Sie können Matrizen kombinieren, um eine einzelne Matrix zu erstellen, die dann mehrere Transformationen umfasst.</span><span class="sxs-lookup"><span data-stu-id="39433-138">You can combine matrices to produce a single matrix that encompasses multiple transforms.</span></span>

<span data-ttu-id="39433-139">Sie können Koordinaten zwischen Modellbereich, Weltbereich und Ansichtsbereich transformieren.</span><span class="sxs-lookup"><span data-stu-id="39433-139">You can transform coordinates between model space, world space, and view space.</span></span>

-   <span data-ttu-id="39433-140">[Welttransformation](world-transform.md) - Konvertiert vom Modellbereich zum Weltbereich.</span><span class="sxs-lookup"><span data-stu-id="39433-140">[World transform](world-transform.md) - Converts from model space to world space.</span></span>
-   <span data-ttu-id="39433-141">[Ansichtstransformation](view-transform.md) - Konvertiert vom Weltbereich zum Ansichtsbereich.</span><span class="sxs-lookup"><span data-stu-id="39433-141">[View transform](view-transform.md) - Converts from world space to view space.</span></span>
-   <span data-ttu-id="39433-142">[Projektionstransformation](projection-transform.md) -Konvertiert vom Ansichtsbereich zum Projektionsbereich.</span><span class="sxs-lookup"><span data-stu-id="39433-142">[Projection transform](projection-transform.md) - Converts from view space to projection space.</span></span>

## <a name="span-idmatrixtransformsspanspan-idmatrixtransformsspanspan-idmatrixtransformsspanmatrix-transforms"></a><span data-ttu-id="39433-143"><span id="Matrix_Transforms"></span><span id="matrix_transforms"></span><span id="MATRIX_TRANSFORMS"></span>Matrixtransformationen</span><span class="sxs-lookup"><span data-stu-id="39433-143"><span id="Matrix_Transforms"></span><span id="matrix_transforms"></span><span id="MATRIX_TRANSFORMS"></span>Matrix Transforms</span></span>


<span data-ttu-id="39433-144">In Anwendungen, die mit 3D-Grafiken arbeiten, können Sie mithilfe geometrischer Transformationen Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="39433-144">In applications that work with 3D graphics, you can use geometrical transforms to do the following:</span></span>

-   <span data-ttu-id="39433-145">Ausdrücken des Orts eines Objekts im Verhältnis zu einem anderen Objekt.</span><span class="sxs-lookup"><span data-stu-id="39433-145">Express the location of an object relative to another object.</span></span>
-   <span data-ttu-id="39433-146">Drehen und Dimensionieren von Objekten.</span><span class="sxs-lookup"><span data-stu-id="39433-146">Rotate and size objects.</span></span>
-   <span data-ttu-id="39433-147">Ändern von Ansichtspositionen, -richtungen und -perspektiven.</span><span class="sxs-lookup"><span data-stu-id="39433-147">Change viewing positions, directions, and perspectives.</span></span>

<span data-ttu-id="39433-148">Sie können einen beliebigen Punkt (x, y, z) mithilfe einer 4x4-Matrix in einen anderen Punkt (x', y', z') transformieren, wie die folgende Gleichung zeigt.</span><span class="sxs-lookup"><span data-stu-id="39433-148">You can transform any point (x,y,z) into another point (x', y', z') by using a 4x4 matrix, as shown in the following equation.</span></span>

![Gleichung für die Transformation eines Punktes in einen anderen Punkt](images/matmult.png)

<span data-ttu-id="39433-150">Führen Sie die folgenden Gleichungen für (x, y, z) und die Matrix durch, um den Punkt (x', y', z') zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="39433-150">Perform the following equations on (x, y, z) and the matrix to produce the point (x', y', z').</span></span>

![Gleichungen für den neuen Punkt](images/matexpnd.png)

<span data-ttu-id="39433-152">Die am häufigsten verwendeten Transformationen sind Übersetzung, Drehung und Skalierung.</span><span class="sxs-lookup"><span data-stu-id="39433-152">The most common transforms are translation, rotation, and scaling.</span></span> <span data-ttu-id="39433-153">Sie können die Matrizen, die diese Effekte produzieren, zu einer einzelnen Matrix kombinieren, um mehrere Transformationen gleichzeitig zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="39433-153">You can combine the matrices that produce these effects into a single matrix to calculate several transforms at once.</span></span> <span data-ttu-id="39433-154">Beispielsweise können Sie eine einzelne Matrix zum Übersetzen und Drehen eine Reihe von Punkten erstellen.</span><span class="sxs-lookup"><span data-stu-id="39433-154">For example, you can build a single matrix to translate and rotate a series of points.</span></span>

<span data-ttu-id="39433-155">Matrizen werden in der Reihenfolge Zeile-Spalte geschrieben.</span><span class="sxs-lookup"><span data-stu-id="39433-155">Matrices are written in row-column order.</span></span> <span data-ttu-id="39433-156">Die folgende Matrix repräsentiert, in mathematischer Notation, eine Matrix, die Scheitelpunkte entlang der einzelnen Achsen gleichmäßig skaliert (einheitliche Skalierung).</span><span class="sxs-lookup"><span data-stu-id="39433-156">A matrix that evenly scales vertices along each axis, known as uniform scaling, is represented by the following matrix using mathematical notation.</span></span>

![Gleichung einer Matrix für die einheitliche Skalierung](images/matrix.png)

<span data-ttu-id="39433-158">In C++ deklariert Direct3D Matrizen als zweidimensionale Arrays mit einer Matrix-Struktur.</span><span class="sxs-lookup"><span data-stu-id="39433-158">In C++, Direct3D declares matrices as a two-dimensional array, using a matrix struct.</span></span> <span data-ttu-id="39433-159">Das folgende Beispiel demonstriert die Initialisierung einer [**D3DMATRIX**](https://msdn.microsoft.com/library/windows/desktop/bb172573)-Struktur zur Funktion als einheitliche Skalierungsmatrix (Skalierungsfaktor „s“.</span><span class="sxs-lookup"><span data-stu-id="39433-159">The following example shows how to initialize a [**D3DMATRIX**](https://msdn.microsoft.com/library/windows/desktop/bb172573) structure to act as a uniform scaling matrix (scale factor "s").</span></span>

```
D3DMATRIX scale = {
    5.0f,            0.0f,            0.0f,            0.0f,
    0.0f,            5.0f,            0.0f,            0.0f,
    0.0f,            0.0f,            5.0f,            0.0f,
    0.0f,            0.0f,            0.0f,            1.0f
};
```

## <a name="span-idtranslatespanspan-idtranslatespanspan-idtranslatespantranslate"></a><span data-ttu-id="39433-160"><span id="Translate"></span><span id="translate"></span><span id="TRANSLATE"></span>Übersetzen</span><span class="sxs-lookup"><span data-stu-id="39433-160"><span id="Translate"></span><span id="translate"></span><span id="TRANSLATE"></span>Translate</span></span>


<span data-ttu-id="39433-161">Die folgende Gleichung übersetzt den Punkt (x, y, z) zu einem neuen Punkt (x', y', z').</span><span class="sxs-lookup"><span data-stu-id="39433-161">The following equation translates the point (x, y, z) to a new point (x', y', z').</span></span>

![Gleichung einer Übersetzungsmatrix für einen neuen Punkt](images/transl8.png)

<span data-ttu-id="39433-163">Sie können eine Übersetzungsmatrix manuell in C++ erstellen.</span><span class="sxs-lookup"><span data-stu-id="39433-163">You can manually create a translation matrix in C++.</span></span> <span data-ttu-id="39433-164">Das folgende Beispiel zeigt den Quellcode für eine Funktion, die eine Matrix zum Übersetzen von Scheitelpunkten erstellt.</span><span class="sxs-lookup"><span data-stu-id="39433-164">The following example shows the source code for a function that creates a matrix to translate vertices.</span></span>

```
D3DXMATRIX Translate(const float dx, const float dy, const float dz) {
    D3DXMATRIX ret;

    D3DXMatrixIdentity(&ret);
    ret(3, 0) = dx;
    ret(3, 1) = dy;
    ret(3, 2) = dz;
    return ret;
}    // End of Translate
```

## <a name="span-idscalespanspan-idscalespanspan-idscalespanscale"></a><span data-ttu-id="39433-165"><span id="Scale"></span><span id="scale"></span><span id="SCALE"></span>Skalieren</span><span class="sxs-lookup"><span data-stu-id="39433-165"><span id="Scale"></span><span id="scale"></span><span id="SCALE"></span>Scale</span></span>


<span data-ttu-id="39433-166">Die folgende Gleichung skaliert den Punkt (x, y, z), um beliebige Werte in der x-, y- und z-Richtung zu einem neuen Punkt (x', y', z').</span><span class="sxs-lookup"><span data-stu-id="39433-166">The following equation scales the point (x, y, z) by arbitrary values in the x-, y-, and z-directions to a new point (x', y', z').</span></span>

![Gleichung für eine Skalierungsmatrix für einen neuen Punkt](images/matscale.png)

## <a name="span-idrotatespanspan-idrotatespanspan-idrotatespanrotate"></a><span data-ttu-id="39433-168"><span id="Rotate"></span><span id="rotate"></span><span id="ROTATE"></span>Drehen</span><span class="sxs-lookup"><span data-stu-id="39433-168"><span id="Rotate"></span><span id="rotate"></span><span id="ROTATE"></span>Rotate</span></span>


<span data-ttu-id="39433-169">Die hier beschriebenen Transformationen sind für linkshändige Koordinatensysteme gedacht und unterscheiden sich daher möglicherweise von Transformationsmatrizen, die Sie anderswo gesehen haben könnten.</span><span class="sxs-lookup"><span data-stu-id="39433-169">The transforms described here are for left-handed coordinate systems, and so may be different from transform matrices that you have seen elsewhere.</span></span>

<span data-ttu-id="39433-170">Die folgende Gleichung dreht den Punkt (x, y, z) um die x-Achse und erzeugt so einen neuen Punkt (x', y', z').</span><span class="sxs-lookup"><span data-stu-id="39433-170">The following equation rotates the point (x, y, z) around the x-axis, producing a new point (x', y', z').</span></span>

![Gleichung einer x-Drehungsmatrix für einen neuen Punkt](images/matxrot.png)

<span data-ttu-id="39433-172">Die folgende Gleichung dreht den Punkt um die y-Achse.</span><span class="sxs-lookup"><span data-stu-id="39433-172">The following equation rotates the point around the y-axis.</span></span>

![Gleichung einer y-Drehungsmatrix für einen neuen Punkt](images/matyrot.png)

<span data-ttu-id="39433-174">Die folgende Gleichung dreht den Punkt um die z-Achse.</span><span class="sxs-lookup"><span data-stu-id="39433-174">The following equation rotates the point around the z-axis.</span></span>

![Gleichung einer z-Drehungsmatrix für einen neuen Punkt](images/matzrot.png)

<span data-ttu-id="39433-176">In diesen Beispielmatrizen steht der griechische Buchstabe Theta für den Drehwinkel (in Bogenmaß).</span><span class="sxs-lookup"><span data-stu-id="39433-176">In these example matrices, the Greek letter theta stands for the angle of rotation, in radians.</span></span> <span data-ttu-id="39433-177">Winkel werden im Uhrzeigersinn entlang der Drehachse zum Ursprung gemessen.</span><span class="sxs-lookup"><span data-stu-id="39433-177">Angles are measured clockwise when looking along the rotation axis toward the origin.</span></span>

<span data-ttu-id="39433-178">Der folgende Code zeigt eine Funktion für die Drehung um die x-Achse.</span><span class="sxs-lookup"><span data-stu-id="39433-178">The following code shows a function to handle rotation about the X axis.</span></span>

```
    // Inputs are a pointer to a matrix (pOut) and an angle in radians.
    float sin, cos;
    sincosf(angle, &sin, &cos);  // Determine sin and cos of angle

    pOut->_11 = 1.0f; pOut->_12 =  0.0f;   pOut->_13 = 0.0f; pOut->_14 = 0.0f;
    pOut->_21 = 0.0f; pOut->_22 =  cos;    pOut->_23 = sin;  pOut->_24 = 0.0f;
    pOut->_31 = 0.0f; pOut->_32 = -sin;    pOut->_33 = cos;  pOut->_34 = 0.0f;
    pOut->_41 = 0.0f; pOut->_42 =  0.0f;   pOut->_43 = 0.0f; pOut->_44 = 1.0f;

    return pOut;
}
```

## <a name="span-idconcatenatingmatricesspanspan-idconcatenatingmatricesspanspan-idconcatenatingmatricesspanconcatenating-matrices"></a><span data-ttu-id="39433-179"><span id="Concatenating_Matrices"></span><span id="concatenating_matrices"></span><span id="CONCATENATING_MATRICES"></span>Verketten von Matrizen</span><span class="sxs-lookup"><span data-stu-id="39433-179"><span id="Concatenating_Matrices"></span><span id="concatenating_matrices"></span><span id="CONCATENATING_MATRICES"></span>Concatenating Matrices</span></span>


<span data-ttu-id="39433-180">Ein Vorteil der Verwendung von Matrizen ist, dass die Effekte von zwei oder mehr Matrizen kombiniert werden können, indem Sie sie multiplizieren.</span><span class="sxs-lookup"><span data-stu-id="39433-180">One advantage of using matrices is that you can combine the effects of two or more matrices by multiplying them.</span></span> <span data-ttu-id="39433-181">Dies bedeutet, dass Sie nicht zwei Matrizen verwenden müssen, um ein Modell zu drehen und dann zu einem bestimmten Ort zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="39433-181">This means that, to rotate a model and then translate it to some location, you don't need to apply two matrices.</span></span> <span data-ttu-id="39433-182">Stattdessen multiplizieren Sie die Drehungs- und Übersetzungsmatrizen und erzeugen so eine kombinierte Matrix, die alle diese Effekte enthält.</span><span class="sxs-lookup"><span data-stu-id="39433-182">Instead, you multiply the rotation and translation matrices to produce a composite matrix that contains all their effects.</span></span> <span data-ttu-id="39433-183">Dieser Vorgang wird als Matrixverkettung bezeichnet und kann mit der folgenden Gleichung geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="39433-183">This process, called matrix concatenation, can be written with the following equation.</span></span>

![Gleichung für die Matrixverkettung](images/matrxcat.png)

<span data-ttu-id="39433-185">In dieser Gleichung ist C die kombinierte Matrix, die erstellt wird, und M₁ bis Mₙ sind die einzelnen Matrizen.</span><span class="sxs-lookup"><span data-stu-id="39433-185">In this equation, C is the composite matrix being created, and M₁ through Mₙ are the individual matrices.</span></span> <span data-ttu-id="39433-186">In den meisten Fällen werden nur zwei oder drei Matrizen verkettet, es gibt aber keine Beschränkung.</span><span class="sxs-lookup"><span data-stu-id="39433-186">In most cases, only two or three matrices are concatenated, but there is no limit.</span></span>

<span data-ttu-id="39433-187">Die Reihenfolge, in der die Matrixmultiplikation durchgeführt wird, ist entscheidend.</span><span class="sxs-lookup"><span data-stu-id="39433-187">The order in which the matrix multiplication is performed is crucial.</span></span> <span data-ttu-id="39433-188">Die oben aufgeführte Formel gibt die Links-nach-Rechts-Regel für die Matrixverkettung wieder.</span><span class="sxs-lookup"><span data-stu-id="39433-188">The preceding formula reflects the left-to-right rule of matrix concatenation.</span></span> <span data-ttu-id="39433-189">Dies bedeutet, dass die sichtbaren Effekte der Matrizen, aus denen Sie eine kombinierte Matrix erstellen, von links nach rechts auftreten.</span><span class="sxs-lookup"><span data-stu-id="39433-189">That is, the visible effects of the matrices that you use to create a composite matrix occur in left-to-right order.</span></span> <span data-ttu-id="39433-190">Das folgende Beispiel zeigt eine typische Weltmatrix.</span><span class="sxs-lookup"><span data-stu-id="39433-190">A typical world matrix is shown in the following example.</span></span> <span data-ttu-id="39433-191">Stellen Sie sich vor, dass Sie die Weltmatrix für eine klischeehafte fliegende Untertasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="39433-191">Imagine that you are creating the world matrix for a stereotypical flying saucer.</span></span> <span data-ttu-id="39433-192">Möglicherweise soll diese sich um ihren Mittelpunkt drehen – die y-Achse des Modellbereichs – und an einen anderen Ort in Ihrer Szene übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="39433-192">You would probably want to spin the flying saucer around its center - the y-axis of model space - and translate it to some other location in your scene.</span></span> <span data-ttu-id="39433-193">Um diesen Effekt zu erzielen, erstellen Sie zuerst eine Drehungsmatrix und multiplizieren diese dann mit einer Übersetzungsmatrix, wie in der folgenden Gleichung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="39433-193">To accomplish this effect, you first create a rotation matrix, and then multiply it by a translation matrix, as shown in the following equation.</span></span>

![Gleichung einer auf einer Drehungsmatrix und einer Übersetzungsmatrix basieRendern Rotation](images/wrldexpl.png)

<span data-ttu-id="39433-195">In dieser Formel ist R<sub>y</sub> eine Matrix für die Drehung um die y-Achse, und T<sub>w</sub> ist eine Übersetzung zu einer Position in Weltkoordinaten.</span><span class="sxs-lookup"><span data-stu-id="39433-195">In this formula, R<sub>y</sub> is a matrix for rotation about the y-axis, and T<sub>w</sub> is a translation to some position in world coordinates.</span></span>

<span data-ttu-id="39433-196">Die Reihenfolge, in der Sie die Matrizen multiplizieren, ist wichtig, da die Matrix-Multiplikation (anders als die Multiplikation zweier skalarer Werte) nicht kommutativ ist.</span><span class="sxs-lookup"><span data-stu-id="39433-196">The order in which you multiply the matrices is important because, unlike multiplying two scalar values, matrix multiplication is not commutative.</span></span> <span data-ttu-id="39433-197">Die Multiplikation der Matrizen in umgekehrter Reihenfolge führt zu einem visuellen Effekt, bei dem die fliegende Untertasse an ihre Weltbereichsposition übersetzt wird und dann um den Weltursprungspunkt rotiert.</span><span class="sxs-lookup"><span data-stu-id="39433-197">Multiplying the matrices in the opposite order has the visual effect of translating the flying saucer to its world space position, and then rotating it around the world origin.</span></span>

<span data-ttu-id="39433-198">Unabhängig davon, welche Art von Matrix Sie erstellen: Beachten Sie immer die Links-nach-Rechts-Regel, um sicherzustellen, dass Sie die gewünschten Effekte erzielen.</span><span class="sxs-lookup"><span data-stu-id="39433-198">No matter what type of matrix you are creating, remember the left-to-right rule to ensure that you achieve the expected effects.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="39433-199"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="39433-199"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="39433-200">Transformationen</span><span class="sxs-lookup"><span data-stu-id="39433-200">Transforms</span></span>](transforms.md)

 

 




