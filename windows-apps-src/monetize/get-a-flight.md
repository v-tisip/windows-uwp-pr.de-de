---
ms.assetid: 87708690-079A-443D-807E-D2BF9F614DDF
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Daten für eine Flight-Paket für eine app abzurufen, die für Ihr Partner Center-Konto registriert ist.
title: Abrufen eines Flight-Pakets
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight, Flight-Pakete
ms.localizationpriority: medium
ms.openlocfilehash: c4ff6c929a7264b5dece0057701c8348fe5d39be
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7844829"
---
# <a name="get-a-package-flight"></a><span data-ttu-id="28a54-104">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="28a54-104">Get a package flight</span></span>

<span data-ttu-id="28a54-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Daten für eine Flight-Paket für eine app abzurufen, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="28a54-105">Use this method in the Microsoft Store submission API to get data for a package flight for an app that is registered to your Partner Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28a54-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="28a54-106">Prerequisites</span></span>

<span data-ttu-id="28a54-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="28a54-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="28a54-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="28a54-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="28a54-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="28a54-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="28a54-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="28a54-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="28a54-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="28a54-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="28a54-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="28a54-112">Request</span></span>

<span data-ttu-id="28a54-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="28a54-113">This method has the following syntax.</span></span> <span data-ttu-id="28a54-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="28a54-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="28a54-115">Methode</span><span class="sxs-lookup"><span data-stu-id="28a54-115">Method</span></span> | <span data-ttu-id="28a54-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="28a54-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="28a54-117">GET</span><span class="sxs-lookup"><span data-stu-id="28a54-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}``` |


### <a name="request-header"></a><span data-ttu-id="28a54-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="28a54-118">Request header</span></span>

| <span data-ttu-id="28a54-119">Header</span><span class="sxs-lookup"><span data-stu-id="28a54-119">Header</span></span>        | <span data-ttu-id="28a54-120">Typ</span><span class="sxs-lookup"><span data-stu-id="28a54-120">Type</span></span>   | <span data-ttu-id="28a54-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28a54-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="28a54-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="28a54-122">Authorization</span></span> | <span data-ttu-id="28a54-123">String</span><span class="sxs-lookup"><span data-stu-id="28a54-123">string</span></span> | <span data-ttu-id="28a54-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="28a54-124">Required.</span></span> <span data-ttu-id="28a54-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="28a54-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="28a54-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="28a54-126">Request parameters</span></span>

| <span data-ttu-id="28a54-127">Name</span><span class="sxs-lookup"><span data-stu-id="28a54-127">Name</span></span>        | <span data-ttu-id="28a54-128">Typ</span><span class="sxs-lookup"><span data-stu-id="28a54-128">Type</span></span>   | <span data-ttu-id="28a54-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28a54-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="28a54-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="28a54-130">applicationId</span></span> | <span data-ttu-id="28a54-131">String</span><span class="sxs-lookup"><span data-stu-id="28a54-131">string</span></span> | <span data-ttu-id="28a54-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="28a54-132">Required.</span></span> <span data-ttu-id="28a54-133">Die Store-ID der App, die die Flight-Paketübermittlung enthält, die Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="28a54-133">The Store ID of the app that contains the package flight you want to get.</span></span> <span data-ttu-id="28a54-134">Die Store-ID für die app ist im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="28a54-134">The Store ID for the app is available in Partner Center.</span></span>  |
| <span data-ttu-id="28a54-135">flightId</span><span class="sxs-lookup"><span data-stu-id="28a54-135">flightId</span></span> | <span data-ttu-id="28a54-136">String</span><span class="sxs-lookup"><span data-stu-id="28a54-136">string</span></span> | <span data-ttu-id="28a54-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="28a54-137">Required.</span></span> <span data-ttu-id="28a54-138">Die ID des abzurufenden Flight-Pakets.</span><span class="sxs-lookup"><span data-stu-id="28a54-138">The ID of the package flight to get.</span></span> <span data-ttu-id="28a54-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="28a54-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="28a54-140">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Test-Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="28a54-140">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="28a54-141">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="28a54-141">Request body</span></span>

<span data-ttu-id="28a54-142">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="28a54-142">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="28a54-143">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="28a54-143">Request example</span></span>

<span data-ttu-id="28a54-144">Im folgenden Beispiel wird veranschaulicht, wie Informationen über ein Flight-Paket mit der ID 43e448df-97c9-4a43-a0bc-2a445e736bcd für eine App mit dem Store-ID-Wert 9WZDNCRD91MD abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="28a54-144">The following example demonstrates how to retrieve information about a package flight with the ID 43e448df-97c9-4a43-a0bc-2a445e736bcd for an app with the Store ID value 9WZDNCRD91MD.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="28a54-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="28a54-145">Response</span></span>

<span data-ttu-id="28a54-146">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="28a54-146">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="28a54-147">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="28a54-147">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "flightId": "43e448df-97c9-4a43-a0bc-2a445e736bcd",
  "friendlyName": "myflight",
  "lastPublishedFlightSubmission": {
    "id": "1152921504621086517",
    "resourceLocation": "flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621086517"
  },
  "pendingFlightSubmission": {
    "id": "115292150462124364",
    "resourceLocation": "flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243647"
  },
  "groupIds": [
    "0"
  ],
  "rankHigherThan": "671c2857-725e-4faf-9e9e-ea1191ef879c"
}
```

