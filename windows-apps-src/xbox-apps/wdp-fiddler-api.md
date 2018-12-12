---
title: Geräteportal – API-Referenz für Fiddler
description: Erfahren Sie, wie Sie die Fiddler-Ablaufverfolgung programmgesteuert aktivieren/deaktivieren.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: e7d4225e-ac2c-41dc-aca7-9b1a95ec590b
ms.localizationpriority: medium
ms.openlocfilehash: f60f3fc8678208f694a9ffabde06fa60de759a45
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8937811"
---
# <a name="fiddler-settings-api-reference"></a><span data-ttu-id="33cda-104">Fiddler-Einstellungen – API-Referenz</span><span class="sxs-lookup"><span data-stu-id="33cda-104">Fiddler settings API reference</span></span>   
<span data-ttu-id="33cda-105">Sie können die Fiddler-Netzwerkablaufverfolgung für Ihr Dev Kit mittels dieser REST-API aktivieren und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="33cda-105">You can enable and disable Fiddler network tracing on your devkit using this REST API.</span></span>

## <a name="determine-if-fiddler-tracing-is-enabled"></a><span data-ttu-id="33cda-106">Ermitteln Sie, ob der Fiddler-Ablaufverfolgung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="33cda-106">Determine if Fiddler tracing is enabled</span></span>

**<span data-ttu-id="33cda-107">Anforderung</span><span class="sxs-lookup"><span data-stu-id="33cda-107">Request</span></span>**

<span data-ttu-id="33cda-108">Sie können überprüfen, um festzustellen, ob der Fiddler-Ablaufverfolgung mithilfe der folgenden Anforderung für das Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="33cda-108">You can check to see if Fiddler tracing is enabled on the device using the following request.</span></span>

<span data-ttu-id="33cda-109">Methode</span><span class="sxs-lookup"><span data-stu-id="33cda-109">Method</span></span>      | <span data-ttu-id="33cda-110">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="33cda-110">Request URI</span></span>
:------     | :-----
<span data-ttu-id="33cda-111">GET</span><span class="sxs-lookup"><span data-stu-id="33cda-111">GET</span></span> | <span data-ttu-id="33cda-112">/ext/fiddler</span><span class="sxs-lookup"><span data-stu-id="33cda-112">/ext/fiddler</span></span>
<br />
**<span data-ttu-id="33cda-113">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="33cda-113">URI parameters</span></span>**

- <span data-ttu-id="33cda-114">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-114">None</span></span>

**<span data-ttu-id="33cda-115">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="33cda-115">Request headers</span></span>**

- <span data-ttu-id="33cda-116">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-116">None</span></span>

**<span data-ttu-id="33cda-117">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="33cda-117">Request body</span></span>**   

- <span data-ttu-id="33cda-118">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-118">None</span></span>

**<span data-ttu-id="33cda-119">Antwort</span><span class="sxs-lookup"><span data-stu-id="33cda-119">Response</span></span>**   

- <span data-ttu-id="33cda-120">JSON Bool Eigenschaft IsProxyEnabled welche Bezeichner gibt an, ob der Proxy aktiviert ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="33cda-120">JSON bool property IsProxyEnabled which specifiers whether the proxy is enabled or not.</span></span>

**<span data-ttu-id="33cda-121">Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-121">Status code</span></span>**

<span data-ttu-id="33cda-122">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="33cda-122">This API has the following expected status codes.</span></span>

<span data-ttu-id="33cda-123">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-123">HTTP status code</span></span>      | <span data-ttu-id="33cda-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33cda-124">Description</span></span>
:------     | :-----
<span data-ttu-id="33cda-125">200</span><span class="sxs-lookup"><span data-stu-id="33cda-125">200</span></span> | <span data-ttu-id="33cda-126">Erfolg</span><span class="sxs-lookup"><span data-stu-id="33cda-126">Success</span></span>
<span data-ttu-id="33cda-127">4XX</span><span class="sxs-lookup"><span data-stu-id="33cda-127">4XX</span></span> | <span data-ttu-id="33cda-128">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-128">Error codes</span></span>
<span data-ttu-id="33cda-129">5XX</span><span class="sxs-lookup"><span data-stu-id="33cda-129">5XX</span></span> | <span data-ttu-id="33cda-130">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-130">Error codes</span></span>

## <a name="enable-fiddler-tracing"></a><span data-ttu-id="33cda-131">Aktivieren der Fiddler-Ablaufverfolgung</span><span class="sxs-lookup"><span data-stu-id="33cda-131">Enable Fiddler tracing</span></span>

**<span data-ttu-id="33cda-132">Anforderung</span><span class="sxs-lookup"><span data-stu-id="33cda-132">Request</span></span>**

