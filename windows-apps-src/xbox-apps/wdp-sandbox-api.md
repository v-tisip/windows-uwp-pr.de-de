---
title: Device Portal - Referenz zur API für den Xbox Live-Sandkasten
description: Erfahren Sie, wie Sie programmgesteuert auf den Xbox Live-Sandkasten zugreifen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 72c7459c-420a-4da9-8afa-191a846185a5
ms.localizationpriority: medium
ms.openlocfilehash: d05528ecf4408a7e7483b909b75722037c6528b7
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8758430"
---
# <a name="xbox-live-sandbox-api-reference"></a><span data-ttu-id="459b1-104">Referenz zur API für den Xbox Live-Sandkasten</span><span class="sxs-lookup"><span data-stu-id="459b1-104">Xbox Live Sandbox API reference</span></span>   
<span data-ttu-id="459b1-105">Mit dieser REST-API können Sie den Xbox Live-Sandkasten abrufen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="459b1-105">You can get and set your Xbox Live sandbox using this REST API.</span></span>

## <a name="get-the-xbox-live-sandbox"></a><span data-ttu-id="459b1-106">Abrufen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="459b1-106">Get the Xbox Live sandbox</span></span>

**<span data-ttu-id="459b1-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="459b1-107">Request</span></span>**

<span data-ttu-id="459b1-108">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts lesen:</span><span class="sxs-lookup"><span data-stu-id="459b1-108">You can read the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="459b1-109">Methode</span><span class="sxs-lookup"><span data-stu-id="459b1-109">Method</span></span>      | <span data-ttu-id="459b1-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="459b1-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="459b1-111">GET</span><span class="sxs-lookup"><span data-stu-id="459b1-111">GET</span></span> | <span data-ttu-id="459b1-112">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="459b1-112">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="459b1-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="459b1-113">URI parameters</span></span>**

- <span data-ttu-id="459b1-114">Keine</span><span class="sxs-lookup"><span data-stu-id="459b1-114">None</span></span>

**<span data-ttu-id="459b1-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="459b1-115">Request headers</span></span>**

- <span data-ttu-id="459b1-116">Keine</span><span class="sxs-lookup"><span data-stu-id="459b1-116">None</span></span>

**<span data-ttu-id="459b1-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="459b1-117">Request body</span></span>**

- <span data-ttu-id="459b1-118">Keine</span><span class="sxs-lookup"><span data-stu-id="459b1-118">None</span></span>

**<span data-ttu-id="459b1-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="459b1-119">Response</span></span>**   
<span data-ttu-id="459b1-120">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="459b1-120">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="459b1-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="459b1-121">Status code</span></span>**

<span data-ttu-id="459b1-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="459b1-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="459b1-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="459b1-123">HTTP status code</span></span>      | <span data-ttu-id="459b1-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="459b1-124">Description</span></span>
:------     | :-----
<span data-ttu-id="459b1-125">200</span><span class="sxs-lookup"><span data-stu-id="459b1-125">200</span></span> | <span data-ttu-id="459b1-126">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="459b1-126">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="459b1-127">4XX</span><span class="sxs-lookup"><span data-stu-id="459b1-127">4XX</span></span> | <span data-ttu-id="459b1-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="459b1-128">Error codes</span></span>
<span data-ttu-id="459b1-129">5XX</span><span class="sxs-lookup"><span data-stu-id="459b1-129">5XX</span></span> | <span data-ttu-id="459b1-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="459b1-130">Error codes</span></span>

## <a name="set-the-xbox-live-sandbox"></a><span data-ttu-id="459b1-131">Festlegen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="459b1-131">Set the Xbox Live sandbox</span></span>
<span data-ttu-id="459b1-132">Mit der folgenden Anforderung können Sie den Xbox Live-Sandkasten des Geräts ändern.</span><span class="sxs-lookup"><span data-stu-id="459b1-132">You can change the Xbox Live sandbox for the device using the following request.</span></span> <span data-ttu-id="459b1-133">Bei der Xbox One muss das Gerät neu gestartet werden, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="459b1-133">Note that on Xbox One, the device needs to be restarted before the setting takes effect.</span></span>

**<span data-ttu-id="459b1-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="459b1-134">Request</span></span>**

<span data-ttu-id="459b1-135">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts festlegen:</span><span class="sxs-lookup"><span data-stu-id="459b1-135">You can set the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="459b1-136">Methode</span><span class="sxs-lookup"><span data-stu-id="459b1-136">Method</span></span>      | <span data-ttu-id="459b1-137">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="459b1-137">Request URI</span></span>
:------     | :-----
<span data-ttu-id="459b1-138">PUT</span><span class="sxs-lookup"><span data-stu-id="459b1-138">PUT</span></span> | <span data-ttu-id="459b1-139">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="459b1-139">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="459b1-140">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="459b1-140">URI parameters</span></span>**

- <span data-ttu-id="459b1-141">Keine</span><span class="sxs-lookup"><span data-stu-id="459b1-141">None</span></span>

**<span data-ttu-id="459b1-142">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="459b1-142">Request headers</span></span>**

- <span data-ttu-id="459b1-143">Keine</span><span class="sxs-lookup"><span data-stu-id="459b1-143">None</span></span>

**<span data-ttu-id="459b1-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="459b1-144">Request body</span></span>**   
<span data-ttu-id="459b1-145">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="459b1-145">The request body is a JSON object containing the following field:</span></span>   
<span data-ttu-id="459b1-146">Sandbox (Zeichenfolge): Der neue Wert, auf den der Sandkasten des Geräts festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="459b1-146">Sandbox - (String) The new value to set the device's sandbox to.</span></span>

**<span data-ttu-id="459b1-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="459b1-147">Response</span></span>**   
<span data-ttu-id="459b1-148">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="459b1-148">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="459b1-149">Statuscode</span><span class="sxs-lookup"><span data-stu-id="459b1-149">Status code</span></span>**

<span data-ttu-id="459b1-150">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="459b1-150">This API has the following expected status codes.</span></span>

<span data-ttu-id="459b1-151">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="459b1-151">HTTP status code</span></span>      | <span data-ttu-id="459b1-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="459b1-152">Description</span></span>
:------     | :-----
<span data-ttu-id="459b1-153">200</span><span class="sxs-lookup"><span data-stu-id="459b1-153">200</span></span> | <span data-ttu-id="459b1-154">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="459b1-154">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="459b1-155">4XX</span><span class="sxs-lookup"><span data-stu-id="459b1-155">4XX</span></span> | <span data-ttu-id="459b1-156">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="459b1-156">Error codes</span></span>
<span data-ttu-id="459b1-157">5XX</span><span class="sxs-lookup"><span data-stu-id="459b1-157">5XX</span></span> | <span data-ttu-id="459b1-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="459b1-158">Error codes</span></span>

<br />
**<span data-ttu-id="459b1-159">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="459b1-159">Available device families</span></span>**

* <span data-ttu-id="459b1-160">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="459b1-160">Windows Xbox</span></span>

