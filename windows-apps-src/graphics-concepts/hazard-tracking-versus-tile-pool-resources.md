---
title: Konfliktnachverfolgung und Tile-Pool-Ressourcen
description: Für Nicht-Streamingressourcen kann Direct3D bestimmte Konflikte (Hazards) während des Renderns verhindern. Für Streamingressourcen müsste die Nachverfolgung von Konflikten jedoch auf Tile-Ebene erfolgen, was zu aufwändig wäre.
ms.assetid: 8B0C73D3-3F77-41E8-B17D-C595DEE39E49
keywords:
- Konfliktnachverfolgung und Tile-Pool-Ressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e2ff4e2ff079e15c0af41e3232c4b70c582a6a25
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5867018"
---
# <a name="hazard-tracking-versus-tile-pool-resources"></a><span data-ttu-id="12d95-104">Konfliktnachverfolgung und Tile-Pool-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="12d95-104">Hazard tracking versus tile pool resources</span></span>


<span data-ttu-id="12d95-105">Für Nicht-Streamingressourcen kann Direct3D bestimmte Konflikte (Hazards) während des Renderns verhindern. Für Streamingressourcen müsste die Nachverfolgung von Konflikten jedoch auf Tile-Ebene erfolgen, was zu aufwändig wäre.</span><span class="sxs-lookup"><span data-stu-id="12d95-105">For non-streaming resources, Direct3D can prevent certain hazard conditions during rendering, but because hazard tracking would be at a tile level for streaming resources, tracking hazard conditions during rendering of streaming resources might be too expensive.</span></span>

<span data-ttu-id="12d95-106">Beispielsweise erlaubt die Runtime für Nicht-Streamingressourcen nicht, dass eine Unterressource gleichzeitig als Eingabe (z.B. als Shaderressourcenansicht) und als Ausgabe (z.B. als Renderzielansicht) gebunden wird. In einem solchen Fall würde die Runtime die Bindung der Eingabe aufheben.</span><span class="sxs-lookup"><span data-stu-id="12d95-106">For example, for non-streaming resources, the runtime doesn't allow any given SubResource to be bound as an input (such as a Shader Resource View) and as an output (such as a Render Target View) at the same time If such a case is encountered, the runtime unbinds the input.</span></span> <span data-ttu-id="12d95-107">Dieser Nachverfolgungsaufwand in der Runtime ist gering und erfolgt auf der Ebene von Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="12d95-107">This tracking overhead in the runtime is cheap and is done at the subresource level.</span></span> <span data-ttu-id="12d95-108">Einer der Vorteile dieses durch die Nachverfolgung bedingten Mehraufwands ist die Minimierung der Wahrscheinlichkeit, dass Apps versehentlich von der Ausführungsreihenfolge der Hardwareshader abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="12d95-108">One of the benefits of this tracking overhead is to minimize the chances of applications accidentally depending on hardware shader execution order.</span></span> <span data-ttu-id="12d95-109">Die Ausführungsreihenfolge der Hardwareshader kann variieren – wenn nicht für eine bestimmte GPU (Graphics Processing Unit), so doch bestimmt für verschiedene GPUs.</span><span class="sxs-lookup"><span data-stu-id="12d95-109">Hardware shader execution order can vary if not on a given graphics processing unit (GPU), then certainly across different GPUs.</span></span>

<span data-ttu-id="12d95-110">Nachzuverfolgen, wie Ressourcen gebunden sind, kann für Streamingressourcen zu aufwändig sein, da die Überwachung auf Tile-Ebene erfolgt.</span><span class="sxs-lookup"><span data-stu-id="12d95-110">Tracking how resources are bound might be too expensive for streaming resources because tracking is at a tile level.</span></span> <span data-ttu-id="12d95-111">Und es können weitere Probleme auftreten. Möglichweise müssen Versuche unterbunden werden, in eine Render Target View zu rendern, wenn eine Tile gleichzeitig mehreren Bereichen der Oberfläche zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="12d95-111">New issues arise such as possibly validating away attempts to render to a Render Target View with one tile mapped to multiple areas in the surface simultaneously.</span></span> <span data-ttu-id="12d95-112">Wenn diese Konfliktnachverfolgung pro Tile für die Runtime zu aufwändig ist, wäre das eine Option für die Debug-Ebene.</span><span class="sxs-lookup"><span data-stu-id="12d95-112">If it turns out this per-tile hazard tracking is too expensive for the runtime, ideally this would at least be an option in the debug layer.</span></span>

<span data-ttu-id="12d95-113">Eine Anwendung, die mit einem Schreib-oder Lesevorgang auf eine Streamingressource zugreift, die den Tile-Pool-Speicher referenziert, der auch von anderen Streamingressourcen in anschließenden Schreib- oder Lesevorgängen referenziert wird, muss den Grafiktreiber darüber informieren, dass sie erwartet, den ersten Vorgang abschließen zu können, bevor die folgenden Vorgänge beginnen.</span><span class="sxs-lookup"><span data-stu-id="12d95-113">An application must inform the display driver when it has issued a write or read operation to a streaming resource that references tile pool memory that will also be referenced by separate streaming resources in upcoming read or write operations that it is expecting the first operation to complete before the following operations can begin.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="12d95-114"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="12d95-114"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="12d95-115">Zuordnungen erfolgen in einen Kachelpool</span><span class="sxs-lookup"><span data-stu-id="12d95-115">Mappings are into a tile pool</span></span>](mappings-are-into-a-tile-pool.md)

 

 




