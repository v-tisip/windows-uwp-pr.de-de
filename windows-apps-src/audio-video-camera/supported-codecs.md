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
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5868114"
---
# <a name="supported-codecs"></a><span data-ttu-id="fca2e-104">Unterstützte Codecs</span><span class="sxs-lookup"><span data-stu-id="fca2e-104">Supported codecs</span></span>

<span data-ttu-id="fca2e-105">In diesem Artikel ist die Verfügbarkeit von Audio-, Video- und Bild-Codecs und -Formaten für UWP-Apps standardmäßig für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-105">This article lists the audio, video, and image codec and format availability for UWP apps by default for each device family.</span></span> <span data-ttu-id="fca2e-106">Beachten Sie, dass diese Tabellen die Codecs enthalten, die in der Windows10-Installation für die angegebene Gerätefamilie enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="fca2e-106">Note that these tables list the codecs that are included with the Windows 10 installation for the specified device family.</span></span> <span data-ttu-id="fca2e-107">Benutzer und Apps können zusätzliche Codecs installieren, die unter Umständen zur Verwendung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="fca2e-107">Users and apps can install additional codecs that may be available to use.</span></span> <span data-ttu-id="fca2e-108">Sie können zur Laufzeit den Satz von Codecs abfragen, die derzeit für ein bestimmtes Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="fca2e-108">You can query at runtime for the set of codecs that are currently available for a specific device.</span></span> <span data-ttu-id="fca2e-109">Weitere Informationen finden Sie unter [Abfragen von auf einem Gerät installierten Codecs](codec-query.md).</span><span class="sxs-lookup"><span data-stu-id="fca2e-109">For more information, see [Query for codecs installed on a device](codec-query.md).</span></span>

<span data-ttu-id="fca2e-110">In den folgenden Tabellen steht „D“ für Decoderunterstützung und „E“ für Encoderunterstützung.</span><span class="sxs-lookup"><span data-stu-id="fca2e-110">In the tables below "D" indicates decoder support and "E" indicates encoder support.</span></span>

## <a name="audio-codec--format-support"></a><span data-ttu-id="fca2e-111">Unterstützung von Audiocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="fca2e-111">Audio codec & format support</span></span>

<span data-ttu-id="fca2e-112">In den folgenden Tabellen wird die Unterstützung von Audiocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-112">The following tables show the audio codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="fca2e-113">Wo AMR-NB-Unterstützung angegeben ist, wird dieser Codec nicht auf Server-SKUs unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-113">Where AMR-NB support is indicated, this codec is not supported on Server SKUs.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="fca2e-114">Desktop</span><span class="sxs-lookup"><span data-stu-id="fca2e-114">Desktop</span></span>

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
<th align="left"><span data-ttu-id="fca2e-115">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-115">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-116">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-116">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-117">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-117">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-118">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-118">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-119">ADTS</span><span class="sxs-lookup"><span data-stu-id="fca2e-119">ADTS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-120">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-120">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-121">RIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-121">RIFF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-122">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-122">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-123">AC-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-123">AC-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-124">AMR</span><span class="sxs-lookup"><span data-stu-id="fca2e-124">AMR</span></span></th>
<th align="left"><span data-ttu-id="fca2e-125">3GP</span><span class="sxs-lookup"><span data-stu-id="fca2e-125">3GP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-126">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-126">FLAC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-127">WAV</span><span class="sxs-lookup"><span data-stu-id="fca2e-127">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-128">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-128">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-129">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-129">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-130">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-130">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-131">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-131">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-132">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-132">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-133">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-133">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-134">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="fca2e-134">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-135">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-135">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-136">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-136">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-137">AC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-137">AC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-138">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-138">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-139">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-139">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-140">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-140">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-141">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-141">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-142">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-142">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-143">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-143">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-144">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-144">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-145">ALAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-145">ALAC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-146">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-146">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-147">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="fca2e-147">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="fca2e-148">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-148">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-149">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-149">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-150">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-150">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-151">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-151">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-152">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-152">D/E</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-153">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="fca2e-153">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-154">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-154">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-155">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="fca2e-155">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-156">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-156">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-157">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-157">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-158">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-158">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-159">LPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-159">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-160">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-160">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-161">MP3</span><span class="sxs-lookup"><span data-stu-id="fca2e-161">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-162">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-162">D/E</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-163">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="fca2e-163">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-164">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-164">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-165">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-165">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-166">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-166">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-167">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="fca2e-167">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-168">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-168">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-169">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="fca2e-169">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-170">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-170">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-171">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="fca2e-171">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-172">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-172">D/E</span></span></td>
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

 

