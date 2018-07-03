---
author: WilliamsJason
title: Geräteportal-Controller– API-Referenz
description: Hier erfahren Sie, wie Sie die Anzahl der angeschlossenen physischen Controller abrufen und sie programmgesteuert deaktivieren.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 292c9c29149b56b9be4255215e97e703278d8abf
ms.sourcegitcommit: c104b653601d9b81cfc8bb6032ca434cff8fe9b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "1921246"
---
# <a name="controller-api-reference"></a><span data-ttu-id="02dee-104">Controller– API-Referenz</span><span class="sxs-lookup"><span data-stu-id="02dee-104">Controller API reference</span></span>   
<span data-ttu-id="02dee-105">Mit dieser REST-API können Sie die Anzahl der angeschlossenen physischen Controller abrufen und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="02dee-105">You can get the number of attached physical controllers and turn them off using this REST API.</span></span>

## <a name="determine-the-number-of-attached-physical-controllers"></a><span data-ttu-id="02dee-106">Bestimmen der Anzahl der angeschlossenen physischen Controller</span><span class="sxs-lookup"><span data-stu-id="02dee-106">Determine the number of attached physical controllers</span></span>

**<span data-ttu-id="02dee-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="02dee-107">Request</span></span>**

<span data-ttu-id="02dee-108">Sie können die Anzahl der angeschlossenen physischen Controller auf dem Gerät mit der folgenden Anforderung überprüfen.</span><span class="sxs-lookup"><span data-stu-id="02dee-108">You can check the number of attached physical controllers on the device using the following request.</span></span>

<span data-ttu-id="02dee-109">Methode</span><span class="sxs-lookup"><span data-stu-id="02dee-109">Method</span></span>      | <span data-ttu-id="02dee-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="02dee-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="02dee-111">GET</span><span class="sxs-lookup"><span data-stu-id="02dee-111">GET</span></span> | <span data-ttu-id="02dee-112">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="02dee-112">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="02dee-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="02dee-113">URI parameters</span></span>**

- <span data-ttu-id="02dee-114">Keine</span><span class="sxs-lookup"><span data-stu-id="02dee-114">None</span></span>

**<span data-ttu-id="02dee-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="02dee-115">Request headers</span></span>**

- <span data-ttu-id="02dee-116">Keiner</span><span class="sxs-lookup"><span data-stu-id="02dee-116">None</span></span>

**<span data-ttu-id="02dee-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="02dee-117">Request body</span></span>**   

- <span data-ttu-id="02dee-118">Keine</span><span class="sxs-lookup"><span data-stu-id="02dee-118">None</span></span>

**<span data-ttu-id="02dee-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="02dee-119">Response</span></span>**   

- <span data-ttu-id="02dee-120">Die JSON-Number-Eigenschaft ConnectedControllerCount, die die Anzahl der angeschlossenen physischen Controller angibt.</span><span class="sxs-lookup"><span data-stu-id="02dee-120">JSON number property ConnectedControllerCount which specifies the number of attached physical controllers.</span></span>

**<span data-ttu-id="02dee-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="02dee-121">Status code</span></span>**

<span data-ttu-id="02dee-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="02dee-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="02dee-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="02dee-123">HTTP status code</span></span>      | <span data-ttu-id="02dee-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02dee-124">Description</span></span>
:------     | :-----
<span data-ttu-id="02dee-125">200</span><span class="sxs-lookup"><span data-stu-id="02dee-125">200</span></span> | <span data-ttu-id="02dee-126">Erfolg</span><span class="sxs-lookup"><span data-stu-id="02dee-126">Success</span></span>
<span data-ttu-id="02dee-127">4XX</span><span class="sxs-lookup"><span data-stu-id="02dee-127">4XX</span></span> | <span data-ttu-id="02dee-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="02dee-128">Error codes</span></span>
<span data-ttu-id="02dee-129">5XX</span><span class="sxs-lookup"><span data-stu-id="02dee-129">5XX</span></span> | <span data-ttu-id="02dee-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="02dee-130">Error codes</span></span>

## <a name="disconnect-all-physical-controllers-on-the-devkit"></a><span data-ttu-id="02dee-131">Trennen aller physischen Controller im Entwickler-Kit</span><span class="sxs-lookup"><span data-stu-id="02dee-131">Disconnect all physical controllers on the devkit</span></span>

**<span data-ttu-id="02dee-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="02dee-132">Request</span></span>**

<span data-ttu-id="02dee-133">Sie können alle physischen Controller auf dem Gerät mithilfe der folgenden Anforderung trennen.</span><span class="sxs-lookup"><span data-stu-id="02dee-133">You can disconnect all physical controllers on the device using the following request.</span></span>

<span data-ttu-id="02dee-134">Methode</span><span class="sxs-lookup"><span data-stu-id="02dee-134">Method</span></span>      | <span data-ttu-id="02dee-135">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="02dee-135">Request URI</span></span>
:------     | :-----
<span data-ttu-id="02dee-136">DELETE</span><span class="sxs-lookup"><span data-stu-id="02dee-136">DELETE</span></span> | <span data-ttu-id="02dee-137">/ext/remoteinput/controllers</span><span class="sxs-lookup"><span data-stu-id="02dee-137">/ext/remoteinput/controllers</span></span>
<br />
**<span data-ttu-id="02dee-138">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="02dee-138">URI parameters</span></span>**

- <span data-ttu-id="02dee-139">Keine</span><span class="sxs-lookup"><span data-stu-id="02dee-139">None</span></span>

**<span data-ttu-id="02dee-140">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="02dee-140">Request headers</span></span>**

- <span data-ttu-id="02dee-141">Keiner</span><span class="sxs-lookup"><span data-stu-id="02dee-141">None</span></span>

**<span data-ttu-id="02dee-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="02dee-142">Request body</span></span>**   

- <span data-ttu-id="02dee-143">Keine</span><span class="sxs-lookup"><span data-stu-id="02dee-143">None</span></span>

**<span data-ttu-id="02dee-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="02dee-144">Response</span></span>**   

- <span data-ttu-id="02dee-145">Keine</span><span class="sxs-lookup"><span data-stu-id="02dee-145">None</span></span> 

**<span data-ttu-id="02dee-146">Statuscode</span><span class="sxs-lookup"><span data-stu-id="02dee-146">Status code</span></span>**

<span data-ttu-id="02dee-147">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="02dee-147">This API has the following expected status codes.</span></span>

<span data-ttu-id="02dee-148">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="02dee-148">HTTP status code</span></span>      | <span data-ttu-id="02dee-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02dee-149">Description</span></span>
:------     | :-----
<span data-ttu-id="02dee-150">204</span><span class="sxs-lookup"><span data-stu-id="02dee-150">204</span></span> | <span data-ttu-id="02dee-151">Die Anforderung zum Trennen der Controller war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="02dee-151">The request to disconnect controllers was successful.</span></span>
<span data-ttu-id="02dee-152">4XX</span><span class="sxs-lookup"><span data-stu-id="02dee-152">4XX</span></span> | <span data-ttu-id="02dee-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="02dee-153">Error codes</span></span>
<span data-ttu-id="02dee-154">5XX</span><span class="sxs-lookup"><span data-stu-id="02dee-154">5XX</span></span> | <span data-ttu-id="02dee-155">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="02dee-155">Error codes</span></span>

<br />
**<span data-ttu-id="02dee-156">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="02dee-156">Available device families</span></span>**

* <span data-ttu-id="02dee-157">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="02dee-157">Windows Xbox</span></span>
