---
ms.assetid: 934F2DBF-2C7E-4B77-997D-17B9B0535D51
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte app-Übermittlung in Partner Center zu übernehmen.
title: Ausführen eines Commit für eine App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Übernehmen einer App-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 3a860239bcd266f577abca3af1cfc994393cae8e
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8942998"
---
# <a name="commit-an-app-submission"></a><span data-ttu-id="c97c0-104">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-104">Commit an app submission</span></span>


<span data-ttu-id="c97c0-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte app-Übermittlung in Partner Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="c97c0-105">Use this method in the Microsoft Store submission API to commit a new or updated app submission to  Partner Center.</span></span> <span data-ttu-id="c97c0-106">Die übernahmeaktion Partner Center, dass die Übermittlungsdaten (darunter alle zugehörigen Pakete und Bilder) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="c97c0-106">The commit action alerts Partner Center that the submission data has been uploaded (including any related packages and images).</span></span> <span data-ttu-id="c97c0-107">Als Reaktion übernimmt Partner Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="c97c0-107">In response, Partner Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="c97c0-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen an der Übermittlung im Partner Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c97c0-108">After the commit operation succeeds, the changes to the submission are shown in Partner Center.</span></span>

<span data-ttu-id="c97c0-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zur Übermittlung einer App mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="c97c0-109">For more information about how the commit operation fits into the process of submitting an app by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c97c0-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c97c0-110">Prerequisites</span></span>

<span data-ttu-id="c97c0-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="c97c0-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="c97c0-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="c97c0-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="c97c0-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c97c0-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="c97c0-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="c97c0-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="c97c0-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="c97c0-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="c97c0-116">[Erstellen Sie eine App-Übermittlung](create-an-app-submission.md), und [aktualisieren Sie die Übermittlung](update-an-app-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="c97c0-116">[Create an app submission](create-an-app-submission.md) and then [update the submission](update-an-app-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="c97c0-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c97c0-117">Request</span></span>

<span data-ttu-id="c97c0-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="c97c0-118">This method has the following syntax.</span></span> <span data-ttu-id="c97c0-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="c97c0-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="c97c0-120">Methode</span><span class="sxs-lookup"><span data-stu-id="c97c0-120">Method</span></span> | <span data-ttu-id="c97c0-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c97c0-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="c97c0-122">POST</span><span class="sxs-lookup"><span data-stu-id="c97c0-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/commit``` |


### <a name="request-header"></a><span data-ttu-id="c97c0-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c97c0-123">Request header</span></span>

| <span data-ttu-id="c97c0-124">Header</span><span class="sxs-lookup"><span data-stu-id="c97c0-124">Header</span></span>        | <span data-ttu-id="c97c0-125">Typ</span><span class="sxs-lookup"><span data-stu-id="c97c0-125">Type</span></span>   | <span data-ttu-id="c97c0-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c97c0-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c97c0-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="c97c0-127">Authorization</span></span> | <span data-ttu-id="c97c0-128">String</span><span class="sxs-lookup"><span data-stu-id="c97c0-128">string</span></span> | <span data-ttu-id="c97c0-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c97c0-129">Required.</span></span> <span data-ttu-id="c97c0-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="c97c0-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="c97c0-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="c97c0-131">Request parameters</span></span>

| <span data-ttu-id="c97c0-132">Name</span><span class="sxs-lookup"><span data-stu-id="c97c0-132">Name</span></span>        | <span data-ttu-id="c97c0-133">Typ</span><span class="sxs-lookup"><span data-stu-id="c97c0-133">Type</span></span>   | <span data-ttu-id="c97c0-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c97c0-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c97c0-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="c97c0-135">applicationId</span></span> | <span data-ttu-id="c97c0-136">String</span><span class="sxs-lookup"><span data-stu-id="c97c0-136">string</span></span> | <span data-ttu-id="c97c0-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c97c0-137">Required.</span></span> <span data-ttu-id="c97c0-138">Die Store-ID der App, die die Übermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="c97c0-138">The Store ID of the app that contains the submission you want to commit.</span></span> <span data-ttu-id="c97c0-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="c97c0-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="c97c0-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="c97c0-140">submissionId</span></span> | <span data-ttu-id="c97c0-141">String</span><span class="sxs-lookup"><span data-stu-id="c97c0-141">string</span></span> | <span data-ttu-id="c97c0-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c97c0-142">Required.</span></span> <span data-ttu-id="c97c0-143">Die ID der Übermittlung, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="c97c0-143">The ID of the submission you want to commit.</span></span> <span data-ttu-id="c97c0-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c97c0-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="c97c0-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c97c0-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="c97c0-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c97c0-146">Request body</span></span>

