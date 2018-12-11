---
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Paketrollout-Informationen für eine Flight-Paket-Übermittlung abzurufen.
title: Abrufen von Rolloutinformationen für eine Flight-Paketübermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, Flight-Übermittlung
ms.assetid: 397f1b99-2be7-4f65-bcf1-9433a3d496ad
ms.localizationpriority: medium
ms.openlocfilehash: 4e60ecfccecda850a5c83e5840626e1b789a068d
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8887450"
---
# <a name="get-rollout-info-for-a-flight-submission"></a><span data-ttu-id="b58ca-104">Abrufen von Rolloutinformationen für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="b58ca-104">Get rollout info for a flight submission</span></span>


<span data-ttu-id="b58ca-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um [Paketrollout](../publish/gradual-package-rollout.md)-Informationen für eine Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b58ca-105">Use this method in the Microsoft Store submission API to get [package rollout](../publish/gradual-package-rollout.md) info for a package flight submission.</span></span> <span data-ttu-id="b58ca-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="b58ca-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b58ca-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b58ca-107">Prerequisites</span></span>

<span data-ttu-id="b58ca-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="b58ca-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="b58ca-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="b58ca-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="b58ca-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b58ca-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="b58ca-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="b58ca-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="b58ca-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="b58ca-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="b58ca-113">Erstellen Sie eine Test-Flight-Paketübermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="b58ca-113">Create a package flight submission for one of your apps.</span></span> <span data-ttu-id="b58ca-114">Sie dazu im Partner Center, oder Sie können dies tun, indem Sie mit der Methode [Erstellen Sie eine Test-Flight-Paketübermittlung](create-a-flight-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="b58ca-114">You can do this in Partner Center, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="b58ca-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="b58ca-115">Request</span></span>

<span data-ttu-id="b58ca-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="b58ca-116">This method has the following syntax.</span></span> <span data-ttu-id="b58ca-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="b58ca-117">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="b58ca-118">Methode</span><span class="sxs-lookup"><span data-stu-id="b58ca-118">Method</span></span> | <span data-ttu-id="b58ca-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="b58ca-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="b58ca-120">GET</span><span class="sxs-lookup"><span data-stu-id="b58ca-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/packagerollout   ``` |


### <a name="request-header"></a><span data-ttu-id="b58ca-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="b58ca-121">Request header</span></span>

| <span data-ttu-id="b58ca-122">Header</span><span class="sxs-lookup"><span data-stu-id="b58ca-122">Header</span></span>        | <span data-ttu-id="b58ca-123">Typ</span><span class="sxs-lookup"><span data-stu-id="b58ca-123">Type</span></span>   | <span data-ttu-id="b58ca-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b58ca-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="b58ca-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="b58ca-125">Authorization</span></span> | <span data-ttu-id="b58ca-126">String</span><span class="sxs-lookup"><span data-stu-id="b58ca-126">string</span></span> | <span data-ttu-id="b58ca-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b58ca-127">Required.</span></span> <span data-ttu-id="b58ca-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="b58ca-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="b58ca-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="b58ca-129">Request parameters</span></span>

