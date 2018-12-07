---
ms.assetid: 2BCFF687-DC12-49CA-97E4-ACEC72BFCD9B
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über alle apps abzurufen, die für Ihr Partner Center-Konto registriert wurden.
title: Abrufen aller Apps
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Apps
ms.localizationpriority: medium
ms.openlocfilehash: 5c909e707d25e4add534ce89319abe71c2557b59
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8782554"
---
# <a name="get-all-apps"></a><span data-ttu-id="474c5-104">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="474c5-104">Get all apps</span></span>


<span data-ttu-id="474c5-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für alle apps, die für Ihr Partner Center-Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="474c5-105">Use this method in the Microsoft Store submission API to retrieve data for all the apps that are registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="474c5-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="474c5-106">Prerequisites</span></span>

<span data-ttu-id="474c5-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="474c5-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="474c5-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="474c5-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="474c5-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="474c5-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="474c5-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="474c5-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="474c5-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="474c5-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="474c5-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="474c5-112">Request</span></span>

<span data-ttu-id="474c5-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="474c5-113">This method has the following syntax.</span></span> <span data-ttu-id="474c5-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="474c5-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="474c5-115">Methode</span><span class="sxs-lookup"><span data-stu-id="474c5-115">Method</span></span> | <span data-ttu-id="474c5-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="474c5-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="474c5-117">GET</span><span class="sxs-lookup"><span data-stu-id="474c5-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications``` |


### <a name="request-header"></a><span data-ttu-id="474c5-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="474c5-118">Request header</span></span>

| <span data-ttu-id="474c5-119">Header</span><span class="sxs-lookup"><span data-stu-id="474c5-119">Header</span></span>        | <span data-ttu-id="474c5-120">Typ</span><span class="sxs-lookup"><span data-stu-id="474c5-120">Type</span></span>   | <span data-ttu-id="474c5-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="474c5-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="474c5-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="474c5-122">Authorization</span></span> | <span data-ttu-id="474c5-123">String</span><span class="sxs-lookup"><span data-stu-id="474c5-123">string</span></span> | <span data-ttu-id="474c5-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="474c5-124">Required.</span></span> <span data-ttu-id="474c5-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="474c5-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="474c5-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="474c5-126">Request parameters</span></span>

<span data-ttu-id="474c5-127">Alle Anforderungsparameter sind optional für diese Methode.</span><span class="sxs-lookup"><span data-stu-id="474c5-127">All request parameters are optional for this method.</span></span> <span data-ttu-id="474c5-128">Wenn Sie diese Methode ohne Parameter aufrufen, enthält die Antwort Daten für alle Apps, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="474c5-128">If you call this method without parameters, the response contains data for all apps that are registered to your account.</span></span>

|  <span data-ttu-id="474c5-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="474c5-129">Parameter</span></span>  |  <span data-ttu-id="474c5-130">Typ</span><span class="sxs-lookup"><span data-stu-id="474c5-130">Type</span></span>  |  <span data-ttu-id="474c5-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="474c5-131">Description</span></span>  |  <span data-ttu-id="474c5-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="474c5-132">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="474c5-133">top</span><span class="sxs-lookup"><span data-stu-id="474c5-133">top</span></span>  |  <span data-ttu-id="474c5-134">int</span><span class="sxs-lookup"><span data-stu-id="474c5-134">int</span></span>  |  <span data-ttu-id="474c5-135">Die Anzahl von Elementen, die in der Anforderung zurückgegeben werden sollen (d.h. die Anzahl der zurückzugebenden Apps).</span><span class="sxs-lookup"><span data-stu-id="474c5-135">The number of items to return in the request (that is, the number of apps to return).</span></span> <span data-ttu-id="474c5-136">Wenn Ihr Konto über mehr Apps als der Wert verfügt, den Sie in der Abfrage festlegen, enthält der Antworttext einen relativen URI-Pfad, den Sie an den URI der Methode anfügen können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="474c5-136">If your account has more apps than the value you specify in the query, the response body includes a relative URI path that you can append to the method URI to request the next page of data.</span></span>  |  <span data-ttu-id="474c5-137">Nein</span><span class="sxs-lookup"><span data-stu-id="474c5-137">No</span></span>  |
|  <span data-ttu-id="474c5-138">skip</span><span class="sxs-lookup"><span data-stu-id="474c5-138">skip</span></span>  |  <span data-ttu-id="474c5-139">int</span><span class="sxs-lookup"><span data-stu-id="474c5-139">int</span></span>  |  <span data-ttu-id="474c5-140">Die Anzahl der Elemente, die in der Abfrage umgangen werden sollen, bevor die verbleibenden Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="474c5-140">The number of items to bypass in the query before returning the remaining items.</span></span> <span data-ttu-id="474c5-141">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="474c5-141">Use this parameter to page through data sets.</span></span> <span data-ttu-id="474c5-142">Zum Beispiel werden bei top=10 und skip=0 die Elemente 1 bis 10 abgerufen, bei top=10 und skip=10 die Elemente 11 bis 20 und so weiter.</span><span class="sxs-lookup"><span data-stu-id="474c5-142">For example, top=10 and skip=0 retrieves items 1 through 10, top=10 and skip=10 retrieves items 11 through 20, and so on.</span></span>  |  <span data-ttu-id="474c5-143">Nein</span><span class="sxs-lookup"><span data-stu-id="474c5-143">No</span></span>  |


### <a name="request-body"></a><span data-ttu-id="474c5-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="474c5-144">Request body</span></span>

<span data-ttu-id="474c5-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="474c5-145">Do not provide a request body for this method.</span></span>

### <a name="request-examples"></a><span data-ttu-id="474c5-146">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="474c5-146">Request examples</span></span>

<span data-ttu-id="474c5-147">Im folgenden Beispiel wird veranschaulicht, wie Informationen über alle Apps abgerufen werden können, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="474c5-147">The following example demonstrates how to retrieve information about all the apps that are registered to your account.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="474c5-148">Im folgenden Beispiel wird veranschaulicht, wie die ersten 10 Apps abgerufen werden können, die für Ihr Konto registriert sind.</span><span class="sxs-lookup"><span data-stu-id="474c5-148">The following example demonstrates how to retrieve the first 10 apps that are registered to your account.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="474c5-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="474c5-149">Response</span></span>

<span data-ttu-id="474c5-150">Im folgenden Beispiel wird der JSON-Antworttext veranschaulicht, der von einer erfolgreichen Anforderung für die ersten 10 Apps zurückgegeben wird, die für ein Entwicklerkonto mit insgesamt 21 Apps registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="474c5-150">The following example demonstrates the JSON response body returned by a successful request for the first 10 apps that are registered to a developer account with 21 total apps.</span></span> <span data-ttu-id="474c5-151">Aus Platzgründen sind in diesem Beispiel nur die Daten für die ersten beiden Apps dargestellt, die von der Anforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="474c5-151">For brevity, this example only shows the data for the first two apps returned by the request.</span></span> <span data-ttu-id="474c5-152">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="474c5-152">For more details about the values in the response body, see the following section.</span></span>

```json
{
  "@nextLink": "applications?skip=10&top=10",
  "value": [
    {
      "id": "9NBLGGH4R315",
      "primaryName": "Contoso sample app",
      "packageFamilyName": "5224ContosoDeveloper.ContosoSampleApp_ng6try80pwt52",
      "packageIdentityName": "5224ContosoDeveloper.ContosoSampleApp",
      "publisherName": "CN=…",
      "firstPublishedDate": "2016-03-11T01:32:11.0747851Z",
      "pendingApplicationSubmission": {
        "id": "1152921504621134883",
        "resourceLocation": "applications/9NBLGGH4R315/submissions/1152921504621134883"
      }
    },
    {
      "id": "9NBLGGH29DM8",
      "primaryName": "Contoso sample app 2",
      "packageFamilyName": "5224ContosoDeveloper.ContosoSampleApp2_ng6try80pwt52",
      "packageIdentityName": "5224ContosoDeveloper.ContosoSampleApp2",
      "publisherName": "CN=…",
      "firstPublishedDate": "2016-03-12T01:49:11.0747851Z",
      "lastPublishedApplicationSubmission": {
        "id": "1152921504621225621",
        "resourceLocation": "applications/9NBLGGH29DM8/submissions/1152921504621225621"
      }
      // Next 8 apps are omitted for brevity ...
    }
  ],
  "totalCount": 21
}
```

### <a name="response-body"></a><span data-ttu-id="474c5-153">Antworttext</span><span class="sxs-lookup"><span data-stu-id="474c5-153">Response body</span></span>

| <span data-ttu-id="474c5-154">Wert</span><span class="sxs-lookup"><span data-stu-id="474c5-154">Value</span></span>      | <span data-ttu-id="474c5-155">Typ</span><span class="sxs-lookup"><span data-stu-id="474c5-155">Type</span></span>   | <span data-ttu-id="474c5-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="474c5-156">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="474c5-157">value</span><span class="sxs-lookup"><span data-stu-id="474c5-157">value</span></span>      | <span data-ttu-id="474c5-158">Array</span><span class="sxs-lookup"><span data-stu-id="474c5-158">array</span></span>  | <span data-ttu-id="474c5-159">Ein Array von Objekten, die Informationen zu jeder App enthalten, die für Ihr Konto registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="474c5-159">An array of objects that contain information about each app that is registered to your account.</span></span> <span data-ttu-id="474c5-160">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unter [Anwendungsressource](get-app-data.md#application_object).</span><span class="sxs-lookup"><span data-stu-id="474c5-160">For more information about the data in each object, see [Application resource](get-app-data.md#application_object).</span></span>                                                                                                                           |
| @nextLink  | <span data-ttu-id="474c5-161">String</span><span class="sxs-lookup"><span data-stu-id="474c5-161">string</span></span> | <span data-ttu-id="474c5-162">Wenn weitere Datenseiten vorhanden sind, enthält diese Zeichenfolge einen relativen Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` zum Anfordern der nächsten Datenseite anfügen können.</span><span class="sxs-lookup"><span data-stu-id="474c5-162">If there are additional pages of data, this string contains a relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to request the next page of data.</span></span> <span data-ttu-id="474c5-163">Wenn beispielsweise der Parameter *top* des anfänglichen Anforderungstexts auf 10 festgelegt ist, für Ihr Konto jedoch 20Apps registriert wurden, enthält der Antworttext den @nextLink-Wert ```applications?skip=10&top=10```, der angibt, dass Sie ```https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=10&top=10``` aufrufen können, um die nächsten 10 Apps anzufordern.</span><span class="sxs-lookup"><span data-stu-id="474c5-163">For example, if the *top* parameter of the initial request body is set to 10 but there are 20 apps registered to your account, the response body will include a @nextLink value of ```applications?skip=10&top=10```, which indicates that you can call ```https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=10&top=10``` to request the next 10 apps.</span></span> |
| <span data-ttu-id="474c5-164">totalCount</span><span class="sxs-lookup"><span data-stu-id="474c5-164">totalCount</span></span> | <span data-ttu-id="474c5-165">int</span><span class="sxs-lookup"><span data-stu-id="474c5-165">int</span></span>    | <span data-ttu-id="474c5-166">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage (d.h. die Gesamtanzahl von Apps, die für Ihr Konto registriert wurden).</span><span class="sxs-lookup"><span data-stu-id="474c5-166">The total number of rows in the data result for the query (that is, the total number of apps that are registered to your account).</span></span>                                                |


