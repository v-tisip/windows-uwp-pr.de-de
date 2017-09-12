---
author: PatrickFarley
ms.assetid: 41ac0142-4d86-4bb3-b580-36d0d6956091
title: "Referenz zu Geräteportal-APIs für HoloLens"
description: "Hier erhalten Sie Informationen zu den HoloLens-REST-APIs für das Windows Device Portal, die Sie für den Zugriff auf die Daten und die programmatische Steuerung des Geräts verwenden können."
ms.openlocfilehash: 3c000bc19c0bd45050e5be1ca73e5dc7b73d8103
ms.sourcegitcommit: e8cc657d85566768a6efb7cd972ebf64c25e0628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2017
---
# <a name="device-portal-api-reference-for-hololens"></a><span data-ttu-id="358bc-103">Referenz zu Geräteportal-APIs für HoloLens</span><span class="sxs-lookup"><span data-stu-id="358bc-103">Device Portal API reference for HoloLens</span></span>

<span data-ttu-id="358bc-104">Alle Komponenten im Windows Device Portal basieren auf REST-APIs, die Sie für den Zugriff auf die Daten und die programmatische Steuerung des Geräts verwenden können.</span><span class="sxs-lookup"><span data-stu-id="358bc-104">Everything in the Windows Device Portal is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="holographic-os"></a><span data-ttu-id="358bc-105">Holographic – Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="358bc-105">Holographic OS</span></span>
---
### <a name="get-https-requirements-for-the-device-portal"></a><span data-ttu-id="358bc-106">Abrufen der HTTPS-Anforderungen für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="358bc-106">Get HTTPS requirements for the Device Portal</span></span>

**<span data-ttu-id="358bc-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-107">Request</span></span>**

<span data-ttu-id="358bc-108">Mit dem folgenden Anforderungsformat können Sie die HTTPS-Anforderungen für das Geräteportal abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-108">You can get the HTTPS requirements for the Device Portal by using the following request format.</span></span>
 
<span data-ttu-id="358bc-109">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-109">Method</span></span>      | <span data-ttu-id="358bc-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-111">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-111">GET</span></span> | <span data-ttu-id="358bc-112">/api/holographic/os/webmanagement/settings/https</span><span class="sxs-lookup"><span data-stu-id="358bc-112">/api/holographic/os/webmanagement/settings/https</span></span>


**<span data-ttu-id="358bc-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-113">URI parameters</span></span>**

- <span data-ttu-id="358bc-114">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-114">None</span></span>

**<span data-ttu-id="358bc-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-115">Request headers</span></span>**

- <span data-ttu-id="358bc-116">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-116">None</span></span>

**<span data-ttu-id="358bc-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-117">Request body</span></span>**

- <span data-ttu-id="358bc-118">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-118">None</span></span>

**<span data-ttu-id="358bc-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-119">Response</span></span>**

- <span data-ttu-id="358bc-120">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-120">None</span></span>

**<span data-ttu-id="358bc-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-121">Status code</span></span>**

- <span data-ttu-id="358bc-122">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-122">Standard status codes.</span></span>

---
### <a name="get-the-stored-interpupillary-distance-ipd"></a><span data-ttu-id="358bc-123">Abrufen des gespeicherten Pupillenabstands (Interpupillary Distance, IPD)</span><span class="sxs-lookup"><span data-stu-id="358bc-123">Get the stored interpupillary distance (IPD)</span></span>

**<span data-ttu-id="358bc-124">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-124">Request</span></span>**

<span data-ttu-id="358bc-125">Mit dem folgenden Anforderungsformat können Sie den gespeicherten IPD-Wert abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-125">You can get the stored IPD value by using the following request format.</span></span> <span data-ttu-id="358bc-126">Der Wert wird in Millimeter zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="358bc-126">The value is returned in millimeters.</span></span>
 
<span data-ttu-id="358bc-127">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-127">Method</span></span>      | <span data-ttu-id="358bc-128">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-128">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-129">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-129">GET</span></span> | <span data-ttu-id="358bc-130">/api/holographic/os/settings/ipd</span><span class="sxs-lookup"><span data-stu-id="358bc-130">/api/holographic/os/settings/ipd</span></span>


**<span data-ttu-id="358bc-131">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-131">URI parameters</span></span>**

- <span data-ttu-id="358bc-132">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-132">None</span></span>

**<span data-ttu-id="358bc-133">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-133">Request headers</span></span>**

- <span data-ttu-id="358bc-134">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-134">None</span></span>

**<span data-ttu-id="358bc-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-135">Request body</span></span>**

- <span data-ttu-id="358bc-136">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-136">None</span></span>

**<span data-ttu-id="358bc-137">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-137">Response</span></span>**

- <span data-ttu-id="358bc-138">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-138">None</span></span>

**<span data-ttu-id="358bc-139">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-139">Status code</span></span>**

- <span data-ttu-id="358bc-140">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-140">Standard status codes.</span></span>

---
### <a name="get-a-list-of-hololens-specific-etw-providers"></a><span data-ttu-id="358bc-141">Abrufen einer Liste mit ETW-Anbietern für HoloLens</span><span class="sxs-lookup"><span data-stu-id="358bc-141">Get a list of HoloLens specific ETW providers</span></span>

**<span data-ttu-id="358bc-142">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-142">Request</span></span>**

<span data-ttu-id="358bc-143">Mit dem folgenden Anforderungsformat können Sie eine Liste mit ETW-Anbietern für HoloLens abrufen, die nicht im System registriert sind.</span><span class="sxs-lookup"><span data-stu-id="358bc-143">You can get a list of HoloLens specific ETW providers that are not registered with the system by using the following request format.</span></span>
 
<span data-ttu-id="358bc-144">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-144">Method</span></span>      | <span data-ttu-id="358bc-145">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-145">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-146">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-146">GET</span></span> | <span data-ttu-id="358bc-147">/api/holographic/os/etw/customproviders</span><span class="sxs-lookup"><span data-stu-id="358bc-147">/api/holographic/os/etw/customproviders</span></span>


**<span data-ttu-id="358bc-148">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-148">URI parameters</span></span>**

- <span data-ttu-id="358bc-149">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-149">None</span></span>

**<span data-ttu-id="358bc-150">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-150">Request headers</span></span>**

- <span data-ttu-id="358bc-151">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-151">None</span></span>

**<span data-ttu-id="358bc-152">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-152">Request body</span></span>**

- <span data-ttu-id="358bc-153">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-153">None</span></span>

**<span data-ttu-id="358bc-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-154">Response</span></span>**

- <span data-ttu-id="358bc-155">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-155">None</span></span>

**<span data-ttu-id="358bc-156">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-156">Status code</span></span>**

- <span data-ttu-id="358bc-157">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-157">Standard status codes.</span></span>

---
### <a name="return-the-state-for-all-active-services"></a><span data-ttu-id="358bc-158">Gibt den Status für alle aktiven Dienste zurück.</span><span class="sxs-lookup"><span data-stu-id="358bc-158">Return the state for all active services</span></span>

**<span data-ttu-id="358bc-159">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-159">Request</span></span>**

<span data-ttu-id="358bc-160">Mit dem folgenden Anforderungsformat können Sie den Status aller Dienste abrufen, die derzeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="358bc-160">You can get the state of all services that are currently running by using the following request format.</span></span>
 
<span data-ttu-id="358bc-161">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-161">Method</span></span>      | <span data-ttu-id="358bc-162">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-162">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-163">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-163">GET</span></span> | <span data-ttu-id="358bc-164">/api/holographic/os/services</span><span class="sxs-lookup"><span data-stu-id="358bc-164">/api/holographic/os/services</span></span>


**<span data-ttu-id="358bc-165">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-165">URI parameters</span></span>**

- <span data-ttu-id="358bc-166">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-166">None</span></span>

**<span data-ttu-id="358bc-167">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-167">Request headers</span></span>**

- <span data-ttu-id="358bc-168">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-168">None</span></span>

**<span data-ttu-id="358bc-169">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-169">Request body</span></span>**

- <span data-ttu-id="358bc-170">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-170">None</span></span>

**<span data-ttu-id="358bc-171">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-171">Response</span></span>**

- <span data-ttu-id="358bc-172">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-172">None</span></span>

**<span data-ttu-id="358bc-173">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-173">Status code</span></span>**

- <span data-ttu-id="358bc-174">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-174">Standard status codes.</span></span>

---
### <a name="set-the-https-requirement-for-the-device-portal"></a><span data-ttu-id="358bc-175">Festlegen der HTTPS-Anforderung für das Geräteportal</span><span class="sxs-lookup"><span data-stu-id="358bc-175">Set the HTTPS requirement for the Device Portal.</span></span>

**<span data-ttu-id="358bc-176">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-176">Request</span></span>**

<span data-ttu-id="358bc-177">Mit dem folgenden Anforderungsformat können Sie die HTTPS-Anforderungen für das Geräteportal festlegen.</span><span class="sxs-lookup"><span data-stu-id="358bc-177">You can set the HTTPS requirements for the Device Portal by using the following request format.</span></span>
 
<span data-ttu-id="358bc-178">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-178">Method</span></span>      | <span data-ttu-id="358bc-179">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-179">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-180">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-180">POST</span></span> | <span data-ttu-id="358bc-181">/api/holographic/management/settings/https</span><span class="sxs-lookup"><span data-stu-id="358bc-181">/api/holographic/management/settings/https</span></span>


**<span data-ttu-id="358bc-182">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-182">URI parameters</span></span>**

<span data-ttu-id="358bc-183">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-183">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-184">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-184">URI parameter</span></span> | <span data-ttu-id="358bc-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-185">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-186">required</span><span class="sxs-lookup"><span data-stu-id="358bc-186">required</span></span>   | <span data-ttu-id="358bc-187">(**Erforderlich**) Bestimmt, ob für das Geräteportal HTTPS erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="358bc-187">(**required**) Determines whether or not HTTPS is required for the Device Portal.</span></span> <span data-ttu-id="358bc-188">Die möglichen Werte lauten **yes**, **no** und **default**.</span><span class="sxs-lookup"><span data-stu-id="358bc-188">Possible values are **yes**, **no**, and **default**.</span></span>

**<span data-ttu-id="358bc-189">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-189">Request headers</span></span>**

- <span data-ttu-id="358bc-190">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-190">None</span></span>

**<span data-ttu-id="358bc-191">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-191">Request body</span></span>**

- <span data-ttu-id="358bc-192">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-192">None</span></span>

**<span data-ttu-id="358bc-193">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-193">Response</span></span>**

- <span data-ttu-id="358bc-194">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-194">None</span></span>

**<span data-ttu-id="358bc-195">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-195">Status code</span></span>**

- <span data-ttu-id="358bc-196">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-196">Standard status codes.</span></span>

