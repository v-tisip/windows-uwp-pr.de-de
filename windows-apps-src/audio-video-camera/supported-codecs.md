---
author: drewbatgit
ms.assetid: 9347AD7C-3A90-4073-BFF4-9E8237398343
description: In diesem Artikel wird aufgeführt, welche Audio- und Videocodecs und welche Formate für UWP-Apps unterstützt werden.
title: Unterstützte Codecs
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 50d520437f9be9d2e2bc6fe8243c3d34b17ef2d9
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "303680"
---
# <a name="supported-codecs"></a><span data-ttu-id="9371c-104">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="9371c-104">Supported codecs</span></span>

<span data-ttu-id="9371c-105">In diesem Artikel ist die Verfügbarkeit von Audio-, Video- und Bild-Codecs und -Formaten für UWP-Apps standardmäßig für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9371c-105">This article lists the audio, video, and image codec and format availability for UWP apps by default for each device family.</span></span> <span data-ttu-id="9371c-106">Beachten Sie, dass diese Tabellen die Codecs enthalten, die in der Windows10-Installation für die angegebene Gerätefamilie enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="9371c-106">Note that these tables list the codecs that are included with the Windows 10 installation for the specified device family.</span></span> <span data-ttu-id="9371c-107">Benutzer und Apps können zusätzliche Codecs installieren, die unter Umständen zur Verwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="9371c-107">Users and apps can install additional codecs that may be available to use.</span></span> <span data-ttu-id="9371c-108">Sie können zur Laufzeit den Satz von Codecs abfragen, die derzeit für ein bestimmtes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="9371c-108">You can query at runtime for the set of codecs that are currently available for a specific device.</span></span> <span data-ttu-id="9371c-109">Weitere Informationen finden Sie unter [Abfragen von auf einem Gerät installierten Codecs](codec-query.md).</span><span class="sxs-lookup"><span data-stu-id="9371c-109">For more information, see [Query for codecs installed on a device](codec-query.md).</span></span>

<span data-ttu-id="9371c-110">In den folgenden Tabellen steht „D“ für Decoderunterstützung und „E“ für Encoderunterstützung.</span><span class="sxs-lookup"><span data-stu-id="9371c-110">In the tables below "D" indicates decoder support and "E" indicates encoder support.</span></span>

## <a name="audio-codec--format-support"></a><span data-ttu-id="9371c-111">Unterstützung von Audiocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="9371c-111">Audio codec & format support</span></span>

<span data-ttu-id="9371c-112">In den folgenden Tabellen wird die Unterstützung von Audiocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9371c-112">The following tables show the audio codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="9371c-113">Wo AMR-NB-Unterstützung angegeben ist, wird dieser Codec nicht auf Server-SKUs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9371c-113">Where AMR-NB support is indicated, this codec is not supported on Server SKUs.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="9371c-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="9371c-114">Desktop</span></span>

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
<th align="left"><span data-ttu-id="9371c-115">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-115">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-116">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-116">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-117">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="9371c-117">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-118">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-118">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="9371c-119">ADTS</span><span class="sxs-lookup"><span data-stu-id="9371c-119">ADTS</span></span></th>
<th align="left"><span data-ttu-id="9371c-120">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-120">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-121">RIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-121">RIFF</span></span></th>
<th align="left"><span data-ttu-id="9371c-122">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-122">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-123">AC-3</span><span class="sxs-lookup"><span data-stu-id="9371c-123">AC-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-124">AMR</span><span class="sxs-lookup"><span data-stu-id="9371c-124">AMR</span></span></th>
<th align="left"><span data-ttu-id="9371c-125">3GP</span><span class="sxs-lookup"><span data-stu-id="9371c-125">3GP</span></span></th>
<th align="left"><span data-ttu-id="9371c-126">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-126">FLAC</span></span></th>
<th align="left"><span data-ttu-id="9371c-127">WAV</span><span class="sxs-lookup"><span data-stu-id="9371c-127">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-128">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-128">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-129">D</span><span class="sxs-lookup"><span data-stu-id="9371c-129">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-130">D</span><span class="sxs-lookup"><span data-stu-id="9371c-130">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-131">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-131">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-132">D</span><span class="sxs-lookup"><span data-stu-id="9371c-132">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-133">D</span><span class="sxs-lookup"><span data-stu-id="9371c-133">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-134">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="9371c-134">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="9371c-135">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-135">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-136">D</span><span class="sxs-lookup"><span data-stu-id="9371c-136">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-137">AC3</span><span class="sxs-lookup"><span data-stu-id="9371c-137">AC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-138">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-138">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-139">D</span><span class="sxs-lookup"><span data-stu-id="9371c-139">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-140">D</span><span class="sxs-lookup"><span data-stu-id="9371c-140">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-141">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="9371c-141">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-142">D</span><span class="sxs-lookup"><span data-stu-id="9371c-142">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-143">D</span><span class="sxs-lookup"><span data-stu-id="9371c-143">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-144">D</span><span class="sxs-lookup"><span data-stu-id="9371c-144">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-145">ALAC</span><span class="sxs-lookup"><span data-stu-id="9371c-145">ALAC</span></span></td>
<td align="left"><span data-ttu-id="9371c-146">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-146">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-147">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="9371c-147">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="9371c-148">D</span><span class="sxs-lookup"><span data-stu-id="9371c-148">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-149">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-149">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-150">D</span><span class="sxs-lookup"><span data-stu-id="9371c-150">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-151">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-151">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-152">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-152">D/E</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-153">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="9371c-153">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-154">D</span><span class="sxs-lookup"><span data-stu-id="9371c-154">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-155">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="9371c-155">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-156">D</span><span class="sxs-lookup"><span data-stu-id="9371c-156">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-157">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-157">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-158">D</span><span class="sxs-lookup"><span data-stu-id="9371c-158">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-159">LPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-159">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-160">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-160">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-161">MP3</span><span class="sxs-lookup"><span data-stu-id="9371c-161">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-162">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-162">D/E</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-163">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="9371c-163">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-164">D</span><span class="sxs-lookup"><span data-stu-id="9371c-164">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-165">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-165">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-166">D</span><span class="sxs-lookup"><span data-stu-id="9371c-166">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-167">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="9371c-167">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-168">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-168">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-169">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="9371c-169">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-170">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-170">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-171">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="9371c-171">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-172">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-172">D/E</span></span></td>
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

 

