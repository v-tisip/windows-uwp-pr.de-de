---
title: Scheitelpunkt- und Indexpuffer
description: Scheitelpunktpuffer sind Speicherpuffer, die Scheitelpunktdaten enthalten. Scheitelpunkte in einem Scheitelpunktpuffer werden verarbeitet, um Transformation, Beleuchtung und Zuschneiden auszuführen.
ms.assetid: 8A39CD23-85FB-4424-9AC3-37919704CD68
keywords:
- Scheitelpunkt- und Indexpuffer
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 2327036eb53ac34c406aef53163be642468fbddc
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5936668"
---
# <a name="vertex-and-index-buffers"></a><span data-ttu-id="a1b10-104">Scheitelpunkt- und Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="a1b10-104">Vertex and index buffers</span></span>


<span data-ttu-id="a1b10-105">*Scheitelpunktpuffer* sind Speicherpuffer, die Scheitelpunktdaten enthalten. Scheitelpunkte in einem Scheitelpunktpuffer werden verarbeitet, um Transformation, Beleuchtung und Zuschneiden auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a1b10-105">*Vertex buffers* are memory buffers that contain vertex data; vertices in a vertex buffer are processed to perform transformation, lighting, and clipping.</span></span> <span data-ttu-id="a1b10-106">*Indexpuffer* sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Scheitelpunktpuffern darstellen, und zum Rendern von Grundtypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a1b10-106">*Index buffers* are memory buffers that contain index data, which are integer offsets into vertex buffers, used to render primitives.</span></span>

<span data-ttu-id="a1b10-107">Scheitelpunktpuffer können Scheitelpunkte beliebiger Art enthalten, die gerendert werden können – transformiert oder nicht transformiert, beleuchtet oder nicht beleuchtet.</span><span class="sxs-lookup"><span data-stu-id="a1b10-107">Vertex buffers can contain any vertex type - transformed or untransformed, lit or unlit - that can be rendered.</span></span> <span data-ttu-id="a1b10-108">Sie können die Scheitelpunkte in einem Scheitelpunktpuffer verarbeiten, um Vorgänge wie Transformation oder Beleuchtung durchzuführen, oder um Zuschneidemarkierungen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="a1b10-108">You can process the vertices in a vertex buffer to perform operations such as transformation, lighting, or generating clipping flags.</span></span> <span data-ttu-id="a1b10-109">Die Transformation wird immer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a1b10-109">Transformation is always performed.</span></span>

<span data-ttu-id="a1b10-110">Die Flexibilität der Scheitelpunktpuffer macht sie zu idealen Phasenpunkten für die Wiederverwendung einer transformierten Geometrie.</span><span class="sxs-lookup"><span data-stu-id="a1b10-110">The flexibility of vertex buffers make them ideal staging points for reusing transformed geometry.</span></span> <span data-ttu-id="a1b10-111">Sie können etwa einen einzelnen Scheitelpunktpuffer erstellen, die Scheitelpunkte darin transformieren, beleuchten und zuschneiden und dann das Modell in der Szene so oft wie nötig rendern, ohne es erneut zu transformieren, selbst mit überlappenden Renderingzustandsänderungen.</span><span class="sxs-lookup"><span data-stu-id="a1b10-111">You could create a single vertex buffer, transform, light, and clip the vertices in it, and render the model in the scene as many times as needed without re-transforming it, even with interleaved render state changes.</span></span> <span data-ttu-id="a1b10-112">Dies ist nützlich beim Rendern von Modellen, die mehrere Texturen verwenden: Die Geometrie wird nur einmal transformiert, und anschließend können Teile davon nach Bedarf gerendert werden, in Überlappung mit den erforderlichen Texturänderungen.</span><span class="sxs-lookup"><span data-stu-id="a1b10-112">This is useful when rendering models that use multiple textures: the geometry is transformed only once, and then portions of it can be rendered as needed, interleaved with the required texture changes.</span></span> <span data-ttu-id="a1b10-113">Renderingzustandsänderungen, die nach der Verarbeitung von Scheitelpunkten vorgenommen wurden, werden bei der nächsten Verarbeitung der Scheitelpunkte wirksam.</span><span class="sxs-lookup"><span data-stu-id="a1b10-113">Render state changes made after vertices are processed take effect the next time the vertices are processed.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="a1b10-114"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="a1b10-114"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a1b10-115">Thema</span><span class="sxs-lookup"><span data-stu-id="a1b10-115">Topic</span></span></th>
<th align="left"><span data-ttu-id="a1b10-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1b10-116">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="introduction-to-buffers.md"><span data-ttu-id="a1b10-117">Einführung zu Puffern</span><span class="sxs-lookup"><span data-stu-id="a1b10-117">Introduction to buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="a1b10-118">Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="a1b10-118">A buffer resource is a collection of fully typed data, grouped into elements.</span></span> <span data-ttu-id="a1b10-119">Puffer speichern Daten, wie z.B. Texturkoordinaten in einem <em>Scheitelpunktpuffer</em>, Indizes in einem <em>Indexpuffer</em>, Shader-Konstantendaten in einem <em>Konstantenpuffer</em>, Positionsvektoren, normale Vektoren oder den Gerätezustand.</span><span class="sxs-lookup"><span data-stu-id="a1b10-119">Buffers store data, such as texture coordinates in a <em>vertex buffer</em>, indexes in an <em>index buffer</em>, shader constants data in a <em>constant buffer</em>, position vectors, normal vectors, or device state.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="index-buffers.md"><span data-ttu-id="a1b10-120">Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="a1b10-120">Index buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="a1b10-121"><em>Indexpuffer</em> sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Vertexpuffer darstellen, und zum Rendern von Grundtypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a1b10-121"><em>Index buffers</em> are memory buffers that contain index data, which are integer offsets into vertex buffers, used to render primitives.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a1b10-122"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a1b10-122"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a1b10-123">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="a1b10-123">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




