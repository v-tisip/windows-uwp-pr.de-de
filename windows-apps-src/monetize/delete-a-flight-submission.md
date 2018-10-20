---
author: Xansky
ms.assetid: 1A69A388-B1CC-4D2C-886B-EA07E6E60252
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung.
title: Löschen einer Flight-Paketübermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlungen, löschen, Flight-Paket
ms.localizationpriority: medium
ms.openlocfilehash: 8618d93b1a6ec465a95956d01648444313cdf142
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5166693"
---
# <a name="delete-a-package-flight-submission"></a><span data-ttu-id="bd062-104">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-104">Delete a package flight submission</span></span>

<span data-ttu-id="bd062-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="bd062-105">Use this method in the Microsoft Store submission API to delete an existing package flight submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd062-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bd062-106">Prerequisites</span></span>

<span data-ttu-id="bd062-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="bd062-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="bd062-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="bd062-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="bd062-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd062-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="bd062-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="bd062-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="bd062-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="bd062-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="bd062-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="bd062-112">Request</span></span>

<span data-ttu-id="bd062-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="bd062-113">This method has the following syntax.</span></span> <span data-ttu-id="bd062-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="bd062-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="bd062-115">Methode</span><span class="sxs-lookup"><span data-stu-id="bd062-115">Method</span></span> | <span data-ttu-id="bd062-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="bd062-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="bd062-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="bd062-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/flights/{flightId}/submissions/{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="bd062-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="bd062-118">Request header</span></span>

| <span data-ttu-id="bd062-119">Header</span><span class="sxs-lookup"><span data-stu-id="bd062-119">Header</span></span>        | <span data-ttu-id="bd062-120">Typ</span><span class="sxs-lookup"><span data-stu-id="bd062-120">Type</span></span>   | <span data-ttu-id="bd062-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd062-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="bd062-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="bd062-122">Authorization</span></span> | <span data-ttu-id="bd062-123">String</span><span class="sxs-lookup"><span data-stu-id="bd062-123">string</span></span> | <span data-ttu-id="bd062-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bd062-124">Required.</span></span> <span data-ttu-id="bd062-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="bd062-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="bd062-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="bd062-126">Request parameters</span></span>

| <span data-ttu-id="bd062-127">Name</span><span class="sxs-lookup"><span data-stu-id="bd062-127">Name</span></span>        | <span data-ttu-id="bd062-128">Typ</span><span class="sxs-lookup"><span data-stu-id="bd062-128">Type</span></span>   | <span data-ttu-id="bd062-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd062-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="bd062-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="bd062-130">applicationId</span></span> | <span data-ttu-id="bd062-131">String</span><span class="sxs-lookup"><span data-stu-id="bd062-131">string</span></span> | <span data-ttu-id="bd062-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bd062-132">Required.</span></span> <span data-ttu-id="bd062-133">Die Store-ID der App, die die zu löschende Flight-Paketübermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="bd062-133">The Store ID of the app that contains the package flight submission you want to delete.</span></span> <span data-ttu-id="bd062-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="bd062-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="bd062-135">flightId</span><span class="sxs-lookup"><span data-stu-id="bd062-135">flightId</span></span> | <span data-ttu-id="bd062-136">String</span><span class="sxs-lookup"><span data-stu-id="bd062-136">string</span></span> | <span data-ttu-id="bd062-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bd062-137">Required.</span></span> <span data-ttu-id="bd062-138">Die ID des Flight-Pakets, das die zu löschende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="bd062-138">The ID of the package flight that contains the submission to delete.</span></span> <span data-ttu-id="bd062-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="bd062-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="bd062-140">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bd062-140">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="bd062-141">submissionId</span><span class="sxs-lookup"><span data-stu-id="bd062-141">submissionId</span></span> | <span data-ttu-id="bd062-142">String</span><span class="sxs-lookup"><span data-stu-id="bd062-142">string</span></span> | <span data-ttu-id="bd062-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bd062-143">Required.</span></span> <span data-ttu-id="bd062-144">Die ID der zu löschenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="bd062-144">The ID of the submission to delete.</span></span> <span data-ttu-id="bd062-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bd062-145">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="bd062-146">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bd062-146">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="bd062-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="bd062-147">Request body</span></span>

<span data-ttu-id="bd062-148">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="bd062-148">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="bd062-149">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="bd062-149">Request example</span></span>

<span data-ttu-id="bd062-150">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Flight-Paketübermittlung löschen.</span><span class="sxs-lookup"><span data-stu-id="bd062-150">The following example demonstrates how to delete a submission for a package flight.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="bd062-151">Antwort</span><span class="sxs-lookup"><span data-stu-id="bd062-151">Response</span></span>

<span data-ttu-id="bd062-152">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="bd062-152">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="bd062-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="bd062-153">Error codes</span></span>

<span data-ttu-id="bd062-154">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="bd062-154">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="bd062-155">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="bd062-155">Error code</span></span> |  <span data-ttu-id="bd062-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd062-156">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="bd062-157">400</span><span class="sxs-lookup"><span data-stu-id="bd062-157">400</span></span>  | <span data-ttu-id="bd062-158">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="bd062-158">The request parameters are invalid.</span></span> |
| <span data-ttu-id="bd062-159">404</span><span class="sxs-lookup"><span data-stu-id="bd062-159">404</span></span>  | <span data-ttu-id="bd062-160">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="bd062-160">The specified submission could not be found.</span></span> |
| <span data-ttu-id="bd062-161">409</span><span class="sxs-lookup"><span data-stu-id="bd062-161">409</span></span>  | <span data-ttu-id="bd062-162">Die angegebene Übermittlung wurde gefunden, konnte jedoch nicht in ihrem aktuellen Zustand gelöscht werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="bd062-162">The specified submission was found but it could not be deleted in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="bd062-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bd062-163">Related topics</span></span>

* [<span data-ttu-id="bd062-164">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="bd062-164">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="bd062-165">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="bd062-165">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="bd062-166">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-166">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="bd062-167">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-167">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="bd062-168">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-168">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="bd062-169">Aktualisieren einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-169">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="bd062-170">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="bd062-170">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
