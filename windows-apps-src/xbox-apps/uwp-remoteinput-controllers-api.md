---
title: Geräteportal-Controller– API-Referenz
description: Hier erfahren Sie, wie Sie die Anzahl der angeschlossenen physischen Controller abrufen und sie programmgesteuert deaktivieren.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8b5061f9193d78d4ff23f5fa707b0bea67a10f98
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7707047"
---
# <a name="controller-api-reference"></a><span data-ttu-id="c68ab-104">Controller– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="c68ab-104">Controller API reference</span></span>   
<span data-ttu-id="c68ab-105">Mit dieser REST-API können Sie die Anzahl der angeschlossenen physischen Controller abrufen und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="c68ab-105">You can get the number of attached physical controllers and turn them off using this REST API.</span></span>

## <a name="determine-the-number-of-attached-physical-controllers"></a><span data-ttu-id="c68ab-106">Bestimmen der Anzahl der angeschlossenen physischen Controller</span><span class="sxs-lookup"><span data-stu-id="c68ab-106">Determine the number of attached physical controllers</span></span>

**<span data-ttu-id="c68ab-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c68ab-107">Request</span></span>**

<span data-ttu-id="c68ab-108">Sie können die Anzahl der angeschlossenen physischen Controller auf dem Gerät mit der folgenden Anforderung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="c68ab-108">You can check the number of attached physical controllers on the device using the following request.</span></span>

<span data-ttu-id="c68ab-109">Methode</span><span class="sxs-lookup"><span data-stu-id="c68ab-109">Method</span></span>      | <span data-ttu-id="c68ab-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c68ab-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c68ab-111">GET</span><span class="sxs-lookup"><span data-stu-id="c68ab-111">GET</span></span> | <span data-ttu-id="c68ab-112">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="c68ab-112">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="c68ab-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c68ab-113">URI parameters</span></span>**

- <span data-ttu-id="c68ab-114">Keine</span><span class="sxs-lookup"><span data-stu-id="c68ab-114">None</span></span>

**<span data-ttu-id="c68ab-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c68ab-115">Request headers</span></span>**

- <span data-ttu-id="c68ab-116">Keiner</span><span class="sxs-lookup"><span data-stu-id="c68ab-116">None</span></span>

**<span data-ttu-id="c68ab-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c68ab-117">Request body</span></span>**   

- <span data-ttu-id="c68ab-118">Keine</span><span class="sxs-lookup"><span data-stu-id="c68ab-118">None</span></span>

**<span data-ttu-id="c68ab-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="c68ab-119">Response</span></span>**   

- <span data-ttu-id="c68ab-120">Die JSON-Number-Eigenschaft ConnectedControllerCount, die die Anzahl der angeschlossenen physischen Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="c68ab-120">JSON number property ConnectedControllerCount which specifies the number of attached physical controllers.</span></span>

**<span data-ttu-id="c68ab-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c68ab-121">Status code</span></span>**

<span data-ttu-id="c68ab-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c68ab-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="c68ab-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c68ab-123">HTTP status code</span></span>      | <span data-ttu-id="c68ab-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c68ab-124">Description</span></span>
:------     | :-----
<span data-ttu-id="c68ab-125">200</span><span class="sxs-lookup"><span data-stu-id="c68ab-125">200</span></span> | <span data-ttu-id="c68ab-126">Erfolg</span><span class="sxs-lookup"><span data-stu-id="c68ab-126">Success</span></span>
<span data-ttu-id="c68ab-127">4XX</span><span class="sxs-lookup"><span data-stu-id="c68ab-127">4XX</span></span> | <span data-ttu-id="c68ab-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c68ab-128">Error codes</span></span>
<span data-ttu-id="c68ab-129">5XX</span><span class="sxs-lookup"><span data-stu-id="c68ab-129">5XX</span></span> | <span data-ttu-id="c68ab-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c68ab-130">Error codes</span></span>

## <a name="disconnect-all-physical-controllers-on-the-devkit"></a><span data-ttu-id="c68ab-131">Trennen aller physischen Controller im Entwickler-Kit</span><span class="sxs-lookup"><span data-stu-id="c68ab-131">Disconnect all physical controllers on the devkit</span></span>

**<span data-ttu-id="c68ab-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c68ab-132">Request</span></span>**

<span data-ttu-id="c68ab-133">Sie können alle physischen Controller auf dem Gerät mithilfe der folgenden Anforderung trennen.</span><span class="sxs-lookup"><span data-stu-id="c68ab-133">You can disconnect all physical controllers on the device using the following request.</span></span>

<span data-ttu-id="c68ab-134">Methode</span><span class="sxs-lookup"><span data-stu-id="c68ab-134">Method</span></span>      | <span data-ttu-id="c68ab-135">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c68ab-135">Request URI</span></span>
:------     | :-----
<span data-ttu-id="c68ab-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="c68ab-136">DELETE</span></span> | <span data-ttu-id="c68ab-137">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="c68ab-137">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="c68ab-138">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="c68ab-138">URI parameters</span></span>**

- <span data-ttu-id="c68ab-139">Keine</span><span class="sxs-lookup"><span data-stu-id="c68ab-139">None</span></span>

**<span data-ttu-id="c68ab-140">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c68ab-140">Request headers</span></span>**

- <span data-ttu-id="c68ab-141">Keiner</span><span class="sxs-lookup"><span data-stu-id="c68ab-141">None</span></span>

**<span data-ttu-id="c68ab-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c68ab-142">Request body</span></span>**   

- <span data-ttu-id="c68ab-143">Keine</span><span class="sxs-lookup"><span data-stu-id="c68ab-143">None</span></span>

**<span data-ttu-id="c68ab-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="c68ab-144">Response</span></span>**   

- <span data-ttu-id="c68ab-145">Keine</span><span class="sxs-lookup"><span data-stu-id="c68ab-145">None</span></span> 

**<span data-ttu-id="c68ab-146">Statuscode</span><span class="sxs-lookup"><span data-stu-id="c68ab-146">Status code</span></span>**

<span data-ttu-id="c68ab-147">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="c68ab-147">This API has the following expected status codes.</span></span>

<span data-ttu-id="c68ab-148">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="c68ab-148">HTTP status code</span></span>      | <span data-ttu-id="c68ab-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c68ab-149">Description</span></span>
:------     | :-----
<span data-ttu-id="c68ab-150">204</span><span class="sxs-lookup"><span data-stu-id="c68ab-150">204</span></span> | <span data-ttu-id="c68ab-151">Die Anforderung zum Trennen der Controller war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="c68ab-151">The request to disconnect controllers was successful.</span></span>
<span data-ttu-id="c68ab-152">4XX</span><span class="sxs-lookup"><span data-stu-id="c68ab-152">4XX</span></span> | <span data-ttu-id="c68ab-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c68ab-153">Error codes</span></span>
<span data-ttu-id="c68ab-154">5XX</span><span class="sxs-lookup"><span data-stu-id="c68ab-154">5XX</span></span> | <span data-ttu-id="c68ab-155">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c68ab-155">Error codes</span></span>

<br />
**<span data-ttu-id="c68ab-156">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="c68ab-156">Available device families</span></span>**

* <span data-ttu-id="c68ab-157">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="c68ab-157">Windows Xbox</span></span>
