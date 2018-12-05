---
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um das Paketrollout für ein Flight-Paket anzuhalten.
title: Anhalten des Rollouts für ein Test-Flight
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, Flight-Übermittlung, anhalten
ms.assetid: f8ee0687-a421-48e7-a6eb-3fd5633c352b
ms.localizationpriority: medium
ms.openlocfilehash: 74c95e36d0bc4c9848be1e336b2e34c41dc0631f
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8709924"
---
# <a name="halt-the-rollout-for-a-flight"></a><span data-ttu-id="deca1-104">Anhalten des Rollouts für ein Test-Flight</span><span class="sxs-lookup"><span data-stu-id="deca1-104">Halt the rollout for a flight</span></span>

<span data-ttu-id="deca1-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum [Anhalten des Rollouts](../publish/gradual-package-rollout.md#completing-the-rollout) für eine Flight-Paket-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="deca1-105">Use this method in the Microsoft Store submission API to [halt the rollout](../publish/gradual-package-rollout.md#completing-the-rollout) for a package flight submission.</span></span> <span data-ttu-id="deca1-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="deca1-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="deca1-107">Wenn Sie das Rollout für eine Flight-Paket-Übermittlung anhalten und dann [eine neue Flight-Paket-Übermittlung](create-a-flight-submission.md) erstellen, ist die neue Übermittlung ein Klon der angehaltenen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="deca1-107">If you halt the rollout for a package flight submission and then [create a new package flight submission](create-a-flight-submission.md), the new submission is a clone of the halted submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="deca1-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="deca1-108">Prerequisites</span></span>

<span data-ttu-id="deca1-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="deca1-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="deca1-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="deca1-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="deca1-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="deca1-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="deca1-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="deca1-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="deca1-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="deca1-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="deca1-114">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="deca1-114">Create a submission for one of your apps.</span></span> <span data-ttu-id="deca1-115">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="deca1-115">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="deca1-116">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="deca1-116">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="deca1-117">Sie können diese [im Partner Center](../publish/gradual-package-rollout.md), oder Sie können dies tun, indem Sie [mithilfe der Microsoft Store-Übermittlungs-API](manage-flight-submissions.md#manage-gradual-package-rollout).</span><span class="sxs-lookup"><span data-stu-id="deca1-117">You can do this [in Partner Center](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-flight-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="deca1-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="deca1-118">Request</span></span>

<span data-ttu-id="deca1-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="deca1-119">This method has the following syntax.</span></span> <span data-ttu-id="deca1-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="deca1-120">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="deca1-121">Methode</span><span class="sxs-lookup"><span data-stu-id="deca1-121">Method</span></span> | <span data-ttu-id="deca1-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="deca1-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="deca1-123">POST</span><span class="sxs-lookup"><span data-stu-id="deca1-123">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/haltpackagerollout``` |


### <a name="request-header"></a><span data-ttu-id="deca1-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="deca1-124">Request header</span></span>

| <span data-ttu-id="deca1-125">Header</span><span class="sxs-lookup"><span data-stu-id="deca1-125">Header</span></span>        | <span data-ttu-id="deca1-126">Typ</span><span class="sxs-lookup"><span data-stu-id="deca1-126">Type</span></span>   | <span data-ttu-id="deca1-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="deca1-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="deca1-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="deca1-128">Authorization</span></span> | <span data-ttu-id="deca1-129">String</span><span class="sxs-lookup"><span data-stu-id="deca1-129">string</span></span> | <span data-ttu-id="deca1-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="deca1-130">Required.</span></span> <span data-ttu-id="deca1-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="deca1-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="deca1-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="deca1-132">Request parameters</span></span>

| <span data-ttu-id="deca1-133">Name</span><span class="sxs-lookup"><span data-stu-id="deca1-133">Name</span></span>        | <span data-ttu-id="deca1-134">Typ</span><span class="sxs-lookup"><span data-stu-id="deca1-134">Type</span></span>   | <span data-ttu-id="deca1-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="deca1-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="deca1-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="deca1-136">applicationId</span></span> | <span data-ttu-id="deca1-137">String</span><span class="sxs-lookup"><span data-stu-id="deca1-137">string</span></span> | <span data-ttu-id="deca1-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="deca1-138">Required.</span></span> <span data-ttu-id="deca1-139">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="deca1-139">The Store ID of the app that contains the package flight submission with the package rollout you want to halt.</span></span> <span data-ttu-id="deca1-140">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="deca1-140">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="deca1-141">flightId</span><span class="sxs-lookup"><span data-stu-id="deca1-141">flightId</span></span> | <span data-ttu-id="deca1-142">String</span><span class="sxs-lookup"><span data-stu-id="deca1-142">string</span></span> | <span data-ttu-id="deca1-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="deca1-143">Required.</span></span> <span data-ttu-id="deca1-144">Die Store-ID des Flight-Pakets mit der Übermittlung, deren Paketrollout angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="deca1-144">The ID of the package flight that contains the submission with the package rollout you want to halt.</span></span> <span data-ttu-id="deca1-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="deca1-145">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="deca1-146">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Test-Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="deca1-146">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center.</span></span>   |
| <span data-ttu-id="deca1-147">submissionId</span><span class="sxs-lookup"><span data-stu-id="deca1-147">submissionId</span></span> | <span data-ttu-id="deca1-148">String</span><span class="sxs-lookup"><span data-stu-id="deca1-148">string</span></span> | <span data-ttu-id="deca1-149">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="deca1-149">Required.</span></span> <span data-ttu-id="deca1-150">Die ID der Übermittlung mit dem Paketrollout, das angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="deca1-150">The ID of the submission with the package rollout to halt.</span></span> <span data-ttu-id="deca1-151">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="deca1-151">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="deca1-152">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="deca1-152">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="deca1-153">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="deca1-153">Request body</span></span>

<span data-ttu-id="deca1-154">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="deca1-154">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="deca1-155">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="deca1-155">Request example</span></span>

<span data-ttu-id="deca1-156">Im folgenden Beispiel wird das Anhalten des Paketrollouts einer Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="deca1-156">The following example demonstrates how to halt the package rollout for a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243680/haltpackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="deca1-157">Antwort</span><span class="sxs-lookup"><span data-stu-id="deca1-157">Response</span></span>

<span data-ttu-id="deca1-158">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="deca1-158">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="deca1-159">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="deca1-159">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutStopped",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="deca1-160">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="deca1-160">Error codes</span></span>

<span data-ttu-id="deca1-161">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="deca1-161">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="deca1-162">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="deca1-162">Error code</span></span> |  <span data-ttu-id="deca1-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="deca1-163">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="deca1-164">404</span><span class="sxs-lookup"><span data-stu-id="deca1-164">404</span></span>  | <span data-ttu-id="deca1-165">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="deca1-165">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="deca1-166">409</span><span class="sxs-lookup"><span data-stu-id="deca1-166">409</span></span>  | <span data-ttu-id="deca1-167">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="deca1-167">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="deca1-168">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-flight-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="deca1-168">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-flight-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="deca1-169">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="deca1-169">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="deca1-170">Die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="deca1-170">The app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="deca1-171">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="deca1-171">Related topics</span></span>

* [<span data-ttu-id="deca1-172">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="deca1-172">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="deca1-173">Verwalten von Flight-Paket-Übermittlungen mit der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="deca1-173">Manage package flight submissions using the Microsoft Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="deca1-174">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="deca1-174">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
