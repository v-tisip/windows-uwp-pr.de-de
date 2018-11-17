---
author: Xansky
ms.assetid: 55315F38-6EC5-4889-A14E-7D8EC282FE98
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer Add-On-Übermittlung abzurufen.
title: Abrufen des Status einer Add-On-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, Status
ms.localizationpriority: medium
ms.openlocfilehash: e2013a081898dbf46958190da1df01adaac9d820
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7154271"
---
# <a name="get-the-status-of-an-add-on-submission"></a><span data-ttu-id="ba99d-104">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-104">Get the status of an add-on submission</span></span>

<span data-ttu-id="ba99d-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Abrufen des Status für eine Add-On-Übermittlung (auch als In-App-Produkt oder IAP bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="ba99d-105">Use this method in the Microsoft Store submission API to get the status of an add-on (also known as in-app product or IAP) submission.</span></span> <span data-ttu-id="ba99d-106">Weitere Informationen über den Erstellungsprozess einer Add-On-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="ba99d-106">For more information about the process of process of creating an add-on submission by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba99d-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ba99d-107">Prerequisites</span></span>

<span data-ttu-id="ba99d-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ba99d-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ba99d-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="ba99d-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="ba99d-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ba99d-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ba99d-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ba99d-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ba99d-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ba99d-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="ba99d-113">Erstellen einer Add-on-Übermittlungs für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="ba99d-113">Create an add-on submission for one of your apps.</span></span> <span data-ttu-id="ba99d-114">Sie können dies im Partner Center oder hierzu können Sie mithilfe der Methode [Erstellen einer Add-on-Übermittlung](create-an-add-on-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="ba99d-114">You can do this in Partner Center, or you can do this by using the [Create an add-on submission](create-an-add-on-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="ba99d-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ba99d-115">Request</span></span>

<span data-ttu-id="ba99d-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="ba99d-116">This method has the following syntax.</span></span> <span data-ttu-id="ba99d-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="ba99d-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="ba99d-118">Methode</span><span class="sxs-lookup"><span data-stu-id="ba99d-118">Method</span></span> | <span data-ttu-id="ba99d-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ba99d-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="ba99d-120">GET</span><span class="sxs-lookup"><span data-stu-id="ba99d-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}/status``` |


### <a name="request-header"></a><span data-ttu-id="ba99d-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ba99d-121">Request header</span></span>

| <span data-ttu-id="ba99d-122">Header</span><span class="sxs-lookup"><span data-stu-id="ba99d-122">Header</span></span>        | <span data-ttu-id="ba99d-123">Typ</span><span class="sxs-lookup"><span data-stu-id="ba99d-123">Type</span></span>   | <span data-ttu-id="ba99d-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba99d-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ba99d-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ba99d-125">Authorization</span></span> | <span data-ttu-id="ba99d-126">String</span><span class="sxs-lookup"><span data-stu-id="ba99d-126">string</span></span> | <span data-ttu-id="ba99d-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ba99d-127">Required.</span></span> <span data-ttu-id="ba99d-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ba99d-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="ba99d-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ba99d-129">Request parameters</span></span>

| <span data-ttu-id="ba99d-130">Name</span><span class="sxs-lookup"><span data-stu-id="ba99d-130">Name</span></span>        | <span data-ttu-id="ba99d-131">Typ</span><span class="sxs-lookup"><span data-stu-id="ba99d-131">Type</span></span>   | <span data-ttu-id="ba99d-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba99d-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ba99d-133">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="ba99d-133">inAppProductId</span></span> | <span data-ttu-id="ba99d-134">String</span><span class="sxs-lookup"><span data-stu-id="ba99d-134">string</span></span> | <span data-ttu-id="ba99d-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ba99d-135">Required.</span></span> <span data-ttu-id="ba99d-136">Die Store-ID des Add-Ons mit der Übermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ba99d-136">The Store ID of the add-on that contains the submission for which you want to get the status.</span></span> <span data-ttu-id="ba99d-137">Die Store-ID ist im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ba99d-137">The Store ID is available in Partner Center.</span></span>  |
| <span data-ttu-id="ba99d-138">submissionId</span><span class="sxs-lookup"><span data-stu-id="ba99d-138">submissionId</span></span> | <span data-ttu-id="ba99d-139">String</span><span class="sxs-lookup"><span data-stu-id="ba99d-139">string</span></span> | <span data-ttu-id="ba99d-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ba99d-140">Required.</span></span> <span data-ttu-id="ba99d-141">Die ID der Übermittlung, für die der Status abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ba99d-141">The ID of the submission for which you want to get the status.</span></span> <span data-ttu-id="ba99d-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ba99d-142">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="ba99d-143">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ba99d-143">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="ba99d-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="ba99d-144">Request body</span></span>

<span data-ttu-id="ba99d-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="ba99d-145">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="ba99d-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ba99d-146">Request example</span></span>

