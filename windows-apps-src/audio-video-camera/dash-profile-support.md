---
ms.assetid: 3E0FBB43-F6A4-4558-AA89-20E7760BA73F
description: Dieser Artikel enthält eine Liste der Dynamic Adaptive Streaming over HTTP (DASH)-Profile, die für UWP-Apps unterstützt werden.
title: Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung
ms.date: 02/15/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d680f7d4a3510f66cba74d1c8b30d8883b07369a
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8926060"
---
# <a name="dynamic-adaptive-streaming-over-http-dash-profile-support"></a><span data-ttu-id="154a2-104">Dynamic Adaptive Streaming over HTTP (DASH)-Profilunterstützung</span><span class="sxs-lookup"><span data-stu-id="154a2-104">Dynamic Adaptive Streaming over HTTP (DASH) profile support</span></span>


## <a name="supported-dash-profiles"></a><span data-ttu-id="154a2-105">Unterstützte DASH-Profile</span><span class="sxs-lookup"><span data-stu-id="154a2-105">Supported DASH profiles</span></span>
<span data-ttu-id="154a2-106">In der folgenden Tabelle sind die DASH-Profile aufgeführt, die für UWP-Apps unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="154a2-106">The following table lists the DASH profiles that are supported for UWP apps.</span></span>

|<span data-ttu-id="154a2-107">Tag</span><span class="sxs-lookup"><span data-stu-id="154a2-107">Tag</span></span> | <span data-ttu-id="154a2-108">Manifesttyp</span><span class="sxs-lookup"><span data-stu-id="154a2-108">Manifest type</span></span> | <span data-ttu-id="154a2-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="154a2-109">Notes</span></span>|<span data-ttu-id="154a2-110">Juliversion von Windows 10</span><span class="sxs-lookup"><span data-stu-id="154a2-110">July release of Windows 10</span></span>|<span data-ttu-id="154a2-111">Windows 10, Version 1511</span><span class="sxs-lookup"><span data-stu-id="154a2-111">Windows 10, Version 1511</span></span>|<span data-ttu-id="154a2-112">Windows 10, Version 1607</span><span class="sxs-lookup"><span data-stu-id="154a2-112">Windows 10, Version 1607</span></span> |<span data-ttu-id="154a2-113">Windows 10, Version 1607</span><span class="sxs-lookup"><span data-stu-id="154a2-113">Windows 10, Version 1607</span></span> |<span data-ttu-id="154a2-114">Windows 10, Version 1703</span><span class="sxs-lookup"><span data-stu-id="154a2-114">Windows 10, Version 1703</span></span>|
|----------------|------|-------|-----------|--------------|---------|-------|--------|
|<span data-ttu-id="154a2-115">urn:mpeg&#58;dash:profile:isoff-live:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-115">urn:mpeg&#58;dash:profile:isoff-live:2011</span></span> | <span data-ttu-id="154a2-116">Statisch</span><span class="sxs-lookup"><span data-stu-id="154a2-116">Static</span></span> |     |<span data-ttu-id="154a2-117">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-117">Supported</span></span>            |  <span data-ttu-id="154a2-118">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-118">Supported</span></span>              | <span data-ttu-id="154a2-119">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-119">Supported</span></span>        |<span data-ttu-id="154a2-120">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-120">Supported</span></span>| <span data-ttu-id="154a2-121">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-121">Supported</span></span>|
|<span data-ttu-id="154a2-122">urn:mpeg&#58;dash:profile:isoff-main:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-122">urn:mpeg&#58;dash:profile:isoff-main:2011</span></span> |        | <span data-ttu-id="154a2-123">Beste Leistung</span><span class="sxs-lookup"><span data-stu-id="154a2-123">Best effort</span></span> | <span data-ttu-id="154a2-124">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-124">Supported</span></span>            |  <span data-ttu-id="154a2-125">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-125">Supported</span></span>              | <span data-ttu-id="154a2-126">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-126">Supported</span></span>        |<span data-ttu-id="154a2-127">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-127">Supported</span></span>| <span data-ttu-id="154a2-128">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-128">Supported</span></span>|
|<span data-ttu-id="154a2-129">urn:mpeg&#58;dash:profile:isoff-live:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-129">urn:mpeg&#58;dash:profile:isoff-live:2011</span></span> | <span data-ttu-id="154a2-130">Dynamisch</span><span class="sxs-lookup"><span data-stu-id="154a2-130">Dynamic</span></span> | <span data-ttu-id="154a2-131">$Time$ wird in Segmentvorlagen unterstützt, aber $Number$ nicht.</span><span class="sxs-lookup"><span data-stu-id="154a2-131">$Time$ is supported but $Number$ is unsupported in segment templates</span></span> | <span data-ttu-id="154a2-132">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-132">Not Supported</span></span>            | <span data-ttu-id="154a2-133">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-133">Not Supported</span></span>              | <span data-ttu-id="154a2-134">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-134">Not Supported</span></span>        |<span data-ttu-id="154a2-135">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-135">Not Supported</span></span>| <span data-ttu-id="154a2-136">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="154a2-136">Supported</span></span>|


## <a name="unsupported-dash-profiles"></a><span data-ttu-id="154a2-137">Nicht unterstützte DASH-Profile</span><span class="sxs-lookup"><span data-stu-id="154a2-137">Unsupported DASH profiles</span></span>
<span data-ttu-id="154a2-138">Profile, die nicht in der obigen Tabelle aufgeführt sind, werden nicht unterstützt, einschließlich, aber nicht beschränkt auf folgende:</span><span class="sxs-lookup"><span data-stu-id="154a2-138">Profiles not listed in the above table are unsupported, including but not limited to the following:</span></span>

* <span data-ttu-id="154a2-139">urn:mpeg&#58;dash:profile:full:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-139">urn:mpeg&#58;dash:profile:full:2011</span></span>
* <span data-ttu-id="154a2-140">urn:mpeg&#58;dash:profile:isoff-on-demand:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-140">urn:mpeg&#58;dash:profile:isoff-on-demand:2011</span></span>
* <span data-ttu-id="154a2-141">urn:mpeg&#58;dash:profile:mp2t-main:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-141">urn:mpeg&#58;dash:profile:mp2t-main:2011</span></span>
* <span data-ttu-id="154a2-142">urn:mpeg&#58;dash:profile:mp2t-simple:2011</span><span class="sxs-lookup"><span data-stu-id="154a2-142">urn:mpeg&#58;dash:profile:mp2t-simple:2011</span></span>


## <a name="related-topics"></a><span data-ttu-id="154a2-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="154a2-143">Related topics</span></span>

* [<span data-ttu-id="154a2-144">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="154a2-144">Media playback</span></span>](media-playback.md)
* [<span data-ttu-id="154a2-145">Adaptives Streaming</span><span class="sxs-lookup"><span data-stu-id="154a2-145">Adaptive streaming</span></span>](adaptive-streaming.md)
 

 




