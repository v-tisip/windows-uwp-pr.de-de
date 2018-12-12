---
ms.assetid: 1A69A388-B1CC-4D2C-886B-EA07E6E60252
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung.
title: Löschen einer Flight-Paketübermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Flight-Übermittlungen, löschen, Flight-Paket
ms.localizationpriority: medium
ms.openlocfilehash: 1222c730f4e7819037ee42fc0897cf2924586b25
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8933012"
---
# <a name="delete-a-package-flight-submission"></a><span data-ttu-id="4c67c-104">Löschen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-104">Delete a package flight submission</span></span>

<span data-ttu-id="4c67c-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="4c67c-105">Use this method in the Microsoft Store submission API to delete an existing package flight submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c67c-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="4c67c-106">Prerequisites</span></span>

<span data-ttu-id="4c67c-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="4c67c-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="4c67c-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="4c67c-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="4c67c-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4c67c-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="4c67c-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="4c67c-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="4c67c-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="4c67c-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="4c67c-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="4c67c-112">Request</span></span>

<span data-ttu-id="4c67c-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="4c67c-113">This method has the following syntax.</span></span> <span data-ttu-id="4c67c-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="4c67c-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="4c67c-115">Methode</span><span class="sxs-lookup"><span data-stu-id="4c67c-115">Method</span></span> | <span data-ttu-id="4c67c-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="4c67c-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="4c67c-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="4c67c-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationid}/flights/{flightId}/submissions/{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="4c67c-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="4c67c-118">Request header</span></span>

| <span data-ttu-id="4c67c-119">Header</span><span class="sxs-lookup"><span data-stu-id="4c67c-119">Header</span></span>        | <span data-ttu-id="4c67c-120">Typ</span><span class="sxs-lookup"><span data-stu-id="4c67c-120">Type</span></span>   | <span data-ttu-id="4c67c-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c67c-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="4c67c-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="4c67c-122">Authorization</span></span> | <span data-ttu-id="4c67c-123">String</span><span class="sxs-lookup"><span data-stu-id="4c67c-123">string</span></span> | <span data-ttu-id="4c67c-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4c67c-124">Required.</span></span> <span data-ttu-id="4c67c-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="4c67c-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="4c67c-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="4c67c-126">Request parameters</span></span>

| <span data-ttu-id="4c67c-127">Name</span><span class="sxs-lookup"><span data-stu-id="4c67c-127">Name</span></span>        | <span data-ttu-id="4c67c-128">Typ</span><span class="sxs-lookup"><span data-stu-id="4c67c-128">Type</span></span>   | <span data-ttu-id="4c67c-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c67c-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="4c67c-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="4c67c-130">applicationId</span></span> | <span data-ttu-id="4c67c-131">String</span><span class="sxs-lookup"><span data-stu-id="4c67c-131">string</span></span> | <span data-ttu-id="4c67c-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4c67c-132">Required.</span></span> <span data-ttu-id="4c67c-133">Die Store-ID der App, die die zu löschende Flight-Paketübermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="4c67c-133">The Store ID of the app that contains the package flight submission you want to delete.</span></span> <span data-ttu-id="4c67c-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="4c67c-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="4c67c-135">flightId</span><span class="sxs-lookup"><span data-stu-id="4c67c-135">flightId</span></span> | <span data-ttu-id="4c67c-136">String</span><span class="sxs-lookup"><span data-stu-id="4c67c-136">string</span></span> | <span data-ttu-id="4c67c-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4c67c-137">Required.</span></span> <span data-ttu-id="4c67c-138">Die ID des Flight-Pakets, das die zu löschende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="4c67c-138">The ID of the package flight that contains the submission to delete.</span></span> <span data-ttu-id="4c67c-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="4c67c-139">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="4c67c-140">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Test-Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4c67c-140">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center.</span></span>  |
| <span data-ttu-id="4c67c-141">submissionId</span><span class="sxs-lookup"><span data-stu-id="4c67c-141">submissionId</span></span> | <span data-ttu-id="4c67c-142">String</span><span class="sxs-lookup"><span data-stu-id="4c67c-142">string</span></span> | <span data-ttu-id="4c67c-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4c67c-143">Required.</span></span> <span data-ttu-id="4c67c-144">Die ID der zu löschenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="4c67c-144">The ID of the submission to delete.</span></span> <span data-ttu-id="4c67c-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4c67c-145">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="4c67c-146">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4c67c-146">For a submission that was created in  Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="4c67c-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="4c67c-147">Request body</span></span>

<span data-ttu-id="4c67c-148">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="4c67c-148">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="4c67c-149">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="4c67c-149">Request example</span></span>

<span data-ttu-id="4c67c-150">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Flight-Paketübermittlung löschen.</span><span class="sxs-lookup"><span data-stu-id="4c67c-150">The following example demonstrates how to delete a submission for a package flight.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="4c67c-151">Antwort</span><span class="sxs-lookup"><span data-stu-id="4c67c-151">Response</span></span>

<span data-ttu-id="4c67c-152">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="4c67c-152">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="4c67c-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="4c67c-153">Error codes</span></span>

<span data-ttu-id="4c67c-154">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="4c67c-154">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="4c67c-155">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="4c67c-155">Error code</span></span> |  <span data-ttu-id="4c67c-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c67c-156">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="4c67c-157">400</span><span class="sxs-lookup"><span data-stu-id="4c67c-157">400</span></span>  | <span data-ttu-id="4c67c-158">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="4c67c-158">The request parameters are invalid.</span></span> |
| <span data-ttu-id="4c67c-159">404</span><span class="sxs-lookup"><span data-stu-id="4c67c-159">404</span></span>  | <span data-ttu-id="4c67c-160">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="4c67c-160">The specified submission could not be found.</span></span> |
| <span data-ttu-id="4c67c-161">409</span><span class="sxs-lookup"><span data-stu-id="4c67c-161">409</span></span>  | <span data-ttu-id="4c67c-162">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand gelöscht werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="4c67c-162">The specified submission was found but it could not be deleted in its current state, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="4c67c-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="4c67c-163">Related topics</span></span>

* [<span data-ttu-id="4c67c-164">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="4c67c-164">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="4c67c-165">Verwalten von Flight-Paketübermittlungen</span><span class="sxs-lookup"><span data-stu-id="4c67c-165">Manage package flight submissions</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="4c67c-166">Abrufen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-166">Get a package flight submission</span></span>](get-a-flight-submission.md)
* [<span data-ttu-id="4c67c-167">Erstellen einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-167">Create a package flight submission</span></span>](create-a-flight-submission.md)
* [<span data-ttu-id="4c67c-168">Ausführen eines Commit für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-168">Commit a package flight submission</span></span>](commit-a-flight-submission.md)
* [<span data-ttu-id="4c67c-169">Aktualisieren einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-169">Update a package flight submission</span></span>](update-a-flight-submission.md)
* [<span data-ttu-id="4c67c-170">Abrufen des Status einer Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="4c67c-170">Get the status of a package flight submission</span></span>](get-status-for-a-flight-submission.md)
