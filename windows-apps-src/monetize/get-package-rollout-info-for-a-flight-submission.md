---
author: mcleanbyron
description: "Verwenden Sie diese Methode der Windows Store-Übermittlungs-API, um Paketrollout-Informationen für eine Flight-Paket-Übermittlung abzurufen."
title: "Abrufen von Rolloutinformationen für eine Flight-Paketübermittlung"
ms.author: mcleans
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Paketrollout, Flight-Übermittlung"
ms.assetid: 397f1b99-2be7-4f65-bcf1-9433a3d496ad
ms.openlocfilehash: f9245f5887521535da77c5d7e4d795e15ce8d2b4
ms.sourcegitcommit: a8e7dc247196eee79b67aaae2b2a4496c54ce253
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="get-rollout-info-for-a-flight-submission"></a><span data-ttu-id="19143-104">Abrufen von Rolloutinformationen für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="19143-104">Get rollout info for a flight submission</span></span>


<span data-ttu-id="19143-105">Verwenden Sie diese Methode der Windows Store-Übermittlungs-API, um [Paketrollout](../publish/gradual-package-rollout.md)-Informationen für eine Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="19143-105">Use this method in the Windows Store submission API to get [package rollout](../publish/gradual-package-rollout.md) info for a package flight submission.</span></span> <span data-ttu-id="19143-106">Weitere Informationen zum Erstellungsprozess einer Flight-Paket-Übermittlung mithilfe der Windows Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paket-Übermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="19143-106">For more information about the process of process of creating a package flight submission by using the Windows Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19143-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="19143-107">Prerequisites</span></span>

