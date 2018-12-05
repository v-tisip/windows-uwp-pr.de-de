---
ms.assetid: E3DF5D11-8791-4CFC-8131-4F59B928A228
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für eine vorhandene Add-On-Übermittlung.
title: Abrufen einer Add-On-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: a87f0e694434774db215f3f5323588f94ec0465b
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8685156"
---
# <a name="get-an-add-on-submission"></a><span data-ttu-id="99488-104">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-104">Get an add-on submission</span></span>

<span data-ttu-id="99488-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Abrufen der Daten für eine vorhandene Add-On-Übermittlung (auch als In-App-Produkt oder IAP bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="99488-105">Use this method in the Microsoft Store submission API to get data for an existing add-on (also known as in-app product or IAP) submission.</span></span> <span data-ttu-id="99488-106">Weitere Informationen über den Erstellungsprozess einer Add-On-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="99488-106">For more information about the process of process of creating an add-on submission by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99488-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="99488-107">Prerequisites</span></span>

<span data-ttu-id="99488-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="99488-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="99488-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="99488-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="99488-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="99488-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="99488-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="99488-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="99488-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="99488-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="99488-113">Erstellen einer Add-on-Übermittlungs für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="99488-113">Create an add-on submission for one of your apps.</span></span> <span data-ttu-id="99488-114">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode [Erstellen einer Add-on-Übermittlung](create-an-add-on-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="99488-114">You can do this in Partner Center, or you can do this by using the [Create an add-on submission](create-an-add-on-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="99488-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="99488-115">Request</span></span>

<span data-ttu-id="99488-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="99488-116">This method has the following syntax.</span></span> <span data-ttu-id="99488-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="99488-117">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="99488-118">Methode</span><span class="sxs-lookup"><span data-stu-id="99488-118">Method</span></span> | <span data-ttu-id="99488-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="99488-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="99488-120">GET</span><span class="sxs-lookup"><span data-stu-id="99488-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId} ``` |


### <a name="request-header"></a><span data-ttu-id="99488-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="99488-121">Request header</span></span>

| <span data-ttu-id="99488-122">Header</span><span class="sxs-lookup"><span data-stu-id="99488-122">Header</span></span>        | <span data-ttu-id="99488-123">Typ</span><span class="sxs-lookup"><span data-stu-id="99488-123">Type</span></span>   | <span data-ttu-id="99488-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99488-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="99488-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="99488-125">Authorization</span></span> | <span data-ttu-id="99488-126">String</span><span class="sxs-lookup"><span data-stu-id="99488-126">string</span></span> | <span data-ttu-id="99488-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99488-127">Required.</span></span> <span data-ttu-id="99488-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="99488-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="99488-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="99488-129">Request parameters</span></span>

| <span data-ttu-id="99488-130">Name</span><span class="sxs-lookup"><span data-stu-id="99488-130">Name</span></span>        | <span data-ttu-id="99488-131">Typ</span><span class="sxs-lookup"><span data-stu-id="99488-131">Type</span></span>   | <span data-ttu-id="99488-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99488-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="99488-133">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="99488-133">inAppProductId</span></span> | <span data-ttu-id="99488-134">String</span><span class="sxs-lookup"><span data-stu-id="99488-134">string</span></span> | <span data-ttu-id="99488-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99488-135">Required.</span></span> <span data-ttu-id="99488-136">Die Store-ID des Add-Ons mit der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="99488-136">The Store ID of the add-on that contains the submission you want to get.</span></span> <span data-ttu-id="99488-137">Die Store-ID ist im Partner Center verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen eines Add-Ons](create-an-add-on.md) oder [Abrufen von Add-on-Informationen](get-all-add-ons.md)enthalten.</span><span class="sxs-lookup"><span data-stu-id="99488-137">The Store ID is available in Partner Center, and it is included in the response data for requests to [Create an add-on](create-an-add-on.md) or [get add-on details](get-all-add-ons.md).</span></span>  |
| <span data-ttu-id="99488-138">submissionId</span><span class="sxs-lookup"><span data-stu-id="99488-138">submissionId</span></span> | <span data-ttu-id="99488-139">String</span><span class="sxs-lookup"><span data-stu-id="99488-139">string</span></span> | <span data-ttu-id="99488-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99488-140">Required.</span></span> <span data-ttu-id="99488-141">Die ID der abzurufenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="99488-141">The ID of the submission to get.</span></span> <span data-ttu-id="99488-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99488-142">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="99488-143">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99488-143">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="99488-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="99488-144">Request body</span></span>

<span data-ttu-id="99488-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="99488-145">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="99488-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="99488-146">Request example</span></span>

<span data-ttu-id="99488-147">Im folgenden Beispiel wird veranschaulicht, wie eine Add-On-Übermittlung abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="99488-147">The following example demonstrates how to get an add-on submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621243680 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="99488-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="99488-148">Response</span></span>

<span data-ttu-id="99488-149">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="99488-149">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="99488-150">Der Antworttext enthält Informationen über die angegebene Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="99488-150">The response body contains information about the specified submission.</span></span> <span data-ttu-id="99488-151">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-on-submissions.md#add-on-submission-object).</span><span class="sxs-lookup"><span data-stu-id="99488-151">For more details about the values in the response body, see [add-on submission resource](manage-add-on-submissions.md#add-on-submission-object).</span></span>

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
    "sales": [],
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


## <a name="error-codes"></a><span data-ttu-id="99488-152">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="99488-152">Error codes</span></span>

<span data-ttu-id="99488-153">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="99488-153">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="99488-154">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="99488-154">Error code</span></span> |  <span data-ttu-id="99488-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99488-155">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="99488-156">404</span><span class="sxs-lookup"><span data-stu-id="99488-156">404</span></span>  | <span data-ttu-id="99488-157">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="99488-157">The submission could not be found.</span></span> |
| <span data-ttu-id="99488-158">409</span><span class="sxs-lookup"><span data-stu-id="99488-158">409</span></span>  | <span data-ttu-id="99488-159">Die Übermittlung gehört nicht zum angegebenen Add-on, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="99488-159">The submission does not belong to the specified add-on, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="99488-160">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="99488-160">Related topics</span></span>

* [<span data-ttu-id="99488-161">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="99488-161">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="99488-162">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-162">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="99488-163">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-163">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="99488-164">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-164">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="99488-165">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-165">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="99488-166">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="99488-166">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
