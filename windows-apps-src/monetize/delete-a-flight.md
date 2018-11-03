---
author: Xansky
ms.assetid: AD80F9B3-CED0-40BD-A199-AB81CDAE466C
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Löschen eines Flight-Pakets für eine app, die für Ihr Partner Center-Konto registriert ist.
title: Löschen eines Flight-Pakets
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight löschen
ms.localizationpriority: medium
ms.openlocfilehash: 23e90a322f347375cfdb33eca9315a5ca538fd4c
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5995273"
---
# <a name="delete-a-package-flight"></a><span data-ttu-id="3f402-104">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="3f402-104">Delete a package flight</span></span>

<span data-ttu-id="3f402-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum Löschen eines Flight-Pakets für eine app, die für Ihr Partner Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="3f402-105">Use this method in the Microsoft Store submission API to delete a package flight for an app that is registered to your Partner Center account.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="3f402-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3f402-106">Prerequisites</span></span>

<span data-ttu-id="3f402-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="3f402-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="3f402-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="3f402-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="3f402-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3f402-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="3f402-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="3f402-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="3f402-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="3f402-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="3f402-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="3f402-112">Request</span></span>

<span data-ttu-id="3f402-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="3f402-113">This method has the following syntax.</span></span> <span data-ttu-id="3f402-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="3f402-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="3f402-115">Methode</span><span class="sxs-lookup"><span data-stu-id="3f402-115">Method</span></span> | <span data-ttu-id="3f402-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="3f402-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="3f402-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="3f402-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}``` |


### <a name="request-header"></a><span data-ttu-id="3f402-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="3f402-118">Request header</span></span>

| <span data-ttu-id="3f402-119">Header</span><span class="sxs-lookup"><span data-stu-id="3f402-119">Header</span></span>        | <span data-ttu-id="3f402-120">Typ</span><span class="sxs-lookup"><span data-stu-id="3f402-120">Type</span></span>   | <span data-ttu-id="3f402-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3f402-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="3f402-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="3f402-122">Authorization</span></span> | <span data-ttu-id="3f402-123">String</span><span class="sxs-lookup"><span data-stu-id="3f402-123">string</span></span> | <span data-ttu-id="3f402-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3f402-124">Required.</span></span> <span data-ttu-id="3f402-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="3f402-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="3f402-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="3f402-126">Request parameters</span></span>

| <span data-ttu-id="3f402-127">Name</span><span class="sxs-lookup"><span data-stu-id="3f402-127">Name</span></span>        | <span data-ttu-id="3f402-128">Typ</span><span class="sxs-lookup"><span data-stu-id="3f402-128">Type</span></span>   | <span data-ttu-id="3f402-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3f402-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="3f402-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="3f402-130">applicationId</span></span> | <span data-ttu-id="3f402-131">String</span><span class="sxs-lookup"><span data-stu-id="3f402-131">string</span></span> | <span data-ttu-id="3f402-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3f402-132">Required.</span></span> <span data-ttu-id="3f402-133">Die Store-ID der App, das zu löschende Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="3f402-133">The Store ID of the app that contains the package flight you want to delete.</span></span> <span data-ttu-id="3f402-134">Die Store-ID für die app ist im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3f402-134">The Store ID for the app is available in Partner Center.</span></span>  |
| <span data-ttu-id="3f402-135">flightId</span><span class="sxs-lookup"><span data-stu-id="3f402-135">flightId</span></span> | <span data-ttu-id="3f402-136">String</span><span class="sxs-lookup"><span data-stu-id="3f402-136">string</span></span> | <span data-ttu-id="3f402-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3f402-137">Required.</span></span> <span data-ttu-id="3f402-138">Die ID des zu löschenden Flight-Pakets.</span><span class="sxs-lookup"><span data-stu-id="3f402-138">The ID of the package flight to delete.</span></span> <span data-ttu-id="3f402-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="3f402-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="3f402-140">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3f402-140">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="3f402-141">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="3f402-141">Request body</span></span>

<span data-ttu-id="3f402-142">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="3f402-142">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="3f402-143">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="3f402-143">Request example</span></span>

<span data-ttu-id="3f402-144">Im folgenden Beispiel wird veranschaulicht, wie ein Flight-Paket gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="3f402-144">The following example demonstrates how to delete a package flight.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="3f402-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="3f402-145">Response</span></span>

<span data-ttu-id="3f402-146">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="3f402-146">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="3f402-147">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="3f402-147">Error codes</span></span>

<span data-ttu-id="3f402-148">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="3f402-148">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="3f402-149">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="3f402-149">Error code</span></span> |  <span data-ttu-id="3f402-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3f402-150">Description</span></span>                                                                                                                                                                           |
|--------|------------------|
| <span data-ttu-id="3f402-151">400</span><span class="sxs-lookup"><span data-stu-id="3f402-151">400</span></span>  | <span data-ttu-id="3f402-152">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="3f402-152">The request parameters are invalid.</span></span> |
| <span data-ttu-id="3f402-153">404</span><span class="sxs-lookup"><span data-stu-id="3f402-153">404</span></span>  | <span data-ttu-id="3f402-154">Das angegebene Flight-Paket konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="3f402-154">The specified package flight could not be found.</span></span>  |
| <span data-ttu-id="3f402-155">409</span><span class="sxs-lookup"><span data-stu-id="3f402-155">409</span></span>  | <span data-ttu-id="3f402-156">Das angegebene Flight-Paket wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand gelöscht werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="3f402-156">The specified package flight was found but it could not be deleted in its current state, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="3f402-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3f402-157">Related topics</span></span>

* [<span data-ttu-id="3f402-158">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="3f402-158">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="3f402-159">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="3f402-159">Create a package flight</span></span>](create-a-flight.md)
* [<span data-ttu-id="3f402-160">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="3f402-160">Get a package flight</span></span>](get-a-flight.md)
