---
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Paketrollout für eine App-Übermittlung fertigzustellen.
title: Abschließen des Rollouts einer App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, App-Übermittlung, fertigstellen
ms.assetid: c7dd39e6-5162-455a-b03b-1ed76bffcf6e
ms.localizationpriority: medium
ms.openlocfilehash: c8fe211268190ac269018a6bd47acb4b824d2075
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8486819"
---
# <a name="finalize-the-rollout-for-an-app-submission"></a><span data-ttu-id="02108-104">Abschließen des Rollouts einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="02108-104">Finalize the rollout for an app submission</span></span>


<span data-ttu-id="02108-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur [Fertigstellung des Paketrollouts](../publish/gradual-package-rollout.md#completing-the-rollout) für eine App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="02108-105">Use this method in the Microsoft Store submission API to [finalize the package rollout](../publish/gradual-package-rollout.md#completing-the-rollout) for an app submission.</span></span> <span data-ttu-id="02108-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="02108-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02108-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="02108-107">Prerequisites</span></span>

<span data-ttu-id="02108-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="02108-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="02108-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="02108-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="02108-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="02108-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="02108-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="02108-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="02108-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="02108-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="02108-113">Erstellen Sie eine Übermittlung für eine app im Partner Center-Konto an.</span><span class="sxs-lookup"><span data-stu-id="02108-113">Create a submission for an app in your Partner Center account.</span></span> <span data-ttu-id="02108-114">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="02108-114">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="02108-115">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="02108-115">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="02108-116">Sie können diese [im Partner Center](../publish/gradual-package-rollout.md), oder Sie können dies tun, indem Sie [mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md#manage-gradual-package-rollout).</span><span class="sxs-lookup"><span data-stu-id="02108-116">You can do this [in Partner Center](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-app-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="02108-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="02108-117">Request</span></span>

<span data-ttu-id="02108-118">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="02108-118">This method has the following syntax.</span></span> <span data-ttu-id="02108-119">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="02108-119">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="02108-120">Methode</span><span class="sxs-lookup"><span data-stu-id="02108-120">Method</span></span> | <span data-ttu-id="02108-121">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="02108-121">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="02108-122">POST</span><span class="sxs-lookup"><span data-stu-id="02108-122">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/finalizepackagerollout``` |


### <a name="request-header"></a><span data-ttu-id="02108-123">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="02108-123">Request header</span></span>

| <span data-ttu-id="02108-124">Header</span><span class="sxs-lookup"><span data-stu-id="02108-124">Header</span></span>        | <span data-ttu-id="02108-125">Typ</span><span class="sxs-lookup"><span data-stu-id="02108-125">Type</span></span>   | <span data-ttu-id="02108-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02108-126">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="02108-127">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="02108-127">Authorization</span></span> | <span data-ttu-id="02108-128">String</span><span class="sxs-lookup"><span data-stu-id="02108-128">string</span></span> | <span data-ttu-id="02108-129">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="02108-129">Required.</span></span> <span data-ttu-id="02108-130">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="02108-130">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="02108-131">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="02108-131">Request parameters</span></span>

| <span data-ttu-id="02108-132">Name</span><span class="sxs-lookup"><span data-stu-id="02108-132">Name</span></span>        | <span data-ttu-id="02108-133">Typ</span><span class="sxs-lookup"><span data-stu-id="02108-133">Type</span></span>   | <span data-ttu-id="02108-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02108-134">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="02108-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="02108-135">applicationId</span></span> | <span data-ttu-id="02108-136">String</span><span class="sxs-lookup"><span data-stu-id="02108-136">string</span></span> | <span data-ttu-id="02108-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="02108-137">Required.</span></span> <span data-ttu-id="02108-138">Die Store-ID der App mit der Übermittlung, deren Paketrollout fertig gestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="02108-138">The Store ID of the app that contains the submission with the package rollout you want to finalize.</span></span> <span data-ttu-id="02108-139">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="02108-139">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="02108-140">submissionId</span><span class="sxs-lookup"><span data-stu-id="02108-140">submissionId</span></span> | <span data-ttu-id="02108-141">String</span><span class="sxs-lookup"><span data-stu-id="02108-141">string</span></span> | <span data-ttu-id="02108-142">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="02108-142">Required.</span></span> <span data-ttu-id="02108-143">Die ID der Übermittlung mit dem Paketrollout, der fertig gestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="02108-143">The ID of the submission with the package rollout you want to finalize.</span></span> <span data-ttu-id="02108-144">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="02108-144">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="02108-145">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="02108-145">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="02108-146">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="02108-146">Request body</span></span>

<span data-ttu-id="02108-147">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="02108-147">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="02108-148">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="02108-148">Request example</span></span>

<span data-ttu-id="02108-149">Im folgenden Beispiel wird die Fertigstellung des Paketrollouts für eine Flight-Paket-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="02108-149">The following example demonstrates how to finalize the package rollout for a package flight submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680/finalizepackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="02108-150">Antwort</span><span class="sxs-lookup"><span data-stu-id="02108-150">Response</span></span>

<span data-ttu-id="02108-151">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="02108-151">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="02108-152">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-app-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="02108-152">For more details about the values in the response body, see [Package rollout resource](manage-app-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 100.0,
    "packageRolloutStatus": "PackageRolloutComplete",
    "fallbackSubmissionId": "1212922684621243058"
}
```


## <a name="error-codes"></a><span data-ttu-id="02108-153">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="02108-153">Error codes</span></span>

<span data-ttu-id="02108-154">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="02108-154">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="02108-155">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="02108-155">Error code</span></span> |  <span data-ttu-id="02108-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02108-156">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="02108-157">404</span><span class="sxs-lookup"><span data-stu-id="02108-157">404</span></span>  | <span data-ttu-id="02108-158">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="02108-158">The submission could not be found.</span></span> |
| <span data-ttu-id="02108-159">409</span><span class="sxs-lookup"><span data-stu-id="02108-159">409</span></span>  | <span data-ttu-id="02108-160">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="02108-160">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="02108-161">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-app-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="02108-161">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-app-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="02108-162">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="02108-162">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="02108-163">Die app verwendet ein DevPartner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="02108-163">The app uses a DevPartner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="02108-164">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="02108-164">Related topics</span></span>

* [<span data-ttu-id="02108-165">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="02108-165">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="02108-166">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="02108-166">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="02108-167">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="02108-167">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
