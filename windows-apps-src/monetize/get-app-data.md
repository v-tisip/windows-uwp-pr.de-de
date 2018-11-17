---
author: Xansky
ms.assetid: 8D4AE532-22EF-4743-9555-A828B24B8F16
description: Verwenden Sie diese Methoden in der Microsoft Store-Übermittlungs-API zum Abrufen von Daten für apps, die für Ihr Partner Center-Konto registriert wurden.
title: Abrufen von App-Daten
ms.author: mhopkins
ms.date: 02/28/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, App-Daten
ms.localizationpriority: medium
ms.openlocfilehash: ecda61bff6fac407dbde175f584a09d6b871d989
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7173325"
---
# <a name="get-app-data"></a><span data-ttu-id="d7680-104">Abrufen von App-Daten</span><span class="sxs-lookup"><span data-stu-id="d7680-104">Get app data</span></span>

<span data-ttu-id="d7680-105">Verwenden Sie die folgenden Methoden in der Microsoft Store-Übermittlungs-API, um Daten für vorhandene apps im Partner Center-Konto zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d7680-105">Use the following methods in the Microsoft Store submission API to get data for existing apps in your Partner Center account.</span></span> <span data-ttu-id="d7680-106">Eine Einführung in die Microsoft Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit MicrosoftStore-Diensten](create-and-manage-submissions-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="d7680-106">For an introduction to the Microsoft Store submission API, including prerequisites for using the API, see [Create and manage submissions using Microsoft Store services](create-and-manage-submissions-using-windows-store-services.md).</span></span>

<span data-ttu-id="d7680-107">Bevor Sie diese Methoden verwenden können, muss die app bereits im Partner Center-Konto vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="d7680-107">Before you can use these methods, the app must already exist in your Partner Center account.</span></span> <span data-ttu-id="d7680-108">Informationen zum Erstellen oder Verwalten von Übermittlungen für Apps finden Sie unter den Methoden in [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="d7680-108">To create or manage submissions for apps, see the methods in [Manage app submissions](manage-app-submissions.md).</span></span>

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d7680-109">Methode</span><span class="sxs-lookup"><span data-stu-id="d7680-109">Method</span></span></th>
<th align="left"><span data-ttu-id="d7680-110">URI</span><span class="sxs-lookup"><span data-stu-id="d7680-110">URI</span></span></th>
<th align="left"><span data-ttu-id="d7680-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7680-111">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><span data-ttu-id="d7680-112">GET</span><span class="sxs-lookup"><span data-stu-id="d7680-112">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications</td>
<td align="left"><a href="get-all-apps.md"><span data-ttu-id="d7680-113">Daten für Ihre gesamten Apps abrufen</span><span class="sxs-lookup"><span data-stu-id="d7680-113">Get data for all your apps</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="d7680-114">GET</span><span class="sxs-lookup"><span data-stu-id="d7680-114">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}</td>
<td align="left"><a href="get-an-app.md"><span data-ttu-id="d7680-115">Daten für eine bestimmte App abrufen</span><span class="sxs-lookup"><span data-stu-id="d7680-115">Get data for a specific app</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="d7680-116">GET</span><span class="sxs-lookup"><span data-stu-id="d7680-116">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/listinappproducts</td>
<td align="left"><a href="get-add-ons-for-an-app.md"><span data-ttu-id="d7680-117">Add-Ons für eine App abrufen</span><span class="sxs-lookup"><span data-stu-id="d7680-117">Get add-ons for an app</span></span></a></td>
</tr>
<tr>
<td align="left"><span data-ttu-id="d7680-118">GET</span><span class="sxs-lookup"><span data-stu-id="d7680-118">GET</span></span></td>
<td align="left">https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/listflights</td>
<td align="left"><a href="get-flights-for-an-app.md"><span data-ttu-id="d7680-119">Flight-Pakete für eine App abrufen</span><span class="sxs-lookup"><span data-stu-id="d7680-119">Get package flights for an app</span></span></a></td>
</tr>
</tbody>
</table>

<span/>

## <a name="prerequisites"></a><span data-ttu-id="d7680-120">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d7680-120">Prerequisites</span></span>

<span data-ttu-id="d7680-121">Falls noch nicht geschehen, sorgen Sie vor der Verwendung dieser Methoden dafür, dass alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="d7680-121">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API before trying to use any of these methods.</span></span>