<span data-ttu-id="33cda-133">Sie können die Fiddler-Ablaufverfolgung mittels der folgenden Anforderung für das Dev Kit verwenden.</span><span class="sxs-lookup"><span data-stu-id="33cda-133">You can enable Fiddler tracing for the devkit using the following request.</span></span>  <span data-ttu-id="33cda-134">Beachten Sie, dass das Gerät neu gestartet werden muss, bevor dies wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-134">Note that the device must be restarted before this takes effect.</span></span>

<span data-ttu-id="33cda-135">Methode</span><span class="sxs-lookup"><span data-stu-id="33cda-135">Method</span></span>      | <span data-ttu-id="33cda-136">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="33cda-136">Request URI</span></span>
:------     | :-----
<span data-ttu-id="33cda-137">POST</span><span class="sxs-lookup"><span data-stu-id="33cda-137">POST</span></span> | <span data-ttu-id="33cda-138">/ext/fiddler</span><span class="sxs-lookup"><span data-stu-id="33cda-138">/ext/fiddler</span></span>
<br />
**<span data-ttu-id="33cda-139">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="33cda-139">URI parameters</span></span>**

<span data-ttu-id="33cda-140">Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:</span><span class="sxs-lookup"><span data-stu-id="33cda-140">You can specify the following additional parameters on the request URI:</span></span>

| <span data-ttu-id="33cda-141">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="33cda-141">URI parameter</span></span>      | <span data-ttu-id="33cda-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33cda-142">Description</span></span>     | 
| ------------------ |-----------------|
| <span data-ttu-id="33cda-143">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="33cda-143">proxyAddress</span></span>       | <span data-ttu-id="33cda-144">Die IP-Adresse oder der Hostnamen des Geräts, auf dem Fiddler ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-144">The IP address or hostname of the device running Fiddler</span></span> |
| <span data-ttu-id="33cda-145">proxyPort</span><span class="sxs-lookup"><span data-stu-id="33cda-145">proxyPort</span></span>          | <span data-ttu-id="33cda-146">Der Port, den Fiddler für die Überwachung des Datenverkehrs verwendet.</span><span class="sxs-lookup"><span data-stu-id="33cda-146">The port which Fiddler is using for monitoring traffic.</span></span> <span data-ttu-id="33cda-147">Der Standardport ist 8888.</span><span class="sxs-lookup"><span data-stu-id="33cda-147">Defaults to 8888</span></span> |
| <span data-ttu-id="33cda-148">updateCert (optional)</span><span class="sxs-lookup"><span data-stu-id="33cda-148">updateCert (optional)</span></span>| <span data-ttu-id="33cda-149">Ein boolescher Wert, der angibt, ob das Fiddler-Stammzertifikat angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-149">A boolean value indicating if the root Fiddler cert is provided.</span></span> <span data-ttu-id="33cda-150">Dieser Wert muss true sein, wenn Fiddler nie zuvor für dieses Dev Kit oder für einen anderen Host konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="33cda-150">This must be true if Fiddler has never been configured on this devkit or was configured for a different host.</span></span>  |
<br>

**<span data-ttu-id="33cda-151">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="33cda-151">Request headers</span></span>**

- <span data-ttu-id="33cda-152">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-152">None</span></span>

**<span data-ttu-id="33cda-153">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="33cda-153">Request body</span></span>**

- <span data-ttu-id="33cda-154">Keiner, wenn updateCert false ist oder nicht angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-154">None if updateCert is false or not provided.</span></span> <span data-ttu-id="33cda-155">Andernfalls mehrteiliger konformer http-Text, der die Datei FiddlerRoot.cer enthält.</span><span class="sxs-lookup"><span data-stu-id="33cda-155">Multi-part conforming http body containing the FiddlerRoot.cer file otherwise.</span></span>

**<span data-ttu-id="33cda-156">Antwort</span><span class="sxs-lookup"><span data-stu-id="33cda-156">Response</span></span>**   

- <span data-ttu-id="33cda-157">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-157">None</span></span>  

**<span data-ttu-id="33cda-158">Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-158">Status code</span></span>**

<span data-ttu-id="33cda-159">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="33cda-159">This API has the following expected status codes.</span></span>

<span data-ttu-id="33cda-160">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-160">HTTP status code</span></span>      | <span data-ttu-id="33cda-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33cda-161">Description</span></span>
:------     | :-----
<span data-ttu-id="33cda-162">204</span><span class="sxs-lookup"><span data-stu-id="33cda-162">204</span></span> | <span data-ttu-id="33cda-163">Die Anforderung für die Aktivierung von Fiddler wurde akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="33cda-163">The request to enable Fiddler was accepted.</span></span> <span data-ttu-id="33cda-164">Fiddler wird aktiviert, wenn das Gerät das nächste Mal neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-164">Fiddler will be enabled the next time the device reboots.</span></span>
<span data-ttu-id="33cda-165">4XX</span><span class="sxs-lookup"><span data-stu-id="33cda-165">4XX</span></span> | <span data-ttu-id="33cda-166">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-166">Error codes</span></span>
<span data-ttu-id="33cda-167">5XX</span><span class="sxs-lookup"><span data-stu-id="33cda-167">5XX</span></span> | <span data-ttu-id="33cda-168">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-168">Error codes</span></span>