### <a name="mobile"></a><span data-ttu-id="fca2e-173">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="fca2e-173">Mobile</span></span>

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
<th align="left"><span data-ttu-id="fca2e-174">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-174">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-175">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-175">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-176">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-176">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-177">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-177">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-178">ADTS</span><span class="sxs-lookup"><span data-stu-id="fca2e-178">ADTS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-179">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-179">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-180">RIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-180">RIFF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-181">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-181">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-182">AC-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-182">AC-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-183">AMR</span><span class="sxs-lookup"><span data-stu-id="fca2e-183">AMR</span></span></th>
<th align="left"><span data-ttu-id="fca2e-184">3GP</span><span class="sxs-lookup"><span data-stu-id="fca2e-184">3GP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-185">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-185">FLAC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-186">WAV</span><span class="sxs-lookup"><span data-stu-id="fca2e-186">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-187">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-187">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-188">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-188">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-189">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-189">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-190">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-190">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-191">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-191">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-192">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-192">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-193">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="fca2e-193">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-194">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-194">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-195">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-195">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-196">AC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-196">AC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-197">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-197">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-198">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-198">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-199">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-199">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="fca2e-200">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-200">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="fca2e-201">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-201">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"><span data-ttu-id="fca2e-202">D, nur auf Lumia Icon, 830, 930, 1520</span><span class="sxs-lookup"><span data-stu-id="fca2e-202">D, Only on Lumia Icon, 830, 930, 1520</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-203">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-203">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-204">ALAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-204">ALAC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-205">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-205">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-206">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="fca2e-206">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="fca2e-207">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-207">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-208">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-208">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-209">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-209">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-210">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-210">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-211">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-211">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-212">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="fca2e-212">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-213">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-213">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-214">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="fca2e-214">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-215">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-215">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-216">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-216">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-217">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-217">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-218">LPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-218">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-219">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-219">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-220">MP3</span><span class="sxs-lookup"><span data-stu-id="fca2e-220">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-221">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-221">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-222">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="fca2e-222">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-223">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-223">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-224">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-224">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-225">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="fca2e-225">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-226">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-226">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-227">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="fca2e-227">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-228">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-228">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-229">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="fca2e-229">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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

 

### <a name="iot-core-x86"></a><span data-ttu-id="fca2e-230">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="fca2e-230">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="fca2e-231">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-231">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-232">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-232">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-233">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-233">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-234">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-234">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-235">ADTS</span><span class="sxs-lookup"><span data-stu-id="fca2e-235">ADTS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-236">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-236">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-237">RIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-237">RIFF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-238">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-238">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-239">AC-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-239">AC-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-240">AMR</span><span class="sxs-lookup"><span data-stu-id="fca2e-240">AMR</span></span></th>
<th align="left"><span data-ttu-id="fca2e-241">3GP</span><span class="sxs-lookup"><span data-stu-id="fca2e-241">3GP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-242">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-242">FLAC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-243">WAV</span><span class="sxs-lookup"><span data-stu-id="fca2e-243">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-244">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-244">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-245">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-245">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-246">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-246">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-247">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-247">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-248">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-248">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-249">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-249">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-250">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="fca2e-250">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-251">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-251">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-252">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-252">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-253">AC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-253">AC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-254">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-254">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-255">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-255">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-256">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-256">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-257">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-257">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-258">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-258">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-259">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-259">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-260">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-260">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-261">ALAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-261">ALAC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-262">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-262">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-263">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="fca2e-263">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="fca2e-264">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-264">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-265">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-265">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-266">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-266">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-267">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-267">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-268">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-268">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-269">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="fca2e-269">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-270">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-270">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-271">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="fca2e-271">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-272">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-272">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-273">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-273">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-274">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-274">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-275">LPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-275">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-276">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-276">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-277">MP3</span><span class="sxs-lookup"><span data-stu-id="fca2e-277">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-278">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-278">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-279">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="fca2e-279">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-280">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-280">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-281">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-281">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-282">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-282">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-283">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="fca2e-283">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-284">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-284">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-285">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="fca2e-285">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-286">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-286">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-287">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="fca2e-287">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-288">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-288">D</span></span></td>
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

 