## <a name="error-codes"></a><span data-ttu-id="474c5-167">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="474c5-167">Error codes</span></span>

<span data-ttu-id="474c5-168">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="474c5-168">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="474c5-169">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="474c5-169">Error code</span></span> |  <span data-ttu-id="474c5-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="474c5-170">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="474c5-171">404</span><span class="sxs-lookup"><span data-stu-id="474c5-171">404</span></span>  | <span data-ttu-id="474c5-172">Es wurden keine Apps gefunden.</span><span class="sxs-lookup"><span data-stu-id="474c5-172">No apps were found.</span></span> |
| <span data-ttu-id="474c5-173">409</span><span class="sxs-lookup"><span data-stu-id="474c5-173">409</span></span>  | <span data-ttu-id="474c5-174">Die apps verwenden Sie Partner Center-Funktionen, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="474c5-174">The apps use Partner Center features that are [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="474c5-175">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="474c5-175">Related topics</span></span>

* [<span data-ttu-id="474c5-176">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="474c5-176">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="474c5-177">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="474c5-177">Get an app</span></span>](get-an-app.md)
* [<span data-ttu-id="474c5-178">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="474c5-178">Get package flights for an app</span></span>](get-flights-for-an-app.md)
* [<span data-ttu-id="474c5-179">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="474c5-179">Get add-ons for an app</span></span>](get-add-ons-for-an-app.md)
