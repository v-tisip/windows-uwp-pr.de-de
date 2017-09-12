---
author: mcleanbyron
ms.assetid: BF296C25-A2E6-48E4-9D08-0CCDB5FAE0C8
description: "Verwenden Sie diese Methode aus der Windows Store-Übermittlungs-API zum Abrufen von Daten für eine vorhandene App-Übermittlung."
title: "Abrufen einer App-Übermittlung"
ms.author: mcleans
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, App-Übermittlung"
ms.openlocfilehash: 809f96d1610db701baadff74b5a30e523fd44e05
ms.sourcegitcommit: a7a1b41c7dce6d56250ce3113137391d65d9e401
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2017
---
# <a name="get-an-app-submission"></a><span data-ttu-id="78ceb-104">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-104">Get an app submission</span></span>


<span data-ttu-id="78ceb-105">Verwenden Sie diese Methode aus der Windows Store-Übermittlungs-API zum Abrufen von Daten für eine vorhandene App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="78ceb-105">Use this method in the Windows Store submission API to get data for an existing app submission.</span></span> <span data-ttu-id="78ceb-106">Weitere Informationen über den Erstellungsprozess einer App-Übermittlung mithilfe der Windows Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="78ceb-106">For more information about the process of process of creating an app submission by using the Windows Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78ceb-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="78ceb-107">Prerequisites</span></span>

<span data-ttu-id="78ceb-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="78ceb-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="78ceb-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="78ceb-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="78ceb-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="78ceb-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="78ceb-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="78ceb-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="78ceb-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="78ceb-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="78ceb-113">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="78ceb-113">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="78ceb-114">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="78ceb-114">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="78ceb-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="78ceb-115">Request</span></span>

<span data-ttu-id="78ceb-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="78ceb-116">This method has the following syntax.</span></span> <span data-ttu-id="78ceb-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="78ceb-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="78ceb-118">Methode</span><span class="sxs-lookup"><span data-stu-id="78ceb-118">Method</span></span> | <span data-ttu-id="78ceb-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="78ceb-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="78ceb-120">GET</span><span class="sxs-lookup"><span data-stu-id="78ceb-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId} ``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="78ceb-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="78ceb-121">Request header</span></span>

| <span data-ttu-id="78ceb-122">Header</span><span class="sxs-lookup"><span data-stu-id="78ceb-122">Header</span></span>        | <span data-ttu-id="78ceb-123">Typ</span><span class="sxs-lookup"><span data-stu-id="78ceb-123">Type</span></span>   | <span data-ttu-id="78ceb-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78ceb-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="78ceb-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="78ceb-125">Authorization</span></span> | <span data-ttu-id="78ceb-126">String</span><span class="sxs-lookup"><span data-stu-id="78ceb-126">string</span></span> | <span data-ttu-id="78ceb-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="78ceb-127">Required.</span></span> <span data-ttu-id="78ceb-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="78ceb-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="78ceb-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="78ceb-129">Request parameters</span></span>

| <span data-ttu-id="78ceb-130">Name</span><span class="sxs-lookup"><span data-stu-id="78ceb-130">Name</span></span>        | <span data-ttu-id="78ceb-131">Typ</span><span class="sxs-lookup"><span data-stu-id="78ceb-131">Type</span></span>   | <span data-ttu-id="78ceb-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78ceb-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="78ceb-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="78ceb-133">applicationId</span></span> | <span data-ttu-id="78ceb-134">String</span><span class="sxs-lookup"><span data-stu-id="78ceb-134">string</span></span> | <span data-ttu-id="78ceb-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="78ceb-135">Required.</span></span> <span data-ttu-id="78ceb-136">Die Store-ID der App, deren Übermittlung Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="78ceb-136">The Store ID of the app with the submission you want to get.</span></span> <span data-ttu-id="78ceb-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="78ceb-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="78ceb-138">submissionId</span><span class="sxs-lookup"><span data-stu-id="78ceb-138">submissionId</span></span> | <span data-ttu-id="78ceb-139">String</span><span class="sxs-lookup"><span data-stu-id="78ceb-139">string</span></span> | <span data-ttu-id="78ceb-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="78ceb-140">Required.</span></span> <span data-ttu-id="78ceb-141">Die ID der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="78ceb-141">The ID of the submission to get.</span></span> <span data-ttu-id="78ceb-142">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="78ceb-142">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="78ceb-143">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="78ceb-143">Request body</span></span>

<span data-ttu-id="78ceb-144">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="78ceb-144">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="78ceb-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="78ceb-145">Request example</span></span>

<span data-ttu-id="78ceb-146">Im folgenden Beispiel wird das Abrufen einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="78ceb-146">The following example demonstrates how to get an app submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="78ceb-147">Antwort</span><span class="sxs-lookup"><span data-stu-id="78ceb-147">Response</span></span>

<span data-ttu-id="78ceb-148">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="78ceb-148">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="78ceb-149">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="78ceb-149">The response body contains information about the specified submission.</span></span> <span data-ttu-id="78ceb-150">Weitere Informationen zu den Werten im Antworttext finden Sie unter [App-Übermittlungsressource](manage-app-submissions.md#app-submission-object).</span><span class="sxs-lookup"><span data-stu-id="78ceb-150">For more details about the values in the response body, see [App submission resource](manage-app-submissions.md#app-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="78ceb-151">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="78ceb-151">Error codes</span></span>

<span data-ttu-id="78ceb-152">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="78ceb-152">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="78ceb-153">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="78ceb-153">Error code</span></span> |  <span data-ttu-id="78ceb-154">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78ceb-154">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="78ceb-155">404</span><span class="sxs-lookup"><span data-stu-id="78ceb-155">404</span></span>  | <span data-ttu-id="78ceb-156">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="78ceb-156">The submission could not be found.</span></span> |
| <span data-ttu-id="78ceb-157">409</span><span class="sxs-lookup"><span data-stu-id="78ceb-157">409</span></span>  | <span data-ttu-id="78ceb-158">Die Übermittlung gehört nicht zur angegebenen App, oder die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="78ceb-158">The submission does not belong to the specified app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   

<span/>


## <a name="related-topics"></a><span data-ttu-id="78ceb-159">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="78ceb-159">Related topics</span></span>

* [<span data-ttu-id="78ceb-160">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="78ceb-160">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="78ceb-161">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-161">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="78ceb-162">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-162">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="78ceb-163">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-163">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="78ceb-164">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-164">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="78ceb-165">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="78ceb-165">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
