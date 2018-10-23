---
author: Xansky
ms.assetid: 96C090C1-88F8-42E7-AED1-AFA9031E952B
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen App-Übermittlung.
title: Löschen einer App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Microsoft Store-Übermittlungs-API, App-Übermittlung, löschen
ms.localizationpriority: medium
ms.openlocfilehash: c10a8df52c9de2b5a6b2eaf3533dbc3825bf4d8e
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5409832"
---
# <a name="delete-an-app-submission"></a><span data-ttu-id="59ee4-104">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-104">Delete an app submission</span></span>

<span data-ttu-id="59ee4-105">Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zum Löschen einer vorhandenen App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="59ee4-105">Use this method in the Microsoft Store submission API to delete an existing app submission.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59ee4-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="59ee4-106">Prerequisites</span></span>

<span data-ttu-id="59ee4-107">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="59ee4-107">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="59ee4-108">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="59ee4-108">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="59ee4-109">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="59ee4-109">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="59ee4-110">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="59ee4-110">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="59ee4-111">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="59ee4-111">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="59ee4-112">Anforderung</span><span class="sxs-lookup"><span data-stu-id="59ee4-112">Request</span></span>

<span data-ttu-id="59ee4-113">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="59ee4-113">This method has the following syntax.</span></span> <span data-ttu-id="59ee4-114">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="59ee4-114">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="59ee4-115">Methode</span><span class="sxs-lookup"><span data-stu-id="59ee4-115">Method</span></span> | <span data-ttu-id="59ee4-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="59ee4-116">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="59ee4-117">DELETE</span><span class="sxs-lookup"><span data-stu-id="59ee4-117">DELETE</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}``` |


### <a name="request-header"></a><span data-ttu-id="59ee4-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="59ee4-118">Request header</span></span>

| <span data-ttu-id="59ee4-119">Header</span><span class="sxs-lookup"><span data-stu-id="59ee4-119">Header</span></span>        | <span data-ttu-id="59ee4-120">Typ</span><span class="sxs-lookup"><span data-stu-id="59ee4-120">Type</span></span>   | <span data-ttu-id="59ee4-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="59ee4-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="59ee4-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="59ee4-122">Authorization</span></span> | <span data-ttu-id="59ee4-123">String</span><span class="sxs-lookup"><span data-stu-id="59ee4-123">string</span></span> | <span data-ttu-id="59ee4-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="59ee4-124">Required.</span></span> <span data-ttu-id="59ee4-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="59ee4-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="59ee4-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="59ee4-126">Request parameters</span></span>

| <span data-ttu-id="59ee4-127">Name</span><span class="sxs-lookup"><span data-stu-id="59ee4-127">Name</span></span>        | <span data-ttu-id="59ee4-128">Typ</span><span class="sxs-lookup"><span data-stu-id="59ee4-128">Type</span></span>   | <span data-ttu-id="59ee4-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="59ee4-129">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="59ee4-130">applicationId</span><span class="sxs-lookup"><span data-stu-id="59ee4-130">applicationId</span></span> | <span data-ttu-id="59ee4-131">String</span><span class="sxs-lookup"><span data-stu-id="59ee4-131">string</span></span> | <span data-ttu-id="59ee4-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="59ee4-132">Required.</span></span> <span data-ttu-id="59ee4-133">Die Store-ID der App, die die zu löschende Übermittlung enthält.</span><span class="sxs-lookup"><span data-stu-id="59ee4-133">The Store ID of the app that contains the submission to delete.</span></span> <span data-ttu-id="59ee4-134">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="59ee4-134">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="59ee4-135">submissionId</span><span class="sxs-lookup"><span data-stu-id="59ee4-135">submissionId</span></span> | <span data-ttu-id="59ee4-136">String</span><span class="sxs-lookup"><span data-stu-id="59ee4-136">string</span></span> | <span data-ttu-id="59ee4-137">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="59ee4-137">Required.</span></span> <span data-ttu-id="59ee4-138">Die ID der zu löschenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="59ee4-138">The ID of the submission to delete.</span></span> <span data-ttu-id="59ee4-139">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="59ee4-139">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="59ee4-140">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="59ee4-140">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="59ee4-141">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="59ee4-141">Request body</span></span>

<span data-ttu-id="59ee4-142">Stellen Sie keinen Anforderungstext für diese Methode bereit.</span><span class="sxs-lookup"><span data-stu-id="59ee4-142">Do not provide a request body for this method.</span></span>


### <a name="request-example"></a><span data-ttu-id="59ee4-143">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="59ee4-143">Request example</span></span>

<span data-ttu-id="59ee4-144">Im folgenden Beispiel wird das Löschen einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="59ee4-144">The following example demonstrates how to delete an app submission.</span></span>

```
DELETE https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243610 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="59ee4-145">Antwort</span><span class="sxs-lookup"><span data-stu-id="59ee4-145">Response</span></span>

<span data-ttu-id="59ee4-146">Wenn dies erfolgreich war, gibt die Methode einen leeren Antworttext zurück.</span><span class="sxs-lookup"><span data-stu-id="59ee4-146">If successful, this method returns an empty response body.</span></span>

## <a name="error-codes"></a><span data-ttu-id="59ee4-147">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="59ee4-147">Error codes</span></span>

<span data-ttu-id="59ee4-148">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="59ee4-148">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="59ee4-149">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="59ee4-149">Error code</span></span> |  <span data-ttu-id="59ee4-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="59ee4-150">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="59ee4-151">400</span><span class="sxs-lookup"><span data-stu-id="59ee4-151">400</span></span>  | <span data-ttu-id="59ee4-152">Die Anforderungsparameter sind ungültig.</span><span class="sxs-lookup"><span data-stu-id="59ee4-152">The request parameters are invalid.</span></span> |
| <span data-ttu-id="59ee4-153">404</span><span class="sxs-lookup"><span data-stu-id="59ee4-153">404</span></span>  | <span data-ttu-id="59ee4-154">Die angegebene Übermittlung konnte nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="59ee4-154">The specified submission could not be found.</span></span> |
| <span data-ttu-id="59ee4-155">409</span><span class="sxs-lookup"><span data-stu-id="59ee4-155">409</span></span>  | <span data-ttu-id="59ee4-156">Die angegebene Übermittlung wurde gefunden, konnte jedoch nicht in ihrem aktuellen Zustand gelöscht werden. Oder die App verwendet ein Dev Center-Dashboard-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt wird](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span><span class="sxs-lookup"><span data-stu-id="59ee4-156">The specified submission was found but it could not be deleted in its current state, or the app uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |


## <a name="related-topics"></a><span data-ttu-id="59ee4-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="59ee4-157">Related topics</span></span>

* [<span data-ttu-id="59ee4-158">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="59ee4-158">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="59ee4-159">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-159">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="59ee4-160">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-160">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="59ee4-161">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-161">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="59ee4-162">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-162">Update an app submission</span></span>](update-an-app-submission.md)
* [<span data-ttu-id="59ee4-163">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="59ee4-163">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
