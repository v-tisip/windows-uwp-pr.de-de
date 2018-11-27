---
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Paketrollout-Informationen für eine App-Übermittlung abzurufen.
title: Abrufen von Informationen zum Rollout für eine App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, App-Übermittlung
ms.assetid: 9ada5ac3-a86e-4bb6-8ebc-915ba9649e3c
ms.localizationpriority: medium
ms.openlocfilehash: 301973fd231570f0fe63b8838971906c25e2d55c
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7827079"
---
# <a name="get-rollout-info-for-an-app-submission"></a><span data-ttu-id="2c09a-104">Abrufen von Informationen zum Rollout für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2c09a-104">Get rollout info for an app submission</span></span>


<span data-ttu-id="2c09a-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um [Paketrollout](../publish/gradual-package-rollout.md)-Informationen für eine Flight-Paket-Übermittlung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="2c09a-105">Use this method in the Microsoft Store submission API to get [package rollout](../publish/gradual-package-rollout.md) info for a package flight submission.</span></span> <span data-ttu-id="2c09a-106">Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="2c09a-106">For more information about the process of process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c09a-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2c09a-107">Prerequisites</span></span>

<span data-ttu-id="2c09a-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="2c09a-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="2c09a-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="2c09a-109">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="2c09a-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2c09a-110">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="2c09a-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="2c09a-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="2c09a-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="2c09a-112">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="2c09a-113">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="2c09a-113">Create a submission for one of your apps.</span></span> <span data-ttu-id="2c09a-114">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="2c09a-114">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="2c09a-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2c09a-115">Request</span></span>

<span data-ttu-id="2c09a-116">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="2c09a-116">This method has the following syntax.</span></span> <span data-ttu-id="2c09a-117">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="2c09a-117">See the following sections for usage examples and descriptions of the header and request parameters.</span></span>

| <span data-ttu-id="2c09a-118">Methode</span><span class="sxs-lookup"><span data-stu-id="2c09a-118">Method</span></span> | <span data-ttu-id="2c09a-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2c09a-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="2c09a-120">GET</span><span class="sxs-lookup"><span data-stu-id="2c09a-120">GET</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/packagerollout   ``` |


### <a name="request-header"></a><span data-ttu-id="2c09a-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2c09a-121">Request header</span></span>

| <span data-ttu-id="2c09a-122">Header</span><span class="sxs-lookup"><span data-stu-id="2c09a-122">Header</span></span>        | <span data-ttu-id="2c09a-123">Typ</span><span class="sxs-lookup"><span data-stu-id="2c09a-123">Type</span></span>   | <span data-ttu-id="2c09a-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2c09a-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2c09a-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="2c09a-125">Authorization</span></span> | <span data-ttu-id="2c09a-126">String</span><span class="sxs-lookup"><span data-stu-id="2c09a-126">string</span></span> | <span data-ttu-id="2c09a-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2c09a-127">Required.</span></span> <span data-ttu-id="2c09a-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="2c09a-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="2c09a-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="2c09a-129">Request parameters</span></span>

| <span data-ttu-id="2c09a-130">Name</span><span class="sxs-lookup"><span data-stu-id="2c09a-130">Name</span></span>        | <span data-ttu-id="2c09a-131">Typ</span><span class="sxs-lookup"><span data-stu-id="2c09a-131">Type</span></span>   | <span data-ttu-id="2c09a-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2c09a-132">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2c09a-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="2c09a-133">applicationId</span></span> | <span data-ttu-id="2c09a-134">String</span><span class="sxs-lookup"><span data-stu-id="2c09a-134">string</span></span> | <span data-ttu-id="2c09a-135">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2c09a-135">Required.</span></span> <span data-ttu-id="2c09a-136">Die Store-ID der App mit der Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2c09a-136">The Store ID of the app that contains the submission with the package rollout info you want to get.</span></span> <span data-ttu-id="2c09a-137">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="2c09a-137">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="2c09a-138">submissionId</span><span class="sxs-lookup"><span data-stu-id="2c09a-138">submissionId</span></span> | <span data-ttu-id="2c09a-139">String</span><span class="sxs-lookup"><span data-stu-id="2c09a-139">string</span></span> | <span data-ttu-id="2c09a-140">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2c09a-140">Required.</span></span> <span data-ttu-id="2c09a-141">Die ID der Übermittlung mit den Paketrollout-Informationen, die Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="2c09a-141">The ID of the submission with the package rollout info you want to get.</span></span> <span data-ttu-id="2c09a-142">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2c09a-142">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="2c09a-143">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2c09a-143">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="2c09a-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="2c09a-144">Request body</span></span>

<span data-ttu-id="2c09a-145">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="2c09a-145">Do not provide a request body for this method.</span></span>

### <a name="request-example"></a><span data-ttu-id="2c09a-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="2c09a-146">Request example</span></span>

<span data-ttu-id="2c09a-147">Im folgenden Beispiel wird das Abrufen der Paketrollout-Informationen einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="2c09a-147">The following example demonstrates how to get the package rollout info for an app submission.</span></span>

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243649/packagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="2c09a-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="2c09a-148">Response</span></span>

<span data-ttu-id="2c09a-149">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode für eine App-Übermittlung mit aktiviertem schrittweisem Paketrollout.</span><span class="sxs-lookup"><span data-stu-id="2c09a-149">The following example demonstrates the JSON response body for a successful call to this method for an app submission with gradual package rollout enabled.</span></span> <span data-ttu-id="2c09a-150">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Paketrollout-Ressource](manage-app-submissions.md#package-rollout-object).</span><span class="sxs-lookup"><span data-stu-id="2c09a-150">For more details about the values in the response body, see [Package rollout resource](manage-app-submissions.md#package-rollout-object).</span></span>

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

<span data-ttu-id="2c09a-151">Ist für die App-Übermittlung schrittweises Paketrollout nicht aktiviert, wird folgender Antworttext zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2c09a-151">If the app submission does not have gradual package rollout enabled, the following response body will be returned.</span></span>

```json
{
    "isPackageRollout": false,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutNotStarted",
    "fallbackSubmissionId": "0"
}
```

## <a name="error-codes"></a><span data-ttu-id="2c09a-152">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2c09a-152">Error codes</span></span>

<span data-ttu-id="2c09a-153">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="2c09a-153">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="2c09a-154">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="2c09a-154">Error code</span></span> |  <span data-ttu-id="2c09a-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2c09a-155">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="2c09a-156">404</span><span class="sxs-lookup"><span data-stu-id="2c09a-156">404</span></span>  | <span data-ttu-id="2c09a-157">Die Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="2c09a-157">The submission could not be found.</span></span> |
| <span data-ttu-id="2c09a-158">409</span><span class="sxs-lookup"><span data-stu-id="2c09a-158">409</span></span>  | <span data-ttu-id="2c09a-159">Die Übermittlung gehört nicht zur angegebenen app, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="2c09a-159">The submission does not belong to the specified app, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="2c09a-160">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2c09a-160">Related topics</span></span>

* [<span data-ttu-id="2c09a-161">Schrittweiser Paketrollout</span><span class="sxs-lookup"><span data-stu-id="2c09a-161">Gradual package rollout</span></span>](../publish/gradual-package-rollout.md)
* [<span data-ttu-id="2c09a-162">Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API</span><span class="sxs-lookup"><span data-stu-id="2c09a-162">Manage app submissions using the Microsoft Store submission API</span></span>](manage-app-submissions.md)
* [<span data-ttu-id="2c09a-163">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="2c09a-163">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