<span data-ttu-id="19143-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="19143-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="19143-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="19143-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="19143-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="19143-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="19143-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="19143-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="19143-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="19143-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="19143-113">Erstellen Sie eine Flight-Paketübermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="19143-113">Create a package flight submission for an app in your Dev Center account.</span></span> <span data-ttu-id="19143-114">Sie können dies im Dev Center-Dashboard oder unter Verwendung der Methode [Erstellen einer Flight-Paketübermittlung](create-a-flight-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="19143-114">You can do this in the Dev Center dashboard, or you can do this by using the [create a package flight submission](create-a-flight-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="19143-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="19143-115">Request</span></span>

<span data-ttu-id="19143-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="19143-116">This method has the following syntax.</span></span> <span data-ttu-id="19143-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="19143-117">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="19143-118">Methode</span><span class="sxs-lookup"><span data-stu-id="19143-118">Method</span></span> | <span data-ttu-id="19143-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="19143-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="19143-120">GET</span><span class="sxs-lookup"><span data-stu-id="19143-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/packagerollout   ``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="19143-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="19143-121">Request header</span></span>

| <span data-ttu-id="19143-122">Header</span><span class="sxs-lookup"><span data-stu-id="19143-122">Header</span></span>        | <span data-ttu-id="19143-123">Typ</span><span class="sxs-lookup"><span data-stu-id="19143-123">Type</span></span>   | <span data-ttu-id="19143-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19143-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="19143-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="19143-125">Authorization</span></span> | <span data-ttu-id="19143-126">String</span><span class="sxs-lookup"><span data-stu-id="19143-126">string</span></span> | <span data-ttu-id="19143-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="19143-127">Required.</span></span> <span data-ttu-id="19143-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="19143-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="19143-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="19143-129">Request parameters</span></span>

| <span data-ttu-id="19143-130">Name</span><span class="sxs-lookup"><span data-stu-id="19143-130">Name</span></span>        | <span data-ttu-id="19143-131">Typ</span><span class="sxs-lookup"><span data-stu-id="19143-131">Type</span></span>   | <span data-ttu-id="19143-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19143-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="19143-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="19143-133">applicationId</span></span> | <span data-ttu-id="19143-134">String</span><span class="sxs-lookup"><span data-stu-id="19143-134">string</span></span> | <span data-ttu-id="19143-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="19143-135">Required.</span></span> <span data-ttu-id="19143-136">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="19143-136">The Store ID of the app that contains the package flight submission with the package rollout info you want to get.</span></span> <span data-ttu-id="19143-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="19143-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="19143-138">flightId</span><span class="sxs-lookup"><span data-stu-id="19143-138">flightId</span></span> | <span data-ttu-id="19143-139">String</span><span class="sxs-lookup"><span data-stu-id="19143-139">string</span></span> | <span data-ttu-id="19143-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="19143-140">Required.</span></span> <span data-ttu-id="19143-141">Die Store-ID des Flight-Pakets mit der Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="19143-141">The ID of the package flight that contains the submission with the package rollout info you want to get.</span></span> <span data-ttu-id="19143-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="19143-142">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span>  |
| <span data-ttu-id="19143-143">submissionId</span><span class="sxs-lookup"><span data-stu-id="19143-143">submissionId</span></span> | <span data-ttu-id="19143-144">String</span><span class="sxs-lookup"><span data-stu-id="19143-144">string</span></span> | <span data-ttu-id="19143-145">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="19143-145">Required.</span></span> <span data-ttu-id="19143-146">Die ID der Übermittlung mit den abzurufenden Paketrollout-Informationen.</span><span class="sxs-lookup"><span data-stu-id="19143-146">The ID of the submission with the package rollout info to get.</span></span> <span data-ttu-id="19143-147">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="19143-147">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="19143-148">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="19143-148">Request body</span></span>

<span data-ttu-id="19143-149">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="19143-149">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="19143-150">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="19143-150">Request example</span></span>

<span data-ttu-id="19143-151">Im folgenden Beispiel wird das Abrufen der Paketrollout-Informationen einer Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="19143-151">The following example demonstrates how to get the package rollout info for a package flight submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243649/packagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="19143-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="19143-152">Response</span></span>

<span data-ttu-id="19143-153">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode für eine Flight-Paket-Übermittlung mit aktiviertem schrittweisem Paketrollout.</span><span class="sxs-lookup"><span data-stu-id="19143-153">The following example demonstrates the JSON response body for a successful call to this method for a package flight submission with gradual package rollout enabled.</span></span> <span data-ttu-id="19143-154">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Paketrollout-Ressource](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="19143-154">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

<span data-ttu-id="19143-155">Ist für die Flight-Paket-Übermittlung schrittweises Paketrollout nicht aktiviert, wird folgender Antworttext zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="19143-155">If the package flight submission does not have gradual package rollout enabled, the following response body will be returned.</span></span>

```json
{
    "isPackageRollout": false,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutNotStarted",
    "fallbackSubmissionId": "0"
}
```

## <a name="error-codes"></a><span data-ttu-id="19143-156">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="19143-156">Error codes</span></span>

<span data-ttu-id="19143-157">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="19143-157">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="19143-158">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="19143-158">Error code</span></span> |  <span data-ttu-id="19143-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19143-159">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="19143-160">404</span><span class="sxs-lookup"><span data-stu-id="19143-160">404</span></span>  | <span data-ttu-id="19143-161">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="19143-161">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="19143-162">409</span><span class="sxs-lookup"><span data-stu-id="19143-162">409</span></span>  | <span data-ttu-id="19143-163">Die Flight-Paket-Übermittlung gehört nicht zum angegebenen Flight-Paket, oder die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="19143-163">The package flight submission does not belong to the specified package flight, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   

<span/>


## <a name="related-topics"></a><span data-ttu-id="19143-164">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="19143-164">Related topics</span></span>

* [<span data-ttu-id="19143-165">Schrittweises Paketrollout</span><span class="sxs-lookup"><span data-stu-id="19143-165">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="19143-166">Verwalten von Flight-Paket-Übermittlungen mit der Windows Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="19143-166">Manage package flight submissions using the Windows Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="19143-167">Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="19143-167">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
