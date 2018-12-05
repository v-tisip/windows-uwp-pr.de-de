---
ms.assetid: D677E126-C3D6-46B6-87A5-6237EBEDF1A9
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Add-On-Übermittlung.
title: Löschen einer Add-On-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, löschen, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: cdcd74b86ce846f19f8a4eb912781762adb66a2d
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8706176"
---
# <a name="delete-an-add-on-submission"></a><span data-ttu-id="f5850-104">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-104">Delete an add-on submission</span></span>

<span data-ttu-id="f5850-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen Add-On-Übermittlung (Add-Ons werden auch als In-App-Produkt bzw. IAP bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="f5850-105">Use this method in the Microsoft Store submission API to delete an existing add-on (also known as in-app product or IAP) submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f5850-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f5850-106">Prerequisites</span></span>

<span data-ttu-id="f5850-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="f5850-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="f5850-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="f5850-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="f5850-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f5850-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="f5850-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="f5850-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="f5850-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="f5850-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="f5850-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="f5850-112">Request</span></span>

<span data-ttu-id="f5850-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="f5850-113">This method has the following syntax.</span></span> <span data-ttu-id="f5850-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="f5850-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="f5850-115">Methode</span><span class="sxs-lookup"><span data-stu-id="f5850-115">Method</span></span> | <span data-ttu-id="f5850-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="f5850-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="f5850-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="f5850-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="f5850-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="f5850-118">Request header</span></span>

| <span data-ttu-id="f5850-119">Header</span><span class="sxs-lookup"><span data-stu-id="f5850-119">Header</span></span>        | <span data-ttu-id="f5850-120">Typ</span><span class="sxs-lookup"><span data-stu-id="f5850-120">Type</span></span>   | <span data-ttu-id="f5850-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f5850-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f5850-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="f5850-122">Authorization</span></span> | <span data-ttu-id="f5850-123">String</span><span class="sxs-lookup"><span data-stu-id="f5850-123">string</span></span> | <span data-ttu-id="f5850-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f5850-124">Required.</span></span> <span data-ttu-id="f5850-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="f5850-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="f5850-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="f5850-126">Request parameters</span></span>

| <span data-ttu-id="f5850-127">Name</span><span class="sxs-lookup"><span data-stu-id="f5850-127">Name</span></span>        | <span data-ttu-id="f5850-128">Typ</span><span class="sxs-lookup"><span data-stu-id="f5850-128">Type</span></span>   | <span data-ttu-id="f5850-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f5850-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f5850-130">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="f5850-130">inAppProductId</span></span> | <span data-ttu-id="f5850-131">String</span><span class="sxs-lookup"><span data-stu-id="f5850-131">string</span></span> | <span data-ttu-id="f5850-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f5850-132">Required.</span></span> <span data-ttu-id="f5850-133">Die Store-ID des Add-Ons, das die zu löschende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="f5850-133">The Store ID of the add-on that contains the submission to delete.</span></span> <span data-ttu-id="f5850-134">Die Store-ID ist im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f5850-134">The Store ID is available in Partner Center.</span></span>  |
| <span data-ttu-id="f5850-135">submissionId</span><span class="sxs-lookup"><span data-stu-id="f5850-135">submissionId</span></span> | <span data-ttu-id="f5850-136">String</span><span class="sxs-lookup"><span data-stu-id="f5850-136">string</span></span> | <span data-ttu-id="f5850-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f5850-137">Required.</span></span> <span data-ttu-id="f5850-138">Die ID der zu löschenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="f5850-138">The ID of the submission to delete.</span></span> <span data-ttu-id="f5850-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f5850-139">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="f5850-140">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f5850-140">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="f5850-141">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="f5850-141">Request body</span></span>

<span data-ttu-id="f5850-142">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="f5850-142">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="f5850-143">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="f5850-143">Request example</span></span>

<span data-ttu-id="f5850-144">Im folgenden Beispiel wird das Löschen einer Add-On-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f5850-144">The following example demonstrates how to delete an add-on submission.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="f5850-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="f5850-145">Response</span></span>

<span data-ttu-id="f5850-146">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="f5850-146">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="f5850-147">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="f5850-147">Error codes</span></span>

<span data-ttu-id="f5850-148">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="f5850-148">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="f5850-149">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="f5850-149">Error code</span></span> |  <span data-ttu-id="f5850-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f5850-150">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="f5850-151">400</span><span class="sxs-lookup"><span data-stu-id="f5850-151">400</span></span>  | <span data-ttu-id="f5850-152">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="f5850-152">The request parameters are invalid.</span></span> |
| <span data-ttu-id="f5850-153">404</span><span class="sxs-lookup"><span data-stu-id="f5850-153">404</span></span>  | <span data-ttu-id="f5850-154">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="f5850-154">The specified submission could not be found.</span></span> |
| <span data-ttu-id="f5850-155">409</span><span class="sxs-lookup"><span data-stu-id="f5850-155">409</span></span>  | <span data-ttu-id="f5850-156">Die angegebene Übermittlung wurde gefunden, aber es konnte nicht in ihrem aktuellen Zustand gelöscht werden, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="f5850-156">The specified submission was found but it could not be deleted in its current state, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="f5850-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f5850-157">Related topics</span></span>

* [<span data-ttu-id="f5850-158">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="f5850-158">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="f5850-159">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-159">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="f5850-160">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-160">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="f5850-161">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-161">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="f5850-162">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-162">Update an add-on submission</span></span>](update-an-add-on-submission.md)
* [<span data-ttu-id="f5850-163">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="f5850-163">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
