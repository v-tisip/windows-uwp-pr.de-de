---
title: Rechtecke
description: In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm in Bezug auf die umgebenden Rechtecke bezeichnet.
ms.assetid: 3B78AE66-2C1A-4191-BDCA-D737E33460BA
keywords:
- Rechtecke
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: aa94eb00058ba3297e7ca7cc4f93581d9281fd1c
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8749855"
---
# <a name="rectangles"></a><span data-ttu-id="b4bdf-104">Rechtecke</span><span class="sxs-lookup"><span data-stu-id="b4bdf-104">Rectangles</span></span>


<span data-ttu-id="b4bdf-105">In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm als umgebende Rechtecke bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-105">Throughout Direct3D and Windows programming, objects on the screen are referred to in terms of bounding rectangles.</span></span> <span data-ttu-id="b4bdf-106">Die Seiten des umgebenden Rechtecks sind immer parallel zu den Seiten des Bildschirms. So kann das Rechteck mit zwei Punkten, nämlich der obere linke Ecke und der unteren rechten Ecke, beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-106">The sides of a bounding rectangle are always parallel to the sides of the screen, so the rectangle can be described by two points, the upper-left corner and lower-right corner.</span></span>

## <a name="span-idboundingrectanglesspanspan-idboundingrectanglesspanspan-idboundingrectanglesspanbounding-rectangles"></a><span data-ttu-id="b4bdf-107"><span id="Bounding_rectangles"></span><span id="bounding_rectangles"></span><span id="BOUNDING_RECTANGLES"></span>Umgebende Rechtecke</span><span class="sxs-lookup"><span data-stu-id="b4bdf-107"><span id="Bounding_rectangles"></span><span id="bounding_rectangles"></span><span id="BOUNDING_RECTANGLES"></span>Bounding rectangles</span></span>


<span data-ttu-id="b4bdf-108">Die meisten Anwendungen verwenden die [**RECT**](https://msdn.microsoft.com/library/windows/desktop/dd162897)-Struktur (oder ein Typedef-Alias) als Träger von Informationen über ein umgebendes Rechteck, die beim Blitten auf den Bildschirm oder bei der Trefferermittlung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-108">Most applications use the [**RECT**](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure (or a typedef'd alias for it) to carry information about a bounding rectangle to use when blitting to the screen or when performing hit detection.</span></span> <span data-ttu-id="b4bdf-109">In C++ die **RECT** Struktur hat folgende Definition.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-109">In C++, the **RECT** structure has the following definition.</span></span>

```
typedef struct tagRECT { 
    LONG    left;    // This is the upper-left corner x-coordinate.
    LONG    top;     // The upper-left corner y-coordinate.
    LONG    right;   // The lower-right corner x-coordinate.
    LONG    bottom;  // The lower-right corner y-coordinate.
} RECT, *PRECT, NEAR *NPRECT, FAR *LPRECT; 
```

<span data-ttu-id="b4bdf-110">In diesem Beispiel bilden die linken und oberen Elemente die x- und y-Koordinaten für die linke obere Ecke des umgebenden Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-110">In the preceding example, the left and top members are the x- and y-coordinates of a bounding rectangle's upper-left corner.</span></span> <span data-ttu-id="b4bdf-111">Entsprechend bilden die rechten und unteren Elemente die Koordinaten der unteren rechten Ecke.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-111">Similarly, the right and bottom members make up the coordinates of the lower-right corner.</span></span> <span data-ttu-id="b4bdf-112">Die folgende Abbildungzeigt, wie Sie diese Werte darstellen können.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-112">The following illustration shows how you can visualize these values.</span></span>

![Abbildungdes durch die linken, oberen, rechten und unteren Werte begrenzten umgebenden Rechtecks](images/rect.png)

<span data-ttu-id="b4bdf-114">Die Pixelspalte am rechten Rand sowie die Pixelzeile am unteren Rand sind nicht im RECT enthalten.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-114">The column of pixels at the right edge and the row of pixels at the bottom edge are not included in the RECT.</span></span> <span data-ttu-id="b4bdf-115">Das Sperren eines RECT mit den Elementen {10, 10, 138, 138} ergibt ein Objekt, das 128Pixel breit und hoch ist.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-115">For example, locking a RECT with members {10, 10, 138, 138} results in an object 128 pixels in width and height.</span></span>

<span data-ttu-id="b4bdf-116">Für erhöhte Effizienz, Konsistenz und Bedienerfreundlichkeit arbeiten alle Direct3D-Darstellungsfunktionen mit Rechtecken.</span><span class="sxs-lookup"><span data-stu-id="b4bdf-116">For efficiency, consistency, and ease of use, all Direct3D presentation functions work with rectangles.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="b4bdf-117"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b4bdf-117"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="b4bdf-118">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="b4bdf-118">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




