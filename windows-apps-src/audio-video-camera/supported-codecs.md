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
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7570057"
---
# <a name="supported-codecs"></a><span data-ttu-id="bc2c5-104">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="bc2c5-104">Supported codecs</span></span>

<span data-ttu-id="bc2c5-105">In diesem Artikel ist die Verfügbarkeit von Audio-, Video- und Bild-Codecs und -Formaten für UWP-Apps standardmäßig für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-105">This article lists the audio, video, and image codec and format availability for UWP apps by default for each device family.</span></span> <span data-ttu-id="bc2c5-106">Beachten Sie, dass diese Tabellen die Codecs enthalten, die in der Windows10-Installation für die angegebene Gerätefamilie enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-106">Note that these tables list the codecs that are included with the Windows 10 installation for the specified device family.</span></span> <span data-ttu-id="bc2c5-107">Benutzer und Apps können zusätzliche Codecs installieren, die unter Umständen zur Verwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-107">Users and apps can install additional codecs that may be available to use.</span></span> <span data-ttu-id="bc2c5-108">Sie können zur Laufzeit den Satz von Codecs abfragen, die derzeit für ein bestimmtes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-108">You can query at runtime for the set of codecs that are currently available for a specific device.</span></span> <span data-ttu-id="bc2c5-109">Weitere Informationen finden Sie unter [Abfragen von auf einem Gerät installierten Codecs](codec-query.md).</span><span class="sxs-lookup"><span data-stu-id="bc2c5-109">For more information, see [Query for codecs installed on a device](codec-query.md).</span></span>

<span data-ttu-id="bc2c5-110">In den folgenden Tabellen steht „D“ für Decoderunterstützung und „E“ für Encoderunterstützung.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-110">In the tables below "D" indicates decoder support and "E" indicates encoder support.</span></span>

## <a name="audio-codec--format-support"></a><span data-ttu-id="bc2c5-111">Unterstützung von Audiocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="bc2c5-111">Audio codec & format support</span></span>

<span data-ttu-id="bc2c5-112">In den folgenden Tabellen wird die Unterstützung von Audiocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-112">The following tables show the audio codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="bc2c5-113">Wo AMR-NB-Unterstützung angegeben ist, wird dieser Codec nicht auf Server-SKUs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-113">Where AMR-NB support is indicated, this codec is not supported on Server SKUs.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="bc2c5-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="bc2c5-114">Desktop</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-115">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-115">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-116">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-116">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-117">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-117">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-118">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-118">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-119">ADTS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-119">ADTS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-120">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-120">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-121">RIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-121">RIFF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-122">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-122">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-123">AC-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-123">AC-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-124">AMR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-124">AMR</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-125">3GP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-125">3GP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-126">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-126">FLAC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-127">WAV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-127">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-128">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-128">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-129">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-129">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-130">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-130">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-131">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-131">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-132">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-132">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-133">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-133">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-134">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-134">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-135">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-135">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-136">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-136">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-137">AC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-137">AC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-138">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-138">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-139">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-139">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-140">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-140">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-141">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-141">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-142">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-142">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-143">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-143">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-144">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-144">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-145">ALAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-145">ALAC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-146">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-146">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-147">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="bc2c5-147">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-148">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-148">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-149">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-149">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-150">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-150">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-151">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-151">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-152">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-152">D/E</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-153">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-153">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-154">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-154">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-155">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="bc2c5-155">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-156">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-156">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-157">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-157">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-158">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-158">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-159">LPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-159">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-160">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-160">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-161">MP3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-161">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-162">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-162">D/E</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-163">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-163">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-164">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-164">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-165">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-165">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-166">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-166">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-167">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-167">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-168">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-168">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-169">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="bc2c5-169">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-170">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-170">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-171">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="bc2c5-171">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-172">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-172">D/E</span></span></td>
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

 

### <a name="mobile"></a><span data-ttu-id="bc2c5-173">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="bc2c5-173">Mobile</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-174">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-174">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-175">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-175">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-176">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-176">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-177">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-177">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-178">ADTS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-178">ADTS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-179">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-179">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-180">RIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-180">RIFF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-181">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-181">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-182">AC-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-182">AC-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-183">AMR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-183">AMR</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-184">3GP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-184">3GP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-185">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-185">FLAC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-186">WAV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-186">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-187">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-187">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-188">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-188">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-189">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-189">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-190">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-190">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-191">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-191">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-192">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-192">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-193">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-193">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-194">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-194">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-195">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-195">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-196">AC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-196">AC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-197">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-197">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-198">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-198">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-199">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-199">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-200">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-200">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-201">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-201">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-202">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="bc2c5-202">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-203">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-203">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-204">ALAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-204">ALAC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-205">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-205">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-206">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="bc2c5-206">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-207">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-207">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-208">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-208">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-209">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-209">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-210">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-210">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-211">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-211">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-212">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-212">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-213">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-213">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-214">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="bc2c5-214">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-215">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-215">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-216">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-216">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-217">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-217">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-218">LPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-218">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-219">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-219">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-220">MP3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-220">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-221">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-221">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-222">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-222">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-223">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-223">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-224">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-224">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-225">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-225">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-226">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-226">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-227">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="bc2c5-227">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-228">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-228">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-229">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="bc2c5-229">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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

 

