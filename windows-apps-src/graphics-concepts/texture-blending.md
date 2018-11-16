---
title: Texturmischung
description: Direct3D kann bis zu acht Texturen auf Grundtypen in einer einzigen Übergabe auf Grundtypen mischen.
ms.assetid: 9AD388FA-B2B9-44A9-B73E-EDBD7357ACFB
keywords:
- Texturmischung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d4121bd402b048ee6102ed3be30b94a66e274273
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6994528"
---
# <a name="texture-blending"></a><span data-ttu-id="f67c6-104">Texturmischung</span><span class="sxs-lookup"><span data-stu-id="f67c6-104">Texture blending</span></span>


<span data-ttu-id="f67c6-105">Direct3D kann bis zu acht Texturen auf Grundtypen in einem einzigen Durchlauf auf Grundtypen mischen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-105">Direct3D can blend as many as eight textures onto primitives in a single pass.</span></span> <span data-ttu-id="f67c6-106">Die Verwendung von mehreren gemischten Texturen kann die Framerate einer Direct3D-Anwendung erheblich erhöhen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-106">The use of multiple texture blending can profoundly increase the frame rate of a Direct3D application.</span></span> <span data-ttu-id="f67c6-107">Eine Anwendung verwendet mehrere Texturmischungen zur Anwendung von Texturen, Schatten, glänzender Beleuchtung, diffuser Beleuchtung und anderer Spezialeffekte in einem einzigen Durchgang.</span><span class="sxs-lookup"><span data-stu-id="f67c6-107">An application employs multiple texture blending to apply textures, shadows, specular lighting, diffuse lighting, and other special effects in a single pass.</span></span>

<span data-ttu-id="f67c6-108">Um die Texturmischung verwenden zu können, muss Ihre Anwendung zuerst prüfen, ob dies von der Hardware des Benutzers unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="f67c6-108">To use texture blending, your application should first check if the user's hardware supports it.</span></span>

## <a name="span-idtexture-stages-and-the-texture-blending-cascadespanspan-idtexture-stages-and-the-texture-blending-cascadespanspan-idtexture-stages-and-the-texture-blending-cascadespantexture-stages-and-the-texture-blending-cascade"></a><span data-ttu-id="f67c6-109"><span id="Texture-Stages-and-the-Texture-Blending-Cascade"></span><span id="texture-stages-and-the-texture-blending-cascade"></span><span id="TEXTURE-STAGES-AND-THE-TEXTURE-BLENDING-CASCADE"></span>Texturphasen und Texturmischungskaskade</span><span class="sxs-lookup"><span data-stu-id="f67c6-109"><span id="Texture-Stages-and-the-Texture-Blending-Cascade"></span><span id="texture-stages-and-the-texture-blending-cascade"></span><span id="TEXTURE-STAGES-AND-THE-TEXTURE-BLENDING-CASCADE"></span>Texture stages and the texture blending cascade</span></span>


<span data-ttu-id="f67c6-110">Direct3D unterstützt die mehrfache Texturmischung in einem Durchgang durch die Verwendung von Texturphasen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-110">Direct3D supports single-pass multiple texture blending through the use of texture stages.</span></span> <span data-ttu-id="f67c6-111">Eine Texturphase nimmt zwei Argumente und führt darauf einen Mischvorgang aus; das Ergebnis wird dann zur weiteren Verarbeitung oder zur Rasterisierung weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="f67c6-111">A texture stage takes two arguments and performs a blending operation on them, passing on the result for further processing or for rasterization.</span></span> <span data-ttu-id="f67c6-112">Eine Texturphase kann wie im folgenden Diagramm gezeigt visualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="f67c6-112">You can visualize a texture stage as shown in the following diagram.</span></span>

![Diagramm einer Texturphase](images/texstg.png)

