---
author: mcleanbyron
ms.assetid: 87708690-079A-443D-807E-D2BF9F614DDF
description: "Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API, um Daten für ein Flight-Paket für eine App abzurufen, die für Ihr Windows Dev Center-Konto registriert ist."
title: Abrufen eines Flight-Pakets
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Flight, Flight-Paket"
ms.openlocfilehash: f0494a8c0f994d65a7d428b008f06c0bc9aa42c3
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="get-a-package-flight"></a><span data-ttu-id="45322-104">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="45322-104">Get a package flight</span></span>




<span data-ttu-id="45322-105">Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API, um Daten für ein Flight-Paket für eine App abzurufen, die für Ihr Windows Dev Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="45322-105">Use this method in the Windows Store submission API to get data for a package flight for an app that is registered to your Windows Dev Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45322-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="45322-106">Prerequisites</span></span>

<span data-ttu-id="45322-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="45322-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="45322-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="45322-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="45322-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="45322-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="45322-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="45322-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="45322-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="45322-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="45322-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="45322-112">Request</span></span>

<span data-ttu-id="45322-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="45322-113">This method has the following syntax.</span></span> <span data-ttu-id="45322-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="45322-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="45322-115">Methode</span><span class="sxs-lookup"><span data-stu-id="45322-115">Method</span></span> | <span data-ttu-id="45322-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="45322-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="45322-117">GET</span><span class="sxs-lookup"><span data-stu-id="45322-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="45322-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="45322-118">Request header</span></span>

| <span data-ttu-id="45322-119">Header</span><span class="sxs-lookup"><span data-stu-id="45322-119">Header</span></span>        | <span data-ttu-id="45322-120">Typ</span><span class="sxs-lookup"><span data-stu-id="45322-120">Type</span></span>   | <span data-ttu-id="45322-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45322-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="45322-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="45322-122">Authorization</span></span> | <span data-ttu-id="45322-123">String</span><span class="sxs-lookup"><span data-stu-id="45322-123">string</span></span> | <span data-ttu-id="45322-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45322-124">Required.</span></span> <span data-ttu-id="45322-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="45322-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="45322-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="45322-126">Request parameters</span></span>


| <span data-ttu-id="45322-127">Name</span><span class="sxs-lookup"><span data-stu-id="45322-127">Name</span></span>        | <span data-ttu-id="45322-128">Typ</span><span class="sxs-lookup"><span data-stu-id="45322-128">Type</span></span>   | <span data-ttu-id="45322-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45322-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="45322-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="45322-130">applicationId</span></span> | <span data-ttu-id="45322-131">String</span><span class="sxs-lookup"><span data-stu-id="45322-131">string</span></span> | <span data-ttu-id="45322-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45322-132">Required.</span></span> <span data-ttu-id="45322-133">Die Store-ID der App, die die Flight-Paketübermittlung enthält, die Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="45322-133">The Store ID of the app that contains the package flight you want to get.</span></span> <span data-ttu-id="45322-134">Die Store-ID für die App ist im Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="45322-134">The Store ID for the app is available on the Dev Center dashboard.</span></span>  |
| <span data-ttu-id="45322-135">flightId</span><span class="sxs-lookup"><span data-stu-id="45322-135">flightId</span></span> | <span data-ttu-id="45322-136">String</span><span class="sxs-lookup"><span data-stu-id="45322-136">string</span></span> | <span data-ttu-id="45322-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45322-137">Required.</span></span> <span data-ttu-id="45322-138">Die ID des abzurufenden Flight-Pakets.</span><span class="sxs-lookup"><span data-stu-id="45322-138">The ID of the package flight to get.</span></span> <span data-ttu-id="45322-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="45322-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="45322-140">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="45322-140">Request body</span></span>

<span data-ttu-id="45322-141">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="45322-141">Do not provide a request body for this method.</span></span>

<span/>

### <a name="request-example"></a><span data-ttu-id="45322-142">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="45322-142">Request example</span></span>

