---
author: mcleanbyron
ms.assetid: 24C5F796-5FB8-4B5D-B428-C3154B3098BD
description: "Verwenden Sie diese Methode aus der Windows Store-Übermittlung API zur Aktualisierung einer vorhandenen Flight-Paketübermittlung."
title: "Aktualisieren einer Flight-Paketübermittlung"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlung-API, Flight-Übermittlung, Aktualisieren"
ms.openlocfilehash: 3763dcce71ee634d3234280187ac89741e7aed2a
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="update-a-package-flight-submission"></a><span data-ttu-id="ee31b-104">Aktualisieren einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-104">Update a package flight submission</span></span>


<span data-ttu-id="ee31b-105">Verwenden Sie diese Methode aus der Windows Store-Übermittlung API zur Aktualisierung einer vorhandenen Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="ee31b-105">Use this method in the Windows Store submission API to update an existing package flight submission.</span></span> <span data-ttu-id="ee31b-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-a-flight-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="ee31b-106">After you successfully update a submission by using this method, you must [commit the submission](commit-a-flight-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="ee31b-107">Weitere Informationen dazu, wie diese Methode in das Erstellen einer Flight-Paketübermittlung mit der Windows Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="ee31b-107">For more information about how this method fits into the process of creating a package flight submission by using the Windows Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee31b-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ee31b-108">Prerequisites</span></span>

<span data-ttu-id="ee31b-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ee31b-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ee31b-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="ee31b-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="ee31b-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ee31b-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ee31b-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ee31b-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ee31b-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ee31b-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="ee31b-114">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="ee31b-114">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="ee31b-115">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="ee31b-115">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="ee31b-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ee31b-116">Request</span></span>

<span data-ttu-id="ee31b-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="ee31b-117">This method has the following syntax.</span></span> <span data-ttu-id="ee31b-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="ee31b-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="ee31b-119">Methode</span><span class="sxs-lookup"><span data-stu-id="ee31b-119">Method</span></span> | <span data-ttu-id="ee31b-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ee31b-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="ee31b-121">PUT</span><span class="sxs-lookup"><span data-stu-id="ee31b-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions{submissionId}``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="ee31b-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ee31b-122">Request header</span></span>

| <span data-ttu-id="ee31b-123">Header</span><span class="sxs-lookup"><span data-stu-id="ee31b-123">Header</span></span>        | <span data-ttu-id="ee31b-124">Typ</span><span class="sxs-lookup"><span data-stu-id="ee31b-124">Type</span></span>   | <span data-ttu-id="ee31b-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee31b-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ee31b-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ee31b-126">Authorization</span></span> | <span data-ttu-id="ee31b-127">String</span><span class="sxs-lookup"><span data-stu-id="ee31b-127">string</span></span> | <span data-ttu-id="ee31b-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee31b-128">Required.</span></span> <span data-ttu-id="ee31b-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ee31b-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="ee31b-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ee31b-130">Request parameters</span></span>