### <a name="iot-core-arm"></a><span data-ttu-id="fca2e-289">IoT Core (ARM)</span><span class="sxs-lookup"><span data-stu-id="fca2e-289">IoT Core (ARM)</span></span>

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
<th align="left"><span data-ttu-id="fca2e-290">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-290">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-291">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-291">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-292">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-292">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-293">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-293">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-294">ADTS</span><span class="sxs-lookup"><span data-stu-id="fca2e-294">ADTS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-295">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-295">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-296">RIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-296">RIFF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-297">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-297">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-298">AC-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-298">AC-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-299">AMR</span><span class="sxs-lookup"><span data-stu-id="fca2e-299">AMR</span></span></th>
<th align="left"><span data-ttu-id="fca2e-300">3GP</span><span class="sxs-lookup"><span data-stu-id="fca2e-300">3GP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-301">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-301">FLAC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-302">WAV</span><span class="sxs-lookup"><span data-stu-id="fca2e-302">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-303">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-303">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-304">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-304">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-305">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-305">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-306">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-306">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-307">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-307">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-308">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-308">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-309">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="fca2e-309">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-310">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-310">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-311">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-311">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-312">AC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-312">AC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-313">EAC3/EC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-313">EAC3 / EC3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-314">ALAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-314">ALAC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-315">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-315">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-316">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="fca2e-316">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="fca2e-317">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-317">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-318">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-318">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-319">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-319">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-320">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-320">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-321">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-321">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-322">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="fca2e-322">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-323">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-323">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-324">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="fca2e-324">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-325">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-325">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-326">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-326">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-327">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-327">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-328">LPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-328">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-329">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-329">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-330">MP3</span><span class="sxs-lookup"><span data-stu-id="fca2e-330">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-331">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-331">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-332">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="fca2e-332">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-333">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-333">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-334">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-334">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-335">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-335">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-336">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="fca2e-336">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-337">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-337">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-338">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="fca2e-338">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-339">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-339">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-340">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="fca2e-340">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-341">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-341">D</span></span></td>
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

 

