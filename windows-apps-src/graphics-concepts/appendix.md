---
title: Anhänge
description: In diesen Abschnitten werden ausführliche technische Details beschrieben.
ms.assetid: 461CCE6F-BAF0-4965-90A5-FD36B511F72C
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f4cd2e17754dc5b5958e8bca208e30b87718cdd8
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8801349"
---
# <a name="appendices"></a><span data-ttu-id="9d843-104">Anhänge</span><span class="sxs-lookup"><span data-stu-id="9d843-104">Appendices</span></span>

<span data-ttu-id="9d843-105">In diesen Abschnitten werden ausführliche technische Details beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9d843-105">These sections provide in-depth technical details.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="9d843-106"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="9d843-106"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9d843-107">Thema</span><span class="sxs-lookup"><span data-stu-id="9d843-107">Topic</span></span></th>
<th align="left"><span data-ttu-id="9d843-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d843-108">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="floating-point-rules.md"><span data-ttu-id="9d843-109">Gleitkommaregeln</span><span class="sxs-lookup"><span data-stu-id="9d843-109">Floating-point rules</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="9d843-110">Direct3D unterstützt mehrere Gleitkommadarstellungen.</span><span class="sxs-lookup"><span data-stu-id="9d843-110">Direct3D supports several floating-point representations.</span></span> <span data-ttu-id="9d843-111">Alle Gleitkommaberechnungen werden unter einer festgelegten Teilmenge der IEEE 754-Richtlinie der 32-Bit-Gleitkommaregel mit einfacher Genauigkeit ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9d843-111">All floating-point computations operate under a defined subset of the IEEE 754 32-bit single precision floating-point rules.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="data-type-conversion.md"><span data-ttu-id="9d843-112">Konvertieren von Datentypen</span><span class="sxs-lookup"><span data-stu-id="9d843-112">Data type conversion</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="9d843-113">In den folgenden Abschnitten wird beschrieben, wie Direct3D Konvertierungen zwischen Datentypen verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="9d843-113">The following sections describe how Direct3D handles conversions between data types.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="rasterization-rules.md"><span data-ttu-id="9d843-114">Regeln für die Rasterung</span><span class="sxs-lookup"><span data-stu-id="9d843-114">Rasterization rules</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="9d843-115">Die Regeln für die Rasterung legen fest, wie Vektordaten Rasterdaten zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="9d843-115">Rasterization rules define how vector data is mapped into raster data.</span></span> <span data-ttu-id="9d843-116">Rasterdaten werden als Ganzzahl-Positionen angedockt, die dann ausgewählt und gekürzt werden (um eine minimale Anzahl der Pixel zu ergeben). Attribute pro Pixel werden interpoliert (von Attributen pro Scheitelpunkt), bevor diese an einen Pixel-Shader weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="9d843-116">The raster data is snapped to integer locations that are then culled and clipped (to draw the minimum number of pixels), and per-pixel attributes are interpolated (from per-vertex attributes) before being passed to a pixel shader.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture-block-compression.md"><span data-ttu-id="9d843-117">Texturblockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="9d843-117">Texture block compression</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="9d843-118">Die Unterstützung der Blockkomprimierung (BC) für Texturen wurde in Direct3D11 erweitert, um BC6H- und BC7-Algorithmen anzubieten.</span><span class="sxs-lookup"><span data-stu-id="9d843-118">Block Compression (BC) support for textures has been extended in Direct3D 11 to include the BC6H and BC7 algorithms.</span></span> <span data-ttu-id="9d843-119">BC6H unterstützt HDR-Farb-Quelldaten und BC7 bietet überdurchschnittliche Qualität bei der Komprimierung mit weniger Artefakte für Standard-RGB-Quelldaten.</span><span class="sxs-lookup"><span data-stu-id="9d843-119">BC6H supports high-dynamic range color source data, and BC7 provides better-than-average quality compression with less artifacts for standard RGB source data.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="9d843-120"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9d843-120"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="9d843-121">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="9d843-121">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