### <a name="mobile"></a><span data-ttu-id="9371c-173">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="9371c-173">Mobile</span></span>

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
<th align="left"><span data-ttu-id="9371c-174">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-174">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-175">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-175">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-176">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="9371c-176">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-177">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-177">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="9371c-178">ADTS</span><span class="sxs-lookup"><span data-stu-id="9371c-178">ADTS</span></span></th>
<th align="left"><span data-ttu-id="9371c-179">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-179">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-180">RIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-180">RIFF</span></span></th>
<th align="left"><span data-ttu-id="9371c-181">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-181">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-182">AC-3</span><span class="sxs-lookup"><span data-stu-id="9371c-182">AC-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-183">AMR</span><span class="sxs-lookup"><span data-stu-id="9371c-183">AMR</span></span></th>
<th align="left"><span data-ttu-id="9371c-184">3GP</span><span class="sxs-lookup"><span data-stu-id="9371c-184">3GP</span></span></th>
<th align="left"><span data-ttu-id="9371c-185">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-185">FLAC</span></span></th>
<th align="left"><span data-ttu-id="9371c-186">WAV</span><span class="sxs-lookup"><span data-stu-id="9371c-186">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-187">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-187">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-188">D</span><span class="sxs-lookup"><span data-stu-id="9371c-188">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-189">D</span><span class="sxs-lookup"><span data-stu-id="9371c-189">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-190">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-190">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-191">D</span><span class="sxs-lookup"><span data-stu-id="9371c-191">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-192">D</span><span class="sxs-lookup"><span data-stu-id="9371c-192">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-193">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="9371c-193">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="9371c-194">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-194">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-195">D</span><span class="sxs-lookup"><span data-stu-id="9371c-195">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-196">AC3</span><span class="sxs-lookup"><span data-stu-id="9371c-196">AC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-197">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-197">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-198">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-198">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-199">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-199">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="9371c-200">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-200">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="9371c-201">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-201">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="9371c-202">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="9371c-202">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-203">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="9371c-203">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-204">ALAC</span><span class="sxs-lookup"><span data-stu-id="9371c-204">ALAC</span></span></td>
<td align="left"><span data-ttu-id="9371c-205">D</span><span class="sxs-lookup"><span data-stu-id="9371c-205">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-206">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="9371c-206">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="9371c-207">D</span><span class="sxs-lookup"><span data-stu-id="9371c-207">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-208">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-208">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-209">D</span><span class="sxs-lookup"><span data-stu-id="9371c-209">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-210">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-210">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-211">D</span><span class="sxs-lookup"><span data-stu-id="9371c-211">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-212">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="9371c-212">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-213">D</span><span class="sxs-lookup"><span data-stu-id="9371c-213">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-214">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="9371c-214">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-215">D</span><span class="sxs-lookup"><span data-stu-id="9371c-215">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-216">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-216">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-217">D</span><span class="sxs-lookup"><span data-stu-id="9371c-217">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-218">LPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-218">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-219">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-219">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-220">MP3</span><span class="sxs-lookup"><span data-stu-id="9371c-220">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-221">D</span><span class="sxs-lookup"><span data-stu-id="9371c-221">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-222">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="9371c-222">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-223">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-223">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-224">D</span><span class="sxs-lookup"><span data-stu-id="9371c-224">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-225">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="9371c-225">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-226">D</span><span class="sxs-lookup"><span data-stu-id="9371c-226">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-227">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="9371c-227">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-228">D</span><span class="sxs-lookup"><span data-stu-id="9371c-228">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-229">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="9371c-229">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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

 

