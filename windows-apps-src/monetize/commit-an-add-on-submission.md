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
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6203098"
---
# <a name="commit-an-add-on-submission"></a><span data-ttu-id="66fbb-104">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-104">Commit an add-on submission</span></span>

<span data-ttu-id="66fbb-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue oder aktualisierte Add-on (auch bekannt als in-app-Produkt oder IAP)-Übermittlung in Partner Center zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="66fbb-105">Use this method in the Microsoft Store submission API to commit a new or updated add-on (also known as in-app product or IAP) submission to Partner Center.</span></span> <span data-ttu-id="66fbb-106">Die übernahmeaktion Partner Center, dass die Übermittlungsdaten (darunter alle zugehörigen Symbole) hochgeladen wurden.</span><span class="sxs-lookup"><span data-stu-id="66fbb-106">The commit action alerts Partner Center that the submission data has been uploaded (including any related icons).</span></span> <span data-ttu-id="66fbb-107">Als Reaktion übernimmt Partner Center die Änderungen der Übermittlungsdaten zur Aufnahme und Veröffentlichung.</span><span class="sxs-lookup"><span data-stu-id="66fbb-107">In response, Partner Center commits the changes to the submission data for ingestion and publishing.</span></span> <span data-ttu-id="66fbb-108">Nachdem der Übernahmevorgang erfolgreich ausgeführt wurde, werden die Änderungen an der Übermittlung im Partner Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="66fbb-108">After the commit operation succeeds, the changes to the submission are shown in Partner Center.</span></span>

<span data-ttu-id="66fbb-109">Weitere Informationen dazu, wie der Übernahmevorgang in den Prozess zur Übermittlung eines Add-Ons mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="66fbb-109">For more information about how the commit operation fits into the process of submitting an add-on by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66fbb-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="66fbb-110">Prerequisites</span></span>

<span data-ttu-id="66fbb-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="66fbb-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="66fbb-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="66fbb-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="66fbb-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66fbb-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="66fbb-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="66fbb-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="66fbb-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="66fbb-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="66fbb-116">[Erstellen Sie eine Add-On-Übermittlung](create-an-add-on-submission.md), und [aktualisieren Sie die Übermittlung](update-an-add-on-submission.md) mit allen erforderlichen Änderungen der Übermittlungsdaten.</span><span class="sxs-lookup"><span data-stu-id="66fbb-116">[Create an add-on submission](create-an-add-on-submission.md) and then [update the submission](update-an-add-on-submission.md) with any necessary changes to the submission data.</span></span>

## <a name="request"></a><span data-ttu-id="66fbb-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="66fbb-117">Request</span></span>

<span data-ttu-id="66fbb-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="66fbb-118">This method has the following syntax.</span></span> <span data-ttu-id="66fbb-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="66fbb-119">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="66fbb-120">Methode</span><span class="sxs-lookup"><span data-stu-id="66fbb-120">Method</span></span> | <span data-ttu-id="66fbb-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="66fbb-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="66fbb-122">POST</span><span class="sxs-lookup"><span data-stu-id="66fbb-122">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}/commit``` |


### <a name="request-header"></a><span data-ttu-id="66fbb-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="66fbb-123">Request header</span></span>

| <span data-ttu-id="66fbb-124">Header</span><span class="sxs-lookup"><span data-stu-id="66fbb-124">Header</span></span>        | <span data-ttu-id="66fbb-125">Typ</span><span class="sxs-lookup"><span data-stu-id="66fbb-125">Type</span></span>   | <span data-ttu-id="66fbb-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66fbb-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="66fbb-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="66fbb-127">Authorization</span></span> | <span data-ttu-id="66fbb-128">String</span><span class="sxs-lookup"><span data-stu-id="66fbb-128">string</span></span> | <span data-ttu-id="66fbb-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66fbb-129">Required.</span></span> <span data-ttu-id="66fbb-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="66fbb-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="66fbb-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="66fbb-131">Request parameters</span></span>

| <span data-ttu-id="66fbb-132">Name</span><span class="sxs-lookup"><span data-stu-id="66fbb-132">Name</span></span>        | <span data-ttu-id="66fbb-133">Typ</span><span class="sxs-lookup"><span data-stu-id="66fbb-133">Type</span></span>   | <span data-ttu-id="66fbb-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66fbb-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="66fbb-135">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="66fbb-135">inAppProductId</span></span> | <span data-ttu-id="66fbb-136">String</span><span class="sxs-lookup"><span data-stu-id="66fbb-136">string</span></span> | <span data-ttu-id="66fbb-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66fbb-137">Required.</span></span> <span data-ttu-id="66fbb-138">Die Store-ID des Add-Ons, die die Übermittlung enthält, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="66fbb-138">The Store ID of the add-on that contains the submission you want to commit.</span></span> <span data-ttu-id="66fbb-139">Die Store-ID ist im Partner Center verfügbar und in den Antwortdaten für Anforderungen zum [Abrufen aller Add-ons](get-all-add-ons.md) und [Erstellen eines Add-Ons](create-an-add-on.md)enthalten.</span><span class="sxs-lookup"><span data-stu-id="66fbb-139">The Store ID is available in Partner Center, and it is included in the response data for requests to [Get all add-ons](get-all-add-ons.md) and [Create an add-on](create-an-add-on.md).</span></span> |
| <span data-ttu-id="66fbb-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="66fbb-140">submissionId</span></span> | <span data-ttu-id="66fbb-141">String</span><span class="sxs-lookup"><span data-stu-id="66fbb-141">string</span></span> | <span data-ttu-id="66fbb-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66fbb-142">Required.</span></span> <span data-ttu-id="66fbb-143">Die ID der Übermittlung, die Sie übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="66fbb-143">The ID of the submission you want to commit.</span></span> <span data-ttu-id="66fbb-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="66fbb-144">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="66fbb-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="66fbb-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="66fbb-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="66fbb-146">Request body</span></span>

<span data-ttu-id="66fbb-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="66fbb-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="66fbb-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="66fbb-148">Request example</span></span>

<span data-ttu-id="66fbb-149">Im folgenden Beispiel wird veranschaulicht, wie eine Add-On-Übermittlung übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="66fbb-149">The following example demonstrates how to commit an add-on submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023/commit HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="66fbb-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="66fbb-150">Response</span></span>

<span data-ttu-id="66fbb-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="66fbb-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="66fbb-152">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="66fbb-152">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "status": "CommitStarted"
}
```

