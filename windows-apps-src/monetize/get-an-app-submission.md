---
ms.assetid: BF296C25-A2E6-48E4-9D08-0CCDB5FAE0C8
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für eine vorhandene App-Übermittlung.
title: Abrufen einer App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, App-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: ca13ff36db823bfea44fa9e31c20a621c5b8aa2e
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8734857"
---
# <a name="get-an-app-submission"></a><span data-ttu-id="068c3-104">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-104">Get an app submission</span></span>


<span data-ttu-id="068c3-105">Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für eine vorhandene App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="068c3-105">Use this method in the Microsoft Store submission API to get data for an existing app submission.</span></span> <span data-ttu-id="068c3-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="068c3-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="068c3-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="068c3-107">Prerequisites</span></span>

<span data-ttu-id="068c3-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="068c3-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="068c3-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="068c3-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="068c3-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="068c3-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="068c3-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="068c3-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="068c3-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="068c3-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="068c3-113">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="068c3-113">Create a submission for one of your apps.</span></span> <span data-ttu-id="068c3-114">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="068c3-114">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="068c3-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="068c3-115">Request</span></span>

<span data-ttu-id="068c3-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="068c3-116">This method has the following syntax.</span></span> <span data-ttu-id="068c3-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="068c3-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="068c3-118">Methode</span><span class="sxs-lookup"><span data-stu-id="068c3-118">Method</span></span> | <span data-ttu-id="068c3-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="068c3-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="068c3-120">GET</span><span class="sxs-lookup"><span data-stu-id="068c3-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId} ``` |


### <a name="request-header"></a><span data-ttu-id="068c3-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="068c3-121">Request header</span></span>

| <span data-ttu-id="068c3-122">Header</span><span class="sxs-lookup"><span data-stu-id="068c3-122">Header</span></span>        | <span data-ttu-id="068c3-123">Typ</span><span class="sxs-lookup"><span data-stu-id="068c3-123">Type</span></span>   | <span data-ttu-id="068c3-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="068c3-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="068c3-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="068c3-125">Authorization</span></span> | <span data-ttu-id="068c3-126">String</span><span class="sxs-lookup"><span data-stu-id="068c3-126">string</span></span> | <span data-ttu-id="068c3-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="068c3-127">Required.</span></span> <span data-ttu-id="068c3-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="068c3-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="068c3-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="068c3-129">Request parameters</span></span>

| <span data-ttu-id="068c3-130">Name</span><span class="sxs-lookup"><span data-stu-id="068c3-130">Name</span></span>        | <span data-ttu-id="068c3-131">Typ</span><span class="sxs-lookup"><span data-stu-id="068c3-131">Type</span></span>   | <span data-ttu-id="068c3-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="068c3-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="068c3-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="068c3-133">applicationId</span></span> | <span data-ttu-id="068c3-134">String</span><span class="sxs-lookup"><span data-stu-id="068c3-134">string</span></span> | <span data-ttu-id="068c3-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="068c3-135">Required.</span></span> <span data-ttu-id="068c3-136">Die Store-ID der App, deren Übermittlung Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="068c3-136">The Store ID of the app with the submission you want to get.</span></span> <span data-ttu-id="068c3-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="068c3-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="068c3-138">submissionId</span><span class="sxs-lookup"><span data-stu-id="068c3-138">submissionId</span></span> | <span data-ttu-id="068c3-139">String</span><span class="sxs-lookup"><span data-stu-id="068c3-139">string</span></span> | <span data-ttu-id="068c3-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="068c3-140">Required.</span></span> <span data-ttu-id="068c3-141">Die ID der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="068c3-141">The ID of the submission to get.</span></span> <span data-ttu-id="068c3-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="068c3-142">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="068c3-143">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="068c3-143">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="068c3-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="068c3-144">Request body</span></span>

<span data-ttu-id="068c3-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="068c3-145">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="068c3-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="068c3-146">Request example</span></span>

<span data-ttu-id="068c3-147">Im folgenden Beispiel wird das Abrufen einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="068c3-147">The following example demonstrates how to get an app submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="068c3-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="068c3-148">Response</span></span>

<span data-ttu-id="068c3-149">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="068c3-149">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="068c3-150">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="068c3-150">The response body contains information about the specified submission.</span></span> <span data-ttu-id="068c3-151">Weitere Informationen zu den Werten im Antworttext finden Sie unter [App-Übermittlungsressource](manage-app-submissions.md#app-submission-object).</span><span class="sxs-lookup"><span data-stu-id="068c3-151">For more details about the values in the response body, see [App submission resource](manage-app-submissions.md#app-submission-object).</span></span>

```json
{
  "id": "1152921504621243540",
  "applicationCategory": "BooksAndReference_EReader",
  "pricing": {
    "trialPeriod": "FifteenDays",
    "marketSpecificPricings": {},
    "sales": [],
    "priceId": "Tier2",
    "isAdvancedPricingModel": true
  },
  "visibility": "Public",
  "targetPublishMode": "Manual",
  "targetPublishDate": "1601-01-01T00:00:00Z",
  "listings": {
    "en-us": {
      "baseListing": {
        "copyrightAndTrademarkInfo": "",
        "keywords": [
           "epub"
        ],
        "licenseTerms": "",
        "privacyPolicy": "",
        "supportContact": "",
        "websiteUrl": "",
        "description": "Description",
        "features": [
          "Free ebook reader"
        ],
        "releaseNotes": "",
        "images": [
          {
            "fileName": "contoso.png",
            "fileStatus": "Uploaded",
            "id": "1152921504672272757",
            "imageType": "Screenshot"
          }
        ],
        "recommendedHardware": [],
        "title": "Contoso ebook reader"
      },
      "platformOverrides": {
        "Windows81": {
          "description": "Ebook reader for Windows 8.1"
        }
      }
    }
  },
  "hardwarePreferences": [
    "Touch"
  ],
  "automaticBackupEnabled": false,
  "canInstallOnRemovableMedia": true,
  "isGameDvrEnabled": false,
  "gamingOptions": [],
  "hasExternalInAppProducts": false,
  "meetAccessibilityGuidelines": true,
  "notesForCertification": "",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [],
    "warnings": [],
    "certificationReports": []
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/387a9ea8-a412-43a9-8fb3-a38d03eb483d?sv=2014-02-14&sr=b&sig=sdd12JmoaT6BhvC%2BZUrwRweA%2Fkvj%2BEBCY09C2SZZowg%3D&se=2016-06-17T18:32:26Z&sp=rwl",
  "applicationPackages": [
    {
      "fileName": "contoso_app.appx",
      "fileStatus": "Uploaded",
      "id": "1152921504620138797",
      "version": "1.0.0.0",
      "architecture": "ARM",
      "languages": [
        "en-US"
      ],
      "capabilities": [
        "ID_RESOLUTION_HD720P",
        "ID_RESOLUTION_WVGA",
        "ID_RESOLUTION_WXGA"
      ],
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None",
      "targetDeviceFamilies": [
        "Windows.Mobile min version 10.0.10240.0"
      ]
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
  "enterpriseLicensing": "Online",
  "allowMicrosoftDecideAppAvailabilityToFutureDeviceFamilies": true,
  "allowTargetFutureDeviceFamilies": {
    "Desktop": false,
    "Mobile": true,
    "Holographic": true,
    "Xbox": false,
    "Team": true
  },
  "friendlyName": "Submission 2",
  "trailers": []
}
```

## <a name="error-codes"></a><span data-ttu-id="068c3-152">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="068c3-152">Error codes</span></span>

<span data-ttu-id="068c3-153">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="068c3-153">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="068c3-154">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="068c3-154">Error code</span></span> |  <span data-ttu-id="068c3-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="068c3-155">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="068c3-156">404</span><span class="sxs-lookup"><span data-stu-id="068c3-156">404</span></span>  | <span data-ttu-id="068c3-157">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="068c3-157">The submission could not be found.</span></span> |
| <span data-ttu-id="068c3-158">409</span><span class="sxs-lookup"><span data-stu-id="068c3-158">409</span></span>  | <span data-ttu-id="068c3-159">Die Übermittlung gehört nicht zur angegebenen app, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="068c3-159">The submission does not belong to the specified app, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="068c3-160">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="068c3-160">Related topics</span></span>

* [<span data-ttu-id="068c3-161">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="068c3-161">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="068c3-162">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-162">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="068c3-163">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-163">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="068c3-164">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-164">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="068c3-165">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-165">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="068c3-166">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="068c3-166">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
