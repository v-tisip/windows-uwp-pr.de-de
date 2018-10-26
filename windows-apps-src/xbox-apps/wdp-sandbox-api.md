---
author: payzer
title: Device Portal - Referenz zur API für den Xbox Live-Sandkasten
description: Erfahren Sie, wie Sie programmgesteuert auf den Xbox Live-Sandkasten zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 72c7459c-420a-4da9-8afa-191a846185a5
ms.localizationpriority: medium
ms.openlocfilehash: 6f1729f07734b181dc5e0e8c97d702d8592302c2
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5569621"
---
# <a name="xbox-live-sandbox-api-reference"></a><span data-ttu-id="bc480-104">Referenz zur API für den Xbox Live-Sandkasten</span><span class="sxs-lookup"><span data-stu-id="bc480-104">Xbox Live Sandbox API reference</span></span>   
<span data-ttu-id="bc480-105">Mit dieser REST-API können Sie den Xbox Live-Sandkasten abrufen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="bc480-105">You can get and set your Xbox Live sandbox using this REST API.</span></span>

## <a name="get-the-xbox-live-sandbox"></a><span data-ttu-id="bc480-106">Abrufen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="bc480-106">Get the Xbox Live sandbox</span></span>

**<span data-ttu-id="bc480-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bc480-107">Request</span></span>**

<span data-ttu-id="bc480-108">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts lesen:</span><span class="sxs-lookup"><span data-stu-id="bc480-108">You can read the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="bc480-109">Methode</span><span class="sxs-lookup"><span data-stu-id="bc480-109">Method</span></span>      | <span data-ttu-id="bc480-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bc480-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bc480-111">GET</span><span class="sxs-lookup"><span data-stu-id="bc480-111">GET</span></span> | <span data-ttu-id="bc480-112">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="bc480-112">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="bc480-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bc480-113">URI parameters</span></span>**

- <span data-ttu-id="bc480-114">Keine</span><span class="sxs-lookup"><span data-stu-id="bc480-114">None</span></span>

**<span data-ttu-id="bc480-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bc480-115">Request headers</span></span>**

- <span data-ttu-id="bc480-116">Keine</span><span class="sxs-lookup"><span data-stu-id="bc480-116">None</span></span>

**<span data-ttu-id="bc480-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bc480-117">Request body</span></span>**

- <span data-ttu-id="bc480-118">Keine</span><span class="sxs-lookup"><span data-stu-id="bc480-118">None</span></span>

**<span data-ttu-id="bc480-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="bc480-119">Response</span></span>**   
<span data-ttu-id="bc480-120">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="bc480-120">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="bc480-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bc480-121">Status code</span></span>**

<span data-ttu-id="bc480-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bc480-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="bc480-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bc480-123">HTTP status code</span></span>      | <span data-ttu-id="bc480-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bc480-124">Description</span></span>
:------     | :-----
<span data-ttu-id="bc480-125">200</span><span class="sxs-lookup"><span data-stu-id="bc480-125">200</span></span> | <span data-ttu-id="bc480-126">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="bc480-126">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="bc480-127">4XX</span><span class="sxs-lookup"><span data-stu-id="bc480-127">4XX</span></span> | <span data-ttu-id="bc480-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bc480-128">Error codes</span></span>
<span data-ttu-id="bc480-129">5XX</span><span class="sxs-lookup"><span data-stu-id="bc480-129">5XX</span></span> | <span data-ttu-id="bc480-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bc480-130">Error codes</span></span>

## <a name="set-the-xbox-live-sandbox"></a><span data-ttu-id="bc480-131">Festlegen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="bc480-131">Set the Xbox Live sandbox</span></span>
<span data-ttu-id="bc480-132">Mit der folgenden Anforderung können Sie den Xbox Live-Sandkasten des Geräts ändern.</span><span class="sxs-lookup"><span data-stu-id="bc480-132">You can change the Xbox Live sandbox for the device using the following request.</span></span> <span data-ttu-id="bc480-133">Bei der Xbox One muss das Gerät neu gestartet werden, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="bc480-133">Note that on Xbox One, the device needs to be restarted before the setting takes effect.</span></span>

**<span data-ttu-id="bc480-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bc480-134">Request</span></span>**

<span data-ttu-id="bc480-135">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts festlegen:</span><span class="sxs-lookup"><span data-stu-id="bc480-135">You can set the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="bc480-136">Methode</span><span class="sxs-lookup"><span data-stu-id="bc480-136">Method</span></span>      | <span data-ttu-id="bc480-137">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bc480-137">Request URI</span></span>
:------     | :-----
<span data-ttu-id="bc480-138">PUT</span><span class="sxs-lookup"><span data-stu-id="bc480-138">PUT</span></span> | <span data-ttu-id="bc480-139">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="bc480-139">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="bc480-140">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="bc480-140">URI parameters</span></span>**

- <span data-ttu-id="bc480-141">Keine</span><span class="sxs-lookup"><span data-stu-id="bc480-141">None</span></span>

**<span data-ttu-id="bc480-142">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bc480-142">Request headers</span></span>**

- <span data-ttu-id="bc480-143">Keine</span><span class="sxs-lookup"><span data-stu-id="bc480-143">None</span></span>

**<span data-ttu-id="bc480-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bc480-144">Request body</span></span>**   
<span data-ttu-id="bc480-145">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="bc480-145">The request body is a JSON object containing the following field:</span></span>   
<span data-ttu-id="bc480-146">Sandbox (Zeichenfolge): Der neue Wert, auf den der Sandkasten des Geräts festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bc480-146">Sandbox - (String) The new value to set the device's sandbox to.</span></span>

**<span data-ttu-id="bc480-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="bc480-147">Response</span></span>**   
<span data-ttu-id="bc480-148">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="bc480-148">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="bc480-149">Statuscode</span><span class="sxs-lookup"><span data-stu-id="bc480-149">Status code</span></span>**

<span data-ttu-id="bc480-150">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="bc480-150">This API has the following expected status codes.</span></span>

<span data-ttu-id="bc480-151">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="bc480-151">HTTP status code</span></span>      | <span data-ttu-id="bc480-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bc480-152">Description</span></span>
:------     | :-----
<span data-ttu-id="bc480-153">200</span><span class="sxs-lookup"><span data-stu-id="bc480-153">200</span></span> | <span data-ttu-id="bc480-154">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="bc480-154">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="bc480-155">4XX</span><span class="sxs-lookup"><span data-stu-id="bc480-155">4XX</span></span> | <span data-ttu-id="bc480-156">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bc480-156">Error codes</span></span>
<span data-ttu-id="bc480-157">5XX</span><span class="sxs-lookup"><span data-stu-id="bc480-157">5XX</span></span> | <span data-ttu-id="bc480-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bc480-158">Error codes</span></span>

<br />
**<span data-ttu-id="bc480-159">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="bc480-159">Available device families</span></span>**

* <span data-ttu-id="bc480-160">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="bc480-160">Windows Xbox</span></span>