---
### <a name="set-the-interpupillary-distance-ipd"></a><span data-ttu-id="358bc-197">Festlegen des Pupillenabstands (Interpupillary Distance, IPD)</span><span class="sxs-lookup"><span data-stu-id="358bc-197">Set the interpupillary distance (IPD)</span></span>

**<span data-ttu-id="358bc-198">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-198">Request</span></span>**

<span data-ttu-id="358bc-199">Mit dem folgenden Anforderungsformat können Sie den gespeicherten IPD-Wert festlegen.</span><span class="sxs-lookup"><span data-stu-id="358bc-199">You can set the stored IPD by using the following request format.</span></span>
 
<span data-ttu-id="358bc-200">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-200">Method</span></span>      | <span data-ttu-id="358bc-201">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-201">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-202">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-202">POST</span></span> | <span data-ttu-id="358bc-203">/api/holographic/os/settings/ipd</span><span class="sxs-lookup"><span data-stu-id="358bc-203">/api/holographic/os/settings/ipd</span></span>


**<span data-ttu-id="358bc-204">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-204">URI parameters</span></span>**

<span data-ttu-id="358bc-205">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-205">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-206">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-206">URI parameter</span></span> | <span data-ttu-id="358bc-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-207">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-208">ipd</span><span class="sxs-lookup"><span data-stu-id="358bc-208">ipd</span></span>   | <span data-ttu-id="358bc-209">(**erforderlich**) Der neue IPD-Wert, der gespeichert werden soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-209">(**required**) The new IPD value to be stored.</span></span> <span data-ttu-id="358bc-210">Dieser Wert sollte in Millimeter angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="358bc-210">This value should be in millimeters.</span></span>

**<span data-ttu-id="358bc-211">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-211">Request headers</span></span>**

- <span data-ttu-id="358bc-212">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-212">None</span></span>

**<span data-ttu-id="358bc-213">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-213">Request body</span></span>**

- <span data-ttu-id="358bc-214">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-214">None</span></span>

**<span data-ttu-id="358bc-215">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-215">Response</span></span>**

- <span data-ttu-id="358bc-216">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-216">None</span></span>

**<span data-ttu-id="358bc-217">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-217">Status code</span></span>**

- <span data-ttu-id="358bc-218">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-218">Standard status codes.</span></span>

---
## Holographic perception
---
### <a name="accept-websocket-upgrades-and-run-a-mirage-client-that-sends-updates"></a><span data-ttu-id="358bc-219">Akzeptieren von WebSocket-Upgrades und Ausführen eines Mirage-Clients, der Updates sendet</span><span class="sxs-lookup"><span data-stu-id="358bc-219">Accept websocket upgrades and run a mirage client that sends updates</span></span>

**<span data-ttu-id="358bc-220">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-220">Request</span></span>**

<span data-ttu-id="358bc-221">Mit dem folgenden Anforderungsformat können Sie WebSocket-Upgrades akzeptieren und einen Mirage-Client ausführen, der Updates mit 30 fps sendet.</span><span class="sxs-lookup"><span data-stu-id="358bc-221">You can accept websocket upgrades and run a mirage client that sends updates at 30 fps by using the following request format.</span></span>
 
<span data-ttu-id="358bc-222">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-222">Method</span></span>      | <span data-ttu-id="358bc-223">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-223">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-224">GET/WebSocket</span><span class="sxs-lookup"><span data-stu-id="358bc-224">GET/WebSocket</span></span> | <span data-ttu-id="358bc-225">/api/holographic/perception/client</span><span class="sxs-lookup"><span data-stu-id="358bc-225">/api/holographic/perception/client</span></span>


**<span data-ttu-id="358bc-226">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-226">URI parameters</span></span>**

<span data-ttu-id="358bc-227">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-227">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-228">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-228">URI parameter</span></span> | <span data-ttu-id="358bc-229">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-229">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-230">clientmode</span><span class="sxs-lookup"><span data-stu-id="358bc-230">clientmode</span></span>   | <span data-ttu-id="358bc-231">(**erforderlich**) Bestimmt den Nachverfolgungsmodus.</span><span class="sxs-lookup"><span data-stu-id="358bc-231">(**required**) Determines the tracking mode.</span></span> <span data-ttu-id="358bc-232">Mit dem Wert **active** wird der visuelle Nachverfolgungsmodus erzwungen, wenn er nicht passiv erreicht werden kann.</span><span class="sxs-lookup"><span data-stu-id="358bc-232">A value of **active** forces visual tracking mode when it can't be established passively.</span></span>

**<span data-ttu-id="358bc-233">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-233">Request headers</span></span>**

- <span data-ttu-id="358bc-234">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-234">None</span></span>

**<span data-ttu-id="358bc-235">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-235">Request body</span></span>**

- <span data-ttu-id="358bc-236">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-236">None</span></span>

**<span data-ttu-id="358bc-237">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-237">Response</span></span>**

- <span data-ttu-id="358bc-238">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-238">None</span></span>

**<span data-ttu-id="358bc-239">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-239">Status code</span></span>**

- <span data-ttu-id="358bc-240">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-240">Standard status codes.</span></span>

---
## Holographic thermal
---
### <a name="get-the-thermal-stage-of-the-device"></a><span data-ttu-id="358bc-241">Abrufen des Wärmestatus des Geräts</span><span class="sxs-lookup"><span data-stu-id="358bc-241">Get the thermal stage of the device</span></span>

**<span data-ttu-id="358bc-242">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-242">Request</span></span>**

<span data-ttu-id="358bc-243">Mit dem folgenden Anforderungsformat können Sie den Wärmestatus des Geräts abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-243">You can get the thermal stage of the device by using the following request format.</span></span>
 
<span data-ttu-id="358bc-244">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-244">Method</span></span>      | <span data-ttu-id="358bc-245">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-245">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-246">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-246">GET</span></span> | <span data-ttu-id="358bc-247">/api/holographic/</span><span class="sxs-lookup"><span data-stu-id="358bc-247">/api/holographic/</span></span>

**<span data-ttu-id="358bc-248">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-248">URI parameters</span></span>**

- <span data-ttu-id="358bc-249">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-249">None</span></span>

**<span data-ttu-id="358bc-250">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-250">Request headers</span></span>**

- <span data-ttu-id="358bc-251">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-251">None</span></span>

**<span data-ttu-id="358bc-252">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-252">Request body</span></span>**

- <span data-ttu-id="358bc-253">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-253">None</span></span>

**<span data-ttu-id="358bc-254">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-254">Response</span></span>**

<span data-ttu-id="358bc-255">In der folgenden Tabelle werden die möglichen Werte angegeben.</span><span class="sxs-lookup"><span data-stu-id="358bc-255">The possible values are indicated by the following table.</span></span>

<span data-ttu-id="358bc-256">Wert</span><span class="sxs-lookup"><span data-stu-id="358bc-256">Value</span></span> | <span data-ttu-id="358bc-257">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-257">Description</span></span>
--- | ---
<span data-ttu-id="358bc-258">1</span><span class="sxs-lookup"><span data-stu-id="358bc-258">1</span></span> | <span data-ttu-id="358bc-259">Normal</span><span class="sxs-lookup"><span data-stu-id="358bc-259">Normal</span></span>
<span data-ttu-id="358bc-260">2</span><span class="sxs-lookup"><span data-stu-id="358bc-260">2</span></span> | <span data-ttu-id="358bc-261">Warm</span><span class="sxs-lookup"><span data-stu-id="358bc-261">Warm</span></span>
<span data-ttu-id="358bc-262">3</span><span class="sxs-lookup"><span data-stu-id="358bc-262">3</span></span> | <span data-ttu-id="358bc-263">Kritisch</span><span class="sxs-lookup"><span data-stu-id="358bc-263">Critical</span></span>

**<span data-ttu-id="358bc-264">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-264">Status code</span></span>**

- <span data-ttu-id="358bc-265">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-265">Standard status codes.</span></span>

---
## HSimulation control
---
### <a name="create-a-control-stream-or-post-data-to-a-created-stream"></a><span data-ttu-id="358bc-266">Erstellen eines Steuerungsdatenstroms oder Senden von Daten an einen erstellten Datenstrom</span><span class="sxs-lookup"><span data-stu-id="358bc-266">Create a control stream or post data to a created stream</span></span>

**<span data-ttu-id="358bc-267">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-267">Request</span></span>**

<span data-ttu-id="358bc-268">Mit dem folgenden Anforderungsformat können Sie einen Steuerungsdatenstrom erstellen oder Daten an einen erstellten Datenstrom senden.</span><span class="sxs-lookup"><span data-stu-id="358bc-268">You can create a control stream or post data to a created stream by using the following request format.</span></span> <span data-ttu-id="358bc-269">Die gesendeten Daten müssen vom Typ **application/octet-stream** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-269">The posted data is expected to be of type **application/octet-stream**.</span></span>
 
<span data-ttu-id="358bc-270">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-270">Method</span></span>      | <span data-ttu-id="358bc-271">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-271">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-272">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-272">POST</span></span> | <span data-ttu-id="358bc-273">/api/holographic/simulation/control/stream</span><span class="sxs-lookup"><span data-stu-id="358bc-273">/api/holographic/simulation/control/stream</span></span>


**<span data-ttu-id="358bc-274">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-274">URI parameters</span></span>**

<span data-ttu-id="358bc-275">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-275">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-276">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-276">URI parameter</span></span> | <span data-ttu-id="358bc-277">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-277">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-278">priority</span><span class="sxs-lookup"><span data-stu-id="358bc-278">priority</span></span>   | <span data-ttu-id="358bc-279">(**erforderlich, wenn ein Steuerungsdatenstrom erstellt wird**) Gibt die Priorität des Datenstroms an.</span><span class="sxs-lookup"><span data-stu-id="358bc-279">(**required if creating a control stream**) Indicates the priority of the stream.</span></span>
<span data-ttu-id="358bc-280">streamid</span><span class="sxs-lookup"><span data-stu-id="358bc-280">streamid</span></span>   | <span data-ttu-id="358bc-281">(**erforderlich, wenn an einen erstellten Datenstrom gesendet wird**) Der Bezeichner für den Datenstrom, an den gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-281">(**required if posting to a created stream**) The identifier for the stream to post to.</span></span>

**<span data-ttu-id="358bc-282">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-282">Request headers</span></span>**

- <span data-ttu-id="358bc-283">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-283">None</span></span>

**<span data-ttu-id="358bc-284">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-284">Request body</span></span>**

- <span data-ttu-id="358bc-285">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-285">None</span></span>

**<span data-ttu-id="358bc-286">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-286">Response</span></span>**

- <span data-ttu-id="358bc-287">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-287">None</span></span>

**<span data-ttu-id="358bc-288">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-288">Status code</span></span>**

- <span data-ttu-id="358bc-289">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-289">Standard status codes.</span></span>

