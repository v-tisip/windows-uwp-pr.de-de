---
author: Xansky
ms.assetid: 78278741-09A4-4406-A112-9AF3C73F5C16
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über ein Add-On für eine App abzurufen, die für Ihr Windows Dev Center-Konto registriert wurde.
title: Abrufen eines Add-Ons
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 36638c3e3890d5e2bca149d1006469bb97057f05
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5924966"
---
# <a name="get-an-add-on"></a><span data-ttu-id="627ba-104">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="627ba-104">Get an add-on</span></span>

<span data-ttu-id="627ba-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Informationen über ein Add-On (auch als In-App-Produkt oder IAP bezeichnet) für eine App abzurufen, die für Ihr Windows Dev Center-Konto registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="627ba-105">Use this method in the Microsoft Store submission API to retrieve information about an add-on (also known as in-app product or IAP) for an app that is registered to your Windows Dev Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="627ba-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="627ba-106">Prerequisites</span></span>

<span data-ttu-id="627ba-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="627ba-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="627ba-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="627ba-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="627ba-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="627ba-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="627ba-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="627ba-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="627ba-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="627ba-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="627ba-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="627ba-112">Request</span></span>

<span data-ttu-id="627ba-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="627ba-113">This method has the following syntax.</span></span> <span data-ttu-id="627ba-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="627ba-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="627ba-115">Methode</span><span class="sxs-lookup"><span data-stu-id="627ba-115">Method</span></span> | <span data-ttu-id="627ba-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="627ba-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="627ba-117">GET</span><span class="sxs-lookup"><span data-stu-id="627ba-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}``` |


### <a name="request-header"></a><span data-ttu-id="627ba-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="627ba-118">Request header</span></span>

| <span data-ttu-id="627ba-119">Header</span><span class="sxs-lookup"><span data-stu-id="627ba-119">Header</span></span>        | <span data-ttu-id="627ba-120">Typ</span><span class="sxs-lookup"><span data-stu-id="627ba-120">Type</span></span>   | <span data-ttu-id="627ba-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="627ba-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="627ba-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="627ba-122">Authorization</span></span> | <span data-ttu-id="627ba-123">String</span><span class="sxs-lookup"><span data-stu-id="627ba-123">string</span></span> | <span data-ttu-id="627ba-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="627ba-124">Required.</span></span> <span data-ttu-id="627ba-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="627ba-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="627ba-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="627ba-126">Request parameters</span></span>

| <span data-ttu-id="627ba-127">Name</span><span class="sxs-lookup"><span data-stu-id="627ba-127">Name</span></span>        | <span data-ttu-id="627ba-128">Typ</span><span class="sxs-lookup"><span data-stu-id="627ba-128">Type</span></span>   | <span data-ttu-id="627ba-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="627ba-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="627ba-130">id</span><span class="sxs-lookup"><span data-stu-id="627ba-130">id</span></span> | <span data-ttu-id="627ba-131">String</span><span class="sxs-lookup"><span data-stu-id="627ba-131">string</span></span> | <span data-ttu-id="627ba-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="627ba-132">Required.</span></span> <span data-ttu-id="627ba-133">Die Store-ID des abzurufenden Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="627ba-133">The Store ID of the add-on to retrieve.</span></span> <span data-ttu-id="627ba-134">Die Store-ID ist im Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="627ba-134">The Store ID is available on the Dev Center dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="627ba-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="627ba-135">Request body</span></span>

<span data-ttu-id="627ba-136">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="627ba-136">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="627ba-137">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="627ba-137">Request example</span></span>

<span data-ttu-id="627ba-138">Im folgenden Beispiel wird veranschaulicht, wie Informationen über ein Add-On abgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="627ba-138">The following example demonstrates how to retrieve information about an add-on.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="627ba-139">Antwort</span><span class="sxs-lookup"><span data-stu-id="627ba-139">Response</span></span>

<span data-ttu-id="627ba-140">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="627ba-140">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="627ba-141">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-ons.md#add-on-object).</span><span class="sxs-lookup"><span data-stu-id="627ba-141">For more details about the values in the response body, see [add-on resource](manage-add-ons.md#add-on-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="627ba-142">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="627ba-142">Error codes</span></span>

<span data-ttu-id="627ba-143">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="627ba-143">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="627ba-144">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="627ba-144">Error code</span></span> |  <span data-ttu-id="627ba-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="627ba-145">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="627ba-146">404</span><span class="sxs-lookup"><span data-stu-id="627ba-146">404</span></span>  | <span data-ttu-id="627ba-147">Das angegebene Add-On konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="627ba-147">The specified add-on could not be found.</span></span> |
| <span data-ttu-id="627ba-148">409</span><span class="sxs-lookup"><span data-stu-id="627ba-148">409</span></span>  | <span data-ttu-id="627ba-149">Das Add-On verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="627ba-149">The add-on uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="627ba-150">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="627ba-150">Related topics</span></span>

* [<span data-ttu-id="627ba-151">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="627ba-151">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="627ba-152">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="627ba-152">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="627ba-153">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="627ba-153">Get all add-ons</span></span>](get-all-add-ons.md)
* [<span data-ttu-id="627ba-154">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="627ba-154">Create an add-on</span></span>](create-an-add-on.md)
* [<span data-ttu-id="627ba-155">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="627ba-155">Delete an add-on</span></span>](delete-an-add-on.md)