## <a name="disable-fiddler-tracing-on-the-devkit"></a><span data-ttu-id="33cda-169">Deaktivieren Sie die Fiddler-Ablaufverfolgung für das Dev Kit.</span><span class="sxs-lookup"><span data-stu-id="33cda-169">Disable Fiddler tracing on the devkit</span></span>

**<span data-ttu-id="33cda-170">Anforderung</span><span class="sxs-lookup"><span data-stu-id="33cda-170">Request</span></span>**

<span data-ttu-id="33cda-171">Sie können die Fiddler-Ablaufverfolgung mithilfe der folgenden Anforderung für das Gerät deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="33cda-171">You can disable Fiddler tracing on the device using the following request.</span></span> <span data-ttu-id="33cda-172">Beachten Sie, dass das Gerät neu gestartet werden muss, bevor dies wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-172">Note that the device must be restarted before this takes effect.</span></span>

<span data-ttu-id="33cda-173">Methode</span><span class="sxs-lookup"><span data-stu-id="33cda-173">Method</span></span>      | <span data-ttu-id="33cda-174">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="33cda-174">Request URI</span></span>
:------     | :-----
<span data-ttu-id="33cda-175">DELETE</span><span class="sxs-lookup"><span data-stu-id="33cda-175">DELETE</span></span> | <span data-ttu-id="33cda-176">/ext/fiddler</span><span class="sxs-lookup"><span data-stu-id="33cda-176">/ext/fiddler</span></span>
<br />
**<span data-ttu-id="33cda-177">URI-Parameter</span><span class="sxs-lookup"><span data-stu-id="33cda-177">URI parameters</span></span>**

- <span data-ttu-id="33cda-178">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-178">None</span></span>

**<span data-ttu-id="33cda-179">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="33cda-179">Request headers</span></span>**

- <span data-ttu-id="33cda-180">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-180">None</span></span>

**<span data-ttu-id="33cda-181">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="33cda-181">Request body</span></span>**   

- <span data-ttu-id="33cda-182">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-182">None</span></span>

**<span data-ttu-id="33cda-183">Antwort</span><span class="sxs-lookup"><span data-stu-id="33cda-183">Response</span></span>**   

- <span data-ttu-id="33cda-184">Keine</span><span class="sxs-lookup"><span data-stu-id="33cda-184">None</span></span> 

**<span data-ttu-id="33cda-185">Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-185">Status code</span></span>**

<span data-ttu-id="33cda-186">Diese API hat die folgenden erwarteten Statuscodes:</span><span class="sxs-lookup"><span data-stu-id="33cda-186">This API has the following expected status codes.</span></span>

<span data-ttu-id="33cda-187">HTTP-Statuscode</span><span class="sxs-lookup"><span data-stu-id="33cda-187">HTTP status code</span></span>      | <span data-ttu-id="33cda-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33cda-188">Description</span></span>
:------     | :-----
<span data-ttu-id="33cda-189">204</span><span class="sxs-lookup"><span data-stu-id="33cda-189">204</span></span> | <span data-ttu-id="33cda-190">Die Anforderung zum Deaktivieren der Fiddler-Ablaufverfolgung war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="33cda-190">The request to disable Fiddler tracing was successful.</span></span> <span data-ttu-id="33cda-191">Die Nachverfolgung wird deaktiviert, wenn das Gerät das nächste Mal neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="33cda-191">Tracing will be disabled on the next reboot of the device.</span></span>
<span data-ttu-id="33cda-192">4XX</span><span class="sxs-lookup"><span data-stu-id="33cda-192">4XX</span></span> | <span data-ttu-id="33cda-193">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-193">Error codes</span></span>
<span data-ttu-id="33cda-194">5XX</span><span class="sxs-lookup"><span data-stu-id="33cda-194">5XX</span></span> | <span data-ttu-id="33cda-195">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="33cda-195">Error codes</span></span>

<br />
**<span data-ttu-id="33cda-196">Verfügbare Gerätefamilien</span><span class="sxs-lookup"><span data-stu-id="33cda-196">Available device families</span></span>**

* <span data-ttu-id="33cda-197">Windows Xbox</span><span class="sxs-lookup"><span data-stu-id="33cda-197">Windows Xbox</span></span>

## <a name="see-also"></a><span data-ttu-id="33cda-198">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="33cda-198">See also</span></span>
- [<span data-ttu-id="33cda-199">Konfigurieren von Fiddler für UWP auf Xbox</span><span class="sxs-lookup"><span data-stu-id="33cda-199">Configuring Fiddler for UWP on Xbox</span></span>](uwp-fiddler.md)

