---
author: Xansky
ms.assetid: 934F2DBF-2C7E-4B77-997D-17B9B0535D51
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte App-Übermittlung in Windows Dev Center zu übernehmen.
title: Ausführen eines Commit für eine App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Übernehmen einer App-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 5e720e017eb77aad4a2696039b9fd076daf3db9e
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4621697"
---
# <a name="commit-an-app-submission"></a><span data-ttu-id="5a96f-104">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-104">Commit an app submission</span></span>


<span data-ttu-id="5a96f-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte App-Übermittlung in Windows Dev Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="5a96f-105">Use this method in the Microsoft Store submission API to commit a new or updated app submission to Windows Dev Center.</span></span> <span data-ttu-id="5a96f-106">Durch die Übernahmeaktion wird Dev Center darüber benachrichtigt, dass die Übermittlungsdaten (darunter alle zugehörigen Pakete und Bilder) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="5a96f-106">The commit action alerts Dev Center that the submission data has been uploaded (including any related packages and images).</span></span> <span data-ttu-id="5a96f-107">Als Reaktion übernimmt Dev Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="5a96f-107">In response, Dev Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="5a96f-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen der Übermittlung im Dev Center-Dashboard angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a96f-108">After the commit operation succeeds, the changes to the submission are shown in the Dev Center dashboard.</span></span>

<span data-ttu-id="5a96f-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zur Übermittlung einer App mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="5a96f-109">For more information about how the commit operation fits into the process of submitting an app by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a96f-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5a96f-110">Prerequisites</span></span>

<span data-ttu-id="5a96f-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="5a96f-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="5a96f-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="5a96f-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="5a96f-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a96f-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="5a96f-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="5a96f-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="5a96f-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="5a96f-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="5a96f-116">[Erstellen Sie eine App-Übermittlung](create-an-app-submission.md), und [aktualisieren Sie die Übermittlung](update-an-app-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="5a96f-116">[Create an app submission](create-an-app-submission.md) and then [update the submission](update-an-app-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="5a96f-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="5a96f-117">Request</span></span>

