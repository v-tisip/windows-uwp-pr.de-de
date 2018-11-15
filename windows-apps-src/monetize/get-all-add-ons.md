---
author: Xansky
ms.assetid: 7B6A99C6-AC86-41A1-85D0-3EB39A7211B6
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um alle Add-on-Daten für alle apps abzurufen, die für Ihr Partner Center-Konto registriert sind.
title: Abrufen aller Add-Ons
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-Ons, In-App-Produkte, IAPs
ms.localizationpriority: medium
ms.openlocfilehash: 4d58b29a959ed791665af52018062d0cf0a3a969
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6650958"
---
# <a name="get-all-add-ons"></a><span data-ttu-id="46091-104">Abrufen aller Add-Ons</span><span class="sxs-lookup"><span data-stu-id="46091-104">Get all add-ons</span></span>

<span data-ttu-id="46091-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für alle Add-ons für alle apps, die für Ihr Partner Center-Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="46091-105">Use this method in the Microsoft Store submission API to retrieve data for all add-ons for all the apps that are registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46091-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="46091-106">Prerequisites</span></span>

<span data-ttu-id="46091-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="46091-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="46091-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="46091-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="46091-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="46091-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="46091-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="46091-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="46091-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="46091-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="46091-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="46091-112">Request</span></span>

