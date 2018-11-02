---
author: Xansky
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um das Paketrollout für ein Flight-Paket anzuhalten.
title: Anhalten des Rollouts für ein Test-Flight
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, Flight-Übermittlung, anhalten
ms.assetid: f8ee0687-a421-48e7-a6eb-3fd5633c352b
ms.localizationpriority: medium
ms.openlocfilehash: a10b6f75d944a4a0f2935568928ce3b0782a479a
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5936276"
---
# <a name="halt-the-rollout-for-a-flight"></a><span data-ttu-id="d0146-104">Anhalten des Rollouts für ein Test-Flight</span><span class="sxs-lookup"><span data-stu-id="d0146-104">Halt the rollout for a flight</span></span>

<span data-ttu-id="d0146-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum [Anhalten des Rollouts](../publish/gradual-package-rollout.md#completing-the-rollout) für eine Flight-Paket-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d0146-105">Use this method in the Microsoft Store submission API to [halt the rollout](../publish/gradual-package-rollout.md#completing-the-rollout) for a package flight submission.</span></span> <span data-ttu-id="d0146-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="d0146-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d0146-107">Wenn Sie das Rollout für eine Flight-Paket-Übermittlung anhalten und dann [eine neue Flight-Paket-Übermittlung](create-a-flight-submission.md) erstellen, ist die neue Übermittlung ein Klon der angehaltenen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d0146-107">If you halt the rollout for a package flight submission and then [create a new package flight submission](create-a-flight-submission.md), the new submission is a clone of the halted submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0146-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d0146-108">Prerequisites</span></span>

<span data-ttu-id="d0146-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="d0146-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="d0146-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="d0146-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="d0146-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d0146-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="d0146-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="d0146-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="d0146-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="d0146-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="d0146-114">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="d0146-114">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="d0146-115">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="d0146-115">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="d0146-116">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="d0146-116">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="d0146-117">Sie können dies im [Dev Center-Dashboard](../publish/gradual-package-rollout.md) oder durch [Verwenden der Microsoft Store-Übermittlungs-API](manage-flight-submissions.md#manage-gradual-package-rollout) durchführen.</span><span class="sxs-lookup"><span data-stu-id="d0146-117">You can do this in the [Dev Center dashboard](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-flight-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="d0146-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="d0146-118">Request</span></span>

<span data-ttu-id="d0146-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="d0146-119">This method has the following syntax.</span></span> <span data-ttu-id="d0146-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="d0146-120">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="d0146-121">Methode</span><span class="sxs-lookup"><span data-stu-id="d0146-121">Method</span></span> | <span data-ttu-id="d0146-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="d0146-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="d0146-123">POST</span><span class="sxs-lookup"><span data-stu-id="d0146-123">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/haltpackagerollout``` |


### <a name="request-header"></a><span data-ttu-id="d0146-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="d0146-124">Request header</span></span>

| <span data-ttu-id="d0146-125">Header</span><span class="sxs-lookup"><span data-stu-id="d0146-125">Header</span></span>        | <span data-ttu-id="d0146-126">Typ</span><span class="sxs-lookup"><span data-stu-id="d0146-126">Type</span></span>   | <span data-ttu-id="d0146-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0146-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d0146-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="d0146-128">Authorization</span></span> | <span data-ttu-id="d0146-129">String</span><span class="sxs-lookup"><span data-stu-id="d0146-129">string</span></span> | <span data-ttu-id="d0146-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0146-130">Required.</span></span> <span data-ttu-id="d0146-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="d0146-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="d0146-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="d0146-132">Request parameters</span></span>

| <span data-ttu-id="d0146-133">Name</span><span class="sxs-lookup"><span data-stu-id="d0146-133">Name</span></span>        | <span data-ttu-id="d0146-134">Typ</span><span class="sxs-lookup"><span data-stu-id="d0146-134">Type</span></span>   | <span data-ttu-id="d0146-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0146-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="d0146-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="d0146-136">applicationId</span></span> | <span data-ttu-id="d0146-137">String</span><span class="sxs-lookup"><span data-stu-id="d0146-137">string</span></span> | <span data-ttu-id="d0146-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0146-138">Required.</span></span> <span data-ttu-id="d0146-139">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="d0146-139">The Store ID of the app that contains the package flight submission with the package rollout you want to halt.</span></span> <span data-ttu-id="d0146-140">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="d0146-140">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="d0146-141">flightId</span><span class="sxs-lookup"><span data-stu-id="d0146-141">flightId</span></span> | <span data-ttu-id="d0146-142">String</span><span class="sxs-lookup"><span data-stu-id="d0146-142">string</span></span> | <span data-ttu-id="d0146-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0146-143">Required.</span></span> <span data-ttu-id="d0146-144">Die Store-ID des Flight-Pakets mit der Übermittlung, deren Paketrollout angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="d0146-144">The ID of the package flight that contains the submission with the package rollout you want to halt.</span></span> <span data-ttu-id="d0146-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="d0146-145">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="d0146-146">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d0146-146">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>   |
| <span data-ttu-id="d0146-147">submissionId</span><span class="sxs-lookup"><span data-stu-id="d0146-147">submissionId</span></span> | <span data-ttu-id="d0146-148">String</span><span class="sxs-lookup"><span data-stu-id="d0146-148">string</span></span> | <span data-ttu-id="d0146-149">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0146-149">Required.</span></span> <span data-ttu-id="d0146-150">Die ID der Übermittlung mit dem Paketrollout, das angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="d0146-150">The ID of the submission with the package rollout to halt.</span></span> <span data-ttu-id="d0146-151">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d0146-151">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="d0146-152">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d0146-152">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="d0146-153">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="d0146-153">Request body</span></span>

<span data-ttu-id="d0146-154">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="d0146-154">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="d0146-155">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="d0146-155">Request example</span></span>

<span data-ttu-id="d0146-156">Im folgenden Beispiel wird das Anhalten des Paketrollouts einer Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="d0146-156">The following example demonstrates how to halt the package rollout for a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243680/haltpackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="d0146-157">Antwort</span><span class="sxs-lookup"><span data-stu-id="d0146-157">Response</span></span>

<span data-ttu-id="d0146-158">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="d0146-158">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="d0146-159">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="d0146-159">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutStopped",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="d0146-160">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="d0146-160">Error codes</span></span>

<span data-ttu-id="d0146-161">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="d0146-161">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="d0146-162">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="d0146-162">Error code</span></span> |  <span data-ttu-id="d0146-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d0146-163">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="d0146-164">404</span><span class="sxs-lookup"><span data-stu-id="d0146-164">404</span></span>  | <span data-ttu-id="d0146-165">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="d0146-165">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="d0146-166">409</span><span class="sxs-lookup"><span data-stu-id="d0146-166">409</span></span>  | <span data-ttu-id="d0146-167">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="d0146-167">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="d0146-168">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-flight-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="d0146-168">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-flight-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="d0146-169">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="d0146-169">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="d0146-170">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="d0146-170">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="d0146-171">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d0146-171">Related topics</span></span>

* [<span data-ttu-id="d0146-172">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="d0146-172">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="d0146-173">Verwalten von Flight-Paket-Übermittlungen mit der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="d0146-173">Manage package flight submissions using the Microsoft Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="d0146-174">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="d0146-174">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