<span data-ttu-id="c97c0-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="c97c0-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="c97c0-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="c97c0-148">Request example</span></span>

<span data-ttu-id="c97c0-149">Im folgenden Beispiel wird veranschaulicht, wie eine App-Übermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="c97c0-149">The following example demonstrates how to commit an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243610/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="c97c0-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="c97c0-150">Response</span></span>

<span data-ttu-id="c97c0-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="c97c0-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="c97c0-152">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="c97c0-152">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="c97c0-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="c97c0-153">Response body</span></span>

| <span data-ttu-id="c97c0-154">Wert</span><span class="sxs-lookup"><span data-stu-id="c97c0-154">Value</span></span>      | <span data-ttu-id="c97c0-155">Typ</span><span class="sxs-lookup"><span data-stu-id="c97c0-155">Type</span></span>   | <span data-ttu-id="c97c0-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c97c0-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c97c0-157">status</span><span class="sxs-lookup"><span data-stu-id="c97c0-157">status</span></span>           | <span data-ttu-id="c97c0-158">string</span><span class="sxs-lookup"><span data-stu-id="c97c0-158">string</span></span>  | <span data-ttu-id="c97c0-159">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="c97c0-159">The status of the submission.</span></span> <span data-ttu-id="c97c0-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="c97c0-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="c97c0-161">None</span><span class="sxs-lookup"><span data-stu-id="c97c0-161">None</span></span></li><li><span data-ttu-id="c97c0-162">Canceled</span><span class="sxs-lookup"><span data-stu-id="c97c0-162">Canceled</span></span></li><li><span data-ttu-id="c97c0-163">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="c97c0-163">PendingCommit</span></span></li><li><span data-ttu-id="c97c0-164">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="c97c0-164">CommitStarted</span></span></li><li><span data-ttu-id="c97c0-165">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="c97c0-165">CommitFailed</span></span></li><li><span data-ttu-id="c97c0-166">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="c97c0-166">PendingPublication</span></span></li><li><span data-ttu-id="c97c0-167">Publishing</span><span class="sxs-lookup"><span data-stu-id="c97c0-167">Publishing</span></span></li><li><span data-ttu-id="c97c0-168">Published</span><span class="sxs-lookup"><span data-stu-id="c97c0-168">Published</span></span></li><li><span data-ttu-id="c97c0-169">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="c97c0-169">PublishFailed</span></span></li><li><span data-ttu-id="c97c0-170">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="c97c0-170">PreProcessing</span></span></li><li><span data-ttu-id="c97c0-171">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="c97c0-171">PreProcessingFailed</span></span></li><li><span data-ttu-id="c97c0-172">Certification</span><span class="sxs-lookup"><span data-stu-id="c97c0-172">Certification</span></span></li><li><span data-ttu-id="c97c0-173">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="c97c0-173">CertificationFailed</span></span></li><li><span data-ttu-id="c97c0-174">Release</span><span class="sxs-lookup"><span data-stu-id="c97c0-174">Release</span></span></li><li><span data-ttu-id="c97c0-175">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="c97c0-175">ReleaseFailed</span></span></li></ul>  |


## <a name="error-codes"></a><span data-ttu-id="c97c0-176">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c97c0-176">Error codes</span></span>

<span data-ttu-id="c97c0-177">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="c97c0-177">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="c97c0-178">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="c97c0-178">Error code</span></span> |  <span data-ttu-id="c97c0-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c97c0-179">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="c97c0-180">400</span><span class="sxs-lookup"><span data-stu-id="c97c0-180">400</span></span>  | <span data-ttu-id="c97c0-181">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="c97c0-181">The request parameters are invalid.</span></span> |
| <span data-ttu-id="c97c0-182">404</span><span class="sxs-lookup"><span data-stu-id="c97c0-182">404</span></span>  | <span data-ttu-id="c97c0-183">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="c97c0-183">The specified submission could not be found.</span></span> |
| <span data-ttu-id="c97c0-184">409</span><span class="sxs-lookup"><span data-stu-id="c97c0-184">409</span></span>  | <span data-ttu-id="c97c0-185">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand übernommen werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="c97c0-185">The specified submission was found but it could not be committed in its current state, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="c97c0-186">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c97c0-186">Related topics</span></span>

* [<span data-ttu-id="c97c0-187">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="c97c0-187">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="c97c0-188">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-188">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="c97c0-189">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-189">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="c97c0-190">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-190">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="c97c0-191">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-191">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="c97c0-192">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c97c0-192">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
