---
author: mcleanbyron
ms.assetid: F94AF8F6-0742-4A3F-938E-177472F96C00
description: "Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API, um eine neue oder aktualisierte Flight-Paketübermittlung in Windows Dev Center zu übernehmen."
title: "Ausführen eines Commit für eine Flight-Paket-Übermittlung"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Übernehmen einer Flight-Übermittlung"
ms.openlocfilehash: e0fd115dc5e394abe6c0353ba41ebc35fde086c4
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="commit-a-package-flight-submission"></a><span data-ttu-id="4b341-104">Ausführen eines Commit für eine Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-104">Commit a package flight submission</span></span>




<span data-ttu-id="4b341-105">Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API, um eine neue oder aktualisierte Flight-Paketübermittlung in Windows Dev Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="4b341-105">Use this method in the Windows Store submission API to commit a new or updated package flight submission to Windows Dev Center.</span></span> <span data-ttu-id="4b341-106">Durch die Übernahmeaktion wird Dev Center darüber benachrichtigt, dass die Übermittlungsdaten (darunter alle zugehörigen Pakete) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="4b341-106">The commit action alerts Dev Center that the submission data has been uploaded (including any related packages).</span></span> <span data-ttu-id="4b341-107">Als Reaktion übernimmt Dev Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="4b341-107">In response, Dev Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="4b341-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen der Übermittlung im Dev Center-Dashboard angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b341-108">After the commit operation succeeds, the changes to the submission are shown in the Dev Center dashboard.</span></span>

<span data-ttu-id="4b341-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zum Erstellen einer Flight-Paketübermittlung mit der Windows Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="4b341-109">For more information about how the commit operation fits into the process of creating a package flight submission by using the Windows Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b341-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4b341-110">Prerequisites</span></span>

<span data-ttu-id="4b341-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="4b341-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="4b341-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="4b341-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="4b341-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4b341-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="4b341-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="4b341-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="4b341-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="4b341-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="4b341-116">[Erstellen Sie eine Flight-Paketübermittlung](create-a-flight-submission.md), und [aktualisieren Sie die Übermittlung](update-a-flight-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="4b341-116">[Create a package flight submission](create-a-flight-submission.md) and then [update the submission](update-a-flight-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="4b341-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="4b341-117">Request</span></span>

<span data-ttu-id="4b341-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="4b341-118">This method has the following syntax.</span></span> <span data-ttu-id="4b341-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="4b341-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="4b341-120">Methode</span><span class="sxs-lookup"><span data-stu-id="4b341-120">Method</span></span> | <span data-ttu-id="4b341-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="4b341-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="4b341-122">POST</span><span class="sxs-lookup"><span data-stu-id="4b341-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/commit``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="4b341-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="4b341-123">Request header</span></span>

| <span data-ttu-id="4b341-124">Header</span><span class="sxs-lookup"><span data-stu-id="4b341-124">Header</span></span>        | <span data-ttu-id="4b341-125">Typ</span><span class="sxs-lookup"><span data-stu-id="4b341-125">Type</span></span>   | <span data-ttu-id="4b341-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4b341-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="4b341-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="4b341-127">Authorization</span></span> | <span data-ttu-id="4b341-128">String</span><span class="sxs-lookup"><span data-stu-id="4b341-128">string</span></span> | <span data-ttu-id="4b341-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4b341-129">Required.</span></span> <span data-ttu-id="4b341-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="4b341-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="4b341-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="4b341-131">Request parameters</span></span>

| <span data-ttu-id="4b341-132">Name</span><span class="sxs-lookup"><span data-stu-id="4b341-132">Name</span></span>        | <span data-ttu-id="4b341-133">Typ</span><span class="sxs-lookup"><span data-stu-id="4b341-133">Type</span></span>   | <span data-ttu-id="4b341-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4b341-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="4b341-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="4b341-135">applicationId</span></span> | <span data-ttu-id="4b341-136">String</span><span class="sxs-lookup"><span data-stu-id="4b341-136">string</span></span> | <span data-ttu-id="4b341-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4b341-137">Required.</span></span> <span data-ttu-id="4b341-138">Die Store-ID der App, die die Flight-Paketübermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="4b341-138">The Store ID of the app that contains the package flight submission you want to commit.</span></span> <span data-ttu-id="4b341-139">Die Store-ID für die App ist im Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4b341-139">The Store ID for the app is available on the Dev Center dashboard.</span></span>  |
| <span data-ttu-id="4b341-140">flightId</span><span class="sxs-lookup"><span data-stu-id="4b341-140">flightId</span></span> | <span data-ttu-id="4b341-141">String</span><span class="sxs-lookup"><span data-stu-id="4b341-141">string</span></span> | <span data-ttu-id="4b341-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4b341-142">Required.</span></span> <span data-ttu-id="4b341-143">Die ID des Flight-Pakets, das die zu übernehmende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="4b341-143">The ID of the package flight that contains the submission to commit.</span></span> <span data-ttu-id="4b341-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="4b341-144">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |
| <span data-ttu-id="4b341-145">submissionId</span><span class="sxs-lookup"><span data-stu-id="4b341-145">submissionId</span></span> | <span data-ttu-id="4b341-146">String</span><span class="sxs-lookup"><span data-stu-id="4b341-146">string</span></span> | <span data-ttu-id="4b341-147">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4b341-147">Required.</span></span> <span data-ttu-id="4b341-148">Die ID der zu übernehmenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="4b341-148">The ID of the submission to commit.</span></span> <span data-ttu-id="4b341-149">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="4b341-149">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="4b341-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="4b341-150">Request body</span></span>

