---
author: mcleanbyron
ms.assetid: C78176D6-47BB-4C63-92F8-426719A70F04
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen.
title: Abrufen des Status einer Flight-Paketübermittlung
ms.author: mcleans
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlung, Status
ms.localizationpriority: medium
ms.openlocfilehash: 9dbc15b2418c79aa3dee922a61c70364835afe87
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4505942"
---
# <a name="get-the-status-of-a-package-flight-submission"></a><span data-ttu-id="d96b4-104">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-104">Get the status of a package flight submission</span></span>

<span data-ttu-id="d96b4-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Status einer Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d96b4-105">Use this method in the Microsoft Store submission API to get the status of a package flight submission.</span></span> <span data-ttu-id="d96b4-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="d96b4-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d96b4-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d96b4-107">Prerequisites</span></span>

<span data-ttu-id="d96b4-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="d96b4-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="d96b4-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="d96b4-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="d96b4-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d96b4-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="d96b4-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="d96b4-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="d96b4-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="d96b4-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="d96b4-113">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="d96b4-113">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="d96b4-114">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="d96b4-114">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="d96b4-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="d96b4-115">Request</span></span>

<span data-ttu-id="d96b4-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="d96b4-116">This method has the following syntax.</span></span> <span data-ttu-id="d96b4-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="d96b4-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="d96b4-118">Methode</span><span class="sxs-lookup"><span data-stu-id="d96b4-118">Method</span></span> | <span data-ttu-id="d96b4-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="d96b4-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="d96b4-120">GET</span><span class="sxs-lookup"><span data-stu-id="d96b4-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/status``` |


### <a name="request-header"></a><span data-ttu-id="d96b4-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="d96b4-121">Request header</span></span>

| <span data-ttu-id="d96b4-122">Header</span><span class="sxs-lookup"><span data-stu-id="d96b4-122">Header</span></span>        | <span data-ttu-id="d96b4-123">Typ</span><span class="sxs-lookup"><span data-stu-id="d96b4-123">Type</span></span>   | <span data-ttu-id="d96b4-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d96b4-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d96b4-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="d96b4-125">Authorization</span></span> | <span data-ttu-id="d96b4-126">String</span><span class="sxs-lookup"><span data-stu-id="d96b4-126">string</span></span> | <span data-ttu-id="d96b4-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d96b4-127">Required.</span></span> <span data-ttu-id="d96b4-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="d96b4-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="d96b4-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="d96b4-129">Request parameters</span></span>

| <span data-ttu-id="d96b4-130">Name</span><span class="sxs-lookup"><span data-stu-id="d96b4-130">Name</span></span>        | <span data-ttu-id="d96b4-131">Typ</span><span class="sxs-lookup"><span data-stu-id="d96b4-131">Type</span></span>   | <span data-ttu-id="d96b4-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d96b4-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d96b4-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="d96b4-133">applicationId</span></span> | <span data-ttu-id="d96b4-134">String</span><span class="sxs-lookup"><span data-stu-id="d96b4-134">string</span></span> | <span data-ttu-id="d96b4-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d96b4-135">Required.</span></span> <span data-ttu-id="d96b4-136">Die Store-ID der App mit der Flight-Paketübermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="d96b4-136">The Store ID of the app that contains the package flight submission for which you want to get the status.</span></span> <span data-ttu-id="d96b4-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="d96b4-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="d96b4-138">flightId</span><span class="sxs-lookup"><span data-stu-id="d96b4-138">flightId</span></span> | <span data-ttu-id="d96b4-139">String</span><span class="sxs-lookup"><span data-stu-id="d96b4-139">string</span></span> | <span data-ttu-id="d96b4-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d96b4-140">Required.</span></span> <span data-ttu-id="d96b4-141">Die ID des Flight-Pakets mit der Übermittlung, für die der Status abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="d96b4-141">The ID of the package flight that contains the submission for which you want to get the status.</span></span> <span data-ttu-id="d96b4-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="d96b4-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="d96b4-143">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d96b4-143">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="d96b4-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="d96b4-144">submissionId</span></span> | <span data-ttu-id="d96b4-145">String</span><span class="sxs-lookup"><span data-stu-id="d96b4-145">string</span></span> | <span data-ttu-id="d96b4-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d96b4-146">Required.</span></span> <span data-ttu-id="d96b4-147">Die ID der Übermittlung, für die der Status abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d96b4-147">The ID of the submission for which you want to get the status.</span></span> <span data-ttu-id="d96b4-148">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d96b4-148">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="d96b4-149">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d96b4-149">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="d96b4-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="d96b4-150">Request body</span></span>

<span data-ttu-id="d96b4-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="d96b4-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="d96b4-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="d96b4-152">Request example</span></span>

<span data-ttu-id="d96b4-153">Im folgenden Beispiel wird veranschaulicht, wie der Status einer Flight-Paketübermittlung abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="d96b4-153">The following example demonstrates how to get the status of a package flight submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/status HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="d96b4-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="d96b4-154">Response</span></span>

<span data-ttu-id="d96b4-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="d96b4-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="d96b4-156">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d96b4-156">The response body contains information about the specified submission.</span></span> <span data-ttu-id="d96b4-157">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="d96b4-157">For more details about the values in the response body, see the following section.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="d96b4-158">Antworttext</span><span class="sxs-lookup"><span data-stu-id="d96b4-158">Response body</span></span>

| <span data-ttu-id="d96b4-159">Wert</span><span class="sxs-lookup"><span data-stu-id="d96b4-159">Value</span></span>      | <span data-ttu-id="d96b4-160">Typ</span><span class="sxs-lookup"><span data-stu-id="d96b4-160">Type</span></span>   | <span data-ttu-id="d96b4-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d96b4-161">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d96b4-162">status</span><span class="sxs-lookup"><span data-stu-id="d96b4-162">status</span></span>           | <span data-ttu-id="d96b4-163">string</span><span class="sxs-lookup"><span data-stu-id="d96b4-163">string</span></span>  | <span data-ttu-id="d96b4-164">Der Status der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d96b4-164">The status of the submission.</span></span> <span data-ttu-id="d96b4-165">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="d96b4-165">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="d96b4-166">None</span><span class="sxs-lookup"><span data-stu-id="d96b4-166">None</span></span></li><li><span data-ttu-id="d96b4-167">Canceled</span><span class="sxs-lookup"><span data-stu-id="d96b4-167">Canceled</span></span></li><li><span data-ttu-id="d96b4-168">PendingCommit</span><span class="sxs-lookup"><span data-stu-id="d96b4-168">PendingCommit</span></span></li><li><span data-ttu-id="d96b4-169">CommitStarted</span><span class="sxs-lookup"><span data-stu-id="d96b4-169">CommitStarted</span></span></li><li><span data-ttu-id="d96b4-170">CommitFailed</span><span class="sxs-lookup"><span data-stu-id="d96b4-170">CommitFailed</span></span></li><li><span data-ttu-id="d96b4-171">PendingPublication</span><span class="sxs-lookup"><span data-stu-id="d96b4-171">PendingPublication</span></span></li><li><span data-ttu-id="d96b4-172">Publishing</span><span class="sxs-lookup"><span data-stu-id="d96b4-172">Publishing</span></span></li><li><span data-ttu-id="d96b4-173">Published</span><span class="sxs-lookup"><span data-stu-id="d96b4-173">Published</span></span></li><li><span data-ttu-id="d96b4-174">PublishFailed</span><span class="sxs-lookup"><span data-stu-id="d96b4-174">PublishFailed</span></span></li><li><span data-ttu-id="d96b4-175">PreProcessing</span><span class="sxs-lookup"><span data-stu-id="d96b4-175">PreProcessing</span></span></li><li><span data-ttu-id="d96b4-176">PreProcessingFailed</span><span class="sxs-lookup"><span data-stu-id="d96b4-176">PreProcessingFailed</span></span></li><li><span data-ttu-id="d96b4-177">Certification</span><span class="sxs-lookup"><span data-stu-id="d96b4-177">Certification</span></span></li><li><span data-ttu-id="d96b4-178">CertificationFailed</span><span class="sxs-lookup"><span data-stu-id="d96b4-178">CertificationFailed</span></span></li><li><span data-ttu-id="d96b4-179">Release</span><span class="sxs-lookup"><span data-stu-id="d96b4-179">Release</span></span></li><li><span data-ttu-id="d96b4-180">ReleaseFailed</span><span class="sxs-lookup"><span data-stu-id="d96b4-180">ReleaseFailed</span></span></li></ul>   |
| <span data-ttu-id="d96b4-181">statusDetails</span><span class="sxs-lookup"><span data-stu-id="d96b4-181">statusDetails</span></span>           | <span data-ttu-id="d96b4-182">Objekt</span><span class="sxs-lookup"><span data-stu-id="d96b4-182">object</span></span>  |  <span data-ttu-id="d96b4-183">Enthält zusätzliche Details über den Status der Übermittlung, einschließlich Informationen zu Fehlern.</span><span class="sxs-lookup"><span data-stu-id="d96b4-183">Contains additional details about the status of the submission, including information about any errors.</span></span> <span data-ttu-id="d96b4-184">Weitere Informationen finden Sie unter [Statusdetails-Ressource](manage-flight-submissions.md#status-details-object).</span><span class="sxs-lookup"><span data-stu-id="d96b4-184">For more information, see [Status details resource](manage-flight-submissions.md#status-details-object).</span></span> |


## <a name="error-codes"></a><span data-ttu-id="d96b4-185">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="d96b4-185">Error codes</span></span>

<span data-ttu-id="d96b4-186">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="d96b4-186">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="d96b4-187">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="d96b4-187">Error code</span></span> |  <span data-ttu-id="d96b4-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d96b4-188">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="d96b4-189">404</span><span class="sxs-lookup"><span data-stu-id="d96b4-189">404</span></span>  | <span data-ttu-id="d96b4-190">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d96b4-190">The submission could not be found.</span></span> |
| <span data-ttu-id="d96b4-191">409</span><span class="sxs-lookup"><span data-stu-id="d96b4-191">409</span></span>  | <span data-ttu-id="d96b4-192">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="d96b4-192">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="d96b4-193">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d96b4-193">Related topics</span></span>

* [<span data-ttu-id="d96b4-194">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="d96b4-194">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="d96b4-195">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="d96b4-195">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="d96b4-196">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-196">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="d96b4-197">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-197">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="d96b4-198">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-198">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="d96b4-199">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-199">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="d96b4-200">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="d96b4-200">Delete an app submission</span></span>](delete-an-app-submission.md)
