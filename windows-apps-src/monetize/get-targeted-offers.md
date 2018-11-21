---
author: Xansky
ms.assetid: A4C6098B-6CB9-4FAF-B2EA-50B03D027FF1
description: Verwenden Sie diese Methode in der Microsoft Store-API für gezielte Angebote, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer im Zusammenhang mit der aktuellen App verfügbar sind.
title: Abrufen gezielter Angebote
ms.author: mhopkins
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-API für gezielte Angebote, gezielte Angebote abrufen
ms.localizationpriority: medium
ms.openlocfilehash: 87d59a4b5dabbc76c231e84034d701fccfe36fcf
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7557240"
---
# <a name="get-targeted-offers"></a><span data-ttu-id="a5042-104">Abrufen gezielter Angebote</span><span class="sxs-lookup"><span data-stu-id="a5042-104">Get targeted offers</span></span>

<span data-ttu-id="a5042-105">Verwenden Sie diese Methode, um die gezielten Angebote abzurufen, die für den aktuellen Benutzer verfügbar sind– basierend darauf, ob der Benutzer zum Kundensegment für das gezielte Angebot gehört.</span><span class="sxs-lookup"><span data-stu-id="a5042-105">Use this method to get the targeted offers that are available for the current user, based on whether or not the user is part of the customer segment for the targeted offer.</span></span> <span data-ttu-id="a5042-106">Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](manage-targeted-offers-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5042-106">For more information, see [Manage targeted offers using Store services](manage-targeted-offers-using-windows-store-services.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5042-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a5042-107">Prerequisites</span></span>

<span data-ttu-id="a5042-108">Um diese Methode zu verwenden, müssen Sie zunächst [ein Microsoft-Kontotoken abrufen](manage-targeted-offers-using-windows-store-services.md#obtain-a-microsoft-account-token), und zwar für den aktuell angemeldeten Benutzer Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="a5042-108">To use this method, you need to first [obtain a Microsoft Account token](manage-targeted-offers-using-windows-store-services.md#obtain-a-microsoft-account-token) for the current signed-in user of your app.</span></span> <span data-ttu-id="a5042-109">Sie müssen bei dieser Methode das Token an den ```Authorization```-Anforderungsheader übergeben.</span><span class="sxs-lookup"><span data-stu-id="a5042-109">You must pass this token in the ```Authorization``` request header for this method.</span></span> <span data-ttu-id="a5042-110">Dieses Token wird vom Store verwendet, um gezielte Angebote für den aktuellen Benutzer abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a5042-110">This token is used by the Store to get targeted offers for the current user.</span></span>

## <a name="request"></a><span data-ttu-id="a5042-111">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a5042-111">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="a5042-112">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="a5042-112">Request syntax</span></span>

| <span data-ttu-id="a5042-113">Methode</span><span class="sxs-lookup"><span data-stu-id="a5042-113">Method</span></span> | <span data-ttu-id="a5042-114">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a5042-114">Request URI</span></span>                                                                |
|--------|----------------------------------------------------------------------------|
| <span data-ttu-id="a5042-115">GET</span><span class="sxs-lookup"><span data-stu-id="a5042-115">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user``` |


### <a name="request-header"></a><span data-ttu-id="a5042-116">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a5042-116">Request header</span></span>

| <span data-ttu-id="a5042-117">Header</span><span class="sxs-lookup"><span data-stu-id="a5042-117">Header</span></span>        | <span data-ttu-id="a5042-118">Typ</span><span class="sxs-lookup"><span data-stu-id="a5042-118">Type</span></span>   | <span data-ttu-id="a5042-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5042-119">Description</span></span>  |
|---------------|--------|--------------|
| <span data-ttu-id="a5042-120">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="a5042-120">Authorization</span></span> | <span data-ttu-id="a5042-121">String</span><span class="sxs-lookup"><span data-stu-id="a5042-121">string</span></span> | <span data-ttu-id="a5042-122">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a5042-122">Required.</span></span> <span data-ttu-id="a5042-123">Das Microsoft-Kontotoken für den aktuell angemeldeten Benutzer Ihrer App im Format **Bearer**&lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="a5042-123">The Microsoft Account token for the current signed-in user of your app in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="a5042-124">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="a5042-124">Request parameters</span></span>

<span data-ttu-id="a5042-125">Diese Methode hat keinen URI oder Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="a5042-125">This method has no URI or query parameters.</span></span>

### <a name="request-example"></a><span data-ttu-id="a5042-126">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="a5042-126">Request example</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v2.0/my/storeoffers/user HTTP/1.1
Authorization: Bearer <Microsoft Account token>
```

## <a name="response"></a><span data-ttu-id="a5042-127">Antwort</span><span class="sxs-lookup"><span data-stu-id="a5042-127">Response</span></span>

<span data-ttu-id="a5042-128">Diese Methode gibt einen Antworttext im JSON-Format zurück, der ein Array mit Objekten und den folgenden Feldern enthält.</span><span class="sxs-lookup"><span data-stu-id="a5042-128">This method returns a JSON-formatted response body that contains an array of objects with the following fields.</span></span> <span data-ttu-id="a5042-129">Jedes Objekt im Array stellt gezielte Angebote dar, die für den angegebenen Kunden im Rahmen eines bestimmten Kundensegments verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a5042-129">Each object in the array represents the targeted offers that are available for the specified user as part of a particular customer segment.</span></span>

| <span data-ttu-id="a5042-130">Feld</span><span class="sxs-lookup"><span data-stu-id="a5042-130">Field</span></span>      | <span data-ttu-id="a5042-131">Typ</span><span class="sxs-lookup"><span data-stu-id="a5042-131">Type</span></span>   | <span data-ttu-id="a5042-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5042-132">Description</span></span>         |
|------------|--------|------------------|
| <span data-ttu-id="a5042-133">Angebote</span><span class="sxs-lookup"><span data-stu-id="a5042-133">offers</span></span>      | <span data-ttu-id="a5042-134">Array</span><span class="sxs-lookup"><span data-stu-id="a5042-134">array</span></span>  | <span data-ttu-id="a5042-135">Ein Array mit Produkt-IDs für die Add-Ons, die den gezielten Angeboten zugeordnet sind, die für den aktuellen Benutzer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a5042-135">An array of product IDs for the add-ons that are associated with the targeted offers that are available for the current user.</span></span> <span data-ttu-id="a5042-136">Diese Produkt-IDs werden in der Seite **gezielte Angebote** für Ihre app im Partner Center angegeben.</span><span class="sxs-lookup"><span data-stu-id="a5042-136">These product IDs are specified in the **Targeted offers** page for your app in Partner Center.</span></span>            |
| <span data-ttu-id="a5042-137">trackingId</span><span class="sxs-lookup"><span data-stu-id="a5042-137">trackingId</span></span>  | <span data-ttu-id="a5042-138">String</span><span class="sxs-lookup"><span data-stu-id="a5042-138">string</span></span> | <span data-ttu-id="a5042-139">Eine GUID, mit der Sie optional das gezielte Angebot in Ihrem eigenen Code oder Diensten nachverfolgen können.</span><span class="sxs-lookup"><span data-stu-id="a5042-139">A GUID that you can optionally use to keep track of the targeted offer in your own code or services.</span></span> |


### <a name="example"></a><span data-ttu-id="a5042-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a5042-140">Example</span></span>

<span data-ttu-id="a5042-141">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="a5042-141">The following example demonstrates an example JSON response body for this request.</span></span>

```json
[
  {
    "offers": [
      "10x gold coins",
      "100x gold coins"
    ],
    "trackingId": "5de5dd29-6dce-4e68-b45e-d8ee6c2cd203"
  }
]
```

## <a name="related-topics"></a><span data-ttu-id="a5042-142">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a5042-142">Related topics</span></span>

* [<span data-ttu-id="a5042-143">Verwalten von gezielten Angeboten mithilfe von Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="a5042-143">Manage targeted offers using Store services</span></span>](manage-targeted-offers-using-windows-store-services.md)

 

 
