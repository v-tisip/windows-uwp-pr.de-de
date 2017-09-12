---
author: mcleanbyron
ms.assetid: 1A69A388-B1CC-4D2C-886B-EA07E6E60252
description: "Verwenden Sie diese Methode der Windows Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung."
title: "Löschen einer Flight-Paketübermittlung"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Flight-Übermittlungen, löschen, Flight-Paket"
ms.openlocfilehash: b2d6e2a1f92541478b4639133978cf6bdb009214
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="delete-a-package-flight-submission"></a><span data-ttu-id="f84b5-104">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-104">Delete a package flight submission</span></span>




<span data-ttu-id="f84b5-105">Verwenden Sie diese Methode der Windows Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="f84b5-105">Use this method in the Windows Store submission API to delete an existing package flight submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f84b5-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f84b5-106">Prerequisites</span></span>

<span data-ttu-id="f84b5-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="f84b5-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="f84b5-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="f84b5-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="f84b5-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f84b5-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="f84b5-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="f84b5-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="f84b5-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="f84b5-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="f84b5-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="f84b5-112">Request</span></span>

<span data-ttu-id="f84b5-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="f84b5-113">This method has the following syntax.</span></span> <span data-ttu-id="f84b5-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="f84b5-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="f84b5-115">Methode</span><span class="sxs-lookup"><span data-stu-id="f84b5-115">Method</span></span> | <span data-ttu-id="f84b5-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="f84b5-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="f84b5-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="f84b5-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/flights/{flightId}/submissions/{submissionId}``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="f84b5-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="f84b5-118">Request header</span></span>

| <span data-ttu-id="f84b5-119">Header</span><span class="sxs-lookup"><span data-stu-id="f84b5-119">Header</span></span>        | <span data-ttu-id="f84b5-120">Typ</span><span class="sxs-lookup"><span data-stu-id="f84b5-120">Type</span></span>   | <span data-ttu-id="f84b5-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f84b5-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f84b5-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="f84b5-122">Authorization</span></span> | <span data-ttu-id="f84b5-123">String</span><span class="sxs-lookup"><span data-stu-id="f84b5-123">string</span></span> | <span data-ttu-id="f84b5-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f84b5-124">Required.</span></span> <span data-ttu-id="f84b5-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="f84b5-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="f84b5-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="f84b5-126">Request parameters</span></span>

| <span data-ttu-id="f84b5-127">Name</span><span class="sxs-lookup"><span data-stu-id="f84b5-127">Name</span></span>        | <span data-ttu-id="f84b5-128">Typ</span><span class="sxs-lookup"><span data-stu-id="f84b5-128">Type</span></span>   | <span data-ttu-id="f84b5-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f84b5-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f84b5-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="f84b5-130">applicationId</span></span> | <span data-ttu-id="f84b5-131">String</span><span class="sxs-lookup"><span data-stu-id="f84b5-131">string</span></span> | <span data-ttu-id="f84b5-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f84b5-132">Required.</span></span> <span data-ttu-id="f84b5-133">Die Store-ID der App, die die zu löschende Flight-Paketübermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="f84b5-133">The Store ID of the app that contains the package flight submission you want to delete.</span></span> <span data-ttu-id="f84b5-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="f84b5-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="f84b5-135">flightId</span><span class="sxs-lookup"><span data-stu-id="f84b5-135">flightId</span></span> | <span data-ttu-id="f84b5-136">String</span><span class="sxs-lookup"><span data-stu-id="f84b5-136">string</span></span> | <span data-ttu-id="f84b5-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f84b5-137">Required.</span></span> <span data-ttu-id="f84b5-138">Die ID des Flight-Pakets, das die zu löschende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="f84b5-138">The ID of the package flight that contains the submission to delete.</span></span> <span data-ttu-id="f84b5-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="f84b5-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |
| <span data-ttu-id="f84b5-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="f84b5-140">submissionId</span></span> | <span data-ttu-id="f84b5-141">String</span><span class="sxs-lookup"><span data-stu-id="f84b5-141">string</span></span> | <span data-ttu-id="f84b5-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f84b5-142">Required.</span></span> <span data-ttu-id="f84b5-143">Die ID der zu löschenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="f84b5-143">The ID of the submission to delete.</span></span> <span data-ttu-id="f84b5-144">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="f84b5-144">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="f84b5-145">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="f84b5-145">Request body</span></span>

<span data-ttu-id="f84b5-146">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="f84b5-146">Do not provide a request body for this method.</span></span>

<span/>

### <a name="request-example"></a><span data-ttu-id="f84b5-147">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="f84b5-147">Request example</span></span>

<span data-ttu-id="f84b5-148">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Flight-Paketübermittlung löschen.</span><span class="sxs-lookup"><span data-stu-id="f84b5-148">The following example demonstrates how to delete a submission for a package flight.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="f84b5-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="f84b5-149">Response</span></span>

<span data-ttu-id="f84b5-150">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="f84b5-150">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="f84b5-151">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="f84b5-151">Error codes</span></span>

<span data-ttu-id="f84b5-152">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="f84b5-152">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="f84b5-153">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="f84b5-153">Error code</span></span> |  <span data-ttu-id="f84b5-154">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f84b5-154">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="f84b5-155">400</span><span class="sxs-lookup"><span data-stu-id="f84b5-155">400</span></span>  | <span data-ttu-id="f84b5-156">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="f84b5-156">The request parameters are invalid.</span></span> |
| <span data-ttu-id="f84b5-157">404</span><span class="sxs-lookup"><span data-stu-id="f84b5-157">404</span></span>  | <span data-ttu-id="f84b5-158">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="f84b5-158">The specified submission could not be found.</span></span> |
| <span data-ttu-id="f84b5-159">409</span><span class="sxs-lookup"><span data-stu-id="f84b5-159">409</span></span>  | <span data-ttu-id="f84b5-160">Die angegebene Übermittlung wurde gefunden, konnte jedoch nicht in ihrem aktuellen Zustand gelöscht werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="f84b5-160">The specified submission was found but it could not be deleted in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |

<span/>

## <a name="related-topics"></a><span data-ttu-id="f84b5-161">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f84b5-161">Related topics</span></span>

* [<span data-ttu-id="f84b5-162">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="f84b5-162">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="f84b5-163">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="f84b5-163">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="f84b5-164">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-164">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="f84b5-165">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-165">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="f84b5-166">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-166">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="f84b5-167">Aktualisieren einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-167">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="f84b5-168">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="f84b5-168">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
