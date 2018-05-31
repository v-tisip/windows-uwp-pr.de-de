---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um den Paketrollout-Prozentsatz für eine Flight-Paket-Übermittlung zu aktualisieren.
title: Aktualisieren des Prozentsatzes eines Rollouts für eine Flight-Paketübermittlung
ms.author: mcleans
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paket-Rollout, Test-Flight-Übermittlung, Aktualisieren, Prozentsatz
ms.assetid: ee9aa223-e945-4c11-b430-1f4b1e559743
ms.localizationpriority: medium
ms.openlocfilehash: f028e1632eb0a330f9d4b282aa3f8968eff647de
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1815975"
---
# <a name="update-the-rollout-percentage-for-a-flight-submission"></a><span data-ttu-id="cba09-104">Aktualisieren des Prozentsatzes eines Rollouts für eine Flight-Paketübermittlung</span><span class="sxs-lookup"><span data-stu-id="cba09-104">Update the rollout percentage for a flight submission</span></span>


<span data-ttu-id="cba09-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum [Aktualisieren des Rollout-Prozentsatzes](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) für eine Flight-Paket-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="cba09-105">Use this method in the Microsoft Store submission API to [update the rollout percentage](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) for a package flight submission.</span></span> <span data-ttu-id="cba09-106">Weitere Informationen über den Erstellungsprozess einer Flight-Paketübermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von Flight-Paketübermittlungen](manage-flight-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="cba09-106">For more information about the process of process of creating a package flight submission by using the Microsoft Store submission API, see [Manage package flight submissions](manage-flight-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cba09-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="cba09-107">Prerequisites</span></span>

<span data-ttu-id="cba09-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="cba09-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="cba09-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="cba09-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="cba09-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cba09-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="cba09-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="cba09-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="cba09-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="cba09-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="cba09-113">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="cba09-113">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="cba09-114">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="cba09-114">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="cba09-115">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="cba09-115">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="cba09-116">Sie können dies im [Dev Center-Dashboard](../publish/gradual-package-rollout.md) oder durch [Verwenden der Microsoft Store-Übermittlungs-API](manage-flight-submissions.md#manage-gradual-package-rollout) durchführen.</span><span class="sxs-lookup"><span data-stu-id="cba09-116">You can do this in the [Dev Center dashboard](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-flight-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="cba09-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="cba09-117">Request</span></span>

