---
title: Geräteportal – HTTP-Monitor-API-Referenz
description: Erfahren Sie mehr über den Zugriff von HTTP-Datenverkehr aus der fokussierten App auf einer Xbox.
ms.localizationpriority: medium
ms.openlocfilehash: 81de2a2a3194384e9c5de1c5c45a827e4d965c91
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8751929"
---
# <a name="http-monitor-api-reference"></a><span data-ttu-id="ac81b-103">HTTP-Monitor-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="ac81b-103">HTTP Monitor API reference</span></span>   
<span data-ttu-id="ac81b-104">Sie können mit dieser API auf Echtzeit-HTTP-Datenverkehr für die fokussierte App zugreifen, wenn der HTTP-Monitor auf der Xbox-Konsole aktiviert wurde, indem Sie das Kontrollkästchen in Dev Home aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ac81b-104">You can access real-time HTTP traffic for the focused app using this API if the HTTP monitor has been enabled on the Xbox console by checking the box in Dev Home.</span></span>

## <a name="get-if-the-http-monitor-is-enabled"></a><span data-ttu-id="ac81b-105">Abrufen, ob der HTTP-Monitor aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ac81b-105">Get if the HTTP Monitor is enabled</span></span>

**<span data-ttu-id="ac81b-106">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ac81b-106">Request</span></span>**

<span data-ttu-id="ac81b-107">Sie können abrufen, ob der HTTP-Monitor in Dev Home aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="ac81b-107">You can get whether the HTTP monitor has been enabled in Dev Home.</span></span>

<span data-ttu-id="ac81b-108">Methode</span><span class="sxs-lookup"><span data-stu-id="ac81b-108">Method</span></span>      | <span data-ttu-id="ac81b-109">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ac81b-109">Request URI</span></span>
:------     | :-----
<span data-ttu-id="ac81b-110">GET</span><span class="sxs-lookup"><span data-stu-id="ac81b-110">GET</span></span> | <span data-ttu-id="ac81b-111">/ext/httpmonitor/sessions</span><span class="sxs-lookup"><span data-stu-id="ac81b-111">/ext/httpmonitor/sessions</span></span>
<br />
**<span data-ttu-id="ac81b-112">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="ac81b-112">URI parameters</span></span>**

- <span data-ttu-id="ac81b-113">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-113">None</span></span>

**<span data-ttu-id="ac81b-114">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ac81b-114">Request headers</span></span>**

- <span data-ttu-id="ac81b-115">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-115">None</span></span>

**<span data-ttu-id="ac81b-116">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="ac81b-116">Request body</span></span>**

- <span data-ttu-id="ac81b-117">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-117">None</span></span>

**<span data-ttu-id="ac81b-118">Antwort</span><span class="sxs-lookup"><span data-stu-id="ac81b-118">Response</span></span>**   
<span data-ttu-id="ac81b-119">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="ac81b-119">A JSON object with the following fields:</span></span>

* <span data-ttu-id="ac81b-120">Aktiviert – (Bool) Ob der HTTP-Monitor auf der Xbox-Konsole aktiviert wurde, indem das Kontrollkästchen in Dev Home markiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ac81b-120">Enabled - (Bool) Whether the HTTP monitor has been enabled on the Xbox console by checking the box in Dev Home.</span></span>

**<span data-ttu-id="ac81b-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="ac81b-121">Status code</span></span>**

<span data-ttu-id="ac81b-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="ac81b-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="ac81b-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="ac81b-123">HTTP status code</span></span>      | <span data-ttu-id="ac81b-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac81b-124">Description</span></span>
:------     | :-----
<span data-ttu-id="ac81b-125">200</span><span class="sxs-lookup"><span data-stu-id="ac81b-125">200</span></span> | <span data-ttu-id="ac81b-126">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="ac81b-126">Request was successful</span></span>
<span data-ttu-id="ac81b-127">4XX</span><span class="sxs-lookup"><span data-stu-id="ac81b-127">4XX</span></span> | <span data-ttu-id="ac81b-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ac81b-128">Error codes</span></span>
<span data-ttu-id="ac81b-129">5XX</span><span class="sxs-lookup"><span data-stu-id="ac81b-129">5XX</span></span> | <span data-ttu-id="ac81b-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ac81b-130">Error codes</span></span>

## <a name="get-http-traffic-from-the-focused-app"></a><span data-ttu-id="ac81b-131">Abrufen des HTTP-Datenverkehr aus der fokussierten App</span><span class="sxs-lookup"><span data-stu-id="ac81b-131">Get HTTP traffic from the focused app</span></span>
**<span data-ttu-id="ac81b-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ac81b-132">Request</span></span>**

<span data-ttu-id="ac81b-133">Rufen Sie in Echtzeit HTTP-Datenverkehr von der fokussierten App auf der Xbox ab, sofern es keine System-App ist, wenn der HTTP-Monitor über Dev Home aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="ac81b-133">Get HTTP traffic from the focused app on the Xbox, as long as it is not a system app, in real-time, if the HTTP monitor has been enabled from Dev Home.</span></span>

<span data-ttu-id="ac81b-134">Methode</span><span class="sxs-lookup"><span data-stu-id="ac81b-134">Method</span></span>      | <span data-ttu-id="ac81b-135">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ac81b-135">Request URI</span></span>
:------     | :-----
<span data-ttu-id="ac81b-136">Websocket</span><span class="sxs-lookup"><span data-stu-id="ac81b-136">Websocket</span></span> | <span data-ttu-id="ac81b-137">/ext/httpmonitor/sessions</span><span class="sxs-lookup"><span data-stu-id="ac81b-137">/ext/httpmonitor/sessions</span></span>
<br />
**<span data-ttu-id="ac81b-138">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="ac81b-138">URI parameters</span></span>**

