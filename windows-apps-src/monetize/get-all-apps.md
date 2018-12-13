---
ms.assetid: 2BCFF687-DC12-49CA-97E4-ACEC72BFCD9B
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über alle apps abzurufen, die für Ihr Partner Center-Konto registriert wurden.
title: Abrufen aller Apps
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Apps
ms.localizationpriority: medium
ms.openlocfilehash: 267e1d4de3917ae332cdfe15309f3871ef7b6647
ms.sourcegitcommit: dcff44885956094e0a7661b69d54a8983921ce62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "8968564"
---
# <a name="get-all-apps"></a><span data-ttu-id="af105-104">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="af105-104">Get all apps</span></span>


<span data-ttu-id="af105-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für apps, die für Ihr Partner Center-Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="af105-105">Use this method in the Microsoft Store submission API to retrieve data for the apps that are registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af105-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="af105-106">Prerequisites</span></span>

<span data-ttu-id="af105-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="af105-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="af105-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="af105-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="af105-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af105-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="af105-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="af105-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="af105-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="af105-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="af105-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="af105-112">Request</span></span>

<span data-ttu-id="af105-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="af105-113">This method has the following syntax.</span></span> <span data-ttu-id="af105-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="af105-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="af105-115">Methode</span><span class="sxs-lookup"><span data-stu-id="af105-115">Method</span></span> | <span data-ttu-id="af105-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="af105-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="af105-117">GET</span><span class="sxs-lookup"><span data-stu-id="af105-117">GET</span></span>    | `https://manage.devcenter.microsoft.com/v1.0/my/applications` |


### <a name="request-header"></a><span data-ttu-id="af105-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="af105-118">Request header</span></span>

| <span data-ttu-id="af105-119">Header</span><span class="sxs-lookup"><span data-stu-id="af105-119">Header</span></span>        | <span data-ttu-id="af105-120">Typ</span><span class="sxs-lookup"><span data-stu-id="af105-120">Type</span></span>   | <span data-ttu-id="af105-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af105-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="af105-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="af105-122">Authorization</span></span> | <span data-ttu-id="af105-123">String</span><span class="sxs-lookup"><span data-stu-id="af105-123">string</span></span> | <span data-ttu-id="af105-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af105-124">Required.</span></span> <span data-ttu-id="af105-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="af105-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="af105-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="af105-126">Request parameters</span></span>

<span data-ttu-id="af105-127">Alle Anforderungsparameter sind optional für diese Methode.</span><span class="sxs-lookup"><span data-stu-id="af105-127">All request parameters are optional for this method.</span></span> <span data-ttu-id="af105-128">Wenn Sie diese Methode ohne Parameter aufrufen, enthält die Antwort Daten für die ersten 10 apps, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="af105-128">If you call this method without parameters, the response contains data for the first 10 apps that are registered to your account.</span></span>

|  <span data-ttu-id="af105-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="af105-129">Parameter</span></span>  |  <span data-ttu-id="af105-130">Typ</span><span class="sxs-lookup"><span data-stu-id="af105-130">Type</span></span>  |  <span data-ttu-id="af105-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af105-131">Description</span></span>  |  <span data-ttu-id="af105-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="af105-132">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="af105-133">top</span><span class="sxs-lookup"><span data-stu-id="af105-133">top</span></span>  |  <span data-ttu-id="af105-134">int</span><span class="sxs-lookup"><span data-stu-id="af105-134">int</span></span>  |  <span data-ttu-id="af105-135">Die Anzahl von Elementen, die in der Anforderung zurückgegeben werden sollen (d.h. die Anzahl der zurückzugebenden Apps).</span><span class="sxs-lookup"><span data-stu-id="af105-135">The number of items to return in the request (that is, the number of apps to return).</span></span> <span data-ttu-id="af105-136">Wenn Ihr Konto über mehr Apps als der Wert verfügt, den Sie in der Abfrage festlegen, enthält der Antworttext einen relativen URI-Pfad, den Sie an den URI der Methode anfügen können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="af105-136">If your account has more apps than the value you specify in the query, the response body includes a relative URI path that you can append to the method URI to request the next page of data.</span></span>  |  <span data-ttu-id="af105-137">Nein</span><span class="sxs-lookup"><span data-stu-id="af105-137">No</span></span>  |
|  <span data-ttu-id="af105-138">skip</span><span class="sxs-lookup"><span data-stu-id="af105-138">skip</span></span>  |  <span data-ttu-id="af105-139">int</span><span class="sxs-lookup"><span data-stu-id="af105-139">int</span></span>  |  <span data-ttu-id="af105-140">Die Anzahl der Elemente, die in der Abfrage umgangen werden sollen, bevor die verbleibenden Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="af105-140">The number of items to bypass in the query before returning the remaining items.</span></span> <span data-ttu-id="af105-141">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="af105-141">Use this parameter to page through data sets.</span></span> <span data-ttu-id="af105-142">Zum Beispiel werden bei top=10 und skip=0 die Elemente 1 bis 10 abgerufen, bei top=10 und skip=10 die Elemente 11 bis 20 und so weiter.</span><span class="sxs-lookup"><span data-stu-id="af105-142">For example, top=10 and skip=0 retrieves items 1 through 10, top=10 and skip=10 retrieves items 11 through 20, and so on.</span></span>  |  <span data-ttu-id="af105-143">Nein</span><span class="sxs-lookup"><span data-stu-id="af105-143">No</span></span>  |