---
### <a name="delete-a-control-stream"></a><span data-ttu-id="358bc-290">Löschen eines Steuerungsdatenstroms</span><span class="sxs-lookup"><span data-stu-id="358bc-290">Delete a control stream</span></span>

**<span data-ttu-id="358bc-291">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-291">Request</span></span>**

<span data-ttu-id="358bc-292">Mit dem folgenden Anforderungsformat können Sie einen Steuerungsdatenstrom löschen.</span><span class="sxs-lookup"><span data-stu-id="358bc-292">You can delete a control stream by using the following request format.</span></span>
 
<span data-ttu-id="358bc-293">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-293">Method</span></span>      | <span data-ttu-id="358bc-294">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-294">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-295">DELETE</span><span class="sxs-lookup"><span data-stu-id="358bc-295">DELETE</span></span> | <span data-ttu-id="358bc-296">/api/holographic/simulation/control/stream</span><span class="sxs-lookup"><span data-stu-id="358bc-296">/api/holographic/simulation/control/stream</span></span>


**<span data-ttu-id="358bc-297">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-297">URI parameters</span></span>**

- <span data-ttu-id="358bc-298">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-298">None</span></span>

**<span data-ttu-id="358bc-299">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-299">Request headers</span></span>**

- <span data-ttu-id="358bc-300">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-300">None</span></span>

**<span data-ttu-id="358bc-301">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-301">Request body</span></span>**

- <span data-ttu-id="358bc-302">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-302">None</span></span>

**<span data-ttu-id="358bc-303">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-303">Response</span></span>**

- <span data-ttu-id="358bc-304">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-304">None</span></span>

**<span data-ttu-id="358bc-305">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-305">Status code</span></span>**

- <span data-ttu-id="358bc-306">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-306">Standard status codes.</span></span>

---
### <a name="get-a-control-stream"></a><span data-ttu-id="358bc-307">Abrufen eines Steuerungsdatenstroms.</span><span class="sxs-lookup"><span data-stu-id="358bc-307">Get a control stream</span></span>

**<span data-ttu-id="358bc-308">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-308">Request</span></span>**

<span data-ttu-id="358bc-309">Mit dem folgenden Anforderungsformat können Sie eine WebSocket-Verbindung für einen Steuerungsdatenstrom öffnen.</span><span class="sxs-lookup"><span data-stu-id="358bc-309">You can open a web socket connection for a control stream by using the following request format.</span></span>
 
<span data-ttu-id="358bc-310">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-310">Method</span></span>      | <span data-ttu-id="358bc-311">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-311">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-312">GET/WebSocket</span><span class="sxs-lookup"><span data-stu-id="358bc-312">GET/WebSocket</span></span> | <span data-ttu-id="358bc-313">/api/holographic/simulation/control/stream</span><span class="sxs-lookup"><span data-stu-id="358bc-313">/api/holographic/simulation/control/stream</span></span>


**<span data-ttu-id="358bc-314">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-314">URI parameters</span></span>**

- <span data-ttu-id="358bc-315">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-315">None</span></span>

**<span data-ttu-id="358bc-316">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-316">Request headers</span></span>**

- <span data-ttu-id="358bc-317">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-317">None</span></span>

**<span data-ttu-id="358bc-318">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-318">Request body</span></span>**

- <span data-ttu-id="358bc-319">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-319">None</span></span>

**<span data-ttu-id="358bc-320">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-320">Response</span></span>**

- <span data-ttu-id="358bc-321">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-321">None</span></span>

**<span data-ttu-id="358bc-322">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-322">Status code</span></span>**

- <span data-ttu-id="358bc-323">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-323">Standard status codes.</span></span>

---
### <a name="get-the-simluation-mode"></a><span data-ttu-id="358bc-324">Abrufen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="358bc-324">Get the simluation mode</span></span>

**<span data-ttu-id="358bc-325">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-325">Request</span></span>**

<span data-ttu-id="358bc-326">Mit dem folgenden Anforderungsformat können Sie den Simulationsmodus abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-326">You can get the simluation mode by using the following request format.</span></span>
 
<span data-ttu-id="358bc-327">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-327">Method</span></span>      | <span data-ttu-id="358bc-328">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-328">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-329">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-329">GET</span></span> | <span data-ttu-id="358bc-330">/api/holographic/simulation/control/mode</span><span class="sxs-lookup"><span data-stu-id="358bc-330">/api/holographic/simulation/control/mode</span></span>


**<span data-ttu-id="358bc-331">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-331">URI parameters</span></span>**

- <span data-ttu-id="358bc-332">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-332">None</span></span>

**<span data-ttu-id="358bc-333">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-333">Request headers</span></span>**

- <span data-ttu-id="358bc-334">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-334">None</span></span>

**<span data-ttu-id="358bc-335">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-335">Request body</span></span>**

- <span data-ttu-id="358bc-336">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-336">None</span></span>

**<span data-ttu-id="358bc-337">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-337">Response</span></span>**

- <span data-ttu-id="358bc-338">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-338">None</span></span>

**<span data-ttu-id="358bc-339">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-339">Status code</span></span>**

- <span data-ttu-id="358bc-340">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-340">Standard status codes.</span></span>

---
### <a name="set-the-simluation-mode"></a><span data-ttu-id="358bc-341">Festlegen des Simulationsmodus</span><span class="sxs-lookup"><span data-stu-id="358bc-341">Set the simluation mode</span></span>

**<span data-ttu-id="358bc-342">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-342">Request</span></span>**

<span data-ttu-id="358bc-343">Mit dem folgenden Anforderungsformat können Sie den Simulationsmodus festlegen.</span><span class="sxs-lookup"><span data-stu-id="358bc-343">You can set the simulation mode by using the following request format.</span></span>
 
<span data-ttu-id="358bc-344">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-344">Method</span></span>      | <span data-ttu-id="358bc-345">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-345">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-346">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-346">POST</span></span> | <span data-ttu-id="358bc-347">/api/holographic/simluation/control/mode</span><span class="sxs-lookup"><span data-stu-id="358bc-347">/api/holographic/simluation/control/mode</span></span>


**<span data-ttu-id="358bc-348">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-348">URI parameters</span></span>**

<span data-ttu-id="358bc-349">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-349">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-350">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-350">URI parameter</span></span> | <span data-ttu-id="358bc-351">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-351">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-352">mode</span><span class="sxs-lookup"><span data-stu-id="358bc-352">mode</span></span>   | <span data-ttu-id="358bc-353">(**erforderlich**) Gibt den Simulationsmodus an.</span><span class="sxs-lookup"><span data-stu-id="358bc-353">(**required**) Indicates the simulation mode.</span></span> <span data-ttu-id="358bc-354">Die möglichen Werte lauten **default**, **simulation**, **remote** und **legacy**.</span><span class="sxs-lookup"><span data-stu-id="358bc-354">Possible values include **default**, **simulation**, **remote**, and **legacy**.</span></span>

**<span data-ttu-id="358bc-355">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-355">Request headers</span></span>**

- <span data-ttu-id="358bc-356">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-356">None</span></span>

**<span data-ttu-id="358bc-357">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-357">Request body</span></span>**

- <span data-ttu-id="358bc-358">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-358">None</span></span>

**<span data-ttu-id="358bc-359">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-359">Response</span></span>**

- <span data-ttu-id="358bc-360">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-360">None</span></span>

**<span data-ttu-id="358bc-361">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-361">Status code</span></span>**

- <span data-ttu-id="358bc-362">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-362">Standard status codes.</span></span>

---
## HSimulation playback
---
### <a name="delete-a-recording"></a><span data-ttu-id="358bc-363">Löschen einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-363">Delete a recording</span></span>

**<span data-ttu-id="358bc-364">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-364">Request</span></span>**

<span data-ttu-id="358bc-365">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung löschen.</span><span class="sxs-lookup"><span data-stu-id="358bc-365">You can delete a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-366">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-366">Method</span></span>      | <span data-ttu-id="358bc-367">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-367">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-368">DELETE</span><span class="sxs-lookup"><span data-stu-id="358bc-368">DELETE</span></span> | <span data-ttu-id="358bc-369">/api/holographic/simulation/playback/file</span><span class="sxs-lookup"><span data-stu-id="358bc-369">/api/holographic/simulation/playback/file</span></span>


**<span data-ttu-id="358bc-370">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-370">URI parameters</span></span>**

<span data-ttu-id="358bc-371">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-371">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-372">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-372">URI parameter</span></span> | <span data-ttu-id="358bc-373">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-373">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-374">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-374">recording</span></span>   | <span data-ttu-id="358bc-375">(**erforderlich**) Der Name der zu löschenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-375">(**required**) The name of the recording to delete.</span></span>

**<span data-ttu-id="358bc-376">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-376">Request headers</span></span>**

- <span data-ttu-id="358bc-377">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-377">None</span></span>

**<span data-ttu-id="358bc-378">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-378">Request body</span></span>**

- <span data-ttu-id="358bc-379">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-379">None</span></span>

**<span data-ttu-id="358bc-380">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-380">Response</span></span>**

- <span data-ttu-id="358bc-381">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-381">None</span></span>

**<span data-ttu-id="358bc-382">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-382">Status code</span></span>**

- <span data-ttu-id="358bc-383">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-383">Standard status codes.</span></span>

---
### <a name="get-all-recordings"></a><span data-ttu-id="358bc-384">Abrufen aller Aufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="358bc-384">Get all recordings</span></span>

**<span data-ttu-id="358bc-385">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-385">Request</span></span>**

<span data-ttu-id="358bc-386">Mit dem folgenden Anforderungsformat können Sie alle verfügbaren Aufzeichnungen abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-386">You can get all the available recordings by using the following request format.</span></span>
 
<span data-ttu-id="358bc-387">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-387">Method</span></span>      | <span data-ttu-id="358bc-388">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-388">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-389">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-389">GET</span></span> | <span data-ttu-id="358bc-390">/api/holographic/simulation/playback/files</span><span class="sxs-lookup"><span data-stu-id="358bc-390">/api/holographic/simulation/playback/files</span></span>


**<span data-ttu-id="358bc-391">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-391">URI parameters</span></span>**

- <span data-ttu-id="358bc-392">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-392">None</span></span>

**<span data-ttu-id="358bc-393">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-393">Request headers</span></span>**

- <span data-ttu-id="358bc-394">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-394">None</span></span>

**<span data-ttu-id="358bc-395">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-395">Request body</span></span>**

- <span data-ttu-id="358bc-396">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-396">None</span></span>

**<span data-ttu-id="358bc-397">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-397">Response</span></span>**

- <span data-ttu-id="358bc-398">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-398">None</span></span>

**<span data-ttu-id="358bc-399">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-399">Status code</span></span>**

- <span data-ttu-id="358bc-400">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-400">Standard status codes.</span></span>

---
### <a name="get-the-types-of-data-in-a-loaded-recording"></a><span data-ttu-id="358bc-401">Abrufen der Typen von Daten in einer geladenen Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-401">Get the types of data in a loaded recording</span></span>