<span data-ttu-id="ba99d-147">Im folgenden Beispiel wird veranschaulicht, wie der Status einer Add-On-Übermittlung abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ba99d-147">The following example demonstrates how to get the status of an add-on submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621243680/status HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ba99d-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="ba99d-148">Response</span></span>

<span data-ttu-id="ba99d-149">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ba99d-149">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="ba99d-150">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ba99d-150">The response body contains information about the specified submission.</span></span> <span data-ttu-id="ba99d-151">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="ba99d-151">For more details about the values in the response body, see the following sections.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="ba99d-152">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ba99d-152">Response body</span></span>

| <span data-ttu-id="ba99d-153">Wert</span><span class="sxs-lookup"><span data-stu-id="ba99d-153">Value</span></span>      | <span data-ttu-id="ba99d-154">Typ</span><span class="sxs-lookup"><span data-stu-id="ba99d-154">Type</span></span>   | <span data-ttu-id="ba99d-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba99d-155">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ba99d-156">status</span><span class="sxs-lookup"><span data-stu-id="ba99d-156">status</span></span>           | <span data-ttu-id="ba99d-157">string</span><span class="sxs-lookup"><span data-stu-id="ba99d-157">string</span></span>  | <span data-ttu-id="ba99d-158">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ba99d-158">The status of the submission.</span></span> <span data-ttu-id="ba99d-159">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="ba99d-159">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="ba99d-160">None</span><span class="sxs-lookup"><span data-stu-id="ba99d-160">None</span></span></li><li><span data-ttu-id="ba99d-161">Canceled</span><span class="sxs-lookup"><span data-stu-id="ba99d-161">Canceled</span></span></li><li><span data-ttu-id="ba99d-162">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="ba99d-162">PendingCommit</span></span></li><li><span data-ttu-id="ba99d-163">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="ba99d-163">CommitStarted</span></span></li><li><span data-ttu-id="ba99d-164">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="ba99d-164">CommitFailed</span></span></li><li><span data-ttu-id="ba99d-165">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="ba99d-165">PendingPublication</span></span></li><li><span data-ttu-id="ba99d-166">Publishing</span><span class="sxs-lookup"><span data-stu-id="ba99d-166">Publishing</span></span></li><li><span data-ttu-id="ba99d-167">Published</span><span class="sxs-lookup"><span data-stu-id="ba99d-167">Published</span></span></li><li><span data-ttu-id="ba99d-168">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="ba99d-168">PublishFailed</span></span></li><li><span data-ttu-id="ba99d-169">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="ba99d-169">PreProcessing</span></span></li><li><span data-ttu-id="ba99d-170">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="ba99d-170">PreProcessingFailed</span></span></li><li><span data-ttu-id="ba99d-171">Certification</span><span class="sxs-lookup"><span data-stu-id="ba99d-171">Certification</span></span></li><li><span data-ttu-id="ba99d-172">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="ba99d-172">CertificationFailed</span></span></li><li><span data-ttu-id="ba99d-173">Release</span><span class="sxs-lookup"><span data-stu-id="ba99d-173">Release</span></span></li><li><span data-ttu-id="ba99d-174">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="ba99d-174">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="ba99d-175">statusDetails</span><span class="sxs-lookup"><span data-stu-id="ba99d-175">statusDetails</span></span>           | <span data-ttu-id="ba99d-176">Objekt</span><span class="sxs-lookup"><span data-stu-id="ba99d-176">object</span></span>  |  <span data-ttu-id="ba99d-177">Enthält zusätzliche Details über den Status der Übermittlung, einschließlich Informationen zu Fehlern.</span><span class="sxs-lookup"><span data-stu-id="ba99d-177">Contains additional details about the status of the submission, including information about any errors.</span></span> <span data-ttu-id="ba99d-178">Weitere Informationen finden Sie unter [Statusdetails-Ressource](manage-add-on-submissions.md#status-details-object).</span><span class="sxs-lookup"><span data-stu-id="ba99d-178">For more information, see [Status details resource](manage-add-on-submissions.md#status-details-object).</span></span> |


## <a name="error-codes"></a><span data-ttu-id="ba99d-179">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ba99d-179">Error codes</span></span>

<span data-ttu-id="ba99d-180">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="ba99d-180">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="ba99d-181">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="ba99d-181">Error code</span></span> |  <span data-ttu-id="ba99d-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba99d-182">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="ba99d-183">404</span><span class="sxs-lookup"><span data-stu-id="ba99d-183">404</span></span>  | <span data-ttu-id="ba99d-184">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="ba99d-184">The submission could not be found.</span></span> |
| <span data-ttu-id="ba99d-185">409</span><span class="sxs-lookup"><span data-stu-id="ba99d-185">409</span></span>  | <span data-ttu-id="ba99d-186">Das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="ba99d-186">The add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="ba99d-187">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ba99d-187">Related topics</span></span>

* [<span data-ttu-id="ba99d-188">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="ba99d-188">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="ba99d-189">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-189">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="ba99d-190">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-190">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="ba99d-191">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-191">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="ba99d-192">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-192">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="ba99d-193">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="ba99d-193">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