<span data-ttu-id="45322-143">Im folgenden Beispiel wird veranschaulicht, wie Informationen über ein Flight-Paket mit der ID 43e448df-97c9-4a43-a0bc-2a445e736bcd für eine App mit dem Store-ID-Wert 9WZDNCRD91MD abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="45322-143">The following example demonstrates how to retrieve information about a package flight with the ID 43e448df-97c9-4a43-a0bc-2a445e736bcd for an app with the Store ID value 9WZDNCRD91MD.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="45322-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="45322-144">Response</span></span>

<span data-ttu-id="45322-145">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="45322-145">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="45322-146">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="45322-146">For more details about the values in the response body, see the following sections.</span></span>

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

### <a name="response-body"></a><span data-ttu-id="45322-147">Antworttext</span><span class="sxs-lookup"><span data-stu-id="45322-147">Response body</span></span>

| <span data-ttu-id="45322-148">Wert</span><span class="sxs-lookup"><span data-stu-id="45322-148">Value</span></span>      | <span data-ttu-id="45322-149">Typ</span><span class="sxs-lookup"><span data-stu-id="45322-149">Type</span></span>   | <span data-ttu-id="45322-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45322-150">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="45322-151">flightId</span><span class="sxs-lookup"><span data-stu-id="45322-151">flightId</span></span>            | <span data-ttu-id="45322-152">string</span><span class="sxs-lookup"><span data-stu-id="45322-152">string</span></span>  | <span data-ttu-id="45322-153">Die ID für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="45322-153">The ID for the package flight.</span></span> <span data-ttu-id="45322-154">Dieser Wert wird von Dev Center bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="45322-154">This value is supplied by Dev Center.</span></span>  |
| <span data-ttu-id="45322-155">friendlyName</span><span class="sxs-lookup"><span data-stu-id="45322-155">friendlyName</span></span>           | <span data-ttu-id="45322-156">string</span><span class="sxs-lookup"><span data-stu-id="45322-156">string</span></span>  | <span data-ttu-id="45322-157">Der Name des Flight-Pakets nach Vorgabe des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="45322-157">The name of the package flight, as specified by the developer.</span></span>   |  
| <span data-ttu-id="45322-158">lastPublishedFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="45322-158">lastPublishedFlightSubmission</span></span>       | <span data-ttu-id="45322-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="45322-159">object</span></span> | <span data-ttu-id="45322-160">Ein Objekt, das Informationen über die letzte veröffentlichte Übermittlung für das Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="45322-160">An object that provides information about the last published submission for the package flight.</span></span> <span data-ttu-id="45322-161">Weitere Informationen finden Sie unten im Abschnitt [Übermittlungsobjekt](#submission_object).</span><span class="sxs-lookup"><span data-stu-id="45322-161">For more information, see the [Submission object](#submission_object) section below.</span></span>  |
| <span data-ttu-id="45322-162">pendingFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="45322-162">pendingFlightSubmission</span></span>        | <span data-ttu-id="45322-163">Objekt</span><span class="sxs-lookup"><span data-stu-id="45322-163">object</span></span>  |  <span data-ttu-id="45322-164">Ein Objekt, das Informationen über die aktuell ausstehende Übermittlung für das Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="45322-164">An object that provides information about the current pending submission for the package flight.</span></span> <span data-ttu-id="45322-165">Weitere Informationen finden Sie unten im Abschnitt [Übermittlungsobjekt](#submission_object).</span><span class="sxs-lookup"><span data-stu-id="45322-165">For more information, see the [Submission object](#submission_object) section below.</span></span>  |   
| <span data-ttu-id="45322-166">groupIds</span><span class="sxs-lookup"><span data-stu-id="45322-166">groupIds</span></span>           | <span data-ttu-id="45322-167">array</span><span class="sxs-lookup"><span data-stu-id="45322-167">array</span></span>  | <span data-ttu-id="45322-168">Ein Array von Zeichenfolgen, die die IDs der Test-Flight-Gruppen enthalten, die dem Flight-Paket zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="45322-168">An array of strings that contain the IDs of the flight groups that are associated with the package flight.</span></span> <span data-ttu-id="45322-169">Weitere Informationen zu Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="45322-169">For more information about flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>   |
| <span data-ttu-id="45322-170">rankHigherThan</span><span class="sxs-lookup"><span data-stu-id="45322-170">rankHigherThan</span></span>           | <span data-ttu-id="45322-171">string</span><span class="sxs-lookup"><span data-stu-id="45322-171">string</span></span>  | <span data-ttu-id="45322-172">Der Anzeigename des Flight-Pakets, das den unmittelbar niedrigeren Rang als das aktuelle Flight-Paket erhält.</span><span class="sxs-lookup"><span data-stu-id="45322-172">The friendly name of the package flight that is ranked immediately lower than the current package flight.</span></span> <span data-ttu-id="45322-173">Weitere Informationen zur Bewertung von Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="45322-173">For more information about ranking flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>  |

<span id="submission_object" />
### <a name="submission-object"></a><span data-ttu-id="45322-174">Übermittlungsobjekt</span><span class="sxs-lookup"><span data-stu-id="45322-174">Submission object</span></span>

<span data-ttu-id="45322-175">Die Werte *LastPublishedFlightSubmission* und *PendingFlightSubmission* im Antworttext enthalten Objekte mit Ressourceninformationen über eine Übermittlung für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="45322-175">The *lastPublishedFlightSubmission* and *pendingFlightSubmission* values in the response body contain objects that provide resource information about a submission for the package flight.</span></span> <span data-ttu-id="45322-176">Diese Objekte enthalten folgende Werte.</span><span class="sxs-lookup"><span data-stu-id="45322-176">These objects have the following values.</span></span>

| <span data-ttu-id="45322-177">Wert</span><span class="sxs-lookup"><span data-stu-id="45322-177">Value</span></span>           | <span data-ttu-id="45322-178">Typ</span><span class="sxs-lookup"><span data-stu-id="45322-178">Type</span></span>    | <span data-ttu-id="45322-179">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45322-179">Description</span></span>                                                                                                                                                                                                                          |
|-----------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="45322-180">id</span><span class="sxs-lookup"><span data-stu-id="45322-180">id</span></span>            | <span data-ttu-id="45322-181">string</span><span class="sxs-lookup"><span data-stu-id="45322-181">string</span></span>  | <span data-ttu-id="45322-182">Die ID der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="45322-182">The ID of the submission.</span></span>    |
| <span data-ttu-id="45322-183">resourceLocation</span><span class="sxs-lookup"><span data-stu-id="45322-183">resourceLocation</span></span>   | <span data-ttu-id="45322-184">string</span><span class="sxs-lookup"><span data-stu-id="45322-184">string</span></span>  | <span data-ttu-id="45322-185">Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="45322-185">A relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to retrieve the complete data for the submission.</span></span>                                                                                                                                               |
 
<span/>

## <a name="error-codes"></a><span data-ttu-id="45322-186">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="45322-186">Error codes</span></span>

<span data-ttu-id="45322-187">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="45322-187">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="45322-188">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="45322-188">Error code</span></span> |  <span data-ttu-id="45322-189">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="45322-189">Description</span></span>     |
|--------|---------------------  |
| <span data-ttu-id="45322-190">400</span><span class="sxs-lookup"><span data-stu-id="45322-190">400</span></span>  | <span data-ttu-id="45322-191">Die Anforderung ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="45322-191">The request is invalid.</span></span> |
| <span data-ttu-id="45322-192">404</span><span class="sxs-lookup"><span data-stu-id="45322-192">404</span></span>  | <span data-ttu-id="45322-193">Das angegebene Flight-Paket konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="45322-193">The specified package flight could not be found.</span></span>   |   
| <span data-ttu-id="45322-194">409</span><span class="sxs-lookup"><span data-stu-id="45322-194">409</span></span>  | <span data-ttu-id="45322-195">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="45322-195">The app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |                                                                                                 

<span/>

## <a name="related-topics"></a><span data-ttu-id="45322-196">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="45322-196">Related topics</span></span>

* [<span data-ttu-id="45322-197">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="45322-197">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="45322-198">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="45322-198">Create a package flight</span></span>](create-a-flight.md)
* [<span data-ttu-id="45322-199">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="45322-199">Delete a package flight</span></span>](delete-a-flight.md)
