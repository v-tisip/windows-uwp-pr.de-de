---
author: Xansky
ms.assetid: 934F2DBF-2C7E-4B77-997D-17B9B0535D51
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte app-Übermittlung in Partner Center zu übernehmen.
title: Ausführen eines Commit für eine App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Übernehmen einer App-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 7a61fb1568cf85d01a31e5921fa757d3e8c767ff
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6673531"
---
# <a name="commit-an-app-submission"></a><span data-ttu-id="9ec2b-104">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-104">Commit an app submission</span></span>


<span data-ttu-id="9ec2b-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte app-Übermittlung in Partner Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-105">Use this method in the Microsoft Store submission API to commit a new or updated app submission to  Partner Center.</span></span> <span data-ttu-id="9ec2b-106">Die übernahmeaktion Partner Center, dass die Übermittlungsdaten (darunter alle zugehörigen Pakete und Bilder) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-106">The commit action alerts Partner Center that the submission data has been uploaded (including any related packages and images).</span></span> <span data-ttu-id="9ec2b-107">Als Reaktion übernimmt Partner Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-107">In response, Partner Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="9ec2b-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen an der Übermittlung im Partner Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-108">After the commit operation succeeds, the changes to the submission are shown in Partner Center.</span></span>

<span data-ttu-id="9ec2b-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zur Übermittlung einer App mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="9ec2b-109">For more information about how the commit operation fits into the process of submitting an app by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ec2b-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9ec2b-110">Prerequisites</span></span>

