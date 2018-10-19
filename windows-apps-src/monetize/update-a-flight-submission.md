---
author: Xansky
ms.assetid: 24C5F796-5FB8-4B5D-B428-C3154B3098BD
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Flight-Paketübermittlung.
title: Aktualisieren einer Flight-Paketübermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlung, Aktualisieren
ms.localizationpriority: medium
ms.openlocfilehash: 467dae77a7815dba03ce558c7e29e3eea0036d09
ms.sourcegitcommit: 310a4555fedd4246188a98b31f6c094abb33ec60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5128683"
---
# <a name="update-a-package-flight-submission"></a><span data-ttu-id="54c37-104">Aktualisieren einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-104">Update a package flight submission</span></span>


<span data-ttu-id="54c37-105">Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="54c37-105">Use this method in the Microsoft Store submission API to update an existing package flight submission.</span></span> <span data-ttu-id="54c37-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-a-flight-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="54c37-106">After you successfully update a submission by using this method, you must [commit the submission](commit-a-flight-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="54c37-107">Weitere Informationen dazu, wie diese Methode in das Erstellen einer Flight-Paketübermittlung mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="54c37-107">For more information about how this method fits into the process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54c37-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="54c37-108">Prerequisites</span></span>

<span data-ttu-id="54c37-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="54c37-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="54c37-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="54c37-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="54c37-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="54c37-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="54c37-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="54c37-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="54c37-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="54c37-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="54c37-114">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="54c37-114">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="54c37-115">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="54c37-115">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="54c37-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="54c37-116">Request</span></span>

<span data-ttu-id="54c37-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="54c37-117">This method has the following syntax.</span></span> <span data-ttu-id="54c37-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="54c37-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="54c37-119">Methode</span><span class="sxs-lookup"><span data-stu-id="54c37-119">Method</span></span> | <span data-ttu-id="54c37-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="54c37-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="54c37-121">PUT</span><span class="sxs-lookup"><span data-stu-id="54c37-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="54c37-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="54c37-122">Request header</span></span>

| <span data-ttu-id="54c37-123">Header</span><span class="sxs-lookup"><span data-stu-id="54c37-123">Header</span></span>        | <span data-ttu-id="54c37-124">Typ</span><span class="sxs-lookup"><span data-stu-id="54c37-124">Type</span></span>   | <span data-ttu-id="54c37-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54c37-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="54c37-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="54c37-126">Authorization</span></span> | <span data-ttu-id="54c37-127">String</span><span class="sxs-lookup"><span data-stu-id="54c37-127">string</span></span> | <span data-ttu-id="54c37-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54c37-128">Required.</span></span> <span data-ttu-id="54c37-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="54c37-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="54c37-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="54c37-130">Request parameters</span></span>

| <span data-ttu-id="54c37-131">Name</span><span class="sxs-lookup"><span data-stu-id="54c37-131">Name</span></span>        | <span data-ttu-id="54c37-132">Typ</span><span class="sxs-lookup"><span data-stu-id="54c37-132">Type</span></span>   | <span data-ttu-id="54c37-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54c37-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="54c37-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="54c37-134">applicationId</span></span> | <span data-ttu-id="54c37-135">String</span><span class="sxs-lookup"><span data-stu-id="54c37-135">string</span></span> | <span data-ttu-id="54c37-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54c37-136">Required.</span></span> <span data-ttu-id="54c37-137">Die Store-ID der App, für die Sie eine Flight Paketübermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="54c37-137">The Store ID of the app for which you want to update a package flight submission.</span></span> <span data-ttu-id="54c37-138">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="54c37-138">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="54c37-139">flightId</span><span class="sxs-lookup"><span data-stu-id="54c37-139">flightId</span></span> | <span data-ttu-id="54c37-140">String</span><span class="sxs-lookup"><span data-stu-id="54c37-140">string</span></span> | <span data-ttu-id="54c37-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54c37-141">Required.</span></span> <span data-ttu-id="54c37-142">Die ID des Flight-Pakets, für das Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="54c37-142">The ID of the package flight for which you want to update a submission.</span></span> <span data-ttu-id="54c37-143">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="54c37-143">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="54c37-144">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="54c37-144">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="54c37-145">submissionId</span><span class="sxs-lookup"><span data-stu-id="54c37-145">submissionId</span></span> | <span data-ttu-id="54c37-146">String</span><span class="sxs-lookup"><span data-stu-id="54c37-146">string</span></span> | <span data-ttu-id="54c37-147">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54c37-147">Required.</span></span> <span data-ttu-id="54c37-148">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="54c37-148">The ID of the submission to update.</span></span> <span data-ttu-id="54c37-149">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="54c37-149">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="54c37-150">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="54c37-150">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="54c37-151">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="54c37-151">Request body</span></span>

