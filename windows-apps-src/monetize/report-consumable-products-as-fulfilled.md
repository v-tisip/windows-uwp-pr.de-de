---
author: Xansky
ms.assetid: E9BEB2D2-155F-45F6-95F8-6B36C3E81649
description: Verwenden Sie diese Methode aus der Microsoft Store Collection-API, um den Kauf eines Verbrauchsprodukt für einen bestimmten Kunden als abgewickelt zu melden. Damit ein Benutzer ein Verbrauchsprodukt erneut erwerben kann, muss Ihre App oder Ihr Dienst das Verbrauchsprodukt für den betreffenden Benutzer als abgewickelt melden.
title: Verbrauchsprodukte als erfüllt melden
ms.author: mhopkins
ms.date: 03/16/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Sammlungs-API, erfüllen, Verbrauchsprodukt
ms.localizationpriority: medium
ms.openlocfilehash: 69795a40ae5e46f95330cd6a6d2738adc9a74686
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5834525"
---
# <a name="report-consumable-products-as-fulfilled"></a><span data-ttu-id="8b13c-105">Verbrauchsprodukte als erfüllt melden</span><span class="sxs-lookup"><span data-stu-id="8b13c-105">Report consumable products as fulfilled</span></span>

<span data-ttu-id="8b13c-106">Verwenden Sie diese Methode aus der Microsoft Store Collection-API, um den Kauf eines Verbrauchsprodukt für einen bestimmten Kunden als abgewickelt zu melden.</span><span class="sxs-lookup"><span data-stu-id="8b13c-106">Use this method in the Microsoft Store collection API to report a consumable product as fulfilled for a given customer.</span></span> <span data-ttu-id="8b13c-107">Damit ein Benutzer ein Verbrauchsprodukt erneut erwerben kann, muss Ihre App oder Ihr Dienst das Verbrauchsprodukt für den betreffenden Benutzer als erfüllt melden.</span><span class="sxs-lookup"><span data-stu-id="8b13c-107">Before a user can repurchase a consumable product, your app or service must report the consumable product as fulfilled for that user.</span></span>

<span data-ttu-id="8b13c-108">Sie können diese Methode auf zwei Weisen verwenden, um ein Verbrauchsprodukt als erfüllt zu melden:</span><span class="sxs-lookup"><span data-stu-id="8b13c-108">There are two ways you can use this method to report a consumable product as fulfilled:</span></span>

* <span data-ttu-id="8b13c-109">Geben Sie die (im **itemId**-Parameter einer [Produktabfrage](query-for-products.md)) zurückgegebene) Artikelkennung des Verbrauchsprodukts und eine von Ihnen bereitgestellte eindeutige Tracking-ID an.</span><span class="sxs-lookup"><span data-stu-id="8b13c-109">Provide the item ID of the consumable (as returned in the **itemId** parameter of a [query for products](query-for-products.md)), and a unique tracking ID that you provide.</span></span> <span data-ttu-id="8b13c-110">Wenn die gleiche Tracking-ID für mehrere Versuche verwendet wird, wird auch dann das gleiche Ergebnis zurückgegeben, wenn der Artikel bereits in Anspruch genommen wurde.</span><span class="sxs-lookup"><span data-stu-id="8b13c-110">If the same tracking ID is used for multiple tries, the same result will be returned even if the item is already consumed.</span></span> <span data-ttu-id="8b13c-111">Wenn Sie nicht sicher sind, ob eine Verbrauchsanforderung erfolgreich war, sollte Ihr Dienst Verbrauchsanforderungen mit derselben Tracking-ID erneut übermitteln.</span><span class="sxs-lookup"><span data-stu-id="8b13c-111">If you aren't certain if a consume request was successful, your service should resubmit consume requests with the same tracking ID.</span></span> <span data-ttu-id="8b13c-112">Die Tracking-ID ist immer mit der jeweiligen Verbrauchsanforderung verknüpft und kann beliebig oft erneut übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="8b13c-112">The tracking ID will always be tied to that consume request and can be resubmitted indefinitely.</span></span>
* <span data-ttu-id="8b13c-113">Geben Sie die (im **productId**-Parameter einer [Produktabfrage](query-for-products.md) zurückgegebene) Produkt-ID und eine Transaktions-ID an, die aus einer der Quellen abgerufen wird, die in der Beschreibung für den **transactionId**-Parameter im Abschnitt „Anforderungstext“ unten aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="8b13c-113">Provide the product ID (as returned in the **productId** parameter of a [query for products](query-for-products.md)) and a transaction ID that is obtained from one of the sources listed in the description for the **transactionId** parameter in the request body section below.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8b13c-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8b13c-114">Prerequisites</span></span>


