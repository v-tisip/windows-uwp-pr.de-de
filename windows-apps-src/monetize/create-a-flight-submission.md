---
author: Xansky
ms.assetid: CD866083-EB7F-4389-A907-FC43DC2FCB5E
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue Flight-Paketübermittlung für eine app zu erstellen, die für Ihr Partner Center-Konto registriert ist.
title: Erstellen einer Flight-Paket-Übermittlung
ms.author: mhopkins
ms.date: 08/03/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Erstellen einer Flight-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 4cdcc0f06820600523be111d67d3cad5e38b6ceb
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7422271"
---
# <a name="create-a-package-flight-submission"></a><span data-ttu-id="20f1c-104">Erstellen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-104">Create a package flight submission</span></span>

<span data-ttu-id="20f1c-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen einer neuen Übermittlung eines Flight-Pakets für eine App.</span><span class="sxs-lookup"><span data-stu-id="20f1c-105">Use this method in the Microsoft Store submission API to create a new submission for a package flight for an app.</span></span> <span data-ttu-id="20f1c-106">Nachdem Sie erfolgreich eine neue Übermittlung mit dieser Methode erstellt haben, [aktualisieren Sie die Übermittlung](update-a-flight-submission.md), um erforderliche Änderungen an den Übermittlungsdaten vorzunehmen, und führen Sie ein [Commit für die Übermittlung](commit-a-flight-submission.md) zur Aufnahme und Veröffentlichung durch.</span><span class="sxs-lookup"><span data-stu-id="20f1c-106">After you successfully create a new submission by using this method, [update the submission](update-a-flight-submission.md) to make any necessary changes to the submission data, and then [commit the submission](commit-a-flight-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="20f1c-107">Weitere Informationen dazu, wie diese Methode in das Erstellen einer Flight-Paketübermittlung mit der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="20f1c-107">For more information about how this method fits into the process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="20f1c-108">Diese Methode erstellt eine Übermittlung für einen vorhandenes Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="20f1c-108">This method creates a submission for an existing package flight.</span></span> <span data-ttu-id="20f1c-109">Verwenden Sie zum Erstellen eines Flight-Pakets die Methode zum [Erstellen eines Flight-Pakets](create-a-flight.md).</span><span class="sxs-lookup"><span data-stu-id="20f1c-109">To create a package flight, use the [create a package flight](create-a-flight.md) method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20f1c-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="20f1c-110">Prerequisites</span></span>

