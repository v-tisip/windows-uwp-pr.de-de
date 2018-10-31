---
author: Xansky
ms.assetid: C09F4B7C-6324-4973-980A-A60035792EFC
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen einer neuen Add-On-Übermittlung für eine App, die für Ihr Windows Dev Center-Konto registriert ist.
title: Erstellen einer Add-On-Übermittlung
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Erstellen einer Add-On-Übermittlung, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 32e5c803600d0b56e421ae87a5514f6c70cc8d11
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5868440"
---
# <a name="create-an-add-on-submission"></a><span data-ttu-id="76c0d-104">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-104">Create an add-on submission</span></span>


<span data-ttu-id="76c0d-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um eine neue Übermittlung für ein Add-On (auch als In-App-Produkt oder IAP bezeichnet) für eine App zu erstellen, die für Ihr Windows Dev Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="76c0d-105">Use this method in the Microsoft Store submission API to create a new add-on (also known as in-app product or IAP) submission for an app that is registered to your Windows Dev Center account.</span></span> <span data-ttu-id="76c0d-106">Nachdem Sie erfolgreich eine neue Übermittlung mit dieser Methode erstellt haben, [aktualisieren Sie die Übermittlung](update-an-add-on-submission.md), um erforderliche Änderungen an den Übermittlungsdaten vorzunehmen, und führen Sie ein [Commit für die Übermittlung](commit-an-add-on-submission.md) zur Aufnahme und Veröffentlichung durch.</span><span class="sxs-lookup"><span data-stu-id="76c0d-106">After you successfully create a new submission by using this method, [update the submission](update-an-add-on-submission.md) to make any necessary changes to the submission data, and then [commit the submission](commit-an-add-on-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="76c0d-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer Add-On-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="76c0d-107">For more information about how this method fits into the process of creating an add-on submission by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="76c0d-108">Durch diese Methode wird eine Übermittlung für ein vorhandenes Add-On erstellt.</span><span class="sxs-lookup"><span data-stu-id="76c0d-108">This method creates a submission for an existing add-on.</span></span> <span data-ttu-id="76c0d-109">Um ein Add-On zu erstellen, verwenden Sie die Methode zum [Erstellen eines Add-Ons](create-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="76c0d-109">To create an add-on, use the [Create an add-on](create-an-add-on.md) method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76c0d-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="76c0d-110">Prerequisites</span></span>

<span data-ttu-id="76c0d-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="76c0d-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="76c0d-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="76c0d-112">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="76c0d-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="76c0d-113">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="76c0d-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="76c0d-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="76c0d-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="76c0d-115">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="76c0d-116">Erstellen Sie ein Add-On für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="76c0d-116">Create an add-on for an app in your Dev Center account.</span></span> <span data-ttu-id="76c0d-117">Verwenden Sie hierzu das Dev Center-Dashboard oder die Methode zum [Erstellen eines Add-Ons](create-an-add-on.md).</span><span class="sxs-lookup"><span data-stu-id="76c0d-117">You can do this in the Dev Center dashboard, or you can do this by using the [Create an add-on](create-an-add-on.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="76c0d-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="76c0d-118">Request</span></span>

<span data-ttu-id="76c0d-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="76c0d-119">This method has the following syntax.</span></span> <span data-ttu-id="76c0d-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="76c0d-120">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="76c0d-121">Methode</span><span class="sxs-lookup"><span data-stu-id="76c0d-121">Method</span></span> | <span data-ttu-id="76c0d-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="76c0d-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="76c0d-123">POST</span><span class="sxs-lookup"><span data-stu-id="76c0d-123">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions``` |


### <a name="request-header"></a><span data-ttu-id="76c0d-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="76c0d-124">Request header</span></span>

| <span data-ttu-id="76c0d-125">Header</span><span class="sxs-lookup"><span data-stu-id="76c0d-125">Header</span></span>        | <span data-ttu-id="76c0d-126">Typ</span><span class="sxs-lookup"><span data-stu-id="76c0d-126">Type</span></span>   | <span data-ttu-id="76c0d-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76c0d-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="76c0d-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="76c0d-128">Authorization</span></span> | <span data-ttu-id="76c0d-129">String</span><span class="sxs-lookup"><span data-stu-id="76c0d-129">string</span></span> | <span data-ttu-id="76c0d-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="76c0d-130">Required.</span></span> <span data-ttu-id="76c0d-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="76c0d-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="76c0d-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="76c0d-132">Request parameters</span></span>

| <span data-ttu-id="76c0d-133">Name</span><span class="sxs-lookup"><span data-stu-id="76c0d-133">Name</span></span>        | <span data-ttu-id="76c0d-134">Typ</span><span class="sxs-lookup"><span data-stu-id="76c0d-134">Type</span></span>   | <span data-ttu-id="76c0d-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76c0d-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="76c0d-136">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="76c0d-136">inAppProductId</span></span> | <span data-ttu-id="76c0d-137">String</span><span class="sxs-lookup"><span data-stu-id="76c0d-137">string</span></span> | <span data-ttu-id="76c0d-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="76c0d-138">Required.</span></span> <span data-ttu-id="76c0d-139">Die Store-ID des Add-Ons, für das Sie eine Übermittlung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="76c0d-139">The Store ID of the add-on for which you want to create a submission.</span></span> <span data-ttu-id="76c0d-140">Die Store-ID ist im Windows Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen eines Add-Ons](create-an-add-on.md) und zum [Abrufen von Add-On-Details](get-all-add-ons.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="76c0d-140">The Store ID is available on the Dev Center dashboard, and it is included in the response data for requests to [Create an add-on](create-an-add-on.md) or [get add-on details](get-all-add-ons.md).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="76c0d-141">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="76c0d-141">Request body</span></span>

<span data-ttu-id="76c0d-142">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="76c0d-142">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="76c0d-143">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="76c0d-143">Request example</span></span>

<span data-ttu-id="76c0d-144">Im folgenden Beispiel wird gezeigt, wie Sie eine neue Übermittlung für ein Add-On erstellen.</span><span class="sxs-lookup"><span data-stu-id="76c0d-144">The following example demonstrates how to create a new submission for an add-on.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="76c0d-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="76c0d-145">Response</span></span>

<span data-ttu-id="76c0d-146">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="76c0d-146">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="76c0d-147">Der Antworttext enthält Informationen zur neuen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="76c0d-147">The response body contains information about the new submission.</span></span> <span data-ttu-id="76c0d-148">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-on-submissions.md#add-on-submission-object).</span><span class="sxs-lookup"><span data-stu-id="76c0d-148">For more details about the values in the response body, see [add-on submission resource](manage-add-on-submissions.md#add-on-submission-object).</span></span>

```json
{
  "id": "1152921504621243680",
  "contentType": "EMagazine",
  "keywords": [
    "books"
  ],
  "lifetime": "FiveDays",
  "listings": {
    "en": {
      "description": "English add-on description",
      "icon": {
        "fileName": "add-on-en-us-listing2.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (English)"
    },
    "ru": {
      "description": "Russian add-on description",
      "icon": {
        "fileName": "add-on-ru-listing.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (Russian)"
    }
  },
  "pricing": {
    "marketSpecificPricings": {
      "RU": "Tier3",
      "US": "Tier4",
    },
    "sales": [
      {
         "name": "Sale1",
         "basePriceId": "Free",
         "startDate": "2016-05-21T18:40:11.7369008Z",
         "endDate": "2016-05-22T18:40:11.7369008Z",
         "marketSpecificPricings": {
            "RU": "NotAvailable"
         }
      }
    ],
    "priceId": "Free",
    "isAdvancedPricingModel": true
  },
  "targetPublishDate": "2016-03-15T05:10:58.047Z",
  "targetPublishMode": "Immediate",
  "tag": "SampleTag",
  "visibility": "Public",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [
      {
        "code": "None",
        "details": "string"
      }
    ],
    "warnings": [
      {
        "code": "ListingOptOutWarning",
        "details": "You have removed listing language(s): []"
      }
    ],
    "certificationReports": [
      {
      }
    ]
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/26920f66-b592-4439-9a9d-fb0f014902ec?sv=2014-02-14&sr=b&sig=usAN0kNFNnYE2tGQBI%2BARQWejX1Guiz7hdFtRhyK%2Bog%3D&se=2016-06-17T20:45:51Z&sp=rwl",
  "friendlyName": "Submission 2"
}
```

## <a name="error-codes"></a><span data-ttu-id="76c0d-149">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="76c0d-149">Error codes</span></span>

<span data-ttu-id="76c0d-150">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="76c0d-150">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="76c0d-151">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="76c0d-151">Error code</span></span> |  <span data-ttu-id="76c0d-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="76c0d-152">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="76c0d-153">400</span><span class="sxs-lookup"><span data-stu-id="76c0d-153">400</span></span>  | <span data-ttu-id="76c0d-154">Die Übermittlung konnte nicht erstellt werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="76c0d-154">The submission could not be created because the request is invalid.</span></span> |
| <span data-ttu-id="76c0d-155">409</span><span class="sxs-lookup"><span data-stu-id="76c0d-155">409</span></span>  | <span data-ttu-id="76c0d-156">Die Übermittlung konnte im aktuellen Zustand der App nicht erstellt werden, oder in der App wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="76c0d-156">The submission could not be created because of the current state of the app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="76c0d-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="76c0d-157">Related topics</span></span>

* [<span data-ttu-id="76c0d-158">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="76c0d-158">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="76c0d-159">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="76c0d-159">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="76c0d-160">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-160">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="76c0d-161">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-161">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="76c0d-162">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-162">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="76c0d-163">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-163">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="76c0d-164">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="76c0d-164">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