### <a name="iot-core-x86"></a><span data-ttu-id="bc2c5-230">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-230">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-231">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-231">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-232">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-232">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-233">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-233">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-234">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-234">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-235">ADTS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-235">ADTS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-236">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-236">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-237">RIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-237">RIFF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-238">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-238">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-239">AC-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-239">AC-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-240">AMR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-240">AMR</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-241">3GP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-241">3GP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-242">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-242">FLAC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-243">WAV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-243">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-244">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-244">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-245">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-245">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-246">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-246">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-247">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-247">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-248">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-248">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-249">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-249">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-250">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-250">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-251">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-251">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-252">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-252">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-253">AC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-253">AC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-254">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-254">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-255">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-255">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-256">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-256">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-257">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-257">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-258">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-258">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-259">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-259">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-260">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-260">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-261">ALAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-261">ALAC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-262">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-262">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-263">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="bc2c5-263">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-264">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-264">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-265">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-265">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-266">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-266">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-267">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-267">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-268">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-268">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-269">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-269">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-270">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-270">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-271">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="bc2c5-271">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-272">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-272">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-273">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-273">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-274">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-274">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-275">LPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-275">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-276">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-276">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-277">MP3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-277">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-278">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-278">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-279">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-279">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-280">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-280">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-281">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-281">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-282">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-282">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-283">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-283">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-284">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-284">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-285">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="bc2c5-285">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-286">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-286">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-287">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="bc2c5-287">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-288">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-288">D</span></span></td>
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

 

### <a name="iot-core-arm"></a><span data-ttu-id="bc2c5-289">IoT Core (ARM)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-289">IoT Core (ARM)</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-290">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-290">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-291">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-291">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-292">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-292">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-293">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-293">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-294">ADTS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-294">ADTS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-295">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-295">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-296">RIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-296">RIFF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-297">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-297">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-298">AC-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-298">AC-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-299">AMR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-299">AMR</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-300">3GP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-300">3GP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-301">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-301">FLAC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-302">WAV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-302">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-303">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-303">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-304">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-304">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-305">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-305">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-306">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-306">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-307">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-307">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-308">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-308">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-309">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-309">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-310">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-310">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-311">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-311">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-312">AC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-312">AC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-313">EAC3/EC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-313">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-314">ALAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-314">ALAC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-315">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-315">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-316">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="bc2c5-316">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-317">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-317">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-318">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-318">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-319">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-319">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-320">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-320">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-321">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-321">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-322">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-322">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-323">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-323">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-324">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="bc2c5-324">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-325">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-325">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-326">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-326">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-327">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-327">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-328">LPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-328">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-329">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-329">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-330">MP3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-330">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-331">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-331">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-332">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-332">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-333">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-333">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-334">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-334">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-335">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-335">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-336">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-336">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-337">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-337">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-338">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="bc2c5-338">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-339">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-339">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-340">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="bc2c5-340">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-341">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-341">D</span></span></td>
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

 

### <a name="xbox"></a><span data-ttu-id="bc2c5-342">XBox</span><span class="sxs-lookup"><span data-stu-id="bc2c5-342">XBox</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-343">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-343">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-344">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-344">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-345">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-345">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-346">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-346">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-347">ADTS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-347">ADTS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-348">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-348">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-349">RIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-349">RIFF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-350">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-350">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-351">AC-3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-351">AC-3</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-352">AMR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-352">AMR</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-353">3GP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-353">3GP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-354">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-354">FLAC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-355">WAV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-355">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-356">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-356">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-357">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-357">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-358">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-358">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-359">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="bc2c5-359">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-360">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-360">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-361">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-361">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-362">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-362">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-363">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-363">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-364">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-364">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-365">AC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-365">AC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-366">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-366">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-367">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-367">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-368">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-368">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-369">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-369">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-370">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-370">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-371">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-371">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-372">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-372">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-373">ALAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-373">ALAC</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-374">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-374">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-375">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="bc2c5-375">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-376">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-376">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-377">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-377">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-378">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-378">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-379">FLAC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-379">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-380">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-380">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-381">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-381">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-382">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-382">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-383">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="bc2c5-383">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-384">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-384">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-385">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-385">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-386">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-386">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-387">LPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-387">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-388">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-388">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-389">MP3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-389">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-390">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-390">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-391">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-391">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-392">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-392">D</span></span></td>
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
<td align="left"><span data-ttu-id="bc2c5-393">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="bc2c5-393">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-394">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-394">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-395">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="bc2c5-395">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-396">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-396">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-397">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="bc2c5-397">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-398">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-398">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-399">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="bc2c5-399">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-400">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-400">D</span></span></td>
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

 

