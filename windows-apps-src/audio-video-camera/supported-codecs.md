---
author: drewbatgit
ms.assetid: 9347AD7C-3A90-4073-BFF4-9E8237398343
description: In diesem Artikel wird aufgeführt, welche Audio- und Videocodecs und welche Formate für UWP-Apps unterstützt werden.
title: Unterstützte Codecs
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 57a604b1b3996019bcf6e39bc88c9a59a74cb51c
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5939355"
---
# <a name="supported-codecs"></a><span data-ttu-id="2f129-104">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="2f129-104">Supported codecs</span></span>

<span data-ttu-id="2f129-105">In diesem Artikel ist die Verfügbarkeit von Audio-, Video- und Bild-Codecs und -Formaten für UWP-Apps standardmäßig für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2f129-105">This article lists the audio, video, and image codec and format availability for UWP apps by default for each device family.</span></span> <span data-ttu-id="2f129-106">Beachten Sie, dass diese Tabellen die Codecs enthalten, die in der Windows10-Installation für die angegebene Gerätefamilie enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="2f129-106">Note that these tables list the codecs that are included with the Windows 10 installation for the specified device family.</span></span> <span data-ttu-id="2f129-107">Benutzer und Apps können zusätzliche Codecs installieren, die unter Umständen zur Verwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="2f129-107">Users and apps can install additional codecs that may be available to use.</span></span> <span data-ttu-id="2f129-108">Sie können zur Laufzeit den Satz von Codecs abfragen, die derzeit für ein bestimmtes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2f129-108">You can query at runtime for the set of codecs that are currently available for a specific device.</span></span> <span data-ttu-id="2f129-109">Weitere Informationen finden Sie unter [Abfragen von auf einem Gerät installierten Codecs](codec-query.md).</span><span class="sxs-lookup"><span data-stu-id="2f129-109">For more information, see [Query for codecs installed on a device](codec-query.md).</span></span>

<span data-ttu-id="2f129-110">In den folgenden Tabellen steht „D“ für Decoderunterstützung und „E“ für Encoderunterstützung.</span><span class="sxs-lookup"><span data-stu-id="2f129-110">In the tables below "D" indicates decoder support and "E" indicates encoder support.</span></span>

## <a name="audio-codec--format-support"></a><span data-ttu-id="2f129-111">Unterstützung von Audiocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="2f129-111">Audio codec & format support</span></span>

<span data-ttu-id="2f129-112">In den folgenden Tabellen wird die Unterstützung von Audiocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2f129-112">The following tables show the audio codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="2f129-113">Wo AMR-NB-Unterstützung angegeben ist, wird dieser Codec nicht auf Server-SKUs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2f129-113">Where AMR-NB support is indicated, this codec is not supported on Server SKUs.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="2f129-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="2f129-114">Desktop</span></span>

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
<th align="left"><span data-ttu-id="2f129-115">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-115">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-116">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-116">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-117">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="2f129-117">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-118">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-118">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="2f129-119">ADTS</span><span class="sxs-lookup"><span data-stu-id="2f129-119">ADTS</span></span></th>
<th align="left"><span data-ttu-id="2f129-120">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-120">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-121">RIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-121">RIFF</span></span></th>
<th align="left"><span data-ttu-id="2f129-122">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-122">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-123">AC-3</span><span class="sxs-lookup"><span data-stu-id="2f129-123">AC-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-124">AMR</span><span class="sxs-lookup"><span data-stu-id="2f129-124">AMR</span></span></th>
<th align="left"><span data-ttu-id="2f129-125">3GP</span><span class="sxs-lookup"><span data-stu-id="2f129-125">3GP</span></span></th>
<th align="left"><span data-ttu-id="2f129-126">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-126">FLAC</span></span></th>
<th align="left"><span data-ttu-id="2f129-127">WAV</span><span class="sxs-lookup"><span data-stu-id="2f129-127">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-128">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-128">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-129">D</span><span class="sxs-lookup"><span data-stu-id="2f129-129">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-130">D</span><span class="sxs-lookup"><span data-stu-id="2f129-130">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-131">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-131">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-132">D</span><span class="sxs-lookup"><span data-stu-id="2f129-132">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-133">D</span><span class="sxs-lookup"><span data-stu-id="2f129-133">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-134">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="2f129-134">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="2f129-135">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-135">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-136">D</span><span class="sxs-lookup"><span data-stu-id="2f129-136">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-137">AC3</span><span class="sxs-lookup"><span data-stu-id="2f129-137">AC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-138">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-138">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-139">D</span><span class="sxs-lookup"><span data-stu-id="2f129-139">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-140">D</span><span class="sxs-lookup"><span data-stu-id="2f129-140">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-141">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="2f129-141">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-142">D</span><span class="sxs-lookup"><span data-stu-id="2f129-142">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-143">D</span><span class="sxs-lookup"><span data-stu-id="2f129-143">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-144">D</span><span class="sxs-lookup"><span data-stu-id="2f129-144">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-145">ALAC</span><span class="sxs-lookup"><span data-stu-id="2f129-145">ALAC</span></span></td>
<td align="left"><span data-ttu-id="2f129-146">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-146">D/E</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-147">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="2f129-147">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="2f129-148">D</span><span class="sxs-lookup"><span data-stu-id="2f129-148">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-149">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-149">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-150">D</span><span class="sxs-lookup"><span data-stu-id="2f129-150">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-151">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-151">FLAC</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-152">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-152">D/E</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-153">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="2f129-153">G.711 (A-Law, µ-law)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-154">D</span><span class="sxs-lookup"><span data-stu-id="2f129-154">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-155">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="2f129-155">GSM 6.10</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-156">D</span><span class="sxs-lookup"><span data-stu-id="2f129-156">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-157">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-157">IMA ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-158">D</span><span class="sxs-lookup"><span data-stu-id="2f129-158">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-159">LPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-159">LPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-160">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-160">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-161">MP3</span><span class="sxs-lookup"><span data-stu-id="2f129-161">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-162">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-162">D/E</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-163">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="2f129-163">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-164">D</span><span class="sxs-lookup"><span data-stu-id="2f129-164">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-165">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-165">MS ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-166">D</span><span class="sxs-lookup"><span data-stu-id="2f129-166">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-167">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="2f129-167">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-168">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-168">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-169">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="2f129-169">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-170">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-170">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-171">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="2f129-171">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-172">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-172">D/E</span></span></td>
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

 