<span data-ttu-id="8b13c-115">Zur Verwendung dieser Methode benötigen Sie:</span><span class="sxs-lookup"><span data-stu-id="8b13c-115">To use this method, you will need:</span></span>

* <span data-ttu-id="8b13c-116">Ein AzureAD-Zugriffstoken, das mit dem Zielgruppen-URI `https://onestore.microsoft.com` erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="8b13c-116">An Azure AD access token that has the audience URI value `https://onestore.microsoft.com`.</span></span>
* <span data-ttu-id="8b13c-117">Ein Microsoft Store-ID-Schlüssel, der die Identität des Benutzers darstellt, für den Sie ein Verbrauchsprodukt als erfüllt melden möchten.</span><span class="sxs-lookup"><span data-stu-id="8b13c-117">A Microsoft Store ID key that represents the identity of the user for whom you want to report a consumable product as fulfilled.</span></span>

<span data-ttu-id="8b13c-118">Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](view-and-grant-products-from-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="8b13c-118">For more information, see [Manage product entitlements from a service](view-and-grant-products-from-a-service.md).</span></span>

## <a name="request"></a><span data-ttu-id="8b13c-119">Anforderung</span><span class="sxs-lookup"><span data-stu-id="8b13c-119">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="8b13c-120">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="8b13c-120">Request syntax</span></span>

| <span data-ttu-id="8b13c-121">Methode</span><span class="sxs-lookup"><span data-stu-id="8b13c-121">Method</span></span> | <span data-ttu-id="8b13c-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="8b13c-122">Request URI</span></span>                                                   |
|--------|---------------------------------------------------------------|
| <span data-ttu-id="8b13c-123">POST</span><span class="sxs-lookup"><span data-stu-id="8b13c-123">POST</span></span>   | ```https://collections.mp.microsoft.com/v6.0/collections/consume``` |


### <a name="request-header"></a><span data-ttu-id="8b13c-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="8b13c-124">Request header</span></span>

| <span data-ttu-id="8b13c-125">Header</span><span class="sxs-lookup"><span data-stu-id="8b13c-125">Header</span></span>         | <span data-ttu-id="8b13c-126">Typ</span><span class="sxs-lookup"><span data-stu-id="8b13c-126">Type</span></span>   | <span data-ttu-id="8b13c-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8b13c-127">Description</span></span>                                                                                           |
|----------------|--------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8b13c-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="8b13c-128">Authorization</span></span>  | <span data-ttu-id="8b13c-129">String</span><span class="sxs-lookup"><span data-stu-id="8b13c-129">string</span></span> | <span data-ttu-id="8b13c-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8b13c-130">Required.</span></span> <span data-ttu-id="8b13c-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="8b13c-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>                           |
| <span data-ttu-id="8b13c-132">Host</span><span class="sxs-lookup"><span data-stu-id="8b13c-132">Host</span></span>           | <span data-ttu-id="8b13c-133">string</span><span class="sxs-lookup"><span data-stu-id="8b13c-133">string</span></span> | <span data-ttu-id="8b13c-134">Muss auf den Wert **collections.mp.microsoft.com** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="8b13c-134">Must be set to the value **collections.mp.microsoft.com**.</span></span>                                            |
| <span data-ttu-id="8b13c-135">Content-Length</span><span class="sxs-lookup"><span data-stu-id="8b13c-135">Content-Length</span></span> | <span data-ttu-id="8b13c-136">number</span><span class="sxs-lookup"><span data-stu-id="8b13c-136">number</span></span> | <span data-ttu-id="8b13c-137">Die Länge des Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="8b13c-137">The length of the request body.</span></span>                                                                       |
| <span data-ttu-id="8b13c-138">Inhaltstyp</span><span class="sxs-lookup"><span data-stu-id="8b13c-138">Content-Type</span></span>   | <span data-ttu-id="8b13c-139">string</span><span class="sxs-lookup"><span data-stu-id="8b13c-139">string</span></span> | <span data-ttu-id="8b13c-140">Gibt den Anforderungs- und Antworttyp an.</span><span class="sxs-lookup"><span data-stu-id="8b13c-140">Specifies the request and response type.</span></span> <span data-ttu-id="8b13c-141">Derzeit wird als einziger Wert **application/json** unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8b13c-141">Currently, the only supported value is **application/json**.</span></span> |


### <a name="request-body"></a><span data-ttu-id="8b13c-142">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="8b13c-142">Request body</span></span>

| <span data-ttu-id="8b13c-143">Parameter</span><span class="sxs-lookup"><span data-stu-id="8b13c-143">Parameter</span></span>     | <span data-ttu-id="8b13c-144">Typ</span><span class="sxs-lookup"><span data-stu-id="8b13c-144">Type</span></span>         | <span data-ttu-id="8b13c-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8b13c-145">Description</span></span>         | <span data-ttu-id="8b13c-146">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8b13c-146">Required</span></span> |
|---------------|--------------|---------------------|----------|
| <span data-ttu-id="8b13c-147">beneficiary</span><span class="sxs-lookup"><span data-stu-id="8b13c-147">beneficiary</span></span>   | <span data-ttu-id="8b13c-148">UserIdentity</span><span class="sxs-lookup"><span data-stu-id="8b13c-148">UserIdentity</span></span> | <span data-ttu-id="8b13c-149">Der Benutzer, für den dieser Artikel genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="8b13c-149">The user for which this item is being consumed.</span></span> <span data-ttu-id="8b13c-150">Weitere Informationen finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="8b13c-150">For more information, see the following table.</span></span>        | <span data-ttu-id="8b13c-151">Ja</span><span class="sxs-lookup"><span data-stu-id="8b13c-151">Yes</span></span>      |
| <span data-ttu-id="8b13c-152">itemId</span><span class="sxs-lookup"><span data-stu-id="8b13c-152">itemId</span></span>        | <span data-ttu-id="8b13c-153">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8b13c-153">string</span></span>       | <span data-ttu-id="8b13c-154">Der Wert *itemId*, der von einer [Produktanfrage](query-for-products.md) zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b13c-154">The *itemId* value returned by a [query for products](query-for-products.md).</span></span> <span data-ttu-id="8b13c-155">Verwenden Sie diesen Parameter mit *trackingId*.</span><span class="sxs-lookup"><span data-stu-id="8b13c-155">Use this parameter with *trackingId*</span></span>      | <span data-ttu-id="8b13c-156">Nein</span><span class="sxs-lookup"><span data-stu-id="8b13c-156">No</span></span>       |
| <span data-ttu-id="8b13c-157">trackingId</span><span class="sxs-lookup"><span data-stu-id="8b13c-157">trackingId</span></span>    | <span data-ttu-id="8b13c-158">guid</span><span class="sxs-lookup"><span data-stu-id="8b13c-158">guid</span></span>         | <span data-ttu-id="8b13c-159">Eine eindeutige, vom Entwickler angegebene Tracking-ID.</span><span class="sxs-lookup"><span data-stu-id="8b13c-159">A unique tracking ID provided by developer.</span></span> <span data-ttu-id="8b13c-160">Verwenden Sie diesen Parameter mit *itemId*.</span><span class="sxs-lookup"><span data-stu-id="8b13c-160">Use this parameter with *itemId*.</span></span>         | <span data-ttu-id="8b13c-161">Nein</span><span class="sxs-lookup"><span data-stu-id="8b13c-161">No</span></span>       |
| <span data-ttu-id="8b13c-162">Produkt-ID</span><span class="sxs-lookup"><span data-stu-id="8b13c-162">productId</span></span>     | <span data-ttu-id="8b13c-163">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8b13c-163">string</span></span>       | <span data-ttu-id="8b13c-164">Der Wert *productId*, den eine [Produktabfrage](query-for-products.md) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="8b13c-164">The *productId* value returned by a [query for products](query-for-products.md).</span></span> <span data-ttu-id="8b13c-165">Verwenden Sie diesen Parameter mit *transactionId*.</span><span class="sxs-lookup"><span data-stu-id="8b13c-165">Use this parameter with *transactionId*</span></span>   | <span data-ttu-id="8b13c-166">Nein.</span><span class="sxs-lookup"><span data-stu-id="8b13c-166">No</span></span>       |
| <span data-ttu-id="8b13c-167">transactionId</span><span class="sxs-lookup"><span data-stu-id="8b13c-167">transactionId</span></span> | <span data-ttu-id="8b13c-168">guid</span><span class="sxs-lookup"><span data-stu-id="8b13c-168">guid</span></span>         | <span data-ttu-id="8b13c-169">Ein Transaktions-ID-Wert, der aus einer der folgenden Quellen abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8b13c-169">A transaction ID value that is obtained from one of the following sources.</span></span> <span data-ttu-id="8b13c-170">Verwenden Sie diesen Parameter mit *productId*.</span><span class="sxs-lookup"><span data-stu-id="8b13c-170">Use this parameter with *productId*.</span></span><ul><li><span data-ttu-id="8b13c-171">Die [TransactionID](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.purchaseresults.transactionid)-Eigenschaft der [PurchaseResults](https://msdn.microsoft.com/library/windows/apps/dn263392)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="8b13c-171">The [TransactionID](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.purchaseresults.transactionid) property of the [PurchaseResults](https://msdn.microsoft.com/library/windows/apps/dn263392) class.</span></span></li><li><span data-ttu-id="8b13c-172">Der von [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync), [RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestapppurchaseasync) oder [GetAppReceiptAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getappreceiptasync) zurückgegebene App- oder Produktbeleg.</span><span class="sxs-lookup"><span data-stu-id="8b13c-172">The app or product receipt that is returned by [RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync), [RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestapppurchaseasync), or [GetAppReceiptAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getappreceiptasync).</span></span></li><li><span data-ttu-id="8b13c-173">Der Parameter *transactionId*, der von einer [Produktabfrage](query-for-products.md) zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b13c-173">The *transactionId* parameter returned by a [query for products](query-for-products.md).</span></span></li></ul>   | <span data-ttu-id="8b13c-174">Nein</span><span class="sxs-lookup"><span data-stu-id="8b13c-174">No</span></span>       |


<span data-ttu-id="8b13c-175">Das UserIdentity-Objekt enthält die folgenden Parameter.</span><span class="sxs-lookup"><span data-stu-id="8b13c-175">The UserIdentity object contains the following parameters.</span></span>

| <span data-ttu-id="8b13c-176">Parameter</span><span class="sxs-lookup"><span data-stu-id="8b13c-176">Parameter</span></span>            | <span data-ttu-id="8b13c-177">Typ</span><span class="sxs-lookup"><span data-stu-id="8b13c-177">Type</span></span>   | <span data-ttu-id="8b13c-178">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8b13c-178">Description</span></span>       | <span data-ttu-id="8b13c-179">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8b13c-179">Required</span></span> |
|----------------------|--------|-------------------|----------|
| <span data-ttu-id="8b13c-180">identityType</span><span class="sxs-lookup"><span data-stu-id="8b13c-180">identityType</span></span>         | <span data-ttu-id="8b13c-181">string</span><span class="sxs-lookup"><span data-stu-id="8b13c-181">string</span></span> | <span data-ttu-id="8b13c-182">Gibt den Zeichenfolgenwert **b2b** an.</span><span class="sxs-lookup"><span data-stu-id="8b13c-182">Specify the string value **b2b**.</span></span>    | <span data-ttu-id="8b13c-183">Ja</span><span class="sxs-lookup"><span data-stu-id="8b13c-183">Yes</span></span>      |
| <span data-ttu-id="8b13c-184">identityValue</span><span class="sxs-lookup"><span data-stu-id="8b13c-184">identityValue</span></span>        | <span data-ttu-id="8b13c-185">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8b13c-185">string</span></span> | <span data-ttu-id="8b13c-186">Der [Microsoft Store-ID-Schlüssel](view-and-grant-products-from-a-service.md#step-4), der die Identität des Benutzers darstellt, für den Sie ein Verbrauchsprodukt als erfüllt melden möchten.</span><span class="sxs-lookup"><span data-stu-id="8b13c-186">The [Microsoft Store ID key](view-and-grant-products-from-a-service.md#step-4) that represents the identity of the user for whom you want to report a consumable product as fulfilled.</span></span>      | <span data-ttu-id="8b13c-187">Ja</span><span class="sxs-lookup"><span data-stu-id="8b13c-187">Yes</span></span>      |
| <span data-ttu-id="8b13c-188">localTicketReference</span><span class="sxs-lookup"><span data-stu-id="8b13c-188">localTicketReference</span></span> | <span data-ttu-id="8b13c-189">string</span><span class="sxs-lookup"><span data-stu-id="8b13c-189">string</span></span> | <span data-ttu-id="8b13c-190">Der angeforderte Bezeichner für die zurückgegebene Antwort.</span><span class="sxs-lookup"><span data-stu-id="8b13c-190">The requested identifier for the returned response.</span></span> <span data-ttu-id="8b13c-191">Es wird empfohlen, denselben Wert als *userId*-[Anspruch](view-and-grant-products-from-a-service.md#claims-in-a-microsoft-store-id-key) im Microsoft Store-ID-Schlüssel zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b13c-191">We recommend that you use the same value as the *userId*  [claim](view-and-grant-products-from-a-service.md#claims-in-a-microsoft-store-id-key) in the Microsoft Store ID key.</span></span> | <span data-ttu-id="8b13c-192">Ja</span><span class="sxs-lookup"><span data-stu-id="8b13c-192">Yes</span></span>      |


### <a name="request-examples"></a><span data-ttu-id="8b13c-193">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="8b13c-193">Request examples</span></span>

<span data-ttu-id="8b13c-194">Im folgenden Beispiel werden *itemId* und *trackingId* verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b13c-194">The following example uses *itemId* and *trackingId*.</span></span>

```syntax
POST https://collections.mp.microsoft.com/v6.0/collections/consume HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1…..
Host: collections.mp.microsoft.com
Content-Length: 2050
Content-Type: application/json

{
    "beneficiary": {
        "localTicketReference": "testreference",
        "identityValue": "eyJ0eXAiOi…..",
        "identityType": "b2b"
    },
    "itemId": "44c26106-4979-457b-af34-609ae97a084f",
    "trackingId": "44db79ca-e31d-49e9-8896-fa5c7f892b40"
}
```

<span data-ttu-id="8b13c-195">Im folgenden Beispiel werden *productId* und *transactionId* verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b13c-195">The following example uses *productId* and *transactionId*.</span></span>

```syntax
POST https://collections.mp.microsoft.com/v6.0/collections/consume HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1……
Content-Length: 1880
Content-Type: application/json
Host: collections.md.mp.microsoft.com

{
    "beneficiary" : {
        "localTicketReference" : "testReference",
        "identityValue" : "eyJ0eXAiOiJ…..",
        "identitytype" : "b2b"
    },
    "productId" : "9NBLGGH5WVP6",
    "transactionId" : "08a14c7c-1892-49fc-9135-190ca4f10490"
}
```


## <a name="response"></a><span data-ttu-id="8b13c-196">Antwort</span><span class="sxs-lookup"><span data-stu-id="8b13c-196">Response</span></span>

<span data-ttu-id="8b13c-197">Bei erfolgreicher Nutzung wird kein Inhalt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b13c-197">No content will be returned if the consumption was executed successfully.</span></span>

### <a name="response-example"></a><span data-ttu-id="8b13c-198">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="8b13c-198">Response example</span></span>

```syntax
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 386f733d-bc66-4bf9-9b6f-a1ad417f97f0
MS-RequestId: e488cd0a-9fb6-4c2c-bb77-e5100d3c15b1
MS-CV: 5.1
MS-ServerId: 030011326
Date: Tue, 22 Sep 2015 20:40:55 GMT
```

## <a name="error-codes"></a><span data-ttu-id="8b13c-199">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="8b13c-199">Error codes</span></span>


| <span data-ttu-id="8b13c-200">Code</span><span class="sxs-lookup"><span data-stu-id="8b13c-200">Code</span></span> | <span data-ttu-id="8b13c-201">Fehler</span><span class="sxs-lookup"><span data-stu-id="8b13c-201">Error</span></span>        | <span data-ttu-id="8b13c-202">Interner Fehlercode</span><span class="sxs-lookup"><span data-stu-id="8b13c-202">Inner error code</span></span>           | <span data-ttu-id="8b13c-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8b13c-203">Description</span></span>           |
|------|--------------|----------------------------|-----------------------|
| <span data-ttu-id="8b13c-204">401</span><span class="sxs-lookup"><span data-stu-id="8b13c-204">401</span></span>  | <span data-ttu-id="8b13c-205">Nicht autorisiert</span><span class="sxs-lookup"><span data-stu-id="8b13c-205">Unauthorized</span></span> | <span data-ttu-id="8b13c-206">AuthenticationTokenInvalid</span><span class="sxs-lookup"><span data-stu-id="8b13c-206">AuthenticationTokenInvalid</span></span> | <span data-ttu-id="8b13c-207">Das Azure AD-Zugriffstoken ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="8b13c-207">The Azure AD access token is invalid.</span></span> <span data-ttu-id="8b13c-208">In einigen Fällen enthalten die Details zu ServiceError weitere Informationen, z. B. wenn das Token abgelaufen ist oder der *appid*-Anspruch fehlt.</span><span class="sxs-lookup"><span data-stu-id="8b13c-208">In some cases the details of the ServiceError will contain more information, such as when the token is expired or the *appid* claim is missing.</span></span> |
| <span data-ttu-id="8b13c-209">401</span><span class="sxs-lookup"><span data-stu-id="8b13c-209">401</span></span>  | <span data-ttu-id="8b13c-210">Nicht autorisiert</span><span class="sxs-lookup"><span data-stu-id="8b13c-210">Unauthorized</span></span> | <span data-ttu-id="8b13c-211">PartnerAadTicketRequired</span><span class="sxs-lookup"><span data-stu-id="8b13c-211">PartnerAadTicketRequired</span></span>   | <span data-ttu-id="8b13c-212">An den Dienst wurde im Autorisierungsheader kein Azure AD-Zugriffstoken übergeben.</span><span class="sxs-lookup"><span data-stu-id="8b13c-212">An Azure AD access token was not passed to the service in the authorization header.</span></span>                                                                                                   |
| <span data-ttu-id="8b13c-213">401</span><span class="sxs-lookup"><span data-stu-id="8b13c-213">401</span></span>  | <span data-ttu-id="8b13c-214">Nicht autorisiert</span><span class="sxs-lookup"><span data-stu-id="8b13c-214">Unauthorized</span></span> | <span data-ttu-id="8b13c-215">InconsistentClientId</span><span class="sxs-lookup"><span data-stu-id="8b13c-215">InconsistentClientId</span></span>       | <span data-ttu-id="8b13c-216">Der *clientId*-Anspruch im Microsoft Store-ID-Schlüssel im Anforderungstext und der *appid*-Anspruch im Azure AD-Zugriffstoken im Autorisierungsheader stimmen nicht überein.</span><span class="sxs-lookup"><span data-stu-id="8b13c-216">The *clientId* claim in the Microsoft Store ID key in the request body and the *appid* claim in the Azure AD access token in the authorization header do not match.</span></span>                     |

<span/> 

## <a name="related-topics"></a><span data-ttu-id="8b13c-217">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8b13c-217">Related topics</span></span>

* [<span data-ttu-id="8b13c-218">Verwalten von Produktansprüchen aus einem Dienst</span><span class="sxs-lookup"><span data-stu-id="8b13c-218">Manage product entitlements from a service</span></span>](view-and-grant-products-from-a-service.md)
* [<span data-ttu-id="8b13c-219">Produktabfrage</span><span class="sxs-lookup"><span data-stu-id="8b13c-219">Query for products</span></span>](query-for-products.md)
* [<span data-ttu-id="8b13c-220">Gewähren kostenloser Produkte</span><span class="sxs-lookup"><span data-stu-id="8b13c-220">Grant free products</span></span>](grant-free-products.md)
* [<span data-ttu-id="8b13c-221">Verlängern eines Microsoft Store-ID-Schlüssels</span><span class="sxs-lookup"><span data-stu-id="8b13c-221">Renew a Microsoft Store ID key</span></span>](renew-a-windows-store-id-key.md)