**<span data-ttu-id="358bc-402">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-402">Request</span></span>**

<span data-ttu-id="358bc-403">Mit dem folgenden Anforderungsformat können Sie die Typen der Daten in einer geladenen Aufzeichnung abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-403">You can get the types of data in a loaded recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-404">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-404">Method</span></span>      | <span data-ttu-id="358bc-405">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-405">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-406">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-406">GET</span></span> | <span data-ttu-id="358bc-407">/api/holographic/simulation/playback/session/types</span><span class="sxs-lookup"><span data-stu-id="358bc-407">/api/holographic/simulation/playback/session/types</span></span>


**<span data-ttu-id="358bc-408">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-408">URI parameters</span></span>**

<span data-ttu-id="358bc-409">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-409">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-410">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-410">URI parameter</span></span> | <span data-ttu-id="358bc-411">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-411">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-412">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-412">recording</span></span>   | <span data-ttu-id="358bc-413">(**erforderlich**) Der Name der betreffenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-413">(**required**) The name of the recording you are interested in.</span></span>

**<span data-ttu-id="358bc-414">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-414">Request headers</span></span>**

- <span data-ttu-id="358bc-415">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-415">None</span></span>

**<span data-ttu-id="358bc-416">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-416">Request body</span></span>**

- <span data-ttu-id="358bc-417">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-417">None</span></span>

**<span data-ttu-id="358bc-418">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-418">Response</span></span>**

- <span data-ttu-id="358bc-419">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-419">None</span></span>

**<span data-ttu-id="358bc-420">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-420">Status code</span></span>**

- <span data-ttu-id="358bc-421">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-421">Standard status codes.</span></span>

---
### <a name="get-all-the-loaded-recordings"></a><span data-ttu-id="358bc-422">Abrufen aller geladenen Aufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="358bc-422">Get all the loaded recordings</span></span>

**<span data-ttu-id="358bc-423">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-423">Request</span></span>**

<span data-ttu-id="358bc-424">Mit dem folgenden Anforderungsformat können Sie alle geladenen Aufzeichnungen abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-424">You can get all the loaded recordings by using the following request format.</span></span>
 
<span data-ttu-id="358bc-425">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-425">Method</span></span>      | <span data-ttu-id="358bc-426">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-426">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-427">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-427">GET</span></span> | <span data-ttu-id="358bc-428">/api/holographic/simulation/playback/session/files</span><span class="sxs-lookup"><span data-stu-id="358bc-428">/api/holographic/simulation/playback/session/files</span></span>


**<span data-ttu-id="358bc-429">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-429">URI parameters</span></span>**

- <span data-ttu-id="358bc-430">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-430">None</span></span>

**<span data-ttu-id="358bc-431">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-431">Request headers</span></span>**

- <span data-ttu-id="358bc-432">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-432">None</span></span>

**<span data-ttu-id="358bc-433">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-433">Request body</span></span>**

- <span data-ttu-id="358bc-434">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-434">None</span></span>

**<span data-ttu-id="358bc-435">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-435">Response</span></span>**

- <span data-ttu-id="358bc-436">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-436">None</span></span>

**<span data-ttu-id="358bc-437">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-437">Status code</span></span>**

- <span data-ttu-id="358bc-438">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-438">Standard status codes.</span></span>

---
### <a name="get-the-current-playback-state-of-a-recording"></a><span data-ttu-id="358bc-439">Abrufen des aktuellen Wiedergabestatus einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-439">Get the current playback state of a recording</span></span> 

**<span data-ttu-id="358bc-440">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-440">Request</span></span>**

<span data-ttu-id="358bc-441">Mit dem folgenden Anforderungsformat können Sie den aktuellen Wiedergabestatus einer Aufzeichnung abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-441">You can get the current playback state of a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-442">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-442">Method</span></span>      | <span data-ttu-id="358bc-443">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-443">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-444">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-444">GET</span></span> | <span data-ttu-id="358bc-445">/api/holographic/simulation/playback/session</span><span class="sxs-lookup"><span data-stu-id="358bc-445">/api/holographic/simulation/playback/session</span></span>


**<span data-ttu-id="358bc-446">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-446">URI parameters</span></span>**

<span data-ttu-id="358bc-447">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-447">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-448">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-448">URI parameter</span></span> | <span data-ttu-id="358bc-449">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-449">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-450">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-450">recording</span></span>   | <span data-ttu-id="358bc-451">(**erforderlich**) Der Name der betreffenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-451">(**required**) The name of the recording that you are interested in.</span></span>

**<span data-ttu-id="358bc-452">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-452">Request headers</span></span>**

- <span data-ttu-id="358bc-453">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-453">None</span></span>

**<span data-ttu-id="358bc-454">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-454">Request body</span></span>**

- <span data-ttu-id="358bc-455">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-455">None</span></span>

**<span data-ttu-id="358bc-456">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-456">Response</span></span>**

- <span data-ttu-id="358bc-457">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-457">None</span></span>

**<span data-ttu-id="358bc-458">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-458">Status code</span></span>**

- <span data-ttu-id="358bc-459">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-459">Standard status codes.</span></span>

---
### <a name="load-a-recording"></a><span data-ttu-id="358bc-460">Laden einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-460">Load a recording</span></span>

**<span data-ttu-id="358bc-461">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-461">Request</span></span>**

<span data-ttu-id="358bc-462">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung laden.</span><span class="sxs-lookup"><span data-stu-id="358bc-462">You can load a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-463">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-463">Method</span></span>      | <span data-ttu-id="358bc-464">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-464">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-465">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-465">POST</span></span> | <span data-ttu-id="358bc-466">/api/holographic/simulation/playback/session/file</span><span class="sxs-lookup"><span data-stu-id="358bc-466">/api/holographic/simulation/playback/session/file</span></span>


**<span data-ttu-id="358bc-467">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-467">URI parameters</span></span>**

<span data-ttu-id="358bc-468">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-468">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-469">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-469">URI parameter</span></span> | <span data-ttu-id="358bc-470">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-470">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-471">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-471">recording</span></span>   | <span data-ttu-id="358bc-472">(**erforderlich**) Der Name der zu ladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-472">(**required**) The name of the recording to load.</span></span>

**<span data-ttu-id="358bc-473">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-473">Request headers</span></span>**

- <span data-ttu-id="358bc-474">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-474">None</span></span>

**<span data-ttu-id="358bc-475">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-475">Request body</span></span>**

- <span data-ttu-id="358bc-476">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-476">None</span></span>

**<span data-ttu-id="358bc-477">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-477">Response</span></span>**

- <span data-ttu-id="358bc-478">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-478">None</span></span>

**<span data-ttu-id="358bc-479">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-479">Status code</span></span>**

- <span data-ttu-id="358bc-480">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-480">Standard status codes.</span></span>

---
### <a name="pause-a-recording"></a><span data-ttu-id="358bc-481">Anhalten einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-481">Pause a recording</span></span>

**<span data-ttu-id="358bc-482">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-482">Request</span></span>**

<span data-ttu-id="358bc-483">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung anhalten.</span><span class="sxs-lookup"><span data-stu-id="358bc-483">You can pause a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-484">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-484">Method</span></span>      | <span data-ttu-id="358bc-485">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-485">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-486">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-486">POST</span></span> | <span data-ttu-id="358bc-487">/api/holographic/simulation/playback/session/pause</span><span class="sxs-lookup"><span data-stu-id="358bc-487">/api/holographic/simulation/playback/session/pause</span></span>


**<span data-ttu-id="358bc-488">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-488">URI parameters</span></span>**

<span data-ttu-id="358bc-489">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-489">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-490">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-490">URI parameter</span></span> | <span data-ttu-id="358bc-491">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-491">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-492">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-492">recording</span></span>   | <span data-ttu-id="358bc-493">(**erforderlich**) Der Name der anzuhaltenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-493">(**required**) The name of the recording to pause.</span></span>

**<span data-ttu-id="358bc-494">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-494">Request headers</span></span>**

- <span data-ttu-id="358bc-495">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-495">None</span></span>

**<span data-ttu-id="358bc-496">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-496">Request body</span></span>**

- <span data-ttu-id="358bc-497">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-497">None</span></span>

**<span data-ttu-id="358bc-498">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-498">Response</span></span>**

- <span data-ttu-id="358bc-499">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-499">None</span></span>

**<span data-ttu-id="358bc-500">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-500">Status code</span></span>**

- <span data-ttu-id="358bc-501">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-501">Standard status codes.</span></span>

---
### <a name="play-a-recording"></a><span data-ttu-id="358bc-502">Wiedergeben einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-502">Play a recording</span></span>

**<span data-ttu-id="358bc-503">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-503">Request</span></span>**

<span data-ttu-id="358bc-504">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="358bc-504">You can play a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-505">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-505">Method</span></span>      | <span data-ttu-id="358bc-506">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-506">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-507">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-507">POST</span></span> | <span data-ttu-id="358bc-508">/api/holographic/simulation/playback/session/play</span><span class="sxs-lookup"><span data-stu-id="358bc-508">/api/holographic/simulation/playback/session/play</span></span>


**<span data-ttu-id="358bc-509">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-509">URI parameters</span></span>**

<span data-ttu-id="358bc-510">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-510">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-511">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-511">URI parameter</span></span> | <span data-ttu-id="358bc-512">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-512">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-513">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-513">recording</span></span>   | <span data-ttu-id="358bc-514">(**erforderlich**) Der Name der wiederzugebenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-514">(**required**) The name of the recording to play.</span></span>

**<span data-ttu-id="358bc-515">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-515">Request headers</span></span>**

- <span data-ttu-id="358bc-516">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-516">None</span></span>

**<span data-ttu-id="358bc-517">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-517">Request body</span></span>**

- <span data-ttu-id="358bc-518">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-518">None</span></span>

**<span data-ttu-id="358bc-519">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-519">Response</span></span>**

- <span data-ttu-id="358bc-520">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-520">None</span></span>

**<span data-ttu-id="358bc-521">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-521">Status code</span></span>**

- <span data-ttu-id="358bc-522">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-522">Standard status codes.</span></span>

---
### <a name="stop-a-recording"></a><span data-ttu-id="358bc-523">Beenden einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-523">Stop a recording</span></span>

**<span data-ttu-id="358bc-524">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-524">Request</span></span>**

<span data-ttu-id="358bc-525">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung beenden.</span><span class="sxs-lookup"><span data-stu-id="358bc-525">You can stop a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-526">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-526">Method</span></span>      | <span data-ttu-id="358bc-527">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-527">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-528">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-528">POST</span></span> | <span data-ttu-id="358bc-529">/api/holographic/simulation/playback/session/stop</span><span class="sxs-lookup"><span data-stu-id="358bc-529">/api/holographic/simulation/playback/session/stop</span></span>