<span data-ttu-id="cba09-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="cba09-118">This method has the following syntax.</span></span> <span data-ttu-id="cba09-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="cba09-119">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="cba09-120">Methode</span><span class="sxs-lookup"><span data-stu-id="cba09-120">Method</span></span> | <span data-ttu-id="cba09-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="cba09-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="cba09-122">POST</span><span class="sxs-lookup"><span data-stu-id="cba09-122">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}/submissions/{submissionId}/updatepackagerolloutpercentage``` |


### <a name="request-header"></a><span data-ttu-id="cba09-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="cba09-123">Request header</span></span>

| <span data-ttu-id="cba09-124">Header</span><span class="sxs-lookup"><span data-stu-id="cba09-124">Header</span></span>        | <span data-ttu-id="cba09-125">Typ</span><span class="sxs-lookup"><span data-stu-id="cba09-125">Type</span></span>   | <span data-ttu-id="cba09-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cba09-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="cba09-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="cba09-127">Authorization</span></span> | <span data-ttu-id="cba09-128">String</span><span class="sxs-lookup"><span data-stu-id="cba09-128">string</span></span> | <span data-ttu-id="cba09-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cba09-129">Required.</span></span> <span data-ttu-id="cba09-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="cba09-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="cba09-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="cba09-131">Request parameters</span></span>

| <span data-ttu-id="cba09-132">Name</span><span class="sxs-lookup"><span data-stu-id="cba09-132">Name</span></span>        | <span data-ttu-id="cba09-133">Typ</span><span class="sxs-lookup"><span data-stu-id="cba09-133">Type</span></span>   | <span data-ttu-id="cba09-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cba09-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="cba09-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="cba09-135">applicationId</span></span> | <span data-ttu-id="cba09-136">String</span><span class="sxs-lookup"><span data-stu-id="cba09-136">string</span></span> | <span data-ttu-id="cba09-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cba09-137">Required.</span></span> <span data-ttu-id="cba09-138">Die Store-ID der App mit der Flight-Paket-Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="cba09-138">The Store ID of the app that contains the package flight submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="cba09-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="cba09-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="cba09-140">flightId</span><span class="sxs-lookup"><span data-stu-id="cba09-140">flightId</span></span> | <span data-ttu-id="cba09-141">String</span><span class="sxs-lookup"><span data-stu-id="cba09-141">string</span></span> | <span data-ttu-id="cba09-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cba09-142">Required.</span></span> <span data-ttu-id="cba09-143">Die ID des Flight-Pakets mit der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="cba09-143">The ID of the package flight that contains the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="cba09-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen eines Flight-Pakets](create-a-flight.md) und zum [Abrufen von Flight-Paketen für eine App](get-flights-for-an-app.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="cba09-144">This ID is available in the response data for requests to [create a package flight](create-a-flight.md) and [get package flights for an app](get-flights-for-an-app.md).</span></span> <span data-ttu-id="cba09-145">Für einen Flight, der im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Flight-Seite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cba09-145">For a flight that was created in the Dev Center dashboard, this ID is also available in the URL for the flight page in the dashboard.</span></span>  |
| <span data-ttu-id="cba09-146">submissionId</span><span class="sxs-lookup"><span data-stu-id="cba09-146">submissionId</span></span> | <span data-ttu-id="cba09-147">String</span><span class="sxs-lookup"><span data-stu-id="cba09-147">string</span></span> | <span data-ttu-id="cba09-148">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cba09-148">Required.</span></span> <span data-ttu-id="cba09-149">Die ID der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="cba09-149">The ID of the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="cba09-150">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Flight-Paket-Übermittlung](create-a-flight-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cba09-150">This ID is available in the response data for requests to [create a package flight submission](create-a-flight-submission.md).</span></span> <span data-ttu-id="cba09-151">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cba09-151">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |
| <span data-ttu-id="cba09-152">Prozentsatz</span><span class="sxs-lookup"><span data-stu-id="cba09-152">percentage</span></span>  |  <span data-ttu-id="cba09-153">float</span><span class="sxs-lookup"><span data-stu-id="cba09-153">float</span></span>  |  <span data-ttu-id="cba09-154">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cba09-154">Required.</span></span> <span data-ttu-id="cba09-155">Der Prozentsatz der Benutzer, die das Paket für den schrittweisen Rollout erhalten.</span><span class="sxs-lookup"><span data-stu-id="cba09-155">The percentage of users who will receive the gradual rollout package.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="cba09-156">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="cba09-156">Request body</span></span>

<span data-ttu-id="cba09-157">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="cba09-157">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="cba09-158">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="cba09-158">Request example</span></span>

<span data-ttu-id="cba09-159">Im folgenden Beispiel wird das Aktualisieren des Paketrollout-Prozentsatzes einer Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="cba09-159">The following example demonstrates how to update the package rollout percentage for a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/flights/43e448df-97c9-4a43-a0bc-2a445e736bcd/submissions/1152921504621243680/updatepackagerolloutpercentage?percentage=25 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="cba09-160">Antwort</span><span class="sxs-lookup"><span data-stu-id="cba09-160">Response</span></span>

<span data-ttu-id="cba09-161">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="cba09-161">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="cba09-162">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-flight-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="cba09-162">For more details about the values in the response body, see [Package rollout resource](manage-flight-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="cba09-163">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="cba09-163">Error codes</span></span>

<span data-ttu-id="cba09-164">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="cba09-164">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="cba09-165">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="cba09-165">Error code</span></span> |  <span data-ttu-id="cba09-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cba09-166">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="cba09-167">404</span><span class="sxs-lookup"><span data-stu-id="cba09-167">404</span></span>  | <span data-ttu-id="cba09-168">Die angegebene Flight-Paket-Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="cba09-168">The package flight submission could not be found.</span></span> |
| <span data-ttu-id="cba09-169">407</span><span class="sxs-lookup"><span data-stu-id="cba09-169">409</span></span>  | <span data-ttu-id="cba09-170">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="cba09-170">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="cba09-171">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-flight-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="cba09-171">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-flight-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="cba09-172">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="cba09-172">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="cba09-173">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="cba09-173">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="cba09-174">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cba09-174">Related topics</span></span>

* [<span data-ttu-id="cba09-175">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="cba09-175">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="cba09-176">Verwalten von Flight-Paket-Übermittlungen mit der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="cba09-176">Manage package flight submissions using the Microsoft Store submission API</span></span>](manage-flight-submissions.md)
* [<span data-ttu-id="cba09-177">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="cba09-177">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