<span data-ttu-id="f67c6-114">Wie das obige Diagramm zeigt, mischen Texturphasen zwei Argumente unter Verwendung eines angegebenen Operators.</span><span class="sxs-lookup"><span data-stu-id="f67c6-114">As the preceding diagram shows, texture stages blend two arguments by using a specified operator.</span></span> <span data-ttu-id="f67c6-115">Häufig ausgeführte Vorgänge sind u.a. die einfache Modulation oder Hinzufügung der Farb- oder Alphakomponenten der Argumente, insgesamt werden jedoch mehr als zwei Dutzend Vorgänge unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f67c6-115">Common operations include simple modulation or addition of the color or alpha components of the arguments, but more than two dozen operations are supported.</span></span> <span data-ttu-id="f67c6-116">Die Argumente für eine Phase können eine zugeordnete Textur, der iterierte Farb- oder Alphawert (iteriert im Rahmen der Gouraud-Schattierung), ein beliebiger Farb- oder Alphawert oder das Ergebnis der vorherigen Texturphase sein.</span><span class="sxs-lookup"><span data-stu-id="f67c6-116">The arguments for a stage can be an associated texture, the iterated color or alpha (iterated during Gouraud shading), arbitrary color and alpha, or the result from the previous texture stage.</span></span>

<span data-ttu-id="f67c6-117">**Hinweis:**  Direct3D farbmischung von der alphamischung.</span><span class="sxs-lookup"><span data-stu-id="f67c6-117">**Note** Direct3D distinguishes color blending from alpha blending.</span></span> <span data-ttu-id="f67c6-118">Anwendungen stellen Mischvorgänge und Argumente für Farbe und Alpha einzeln ein, und die Ergebnisse dieser Einstellungen sind voneinander unabhängig.</span><span class="sxs-lookup"><span data-stu-id="f67c6-118">Applications set blending operations and arguments for color and alpha individually, and the results of those settings are independent of one another.</span></span>

 

<span data-ttu-id="f67c6-119">Die Kombination der von mehreren Mischphasen verwendeten Argumente und Vorgänge definiert eine einfache, ablaufbasierte Mischungssprache.</span><span class="sxs-lookup"><span data-stu-id="f67c6-119">The combination of arguments and operations used by multiple blending stages define a simple flow-based blending language.</span></span> <span data-ttu-id="f67c6-120">Die Ergebnisse werden von einer Phase an die nächste übergeben, von dieser Phase wieder an die nächste und so weiter.</span><span class="sxs-lookup"><span data-stu-id="f67c6-120">The results from one stage flow down to another stage, from that stage to the next, and so on.</span></span> <span data-ttu-id="f67c6-121">Dieses Konzept der Weitergabe der Ergebnisse von Phase zu Phase bis zur schließlichen Rasterisierung auf einem Vieleck wird oft als „Texturmischungskaskade“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="f67c6-121">The concept of results flowing from stage to stage to eventually be rasterized on a polygon is often called the texture blending cascade.</span></span> <span data-ttu-id="f67c6-122">Das folgende Diagramm zeigt, wie einzelne Texturphasen die Texturmischungskaskade bilden.</span><span class="sxs-lookup"><span data-stu-id="f67c6-122">The following diagram shows how individual texture stages make up the texture blending cascade.</span></span>

![Diagramm der Texturphasen in einer Texturmischungskaskade](images/tcascade.png)

<span data-ttu-id="f67c6-124">Jede Phase in einem Gerät hat einen nullbasierten Index.</span><span class="sxs-lookup"><span data-stu-id="f67c6-124">Each stage in a device has a zero-based index.</span></span> <span data-ttu-id="f67c6-125">Direct3D erlaubt bis zu acht Mischungsphasen; Sie sollten jedoch stets die Möglichkeiten des Geräts prüfen, um festzustellen, wie viele Phasen die aktuell verwendete Hardware unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f67c6-125">Direct3D allows up to eight blending stages, although you should always check device capabilities to determine how many stages the current hardware supports.</span></span> <span data-ttu-id="f67c6-126">Die erste Mischungsphase befindet sich bei Index 0, die zweite bei Index 1 und so weiter, bis Index 7.</span><span class="sxs-lookup"><span data-stu-id="f67c6-126">The first blending stage is at index 0, the second is at 1, and so on, up to index 7.</span></span> <span data-ttu-id="f67c6-127">Das System mischt Phasen in aufsteigender Reihenfolge der Indizes.</span><span class="sxs-lookup"><span data-stu-id="f67c6-127">The system blends stages in increasing index order.</span></span>