### <a name="xbox"></a><span data-ttu-id="fca2e-342">XBox</span><span class="sxs-lookup"><span data-stu-id="fca2e-342">XBox</span></span>

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
<th align="left"><span data-ttu-id="fca2e-343">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-343">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-344">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-344">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-345">MPEG-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-345">MPEG-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-346">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-346">MPEG-2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-347">ADTS</span><span class="sxs-lookup"><span data-stu-id="fca2e-347">ADTS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-348">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-348">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-349">RIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-349">RIFF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-350">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-350">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-351">AC-3</span><span class="sxs-lookup"><span data-stu-id="fca2e-351">AC-3</span></span></th>
<th align="left"><span data-ttu-id="fca2e-352">AMR</span><span class="sxs-lookup"><span data-stu-id="fca2e-352">AMR</span></span></th>
<th align="left"><span data-ttu-id="fca2e-353">3GP</span><span class="sxs-lookup"><span data-stu-id="fca2e-353">3GP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-354">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-354">FLAC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-355">WAV</span><span class="sxs-lookup"><span data-stu-id="fca2e-355">WAV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-356">HE-AAC v1 / AAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-356">HE-AAC v1 / AAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-357">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-357">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-358">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-358">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-359">HE-AAC v2 / eAAC+</span><span class="sxs-lookup"><span data-stu-id="fca2e-359">HE-AAC v2 / eAAC+</span></span></td>
<td align="left"><span data-ttu-id="fca2e-360">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-360">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-361">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-361">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-362">AAC-LC</span><span class="sxs-lookup"><span data-stu-id="fca2e-362">AAC-LC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-363">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-363">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-364">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-364">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-365">AC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-365">AC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-366">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-366">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-367">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-367">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-368">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-368">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-369">EAC3 / EC3</span><span class="sxs-lookup"><span data-stu-id="fca2e-369">EAC3 / EC3</span></span></td>
<td align="left"><span data-ttu-id="fca2e-370">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-370">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-371">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-371">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-372">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-372">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-373">ALAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-373">ALAC</span></span></td>
<td align="left"><span data-ttu-id="fca2e-374">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-374">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-375">AMR-NB</span><span class="sxs-lookup"><span data-stu-id="fca2e-375">AMR-NB</span></span></td>
<td align="left"><span data-ttu-id="fca2e-376">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-376">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-377">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-377">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-378">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-378">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-379">FLAC</span><span class="sxs-lookup"><span data-stu-id="fca2e-379">FLAC</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-380">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-380">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-381">G.711 (A-Law, µ-law)</span><span class="sxs-lookup"><span data-stu-id="fca2e-381">G.711 (A-Law, µ-law)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-382">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-382">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-383">GSM 6.10</span><span class="sxs-lookup"><span data-stu-id="fca2e-383">GSM 6.10</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-384">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-384">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-385">IMA ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-385">IMA ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-386">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-386">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-387">LPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-387">LPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-388">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-388">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-389">MP3</span><span class="sxs-lookup"><span data-stu-id="fca2e-389">MP3</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-390">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-390">D</span></span></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-391">MPEG-1/2</span><span class="sxs-lookup"><span data-stu-id="fca2e-391">MPEG-1/2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-392">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-392">D</span></span></td>
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
<td align="left"><span data-ttu-id="fca2e-393">MS ADPCM</span><span class="sxs-lookup"><span data-stu-id="fca2e-393">MS ADPCM</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-394">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-394">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-395">WMA 1/2/3</span><span class="sxs-lookup"><span data-stu-id="fca2e-395">WMA 1/2/3</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-396">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-396">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-397">WMA Pro</span><span class="sxs-lookup"><span data-stu-id="fca2e-397">WMA Pro</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-398">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-398">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-399">WMA Voice</span><span class="sxs-lookup"><span data-stu-id="fca2e-399">WMA Voice</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-400">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-400">D</span></span></td>
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

 

## <a name="video-codec--format-support"></a><span data-ttu-id="fca2e-401">Unterstützung von Videocodecs und Formaten</span><span class="sxs-lookup"><span data-stu-id="fca2e-401">Video codec & format support</span></span>

<span data-ttu-id="fca2e-402">In den folgenden Tabellen wird die Unterstützung von Videocodecs und Formaten für jede Gerätefamilie aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-402">The following tables show the video codec and format support for each device family.</span></span>

> [!NOTE] 
> <span data-ttu-id="fca2e-403">Wo H.265-Unterstützung angegeben ist, gilt diese nicht unbedingt für alle Geräten innerhalb der Gerätefamilie.</span><span class="sxs-lookup"><span data-stu-id="fca2e-403">Where H.265 support is indicated, it is not necessarily supported by all devices within the device family.</span></span>
> <span data-ttu-id="fca2e-404">Wo MPEG-2/MPEG-1-Unterstützung angegeben ist, gilt diese nur mit der Installation der optionalen universellen Microsoft DVD-Windows-App.</span><span class="sxs-lookup"><span data-stu-id="fca2e-404">Where MPEG-2/MPEG-1 support is indicated, it is only supported with the installation of the optional Microsoft DVD Universal Windows app.</span></span>

 

