---
ms.assetid: E59FB6FE-5318-46DF-B050-73F599C3972A
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über in-app-Einkäufe für eine app abzurufen, die in Ihrem Partner Center registriert ist.
title: Abrufen von Add-Ons für eine App
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-Ons, In-App-Produkte, IAPs
ms.localizationpriority: medium
ms.openlocfilehash: ec065eef5d411e35515837b169fd57d71e4ef6ac
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7718471"
---
# <a name="get-add-ons-for-an-app"></a><span data-ttu-id="9d666-104">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="9d666-104">Get add-ons for an app</span></span>

<span data-ttu-id="9d666-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Auflisten der Add-ons für eine app, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="9d666-105">Use this method in the Microsoft Store submission API to list the add-ons for an app that is registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9d666-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9d666-106">Prerequisites</span></span>

<span data-ttu-id="9d666-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="9d666-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="9d666-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="9d666-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="9d666-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9d666-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="9d666-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="9d666-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="9d666-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="9d666-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="9d666-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="9d666-112">Request</span></span>

<span data-ttu-id="9d666-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="9d666-113">This method has the following syntax.</span></span> <span data-ttu-id="9d666-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="9d666-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="9d666-115">Methode</span><span class="sxs-lookup"><span data-stu-id="9d666-115">Method</span></span> | <span data-ttu-id="9d666-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="9d666-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="9d666-117">GET</span><span class="sxs-lookup"><span data-stu-id="9d666-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/listinappproducts``` |


### <a name="request-header"></a><span data-ttu-id="9d666-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="9d666-118">Request header</span></span>

| <span data-ttu-id="9d666-119">Header</span><span class="sxs-lookup"><span data-stu-id="9d666-119">Header</span></span>        | <span data-ttu-id="9d666-120">Typ</span><span class="sxs-lookup"><span data-stu-id="9d666-120">Type</span></span>   | <span data-ttu-id="9d666-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d666-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="9d666-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="9d666-122">Authorization</span></span> | <span data-ttu-id="9d666-123">String</span><span class="sxs-lookup"><span data-stu-id="9d666-123">string</span></span> | <span data-ttu-id="9d666-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9d666-124">Required.</span></span> <span data-ttu-id="9d666-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="9d666-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="9d666-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="9d666-126">Request parameters</span></span>


|  <span data-ttu-id="9d666-127">Name</span><span class="sxs-lookup"><span data-stu-id="9d666-127">Name</span></span>  |  <span data-ttu-id="9d666-128">Typ</span><span class="sxs-lookup"><span data-stu-id="9d666-128">Type</span></span>  |  <span data-ttu-id="9d666-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d666-129">Description</span></span>  |  <span data-ttu-id="9d666-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9d666-130">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="9d666-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="9d666-131">applicationId</span></span>  |  <span data-ttu-id="9d666-132">string</span><span class="sxs-lookup"><span data-stu-id="9d666-132">string</span></span>  |  <span data-ttu-id="9d666-133">Die Store-ID der App, für die Sie Add-Ons abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="9d666-133">The Store ID of the app for which you want to retrieve the add-ons.</span></span> <span data-ttu-id="9d666-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="9d666-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |  <span data-ttu-id="9d666-135">Ja</span><span class="sxs-lookup"><span data-stu-id="9d666-135">Yes</span></span>  |
|  <span data-ttu-id="9d666-136">top</span><span class="sxs-lookup"><span data-stu-id="9d666-136">top</span></span>  |  <span data-ttu-id="9d666-137">int</span><span class="sxs-lookup"><span data-stu-id="9d666-137">int</span></span>  |  <span data-ttu-id="9d666-138">Die Anzahl von Elementen, die in der Anforderung zurückgegeben werden sollen (d.h. die Anzahl der zurückzugebenden-Add-Ons).</span><span class="sxs-lookup"><span data-stu-id="9d666-138">The number of items to return in the request (that is, the number of add-ons to return).</span></span> <span data-ttu-id="9d666-139">Wenn die App mehr Add-Ons als der Wert verfügt, den Sie in der Abfrage festlegen, enthält der Antworttext einen relativen URI-Pfad, den Sie an den URI der Methode anfügen können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="9d666-139">If the app has more add-ons than the value you specify in the query, the response body includes a relative URI path that you can append to the method URI to request the next page of data.</span></span>  |  <span data-ttu-id="9d666-140">Nein</span><span class="sxs-lookup"><span data-stu-id="9d666-140">No</span></span>  |
|  <span data-ttu-id="9d666-141">skip</span><span class="sxs-lookup"><span data-stu-id="9d666-141">skip</span></span> |  <span data-ttu-id="9d666-142">int</span><span class="sxs-lookup"><span data-stu-id="9d666-142">int</span></span>  | <span data-ttu-id="9d666-143">Die Anzahl der Elemente, die in der Abfrage umgangen werden sollen, bevor die verbleibenden Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9d666-143">The number of items to bypass in the query before returning the remaining items.</span></span> <span data-ttu-id="9d666-144">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="9d666-144">Use this parameter to page through data sets.</span></span> <span data-ttu-id="9d666-145">Zum Beispiel werden bei top=10 und skip=0 die Elemente 1 bis 10 abgerufen, bei top=10 und skip=10 die Elemente 11 bis 20 und so weiter.</span><span class="sxs-lookup"><span data-stu-id="9d666-145">For example, top=10 and skip=0 retrieves items 1 through 10, top=10 and skip=10 retrieves items 11 through 20, and so on.</span></span>   |  <span data-ttu-id="9d666-146">Nein</span><span class="sxs-lookup"><span data-stu-id="9d666-146">No</span></span>  |


### <a name="request-body"></a><span data-ttu-id="9d666-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="9d666-147">Request body</span></span>

<span data-ttu-id="9d666-148">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="9d666-148">Do not provide a request body for this method.</span></span>

### <a name="request-examples"></a><span data-ttu-id="9d666-149">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="9d666-149">Request examples</span></span>

<span data-ttu-id="9d666-150">Im folgenden Beispiel wird veranschaulicht, wie alle Add-Ons für eine App aufgelistet werden können.</span><span class="sxs-lookup"><span data-stu-id="9d666-150">The following example demonstrates how to list all the add-ons for an app.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/listinappproducts HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="9d666-151">Im folgenden Beispiel wird veranschaulicht, wie die ersten 10 Add-Ons für eine App aufgelistet werden können.</span><span class="sxs-lookup"><span data-stu-id="9d666-151">The following example demonstrates how to list the first 10 add-ons for an app.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/listinappproducts?top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="9d666-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="9d666-152">Response</span></span>

<span data-ttu-id="9d666-153">Das folgende Beispiel veranschaulicht den JSON-Antworttext, der von einer erfolgreichen Anforderung für die ersten 10 Add-Ons für eine App mit insgesamt 53 Add-Ons zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="9d666-153">The following example demonstrates the JSON response body returned by a successful request for the first 10 add-ons for an app with 53 total add-ons.</span></span> <span data-ttu-id="9d666-154">Aus Platzgründen sind in diesem Beispiel nur die Daten für die ersten drei Add-Ons dargestellt, die von der Anforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9d666-154">For brevity, this example only shows the data for the first three add-ons returned by the request.</span></span> <span data-ttu-id="9d666-155">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="9d666-155">For more details about the values in the response body, see the following section.</span></span>

```json
{
  "@nextLink": "applications/9NBLGGH4R315/listinappproducts/?skip=10&top=10",
  "value": [
    {
      "inAppProductId": "9NBLGGH4TNMP"
    },
    {
      "inAppProductId": "9NBLGGH4TNMN"
    },
    {
      "inAppProductId": "9NBLGGH4TNNR"
    },
    // Next 7 add-ons  are omitted for brevity ...
  ],
  "totalCount": 53
}
```

### <a name="response-body"></a><span data-ttu-id="9d666-156">Antworttext</span><span class="sxs-lookup"><span data-stu-id="9d666-156">Response body</span></span>

| <span data-ttu-id="9d666-157">Wert</span><span class="sxs-lookup"><span data-stu-id="9d666-157">Value</span></span>      | <span data-ttu-id="9d666-158">Typ</span><span class="sxs-lookup"><span data-stu-id="9d666-158">Type</span></span>   | <span data-ttu-id="9d666-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d666-159">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @nextLink  | <span data-ttu-id="9d666-160">String</span><span class="sxs-lookup"><span data-stu-id="9d666-160">string</span></span> | <span data-ttu-id="9d666-161">Wenn weitere Datenseiten vorhanden sind, enthält diese Zeichenfolge einen relativen Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` zum Anfordern der nächsten Datenseite anfügen können.</span><span class="sxs-lookup"><span data-stu-id="9d666-161">If there are additional pages of data, this string contains a relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to request the next page of data.</span></span> <span data-ttu-id="9d666-162">Wenn beispielsweise der Parameter *top* des anfänglichen Anforderungstexts auf 10 festgelegt ist, für die App jedoch 50Add-Ons vorhanden sind, enthält der Antworttext den @nextLink-Wert ```applications/{applicationid}/listinappproducts/?skip=10&top=10```, der angibt, dass Sie ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/listinappproducts/?skip=10&top=10``` aufrufen können, um die nächsten 10Add-Ons anzufordern.</span><span class="sxs-lookup"><span data-stu-id="9d666-162">For example, if the *top* parameter of the initial request body is set to 10 but there are 50 add-ons for the app, the response body will include a @nextLink value of ```applications/{applicationid}/listinappproducts/?skip=10&top=10```, which indicates that you can call ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/listinappproducts/?skip=10&top=10``` to request the next 10 add-ons.</span></span> |
| <span data-ttu-id="9d666-163">value</span><span class="sxs-lookup"><span data-stu-id="9d666-163">value</span></span>      | <span data-ttu-id="9d666-164">array</span><span class="sxs-lookup"><span data-stu-id="9d666-164">array</span></span>  | <span data-ttu-id="9d666-165">Ein Array von Objekten, die die Store-ID für jedes Add-On für die angegebene App auflisten.</span><span class="sxs-lookup"><span data-stu-id="9d666-165">An array of objects that list the Store ID of each add-on for the specified app.</span></span> <span data-ttu-id="9d666-166">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unter [-Add-On-Ressource](get-app-data.md#add-on-object).</span><span class="sxs-lookup"><span data-stu-id="9d666-166">For more information about the data in each object, see [add-on resource](get-app-data.md#add-on-object).</span></span>                                                                                                                           |
| <span data-ttu-id="9d666-167">totalCount</span><span class="sxs-lookup"><span data-stu-id="9d666-167">totalCount</span></span> | <span data-ttu-id="9d666-168">int</span><span class="sxs-lookup"><span data-stu-id="9d666-168">int</span></span>    | <span data-ttu-id="9d666-169">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage (d.h. die Gesamtanzahl der Add-Ons für die angegebene App).</span><span class="sxs-lookup"><span data-stu-id="9d666-169">The total number of rows in the data result for the query (that is, the total number of add-ons for the specified app).</span></span>    |


## <a name="error-codes"></a><span data-ttu-id="9d666-170">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="9d666-170">Error codes</span></span>

<span data-ttu-id="9d666-171">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="9d666-171">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="9d666-172">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="9d666-172">Error code</span></span> |  <span data-ttu-id="9d666-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9d666-173">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="9d666-174">404</span><span class="sxs-lookup"><span data-stu-id="9d666-174">404</span></span>  | <span data-ttu-id="9d666-175">Es wurden keine Add-Ons gefunden.</span><span class="sxs-lookup"><span data-stu-id="9d666-175">No add-ons were found.</span></span> |
| <span data-ttu-id="9d666-176">409</span><span class="sxs-lookup"><span data-stu-id="9d666-176">409</span></span>  | <span data-ttu-id="9d666-177">Die Add-ons verwenden die Partner Center-Funktionen, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="9d666-177">The add-ons use Partner Center features that are [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="9d666-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9d666-178">Related topics</span></span>

* [<span data-ttu-id="9d666-179">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="9d666-179">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="9d666-180">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="9d666-180">Get all apps</span></span>](get-all-apps.md)
* [<span data-ttu-id="9d666-181">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="9d666-181">Get an app</span></span>](get-an-app.md)
* [<span data-ttu-id="9d666-182">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="9d666-182">Get package flights for an app</span></span>](get-flights-for-an-app.md)