### <a name="iot-core-x86"></a><span data-ttu-id="9371c-230">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="9371c-230">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="9371c-231">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-231">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-232">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-232">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-233">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="9371c-233">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-234">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-234">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="9371c-235">ADTS</span><span class="sxs-lookup"><span data-stu-id="9371c-235">ADTS</span></span></th>
<th align="left"><span data-ttu-id="9371c-236">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-236">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-237">RIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-237">RIFF</span></span></th>
<th align="left"><span data-ttu-id="9371c-238">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-238">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-239">AC-3</span><span class="sxs-lookup"><span data-stu-id="9371c-239">AC-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-240">AMR</span><span class="sxs-lookup"><span data-stu-id="9371c-240">AMR</span></span></th>
<th align="left"><span data-ttu-id="9371c-241">3GP</span><span class="sxs-lookup"><span data-stu-id="9371c-241">3GP</span></span></th>
<th align="left"><span data-ttu-id="9371c-242">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-242">FLAC</span></span></th>
<th align="left"><span data-ttu-id="9371c-243">WAV</span><span class="sxs-lookup"><span data-stu-id="9371c-243">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-244">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-244">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-245">D</span><span class="sxs-lookup"><span data-stu-id="9371c-245">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-246">D</span><span class="sxs-lookup"><span data-stu-id="9371c-246">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-247">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-247">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-248">D</span><span class="sxs-lookup"><span data-stu-id="9371c-248">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-249">D</span><span class="sxs-lookup"><span data-stu-id="9371c-249">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-250">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="9371c-250">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="9371c-251">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-251">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-252">D</span><span class="sxs-lookup"><span data-stu-id="9371c-252">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-253">AC3</span><span class="sxs-lookup"><span data-stu-id="9371c-253">AC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-254">D</span><span class="sxs-lookup"><span data-stu-id="9371c-254">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-255">D</span><span class="sxs-lookup"><span data-stu-id="9371c-255">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-256">D</span><span class="sxs-lookup"><span data-stu-id="9371c-256">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-257">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="9371c-257">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-258">D</span><span class="sxs-lookup"><span data-stu-id="9371c-258">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-259">D</span><span class="sxs-lookup"><span data-stu-id="9371c-259">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-260">D</span><span class="sxs-lookup"><span data-stu-id="9371c-260">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-261">ALAC</span><span class="sxs-lookup"><span data-stu-id="9371c-261">ALAC</span></span></td>
<td align="left"><span data-ttu-id="9371c-262">D</span><span class="sxs-lookup"><span data-stu-id="9371c-262">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-263">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="9371c-263">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="9371c-264">D</span><span class="sxs-lookup"><span data-stu-id="9371c-264">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-265">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-265">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-266">D</span><span class="sxs-lookup"><span data-stu-id="9371c-266">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-267">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-267">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-268">D</span><span class="sxs-lookup"><span data-stu-id="9371c-268">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-269">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="9371c-269">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-270">D</span><span class="sxs-lookup"><span data-stu-id="9371c-270">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-271">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="9371c-271">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-272">D</span><span class="sxs-lookup"><span data-stu-id="9371c-272">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-273">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-273">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-274">D</span><span class="sxs-lookup"><span data-stu-id="9371c-274">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-275">LPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-275">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-276">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-276">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-277">MP3</span><span class="sxs-lookup"><span data-stu-id="9371c-277">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-278">D</span><span class="sxs-lookup"><span data-stu-id="9371c-278">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-279">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="9371c-279">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-280">D</span><span class="sxs-lookup"><span data-stu-id="9371c-280">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-281">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-281">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-282">D</span><span class="sxs-lookup"><span data-stu-id="9371c-282">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-283">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="9371c-283">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-284">D</span><span class="sxs-lookup"><span data-stu-id="9371c-284">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-285">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="9371c-285">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-286">D</span><span class="sxs-lookup"><span data-stu-id="9371c-286">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-287">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="9371c-287">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-288">D</span><span class="sxs-lookup"><span data-stu-id="9371c-288">D</span></span></td>
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

 

### <a name="iot-core-arm"></a><span data-ttu-id="9371c-289">IoT Core (ARM)</span><span class="sxs-lookup"><span data-stu-id="9371c-289">IoT Core (ARM)</span></span>

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
<th align="left"><span data-ttu-id="9371c-290">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-290">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-291">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-291">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-292">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="9371c-292">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-293">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-293">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="9371c-294">ADTS</span><span class="sxs-lookup"><span data-stu-id="9371c-294">ADTS</span></span></th>
<th align="left"><span data-ttu-id="9371c-295">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-295">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-296">RIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-296">RIFF</span></span></th>
<th align="left"><span data-ttu-id="9371c-297">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-297">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-298">AC-3</span><span class="sxs-lookup"><span data-stu-id="9371c-298">AC-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-299">AMR</span><span class="sxs-lookup"><span data-stu-id="9371c-299">AMR</span></span></th>
<th align="left"><span data-ttu-id="9371c-300">3GP</span><span class="sxs-lookup"><span data-stu-id="9371c-300">3GP</span></span></th>
<th align="left"><span data-ttu-id="9371c-301">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-301">FLAC</span></span></th>
<th align="left"><span data-ttu-id="9371c-302">WAV</span><span class="sxs-lookup"><span data-stu-id="9371c-302">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-303">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-303">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-304">D</span><span class="sxs-lookup"><span data-stu-id="9371c-304">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-305">D</span><span class="sxs-lookup"><span data-stu-id="9371c-305">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-306">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-306">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-307">D</span><span class="sxs-lookup"><span data-stu-id="9371c-307">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-308">D</span><span class="sxs-lookup"><span data-stu-id="9371c-308">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-309">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="9371c-309">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="9371c-310">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-310">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-311">D</span><span class="sxs-lookup"><span data-stu-id="9371c-311">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-312">AC3</span><span class="sxs-lookup"><span data-stu-id="9371c-312">AC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-313">EAC3/EC3</span><span class="sxs-lookup"><span data-stu-id="9371c-313">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-314">ALAC</span><span class="sxs-lookup"><span data-stu-id="9371c-314">ALAC</span></span></td>
<td align="left"><span data-ttu-id="9371c-315">D</span><span class="sxs-lookup"><span data-stu-id="9371c-315">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-316">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="9371c-316">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="9371c-317">D</span><span class="sxs-lookup"><span data-stu-id="9371c-317">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-318">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-318">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-319">D</span><span class="sxs-lookup"><span data-stu-id="9371c-319">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-320">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-320">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-321">D</span><span class="sxs-lookup"><span data-stu-id="9371c-321">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-322">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="9371c-322">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-323">D</span><span class="sxs-lookup"><span data-stu-id="9371c-323">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-324">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="9371c-324">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-325">D</span><span class="sxs-lookup"><span data-stu-id="9371c-325">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-326">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-326">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-327">D</span><span class="sxs-lookup"><span data-stu-id="9371c-327">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-328">LPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-328">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-329">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-329">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-330">MP3</span><span class="sxs-lookup"><span data-stu-id="9371c-330">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-331">D</span><span class="sxs-lookup"><span data-stu-id="9371c-331">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-332">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="9371c-332">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-333">D</span><span class="sxs-lookup"><span data-stu-id="9371c-333">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-334">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-334">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-335">D</span><span class="sxs-lookup"><span data-stu-id="9371c-335">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-336">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="9371c-336">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-337">D</span><span class="sxs-lookup"><span data-stu-id="9371c-337">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-338">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="9371c-338">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-339">D</span><span class="sxs-lookup"><span data-stu-id="9371c-339">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-340">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="9371c-340">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-341">D</span><span class="sxs-lookup"><span data-stu-id="9371c-341">D</span></span></td>
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

 

