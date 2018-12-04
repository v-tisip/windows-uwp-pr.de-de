---
title: Geräteportal-Controller– API-Referenz
description: Hier erfahren Sie, wie Sie die Anzahl der angeschlossenen physischen Controller abrufen und sie programmgesteuert deaktivieren.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8b5061f9193d78d4ff23f5fa707b0bea67a10f98
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8478395"
---
# <a name="controller-api-reference"></a><span data-ttu-id="a71c5-104">Controller– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="a71c5-104">Controller API reference</span></span>   
<span data-ttu-id="a71c5-105">Mit dieser REST-API können Sie die Anzahl der angeschlossenen physischen Controller abrufen und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a71c5-105">You can get the number of attached physical controllers and turn them off using this REST API.</span></span>

## <a name="determine-the-number-of-attached-physical-controllers"></a><span data-ttu-id="a71c5-106">Bestimmen der Anzahl der angeschlossenen physischen Controller</span><span class="sxs-lookup"><span data-stu-id="a71c5-106">Determine the number of attached physical controllers</span></span>

**<span data-ttu-id="a71c5-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a71c5-107">Request</span></span>**

<span data-ttu-id="a71c5-108">Sie können die Anzahl der angeschlossenen physischen Controller auf dem Gerät mit der folgenden Anforderung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="a71c5-108">You can check the number of attached physical controllers on the device using the following request.</span></span>

<span data-ttu-id="a71c5-109">Methode</span><span class="sxs-lookup"><span data-stu-id="a71c5-109">Method</span></span>      | <span data-ttu-id="a71c5-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a71c5-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="a71c5-111">GET</span><span class="sxs-lookup"><span data-stu-id="a71c5-111">GET</span></span> | <span data-ttu-id="a71c5-112">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="a71c5-112">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="a71c5-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="a71c5-113">URI parameters</span></span>**

- <span data-ttu-id="a71c5-114">Keine</span><span class="sxs-lookup"><span data-stu-id="a71c5-114">None</span></span>

**<span data-ttu-id="a71c5-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a71c5-115">Request headers</span></span>**

- <span data-ttu-id="a71c5-116">Keiner</span><span class="sxs-lookup"><span data-stu-id="a71c5-116">None</span></span>

**<span data-ttu-id="a71c5-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="a71c5-117">Request body</span></span>**   

- <span data-ttu-id="a71c5-118">Keine</span><span class="sxs-lookup"><span data-stu-id="a71c5-118">None</span></span>

**<span data-ttu-id="a71c5-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="a71c5-119">Response</span></span>**   

- <span data-ttu-id="a71c5-120">Die JSON-Number-Eigenschaft ConnectedControllerCount, die die Anzahl der angeschlossenen physischen Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="a71c5-120">JSON number property ConnectedControllerCount which specifies the number of attached physical controllers.</span></span>

**<span data-ttu-id="a71c5-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="a71c5-121">Status code</span></span>**

<span data-ttu-id="a71c5-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="a71c5-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="a71c5-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="a71c5-123">HTTP status code</span></span>      | <span data-ttu-id="a71c5-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a71c5-124">Description</span></span>
:------     | :-----
<span data-ttu-id="a71c5-125">200</span><span class="sxs-lookup"><span data-stu-id="a71c5-125">200</span></span> | <span data-ttu-id="a71c5-126">Erfolg</span><span class="sxs-lookup"><span data-stu-id="a71c5-126">Success</span></span>
<span data-ttu-id="a71c5-127">4XX</span><span class="sxs-lookup"><span data-stu-id="a71c5-127">4XX</span></span> | <span data-ttu-id="a71c5-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a71c5-128">Error codes</span></span>
<span data-ttu-id="a71c5-129">5XX</span><span class="sxs-lookup"><span data-stu-id="a71c5-129">5XX</span></span> | <span data-ttu-id="a71c5-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a71c5-130">Error codes</span></span>

## <a name="disconnect-all-physical-controllers-on-the-devkit"></a><span data-ttu-id="a71c5-131">Trennen aller physischen Controller im Entwickler-Kit</span><span class="sxs-lookup"><span data-stu-id="a71c5-131">Disconnect all physical controllers on the devkit</span></span>

**<span data-ttu-id="a71c5-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a71c5-132">Request</span></span>**

<span data-ttu-id="a71c5-133">Sie können alle physischen Controller auf dem Gerät mithilfe der folgenden Anforderung trennen.</span><span class="sxs-lookup"><span data-stu-id="a71c5-133">You can disconnect all physical controllers on the device using the following request.</span></span>

<span data-ttu-id="a71c5-134">Methode</span><span class="sxs-lookup"><span data-stu-id="a71c5-134">Method</span></span>      | <span data-ttu-id="a71c5-135">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a71c5-135">Request URI</span></span>
:------     | :-----
<span data-ttu-id="a71c5-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="a71c5-136">DELETE</span></span> | <span data-ttu-id="a71c5-137">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="a71c5-137">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="a71c5-138">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="a71c5-138">URI parameters</span></span>**

- <span data-ttu-id="a71c5-139">Keine</span><span class="sxs-lookup"><span data-stu-id="a71c5-139">None</span></span>

**<span data-ttu-id="a71c5-140">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a71c5-140">Request headers</span></span>**

- <span data-ttu-id="a71c5-141">Keiner</span><span class="sxs-lookup"><span data-stu-id="a71c5-141">None</span></span>

**<span data-ttu-id="a71c5-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="a71c5-142">Request body</span></span>**   

- <span data-ttu-id="a71c5-143">Keine</span><span class="sxs-lookup"><span data-stu-id="a71c5-143">None</span></span>

**<span data-ttu-id="a71c5-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="a71c5-144">Response</span></span>**   

- <span data-ttu-id="a71c5-145">Keine</span><span class="sxs-lookup"><span data-stu-id="a71c5-145">None</span></span> 

**<span data-ttu-id="a71c5-146">Statuscode</span><span class="sxs-lookup"><span data-stu-id="a71c5-146">Status code</span></span>**

<span data-ttu-id="a71c5-147">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="a71c5-147">This API has the following expected status codes.</span></span>

<span data-ttu-id="a71c5-148">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="a71c5-148">HTTP status code</span></span>      | <span data-ttu-id="a71c5-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a71c5-149">Description</span></span>
:------     | :-----
<span data-ttu-id="a71c5-150">204</span><span class="sxs-lookup"><span data-stu-id="a71c5-150">204</span></span> | <span data-ttu-id="a71c5-151">Die Anforderung zum Trennen der Controller war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="a71c5-151">The request to disconnect controllers was successful.</span></span>
<span data-ttu-id="a71c5-152">4XX</span><span class="sxs-lookup"><span data-stu-id="a71c5-152">4XX</span></span> | <span data-ttu-id="a71c5-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a71c5-153">Error codes</span></span>
<span data-ttu-id="a71c5-154">5XX</span><span class="sxs-lookup"><span data-stu-id="a71c5-154">5XX</span></span> | <span data-ttu-id="a71c5-155">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a71c5-155">Error codes</span></span>

<br />
**<span data-ttu-id="a71c5-156">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="a71c5-156">Available device families</span></span>**

* <span data-ttu-id="a71c5-157">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="a71c5-157">Windows Xbox</span></span>
