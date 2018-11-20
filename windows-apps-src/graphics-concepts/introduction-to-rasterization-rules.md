---
title: Einführung in die Regeln für die Rasterung
description: Häufig entsprechend die Punkte von Vertizes nicht exakt den Pixel auf dem Bildschirm. Wenn dieser Fall eintritt, verwendet Direct3D Dreiecksrasterregeln, um zu entscheiden, welche Pixel für ein vorhandenes Dreieck gelten.
ms.assetid: 4232CDBA-F669-4417-9378-F9013E83462C
keywords:
- Einführung in die Regeln für die Rasterung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 65522195b9729ddd4f2ebeb193f43c905359eda2
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7293592"
---
# <a name="introduction-to-rasterization-rules"></a><span data-ttu-id="e46b8-105">Einführung in die Regeln für die Rasterung</span><span class="sxs-lookup"><span data-stu-id="e46b8-105">Introduction to rasterization rules</span></span>


<span data-ttu-id="e46b8-106">Häufig entsprechend die Punkte von Vertizes nicht exakt den Pixel auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e46b8-106">Often, the points specified for vertices do not precisely match the pixels on the screen.</span></span> <span data-ttu-id="e46b8-107">Wenn dieser Fall eintritt, verwendet Direct3D Dreiecksrasterregeln, um zu entscheiden, welche Pixel für ein vorhandenes Dreieck gelten.</span><span class="sxs-lookup"><span data-stu-id="e46b8-107">When this happens, Direct3D applies triangle rasterization rules to decide which pixels apply to a given triangle.</span></span>

<span data-ttu-id="e46b8-108">Es folgt eine vereinfachte Einführung in die Regeln für die Rasterung.</span><span class="sxs-lookup"><span data-stu-id="e46b8-108">This is a simplified introduction to rasterization rules.</span></span> <span data-ttu-id="e46b8-109">Weitere Einzelheiten finden Sie unter [Regeln für die Rasterung](rasterization-rules.md).</span><span class="sxs-lookup"><span data-stu-id="e46b8-109">For more details, see [Rasterization rules](rasterization-rules.md).</span></span> <span data-ttu-id="e46b8-110">Siehe auch [Rasterizerphase (RS)](rasterizer-stage--rs-.md).</span><span class="sxs-lookup"><span data-stu-id="e46b8-110">See also [Rasterizer (RS) stage](rasterizer-stage--rs-.md).</span></span>

## <a name="span-idtrianglerasterizationrulesspanspan-idtrianglerasterizationrulesspanspan-idtrianglerasterizationrulesspantriangle-rasterization-rules"></a><span data-ttu-id="e46b8-111"><span id="Triangle_Rasterization_Rules"></span><span id="triangle_rasterization_rules"></span><span id="TRIANGLE_RASTERIZATION_RULES"></span>Regeln für das Dreiecksraster</span><span class="sxs-lookup"><span data-stu-id="e46b8-111"><span id="Triangle_Rasterization_Rules"></span><span id="triangle_rasterization_rules"></span><span id="TRIANGLE_RASTERIZATION_RULES"></span>Triangle Rasterization Rules</span></span>


<span data-ttu-id="e46b8-112">Direct3D verwendet für die Füllgeometrie eine Oben-Links-Füllkonvention.</span><span class="sxs-lookup"><span data-stu-id="e46b8-112">Direct3D uses a top-left filling convention for filling geometry.</span></span> <span data-ttu-id="e46b8-113">Es handelt sich hierbei um die gleiche Konvention, die in GDI und OpenGL für Rechtecke verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e46b8-113">This is the same convention that is used for rectangles in GDI and OpenGL.</span></span> <span data-ttu-id="e46b8-114">In Direct3D ist der Mittelpunkt eines Pixels der entscheidende Punkt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-114">In Direct3D, the center of the pixel is the decisive point.</span></span> <span data-ttu-id="e46b8-115">Wenn der Mittelpunkt in einem Dreieck liegt, ist das Pixel Teil des Dreiecks.</span><span class="sxs-lookup"><span data-stu-id="e46b8-115">If the center is inside a triangle, the pixel is part of the triangle.</span></span> <span data-ttu-id="e46b8-116">Die Mittelpunkte der Pixel liegen auf ganzzahligen Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="e46b8-116">Pixel centers are at integer coordinates.</span></span>

<span data-ttu-id="e46b8-117">Die Beschreibung der von Direct3D verwendeten Dreiecksrasterregeln gilt nicht automatisch für jede verfügbare Hardware.</span><span class="sxs-lookup"><span data-stu-id="e46b8-117">This description of triangle-rasterization rules used by Direct3D does not necessarily apply to all available hardware.</span></span> <span data-ttu-id="e46b8-118">Beim Testen werden Sie unter Umständen minimale Abweichungen in der Implementierung dieser Regeln aufdecken.</span><span class="sxs-lookup"><span data-stu-id="e46b8-118">Your testing may uncover minor variations in the implementation of these rules.</span></span>