<span data-ttu-id="20f1c-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="20f1c-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="20f1c-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="20f1c-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="20f1c-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="20f1c-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="20f1c-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="20f1c-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="20f1c-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="20f1c-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="20f1c-116">Erstellen Sie eine Flight-Paket für eine app.</span><span class="sxs-lookup"><span data-stu-id="20f1c-116">Create a package flight for an app.</span></span> <span data-ttu-id="20f1c-117">Sie dazu im Partner Center, oder Sie können dies tun, indem Sie mit der Methode [eine Flight-Paket zu erstellen](create-a-flight.md) .</span><span class="sxs-lookup"><span data-stu-id="20f1c-117">You can do this in Partner Center, or you can do this by using the [create a package flight](create-a-flight.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="20f1c-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="20f1c-118">Request</span></span>

<span data-ttu-id="20f1c-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="20f1c-119">This method has the following syntax.</span></span> <span data-ttu-id="20f1c-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="20f1c-120">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="20f1c-121">Methode</span><span class="sxs-lookup"><span data-stu-id="20f1c-121">Method</span></span> | <span data-ttu-id="20f1c-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="20f1c-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="20f1c-123">POST</span><span class="sxs-lookup"><span data-stu-id="20f1c-123">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions``` |


### <a name="request-header"></a><span data-ttu-id="20f1c-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="20f1c-124">Request header</span></span>

| <span data-ttu-id="20f1c-125">Header</span><span class="sxs-lookup"><span data-stu-id="20f1c-125">Header</span></span>        | <span data-ttu-id="20f1c-126">Typ</span><span class="sxs-lookup"><span data-stu-id="20f1c-126">Type</span></span>   | <span data-ttu-id="20f1c-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="20f1c-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="20f1c-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="20f1c-128">Authorization</span></span> | <span data-ttu-id="20f1c-129">String</span><span class="sxs-lookup"><span data-stu-id="20f1c-129">string</span></span> | <span data-ttu-id="20f1c-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="20f1c-130">Required.</span></span> <span data-ttu-id="20f1c-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="20f1c-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="20f1c-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="20f1c-132">Request parameters</span></span>

| <span data-ttu-id="20f1c-133">Name</span><span class="sxs-lookup"><span data-stu-id="20f1c-133">Name</span></span>        | <span data-ttu-id="20f1c-134">Typ</span><span class="sxs-lookup"><span data-stu-id="20f1c-134">Type</span></span>   | <span data-ttu-id="20f1c-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="20f1c-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="20f1c-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="20f1c-136">applicationId</span></span> | <span data-ttu-id="20f1c-137">String</span><span class="sxs-lookup"><span data-stu-id="20f1c-137">string</span></span> | <span data-ttu-id="20f1c-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="20f1c-138">Required.</span></span> <span data-ttu-id="20f1c-139">Die Store-ID der App, für die Sie eine Flight-Paketübermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="20f1c-139">The Store ID of the app for which you want to create a package flight submission.</span></span> <span data-ttu-id="20f1c-140">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="20f1c-140">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="20f1c-141">flightId</span><span class="sxs-lookup"><span data-stu-id="20f1c-141">flightId</span></span> | <span data-ttu-id="20f1c-142">String</span><span class="sxs-lookup"><span data-stu-id="20f1c-142">string</span></span> | <span data-ttu-id="20f1c-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="20f1c-143">Required.</span></span> <span data-ttu-id="20f1c-144">Die ID des Flight-Pakets, für das Sie die Übermittlung hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="20f1c-144">The ID of the package flight for which you want to add the submission.</span></span> <span data-ttu-id="20f1c-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="20f1c-145">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="20f1c-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="20f1c-146">Request body</span></span>

<span data-ttu-id="20f1c-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="20f1c-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="20f1c-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="20f1c-148">Request example</span></span>

<span data-ttu-id="20f1c-149">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Flight-Paketübermittlung für eine App mit der Store-ID 9WZDNCRD91MD erstellen.</span><span class="sxs-lookup"><span data-stu-id="20f1c-149">The following example demonstrates how to create a new package flight submission for an app that has the Store ID 9WZDNCRD91MD.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="20f1c-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="20f1c-150">Response</span></span>

<span data-ttu-id="20f1c-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="20f1c-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="20f1c-152">Der Antworttext enthält Informationen zur neuen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="20f1c-152">The response body contains information about the new submission.</span></span> <span data-ttu-id="20f1c-153">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="20f1c-153">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="20f1c-154">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="20f1c-154">Error codes</span></span>

<span data-ttu-id="20f1c-155">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="20f1c-155">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="20f1c-156">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="20f1c-156">Error code</span></span> |  <span data-ttu-id="20f1c-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="20f1c-157">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="20f1c-158">400</span><span class="sxs-lookup"><span data-stu-id="20f1c-158">400</span></span>  | <span data-ttu-id="20f1c-159">Die Flight-Paketübermittlung konnte nicht erstellt werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="20f1c-159">The package flight submission could not be created because the request is invalid.</span></span> |
| <span data-ttu-id="20f1c-160">409</span><span class="sxs-lookup"><span data-stu-id="20f1c-160">409</span></span>  | <span data-ttu-id="20f1c-161">Die Flight-Paketübermittlung konnte im aktuellen Zustand der app nicht erstellt werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="20f1c-161">The package flight submission could not be created because of the current state of the app, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="20f1c-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="20f1c-162">Related topics</span></span>

* [<span data-ttu-id="20f1c-163">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="20f1c-163">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="20f1c-164">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="20f1c-164">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="20f1c-165">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-165">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="20f1c-166">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-166">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="20f1c-167">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-167">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="20f1c-168">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-168">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
* [<span data-ttu-id="20f1c-169">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="20f1c-169">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