<span data-ttu-id="46091-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="46091-113">This method has the following syntax.</span></span> <span data-ttu-id="46091-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="46091-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="46091-115">Methode</span><span class="sxs-lookup"><span data-stu-id="46091-115">Method</span></span> | <span data-ttu-id="46091-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="46091-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="46091-117">GET</span><span class="sxs-lookup"><span data-stu-id="46091-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts``` |


### <a name="request-header"></a><span data-ttu-id="46091-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="46091-118">Request header</span></span>

| <span data-ttu-id="46091-119">Header</span><span class="sxs-lookup"><span data-stu-id="46091-119">Header</span></span>        | <span data-ttu-id="46091-120">Typ</span><span class="sxs-lookup"><span data-stu-id="46091-120">Type</span></span>   | <span data-ttu-id="46091-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="46091-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="46091-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="46091-122">Authorization</span></span> | <span data-ttu-id="46091-123">String</span><span class="sxs-lookup"><span data-stu-id="46091-123">string</span></span> | <span data-ttu-id="46091-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="46091-124">Required.</span></span> <span data-ttu-id="46091-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="46091-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="46091-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="46091-126">Request parameters</span></span>

<span data-ttu-id="46091-127">Alle Anforderungsparameter sind optional für diese Methode.</span><span class="sxs-lookup"><span data-stu-id="46091-127">All request parameters are optional for this method.</span></span> <span data-ttu-id="46091-128">Wenn Sie diese Methode ohne Parameter aufrufen, enthält die Antwort Daten für alle Add-Ons für alle Apps, die für Ihr Konto registriert sind.</span><span class="sxs-lookup"><span data-stu-id="46091-128">If you call this method without parameters, the response contains data for all add-ons for all apps that are registered to your account.</span></span>

|  <span data-ttu-id="46091-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="46091-129">Parameter</span></span>  |  <span data-ttu-id="46091-130">Typ</span><span class="sxs-lookup"><span data-stu-id="46091-130">Type</span></span>  |  <span data-ttu-id="46091-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="46091-131">Description</span></span>  |  <span data-ttu-id="46091-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="46091-132">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="46091-133">top</span><span class="sxs-lookup"><span data-stu-id="46091-133">top</span></span>  |  <span data-ttu-id="46091-134">int</span><span class="sxs-lookup"><span data-stu-id="46091-134">int</span></span>  |  <span data-ttu-id="46091-135">Die Anzahl von Elementen, die in der Anforderung zurückgegeben werden sollen (d.h. die Anzahl der zurückzugebenden-Add-Ons).</span><span class="sxs-lookup"><span data-stu-id="46091-135">The number of items to return in the request (that is, the number of add-ons to return).</span></span> <span data-ttu-id="46091-136">Wenn Ihr Konto über mehr Add-Ons als der Wert verfügt, den Sie in der Abfrage festlegen, enthält der Antworttext einen relativen URI-Pfad, den Sie an den URI der Methode anfügen können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="46091-136">If your account has more add-ons than the value you specify in the query, the response body includes a relative URI path that you can append to the method URI to request the next page of data.</span></span>  |  <span data-ttu-id="46091-137">Nein</span><span class="sxs-lookup"><span data-stu-id="46091-137">No</span></span>  |
|  <span data-ttu-id="46091-138">skip</span><span class="sxs-lookup"><span data-stu-id="46091-138">skip</span></span>  |  <span data-ttu-id="46091-139">int</span><span class="sxs-lookup"><span data-stu-id="46091-139">int</span></span>  |  <span data-ttu-id="46091-140">Die Anzahl der Elemente, die in der Abfrage umgangen werden sollen, bevor die verbleibenden Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="46091-140">The number of items to bypass in the query before returning the remaining items.</span></span> <span data-ttu-id="46091-141">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="46091-141">Use this parameter to page through data sets.</span></span> <span data-ttu-id="46091-142">Zum Beispiel werden bei top=10 und skip=0 die Elemente 1 bis 10 abgerufen, bei top=10 und skip=10 die Elemente 11 bis 20 und so weiter.</span><span class="sxs-lookup"><span data-stu-id="46091-142">For example, top=10 and skip=0 retrieves items 1 through 10, top=10 and skip=10 retrieves items 11 through 20, and so on.</span></span>  |  <span data-ttu-id="46091-143">Nein</span><span class="sxs-lookup"><span data-stu-id="46091-143">No</span></span>  |


### <a name="request-body"></a><span data-ttu-id="46091-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="46091-144">Request body</span></span>

<span data-ttu-id="46091-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="46091-145">Do not provide a request body for this method.</span></span>

### <a name="request-examples"></a><span data-ttu-id="46091-146">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="46091-146">Request examples</span></span>

<span data-ttu-id="46091-147">Im folgenden Beispiel wird veranschaulicht, wie alle Add-On-Daten für alle Apps abgerufen werden können, die für Ihr Konto registriert sind.</span><span class="sxs-lookup"><span data-stu-id="46091-147">The following example demonstrates how to retrieve all add-on data for all the apps that are registered to your account.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="46091-148">Im folgenden Beispiel wird veranschaulicht, wie nur die ersten 10 Add-Ons abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="46091-148">The following example demonstrates how to retrieve the first 10 add-ons only.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/inappproducts?top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="46091-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="46091-149">Response</span></span>

<span data-ttu-id="46091-150">Im folgenden Beispiel wird der JSON-Antworttext veranschaulicht, der von einer erfolgreichen Anforderung für die ersten 5 Add-Ons zurückgegeben wird, die für ein Entwicklerkonto mit insgesamt 1072 Add-Ons registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="46091-150">The following example demonstrates the JSON response body returned by a successful request for the first 5 add-ons that are registered to a developer account with 1072 total add-ons.</span></span> <span data-ttu-id="46091-151">Aus Platzgründen sind in diesem Beispiel nur die Daten für die ersten beiden Add-Ons dargestellt, die von der Anforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="46091-151">For brevity, this example only shows the data for the first two add-ons returned by the request.</span></span> <span data-ttu-id="46091-152">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="46091-152">For more details about the values in the response body, see the following section.</span></span>

```json
{
  "@nextLink": "inappproducts/?skip=5&top=5",
  "value": [
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
      "productId": "a8b8310b-fa8d-4da0-aca0-577ef6dce4dd",
      "productType": "Consumable",
      "pendingInAppProductSubmission": {
        "id": "1152921504621243619",
        "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
      },
      "lastPublishedInAppProductSubmission": {
        "id": "1152921504621243705",
        "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243705"
      }
    },
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
      "id": "9NBLGGH4TNMN",
      "productId": "6a3c9788-a350-448a-bd32-16160a13018a",
      "productType": "Consumable",
      "pendingInAppProductSubmission": {
        "id": "1152921504621243538",
        "resourceLocation": "inappproducts/9NBLGGH4TNMN/submissions/1152921504621243538"
      },
      "lastPublishedInAppProductSubmission": {
        "id": "1152921504621243106",
        "resourceLocation": "inappproducts/9NBLGGH4TNMN/submissions/1152921504621243106"
      }
    },

  // Other add-ons omitted for brevity...
  ],
  "totalCount": 1072
}
```

### <a name="response-body"></a><span data-ttu-id="46091-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="46091-153">Response body</span></span>

| <span data-ttu-id="46091-154">Wert</span><span class="sxs-lookup"><span data-stu-id="46091-154">Value</span></span>      | <span data-ttu-id="46091-155">Typ</span><span class="sxs-lookup"><span data-stu-id="46091-155">Type</span></span>   | <span data-ttu-id="46091-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="46091-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @nextLink  | <span data-ttu-id="46091-157">String</span><span class="sxs-lookup"><span data-stu-id="46091-157">string</span></span> | <span data-ttu-id="46091-158">Wenn weitere Datenseiten vorhanden sind, enthält diese Zeichenfolge einen relativen Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` zum Anfordern der nächsten Datenseite anfügen können.</span><span class="sxs-lookup"><span data-stu-id="46091-158">If there are additional pages of data, this string contains a relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to request the next page of data.</span></span> <span data-ttu-id="46091-159">Wenn beispielsweise der Parameter *top* des anfänglichen Anforderungstexts auf 10 festgelegt ist, für Ihr Konto jedoch 100Add-Ons registriert wurden, enthält der Antworttext den @nextLink-Wert ```inappproducts?skip=10&top=10```, der angibt, dass Sie ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts?skip=10&top=10``` aufrufen können, um die nächsten 10 Add-Ons anzufordern.</span><span class="sxs-lookup"><span data-stu-id="46091-159">For example, if the *top* parameter of the initial request body is set to 10 but there are 100 add-ons registered to your account, the response body will include a @nextLink value of ```inappproducts?skip=10&top=10```, which indicates that you can call ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts?skip=10&top=10``` to request the next 10 add-ons.</span></span> |
| <span data-ttu-id="46091-160">value</span><span class="sxs-lookup"><span data-stu-id="46091-160">value</span></span>            | <span data-ttu-id="46091-161">Array</span><span class="sxs-lookup"><span data-stu-id="46091-161">array</span></span>  |  <span data-ttu-id="46091-162">Ein Array, das die Objekte enthält, die Informationen über jedes Add-On bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="46091-162">An array that contains objects that provide information about each add-on.</span></span> <span data-ttu-id="46091-163">Weitere Informationen finden Sie unter [Add-On-Ressource](manage-add-ons.md#add-on-object).</span><span class="sxs-lookup"><span data-stu-id="46091-163">For more information, see [add-on resource](manage-add-ons.md#add-on-object).</span></span>   |
| <span data-ttu-id="46091-164">totalCount</span><span class="sxs-lookup"><span data-stu-id="46091-164">totalCount</span></span>   | <span data-ttu-id="46091-165">int</span><span class="sxs-lookup"><span data-stu-id="46091-165">int</span></span>  | <span data-ttu-id="46091-166">Die Anzahl der App-Objekte im *value*-Array des Antworttexts.</span><span class="sxs-lookup"><span data-stu-id="46091-166">The number of app objects in the *value* array of the response body.</span></span>     |


## <a name="error-codes"></a><span data-ttu-id="46091-167">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="46091-167">Error codes</span></span>

<span data-ttu-id="46091-168">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="46091-168">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="46091-169">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="46091-169">Error code</span></span> |  <span data-ttu-id="46091-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="46091-170">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="46091-171">404</span><span class="sxs-lookup"><span data-stu-id="46091-171">404</span></span>  | <span data-ttu-id="46091-172">Es wurden keine Add-Ons gefunden.</span><span class="sxs-lookup"><span data-stu-id="46091-172">No add-ons were found.</span></span> |
| <span data-ttu-id="46091-173">409</span><span class="sxs-lookup"><span data-stu-id="46091-173">409</span></span>  | <span data-ttu-id="46091-174">Die apps oder Add-ons verwenden Partner Center-Funktionen, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="46091-174">The apps or add-ons use Partner Center features that are [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="46091-175">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="46091-175">Related topics</span></span>

* [<span data-ttu-id="46091-176">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="46091-176">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="46091-177">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="46091-177">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="46091-178">Abrufen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="46091-178">Get an add-on</span></span>](get-an-add-on.md)
* [<span data-ttu-id="46091-179">Erstellen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="46091-179">Create an add-on</span></span>](create-an-add-on.md)
* [<span data-ttu-id="46091-180">Löschen eines Add-Ons</span><span class="sxs-lookup"><span data-stu-id="46091-180">Delete an add-on</span></span>](delete-an-add-on.md)
