---
title: Transformationen
description: "Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine."
ms.assetid: 0DF2A99A-335C-4D14-9720-6D7996DD635A
keywords: Transformationen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: e5eb63a41ad04577196b6a622736211c1d1576f9
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="transforms"></a><span data-ttu-id="c9ac5-104">Transformationen</span><span class="sxs-lookup"><span data-stu-id="c9ac5-104">Transforms</span></span>


<span data-ttu-id="c9ac5-105">Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-105">The part of Direct3D that pushes geometry through the fixed function geometry pipeline is the transform engine.</span></span> <span data-ttu-id="c9ac5-106">Es ermittelt das Modell und die Anzeige im Raum, projiziert Scheitelpunkte für die Anzeige auf den Bildschirm und beschneidet Scheitelpunkte im Viewport.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-106">It locates the model and viewer in the world, projects vertices for display on the screen, and clips vertices to the viewport.</span></span> <span data-ttu-id="c9ac5-107">Darüber hinaus führt die Transformationsengine Beleuchtungsberechnungen durch, um diffuse und ausgeleuchtete Komponenten der einzelnen Scheitelpunkte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-107">The transform engine also performs lighting computations to determine diffuse and specular components at each vertex.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="c9ac5-108"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="c9ac5-108"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c9ac5-109">Thema</span><span class="sxs-lookup"><span data-stu-id="c9ac5-109">Topic</span></span></th>
<th align="left"><span data-ttu-id="c9ac5-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c9ac5-110">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="c9ac5-111">Übersicht über Transformationen</span><span class="sxs-lookup"><span data-stu-id="c9ac5-111">Transform overview</span></span>](transform-overview.md)</p></td>
<td align="left"><p><span data-ttu-id="c9ac5-112">Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-112">Matrix transformations handle a lot of the low level math of 3D graphics.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="c9ac5-113">Welttransformationen</span><span class="sxs-lookup"><span data-stu-id="c9ac5-113">World transform</span></span>](world-transform.md)</p></td>
<td align="left"><p><span data-ttu-id="c9ac5-114">Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-114">A world transform changes coordinates from model space, where vertices are defined relative to a model's local origin, to world space.</span></span> <span data-ttu-id="c9ac5-115">Im Weltbereich werden Scheitelpunkte relativ zu einem Ursprung definiert, der allen Objekten in einer Szene gemeinsam ist.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-115">In world space, vertices are defined relative to an origin common to all the objects in a scene.</span></span> <span data-ttu-id="c9ac5-116">Die Welt-Transformation platziert ein Modell in der Welt.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-116">The world transform places a model into the world.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="c9ac5-117">Ansichtstransformation</span><span class="sxs-lookup"><span data-stu-id="c9ac5-117">View transform</span></span>](view-transform.md)</p></td>
<td align="left"><p><span data-ttu-id="c9ac5-118">Eine <em>Ansichtstransformation</em> lokalisiert den Betrachter im Weltbereich und transformiert dazu Scheitelpunkte in den Kamerabereich.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-118">A <em>view transform</em> locates the viewer in world space, transforming vertices into camera space.</span></span> <span data-ttu-id="c9ac5-119">Im Kamerabereich befindet sich die Kamera, bzw. der Betrachter, am Ursprungspunkt und blickt in die positive z-Richtung.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-119">In camera space, the camera, or viewer, is at the origin, looking in the positive z-direction.</span></span> <span data-ttu-id="c9ac5-120">Die Ansichtsmatrix verschiebt die Objekte in der Welt um die Position einer Kamera - den Ursprung des Kamerabereichs - und ihre Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-120">The view matrix relocates the objects in the world around a camera's position - the origin of camera space - and orientation.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="c9ac5-121">Projektionstransformation</span><span class="sxs-lookup"><span data-stu-id="c9ac5-121">Projection transform</span></span>](projection-transform.md)</p></td>
<td align="left"><p><span data-ttu-id="c9ac5-122">Eine <em>Projektionstransformation</em> steuert die internen Elemente der Kamera, z.B. die Auswahl eines Objektivs für eine Kamera.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-122">A <em>projection transformation</em> controls the camera's internals, like choosing a lens for a camera.</span></span> <span data-ttu-id="c9ac5-123">Dies ist der komplizierteste der drei Transformationstypen.</span><span class="sxs-lookup"><span data-stu-id="c9ac5-123">This is the most complicated of the three transformation types.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="c9ac5-124"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c9ac5-124"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="c9ac5-125">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="c9ac5-125">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