## <a name="data-resources"></a><span data-ttu-id="d7680-122">Datenressourcen</span><span class="sxs-lookup"><span data-stu-id="d7680-122">Data resources</span></span>

<span data-ttu-id="d7680-123">Die Microsoft Store-Übermittlungs-API-Methoden für das Abrufen von App-Daten verwenden die folgenden JSON-Datenressourcen.</span><span class="sxs-lookup"><span data-stu-id="d7680-123">The Microsoft Store submission API methods for getting app data use the following JSON data resources.</span></span>

<span id="application_object" />

### <a name="application-resource"></a><span data-ttu-id="d7680-124">Anwendungsressource</span><span class="sxs-lookup"><span data-stu-id="d7680-124">Application resource</span></span>

<span data-ttu-id="d7680-125">Diese Ressource steht für eine App, die in Ihrem Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="d7680-125">This resource represents an app that is registered to your account.</span></span>

```json
{
  "id": "9NBLGGH4R315",
  "primaryName": "ApiTestApp",
  "packageFamilyName": "30481DevCenterAPITester.ApiTestAppForDevbox_ng6try80pwt52",
  "packageIdentityName": "30481DevCenterAPITester.ApiTestAppForDevbox",
  "publisherName": "CN=…",
  "firstPublishedDate": "1601-01-01T00:00:00Z",
  "lastPublishedApplicationSubmission": {
    "id": "1152921504621086517",
    "resourceLocation": "applications/9NBLGGH4R315/submissions/1152921504621086517"
  },
  "pendingApplicationSubmission": {
    "id": "1152921504621243487",
    "resourceLocation": "applications/9NBLGGH4R315/submissions/1152921504621243487"
  },
  "hasAdvancedListingPermission": true
}
```

<span data-ttu-id="d7680-126">Diese Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="d7680-126">This resource has the following values.</span></span>

