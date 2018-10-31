---
title: Grundtypen
description: Ein 3D-Grundtyp ist eine Sammlung von Scheitelpunkten, die eine einzelne 3D-Entität bilden.
ms.assetid: A1FE6F49-B0D4-4665-90E1-40AD98E668B1
keywords:
- Grundtypen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 349d4aa4fbf35bd7dccbd48b0251f5bb9e90a779
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5860327"
---
# <a name="primitives"></a><span data-ttu-id="1f3e4-104">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="1f3e4-104">Primitives</span></span>


<span data-ttu-id="1f3e4-105">Ein 3D-*Grundtyp* ist eine Sammlung von Scheitelpunkten, die eine einzelne 3D-Entität bilden.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-105">A 3D *primitive* is a collection of vertices that form a single 3D entity.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="1f3e4-106"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="1f3e4-106"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1f3e4-107">Thema</span><span class="sxs-lookup"><span data-stu-id="1f3e4-107">Topic</span></span></th>
<th align="left"><span data-ttu-id="1f3e4-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f3e4-108">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="point-lists.md"><span data-ttu-id="1f3e4-109">Punktelisten</span><span class="sxs-lookup"><span data-stu-id="1f3e4-109">Point lists</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1f3e4-110">Eine Punkteliste ist eine Sammlung von Scheitelpunkten, die als isolierte Punkte dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-110">A point list is a collection of vertices that are rendered as isolated points.</span></span> <span data-ttu-id="1f3e4-111">Die Anwendung kann Punktelisten in 3D-Szenen für Sternenfelder oder gepunktete Linien auf der Oberfläche eines Polygons verwenden.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-111">Your application can use point lists in 3D scenes for star fields, or dotted lines on the surface of a polygon.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="line-lists.md"><span data-ttu-id="1f3e4-112">Zeilenlisten</span><span class="sxs-lookup"><span data-stu-id="1f3e4-112">Line lists</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1f3e4-113">Bei einer Zeilenliste handelt es sich um eine Liste isolierter, gerader Liniensegmente.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-113">A line list is a list of isolated, straight line segments.</span></span> <span data-ttu-id="1f3e4-114">Zeilenlisten sind hilfreich für Aufgaben wie das Hinzufügen von Schneeregen oder Starkregen zu einer 3D-Szene.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-114">Line lists are useful for such tasks as adding sleet or heavy rain to a 3D scene.</span></span> <span data-ttu-id="1f3e4-115">Anwendungen erstellen eine Zeilenliste, indem sie eine Reihe von Scheitelpunkten ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-115">Applications create a line list by filling an array of vertices.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="line-strips.md"><span data-ttu-id="1f3e4-116">Zeilenstrips</span><span class="sxs-lookup"><span data-stu-id="1f3e4-116">Line strips</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1f3e4-117">Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Liniensegmenten besteht.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-117">A line strip is a primitive that is composed of connected line segments.</span></span> <span data-ttu-id="1f3e4-118">Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-118">Your application can use line strips for creating polygons that are not closed.</span></span> <span data-ttu-id="1f3e4-119">Bei einem geschlossenes Polygon handelt es sich um ein Polygon, dessen letzter Scheitelpunkt über ein Liniensegment mit dem ersten Scheitelpunkt verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-119">A closed polygon is a polygon whose last vertex is connected to its first vertex by a line segment.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="triangle-lists.md"><span data-ttu-id="1f3e4-120">Dreieckslisten</span><span class="sxs-lookup"><span data-stu-id="1f3e4-120">Triangle lists</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1f3e4-121">Eine Dreiecksliste ist eine Liste isolierter Dreiecke.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-121">A triangle list is a list of isolated triangles.</span></span> <span data-ttu-id="1f3e4-122">Die isolierten Dreiecke können sich nahe beieinander befinden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-122">The isolated triangles might or might not be near each other.</span></span> <span data-ttu-id="1f3e4-123">Eine Dreiecksliste muss mindestens drei Scheitelpunkte enthalten, und die Gesamtzahl der Scheitelpunkte muss durch drei teilbar sein.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-123">A triangle list must have at least three vertices and the total number of vertices must be divisible by three.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="triangle-strips.md"><span data-ttu-id="1f3e4-124">Dreiecksstrips</span><span class="sxs-lookup"><span data-stu-id="1f3e4-124">Triangle strips</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1f3e4-125">Ein Dreiecksstrip ist eine Reihe verbundener Dreiecke.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-125">A triangle strip is a series of connected triangles.</span></span> <span data-ttu-id="1f3e4-126">Da die Dreiecke verbunden sind, muss die Anwendung nicht immer wieder alle drei Scheitelpunkte für alle Dreiecke angeben.</span><span class="sxs-lookup"><span data-stu-id="1f3e4-126">Because the triangles are connected, the application does not need to repeatedly specify all three vertices for each triangle.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1f3e4-127"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1f3e4-127"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1f3e4-128">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="1f3e4-128">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