### <a name="response-body"></a><span data-ttu-id="66fbb-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="66fbb-153">Response body</span></span>

| <span data-ttu-id="66fbb-154">Wert</span><span class="sxs-lookup"><span data-stu-id="66fbb-154">Value</span></span>      | <span data-ttu-id="66fbb-155">Typ</span><span class="sxs-lookup"><span data-stu-id="66fbb-155">Type</span></span>   | <span data-ttu-id="66fbb-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66fbb-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="66fbb-157">status</span><span class="sxs-lookup"><span data-stu-id="66fbb-157">status</span></span>           | <span data-ttu-id="66fbb-158">string</span><span class="sxs-lookup"><span data-stu-id="66fbb-158">string</span></span>  | <span data-ttu-id="66fbb-159">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="66fbb-159">The status of the submission.</span></span> <span data-ttu-id="66fbb-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="66fbb-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="66fbb-161">None</span><span class="sxs-lookup"><span data-stu-id="66fbb-161">None</span></span></li><li><span data-ttu-id="66fbb-162">Canceled</span><span class="sxs-lookup"><span data-stu-id="66fbb-162">Canceled</span></span></li><li><span data-ttu-id="66fbb-163">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="66fbb-163">PendingCommit</span></span></li><li><span data-ttu-id="66fbb-164">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="66fbb-164">CommitStarted</span></span></li><li><span data-ttu-id="66fbb-165">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="66fbb-165">CommitFailed</span></span></li><li><span data-ttu-id="66fbb-166">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="66fbb-166">PendingPublication</span></span></li><li><span data-ttu-id="66fbb-167">Publishing</span><span class="sxs-lookup"><span data-stu-id="66fbb-167">Publishing</span></span></li><li><span data-ttu-id="66fbb-168">Published</span><span class="sxs-lookup"><span data-stu-id="66fbb-168">Published</span></span></li><li><span data-ttu-id="66fbb-169">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="66fbb-169">PublishFailed</span></span></li><li><span data-ttu-id="66fbb-170">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="66fbb-170">PreProcessing</span></span></li><li><span data-ttu-id="66fbb-171">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="66fbb-171">PreProcessingFailed</span></span></li><li><span data-ttu-id="66fbb-172">Certification</span><span class="sxs-lookup"><span data-stu-id="66fbb-172">Certification</span></span></li><li><span data-ttu-id="66fbb-173">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="66fbb-173">CertificationFailed</span></span></li><li><span data-ttu-id="66fbb-174">Release</span><span class="sxs-lookup"><span data-stu-id="66fbb-174">Release</span></span></li><li><span data-ttu-id="66fbb-175">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="66fbb-175">ReleaseFailed</span></span></li></ul>  |


## <a name="error-codes"></a><span data-ttu-id="66fbb-176">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="66fbb-176">Error codes</span></span>

<span data-ttu-id="66fbb-177">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="66fbb-177">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="66fbb-178">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="66fbb-178">Error code</span></span> |  <span data-ttu-id="66fbb-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66fbb-179">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="66fbb-180">400</span><span class="sxs-lookup"><span data-stu-id="66fbb-180">400</span></span>  | <span data-ttu-id="66fbb-181">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="66fbb-181">The request parameters are invalid.</span></span> |
| <span data-ttu-id="66fbb-182">404</span><span class="sxs-lookup"><span data-stu-id="66fbb-182">404</span></span>  | <span data-ttu-id="66fbb-183">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="66fbb-183">The specified submission could not be found.</span></span> |
| <span data-ttu-id="66fbb-184">409</span><span class="sxs-lookup"><span data-stu-id="66fbb-184">409</span></span>  | <span data-ttu-id="66fbb-185">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand übernommen werden, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="66fbb-185">The specified submission was found but it could not be committed in its current state, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="66fbb-186">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="66fbb-186">Related topics</span></span>

* [<span data-ttu-id="66fbb-187">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="66fbb-187">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="66fbb-188">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-188">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="66fbb-189">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-189">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="66fbb-190">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-190">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="66fbb-191">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-191">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="66fbb-192">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="66fbb-192">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
