---
ms.assetid: 9347AD7C-3A90-4073-BFF4-9E8237398343
description: In diesem Artikel wird aufgeführt, welche Audio- und Videocodecs und welche Formate für UWP-Apps unterstützt werden.
title: Unterstützte Codecs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 02d8c67c92a070fbeaaab81ef6c5145dec90e411
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8736570"
---
# <a name="supported-codecs"></a><span data-ttu-id="ecf01-104">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="ecf01-104">Supported codecs</span></span>

<span data-ttu-id="ecf01-105">In diesem Artikel ist die Verfügbarkeit von Audio-, Video- und Bild-Codecs und -Formaten für UWP-Apps standardmäßig für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-105">This article lists the audio, video, and image codec and format availability for UWP apps by default for each device family.</span></span> <span data-ttu-id="ecf01-106">Beachten Sie, dass diese Tabellen die Codecs enthalten, die in der Windows10-Installation für die angegebene Gerätefamilie enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="ecf01-106">Note that these tables list the codecs that are included with the Windows 10 installation for the specified device family.</span></span> <span data-ttu-id="ecf01-107">Benutzer und Apps können zusätzliche Codecs installieren, die unter Umständen zur Verwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="ecf01-107">Users and apps can install additional codecs that may be available to use.</span></span> <span data-ttu-id="ecf01-108">Sie können zur Laufzeit den Satz von Codecs abfragen, die derzeit für ein bestimmtes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ecf01-108">You can query at runtime for the set of codecs that are currently available for a specific device.</span></span> <span data-ttu-id="ecf01-109">Weitere Informationen finden Sie unter [Abfragen von auf einem Gerät installierten Codecs](codec-query.md).</span><span class="sxs-lookup"><span data-stu-id="ecf01-109">For more information, see [Query for codecs installed on a device](codec-query.md).</span></span>

<span data-ttu-id="ecf01-110">In den folgenden Tabellen steht „D“ für Decoderunterstützung und „E“ für Encoderunterstützung.</span><span class="sxs-lookup"><span data-stu-id="ecf01-110">In the tables below "D" indicates decoder support and "E" indicates encoder support.</span></span>

## <a name="audio-codec--format-support"></a><span data-ttu-id="ecf01-111">Unterstützung von Audiocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="ecf01-111">Audio codec & format support</span></span>

