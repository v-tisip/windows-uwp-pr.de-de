---
author: Xansky
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur Fertigstellung des Paketrollouts für eine Flight-Paket-Übermittlung.
title: Abschließen des Rollouts für eine Flight-Paketübermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, Flight Übermittlung, fertigstellen
ms.assetid: e4a645f6-1f00-4af5-80d6-d2ee179acc8a
ms.localizationpriority: medium
ms.openlocfilehash: 896fec01072f23d11bf949626b309be836958beb
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5766929"
---
# <a name="finalize-the-rollout-for-a-flight-submission"></a><span data-ttu-id="d6c61-104">Abschließen des Rollouts für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="d6c61-104">Finalize the rollout for a flight submission</span></span>


<span data-ttu-id="d6c61-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur [Fertigstellung des Paketrollouts](../publish/gradual-package-rollout.md#completing-the-rollout) für eine Flight-Paketübermittlung.</span><span class="sxs-lookup"><span data-stu-id="d6c61-105">Use this method in the Microsoft Store submission API to [finalize the package rollout](../publish/gradual-package-rollout.md#completing-the-rollout) for a package flight submission.</span></span> <span data-ttu-id="d6c61-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="d6c61-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>


## <a name="prerequisites"></a><span data-ttu-id="d6c61-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d6c61-107">Prerequisites</span></span>

<span data-ttu-id="d6c61-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="d6c61-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="d6c61-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="d6c61-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="d6c61-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d6c61-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="d6c61-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="d6c61-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="d6c61-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="d6c61-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="d6c61-113">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="d6c61-113">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="d6c61-114">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="d6c61-114">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="d6c61-115">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d6c61-115">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="d6c61-116">Sie können dies im [Dev Center-Dashboard](../publish/gradual-package-rollout.md) oder durch [Verwenden der Microsoft Store-Übermittlungs-API](manage-flight-submissions.md#manage-gradual-package-rollout) durchführen.</span><span class="sxs-lookup"><span data-stu-id="d6c61-116">You can do this in the [Dev Center dashboard](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-flight-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="d6c61-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="d6c61-117">Request</span></span>

<span data-ttu-id="d6c61-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="d6c61-118">This method has the following syntax.</span></span> <span data-ttu-id="d6c61-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="d6c61-119">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="d6c61-120">Methode</span><span class="sxs-lookup"><span data-stu-id="d6c61-120">Method</span></span> | <span data-ttu-id="d6c61-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="d6c61-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="d6c61-122">POST</span><span class="sxs-lookup"><span data-stu-id="d6c61-122">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/finalizepackagerollout``` |


### <a name="request-header"></a><span data-ttu-id="d6c61-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="d6c61-123">Request header</span></span>

| <span data-ttu-id="d6c61-124">Header</span><span class="sxs-lookup"><span data-stu-id="d6c61-124">Header</span></span>        | <span data-ttu-id="d6c61-125">Typ</span><span class="sxs-lookup"><span data-stu-id="d6c61-125">Type</span></span>   | <span data-ttu-id="d6c61-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6c61-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d6c61-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="d6c61-127">Authorization</span></span> | <span data-ttu-id="d6c61-128">String</span><span class="sxs-lookup"><span data-stu-id="d6c61-128">string</span></span> | <span data-ttu-id="d6c61-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6c61-129">Required.</span></span> <span data-ttu-id="d6c61-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="d6c61-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="d6c61-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="d6c61-131">Request parameters</span></span>

| <span data-ttu-id="d6c61-132">Name</span><span class="sxs-lookup"><span data-stu-id="d6c61-132">Name</span></span>        | <span data-ttu-id="d6c61-133">Typ</span><span class="sxs-lookup"><span data-stu-id="d6c61-133">Type</span></span>   | <span data-ttu-id="d6c61-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6c61-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d6c61-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="d6c61-135">applicationId</span></span> | <span data-ttu-id="d6c61-136">String</span><span class="sxs-lookup"><span data-stu-id="d6c61-136">string</span></span> | <span data-ttu-id="d6c61-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6c61-137">Required.</span></span> <span data-ttu-id="d6c61-138">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout fertig gestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d6c61-138">The Store ID of the app that contains the package flight submission with the package rollout you want to finalize.</span></span> <span data-ttu-id="d6c61-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="d6c61-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="d6c61-140">flightId</span><span class="sxs-lookup"><span data-stu-id="d6c61-140">flightId</span></span> | <span data-ttu-id="d6c61-141">String</span><span class="sxs-lookup"><span data-stu-id="d6c61-141">string</span></span> | <span data-ttu-id="d6c61-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6c61-142">Required.</span></span> <span data-ttu-id="d6c61-143">Die ID des Flight-Pakets mit der Übermittlung, deren Paketrollout fertig gestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d6c61-143">The ID of the package flight that contains the submission with the package rollout you want to finalize.</span></span> <span data-ttu-id="d6c61-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="d6c61-144">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="d6c61-145">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d6c61-145">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span> |
| <span data-ttu-id="d6c61-146">submissionId</span><span class="sxs-lookup"><span data-stu-id="d6c61-146">submissionId</span></span> | <span data-ttu-id="d6c61-147">String</span><span class="sxs-lookup"><span data-stu-id="d6c61-147">string</span></span> | <span data-ttu-id="d6c61-148">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d6c61-148">Required.</span></span> <span data-ttu-id="d6c61-149">Die ID der Übermittlung mit dem Paketrollout, der fertig gestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d6c61-149">The ID of the submission with the package rollout you want to finalize.</span></span> <span data-ttu-id="d6c61-150">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d6c61-150">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="d6c61-151">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d6c61-151">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="d6c61-152">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="d6c61-152">Request body</span></span>

<span data-ttu-id="d6c61-153">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="d6c61-153">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="d6c61-154">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="d6c61-154">Request example</span></span>

<span data-ttu-id="d6c61-155">Im folgenden Beispiel wird die Fertigstellung des Paketrollouts für eine Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="d6c61-155">The following example demonstrates how to finalize the package rollout for a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243680/finalizepackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="d6c61-156">Antwort</span><span class="sxs-lookup"><span data-stu-id="d6c61-156">Response</span></span>

<span data-ttu-id="d6c61-157">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="d6c61-157">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="d6c61-158">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="d6c61-158">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 100.0,
    "packageRolloutStatus": "PackageRolloutComplete",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="d6c61-159">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="d6c61-159">Error codes</span></span>

<span data-ttu-id="d6c61-160">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="d6c61-160">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="d6c61-161">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="d6c61-161">Error code</span></span> |  <span data-ttu-id="d6c61-162">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6c61-162">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="d6c61-163">404</span><span class="sxs-lookup"><span data-stu-id="d6c61-163">404</span></span>  | <span data-ttu-id="d6c61-164">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d6c61-164">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="d6c61-165">409</span><span class="sxs-lookup"><span data-stu-id="d6c61-165">409</span></span>  | <span data-ttu-id="d6c61-166">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="d6c61-166">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="d6c61-167">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-flight-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="d6c61-167">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-flight-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="d6c61-168">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="d6c61-168">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="d6c61-169">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="d6c61-169">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="d6c61-170">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d6c61-170">Related topics</span></span>

* [<span data-ttu-id="d6c61-171">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="d6c61-171">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="d6c61-172">Verwalten von Flight-Paket-Übermittlungen mit der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="d6c61-172">Manage package flight submissions using the Microsoft Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="d6c61-173">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="d6c61-173">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