| <span data-ttu-id="ee31b-131">Name</span><span class="sxs-lookup"><span data-stu-id="ee31b-131">Name</span></span>        | <span data-ttu-id="ee31b-132">Typ</span><span class="sxs-lookup"><span data-stu-id="ee31b-132">Type</span></span>   | <span data-ttu-id="ee31b-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee31b-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ee31b-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="ee31b-134">applicationId</span></span> | <span data-ttu-id="ee31b-135">String</span><span class="sxs-lookup"><span data-stu-id="ee31b-135">string</span></span> | <span data-ttu-id="ee31b-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee31b-136">Required.</span></span> <span data-ttu-id="ee31b-137">Die Store-ID der App, für die Sie eine Flight Paketübermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ee31b-137">The Store ID of the app for which you want to update a package flight submission.</span></span> <span data-ttu-id="ee31b-138">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="ee31b-138">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="ee31b-139">flightId</span><span class="sxs-lookup"><span data-stu-id="ee31b-139">flightId</span></span> | <span data-ttu-id="ee31b-140">String</span><span class="sxs-lookup"><span data-stu-id="ee31b-140">string</span></span> | <span data-ttu-id="ee31b-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee31b-141">Required.</span></span> <span data-ttu-id="ee31b-142">Die ID des Flight-Pakets, für das Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ee31b-142">The ID of the package flight for which you want to update a submission.</span></span> <span data-ttu-id="ee31b-143">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="ee31b-143">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |
| <span data-ttu-id="ee31b-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="ee31b-144">submissionId</span></span> | <span data-ttu-id="ee31b-145">String</span><span class="sxs-lookup"><span data-stu-id="ee31b-145">string</span></span> | <span data-ttu-id="ee31b-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee31b-146">Required.</span></span> <span data-ttu-id="ee31b-147">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ee31b-147">The ID of the submission to update.</span></span> <span data-ttu-id="ee31b-148">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="ee31b-148">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="ee31b-149">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="ee31b-149">Request body</span></span>

<span data-ttu-id="ee31b-150">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="ee31b-150">The request body has the following parameters.</span></span>