### <a name="mobile"></a><span data-ttu-id="2f129-173">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="2f129-173">Mobile</span></span>

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
<th align="left"><span data-ttu-id="2f129-174">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-174">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-175">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-175">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-176">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="2f129-176">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-177">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-177">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="2f129-178">ADTS</span><span class="sxs-lookup"><span data-stu-id="2f129-178">ADTS</span></span></th>
<th align="left"><span data-ttu-id="2f129-179">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-179">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-180">RIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-180">RIFF</span></span></th>
<th align="left"><span data-ttu-id="2f129-181">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-181">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-182">AC-3</span><span class="sxs-lookup"><span data-stu-id="2f129-182">AC-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-183">AMR</span><span class="sxs-lookup"><span data-stu-id="2f129-183">AMR</span></span></th>
<th align="left"><span data-ttu-id="2f129-184">3GP</span><span class="sxs-lookup"><span data-stu-id="2f129-184">3GP</span></span></th>
<th align="left"><span data-ttu-id="2f129-185">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-185">FLAC</span></span></th>
<th align="left"><span data-ttu-id="2f129-186">WAV</span><span class="sxs-lookup"><span data-stu-id="2f129-186">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-187">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-187">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-188">D</span><span class="sxs-lookup"><span data-stu-id="2f129-188">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-189">D</span><span class="sxs-lookup"><span data-stu-id="2f129-189">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-190">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-190">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-191">D</span><span class="sxs-lookup"><span data-stu-id="2f129-191">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-192">D</span><span class="sxs-lookup"><span data-stu-id="2f129-192">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-193">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="2f129-193">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="2f129-194">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-194">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-195">D</span><span class="sxs-lookup"><span data-stu-id="2f129-195">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-196">AC3</span><span class="sxs-lookup"><span data-stu-id="2f129-196">AC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-197">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-197">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-198">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-198">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-199">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-199">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="2f129-200">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-200">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="2f129-201">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-201">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="2f129-202">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="2f129-202">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-203">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="2f129-203">EAC3 / EC3</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-204">ALAC</span><span class="sxs-lookup"><span data-stu-id="2f129-204">ALAC</span></span></td>
<td align="left"><span data-ttu-id="2f129-205">D</span><span class="sxs-lookup"><span data-stu-id="2f129-205">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-206">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="2f129-206">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="2f129-207">D</span><span class="sxs-lookup"><span data-stu-id="2f129-207">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-208">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-208">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-209">D</span><span class="sxs-lookup"><span data-stu-id="2f129-209">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-210">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-210">FLAC</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-211">D</span><span class="sxs-lookup"><span data-stu-id="2f129-211">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-212">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="2f129-212">G.711 (A-Law, µ-law)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-213">D</span><span class="sxs-lookup"><span data-stu-id="2f129-213">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-214">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="2f129-214">GSM 6.10</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-215">D</span><span class="sxs-lookup"><span data-stu-id="2f129-215">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-216">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-216">IMA ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-217">D</span><span class="sxs-lookup"><span data-stu-id="2f129-217">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-218">LPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-218">LPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-219">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-219">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-220">MP3</span><span class="sxs-lookup"><span data-stu-id="2f129-220">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-221">D</span><span class="sxs-lookup"><span data-stu-id="2f129-221">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-222">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="2f129-222">MPEG-1/2</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-223">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-223">MS ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-224">D</span><span class="sxs-lookup"><span data-stu-id="2f129-224">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-225">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="2f129-225">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-226">D</span><span class="sxs-lookup"><span data-stu-id="2f129-226">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-227">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="2f129-227">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-228">D</span><span class="sxs-lookup"><span data-stu-id="2f129-228">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-229">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="2f129-229">WMA Voice</span></span></td>
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

 