| <span data-ttu-id="d7680-127">Wert</span><span class="sxs-lookup"><span data-stu-id="d7680-127">Value</span></span>           | <span data-ttu-id="d7680-128">Typ</span><span class="sxs-lookup"><span data-stu-id="d7680-128">Type</span></span>    | <span data-ttu-id="d7680-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7680-129">Description</span></span>       |
|-----------------|---------|---------------------|
| <span data-ttu-id="d7680-130">id</span><span class="sxs-lookup"><span data-stu-id="d7680-130">id</span></span>            | <span data-ttu-id="d7680-131">String</span><span class="sxs-lookup"><span data-stu-id="d7680-131">string</span></span>  | <span data-ttu-id="d7680-132">Die Store-ID der App.</span><span class="sxs-lookup"><span data-stu-id="d7680-132">The Store ID of the app.</span></span> <span data-ttu-id="d7680-133">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="d7680-133">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>   |
| <span data-ttu-id="d7680-134">primaryName</span><span class="sxs-lookup"><span data-stu-id="d7680-134">primaryName</span></span>   | <span data-ttu-id="d7680-135">String</span><span class="sxs-lookup"><span data-stu-id="d7680-135">string</span></span>  | <span data-ttu-id="d7680-136">Der Primärname der App.</span><span class="sxs-lookup"><span data-stu-id="d7680-136">The primary name of the app.</span></span>      |
| <span data-ttu-id="d7680-137">packageFamilyName</span><span class="sxs-lookup"><span data-stu-id="d7680-137">packageFamilyName</span></span> | <span data-ttu-id="d7680-138">string</span><span class="sxs-lookup"><span data-stu-id="d7680-138">string</span></span>  | <span data-ttu-id="d7680-139">Der Paketfamilienname der App.</span><span class="sxs-lookup"><span data-stu-id="d7680-139">The package family name of the app.</span></span>      |
| <span data-ttu-id="d7680-140">packageIdentityName</span><span class="sxs-lookup"><span data-stu-id="d7680-140">packageIdentityName</span></span>          | <span data-ttu-id="d7680-141">string</span><span class="sxs-lookup"><span data-stu-id="d7680-141">string</span></span>  | <span data-ttu-id="d7680-142">Die Paketidentität der App.</span><span class="sxs-lookup"><span data-stu-id="d7680-142">The package identity name of the app.</span></span>                       |
| <span data-ttu-id="d7680-143">publisherName</span><span class="sxs-lookup"><span data-stu-id="d7680-143">publisherName</span></span>       | <span data-ttu-id="d7680-144">string</span><span class="sxs-lookup"><span data-stu-id="d7680-144">string</span></span>  | <span data-ttu-id="d7680-145">Die Windows-Herausgeber-ID, die mit der App verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="d7680-145">The Windows publisher ID that is associated with the app.</span></span> <span data-ttu-id="d7680-146">Dies entspricht dem **Package/Identity/Publisher** -Wert, der auf der Seite [App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details) für die app im Partner Center angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d7680-146">This corresponds to the **Package/Identity/Publisher** value that appears on the [App identity](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details) page for the app in Partner Center.</span></span>       |
| <span data-ttu-id="d7680-147">firstPublishedDate</span><span class="sxs-lookup"><span data-stu-id="d7680-147">firstPublishedDate</span></span>      | <span data-ttu-id="d7680-148">string</span><span class="sxs-lookup"><span data-stu-id="d7680-148">string</span></span>  | <span data-ttu-id="d7680-149">Das Datum, an dem die App erstmals im Format ISO 8601 veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="d7680-149">The date the app was first published, in ISO 8601 format.</span></span>   |
| <span data-ttu-id="d7680-150">lastPublishedApplicationSubmission</span><span class="sxs-lookup"><span data-stu-id="d7680-150">lastPublishedApplicationSubmission</span></span>       | <span data-ttu-id="d7680-151">object</span><span class="sxs-lookup"><span data-stu-id="d7680-151">object</span></span> | <span data-ttu-id="d7680-152">Eine [Übermittlungsressource](#submission_object) mit Informationen über die letzte veröffentlichte Übermittlung für die App.</span><span class="sxs-lookup"><span data-stu-id="d7680-152">A [submission resource](#submission_object) that provides information about the last published submission for the app.</span></span>    |
| <span data-ttu-id="d7680-153">pendingApplicationSubmission</span><span class="sxs-lookup"><span data-stu-id="d7680-153">pendingApplicationSubmission</span></span>        | <span data-ttu-id="d7680-154">object</span><span class="sxs-lookup"><span data-stu-id="d7680-154">object</span></span>  |  <span data-ttu-id="d7680-155">Eine [Übermittlungsressource](#submission_object) mit Informationen über die aktuelle ausstehende Übermittlung für die App.</span><span class="sxs-lookup"><span data-stu-id="d7680-155">A [submission resource](#submission_object) that provides information about the current pending submission for the app.</span></span>   |   
| <span data-ttu-id="d7680-156">hasAdvancedListingPermission</span><span class="sxs-lookup"><span data-stu-id="d7680-156">hasAdvancedListingPermission</span></span>        | <span data-ttu-id="d7680-157">boolean</span><span class="sxs-lookup"><span data-stu-id="d7680-157">boolean</span></span>  |  <span data-ttu-id="d7680-158">Gibt an, ob Sie die [gamingOptions](manage-app-submissions.md#gaming-options-object) oder [trailers](manage-app-submissions.md#trailer-object) für Übermittlungen für die App konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="d7680-158">Indicates whether you can configure the [gamingOptions](manage-app-submissions.md#gaming-options-object) or [trailers](manage-app-submissions.md#trailer-object) for submissions for the app.</span></span> <span data-ttu-id="d7680-159">Dieser Wert gilt für Übermittlungen, die später als Mai 2017 erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="d7680-159">This value is true for submissions created after May 2017.</span></span> |  |


<span id="add-on-object" />

### <a name="add-on-resouce"></a><span data-ttu-id="d7680-160">Add-On-Ressource</span><span class="sxs-lookup"><span data-stu-id="d7680-160">Add-on resouce</span></span>

<span data-ttu-id="d7680-161">Diese Ressource enthält Informationen zu einem Add-On.</span><span class="sxs-lookup"><span data-stu-id="d7680-161">This resource provides information about an add-on.</span></span>

```json
{
    "inAppProductId": "9WZDNCRD7DLK"
}
```

<span data-ttu-id="d7680-162">Diese Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="d7680-162">This resource has the following values.</span></span>

| <span data-ttu-id="d7680-163">Wert</span><span class="sxs-lookup"><span data-stu-id="d7680-163">Value</span></span>           | <span data-ttu-id="d7680-164">Typ</span><span class="sxs-lookup"><span data-stu-id="d7680-164">Type</span></span>    | <span data-ttu-id="d7680-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7680-165">Description</span></span>         |
|-----------------|---------|----------------------|
| <span data-ttu-id="d7680-166">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="d7680-166">inAppProductId</span></span>            | <span data-ttu-id="d7680-167">string</span><span class="sxs-lookup"><span data-stu-id="d7680-167">string</span></span>  | <span data-ttu-id="d7680-168">Die Store-ID des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="d7680-168">The Store ID of the add-on.</span></span> <span data-ttu-id="d7680-169">Dieser Wert wird vom Store bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d7680-169">This value is supplied by the Store.</span></span> <span data-ttu-id="d7680-170">Beispiel für eine Store-ID: 9NBLGGH4TNMP.</span><span class="sxs-lookup"><span data-stu-id="d7680-170">An example Store ID is 9NBLGGH4TNMP.</span></span>   |


<span id="flight-object" />

### <a name="flight-resource"></a><span data-ttu-id="d7680-171">Flight-Ressource</span><span class="sxs-lookup"><span data-stu-id="d7680-171">Flight resource</span></span>

<span data-ttu-id="d7680-172">Diese Ressource enthält Informationen zu einem Flight-Paket für eine App.</span><span class="sxs-lookup"><span data-stu-id="d7680-172">This resource provides information about a package flight for an app.</span></span>

```json
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
```

<span data-ttu-id="d7680-173">Diese Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="d7680-173">This resource has the following values.</span></span>

| <span data-ttu-id="d7680-174">Wert</span><span class="sxs-lookup"><span data-stu-id="d7680-174">Value</span></span>           | <span data-ttu-id="d7680-175">Typ</span><span class="sxs-lookup"><span data-stu-id="d7680-175">Type</span></span>    | <span data-ttu-id="d7680-176">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7680-176">Description</span></span>           |
|-----------------|---------|------------------------|
| <span data-ttu-id="d7680-177">flightId</span><span class="sxs-lookup"><span data-stu-id="d7680-177">flightId</span></span>            | <span data-ttu-id="d7680-178">string</span><span class="sxs-lookup"><span data-stu-id="d7680-178">string</span></span>  | <span data-ttu-id="d7680-179">Die ID für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="d7680-179">The ID for the package flight.</span></span> <span data-ttu-id="d7680-180">Dieser Wert wird vom Partner Center bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d7680-180">This value is supplied by Partner Center.</span></span>  |
| <span data-ttu-id="d7680-181">friendlyName</span><span class="sxs-lookup"><span data-stu-id="d7680-181">friendlyName</span></span>           | <span data-ttu-id="d7680-182">string</span><span class="sxs-lookup"><span data-stu-id="d7680-182">string</span></span>  | <span data-ttu-id="d7680-183">Der Name des Flight-Pakets nach Vorgabe des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="d7680-183">The name of the package flight, as specified by the developer.</span></span>   |
| <span data-ttu-id="d7680-184">lastPublishedFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="d7680-184">lastPublishedFlightSubmission</span></span>       | <span data-ttu-id="d7680-185">object</span><span class="sxs-lookup"><span data-stu-id="d7680-185">object</span></span> | <span data-ttu-id="d7680-186">Eine [Übermittlungsressource](#submission_object) mit Informationen über die letzte veröffentlichte Übermittlung für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="d7680-186">A [submission resource](#submission_object) that provides information about the last published submission for the package flight.</span></span>   |
| <span data-ttu-id="d7680-187">pendingFlightSubmission</span><span class="sxs-lookup"><span data-stu-id="d7680-187">pendingFlightSubmission</span></span>        | <span data-ttu-id="d7680-188">object</span><span class="sxs-lookup"><span data-stu-id="d7680-188">object</span></span>  |  <span data-ttu-id="d7680-189">Eine [Übermittlungsressource](#submission_object) mit Informationen über die aktuelle ausstehende Übermittlung für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="d7680-189">A [submission resource](#submission_object) that provides information about the current pending submission for the package flight.</span></span>  |    
| <span data-ttu-id="d7680-190">groupIds</span><span class="sxs-lookup"><span data-stu-id="d7680-190">groupIds</span></span>           | <span data-ttu-id="d7680-191">array</span><span class="sxs-lookup"><span data-stu-id="d7680-191">array</span></span>  | <span data-ttu-id="d7680-192">Ein Array von Zeichenfolgen, die die IDs der Test-Flight-Gruppen enthalten, die dem Flight-Paket zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="d7680-192">An array of strings that contain the IDs of the flight groups that are associated with the package flight.</span></span> <span data-ttu-id="d7680-193">Weitere Informationen zu Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="d7680-193">For more information about flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>   |
| <span data-ttu-id="d7680-194">rankHigherThan</span><span class="sxs-lookup"><span data-stu-id="d7680-194">rankHigherThan</span></span>           | <span data-ttu-id="d7680-195">string</span><span class="sxs-lookup"><span data-stu-id="d7680-195">string</span></span>  | <span data-ttu-id="d7680-196">Der Anzeigename des Flight-Pakets, das den unmittelbar niedrigeren Rang als das aktuelle Flight-Paket erhält.</span><span class="sxs-lookup"><span data-stu-id="d7680-196">The friendly name of the package flight that is ranked immediately lower than the current package flight.</span></span> <span data-ttu-id="d7680-197">Weitere Informationen zur Bewertung von Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="d7680-197">For more information about ranking flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>  |


<span id="submission_object" />

### <a name="submission-resource"></a><span data-ttu-id="d7680-198">Übermittlungsressource</span><span class="sxs-lookup"><span data-stu-id="d7680-198">Submission resource</span></span>

<span data-ttu-id="d7680-199">Diese Ressource enthält Informationen zu einer Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d7680-199">This resource provides information about a submission.</span></span> <span data-ttu-id="d7680-200">Das folgende Beispiel veranschaulicht das Format der Ressource.</span><span class="sxs-lookup"><span data-stu-id="d7680-200">The following example demonstrates the format of this resource.</span></span>

```json
{
  "pendingApplicationSubmission": {
    "id": "1152921504621243487",
    "resourceLocation": "applications/9WZDNCRD9MMD/submissions/1152921504621243487"
  }
}
```

<span data-ttu-id="d7680-201">Die Ressource hat die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="d7680-201">This resource has the following values.</span></span>

| <span data-ttu-id="d7680-202">Wert</span><span class="sxs-lookup"><span data-stu-id="d7680-202">Value</span></span>           | <span data-ttu-id="d7680-203">Typ</span><span class="sxs-lookup"><span data-stu-id="d7680-203">Type</span></span>    | <span data-ttu-id="d7680-204">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7680-204">Description</span></span>                 |
|-----------------|---------|------------------------------|
| <span data-ttu-id="d7680-205">id</span><span class="sxs-lookup"><span data-stu-id="d7680-205">id</span></span>            | <span data-ttu-id="d7680-206">string</span><span class="sxs-lookup"><span data-stu-id="d7680-206">string</span></span>  | <span data-ttu-id="d7680-207">Die ID der Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d7680-207">The ID of the submission.</span></span>    |
| <span data-ttu-id="d7680-208">resourceLocation</span><span class="sxs-lookup"><span data-stu-id="d7680-208">resourceLocation</span></span>   | <span data-ttu-id="d7680-209">string</span><span class="sxs-lookup"><span data-stu-id="d7680-209">string</span></span>  | <span data-ttu-id="d7680-210">Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d7680-210">A relative path that you can append to the base ```https://manage.devcenter.microsoft.com/v1.0/my/``` request URI to retrieve the complete data for the submission.</span></span>            |
 
<span/>

## <a name="related-topics"></a><span data-ttu-id="d7680-211">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d7680-211">Related topics</span></span>

* [<span data-ttu-id="d7680-212">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="d7680-212">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="d7680-213">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="d7680-213">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="d7680-214">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="d7680-214">Get all apps</span></span>](get-all-apps.md)
* [<span data-ttu-id="d7680-215">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="d7680-215">Get an app</span></span>](get-an-app.md)
* [<span data-ttu-id="d7680-216">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="d7680-216">Get add-ons for an app</span></span>](get-add-ons-for-an-app.md)
* [<span data-ttu-id="d7680-217">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="d7680-217">Get package flights for an app</span></span>](get-flights-for-an-app.md)
