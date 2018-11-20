---
author: Xansky
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um das Paketrollout für eine App-Übermittlung anzuhalten.
title: Anhalten des Rollouts einer App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, App-Übermittlung, anhalten
ms.assetid: 4ce79fe3-deda-4d31-b938-d672c3869051
ms.localizationpriority: medium
ms.openlocfilehash: df6db5ee434aabaaa56b309e02aa9197d72f4469
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7288000"
---
# <a name="halt-the-rollout-for-an-app-submission"></a><span data-ttu-id="de45c-104">Anhalten des Rollouts einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="de45c-104">Halt the rollout for an app submission</span></span>


<span data-ttu-id="de45c-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um [das Paketrollout](../publish/gradual-package-rollout.md#completing-the-rollout) für eine App-Übermittlung anzuhalten.</span><span class="sxs-lookup"><span data-stu-id="de45c-105">Use this method in the Microsoft Store submission API to [halt the package rollout](../publish/gradual-package-rollout.md#completing-the-rollout) for an app submission.</span></span> <span data-ttu-id="de45c-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="de45c-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="de45c-107">Wenn Sie das Rollout für eine App-Übermittlung anhalten und dann [eine neue App-Übermittlung erstellen](create-an-app-submission.md), ist die neue Übermittlung ein Klon der angehaltenen Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="de45c-107">If you halt the rollout for an app submission and then [create a new app submission](create-an-app-submission.md), the new submission is a clone of the halted submission.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="de45c-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="de45c-108">Prerequisites</span></span>

