---
author: Xansky
ms.assetid: AC74B4FA-5554-4C03-9683-86EE48546C05
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte Add-on-Übermittlung in Partner Center zu übernehmen.
title: Ausführen eines Commit für eine Add-On-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Übernehmen einer Add-On-Übermittlung, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 6f0d7ed15d3328ceffa9aa65a38c129f735c41ba
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7303540"
---
# <a name="commit-an-add-on-submission"></a><span data-ttu-id="d6f9f-104">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-104">Commit an add-on submission</span></span>

<span data-ttu-id="d6f9f-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte Add-on (auch bekannt als in-app-Produkt oder IAP)-Übermittlung in Partner Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-105">Use this method in the Microsoft Store submission API to commit a new or updated add-on (also known as in-app product or IAP) submission to Partner Center.</span></span> <span data-ttu-id="d6f9f-106">Die übernahmeaktion Partner Center, dass die Übermittlungsdaten (darunter alle zugehörigen Symbole) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-106">The commit action alerts Partner Center that the submission data has been uploaded (including any related icons).</span></span> <span data-ttu-id="d6f9f-107">Als Reaktion übernimmt Partner Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-107">In response, Partner Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="d6f9f-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen an der Übermittlung im Partner Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-108">After the commit operation succeeds, the changes to the submission are shown in Partner Center.</span></span>

<span data-ttu-id="d6f9f-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zur Übermittlung eines Add-Ons mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="d6f9f-109">For more information about how the commit operation fits into the process of submitting an add-on by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6f9f-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d6f9f-110">Prerequisites</span></span>