<span data-ttu-id="54c37-152">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="54c37-152">The request body has the following parameters.</span></span>

| <span data-ttu-id="54c37-153">Wert</span><span class="sxs-lookup"><span data-stu-id="54c37-153">Value</span></span>      | <span data-ttu-id="54c37-154">Typ</span><span class="sxs-lookup"><span data-stu-id="54c37-154">Type</span></span>   | <span data-ttu-id="54c37-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54c37-155">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="54c37-156">flightPackages</span><span class="sxs-lookup"><span data-stu-id="54c37-156">flightPackages</span></span>           | <span data-ttu-id="54c37-157">array</span><span class="sxs-lookup"><span data-stu-id="54c37-157">array</span></span>  | <span data-ttu-id="54c37-158">Enthält Objekte, die Details über die einzelnen Pakete der Übermittlung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="54c37-158">Contains objects that provide details about each package in the submission.</span></span> <span data-ttu-id="54c37-159">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-package-object).</span><span class="sxs-lookup"><span data-stu-id="54c37-159">For more details about the values in the response body, see [Flight package resource](manage-flight-submissions.md#flight-package-object).</span></span> <span data-ttu-id="54c37-160">Beim Aufruf dieser Methode zur Aktualisierung einer App-Übermittlung sind im Antworttext nur die *fileName*-, *fileStatus*-, *minimumDirectXVersion*- und *minimumSystemRam*-Werte dieser Objekte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54c37-160">When calling this method to update an app submission, only the *fileName*, *fileStatus*, *minimumDirectXVersion*, and *minimumSystemRam* values of these objects are required in the request body.</span></span> <span data-ttu-id="54c37-161">Die übrigen Werte werden von Dev Center aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="54c37-161">The other values are populated by Dev Center.</span></span> |
| <span data-ttu-id="54c37-162">packageDeliveryOptions</span><span class="sxs-lookup"><span data-stu-id="54c37-162">packageDeliveryOptions</span></span>    | <span data-ttu-id="54c37-163">object</span><span class="sxs-lookup"><span data-stu-id="54c37-163">object</span></span>  | <span data-ttu-id="54c37-164">Enthält den schrittweisen Paketrollout sowie erforderliche Einstellungen für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="54c37-164">Contains gradual package rollout and mandatory update settings for the submission.</span></span> <span data-ttu-id="54c37-165">Weitere Informationen finden Sie unter [options-Objekt für die Paketübermittlung](manage-flight-submissions.md#package-delivery-options-object).</span><span class="sxs-lookup"><span data-stu-id="54c37-165">For more information, see [Package delivery options object](manage-flight-submissions.md#package-delivery-options-object).</span></span>  |
| <span data-ttu-id="54c37-166">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="54c37-166">targetPublishMode</span></span>           | <span data-ttu-id="54c37-167">string</span><span class="sxs-lookup"><span data-stu-id="54c37-167">string</span></span>  | <span data-ttu-id="54c37-168">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="54c37-168">The publish mode for the submission.</span></span> <span data-ttu-id="54c37-169">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="54c37-169">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="54c37-170">Immediate</span><span class="sxs-lookup"><span data-stu-id="54c37-170">Immediate</span></span></li><li><span data-ttu-id="54c37-171">Manual</span><span class="sxs-lookup"><span data-stu-id="54c37-171">Manual</span></span></li><li><span data-ttu-id="54c37-172">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="54c37-172">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="54c37-173">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="54c37-173">targetPublishDate</span></span>           | <span data-ttu-id="54c37-174">string</span><span class="sxs-lookup"><span data-stu-id="54c37-174">string</span></span>  | <span data-ttu-id="54c37-175">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="54c37-175">The publish date for the submission in in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |
| <span data-ttu-id="54c37-176">notesForCertification</span><span class="sxs-lookup"><span data-stu-id="54c37-176">notesForCertification</span></span>           | <span data-ttu-id="54c37-177">string</span><span class="sxs-lookup"><span data-stu-id="54c37-177">string</span></span>  |  <span data-ttu-id="54c37-178">Enthält zusätzliche Informationen für Zertifizierungstester wie Anmeldeinformationen für Testkonten und Schritte zum Zugriff auf und zur Überprüfung von Features.</span><span class="sxs-lookup"><span data-stu-id="54c37-178">Provides additional info for the certification testers, such as test account credentials and steps to access and verify features.</span></span> <span data-ttu-id="54c37-179">Weitere Informationen finden Sie unter [Hinweise zur Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span><span class="sxs-lookup"><span data-stu-id="54c37-179">For more information, see [Notes for certification](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span></span> |


### <a name="request-example"></a><span data-ttu-id="54c37-180">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="54c37-180">Request example</span></span>

<span data-ttu-id="54c37-181">Im folgenden Beispiel wird die Aktualisierung einer Flight-Paketübermittlung für eine App veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="54c37-181">The following example demonstrates how to update a package flight submission for an app.</span></span>

```json
PUT https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
Content-Type: application/json
{
  "flightPackages": [
    {
      "fileName": "newPackage.appx",
      "fileStatus": "PendingUpload",
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None"
    }
  ],
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
  "targetPublishMode": "Immediate",
  "targetPublishDate": "",
  "notesForCertification": "No special steps are required for certification of this app."
}
```

## <a name="response"></a><span data-ttu-id="54c37-182">Antwort</span><span class="sxs-lookup"><span data-stu-id="54c37-182">Response</span></span>

<span data-ttu-id="54c37-183">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="54c37-183">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="54c37-184">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="54c37-184">The response body contains information about the updated submission.</span></span> <span data-ttu-id="54c37-185">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="54c37-185">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

```json
{
  "id": "1152921504621243649",
  "flightId": "cd2e368a-0da5-4026-9f34-0e7934bc6f23",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [],
    "warnings": [],
    "certificationReports": []
  },
  "flightPackages": [
    {
      "fileName": "newPackage.appx",
      "fileStatus": "PendingUpload",
      "id": "",
      "version": "1.0.0.0",
      "languages": ["en-us"],
      "capabilities": [],
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None"
    }
  ],
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/8b389577-5d5e-4cbe-a744-1ff2e97a9eb8?sv=2014-02-14&sr=b&sig=wgMCQPjPDkuuxNLkeG35rfHaMToebCxBNMPw7WABdXU%3D&se=2016-06-17T21:29:44Z&sp=rwl",
  "targetPublishMode": "Immediate",
  "targetPublishDate": "",
  "notesForCertification": "No special steps are required for certification of this app."
}
```

## <a name="error-codes"></a><span data-ttu-id="54c37-186">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="54c37-186">Error codes</span></span>

<span data-ttu-id="54c37-187">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="54c37-187">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="54c37-188">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="54c37-188">Error code</span></span> |  <span data-ttu-id="54c37-189">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54c37-189">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="54c37-190">400</span><span class="sxs-lookup"><span data-stu-id="54c37-190">400</span></span>  | <span data-ttu-id="54c37-191">Die Flight-Paketübermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="54c37-191">The package flight submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="54c37-192">409</span><span class="sxs-lookup"><span data-stu-id="54c37-192">409</span></span>  | <span data-ttu-id="54c37-193">Die Flight-Paketübermittlung konnte aufgrund des aktuellen Zustands der App nicht aktualisiert werden, oder in der App wird ein Dev Center-Dashboard-Merkmal verwendet, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="54c37-193">The package flight submission could not be updated because of the current state of the app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="54c37-194">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="54c37-194">Related topics</span></span>

* [<span data-ttu-id="54c37-195">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="54c37-195">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="54c37-196">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="54c37-196">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="54c37-197">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-197">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="54c37-198">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-198">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="54c37-199">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-199">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="54c37-200">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-200">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="54c37-201">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="54c37-201">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
