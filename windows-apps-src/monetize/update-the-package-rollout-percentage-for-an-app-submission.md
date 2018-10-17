---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um den Paketrollout-Prozentsatz für eine App-Übermittlung zu aktualisieren.
title: Aktualisieren des Prozentsatzes eines Rollouts einer App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paket-Rollout, App-Übermittlung, Aktualisieren, Prozentsatz
ms.assetid: 4c82d837-7a25-4f3a-997e-b7be33b521cc
ms.localizationpriority: medium
ms.openlocfilehash: d39507af310c34621d7a4951e426bc6596284234
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4743899"
---
# <a name="update-the-rollout-percentage-for-an-app-submission"></a><span data-ttu-id="6733d-104">Aktualisieren des Prozentsatzes eines Rollouts einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="6733d-104">Update the rollout percentage for an app submission</span></span>


<span data-ttu-id="6733d-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum [Aktualisieren des Rollout-Prozentsatzes](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="6733d-105">Use this method in the Microsoft Store submission API to [update the rollout percentage](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) for an app submission.</span></span> <span data-ttu-id="6733d-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="6733d-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>


## <a name="prerequisites"></a><span data-ttu-id="6733d-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6733d-107">Prerequisites</span></span>

<span data-ttu-id="6733d-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="6733d-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="6733d-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="6733d-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="6733d-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6733d-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="6733d-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="6733d-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="6733d-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="6733d-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="6733d-113">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="6733d-113">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="6733d-114">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="6733d-114">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="6733d-115">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="6733d-115">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="6733d-116">Sie können dies im [Dev Center-Dashboard](../publish/gradual-package-rollout.md) oder durch [Verwenden der Microsoft Store-Übermittlungs-API](manage-app-submissions.md#manage-gradual-package-rollout) durchführen.</span><span class="sxs-lookup"><span data-stu-id="6733d-116">You can do this in the [Dev Center dashboard](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-app-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="6733d-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="6733d-117">Request</span></span>

<span data-ttu-id="6733d-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="6733d-118">This method has the following syntax.</span></span> <span data-ttu-id="6733d-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="6733d-119">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="6733d-120">Methode</span><span class="sxs-lookup"><span data-stu-id="6733d-120">Method</span></span> | <span data-ttu-id="6733d-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="6733d-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="6733d-122">POST</span><span class="sxs-lookup"><span data-stu-id="6733d-122">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/updatepackagerolloutpercentage``` |


### <a name="request-header"></a><span data-ttu-id="6733d-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="6733d-123">Request header</span></span>

| <span data-ttu-id="6733d-124">Header</span><span class="sxs-lookup"><span data-stu-id="6733d-124">Header</span></span>        | <span data-ttu-id="6733d-125">Typ</span><span class="sxs-lookup"><span data-stu-id="6733d-125">Type</span></span>   | <span data-ttu-id="6733d-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6733d-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="6733d-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="6733d-127">Authorization</span></span> | <span data-ttu-id="6733d-128">String</span><span class="sxs-lookup"><span data-stu-id="6733d-128">string</span></span> | <span data-ttu-id="6733d-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6733d-129">Required.</span></span> <span data-ttu-id="6733d-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="6733d-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="6733d-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="6733d-131">Request parameters</span></span>

| <span data-ttu-id="6733d-132">Name</span><span class="sxs-lookup"><span data-stu-id="6733d-132">Name</span></span>        | <span data-ttu-id="6733d-133">Typ</span><span class="sxs-lookup"><span data-stu-id="6733d-133">Type</span></span>   | <span data-ttu-id="6733d-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6733d-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="6733d-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="6733d-135">applicationId</span></span> | <span data-ttu-id="6733d-136">String</span><span class="sxs-lookup"><span data-stu-id="6733d-136">string</span></span> | <span data-ttu-id="6733d-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6733d-137">Required.</span></span> <span data-ttu-id="6733d-138">Die Store-ID der App mit der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="6733d-138">The Store ID of the app that contains the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="6733d-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="6733d-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="6733d-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="6733d-140">submissionId</span></span> | <span data-ttu-id="6733d-141">String</span><span class="sxs-lookup"><span data-stu-id="6733d-141">string</span></span> | <span data-ttu-id="6733d-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6733d-142">Required.</span></span> <span data-ttu-id="6733d-143">Die ID der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="6733d-143">The ID of the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="6733d-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6733d-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="6733d-145">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6733d-145">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>   |
| <span data-ttu-id="6733d-146">Prozentsatz</span><span class="sxs-lookup"><span data-stu-id="6733d-146">percentage</span></span>  |  <span data-ttu-id="6733d-147">float</span><span class="sxs-lookup"><span data-stu-id="6733d-147">float</span></span>  |  <span data-ttu-id="6733d-148">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6733d-148">Required.</span></span> <span data-ttu-id="6733d-149">Der Prozentsatz der Benutzer, die das Paket für den schrittweisen Rollout erhalten.</span><span class="sxs-lookup"><span data-stu-id="6733d-149">The percentage of users who will receive the gradual rollout package.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="6733d-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="6733d-150">Request body</span></span>

<span data-ttu-id="6733d-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="6733d-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="6733d-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="6733d-152">Request example</span></span>

<span data-ttu-id="6733d-153">Im folgenden Beispiel wird das Aktualisieren des Paketrollout-Prozentsatzes einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="6733d-153">The following example demonstrates how to update the package rollout percentage for an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680/updatepackagerolloutpercentage?percentage=25 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="6733d-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="6733d-154">Response</span></span>

<span data-ttu-id="6733d-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="6733d-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="6733d-156">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-app-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="6733d-156">For more details about the values in the response body, see [Package rollout resource](manage-app-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="6733d-157">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="6733d-157">Error codes</span></span>

<span data-ttu-id="6733d-158">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="6733d-158">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="6733d-159">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="6733d-159">Error code</span></span> |  <span data-ttu-id="6733d-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6733d-160">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="6733d-161">404</span><span class="sxs-lookup"><span data-stu-id="6733d-161">404</span></span>  | <span data-ttu-id="6733d-162">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="6733d-162">The submission could not be found.</span></span> |
| <span data-ttu-id="6733d-163">409</span><span class="sxs-lookup"><span data-stu-id="6733d-163">409</span></span>  | <span data-ttu-id="6733d-164">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="6733d-164">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="6733d-165">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-app-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="6733d-165">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-app-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="6733d-166">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="6733d-166">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="6733d-167">Die App verwendet eine Dev Center-Dashboard-Funktion, die [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="6733d-167">The app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="6733d-168">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6733d-168">Related topics</span></span>

* [<span data-ttu-id="6733d-169">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="6733d-169">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="6733d-170">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="6733d-170">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="6733d-171">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="6733d-171">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