### <a name="request-body"></a><span data-ttu-id="af105-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="af105-144">Request body</span></span>

<span data-ttu-id="af105-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="af105-145">Do not provide a request body for this method.</span></span>

### <a name="request-examples"></a><span data-ttu-id="af105-146">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="af105-146">Request examples</span></span>

<span data-ttu-id="af105-147">Im folgenden Beispiel wird veranschaulicht, wie die ersten 10 Apps abgerufen werden können, die für Ihr Konto registriert sind.</span><span class="sxs-lookup"><span data-stu-id="af105-147">The following example demonstrates how to retrieve the first 10 apps that are registered to your account.</span></span>

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="af105-148">Im folgenden Beispiel wird veranschaulicht, wie Informationen über alle Apps abgerufen werden können, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="af105-148">The following example demonstrates how to retrieve information about all the apps that are registered to your account.</span></span> <span data-ttu-id="af105-149">Rufen Sie zunächst die ersten 10 apps:</span><span class="sxs-lookup"><span data-stu-id="af105-149">First, get the top 10 apps:</span></span>

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="af105-150">Anschließend rekursiv Aufruf `GET https://manage.devcenter.microsoft.com/v1.0/my/{@nextLink}` bis `{@nextlink}` ist null oder nicht vorhanden ist, in der Antwort.</span><span class="sxs-lookup"><span data-stu-id="af105-150">Then recursively call `GET https://manage.devcenter.microsoft.com/v1.0/my/{@nextLink}` until `{@nextlink}` is null or doesn't exist in the response.</span></span> <span data-ttu-id="af105-151">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="af105-151">For example:</span></span>

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=10&top=10 HTTP/1.1
Authorization: Bearer <your access token>
```
  
```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=20&top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=30&top=10 HTTP/1.1
Authorization: Bearer <your access token>
```

<span data-ttu-id="af105-152">Wenn Sie die Gesamtanzahl von apps, die Sie in Ihrem Konto haben bereits kennen, können Sie einfach die Anzahl in der **oberen** Parameter zum Abrufen von Informationen über alle Ihre apps übergeben.</span><span class="sxs-lookup"><span data-stu-id="af105-152">If you already know the total number of apps you have in your account, you can simply pass that number in the **top** parameter to get information about all your apps.</span></span>

```http
GET https://manage.devcenter.microsoft.com/v1.0/my/applications?top=23 HTTP/1.1
Authorization: Bearer <your access token>
```


## <a name="response"></a><span data-ttu-id="af105-153">Antwort</span><span class="sxs-lookup"><span data-stu-id="af105-153">Response</span></span>

<span data-ttu-id="af105-154">Im folgenden Beispiel wird der JSON-Antworttext veranschaulicht, der von einer erfolgreichen Anforderung für die ersten 10 Apps zurückgegeben wird, die für ein Entwicklerkonto mit insgesamt 21 Apps registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="af105-154">The following example demonstrates the JSON response body returned by a successful request for the first 10 apps that are registered to a developer account with 21 total apps.</span></span> <span data-ttu-id="af105-155">Aus Platzgründen sind in diesem Beispiel nur die Daten für die ersten beiden Apps dargestellt, die von der Anforderung zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="af105-155">For brevity, this example only shows the data for the first two apps returned by the request.</span></span> <span data-ttu-id="af105-156">Weitere Informationen zu den Werten im Antworttext finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="af105-156">For more details about the values in the response body, see the following section.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="af105-157">Antworttext</span><span class="sxs-lookup"><span data-stu-id="af105-157">Response body</span></span>

| <span data-ttu-id="af105-158">Wert</span><span class="sxs-lookup"><span data-stu-id="af105-158">Value</span></span>      | <span data-ttu-id="af105-159">Typ</span><span class="sxs-lookup"><span data-stu-id="af105-159">Type</span></span>   | <span data-ttu-id="af105-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af105-160">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="af105-161">value</span><span class="sxs-lookup"><span data-stu-id="af105-161">value</span></span>      | <span data-ttu-id="af105-162">Array</span><span class="sxs-lookup"><span data-stu-id="af105-162">array</span></span>  | <span data-ttu-id="af105-163">Ein Array von Objekten, die Informationen zu jeder App enthalten, die für Ihr Konto registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="af105-163">An array of objects that contain information about each app that is registered to your account.</span></span> <span data-ttu-id="af105-164">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unter [Anwendungsressource](get-app-data.md#application_object).</span><span class="sxs-lookup"><span data-stu-id="af105-164">For more information about the data in each object, see [Application resource](get-app-data.md#application_object).</span></span>                                                                                                                           |
| @nextLink  | <span data-ttu-id="af105-165">String</span><span class="sxs-lookup"><span data-stu-id="af105-165">string</span></span> | <span data-ttu-id="af105-166">Wenn weitere Datenseiten vorhanden sind, enthält diese Zeichenfolge einen relativen Pfad, den Sie an den Basisanforderungs-URI `https://manage.devcenter.microsoft.com/v1.0/my/` zum Anfordern der nächsten Datenseite anfügen können.</span><span class="sxs-lookup"><span data-stu-id="af105-166">If there are additional pages of data, this string contains a relative path that you can append to the base `https://manage.devcenter.microsoft.com/v1.0/my/` request URI to request the next page of data.</span></span> <span data-ttu-id="af105-167">Wenn beispielsweise der Parameter *top* des anfänglichen Anforderungstexts auf 10 festgelegt ist, für Ihr Konto jedoch 20Apps registriert wurden, enthält der Antworttext den @nextLink-Wert `applications?skip=10&top=10`, der angibt, dass Sie `https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=10&top=10` aufrufen können, um die nächsten 10 Apps anzufordern.</span><span class="sxs-lookup"><span data-stu-id="af105-167">For example, if the *top* parameter of the initial request body is set to 10 but there are 20 apps registered to your account, the response body will include a @nextLink value of `applications?skip=10&top=10`, which indicates that you can call `https://manage.devcenter.microsoft.com/v1.0/my/applications?skip=10&top=10` to request the next 10 apps.</span></span> |
| <span data-ttu-id="af105-168">totalCount</span><span class="sxs-lookup"><span data-stu-id="af105-168">totalCount</span></span> | <span data-ttu-id="af105-169">int</span><span class="sxs-lookup"><span data-stu-id="af105-169">int</span></span>    | <span data-ttu-id="af105-170">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage (d.h. die Gesamtanzahl von Apps, die für Ihr Konto registriert wurden).</span><span class="sxs-lookup"><span data-stu-id="af105-170">The total number of rows in the data result for the query (that is, the total number of apps that are registered to your account).</span></span>                                                |


