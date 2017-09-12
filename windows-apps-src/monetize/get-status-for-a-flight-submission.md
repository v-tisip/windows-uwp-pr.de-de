---
author: mcleanbyron
ms.assetid: C78176D6-47BB-4C63-92F8-426719A70F04
description: "Verwenden Sie diese Methode der Windows Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen."
title: "Abrufen des Status einer Flight-Paketübermittlung"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Flight-Übermittlung, Status"
ms.openlocfilehash: 9397b0e3bd43ae77fd68e564c0af9a1c4ad67282
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="get-the-status-of-a-package-flight-submission"></a><span data-ttu-id="0f2bf-104">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-104">Get the status of a package flight submission</span></span>




<span data-ttu-id="0f2bf-105">Verwenden Sie diese Methode der Windows Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-105">Use this method in the Windows Store submission API to get the status of a package flight submission.</span></span> <span data-ttu-id="0f2bf-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Windows Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="0f2bf-106">For more information about the process of process of creating a package flight submission by using the Windows Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f2bf-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0f2bf-107">Prerequisites</span></span>

<span data-ttu-id="0f2bf-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="0f2bf-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="0f2bf-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="0f2bf-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="0f2bf-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="0f2bf-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="0f2bf-113">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-113">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="0f2bf-114">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-114">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="0f2bf-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-115">Request</span></span>

<span data-ttu-id="0f2bf-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-116">This method has the following syntax.</span></span> <span data-ttu-id="0f2bf-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="0f2bf-118">Methode</span><span class="sxs-lookup"><span data-stu-id="0f2bf-118">Method</span></span> | <span data-ttu-id="0f2bf-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="0f2bf-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="0f2bf-120">GET</span><span class="sxs-lookup"><span data-stu-id="0f2bf-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions{submissionId}/status``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="0f2bf-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="0f2bf-121">Request header</span></span>

| <span data-ttu-id="0f2bf-122">Header</span><span class="sxs-lookup"><span data-stu-id="0f2bf-122">Header</span></span>        | <span data-ttu-id="0f2bf-123">Typ</span><span class="sxs-lookup"><span data-stu-id="0f2bf-123">Type</span></span>   | <span data-ttu-id="0f2bf-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="0f2bf-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-125">Authorization</span></span> | <span data-ttu-id="0f2bf-126">String</span><span class="sxs-lookup"><span data-stu-id="0f2bf-126">string</span></span> | <span data-ttu-id="0f2bf-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-127">Required.</span></span> <span data-ttu-id="0f2bf-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="0f2bf-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="0f2bf-129">Request parameters</span></span>

| <span data-ttu-id="0f2bf-130">Name</span><span class="sxs-lookup"><span data-stu-id="0f2bf-130">Name</span></span>        | <span data-ttu-id="0f2bf-131">Typ</span><span class="sxs-lookup"><span data-stu-id="0f2bf-131">Type</span></span>   | <span data-ttu-id="0f2bf-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="0f2bf-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="0f2bf-133">applicationId</span></span> | <span data-ttu-id="0f2bf-134">String</span><span class="sxs-lookup"><span data-stu-id="0f2bf-134">string</span></span> | <span data-ttu-id="0f2bf-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-135">Required.</span></span> <span data-ttu-id="0f2bf-136">Die Store-ID der App mit der Flight-Paketübermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-136">The Store ID of the app that contains the package flight submission for which you want to get the status.</span></span> <span data-ttu-id="0f2bf-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="0f2bf-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="0f2bf-138">flightId</span><span class="sxs-lookup"><span data-stu-id="0f2bf-138">flightId</span></span> | <span data-ttu-id="0f2bf-139">String</span><span class="sxs-lookup"><span data-stu-id="0f2bf-139">string</span></span> | <span data-ttu-id="0f2bf-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-140">Required.</span></span> <span data-ttu-id="0f2bf-141">Die ID des Flight-Pakets mit der Übermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-141">The ID of the package flight that contains the submission for which you want to get the status.</span></span> <span data-ttu-id="0f2bf-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |
| <span data-ttu-id="0f2bf-143">submissionId</span><span class="sxs-lookup"><span data-stu-id="0f2bf-143">submissionId</span></span> | <span data-ttu-id="0f2bf-144">String</span><span class="sxs-lookup"><span data-stu-id="0f2bf-144">string</span></span> | <span data-ttu-id="0f2bf-145">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-145">Required.</span></span> <span data-ttu-id="0f2bf-146">Die ID der Übermittlung, für die der Status abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-146">The ID of the submission for which you want to get the status.</span></span> <span data-ttu-id="0f2bf-147">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-147">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="0f2bf-148">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="0f2bf-148">Request body</span></span>

<span data-ttu-id="0f2bf-149">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-149">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="0f2bf-150">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="0f2bf-150">Request example</span></span>

<span data-ttu-id="0f2bf-151">Im folgenden Beispiel wird veranschaulicht, wie der Status einer Flight-Paketübermittlung abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-151">The following example demonstrates how to get the status of a package flight submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/status HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="0f2bf-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="0f2bf-152">Response</span></span>