**<span data-ttu-id="358bc-530">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-530">URI parameters</span></span>**

<span data-ttu-id="358bc-531">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-531">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-532">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-532">URI parameter</span></span> | <span data-ttu-id="358bc-533">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-533">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-534">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-534">recording</span></span>   | <span data-ttu-id="358bc-535">(**erforderlich**) Der Name der zu beendenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-535">(**required**) The name of the recording to stop.</span></span>

**<span data-ttu-id="358bc-536">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-536">Request headers</span></span>**

- <span data-ttu-id="358bc-537">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-537">None</span></span>

**<span data-ttu-id="358bc-538">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-538">Request body</span></span>**

- <span data-ttu-id="358bc-539">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-539">None</span></span>

**<span data-ttu-id="358bc-540">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-540">Response</span></span>**

- <span data-ttu-id="358bc-541">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-541">None</span></span>

**<span data-ttu-id="358bc-542">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-542">Status code</span></span>**

- <span data-ttu-id="358bc-543">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-543">Standard status codes.</span></span>

---
### <a name="unload-a-recording"></a><span data-ttu-id="358bc-544">Entladen einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-544">Unload a recording</span></span>

**<span data-ttu-id="358bc-545">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-545">Request</span></span>**

<span data-ttu-id="358bc-546">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung entladen.</span><span class="sxs-lookup"><span data-stu-id="358bc-546">You can unload a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-547">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-547">Method</span></span>      | <span data-ttu-id="358bc-548">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-548">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-549">DELETE</span><span class="sxs-lookup"><span data-stu-id="358bc-549">DELETE</span></span> | <span data-ttu-id="358bc-550">/api/holographic/simulation/playback/session/file</span><span class="sxs-lookup"><span data-stu-id="358bc-550">/api/holographic/simulation/playback/session/file</span></span>


**<span data-ttu-id="358bc-551">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-551">URI parameters</span></span>**

<span data-ttu-id="358bc-552">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-552">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-553">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-553">URI parameter</span></span> | <span data-ttu-id="358bc-554">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-554">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-555">recording</span><span class="sxs-lookup"><span data-stu-id="358bc-555">recording</span></span>   | <span data-ttu-id="358bc-556">(**erforderlich**) Der Name der zu entladenden Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-556">(**required**) The name of the recording to unload.</span></span>

**<span data-ttu-id="358bc-557">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-557">Request headers</span></span>**

- <span data-ttu-id="358bc-558">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-558">None</span></span>

**<span data-ttu-id="358bc-559">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-559">Request body</span></span>**

- <span data-ttu-id="358bc-560">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-560">None</span></span>

**<span data-ttu-id="358bc-561">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-561">Response</span></span>**

- <span data-ttu-id="358bc-562">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-562">None</span></span>

**<span data-ttu-id="358bc-563">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-563">Status code</span></span>**

- <span data-ttu-id="358bc-564">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-564">Standard status codes.</span></span>

---
### <a name="upload-a-recording"></a><span data-ttu-id="358bc-565">Hochladen einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-565">Upload a recording</span></span>

**<span data-ttu-id="358bc-566">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-566">Request</span></span>**

<span data-ttu-id="358bc-567">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung hochladen.</span><span class="sxs-lookup"><span data-stu-id="358bc-567">You can upload a recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-568">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-568">Method</span></span>      | <span data-ttu-id="358bc-569">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-569">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-570">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-570">POST</span></span> | <span data-ttu-id="358bc-571">/api/holographic/simulation/playback/file</span><span class="sxs-lookup"><span data-stu-id="358bc-571">/api/holographic/simulation/playback/file</span></span>


**<span data-ttu-id="358bc-572">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-572">URI parameters</span></span>**

- <span data-ttu-id="358bc-573">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-573">None</span></span>

**<span data-ttu-id="358bc-574">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-574">Request headers</span></span>**

- <span data-ttu-id="358bc-575">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-575">None</span></span>

**<span data-ttu-id="358bc-576">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-576">Request body</span></span>**

- <span data-ttu-id="358bc-577">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-577">None</span></span>

**<span data-ttu-id="358bc-578">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-578">Response</span></span>**

- <span data-ttu-id="358bc-579">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-579">None</span></span>

**<span data-ttu-id="358bc-580">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-580">Status code</span></span>**

- <span data-ttu-id="358bc-581">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-581">Standard status codes.</span></span>

---
## HSimulation recording
---
### <a name="get-the-recording-state"></a><span data-ttu-id="358bc-582">Abrufen des Aufzeichnungsstatus</span><span class="sxs-lookup"><span data-stu-id="358bc-582">Get the recording state</span></span>

**<span data-ttu-id="358bc-583">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-583">Request</span></span>**

<span data-ttu-id="358bc-584">Mit dem folgenden Anforderungsformat können Sie den aktuellen Aufzeichnungsstatus abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-584">You can get the current recording state by using the following request format.</span></span>
 
<span data-ttu-id="358bc-585">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-585">Method</span></span>      | <span data-ttu-id="358bc-586">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-586">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-587">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-587">GET</span></span> | <span data-ttu-id="358bc-588">/api/holographic/simulation/recording/status</span><span class="sxs-lookup"><span data-stu-id="358bc-588">/api/holographic/simulation/recording/status</span></span>


**<span data-ttu-id="358bc-589">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-589">URI parameters</span></span>**

- <span data-ttu-id="358bc-590">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-590">None</span></span>

**<span data-ttu-id="358bc-591">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-591">Request headers</span></span>**

- <span data-ttu-id="358bc-592">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-592">None</span></span>

**<span data-ttu-id="358bc-593">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-593">Request body</span></span>**

- <span data-ttu-id="358bc-594">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-594">None</span></span>

**<span data-ttu-id="358bc-595">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-595">Response</span></span>**

- <span data-ttu-id="358bc-596">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-596">None</span></span>

**<span data-ttu-id="358bc-597">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-597">Status code</span></span>**

- <span data-ttu-id="358bc-598">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-598">Standard status codes.</span></span>

---
### <a name="start-a-recording"></a><span data-ttu-id="358bc-599">Starten einer Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-599">Start a recording</span></span>

**<span data-ttu-id="358bc-600">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-600">Request</span></span>**

<span data-ttu-id="358bc-601">Mit dem folgenden Anforderungsformat können Sie eine Aufzeichnung starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-601">You can start a recording by using the following request format.</span></span> <span data-ttu-id="358bc-602">Es kann nur jeweils eine aktive Aufzeichnung vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-602">There can only be one active recording at a time.</span></span> 
 
<span data-ttu-id="358bc-603">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-603">Method</span></span>      | <span data-ttu-id="358bc-604">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-604">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-605">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-605">POST</span></span> | <span data-ttu-id="358bc-606">/api/holographic/simulation/recording/start</span><span class="sxs-lookup"><span data-stu-id="358bc-606">/api/holographic/simulation/recording/start</span></span>


**<span data-ttu-id="358bc-607">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-607">URI parameters</span></span>**

<span data-ttu-id="358bc-608">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-608">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-609">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-609">URI parameter</span></span> | <span data-ttu-id="358bc-610">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-610">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-611">head</span><span class="sxs-lookup"><span data-stu-id="358bc-611">head</span></span>   | <span data-ttu-id="358bc-612">(**siehe unten**) Legen Sie diesen Wert auf 1 fest, um anzugeben, dass das System Kopfdaten aufzeichnen soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-612">(**see below**) Set this value to 1 to indicate the system should record head data.</span></span>
<span data-ttu-id="358bc-613">hands</span><span class="sxs-lookup"><span data-stu-id="358bc-613">hands</span></span>   | <span data-ttu-id="358bc-614">(**siehe unten**) Legen Sie diesen Wert auf 1 fest, um anzugeben, dass das System Handdaten aufzeichnen soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-614">(**see below**) Set this value to 1 to indicate the system should record hands data.</span></span>
<span data-ttu-id="358bc-615">spatialMapping</span><span class="sxs-lookup"><span data-stu-id="358bc-615">spatialMapping</span></span>   | <span data-ttu-id="358bc-616">(**siehe unten**) Legen Sie diesen Wert auf 1 fest, um anzugeben, dass das System Spatial-Mapping-Daten aufzeichnen soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-616">(**see below**) Set this value to 1 to indicate the system should record spatial mapping data.</span></span>
<span data-ttu-id="358bc-617">environment</span><span class="sxs-lookup"><span data-stu-id="358bc-617">environment</span></span>   | <span data-ttu-id="358bc-618">(**siehe unten**) Legen Sie diesen Wert auf 1 fest, um anzugeben, dass das System Umgebungsdaten aufzeichnen soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-618">(**see below**) Set this value to 1 to indicate the system should record environment data.</span></span>
<span data-ttu-id="358bc-619">name</span><span class="sxs-lookup"><span data-stu-id="358bc-619">name</span></span>   | <span data-ttu-id="358bc-620">(**erforderlich**) Der Name der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="358bc-620">(**required**) The name of the recording.</span></span>
<span data-ttu-id="358bc-621">singleSpatialMappingFrame</span><span class="sxs-lookup"><span data-stu-id="358bc-621">singleSpatialMappingFrame</span></span>   | <span data-ttu-id="358bc-622">(**optional**) Legen Sie diesen Wert auf 1 fest, um anzugeben, dass nur ein einzelner Spatial-Mapping-Frame aufgezeichnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="358bc-622">(**optional**) Set this value to 1 to indicate that only a single sptial mapping frame should be recorded.</span></span>

<span data-ttu-id="358bc-623">Für diese Parameter muss genau einer der folgenden Parameter auf 1 festgelegt werden: *head*, *hands*, *spatialMapping* oder *environment*.</span><span class="sxs-lookup"><span data-stu-id="358bc-623">For these parameters, exactly one of the following parameters must be set to 1: *head*, *hands*, *spatialMapping*, or *environment*.</span></span>

**<span data-ttu-id="358bc-624">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-624">Request headers</span></span>**

- <span data-ttu-id="358bc-625">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-625">None</span></span>

**<span data-ttu-id="358bc-626">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-626">Request body</span></span>**

- <span data-ttu-id="358bc-627">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-627">None</span></span>

**<span data-ttu-id="358bc-628">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-628">Response</span></span>**

- <span data-ttu-id="358bc-629">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-629">None</span></span>

**<span data-ttu-id="358bc-630">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-630">Status code</span></span>**

- <span data-ttu-id="358bc-631">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-631">Standard status codes.</span></span>

---
### <a name="stop-the-current-recording"></a><span data-ttu-id="358bc-632">Beenden der aktuellen Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="358bc-632">Stop the current recording</span></span>

**<span data-ttu-id="358bc-633">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-633">Request</span></span>**

