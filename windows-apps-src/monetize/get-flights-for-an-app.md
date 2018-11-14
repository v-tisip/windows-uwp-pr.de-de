---
author: Xansky
ms.assetid: B0AD0B8E-867E-4403-9CF6-43C81F3C30CA
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen zu einem Flight-Paket für eine app abzurufen, die für Ihr Partner Center-Konto registriert ist.
title: Abrufen von Flight-Paketen für eine App
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight, Flight-Pakete
ms.localizationpriority: medium
ms.openlocfilehash: f67bb76e1d964dd246be16870a7c76591eb1e7d6
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6656738"
---
# <a name="get-package-flights-for-an-app"></a><span data-ttu-id="3a3b9-104">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="3a3b9-104">Get package flights for an app</span></span>

<span data-ttu-id="3a3b9-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, Flight-Pakete für eine app aufgelistet, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-105">Use this method in the Microsoft Store submission API to list the package flights for an app that is registered to your Partner Center account.</span></span> <span data-ttu-id="3a3b9-106">Weitere Informationen zu Flight-Paketen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="3a3b9-106">For more information about package flights, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a3b9-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3a3b9-107">Prerequisites</span></span>

<span data-ttu-id="3a3b9-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="3a3b9-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="3a3b9-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="3a3b9-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="3a3b9-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="3a3b9-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="3a3b9-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-113">Request</span></span>