### <a name="desktop"></a><span data-ttu-id="fca2e-405">Desktop</span><span class="sxs-lookup"><span data-stu-id="fca2e-405">Desktop</span></span>

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
<th align="left"><span data-ttu-id="fca2e-406">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-406">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-407">FOURCC</span><span class="sxs-lookup"><span data-stu-id="fca2e-407">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-408">fMP4</span><span class="sxs-lookup"><span data-stu-id="fca2e-408">fMP4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-409">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-409">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-410">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="fca2e-410">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-411">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="fca2e-411">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-412">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-412">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="fca2e-413">3GPP</span><span class="sxs-lookup"><span data-stu-id="fca2e-413">3GPP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-414">3GPP2</span><span class="sxs-lookup"><span data-stu-id="fca2e-414">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-415">AVCHD</span><span class="sxs-lookup"><span data-stu-id="fca2e-415">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="fca2e-416">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-416">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-417">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-417">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-418">MKV</span><span class="sxs-lookup"><span data-stu-id="fca2e-418">MKV</span></span></th>
<th align="left"><span data-ttu-id="fca2e-419">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-419">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-420">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-420">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-421">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-421">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-422">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-422">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-423">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-423">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-424">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-424">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-425">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-425">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-426">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-426">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-427">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-427">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-428">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-428">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-429">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-429">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-430">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-430">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-431">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="fca2e-431">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-432">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-432">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-433">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-433">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-434">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-434">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-435">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-435">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-436">H.265</span><span class="sxs-lookup"><span data-stu-id="fca2e-436">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-437">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-437">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-438">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-438">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-439">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-439">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-440">H.264</span><span class="sxs-lookup"><span data-stu-id="fca2e-440">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-441">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-441">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-442">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-442">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-443">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-443">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-444">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-444">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-445">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-445">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-446">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-446">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-447">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-447">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-448">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-448">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-449">H.263</span><span class="sxs-lookup"><span data-stu-id="fca2e-449">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-450">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-450">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-451">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-451">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-452">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-452">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-453">VC-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-453">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-454">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-454">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-455">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-455">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-456">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-456">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-457">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-457">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-458">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="fca2e-458">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-459">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-459">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-460">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-460">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-461">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-461">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-462">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="fca2e-462">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-463">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-463">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-464">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-464">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-465">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-465">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-466">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-466">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-467">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-467">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-468">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-468">D</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-469">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-469">D</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-470">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-470">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-471">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-471">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-472">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-472">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="mobile"></a><span data-ttu-id="fca2e-473">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="fca2e-473">Mobile</span></span>

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
<th align="left"><span data-ttu-id="fca2e-474">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-474">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-475">FOURCC</span><span class="sxs-lookup"><span data-stu-id="fca2e-475">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-476">fMP4</span><span class="sxs-lookup"><span data-stu-id="fca2e-476">fMP4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-477">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-477">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-478">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="fca2e-478">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-479">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="fca2e-479">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-480">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-480">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="fca2e-481">3GPP</span><span class="sxs-lookup"><span data-stu-id="fca2e-481">3GPP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-482">3GPP2</span><span class="sxs-lookup"><span data-stu-id="fca2e-482">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-483">AVCHD</span><span class="sxs-lookup"><span data-stu-id="fca2e-483">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="fca2e-484">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-484">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-485">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-485">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-486">MKV</span><span class="sxs-lookup"><span data-stu-id="fca2e-486">MKV</span></span></th>
<th align="left"><span data-ttu-id="fca2e-487">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-487">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-488">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-488">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-489">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-489">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-490">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="fca2e-490">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-491">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-491">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-492">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-492">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-493">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-493">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-494">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-494">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-495">H.265</span><span class="sxs-lookup"><span data-stu-id="fca2e-495">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-496">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-496">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-497">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-497">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-498">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-498">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-499">H.264</span><span class="sxs-lookup"><span data-stu-id="fca2e-499">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-500">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-500">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-501">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-501">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-502">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-502">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-503">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-503">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-504">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-504">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-505">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-505">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-506">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-506">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-507">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-507">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-508">H.263</span><span class="sxs-lookup"><span data-stu-id="fca2e-508">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-509">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-509">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-510">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-510">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-511">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-511">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-512">VC-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-512">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-513">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-513">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-514">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-514">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-515">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-515">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-516">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="fca2e-516">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-517">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="fca2e-517">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-518">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-518">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-519">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-519">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-520">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-520">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-521">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-521">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-core-x86"></a><span data-ttu-id="fca2e-522">IoT Core (x86)</span><span class="sxs-lookup"><span data-stu-id="fca2e-522">IoT Core (x86)</span></span>

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
<th align="left"><span data-ttu-id="fca2e-523">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-523">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-524">FOURCC</span><span class="sxs-lookup"><span data-stu-id="fca2e-524">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-525">fMP4</span><span class="sxs-lookup"><span data-stu-id="fca2e-525">fMP4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-526">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-526">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-527">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="fca2e-527">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-528">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="fca2e-528">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-529">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-529">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="fca2e-530">3GPP</span><span class="sxs-lookup"><span data-stu-id="fca2e-530">3GPP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-531">3GPP2</span><span class="sxs-lookup"><span data-stu-id="fca2e-531">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-532">AVCHD</span><span class="sxs-lookup"><span data-stu-id="fca2e-532">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="fca2e-533">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-533">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-534">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-534">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-535">MKV</span><span class="sxs-lookup"><span data-stu-id="fca2e-535">MKV</span></span></th>
<th align="left"><span data-ttu-id="fca2e-536">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-536">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-537">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-537">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-538">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-538">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-539">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="fca2e-539">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-540">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-540">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-541">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-541">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-542">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-542">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-543">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-543">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-544">H.265</span><span class="sxs-lookup"><span data-stu-id="fca2e-544">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-545">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-545">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-546">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-546">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-547">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-547">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-548">H.264</span><span class="sxs-lookup"><span data-stu-id="fca2e-548">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-549">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-549">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-550">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-550">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-551">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-551">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-552">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-552">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-553">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-553">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-554">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-554">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-555">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-555">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-556">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-556">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-557">H.263</span><span class="sxs-lookup"><span data-stu-id="fca2e-557">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-558">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-558">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-559">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-559">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-560">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-560">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-561">VC-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-561">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-562">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-562">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-563">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-563">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-564">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-564">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-565">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-565">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-566">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="fca2e-566">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-567">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-567">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-568">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-568">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-569">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-569">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-570">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="fca2e-570">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-571">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-571">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-572">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-572">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-573">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-573">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-574">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-574">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-575">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-575">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-576">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-576">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-577">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-577">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="iot-arm"></a><span data-ttu-id="fca2e-578">IoT (ARM)</span><span class="sxs-lookup"><span data-stu-id="fca2e-578">IoT (ARM)</span></span>

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
<th align="left"><span data-ttu-id="fca2e-579">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-579">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-580">FOURCC</span><span class="sxs-lookup"><span data-stu-id="fca2e-580">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-581">fMP4</span><span class="sxs-lookup"><span data-stu-id="fca2e-581">fMP4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-582">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-582">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-583">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="fca2e-583">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-584">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="fca2e-584">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-585">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-585">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="fca2e-586">3GPP</span><span class="sxs-lookup"><span data-stu-id="fca2e-586">3GPP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-587">3GPP2</span><span class="sxs-lookup"><span data-stu-id="fca2e-587">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-588">AVCHD</span><span class="sxs-lookup"><span data-stu-id="fca2e-588">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="fca2e-589">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-589">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-590">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-590">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-591">MKV</span><span class="sxs-lookup"><span data-stu-id="fca2e-591">MKV</span></span></th>
<th align="left"><span data-ttu-id="fca2e-592">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-592">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-593">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-593">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-594">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-594">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-595">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="fca2e-595">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-596">H.265</span><span class="sxs-lookup"><span data-stu-id="fca2e-596">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-597">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-597">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-598">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-598">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-599">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-599">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-600">H.264</span><span class="sxs-lookup"><span data-stu-id="fca2e-600">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-601">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-601">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-602">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-602">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-603">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-603">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-604">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-604">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-605">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-605">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-606">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-606">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-607">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-607">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-608">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-608">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-609">H.263</span><span class="sxs-lookup"><span data-stu-id="fca2e-609">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-610">VC-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-610">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-611">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-611">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-612">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-612">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-613">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-613">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-614">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-614">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-615">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="fca2e-615">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-616">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-616">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-617">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-617">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-618">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-618">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-619">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="fca2e-619">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-620">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-620">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-621">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-621">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-622">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-622">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-623">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-623">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