<span data-ttu-id="0f2bf-153">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-153">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="0f2bf-154">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-154">The response body contains information about the specified submission.</span></span> <span data-ttu-id="0f2bf-155">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-155">For more details about the values in the response body, see the following section.</span></span>

```json
{
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [],
    "warnings": [],
    "certificationReports": []
  },
}
```

### <a name="response-body"></a><span data-ttu-id="0f2bf-156">Antworttext</span><span class="sxs-lookup"><span data-stu-id="0f2bf-156">Response body</span></span>

| <span data-ttu-id="0f2bf-157">Wert</span><span class="sxs-lookup"><span data-stu-id="0f2bf-157">Value</span></span>      | <span data-ttu-id="0f2bf-158">Typ</span><span class="sxs-lookup"><span data-stu-id="0f2bf-158">Type</span></span>   | <span data-ttu-id="0f2bf-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-159">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0f2bf-160">status</span><span class="sxs-lookup"><span data-stu-id="0f2bf-160">status</span></span>           | <span data-ttu-id="0f2bf-161">string</span><span class="sxs-lookup"><span data-stu-id="0f2bf-161">string</span></span>  | <span data-ttu-id="0f2bf-162">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-162">The status of the submission.</span></span> <span data-ttu-id="0f2bf-163">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="0f2bf-163">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="0f2bf-164">None</span><span class="sxs-lookup"><span data-stu-id="0f2bf-164">None</span></span></li><li><span data-ttu-id="0f2bf-165">Canceled</span><span class="sxs-lookup"><span data-stu-id="0f2bf-165">Canceled</span></span></li><li><span data-ttu-id="0f2bf-166">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="0f2bf-166">PendingCommit</span></span></li><li><span data-ttu-id="0f2bf-167">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="0f2bf-167">CommitStarted</span></span></li><li><span data-ttu-id="0f2bf-168">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="0f2bf-168">CommitFailed</span></span></li><li><span data-ttu-id="0f2bf-169">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="0f2bf-169">PendingPublication</span></span></li><li><span data-ttu-id="0f2bf-170">Publishing</span><span class="sxs-lookup"><span data-stu-id="0f2bf-170">Publishing</span></span></li><li><span data-ttu-id="0f2bf-171">Published</span><span class="sxs-lookup"><span data-stu-id="0f2bf-171">Published</span></span></li><li><span data-ttu-id="0f2bf-172">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="0f2bf-172">PublishFailed</span></span></li><li><span data-ttu-id="0f2bf-173">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="0f2bf-173">PreProcessing</span></span></li><li><span data-ttu-id="0f2bf-174">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="0f2bf-174">PreProcessingFailed</span></span></li><li><span data-ttu-id="0f2bf-175">Certification</span><span class="sxs-lookup"><span data-stu-id="0f2bf-175">Certification</span></span></li><li><span data-ttu-id="0f2bf-176">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="0f2bf-176">CertificationFailed</span></span></li><li><span data-ttu-id="0f2bf-177">Release</span><span class="sxs-lookup"><span data-stu-id="0f2bf-177">Release</span></span></li><li><span data-ttu-id="0f2bf-178">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="0f2bf-178">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="0f2bf-179">statusDetails</span><span class="sxs-lookup"><span data-stu-id="0f2bf-179">statusDetails</span></span>           | <span data-ttu-id="0f2bf-180">Objekt</span><span class="sxs-lookup"><span data-stu-id="0f2bf-180">object</span></span>  |  <span data-ttu-id="0f2bf-181">Enthält zusätzliche Details über den Status der Übermittlung, einschließlich Informationen zu Fehlern.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-181">Contains additional details about the status of the submission, including information about any errors.</span></span> <span data-ttu-id="0f2bf-182">Weitere Informationen finden Sie unter [Statusdetails-Ressource](manage-flight-submissions.md#status-details-object).</span><span class="sxs-lookup"><span data-stu-id="0f2bf-182">For more information, see [Status details resource](manage-flight-submissions.md#status-details-object).</span></span> |


<span/>

## <a name="error-codes"></a><span data-ttu-id="0f2bf-183">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="0f2bf-183">Error codes</span></span>

<span data-ttu-id="0f2bf-184">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-184">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="0f2bf-185">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="0f2bf-185">Error code</span></span> |  <span data-ttu-id="0f2bf-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-186">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="0f2bf-187">404</span><span class="sxs-lookup"><span data-stu-id="0f2bf-187">404</span></span>  | <span data-ttu-id="0f2bf-188">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="0f2bf-188">The submission could not be found.</span></span> |
| <span data-ttu-id="0f2bf-189">409</span><span class="sxs-lookup"><span data-stu-id="0f2bf-189">409</span></span>  | <span data-ttu-id="0f2bf-190">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="0f2bf-190">The app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |

<span/>


## <a name="related-topics"></a><span data-ttu-id="0f2bf-191">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0f2bf-191">Related topics</span></span>

* [<span data-ttu-id="0f2bf-192">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="0f2bf-192">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="0f2bf-193">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="0f2bf-193">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="0f2bf-194">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-194">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="0f2bf-195">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-195">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="0f2bf-196">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-196">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="0f2bf-197">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-197">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="0f2bf-198">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="0f2bf-198">Delete an app submission</span></span>](delete-an-app-submission.md)