<span data-ttu-id="358bc-634">Mit dem folgenden Anforderungsformat können Sie die aktuelle Aufzeichnung beenden.</span><span class="sxs-lookup"><span data-stu-id="358bc-634">You can stop the current recording by using the following request format.</span></span> <span data-ttu-id="358bc-635">Die Aufzeichnung wird als Datei zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="358bc-635">The recording will be returned as a file.</span></span>
 
<span data-ttu-id="358bc-636">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-636">Method</span></span>      | <span data-ttu-id="358bc-637">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-637">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-638">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-638">POST</span></span> | <span data-ttu-id="358bc-639">/api/holographic/simulation/recording/stop</span><span class="sxs-lookup"><span data-stu-id="358bc-639">/api/holographic/simulation/recording/stop</span></span>


**<span data-ttu-id="358bc-640">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-640">URI parameters</span></span>**

- <span data-ttu-id="358bc-641">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-641">None</span></span>

**<span data-ttu-id="358bc-642">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-642">Request headers</span></span>**

- <span data-ttu-id="358bc-643">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-643">None</span></span>

**<span data-ttu-id="358bc-644">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-644">Request body</span></span>**

- <span data-ttu-id="358bc-645">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-645">None</span></span>

**<span data-ttu-id="358bc-646">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-646">Response</span></span>**

- <span data-ttu-id="358bc-647">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-647">None</span></span>

**<span data-ttu-id="358bc-648">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-648">Status code</span></span>**

- <span data-ttu-id="358bc-649">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-649">Standard status codes.</span></span>

---
## Mixed reality capture
---
### <a name="delete-a-mixed-reality-capture-mrc-recording-from-the-device"></a><span data-ttu-id="358bc-650">Löschen einer Mixed Reality-Aufnahme (Mixed Reality Capture, MRC) vom Gerät</span><span class="sxs-lookup"><span data-stu-id="358bc-650">Delete a mixed reality capture (MRC) recording from the device</span></span>

**<span data-ttu-id="358bc-651">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-651">Request</span></span>**

<span data-ttu-id="358bc-652">Mit dem folgenden Anforderungsformat können Sie eine MRC-Aufzeichnung löschen.</span><span class="sxs-lookup"><span data-stu-id="358bc-652">You can delete an MRC recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-653">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-653">Method</span></span>      | <span data-ttu-id="358bc-654">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-654">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-655">DELETE</span><span class="sxs-lookup"><span data-stu-id="358bc-655">DELETE</span></span> | <span data-ttu-id="358bc-656">/api/holographic/mrc/file</span><span class="sxs-lookup"><span data-stu-id="358bc-656">/api/holographic/mrc/file</span></span>


**<span data-ttu-id="358bc-657">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-657">URI parameters</span></span>**

<span data-ttu-id="358bc-658">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-658">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-659">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-659">URI parameter</span></span> | <span data-ttu-id="358bc-660">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-660">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-661">filename</span><span class="sxs-lookup"><span data-stu-id="358bc-661">filename</span></span>   | <span data-ttu-id="358bc-662">(**erforderlich**) Der Name der zu löschenden Videodatei.</span><span class="sxs-lookup"><span data-stu-id="358bc-662">(**required**) The name of the video file to delete.</span></span> <span data-ttu-id="358bc-663">Der Name sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-663">The name should be hex64 encoded.</span></span>

**<span data-ttu-id="358bc-664">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-664">Request headers</span></span>**

- <span data-ttu-id="358bc-665">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-665">None</span></span>

**<span data-ttu-id="358bc-666">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-666">Request body</span></span>**

- <span data-ttu-id="358bc-667">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-667">None</span></span>

**<span data-ttu-id="358bc-668">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-668">Response</span></span>**

- <span data-ttu-id="358bc-669">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-669">None</span></span>

**<span data-ttu-id="358bc-670">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-670">Status code</span></span>**

- <span data-ttu-id="358bc-671">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-671">Standard status codes.</span></span>

---
### <a name="download-a-mixed-reality-capture-mrc-file"></a><span data-ttu-id="358bc-672">Herunterladen einer MRC-Datei (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-672">Download a mixed reality capture (MRC) file</span></span>

**<span data-ttu-id="358bc-673">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-673">Request</span></span>**

<span data-ttu-id="358bc-674">Mit dem folgenden Anforderungsformat können Sie eine MRC-Datei vom Gerät herunterladen.</span><span class="sxs-lookup"><span data-stu-id="358bc-674">You can download an MRC file from the device by using the following request format.</span></span>
 
<span data-ttu-id="358bc-675">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-675">Method</span></span>      | <span data-ttu-id="358bc-676">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-676">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-677">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-677">GET</span></span> | <span data-ttu-id="358bc-678">/api/holographic/mrc/file</span><span class="sxs-lookup"><span data-stu-id="358bc-678">/api/holographic/mrc/file</span></span>


**<span data-ttu-id="358bc-679">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-679">URI parameters</span></span>**

<span data-ttu-id="358bc-680">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-680">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-681">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-681">URI parameter</span></span> | <span data-ttu-id="358bc-682">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-682">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-683">filename</span><span class="sxs-lookup"><span data-stu-id="358bc-683">filename</span></span>   | <span data-ttu-id="358bc-684">(**erforderlich**) Der Name der Videodatei, die Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="358bc-684">(**required**) The name of the video file you want to get.</span></span> <span data-ttu-id="358bc-685">Der Name sollte hex64-codiert sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-685">The name should be hex64 encoded.</span></span>
<span data-ttu-id="358bc-686">op</span><span class="sxs-lookup"><span data-stu-id="358bc-686">op</span></span>   | <span data-ttu-id="358bc-687">(**optional**) Legen Sie diesen Wert auf **stream** fest, wenn Sie einen Datenstrom herunterladen möchten.</span><span class="sxs-lookup"><span data-stu-id="358bc-687">(**optional**) Set this value to **stream** if you want to download a stream.</span></span>

**<span data-ttu-id="358bc-688">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-688">Request headers</span></span>**

- <span data-ttu-id="358bc-689">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-689">None</span></span>

**<span data-ttu-id="358bc-690">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-690">Request body</span></span>**

- <span data-ttu-id="358bc-691">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-691">None</span></span>

**<span data-ttu-id="358bc-692">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-692">Response</span></span>**

- <span data-ttu-id="358bc-693">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-693">None</span></span>

**<span data-ttu-id="358bc-694">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-694">Status code</span></span>**

- <span data-ttu-id="358bc-695">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-695">Standard status codes.</span></span>

---
### <a name="get-the-mixed-reality-capture-mrc-settings"></a><span data-ttu-id="358bc-696">Abrufen der MRC-Einstellungen (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-696">Get the mixed reality capture (MRC) settings</span></span>

**<span data-ttu-id="358bc-697">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-697">Request</span></span>**

<span data-ttu-id="358bc-698">Mit dem folgenden Anforderungsformat können Sie die MRC-Einstellungen abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-698">You can get the MRC settings by using the following request format.</span></span>
 
<span data-ttu-id="358bc-699">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-699">Method</span></span>      | <span data-ttu-id="358bc-700">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-700">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-701">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-701">GET</span></span> | <span data-ttu-id="358bc-702">/api/holographic/mrc/settings</span><span class="sxs-lookup"><span data-stu-id="358bc-702">/api/holographic/mrc/settings</span></span>


**<span data-ttu-id="358bc-703">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-703">URI parameters</span></span>**

- <span data-ttu-id="358bc-704">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-704">None</span></span>

**<span data-ttu-id="358bc-705">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-705">Request headers</span></span>**

- <span data-ttu-id="358bc-706">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-706">None</span></span>

**<span data-ttu-id="358bc-707">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-707">Request body</span></span>**

- <span data-ttu-id="358bc-708">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-708">None</span></span>

**<span data-ttu-id="358bc-709">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-709">Response</span></span>**

- <span data-ttu-id="358bc-710">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-710">None</span></span>

**<span data-ttu-id="358bc-711">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-711">Status code</span></span>**

- <span data-ttu-id="358bc-712">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-712">Standard status codes.</span></span>

---
### <a name="get-the-status-of-the-mixed-reality-capture-mrc-recording"></a><span data-ttu-id="358bc-713">Abrufen des Status der MRC-Aufzeichnung (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-713">Get the status of the mixed reality capture (MRC) recording</span></span>

**<span data-ttu-id="358bc-714">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-714">Request</span></span>**

<span data-ttu-id="358bc-715">Mit dem folgenden Anforderungsformat können Sie den Status der MRC-Aufzeichnung abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-715">You can get the MRC recording status by using the following request format.</span></span> <span data-ttu-id="358bc-716">Mögliche Werte: **running** und **stopped**.</span><span class="sxs-lookup"><span data-stu-id="358bc-716">The possible values include **running** and **stopped**.</span></span>
 
<span data-ttu-id="358bc-717">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-717">Method</span></span>      | <span data-ttu-id="358bc-718">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-718">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-719">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-719">GET</span></span> | <span data-ttu-id="358bc-720">/api/holographic/mrc/status</span><span class="sxs-lookup"><span data-stu-id="358bc-720">/api/holographic/mrc/status</span></span>


**<span data-ttu-id="358bc-721">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-721">URI parameters</span></span>**

- <span data-ttu-id="358bc-722">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-722">None</span></span>

**<span data-ttu-id="358bc-723">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-723">Request headers</span></span>**

- <span data-ttu-id="358bc-724">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-724">None</span></span>

**<span data-ttu-id="358bc-725">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-725">Request body</span></span>**

- <span data-ttu-id="358bc-726">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-726">None</span></span>

**<span data-ttu-id="358bc-727">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-727">Response</span></span>**

- <span data-ttu-id="358bc-728">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-728">None</span></span>

**<span data-ttu-id="358bc-729">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-729">Status code</span></span>**

- <span data-ttu-id="358bc-730">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-730">Standard status codes.</span></span>

---
### <a name="get-the-list-of-mixed-reality-capture-mrc-files"></a><span data-ttu-id="358bc-731">Abrufen der Liste der MRC-Dateien (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-731">Get the list of mixed reality capture (MRC) files</span></span>

**<span data-ttu-id="358bc-732">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-732">Request</span></span>**

<span data-ttu-id="358bc-733">Mit dem folgenden Anforderungsformat können Sie die auf dem Gerät gespeicherten MRC-Dateien abrufen.</span><span class="sxs-lookup"><span data-stu-id="358bc-733">You can get the MRC files stored on the device by using the following request format.</span></span>
 
<span data-ttu-id="358bc-734">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-734">Method</span></span>      | <span data-ttu-id="358bc-735">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-735">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-736">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-736">GET</span></span> | <span data-ttu-id="358bc-737">/api/holographic/mrc/files</span><span class="sxs-lookup"><span data-stu-id="358bc-737">/api/holographic/mrc/files</span></span>


**<span data-ttu-id="358bc-738">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-738">URI parameters</span></span>**

- <span data-ttu-id="358bc-739">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-739">None</span></span>

**<span data-ttu-id="358bc-740">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-740">Request headers</span></span>**