### <a name="iot-core-x86"></a><span data-ttu-id="2f129-230">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="2f129-230">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="2f129-231">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-231">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-232">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-232">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-233">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="2f129-233">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-234">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-234">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="2f129-235">ADTS</span><span class="sxs-lookup"><span data-stu-id="2f129-235">ADTS</span></span></th>
<th align="left"><span data-ttu-id="2f129-236">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-236">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-237">RIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-237">RIFF</span></span></th>
<th align="left"><span data-ttu-id="2f129-238">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-238">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-239">AC-3</span><span class="sxs-lookup"><span data-stu-id="2f129-239">AC-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-240">AMR</span><span class="sxs-lookup"><span data-stu-id="2f129-240">AMR</span></span></th>
<th align="left"><span data-ttu-id="2f129-241">3GP</span><span class="sxs-lookup"><span data-stu-id="2f129-241">3GP</span></span></th>
<th align="left"><span data-ttu-id="2f129-242">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-242">FLAC</span></span></th>
<th align="left"><span data-ttu-id="2f129-243">WAV</span><span class="sxs-lookup"><span data-stu-id="2f129-243">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-244">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-244">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-245">D</span><span class="sxs-lookup"><span data-stu-id="2f129-245">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-246">D</span><span class="sxs-lookup"><span data-stu-id="2f129-246">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-247">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-247">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-248">D</span><span class="sxs-lookup"><span data-stu-id="2f129-248">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-249">D</span><span class="sxs-lookup"><span data-stu-id="2f129-249">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-250">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="2f129-250">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="2f129-251">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-251">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-252">D</span><span class="sxs-lookup"><span data-stu-id="2f129-252">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-253">AC3</span><span class="sxs-lookup"><span data-stu-id="2f129-253">AC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-254">D</span><span class="sxs-lookup"><span data-stu-id="2f129-254">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-255">D</span><span class="sxs-lookup"><span data-stu-id="2f129-255">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-256">D</span><span class="sxs-lookup"><span data-stu-id="2f129-256">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-257">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="2f129-257">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-258">D</span><span class="sxs-lookup"><span data-stu-id="2f129-258">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-259">D</span><span class="sxs-lookup"><span data-stu-id="2f129-259">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-260">D</span><span class="sxs-lookup"><span data-stu-id="2f129-260">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-261">ALAC</span><span class="sxs-lookup"><span data-stu-id="2f129-261">ALAC</span></span></td>
<td align="left"><span data-ttu-id="2f129-262">D</span><span class="sxs-lookup"><span data-stu-id="2f129-262">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-263">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="2f129-263">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="2f129-264">D</span><span class="sxs-lookup"><span data-stu-id="2f129-264">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-265">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-265">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-266">D</span><span class="sxs-lookup"><span data-stu-id="2f129-266">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-267">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-267">FLAC</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-268">D</span><span class="sxs-lookup"><span data-stu-id="2f129-268">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-269">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="2f129-269">G.711 (A-Law, µ-law)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-270">D</span><span class="sxs-lookup"><span data-stu-id="2f129-270">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-271">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="2f129-271">GSM 6.10</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-272">D</span><span class="sxs-lookup"><span data-stu-id="2f129-272">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-273">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-273">IMA ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-274">D</span><span class="sxs-lookup"><span data-stu-id="2f129-274">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-275">LPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-275">LPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-276">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-276">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-277">MP3</span><span class="sxs-lookup"><span data-stu-id="2f129-277">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-278">D</span><span class="sxs-lookup"><span data-stu-id="2f129-278">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-279">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="2f129-279">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-280">D</span><span class="sxs-lookup"><span data-stu-id="2f129-280">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-281">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-281">MS ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-282">D</span><span class="sxs-lookup"><span data-stu-id="2f129-282">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-283">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="2f129-283">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-284">D</span><span class="sxs-lookup"><span data-stu-id="2f129-284">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-285">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="2f129-285">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-286">D</span><span class="sxs-lookup"><span data-stu-id="2f129-286">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-287">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="2f129-287">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-288">D</span><span class="sxs-lookup"><span data-stu-id="2f129-288">D</span></span></td>
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

 

### <a name="iot-core-arm"></a><span data-ttu-id="2f129-289">IoT Core (ARM)</span><span class="sxs-lookup"><span data-stu-id="2f129-289">IoT Core (ARM)</span></span>

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
<th align="left"><span data-ttu-id="2f129-290">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-290">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-291">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-291">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-292">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="2f129-292">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-293">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-293">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="2f129-294">ADTS</span><span class="sxs-lookup"><span data-stu-id="2f129-294">ADTS</span></span></th>
<th align="left"><span data-ttu-id="2f129-295">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-295">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-296">RIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-296">RIFF</span></span></th>
<th align="left"><span data-ttu-id="2f129-297">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-297">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-298">AC-3</span><span class="sxs-lookup"><span data-stu-id="2f129-298">AC-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-299">AMR</span><span class="sxs-lookup"><span data-stu-id="2f129-299">AMR</span></span></th>
<th align="left"><span data-ttu-id="2f129-300">3GP</span><span class="sxs-lookup"><span data-stu-id="2f129-300">3GP</span></span></th>
<th align="left"><span data-ttu-id="2f129-301">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-301">FLAC</span></span></th>
<th align="left"><span data-ttu-id="2f129-302">WAV</span><span class="sxs-lookup"><span data-stu-id="2f129-302">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-303">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-303">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-304">D</span><span class="sxs-lookup"><span data-stu-id="2f129-304">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-305">D</span><span class="sxs-lookup"><span data-stu-id="2f129-305">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-306">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-306">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-307">D</span><span class="sxs-lookup"><span data-stu-id="2f129-307">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-308">D</span><span class="sxs-lookup"><span data-stu-id="2f129-308">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-309">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="2f129-309">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="2f129-310">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-310">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-311">D</span><span class="sxs-lookup"><span data-stu-id="2f129-311">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-312">AC3</span><span class="sxs-lookup"><span data-stu-id="2f129-312">AC3</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-313">EAC3/EC3</span><span class="sxs-lookup"><span data-stu-id="2f129-313">EAC3 / EC3</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-314">ALAC</span><span class="sxs-lookup"><span data-stu-id="2f129-314">ALAC</span></span></td>
<td align="left"><span data-ttu-id="2f129-315">D</span><span class="sxs-lookup"><span data-stu-id="2f129-315">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-316">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="2f129-316">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="2f129-317">D</span><span class="sxs-lookup"><span data-stu-id="2f129-317">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-318">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-318">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-319">D</span><span class="sxs-lookup"><span data-stu-id="2f129-319">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-320">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-320">FLAC</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-321">D</span><span class="sxs-lookup"><span data-stu-id="2f129-321">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-322">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="2f129-322">G.711 (A-Law, µ-law)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-323">D</span><span class="sxs-lookup"><span data-stu-id="2f129-323">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-324">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="2f129-324">GSM 6.10</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-325">D</span><span class="sxs-lookup"><span data-stu-id="2f129-325">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-326">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-326">IMA ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-327">D</span><span class="sxs-lookup"><span data-stu-id="2f129-327">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-328">LPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-328">LPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-329">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-329">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-330">MP3</span><span class="sxs-lookup"><span data-stu-id="2f129-330">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-331">D</span><span class="sxs-lookup"><span data-stu-id="2f129-331">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-332">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="2f129-332">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-333">D</span><span class="sxs-lookup"><span data-stu-id="2f129-333">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-334">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-334">MS ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-335">D</span><span class="sxs-lookup"><span data-stu-id="2f129-335">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-336">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="2f129-336">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-337">D</span><span class="sxs-lookup"><span data-stu-id="2f129-337">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-338">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="2f129-338">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-339">D</span><span class="sxs-lookup"><span data-stu-id="2f129-339">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-340">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="2f129-340">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-341">D</span><span class="sxs-lookup"><span data-stu-id="2f129-341">D</span></span></td>
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

 

