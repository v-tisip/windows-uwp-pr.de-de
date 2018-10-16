---
author: Xansky
ms.assetid: C78176D6-47BB-4C63-92F8-426719A70F04
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen.
title: Abrufen des Status einer Flight-Paketübermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlung, Status
ms.localizationpriority: medium
ms.openlocfilehash: 7d661800371d90f15a5b7e355c2f06b7bd631f6b
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "4679840"
---
# <a name="get-the-status-of-a-package-flight-submission"></a><span data-ttu-id="9c9da-104">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-104">Get the status of a package flight submission</span></span>

<span data-ttu-id="9c9da-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="9c9da-105">Use this method in the Microsoft Store submission API to get the status of a package flight submission.</span></span> <span data-ttu-id="9c9da-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="9c9da-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c9da-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9c9da-107">Prerequisites</span></span>

<span data-ttu-id="9c9da-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="9c9da-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="9c9da-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="9c9da-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="9c9da-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9c9da-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="9c9da-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="9c9da-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="9c9da-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="9c9da-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="9c9da-113">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="9c9da-113">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="9c9da-114">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="9c9da-114">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="9c9da-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="9c9da-115">Request</span></span>

<span data-ttu-id="9c9da-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="9c9da-116">This method has the following syntax.</span></span> <span data-ttu-id="9c9da-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="9c9da-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="9c9da-118">Methode</span><span class="sxs-lookup"><span data-stu-id="9c9da-118">Method</span></span> | <span data-ttu-id="9c9da-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="9c9da-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="9c9da-120">GET</span><span class="sxs-lookup"><span data-stu-id="9c9da-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/status``` |


### <a name="request-header"></a><span data-ttu-id="9c9da-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="9c9da-121">Request header</span></span>

| <span data-ttu-id="9c9da-122">Header</span><span class="sxs-lookup"><span data-stu-id="9c9da-122">Header</span></span>        | <span data-ttu-id="9c9da-123">Typ</span><span class="sxs-lookup"><span data-stu-id="9c9da-123">Type</span></span>   | <span data-ttu-id="9c9da-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9c9da-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="9c9da-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="9c9da-125">Authorization</span></span> | <span data-ttu-id="9c9da-126">String</span><span class="sxs-lookup"><span data-stu-id="9c9da-126">string</span></span> | <span data-ttu-id="9c9da-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9c9da-127">Required.</span></span> <span data-ttu-id="9c9da-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="9c9da-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="9c9da-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="9c9da-129">Request parameters</span></span>

| <span data-ttu-id="9c9da-130">Name</span><span class="sxs-lookup"><span data-stu-id="9c9da-130">Name</span></span>        | <span data-ttu-id="9c9da-131">Typ</span><span class="sxs-lookup"><span data-stu-id="9c9da-131">Type</span></span>   | <span data-ttu-id="9c9da-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9c9da-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="9c9da-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="9c9da-133">applicationId</span></span> | <span data-ttu-id="9c9da-134">String</span><span class="sxs-lookup"><span data-stu-id="9c9da-134">string</span></span> | <span data-ttu-id="9c9da-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9c9da-135">Required.</span></span> <span data-ttu-id="9c9da-136">Die Store-ID der App mit der Flight-Paketübermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="9c9da-136">The Store ID of the app that contains the package flight submission for which you want to get the status.</span></span> <span data-ttu-id="9c9da-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="9c9da-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="9c9da-138">flightId</span><span class="sxs-lookup"><span data-stu-id="9c9da-138">flightId</span></span> | <span data-ttu-id="9c9da-139">String</span><span class="sxs-lookup"><span data-stu-id="9c9da-139">string</span></span> | <span data-ttu-id="9c9da-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9c9da-140">Required.</span></span> <span data-ttu-id="9c9da-141">Die ID des Flight-Pakets mit der Übermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="9c9da-141">The ID of the package flight that contains the submission for which you want to get the status.</span></span> <span data-ttu-id="9c9da-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="9c9da-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="9c9da-143">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9c9da-143">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="9c9da-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="9c9da-144">submissionId</span></span> | <span data-ttu-id="9c9da-145">String</span><span class="sxs-lookup"><span data-stu-id="9c9da-145">string</span></span> | <span data-ttu-id="9c9da-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9c9da-146">Required.</span></span> <span data-ttu-id="9c9da-147">Die ID der Übermittlung, für die der Status abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="9c9da-147">The ID of the submission for which you want to get the status.</span></span> <span data-ttu-id="9c9da-148">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9c9da-148">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="9c9da-149">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9c9da-149">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="9c9da-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="9c9da-150">Request body</span></span>

<span data-ttu-id="9c9da-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="9c9da-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="9c9da-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="9c9da-152">Request example</span></span>

<span data-ttu-id="9c9da-153">Im folgenden Beispiel wird veranschaulicht, wie der Status einer Flight-Paketübermittlung abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9c9da-153">The following example demonstrates how to get the status of a package flight submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/status HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="9c9da-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="9c9da-154">Response</span></span>

<span data-ttu-id="9c9da-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="9c9da-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="9c9da-156">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="9c9da-156">The response body contains information about the specified submission.</span></span> <span data-ttu-id="9c9da-157">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="9c9da-157">For more details about the values in the response body, see the following section.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="9c9da-158">Antworttext</span><span class="sxs-lookup"><span data-stu-id="9c9da-158">Response body</span></span>

| <span data-ttu-id="9c9da-159">Wert</span><span class="sxs-lookup"><span data-stu-id="9c9da-159">Value</span></span>      | <span data-ttu-id="9c9da-160">Typ</span><span class="sxs-lookup"><span data-stu-id="9c9da-160">Type</span></span>   | <span data-ttu-id="9c9da-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9c9da-161">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9c9da-162">status</span><span class="sxs-lookup"><span data-stu-id="9c9da-162">status</span></span>           | <span data-ttu-id="9c9da-163">string</span><span class="sxs-lookup"><span data-stu-id="9c9da-163">string</span></span>  | <span data-ttu-id="9c9da-164">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="9c9da-164">The status of the submission.</span></span> <span data-ttu-id="9c9da-165">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="9c9da-165">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="9c9da-166">None</span><span class="sxs-lookup"><span data-stu-id="9c9da-166">None</span></span></li><li><span data-ttu-id="9c9da-167">Canceled</span><span class="sxs-lookup"><span data-stu-id="9c9da-167">Canceled</span></span></li><li><span data-ttu-id="9c9da-168">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="9c9da-168">PendingCommit</span></span></li><li><span data-ttu-id="9c9da-169">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="9c9da-169">CommitStarted</span></span></li><li><span data-ttu-id="9c9da-170">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="9c9da-170">CommitFailed</span></span></li><li><span data-ttu-id="9c9da-171">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="9c9da-171">PendingPublication</span></span></li><li><span data-ttu-id="9c9da-172">Publishing</span><span class="sxs-lookup"><span data-stu-id="9c9da-172">Publishing</span></span></li><li><span data-ttu-id="9c9da-173">Published</span><span class="sxs-lookup"><span data-stu-id="9c9da-173">Published</span></span></li><li><span data-ttu-id="9c9da-174">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="9c9da-174">PublishFailed</span></span></li><li><span data-ttu-id="9c9da-175">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="9c9da-175">PreProcessing</span></span></li><li><span data-ttu-id="9c9da-176">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="9c9da-176">PreProcessingFailed</span></span></li><li><span data-ttu-id="9c9da-177">Certification</span><span class="sxs-lookup"><span data-stu-id="9c9da-177">Certification</span></span></li><li><span data-ttu-id="9c9da-178">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="9c9da-178">CertificationFailed</span></span></li><li><span data-ttu-id="9c9da-179">Release</span><span class="sxs-lookup"><span data-stu-id="9c9da-179">Release</span></span></li><li><span data-ttu-id="9c9da-180">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="9c9da-180">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="9c9da-181">statusDetails</span><span class="sxs-lookup"><span data-stu-id="9c9da-181">statusDetails</span></span>           | <span data-ttu-id="9c9da-182">Objekt</span><span class="sxs-lookup"><span data-stu-id="9c9da-182">object</span></span>  |  <span data-ttu-id="9c9da-183">Enthält zusätzliche Details über den Status der Übermittlung, einschließlich Informationen zu Fehlern.</span><span class="sxs-lookup"><span data-stu-id="9c9da-183">Contains additional details about the status of the submission, including information about any errors.</span></span> <span data-ttu-id="9c9da-184">Weitere Informationen finden Sie unter [Statusdetails-Ressource](manage-flight-submissions.md#status-details-object).</span><span class="sxs-lookup"><span data-stu-id="9c9da-184">For more information, see [Status details resource](manage-flight-submissions.md#status-details-object).</span></span> |


## <a name="error-codes"></a><span data-ttu-id="9c9da-185">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="9c9da-185">Error codes</span></span>

<span data-ttu-id="9c9da-186">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="9c9da-186">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="9c9da-187">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="9c9da-187">Error code</span></span> |  <span data-ttu-id="9c9da-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9c9da-188">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="9c9da-189">404</span><span class="sxs-lookup"><span data-stu-id="9c9da-189">404</span></span>  | <span data-ttu-id="9c9da-190">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="9c9da-190">The submission could not be found.</span></span> |
| <span data-ttu-id="9c9da-191">409</span><span class="sxs-lookup"><span data-stu-id="9c9da-191">409</span></span>  | <span data-ttu-id="9c9da-192">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="9c9da-192">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="9c9da-193">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9c9da-193">Related topics</span></span>

* [<span data-ttu-id="9c9da-194">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="9c9da-194">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="9c9da-195">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="9c9da-195">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="9c9da-196">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-196">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="9c9da-197">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-197">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="9c9da-198">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-198">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="9c9da-199">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-199">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="9c9da-200">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="9c9da-200">Delete an app submission</span></span>](delete-an-app-submission.md)
