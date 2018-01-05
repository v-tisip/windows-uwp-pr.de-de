---
author: payzer
title: "Device Portal - Referenz zur API für den Xbox Live-Sandkasten"
description: Erfahren Sie, wie Sie programmgesteuert auf den Xbox Live-Sandkasten zugreifen.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 72c7459c-420a-4da9-8afa-191a846185a5
ms.openlocfilehash: d31c943336b36c325218b0b2a8830daf54ed25ca
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="xbox-live-sandbox-api-reference"></a><span data-ttu-id="4fb7f-104">Referenz zur API für den Xbox Live-Sandkasten</span><span class="sxs-lookup"><span data-stu-id="4fb7f-104">Xbox Live Sandbox API reference</span></span>   
<span data-ttu-id="4fb7f-105">Mit dieser REST-API können Sie den Xbox Live-Sandkasten abrufen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-105">You can get and set your Xbox Live sandbox using this REST API.</span></span>

## <a name="get-the-xbox-live-sandbox"></a><span data-ttu-id="4fb7f-106">Abrufen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="4fb7f-106">Get the Xbox Live sandbox</span></span>

**<span data-ttu-id="4fb7f-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="4fb7f-107">Request</span></span>**

<span data-ttu-id="4fb7f-108">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts lesen:</span><span class="sxs-lookup"><span data-stu-id="4fb7f-108">You can read the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="4fb7f-109">Methode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-109">Method</span></span>      | <span data-ttu-id="4fb7f-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="4fb7f-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="4fb7f-111">GET</span><span class="sxs-lookup"><span data-stu-id="4fb7f-111">GET</span></span> | <span data-ttu-id="4fb7f-112">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="4fb7f-112">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="4fb7f-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="4fb7f-113">URI parameters</span></span>**

- <span data-ttu-id="4fb7f-114">Keine</span><span class="sxs-lookup"><span data-stu-id="4fb7f-114">None</span></span>

**<span data-ttu-id="4fb7f-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="4fb7f-115">Request headers</span></span>**

- <span data-ttu-id="4fb7f-116">Keine</span><span class="sxs-lookup"><span data-stu-id="4fb7f-116">None</span></span>

**<span data-ttu-id="4fb7f-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="4fb7f-117">Request body</span></span>**

- <span data-ttu-id="4fb7f-118">Keine</span><span class="sxs-lookup"><span data-stu-id="4fb7f-118">None</span></span>

**<span data-ttu-id="4fb7f-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="4fb7f-119">Response</span></span>**   
<span data-ttu-id="4fb7f-120">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-120">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="4fb7f-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-121">Status code</span></span>**

<span data-ttu-id="4fb7f-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="4fb7f-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="4fb7f-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-123">HTTP status code</span></span>      | <span data-ttu-id="4fb7f-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4fb7f-124">Description</span></span>
:------     | :-----
<span data-ttu-id="4fb7f-125">200</span><span class="sxs-lookup"><span data-stu-id="4fb7f-125">200</span></span> | <span data-ttu-id="4fb7f-126">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-126">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="4fb7f-127">4XX</span><span class="sxs-lookup"><span data-stu-id="4fb7f-127">4XX</span></span> | <span data-ttu-id="4fb7f-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4fb7f-128">Error codes</span></span>
<span data-ttu-id="4fb7f-129">5XX</span><span class="sxs-lookup"><span data-stu-id="4fb7f-129">5XX</span></span> | <span data-ttu-id="4fb7f-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4fb7f-130">Error codes</span></span>

## <a name="set-the-xbox-live-sandbox"></a><span data-ttu-id="4fb7f-131">Festlegen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="4fb7f-131">Set the Xbox Live sandbox</span></span>
<span data-ttu-id="4fb7f-132">Mit der folgenden Anforderung können Sie den Xbox Live-Sandkasten des Geräts ändern.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-132">You can change the Xbox Live sandbox for the device using the following request.</span></span> <span data-ttu-id="4fb7f-133">Bei der Xbox One muss das Gerät neu gestartet werden, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-133">Note that on Xbox One, the device needs to be restarted before the setting takes effect.</span></span>

**<span data-ttu-id="4fb7f-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="4fb7f-134">Request</span></span>**

<span data-ttu-id="4fb7f-135">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts festlegen:</span><span class="sxs-lookup"><span data-stu-id="4fb7f-135">You can set the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="4fb7f-136">Methode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-136">Method</span></span>      | <span data-ttu-id="4fb7f-137">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="4fb7f-137">Request URI</span></span>
:------     | :-----
<span data-ttu-id="4fb7f-138">PUT</span><span class="sxs-lookup"><span data-stu-id="4fb7f-138">PUT</span></span> | <span data-ttu-id="4fb7f-139">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="4fb7f-139">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="4fb7f-140">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="4fb7f-140">URI parameters</span></span>**

- <span data-ttu-id="4fb7f-141">Keine</span><span class="sxs-lookup"><span data-stu-id="4fb7f-141">None</span></span>

**<span data-ttu-id="4fb7f-142">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="4fb7f-142">Request headers</span></span>**

- <span data-ttu-id="4fb7f-143">Keine</span><span class="sxs-lookup"><span data-stu-id="4fb7f-143">None</span></span>

**<span data-ttu-id="4fb7f-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="4fb7f-144">Request body</span></span>**   
<span data-ttu-id="4fb7f-145">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="4fb7f-145">The request body is a JSON object containing the following field:</span></span>   
<span data-ttu-id="4fb7f-146">Sandbox (Zeichenfolge): Der neue Wert, auf den der Sandkasten des Geräts festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-146">Sandbox - (String) The new value to set the device's sandbox to.</span></span>

**<span data-ttu-id="4fb7f-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="4fb7f-147">Response</span></span>**   
<span data-ttu-id="4fb7f-148">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-148">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="4fb7f-149">Statuscode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-149">Status code</span></span>**

<span data-ttu-id="4fb7f-150">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="4fb7f-150">This API has the following expected status codes.</span></span>

<span data-ttu-id="4fb7f-151">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="4fb7f-151">HTTP status code</span></span>      | <span data-ttu-id="4fb7f-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4fb7f-152">Description</span></span>
:------     | :-----
<span data-ttu-id="4fb7f-153">200</span><span class="sxs-lookup"><span data-stu-id="4fb7f-153">200</span></span> | <span data-ttu-id="4fb7f-154">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="4fb7f-154">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="4fb7f-155">4XX</span><span class="sxs-lookup"><span data-stu-id="4fb7f-155">4XX</span></span> | <span data-ttu-id="4fb7f-156">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4fb7f-156">Error codes</span></span>
<span data-ttu-id="4fb7f-157">5XX</span><span class="sxs-lookup"><span data-stu-id="4fb7f-157">5XX</span></span> | <span data-ttu-id="4fb7f-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4fb7f-158">Error codes</span></span>

<br />
**<span data-ttu-id="4fb7f-159">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="4fb7f-159">Available device families</span></span>**

* <span data-ttu-id="4fb7f-160">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="4fb7f-160">Windows Xbox</span></span>

