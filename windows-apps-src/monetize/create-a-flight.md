---
author: Xansky
ms.assetid: 8C1E9E36-13AF-4386-9D0F-F9CB320F02F5
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen eines Flight-Pakets für eine App, die für Ihr Windows Dev Center-Konto registriert ist.
title: Erstellen eines Flight-Pakets
ms.author: mhopkins
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight erstellen
ms.localizationpriority: medium
ms.openlocfilehash: 5e6a547c8baf0f8990415e303d6b69ca04986d3b
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5166647"
---
# <a name="create-a-package-flight"></a><span data-ttu-id="64ade-104">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="64ade-104">Create a package flight</span></span>

<span data-ttu-id="64ade-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Erstellen eines Flight-Pakets für eine App, die für Ihr Windows Dev Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="64ade-105">Use this method in the Microsoft Store submission API to create a package flight for an app that is registered to your Windows Dev Center account.</span></span>

> [!NOTE]
> <span data-ttu-id="64ade-106">Durch diese Methode wird ein Flight-Paket ohne Übermittlungen erstellt.</span><span class="sxs-lookup"><span data-stu-id="64ade-106">This method creates a package flight without any submissions.</span></span> <span data-ttu-id="64ade-107">Verwenden Sie zum Erstellen einer Übermittlung für ein Flight-Paket die Methoden unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="64ade-107">To create a submission for package flight, see the methods in [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64ade-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="64ade-108">Prerequisites</span></span>

<span data-ttu-id="64ade-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="64ade-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="64ade-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="64ade-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="64ade-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="64ade-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="64ade-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="64ade-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="64ade-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="64ade-113">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="64ade-114">Anforderung</span><span class="sxs-lookup"><span data-stu-id="64ade-114">Request</span></span>

<span data-ttu-id="64ade-115">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="64ade-115">This method has the following syntax.</span></span> <span data-ttu-id="64ade-116">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="64ade-116">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="64ade-117">Methode</span><span class="sxs-lookup"><span data-stu-id="64ade-117">Method</span></span> | <span data-ttu-id="64ade-118">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="64ade-118">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="64ade-119">POST</span><span class="sxs-lookup"><span data-stu-id="64ade-119">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights``` |


### <a name="request-header"></a><span data-ttu-id="64ade-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="64ade-120">Request header</span></span>

| <span data-ttu-id="64ade-121">Header</span><span class="sxs-lookup"><span data-stu-id="64ade-121">Header</span></span>        | <span data-ttu-id="64ade-122">Typ</span><span class="sxs-lookup"><span data-stu-id="64ade-122">Type</span></span>   | <span data-ttu-id="64ade-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64ade-123">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="64ade-124">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="64ade-124">Authorization</span></span> | <span data-ttu-id="64ade-125">String</span><span class="sxs-lookup"><span data-stu-id="64ade-125">string</span></span> | <span data-ttu-id="64ade-126">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="64ade-126">Required.</span></span> <span data-ttu-id="64ade-127">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="64ade-127">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="64ade-128">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="64ade-128">Request parameters</span></span>

| <span data-ttu-id="64ade-129">Name</span><span class="sxs-lookup"><span data-stu-id="64ade-129">Name</span></span>        | <span data-ttu-id="64ade-130">Typ</span><span class="sxs-lookup"><span data-stu-id="64ade-130">Type</span></span>   | <span data-ttu-id="64ade-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64ade-131">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="64ade-132">applicationId</span><span class="sxs-lookup"><span data-stu-id="64ade-132">applicationId</span></span> | <span data-ttu-id="64ade-133">String</span><span class="sxs-lookup"><span data-stu-id="64ade-133">string</span></span> | <span data-ttu-id="64ade-134">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="64ade-134">Required.</span></span> <span data-ttu-id="64ade-135">Die Store-ID der App, für die Sie ein Flight-Paket erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="64ade-135">The Store ID of the app for which you want to create a package flight.</span></span> <span data-ttu-id="64ade-136">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="64ade-136">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="64ade-137">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="64ade-137">Request body</span></span>

<span data-ttu-id="64ade-138">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="64ade-138">The request body has the following parameters.</span></span>

|  <span data-ttu-id="64ade-139">Parameter</span><span class="sxs-lookup"><span data-stu-id="64ade-139">Parameter</span></span>  |  <span data-ttu-id="64ade-140">Typ</span><span class="sxs-lookup"><span data-stu-id="64ade-140">Type</span></span>  |  <span data-ttu-id="64ade-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64ade-141">Description</span></span>  |  <span data-ttu-id="64ade-142">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="64ade-142">Required</span></span>  |
|------|------|------|------|
|  <span data-ttu-id="64ade-143">friendlyName</span><span class="sxs-lookup"><span data-stu-id="64ade-143">friendlyName</span></span>  |  <span data-ttu-id="64ade-144">string</span><span class="sxs-lookup"><span data-stu-id="64ade-144">string</span></span>  |  <span data-ttu-id="64ade-145">Der Name des Flight-Pakets nach Vorgabe des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="64ade-145">The name of the package flight, as specified by the developer.</span></span>  |  <span data-ttu-id="64ade-146">Nein</span><span class="sxs-lookup"><span data-stu-id="64ade-146">No</span></span>  |
|  <span data-ttu-id="64ade-147">groupIds</span><span class="sxs-lookup"><span data-stu-id="64ade-147">groupIds</span></span>  |  <span data-ttu-id="64ade-148">array</span><span class="sxs-lookup"><span data-stu-id="64ade-148">array</span></span>  |  <span data-ttu-id="64ade-149">Ein Array von Zeichenfolgen, die die IDs der Test-Flight-Gruppen enthalten, die dem Flight-Paket zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="64ade-149">An array of strings that contain the IDs of the flight groups that are associated with the package flight.</span></span> <span data-ttu-id="64ade-150">Weitere Informationen zu Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="64ade-150">For more information about flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>  |  <span data-ttu-id="64ade-151">Nein</span><span class="sxs-lookup"><span data-stu-id="64ade-151">No</span></span>  |
|  <span data-ttu-id="64ade-152">rankHigherThan</span><span class="sxs-lookup"><span data-stu-id="64ade-152">rankHigherThan</span></span>  |  <span data-ttu-id="64ade-153">string</span><span class="sxs-lookup"><span data-stu-id="64ade-153">string</span></span>  |  <span data-ttu-id="64ade-154">Der Anzeigename des Flight-Pakets, das den unmittelbar niedrigeren Rang als das aktuelle Flight-Paket erhält.</span><span class="sxs-lookup"><span data-stu-id="64ade-154">The friendly name of the package flight that is ranked immediately lower than the current package flight.</span></span> <span data-ttu-id="64ade-155">Wenn Sie diesen Parameter nicht festlegen, erhält das neue Flight-Paket den höchsten Rang aller Flight-Pakete.</span><span class="sxs-lookup"><span data-stu-id="64ade-155">If you do not set this parameter, the new package flight will have the highest rank of all package flights.</span></span> <span data-ttu-id="64ade-156">Weitere Informationen zur Bewertung von Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="64ade-156">For more information about ranking flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>    |  <span data-ttu-id="64ade-157">Nein</span><span class="sxs-lookup"><span data-stu-id="64ade-157">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="64ade-158">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="64ade-158">Request example</span></span>

<span data-ttu-id="64ade-159">Im folgenden Beispiel wird gezeigt, wie Sie ein neues Flight-Paket für eine App mit der Store-ID 9WZDNCRD911W erstellen.</span><span class="sxs-lookup"><span data-stu-id="64ade-159">The following example demonstrates how to create a new package flight for an app that has the Store ID 9WZDNCRD911W.</span></span>

```syntax
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1Q...
Content-Type: application/json
{
  "friendlyName": "myflight",
  "groupIds": [
    0
  ],
  "rankHigherThan": null
}

```

## <a name="response"></a><span data-ttu-id="64ade-160">Antwort</span><span class="sxs-lookup"><span data-stu-id="64ade-160">Response</span></span>

<span data-ttu-id="64ade-161">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="64ade-161">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="64ade-162">Weitere Informationen zu den Werten im Antworttext finden Sie in den folgenden Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="64ade-162">For more details about the values in the response body, see the following sections.</span></span>

```json
{
  "flightId": "43e448df-97c9-4a43-a0bc-2a445e736bcd",
  "friendlyName": "myflight",
  "groupIds": [
    "0"
  ],
  "rankHigherThan": "671c2857-725e-4faf-9e9e-ea1191ef879c"
}
```

### <a name="response-body"></a><span data-ttu-id="64ade-163">Antworttext</span><span class="sxs-lookup"><span data-stu-id="64ade-163">Response body</span></span>

| <span data-ttu-id="64ade-164">Wert</span><span class="sxs-lookup"><span data-stu-id="64ade-164">Value</span></span>      | <span data-ttu-id="64ade-165">Typ</span><span class="sxs-lookup"><span data-stu-id="64ade-165">Type</span></span>   | <span data-ttu-id="64ade-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64ade-166">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="64ade-167">flightId</span><span class="sxs-lookup"><span data-stu-id="64ade-167">flightId</span></span>            | <span data-ttu-id="64ade-168">string</span><span class="sxs-lookup"><span data-stu-id="64ade-168">string</span></span>  | <span data-ttu-id="64ade-169">Die ID für das Flight-Paket.</span><span class="sxs-lookup"><span data-stu-id="64ade-169">The ID for the package flight.</span></span> <span data-ttu-id="64ade-170">Dieser Wert wird von Dev Center bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="64ade-170">This value is supplied by Dev Center.</span></span>  |
| <span data-ttu-id="64ade-171">friendlyName</span><span class="sxs-lookup"><span data-stu-id="64ade-171">friendlyName</span></span>           | <span data-ttu-id="64ade-172">string</span><span class="sxs-lookup"><span data-stu-id="64ade-172">string</span></span>  | <span data-ttu-id="64ade-173">Der Name des Flight-Pakets gemäß der Angabe in der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="64ade-173">The name of the package flight, as specified in the request.</span></span>   |  
| <span data-ttu-id="64ade-174">groupIds</span><span class="sxs-lookup"><span data-stu-id="64ade-174">groupIds</span></span>           | <span data-ttu-id="64ade-175">array</span><span class="sxs-lookup"><span data-stu-id="64ade-175">array</span></span>  | <span data-ttu-id="64ade-176">Ein Array von Zeichenfolgen, die die IDs der Test-Flight-Gruppen enthalten, die dem Flight-Paket zugeordnet sind, gemäß der Angabe in der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="64ade-176">An array of strings that contain the IDs of the flight groups that are associated with the package flight, as specified in the request.</span></span> <span data-ttu-id="64ade-177">Weitere Informationen zu Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="64ade-177">For more information about flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>   |
| <span data-ttu-id="64ade-178">rankHigherThan</span><span class="sxs-lookup"><span data-stu-id="64ade-178">rankHigherThan</span></span>           | <span data-ttu-id="64ade-179">string</span><span class="sxs-lookup"><span data-stu-id="64ade-179">string</span></span>  | <span data-ttu-id="64ade-180">Der Anzeigename des Flight-Pakets, das den unmittelbar niedrigeren Rang als das aktuelle Flight-Paket erhält, gemäß der Angabe in der Anforderung.</span><span class="sxs-lookup"><span data-stu-id="64ade-180">The friendly name of the package flight that is ranked immediately lower than the current package flight, as specified in the request.</span></span> <span data-ttu-id="64ade-181">Weitere Informationen zur Bewertung von Test-Flight-Gruppen finden Sie unter [Flight-Pakete](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span><span class="sxs-lookup"><span data-stu-id="64ade-181">For more information about ranking flight groups, see [Package flights](https://msdn.microsoft.com/windows/uwp/publish/package-flights).</span></span>  |


## <a name="error-codes"></a><span data-ttu-id="64ade-182">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="64ade-182">Error codes</span></span>

<span data-ttu-id="64ade-183">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="64ade-183">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="64ade-184">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="64ade-184">Error code</span></span> |  <span data-ttu-id="64ade-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="64ade-185">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="64ade-186">400</span><span class="sxs-lookup"><span data-stu-id="64ade-186">400</span></span>  | <span data-ttu-id="64ade-187">Die Anforderung ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="64ade-187">The request is invalid.</span></span> |
| <span data-ttu-id="64ade-188">409</span><span class="sxs-lookup"><span data-stu-id="64ade-188">409</span></span>  | <span data-ttu-id="64ade-189">Das Flight-Paket konnte im aktuellen Zustand nicht erstellt werden, oder in der App wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="64ade-189">The package flight could not be created because of its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="64ade-190">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="64ade-190">Related topics</span></span>

* [<span data-ttu-id="64ade-191">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="64ade-191">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="64ade-192">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="64ade-192">Get a package flight</span></span>](get-a-flight.md)
* [<span data-ttu-id="64ade-193">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="64ade-193">Delete a package flight</span></span>](delete-a-flight.md)