- <span data-ttu-id="358bc-741">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-741">None</span></span>

**<span data-ttu-id="358bc-742">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-742">Request body</span></span>**

- <span data-ttu-id="358bc-743">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-743">None</span></span>

**<span data-ttu-id="358bc-744">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-744">Response</span></span>**

- <span data-ttu-id="358bc-745">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-745">None</span></span>

**<span data-ttu-id="358bc-746">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-746">Status code</span></span>**

- <span data-ttu-id="358bc-747">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-747">Standard status codes.</span></span>

---
### <a name="set-the-mixed-reality-capture-mrc-settings"></a><span data-ttu-id="358bc-748">Festlegen der MRC-Einstellungen (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-748">Set the mixed reality capture (MRC) settings</span></span>

**<span data-ttu-id="358bc-749">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-749">Request</span></span>**

<span data-ttu-id="358bc-750">Mit dem folgenden Anforderungsformat können Sie die MRC-Einstellungen festlegen.</span><span class="sxs-lookup"><span data-stu-id="358bc-750">You can set the MRC settings by using the following request format.</span></span>
 
<span data-ttu-id="358bc-751">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-751">Method</span></span>      | <span data-ttu-id="358bc-752">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-752">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-753">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-753">POST</span></span> | <span data-ttu-id="358bc-754">/api/holographic/mrc/settings</span><span class="sxs-lookup"><span data-stu-id="358bc-754">/api/holographic/mrc/settings</span></span>


**<span data-ttu-id="358bc-755">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-755">URI parameters</span></span>**

- <span data-ttu-id="358bc-756">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-756">None</span></span>

**<span data-ttu-id="358bc-757">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-757">Request headers</span></span>**

- <span data-ttu-id="358bc-758">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-758">None</span></span>

**<span data-ttu-id="358bc-759">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-759">Request body</span></span>**

- <span data-ttu-id="358bc-760">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-760">None</span></span>

**<span data-ttu-id="358bc-761">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-761">Response</span></span>**

- <span data-ttu-id="358bc-762">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-762">None</span></span>

**<span data-ttu-id="358bc-763">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-763">Status code</span></span>**

- <span data-ttu-id="358bc-764">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-764">Standard status codes.</span></span>

---
### <a name="starts-a-mixed-reality-capture-mrc-recording"></a><span data-ttu-id="358bc-765">Starten einer MRC-Aufzeichnung (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-765">Starts a mixed reality capture (MRC) recording</span></span>

**<span data-ttu-id="358bc-766">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-766">Request</span></span>**

<span data-ttu-id="358bc-767">Mit dem folgenden Anforderungsformat können Sie eine MRC-Aufzeichnung starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-767">You can start an MRC recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-768">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-768">Method</span></span>      | <span data-ttu-id="358bc-769">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-769">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-770">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-770">POST</span></span> | <span data-ttu-id="358bc-771">/api/holographic/mrc/video/control/start</span><span class="sxs-lookup"><span data-stu-id="358bc-771">/api/holographic/mrc/video/control/start</span></span>


**<span data-ttu-id="358bc-772">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-772">URI parameters</span></span>**

- <span data-ttu-id="358bc-773">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-773">None</span></span>

**<span data-ttu-id="358bc-774">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-774">Request headers</span></span>**

- <span data-ttu-id="358bc-775">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-775">None</span></span>

**<span data-ttu-id="358bc-776">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-776">Request body</span></span>**

- <span data-ttu-id="358bc-777">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-777">None</span></span>

**<span data-ttu-id="358bc-778">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-778">Response</span></span>**

- <span data-ttu-id="358bc-779">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-779">None</span></span>

**<span data-ttu-id="358bc-780">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-780">Status code</span></span>**

- <span data-ttu-id="358bc-781">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-781">Standard status codes.</span></span>

---
### <a name="stop-the-current-mixed-reality-capture-mrc-recording"></a><span data-ttu-id="358bc-782">Beenden der aktuellen MRC-Aufzeichnung (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-782">Stop the current mixed reality capture (MRC) recording</span></span>

**<span data-ttu-id="358bc-783">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-783">Request</span></span>**

<span data-ttu-id="358bc-784">Mit dem folgenden Anforderungsformat können Sie die aktuelle MRC-Aufzeichnung beenden.</span><span class="sxs-lookup"><span data-stu-id="358bc-784">You can stop the current MRC recording by using the following request format.</span></span>
 
<span data-ttu-id="358bc-785">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-785">Method</span></span>      | <span data-ttu-id="358bc-786">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-786">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-787">POST</span><span class="sxs-lookup"><span data-stu-id="358bc-787">POST</span></span> | <span data-ttu-id="358bc-788">/api/holographic/mrc/video/control/stop</span><span class="sxs-lookup"><span data-stu-id="358bc-788">/api/holographic/mrc/video/control/stop</span></span>


**<span data-ttu-id="358bc-789">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-789">URI parameters</span></span>**

- <span data-ttu-id="358bc-790">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-790">None</span></span>

**<span data-ttu-id="358bc-791">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-791">Request headers</span></span>**

- <span data-ttu-id="358bc-792">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-792">None</span></span>

**<span data-ttu-id="358bc-793">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-793">Request body</span></span>**

- <span data-ttu-id="358bc-794">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-794">None</span></span>

**<span data-ttu-id="358bc-795">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-795">Response</span></span>**

- <span data-ttu-id="358bc-796">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-796">None</span></span>

**<span data-ttu-id="358bc-797">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-797">Status code</span></span>**

- <span data-ttu-id="358bc-798">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-798">Standard status codes.</span></span>

---
### <a name="take-a-mixed-reality-capture-mrc-photo"></a><span data-ttu-id="358bc-799">Aufnehmen eines MRC-Fotos (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="358bc-799">Take a mixed reality capture (MRC) photo</span></span>

**<span data-ttu-id="358bc-800">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-800">Request</span></span>**

<span data-ttu-id="358bc-801">Mit dem folgenden Anforderungsformat können Sie ein MRC-Foto aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="358bc-801">You can take an MRC photo by using the following request format.</span></span> <span data-ttu-id="358bc-802">Das Foto wird im JPEG-Format zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="358bc-802">The photo is returned in JPEG format.</span></span>
 
<span data-ttu-id="358bc-803">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-803">Method</span></span>      | <span data-ttu-id="358bc-804">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-804">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-805">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-805">GET</span></span> | <span data-ttu-id="358bc-806">/api/holographic/mrc/photo</span><span class="sxs-lookup"><span data-stu-id="358bc-806">/api/holographic/mrc/photo</span></span>


**<span data-ttu-id="358bc-807">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-807">URI parameters</span></span>**

- <span data-ttu-id="358bc-808">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-808">None</span></span>

**<span data-ttu-id="358bc-809">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-809">Request headers</span></span>**

- <span data-ttu-id="358bc-810">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-810">None</span></span>

**<span data-ttu-id="358bc-811">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-811">Request body</span></span>**

- <span data-ttu-id="358bc-812">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-812">None</span></span>

**<span data-ttu-id="358bc-813">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-813">Response</span></span>**

- <span data-ttu-id="358bc-814">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-814">None</span></span>

**<span data-ttu-id="358bc-815">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-815">Status code</span></span>**

- <span data-ttu-id="358bc-816">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-816">Standard status codes.</span></span>

---
## Mixed reality streaming
---
### <a name="initiates-a-chunked-download-of-a-fragmented-mp4"></a><span data-ttu-id="358bc-817">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="358bc-817">Initiates a chunked download of a fragmented mp4</span></span>

**<span data-ttu-id="358bc-818">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-818">Request</span></span>**

<span data-ttu-id="358bc-819">Mit dem folgenden Anforderungsformat können Sie den portionsweisen Download einer fragmentierten MP4-Datei starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-819">You can initiate a chunked download of a fragmented mp4 by using the following request format.</span></span> <span data-ttu-id="358bc-820">Diese API verwendet die Standardqualität.</span><span class="sxs-lookup"><span data-stu-id="358bc-820">This API uses the default quality.</span></span>
 
<span data-ttu-id="358bc-821">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-821">Method</span></span>      | <span data-ttu-id="358bc-822">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-822">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-823">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-823">GET</span></span> | <span data-ttu-id="358bc-824">/api/holographic/stream/live.mp4</span><span class="sxs-lookup"><span data-stu-id="358bc-824">/api/holographic/stream/live.mp4</span></span>


**<span data-ttu-id="358bc-825">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-825">URI parameters</span></span>**

<span data-ttu-id="358bc-826">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-826">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-827">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-827">URI parameter</span></span> | <span data-ttu-id="358bc-828">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-828">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-829">pv</span><span class="sxs-lookup"><span data-stu-id="358bc-829">pv</span></span>   | <span data-ttu-id="358bc-830">(**optional**) Gibt an, ob Aufnahmen der Foto-/Videokamera aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-830">(**optional**) Indiates whether to capture the PV camera.</span></span> <span data-ttu-id="358bc-831">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-831">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-832">holo</span><span class="sxs-lookup"><span data-stu-id="358bc-832">holo</span></span>   | <span data-ttu-id="358bc-833">(**optional**) Gibt an, ob Hologramme aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-833">(**optional**) Indiates whether to capture holograms.</span></span> <span data-ttu-id="358bc-834">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-834">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-835">mic</span><span class="sxs-lookup"><span data-stu-id="358bc-835">mic</span></span>   | <span data-ttu-id="358bc-836">(**optional**) Gibt an, ob Aufnahmen des Mikrofons aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-836">(**optional**) Indiates whether to capture the microphone.</span></span> <span data-ttu-id="358bc-837">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-837">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-838">loopback</span><span class="sxs-lookup"><span data-stu-id="358bc-838">loopback</span></span>   | <span data-ttu-id="358bc-839">(**optional**) Gibt an, ob Audioaufnahmen der Anwendung aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-839">(**optional**) Indiates whether to capture the application audio.</span></span> <span data-ttu-id="358bc-840">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-840">Should be **true** or **false**.</span></span>

**<span data-ttu-id="358bc-841">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-841">Request headers</span></span>**

- <span data-ttu-id="358bc-842">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-842">None</span></span>

**<span data-ttu-id="358bc-843">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-843">Request body</span></span>**

- <span data-ttu-id="358bc-844">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-844">None</span></span>

**<span data-ttu-id="358bc-845">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-845">Response</span></span>**

- <span data-ttu-id="358bc-846">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-846">None</span></span>

**<span data-ttu-id="358bc-847">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-847">Status code</span></span>**

- <span data-ttu-id="358bc-848">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-848">Standard status codes.</span></span>

---
### <a name="initiates-a-chunked-download-of-a-fragmented-mp4"></a><span data-ttu-id="358bc-849">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="358bc-849">Initiates a chunked download of a fragmented mp4</span></span>

**<span data-ttu-id="358bc-850">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-850">Request</span></span>**