<span data-ttu-id="e46b8-119">In der folgenden Abbildung wird ein Rechteck dargestellt, dessen obere linke Ecke bei (0, 0) liegt und dessen untere Rechte Ecke bei (5, 5) liegt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-119">The following illustration shows a rectangle whose upper-left corner is at (0, 0) and whose lower-right corner is at (5, 5).</span></span> <span data-ttu-id="e46b8-120">Dieses Rechteck füllt, genau wie erwartet, 25 Pixel.</span><span class="sxs-lookup"><span data-stu-id="e46b8-120">This rectangle fills 25 pixels, just as you would expect.</span></span> <span data-ttu-id="e46b8-121">Die Breite des Rechtecks wird durch „Rechts minus Links“ definiert.</span><span class="sxs-lookup"><span data-stu-id="e46b8-121">The width of the rectangle is defined as right minus left.</span></span> <span data-ttu-id="e46b8-122">Die Höhe wird durch „Unterseite minus Oberseite“ definiert.</span><span class="sxs-lookup"><span data-stu-id="e46b8-122">The height is defined as bottom minus top.</span></span>

![ein nummeriertes Viereck, unterteilt in sechs Reihen und Spalten.](images/pixmap.png)

<span data-ttu-id="e46b8-124">Gemäß der Oben-Links-Füllkonvention, bezieht sich *Oben* auf die vertikale Position der horizontalen Struktur und *Links* auf die horizontale Position des Pixels in einer Struktur.</span><span class="sxs-lookup"><span data-stu-id="e46b8-124">In the top-left filling convention, *top* refers to the vertical location of horizontal spans, and *left* refers to the horizontal location of pixels within a span.</span></span> <span data-ttu-id="e46b8-125">Bei einer Kante kann es sich nicht um eine Oberkante handeln, wenn sie nicht horizontal liegt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-125">An edge cannot be a top edge unless it is horizontal.</span></span> <span data-ttu-id="e46b8-126">Grundsätzlich haben die meisten Dreiecke nur linke und rechte Kanten.</span><span class="sxs-lookup"><span data-stu-id="e46b8-126">In general, most triangles have only left and right edges.</span></span> <span data-ttu-id="e46b8-127">In der folgenden Abbildung wird eine Oberkante und eine rechte Kante dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-127">The following illustration shows a top edge and a right edge.</span></span>

![ein nummeriertes Viereck, in dem sich zwei Dreiecke befinden](images/triedge.png)

<span data-ttu-id="e46b8-129">Die Oben-Links-Konvention bestimmt die von Direct3D unternommenen Aktionen, wenn ein Dreieck durch den Mittelpunkt eines Pixels verläuft.</span><span class="sxs-lookup"><span data-stu-id="e46b8-129">The top-left filling convention determines the action taken by Direct3D when a triangle passes through the center of a pixel.</span></span> <span data-ttu-id="e46b8-130">In der folgenden Abbildung werden zwei Dreiecke dargestellt. Eines liegt bei (0, 0), (5, 0) und (5, 5), das andere bei (0, 5), (0, 0) und (5, 5).</span><span class="sxs-lookup"><span data-stu-id="e46b8-130">The following illustration shows two triangles, one at (0, 0), (5, 0), and (5, 5), and the other at (0, 5), (0, 0), and (5, 5).</span></span> <span data-ttu-id="e46b8-131">Das erste Dreieck erhält in diesem Fall 15 Pixel (schwarz dargestellt), wobei das zweite Dreieck nur 10 Pixel (grau dargestellt) erhält, weil die gemeinsame Kante auch die linke Kante des ersten Dreiecks ist.</span><span class="sxs-lookup"><span data-stu-id="e46b8-131">The first triangle in this case gets 15 pixels (shown in black), whereas the second gets only 10 pixels (shown in gray) because the shared edge is the left edge of the first triangle.</span></span>

![ein nummeriertes Viereck mit zwei Dreiecken](images/twotris.png)

<span data-ttu-id="e46b8-133">Wenn Sie ein Rechteck mit der unteren linken Ecke bei (0,5, 0,5) und der unteren rechten Ecke bei (2,5, 4,5) definieren, liegt der Mittelpunkt des Rechtecks bei (1,5, 2,5).</span><span class="sxs-lookup"><span data-stu-id="e46b8-133">If you define a rectangle with its upper-left corner at (0.5, 0.5) and its lower-right corner at (2.5, 4.5), the center point of this rectangle is at (1.5, 2.5).</span></span> <span data-ttu-id="e46b8-134">Wenn der Direct3D-Rasterizer dieses Rechteck tesseliert, liegt der Mittelpunkt eines jeden Pixels eindeutig innerhalb jedem der vier Dreiecke, und die Oben-Links-Konvention ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e46b8-134">When the Direct3D rasterizer tessellates this rectangle, the center of each pixel is unambiguously inside each of the four triangles, and the top-left filling convention is not needed.</span></span> <span data-ttu-id="e46b8-135">Die folgende Abbildung stellt dies dar.</span><span class="sxs-lookup"><span data-stu-id="e46b8-135">The following illustration shows this.</span></span> <span data-ttu-id="e46b8-136">Die Pixel im Rechteck werden gemäß dem Dreieck bezeichnet, dem Direct3D sie zuordnet.</span><span class="sxs-lookup"><span data-stu-id="e46b8-136">The pixels in the rectangle are labeled according to the triangle in which Direct3D includes them.</span></span>

