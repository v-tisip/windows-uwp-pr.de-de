---
title: Exposition von HLSL-Streamingressourcen
description: Zur Unterstützung von Streamingressourcen in Shader Model 5 ist eine spezielle Microsoft High Level Shader Language (HLSL)-Syntax erforderlich.
ms.assetid: 00A40D82-0565-43DC-82AB-0675B7E772E3
keywords:
- Exposition von HLSL-Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a8523f4895c541ffb3b92ee00d5b62c57343ae00
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6849152"
---
# <a name="hlsl-streaming-resources-exposure"></a><span data-ttu-id="11b19-104">Exposition von HLSL-Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="11b19-104">HLSL streaming resources exposure</span></span>


<span data-ttu-id="11b19-105">Zur Unterstützung von Streamingressourcen in [Shader Model 5](https://msdn.microsoft.com/library/windows/desktop/ff471356) ist eine spezielle Microsoft High Level Shader Language (HLSL)-Syntax erforderlich.</span><span class="sxs-lookup"><span data-stu-id="11b19-105">A specific Microsoft High Level Shader Language (HLSL) syntax is required to support streaming resources in [Shader Model 5](https://msdn.microsoft.com/library/windows/desktop/ff471356).</span></span>

<span data-ttu-id="11b19-106">Die HLSL-Syntax für Shader Model 5 ist nur auf Geräten zulässig, die Streamingressourcen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="11b19-106">The HLSL syntax for Shader Model 5 is allowed only on devices with streaming resources support.</span></span> <span data-ttu-id="11b19-107">Jede relevante HLSL-Methode für das Streaming von Ressourcen in der folgenden Tabelle akzeptiert einen (feedback) oder zwei (clamp und feedback in dieser Reihenfolge) zusätzliche optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="11b19-107">Each relevant HLSL method for streaming resources in the following table accepts either one (feedback) or two (clamp and feedback in this order) additional optional parameters.</span></span> <span data-ttu-id="11b19-108">Aufbau einer **Sample**-Methode:</span><span class="sxs-lookup"><span data-stu-id="11b19-108">For example, a **Sample** method is:</span></span>

**<span data-ttu-id="11b19-109">Sample(sampler, location \[, offset \[, clamp \[, feedback\] \] \])</span><span class="sxs-lookup"><span data-stu-id="11b19-109">Sample(sampler, location \[, offset \[, clamp \[, feedback\] \] \])</span></span>**

<span data-ttu-id="11b19-110">Ein Beispiel für eine **Sample**-Methode ist [**Texture2D.Sample(S,float,int,float,uint)**](https://msdn.microsoft.com/library/windows/desktop/dn393787).</span><span class="sxs-lookup"><span data-stu-id="11b19-110">An example of a **Sample** method is [**Texture2D.Sample(S,float,int,float,uint)**](https://msdn.microsoft.com/library/windows/desktop/dn393787).</span></span>

<span data-ttu-id="11b19-111">Die Parameter offset, clamp und feedback sind optional.</span><span class="sxs-lookup"><span data-stu-id="11b19-111">The offset, clamp and feedback parameters are optional.</span></span> <span data-ttu-id="11b19-112">Sie müssen alle optionalen Parameter bis zu dem angeben, den Sie benötigen, was mit den C++- Regeln für Standardfunktionsargumente übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="11b19-112">You must specify all optional parameters up to the one you need, which is consistent with the C++ rules for default function arguments.</span></span> <span data-ttu-id="11b19-113">Wenn zum Beispiel der Feedbackstatus erforderlich ist, müssen Sie sowohl den offset- als auch den clamp-Parameter explizit für **Sample** bereitstellen, obwohl diese Parameter möglicherweise logisch nicht benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="11b19-113">For example, if the feedback status is needed, both offset and clamp parameters need to be explicitly supplied to **Sample**, even though they may not be logically needed.</span></span>

<span data-ttu-id="11b19-114">Der Parameter clamp ist ein skalarer Float-Wert.</span><span class="sxs-lookup"><span data-stu-id="11b19-114">The clamp parameter is a scalar float value.</span></span> <span data-ttu-id="11b19-115">Mit clamp=0.0f geben Sie an, dass der Clampvorgang nicht durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="11b19-115">The literal value of clamp=0.0f indicates that the clamp operation isn't performed.</span></span>

<span data-ttu-id="11b19-116">Der Parameter feedback ist eine **Uint**-Variable, die Sie der internen Funktion [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) bereitstellen können, mit der Speicherzugriff angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="11b19-116">The feedback parameter is a **uint** variable that you can supply to the memory-access querying intrinsic [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) function.</span></span> <span data-ttu-id="11b19-117">Sie müssen den Parameter feedback nicht ändern oder interpretieren – der Compiler stellt keine erweiterten Analyse- oder Diagnosemöglichkeiten bereit, um festzustellen, ob Sie den Wert geändert haben.</span><span class="sxs-lookup"><span data-stu-id="11b19-117">You must not modify or interpret the value of the feedback parameter; but, the compiler doesn't provide any advanced analysis and diagnostics to detect whether you modified the value.</span></span>

<span data-ttu-id="11b19-118">So lautet die Syntax für [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083):</span><span class="sxs-lookup"><span data-stu-id="11b19-118">Here is the syntax of [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083):</span></span>

**<span data-ttu-id="11b19-119">bool CheckAccessFullyMapped(in uint FeedbackVar);</span><span class="sxs-lookup"><span data-stu-id="11b19-119">bool CheckAccessFullyMapped(in uint FeedbackVar);</span></span>**

<span data-ttu-id="11b19-120">[**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) interpretiert den Wert von *FeedbackVar* und gibt TRUE zurück, wenn alle Daten, auf die zugegriffen wird, der Ressource zugeordnet wurden. Andernfalls gibt **CheckAccessFullyMapped** den Wert FALSE zurück.</span><span class="sxs-lookup"><span data-stu-id="11b19-120">[**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) interprets the value of *FeedbackVar* and returns true if all data being accessed was mapped in the resource; otherwise, **CheckAccessFullyMapped** returns false.</span></span>

<span data-ttu-id="11b19-121">Wenn der Parameter clamp oder feedback vorhanden ist, gibt der Compiler eine Variante der Grundanweisung aus.</span><span class="sxs-lookup"><span data-stu-id="11b19-121">If either the clamp or feedback parameter is present, the compiler emits a variant of the basic instruction.</span></span> <span data-ttu-id="11b19-122">Beispielsweise generiert sample für eine Streamingressource die Anweisung `sample_cl_s`.</span><span class="sxs-lookup"><span data-stu-id="11b19-122">For example, sample of a streaming resource generates the `sample_cl_s` instruction.</span></span>

<span data-ttu-id="11b19-123">Ist weder clamp noch feedback angegeben, gibt der Compiler die Grundanweisung aus, sodass sich das aktuelle Verhalten nicht ändert.</span><span class="sxs-lookup"><span data-stu-id="11b19-123">If neither clamp nor feedback is specified, the compiler emits the basic instruction, so that there is no change from the current behavior.</span></span>

<span data-ttu-id="11b19-124">Der clamp-Wert 0.0f gibt an, dass kein Clamp-Vorgang ausgeführt wird. Daher kann der Treibercompiler die Anweisung weiter an die Zielarchitektur anpassen.</span><span class="sxs-lookup"><span data-stu-id="11b19-124">The clamp value of 0.0f indicates that no clamp is performed; thus, the driver compiler can further tailor the instruction to the target hardware.</span></span> <span data-ttu-id="11b19-125">Ist feedback ein NULL-Register in einer Anweisung, wird das Feedback nicht verwendet. Daher kann der Treibercompiler die Anweisung weiter an die Zielarchitektur anpassen.</span><span class="sxs-lookup"><span data-stu-id="11b19-125">If feedback is a NULL register in an instruction, the feedback is unused; thus, the driver compiler can further tailor the instruction to the target architecture.</span></span>

<span data-ttu-id="11b19-126">Wenn der HLSL-Compiler erkennt, dass clamp den Wert 0.0f hat und feedback nicht verwendet wird, gibt der Compiler die entsprechende Grundanweisung aus (z.B. `sample` statt `sample_cl_s`).</span><span class="sxs-lookup"><span data-stu-id="11b19-126">If the HLSL compiler infers that clamp is 0.0f and feedback is unused, the compiler emits the corresponding basic instruction (for example, `sample` rather than `sample_cl_s`).</span></span>

<span data-ttu-id="11b19-127">Besteht ein Streamingressourcenzugriff aus mehreren Bytecodeanweisungen, beispielsweise für strukturierte Ressourcen, aggregiert der Compiler einzelne feedback-Werte mit der OR-Operation, um den endgültigen feedback-Wert zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="11b19-127">If a streaming resource access consists of several constituent byte code instructions, for example, for structured resources, the compiler aggregates individual feedback values via the OR operation to produce the final feedback value.</span></span> <span data-ttu-id="11b19-128">Dadurch ergibt sich für einen solchen komplexen Zugriff ein einzelner feedback-Wert.</span><span class="sxs-lookup"><span data-stu-id="11b19-128">Therefore, you see a single feedback value for such a complex access.</span></span>

<span data-ttu-id="11b19-129">In der folgende Tabelle sind die HLSL-Methoden zusammengefasst, die geändert wurden, um feedback und/oder clamp zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="11b19-129">This is the summary table of HLSL methods that are changed to support feedback and/or clamp.</span></span> <span data-ttu-id="11b19-130">Sie alle arbeiten mit strukturierten und Nicht-Streamingressourcen aller Dimensionen.</span><span class="sxs-lookup"><span data-stu-id="11b19-130">These all work on tiled and non-streaming resources of all dimensions.</span></span> <span data-ttu-id="11b19-131">Nicht-Streamingressourcen scheinen immer vollständig zugeordnet zu sein.</span><span class="sxs-lookup"><span data-stu-id="11b19-131">Non-streaming resources always appear to be fully mapped.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><a href="https://msdn.microsoft.com/library/windows/desktop/ff471359"><span data-ttu-id="11b19-132">HLSL-Objekte</span><span class="sxs-lookup"><span data-stu-id="11b19-132">HLSL objects</span></span></a> </th>
<th align="left"><span data-ttu-id="11b19-133">Intrinsische Methoden mit feedback-Option – (\*) verfügt auch über die clamp-Option</span><span class="sxs-lookup"><span data-stu-id="11b19-133">Intrinsic methods with feedback option (\*) - also has clamp option</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="11b19-134">[RW]Texture2D</span><span class="sxs-lookup"><span data-stu-id="11b19-134">[RW]Texture2D</span></span></p>
<p><span data-ttu-id="11b19-135">[RW]Texture2DArray</span><span class="sxs-lookup"><span data-stu-id="11b19-135">[RW]Texture2DArray</span></span></p>
<p><span data-ttu-id="11b19-136">TextureCUBE</span><span class="sxs-lookup"><span data-stu-id="11b19-136">TextureCUBE</span></span></p>
<p><span data-ttu-id="11b19-137">TextureCUBEArray</span><span class="sxs-lookup"><span data-stu-id="11b19-137">TextureCUBEArray</span></span></p></td>
<td align="left"><p><span data-ttu-id="11b19-138">Gather</span><span class="sxs-lookup"><span data-stu-id="11b19-138">Gather</span></span></p>
<p><span data-ttu-id="11b19-139">GatherRed</span><span class="sxs-lookup"><span data-stu-id="11b19-139">GatherRed</span></span></p>
<p><span data-ttu-id="11b19-140">GatherGreen</span><span class="sxs-lookup"><span data-stu-id="11b19-140">GatherGreen</span></span></p>
<p><span data-ttu-id="11b19-141">GatherBlue</span><span class="sxs-lookup"><span data-stu-id="11b19-141">GatherBlue</span></span></p>
<p><span data-ttu-id="11b19-142">GatherAlpha</span><span class="sxs-lookup"><span data-stu-id="11b19-142">GatherAlpha</span></span></p>
<p><span data-ttu-id="11b19-143">GatherCmp</span><span class="sxs-lookup"><span data-stu-id="11b19-143">GatherCmp</span></span></p>
<p><span data-ttu-id="11b19-144">GatherCmpRed</span><span class="sxs-lookup"><span data-stu-id="11b19-144">GatherCmpRed</span></span></p>
<p><span data-ttu-id="11b19-145">GatherCmpGreen</span><span class="sxs-lookup"><span data-stu-id="11b19-145">GatherCmpGreen</span></span></p>
<p><span data-ttu-id="11b19-146">GatherCmpBlue</span><span class="sxs-lookup"><span data-stu-id="11b19-146">GatherCmpBlue</span></span></p>
<p><span data-ttu-id="11b19-147">GatherCmpAlpha</span><span class="sxs-lookup"><span data-stu-id="11b19-147">GatherCmpAlpha</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="11b19-148">[RW]Texture1D</span><span class="sxs-lookup"><span data-stu-id="11b19-148">[RW]Texture1D</span></span></p>
<p><span data-ttu-id="11b19-149">[RW]Texture1DArray</span><span class="sxs-lookup"><span data-stu-id="11b19-149">[RW]Texture1DArray</span></span></p>
<p><span data-ttu-id="11b19-150">[RW]Texture2D</span><span class="sxs-lookup"><span data-stu-id="11b19-150">[RW]Texture2D</span></span></p>
<p><span data-ttu-id="11b19-151">[RW]Texture2DArray</span><span class="sxs-lookup"><span data-stu-id="11b19-151">[RW]Texture2DArray</span></span></p>
<p><span data-ttu-id="11b19-152">[RW]Texture3D</span><span class="sxs-lookup"><span data-stu-id="11b19-152">[RW]Texture3D</span></span></p>
<p><span data-ttu-id="11b19-153">TextureCUBE</span><span class="sxs-lookup"><span data-stu-id="11b19-153">TextureCUBE</span></span></p>
<p><span data-ttu-id="11b19-154">TextureCUBEArray</span><span class="sxs-lookup"><span data-stu-id="11b19-154">TextureCUBEArray</span></span></p></td>
<td align="left"><p><span data-ttu-id="11b19-155">Sample\*</span><span class="sxs-lookup"><span data-stu-id="11b19-155">Sample\*</span></span></p>
<p><span data-ttu-id="11b19-156">SampleBias\*</span><span class="sxs-lookup"><span data-stu-id="11b19-156">SampleBias\*</span></span></p>
<p><span data-ttu-id="11b19-157">SampleCmp\*</span><span class="sxs-lookup"><span data-stu-id="11b19-157">SampleCmp\*</span></span></p>
<p><span data-ttu-id="11b19-158">SampleCmpLevelZero</span><span class="sxs-lookup"><span data-stu-id="11b19-158">SampleCmpLevelZero</span></span></p>
<p><span data-ttu-id="11b19-159">SampleGrad\*</span><span class="sxs-lookup"><span data-stu-id="11b19-159">SampleGrad\*</span></span></p>
<p><span data-ttu-id="11b19-160">SampleLevel</span><span class="sxs-lookup"><span data-stu-id="11b19-160">SampleLevel</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="11b19-161">[RW]Texture1D</span><span class="sxs-lookup"><span data-stu-id="11b19-161">[RW]Texture1D</span></span></p>
<p><span data-ttu-id="11b19-162">[RW]Texture1DArray</span><span class="sxs-lookup"><span data-stu-id="11b19-162">[RW]Texture1DArray</span></span></p>
<p><span data-ttu-id="11b19-163">[RW]Texture2D</span><span class="sxs-lookup"><span data-stu-id="11b19-163">[RW]Texture2D</span></span></p>
<p><span data-ttu-id="11b19-164">Texture2DMS</span><span class="sxs-lookup"><span data-stu-id="11b19-164">Texture2DMS</span></span></p>
<p><span data-ttu-id="11b19-165">[RW]Texture2DArray</span><span class="sxs-lookup"><span data-stu-id="11b19-165">[RW]Texture2DArray</span></span></p>
<p><span data-ttu-id="11b19-166">Texture2DArrayMS</span><span class="sxs-lookup"><span data-stu-id="11b19-166">Texture2DArrayMS</span></span></p>
<p><span data-ttu-id="11b19-167">[RW]Texture3D</span><span class="sxs-lookup"><span data-stu-id="11b19-167">[RW]Texture3D</span></span></p>
<p><span data-ttu-id="11b19-168">[RW]Buffer</span><span class="sxs-lookup"><span data-stu-id="11b19-168">[RW]Buffer</span></span></p>
<p><span data-ttu-id="11b19-169">[RW]ByteAddressBuffer</span><span class="sxs-lookup"><span data-stu-id="11b19-169">[RW]ByteAddressBuffer</span></span></p>
<p><span data-ttu-id="11b19-170">[RW]StructuredBuffer</span><span class="sxs-lookup"><span data-stu-id="11b19-170">[RW]StructuredBuffer</span></span></p></td>
<td align="left"><span data-ttu-id="11b19-171">Load</span><span class="sxs-lookup"><span data-stu-id="11b19-171">Load</span></span></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="11b19-172"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11b19-172"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="11b19-173">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="11b19-173">Pipeline access to streaming resources</span></span>](pipeline-access-to-streaming-resources.md)

 

 




