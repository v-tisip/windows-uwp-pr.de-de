---
author: Xansky
ms.assetid: 78278741-09A4-4406-A112-9AF3C73F5C16
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Abrufen von Informationen über ein Add-on für eine app, die für Ihr Partner Center-Konto registriert ist.
title: Abrufen eines Add-Ons
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 9620b0b7cf4d1ecb583215b2ab0fafe0e82712bf
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7101649"
---
# <a name="get-an-add-on"></a><span data-ttu-id="ec9f0-104">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="ec9f0-104">Get an add-on</span></span>

<span data-ttu-id="ec9f0-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Abrufen von Informationen über ein Add-on (auch bekannt als in-app-Produkt oder IAP) für eine app, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-105">Use this method in the Microsoft Store submission API to retrieve information about an add-on (also known as in-app product or IAP) for an app that is registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec9f0-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ec9f0-106">Prerequisites</span></span>

<span data-ttu-id="ec9f0-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ec9f0-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ec9f0-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="ec9f0-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ec9f0-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ec9f0-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="ec9f0-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ec9f0-112">Request</span></span>

<span data-ttu-id="ec9f0-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-113">This method has the following syntax.</span></span> <span data-ttu-id="ec9f0-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="ec9f0-115">Methode</span><span class="sxs-lookup"><span data-stu-id="ec9f0-115">Method</span></span> | <span data-ttu-id="ec9f0-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ec9f0-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="ec9f0-117">GET</span><span class="sxs-lookup"><span data-stu-id="ec9f0-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}``` |


### <a name="request-header"></a><span data-ttu-id="ec9f0-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ec9f0-118">Request header</span></span>

| <span data-ttu-id="ec9f0-119">Header</span><span class="sxs-lookup"><span data-stu-id="ec9f0-119">Header</span></span>        | <span data-ttu-id="ec9f0-120">Typ</span><span class="sxs-lookup"><span data-stu-id="ec9f0-120">Type</span></span>   | <span data-ttu-id="ec9f0-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ec9f0-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ec9f0-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ec9f0-122">Authorization</span></span> | <span data-ttu-id="ec9f0-123">String</span><span class="sxs-lookup"><span data-stu-id="ec9f0-123">string</span></span> | <span data-ttu-id="ec9f0-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-124">Required.</span></span> <span data-ttu-id="ec9f0-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="ec9f0-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ec9f0-126">Request parameters</span></span>

| <span data-ttu-id="ec9f0-127">Name</span><span class="sxs-lookup"><span data-stu-id="ec9f0-127">Name</span></span>        | <span data-ttu-id="ec9f0-128">Typ</span><span class="sxs-lookup"><span data-stu-id="ec9f0-128">Type</span></span>   | <span data-ttu-id="ec9f0-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ec9f0-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ec9f0-130">id</span><span class="sxs-lookup"><span data-stu-id="ec9f0-130">id</span></span> | <span data-ttu-id="ec9f0-131">String</span><span class="sxs-lookup"><span data-stu-id="ec9f0-131">string</span></span> | <span data-ttu-id="ec9f0-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-132">Required.</span></span> <span data-ttu-id="ec9f0-133">Die Store-ID des abzurufenden Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-133">The Store ID of the add-on to retrieve.</span></span> <span data-ttu-id="ec9f0-134">Die Store-ID ist im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-134">The Store ID is available in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="ec9f0-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="ec9f0-135">Request body</span></span>

<span data-ttu-id="ec9f0-136">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-136">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="ec9f0-137">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ec9f0-137">Request example</span></span>

<span data-ttu-id="ec9f0-138">Im folgenden Beispiel wird veranschaulicht, wie Informationen über ein Add-On abgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-138">The following example demonstrates how to retrieve information about an add-on.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ec9f0-139">Antwort</span><span class="sxs-lookup"><span data-stu-id="ec9f0-139">Response</span></span>

<span data-ttu-id="ec9f0-140">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-140">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="ec9f0-141">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-ons.md#add-on-object).</span><span class="sxs-lookup"><span data-stu-id="ec9f0-141">For more details about the values in the response body, see [add-on resource](manage-add-ons.md#add-on-object).</span></span>

```json
{
  "applications": {
    "value": [
      {
        "id": "9NBLGGH4R315",
        "resourceLocation": "applications/9NBLGGH4R315"
      }
    ],
    "totalCount": 1
  },
  "id": "9NBLGGH4TNMP",
  "productId": "Test-add-on",
  "productType": "Durable",
  "pendingInAppProductSubmission": {
    "id": "1152921504621243619",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
  },
  "lastPublishedInAppProductSubmission": {
    "id": "1152921504621243705",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243705"
  }
}
```

## <a name="error-codes"></a><span data-ttu-id="ec9f0-142">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="ec9f0-142">Error codes</span></span>

<span data-ttu-id="ec9f0-143">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-143">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="ec9f0-144">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="ec9f0-144">Error code</span></span> |  <span data-ttu-id="ec9f0-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ec9f0-145">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="ec9f0-146">404</span><span class="sxs-lookup"><span data-stu-id="ec9f0-146">404</span></span>  | <span data-ttu-id="ec9f0-147">Das angegebene Add-On konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-147">The specified add-on could not be found.</span></span> |
| <span data-ttu-id="ec9f0-148">409</span><span class="sxs-lookup"><span data-stu-id="ec9f0-148">409</span></span>  | <span data-ttu-id="ec9f0-149">Das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="ec9f0-149">The add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="ec9f0-150">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ec9f0-150">Related topics</span></span>

* [<span data-ttu-id="ec9f0-151">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="ec9f0-151">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="ec9f0-152">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="ec9f0-152">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="ec9f0-153">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="ec9f0-153">Get all add-ons</span></span>](get-all-add-ons.md)
* [<span data-ttu-id="ec9f0-154">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="ec9f0-154">Create an add-on</span></span>](create-an-add-on.md)
* [<span data-ttu-id="ec9f0-155">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="ec9f0-155">Delete an add-on</span></span>](delete-an-add-on.md)