<span data-ttu-id="d6f9f-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="d6f9f-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="d6f9f-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="d6f9f-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="d6f9f-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="d6f9f-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="d6f9f-116">[Erstellen Sie eine Add-On-Übermittlung](create-an-add-on-submission.md), und [aktualisieren Sie die Übermittlung](update-an-add-on-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-116">[Create an add-on submission](create-an-add-on-submission.md) and then [update the submission](update-an-add-on-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="d6f9f-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-117">Request</span></span>

<span data-ttu-id="d6f9f-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-118">This method has the following syntax.</span></span> <span data-ttu-id="d6f9f-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="d6f9f-120">Methode</span><span class="sxs-lookup"><span data-stu-id="d6f9f-120">Method</span></span> | <span data-ttu-id="d6f9f-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="d6f9f-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="d6f9f-122">POST</span><span class="sxs-lookup"><span data-stu-id="d6f9f-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}/commit``` |


### <a name="request-header"></a><span data-ttu-id="d6f9f-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="d6f9f-123">Request header</span></span>

| <span data-ttu-id="d6f9f-124">Header</span><span class="sxs-lookup"><span data-stu-id="d6f9f-124">Header</span></span>        | <span data-ttu-id="d6f9f-125">Typ</span><span class="sxs-lookup"><span data-stu-id="d6f9f-125">Type</span></span>   | <span data-ttu-id="d6f9f-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d6f9f-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-127">Authorization</span></span> | <span data-ttu-id="d6f9f-128">String</span><span class="sxs-lookup"><span data-stu-id="d6f9f-128">string</span></span> | <span data-ttu-id="d6f9f-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-129">Required.</span></span> <span data-ttu-id="d6f9f-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="d6f9f-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="d6f9f-131">Request parameters</span></span>

| <span data-ttu-id="d6f9f-132">Name</span><span class="sxs-lookup"><span data-stu-id="d6f9f-132">Name</span></span>        | <span data-ttu-id="d6f9f-133">Typ</span><span class="sxs-lookup"><span data-stu-id="d6f9f-133">Type</span></span>   | <span data-ttu-id="d6f9f-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d6f9f-135">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="d6f9f-135">inAppProductId</span></span> | <span data-ttu-id="d6f9f-136">String</span><span class="sxs-lookup"><span data-stu-id="d6f9f-136">string</span></span> | <span data-ttu-id="d6f9f-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-137">Required.</span></span> <span data-ttu-id="d6f9f-138">Die Store-ID des Add-Ons, die die Übermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-138">The Store ID of the add-on that contains the submission you want to commit.</span></span> <span data-ttu-id="d6f9f-139">Die Store-ID ist im Partner Center verfügbar und in den Antwortdaten für Anforderungen zum [Abrufen aller Add-ons](get-all-add-ons.md) und [Erstellen eines Add-Ons](create-an-add-on.md)enthalten.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-139">The Store ID is available in Partner Center, and it is included in the response data for requests to [Get all add-ons](get-all-add-ons.md) and [Create an add-on](create-an-add-on.md).</span></span> |
| <span data-ttu-id="d6f9f-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="d6f9f-140">submissionId</span></span> | <span data-ttu-id="d6f9f-141">String</span><span class="sxs-lookup"><span data-stu-id="d6f9f-141">string</span></span> | <span data-ttu-id="d6f9f-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-142">Required.</span></span> <span data-ttu-id="d6f9f-143">Die ID der Übermittlung, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-143">The ID of the submission you want to commit.</span></span> <span data-ttu-id="d6f9f-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-144">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="d6f9f-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="d6f9f-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="d6f9f-146">Request body</span></span>

<span data-ttu-id="d6f9f-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="d6f9f-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="d6f9f-148">Request example</span></span>

<span data-ttu-id="d6f9f-149">Im folgenden Beispiel wird veranschaulicht, wie eine Add-On-Übermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-149">The following example demonstrates how to commit an add-on submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="d6f9f-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="d6f9f-150">Response</span></span>

<span data-ttu-id="d6f9f-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="d6f9f-152">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-152">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="d6f9f-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="d6f9f-153">Response body</span></span>

| <span data-ttu-id="d6f9f-154">Wert</span><span class="sxs-lookup"><span data-stu-id="d6f9f-154">Value</span></span>      | <span data-ttu-id="d6f9f-155">Typ</span><span class="sxs-lookup"><span data-stu-id="d6f9f-155">Type</span></span>   | <span data-ttu-id="d6f9f-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d6f9f-157">status</span><span class="sxs-lookup"><span data-stu-id="d6f9f-157">status</span></span>           | <span data-ttu-id="d6f9f-158">string</span><span class="sxs-lookup"><span data-stu-id="d6f9f-158">string</span></span>  | <span data-ttu-id="d6f9f-159">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-159">The status of the submission.</span></span> <span data-ttu-id="d6f9f-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="d6f9f-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="d6f9f-161">None</span><span class="sxs-lookup"><span data-stu-id="d6f9f-161">None</span></span></li><li><span data-ttu-id="d6f9f-162">Canceled</span><span class="sxs-lookup"><span data-stu-id="d6f9f-162">Canceled</span></span></li><li><span data-ttu-id="d6f9f-163">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="d6f9f-163">PendingCommit</span></span></li><li><span data-ttu-id="d6f9f-164">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="d6f9f-164">CommitStarted</span></span></li><li><span data-ttu-id="d6f9f-165">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="d6f9f-165">CommitFailed</span></span></li><li><span data-ttu-id="d6f9f-166">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="d6f9f-166">PendingPublication</span></span></li><li><span data-ttu-id="d6f9f-167">Publishing</span><span class="sxs-lookup"><span data-stu-id="d6f9f-167">Publishing</span></span></li><li><span data-ttu-id="d6f9f-168">Published</span><span class="sxs-lookup"><span data-stu-id="d6f9f-168">Published</span></span></li><li><span data-ttu-id="d6f9f-169">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="d6f9f-169">PublishFailed</span></span></li><li><span data-ttu-id="d6f9f-170">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="d6f9f-170">PreProcessing</span></span></li><li><span data-ttu-id="d6f9f-171">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="d6f9f-171">PreProcessingFailed</span></span></li><li><span data-ttu-id="d6f9f-172">Certification</span><span class="sxs-lookup"><span data-stu-id="d6f9f-172">Certification</span></span></li><li><span data-ttu-id="d6f9f-173">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="d6f9f-173">CertificationFailed</span></span></li><li><span data-ttu-id="d6f9f-174">Release</span><span class="sxs-lookup"><span data-stu-id="d6f9f-174">Release</span></span></li><li><span data-ttu-id="d6f9f-175">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="d6f9f-175">ReleaseFailed</span></span></li></ul>  |


## <a name="error-codes"></a><span data-ttu-id="d6f9f-176">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="d6f9f-176">Error codes</span></span>

<span data-ttu-id="d6f9f-177">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-177">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="d6f9f-178">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="d6f9f-178">Error code</span></span> |  <span data-ttu-id="d6f9f-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-179">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="d6f9f-180">400</span><span class="sxs-lookup"><span data-stu-id="d6f9f-180">400</span></span>  | <span data-ttu-id="d6f9f-181">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-181">The request parameters are invalid.</span></span> |
| <span data-ttu-id="d6f9f-182">404</span><span class="sxs-lookup"><span data-stu-id="d6f9f-182">404</span></span>  | <span data-ttu-id="d6f9f-183">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-183">The specified submission could not be found.</span></span> |
| <span data-ttu-id="d6f9f-184">409</span><span class="sxs-lookup"><span data-stu-id="d6f9f-184">409</span></span>  | <span data-ttu-id="d6f9f-185">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand übernommen werden, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="d6f9f-185">The specified submission was found but it could not be committed in its current state, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="d6f9f-186">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d6f9f-186">Related topics</span></span>

* [<span data-ttu-id="d6f9f-187">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="d6f9f-187">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="d6f9f-188">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-188">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="d6f9f-189">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-189">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="d6f9f-190">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-190">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="d6f9f-191">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-191">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="d6f9f-192">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d6f9f-192">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