<span data-ttu-id="ecf01-112">In den folgenden Tabellen wird die Unterstützung von Audiocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-112">The following tables show the audio codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="ecf01-113">Wo AMR-NB-Unterstützung angegeben ist, wird dieser Codec nicht auf Server-SKUs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-113">Where AMR-NB support is indicated, this codec is not supported on Server SKUs.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="ecf01-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="ecf01-114">Desktop</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-115">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-115">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-116">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-116">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-117">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-117">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-118">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-118">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-119">ADTS</span><span class="sxs-lookup"><span data-stu-id="ecf01-119">ADTS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-120">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-120">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-121">RIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-121">RIFF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-122">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-122">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-123">AC-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-123">AC-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-124">AMR</span><span class="sxs-lookup"><span data-stu-id="ecf01-124">AMR</span></span></th>
<th align="left"><span data-ttu-id="ecf01-125">3GP</span><span class="sxs-lookup"><span data-stu-id="ecf01-125">3GP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-126">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-126">FLAC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-127">WAV</span><span class="sxs-lookup"><span data-stu-id="ecf01-127">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-128">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-128">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-129">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-129">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-130">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-130">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-131">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-131">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-132">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-132">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-133">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-133">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-134">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="ecf01-134">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-135">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-135">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-136">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-136">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-137">AC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-137">AC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-138">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-138">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-139">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-139">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-140">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-140">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-141">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-141">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-142">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-142">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-143">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-143">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-144">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-144">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-145">ALAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-145">ALAC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-146">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-146">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-147">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="ecf01-147">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="ecf01-148">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-148">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-149">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-149">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-150">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-150">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-151">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-151">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-152">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-152">D/E</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-153">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="ecf01-153">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-154">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-154">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-155">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="ecf01-155">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-156">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-156">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-157">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-157">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-158">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-158">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-159">LPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-159">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-160">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-160">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-161">MP3</span><span class="sxs-lookup"><span data-stu-id="ecf01-161">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-162">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-162">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-163">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="ecf01-163">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-164">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-164">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-165">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-165">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-166">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-166">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-167">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="ecf01-167">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-168">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-168">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-169">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="ecf01-169">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-170">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-170">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-171">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="ecf01-171">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-172">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-172">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="ecf01-173">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="ecf01-173">Mobile</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-174">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-174">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-175">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-175">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-176">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-176">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-177">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-177">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-178">ADTS</span><span class="sxs-lookup"><span data-stu-id="ecf01-178">ADTS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-179">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-179">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-180">RIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-180">RIFF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-181">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-181">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-182">AC-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-182">AC-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-183">AMR</span><span class="sxs-lookup"><span data-stu-id="ecf01-183">AMR</span></span></th>
<th align="left"><span data-ttu-id="ecf01-184">3GP</span><span class="sxs-lookup"><span data-stu-id="ecf01-184">3GP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-185">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-185">FLAC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-186">WAV</span><span class="sxs-lookup"><span data-stu-id="ecf01-186">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-187">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-187">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-188">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-188">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-189">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-189">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-190">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-190">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-191">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-191">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-192">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-192">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-193">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="ecf01-193">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-194">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-194">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-195">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-195">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-196">AC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-196">AC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-197">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-197">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-198">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-198">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-199">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-199">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="ecf01-200">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-200">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="ecf01-201">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-201">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="ecf01-202">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="ecf01-202">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-203">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-203">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-204">ALAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-204">ALAC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-205">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-205">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-206">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="ecf01-206">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="ecf01-207">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-207">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-208">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-208">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-209">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-209">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-210">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-210">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-211">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-211">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-212">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="ecf01-212">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-213">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-213">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-214">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="ecf01-214">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-215">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-215">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-216">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-216">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-217">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-217">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-218">LPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-218">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-219">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-219">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-220">MP3</span><span class="sxs-lookup"><span data-stu-id="ecf01-220">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-221">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-221">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-222">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="ecf01-222">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-223">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-223">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-224">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-224">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-225">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="ecf01-225">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-226">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-226">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-227">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="ecf01-227">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-228">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-228">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-229">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="ecf01-229">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="ecf01-230">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="ecf01-230">IoT Core (x86)</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-231">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-231">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-232">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-232">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-233">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-233">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-234">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-234">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-235">ADTS</span><span class="sxs-lookup"><span data-stu-id="ecf01-235">ADTS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-236">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-236">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-237">RIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-237">RIFF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-238">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-238">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-239">AC-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-239">AC-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-240">AMR</span><span class="sxs-lookup"><span data-stu-id="ecf01-240">AMR</span></span></th>
<th align="left"><span data-ttu-id="ecf01-241">3GP</span><span class="sxs-lookup"><span data-stu-id="ecf01-241">3GP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-242">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-242">FLAC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-243">WAV</span><span class="sxs-lookup"><span data-stu-id="ecf01-243">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-244">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-244">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-245">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-245">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-246">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-246">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-247">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-247">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-248">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-248">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-249">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-249">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-250">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="ecf01-250">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-251">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-251">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-252">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-252">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-253">AC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-253">AC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-254">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-254">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-255">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-255">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-256">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-256">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-257">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-257">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-258">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-258">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-259">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-259">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-260">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-260">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-261">ALAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-261">ALAC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-262">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-262">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-263">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="ecf01-263">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="ecf01-264">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-264">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-265">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-265">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-266">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-266">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-267">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-267">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-268">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-268">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-269">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="ecf01-269">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-270">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-270">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-271">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="ecf01-271">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-272">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-272">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-273">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-273">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-274">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-274">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-275">LPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-275">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-276">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-276">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-277">MP3</span><span class="sxs-lookup"><span data-stu-id="ecf01-277">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-278">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-278">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-279">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="ecf01-279">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-280">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-280">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-281">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-281">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-282">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-282">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-283">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="ecf01-283">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-284">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-284">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-285">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="ecf01-285">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-286">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-286">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-287">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="ecf01-287">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-288">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-288">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-arm"></a><span data-ttu-id="ecf01-289">IoT Core (ARM)</span><span class="sxs-lookup"><span data-stu-id="ecf01-289">IoT Core (ARM)</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-290">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-290">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-291">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-291">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-292">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-292">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-293">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-293">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-294">ADTS</span><span class="sxs-lookup"><span data-stu-id="ecf01-294">ADTS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-295">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-295">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-296">RIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-296">RIFF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-297">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-297">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-298">AC-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-298">AC-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-299">AMR</span><span class="sxs-lookup"><span data-stu-id="ecf01-299">AMR</span></span></th>
<th align="left"><span data-ttu-id="ecf01-300">3GP</span><span class="sxs-lookup"><span data-stu-id="ecf01-300">3GP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-301">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-301">FLAC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-302">WAV</span><span class="sxs-lookup"><span data-stu-id="ecf01-302">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-303">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-303">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-304">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-304">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-305">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-305">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-306">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-306">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-307">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-307">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-308">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-308">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-309">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="ecf01-309">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-310">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-310">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-311">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-311">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-312">AC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-312">AC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-313">EAC3/EC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-313">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-314">ALAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-314">ALAC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-315">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-315">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-316">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="ecf01-316">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="ecf01-317">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-317">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-318">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-318">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-319">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-319">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-320">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-320">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-321">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-321">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-322">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="ecf01-322">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-323">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-323">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-324">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="ecf01-324">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-325">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-325">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-326">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-326">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-327">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-327">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-328">LPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-328">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-329">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-329">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-330">MP3</span><span class="sxs-lookup"><span data-stu-id="ecf01-330">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-331">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-331">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-332">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="ecf01-332">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-333">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-333">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-334">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-334">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-335">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-335">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-336">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="ecf01-336">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-337">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-337">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-338">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="ecf01-338">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-339">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-339">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-340">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="ecf01-340">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-341">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-341">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="ecf01-342">XBox</span><span class="sxs-lookup"><span data-stu-id="ecf01-342">XBox</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-343">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-343">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-344">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-344">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-345">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-345">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-346">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-346">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-347">ADTS</span><span class="sxs-lookup"><span data-stu-id="ecf01-347">ADTS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-348">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-348">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-349">RIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-349">RIFF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-350">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-350">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-351">AC-3</span><span class="sxs-lookup"><span data-stu-id="ecf01-351">AC-3</span></span></th>
<th align="left"><span data-ttu-id="ecf01-352">AMR</span><span class="sxs-lookup"><span data-stu-id="ecf01-352">AMR</span></span></th>
<th align="left"><span data-ttu-id="ecf01-353">3GP</span><span class="sxs-lookup"><span data-stu-id="ecf01-353">3GP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-354">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-354">FLAC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-355">WAV</span><span class="sxs-lookup"><span data-stu-id="ecf01-355">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-356">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-356">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-357">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-357">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-358">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-358">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-359">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="ecf01-359">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="ecf01-360">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-360">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-361">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-361">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-362">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="ecf01-362">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-363">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-363">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-364">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-364">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-365">AC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-365">AC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-366">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-366">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-367">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-367">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-368">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-368">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-369">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="ecf01-369">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="ecf01-370">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-370">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-371">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-371">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-372">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-372">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-373">ALAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-373">ALAC</span></span></td>
<td align="left"><span data-ttu-id="ecf01-374">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-374">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-375">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="ecf01-375">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="ecf01-376">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-376">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-377">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-377">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-378">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-378">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-379">FLAC</span><span class="sxs-lookup"><span data-stu-id="ecf01-379">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-380">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-380">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-381">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="ecf01-381">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-382">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-382">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-383">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="ecf01-383">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-384">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-384">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-385">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-385">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-386">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-386">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-387">LPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-387">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-388">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-388">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-389">MP3</span><span class="sxs-lookup"><span data-stu-id="ecf01-389">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-390">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-390">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-391">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="ecf01-391">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-392">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-392">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-393">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="ecf01-393">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-394">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-394">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-395">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="ecf01-395">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-396">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-396">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-397">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="ecf01-397">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-398">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-398">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-399">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="ecf01-399">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-400">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-400">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

