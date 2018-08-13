---
title: Welttransformationen
description: Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich.
ms.assetid: 767B032C-69D0-4583-8FEB-247F4C41E31D
keywords:
- Welttransformationen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 1f4d40360833596b9ef9eed97c426a5ec90db353
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1043959"
---
# <a name="world-transform"></a><span data-ttu-id="57b34-104">Welttransformationen</span><span class="sxs-lookup"><span data-stu-id="57b34-104">World transform</span></span>


<span data-ttu-id="57b34-105">Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich.</span><span class="sxs-lookup"><span data-stu-id="57b34-105">A world transform changes coordinates from model space, where vertices are defined relative to a model's local origin, to world space.</span></span> <span data-ttu-id="57b34-106">Im Weltbereich werden Scheitelpunkte relativ zu einem Ursprung definiert, der allen Objekten in einer Szene gemeinsam ist.</span><span class="sxs-lookup"><span data-stu-id="57b34-106">In world space, vertices are defined relative to an origin common to all the objects in a scene.</span></span> <span data-ttu-id="57b34-107">Die Welttransformation platziert ein Modell in der Welt.</span><span class="sxs-lookup"><span data-stu-id="57b34-107">The world transform places a model into the world.</span></span>

## <span id="What_Is_a_World_Transform"></span><span id="what_is_a_world_transform"></span><span id="WHAT_IS_A_WORLD_TRANSFORM"></span>


<span data-ttu-id="57b34-108">Das folgende Diagramm zeigt die Beziehung zwischen dem Weltkoordinatensystem und einem lokalen Koordinatensystem des Modells.</span><span class="sxs-lookup"><span data-stu-id="57b34-108">The following diagram shows the relationship between the world coordinate system and a model's local coordinate system.</span></span>

![Diagramm zur Beziehung zwischen Weltkoordinaten und lokalen Koordinaten](images/worldcrd.png)

<span data-ttu-id="57b34-110">Welttransformationen können eine beliebige Kombination von Übersetzungen, Drehungen und Skalierungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="57b34-110">The world transform can include any combination of translations, rotations, and scalings.</span></span>

## <a name="span-idsettingupaworldmatrixxmlspansetting-up-a-world-matrix"></a><span data-ttu-id="57b34-111"><span id="SETTING_UP_A_WORLD_MATRIX.XML"></span>Einrichten einer Weltmatrix</span><span class="sxs-lookup"><span data-stu-id="57b34-111"><span id="SETTING_UP_A_WORLD_MATRIX.XML"></span>Setting Up a World Matrix</span></span>


<span data-ttu-id="57b34-112">Sie erstellen, wie bei allen anderen Transformationen auch, die Welt, indem Sie eine Reihe von Matrizen zu einer einzelnen Matrix konkatenieren, die die Summe der Effekte der einzelnen Matrizen enthält.</span><span class="sxs-lookup"><span data-stu-id="57b34-112">As with any other transform, create the world transform by concatenating a series of matrices into a single matrix that contains the sum total of their effects.</span></span> <span data-ttu-id="57b34-113">Im einfachste Fall befindet sich ein Modell am Ursprung der Welt, und seine lokalen Koordinatenachsen sind genauso ausgerichtet wie der Raum der Welt. In diesem Fall ist die Weltmatrix die Identitätsmatrix.</span><span class="sxs-lookup"><span data-stu-id="57b34-113">In the simplest case, when a model is at the world origin and its local coordinate axes are oriented the same as world space, the world matrix is the identity matrix.</span></span> <span data-ttu-id="57b34-114">In der Regel ist jedoch die Weltmatrix eine Kombination aus einer Übersetzung in den Raum der Welt und möglicherweise einer oder ggf. mehreren Drehungen des Modell.</span><span class="sxs-lookup"><span data-stu-id="57b34-114">More commonly, the world matrix is a combination of a translation into world space and possibly one or more rotations to turn the model as needed.</span></span>

<span data-ttu-id="57b34-115">Direct3D verwendet die Welt- und Ansichtsmatrizen, die Sie einrichten, um mehrere interne Datenstrukturen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="57b34-115">Direct3D uses the world and view matrices that you set to configure several internal data structures.</span></span> <span data-ttu-id="57b34-116">Jedes Mal, wenn Sie eine neue Welt- oder Ansichtsmatrix festlegen, berechnet das System die zugehörigen internen Strukturen.</span><span class="sxs-lookup"><span data-stu-id="57b34-116">Each time you set a new world or view matrix, the system recalculates the associated internal structures.</span></span> <span data-ttu-id="57b34-117">Diese Matrizen festzulegen – z.B. mehrere Tausend Male pro Frame ist rechenintensiv und zeitaufwändig.</span><span class="sxs-lookup"><span data-stu-id="57b34-117">Setting these matrices frequently-for example, thousands of times per frame-is computationally time-consuming.</span></span> <span data-ttu-id="57b34-118">Sie können die Anzahl der erforderlichen Berechnungen minimieren, indem Sie die Welt- und die Ansichtsmatrizen zu einer Welt-Ansichtsmatrix verketten, die Sie als die Weltmatrix festlegen, und dann für die Ansichtsmatrix die Identitätsmatrix verwenden.</span><span class="sxs-lookup"><span data-stu-id="57b34-118">You can minimize the number of required calculations by concatenating your world and view matrices into a world-view matrix that you set as the world matrix, and then setting the view matrix to the identity.</span></span> <span data-ttu-id="57b34-119">Halten Sie zwischengespeicherte Kopien der einzelnen Welt- und Ansichtsmatrizen an, damit Sie die Weltmatrix bei Bedarf ändern, verketten und zurücksetzen können.</span><span class="sxs-lookup"><span data-stu-id="57b34-119">Keep cached copies of individual world and view matrices so that you can modify, concatenate, and reset the world matrix as needed.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="57b34-120"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="57b34-120"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="57b34-121">Transformationen</span><span class="sxs-lookup"><span data-stu-id="57b34-121">Transforms</span></span>](transforms.md)

 

 




