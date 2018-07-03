---
author: drewbatgit
ms.assetid: 3E0FBB43-F6A4-4558-AA89-20E7760BA73F
description: Dieser Artikel enthält eine Liste der Dynamic Adaptive Streaming over HTTP (DASH)-Profile, die für UWP-Apps unterstützt werden.
title: Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung
ms.author: drewbat
ms.date: 02/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c411d479430f793d85863f66c64758155b8a5758
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1842337"
---
# <a name="dynamic-adaptive-streaming-over-http-dash-profile-support"></a><span data-ttu-id="198da-104">Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung</span><span class="sxs-lookup"><span data-stu-id="198da-104">Dynamic Adaptive Streaming over HTTP (DASH) profile support</span></span>


## <a name="supported-dash-profiles"></a><span data-ttu-id="198da-105">Unterstützte DASH-Profile</span><span class="sxs-lookup"><span data-stu-id="198da-105">Supported DASH profiles</span></span>
<span data-ttu-id="198da-106">In der folgenden Tabelle sind die DASH-Profile aufgeführt, die für UWP-Apps unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="198da-106">The following table lists the DASH profiles that are supported for UWP apps.</span></span>

|<span data-ttu-id="198da-107">Tag</span><span class="sxs-lookup"><span data-stu-id="198da-107">Tag</span></span> | <span data-ttu-id="198da-108">Manifesttyp</span><span class="sxs-lookup"><span data-stu-id="198da-108">Manifest type</span></span> | <span data-ttu-id="198da-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="198da-109">Notes</span></span>|<span data-ttu-id="198da-110">Juliversion von Windows 10</span><span class="sxs-lookup"><span data-stu-id="198da-110">July release of Windows 10</span></span>|<span data-ttu-id="198da-111">Windows 10, Version 1511</span><span class="sxs-lookup"><span data-stu-id="198da-111">Windows 10, Version 1511</span></span>|<span data-ttu-id="198da-112">Windows 10, Version 1607</span><span class="sxs-lookup"><span data-stu-id="198da-112">Windows 10, Version 1607</span></span> |<span data-ttu-id="198da-113">Windows 10, Version 1607</span><span class="sxs-lookup"><span data-stu-id="198da-113">Windows 10, Version 1607</span></span> |<span data-ttu-id="198da-114">Windows 10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="198da-114">Windows 10, Version 1703</span></span>|
|----------------|------|-------|-----------|--------------|---------|-------|--------|
|<span data-ttu-id="198da-115">urn:mpeg&#58;dash:profile:isoff-live:2011</span><span class="sxs-lookup"><span data-stu-id="198da-115">urn:mpeg&#58;dash:profile:isoff-live:2011</span></span> | <span data-ttu-id="198da-116">Statisch</span><span class="sxs-lookup"><span data-stu-id="198da-116">Static</span></span> |     |<span data-ttu-id="198da-117">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-117">Supported</span></span>            |  <span data-ttu-id="198da-118">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-118">Supported</span></span>              | <span data-ttu-id="198da-119">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-119">Supported</span></span>        |<span data-ttu-id="198da-120">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-120">Supported</span></span>| <span data-ttu-id="198da-121">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-121">Supported</span></span>|
|<span data-ttu-id="198da-122">urn:mpeg&#58;dash:profile:isoff-main:2011</span><span class="sxs-lookup"><span data-stu-id="198da-122">urn:mpeg&#58;dash:profile:isoff-main:2011</span></span> |        | <span data-ttu-id="198da-123">Beste Leistung</span><span class="sxs-lookup"><span data-stu-id="198da-123">Best effort</span></span> | <span data-ttu-id="198da-124">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-124">Supported</span></span>            |  <span data-ttu-id="198da-125">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-125">Supported</span></span>              | <span data-ttu-id="198da-126">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-126">Supported</span></span>        |<span data-ttu-id="198da-127">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-127">Supported</span></span>| <span data-ttu-id="198da-128">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-128">Supported</span></span>|
|<span data-ttu-id="198da-129">urn:mpeg&#58;dash:profile:isoff-live:2011</span><span class="sxs-lookup"><span data-stu-id="198da-129">urn:mpeg&#58;dash:profile:isoff-live:2011</span></span> | <span data-ttu-id="198da-130">Dynamisch</span><span class="sxs-lookup"><span data-stu-id="198da-130">Dynamic</span></span> | <span data-ttu-id="198da-131">$Time$ wird in Segmentvorlagen unterstützt, aber $Number$ nicht.</span><span class="sxs-lookup"><span data-stu-id="198da-131">$Time$ is supported but $Number$ is unsupported in segment templates</span></span> | <span data-ttu-id="198da-132">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-132">Not Supported</span></span>            | <span data-ttu-id="198da-133">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-133">Not Supported</span></span>              | <span data-ttu-id="198da-134">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-134">Not Supported</span></span>        |<span data-ttu-id="198da-135">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-135">Not Supported</span></span>| <span data-ttu-id="198da-136">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="198da-136">Supported</span></span>|


## <a name="unsupported-dash-profiles"></a><span data-ttu-id="198da-137">Nicht unterstützte DASH-Profile</span><span class="sxs-lookup"><span data-stu-id="198da-137">Unsupported DASH profiles</span></span>
<span data-ttu-id="198da-138">Profile, die nicht in der obigen Tabelle aufgeführt sind, werden nicht unterstützt, einschließlich, aber nicht beschränkt auf folgende:</span><span class="sxs-lookup"><span data-stu-id="198da-138">Profiles not listed in the above table are unsupported, including but not limited to the following:</span></span>

* <span data-ttu-id="198da-139">urn:mpeg&#58;dash:profile:full:2011</span><span class="sxs-lookup"><span data-stu-id="198da-139">urn:mpeg&#58;dash:profile:full:2011</span></span>
* <span data-ttu-id="198da-140">urn:mpeg&#58;dash:profile:isoff-on-demand:2011</span><span class="sxs-lookup"><span data-stu-id="198da-140">urn:mpeg&#58;dash:profile:isoff-on-demand:2011</span></span>
* <span data-ttu-id="198da-141">urn:mpeg&#58;dash:profile:mp2t-main:2011</span><span class="sxs-lookup"><span data-stu-id="198da-141">urn:mpeg&#58;dash:profile:mp2t-main:2011</span></span>
* <span data-ttu-id="198da-142">urn:mpeg&#58;dash:profile:mp2t-simple:2011</span><span class="sxs-lookup"><span data-stu-id="198da-142">urn:mpeg&#58;dash:profile:mp2t-simple:2011</span></span>


## <a name="related-topics"></a><span data-ttu-id="198da-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="198da-143">Related topics</span></span>

* [<span data-ttu-id="198da-144">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="198da-144">Media playback</span></span>](media-playback.md)
* [<span data-ttu-id="198da-145">Adaptives Streaming</span><span class="sxs-lookup"><span data-stu-id="198da-145">Adaptive streaming</span></span>](adaptive-streaming.md)
 

 