## <a name="error-codes"></a><span data-ttu-id="af105-171">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="af105-171">Error codes</span></span>

<span data-ttu-id="af105-172">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="af105-172">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="af105-173">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="af105-173">Error code</span></span> |  <span data-ttu-id="af105-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af105-174">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="af105-175">404</span><span class="sxs-lookup"><span data-stu-id="af105-175">404</span></span>  | <span data-ttu-id="af105-176">Es wurden keine Apps gefunden.</span><span class="sxs-lookup"><span data-stu-id="af105-176">No apps were found.</span></span> |
| <span data-ttu-id="af105-177">409</span><span class="sxs-lookup"><span data-stu-id="af105-177">409</span></span>  | <span data-ttu-id="af105-178">Die apps verwenden Sie Partner Center-Funktionen, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="af105-178">The apps use Partner Center features that are [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="af105-179">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="af105-179">Related topics</span></span>

* [<span data-ttu-id="af105-180">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="af105-180">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="af105-181">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="af105-181">Get an app</span></span>](get-an-app.md)
* [<span data-ttu-id="af105-182">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="af105-182">Get package flights for an app</span></span>](get-flights-for-an-app.md)
* [<span data-ttu-id="af105-183">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="af105-183">Get add-ons for an app</span></span>](get-add-ons-for-an-app.md)