## <a name="video-codec--format-support"></a><span data-ttu-id="ecf01-401">Unterstützung von Videocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="ecf01-401">Video codec & format support</span></span>

<span data-ttu-id="ecf01-402">In den folgenden Tabellen wird die Unterstützung von Videocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-402">The following tables show the video codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="ecf01-403">Wo H.265-Unterstützung angegeben ist, gilt diese nicht unbedingt für alle Geräten innerhalb der Gerätefamilie.</span><span class="sxs-lookup"><span data-stu-id="ecf01-403">Where H.265 support is indicated, it is not necessarily supported by all devices within the device family.</span></span>
> <span data-ttu-id="ecf01-404">Wo MPEG-2/MPEG-1-Unterstützung angegeben ist, gilt diese nur mit der Installation der optionalen universellen Microsoft DVD-Windows-App.</span><span class="sxs-lookup"><span data-stu-id="ecf01-404">Where MPEG-2/MPEG-1 support is indicated, it is only supported with the installation of the optional Microsoft DVD Universal Windows app.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="ecf01-405">Desktop</span><span class="sxs-lookup"><span data-stu-id="ecf01-405">Desktop</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-406">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-406">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-407">FOURCC</span><span class="sxs-lookup"><span data-stu-id="ecf01-407">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-408">fMP4</span><span class="sxs-lookup"><span data-stu-id="ecf01-408">fMP4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-409">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-409">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-410">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="ecf01-410">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-411">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="ecf01-411">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-412">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-412">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="ecf01-413">3GPP</span><span class="sxs-lookup"><span data-stu-id="ecf01-413">3GPP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-414">3GPP2</span><span class="sxs-lookup"><span data-stu-id="ecf01-414">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-415">AVCHD</span><span class="sxs-lookup"><span data-stu-id="ecf01-415">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="ecf01-416">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-416">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-417">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-417">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-418">MKV</span><span class="sxs-lookup"><span data-stu-id="ecf01-418">MKV</span></span></th>
<th align="left"><span data-ttu-id="ecf01-419">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-419">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-420">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-420">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-421">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-421">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-422">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-422">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-423">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-423">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-424">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-424">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-425">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-425">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-426">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-426">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-427">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-427">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-428">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-428">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-429">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-429">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-430">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-430">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-431">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="ecf01-431">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-432">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-432">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-433">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-433">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-434">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-434">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-435">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-435">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-436">H.265</span><span class="sxs-lookup"><span data-stu-id="ecf01-436">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-437">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-437">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-438">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-438">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-439">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-439">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-440">H.264</span><span class="sxs-lookup"><span data-stu-id="ecf01-440">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-441">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-441">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-442">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-442">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-443">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-443">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-444">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-444">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-445">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-445">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-446">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-446">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-447">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-447">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-448">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-448">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-449">H.263</span><span class="sxs-lookup"><span data-stu-id="ecf01-449">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-450">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-450">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-451">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-451">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-452">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-452">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-453">VC-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-453">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-454">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-454">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-455">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-455">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-456">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-456">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-457">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-457">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-458">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="ecf01-458">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-459">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-459">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-460">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-460">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-461">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-461">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-462">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="ecf01-462">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-463">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-463">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-464">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-464">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-465">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-465">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-466">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-466">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-467">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-467">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-468">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-468">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-469">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-469">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-470">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-470">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-471">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-471">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-472">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-472">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="ecf01-473">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="ecf01-473">Mobile</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-474">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-474">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-475">FOURCC</span><span class="sxs-lookup"><span data-stu-id="ecf01-475">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-476">fMP4</span><span class="sxs-lookup"><span data-stu-id="ecf01-476">fMP4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-477">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-477">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-478">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="ecf01-478">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-479">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="ecf01-479">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-480">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-480">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="ecf01-481">3GPP</span><span class="sxs-lookup"><span data-stu-id="ecf01-481">3GPP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-482">3GPP2</span><span class="sxs-lookup"><span data-stu-id="ecf01-482">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-483">AVCHD</span><span class="sxs-lookup"><span data-stu-id="ecf01-483">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="ecf01-484">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-484">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-485">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-485">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-486">MKV</span><span class="sxs-lookup"><span data-stu-id="ecf01-486">MKV</span></span></th>
<th align="left"><span data-ttu-id="ecf01-487">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-487">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-488">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-488">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-489">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-489">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-490">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="ecf01-490">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-491">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-491">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-492">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-492">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-493">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-493">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-494">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-494">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-495">H.265</span><span class="sxs-lookup"><span data-stu-id="ecf01-495">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-496">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-496">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-497">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-497">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-498">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-498">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-499">H.264</span><span class="sxs-lookup"><span data-stu-id="ecf01-499">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-500">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-500">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-501">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-501">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-502">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-502">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-503">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-503">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-504">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-504">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-505">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-505">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-506">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-506">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-507">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-507">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-508">H.263</span><span class="sxs-lookup"><span data-stu-id="ecf01-508">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-509">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-509">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-510">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-510">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-511">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-511">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-512">VC-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-512">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-513">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-513">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-514">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-514">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-515">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-515">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-516">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="ecf01-516">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-517">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="ecf01-517">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-518">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-518">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-519">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-519">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-520">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-520">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-521">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-521">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="ecf01-522">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="ecf01-522">IoT Core (x86)</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-523">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-523">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-524">FOURCC</span><span class="sxs-lookup"><span data-stu-id="ecf01-524">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-525">fMP4</span><span class="sxs-lookup"><span data-stu-id="ecf01-525">fMP4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-526">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-526">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-527">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="ecf01-527">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-528">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="ecf01-528">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-529">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-529">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="ecf01-530">3GPP</span><span class="sxs-lookup"><span data-stu-id="ecf01-530">3GPP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-531">3GPP2</span><span class="sxs-lookup"><span data-stu-id="ecf01-531">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-532">AVCHD</span><span class="sxs-lookup"><span data-stu-id="ecf01-532">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="ecf01-533">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-533">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-534">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-534">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-535">MKV</span><span class="sxs-lookup"><span data-stu-id="ecf01-535">MKV</span></span></th>
<th align="left"><span data-ttu-id="ecf01-536">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-536">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-537">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-537">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-538">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-538">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-539">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="ecf01-539">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-540">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-540">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-541">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-541">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-542">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-542">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-543">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-543">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-544">H.265</span><span class="sxs-lookup"><span data-stu-id="ecf01-544">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-545">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-545">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-546">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-546">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-547">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-547">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-548">H.264</span><span class="sxs-lookup"><span data-stu-id="ecf01-548">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-549">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-549">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-550">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-550">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-551">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-551">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-552">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-552">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-553">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-553">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-554">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-554">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-555">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-555">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-556">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-556">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-557">H.263</span><span class="sxs-lookup"><span data-stu-id="ecf01-557">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-558">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-558">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-559">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-559">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-560">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-560">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-561">VC-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-561">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-562">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-562">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-563">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-563">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-564">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-564">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-565">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-565">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-566">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="ecf01-566">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-567">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-567">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-568">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-568">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-569">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-569">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-570">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="ecf01-570">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-571">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-571">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-572">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-572">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-573">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-573">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-574">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-574">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-575">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-575">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-576">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-576">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-577">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-577">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-arm"></a><span data-ttu-id="ecf01-578">IoT (ARM)</span><span class="sxs-lookup"><span data-stu-id="ecf01-578">IoT (ARM)</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-579">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-579">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-580">FOURCC</span><span class="sxs-lookup"><span data-stu-id="ecf01-580">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-581">fMP4</span><span class="sxs-lookup"><span data-stu-id="ecf01-581">fMP4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-582">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-582">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-583">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="ecf01-583">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-584">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="ecf01-584">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-585">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-585">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="ecf01-586">3GPP</span><span class="sxs-lookup"><span data-stu-id="ecf01-586">3GPP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-587">3GPP2</span><span class="sxs-lookup"><span data-stu-id="ecf01-587">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-588">AVCHD</span><span class="sxs-lookup"><span data-stu-id="ecf01-588">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="ecf01-589">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-589">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-590">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-590">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-591">MKV</span><span class="sxs-lookup"><span data-stu-id="ecf01-591">MKV</span></span></th>
<th align="left"><span data-ttu-id="ecf01-592">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-592">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-593">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-593">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-594">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-594">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-595">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="ecf01-595">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-596">H.265</span><span class="sxs-lookup"><span data-stu-id="ecf01-596">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-597">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-597">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-598">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-598">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-599">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-599">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-600">H.264</span><span class="sxs-lookup"><span data-stu-id="ecf01-600">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-601">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-601">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-602">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-602">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-603">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-603">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-604">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-604">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-605">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-605">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-606">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-606">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-607">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-607">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-608">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-608">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-609">H.263</span><span class="sxs-lookup"><span data-stu-id="ecf01-609">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-610">VC-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-610">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-611">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-611">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-612">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-612">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-613">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-613">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-614">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-614">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-615">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="ecf01-615">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-616">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-616">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-617">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-617">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-618">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-618">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-619">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="ecf01-619">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-620">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-620">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-621">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-621">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-622">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-622">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-623">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-623">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="ecf01-624">XBox</span><span class="sxs-lookup"><span data-stu-id="ecf01-624">XBox</span></span>

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-625">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="ecf01-625">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="ecf01-626">FOURCC</span><span class="sxs-lookup"><span data-stu-id="ecf01-626">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="ecf01-627">fMP4</span><span class="sxs-lookup"><span data-stu-id="ecf01-627">fMP4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-628">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="ecf01-628">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="ecf01-629">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="ecf01-629">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-630">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="ecf01-630">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="ecf01-631">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-631">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="ecf01-632">3GPP</span><span class="sxs-lookup"><span data-stu-id="ecf01-632">3GPP</span></span></th>
<th align="left"><span data-ttu-id="ecf01-633">3GPP2</span><span class="sxs-lookup"><span data-stu-id="ecf01-633">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="ecf01-634">AVCHD</span><span class="sxs-lookup"><span data-stu-id="ecf01-634">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="ecf01-635">ASF</span><span class="sxs-lookup"><span data-stu-id="ecf01-635">ASF</span></span></th>
<th align="left"><span data-ttu-id="ecf01-636">AVI</span><span class="sxs-lookup"><span data-stu-id="ecf01-636">AVI</span></span></th>
<th align="left"><span data-ttu-id="ecf01-637">MKV</span><span class="sxs-lookup"><span data-stu-id="ecf01-637">MKV</span></span></th>
<th align="left"><span data-ttu-id="ecf01-638">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-638">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-639">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-639">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-640">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-640">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-641">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-641">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-642">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-642">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-643">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-643">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-644">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-644">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-645">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="ecf01-645">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-646">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-646">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-647">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-647">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-648">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-648">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-649">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-649">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-650">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="ecf01-650">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-651">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-651">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-652">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-652">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-653">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-653">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-654">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-654">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-655">H.265</span><span class="sxs-lookup"><span data-stu-id="ecf01-655">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-656">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-656">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-657">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-657">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-658">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-658">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-659">H.264</span><span class="sxs-lookup"><span data-stu-id="ecf01-659">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-660">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-660">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-661">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-661">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-662">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-662">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-663">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-663">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-664">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-664">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-665">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-665">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-666">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-666">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-667">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-667">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-668">H.263</span><span class="sxs-lookup"><span data-stu-id="ecf01-668">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-669">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-669">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-670">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-670">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-671">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-671">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-672">VC-1</span><span class="sxs-lookup"><span data-stu-id="ecf01-672">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-673">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-673">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-674">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-674">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-675">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-675">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-676">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="ecf01-676">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-677">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="ecf01-677">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-678">DV</span><span class="sxs-lookup"><span data-stu-id="ecf01-678">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-679">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-679">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-680">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-680">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="ecf01-681">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-681">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="image-codec--format-support"></a><span data-ttu-id="ecf01-682">Unterstützung von Bildcodecs und -formaten</span><span class="sxs-lookup"><span data-stu-id="ecf01-682">Image codec & format support</span></span> 

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ecf01-683">Codec</span><span class="sxs-lookup"><span data-stu-id="ecf01-683">Codec</span></span></th>
<th align="left"><span data-ttu-id="ecf01-684">Desktop</span><span class="sxs-lookup"><span data-stu-id="ecf01-684">Desktop</span></span></th>
<th align="left"><span data-ttu-id="ecf01-685">Andere Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="ecf01-685">Other device families</span></span></th>
</tr>
</thead>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-686">BMP</span><span class="sxs-lookup"><span data-stu-id="ecf01-686">BMP</span></span></td>
<td align="left"><span data-ttu-id="ecf01-687">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-687">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-688">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-688">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-689">DDS</span><span class="sxs-lookup"><span data-stu-id="ecf01-689">DDS</span></span></td>
<td align="left"><span data-ttu-id="ecf01-690">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ecf01-690">D/E<sup>1</sup></span></span></td>
<td align="left"><span data-ttu-id="ecf01-691">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ecf01-691">D/E<sup>1</sup></span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-692">DNG</span><span class="sxs-lookup"><span data-stu-id="ecf01-692">DNG</span></span></td>
<td align="left"><span data-ttu-id="ecf01-693">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ecf01-693">D<sup>2</sup></span></span></td>
<td align="left"><span data-ttu-id="ecf01-694">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ecf01-694">D<sup>2</sup></span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-695">GIF</span><span class="sxs-lookup"><span data-stu-id="ecf01-695">GIF</span></span></td>
<td align="left"><span data-ttu-id="ecf01-696">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-696">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-697">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-697">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-698">ICO</span><span class="sxs-lookup"><span data-stu-id="ecf01-698">ICO</span></span></td>
<td align="left"><span data-ttu-id="ecf01-699">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-699">D</span></span></td>
<td align="left"><span data-ttu-id="ecf01-700">D</span><span class="sxs-lookup"><span data-stu-id="ecf01-700">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-701">JPEG</span><span class="sxs-lookup"><span data-stu-id="ecf01-701">JPEG</span></span></td>
<td align="left"><span data-ttu-id="ecf01-702">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-702">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-703">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-703">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-704">JPEG-XR</span><span class="sxs-lookup"><span data-stu-id="ecf01-704">JPEG-XR</span></span></td>
<td align="left"><span data-ttu-id="ecf01-705">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-705">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-706">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-706">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-707">PNG</span><span class="sxs-lookup"><span data-stu-id="ecf01-707">PNG</span></span></td>
<td align="left"><span data-ttu-id="ecf01-708">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-708">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-709">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-709">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="ecf01-710">TIFF</span><span class="sxs-lookup"><span data-stu-id="ecf01-710">TIFF</span></span></td>
<td align="left"><span data-ttu-id="ecf01-711">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-711">D/E</span></span></td>
<td align="left"><span data-ttu-id="ecf01-712">D/E</span><span class="sxs-lookup"><span data-stu-id="ecf01-712">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="ecf01-713">Kamera-RAW</span><span class="sxs-lookup"><span data-stu-id="ecf01-713">Camera RAW</span></span></td>
<td align="left"><span data-ttu-id="ecf01-714">D<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="ecf01-714">D<sup>3</sup></span></span></td>
<td align="left"><span data-ttu-id="ecf01-715">Nein</span><span class="sxs-lookup"><span data-stu-id="ecf01-715">No</span></span></td>
</tr>
</table>

<span data-ttu-id="ecf01-716"><sup>1</sup> DDS-Bilder mit BC1- bis BC5-Komprimierung werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-716"><sup>1</sup> DDS images using BC1 through BC5 compression are supported.</span></span>  
<span data-ttu-id="ecf01-717"><sup>2</sup> DNG-Bilder mit einer nicht als RAW eingebetteten Vorschau werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-717"><sup>2</sup> DNG images with a non-RAW embedded preview are supported.</span></span>  
<span data-ttu-id="ecf01-718"><sup>3</sup> Nur bestimmte Kamera-RAW-Formate werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ecf01-718"><sup>3</sup> Only certain camera RAW formats are supported.</span></span>  

<span data-ttu-id="ecf01-719">Weitere Informationen zu Bildcodecs finden Sie unter [Systemeigene WIC-Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span><span class="sxs-lookup"><span data-stu-id="ecf01-719">For more information on image codecs, see [Native WIC Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span></span>