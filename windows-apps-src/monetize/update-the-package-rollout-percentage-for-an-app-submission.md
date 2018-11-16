---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API, um den Paketrollout-Prozentsatz für eine App-Übermittlung zu aktualisieren.
title: Aktualisieren des Prozentsatzes eines Rollouts einer App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paket-Rollout, App-Übermittlung, Aktualisieren, Prozentsatz
ms.assetid: 4c82d837-7a25-4f3a-997e-b7be33b521cc
ms.localizationpriority: medium
ms.openlocfilehash: ee7657a1ebd08e70e6b5dac8a9a723637539066e
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6968939"
---
# <a name="update-the-rollout-percentage-for-an-app-submission"></a><span data-ttu-id="c94bc-104">Aktualisieren des Prozentsatzes eines Rollouts einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c94bc-104">Update the rollout percentage for an app submission</span></span>


<span data-ttu-id="c94bc-105">Verwenden Sie diese Methode in der Microsoft Store-Übermittlungs-API zum [Aktualisieren des Rollout-Prozentsatzes](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="c94bc-105">Use this method in the Microsoft Store submission API to [update the rollout percentage](../publish/gradual-package-rollout.md#setting-the-rollout-percentage) for an app submission.</span></span> <span data-ttu-id="c94bc-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="c94bc-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>


## <a name="prerequisites"></a><span data-ttu-id="c94bc-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c94bc-107">Prerequisites</span></span>

<span data-ttu-id="c94bc-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="c94bc-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="c94bc-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="c94bc-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="c94bc-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c94bc-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="c94bc-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="c94bc-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="c94bc-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="c94bc-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="c94bc-113">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="c94bc-113">Create a submission for one of your apps.</span></span> <span data-ttu-id="c94bc-114">Sie können dies im Partner Center oder können Sie dies tun, indem Sie mithilfe der Methode zum [Erstellen einer app-Übermittlung](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="c94bc-114">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="c94bc-115">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="c94bc-115">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="c94bc-116">Sie hierzu [im Partner Center](../publish/gradual-package-rollout.md), oder Sie können dies tun, indem Sie [mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md#manage-gradual-package-rollout).</span><span class="sxs-lookup"><span data-stu-id="c94bc-116">You can do this in [in Partner Center](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-app-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="c94bc-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="c94bc-117">Request</span></span>

<span data-ttu-id="c94bc-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="c94bc-118">This method has the following syntax.</span></span> <span data-ttu-id="c94bc-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="c94bc-119">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="c94bc-120">Methode</span><span class="sxs-lookup"><span data-stu-id="c94bc-120">Method</span></span> | <span data-ttu-id="c94bc-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="c94bc-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="c94bc-122">POST</span><span class="sxs-lookup"><span data-stu-id="c94bc-122">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/updatepackagerolloutpercentage``` |


### <a name="request-header"></a><span data-ttu-id="c94bc-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c94bc-123">Request header</span></span>

| <span data-ttu-id="c94bc-124">Header</span><span class="sxs-lookup"><span data-stu-id="c94bc-124">Header</span></span>        | <span data-ttu-id="c94bc-125">Typ</span><span class="sxs-lookup"><span data-stu-id="c94bc-125">Type</span></span>   | <span data-ttu-id="c94bc-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c94bc-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c94bc-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="c94bc-127">Authorization</span></span> | <span data-ttu-id="c94bc-128">String</span><span class="sxs-lookup"><span data-stu-id="c94bc-128">string</span></span> | <span data-ttu-id="c94bc-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c94bc-129">Required.</span></span> <span data-ttu-id="c94bc-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="c94bc-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="c94bc-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="c94bc-131">Request parameters</span></span>

| <span data-ttu-id="c94bc-132">Name</span><span class="sxs-lookup"><span data-stu-id="c94bc-132">Name</span></span>        | <span data-ttu-id="c94bc-133">Typ</span><span class="sxs-lookup"><span data-stu-id="c94bc-133">Type</span></span>   | <span data-ttu-id="c94bc-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c94bc-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="c94bc-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="c94bc-135">applicationId</span></span> | <span data-ttu-id="c94bc-136">String</span><span class="sxs-lookup"><span data-stu-id="c94bc-136">string</span></span> | <span data-ttu-id="c94bc-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c94bc-137">Required.</span></span> <span data-ttu-id="c94bc-138">Die Store-ID der App mit der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c94bc-138">The Store ID of the app that contains the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="c94bc-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="c94bc-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="c94bc-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="c94bc-140">submissionId</span></span> | <span data-ttu-id="c94bc-141">String</span><span class="sxs-lookup"><span data-stu-id="c94bc-141">string</span></span> | <span data-ttu-id="c94bc-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c94bc-142">Required.</span></span> <span data-ttu-id="c94bc-143">Die ID der Übermittlung, deren Paketrollout-Prozentsatz aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c94bc-143">The ID of the submission with the package rollout percentage you want to update.</span></span> <span data-ttu-id="c94bc-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c94bc-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="c94bc-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c94bc-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>   |
| <span data-ttu-id="c94bc-146">Prozentsatz</span><span class="sxs-lookup"><span data-stu-id="c94bc-146">percentage</span></span>  |  <span data-ttu-id="c94bc-147">float</span><span class="sxs-lookup"><span data-stu-id="c94bc-147">float</span></span>  |  <span data-ttu-id="c94bc-148">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c94bc-148">Required.</span></span> <span data-ttu-id="c94bc-149">Der Prozentsatz der Benutzer, die das Paket für den schrittweisen Rollout erhalten.</span><span class="sxs-lookup"><span data-stu-id="c94bc-149">The percentage of users who will receive the gradual rollout package.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="c94bc-150">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="c94bc-150">Request body</span></span>

<span data-ttu-id="c94bc-151">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="c94bc-151">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="c94bc-152">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="c94bc-152">Request example</span></span>

<span data-ttu-id="c94bc-153">Im folgenden Beispiel wird das Aktualisieren des Paketrollout-Prozentsatzes einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="c94bc-153">The following example demonstrates how to update the package rollout percentage for an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680/updatepackagerolloutpercentage?percentage=25 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="c94bc-154">Antwort</span><span class="sxs-lookup"><span data-stu-id="c94bc-154">Response</span></span>

<span data-ttu-id="c94bc-155">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="c94bc-155">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="c94bc-156">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-app-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="c94bc-156">For more details about the values in the response body, see [Package rollout resource](manage-app-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="c94bc-157">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="c94bc-157">Error codes</span></span>

<span data-ttu-id="c94bc-158">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="c94bc-158">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="c94bc-159">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="c94bc-159">Error code</span></span> |  <span data-ttu-id="c94bc-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c94bc-160">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="c94bc-161">404</span><span class="sxs-lookup"><span data-stu-id="c94bc-161">404</span></span>  | <span data-ttu-id="c94bc-162">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="c94bc-162">The submission could not be found.</span></span> |
| <span data-ttu-id="c94bc-163">409</span><span class="sxs-lookup"><span data-stu-id="c94bc-163">409</span></span>  | <span data-ttu-id="c94bc-164">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="c94bc-164">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="c94bc-165">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-app-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="c94bc-165">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-app-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="c94bc-166">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="c94bc-166">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="c94bc-167">Die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="c94bc-167">The app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="c94bc-168">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c94bc-168">Related topics</span></span>

* [<span data-ttu-id="c94bc-169">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="c94bc-169">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="c94bc-170">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="c94bc-170">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="c94bc-171">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="c94bc-171">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