![ein nummeriertes Viereck, das ein Rechteck enthält, welches in vier Dreiecke unterteilt ist](images/noambig.png)

<span data-ttu-id="e46b8-138">Wenn Sie das Rechteck aus der vorherigen Abbildung verschieben, so dass die linke obere Ecke bei (1,0, 1,0), die untere rechte Ecke bei (3,0, 5,0) und der Mittelpunkt bei (2,0, 3,0) liegen, wendet Direct3D die Oben-Links-Konvention an.</span><span class="sxs-lookup"><span data-stu-id="e46b8-138">If you move the rectangle in the preceding illustration so that its upper-left corner is at (1.0, 1.0), its lower-right corner at (3.0, 5.0), and its center point at (2.0, 3.0), Direct3D applies the top-left filling convention.</span></span> <span data-ttu-id="e46b8-139">Die meisten Pixel in diesem Rechteck überspannen die Grenze zwischen zwei oder mehr Dreiecken, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-139">Most pixels in this rectangle straddle the border between two or more triangles, as the following illustration shows.</span></span>

![ein nummeriertes Viereck, das ein Rechteck enthält, welches in vier Dreiecke unterteilt ist](images/fillrule.png)

<span data-ttu-id="e46b8-141">Für die beiden Rechtecke sind die gleichen Pixel betroffen, wie in folgender Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e46b8-141">For both rectangles, the same pixels are affected, as shown in the following illustration.</span></span>

![Pixel, die für die beiden vorherigen nummerierten Vierecke gelten](images/samepix.png)

## <a name="span-idpointandlinerulesspanspan-idpointandlinerulesspanspan-idpointandlinerulesspanpoint-and-line-rules"></a><span data-ttu-id="e46b8-143"><span id="Point_and_Line_Rules"></span><span id="point_and_line_rules"></span><span id="POINT_AND_LINE_RULES"></span>Punkt- und Linienregeln</span><span class="sxs-lookup"><span data-stu-id="e46b8-143"><span id="Point_and_Line_Rules"></span><span id="point_and_line_rules"></span><span id="POINT_AND_LINE_RULES"></span>Point and Line Rules</span></span>


<span data-ttu-id="e46b8-144">Punkte werden auf die gleiche Weise gerendert wie Punkt-Sprites, welche beide als am Bildschirm ausgerichtete Vierecke gerendert werden und deshalb den gleichen Regeln wie beim Polygon-Rendering unterliegen.</span><span class="sxs-lookup"><span data-stu-id="e46b8-144">Points are rendered the same as point sprites, which are both rendered as screen-aligned quadrilaterals and thus adhere to the same rules as polygon rendering.</span></span>

<span data-ttu-id="e46b8-145">Die Rendering-Regeln für nicht geglättete Linien stimmen exakt mit denen für [GDI lines](https://msdn.microsoft.com/library/windows/desktop/dd145027) überein.</span><span class="sxs-lookup"><span data-stu-id="e46b8-145">Non-antialiased line rendering rules are exactly the same as those for [GDI lines](https://msdn.microsoft.com/library/windows/desktop/dd145027).</span></span>

## <a name="span-idpointspriterulesspanspan-idpointspriterulesspanspan-idpointspriterulesspanpoint-sprite-rules"></a><span data-ttu-id="e46b8-146"><span id="Point_Sprite_Rules"></span><span id="point_sprite_rules"></span><span id="POINT_SPRITE_RULES"></span>Punkt-Sprite-Regeln</span><span class="sxs-lookup"><span data-stu-id="e46b8-146"><span id="Point_Sprite_Rules"></span><span id="point_sprite_rules"></span><span id="POINT_SPRITE_RULES"></span>Point Sprite Rules</span></span>


<span data-ttu-id="e46b8-147">Punkt-Sprites und Patch-Grundtypen sind gerastert, da die Grundtypen zuerst in Dreiecke tesseliert, und die daraus entstehenden Dreiecke dann gerastert werden.</span><span class="sxs-lookup"><span data-stu-id="e46b8-147">Point sprites and patch primitives are rasterized as if the primitives were first tessellated into triangles and the resulting triangles rasterized.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e46b8-148"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e46b8-148"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e46b8-149">Geräte</span><span class="sxs-lookup"><span data-stu-id="e46b8-149">Devices</span></span>](devices.md)

[<span data-ttu-id="e46b8-150">Rasterizerphase (RS)</span><span class="sxs-lookup"><span data-stu-id="e46b8-150">Rasterizer (RS) stage</span></span>](rasterizer-stage--rs-.md)

[<span data-ttu-id="e46b8-151">Regeln für die Rasterung</span><span class="sxs-lookup"><span data-stu-id="e46b8-151">Rasterization rules</span></span>](rasterization-rules.md)

 

 