### <a name="xbox"></a><span data-ttu-id="fca2e-624">XBox</span><span class="sxs-lookup"><span data-stu-id="fca2e-624">XBox</span></span>

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
<th align="left"><span data-ttu-id="fca2e-625">Codec/Container</span><span class="sxs-lookup"><span data-stu-id="fca2e-625">Codec/Container</span></span></th>
<th align="left"><span data-ttu-id="fca2e-626">FOURCC</span><span class="sxs-lookup"><span data-stu-id="fca2e-626">FOURCC</span></span></th>
<th align="left"><span data-ttu-id="fca2e-627">fMP4</span><span class="sxs-lookup"><span data-stu-id="fca2e-627">fMP4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-628">MPEG-4</span><span class="sxs-lookup"><span data-stu-id="fca2e-628">MPEG-4</span></span></th>
<th align="left"><span data-ttu-id="fca2e-629">MPEG-2-PS</span><span class="sxs-lookup"><span data-stu-id="fca2e-629">MPEG-2 PS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-630">MPEG-2 TS</span><span class="sxs-lookup"><span data-stu-id="fca2e-630">MPEG-2 TS</span></span></th>
<th align="left"><span data-ttu-id="fca2e-631">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-631">MPEG-1</span></span></th>
<th align="left"><span data-ttu-id="fca2e-632">3GPP</span><span class="sxs-lookup"><span data-stu-id="fca2e-632">3GPP</span></span></th>
<th align="left"><span data-ttu-id="fca2e-633">3GPP2</span><span class="sxs-lookup"><span data-stu-id="fca2e-633">3GPP2</span></span></th>
<th align="left"><span data-ttu-id="fca2e-634">AVCHD</span><span class="sxs-lookup"><span data-stu-id="fca2e-634">AVCHD</span></span></th>
<th align="left"><span data-ttu-id="fca2e-635">ASF</span><span class="sxs-lookup"><span data-stu-id="fca2e-635">ASF</span></span></th>
<th align="left"><span data-ttu-id="fca2e-636">AVI</span><span class="sxs-lookup"><span data-stu-id="fca2e-636">AVI</span></span></th>
<th align="left"><span data-ttu-id="fca2e-637">MKV</span><span class="sxs-lookup"><span data-stu-id="fca2e-637">MKV</span></span></th>
<th align="left"><span data-ttu-id="fca2e-638">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-638">DV</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-639">MPEG-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-639">MPEG-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-640">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-640">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-641">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-641">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-642">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-642">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-643">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-643">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-644">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-644">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-645">MPEG-2</span><span class="sxs-lookup"><span data-stu-id="fca2e-645">MPEG-2</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-646">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-646">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-647">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-647">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-648">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-648">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-649">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-649">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-650">MPEG-4 (Teil 2)</span><span class="sxs-lookup"><span data-stu-id="fca2e-650">MPEG-4 (Part 2)</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-651">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-651">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-652">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-652">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-653">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-653">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-654">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-654">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-655">H.265</span><span class="sxs-lookup"><span data-stu-id="fca2e-655">H.265</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-656">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-656">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-657">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-657">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-658">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-658">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-659">H.264</span><span class="sxs-lookup"><span data-stu-id="fca2e-659">H.264</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-660">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-660">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-661">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-661">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-662">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-662">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-663">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-663">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-664">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-664">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-665">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-665">D/E</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-666">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-666">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-667">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-667">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-668">H.263</span><span class="sxs-lookup"><span data-stu-id="fca2e-668">H.263</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-669">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-669">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-670">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-670">D/E</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-671">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-671">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-672">VC-1</span><span class="sxs-lookup"><span data-stu-id="fca2e-672">VC-1</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-673">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-673">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-674">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-674">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-675">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-675">D</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-676">WMV7/8/9</span><span class="sxs-lookup"><span data-stu-id="fca2e-676">WMV7/8/9</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-677">WMV9-Bildschirm</span><span class="sxs-lookup"><span data-stu-id="fca2e-677">WMV9 Screen</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-678">DV</span><span class="sxs-lookup"><span data-stu-id="fca2e-678">DV</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
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
<td align="left"><span data-ttu-id="fca2e-679">Motion JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-679">Motion JPEG</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-680">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-680">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="fca2e-681">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-681">D</span></span></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="image-codec--format-support"></a><span data-ttu-id="fca2e-682">Unterstützung von Bildcodecs und -formaten</span><span class="sxs-lookup"><span data-stu-id="fca2e-682">Image codec & format support</span></span> 

