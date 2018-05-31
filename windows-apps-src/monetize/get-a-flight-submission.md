---
author: mcleanbyron
ms.assetid: A0DFF26B-FE06-459B-ABDC-3EA4FEB7A21E
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Daten für eine vorhandene Flight-Paketübermittlung abzurufen.
title: Abrufen einer Flight-Paket-Übermittlung
ms.author: mcleans
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: b3c2dcafb391877c878c368beb97d32416cf00fe
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817398"
---
# <a name="get-a-package-flight-submission"></a><span data-ttu-id="8ec1a-104">Abrufen einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-104">Get a package flight submission</span></span>

<span data-ttu-id="8ec1a-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Daten für eine vorhandene Flight-Paketübermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-105">Use this method in the Microsoft Store submission API to get data for an existing package flight submission.</span></span> <span data-ttu-id="8ec1a-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1a-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ec1a-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8ec1a-107">Prerequisites</span></span>

<span data-ttu-id="8ec1a-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="8ec1a-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="8ec1a-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="8ec1a-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="8ec1a-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="8ec1a-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="8ec1a-113">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-113">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="8ec1a-114">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-114">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="8ec1a-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-115">Request</span></span>

<span data-ttu-id="8ec1a-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-116">This method has the following syntax.</span></span> <span data-ttu-id="8ec1a-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="8ec1a-118">Methode</span><span class="sxs-lookup"><span data-stu-id="8ec1a-118">Method</span></span> | <span data-ttu-id="8ec1a-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="8ec1a-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="8ec1a-120">GET</span><span class="sxs-lookup"><span data-stu-id="8ec1a-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="8ec1a-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="8ec1a-121">Request header</span></span>

| <span data-ttu-id="8ec1a-122">Header</span><span class="sxs-lookup"><span data-stu-id="8ec1a-122">Header</span></span>        | <span data-ttu-id="8ec1a-123">Typ</span><span class="sxs-lookup"><span data-stu-id="8ec1a-123">Type</span></span>   | <span data-ttu-id="8ec1a-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="8ec1a-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-125">Authorization</span></span> | <span data-ttu-id="8ec1a-126">String</span><span class="sxs-lookup"><span data-stu-id="8ec1a-126">string</span></span> | <span data-ttu-id="8ec1a-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-127">Required.</span></span> <span data-ttu-id="8ec1a-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="8ec1a-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="8ec1a-129">Request parameters</span></span>

| <span data-ttu-id="8ec1a-130">Name</span><span class="sxs-lookup"><span data-stu-id="8ec1a-130">Name</span></span>        | <span data-ttu-id="8ec1a-131">Typ</span><span class="sxs-lookup"><span data-stu-id="8ec1a-131">Type</span></span>   | <span data-ttu-id="8ec1a-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="8ec1a-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="8ec1a-133">applicationId</span></span> | <span data-ttu-id="8ec1a-134">String</span><span class="sxs-lookup"><span data-stu-id="8ec1a-134">string</span></span> | <span data-ttu-id="8ec1a-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-135">Required.</span></span> <span data-ttu-id="8ec1a-136">Die Store-ID der App mit der abzurufenden Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-136">The Store ID of the app that contains the package flight submission you want to get.</span></span> <span data-ttu-id="8ec1a-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="8ec1a-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="8ec1a-138">flightId</span><span class="sxs-lookup"><span data-stu-id="8ec1a-138">flightId</span></span> | <span data-ttu-id="8ec1a-139">String</span><span class="sxs-lookup"><span data-stu-id="8ec1a-139">string</span></span> | <span data-ttu-id="8ec1a-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-140">Required.</span></span> <span data-ttu-id="8ec1a-141">Die ID des Flight-Pakets mit der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-141">The ID of the package flight that contains the submission you want to get.</span></span> <span data-ttu-id="8ec1a-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="8ec1a-143">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-143">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="8ec1a-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="8ec1a-144">submissionId</span></span> | <span data-ttu-id="8ec1a-145">String</span><span class="sxs-lookup"><span data-stu-id="8ec1a-145">string</span></span> | <span data-ttu-id="8ec1a-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-146">Required.</span></span> <span data-ttu-id="8ec1a-147">Die ID der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-147">The ID of the submission to get.</span></span> <span data-ttu-id="8ec1a-148">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-148">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="8ec1a-149">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-149">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="8ec1a-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="8ec1a-150">Request body</span></span>

<span data-ttu-id="8ec1a-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="8ec1a-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="8ec1a-152">Request example</span></span>

<span data-ttu-id="8ec1a-153">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Flight-Paketübermittlung für eine App mit der Store-ID 9WZDNCRD91MD abrufen können.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-153">The following example demonstrates how to get a package flight submission for an app that has the Store ID 9WZDNCRD91MD.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="8ec1a-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="8ec1a-154">Response</span></span>

<span data-ttu-id="8ec1a-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="8ec1a-156">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-156">The response body contains information about the specified submission.</span></span> <span data-ttu-id="8ec1a-157">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Flight-Paketübermittlungsressource](manage-flight-submissions.md#flight-submission-object).</span><span class="sxs-lookup"><span data-stu-id="8ec1a-157">For more details about the values in the response body, see [Package flight submission resource](manage-flight-submissions.md#flight-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="8ec1a-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="8ec1a-158">Error codes</span></span>

<span data-ttu-id="8ec1a-159">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-159">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="8ec1a-160">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="8ec1a-160">Error code</span></span> |  <span data-ttu-id="8ec1a-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-161">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="8ec1a-162">404</span><span class="sxs-lookup"><span data-stu-id="8ec1a-162">404</span></span>  | <span data-ttu-id="8ec1a-163">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="8ec1a-163">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="8ec1a-164">409</span><span class="sxs-lookup"><span data-stu-id="8ec1a-164">409</span></span>  | <span data-ttu-id="8ec1a-165">Die Flight-Paket-Übermittlung gehört nicht zum angegebenen Flight-Paket, oder die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="8ec1a-165">The package flight submission does not belong to the specified package flight, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="8ec1a-166">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8ec1a-166">Related topics</span></span>

* [<span data-ttu-id="8ec1a-167">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="8ec1a-167">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="8ec1a-168">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="8ec1a-168">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="8ec1a-169">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-169">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="8ec1a-170">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-170">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="8ec1a-171">Aktualisieren einer Flight-Paket-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-171">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="8ec1a-172">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="8ec1a-172">Delete a package flight submission</span></span>](delete-a-flight-submission.md)
