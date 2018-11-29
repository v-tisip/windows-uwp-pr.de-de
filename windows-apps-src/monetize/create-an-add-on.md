---
ms.assetid: 5BD650D2-AA26-4DE9-8243-374FDB7D932B
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen eines Add-Ons für eine app, die für Ihr PartnerCenter-Konto registriert ist.
title: Erstellen eines Add-Ons
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Erstellen eines Add-Ons, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: 8465dc7a42961a20fcd33ba8d43c71e2d73727ff
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7985513"
---
# <a name="create-an-add-on"></a><span data-ttu-id="e4ec8-104">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="e4ec8-104">Create an add-on</span></span>

<span data-ttu-id="e4ec8-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen eines Add-Ons (auch bekannt als in-app-Produkt oder IAP) für eine app, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-105">Use this method in the Microsoft Store submission API to create an add-on (also known as in-app product or IAP) for an app that is registered to your Partner Center account.</span></span>

> [!NOTE]
> <span data-ttu-id="e4ec8-106">Durch diese Methode wird ein Add-On ohne Übermittlungen erstellt.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-106">This method creates an add-on without any submissions.</span></span> <span data-ttu-id="e4ec8-107">Verwenden Sie zum Erstellen einer Übermittlung für ein Add-On die Methoden unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="e4ec8-107">To create a submission for an add-on, see the methods in [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4ec8-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e4ec8-108">Prerequisites</span></span>

<span data-ttu-id="e4ec8-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="e4ec8-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="e4ec8-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="e4ec8-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="e4ec8-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="e4ec8-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-113">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="e4ec8-114">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e4ec8-114">Request</span></span>

<span data-ttu-id="e4ec8-115">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-115">This method has the following syntax.</span></span> <span data-ttu-id="e4ec8-116">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-116">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="e4ec8-117">Methode</span><span class="sxs-lookup"><span data-stu-id="e4ec8-117">Method</span></span> | <span data-ttu-id="e4ec8-118">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e4ec8-118">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="e4ec8-119">POST</span><span class="sxs-lookup"><span data-stu-id="e4ec8-119">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts``` |


### <a name="request-header"></a><span data-ttu-id="e4ec8-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e4ec8-120">Request header</span></span>

| <span data-ttu-id="e4ec8-121">Header</span><span class="sxs-lookup"><span data-stu-id="e4ec8-121">Header</span></span>        | <span data-ttu-id="e4ec8-122">Typ</span><span class="sxs-lookup"><span data-stu-id="e4ec8-122">Type</span></span>   | <span data-ttu-id="e4ec8-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e4ec8-123">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="e4ec8-124">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="e4ec8-124">Authorization</span></span> | <span data-ttu-id="e4ec8-125">String</span><span class="sxs-lookup"><span data-stu-id="e4ec8-125">string</span></span> | <span data-ttu-id="e4ec8-126">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-126">Required.</span></span> <span data-ttu-id="e4ec8-127">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-127">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-body"></a><span data-ttu-id="e4ec8-128">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="e4ec8-128">Request body</span></span>

<span data-ttu-id="e4ec8-129">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-129">The request body has the following parameters.</span></span>