<span data-ttu-id="4b341-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="4b341-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="4b341-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="4b341-152">Request example</span></span>

<span data-ttu-id="4b341-153">Im folgenden Beispiel wird veranschaulicht, wie eine Flight-Paketübermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="4b341-153">The following example demonstrates how to commit a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="4b341-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="4b341-154">Response</span></span>

<span data-ttu-id="4b341-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="4b341-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="4b341-156">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="4b341-156">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="4b341-157">Antworttext</span><span class="sxs-lookup"><span data-stu-id="4b341-157">Response body</span></span>

| <span data-ttu-id="4b341-158">Wert</span><span class="sxs-lookup"><span data-stu-id="4b341-158">Value</span></span>      | <span data-ttu-id="4b341-159">Typ</span><span class="sxs-lookup"><span data-stu-id="4b341-159">Type</span></span>   | <span data-ttu-id="4b341-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4b341-160">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4b341-161">status</span><span class="sxs-lookup"><span data-stu-id="4b341-161">status</span></span>           | <span data-ttu-id="4b341-162">string</span><span class="sxs-lookup"><span data-stu-id="4b341-162">string</span></span>  | <span data-ttu-id="4b341-163">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="4b341-163">The status of the submission.</span></span> <span data-ttu-id="4b341-164">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="4b341-164">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="4b341-165">None</span><span class="sxs-lookup"><span data-stu-id="4b341-165">None</span></span></li><li><span data-ttu-id="4b341-166">Canceled</span><span class="sxs-lookup"><span data-stu-id="4b341-166">Canceled</span></span></li><li><span data-ttu-id="4b341-167">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="4b341-167">PendingCommit</span></span></li><li><span data-ttu-id="4b341-168">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="4b341-168">CommitStarted</span></span></li><li><span data-ttu-id="4b341-169">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="4b341-169">CommitFailed</span></span></li><li><span data-ttu-id="4b341-170">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="4b341-170">PendingPublication</span></span></li><li><span data-ttu-id="4b341-171">Publishing</span><span class="sxs-lookup"><span data-stu-id="4b341-171">Publishing</span></span></li><li><span data-ttu-id="4b341-172">Published</span><span class="sxs-lookup"><span data-stu-id="4b341-172">Published</span></span></li><li><span data-ttu-id="4b341-173">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="4b341-173">PublishFailed</span></span></li><li><span data-ttu-id="4b341-174">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="4b341-174">PreProcessing</span></span></li><li><span data-ttu-id="4b341-175">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="4b341-175">PreProcessingFailed</span></span></li><li><span data-ttu-id="4b341-176">Certification</span><span class="sxs-lookup"><span data-stu-id="4b341-176">Certification</span></span></li><li><span data-ttu-id="4b341-177">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="4b341-177">CertificationFailed</span></span></li><li><span data-ttu-id="4b341-178">Release</span><span class="sxs-lookup"><span data-stu-id="4b341-178">Release</span></span></li><li><span data-ttu-id="4b341-179">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="4b341-179">ReleaseFailed</span></span></li></ul>  |

<span/>

## <a name="error-codes"></a><span data-ttu-id="4b341-180">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4b341-180">Error codes</span></span>

<span data-ttu-id="4b341-181">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="4b341-181">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="4b341-182">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="4b341-182">Error code</span></span> |  <span data-ttu-id="4b341-183">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4b341-183">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="4b341-184">400</span><span class="sxs-lookup"><span data-stu-id="4b341-184">400</span></span>  | <span data-ttu-id="4b341-185">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="4b341-185">The request parameters are invalid.</span></span> |
| <span data-ttu-id="4b341-186">404</span><span class="sxs-lookup"><span data-stu-id="4b341-186">404</span></span>  | <span data-ttu-id="4b341-187">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="4b341-187">The specified submission could not be found.</span></span> |
| <span data-ttu-id="4b341-188">409</span><span class="sxs-lookup"><span data-stu-id="4b341-188">409</span></span>  | <span data-ttu-id="4b341-189">Die angegebene Übermittlung wurde gefunden, konnte jedoch nicht in ihrem aktuellen Zustand übernommen werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="4b341-189">The specified submission was found but it could not be committed in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |

<span/>


## <a name="related-topics"></a><span data-ttu-id="4b341-190">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="4b341-190">Related topics</span></span>

* [<span data-ttu-id="4b341-191">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="4b341-191">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="4b341-192">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="4b341-192">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="4b341-193">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-193">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="4b341-194">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-194">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="4b341-195">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-195">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="4b341-196">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-196">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="4b341-197">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4b341-197">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