<span data-ttu-id="f67c6-128">Verwenden Sie nur die Anzahl der Phasen, die Sie benötigen. die nicht verwendeten Mischungsphasen sind standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="f67c6-128">Use only the number of stages you need; the unused blending stages are disabled by default.</span></span> <span data-ttu-id="f67c6-129">Wenn Ihre Anwendung nur die ersten beiden Phasen verwendet, müssen daher nur Vorgänge und Argumente für Phase 0 und 1 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f67c6-129">So, if your application only uses the first two stages, it need only set operations and arguments for stage 0 and 1.</span></span> <span data-ttu-id="f67c6-130">Das System mischt die beiden Phasen und berücksichtigt die deaktivierten Phasen nicht.</span><span class="sxs-lookup"><span data-stu-id="f67c6-130">The system blends the two stages, and ignores the disabled stages.</span></span>

<span data-ttu-id="f67c6-131">Wenn Ihre Anwendung für unterschiedliche Situationen unterschiedlich viele Phasen verwendet – z.B. vier Phasen für einige Objekte und nur zwei für andere -, müssen Sie nicht alle vorher verwendeten Phasen explizit deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="f67c6-131">If your application varies the number of stages it uses for different situations - such as four stages for some objects, and only two for others - you don't need to explicitly disable all previously used stages.</span></span> <span data-ttu-id="f67c6-132">Eine Möglichkeit besteht darin, den Farbvorgang für die erste nicht verwendete Phase zu deaktivieren; dann werden alle Phasen mit einem höheren Index nicht angewendet.</span><span class="sxs-lookup"><span data-stu-id="f67c6-132">One option is to disable the color operation for the first unused stage, then all stages with a higher index will not be applied.</span></span> <span data-ttu-id="f67c6-133">Eine weitere Möglichkeit ist, die Texturzuordnung ganz zu deaktivieren, indem Sie den Farbvorgang für die erste Texturphase (Phase 0) in den deaktivierten Zustand versetzen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-133">Another option is to disable texture mapping altogether by setting the color operation for the first texture stage (stage 0) to a disabled state.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="f67c6-134"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="f67c6-134"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f67c6-135">Thema</span><span class="sxs-lookup"><span data-stu-id="f67c6-135">Topic</span></span></th>
<th align="left"><span data-ttu-id="f67c6-136">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f67c6-136">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="blending-stages.md"><span data-ttu-id="f67c6-137">Mischungsphasen</span><span class="sxs-lookup"><span data-stu-id="f67c6-137">Blending stages</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="f67c6-138">Eine Mischungsphase ist ein Satz von Texturvorgängen und ihren Argumenten, die festlegen, wie Texturen gemischt werden.</span><span class="sxs-lookup"><span data-stu-id="f67c6-138">A blending stage is a set of texture operations and their arguments that define how textures are blended.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="multipass-texture-blending.md"><span data-ttu-id="f67c6-139">Mehrstufige Texturmischung</span><span class="sxs-lookup"><span data-stu-id="f67c6-139">Multipass texture blending</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="f67c6-140">Direct3D-Anwendungen können durch die Anwendung verschiedener Texturen auf einen Grundtyp im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-140">Direct3D applications can achieve numerous special effects by applying various textures to a primitive over the course of multiple rendering passes.</span></span> <span data-ttu-id="f67c6-141">Der allgemeine Begriff dafür ist <em>Mehrstufige Texturmischung</em>.</span><span class="sxs-lookup"><span data-stu-id="f67c6-141">The common term for this is <em>multipass texture blending</em>.</span></span> <span data-ttu-id="f67c6-142">Eine typische Anwendung der mehrstufigen Texturmischung ist die Nachbildung der Effekte komplexer Beleuchtungs- und Schattierungsmodelle durch die Anwendung mehrerer Farben aus mehreren unterschiedlichen Texturen.</span><span class="sxs-lookup"><span data-stu-id="f67c6-142">A typical use for multipass texture blending is to emulate the effects of complex lighting and shading models by applying multiple colors from several different textures.</span></span> <span data-ttu-id="f67c6-143">Eine solche Anwendung heißt <em>Lichtzuordnung</em>.</span><span class="sxs-lookup"><span data-stu-id="f67c6-143">One such application is called <em>light mapping</em>.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="f67c6-144"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f67c6-144"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="f67c6-145">Texturen</span><span class="sxs-lookup"><span data-stu-id="f67c6-145">Textures</span></span>](textures.md)

 

 