|  <span data-ttu-id="e4ec8-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="e4ec8-130">Parameter</span></span>  |  <span data-ttu-id="e4ec8-131">Typ</span><span class="sxs-lookup"><span data-stu-id="e4ec8-131">Type</span></span>  |  <span data-ttu-id="e4ec8-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e4ec8-132">Description</span></span>  |  <span data-ttu-id="e4ec8-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="e4ec8-133">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="e4ec8-134">applicationIds</span><span class="sxs-lookup"><span data-stu-id="e4ec8-134">applicationIds</span></span>  |  <span data-ttu-id="e4ec8-135">array</span><span class="sxs-lookup"><span data-stu-id="e4ec8-135">array</span></span>  |  <span data-ttu-id="e4ec8-136">Ein Array, das die Store-ID der App enthält, der dieses Add-On zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-136">An array that contains the Store ID of the app that this add-on is associated with.</span></span> <span data-ttu-id="e4ec8-137">In diesem Array wird nur ein Element unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-137">Only one item is supported in this array.</span></span>   |  <span data-ttu-id="e4ec8-138">Ja</span><span class="sxs-lookup"><span data-stu-id="e4ec8-138">Yes</span></span>  |
|  <span data-ttu-id="e4ec8-139">Produkt-ID</span><span class="sxs-lookup"><span data-stu-id="e4ec8-139">productId</span></span>  |  <span data-ttu-id="e4ec8-140">string</span><span class="sxs-lookup"><span data-stu-id="e4ec8-140">string</span></span>  |  <span data-ttu-id="e4ec8-141">Die Produkt-ID des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-141">The product ID of the add-on.</span></span> <span data-ttu-id="e4ec8-142">Dies ist eine ID, die im Code verwendet werden kann, um auf das Add-On zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-142">This is an identifier that can use in code to refer to the add-on.</span></span> <span data-ttu-id="e4ec8-143">Weitere Informationen finden Sie unter [Festlegen von Produkttyp und Produkt-ID für das IAP](https://msdn.microsoft.com/windows/uwp/publish/set-your-iap-product-id).</span><span class="sxs-lookup"><span data-stu-id="e4ec8-143">For more information, see [Set your product type and product ID](https://msdn.microsoft.com/windows/uwp/publish/set-your-iap-product-id).</span></span>  |  <span data-ttu-id="e4ec8-144">Ja</span><span class="sxs-lookup"><span data-stu-id="e4ec8-144">Yes</span></span>  |
|  <span data-ttu-id="e4ec8-145">Produkttyp</span><span class="sxs-lookup"><span data-stu-id="e4ec8-145">productType</span></span>  |  <span data-ttu-id="e4ec8-146">string</span><span class="sxs-lookup"><span data-stu-id="e4ec8-146">string</span></span>  |  <span data-ttu-id="e4ec8-147">Der Produkttyp des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-147">The product type of the add-on.</span></span> <span data-ttu-id="e4ec8-148">Die folgenden Werte werden unterstützt: **Gebrauchsgut** und **Verbrauchsartikel**.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-148">The following values are supported: **Durable** and **Consumable**.</span></span>  |  <span data-ttu-id="e4ec8-149">Ja</span><span class="sxs-lookup"><span data-stu-id="e4ec8-149">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="e4ec8-150">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="e4ec8-150">Request example</span></span>

<span data-ttu-id="e4ec8-151">Im folgenden Beispiel wird gezeigt, wie Sie ein neues Endverbraucher-Add-On für eine App erstellen.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-151">The following example demonstrates how to create a new consumable add-on for an app.</span></span>

```syntax
POST https://manage.devcenter.microsoft.com/v1.0/my/inappproducts HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1Q...
Content-Type: application/json
{
    "applicationIds": [  "9NBLGGH4R315"  ],
    "productId": "my-new-add-on",
    "productType": "Consumable",
}
```

## <a name="response"></a><span data-ttu-id="e4ec8-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="e4ec8-152">Response</span></span>

<span data-ttu-id="e4ec8-153">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-153">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="e4ec8-154">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-ons.md#add-on-object).</span><span class="sxs-lookup"><span data-stu-id="e4ec8-154">For more details about the values in the response body, see [add-on resource](manage-add-ons.md#add-on-object).</span></span>

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
  "productId": "my-new-add-on",
  "productType": "Consumable",
}
```

## <a name="error-codes"></a><span data-ttu-id="e4ec8-155">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e4ec8-155">Error codes</span></span>

<span data-ttu-id="e4ec8-156">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-156">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="e4ec8-157">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="e4ec8-157">Error code</span></span> |  <span data-ttu-id="e4ec8-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e4ec8-158">Description</span></span>                                                                                                                                                                           |
|--------|------------------|
| <span data-ttu-id="e4ec8-159">400</span><span class="sxs-lookup"><span data-stu-id="e4ec8-159">400</span></span>  | <span data-ttu-id="e4ec8-160">Die Anforderung ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-160">The request is invalid.</span></span> |
| <span data-ttu-id="e4ec8-161">409</span><span class="sxs-lookup"><span data-stu-id="e4ec8-161">409</span></span>  | <span data-ttu-id="e4ec8-162">Das Add-on konnte im aktuellen Zustand nicht erstellt werden, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="e4ec8-162">The add-on could not be created because of its current state, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="e4ec8-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e4ec8-163">Related topics</span></span>

* [<span data-ttu-id="e4ec8-164">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="e4ec8-164">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="e4ec8-165">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="e4ec8-165">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="e4ec8-166">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="e4ec8-166">Get all add-ons</span></span>](get-all-add-ons.md)
* [<span data-ttu-id="e4ec8-167">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="e4ec8-167">Get an add-on</span></span>](get-an-add-on.md)
* [<span data-ttu-id="e4ec8-168">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="e4ec8-168">Delete an add-on</span></span>](delete-an-add-on.md)