### <a name="response-body"></a><span data-ttu-id="28a54-148">Antworttext</span><span class="sxs-lookup"><span data-stu-id="28a54-148">Response body</span></span>

| <span data-ttu-id="28a54-149">Wert</span><span class="sxs-lookup"><span data-stu-id="28a54-149">Value</span></span>      | <span data-ttu-id="28a54-150">Typ</span><span class="sxs-lookup"><span data-stu-id="28a54-150">Type</span></span>   | <span data-ttu-id="28a54-151">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28a54-151">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28a54-152">flightId</span><span class="sxs-lookup"><span data-stu-id="28a54-152">flightId</span></span>            | <span data-ttu-id="28a54-153">string</span><span class="sxs-lookup"><span data-stu-id="28a54-153">string</span></span>  | <span data-ttu-id="28a54-154">Die ID für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="28a54-154">The ID for the package flight.</span></span> <span data-ttu-id="28a54-155">Dieser Wert wird vom Partner Center bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="28a54-155">This value is supplied by Partner Center.</span></span>  |
| <span data-ttu-id="28a54-156">friendlyName</span><span class="sxs-lookup"><span data-stu-id="28a54-156">friendlyName</span></span>           | <span data-ttu-id="28a54-157">string</span><span class="sxs-lookup"><span data-stu-id="28a54-157">string</span></span>  | <span data-ttu-id="28a54-158">Der Name des Flight-Pakets nach Vorgabe des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="28a54-158">The name of the package flight, as specified by the developer.</span></span>   |  
| <span data-ttu-id="28a54-159">lastPublishedFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="28a54-159">lastPublishedFlightSubmission</span></span>       | <span data-ttu-id="28a54-160">Objekt</span><span class="sxs-lookup"><span data-stu-id="28a54-160">object</span></span> | <span data-ttu-id="28a54-161">Ein Objekt, das Informationen über die letzte veröffentlichte Übermittlung für das Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="28a54-161">An object that provides information about the last published submission for the package flight.</span></span> <span data-ttu-id="28a54-162">Weitere Informationen finden Sie unten im Abschnitt [Übermittlungsobjekt](#submission_object).</span><span class="sxs-lookup"><span data-stu-id="28a54-162">For more information, see the [Submission object](#submission_object) section below.</span></span>  |
| <span data-ttu-id="28a54-163">pendingFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="28a54-163">pendingFlightSubmission</span></span>        | <span data-ttu-id="28a54-164">Objekt</span><span class="sxs-lookup"><span data-stu-id="28a54-164">object</span></span>  |  <span data-ttu-id="28a54-165">Ein Objekt, das Informationen über die aktuell ausstehende Übermittlung für das Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="28a54-165">An object that provides information about the current pending submission for the package flight.</span></span> <span data-ttu-id="28a54-166">Weitere Informationen finden Sie unten im Abschnitt [Übermittlungsobjekt](#submission_object).</span><span class="sxs-lookup"><span data-stu-id="28a54-166">For more information, see the [Submission object](#submission_object) section below.</span></span>  |   
| <span data-ttu-id="28a54-167">groupIds</span><span class="sxs-lookup"><span data-stu-id="28a54-167">groupIds</span></span>           | <span data-ttu-id="28a54-168">array</span><span class="sxs-lookup"><span data-stu-id="28a54-168">array</span></span>  | <span data-ttu-id="28a54-169">Ein Array von Zeichenfolgen, die die IDs der Test-Flight-Gruppen enthalten, die dem Flight-Paket zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="28a54-169">An array of strings that contain the IDs of the flight groups that are associated with the package flight.</span></span> <span data-ttu-id="28a54-170">Weitere Informationen zu Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="28a54-170">For more information about flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>   |
| <span data-ttu-id="28a54-171">rankHigherThan</span><span class="sxs-lookup"><span data-stu-id="28a54-171">rankHigherThan</span></span>           | <span data-ttu-id="28a54-172">string</span><span class="sxs-lookup"><span data-stu-id="28a54-172">string</span></span>  | <span data-ttu-id="28a54-173">Der Anzeigename des Flight-Pakets, das den unmittelbar niedrigeren Rang als das aktuelle Flight-Paket erhält.</span><span class="sxs-lookup"><span data-stu-id="28a54-173">The friendly name of the package flight that is ranked immediately lower than the current package flight.</span></span> <span data-ttu-id="28a54-174">Weitere Informationen zur Bewertung von Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="28a54-174">For more information about ranking flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>  |


<span id="submission_object" />

### <a name="submission-object"></a><span data-ttu-id="28a54-175">Übermittlungsobjekt</span><span class="sxs-lookup"><span data-stu-id="28a54-175">Submission object</span></span>

<span data-ttu-id="28a54-176">Die Werte *LastPublishedFlightSubmission* und *PendingFlightSubmission* im Antworttext enthalten Objekte mit Ressourceninformationen über eine Übermittlung für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="28a54-176">The *lastPublishedFlightSubmission* and *pendingFlightSubmission* values in the response body contain objects that provide resource information about a submission for the package flight.</span></span> <span data-ttu-id="28a54-177">Diese Objekte enthalten folgende Werte.</span><span class="sxs-lookup"><span data-stu-id="28a54-177">These objects have the following values.</span></span>

| <span data-ttu-id="28a54-178">Wert</span><span class="sxs-lookup"><span data-stu-id="28a54-178">Value</span></span>           | <span data-ttu-id="28a54-179">Typ</span><span class="sxs-lookup"><span data-stu-id="28a54-179">Type</span></span>    | <span data-ttu-id="28a54-180">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28a54-180">Description</span></span>                                                                                                                                                                                                                          |
|-----------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28a54-181">id</span><span class="sxs-lookup"><span data-stu-id="28a54-181">id</span></span>            | <span data-ttu-id="28a54-182">string</span><span class="sxs-lookup"><span data-stu-id="28a54-182">string</span></span>  | <span data-ttu-id="28a54-183">Die ID der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="28a54-183">The ID of the submission.</span></span>    |
| <span data-ttu-id="28a54-184">resourceLocation</span><span class="sxs-lookup"><span data-stu-id="28a54-184">resourceLocation</span></span>   | <span data-ttu-id="28a54-185">string</span><span class="sxs-lookup"><span data-stu-id="28a54-185">string</span></span>  | <span data-ttu-id="28a54-186">Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="28a54-186">A relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to retrieve the complete data for the submission.</span></span>               |


## <a name="error-codes"></a><span data-ttu-id="28a54-187">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="28a54-187">Error codes</span></span>

<span data-ttu-id="28a54-188">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="28a54-188">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="28a54-189">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="28a54-189">Error code</span></span> |  <span data-ttu-id="28a54-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="28a54-190">Description</span></span>     |
|--------|---------------------  |
| <span data-ttu-id="28a54-191">400</span><span class="sxs-lookup"><span data-stu-id="28a54-191">400</span></span>  | <span data-ttu-id="28a54-192">Die Anforderung ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="28a54-192">The request is invalid.</span></span> |
| <span data-ttu-id="28a54-193">404</span><span class="sxs-lookup"><span data-stu-id="28a54-193">404</span></span>  | <span data-ttu-id="28a54-194">Das angegebene Flight-Paket konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="28a54-194">The specified package flight could not be found.</span></span>   |   
| <span data-ttu-id="28a54-195">409</span><span class="sxs-lookup"><span data-stu-id="28a54-195">409</span></span>  | <span data-ttu-id="28a54-196">Die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="28a54-196">The app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |                                                                                                 


## <a name="related-topics"></a><span data-ttu-id="28a54-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="28a54-197">Related topics</span></span>

* [<span data-ttu-id="28a54-198">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="28a54-198">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="28a54-199">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="28a54-199">Create a package flight</span></span>](create-a-flight.md)
* [<span data-ttu-id="28a54-200">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="28a54-200">Delete a package flight</span></span>](delete-a-flight.md)