<span data-ttu-id="9ec2b-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="9ec2b-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="9ec2b-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="9ec2b-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="9ec2b-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="9ec2b-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="9ec2b-116">[Erstellen Sie eine App-Übermittlung](create-an-app-submission.md), und [aktualisieren Sie die Übermittlung](update-an-app-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-116">[Create an app submission](create-an-app-submission.md) and then [update the submission](update-an-app-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="9ec2b-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-117">Request</span></span>

<span data-ttu-id="9ec2b-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-118">This method has the following syntax.</span></span> <span data-ttu-id="9ec2b-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="9ec2b-120">Methode</span><span class="sxs-lookup"><span data-stu-id="9ec2b-120">Method</span></span> | <span data-ttu-id="9ec2b-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="9ec2b-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="9ec2b-122">POST</span><span class="sxs-lookup"><span data-stu-id="9ec2b-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/commit``` |


### <a name="request-header"></a><span data-ttu-id="9ec2b-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="9ec2b-123">Request header</span></span>

| <span data-ttu-id="9ec2b-124">Header</span><span class="sxs-lookup"><span data-stu-id="9ec2b-124">Header</span></span>        | <span data-ttu-id="9ec2b-125">Typ</span><span class="sxs-lookup"><span data-stu-id="9ec2b-125">Type</span></span>   | <span data-ttu-id="9ec2b-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="9ec2b-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-127">Authorization</span></span> | <span data-ttu-id="9ec2b-128">String</span><span class="sxs-lookup"><span data-stu-id="9ec2b-128">string</span></span> | <span data-ttu-id="9ec2b-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-129">Required.</span></span> <span data-ttu-id="9ec2b-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="9ec2b-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="9ec2b-131">Request parameters</span></span>

| <span data-ttu-id="9ec2b-132">Name</span><span class="sxs-lookup"><span data-stu-id="9ec2b-132">Name</span></span>        | <span data-ttu-id="9ec2b-133">Typ</span><span class="sxs-lookup"><span data-stu-id="9ec2b-133">Type</span></span>   | <span data-ttu-id="9ec2b-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="9ec2b-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="9ec2b-135">applicationId</span></span> | <span data-ttu-id="9ec2b-136">String</span><span class="sxs-lookup"><span data-stu-id="9ec2b-136">string</span></span> | <span data-ttu-id="9ec2b-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-137">Required.</span></span> <span data-ttu-id="9ec2b-138">Die Store-ID der App, die die Übermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-138">The Store ID of the app that contains the submission you want to commit.</span></span> <span data-ttu-id="9ec2b-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="9ec2b-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="9ec2b-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="9ec2b-140">submissionId</span></span> | <span data-ttu-id="9ec2b-141">String</span><span class="sxs-lookup"><span data-stu-id="9ec2b-141">string</span></span> | <span data-ttu-id="9ec2b-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-142">Required.</span></span> <span data-ttu-id="9ec2b-143">Die ID der Übermittlung, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-143">The ID of the submission you want to commit.</span></span> <span data-ttu-id="9ec2b-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="9ec2b-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="9ec2b-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="9ec2b-146">Request body</span></span>

<span data-ttu-id="9ec2b-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="9ec2b-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="9ec2b-148">Request example</span></span>

<span data-ttu-id="9ec2b-149">Im folgenden Beispiel wird veranschaulicht, wie eine App-Übermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-149">The following example demonstrates how to commit an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243610/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="9ec2b-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="9ec2b-150">Response</span></span>

<span data-ttu-id="9ec2b-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="9ec2b-152">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-152">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="9ec2b-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="9ec2b-153">Response body</span></span>

| <span data-ttu-id="9ec2b-154">Wert</span><span class="sxs-lookup"><span data-stu-id="9ec2b-154">Value</span></span>      | <span data-ttu-id="9ec2b-155">Typ</span><span class="sxs-lookup"><span data-stu-id="9ec2b-155">Type</span></span>   | <span data-ttu-id="9ec2b-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9ec2b-157">status</span><span class="sxs-lookup"><span data-stu-id="9ec2b-157">status</span></span>           | <span data-ttu-id="9ec2b-158">string</span><span class="sxs-lookup"><span data-stu-id="9ec2b-158">string</span></span>  | <span data-ttu-id="9ec2b-159">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-159">The status of the submission.</span></span> <span data-ttu-id="9ec2b-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="9ec2b-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="9ec2b-161">None</span><span class="sxs-lookup"><span data-stu-id="9ec2b-161">None</span></span></li><li><span data-ttu-id="9ec2b-162">Canceled</span><span class="sxs-lookup"><span data-stu-id="9ec2b-162">Canceled</span></span></li><li><span data-ttu-id="9ec2b-163">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="9ec2b-163">PendingCommit</span></span></li><li><span data-ttu-id="9ec2b-164">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="9ec2b-164">CommitStarted</span></span></li><li><span data-ttu-id="9ec2b-165">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="9ec2b-165">CommitFailed</span></span></li><li><span data-ttu-id="9ec2b-166">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="9ec2b-166">PendingPublication</span></span></li><li><span data-ttu-id="9ec2b-167">Publishing</span><span class="sxs-lookup"><span data-stu-id="9ec2b-167">Publishing</span></span></li><li><span data-ttu-id="9ec2b-168">Published</span><span class="sxs-lookup"><span data-stu-id="9ec2b-168">Published</span></span></li><li><span data-ttu-id="9ec2b-169">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="9ec2b-169">PublishFailed</span></span></li><li><span data-ttu-id="9ec2b-170">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="9ec2b-170">PreProcessing</span></span></li><li><span data-ttu-id="9ec2b-171">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="9ec2b-171">PreProcessingFailed</span></span></li><li><span data-ttu-id="9ec2b-172">Certification</span><span class="sxs-lookup"><span data-stu-id="9ec2b-172">Certification</span></span></li><li><span data-ttu-id="9ec2b-173">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="9ec2b-173">CertificationFailed</span></span></li><li><span data-ttu-id="9ec2b-174">Release</span><span class="sxs-lookup"><span data-stu-id="9ec2b-174">Release</span></span></li><li><span data-ttu-id="9ec2b-175">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="9ec2b-175">ReleaseFailed</span></span></li></ul>  |


## <a name="error-codes"></a><span data-ttu-id="9ec2b-176">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="9ec2b-176">Error codes</span></span>

<span data-ttu-id="9ec2b-177">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-177">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="9ec2b-178">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="9ec2b-178">Error code</span></span> |  <span data-ttu-id="9ec2b-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-179">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="9ec2b-180">400</span><span class="sxs-lookup"><span data-stu-id="9ec2b-180">400</span></span>  | <span data-ttu-id="9ec2b-181">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-181">The request parameters are invalid.</span></span> |
| <span data-ttu-id="9ec2b-182">404</span><span class="sxs-lookup"><span data-stu-id="9ec2b-182">404</span></span>  | <span data-ttu-id="9ec2b-183">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-183">The specified submission could not be found.</span></span> |
| <span data-ttu-id="9ec2b-184">409</span><span class="sxs-lookup"><span data-stu-id="9ec2b-184">409</span></span>  | <span data-ttu-id="9ec2b-185">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand übernommen werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="9ec2b-185">The specified submission was found but it could not be committed in its current state, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="9ec2b-186">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9ec2b-186">Related topics</span></span>

* [<span data-ttu-id="9ec2b-187">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="9ec2b-187">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="9ec2b-188">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-188">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="9ec2b-189">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-189">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="9ec2b-190">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-190">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="9ec2b-191">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-191">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="9ec2b-192">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9ec2b-192">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