| <span data-ttu-id="b58ca-130">Name</span><span class="sxs-lookup"><span data-stu-id="b58ca-130">Name</span></span>        | <span data-ttu-id="b58ca-131">Typ</span><span class="sxs-lookup"><span data-stu-id="b58ca-131">Type</span></span>   | <span data-ttu-id="b58ca-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b58ca-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="b58ca-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="b58ca-133">applicationId</span></span> | <span data-ttu-id="b58ca-134">String</span><span class="sxs-lookup"><span data-stu-id="b58ca-134">string</span></span> | <span data-ttu-id="b58ca-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b58ca-135">Required.</span></span> <span data-ttu-id="b58ca-136">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b58ca-136">The Store ID of the app that contains the package flight submission with the package rollout info you want to get.</span></span> <span data-ttu-id="b58ca-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="b58ca-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="b58ca-138">flightId</span><span class="sxs-lookup"><span data-stu-id="b58ca-138">flightId</span></span> | <span data-ttu-id="b58ca-139">String</span><span class="sxs-lookup"><span data-stu-id="b58ca-139">string</span></span> | <span data-ttu-id="b58ca-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b58ca-140">Required.</span></span> <span data-ttu-id="b58ca-141">Die Store-ID des Flight-Pakets mit der Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b58ca-141">The ID of the package flight that contains the submission with the package rollout info you want to get.</span></span> <span data-ttu-id="b58ca-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="b58ca-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="b58ca-143">Für einen Flight, der im Partner Center erstellt wurde, ist diese ID auch in der URL für die Test-Flight-Seite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b58ca-143">For a flight that was created in Partner Center, this ID is also available in the URL for the flight page in Partner Center .</span></span>    |
| <span data-ttu-id="b58ca-144">submissionId</span><span class="sxs-lookup"><span data-stu-id="b58ca-144">submissionId</span></span> | <span data-ttu-id="b58ca-145">String</span><span class="sxs-lookup"><span data-stu-id="b58ca-145">string</span></span> | <span data-ttu-id="b58ca-146">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b58ca-146">Required.</span></span> <span data-ttu-id="b58ca-147">Die ID der Übermittlung mit den abzurufenden Paketrollout-Informationen.</span><span class="sxs-lookup"><span data-stu-id="b58ca-147">The ID of the submission with the package rollout info to get.</span></span> <span data-ttu-id="b58ca-148">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b58ca-148">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="b58ca-149">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b58ca-149">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>   |


### <a name="request-body"></a><span data-ttu-id="b58ca-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="b58ca-150">Request body</span></span>

<span data-ttu-id="b58ca-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="b58ca-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="b58ca-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="b58ca-152">Request example</span></span>

<span data-ttu-id="b58ca-153">Im folgenden Beispiel wird das Abrufen der Paketrollout-Informationen einer Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="b58ca-153">The following example demonstrates how to get the package rollout info for a package flight submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/packagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="b58ca-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="b58ca-154">Response</span></span>

<span data-ttu-id="b58ca-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode für eine Flight-Paket-Übermittlung mit aktiviertem schrittweisem Paketrollout.</span><span class="sxs-lookup"><span data-stu-id="b58ca-155">The following example demonstrates the JSON response body for a successful call to this method for a package flight submission with gradual package rollout enabled.</span></span> <span data-ttu-id="b58ca-156">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Paketrollout-Ressource](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="b58ca-156">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

<span data-ttu-id="b58ca-157">Ist für die Flight-Paket-Übermittlung schrittweises Paketrollout nicht aktiviert, wird folgender Antworttext zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b58ca-157">If the package flight submission does not have gradual package rollout enabled, the following response body will be returned.</span></span>

```json
{
    "isPackageRollout": false,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutNotStarted",
    "fallbackSubmissionId": "0"
}
```

## <a name="error-codes"></a><span data-ttu-id="b58ca-158">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="b58ca-158">Error codes</span></span>

<span data-ttu-id="b58ca-159">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="b58ca-159">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="b58ca-160">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="b58ca-160">Error code</span></span> |  <span data-ttu-id="b58ca-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b58ca-161">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="b58ca-162">404</span><span class="sxs-lookup"><span data-stu-id="b58ca-162">404</span></span>  | <span data-ttu-id="b58ca-163">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="b58ca-163">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="b58ca-164">409</span><span class="sxs-lookup"><span data-stu-id="b58ca-164">409</span></span>  | <span data-ttu-id="b58ca-165">Die Flight-Paketübermittlung gehört nicht zum das angegebene Flight-Paket, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="b58ca-165">The package flight submission does not belong to the specified package flight, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="b58ca-166">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b58ca-166">Related topics</span></span>

* [<span data-ttu-id="b58ca-167">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="b58ca-167">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="b58ca-168">Verwalten von Flight-Paket-Übermittlungen mit der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="b58ca-168">Manage package flight submissions using the Microsoft Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="b58ca-169">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="b58ca-169">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