<span data-ttu-id="de45c-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="de45c-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="de45c-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="de45c-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="de45c-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="de45c-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="de45c-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="de45c-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="de45c-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="de45c-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="de45c-114">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="de45c-114">Create a submission for one of your apps.</span></span> <span data-ttu-id="de45c-115">Sie können dies im Partner Center oder können Sie dies tun, indem Sie mithilfe der Methode zum [Erstellen einer app-Übermittlung](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="de45c-115">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>
* <span data-ttu-id="de45c-116">Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="de45c-116">Enable a gradual package rollout for the submission.</span></span> <span data-ttu-id="de45c-117">Sie können diese [im Partner Center](../publish/gradual-package-rollout.md), oder Sie können dies tun, indem Sie [mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md#manage-gradual-package-rollout).</span><span class="sxs-lookup"><span data-stu-id="de45c-117">You can do this [in Partner Center](../publish/gradual-package-rollout.md), or you can do this by [using the Microsoft Store submission API](manage-app-submissions.md#manage-gradual-package-rollout).</span></span>

## <a name="request"></a><span data-ttu-id="de45c-118">Anforderung</span><span class="sxs-lookup"><span data-stu-id="de45c-118">Request</span></span>

<span data-ttu-id="de45c-119">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="de45c-119">This method has the following syntax.</span></span> <span data-ttu-id="de45c-120">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="de45c-120">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="de45c-121">Methode</span><span class="sxs-lookup"><span data-stu-id="de45c-121">Method</span></span> | <span data-ttu-id="de45c-122">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="de45c-122">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="de45c-123">POST</span><span class="sxs-lookup"><span data-stu-id="de45c-123">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/haltpackagerollout``` |


### <a name="request-header"></a><span data-ttu-id="de45c-124">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="de45c-124">Request header</span></span>

| <span data-ttu-id="de45c-125">Header</span><span class="sxs-lookup"><span data-stu-id="de45c-125">Header</span></span>        | <span data-ttu-id="de45c-126">Typ</span><span class="sxs-lookup"><span data-stu-id="de45c-126">Type</span></span>   | <span data-ttu-id="de45c-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de45c-127">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="de45c-128">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="de45c-128">Authorization</span></span> | <span data-ttu-id="de45c-129">String</span><span class="sxs-lookup"><span data-stu-id="de45c-129">string</span></span> | <span data-ttu-id="de45c-130">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de45c-130">Required.</span></span> <span data-ttu-id="de45c-131">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="de45c-131">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="de45c-132">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="de45c-132">Request parameters</span></span>

| <span data-ttu-id="de45c-133">Name</span><span class="sxs-lookup"><span data-stu-id="de45c-133">Name</span></span>        | <span data-ttu-id="de45c-134">Typ</span><span class="sxs-lookup"><span data-stu-id="de45c-134">Type</span></span>   | <span data-ttu-id="de45c-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de45c-135">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="de45c-136">applicationId</span><span class="sxs-lookup"><span data-stu-id="de45c-136">applicationId</span></span> | <span data-ttu-id="de45c-137">String</span><span class="sxs-lookup"><span data-stu-id="de45c-137">string</span></span> | <span data-ttu-id="de45c-138">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de45c-138">Required.</span></span> <span data-ttu-id="de45c-139">Die Store-ID der App mit der Übermittlung, deren Paketrollout angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="de45c-139">The Store ID of the app that contains the submission with the package rollout you want to halt.</span></span> <span data-ttu-id="de45c-140">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="de45c-140">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="de45c-141">submissionId</span><span class="sxs-lookup"><span data-stu-id="de45c-141">submissionId</span></span> | <span data-ttu-id="de45c-142">String</span><span class="sxs-lookup"><span data-stu-id="de45c-142">string</span></span> | <span data-ttu-id="de45c-143">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de45c-143">Required.</span></span> <span data-ttu-id="de45c-144">Die ID der Übermittlung mit dem Paketrollout, das angehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="de45c-144">The ID of the submission with the package rollout you want to halt.</span></span> <span data-ttu-id="de45c-145">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="de45c-145">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="de45c-146">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="de45c-146">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="de45c-147">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="de45c-147">Request body</span></span>

<span data-ttu-id="de45c-148">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="de45c-148">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="de45c-149">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="de45c-149">Request example</span></span>

<span data-ttu-id="de45c-150">Im folgenden Beispiel wird das Anhalten des Paketrollouts einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="de45c-150">The following example demonstrates how to halt the package rollout for an app submission.</span></span>

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680/haltpackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="de45c-151">Antwort</span><span class="sxs-lookup"><span data-stu-id="de45c-151">Response</span></span>

<span data-ttu-id="de45c-152">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="de45c-152">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="de45c-153">Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-app-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="de45c-153">For more details about the values in the response body, see [Package rollout resource](manage-app-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutStopped",
    "fallbackSubmissionId": "1212922684621243058"
}
```

## <a name="error-codes"></a><span data-ttu-id="de45c-154">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="de45c-154">Error codes</span></span>

<span data-ttu-id="de45c-155">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="de45c-155">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="de45c-156">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="de45c-156">Error code</span></span> |  <span data-ttu-id="de45c-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de45c-157">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="de45c-158">404</span><span class="sxs-lookup"><span data-stu-id="de45c-158">404</span></span>  | <span data-ttu-id="de45c-159">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="de45c-159">The submission could not be found.</span></span> |
| <span data-ttu-id="de45c-160">409</span><span class="sxs-lookup"><span data-stu-id="de45c-160">409</span></span>  | <span data-ttu-id="de45c-161">Dieser Code weist auf einen der folgenden Fehler hin:</span><span class="sxs-lookup"><span data-stu-id="de45c-161">This code indicates one of the following errors:</span></span><br/><br/><ul><li><span data-ttu-id="de45c-162">Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-app-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="de45c-162">The submission is not in a valid state for the gradual rollout operation (before calling this method, the submission must be published and the [packageRolloutStatus](manage-app-submissions.md#package-rollout-object) value must be set to **PackageRolloutInProgress**).</span></span></li><li><span data-ttu-id="de45c-163">Die Übermittlung gehört nicht zur angegebenen App.</span><span class="sxs-lookup"><span data-stu-id="de45c-163">The submission does not belong to the specified app.</span></span></li><li><span data-ttu-id="de45c-164">Die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="de45c-164">The app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span></li></ul> |   


## <a name="related-topics"></a><span data-ttu-id="de45c-165">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="de45c-165">Related topics</span></span>

* [<span data-ttu-id="de45c-166">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="de45c-166">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="de45c-167">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="de45c-167">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="de45c-168">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="de45c-168">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
