---
ms.assetid: D34447FF-21D2-44D0-92B0-B3FF9B32D6F7
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue Übermittlung für eine app erstellen, die für Ihr Partner Center-Konto registriert ist.
title: Erstellen einer App-Übermittlung
ms.date: 07/10/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Erstellen einer App-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: a90be116a9d85eeae7cb7c44c2bbfe96da472f65
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8887503"
---
# <a name="create-an-app-submission"></a><span data-ttu-id="c24bc-104">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-104">Create an app submission</span></span>

<span data-ttu-id="c24bc-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue Übermittlung für eine app erstellen, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="c24bc-105">Use this method in the Microsoft Store submission API to create a new submission for an app that is registered to your Partner Center account.</span></span> <span data-ttu-id="c24bc-106">Nachdem Sie erfolgreich eine neue Übermittlung mit dieser Methode erstellt haben, [aktualisieren Sie die Übermittlung](update-an-app-submission.md), um erforderliche Änderungen an den Übermittlungsdaten vorzunehmen, und führen Sie ein [Commit für die Übermittlung](commit-an-app-submission.md) zur Aufnahme und Veröffentlichung durch.</span><span class="sxs-lookup"><span data-stu-id="c24bc-106">After you successfully create a new submission by using this method, [update the submission](update-an-app-submission.md) to make any necessary changes to the submission data, and then [commit the submission](commit-an-app-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="c24bc-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="c24bc-107">For more information about how this method fits into the process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>


## <a name="prerequisites"></a><span data-ttu-id="c24bc-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c24bc-108">Prerequisites</span></span>

<span data-ttu-id="c24bc-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="c24bc-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="c24bc-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="c24bc-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="c24bc-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c24bc-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="c24bc-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="c24bc-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="c24bc-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="c24bc-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="c24bc-114">Stellen Sie sicher, dass für die App bereits mindestens eine Übermittlung mit abgeschlossenen Informationen zu den [Altersfreigaben](https://msdn.microsoft.com/windows/uwp/publish/age-ratings) vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c24bc-114">Make sure the app already has at least one submission with the [age ratings](https://msdn.microsoft.com/windows/uwp/publish/age-ratings) information completed.</span></span>

## <a name="request"></a><span data-ttu-id="c24bc-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c24bc-115">Request</span></span>

<span data-ttu-id="c24bc-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="c24bc-116">This method has the following syntax.</span></span> <span data-ttu-id="c24bc-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="c24bc-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="c24bc-118">Methode</span><span class="sxs-lookup"><span data-stu-id="c24bc-118">Method</span></span> | <span data-ttu-id="c24bc-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c24bc-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="c24bc-120">POST</span><span class="sxs-lookup"><span data-stu-id="c24bc-120">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions``` |


### <a name="request-header"></a><span data-ttu-id="c24bc-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c24bc-121">Request header</span></span>

| <span data-ttu-id="c24bc-122">Header</span><span class="sxs-lookup"><span data-stu-id="c24bc-122">Header</span></span>        | <span data-ttu-id="c24bc-123">Typ</span><span class="sxs-lookup"><span data-stu-id="c24bc-123">Type</span></span>   | <span data-ttu-id="c24bc-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c24bc-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c24bc-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="c24bc-125">Authorization</span></span> | <span data-ttu-id="c24bc-126">String</span><span class="sxs-lookup"><span data-stu-id="c24bc-126">string</span></span> | <span data-ttu-id="c24bc-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c24bc-127">Required.</span></span> <span data-ttu-id="c24bc-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="c24bc-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="c24bc-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="c24bc-129">Request parameters</span></span>

| <span data-ttu-id="c24bc-130">Name</span><span class="sxs-lookup"><span data-stu-id="c24bc-130">Name</span></span>        | <span data-ttu-id="c24bc-131">Typ</span><span class="sxs-lookup"><span data-stu-id="c24bc-131">Type</span></span>   | <span data-ttu-id="c24bc-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c24bc-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c24bc-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="c24bc-133">applicationId</span></span> | <span data-ttu-id="c24bc-134">String</span><span class="sxs-lookup"><span data-stu-id="c24bc-134">string</span></span> | <span data-ttu-id="c24bc-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c24bc-135">Required.</span></span> <span data-ttu-id="c24bc-136">Die Store-ID der App, für die Sie eine Übermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="c24bc-136">The Store ID of the app for which you want to create a submission.</span></span> <span data-ttu-id="c24bc-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="c24bc-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="c24bc-138">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c24bc-138">Request body</span></span>

<span data-ttu-id="c24bc-139">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="c24bc-139">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="c24bc-140">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="c24bc-140">Request example</span></span>

<span data-ttu-id="c24bc-141">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Übermittlung für eine App erstellen.</span><span class="sxs-lookup"><span data-stu-id="c24bc-141">The following example demonstrates how to create a new submission for an app.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="c24bc-142">Antwort</span><span class="sxs-lookup"><span data-stu-id="c24bc-142">Response</span></span>

<span data-ttu-id="c24bc-143">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="c24bc-143">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="c24bc-144">Der Antworttext enthält Informationen zur neuen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="c24bc-144">The response body contains information about the new submission.</span></span> <span data-ttu-id="c24bc-145">Weitere Informationen zu den Werten im Antworttext finden Sie unter [App-Übermittlungsressource](manage-app-submissions.md#app-submission-object).</span><span class="sxs-lookup"><span data-stu-id="c24bc-145">For more details about the values in the response body, see [App submission resource](manage-app-submissions.md#app-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="c24bc-146">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c24bc-146">Error codes</span></span>

<span data-ttu-id="c24bc-147">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="c24bc-147">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="c24bc-148">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="c24bc-148">Error code</span></span> |  <span data-ttu-id="c24bc-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c24bc-149">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="c24bc-150">400</span><span class="sxs-lookup"><span data-stu-id="c24bc-150">400</span></span>  | <span data-ttu-id="c24bc-151">Die Übermittlung konnte nicht erstellt werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="c24bc-151">The submission could not be created because the request is invalid.</span></span> |
| <span data-ttu-id="c24bc-152">409</span><span class="sxs-lookup"><span data-stu-id="c24bc-152">409</span></span>  | <span data-ttu-id="c24bc-153">Die Übermittlung konnte im aktuellen Zustand der app nicht erstellt werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="c24bc-153">The submission could not be created because of the current state of the app, or the app uses a Partner Center  feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="c24bc-154">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c24bc-154">Related topics</span></span>

* [<span data-ttu-id="c24bc-155">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="c24bc-155">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="c24bc-156">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-156">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="c24bc-157">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-157">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="c24bc-158">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-158">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="c24bc-159">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-159">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="c24bc-160">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c24bc-160">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