## <a name="video-codec--format-support"></a><span data-ttu-id="bc2c5-401">Unterstützung von Videocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="bc2c5-401">Video codec & format support</span></span>

<span data-ttu-id="bc2c5-402">In den folgenden Tabellen wird die Unterstützung von Videocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-402">The following tables show the video codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="bc2c5-403">Wo H.265-Unterstützung angegeben ist, gilt diese nicht unbedingt für alle Geräten innerhalb der Gerätefamilie.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-403">Where H.265 support is indicated, it is not necessarily supported by all devices within the device family.</span></span>
> <span data-ttu-id="bc2c5-404">Wo MPEG-2/MPEG-1-Unterstützung angegeben ist, gilt diese nur mit der Installation der optionalen universellen Microsoft DVD-Windows-App.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-404">Where MPEG-2/MPEG-1 support is indicated, it is only supported with the installation of the optional Microsoft DVD Universal Windows app.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="bc2c5-405">Desktop</span><span class="sxs-lookup"><span data-stu-id="bc2c5-405">Desktop</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-406">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-406">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-407">FOURCC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-407">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-408">fMP4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-408">fMP4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-409">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-409">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-410">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-410">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-411">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-411">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-412">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-412">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-413">3GPP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-413">3GPP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-414">3GPP2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-414">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-415">AVCHD</span><span class="sxs-lookup"><span data-stu-id="bc2c5-415">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-416">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-416">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-417">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-417">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-418">MKV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-418">MKV</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-419">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-419">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-420">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-420">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-421">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-421">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-422">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-422">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-423">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-423">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-424">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-424">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-425">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-425">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-426">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-426">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-427">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-427">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-428">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-428">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-429">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-429">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-430">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-430">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-431">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-431">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-432">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-432">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-433">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-433">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-434">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-434">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-435">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-435">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-436">H.265</span><span class="sxs-lookup"><span data-stu-id="bc2c5-436">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-437">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-437">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-438">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-438">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-439">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-439">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-440">H.264</span><span class="sxs-lookup"><span data-stu-id="bc2c5-440">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-441">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-441">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-442">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-442">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-443">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-443">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-444">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-444">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-445">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-445">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-446">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-446">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-447">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-447">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-448">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-448">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-449">H.263</span><span class="sxs-lookup"><span data-stu-id="bc2c5-449">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-450">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-450">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-451">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-451">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-452">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-452">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-453">VC-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-453">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-454">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-454">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-455">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-455">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-456">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-456">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-457">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-457">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-458">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="bc2c5-458">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-459">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-459">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-460">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-460">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-461">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-461">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-462">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="bc2c5-462">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-463">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-463">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-464">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-464">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-465">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-465">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-466">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-466">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-467">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-467">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-468">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-468">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-469">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-469">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-470">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-470">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-471">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-471">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-472">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-472">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="bc2c5-473">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="bc2c5-473">Mobile</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-474">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-474">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-475">FOURCC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-475">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-476">fMP4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-476">fMP4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-477">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-477">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-478">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-478">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-479">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-479">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-480">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-480">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-481">3GPP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-481">3GPP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-482">3GPP2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-482">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-483">AVCHD</span><span class="sxs-lookup"><span data-stu-id="bc2c5-483">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-484">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-484">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-485">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-485">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-486">MKV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-486">MKV</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-487">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-487">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-488">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-488">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-489">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-489">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-490">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-490">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-491">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-491">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-492">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-492">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-493">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-493">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-494">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-494">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-495">H.265</span><span class="sxs-lookup"><span data-stu-id="bc2c5-495">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-496">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-496">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-497">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-497">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-498">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-498">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-499">H.264</span><span class="sxs-lookup"><span data-stu-id="bc2c5-499">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-500">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-500">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-501">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-501">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-502">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-502">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-503">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-503">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-504">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-504">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-505">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-505">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-506">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-506">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-507">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-507">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-508">H.263</span><span class="sxs-lookup"><span data-stu-id="bc2c5-508">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-509">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-509">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-510">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-510">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-511">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-511">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-512">VC-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-512">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-513">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-513">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-514">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-514">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-515">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-515">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-516">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="bc2c5-516">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-517">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="bc2c5-517">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-518">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-518">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-519">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-519">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-520">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-520">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-521">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-521">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="bc2c5-522">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-522">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-523">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-523">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-524">FOURCC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-524">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-525">fMP4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-525">fMP4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-526">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-526">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-527">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-527">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-528">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-528">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-529">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-529">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-530">3GPP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-530">3GPP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-531">3GPP2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-531">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-532">AVCHD</span><span class="sxs-lookup"><span data-stu-id="bc2c5-532">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-533">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-533">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-534">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-534">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-535">MKV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-535">MKV</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-536">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-536">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-537">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-537">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-538">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-538">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-539">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-539">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-540">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-540">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-541">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-541">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-542">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-542">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-543">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-543">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-544">H.265</span><span class="sxs-lookup"><span data-stu-id="bc2c5-544">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-545">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-545">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-546">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-546">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-547">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-547">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-548">H.264</span><span class="sxs-lookup"><span data-stu-id="bc2c5-548">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-549">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-549">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-550">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-550">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-551">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-551">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-552">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-552">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-553">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-553">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-554">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-554">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-555">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-555">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-556">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-556">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-557">H.263</span><span class="sxs-lookup"><span data-stu-id="bc2c5-557">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-558">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-558">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-559">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-559">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-560">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-560">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-561">VC-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-561">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-562">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-562">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-563">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-563">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-564">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-564">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-565">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-565">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-566">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="bc2c5-566">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-567">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-567">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-568">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-568">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-569">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-569">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-570">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="bc2c5-570">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-571">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-571">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-572">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-572">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-573">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-573">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-574">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-574">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-575">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-575">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-576">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-576">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-577">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-577">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-arm"></a><span data-ttu-id="bc2c5-578">IoT (ARM)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-578">IoT (ARM)</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-579">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-579">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-580">FOURCC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-580">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-581">fMP4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-581">fMP4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-582">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-582">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-583">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-583">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-584">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-584">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-585">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-585">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-586">3GPP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-586">3GPP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-587">3GPP2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-587">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-588">AVCHD</span><span class="sxs-lookup"><span data-stu-id="bc2c5-588">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-589">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-589">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-590">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-590">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-591">MKV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-591">MKV</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-592">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-592">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-593">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-593">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-594">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-594">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-595">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-595">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-596">H.265</span><span class="sxs-lookup"><span data-stu-id="bc2c5-596">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-597">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-597">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-598">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-598">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-599">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-599">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-600">H.264</span><span class="sxs-lookup"><span data-stu-id="bc2c5-600">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-601">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-601">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-602">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-602">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-603">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-603">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-604">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-604">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-605">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-605">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-606">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-606">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-607">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-607">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-608">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-608">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-609">H.263</span><span class="sxs-lookup"><span data-stu-id="bc2c5-609">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-610">VC-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-610">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-611">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-611">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-612">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-612">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-613">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-613">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-614">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-614">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-615">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="bc2c5-615">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-616">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-616">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-617">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-617">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-618">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-618">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-619">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="bc2c5-619">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-620">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-620">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-621">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-621">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-622">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-622">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-623">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-623">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="bc2c5-624">XBox</span><span class="sxs-lookup"><span data-stu-id="bc2c5-624">XBox</span></span>

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
<th align="left"><span data-ttu-id="bc2c5-625">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="bc2c5-625">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-626">FOURCC</span><span class="sxs-lookup"><span data-stu-id="bc2c5-626">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-627">fMP4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-627">fMP4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-628">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="bc2c5-628">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-629">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-629">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-630">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-630">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-631">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-631">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-632">3GPP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-632">3GPP</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-633">3GPP2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-633">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-634">AVCHD</span><span class="sxs-lookup"><span data-stu-id="bc2c5-634">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-635">ASF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-635">ASF</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-636">AVI</span><span class="sxs-lookup"><span data-stu-id="bc2c5-636">AVI</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-637">MKV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-637">MKV</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-638">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-638">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-639">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-639">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-640">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-640">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-641">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-641">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-642">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-642">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-643">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-643">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-644">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-644">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-645">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="bc2c5-645">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-646">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-646">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-647">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-647">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-648">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-648">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-649">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-649">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-650">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="bc2c5-650">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-651">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-651">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-652">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-652">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-653">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-653">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-654">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-654">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-655">H.265</span><span class="sxs-lookup"><span data-stu-id="bc2c5-655">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-656">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-656">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-657">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-657">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-658">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-658">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-659">H.264</span><span class="sxs-lookup"><span data-stu-id="bc2c5-659">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-660">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-660">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-661">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-661">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-662">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-662">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-663">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-663">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-664">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-664">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-665">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-665">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-666">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-666">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-667">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-667">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-668">H.263</span><span class="sxs-lookup"><span data-stu-id="bc2c5-668">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-669">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-669">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-670">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-670">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-671">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-671">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-672">VC-1</span><span class="sxs-lookup"><span data-stu-id="bc2c5-672">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-673">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-673">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-674">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-674">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-675">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-675">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-676">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="bc2c5-676">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-677">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="bc2c5-677">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-678">DV</span><span class="sxs-lookup"><span data-stu-id="bc2c5-678">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="bc2c5-679">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-679">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-680">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-680">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="bc2c5-681">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-681">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="image-codec--format-support"></a><span data-ttu-id="bc2c5-682">Unterstützung von Bildcodecs und -formaten</span><span class="sxs-lookup"><span data-stu-id="bc2c5-682">Image codec & format support</span></span> 

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bc2c5-683">Codec</span><span class="sxs-lookup"><span data-stu-id="bc2c5-683">Codec</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-684">Desktop</span><span class="sxs-lookup"><span data-stu-id="bc2c5-684">Desktop</span></span></th>
<th align="left"><span data-ttu-id="bc2c5-685">Andere Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="bc2c5-685">Other device families</span></span></th>
</tr>
</thead>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-686">BMP</span><span class="sxs-lookup"><span data-stu-id="bc2c5-686">BMP</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-687">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-687">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-688">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-688">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-689">DDS</span><span class="sxs-lookup"><span data-stu-id="bc2c5-689">DDS</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-690">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bc2c5-690">D/E<sup>1</sup></span></span></td>
<td align="left"><span data-ttu-id="bc2c5-691">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bc2c5-691">D/E<sup>1</sup></span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-692">DNG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-692">DNG</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-693">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bc2c5-693">D<sup>2</sup></span></span></td>
<td align="left"><span data-ttu-id="bc2c5-694">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bc2c5-694">D<sup>2</sup></span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-695">GIF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-695">GIF</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-696">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-696">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-697">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-697">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-698">ICO</span><span class="sxs-lookup"><span data-stu-id="bc2c5-698">ICO</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-699">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-699">D</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-700">D</span><span class="sxs-lookup"><span data-stu-id="bc2c5-700">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-701">JPEG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-701">JPEG</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-702">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-702">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-703">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-703">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-704">JPEG-XR</span><span class="sxs-lookup"><span data-stu-id="bc2c5-704">JPEG-XR</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-705">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-705">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-706">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-706">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-707">PNG</span><span class="sxs-lookup"><span data-stu-id="bc2c5-707">PNG</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-708">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-708">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-709">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-709">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="bc2c5-710">TIFF</span><span class="sxs-lookup"><span data-stu-id="bc2c5-710">TIFF</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-711">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-711">D/E</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-712">D/E</span><span class="sxs-lookup"><span data-stu-id="bc2c5-712">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="bc2c5-713">Kamera-RAW</span><span class="sxs-lookup"><span data-stu-id="bc2c5-713">Camera RAW</span></span></td>
<td align="left"><span data-ttu-id="bc2c5-714">D<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="bc2c5-714">D<sup>3</sup></span></span></td>
<td align="left"><span data-ttu-id="bc2c5-715">Nein</span><span class="sxs-lookup"><span data-stu-id="bc2c5-715">No</span></span></td>
</tr>
</table>

<span data-ttu-id="bc2c5-716"><sup>1</sup> DDS-Bilder mit BC1- bis BC5-Komprimierung werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-716"><sup>1</sup> DDS images using BC1 through BC5 compression are supported.</span></span>  
<span data-ttu-id="bc2c5-717"><sup>2</sup> DNG-Bilder mit einer nicht als RAW eingebetteten Vorschau werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-717"><sup>2</sup> DNG images with a non-RAW embedded preview are supported.</span></span>  
<span data-ttu-id="bc2c5-718"><sup>3</sup> Nur bestimmte Kamera-RAW-Formate werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bc2c5-718"><sup>3</sup> Only certain camera RAW formats are supported.</span></span>  

<span data-ttu-id="bc2c5-719">Weitere Informationen zu Bildcodecs finden Sie unter [Systemeigene WIC-Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span><span class="sxs-lookup"><span data-stu-id="bc2c5-719">For more information on image codecs, see [Native WIC Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span></span>