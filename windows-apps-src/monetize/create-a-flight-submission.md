---
author: Xansky
ms.assetid: CD866083-EB7F-4389-A907-FC43DC2FCB5E
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen einer neuen Flight-Paketübermittlung für eine App, die für Ihr Windows Dev Center-Konto registriert ist.
title: Erstellen einer Flight-Paket-Übermittlung
ms.author: mhopkins
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Erstellen einer Flight-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 87e544c2d9d04e62f324fe14cd7aab3e1b7ee500
ms.sourcegitcommit: 2c4daa36fb9fd3e8daa83c2bd0825f3989d24be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5512217"
---
# <a name="create-a-package-flight-submission"></a><span data-ttu-id="3c8c5-104">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-104">Create a package flight submission</span></span>

<span data-ttu-id="3c8c5-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen einer neuen Übermittlung eines Flight-Pakets für eine App.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-105">Use this method in the Microsoft Store submission API to create a new submission for a package flight for an app.</span></span> <span data-ttu-id="3c8c5-106">Nachdem Sie erfolgreich eine neue Übermittlung mit dieser Methode erstellt haben, [aktualisieren Sie die Übermittlung](update-a-flight-submission.md), um erforderliche Änderungen an den Übermittlungsdaten vorzunehmen, und führen Sie ein [Commit für die Übermittlung](commit-a-flight-submission.md) zur Aufnahme und Veröffentlichung durch.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-106">After you successfully create a new submission by using this method, [update the submission](update-a-flight-submission.md) to make any necessary changes to the submission data, and then [commit the submission](commit-a-flight-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="3c8c5-107">Weitere Informationen dazu, wie diese Methode in das Erstellen einer Flight-Paketübermittlung mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="3c8c5-107">For more information about how this method fits into the process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3c8c5-108">Diese Methode erstellt eine Übermittlung für einen vorhandenes Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-108">This method creates a submission for an existing package flight.</span></span> <span data-ttu-id="3c8c5-109">Verwenden Sie zum Erstellen eines Flight-Pakets die Methode zum [Erstellen eines Flight-Pakets](create-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="3c8c5-109">To create a package flight, use the [create a package flight](create-a-flight.md) method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3c8c5-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3c8c5-110">Prerequisites</span></span>

<span data-ttu-id="3c8c5-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="3c8c5-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="3c8c5-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="3c8c5-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="3c8c5-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="3c8c5-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="3c8c5-116">Erstellen Sie ein Flight-Paket für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-116">Create a package flight for an app in your Dev Center account.</span></span> <span data-ttu-id="3c8c5-117">Verwenden Sie hierzu das Dev Center-Dashboard oder die Methode zum [Erstellen eines Flight-Pakets](create-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="3c8c5-117">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight](create-a-flight.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="3c8c5-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-118">Request</span></span>

<span data-ttu-id="3c8c5-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-119">This method has the following syntax.</span></span> <span data-ttu-id="3c8c5-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-120">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="3c8c5-121">Methode</span><span class="sxs-lookup"><span data-stu-id="3c8c5-121">Method</span></span> | <span data-ttu-id="3c8c5-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="3c8c5-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="3c8c5-123">POST</span><span class="sxs-lookup"><span data-stu-id="3c8c5-123">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions``` |


### <a name="request-header"></a><span data-ttu-id="3c8c5-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="3c8c5-124">Request header</span></span>

| <span data-ttu-id="3c8c5-125">Header</span><span class="sxs-lookup"><span data-stu-id="3c8c5-125">Header</span></span>        | <span data-ttu-id="3c8c5-126">Typ</span><span class="sxs-lookup"><span data-stu-id="3c8c5-126">Type</span></span>   | <span data-ttu-id="3c8c5-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="3c8c5-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-128">Authorization</span></span> | <span data-ttu-id="3c8c5-129">String</span><span class="sxs-lookup"><span data-stu-id="3c8c5-129">string</span></span> | <span data-ttu-id="3c8c5-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-130">Required.</span></span> <span data-ttu-id="3c8c5-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="3c8c5-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="3c8c5-132">Request parameters</span></span>

| <span data-ttu-id="3c8c5-133">Name</span><span class="sxs-lookup"><span data-stu-id="3c8c5-133">Name</span></span>        | <span data-ttu-id="3c8c5-134">Typ</span><span class="sxs-lookup"><span data-stu-id="3c8c5-134">Type</span></span>   | <span data-ttu-id="3c8c5-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="3c8c5-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="3c8c5-136">applicationId</span></span> | <span data-ttu-id="3c8c5-137">String</span><span class="sxs-lookup"><span data-stu-id="3c8c5-137">string</span></span> | <span data-ttu-id="3c8c5-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-138">Required.</span></span> <span data-ttu-id="3c8c5-139">Die Store-ID der App, für die Sie eine Flight-Paketübermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-139">The Store ID of the app for which you want to create a package flight submission.</span></span> <span data-ttu-id="3c8c5-140">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="3c8c5-140">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="3c8c5-141">flightId</span><span class="sxs-lookup"><span data-stu-id="3c8c5-141">flightId</span></span> | <span data-ttu-id="3c8c5-142">String</span><span class="sxs-lookup"><span data-stu-id="3c8c5-142">string</span></span> | <span data-ttu-id="3c8c5-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-143">Required.</span></span> <span data-ttu-id="3c8c5-144">Die ID des Flight-Pakets, für das Sie die Übermittlung hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-144">The ID of the package flight for which you want to add the submission.</span></span> <span data-ttu-id="3c8c5-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-145">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="3c8c5-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="3c8c5-146">Request body</span></span>

<span data-ttu-id="3c8c5-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="3c8c5-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="3c8c5-148">Request example</span></span>

<span data-ttu-id="3c8c5-149">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Flight-Paketübermittlung für eine App mit der Store-ID 9WZDNCRD91MD erstellen.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-149">The following example demonstrates how to create a new package flight submission for an app that has the Store ID 9WZDNCRD91MD.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="3c8c5-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="3c8c5-150">Response</span></span>

<span data-ttu-id="3c8c5-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="3c8c5-152">Der Antworttext enthält Informationen zur neuen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-152">The response body contains information about the new submission.</span></span> <span data-ttu-id="3c8c5-153">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="3c8c5-153">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="3c8c5-154">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3c8c5-154">Error codes</span></span>

<span data-ttu-id="3c8c5-155">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-155">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="3c8c5-156">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="3c8c5-156">Error code</span></span> |  <span data-ttu-id="3c8c5-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-157">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="3c8c5-158">400</span><span class="sxs-lookup"><span data-stu-id="3c8c5-158">400</span></span>  | <span data-ttu-id="3c8c5-159">Die Flight-Paketübermittlung konnte nicht erstellt werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-159">The package flight submission could not be created because the request is invalid.</span></span> |
| <span data-ttu-id="3c8c5-160">409</span><span class="sxs-lookup"><span data-stu-id="3c8c5-160">409</span></span>  | <span data-ttu-id="3c8c5-161">Die Flight-Paketübermittlung konnte im aktuellen Zustand der App nicht erstellt werden, oder in der App wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="3c8c5-161">The package flight submission could not be created because of the current state of the app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="3c8c5-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3c8c5-162">Related topics</span></span>

* [<span data-ttu-id="3c8c5-163">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="3c8c5-163">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="3c8c5-164">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="3c8c5-164">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="3c8c5-165">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-165">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="3c8c5-166">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-166">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="3c8c5-167">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-167">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="3c8c5-168">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-168">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="3c8c5-169">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="3c8c5-169">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