| <span data-ttu-id="ee31b-151">Wert</span><span class="sxs-lookup"><span data-stu-id="ee31b-151">Value</span></span>      | <span data-ttu-id="ee31b-152">Typ</span><span class="sxs-lookup"><span data-stu-id="ee31b-152">Type</span></span>   | <span data-ttu-id="ee31b-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee31b-153">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ee31b-154">flightPackages</span><span class="sxs-lookup"><span data-stu-id="ee31b-154">flightPackages</span></span>           | <span data-ttu-id="ee31b-155">array</span><span class="sxs-lookup"><span data-stu-id="ee31b-155">array</span></span>  | <span data-ttu-id="ee31b-156">Enthält Objekte, die Details über die einzelnen Pakete der Übermittlung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ee31b-156">Contains objects that provide details about each package in the submission.</span></span> <span data-ttu-id="ee31b-157">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-package-object).</span><span class="sxs-lookup"><span data-stu-id="ee31b-157">For more details about the values in the response body, see [Flight package resource](manage-flight-submissions.md#flight-package-object).</span></span> <span data-ttu-id="ee31b-158">Beim Aufruf dieser Methode zur Aktualisierung einer App-Übermittlung sind im Antworttext nur die *fileName*-, *fileStatus*-, *minimumDirectXVersion*- und *minimumSystemRam*-Werte dieser Objekte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ee31b-158">When calling this method to update an app submission, only the *fileName*, *fileStatus*, *minimumDirectXVersion*, and *minimumSystemRam* values of these objects are required in the request body.</span></span> <span data-ttu-id="ee31b-159">Die übrigen Werte werden von Dev Center aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="ee31b-159">The other values are populated by Dev Center.</span></span> |
| <span data-ttu-id="ee31b-160">packageDeliveryOptions</span><span class="sxs-lookup"><span data-stu-id="ee31b-160">packageDeliveryOptions</span></span>    | <span data-ttu-id="ee31b-161">object</span><span class="sxs-lookup"><span data-stu-id="ee31b-161">object</span></span>  | <span data-ttu-id="ee31b-162">Enthält den schrittweisen Paketrollout sowie erforderliche Einstellungen für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ee31b-162">Contains gradual package rollout and mandatory update settings for the submission.</span></span> <span data-ttu-id="ee31b-163">Weitere Informationen finden Sie unter [options-Objekt für die Paketübermittlung](manage-flight-submissions.md#package-delivery-options-object).</span><span class="sxs-lookup"><span data-stu-id="ee31b-163">For more information, see [Package delivery options object](manage-flight-submissions.md#package-delivery-options-object).</span></span>  |
| <span data-ttu-id="ee31b-164">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="ee31b-164">targetPublishMode</span></span>           | <span data-ttu-id="ee31b-165">string</span><span class="sxs-lookup"><span data-stu-id="ee31b-165">string</span></span>  | <span data-ttu-id="ee31b-166">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ee31b-166">The publish mode for the submission.</span></span> <span data-ttu-id="ee31b-167">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="ee31b-167">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="ee31b-168">Immediate</span><span class="sxs-lookup"><span data-stu-id="ee31b-168">Immediate</span></span></li><li><span data-ttu-id="ee31b-169">Manual</span><span class="sxs-lookup"><span data-stu-id="ee31b-169">Manual</span></span></li><li><span data-ttu-id="ee31b-170">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="ee31b-170">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="ee31b-171">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="ee31b-171">targetPublishDate</span></span>           | <span data-ttu-id="ee31b-172">string</span><span class="sxs-lookup"><span data-stu-id="ee31b-172">string</span></span>  | <span data-ttu-id="ee31b-173">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="ee31b-173">The publish date for the submission in in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |
| <span data-ttu-id="ee31b-174">notesForCertification</span><span class="sxs-lookup"><span data-stu-id="ee31b-174">notesForCertification</span></span>           | <span data-ttu-id="ee31b-175">string</span><span class="sxs-lookup"><span data-stu-id="ee31b-175">string</span></span>  |  <span data-ttu-id="ee31b-176">Enthält zusätzliche Informationen für Zertifizierungstester wie Anmeldeinformationen für Testkonten und Schritte zum Zugriff auf und zur Überprüfung von Features.</span><span class="sxs-lookup"><span data-stu-id="ee31b-176">Provides additional info for the certification testers, such as test account credentials and steps to access and verify features.</span></span> <span data-ttu-id="ee31b-177">Weitere Informationen finden Sie unter [Hinweise zur Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span><span class="sxs-lookup"><span data-stu-id="ee31b-177">For more information, see [Notes for certification](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification).</span></span> |

<span/>

### <a name="request-example"></a><span data-ttu-id="ee31b-178">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ee31b-178">Request example</span></span>

<span data-ttu-id="ee31b-179">Im folgenden Beispiel wird die Aktualisierung einer Flight-Paketübermittlung für eine App veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="ee31b-179">The following example demonstrates how to update a package flight submission for an app.</span></span>

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

## <a name="response"></a><span data-ttu-id="ee31b-180">Antwort</span><span class="sxs-lookup"><span data-stu-id="ee31b-180">Response</span></span>

<span data-ttu-id="ee31b-181">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ee31b-181">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="ee31b-182">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="ee31b-182">The response body contains information about the updated submission.</span></span> <span data-ttu-id="ee31b-183">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="ee31b-183">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="ee31b-184">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ee31b-184">Error codes</span></span>

<span data-ttu-id="ee31b-185">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="ee31b-185">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="ee31b-186">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="ee31b-186">Error code</span></span> |  <span data-ttu-id="ee31b-187">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ee31b-187">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="ee31b-188">400</span><span class="sxs-lookup"><span data-stu-id="ee31b-188">400</span></span>  | <span data-ttu-id="ee31b-189">Die Flight-Paketübermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="ee31b-189">The package flight submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="ee31b-190">409</span><span class="sxs-lookup"><span data-stu-id="ee31b-190">409</span></span>  | <span data-ttu-id="ee31b-191">Die Flight-Paketübermittlung konnte im aktuellen Zustand der App nicht aktualisiert werden, oder in der App wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="ee31b-191">The package flight submission could not be updated because of the current state of the app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   

<span/>


## <a name="related-topics"></a><span data-ttu-id="ee31b-192">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ee31b-192">Related topics</span></span>

* [<span data-ttu-id="ee31b-193">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="ee31b-193">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="ee31b-194">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="ee31b-194">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="ee31b-195">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-195">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="ee31b-196">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-196">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="ee31b-197">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-197">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="ee31b-198">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-198">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="ee31b-199">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="ee31b-199">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
