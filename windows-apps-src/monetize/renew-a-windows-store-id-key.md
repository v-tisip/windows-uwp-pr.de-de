---
author: Xansky
ms.assetid: 3569C505-8D8C-4D85-B383-4839F13B2466
description: Verwenden Sie diese Microsoft zum Verlängern eines Microsoft Store-Schlüssels.
title: Verlängern eines Microsoft Store-ID-Schlüssels
ms.author: mhopkins
ms.date: 03/16/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Sammlungs-API, Microsoft Store-Einkaufs-API, Microsoft Store-ID-Schlüssel, verlängern
ms.localizationpriority: medium
ms.openlocfilehash: 95ee20628108bd3ea8eb9e48955a356410e91b1b
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5918811"
---
# <a name="renew-a-microsoft-store-id-key"></a><span data-ttu-id="a1912-104">Verlängern eines Microsoft Store-ID-Schlüssels</span><span class="sxs-lookup"><span data-stu-id="a1912-104">Renew a Microsoft Store ID key</span></span>


<span data-ttu-id="a1912-105">Verwenden Sie diese Microsoft zum Verlängern eines Microsoft Store-Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="a1912-105">Use this method to renew a Microsoft Store key.</span></span> <span data-ttu-id="a1912-106">Wenn Sie einen [Microsoft Store-ID-Schlüssel generieren](view-and-grant-products-from-a-service.md#step-4), ist dieser 90Tage lang gültig.</span><span class="sxs-lookup"><span data-stu-id="a1912-106">When you [generate a Microsoft Store ID key](view-and-grant-products-from-a-service.md#step-4), the key is valid for 90 days.</span></span> <span data-ttu-id="a1912-107">Nach Ablauf des Schlüssels können Sie anhand des abgelaufenen Schlüssels einen neuen Schlüssel aushandeln, indem Sie diese Methode anwenden.</span><span class="sxs-lookup"><span data-stu-id="a1912-107">After the key expires, you can use the expired key to renegotiate a new key by using this method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1912-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a1912-108">Prerequisites</span></span>


<span data-ttu-id="a1912-109">Zur Verwendung dieser Methode benötigen Sie:</span><span class="sxs-lookup"><span data-stu-id="a1912-109">To use this method, you will need:</span></span>

* <span data-ttu-id="a1912-110">Ein AzureAD-Zugriffstoken, das mit dem Zielgruppen-URI `https://onestore.microsoft.com` erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a1912-110">An Azure AD access token that has the audience URI value `https://onestore.microsoft.com`.</span></span>
* <span data-ttu-id="a1912-111">Ein abgelaufener MicrosoftStore-ID-Schlüssel, der [aus clientseitigem Code in Ihrer App generiert wurde](view-and-grant-products-from-a-service.md#step-4).</span><span class="sxs-lookup"><span data-stu-id="a1912-111">An expired Microsoft Store ID key that was [generated from client-side code in your app](view-and-grant-products-from-a-service.md#step-4).</span></span>

<span data-ttu-id="a1912-112">Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](view-and-grant-products-from-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="a1912-112">For more information, see [Manage product entitlements from a service](view-and-grant-products-from-a-service.md).</span></span>

## <a name="request"></a><span data-ttu-id="a1912-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a1912-113">Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a1912-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="a1912-114">Request syntax</span></span>

| <span data-ttu-id="a1912-115">Schlüsseltyp</span><span class="sxs-lookup"><span data-stu-id="a1912-115">Key type</span></span>    | <span data-ttu-id="a1912-116">Methode</span><span class="sxs-lookup"><span data-stu-id="a1912-116">Method</span></span> | <span data-ttu-id="a1912-117">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a1912-117">Request URI</span></span>                                              |
|-------------|--------|----------------------------------------------------------|
| <span data-ttu-id="a1912-118">Sammlungen</span><span class="sxs-lookup"><span data-stu-id="a1912-118">Collections</span></span> | <span data-ttu-id="a1912-119">POST</span><span class="sxs-lookup"><span data-stu-id="a1912-119">POST</span></span>   | ```https://collections.mp.microsoft.com/v6.0/b2b/keys/renew``` |
| <span data-ttu-id="a1912-120">Einkauf</span><span class="sxs-lookup"><span data-stu-id="a1912-120">Purchase</span></span>    | <span data-ttu-id="a1912-121">POST</span><span class="sxs-lookup"><span data-stu-id="a1912-121">POST</span></span>   | ```https://purchase.mp.microsoft.com/v6.0/b2b/keys/renew```    |


### <a name="request-header"></a><span data-ttu-id="a1912-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a1912-122">Request header</span></span>

| <span data-ttu-id="a1912-123">Header</span><span class="sxs-lookup"><span data-stu-id="a1912-123">Header</span></span>         | <span data-ttu-id="a1912-124">Typ</span><span class="sxs-lookup"><span data-stu-id="a1912-124">Type</span></span>   | <span data-ttu-id="a1912-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1912-125">Description</span></span>                                                                                           |
|----------------|--------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a1912-126">Host</span><span class="sxs-lookup"><span data-stu-id="a1912-126">Host</span></span>           | <span data-ttu-id="a1912-127">string</span><span class="sxs-lookup"><span data-stu-id="a1912-127">string</span></span> | <span data-ttu-id="a1912-128">Muss auf den Wert **collections.mp.microsoft.com** oder **purchase.mp.microsoft.com** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a1912-128">Must be set to the value **collections.mp.microsoft.com** or **purchase.mp.microsoft.com**.</span></span>           |
| <span data-ttu-id="a1912-129">Content-Length</span><span class="sxs-lookup"><span data-stu-id="a1912-129">Content-Length</span></span> | <span data-ttu-id="a1912-130">number</span><span class="sxs-lookup"><span data-stu-id="a1912-130">number</span></span> | <span data-ttu-id="a1912-131">Die Länge des Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="a1912-131">The length of the request body.</span></span>                                                                       |
| <span data-ttu-id="a1912-132">Inhaltstyp</span><span class="sxs-lookup"><span data-stu-id="a1912-132">Content-Type</span></span>   | <span data-ttu-id="a1912-133">string</span><span class="sxs-lookup"><span data-stu-id="a1912-133">string</span></span> | <span data-ttu-id="a1912-134">Gibt den Anforderungs- und Antworttyp an.</span><span class="sxs-lookup"><span data-stu-id="a1912-134">Specifies the request and response type.</span></span> <span data-ttu-id="a1912-135">Derzeit wird als einziger Wert **application/json** unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a1912-135">Currently, the only supported value is **application/json**.</span></span> |


### <a name="request-body"></a><span data-ttu-id="a1912-136">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="a1912-136">Request body</span></span>

| <span data-ttu-id="a1912-137">Parameter</span><span class="sxs-lookup"><span data-stu-id="a1912-137">Parameter</span></span>     | <span data-ttu-id="a1912-138">Typ</span><span class="sxs-lookup"><span data-stu-id="a1912-138">Type</span></span>   | <span data-ttu-id="a1912-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1912-139">Description</span></span>                       | <span data-ttu-id="a1912-140">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="a1912-140">Required</span></span> |
|---------------|--------|-----------------------------------|----------|
| <span data-ttu-id="a1912-141">serviceTicket</span><span class="sxs-lookup"><span data-stu-id="a1912-141">serviceTicket</span></span> | <span data-ttu-id="a1912-142">string</span><span class="sxs-lookup"><span data-stu-id="a1912-142">string</span></span> | <span data-ttu-id="a1912-143">Das Azure AD-Zugriffstoken.</span><span class="sxs-lookup"><span data-stu-id="a1912-143">The Azure AD access token.</span></span>        | <span data-ttu-id="a1912-144">Ja</span><span class="sxs-lookup"><span data-stu-id="a1912-144">Yes</span></span>      |
| <span data-ttu-id="a1912-145">key</span><span class="sxs-lookup"><span data-stu-id="a1912-145">key</span></span>           | <span data-ttu-id="a1912-146">string</span><span class="sxs-lookup"><span data-stu-id="a1912-146">string</span></span> | <span data-ttu-id="a1912-147">Der abgelaufene Microsoft Store-ID-Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="a1912-147">The expired Microsoft Store ID key.</span></span> | <span data-ttu-id="a1912-148">Ja</span><span class="sxs-lookup"><span data-stu-id="a1912-148">Yes</span></span>       |


### <a name="request-example"></a><span data-ttu-id="a1912-149">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="a1912-149">Request example</span></span>

```syntax
POST https://collections.mp.microsoft.com/v6.0/b2b/keys/renew HTTP/1.1
Content-Length: 2774
Content-Type: application/json
Host: collections.mp.microsoft.com

{
    "serviceTicket": "eyJ0eXAiOiJKV1QiLCJhb….",
    "Key": "eyJ0eXAiOiJKV1QiLCJhbG…."
}
```

## <a name="response"></a><span data-ttu-id="a1912-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="a1912-150">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="a1912-151">Antworttext</span><span class="sxs-lookup"><span data-stu-id="a1912-151">Response body</span></span>

| <span data-ttu-id="a1912-152">Parameter</span><span class="sxs-lookup"><span data-stu-id="a1912-152">Parameter</span></span> | <span data-ttu-id="a1912-153">Typ</span><span class="sxs-lookup"><span data-stu-id="a1912-153">Type</span></span>   | <span data-ttu-id="a1912-154">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1912-154">Description</span></span>                                                                                                            |
|-----------|--------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a1912-155">key</span><span class="sxs-lookup"><span data-stu-id="a1912-155">key</span></span>       | <span data-ttu-id="a1912-156">string</span><span class="sxs-lookup"><span data-stu-id="a1912-156">string</span></span> | <span data-ttu-id="a1912-157">Der aktualisierte Microsoft Store-Schlüssel kann dann für zukünftige Aufrufe der Sammlungs- oder Einkaufs-API von Microsoft Store verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a1912-157">The refreshed Microsoft Store key that can be used in future calls to the Microsoft Store collections API or purchase API.</span></span> |


### <a name="response-example"></a><span data-ttu-id="a1912-158">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="a1912-158">Response example</span></span>

```syntax
HTTP/1.1 200 OK
Content-Length: 1646
Content-Type: application/json
MS-CorrelationId: bfebe80c-ff89-4c4b-8897-67b45b916e47
MS-RequestId: 1b5fa630-d672-4971-b2c0-3713f4ea6c85
MS-CV: xu2HW6SrSkyfHyFh.0.0
MS-ServerId: 030011428
Date: Tue, 13 Sep 2015 07:31:12 GMT

{
    "key":"eyJ0eXAi….."
}
```

## <a name="error-codes"></a><span data-ttu-id="a1912-159">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="a1912-159">Error codes</span></span>


| <span data-ttu-id="a1912-160">Code</span><span class="sxs-lookup"><span data-stu-id="a1912-160">Code</span></span> | <span data-ttu-id="a1912-161">Fehler</span><span class="sxs-lookup"><span data-stu-id="a1912-161">Error</span></span>        | <span data-ttu-id="a1912-162">Interner Fehlercode</span><span class="sxs-lookup"><span data-stu-id="a1912-162">Inner error code</span></span>           | <span data-ttu-id="a1912-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1912-163">Description</span></span>   |
|------|--------------|----------------------------|---------------|
| <span data-ttu-id="a1912-164">401</span><span class="sxs-lookup"><span data-stu-id="a1912-164">401</span></span>  | <span data-ttu-id="a1912-165">Nicht autorisiert</span><span class="sxs-lookup"><span data-stu-id="a1912-165">Unauthorized</span></span> | <span data-ttu-id="a1912-166">AuthenticationTokenInvalid</span><span class="sxs-lookup"><span data-stu-id="a1912-166">AuthenticationTokenInvalid</span></span> | <span data-ttu-id="a1912-167">Das Azure AD-Zugriffstoken ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="a1912-167">The Azure AD access token is invalid.</span></span> <span data-ttu-id="a1912-168">In einigen Fällen enthalten die Details zu ServiceError weitere Informationen, z. B. wenn das Token abgelaufen ist oder der *appid*-Anspruch fehlt.</span><span class="sxs-lookup"><span data-stu-id="a1912-168">In some cases the details of the ServiceError will contain more information, such as when the token is expired or the *appid* claim is missing.</span></span> |
| <span data-ttu-id="a1912-169">401</span><span class="sxs-lookup"><span data-stu-id="a1912-169">401</span></span>  | <span data-ttu-id="a1912-170">Nicht autorisiert</span><span class="sxs-lookup"><span data-stu-id="a1912-170">Unauthorized</span></span> | <span data-ttu-id="a1912-171">InconsistentClientId</span><span class="sxs-lookup"><span data-stu-id="a1912-171">InconsistentClientId</span></span>       | <span data-ttu-id="a1912-172">Der *clientId*-Anspruch im Microsoft Store-ID-Schlüssel und der *appid*-Anspruch im Azure AD-Zugriffstoken stimmen nicht überein.</span><span class="sxs-lookup"><span data-stu-id="a1912-172">The *clientId* claim in the Microsoft Store ID key and the *appid* claim in the Azure AD access token do not match.</span></span>                                                                     |


## <a name="related-topics"></a><span data-ttu-id="a1912-173">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a1912-173">Related topics</span></span>


* [<span data-ttu-id="a1912-174">Verwalten von Produktansprüchen aus einem Dienst</span><span class="sxs-lookup"><span data-stu-id="a1912-174">Manage product entitlements from a service</span></span>](view-and-grant-products-from-a-service.md)
* [<span data-ttu-id="a1912-175">Produktabfrage</span><span class="sxs-lookup"><span data-stu-id="a1912-175">Query for products</span></span>](query-for-products.md)
* [<span data-ttu-id="a1912-176">Melden von Verbrauchsprodukten als erfüllt</span><span class="sxs-lookup"><span data-stu-id="a1912-176">Report consumable products as fulfilled</span></span>](report-consumable-products-as-fulfilled.md)
* [<span data-ttu-id="a1912-177">Gewähren kostenloser Produkte</span><span class="sxs-lookup"><span data-stu-id="a1912-177">Grant free products</span></span>](grant-free-products.md)