### <a name="xbox"></a><span data-ttu-id="9371c-342">XBox</span><span class="sxs-lookup"><span data-stu-id="9371c-342">XBox</span></span>

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
<th align="left"><span data-ttu-id="9371c-343">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-343">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-344">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-344">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-345">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="9371c-345">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-346">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-346">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="9371c-347">ADTS</span><span class="sxs-lookup"><span data-stu-id="9371c-347">ADTS</span></span></th>
<th align="left"><span data-ttu-id="9371c-348">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-348">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-349">RIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-349">RIFF</span></span></th>
<th align="left"><span data-ttu-id="9371c-350">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-350">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-351">AC-3</span><span class="sxs-lookup"><span data-stu-id="9371c-351">AC-3</span></span></th>
<th align="left"><span data-ttu-id="9371c-352">AMR</span><span class="sxs-lookup"><span data-stu-id="9371c-352">AMR</span></span></th>
<th align="left"><span data-ttu-id="9371c-353">3GP</span><span class="sxs-lookup"><span data-stu-id="9371c-353">3GP</span></span></th>
<th align="left"><span data-ttu-id="9371c-354">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-354">FLAC</span></span></th>
<th align="left"><span data-ttu-id="9371c-355">WAV</span><span class="sxs-lookup"><span data-stu-id="9371c-355">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-356">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-356">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-357">D</span><span class="sxs-lookup"><span data-stu-id="9371c-357">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-358">D</span><span class="sxs-lookup"><span data-stu-id="9371c-358">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-359">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="9371c-359">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="9371c-360">D</span><span class="sxs-lookup"><span data-stu-id="9371c-360">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-361">D</span><span class="sxs-lookup"><span data-stu-id="9371c-361">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-362">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="9371c-362">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="9371c-363">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-363">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-364">D</span><span class="sxs-lookup"><span data-stu-id="9371c-364">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-365">AC3</span><span class="sxs-lookup"><span data-stu-id="9371c-365">AC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-366">D</span><span class="sxs-lookup"><span data-stu-id="9371c-366">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-367">D</span><span class="sxs-lookup"><span data-stu-id="9371c-367">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-368">D</span><span class="sxs-lookup"><span data-stu-id="9371c-368">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-369">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="9371c-369">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="9371c-370">D</span><span class="sxs-lookup"><span data-stu-id="9371c-370">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-371">D</span><span class="sxs-lookup"><span data-stu-id="9371c-371">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-372">D</span><span class="sxs-lookup"><span data-stu-id="9371c-372">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-373">ALAC</span><span class="sxs-lookup"><span data-stu-id="9371c-373">ALAC</span></span></td>
<td align="left"><span data-ttu-id="9371c-374">D</span><span class="sxs-lookup"><span data-stu-id="9371c-374">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-375">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="9371c-375">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="9371c-376">D</span><span class="sxs-lookup"><span data-stu-id="9371c-376">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-377">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-377">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-378">D</span><span class="sxs-lookup"><span data-stu-id="9371c-378">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-379">FLAC</span><span class="sxs-lookup"><span data-stu-id="9371c-379">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-380">D</span><span class="sxs-lookup"><span data-stu-id="9371c-380">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-381">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="9371c-381">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-382">D</span><span class="sxs-lookup"><span data-stu-id="9371c-382">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-383">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="9371c-383">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-384">D</span><span class="sxs-lookup"><span data-stu-id="9371c-384">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-385">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-385">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-386">D</span><span class="sxs-lookup"><span data-stu-id="9371c-386">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-387">LPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-387">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-388">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-388">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-389">MP3</span><span class="sxs-lookup"><span data-stu-id="9371c-389">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-390">D</span><span class="sxs-lookup"><span data-stu-id="9371c-390">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-391">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="9371c-391">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-392">D</span><span class="sxs-lookup"><span data-stu-id="9371c-392">D</span></span></td>
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
<td align="left"><span data-ttu-id="9371c-393">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="9371c-393">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-394">D</span><span class="sxs-lookup"><span data-stu-id="9371c-394">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-395">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="9371c-395">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-396">D</span><span class="sxs-lookup"><span data-stu-id="9371c-396">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-397">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="9371c-397">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-398">D</span><span class="sxs-lookup"><span data-stu-id="9371c-398">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-399">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="9371c-399">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-400">D</span><span class="sxs-lookup"><span data-stu-id="9371c-400">D</span></span></td>
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

 

## <a name="video-codec--format-support"></a><span data-ttu-id="9371c-401">Unterstützung von Videocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="9371c-401">Video codec & format support</span></span>

