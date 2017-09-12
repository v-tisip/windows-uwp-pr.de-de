---
author: mcleanbyron
ms.assetid: AD80F9B3-CED0-40BD-A199-AB81CDAE466C
description: "Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API zum Löschen eines Flight-Pakets für eine App, die für Ihr Windows Dev Center-Konto registriert ist."
title: "Löschen eines Flight-Pakets"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Flight löschen"
ms.openlocfilehash: 4a05e69f3dd1c530fee630cc3af13809fc1ac0b6
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="delete-a-package-flight"></a><span data-ttu-id="14118-104">Löschen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="14118-104">Delete a package flight</span></span>




<span data-ttu-id="14118-105">Verwenden Sie diese Methode in der Windows Store-Übermittlungs-API zum Löschen eines Flight-Pakets für eine App, die für Ihr Windows Dev Center-Konto registriert ist.</span><span class="sxs-lookup"><span data-stu-id="14118-105">Use this method in the Windows Store submission API to delete a package flight for an app that is registered to your Windows Dev Center account.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="14118-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="14118-106">Prerequisites</span></span>

<span data-ttu-id="14118-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="14118-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="14118-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="14118-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="14118-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="14118-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="14118-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="14118-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="14118-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="14118-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="14118-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="14118-112">Request</span></span>

<span data-ttu-id="14118-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="14118-113">This method has the following syntax.</span></span> <span data-ttu-id="14118-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="14118-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="14118-115">Methode</span><span class="sxs-lookup"><span data-stu-id="14118-115">Method</span></span> | <span data-ttu-id="14118-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="14118-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="14118-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="14118-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="14118-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="14118-118">Request header</span></span>

| <span data-ttu-id="14118-119">Header</span><span class="sxs-lookup"><span data-stu-id="14118-119">Header</span></span>        | <span data-ttu-id="14118-120">Typ</span><span class="sxs-lookup"><span data-stu-id="14118-120">Type</span></span>   | <span data-ttu-id="14118-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14118-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="14118-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="14118-122">Authorization</span></span> | <span data-ttu-id="14118-123">String</span><span class="sxs-lookup"><span data-stu-id="14118-123">string</span></span> | <span data-ttu-id="14118-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="14118-124">Required.</span></span> <span data-ttu-id="14118-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="14118-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="14118-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="14118-126">Request parameters</span></span>

| <span data-ttu-id="14118-127">Name</span><span class="sxs-lookup"><span data-stu-id="14118-127">Name</span></span>        | <span data-ttu-id="14118-128">Typ</span><span class="sxs-lookup"><span data-stu-id="14118-128">Type</span></span>   | <span data-ttu-id="14118-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14118-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="14118-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="14118-130">applicationId</span></span> | <span data-ttu-id="14118-131">String</span><span class="sxs-lookup"><span data-stu-id="14118-131">string</span></span> | <span data-ttu-id="14118-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="14118-132">Required.</span></span> <span data-ttu-id="14118-133">Die Store-ID der App, das zu löschende Flight-Paket enthält.</span><span class="sxs-lookup"><span data-stu-id="14118-133">The Store ID of the app that contains the package flight you want to delete.</span></span> <span data-ttu-id="14118-134">Die Store-ID für die App ist im Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14118-134">The Store ID for the app is available on the Dev Center dashboard.</span></span>  |
| <span data-ttu-id="14118-135">flightId</span><span class="sxs-lookup"><span data-stu-id="14118-135">flightId</span></span> | <span data-ttu-id="14118-136">String</span><span class="sxs-lookup"><span data-stu-id="14118-136">string</span></span> | <span data-ttu-id="14118-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="14118-137">Required.</span></span> <span data-ttu-id="14118-138">Die ID des zu löschenden Flight-Pakets.</span><span class="sxs-lookup"><span data-stu-id="14118-138">The ID of the package flight to delete.</span></span> <span data-ttu-id="14118-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="14118-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="14118-140">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="14118-140">Request body</span></span>

<span data-ttu-id="14118-141">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="14118-141">Do not provide a request body for this method.</span></span>

<span/>

### <a name="request-example"></a><span data-ttu-id="14118-142">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="14118-142">Request example</span></span>

<span data-ttu-id="14118-143">Im folgenden Beispiel wird veranschaulicht, wie ein Flight-Paket gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="14118-143">The following example demonstrates how to delete a package flight.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="14118-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="14118-144">Response</span></span>

<span data-ttu-id="14118-145">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="14118-145">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="14118-146">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="14118-146">Error codes</span></span>

<span data-ttu-id="14118-147">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="14118-147">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="14118-148">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="14118-148">Error code</span></span> |  <span data-ttu-id="14118-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14118-149">Description</span></span>                                                                                                                                                                           |
|--------|------------------|
| <span data-ttu-id="14118-150">400</span><span class="sxs-lookup"><span data-stu-id="14118-150">400</span></span>  | <span data-ttu-id="14118-151">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="14118-151">The request parameters are invalid.</span></span> |
| <span data-ttu-id="14118-152">404</span><span class="sxs-lookup"><span data-stu-id="14118-152">404</span></span>  | <span data-ttu-id="14118-153">Das angegebene Flight-Paket konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="14118-153">The specified package flight could not be found.</span></span>  |
| <span data-ttu-id="14118-154">409</span><span class="sxs-lookup"><span data-stu-id="14118-154">409</span></span>  | <span data-ttu-id="14118-155">Das angegebene Flight-Paket wurde gefunden, konnte jedoch nicht im aktuellen Zustand gelöscht werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="14118-155">The specified package flight was found but it could not be deleted in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   

<span/>

## <a name="related-topics"></a><span data-ttu-id="14118-156">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="14118-156">Related topics</span></span>

* [<span data-ttu-id="14118-157">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="14118-157">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="14118-158">Erstellen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="14118-158">Create a package flight</span></span>](create-a-flight.md)
* [<span data-ttu-id="14118-159">Abrufen eines Flight-Pakets</span><span class="sxs-lookup"><span data-stu-id="14118-159">Get a package flight</span></span>](get-a-flight.md)