<span data-ttu-id="3a3b9-114">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-114">This method has the following syntax.</span></span> <span data-ttu-id="3a3b9-115">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-115">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="3a3b9-116">Methode</span><span class="sxs-lookup"><span data-stu-id="3a3b9-116">Method</span></span> | <span data-ttu-id="3a3b9-117">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="3a3b9-117">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="3a3b9-118">GET</span><span class="sxs-lookup"><span data-stu-id="3a3b9-118">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/listflights``` |


### <a name="request-header"></a><span data-ttu-id="3a3b9-119">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="3a3b9-119">Request header</span></span>

| <span data-ttu-id="3a3b9-120">Header</span><span class="sxs-lookup"><span data-stu-id="3a3b9-120">Header</span></span>        | <span data-ttu-id="3a3b9-121">Typ</span><span class="sxs-lookup"><span data-stu-id="3a3b9-121">Type</span></span>   | <span data-ttu-id="3a3b9-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-122">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="3a3b9-123">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-123">Authorization</span></span> | <span data-ttu-id="3a3b9-124">String</span><span class="sxs-lookup"><span data-stu-id="3a3b9-124">string</span></span> | <span data-ttu-id="3a3b9-125">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-125">Required.</span></span> <span data-ttu-id="3a3b9-126">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-126">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="3a3b9-127">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="3a3b9-127">Request parameters</span></span>

|  <span data-ttu-id="3a3b9-128">Name</span><span class="sxs-lookup"><span data-stu-id="3a3b9-128">Name</span></span>  |  <span data-ttu-id="3a3b9-129">Typ</span><span class="sxs-lookup"><span data-stu-id="3a3b9-129">Type</span></span>  |  <span data-ttu-id="3a3b9-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-130">Description</span></span>  |  <span data-ttu-id="3a3b9-131">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="3a3b9-131">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="3a3b9-132">applicationId</span><span class="sxs-lookup"><span data-stu-id="3a3b9-132">applicationId</span></span>  |  <span data-ttu-id="3a3b9-133">string</span><span class="sxs-lookup"><span data-stu-id="3a3b9-133">string</span></span>  |  <span data-ttu-id="3a3b9-134">Die Store-ID der App, für die Flight-Pakete abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-134">The Store ID of the app for which you want to retrieve the package flights.</span></span> <span data-ttu-id="3a3b9-135">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="3a3b9-135">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |  <span data-ttu-id="3a3b9-136">Ja</span><span class="sxs-lookup"><span data-stu-id="3a3b9-136">Yes</span></span>  |
|  <span data-ttu-id="3a3b9-137">top</span><span class="sxs-lookup"><span data-stu-id="3a3b9-137">top</span></span>  |  <span data-ttu-id="3a3b9-138">int</span><span class="sxs-lookup"><span data-stu-id="3a3b9-138">int</span></span>  |  <span data-ttu-id="3a3b9-139">Die Anzahl von Elementen, die in der Anforderung zurückgegeben werden sollen (d.h. die Anzahl der zurückzugebenden Flight-Pakete).</span><span class="sxs-lookup"><span data-stu-id="3a3b9-139">The number of items to return in the request (that is, the number of package flights to return).</span></span> <span data-ttu-id="3a3b9-140">Wenn Ihr Konto über mehr Flight-Pakete als der Wert verfügt, den Sie in der Abfrage festlegen, enthält der Antworttext einen relativen URI-Pfad, den Sie an die URI der Methode anfügen können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-140">If your account has more package flights than the value you specify in the query, the response body includes a relative URI path that you can append to the method URI to request the next page of data.</span></span>  |  <span data-ttu-id="3a3b9-141">Nein</span><span class="sxs-lookup"><span data-stu-id="3a3b9-141">No</span></span>  |
|  <span data-ttu-id="3a3b9-142">skip</span><span class="sxs-lookup"><span data-stu-id="3a3b9-142">skip</span></span>  |  <span data-ttu-id="3a3b9-143">int</span><span class="sxs-lookup"><span data-stu-id="3a3b9-143">int</span></span>  |  <span data-ttu-id="3a3b9-144">Die Anzahl der Elemente, die in der Abfrage umgangen werden sollen, bevor die verbleibenden Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-144">The number of items to bypass in the query before returning the remaining items.</span></span> <span data-ttu-id="3a3b9-145">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-145">Use this parameter to page through data sets.</span></span> <span data-ttu-id="3a3b9-146">Zum Beispiel werden bei top=10 und skip=0 die Elemente 1 bis 10 abgerufen, bei top=10 und skip=10 die Elemente 11 bis 20 und so weiter.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-146">For example, top=10 and skip=0 retrieves items 1 through 10, top=10 and skip=10 retrieves items 11 through 20, and so on.</span></span>  |  <span data-ttu-id="3a3b9-147">Nein</span><span class="sxs-lookup"><span data-stu-id="3a3b9-147">No</span></span>  |


### <a name="request-body"></a><span data-ttu-id="3a3b9-148">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="3a3b9-148">Request body</span></span>

<span data-ttu-id="3a3b9-149">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-149">Do not provide a request body for this method.</span></span>

### <a name="request-examples"></a><span data-ttu-id="3a3b9-150">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="3a3b9-150">Request examples</span></span>

<span data-ttu-id="3a3b9-151">Im folgenden Beispiel wird veranschaulicht, wie alle Flight-Pakete für eine App aufgelistet werden können.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-151">The following example demonstrates how to list all the package flights for an app.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/listflights HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="3a3b9-152">Im folgenden Beispiel wird veranschaulicht, wie das erste Flight-Paket für eine App aufgelistet wird.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-152">The following example demonstrates how to list the first package flight for an app.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/listflights?top=1 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="3a3b9-153">Antwort</span><span class="sxs-lookup"><span data-stu-id="3a3b9-153">Response</span></span>

<span data-ttu-id="3a3b9-154">Das folgende Beispiel zeigt einen JSON-Antworttext, der von einer erfolgreichen Anforderung für das erste Flight-Paket für eine App mit insgesamt drei Flight-Paketen zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-154">The following example demonstrates the JSON response body returned by a successful request for the first package flight for an app with three total package flights.</span></span> <span data-ttu-id="3a3b9-155">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-155">For more details about the values in the response body, see the following section.</span></span>

```json
{
  "value": [
    {
      "flightId": "7bfc11d5-f710-47c5-8a98-e04bb5aad310",
      "friendlyName": "myflight",
      "lastPublishedFlightSubmission": {
        "id": "1152921504621086517",
        "resourceLocation": "flights/7bfc11d5-f710-47c5-8a98-e04bb5aad310/submissions/1152921504621086517"
      },
      "pendingFlightSubmission": {
        "id": "1152921504621215786",
        "resourceLocation": "flights/7bfc11d5-f710-47c5-8a98-e04bb5aad310/submissions/1152921504621215786"
      },
      "groupIds": [
        "1152921504606962205"
      ],
      "rankHigherThan": "Non-flighted submission"
    }
  ],
  "totalCount": 3
}
```

### <a name="response-body"></a><span data-ttu-id="3a3b9-156">Antworttext</span><span class="sxs-lookup"><span data-stu-id="3a3b9-156">Response body</span></span>

| <span data-ttu-id="3a3b9-157">Wert</span><span class="sxs-lookup"><span data-stu-id="3a3b9-157">Value</span></span>      | <span data-ttu-id="3a3b9-158">Typ</span><span class="sxs-lookup"><span data-stu-id="3a3b9-158">Type</span></span>   | <span data-ttu-id="3a3b9-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-159">Description</span></span>       |
|------------|--------|---------------------|
| @nextLink  | <span data-ttu-id="3a3b9-160">String</span><span class="sxs-lookup"><span data-stu-id="3a3b9-160">string</span></span> | <span data-ttu-id="3a3b9-161">Wenn weitere Datenseiten vorhanden sind, enthält diese Zeichenfolge einen relativen Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` zum Anfordern der nächsten Datenseite anfügen können.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-161">If there are additional pages of data, this string contains a relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to request the next page of data.</span></span> <span data-ttu-id="3a3b9-162">Wenn beispielsweise der Parameter *top* des anfänglichen Anforderungstexts auf 2festgelegt ist, für die App jedoch 4Flight-Pakete vorhanden sind, enthält der Antworttext den @nextLink-Wert ```applications/{applicationid}/listflights/?skip=2&top=2```, der angibt, dass Sie ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/listflights/?skip=2&top=2``` aufrufen können, um die nächsten 2Flight-Pakete anzufordern.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-162">For example, if the *top* parameter of the initial request body is set to 2 but there are 4 package flights for the app, the response body will include a @nextLink value of ```applications/{applicationid}/listflights/?skip=2&top=2```, which indicates that you can call ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/listflights/?skip=2&top=2``` to request the next 2 package flights.</span></span> |
| <span data-ttu-id="3a3b9-163">value</span><span class="sxs-lookup"><span data-stu-id="3a3b9-163">value</span></span>      | <span data-ttu-id="3a3b9-164">array</span><span class="sxs-lookup"><span data-stu-id="3a3b9-164">array</span></span>  | <span data-ttu-id="3a3b9-165">Ein Array von Objekten, die Informationen zu Flight-Paketen für die angegebene App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-165">An array of objects that provide information about package flights for the specified app.</span></span> <span data-ttu-id="3a3b9-166">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unter [Flight-Ressource](get-app-data.md#flight-object).</span><span class="sxs-lookup"><span data-stu-id="3a3b9-166">For more information about the data in each object, see [Flight resource](get-app-data.md#flight-object).</span></span>               |
| <span data-ttu-id="3a3b9-167">totalCount</span><span class="sxs-lookup"><span data-stu-id="3a3b9-167">totalCount</span></span> | <span data-ttu-id="3a3b9-168">int</span><span class="sxs-lookup"><span data-stu-id="3a3b9-168">int</span></span>    | <span data-ttu-id="3a3b9-169">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage (d.h. die Gesamtanzahl der Flight-Pakete für die angegebene App).</span><span class="sxs-lookup"><span data-stu-id="3a3b9-169">The total number of rows in the data result for the query (that is, the total number of package flights for the specified app).</span></span>   |


## <a name="error-codes"></a><span data-ttu-id="3a3b9-170">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3a3b9-170">Error codes</span></span>

<span data-ttu-id="3a3b9-171">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-171">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="3a3b9-172">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="3a3b9-172">Error code</span></span> |  <span data-ttu-id="3a3b9-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a3b9-173">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="3a3b9-174">404</span><span class="sxs-lookup"><span data-stu-id="3a3b9-174">404</span></span>  | <span data-ttu-id="3a3b9-175">Es wurden keine Flight-Pakete gefunden.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-175">No package flights were found.</span></span> |
| <span data-ttu-id="3a3b9-176">409</span><span class="sxs-lookup"><span data-stu-id="3a3b9-176">409</span></span>  | <span data-ttu-id="3a3b9-177">Die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="3a3b9-177">The app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="3a3b9-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3a3b9-178">Related topics</span></span>

* [<span data-ttu-id="3a3b9-179">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="3a3b9-179">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="3a3b9-180">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="3a3b9-180">Get all apps</span></span>](get-all-apps.md)
* [<span data-ttu-id="3a3b9-181">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="3a3b9-181">Get an app</span></span>](get-an-app.md)
* [<span data-ttu-id="3a3b9-182">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="3a3b9-182">Get add-ons for an app</span></span>](get-add-ons-for-an-app.md)
