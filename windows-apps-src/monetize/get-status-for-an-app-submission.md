---
author: Xansky
ms.assetid: 039B8810-5C9E-4DB9-A6AF-33E7401311FF
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer App-Übermittlung abzurufen.
title: Abrufen des Status einer App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, App-Übermittlung, Status
ms.localizationpriority: medium
ms.openlocfilehash: 7d14ce17f4e6dff08351ca0764f3b6a173550426
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4624148"
---
# <a name="get-the-status-of-an-app-submission"></a><span data-ttu-id="7dd4e-104">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-104">Get the status of an app submission</span></span>

<span data-ttu-id="7dd4e-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer App-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-105">Use this method in the Microsoft Store submission API to get the status of an app submission.</span></span> <span data-ttu-id="7dd4e-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="7dd4e-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7dd4e-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7dd4e-107">Prerequisites</span></span>

<span data-ttu-id="7dd4e-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="7dd4e-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="7dd4e-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="7dd4e-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="7dd4e-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="7dd4e-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="7dd4e-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-113">Request</span></span>

<span data-ttu-id="7dd4e-114">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-114">This method has the following syntax.</span></span> <span data-ttu-id="7dd4e-115">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-115">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="7dd4e-116">Methode</span><span class="sxs-lookup"><span data-stu-id="7dd4e-116">Method</span></span> | <span data-ttu-id="7dd4e-117">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="7dd4e-117">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="7dd4e-118">GET</span><span class="sxs-lookup"><span data-stu-id="7dd4e-118">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/status``` |


### <a name="request-header"></a><span data-ttu-id="7dd4e-119">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="7dd4e-119">Request header</span></span>

| <span data-ttu-id="7dd4e-120">Header</span><span class="sxs-lookup"><span data-stu-id="7dd4e-120">Header</span></span>        | <span data-ttu-id="7dd4e-121">Typ</span><span class="sxs-lookup"><span data-stu-id="7dd4e-121">Type</span></span>   | <span data-ttu-id="7dd4e-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-122">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="7dd4e-123">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-123">Authorization</span></span> | <span data-ttu-id="7dd4e-124">String</span><span class="sxs-lookup"><span data-stu-id="7dd4e-124">string</span></span> | <span data-ttu-id="7dd4e-125">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-125">Required.</span></span> <span data-ttu-id="7dd4e-126">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-126">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="7dd4e-127">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="7dd4e-127">Request parameters</span></span>

| <span data-ttu-id="7dd4e-128">Name</span><span class="sxs-lookup"><span data-stu-id="7dd4e-128">Name</span></span>        | <span data-ttu-id="7dd4e-129">Typ</span><span class="sxs-lookup"><span data-stu-id="7dd4e-129">Type</span></span>   | <span data-ttu-id="7dd4e-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-130">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="7dd4e-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="7dd4e-131">applicationId</span></span> | <span data-ttu-id="7dd4e-132">String</span><span class="sxs-lookup"><span data-stu-id="7dd4e-132">string</span></span> | <span data-ttu-id="7dd4e-133">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-133">Required.</span></span> <span data-ttu-id="7dd4e-134">Die Store-ID der App mit der Übermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-134">The Store ID of the app that contains the submission for which you want to get the status.</span></span> <span data-ttu-id="7dd4e-135">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="7dd4e-135">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="7dd4e-136">submissionId</span><span class="sxs-lookup"><span data-stu-id="7dd4e-136">submissionId</span></span> | <span data-ttu-id="7dd4e-137">String</span><span class="sxs-lookup"><span data-stu-id="7dd4e-137">string</span></span> | <span data-ttu-id="7dd4e-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-138">Required.</span></span> <span data-ttu-id="7dd4e-139">Die ID der Übermittlung, für die der Status abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-139">The ID of the submission for which you want to get the status.</span></span> <span data-ttu-id="7dd4e-140">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-140">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="7dd4e-141">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-141">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="7dd4e-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="7dd4e-142">Request body</span></span>

<span data-ttu-id="7dd4e-143">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-143">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="7dd4e-144">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="7dd4e-144">Request example</span></span>

<span data-ttu-id="7dd4e-145">Im folgenden Beispiel wird veranschaulicht, wie der Status einer App-Übermittlung abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-145">The following example demonstrates how to get the status of an app submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243610/status HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="7dd4e-146">Antwort</span><span class="sxs-lookup"><span data-stu-id="7dd4e-146">Response</span></span>

<span data-ttu-id="7dd4e-147">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-147">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="7dd4e-148">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-148">The response body contains information about the specified submission.</span></span> <span data-ttu-id="7dd4e-149">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-149">For more details about the values in the response body, see the following sections.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="7dd4e-150">Antworttext</span><span class="sxs-lookup"><span data-stu-id="7dd4e-150">Response body</span></span>

| <span data-ttu-id="7dd4e-151">Wert</span><span class="sxs-lookup"><span data-stu-id="7dd4e-151">Value</span></span>      | <span data-ttu-id="7dd4e-152">Typ</span><span class="sxs-lookup"><span data-stu-id="7dd4e-152">Type</span></span>   | <span data-ttu-id="7dd4e-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-153">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7dd4e-154">status</span><span class="sxs-lookup"><span data-stu-id="7dd4e-154">status</span></span>           | <span data-ttu-id="7dd4e-155">string</span><span class="sxs-lookup"><span data-stu-id="7dd4e-155">string</span></span>  | <span data-ttu-id="7dd4e-156">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-156">The status of the submission.</span></span> <span data-ttu-id="7dd4e-157">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="7dd4e-157">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="7dd4e-158">None</span><span class="sxs-lookup"><span data-stu-id="7dd4e-158">None</span></span></li><li><span data-ttu-id="7dd4e-159">Canceled</span><span class="sxs-lookup"><span data-stu-id="7dd4e-159">Canceled</span></span></li><li><span data-ttu-id="7dd4e-160">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="7dd4e-160">PendingCommit</span></span></li><li><span data-ttu-id="7dd4e-161">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="7dd4e-161">CommitStarted</span></span></li><li><span data-ttu-id="7dd4e-162">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="7dd4e-162">CommitFailed</span></span></li><li><span data-ttu-id="7dd4e-163">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="7dd4e-163">PendingPublication</span></span></li><li><span data-ttu-id="7dd4e-164">Publishing</span><span class="sxs-lookup"><span data-stu-id="7dd4e-164">Publishing</span></span></li><li><span data-ttu-id="7dd4e-165">Published</span><span class="sxs-lookup"><span data-stu-id="7dd4e-165">Published</span></span></li><li><span data-ttu-id="7dd4e-166">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="7dd4e-166">PublishFailed</span></span></li><li><span data-ttu-id="7dd4e-167">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="7dd4e-167">PreProcessing</span></span></li><li><span data-ttu-id="7dd4e-168">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="7dd4e-168">PreProcessingFailed</span></span></li><li><span data-ttu-id="7dd4e-169">Certification</span><span class="sxs-lookup"><span data-stu-id="7dd4e-169">Certification</span></span></li><li><span data-ttu-id="7dd4e-170">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="7dd4e-170">CertificationFailed</span></span></li><li><span data-ttu-id="7dd4e-171">Release</span><span class="sxs-lookup"><span data-stu-id="7dd4e-171">Release</span></span></li><li><span data-ttu-id="7dd4e-172">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="7dd4e-172">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="7dd4e-173">statusDetails</span><span class="sxs-lookup"><span data-stu-id="7dd4e-173">statusDetails</span></span>           | <span data-ttu-id="7dd4e-174">Objekt</span><span class="sxs-lookup"><span data-stu-id="7dd4e-174">object</span></span>  |  <span data-ttu-id="7dd4e-175">Enthält zusätzliche Details über den Status der Übermittlung, einschließlich Informationen zu Fehlern.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-175">Contains additional details about the status of the submission, including information about any errors.</span></span> <span data-ttu-id="7dd4e-176">Weitere Informationen finden Sie in der [Statusdetails-Ressource](manage-app-submissions.md#status-details-object).</span><span class="sxs-lookup"><span data-stu-id="7dd4e-176">For more information, see the [Status details resource](manage-app-submissions.md#status-details-object).</span></span> |


## <a name="error-codes"></a><span data-ttu-id="7dd4e-177">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="7dd4e-177">Error codes</span></span>

<span data-ttu-id="7dd4e-178">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-178">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="7dd4e-179">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="7dd4e-179">Error code</span></span> |  <span data-ttu-id="7dd4e-180">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-180">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="7dd4e-181">404</span><span class="sxs-lookup"><span data-stu-id="7dd4e-181">404</span></span>  | <span data-ttu-id="7dd4e-182">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="7dd4e-182">The submission could not be found.</span></span> |
| <span data-ttu-id="7dd4e-183">409</span><span class="sxs-lookup"><span data-stu-id="7dd4e-183">409</span></span>  | <span data-ttu-id="7dd4e-184">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="7dd4e-184">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="7dd4e-185">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7dd4e-185">Related topics</span></span>

* [<span data-ttu-id="7dd4e-186">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="7dd4e-186">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="7dd4e-187">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-187">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="7dd4e-188">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-188">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="7dd4e-189">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-189">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="7dd4e-190">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-190">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="7dd4e-191">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="7dd4e-191">Delete an app submission</span></span>](delete-an-app-submission.md)
