---
author: WilliamsJason
title: Geräteportal-Controller– API-Referenz
description: Hier erfahren Sie, wie Sie die Anzahl der angeschlossenen physischen Controller abrufen und sie programmgesteuert deaktivieren.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5e0b85293ada8619246c3c23ef2103ead5f40c23
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5989370"
---
# <a name="controller-api-reference"></a><span data-ttu-id="1116f-104">Controller– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="1116f-104">Controller API reference</span></span>   
<span data-ttu-id="1116f-105">Mit dieser REST-API können Sie die Anzahl der angeschlossenen physischen Controller abrufen und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1116f-105">You can get the number of attached physical controllers and turn them off using this REST API.</span></span>

## <a name="determine-the-number-of-attached-physical-controllers"></a><span data-ttu-id="1116f-106">Bestimmen der Anzahl der angeschlossenen physischen Controller</span><span class="sxs-lookup"><span data-stu-id="1116f-106">Determine the number of attached physical controllers</span></span>

**<span data-ttu-id="1116f-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="1116f-107">Request</span></span>**

<span data-ttu-id="1116f-108">Sie können die Anzahl der angeschlossenen physischen Controller auf dem Gerät mit der folgenden Anforderung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1116f-108">You can check the number of attached physical controllers on the device using the following request.</span></span>

<span data-ttu-id="1116f-109">Methode</span><span class="sxs-lookup"><span data-stu-id="1116f-109">Method</span></span>      | <span data-ttu-id="1116f-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="1116f-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="1116f-111">GET</span><span class="sxs-lookup"><span data-stu-id="1116f-111">GET</span></span> | <span data-ttu-id="1116f-112">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="1116f-112">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="1116f-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="1116f-113">URI parameters</span></span>**

- <span data-ttu-id="1116f-114">Keine</span><span class="sxs-lookup"><span data-stu-id="1116f-114">None</span></span>

**<span data-ttu-id="1116f-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="1116f-115">Request headers</span></span>**

- <span data-ttu-id="1116f-116">Keiner</span><span class="sxs-lookup"><span data-stu-id="1116f-116">None</span></span>

**<span data-ttu-id="1116f-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="1116f-117">Request body</span></span>**   

- <span data-ttu-id="1116f-118">Keine</span><span class="sxs-lookup"><span data-stu-id="1116f-118">None</span></span>

**<span data-ttu-id="1116f-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="1116f-119">Response</span></span>**   

- <span data-ttu-id="1116f-120">Die JSON-Number-Eigenschaft ConnectedControllerCount, die die Anzahl der angeschlossenen physischen Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="1116f-120">JSON number property ConnectedControllerCount which specifies the number of attached physical controllers.</span></span>

**<span data-ttu-id="1116f-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="1116f-121">Status code</span></span>**

<span data-ttu-id="1116f-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="1116f-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="1116f-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="1116f-123">HTTP status code</span></span>      | <span data-ttu-id="1116f-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1116f-124">Description</span></span>
:------     | :-----
<span data-ttu-id="1116f-125">200</span><span class="sxs-lookup"><span data-stu-id="1116f-125">200</span></span> | <span data-ttu-id="1116f-126">Erfolg</span><span class="sxs-lookup"><span data-stu-id="1116f-126">Success</span></span>
<span data-ttu-id="1116f-127">4XX</span><span class="sxs-lookup"><span data-stu-id="1116f-127">4XX</span></span> | <span data-ttu-id="1116f-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="1116f-128">Error codes</span></span>
<span data-ttu-id="1116f-129">5XX</span><span class="sxs-lookup"><span data-stu-id="1116f-129">5XX</span></span> | <span data-ttu-id="1116f-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="1116f-130">Error codes</span></span>

## <a name="disconnect-all-physical-controllers-on-the-devkit"></a><span data-ttu-id="1116f-131">Trennen aller physischen Controller im Entwickler-Kit</span><span class="sxs-lookup"><span data-stu-id="1116f-131">Disconnect all physical controllers on the devkit</span></span>

**<span data-ttu-id="1116f-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="1116f-132">Request</span></span>**

<span data-ttu-id="1116f-133">Sie können alle physischen Controller auf dem Gerät mithilfe der folgenden Anforderung trennen.</span><span class="sxs-lookup"><span data-stu-id="1116f-133">You can disconnect all physical controllers on the device using the following request.</span></span>

<span data-ttu-id="1116f-134">Methode</span><span class="sxs-lookup"><span data-stu-id="1116f-134">Method</span></span>      | <span data-ttu-id="1116f-135">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="1116f-135">Request URI</span></span>
:------     | :-----
<span data-ttu-id="1116f-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="1116f-136">DELETE</span></span> | <span data-ttu-id="1116f-137">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="1116f-137">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="1116f-138">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="1116f-138">URI parameters</span></span>**

- <span data-ttu-id="1116f-139">Keine</span><span class="sxs-lookup"><span data-stu-id="1116f-139">None</span></span>

**<span data-ttu-id="1116f-140">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="1116f-140">Request headers</span></span>**

- <span data-ttu-id="1116f-141">Keiner</span><span class="sxs-lookup"><span data-stu-id="1116f-141">None</span></span>

**<span data-ttu-id="1116f-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="1116f-142">Request body</span></span>**   

- <span data-ttu-id="1116f-143">Keine</span><span class="sxs-lookup"><span data-stu-id="1116f-143">None</span></span>

**<span data-ttu-id="1116f-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="1116f-144">Response</span></span>**   

- <span data-ttu-id="1116f-145">Keine</span><span class="sxs-lookup"><span data-stu-id="1116f-145">None</span></span> 

**<span data-ttu-id="1116f-146">Statuscode</span><span class="sxs-lookup"><span data-stu-id="1116f-146">Status code</span></span>**

<span data-ttu-id="1116f-147">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="1116f-147">This API has the following expected status codes.</span></span>

<span data-ttu-id="1116f-148">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="1116f-148">HTTP status code</span></span>      | <span data-ttu-id="1116f-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1116f-149">Description</span></span>
:------     | :-----
<span data-ttu-id="1116f-150">204</span><span class="sxs-lookup"><span data-stu-id="1116f-150">204</span></span> | <span data-ttu-id="1116f-151">Die Anforderung zum Trennen der Controller war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="1116f-151">The request to disconnect controllers was successful.</span></span>
<span data-ttu-id="1116f-152">4XX</span><span class="sxs-lookup"><span data-stu-id="1116f-152">4XX</span></span> | <span data-ttu-id="1116f-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="1116f-153">Error codes</span></span>
<span data-ttu-id="1116f-154">5XX</span><span class="sxs-lookup"><span data-stu-id="1116f-154">5XX</span></span> | <span data-ttu-id="1116f-155">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="1116f-155">Error codes</span></span>

<br />
**<span data-ttu-id="1116f-156">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="1116f-156">Available device families</span></span>**

* <span data-ttu-id="1116f-157">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="1116f-157">Windows Xbox</span></span>