### <a name="xbox"></a><span data-ttu-id="2f129-342">XBox</span><span class="sxs-lookup"><span data-stu-id="2f129-342">XBox</span></span>

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
<th align="left"><span data-ttu-id="2f129-343">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-343">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-344">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-344">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-345">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="2f129-345">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-346">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-346">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="2f129-347">ADTS</span><span class="sxs-lookup"><span data-stu-id="2f129-347">ADTS</span></span></th>
<th align="left"><span data-ttu-id="2f129-348">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-348">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-349">RIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-349">RIFF</span></span></th>
<th align="left"><span data-ttu-id="2f129-350">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-350">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-351">AC-3</span><span class="sxs-lookup"><span data-stu-id="2f129-351">AC-3</span></span></th>
<th align="left"><span data-ttu-id="2f129-352">AMR</span><span class="sxs-lookup"><span data-stu-id="2f129-352">AMR</span></span></th>
<th align="left"><span data-ttu-id="2f129-353">3GP</span><span class="sxs-lookup"><span data-stu-id="2f129-353">3GP</span></span></th>
<th align="left"><span data-ttu-id="2f129-354">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-354">FLAC</span></span></th>
<th align="left"><span data-ttu-id="2f129-355">WAV</span><span class="sxs-lookup"><span data-stu-id="2f129-355">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-356">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-356">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-357">D</span><span class="sxs-lookup"><span data-stu-id="2f129-357">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-358">D</span><span class="sxs-lookup"><span data-stu-id="2f129-358">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-359">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="2f129-359">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="2f129-360">D</span><span class="sxs-lookup"><span data-stu-id="2f129-360">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-361">D</span><span class="sxs-lookup"><span data-stu-id="2f129-361">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-362">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="2f129-362">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="2f129-363">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-363">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-364">D</span><span class="sxs-lookup"><span data-stu-id="2f129-364">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-365">AC3</span><span class="sxs-lookup"><span data-stu-id="2f129-365">AC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-366">D</span><span class="sxs-lookup"><span data-stu-id="2f129-366">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-367">D</span><span class="sxs-lookup"><span data-stu-id="2f129-367">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-368">D</span><span class="sxs-lookup"><span data-stu-id="2f129-368">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-369">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="2f129-369">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="2f129-370">D</span><span class="sxs-lookup"><span data-stu-id="2f129-370">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-371">D</span><span class="sxs-lookup"><span data-stu-id="2f129-371">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-372">D</span><span class="sxs-lookup"><span data-stu-id="2f129-372">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-373">ALAC</span><span class="sxs-lookup"><span data-stu-id="2f129-373">ALAC</span></span></td>
<td align="left"><span data-ttu-id="2f129-374">D</span><span class="sxs-lookup"><span data-stu-id="2f129-374">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-375">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="2f129-375">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="2f129-376">D</span><span class="sxs-lookup"><span data-stu-id="2f129-376">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-377">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-377">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-378">D</span><span class="sxs-lookup"><span data-stu-id="2f129-378">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-379">FLAC</span><span class="sxs-lookup"><span data-stu-id="2f129-379">FLAC</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-380">D</span><span class="sxs-lookup"><span data-stu-id="2f129-380">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-381">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="2f129-381">G.711 (A-Law, µ-law)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-382">D</span><span class="sxs-lookup"><span data-stu-id="2f129-382">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-383">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="2f129-383">GSM 6.10</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-384">D</span><span class="sxs-lookup"><span data-stu-id="2f129-384">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-385">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-385">IMA ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-386">D</span><span class="sxs-lookup"><span data-stu-id="2f129-386">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-387">LPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-387">LPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-388">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-388">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-389">MP3</span><span class="sxs-lookup"><span data-stu-id="2f129-389">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-390">D</span><span class="sxs-lookup"><span data-stu-id="2f129-390">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-391">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="2f129-391">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-392">D</span><span class="sxs-lookup"><span data-stu-id="2f129-392">D</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-393">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="2f129-393">MS ADPCM</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-394">D</span><span class="sxs-lookup"><span data-stu-id="2f129-394">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-395">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="2f129-395">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-396">D</span><span class="sxs-lookup"><span data-stu-id="2f129-396">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-397">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="2f129-397">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-398">D</span><span class="sxs-lookup"><span data-stu-id="2f129-398">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-399">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="2f129-399">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-400">D</span><span class="sxs-lookup"><span data-stu-id="2f129-400">D</span></span></td>
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

 

## <a name="video-codec--format-support"></a><span data-ttu-id="2f129-401">Unterstützung von Videocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="2f129-401">Video codec & format support</span></span>

