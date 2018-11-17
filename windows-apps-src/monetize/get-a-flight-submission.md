---
author: Xansky
ms.assetid: A0DFF26B-FE06-459B-ABDC-3EA4FEB7A21E
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Daten für eine vorhandene Flight-Paketübermittlung abzurufen.
title: Abrufen einer Flight-Paket-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: f9f40219503c0a57f76fcee81858acf51f59b1df
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7106576"
---
# <a name="get-a-package-flight-submission"></a><span data-ttu-id="099be-104">Abrufen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="099be-104">Get a package flight submission</span></span>

<span data-ttu-id="099be-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Daten für eine vorhandene Flight-Paketübermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="099be-105">Use this method in the Microsoft Store submission API to get data for an existing package flight submission.</span></span> <span data-ttu-id="099be-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="099be-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="099be-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="099be-107">Prerequisites</span></span>

<span data-ttu-id="099be-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="099be-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="099be-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="099be-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="099be-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="099be-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="099be-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="099be-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="099be-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="099be-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="099be-113">Erstellen Sie eine Flight-Paketübermittlung für eine app im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="099be-113">Create a package flight submission for an app in Partner Center.</span></span> <span data-ttu-id="099be-114">Sie können dies im Partner Center oder hierzu können Sie mithilfe der Methode [Erstellen Sie eine Flight-Paketübermittlung](create-a-flight-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="099be-114">You can do this in Partner Center, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="099be-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="099be-115">Request</span></span>

<span data-ttu-id="099be-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="099be-116">This method has the following syntax.</span></span> <span data-ttu-id="099be-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="099be-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="099be-118">Methode</span><span class="sxs-lookup"><span data-stu-id="099be-118">Method</span></span> | <span data-ttu-id="099be-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="099be-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="099be-120">GET</span><span class="sxs-lookup"><span data-stu-id="099be-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="099be-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="099be-121">Request header</span></span>

| <span data-ttu-id="099be-122">Header</span><span class="sxs-lookup"><span data-stu-id="099be-122">Header</span></span>        | <span data-ttu-id="099be-123">Typ</span><span class="sxs-lookup"><span data-stu-id="099be-123">Type</span></span>   | <span data-ttu-id="099be-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="099be-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="099be-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="099be-125">Authorization</span></span> | <span data-ttu-id="099be-126">String</span><span class="sxs-lookup"><span data-stu-id="099be-126">string</span></span> | <span data-ttu-id="099be-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="099be-127">Required.</span></span> <span data-ttu-id="099be-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="099be-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="099be-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="099be-129">Request parameters</span></span>

| <span data-ttu-id="099be-130">Name</span><span class="sxs-lookup"><span data-stu-id="099be-130">Name</span></span>        | <span data-ttu-id="099be-131">Typ</span><span class="sxs-lookup"><span data-stu-id="099be-131">Type</span></span>   | <span data-ttu-id="099be-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="099be-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="099be-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="099be-133">applicationId</span></span> | <span data-ttu-id="099be-134">String</span><span class="sxs-lookup"><span data-stu-id="099be-134">string</span></span> | <span data-ttu-id="099be-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="099be-135">Required.</span></span> <span data-ttu-id="099be-136">Die Store-ID der App mit der abzurufenden Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="099be-136">The Store ID of the app that contains the package flight submission you want to get.</span></span> <span data-ttu-id="099be-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="099be-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="099be-138">flightId</span><span class="sxs-lookup"><span data-stu-id="099be-138">flightId</span></span> | <span data-ttu-id="099be-139">String</span><span class="sxs-lookup"><span data-stu-id="099be-139">string</span></span> | <span data-ttu-id="099be-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="099be-140">Required.</span></span> <span data-ttu-id="099be-141">Die ID des Flight-Pakets mit der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="099be-141">The ID of the package flight that contains the submission you want to get.</span></span> <span data-ttu-id="099be-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="099be-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="099be-143">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="099be-143">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center.</span></span>  |
| <span data-ttu-id="099be-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="099be-144">submissionId</span></span> | <span data-ttu-id="099be-145">String</span><span class="sxs-lookup"><span data-stu-id="099be-145">string</span></span> | <span data-ttu-id="099be-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="099be-146">Required.</span></span> <span data-ttu-id="099be-147">Die ID der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="099be-147">The ID of the submission to get.</span></span> <span data-ttu-id="099be-148">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="099be-148">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="099be-149">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="099be-149">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="099be-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="099be-150">Request body</span></span>

<span data-ttu-id="099be-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="099be-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="099be-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="099be-152">Request example</span></span>

<span data-ttu-id="099be-153">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Flight-Paketübermittlung für eine App mit der Store-ID 9WZDNCRD91MD abrufen können.</span><span class="sxs-lookup"><span data-stu-id="099be-153">The following example demonstrates how to get a package flight submission for an app that has the Store ID 9WZDNCRD91MD.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="099be-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="099be-154">Response</span></span>

<span data-ttu-id="099be-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="099be-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="099be-156">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="099be-156">The response body contains information about the specified submission.</span></span> <span data-ttu-id="099be-157">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketübermittlungsressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="099be-157">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="099be-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="099be-158">Error codes</span></span>

<span data-ttu-id="099be-159">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="099be-159">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="099be-160">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="099be-160">Error code</span></span> |  <span data-ttu-id="099be-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="099be-161">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="099be-162">404</span><span class="sxs-lookup"><span data-stu-id="099be-162">404</span></span>  | <span data-ttu-id="099be-163">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="099be-163">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="099be-164">409</span><span class="sxs-lookup"><span data-stu-id="099be-164">409</span></span>  | <span data-ttu-id="099be-165">Die Flight-Paketübermittlung gehört nicht zum das angegebene Flight-Paket, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="099be-165">The package flight submission does not belong to the specified package flight, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="099be-166">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="099be-166">Related topics</span></span>

* [<span data-ttu-id="099be-167">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="099be-167">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="099be-168">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="099be-168">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="099be-169">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="099be-169">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="099be-170">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="099be-170">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="099be-171">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="099be-171">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="099be-172">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="099be-172">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
