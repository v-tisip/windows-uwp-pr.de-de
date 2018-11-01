---
title: Compute-Pipeline
description: Die Direct3D-Compute-Pipeline wurde für die Behandlung von Berechnungen konzipiert, die hauptsächlich parallel zur Grafikpipeline ausgeführt werden können.
ms.assetid: 355B66C6-C0DF-47BA-A9C9-7AFA50B5B614
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 91c95019c327f39a58a7397a66f9d4bbc88f843d
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5922685"
---
# <a name="compute-pipeline"></a><span data-ttu-id="a24c9-104">Compute-Pipeline</span><span class="sxs-lookup"><span data-stu-id="a24c9-104">Compute pipeline</span></span>


<span data-ttu-id="a24c9-105">\[Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="a24c9-105">\[Some information relates to pre-released product which may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="a24c9-106">Microsoft übernimmt für die hier bereitgestellten Informationen keine Garantien, weder ausdrücklicher noch impliziter Art.\]</span><span class="sxs-lookup"><span data-stu-id="a24c9-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.\]</span></span>


<span data-ttu-id="a24c9-107">Die Direct3D-Compute-Pipeline wurde für die Behandlung von Berechnungen konzipiert, die hauptsächlich parallel zur Grafikpipeline ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="a24c9-107">The Direct3D compute pipeline is designed to handle calculations that can be done mostly in parallel with the graphics pipeline.</span></span> <span data-ttu-id="a24c9-108">Die Compute-Pipeline enthält nur wenige Schritte, bei der Daten zwischen Eingabe und Ausgabe über von Eingaben über die programmierbare Computeshaderphase fließen.</span><span class="sxs-lookup"><span data-stu-id="a24c9-108">There are only a few steps in the compute pipeline, with data flowing from input to output through the programmable compute shader stage.</span></span>

| | |
|-|-|
|<span data-ttu-id="a24c9-109">Zweck</span><span class="sxs-lookup"><span data-stu-id="a24c9-109">Purpose</span></span>|<span data-ttu-id="a24c9-110">Wie andere programmierbare Shader wurde auch die [Computeshaderphase (CS)](compute-shader-stage--cs-.md) mit HLSL entwickelt und implementiert.</span><span class="sxs-lookup"><span data-stu-id="a24c9-110">Like other programmable shaders, [Compute Shader (CS) stage](compute-shader-stage--cs-.md) is designed and implemented with HLSL.</span></span> <span data-ttu-id="a24c9-111">Ein Computeshader bietet schnelle, allgemeine Berechnungen und nutzt die große Anzahl von parallelen Prozessoren auf dem Grafikprozessor (GPU).</span><span class="sxs-lookup"><span data-stu-id="a24c9-111">A compute shader provides high-speed general purpose computing and takes advantage of the large numbers of parallel processors on the graphics processing unit (GPU).</span></span> <span data-ttu-id="a24c9-112">Der Computeshader bietet die Freigabe des Arbeitsspeichers und Threadsynchronisierung, um effektivere parallele Programmiermethoden zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a24c9-112">The compute shader provides memory sharing and thread synchronization features to allow more effective parallel programming methods.</span></span>|
|<span data-ttu-id="a24c9-113">Eingabe</span><span class="sxs-lookup"><span data-stu-id="a24c9-113">Input</span></span>|<span data-ttu-id="a24c9-114">Im Gegensatz zu anderen programmierbaren Shadern ist die Definition der Eingabe abstrakt.</span><span class="sxs-lookup"><span data-stu-id="a24c9-114">Unlike other programmable shaders, the definition of input is abstract.</span></span> <span data-ttu-id="a24c9-115">Die Eingabe kann ein-, zwei- oder dreidimensionaler Natur sein, um die Anzahl der auszufühRendern Aufrufe des Computeshaders festzulegen.</span><span class="sxs-lookup"><span data-stu-id="a24c9-115">The input can be one, two or three-dimensional in nature, determining the number of invocations of the compute shader to execute.</span></span> <span data-ttu-id="a24c9-116">Es ist möglich, gemeinsam genutzte Daten für einen Satz zu lesender Aufrufe zu definieren.</span><span class="sxs-lookup"><span data-stu-id="a24c9-116">It is possible to define shared data for one set of invocations to read.</span></span>|
|<span data-ttu-id="a24c9-117">Ausgabe</span><span class="sxs-lookup"><span data-stu-id="a24c9-117">Output</span></span>|<span data-ttu-id="a24c9-118">Ausgabedaten des Computeshaders können die stark variiert und mit der Grafikrenderingpipeline synchronisiert werden, wenn die berechneten Daten erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a24c9-118">Output data from the compute shader, which can be highly varied, can be synchronized with the graphics rendering pipeline when the computed data is required.</span></span>|
| | |




<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">Like other programmable shaders, <a href="#compute-shader-stage--cs-.md">Compute Shader (CS) stage</a> is designed and implemented with HLSL. A compute shader provides high-speed general purpose computing and takes advantage of the large numbers of parallel processors on the graphics processing unit (GPU). The compute shader provides memory sharing and thread synchronization features to allow more effective parallel programming methods.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">Unlike other programmable shaders, the definition of input is abstract. The input can be one, two or three-dimensional in nature, determining the number of invocations of the compute shader to execute. It is possible to define shared data for one set of invocations to read.</td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">Output data from the compute shader, which can be highly varied, can be synchronized with the graphics rendering pipeline when the computed data is required.</td>
</tr>
</tbody>
</table>
-->

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a24c9-119"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a24c9-119"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a24c9-120">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="a24c9-120">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 