<span data-ttu-id="358bc-851">Mit dem folgenden Anforderungsformat können Sie den portionsweisen Download einer fragmentierten MP4-Datei starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-851">You can initiate a chunked download of a fragmented mp4 by using the following request format.</span></span> <span data-ttu-id="358bc-852">Diese API verwendet die hohe Qualität.</span><span class="sxs-lookup"><span data-stu-id="358bc-852">This API uses the high quality.</span></span>
 
<span data-ttu-id="358bc-853">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-853">Method</span></span>      | <span data-ttu-id="358bc-854">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-854">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-855">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-855">GET</span></span> | <span data-ttu-id="358bc-856">/api/holographic/stream/live_high.mp4</span><span class="sxs-lookup"><span data-stu-id="358bc-856">/api/holographic/stream/live_high.mp4</span></span>


**<span data-ttu-id="358bc-857">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-857">URI parameters</span></span>**

<span data-ttu-id="358bc-858">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-858">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-859">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-859">URI parameter</span></span> | <span data-ttu-id="358bc-860">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-860">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-861">pv</span><span class="sxs-lookup"><span data-stu-id="358bc-861">pv</span></span>   | <span data-ttu-id="358bc-862">(**optional**) Gibt an, ob Aufnahmen der Foto-/Videokamera aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-862">(**optional**) Indiates whether to capture the PV camera.</span></span> <span data-ttu-id="358bc-863">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-863">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-864">holo</span><span class="sxs-lookup"><span data-stu-id="358bc-864">holo</span></span>   | <span data-ttu-id="358bc-865">(**optional**) Gibt an, ob Hologramme aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-865">(**optional**) Indiates whether to capture holograms.</span></span> <span data-ttu-id="358bc-866">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-866">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-867">mic</span><span class="sxs-lookup"><span data-stu-id="358bc-867">mic</span></span>   | <span data-ttu-id="358bc-868">(**optional**) Gibt an, ob Aufnahmen des Mikrofons aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-868">(**optional**) Indiates whether to capture the microphone.</span></span> <span data-ttu-id="358bc-869">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-869">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-870">loopback</span><span class="sxs-lookup"><span data-stu-id="358bc-870">loopback</span></span>   | <span data-ttu-id="358bc-871">(**optional**) Gibt an, ob Audioaufnahmen der Anwendung aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-871">(**optional**) Indiates whether to capture the application audio.</span></span> <span data-ttu-id="358bc-872">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-872">Should be **true** or **false**.</span></span>

**<span data-ttu-id="358bc-873">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-873">Request headers</span></span>**

- <span data-ttu-id="358bc-874">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-874">None</span></span>

**<span data-ttu-id="358bc-875">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-875">Request body</span></span>**

- <span data-ttu-id="358bc-876">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-876">None</span></span>

**<span data-ttu-id="358bc-877">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-877">Response</span></span>**

- <span data-ttu-id="358bc-878">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-878">None</span></span>

**<span data-ttu-id="358bc-879">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-879">Status code</span></span>**

- <span data-ttu-id="358bc-880">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-880">Standard status codes.</span></span>

---
### <a name="initiates-a-chunked-download-of-a-fragmented-mp4"></a><span data-ttu-id="358bc-881">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="358bc-881">Initiates a chunked download of a fragmented mp4</span></span>

**<span data-ttu-id="358bc-882">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-882">Request</span></span>**

<span data-ttu-id="358bc-883">Mit dem folgenden Anforderungsformat können Sie den portionsweisen Download einer fragmentierten MP4-Datei starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-883">You can initiate a chunked download of a fragmented mp4 by using the following request format.</span></span> <span data-ttu-id="358bc-884">Diese API verwendet die niedrige Qualität.</span><span class="sxs-lookup"><span data-stu-id="358bc-884">This API uses the low quality.</span></span>
 
<span data-ttu-id="358bc-885">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-885">Method</span></span>      | <span data-ttu-id="358bc-886">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-886">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-887">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-887">GET</span></span> | <span data-ttu-id="358bc-888">/api/holographic/stream/live_low.mp4</span><span class="sxs-lookup"><span data-stu-id="358bc-888">/api/holographic/stream/live_low.mp4</span></span>


**<span data-ttu-id="358bc-889">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-889">URI parameters</span></span>**

<span data-ttu-id="358bc-890">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-890">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-891">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-891">URI parameter</span></span> | <span data-ttu-id="358bc-892">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-892">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-893">pv</span><span class="sxs-lookup"><span data-stu-id="358bc-893">pv</span></span>   | <span data-ttu-id="358bc-894">(**optional**) Gibt an, ob Aufnahmen der Foto-/Videokamera aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-894">(**optional**) Indiates whether to capture the PV camera.</span></span> <span data-ttu-id="358bc-895">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-895">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-896">holo</span><span class="sxs-lookup"><span data-stu-id="358bc-896">holo</span></span>   | <span data-ttu-id="358bc-897">(**optional**) Gibt an, ob Hologramme aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-897">(**optional**) Indiates whether to capture holograms.</span></span> <span data-ttu-id="358bc-898">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-898">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-899">mic</span><span class="sxs-lookup"><span data-stu-id="358bc-899">mic</span></span>   | <span data-ttu-id="358bc-900">(**optional**) Gibt an, ob Aufnahmen des Mikrofons aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-900">(**optional**) Indiates whether to capture the microphone.</span></span> <span data-ttu-id="358bc-901">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-901">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-902">loopback</span><span class="sxs-lookup"><span data-stu-id="358bc-902">loopback</span></span>   | <span data-ttu-id="358bc-903">(**optional**) Gibt an, ob Audioaufnahmen der Anwendung aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-903">(**optional**) Indiates whether to capture the application audio.</span></span> <span data-ttu-id="358bc-904">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-904">Should be **true** or **false**.</span></span>

**<span data-ttu-id="358bc-905">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-905">Request headers</span></span>**

- <span data-ttu-id="358bc-906">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-906">None</span></span>

**<span data-ttu-id="358bc-907">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-907">Request body</span></span>**

- <span data-ttu-id="358bc-908">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-908">None</span></span>

**<span data-ttu-id="358bc-909">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-909">Response</span></span>**

- <span data-ttu-id="358bc-910">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-910">None</span></span>

**<span data-ttu-id="358bc-911">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-911">Status code</span></span>**

- <span data-ttu-id="358bc-912">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-912">Standard status codes.</span></span>

---
### <a name="initiates-a-chunked-download-of-a-fragmented-mp4"></a><span data-ttu-id="358bc-913">Starten des portionsweisen Downloads einer fragmentierten MP4-Datei</span><span class="sxs-lookup"><span data-stu-id="358bc-913">Initiates a chunked download of a fragmented mp4</span></span>

**<span data-ttu-id="358bc-914">Anforderung</span><span class="sxs-lookup"><span data-stu-id="358bc-914">Request</span></span>**

<span data-ttu-id="358bc-915">Mit dem folgenden Anforderungsformat können Sie den portionsweisen Download einer fragmentierten MP4-Datei starten.</span><span class="sxs-lookup"><span data-stu-id="358bc-915">You can initiate a chunked download of a fragmented mp4 by using the following request format.</span></span> <span data-ttu-id="358bc-916">Diese API verwendet die mittlere Qualität.</span><span class="sxs-lookup"><span data-stu-id="358bc-916">This API uses the medium quality.</span></span>
 
<span data-ttu-id="358bc-917">Methode</span><span class="sxs-lookup"><span data-stu-id="358bc-917">Method</span></span>      | <span data-ttu-id="358bc-918">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="358bc-918">Request URI</span></span>
:------     | :-----
<span data-ttu-id="358bc-919">GET</span><span class="sxs-lookup"><span data-stu-id="358bc-919">GET</span></span> | <span data-ttu-id="358bc-920">/api/holographic/stream/live_med.mp4</span><span class="sxs-lookup"><span data-stu-id="358bc-920">/api/holographic/stream/live_med.mp4</span></span>


**<span data-ttu-id="358bc-921">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-921">URI parameters</span></span>**

<span data-ttu-id="358bc-922">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="358bc-922">You can specify the following additional parameters on the request URI:</span></span>

<span data-ttu-id="358bc-923">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="358bc-923">URI parameter</span></span> | <span data-ttu-id="358bc-924">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="358bc-924">Description</span></span>
:---          | :---
<span data-ttu-id="358bc-925">pv</span><span class="sxs-lookup"><span data-stu-id="358bc-925">pv</span></span>   | <span data-ttu-id="358bc-926">(**optional**) Gibt an, ob Aufnahmen der Foto-/Videokamera aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-926">(**optional**) Indiates whether to capture the PV camera.</span></span> <span data-ttu-id="358bc-927">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-927">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-928">holo</span><span class="sxs-lookup"><span data-stu-id="358bc-928">holo</span></span>   | <span data-ttu-id="358bc-929">(**optional**) Gibt an, ob Hologramme aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-929">(**optional**) Indiates whether to capture holograms.</span></span> <span data-ttu-id="358bc-930">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-930">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-931">mic</span><span class="sxs-lookup"><span data-stu-id="358bc-931">mic</span></span>   | <span data-ttu-id="358bc-932">(**optional**) Gibt an, ob Aufnahmen des Mikrofons aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-932">(**optional**) Indiates whether to capture the microphone.</span></span> <span data-ttu-id="358bc-933">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-933">Should be **true** or **false**.</span></span>
<span data-ttu-id="358bc-934">loopback</span><span class="sxs-lookup"><span data-stu-id="358bc-934">loopback</span></span>   | <span data-ttu-id="358bc-935">(**optional**) Gibt an, ob Audioaufnahmen der Anwendung aufgezeichnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="358bc-935">(**optional**) Indiates whether to capture the application audio.</span></span> <span data-ttu-id="358bc-936">Sollte **true** oder **false** sein.</span><span class="sxs-lookup"><span data-stu-id="358bc-936">Should be **true** or **false**.</span></span>

**<span data-ttu-id="358bc-937">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="358bc-937">Request headers</span></span>**

- <span data-ttu-id="358bc-938">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-938">None</span></span>

**<span data-ttu-id="358bc-939">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="358bc-939">Request body</span></span>**

- <span data-ttu-id="358bc-940">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-940">None</span></span>

**<span data-ttu-id="358bc-941">Antwort</span><span class="sxs-lookup"><span data-stu-id="358bc-941">Response</span></span>**

- <span data-ttu-id="358bc-942">Keine</span><span class="sxs-lookup"><span data-stu-id="358bc-942">None</span></span>

**<span data-ttu-id="358bc-943">Statuscode</span><span class="sxs-lookup"><span data-stu-id="358bc-943">Status code</span></span>**

- <span data-ttu-id="358bc-944">Standardstatuscodes</span><span class="sxs-lookup"><span data-stu-id="358bc-944">Standard status codes.</span></span>
