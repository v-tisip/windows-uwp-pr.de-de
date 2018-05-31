---
author: mcleanbyron
ms.assetid: DAF92881-6AF6-44C7-B466-215F5226AE04
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über eine bestimmte Apps abzurufen, die für Ihr Windows Dev Center-Konto registriert wurde.
title: Abrufen einer App
ms.author: mcleans
ms.date: 02/28/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, App
ms.localizationpriority: medium
ms.openlocfilehash: 87995e0ee50b762f4b626be0b3796cc10390a02d
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1661950"
---
# <a name="get-an-app"></a><span data-ttu-id="de11e-104">Abrufen einer App</span><span class="sxs-lookup"><span data-stu-id="de11e-104">Get an app</span></span>

<span data-ttu-id="de11e-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um Informationen über eine bestimmte Apps abzurufen, die für Ihr Windows Dev Center-Konto registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="de11e-105">Use this method in the Microsoft Store submission API to retrieve information about a specific app that is registered to your Windows Dev Center account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de11e-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="de11e-106">Prerequisites</span></span>

<span data-ttu-id="de11e-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="de11e-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="de11e-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="de11e-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="de11e-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="de11e-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="de11e-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="de11e-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="de11e-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="de11e-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="de11e-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="de11e-112">Request</span></span>

<span data-ttu-id="de11e-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="de11e-113">This method has the following syntax.</span></span> <span data-ttu-id="de11e-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="de11e-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="de11e-115">Methode</span><span class="sxs-lookup"><span data-stu-id="de11e-115">Method</span></span> | <span data-ttu-id="de11e-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="de11e-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="de11e-117">GET</span><span class="sxs-lookup"><span data-stu-id="de11e-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}``` |


### <a name="request-header"></a><span data-ttu-id="de11e-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="de11e-118">Request header</span></span>

| <span data-ttu-id="de11e-119">Header</span><span class="sxs-lookup"><span data-stu-id="de11e-119">Header</span></span>        | <span data-ttu-id="de11e-120">Typ</span><span class="sxs-lookup"><span data-stu-id="de11e-120">Type</span></span>   | <span data-ttu-id="de11e-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de11e-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="de11e-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="de11e-122">Authorization</span></span> | <span data-ttu-id="de11e-123">String</span><span class="sxs-lookup"><span data-stu-id="de11e-123">string</span></span> | <span data-ttu-id="de11e-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de11e-124">Required.</span></span> <span data-ttu-id="de11e-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="de11e-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="de11e-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="de11e-126">Request parameters</span></span>

| <span data-ttu-id="de11e-127">Name</span><span class="sxs-lookup"><span data-stu-id="de11e-127">Name</span></span>        | <span data-ttu-id="de11e-128">Typ</span><span class="sxs-lookup"><span data-stu-id="de11e-128">Type</span></span>   | <span data-ttu-id="de11e-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de11e-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="de11e-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="de11e-130">applicationId</span></span> | <span data-ttu-id="de11e-131">String</span><span class="sxs-lookup"><span data-stu-id="de11e-131">string</span></span> | <span data-ttu-id="de11e-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de11e-132">Required.</span></span> <span data-ttu-id="de11e-133">Die Store-ID der abzurufenden App.</span><span class="sxs-lookup"><span data-stu-id="de11e-133">The Store ID of the app to retrieve.</span></span> <span data-ttu-id="de11e-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="de11e-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |


### <a name="request-body"></a><span data-ttu-id="de11e-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="de11e-135">Request body</span></span>

<span data-ttu-id="de11e-136">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="de11e-136">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="de11e-137">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="de11e-137">Request example</span></span>

<span data-ttu-id="de11e-138">Im folgenden Beispiel wird veranschaulicht, wie Informationen über eine App mit dem Store-ID-Wert 9NBLGGH4R315 abgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="de11e-138">The following example demonstrates how to retrieve information about an app with the Store ID value 9NBLGGH4R315.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="de11e-139">Antwort</span><span class="sxs-lookup"><span data-stu-id="de11e-139">Response</span></span>

<span data-ttu-id="de11e-140">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="de11e-140">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="de11e-141">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Anwendungsressource](get-app-data.md#application_object).</span><span class="sxs-lookup"><span data-stu-id="de11e-141">For more details about the values in the response body, see [Application resource](get-app-data.md#application_object).</span></span>

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
  "hasAdvancedListingPermission": false
}
```

## <a name="error-codes"></a><span data-ttu-id="de11e-142">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="de11e-142">Error codes</span></span>

<span data-ttu-id="de11e-143">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="de11e-143">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="de11e-144">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="de11e-144">Error code</span></span> |  <span data-ttu-id="de11e-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de11e-145">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="de11e-146">404</span><span class="sxs-lookup"><span data-stu-id="de11e-146">404</span></span>  | <span data-ttu-id="de11e-147">Die angegebene App konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="de11e-147">The specified app could not be found.</span></span> |
| <span data-ttu-id="de11e-148">409</span><span class="sxs-lookup"><span data-stu-id="de11e-148">409</span></span>  | <span data-ttu-id="de11e-149">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="de11e-149">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span>  |


## <a name="related-topics"></a><span data-ttu-id="de11e-150">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="de11e-150">Related topics</span></span>

* [<span data-ttu-id="de11e-151">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="de11e-151">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="de11e-152">Abrufen aller Apps</span><span class="sxs-lookup"><span data-stu-id="de11e-152">Get all apps</span></span>](get-all-apps.md)
* [<span data-ttu-id="de11e-153">Abrufen von Flight-Paketen für eine App</span><span class="sxs-lookup"><span data-stu-id="de11e-153">Get package flights for an app</span></span>](get-flights-for-an-app.md)
* [<span data-ttu-id="de11e-154">Abrufen von Add-Ons für eine App</span><span class="sxs-lookup"><span data-stu-id="de11e-154">Get add-ons for an app</span></span>](get-add-ons-for-an-app.md)
