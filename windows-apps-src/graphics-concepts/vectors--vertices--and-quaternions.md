---
title: Vektoren, Scheitelpunkte und Quaternionen
description: In Direct3D beschreiben Scheitelpunkte die Position und Ausrichtung. Jeder Scheitelpunkt in einem Grundtyp wird durch einen Vektor, der seine Position, Farbe, Textur und Koordinaten angibt, sowie einen normalen Vektor für seine Ausrichtung beschrieben.
ms.assetid: 94EC3D59-43FC-4509-A233-916E9FA8381E
keywords:
- Vektoren, Scheitelpunkte und Quaternionen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 2373d18b51015652bc1ef3035402e1da95a54abf
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7563494"
---
# <a name="vectors-vertices-and-quaternions"></a><span data-ttu-id="0cffa-105">Vektoren, Scheitelpunkte und Quaternionen</span><span class="sxs-lookup"><span data-stu-id="0cffa-105">Vectors, vertices, and quaternions</span></span>


<span data-ttu-id="0cffa-106">In Direct3D beschreiben Scheitelpunkte die Position und Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="0cffa-106">Throughout Direct3D, vertices describe position and orientation.</span></span> <span data-ttu-id="0cffa-107">Jeder Scheitelpunkt in einem Grundtyp wird durch einen Vektor, der seine Position, Farbe, Textur und Koordinaten angibt, sowie einen normalen Vektor für seine Ausrichtung beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0cffa-107">Each vertex in a primitive is described by a vector that gives its position, color, texture coordinates, and a normal vector that gives its orientation.</span></span>

<span data-ttu-id="0cffa-108">Quaternionen fügen ein viertes Element zu den \[x, y, Z\]-Werten hinzu, die einen Drei-Komponenten-Vektor definieren.</span><span class="sxs-lookup"><span data-stu-id="0cffa-108">Quaternions add a fourth element to the \[x, y, z\] values that define a three-component-vector.</span></span> <span data-ttu-id="0cffa-109">Quaternionen sind eine Alternative zu Matrix-Methoden, die in der Regel für 3D -Drehungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0cffa-109">Quaternions are an alternative to the matrix methods that are typically used for 3D rotations.</span></span> <span data-ttu-id="0cffa-110">Ein Quaternion repräsentiert eine Achse im 3D-Raum sowie eine Drehung um diese Achse.</span><span class="sxs-lookup"><span data-stu-id="0cffa-110">A quaternion represents an axis in 3D space and a rotation around that axis.</span></span> <span data-ttu-id="0cffa-111">Beispielsweise kann ein Quaternion eine (1,1,2)-Achse und eine Drehung um ein Bogenmaß repräsentieren.</span><span class="sxs-lookup"><span data-stu-id="0cffa-111">For example, a quaternion might represent a (1,1,2) axis and a rotation of 1 radian.</span></span> <span data-ttu-id="0cffa-112">Quaternionen enthalten wertvolle Informationen, ihr wirklicher Nutzen liegt jedoch in zwei Operationen, die Sie mit ihnen durchführen können: Komposition und Interpolation.</span><span class="sxs-lookup"><span data-stu-id="0cffa-112">Quaternions carry valuable information, but their true power comes from the two operations that you can perform on them: composition and interpolation.</span></span>

<span data-ttu-id="0cffa-113">Die Durchführung einer Komposition mit Quaternionen ist vergleichbar mit ihrer Kombinierung.</span><span class="sxs-lookup"><span data-stu-id="0cffa-113">Performing composition on quaternions is similar to combining them.</span></span> <span data-ttu-id="0cffa-114">Die Komposition von zwei Quaternionen wird wie in der folgenden Abbildung gezeigt notiert.</span><span class="sxs-lookup"><span data-stu-id="0cffa-114">The composition of two quaternions is notated like the following illustration.</span></span>

![Illustrationder Quaternionendrehung](images/quateq.png)

<span data-ttu-id="0cffa-116">Die Komposition von zwei Quaternionen für eine Geometrie bedeutet die „Drehung der Geometrie um Ache₂ mit Drehung₂ und anschließend um Achse₁ mit Drehung₁".</span><span class="sxs-lookup"><span data-stu-id="0cffa-116">The composition of two quaternions applied to a geometry means "rotate the geometry around axis₂ by rotation₂, then rotate it around axis₁ by rotation₁."</span></span> <span data-ttu-id="0cffa-117">In diesem Fall ist Q eine Drehung um eine einzelne Achse als Ergebnis der Anwendung von q₂ und dann von q₁ auf die Geometrie.</span><span class="sxs-lookup"><span data-stu-id="0cffa-117">In this case, Q represents a rotation around a single axis that is the result of applying q₂, then q₁ to the geometry.</span></span>

<span data-ttu-id="0cffa-118">Mit der Quaternioneninterpolation kann eine Anwendung einen reibungslosen und angemessenen Übergangspfad von einer Achse und Ausrichtung zu einer anderen berechnen.</span><span class="sxs-lookup"><span data-stu-id="0cffa-118">Using quaternion interpolation, an application can calculate a smooth and reasonable path from one axis and orientation to another.</span></span> <span data-ttu-id="0cffa-119">Daher bietet eine Interpolation zwischen q₁ und q₂ eine einfache Möglichkeit für Animationen von einer Ausrichtung zu einer anderen.</span><span class="sxs-lookup"><span data-stu-id="0cffa-119">Therefore, interpolation between q₁ and q₂ provides a simple way to animate from one orientation to another.</span></span>

<span data-ttu-id="0cffa-120">Wenn Sie Komposition und Interpolation zusammen verwenden, erhalten Sie damit eine einfache Möglichkeit zur Manipulation einer komplex erscheinenden Geometrie.</span><span class="sxs-lookup"><span data-stu-id="0cffa-120">When you use composition and interpolation together, they provide you with a simple way to manipulate a geometry in a manner that appears complex.</span></span> <span data-ttu-id="0cffa-121">Stellen Sie sich beispielsweise vor, dass Sie eine Geometrie haben, die Sie in einer bestimmten Ausrichtung drehen möchten.</span><span class="sxs-lookup"><span data-stu-id="0cffa-121">For example, imagine that you have a geometry that you want to rotate to a given orientation.</span></span> <span data-ttu-id="0cffa-122">Sie wissen, dass Sie sie um r₂ Grad um Achse₂ drehen und anschließend um r₁ Grad um Ache₁ drehen möchten, Sie kennen aber das endgültige Quaternion nicht.</span><span class="sxs-lookup"><span data-stu-id="0cffa-122">You know that you want to rotate it r₂ degrees around axis₂, then rotate it r₁ degrees around axis₁, but you don't know the final quaternion.</span></span> <span data-ttu-id="0cffa-123">Durch Verwendung der Komposition können Sie die zwei Drehungen auf der Geometrie kombinieren, um ein einziges Quaternion als Ergebnis zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0cffa-123">By using composition, you could combine the two rotations on the geometry to get a single quaternion that is the result.</span></span> <span data-ttu-id="0cffa-124">Anschließend können Sie die Interpolation vom ursprünglichen zum komponierten Quaternion durchführen und so einen glatten Übergang zwischen beiden erreichen.</span><span class="sxs-lookup"><span data-stu-id="0cffa-124">Then, you could interpolate from the original to the composed quaternion to achieve a smooth transition from one to the other.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="0cffa-125"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0cffa-125"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="0cffa-126">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="0cffa-126">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