<span data-ttu-id="9371c-402">In den folgenden Tabellen wird die Unterstützung von Videocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9371c-402">The following tables show the video codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="9371c-403">Wo H.265-Unterstützung angegeben ist, gilt diese nicht unbedingt für alle Geräten innerhalb der Gerätefamilie.</span><span class="sxs-lookup"><span data-stu-id="9371c-403">Where H.265 support is indicated, it is not necessarily supported by all devices within the device family.</span></span>
> <span data-ttu-id="9371c-404">Wo MPEG-2/MPEG-1-Unterstützung angegeben ist, gilt diese nur mit der Installation der optionalen universellen Microsoft DVD-Windows-App.</span><span class="sxs-lookup"><span data-stu-id="9371c-404">Where MPEG-2/MPEG-1 support is indicated, it is only supported with the installation of the optional Microsoft DVD Universal Windows app.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="9371c-405">Desktop</span><span class="sxs-lookup"><span data-stu-id="9371c-405">Desktop</span></span>

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
<th align="left"><span data-ttu-id="9371c-406">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-406">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-407">FOURCC</span><span class="sxs-lookup"><span data-stu-id="9371c-407">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="9371c-408">fMP4</span><span class="sxs-lookup"><span data-stu-id="9371c-408">fMP4</span></span></th>
<th align="left"><span data-ttu-id="9371c-409">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-409">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-410">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="9371c-410">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="9371c-411">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="9371c-411">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="9371c-412">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-412">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="9371c-413">3GPP</span><span class="sxs-lookup"><span data-stu-id="9371c-413">3GPP</span></span></th>
<th align="left"><span data-ttu-id="9371c-414">3GPP2</span><span class="sxs-lookup"><span data-stu-id="9371c-414">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="9371c-415">AVCHD</span><span class="sxs-lookup"><span data-stu-id="9371c-415">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="9371c-416">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-416">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-417">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-417">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-418">MKV</span><span class="sxs-lookup"><span data-stu-id="9371c-418">MKV</span></span></th>
<th align="left"><span data-ttu-id="9371c-419">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-419">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-420">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-420">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-421">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-421">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-422">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-422">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-423">D</span><span class="sxs-lookup"><span data-stu-id="9371c-423">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-424">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-424">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-425">D</span><span class="sxs-lookup"><span data-stu-id="9371c-425">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-426">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-426">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-427">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-427">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-428">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-428">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-429">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-429">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-430">D</span><span class="sxs-lookup"><span data-stu-id="9371c-430">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-431">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="9371c-431">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-432">D</span><span class="sxs-lookup"><span data-stu-id="9371c-432">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-433">D</span><span class="sxs-lookup"><span data-stu-id="9371c-433">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-434">D</span><span class="sxs-lookup"><span data-stu-id="9371c-434">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-435">D</span><span class="sxs-lookup"><span data-stu-id="9371c-435">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-436">H.265</span><span class="sxs-lookup"><span data-stu-id="9371c-436">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-437">D</span><span class="sxs-lookup"><span data-stu-id="9371c-437">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-438">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-438">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-439">D</span><span class="sxs-lookup"><span data-stu-id="9371c-439">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-440">H.264</span><span class="sxs-lookup"><span data-stu-id="9371c-440">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-441">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-441">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-442">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-442">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-443">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-443">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-444">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-444">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-445">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-445">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-446">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-446">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-447">D</span><span class="sxs-lookup"><span data-stu-id="9371c-447">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-448">D</span><span class="sxs-lookup"><span data-stu-id="9371c-448">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-449">H.263</span><span class="sxs-lookup"><span data-stu-id="9371c-449">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-450">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-450">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-451">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-451">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-452">D</span><span class="sxs-lookup"><span data-stu-id="9371c-452">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-453">VC-1</span><span class="sxs-lookup"><span data-stu-id="9371c-453">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-454">D</span><span class="sxs-lookup"><span data-stu-id="9371c-454">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-455">D</span><span class="sxs-lookup"><span data-stu-id="9371c-455">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-456">D</span><span class="sxs-lookup"><span data-stu-id="9371c-456">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-457">D</span><span class="sxs-lookup"><span data-stu-id="9371c-457">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-458">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="9371c-458">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-459">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-459">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-460">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-460">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-461">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-461">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-462">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="9371c-462">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-463">D</span><span class="sxs-lookup"><span data-stu-id="9371c-463">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-464">D</span><span class="sxs-lookup"><span data-stu-id="9371c-464">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-465">D</span><span class="sxs-lookup"><span data-stu-id="9371c-465">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-466">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-466">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-467">D</span><span class="sxs-lookup"><span data-stu-id="9371c-467">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-468">D</span><span class="sxs-lookup"><span data-stu-id="9371c-468">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-469">D</span><span class="sxs-lookup"><span data-stu-id="9371c-469">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-470">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-470">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-471">D</span><span class="sxs-lookup"><span data-stu-id="9371c-471">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-472">D</span><span class="sxs-lookup"><span data-stu-id="9371c-472">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="9371c-473">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="9371c-473">Mobile</span></span>

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
<th align="left"><span data-ttu-id="9371c-474">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-474">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-475">FOURCC</span><span class="sxs-lookup"><span data-stu-id="9371c-475">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="9371c-476">fMP4</span><span class="sxs-lookup"><span data-stu-id="9371c-476">fMP4</span></span></th>
<th align="left"><span data-ttu-id="9371c-477">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-477">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-478">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="9371c-478">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="9371c-479">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="9371c-479">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="9371c-480">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-480">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="9371c-481">3GPP</span><span class="sxs-lookup"><span data-stu-id="9371c-481">3GPP</span></span></th>
<th align="left"><span data-ttu-id="9371c-482">3GPP2</span><span class="sxs-lookup"><span data-stu-id="9371c-482">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="9371c-483">AVCHD</span><span class="sxs-lookup"><span data-stu-id="9371c-483">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="9371c-484">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-484">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-485">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-485">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-486">MKV</span><span class="sxs-lookup"><span data-stu-id="9371c-486">MKV</span></span></th>
<th align="left"><span data-ttu-id="9371c-487">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-487">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-488">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-488">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-489">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-489">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-490">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="9371c-490">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-491">D</span><span class="sxs-lookup"><span data-stu-id="9371c-491">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-492">D</span><span class="sxs-lookup"><span data-stu-id="9371c-492">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-493">D</span><span class="sxs-lookup"><span data-stu-id="9371c-493">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-494">D</span><span class="sxs-lookup"><span data-stu-id="9371c-494">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-495">H.265</span><span class="sxs-lookup"><span data-stu-id="9371c-495">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-496">D</span><span class="sxs-lookup"><span data-stu-id="9371c-496">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-497">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-497">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-498">D</span><span class="sxs-lookup"><span data-stu-id="9371c-498">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-499">H.264</span><span class="sxs-lookup"><span data-stu-id="9371c-499">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-500">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-500">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-501">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-501">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-502">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-502">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-503">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-503">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-504">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-504">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-505">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-505">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-506">D</span><span class="sxs-lookup"><span data-stu-id="9371c-506">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-507">D</span><span class="sxs-lookup"><span data-stu-id="9371c-507">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-508">H.263</span><span class="sxs-lookup"><span data-stu-id="9371c-508">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-509">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-509">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-510">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-510">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-511">D</span><span class="sxs-lookup"><span data-stu-id="9371c-511">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-512">VC-1</span><span class="sxs-lookup"><span data-stu-id="9371c-512">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-513">D</span><span class="sxs-lookup"><span data-stu-id="9371c-513">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-514">D</span><span class="sxs-lookup"><span data-stu-id="9371c-514">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-515">D</span><span class="sxs-lookup"><span data-stu-id="9371c-515">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-516">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="9371c-516">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-517">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="9371c-517">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-518">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-518">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-519">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-519">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-520">D</span><span class="sxs-lookup"><span data-stu-id="9371c-520">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-521">D</span><span class="sxs-lookup"><span data-stu-id="9371c-521">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="9371c-522">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="9371c-522">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="9371c-523">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-523">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-524">FOURCC</span><span class="sxs-lookup"><span data-stu-id="9371c-524">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="9371c-525">fMP4</span><span class="sxs-lookup"><span data-stu-id="9371c-525">fMP4</span></span></th>
<th align="left"><span data-ttu-id="9371c-526">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-526">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-527">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="9371c-527">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="9371c-528">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="9371c-528">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="9371c-529">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-529">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="9371c-530">3GPP</span><span class="sxs-lookup"><span data-stu-id="9371c-530">3GPP</span></span></th>
<th align="left"><span data-ttu-id="9371c-531">3GPP2</span><span class="sxs-lookup"><span data-stu-id="9371c-531">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="9371c-532">AVCHD</span><span class="sxs-lookup"><span data-stu-id="9371c-532">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="9371c-533">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-533">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-534">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-534">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-535">MKV</span><span class="sxs-lookup"><span data-stu-id="9371c-535">MKV</span></span></th>
<th align="left"><span data-ttu-id="9371c-536">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-536">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-537">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-537">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-538">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-538">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-539">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="9371c-539">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-540">D</span><span class="sxs-lookup"><span data-stu-id="9371c-540">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-541">D</span><span class="sxs-lookup"><span data-stu-id="9371c-541">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-542">D</span><span class="sxs-lookup"><span data-stu-id="9371c-542">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-543">D</span><span class="sxs-lookup"><span data-stu-id="9371c-543">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-544">H.265</span><span class="sxs-lookup"><span data-stu-id="9371c-544">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-545">D</span><span class="sxs-lookup"><span data-stu-id="9371c-545">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-546">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-546">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-547">D</span><span class="sxs-lookup"><span data-stu-id="9371c-547">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-548">H.264</span><span class="sxs-lookup"><span data-stu-id="9371c-548">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-549">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-549">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-550">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-550">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-551">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-551">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-552">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-552">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-553">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-553">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-554">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-554">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-555">D</span><span class="sxs-lookup"><span data-stu-id="9371c-555">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-556">D</span><span class="sxs-lookup"><span data-stu-id="9371c-556">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-557">H.263</span><span class="sxs-lookup"><span data-stu-id="9371c-557">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-558">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-558">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-559">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-559">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-560">D</span><span class="sxs-lookup"><span data-stu-id="9371c-560">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-561">VC-1</span><span class="sxs-lookup"><span data-stu-id="9371c-561">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-562">D</span><span class="sxs-lookup"><span data-stu-id="9371c-562">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-563">D</span><span class="sxs-lookup"><span data-stu-id="9371c-563">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-564">D</span><span class="sxs-lookup"><span data-stu-id="9371c-564">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-565">D</span><span class="sxs-lookup"><span data-stu-id="9371c-565">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-566">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="9371c-566">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-567">D</span><span class="sxs-lookup"><span data-stu-id="9371c-567">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-568">D</span><span class="sxs-lookup"><span data-stu-id="9371c-568">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-569">D</span><span class="sxs-lookup"><span data-stu-id="9371c-569">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-570">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="9371c-570">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-571">D</span><span class="sxs-lookup"><span data-stu-id="9371c-571">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-572">D</span><span class="sxs-lookup"><span data-stu-id="9371c-572">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-573">D</span><span class="sxs-lookup"><span data-stu-id="9371c-573">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-574">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-574">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-575">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-575">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-576">D</span><span class="sxs-lookup"><span data-stu-id="9371c-576">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-577">D</span><span class="sxs-lookup"><span data-stu-id="9371c-577">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-arm"></a><span data-ttu-id="9371c-578">IoT (ARM)</span><span class="sxs-lookup"><span data-stu-id="9371c-578">IoT (ARM)</span></span>

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
<th align="left"><span data-ttu-id="9371c-579">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-579">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-580">FOURCC</span><span class="sxs-lookup"><span data-stu-id="9371c-580">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="9371c-581">fMP4</span><span class="sxs-lookup"><span data-stu-id="9371c-581">fMP4</span></span></th>
<th align="left"><span data-ttu-id="9371c-582">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-582">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-583">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="9371c-583">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="9371c-584">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="9371c-584">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="9371c-585">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-585">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="9371c-586">3GPP</span><span class="sxs-lookup"><span data-stu-id="9371c-586">3GPP</span></span></th>
<th align="left"><span data-ttu-id="9371c-587">3GPP2</span><span class="sxs-lookup"><span data-stu-id="9371c-587">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="9371c-588">AVCHD</span><span class="sxs-lookup"><span data-stu-id="9371c-588">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="9371c-589">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-589">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-590">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-590">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-591">MKV</span><span class="sxs-lookup"><span data-stu-id="9371c-591">MKV</span></span></th>
<th align="left"><span data-ttu-id="9371c-592">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-592">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-593">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-593">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-594">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-594">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-595">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="9371c-595">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-596">H.265</span><span class="sxs-lookup"><span data-stu-id="9371c-596">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-597">D</span><span class="sxs-lookup"><span data-stu-id="9371c-597">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-598">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-598">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-599">D</span><span class="sxs-lookup"><span data-stu-id="9371c-599">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-600">H.264</span><span class="sxs-lookup"><span data-stu-id="9371c-600">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-601">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-601">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-602">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-602">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-603">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-603">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-604">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-604">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-605">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-605">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-606">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-606">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-607">D</span><span class="sxs-lookup"><span data-stu-id="9371c-607">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-608">D</span><span class="sxs-lookup"><span data-stu-id="9371c-608">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-609">H.263</span><span class="sxs-lookup"><span data-stu-id="9371c-609">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-610">VC-1</span><span class="sxs-lookup"><span data-stu-id="9371c-610">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-611">D</span><span class="sxs-lookup"><span data-stu-id="9371c-611">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-612">D</span><span class="sxs-lookup"><span data-stu-id="9371c-612">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-613">D</span><span class="sxs-lookup"><span data-stu-id="9371c-613">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-614">D</span><span class="sxs-lookup"><span data-stu-id="9371c-614">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-615">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="9371c-615">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-616">D</span><span class="sxs-lookup"><span data-stu-id="9371c-616">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-617">D</span><span class="sxs-lookup"><span data-stu-id="9371c-617">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-618">D</span><span class="sxs-lookup"><span data-stu-id="9371c-618">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-619">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="9371c-619">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-620">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-620">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-621">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-621">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-622">D</span><span class="sxs-lookup"><span data-stu-id="9371c-622">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-623">D</span><span class="sxs-lookup"><span data-stu-id="9371c-623">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="9371c-624">XBox</span><span class="sxs-lookup"><span data-stu-id="9371c-624">XBox</span></span>

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
<th align="left"><span data-ttu-id="9371c-625">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="9371c-625">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="9371c-626">FOURCC</span><span class="sxs-lookup"><span data-stu-id="9371c-626">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="9371c-627">fMP4</span><span class="sxs-lookup"><span data-stu-id="9371c-627">fMP4</span></span></th>
<th align="left"><span data-ttu-id="9371c-628">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="9371c-628">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="9371c-629">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="9371c-629">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="9371c-630">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="9371c-630">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="9371c-631">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-631">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="9371c-632">3GPP</span><span class="sxs-lookup"><span data-stu-id="9371c-632">3GPP</span></span></th>
<th align="left"><span data-ttu-id="9371c-633">3GPP2</span><span class="sxs-lookup"><span data-stu-id="9371c-633">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="9371c-634">AVCHD</span><span class="sxs-lookup"><span data-stu-id="9371c-634">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="9371c-635">ASF</span><span class="sxs-lookup"><span data-stu-id="9371c-635">ASF</span></span></th>
<th align="left"><span data-ttu-id="9371c-636">AVI</span><span class="sxs-lookup"><span data-stu-id="9371c-636">AVI</span></span></th>
<th align="left"><span data-ttu-id="9371c-637">MKV</span><span class="sxs-lookup"><span data-stu-id="9371c-637">MKV</span></span></th>
<th align="left"><span data-ttu-id="9371c-638">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-638">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-639">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="9371c-639">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-640">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-640">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-641">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-641">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-642">D</span><span class="sxs-lookup"><span data-stu-id="9371c-642">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-643">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-643">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-644">D</span><span class="sxs-lookup"><span data-stu-id="9371c-644">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-645">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="9371c-645">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-646">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-646">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-647">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-647">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-648">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-648">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-649">D</span><span class="sxs-lookup"><span data-stu-id="9371c-649">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-650">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="9371c-650">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-651">D</span><span class="sxs-lookup"><span data-stu-id="9371c-651">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-652">D</span><span class="sxs-lookup"><span data-stu-id="9371c-652">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-653">D</span><span class="sxs-lookup"><span data-stu-id="9371c-653">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-654">D</span><span class="sxs-lookup"><span data-stu-id="9371c-654">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-655">H.265</span><span class="sxs-lookup"><span data-stu-id="9371c-655">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-656">D</span><span class="sxs-lookup"><span data-stu-id="9371c-656">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-657">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-657">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-658">D</span><span class="sxs-lookup"><span data-stu-id="9371c-658">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-659">H.264</span><span class="sxs-lookup"><span data-stu-id="9371c-659">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-660">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-660">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-661">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-661">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-662">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-662">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-663">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-663">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-664">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-664">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-665">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-665">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-666">D</span><span class="sxs-lookup"><span data-stu-id="9371c-666">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-667">D</span><span class="sxs-lookup"><span data-stu-id="9371c-667">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-668">H.263</span><span class="sxs-lookup"><span data-stu-id="9371c-668">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-669">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-669">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-670">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-670">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-671">D</span><span class="sxs-lookup"><span data-stu-id="9371c-671">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-672">VC-1</span><span class="sxs-lookup"><span data-stu-id="9371c-672">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-673">D</span><span class="sxs-lookup"><span data-stu-id="9371c-673">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-674">D</span><span class="sxs-lookup"><span data-stu-id="9371c-674">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-675">D</span><span class="sxs-lookup"><span data-stu-id="9371c-675">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-676">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="9371c-676">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-677">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="9371c-677">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-678">DV</span><span class="sxs-lookup"><span data-stu-id="9371c-678">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="9371c-679">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-679">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-680">D</span><span class="sxs-lookup"><span data-stu-id="9371c-680">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="9371c-681">D</span><span class="sxs-lookup"><span data-stu-id="9371c-681">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="image-codec--format-support"></a><span data-ttu-id="9371c-682">Unterstützung von Bildcodecs und -formaten</span><span class="sxs-lookup"><span data-stu-id="9371c-682">Image codec & format support</span></span> 

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="9371c-683">Codec</span><span class="sxs-lookup"><span data-stu-id="9371c-683">Codec</span></span></th>
<th align="left"><span data-ttu-id="9371c-684">Desktop</span><span class="sxs-lookup"><span data-stu-id="9371c-684">Desktop</span></span></th>
<th align="left"><span data-ttu-id="9371c-685">Andere Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="9371c-685">Other device families</span></span></th>
</tr>
</thead>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-686">BMP</span><span class="sxs-lookup"><span data-stu-id="9371c-686">BMP</span></span></td>
<td align="left"><span data-ttu-id="9371c-687">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-687">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-688">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-688">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-689">DDS</span><span class="sxs-lookup"><span data-stu-id="9371c-689">DDS</span></span></td>
<td align="left"><span data-ttu-id="9371c-690">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9371c-690">D/E<sup>1</sup></span></span></td>
<td align="left"><span data-ttu-id="9371c-691">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9371c-691">D/E<sup>1</sup></span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-692">DNG</span><span class="sxs-lookup"><span data-stu-id="9371c-692">DNG</span></span></td>
<td align="left"><span data-ttu-id="9371c-693">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="9371c-693">D<sup>2</sup></span></span></td>
<td align="left"><span data-ttu-id="9371c-694">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="9371c-694">D<sup>2</sup></span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-695">GIF</span><span class="sxs-lookup"><span data-stu-id="9371c-695">GIF</span></span></td>
<td align="left"><span data-ttu-id="9371c-696">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-696">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-697">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-697">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-698">ICO</span><span class="sxs-lookup"><span data-stu-id="9371c-698">ICO</span></span></td>
<td align="left"><span data-ttu-id="9371c-699">D</span><span class="sxs-lookup"><span data-stu-id="9371c-699">D</span></span></td>
<td align="left"><span data-ttu-id="9371c-700">D</span><span class="sxs-lookup"><span data-stu-id="9371c-700">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-701">JPEG</span><span class="sxs-lookup"><span data-stu-id="9371c-701">JPEG</span></span></td>
<td align="left"><span data-ttu-id="9371c-702">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-702">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-703">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-703">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-704">JPEG-XR</span><span class="sxs-lookup"><span data-stu-id="9371c-704">JPEG-XR</span></span></td>
<td align="left"><span data-ttu-id="9371c-705">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-705">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-706">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-706">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-707">PNG</span><span class="sxs-lookup"><span data-stu-id="9371c-707">PNG</span></span></td>
<td align="left"><span data-ttu-id="9371c-708">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-708">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-709">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-709">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="9371c-710">TIFF</span><span class="sxs-lookup"><span data-stu-id="9371c-710">TIFF</span></span></td>
<td align="left"><span data-ttu-id="9371c-711">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-711">D/E</span></span></td>
<td align="left"><span data-ttu-id="9371c-712">D/E</span><span class="sxs-lookup"><span data-stu-id="9371c-712">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="9371c-713">Kamera-RAW</span><span class="sxs-lookup"><span data-stu-id="9371c-713">Camera RAW</span></span></td>
<td align="left"><span data-ttu-id="9371c-714">D<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="9371c-714">D<sup>3</sup></span></span></td>
<td align="left"><span data-ttu-id="9371c-715">Nein</span><span class="sxs-lookup"><span data-stu-id="9371c-715">No</span></span></td>
</tr>
</table>

<span data-ttu-id="9371c-716"><sup>1</sup> DDS-Bilder mit BC1- bis BC5-Komprimierung werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9371c-716"><sup>1</sup> DDS images using BC1 through BC5 compression are supported.</span></span>  
<span data-ttu-id="9371c-717"><sup>2</sup> DNG-Bilder mit einer nicht als RAW eingebetteten Vorschau werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9371c-717"><sup>2</sup> DNG images with a non-RAW embedded preview are supported.</span></span>  
<span data-ttu-id="9371c-718"><sup>3</sup> Nur bestimmte Kamera-RAW-Formate werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9371c-718"><sup>3</sup> Only certain camera RAW formats are supported.</span></span>  

<span data-ttu-id="9371c-719">Weitere Informationen zu Bildcodecs finden Sie unter [Systemeigene WIC-Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span><span class="sxs-lookup"><span data-stu-id="9371c-719">For more information on image codecs, see [Native WIC Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span></span>