- <span data-ttu-id="ac81b-139">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-139">None</span></span>

**<span data-ttu-id="ac81b-140">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ac81b-140">Request headers</span></span>**

- <span data-ttu-id="ac81b-141">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-141">None</span></span>

**<span data-ttu-id="ac81b-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="ac81b-142">Request body</span></span>**

- <span data-ttu-id="ac81b-143">Keine</span><span class="sxs-lookup"><span data-stu-id="ac81b-143">None</span></span>

**<span data-ttu-id="ac81b-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="ac81b-144">Response</span></span>**   
<span data-ttu-id="ac81b-145">Ein JSON-Objekt mit den folgenden Feldern:</span><span class="sxs-lookup"><span data-stu-id="ac81b-145">A JSON object with the following fields:</span></span>

* <span data-ttu-id="ac81b-146">Sessions</span><span class="sxs-lookup"><span data-stu-id="ac81b-146">Sessions</span></span>
    * <span data-ttu-id="ac81b-147">RequestHeaders – (JSON-Objekt) Die Anforderungsheader aus der HTTP-Anforderung.</span><span class="sxs-lookup"><span data-stu-id="ac81b-147">RequestHeaders - (JSON Object) The request headers from the HTTP Request.</span></span>
    * <span data-ttu-id="ac81b-148">RequestContentHeaders – (JSON-Objekt) Die Anforderungsinhaltsheader aus der HTTP-Anforderung.</span><span class="sxs-lookup"><span data-stu-id="ac81b-148">RequestContentHeaders - (JSON Object) The request content headers from the HTTP Request.</span></span>
    * <span data-ttu-id="ac81b-149">RequestURL - (Zeichenfolge) Die Anforderungs-URL.</span><span class="sxs-lookup"><span data-stu-id="ac81b-149">RequestURL - (String) The request URL.</span></span>
    * <span data-ttu-id="ac81b-150">RequestMethod – (Zeichenfolge) Die Anforderungsmethode.</span><span class="sxs-lookup"><span data-stu-id="ac81b-150">RequestMethod - (String) The request method.</span></span>
    * <span data-ttu-id="ac81b-151">RequestMessage – (Zeichenfolge) Die Anforderungsnachricht, unterstützt derzeit nur JSON- und Textinhalt.</span><span class="sxs-lookup"><span data-stu-id="ac81b-151">RequestMessage - (String) The request message, currently only supporting JSON and text content.</span></span>
    * <span data-ttu-id="ac81b-152">ResponseHeaders – (JSON-Objekt) Die Antwortheader der HTTP-Antwort.</span><span class="sxs-lookup"><span data-stu-id="ac81b-152">ResponseHeaders - (JSON Object) The response headers from the HTTP Response.</span></span>
    * <span data-ttu-id="ac81b-153">ResponseContentHeaders – (JSON-Objekt) Die Antwortinhaltsheader der HTTP-Antwort.</span><span class="sxs-lookup"><span data-stu-id="ac81b-153">ResponseContentHeaders - (JSON Object) The response content headers from the HTTP Response.</span></span>
    * <span data-ttu-id="ac81b-154">StatusCode – (Zahl) Der Antwortstatuscode.</span><span class="sxs-lookup"><span data-stu-id="ac81b-154">StatusCode - (Number) The response status code.</span></span>
    * <span data-ttu-id="ac81b-155">ReasponsePhrase – (Zeichenfolge) Der Antwortgrundausdruck.</span><span class="sxs-lookup"><span data-stu-id="ac81b-155">ReasponsePhrase - (String) The response reason phrase.</span></span>
    * <span data-ttu-id="ac81b-156">ResponseMessage – (Zeichenfolge) Die Antwortnachricht, unterstützt derzeit nur JSON- und Textinhalt.</span><span class="sxs-lookup"><span data-stu-id="ac81b-156">ResponseMessage - (String) The response message, currently only supporting JSON and text content.</span></span>

**<span data-ttu-id="ac81b-157">Statuscode</span><span class="sxs-lookup"><span data-stu-id="ac81b-157">Status code</span></span>**

<span data-ttu-id="ac81b-158">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="ac81b-158">This API has the following expected status codes.</span></span>

<span data-ttu-id="ac81b-159">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="ac81b-159">HTTP status code</span></span>      | <span data-ttu-id="ac81b-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ac81b-160">Description</span></span>
:------     | :-----
<span data-ttu-id="ac81b-161">200</span><span class="sxs-lookup"><span data-stu-id="ac81b-161">200</span></span> | <span data-ttu-id="ac81b-162">Die Anforderung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="ac81b-162">Request was successful</span></span>
<span data-ttu-id="ac81b-163">4XX</span><span class="sxs-lookup"><span data-stu-id="ac81b-163">4XX</span></span> | <span data-ttu-id="ac81b-164">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ac81b-164">Error codes</span></span>
<span data-ttu-id="ac81b-165">403</span><span class="sxs-lookup"><span data-stu-id="ac81b-165">403</span></span> | <span data-ttu-id="ac81b-166">HTTP-Monitor ist deaktiviert, muss in Dev Home aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="ac81b-166">HTTP Monitor disabled, must be enabled in Dev Home</span></span>
<span data-ttu-id="ac81b-167">5XX</span><span class="sxs-lookup"><span data-stu-id="ac81b-167">5XX</span></span> | <span data-ttu-id="ac81b-168">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ac81b-168">Error codes</span></span>

<br />
**<span data-ttu-id="ac81b-169">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="ac81b-169">Available device families</span></span>**

* <span data-ttu-id="ac81b-170">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="ac81b-170">Windows Xbox</span></span>