<span data-ttu-id="5a96f-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="5a96f-118">This method has the following syntax.</span></span> <span data-ttu-id="5a96f-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="5a96f-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="5a96f-120">Methode</span><span class="sxs-lookup"><span data-stu-id="5a96f-120">Method</span></span> | <span data-ttu-id="5a96f-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="5a96f-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="5a96f-122">POST</span><span class="sxs-lookup"><span data-stu-id="5a96f-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/commit``` |


### <a name="request-header"></a><span data-ttu-id="5a96f-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="5a96f-123">Request header</span></span>

| <span data-ttu-id="5a96f-124">Header</span><span class="sxs-lookup"><span data-stu-id="5a96f-124">Header</span></span>        | <span data-ttu-id="5a96f-125">Typ</span><span class="sxs-lookup"><span data-stu-id="5a96f-125">Type</span></span>   | <span data-ttu-id="5a96f-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a96f-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="5a96f-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="5a96f-127">Authorization</span></span> | <span data-ttu-id="5a96f-128">String</span><span class="sxs-lookup"><span data-stu-id="5a96f-128">string</span></span> | <span data-ttu-id="5a96f-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a96f-129">Required.</span></span> <span data-ttu-id="5a96f-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="5a96f-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="5a96f-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="5a96f-131">Request parameters</span></span>

| <span data-ttu-id="5a96f-132">Name</span><span class="sxs-lookup"><span data-stu-id="5a96f-132">Name</span></span>        | <span data-ttu-id="5a96f-133">Typ</span><span class="sxs-lookup"><span data-stu-id="5a96f-133">Type</span></span>   | <span data-ttu-id="5a96f-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a96f-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="5a96f-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="5a96f-135">applicationId</span></span> | <span data-ttu-id="5a96f-136">String</span><span class="sxs-lookup"><span data-stu-id="5a96f-136">string</span></span> | <span data-ttu-id="5a96f-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a96f-137">Required.</span></span> <span data-ttu-id="5a96f-138">Die Store-ID der App, die die Übermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="5a96f-138">The Store ID of the app that contains the submission you want to commit.</span></span> <span data-ttu-id="5a96f-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="5a96f-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="5a96f-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="5a96f-140">submissionId</span></span> | <span data-ttu-id="5a96f-141">String</span><span class="sxs-lookup"><span data-stu-id="5a96f-141">string</span></span> | <span data-ttu-id="5a96f-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a96f-142">Required.</span></span> <span data-ttu-id="5a96f-143">Die ID der Übermittlung, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="5a96f-143">The ID of the submission you want to commit.</span></span> <span data-ttu-id="5a96f-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5a96f-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="5a96f-145">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5a96f-145">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="5a96f-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="5a96f-146">Request body</span></span>

<span data-ttu-id="5a96f-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="5a96f-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="5a96f-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="5a96f-148">Request example</span></span>

<span data-ttu-id="5a96f-149">Im folgenden Beispiel wird veranschaulicht, wie eine App-Übermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="5a96f-149">The following example demonstrates how to commit an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243610/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="5a96f-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="5a96f-150">Response</span></span>

<span data-ttu-id="5a96f-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="5a96f-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="5a96f-152">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="5a96f-152">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="5a96f-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="5a96f-153">Response body</span></span>

| <span data-ttu-id="5a96f-154">Wert</span><span class="sxs-lookup"><span data-stu-id="5a96f-154">Value</span></span>      | <span data-ttu-id="5a96f-155">Typ</span><span class="sxs-lookup"><span data-stu-id="5a96f-155">Type</span></span>   | <span data-ttu-id="5a96f-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a96f-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5a96f-157">status</span><span class="sxs-lookup"><span data-stu-id="5a96f-157">status</span></span>           | <span data-ttu-id="5a96f-158">string</span><span class="sxs-lookup"><span data-stu-id="5a96f-158">string</span></span>  | <span data-ttu-id="5a96f-159">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="5a96f-159">The status of the submission.</span></span> <span data-ttu-id="5a96f-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="5a96f-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="5a96f-161">None</span><span class="sxs-lookup"><span data-stu-id="5a96f-161">None</span></span></li><li><span data-ttu-id="5a96f-162">Canceled</span><span class="sxs-lookup"><span data-stu-id="5a96f-162">Canceled</span></span></li><li><span data-ttu-id="5a96f-163">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="5a96f-163">PendingCommit</span></span></li><li><span data-ttu-id="5a96f-164">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="5a96f-164">CommitStarted</span></span></li><li><span data-ttu-id="5a96f-165">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="5a96f-165">CommitFailed</span></span></li><li><span data-ttu-id="5a96f-166">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="5a96f-166">PendingPublication</span></span></li><li><span data-ttu-id="5a96f-167">Publishing</span><span class="sxs-lookup"><span data-stu-id="5a96f-167">Publishing</span></span></li><li><span data-ttu-id="5a96f-168">Published</span><span class="sxs-lookup"><span data-stu-id="5a96f-168">Published</span></span></li><li><span data-ttu-id="5a96f-169">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="5a96f-169">PublishFailed</span></span></li><li><span data-ttu-id="5a96f-170">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="5a96f-170">PreProcessing</span></span></li><li><span data-ttu-id="5a96f-171">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="5a96f-171">PreProcessingFailed</span></span></li><li><span data-ttu-id="5a96f-172">Certification</span><span class="sxs-lookup"><span data-stu-id="5a96f-172">Certification</span></span></li><li><span data-ttu-id="5a96f-173">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="5a96f-173">CertificationFailed</span></span></li><li><span data-ttu-id="5a96f-174">Release</span><span class="sxs-lookup"><span data-stu-id="5a96f-174">Release</span></span></li><li><span data-ttu-id="5a96f-175">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="5a96f-175">ReleaseFailed</span></span></li></ul>  |


## <a name="error-codes"></a><span data-ttu-id="5a96f-176">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="5a96f-176">Error codes</span></span>

<span data-ttu-id="5a96f-177">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="5a96f-177">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="5a96f-178">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="5a96f-178">Error code</span></span> |  <span data-ttu-id="5a96f-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a96f-179">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="5a96f-180">400</span><span class="sxs-lookup"><span data-stu-id="5a96f-180">400</span></span>  | <span data-ttu-id="5a96f-181">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="5a96f-181">The request parameters are invalid.</span></span> |
| <span data-ttu-id="5a96f-182">404</span><span class="sxs-lookup"><span data-stu-id="5a96f-182">404</span></span>  | <span data-ttu-id="5a96f-183">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="5a96f-183">The specified submission could not be found.</span></span> |
| <span data-ttu-id="5a96f-184">409</span><span class="sxs-lookup"><span data-stu-id="5a96f-184">409</span></span>  | <span data-ttu-id="5a96f-185">Die angegebene Übermittlung wurde gefunden, konnte jedoch nicht in ihrem aktuellen Zustand übernommen werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="5a96f-185">The specified submission was found but it could not be committed in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="5a96f-186">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5a96f-186">Related topics</span></span>

* [<span data-ttu-id="5a96f-187">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="5a96f-187">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="5a96f-188">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-188">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="5a96f-189">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-189">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="5a96f-190">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-190">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="5a96f-191">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-191">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="5a96f-192">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="5a96f-192">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
