---
title: Transformationen
description: Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.
ms.assetid: 0DF2A99A-335C-4D14-9720-6D7996DD635A
keywords:
- Transformationen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a29d42a9254ca47402a38ea71c8c1ef69de5c6c7
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8744202"
---
# <a name="transforms"></a><span data-ttu-id="72f0f-104">Transformationen</span><span class="sxs-lookup"><span data-stu-id="72f0f-104">Transforms</span></span>


<span data-ttu-id="72f0f-105">Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.</span><span class="sxs-lookup"><span data-stu-id="72f0f-105">The part of Direct3D that pushes geometry through the fixed function geometry pipeline is the transform engine.</span></span> <span data-ttu-id="72f0f-106">Es ermittelt das Modell und die Anzeige im Raum, projiziert Scheitelpunkte für die Anzeige auf den Bildschirm und beschneidet Scheitelpunkte im Viewport.</span><span class="sxs-lookup"><span data-stu-id="72f0f-106">It locates the model and viewer in the world, projects vertices for display on the screen, and clips vertices to the viewport.</span></span> <span data-ttu-id="72f0f-107">Darüber hinaus führt die Transformationsengine Beleuchtungsberechnungen durch, um diffuse und ausgeleuchtete Komponenten der einzelnen Scheitelpunkte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="72f0f-107">The transform engine also performs lighting computations to determine diffuse and specular components at each vertex.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="72f0f-108"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="72f0f-108"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="72f0f-109">Thema</span><span class="sxs-lookup"><span data-stu-id="72f0f-109">Topic</span></span></th>
<th align="left"><span data-ttu-id="72f0f-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="72f0f-110">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="transform-overview.md"><span data-ttu-id="72f0f-111">Übersicht über Transformationen</span><span class="sxs-lookup"><span data-stu-id="72f0f-111">Transform overview</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="72f0f-112">Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="72f0f-112">Matrix transformations handle a lot of the low level math of 3D graphics.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="world-transform.md"><span data-ttu-id="72f0f-113">Welttransformationen</span><span class="sxs-lookup"><span data-stu-id="72f0f-113">World transform</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="72f0f-114">Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich.</span><span class="sxs-lookup"><span data-stu-id="72f0f-114">A world transform changes coordinates from model space, where vertices are defined relative to a model's local origin, to world space.</span></span> <span data-ttu-id="72f0f-115">Im Weltbereich werden Scheitelpunkte relativ zu einem Ursprung definiert, der allen Objekten in einer Szene gemeinsam ist.</span><span class="sxs-lookup"><span data-stu-id="72f0f-115">In world space, vertices are defined relative to an origin common to all the objects in a scene.</span></span> <span data-ttu-id="72f0f-116">Die Welt-Transformation platziert ein Modell in der Welt.</span><span class="sxs-lookup"><span data-stu-id="72f0f-116">The world transform places a model into the world.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="view-transform.md"><span data-ttu-id="72f0f-117">Ansichtstransformation</span><span class="sxs-lookup"><span data-stu-id="72f0f-117">View transform</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="72f0f-118">Eine <em>Ansichtstransformation</em> lokalisiert den Betrachter im Weltbereich und transformiert dazu Scheitelpunkte in den Kamerabereich.</span><span class="sxs-lookup"><span data-stu-id="72f0f-118">A <em>view transform</em> locates the viewer in world space, transforming vertices into camera space.</span></span> <span data-ttu-id="72f0f-119">Im Kamerabereich befindet sich die Kamera, bzw. der Betrachter, am Ursprungspunkt und blickt in die positive z-Richtung.</span><span class="sxs-lookup"><span data-stu-id="72f0f-119">In camera space, the camera, or viewer, is at the origin, looking in the positive z-direction.</span></span> <span data-ttu-id="72f0f-120">Die Ansichtsmatrix verschiebt die Objekte in der Welt um die Position einer Kamera - den Ursprung des Kamerabereichs - und ihre Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="72f0f-120">The view matrix relocates the objects in the world around a camera's position - the origin of camera space - and orientation.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="projection-transform.md"><span data-ttu-id="72f0f-121">Projektionstransformation</span><span class="sxs-lookup"><span data-stu-id="72f0f-121">Projection transform</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="72f0f-122">Eine <em>Projektionstransformation</em> steuert die internen Elemente der Kamera, z.B. die Auswahl eines Objektivs für eine Kamera.</span><span class="sxs-lookup"><span data-stu-id="72f0f-122">A <em>projection transformation</em> controls the camera's internals, like choosing a lens for a camera.</span></span> <span data-ttu-id="72f0f-123">Dies ist der komplizierteste der drei Transformationstypen.</span><span class="sxs-lookup"><span data-stu-id="72f0f-123">This is the most complicated of the three transformation types.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="72f0f-124"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="72f0f-124"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="72f0f-125">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="72f0f-125">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