<table>
<colgroup>
<col width="7%" />
<col width="7%" />
<col width="7%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fca2e-683">Codec</span><span class="sxs-lookup"><span data-stu-id="fca2e-683">Codec</span></span></th>
<th align="left"><span data-ttu-id="fca2e-684">Desktop</span><span class="sxs-lookup"><span data-stu-id="fca2e-684">Desktop</span></span></th>
<th align="left"><span data-ttu-id="fca2e-685">Andere Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="fca2e-685">Other device families</span></span></th>
</tr>
</thead>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-686">BMP</span><span class="sxs-lookup"><span data-stu-id="fca2e-686">BMP</span></span></td>
<td align="left"><span data-ttu-id="fca2e-687">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-687">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-688">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-688">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-689">DDS</span><span class="sxs-lookup"><span data-stu-id="fca2e-689">DDS</span></span></td>
<td align="left"><span data-ttu-id="fca2e-690">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fca2e-690">D/E<sup>1</sup></span></span></td>
<td align="left"><span data-ttu-id="fca2e-691">D/E<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fca2e-691">D/E<sup>1</sup></span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-692">DNG</span><span class="sxs-lookup"><span data-stu-id="fca2e-692">DNG</span></span></td>
<td align="left"><span data-ttu-id="fca2e-693">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fca2e-693">D<sup>2</sup></span></span></td>
<td align="left"><span data-ttu-id="fca2e-694">D<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fca2e-694">D<sup>2</sup></span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-695">GIF</span><span class="sxs-lookup"><span data-stu-id="fca2e-695">GIF</span></span></td>
<td align="left"><span data-ttu-id="fca2e-696">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-696">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-697">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-697">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-698">ICO</span><span class="sxs-lookup"><span data-stu-id="fca2e-698">ICO</span></span></td>
<td align="left"><span data-ttu-id="fca2e-699">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-699">D</span></span></td>
<td align="left"><span data-ttu-id="fca2e-700">D</span><span class="sxs-lookup"><span data-stu-id="fca2e-700">D</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-701">JPEG</span><span class="sxs-lookup"><span data-stu-id="fca2e-701">JPEG</span></span></td>
<td align="left"><span data-ttu-id="fca2e-702">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-702">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-703">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-703">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-704">JPEG-XR</span><span class="sxs-lookup"><span data-stu-id="fca2e-704">JPEG-XR</span></span></td>
<td align="left"><span data-ttu-id="fca2e-705">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-705">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-706">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-706">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-707">PNG</span><span class="sxs-lookup"><span data-stu-id="fca2e-707">PNG</span></span></td>
<td align="left"><span data-ttu-id="fca2e-708">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-708">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-709">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-709">D/E</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fca2e-710">TIFF</span><span class="sxs-lookup"><span data-stu-id="fca2e-710">TIFF</span></span></td>
<td align="left"><span data-ttu-id="fca2e-711">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-711">D/E</span></span></td>
<td align="left"><span data-ttu-id="fca2e-712">D/E</span><span class="sxs-lookup"><span data-stu-id="fca2e-712">D/E</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fca2e-713">Kamera-RAW</span><span class="sxs-lookup"><span data-stu-id="fca2e-713">Camera RAW</span></span></td>
<td align="left"><span data-ttu-id="fca2e-714">D<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="fca2e-714">D<sup>3</sup></span></span></td>
<td align="left"><span data-ttu-id="fca2e-715">Nein</span><span class="sxs-lookup"><span data-stu-id="fca2e-715">No</span></span></td>
</tr>
</table>

<span data-ttu-id="fca2e-716"><sup>1</sup> DDS-Bilder mit BC1- bis BC5-Komprimierung werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-716"><sup>1</sup> DDS images using BC1 through BC5 compression are supported.</span></span>  
<span data-ttu-id="fca2e-717"><sup>2</sup> DNG-Bilder mit einer nicht als RAW eingebetteten Vorschau werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-717"><sup>2</sup> DNG images with a non-RAW embedded preview are supported.</span></span>  
<span data-ttu-id="fca2e-718"><sup>3</sup> Nur bestimmte Kamera-RAW-Formate werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fca2e-718"><sup>3</sup> Only certain camera RAW formats are supported.</span></span>  

<span data-ttu-id="fca2e-719">Weitere Informationen zu Bildcodecs finden Sie unter [Systemeigene WIC-Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span><span class="sxs-lookup"><span data-stu-id="fca2e-719">For more information on image codecs, see [Native WIC Codecs](https://msdn.microsoft.com/library/windows/desktop/gg430027.aspx).</span></span>