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
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5977671"
---
# <a name="xbox-live-sandbox-api-reference"></a><span data-ttu-id="71af7-104">Referenz zur API für den Xbox Live-Sandkasten</span><span class="sxs-lookup"><span data-stu-id="71af7-104">Xbox Live Sandbox API reference</span></span>   
<span data-ttu-id="71af7-105">Mit dieser REST-API können Sie den Xbox Live-Sandkasten abrufen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="71af7-105">You can get and set your Xbox Live sandbox using this REST API.</span></span>

## <a name="get-the-xbox-live-sandbox"></a><span data-ttu-id="71af7-106">Abrufen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="71af7-106">Get the Xbox Live sandbox</span></span>

**<span data-ttu-id="71af7-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="71af7-107">Request</span></span>**

<span data-ttu-id="71af7-108">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts lesen:</span><span class="sxs-lookup"><span data-stu-id="71af7-108">You can read the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="71af7-109">Methode</span><span class="sxs-lookup"><span data-stu-id="71af7-109">Method</span></span>      | <span data-ttu-id="71af7-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="71af7-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="71af7-111">GET</span><span class="sxs-lookup"><span data-stu-id="71af7-111">GET</span></span> | <span data-ttu-id="71af7-112">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="71af7-112">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="71af7-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="71af7-113">URI parameters</span></span>**

- <span data-ttu-id="71af7-114">Keine</span><span class="sxs-lookup"><span data-stu-id="71af7-114">None</span></span>

**<span data-ttu-id="71af7-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="71af7-115">Request headers</span></span>**

- <span data-ttu-id="71af7-116">Keine</span><span class="sxs-lookup"><span data-stu-id="71af7-116">None</span></span>

**<span data-ttu-id="71af7-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="71af7-117">Request body</span></span>**

- <span data-ttu-id="71af7-118">Keine</span><span class="sxs-lookup"><span data-stu-id="71af7-118">None</span></span>

**<span data-ttu-id="71af7-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="71af7-119">Response</span></span>**   
<span data-ttu-id="71af7-120">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="71af7-120">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="71af7-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="71af7-121">Status code</span></span>**

<span data-ttu-id="71af7-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="71af7-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="71af7-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="71af7-123">HTTP status code</span></span>      | <span data-ttu-id="71af7-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="71af7-124">Description</span></span>
:------     | :-----
<span data-ttu-id="71af7-125">200</span><span class="sxs-lookup"><span data-stu-id="71af7-125">200</span></span> | <span data-ttu-id="71af7-126">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="71af7-126">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="71af7-127">4XX</span><span class="sxs-lookup"><span data-stu-id="71af7-127">4XX</span></span> | <span data-ttu-id="71af7-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="71af7-128">Error codes</span></span>
<span data-ttu-id="71af7-129">5XX</span><span class="sxs-lookup"><span data-stu-id="71af7-129">5XX</span></span> | <span data-ttu-id="71af7-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="71af7-130">Error codes</span></span>

## <a name="set-the-xbox-live-sandbox"></a><span data-ttu-id="71af7-131">Festlegen des Xbox Live-Sandkastens</span><span class="sxs-lookup"><span data-stu-id="71af7-131">Set the Xbox Live sandbox</span></span>
<span data-ttu-id="71af7-132">Mit der folgenden Anforderung können Sie den Xbox Live-Sandkasten des Geräts ändern.</span><span class="sxs-lookup"><span data-stu-id="71af7-132">You can change the Xbox Live sandbox for the device using the following request.</span></span> <span data-ttu-id="71af7-133">Bei der Xbox One muss das Gerät neu gestartet werden, damit die Einstellung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="71af7-133">Note that on Xbox One, the device needs to be restarted before the setting takes effect.</span></span>

**<span data-ttu-id="71af7-134">Anforderung</span><span class="sxs-lookup"><span data-stu-id="71af7-134">Request</span></span>**

<span data-ttu-id="71af7-135">Mit der folgenden Anforderung können Sie den aktuellen Wert für den Xbox Live-Sandkasten des Geräts festlegen:</span><span class="sxs-lookup"><span data-stu-id="71af7-135">You can set the current value for the device's Xbox Live sandbox using the following request:</span></span>

<span data-ttu-id="71af7-136">Methode</span><span class="sxs-lookup"><span data-stu-id="71af7-136">Method</span></span>      | <span data-ttu-id="71af7-137">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="71af7-137">Request URI</span></span>
:------     | :-----
<span data-ttu-id="71af7-138">PUT</span><span class="sxs-lookup"><span data-stu-id="71af7-138">PUT</span></span> | <span data-ttu-id="71af7-139">/ext/xboxlive/sandbox</span><span class="sxs-lookup"><span data-stu-id="71af7-139">/ext/xboxlive/sandbox</span></span>
<br />
**<span data-ttu-id="71af7-140">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="71af7-140">URI parameters</span></span>**

- <span data-ttu-id="71af7-141">Keine</span><span class="sxs-lookup"><span data-stu-id="71af7-141">None</span></span>

**<span data-ttu-id="71af7-142">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="71af7-142">Request headers</span></span>**

- <span data-ttu-id="71af7-143">Keine</span><span class="sxs-lookup"><span data-stu-id="71af7-143">None</span></span>

**<span data-ttu-id="71af7-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="71af7-144">Request body</span></span>**   
<span data-ttu-id="71af7-145">Der Anforderungstext ist ein JSON-Objekt mit dem folgenden Feld:</span><span class="sxs-lookup"><span data-stu-id="71af7-145">The request body is a JSON object containing the following field:</span></span>   
<span data-ttu-id="71af7-146">Sandbox (Zeichenfolge): Der neue Wert, auf den der Sandkasten des Geräts festgelegt werden soll.</span><span class="sxs-lookup"><span data-stu-id="71af7-146">Sandbox - (String) The new value to set the device's sandbox to.</span></span>

**<span data-ttu-id="71af7-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="71af7-147">Response</span></span>**   
<span data-ttu-id="71af7-148">Sandbox (Zeichenfolge): Der aktuelle Sandkasten, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="71af7-148">Sandbox - (String) The current Sandbox the device is in.</span></span>   

**<span data-ttu-id="71af7-149">Statuscode</span><span class="sxs-lookup"><span data-stu-id="71af7-149">Status code</span></span>**

<span data-ttu-id="71af7-150">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="71af7-150">This API has the following expected status codes.</span></span>

<span data-ttu-id="71af7-151">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="71af7-151">HTTP status code</span></span>      | <span data-ttu-id="71af7-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="71af7-152">Description</span></span>
:------     | :-----
<span data-ttu-id="71af7-153">200</span><span class="sxs-lookup"><span data-stu-id="71af7-153">200</span></span> | <span data-ttu-id="71af7-154">Die Anforderung für den Zugriff auf die Anmeldeinformationen für die Dateifreigabe wurde gewährt.</span><span class="sxs-lookup"><span data-stu-id="71af7-154">The request to access the credentials for the file share was granted.</span></span>
<span data-ttu-id="71af7-155">4XX</span><span class="sxs-lookup"><span data-stu-id="71af7-155">4XX</span></span> | <span data-ttu-id="71af7-156">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="71af7-156">Error codes</span></span>
<span data-ttu-id="71af7-157">5XX</span><span class="sxs-lookup"><span data-stu-id="71af7-157">5XX</span></span> | <span data-ttu-id="71af7-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="71af7-158">Error codes</span></span>

<br />
**<span data-ttu-id="71af7-159">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="71af7-159">Available device families</span></span>**

* <span data-ttu-id="71af7-160">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="71af7-160">Windows Xbox</span></span>