<span data-ttu-id="2f129-402">In den folgenden Tabellen wird die Unterstützung von Videocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2f129-402">The following tables show the video codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="2f129-403">Wo H.265-Unterstützung angegeben ist, gilt diese nicht unbedingt für alle Geräten innerhalb der Gerätefamilie.</span><span class="sxs-lookup"><span data-stu-id="2f129-403">Where H.265 support is indicated, it is not necessarily supported by all devices within the device family.</span></span>
> <span data-ttu-id="2f129-404">Wo MPEG-2/MPEG-1-Unterstützung angegeben ist, gilt diese nur mit der Installation der optionalen universellen Microsoft DVD-Windows-App.</span><span class="sxs-lookup"><span data-stu-id="2f129-404">Where MPEG-2/MPEG-1 support is indicated, it is only supported with the installation of the optional Microsoft DVD Universal Windows app.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="2f129-405">Desktop</span><span class="sxs-lookup"><span data-stu-id="2f129-405">Desktop</span></span>

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
<th align="left"><span data-ttu-id="2f129-406">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-406">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-407">FOURCC</span><span class="sxs-lookup"><span data-stu-id="2f129-407">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="2f129-408">fMP4</span><span class="sxs-lookup"><span data-stu-id="2f129-408">fMP4</span></span></th>
<th align="left"><span data-ttu-id="2f129-409">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-409">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-410">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="2f129-410">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="2f129-411">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="2f129-411">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="2f129-412">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-412">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="2f129-413">3GPP</span><span class="sxs-lookup"><span data-stu-id="2f129-413">3GPP</span></span></th>
<th align="left"><span data-ttu-id="2f129-414">3GPP2</span><span class="sxs-lookup"><span data-stu-id="2f129-414">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="2f129-415">AVCHD</span><span class="sxs-lookup"><span data-stu-id="2f129-415">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="2f129-416">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-416">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-417">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-417">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-418">MKV</span><span class="sxs-lookup"><span data-stu-id="2f129-418">MKV</span></span></th>
<th align="left"><span data-ttu-id="2f129-419">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-419">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-420">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-420">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-421">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-421">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-422">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-422">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-423">D</span><span class="sxs-lookup"><span data-stu-id="2f129-423">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-424">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-424">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-425">D</span><span class="sxs-lookup"><span data-stu-id="2f129-425">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-426">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-426">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-427">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-427">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-428">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-428">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-429">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-429">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-430">D</span><span class="sxs-lookup"><span data-stu-id="2f129-430">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-431">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2f129-431">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-432">D</span><span class="sxs-lookup"><span data-stu-id="2f129-432">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-433">D</span><span class="sxs-lookup"><span data-stu-id="2f129-433">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-434">D</span><span class="sxs-lookup"><span data-stu-id="2f129-434">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-435">D</span><span class="sxs-lookup"><span data-stu-id="2f129-435">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-436">H.265</span><span class="sxs-lookup"><span data-stu-id="2f129-436">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-437">D</span><span class="sxs-lookup"><span data-stu-id="2f129-437">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-438">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-438">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-439">D</span><span class="sxs-lookup"><span data-stu-id="2f129-439">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-440">H.264</span><span class="sxs-lookup"><span data-stu-id="2f129-440">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-441">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-441">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-442">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-442">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-443">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-443">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-444">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-444">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-445">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-445">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-446">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-446">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-447">D</span><span class="sxs-lookup"><span data-stu-id="2f129-447">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-448">D</span><span class="sxs-lookup"><span data-stu-id="2f129-448">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-449">H.263</span><span class="sxs-lookup"><span data-stu-id="2f129-449">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-450">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-450">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-451">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-451">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-452">D</span><span class="sxs-lookup"><span data-stu-id="2f129-452">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-453">VC-1</span><span class="sxs-lookup"><span data-stu-id="2f129-453">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-454">D</span><span class="sxs-lookup"><span data-stu-id="2f129-454">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-455">D</span><span class="sxs-lookup"><span data-stu-id="2f129-455">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-456">D</span><span class="sxs-lookup"><span data-stu-id="2f129-456">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-457">D</span><span class="sxs-lookup"><span data-stu-id="2f129-457">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-458">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="2f129-458">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-459">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-459">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-460">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-460">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-461">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-461">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-462">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="2f129-462">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-463">D</span><span class="sxs-lookup"><span data-stu-id="2f129-463">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-464">D</span><span class="sxs-lookup"><span data-stu-id="2f129-464">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-465">D</span><span class="sxs-lookup"><span data-stu-id="2f129-465">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-466">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-466">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-467">D</span><span class="sxs-lookup"><span data-stu-id="2f129-467">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-468">D</span><span class="sxs-lookup"><span data-stu-id="2f129-468">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-469">D</span><span class="sxs-lookup"><span data-stu-id="2f129-469">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-470">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-470">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-471">D</span><span class="sxs-lookup"><span data-stu-id="2f129-471">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-472">D</span><span class="sxs-lookup"><span data-stu-id="2f129-472">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="2f129-473">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="2f129-473">Mobile</span></span>

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
<th align="left"><span data-ttu-id="2f129-474">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-474">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-475">FOURCC</span><span class="sxs-lookup"><span data-stu-id="2f129-475">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="2f129-476">fMP4</span><span class="sxs-lookup"><span data-stu-id="2f129-476">fMP4</span></span></th>
<th align="left"><span data-ttu-id="2f129-477">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-477">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-478">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="2f129-478">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="2f129-479">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="2f129-479">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="2f129-480">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-480">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="2f129-481">3GPP</span><span class="sxs-lookup"><span data-stu-id="2f129-481">3GPP</span></span></th>
<th align="left"><span data-ttu-id="2f129-482">3GPP2</span><span class="sxs-lookup"><span data-stu-id="2f129-482">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="2f129-483">AVCHD</span><span class="sxs-lookup"><span data-stu-id="2f129-483">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="2f129-484">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-484">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-485">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-485">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-486">MKV</span><span class="sxs-lookup"><span data-stu-id="2f129-486">MKV</span></span></th>
<th align="left"><span data-ttu-id="2f129-487">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-487">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-488">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-488">MPEG-1</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-489">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-489">MPEG-2</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-490">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2f129-490">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-491">D</span><span class="sxs-lookup"><span data-stu-id="2f129-491">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-492">D</span><span class="sxs-lookup"><span data-stu-id="2f129-492">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-493">D</span><span class="sxs-lookup"><span data-stu-id="2f129-493">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-494">D</span><span class="sxs-lookup"><span data-stu-id="2f129-494">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-495">H.265</span><span class="sxs-lookup"><span data-stu-id="2f129-495">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-496">D</span><span class="sxs-lookup"><span data-stu-id="2f129-496">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-497">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-497">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-498">D</span><span class="sxs-lookup"><span data-stu-id="2f129-498">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-499">H.264</span><span class="sxs-lookup"><span data-stu-id="2f129-499">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-500">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-500">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-501">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-501">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-502">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-502">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-503">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-503">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-504">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-504">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-505">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-505">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-506">D</span><span class="sxs-lookup"><span data-stu-id="2f129-506">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-507">D</span><span class="sxs-lookup"><span data-stu-id="2f129-507">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-508">H.263</span><span class="sxs-lookup"><span data-stu-id="2f129-508">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-509">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-509">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-510">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-510">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-511">D</span><span class="sxs-lookup"><span data-stu-id="2f129-511">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-512">VC-1</span><span class="sxs-lookup"><span data-stu-id="2f129-512">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-513">D</span><span class="sxs-lookup"><span data-stu-id="2f129-513">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-514">D</span><span class="sxs-lookup"><span data-stu-id="2f129-514">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-515">D</span><span class="sxs-lookup"><span data-stu-id="2f129-515">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-516">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="2f129-516">WMV7/8/9</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-517">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="2f129-517">WMV9 Screen</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-518">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-518">DV</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-519">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-519">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-520">D</span><span class="sxs-lookup"><span data-stu-id="2f129-520">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-521">D</span><span class="sxs-lookup"><span data-stu-id="2f129-521">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="2f129-522">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="2f129-522">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="2f129-523">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-523">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-524">FOURCC</span><span class="sxs-lookup"><span data-stu-id="2f129-524">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="2f129-525">fMP4</span><span class="sxs-lookup"><span data-stu-id="2f129-525">fMP4</span></span></th>
<th align="left"><span data-ttu-id="2f129-526">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-526">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-527">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="2f129-527">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="2f129-528">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="2f129-528">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="2f129-529">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-529">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="2f129-530">3GPP</span><span class="sxs-lookup"><span data-stu-id="2f129-530">3GPP</span></span></th>
<th align="left"><span data-ttu-id="2f129-531">3GPP2</span><span class="sxs-lookup"><span data-stu-id="2f129-531">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="2f129-532">AVCHD</span><span class="sxs-lookup"><span data-stu-id="2f129-532">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="2f129-533">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-533">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-534">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-534">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-535">MKV</span><span class="sxs-lookup"><span data-stu-id="2f129-535">MKV</span></span></th>
<th align="left"><span data-ttu-id="2f129-536">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-536">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-537">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-537">MPEG-1</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-538">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-538">MPEG-2</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-539">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2f129-539">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-540">D</span><span class="sxs-lookup"><span data-stu-id="2f129-540">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-541">D</span><span class="sxs-lookup"><span data-stu-id="2f129-541">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-542">D</span><span class="sxs-lookup"><span data-stu-id="2f129-542">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-543">D</span><span class="sxs-lookup"><span data-stu-id="2f129-543">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-544">H.265</span><span class="sxs-lookup"><span data-stu-id="2f129-544">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-545">D</span><span class="sxs-lookup"><span data-stu-id="2f129-545">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-546">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-546">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-547">D</span><span class="sxs-lookup"><span data-stu-id="2f129-547">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-548">H.264</span><span class="sxs-lookup"><span data-stu-id="2f129-548">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-549">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-549">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-550">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-550">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-551">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-551">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-552">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-552">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-553">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-553">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-554">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-554">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-555">D</span><span class="sxs-lookup"><span data-stu-id="2f129-555">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-556">D</span><span class="sxs-lookup"><span data-stu-id="2f129-556">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-557">H.263</span><span class="sxs-lookup"><span data-stu-id="2f129-557">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-558">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-558">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-559">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-559">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-560">D</span><span class="sxs-lookup"><span data-stu-id="2f129-560">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-561">VC-1</span><span class="sxs-lookup"><span data-stu-id="2f129-561">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-562">D</span><span class="sxs-lookup"><span data-stu-id="2f129-562">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-563">D</span><span class="sxs-lookup"><span data-stu-id="2f129-563">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-564">D</span><span class="sxs-lookup"><span data-stu-id="2f129-564">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-565">D</span><span class="sxs-lookup"><span data-stu-id="2f129-565">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-566">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="2f129-566">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-567">D</span><span class="sxs-lookup"><span data-stu-id="2f129-567">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-568">D</span><span class="sxs-lookup"><span data-stu-id="2f129-568">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-569">D</span><span class="sxs-lookup"><span data-stu-id="2f129-569">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-570">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="2f129-570">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-571">D</span><span class="sxs-lookup"><span data-stu-id="2f129-571">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-572">D</span><span class="sxs-lookup"><span data-stu-id="2f129-572">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-573">D</span><span class="sxs-lookup"><span data-stu-id="2f129-573">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-574">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-574">DV</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-575">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-575">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-576">D</span><span class="sxs-lookup"><span data-stu-id="2f129-576">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-577">D</span><span class="sxs-lookup"><span data-stu-id="2f129-577">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-arm"></a><span data-ttu-id="2f129-578">IoT (ARM)</span><span class="sxs-lookup"><span data-stu-id="2f129-578">IoT (ARM)</span></span>

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
<th align="left"><span data-ttu-id="2f129-579">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-579">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-580">FOURCC</span><span class="sxs-lookup"><span data-stu-id="2f129-580">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="2f129-581">fMP4</span><span class="sxs-lookup"><span data-stu-id="2f129-581">fMP4</span></span></th>
<th align="left"><span data-ttu-id="2f129-582">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-582">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-583">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="2f129-583">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="2f129-584">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="2f129-584">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="2f129-585">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-585">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="2f129-586">3GPP</span><span class="sxs-lookup"><span data-stu-id="2f129-586">3GPP</span></span></th>
<th align="left"><span data-ttu-id="2f129-587">3GPP2</span><span class="sxs-lookup"><span data-stu-id="2f129-587">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="2f129-588">AVCHD</span><span class="sxs-lookup"><span data-stu-id="2f129-588">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="2f129-589">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-589">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-590">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-590">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-591">MKV</span><span class="sxs-lookup"><span data-stu-id="2f129-591">MKV</span></span></th>
<th align="left"><span data-ttu-id="2f129-592">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-592">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-593">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-593">MPEG-1</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-594">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-594">MPEG-2</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-595">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2f129-595">MPEG-4 (Part 2)</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-596">H.265</span><span class="sxs-lookup"><span data-stu-id="2f129-596">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-597">D</span><span class="sxs-lookup"><span data-stu-id="2f129-597">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-598">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-598">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-599">D</span><span class="sxs-lookup"><span data-stu-id="2f129-599">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-600">H.264</span><span class="sxs-lookup"><span data-stu-id="2f129-600">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-601">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-601">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-602">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-602">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-603">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-603">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-604">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-604">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-605">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-605">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-606">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-606">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-607">D</span><span class="sxs-lookup"><span data-stu-id="2f129-607">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-608">D</span><span class="sxs-lookup"><span data-stu-id="2f129-608">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-609">H.263</span><span class="sxs-lookup"><span data-stu-id="2f129-609">H.263</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-610">VC-1</span><span class="sxs-lookup"><span data-stu-id="2f129-610">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-611">D</span><span class="sxs-lookup"><span data-stu-id="2f129-611">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-612">D</span><span class="sxs-lookup"><span data-stu-id="2f129-612">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-613">D</span><span class="sxs-lookup"><span data-stu-id="2f129-613">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-614">D</span><span class="sxs-lookup"><span data-stu-id="2f129-614">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-615">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="2f129-615">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-616">D</span><span class="sxs-lookup"><span data-stu-id="2f129-616">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-617">D</span><span class="sxs-lookup"><span data-stu-id="2f129-617">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-618">D</span><span class="sxs-lookup"><span data-stu-id="2f129-618">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-619">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="2f129-619">WMV9 Screen</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-620">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-620">DV</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-621">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-621">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-622">D</span><span class="sxs-lookup"><span data-stu-id="2f129-622">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-623">D</span><span class="sxs-lookup"><span data-stu-id="2f129-623">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="2f129-624">XBox</span><span class="sxs-lookup"><span data-stu-id="2f129-624">XBox</span></span>

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
<th align="left"><span data-ttu-id="2f129-625">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="2f129-625">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="2f129-626">FOURCC</span><span class="sxs-lookup"><span data-stu-id="2f129-626">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="2f129-627">fMP4</span><span class="sxs-lookup"><span data-stu-id="2f129-627">fMP4</span></span></th>
<th align="left"><span data-ttu-id="2f129-628">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="2f129-628">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="2f129-629">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="2f129-629">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="2f129-630">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="2f129-630">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="2f129-631">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-631">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="2f129-632">3GPP</span><span class="sxs-lookup"><span data-stu-id="2f129-632">3GPP</span></span></th>
<th align="left"><span data-ttu-id="2f129-633">3GPP2</span><span class="sxs-lookup"><span data-stu-id="2f129-633">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="2f129-634">AVCHD</span><span class="sxs-lookup"><span data-stu-id="2f129-634">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="2f129-635">ASF</span><span class="sxs-lookup"><span data-stu-id="2f129-635">ASF</span></span></th>
<th align="left"><span data-ttu-id="2f129-636">AVI</span><span class="sxs-lookup"><span data-stu-id="2f129-636">AVI</span></span></th>
<th align="left"><span data-ttu-id="2f129-637">MKV</span><span class="sxs-lookup"><span data-stu-id="2f129-637">MKV</span></span></th>
<th align="left"><span data-ttu-id="2f129-638">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-638">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-639">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="2f129-639">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-640">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-640">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-641">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-641">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-642">D</span><span class="sxs-lookup"><span data-stu-id="2f129-642">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-643">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-643">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-644">D</span><span class="sxs-lookup"><span data-stu-id="2f129-644">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-645">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="2f129-645">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-646">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-646">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-647">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-647">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-648">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-648">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-649">D</span><span class="sxs-lookup"><span data-stu-id="2f129-649">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-650">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="2f129-650">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-651">D</span><span class="sxs-lookup"><span data-stu-id="2f129-651">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-652">D</span><span class="sxs-lookup"><span data-stu-id="2f129-652">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-653">D</span><span class="sxs-lookup"><span data-stu-id="2f129-653">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-654">D</span><span class="sxs-lookup"><span data-stu-id="2f129-654">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-655">H.265</span><span class="sxs-lookup"><span data-stu-id="2f129-655">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-656">D</span><span class="sxs-lookup"><span data-stu-id="2f129-656">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-657">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-657">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-658">D</span><span class="sxs-lookup"><span data-stu-id="2f129-658">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-659">H.264</span><span class="sxs-lookup"><span data-stu-id="2f129-659">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-660">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-660">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-661">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-661">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-662">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-662">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-663">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-663">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-664">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-664">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-665">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-665">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-666">D</span><span class="sxs-lookup"><span data-stu-id="2f129-666">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-667">D</span><span class="sxs-lookup"><span data-stu-id="2f129-667">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-668">H.263</span><span class="sxs-lookup"><span data-stu-id="2f129-668">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-669">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-669">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-670">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-670">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-671">D</span><span class="sxs-lookup"><span data-stu-id="2f129-671">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-672">VC-1</span><span class="sxs-lookup"><span data-stu-id="2f129-672">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-673">D</span><span class="sxs-lookup"><span data-stu-id="2f129-673">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-674">D</span><span class="sxs-lookup"><span data-stu-id="2f129-674">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-675">D</span><span class="sxs-lookup"><span data-stu-id="2f129-675">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-676">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="2f129-676">WMV7/8/9</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-677">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="2f129-677">WMV9 Screen</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-678">DV</span><span class="sxs-lookup"><span data-stu-id="2f129-678">DV</span></span></td>
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
<td align="left"><span data-ttu-id="2f129-679">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-679">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-680">D</span><span class="sxs-lookup"><span data-stu-id="2f129-680">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="2f129-681">D</span><span class="sxs-lookup"><span data-stu-id="2f129-681">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="image-codec--format-support"></a><span data-ttu-id="2f129-682">Unterstützung von Bildcodecs und -formaten</span><span class="sxs-lookup"><span data-stu-id="2f129-682">Image codec & format support</span></span> 

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2f129-683">Codec</span><span class="sxs-lookup"><span data-stu-id="2f129-683">Codec</span></span></th>
<th align="left"><span data-ttu-id="2f129-684">Desktop</span><span class="sxs-lookup"><span data-stu-id="2f129-684">Desktop</span></span></th>
<th align="left"><span data-ttu-id="2f129-685">Andere Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="2f129-685">Other device families</span></span></th>
</tr>
</thead>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-686">BMP</span><span class="sxs-lookup"><span data-stu-id="2f129-686">BMP</span></span></td>
<td align="left"><span data-ttu-id="2f129-687">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-687">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-688">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-688">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-689">DDS</span><span class="sxs-lookup"><span data-stu-id="2f129-689">DDS</span></span></td>
<td align="left"><span data-ttu-id="2f129-690">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2f129-690">D/E<sup>1</sup></span></span></td>
<td align="left"><span data-ttu-id="2f129-691">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2f129-691">D/E<sup>1</sup></span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-692">DNG</span><span class="sxs-lookup"><span data-stu-id="2f129-692">DNG</span></span></td>
<td align="left"><span data-ttu-id="2f129-693">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2f129-693">D<sup>2</sup></span></span></td>
<td align="left"><span data-ttu-id="2f129-694">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2f129-694">D<sup>2</sup></span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-695">GIF</span><span class="sxs-lookup"><span data-stu-id="2f129-695">GIF</span></span></td>
<td align="left"><span data-ttu-id="2f129-696">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-696">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-697">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-697">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-698">ICO</span><span class="sxs-lookup"><span data-stu-id="2f129-698">ICO</span></span></td>
<td align="left"><span data-ttu-id="2f129-699">D</span><span class="sxs-lookup"><span data-stu-id="2f129-699">D</span></span></td>
<td align="left"><span data-ttu-id="2f129-700">D</span><span class="sxs-lookup"><span data-stu-id="2f129-700">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-701">JPEG</span><span class="sxs-lookup"><span data-stu-id="2f129-701">JPEG</span></span></td>
<td align="left"><span data-ttu-id="2f129-702">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-702">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-703">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-703">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-704">JPEG-XR</span><span class="sxs-lookup"><span data-stu-id="2f129-704">JPEG-XR</span></span></td>
<td align="left"><span data-ttu-id="2f129-705">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-705">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-706">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-706">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-707">PNG</span><span class="sxs-lookup"><span data-stu-id="2f129-707">PNG</span></span></td>
<td align="left"><span data-ttu-id="2f129-708">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-708">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-709">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-709">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2f129-710">TIFF</span><span class="sxs-lookup"><span data-stu-id="2f129-710">TIFF</span></span></td>
<td align="left"><span data-ttu-id="2f129-711">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-711">D/E</span></span></td>
<td align="left"><span data-ttu-id="2f129-712">D/E</span><span class="sxs-lookup"><span data-stu-id="2f129-712">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2f129-713">Kamera-RAW</span><span class="sxs-lookup"><span data-stu-id="2f129-713">Camera RAW</span></span></td>
<td align="left"><span data-ttu-id="2f129-714">D<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2f129-714">D<sup>3</sup></span></span></td>
<td align="left"><span data-ttu-id="2f129-715">Nein</span><span class="sxs-lookup"><span data-stu-id="2f129-715">No</span></span></td>
</tr>
</table>

<span data-ttu-id="2f129-716"><sup>1</sup> DDS-Bilder mit BC1- bis BC5-Komprimierung werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2f129-716"><sup>1</sup> DDS images using BC1 through BC5 compression are supported.</span></span>  
<span data-ttu-id="2f129-717"><sup>2</sup> DNG-Bilder mit einer nicht als RAW eingebetteten Vorschau werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2f129-717"><sup>2</sup> DNG images with a non-RAW embedded preview are supported.</span></span>  
<span data-ttu-id="2f129-718"><sup>3</sup> Nur bestimmte Kamera-RAW-Formate werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2f129-718"><sup>3</sup> Only certain camera RAW formats are supported.</span></span>  

<span data-ttu-id="2f129-719">Weitere Informationen zu Bildcodecs finden Sie unter [Systemeigene WIC-Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span><span class="sxs-lookup"><span data-stu-id="2f129-719">For more information on image codecs, see [Native WIC Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span></span>