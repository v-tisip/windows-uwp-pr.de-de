---
ms.assetid: 8C63D33B-557D-436E-9DDA-11F7A5BFA2D7
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Add-On-Übermittlung.
title: Aktualisieren einer Add-On-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, Aktualisieren, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: fd0bb8df9b9fc36216da72e4ad01ebd2e650ad1a
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7698026"
---
# <a name="update-an-add-on-submission"></a><span data-ttu-id="e0b3e-104">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-104">Update an add-on submission</span></span>


<span data-ttu-id="e0b3e-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Add-On-Übermittlung (Add-Ons werden auch als In-App-Produkt bzw. IAP bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-105">Use this method in the Microsoft Store submission API to update an existing add-on (also known as in-app product or IAP) submission.</span></span> <span data-ttu-id="e0b3e-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-an-add-on-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-106">After you successfully update a submission by using this method, you must [commit the submission](commit-an-add-on-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="e0b3e-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer Add-On-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-107">For more information about how this method fits into the process of creating an add-on submission by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0b3e-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e0b3e-108">Prerequisites</span></span>

<span data-ttu-id="e0b3e-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="e0b3e-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="e0b3e-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="e0b3e-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="e0b3e-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="e0b3e-114">Erstellen einer Add-on-Übermittlungs für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-114">Create an add-on submission for one of your apps.</span></span> <span data-ttu-id="e0b3e-115">Sie können dies im Partner Center oder hierzu können Sie mithilfe der Methode [Erstellen einer Add-on-Übermittlung](create-an-add-on-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="e0b3e-115">You can do this in Partner Center, or you can do this by using the [Create an add-on submission](create-an-add-on-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="e0b3e-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-116">Request</span></span>

<span data-ttu-id="e0b3e-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-117">This method has the following syntax.</span></span> <span data-ttu-id="e0b3e-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="e0b3e-119">Methode</span><span class="sxs-lookup"><span data-stu-id="e0b3e-119">Method</span></span> | <span data-ttu-id="e0b3e-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e0b3e-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="e0b3e-121">PUT</span><span class="sxs-lookup"><span data-stu-id="e0b3e-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId} ``` |


### <a name="request-header"></a><span data-ttu-id="e0b3e-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e0b3e-122">Request header</span></span>

| <span data-ttu-id="e0b3e-123">Header</span><span class="sxs-lookup"><span data-stu-id="e0b3e-123">Header</span></span>        | <span data-ttu-id="e0b3e-124">Typ</span><span class="sxs-lookup"><span data-stu-id="e0b3e-124">Type</span></span>   | <span data-ttu-id="e0b3e-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="e0b3e-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-126">Authorization</span></span> | <span data-ttu-id="e0b3e-127">String</span><span class="sxs-lookup"><span data-stu-id="e0b3e-127">string</span></span> | <span data-ttu-id="e0b3e-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-128">Required.</span></span> <span data-ttu-id="e0b3e-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="e0b3e-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="e0b3e-130">Request parameters</span></span>

| <span data-ttu-id="e0b3e-131">Name</span><span class="sxs-lookup"><span data-stu-id="e0b3e-131">Name</span></span>        | <span data-ttu-id="e0b3e-132">Typ</span><span class="sxs-lookup"><span data-stu-id="e0b3e-132">Type</span></span>   | <span data-ttu-id="e0b3e-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="e0b3e-134">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="e0b3e-134">inAppProductId</span></span> | <span data-ttu-id="e0b3e-135">String</span><span class="sxs-lookup"><span data-stu-id="e0b3e-135">string</span></span> | <span data-ttu-id="e0b3e-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-136">Required.</span></span> <span data-ttu-id="e0b3e-137">Die Store-ID des Add-Ons, für das Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-137">The Store ID of the add-on for which you want to update a submission.</span></span> <span data-ttu-id="e0b3e-138">Die Store-ID ist im Partner Center verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen eines Add-Ons](create-an-add-on.md) oder [Abrufen von Add-on-Informationen](get-all-add-ons.md)enthalten.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-138">The Store ID is available in Partner Center, and it is included in the response data for requests to [Create an add-on](create-an-add-on.md) or [get add-on details](get-all-add-ons.md).</span></span>  |
| <span data-ttu-id="e0b3e-139">submissionId</span><span class="sxs-lookup"><span data-stu-id="e0b3e-139">submissionId</span></span> | <span data-ttu-id="e0b3e-140">String</span><span class="sxs-lookup"><span data-stu-id="e0b3e-140">string</span></span> | <span data-ttu-id="e0b3e-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-141">Required.</span></span> <span data-ttu-id="e0b3e-142">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-142">The ID of the submission to update.</span></span> <span data-ttu-id="e0b3e-143">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-143">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="e0b3e-144">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-144">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="e0b3e-145">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="e0b3e-145">Request body</span></span>

<span data-ttu-id="e0b3e-146">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-146">The request body has the following parameters.</span></span>

| <span data-ttu-id="e0b3e-147">Wert</span><span class="sxs-lookup"><span data-stu-id="e0b3e-147">Value</span></span>      | <span data-ttu-id="e0b3e-148">Typ</span><span class="sxs-lookup"><span data-stu-id="e0b3e-148">Type</span></span>   | <span data-ttu-id="e0b3e-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-149">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e0b3e-150">contentType</span><span class="sxs-lookup"><span data-stu-id="e0b3e-150">contentType</span></span>           | <span data-ttu-id="e0b3e-151">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-151">string</span></span>  |  <span data-ttu-id="e0b3e-152">Der [Inhaltstyp](../publish/enter-add-on-properties.md#content-type), der im Add-On bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-152">The [type of content](../publish/enter-add-on-properties.md#content-type) that is provided in the add-on.</span></span> <span data-ttu-id="e0b3e-153">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-153">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="e0b3e-154">NotSet</span><span class="sxs-lookup"><span data-stu-id="e0b3e-154">NotSet</span></span></li><li><span data-ttu-id="e0b3e-155">BookDownload</span><span class="sxs-lookup"><span data-stu-id="e0b3e-155">BookDownload</span></span></li><li><span data-ttu-id="e0b3e-156">EMagazine</span><span class="sxs-lookup"><span data-stu-id="e0b3e-156">EMagazine</span></span></li><li><span data-ttu-id="e0b3e-157">ENewspaper</span><span class="sxs-lookup"><span data-stu-id="e0b3e-157">ENewspaper</span></span></li><li><span data-ttu-id="e0b3e-158">MusicDownload</span><span class="sxs-lookup"><span data-stu-id="e0b3e-158">MusicDownload</span></span></li><li><span data-ttu-id="e0b3e-159">MusicStream</span><span class="sxs-lookup"><span data-stu-id="e0b3e-159">MusicStream</span></span></li><li><span data-ttu-id="e0b3e-160">OnlineDataStorage</span><span class="sxs-lookup"><span data-stu-id="e0b3e-160">OnlineDataStorage</span></span></li><li><span data-ttu-id="e0b3e-161">VideoDownload</span><span class="sxs-lookup"><span data-stu-id="e0b3e-161">VideoDownload</span></span></li><li><span data-ttu-id="e0b3e-162">VideoStream</span><span class="sxs-lookup"><span data-stu-id="e0b3e-162">VideoStream</span></span></li><li><span data-ttu-id="e0b3e-163">Asp</span><span class="sxs-lookup"><span data-stu-id="e0b3e-163">Asp</span></span></li><li><span data-ttu-id="e0b3e-164">OnlineDownload</span><span class="sxs-lookup"><span data-stu-id="e0b3e-164">OnlineDownload</span></span></li></ul> |  
| <span data-ttu-id="e0b3e-165">keywords</span><span class="sxs-lookup"><span data-stu-id="e0b3e-165">keywords</span></span>           | <span data-ttu-id="e0b3e-166">array</span><span class="sxs-lookup"><span data-stu-id="e0b3e-166">array</span></span>  | <span data-ttu-id="e0b3e-167">Ein Array von Zeichenfolgen, das bis zu 10 [Schlüsselwörter](../publish/enter-add-on-properties.md#keywords) für das Add-On enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-167">An array of strings that contain up to 10 [keywords](../publish/enter-add-on-properties.md#keywords) for the add-on.</span></span> <span data-ttu-id="e0b3e-168">Die App kann mit diesen Schlüsselwörter Add-Ons abfragen.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-168">Your app can query for add-ons using these keywords.</span></span>   |
| <span data-ttu-id="e0b3e-169">lifetime</span><span class="sxs-lookup"><span data-stu-id="e0b3e-169">lifetime</span></span>           | <span data-ttu-id="e0b3e-170">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-170">string</span></span>  |  <span data-ttu-id="e0b3e-171">Die Lebensdauer des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-171">The lifetime of the add-on.</span></span> <span data-ttu-id="e0b3e-172">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-172">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="e0b3e-173">Forever</span><span class="sxs-lookup"><span data-stu-id="e0b3e-173">Forever</span></span></li><li><span data-ttu-id="e0b3e-174">OneDay</span><span class="sxs-lookup"><span data-stu-id="e0b3e-174">OneDay</span></span></li><li><span data-ttu-id="e0b3e-175">ThreeDays</span><span class="sxs-lookup"><span data-stu-id="e0b3e-175">ThreeDays</span></span></li><li><span data-ttu-id="e0b3e-176">FiveDays</span><span class="sxs-lookup"><span data-stu-id="e0b3e-176">FiveDays</span></span></li><li><span data-ttu-id="e0b3e-177">OneWeek</span><span class="sxs-lookup"><span data-stu-id="e0b3e-177">OneWeek</span></span></li><li><span data-ttu-id="e0b3e-178">TwoWeeks</span><span class="sxs-lookup"><span data-stu-id="e0b3e-178">TwoWeeks</span></span></li><li><span data-ttu-id="e0b3e-179">OneMonth</span><span class="sxs-lookup"><span data-stu-id="e0b3e-179">OneMonth</span></span></li><li><span data-ttu-id="e0b3e-180">TwoMonths</span><span class="sxs-lookup"><span data-stu-id="e0b3e-180">TwoMonths</span></span></li><li><span data-ttu-id="e0b3e-181">ThreeMonths</span><span class="sxs-lookup"><span data-stu-id="e0b3e-181">ThreeMonths</span></span></li><li><span data-ttu-id="e0b3e-182">SixMonths</span><span class="sxs-lookup"><span data-stu-id="e0b3e-182">SixMonths</span></span></li><li><span data-ttu-id="e0b3e-183">OneYear</span><span class="sxs-lookup"><span data-stu-id="e0b3e-183">OneYear</span></span></li></ul> |
| <span data-ttu-id="e0b3e-184">listings</span><span class="sxs-lookup"><span data-stu-id="e0b3e-184">listings</span></span>           | <span data-ttu-id="e0b3e-185">object</span><span class="sxs-lookup"><span data-stu-id="e0b3e-185">object</span></span>  | <span data-ttu-id="e0b3e-186">Ein Objekt, das Eintragsinfos für das Add-On enthält.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-186">An object that contains listing info for the add-on.</span></span> <span data-ttu-id="e0b3e-187">Weitere Informationen finden Sie unter [Eintragsressource](manage-add-on-submissions.md#listing-object).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-187">For more information, see [Listing resource](manage-add-on-submissions.md#listing-object).</span></span>  |
| <span data-ttu-id="e0b3e-188">pricing</span><span class="sxs-lookup"><span data-stu-id="e0b3e-188">pricing</span></span>           | <span data-ttu-id="e0b3e-189">object</span><span class="sxs-lookup"><span data-stu-id="e0b3e-189">object</span></span>  | <span data-ttu-id="e0b3e-190">Ein Objekt, das Eintragsinfos für das Add-On enthält.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-190">An object that contains pricing info for the add-on.</span></span> <span data-ttu-id="e0b3e-191">Weitere Informationen finden Sie unter [Preisressource](manage-add-on-submissions.md#pricing-object).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-191">For more information, see [Pricing resource](manage-add-on-submissions.md#pricing-object).</span></span>  |
| <span data-ttu-id="e0b3e-192">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="e0b3e-192">targetPublishMode</span></span>           | <span data-ttu-id="e0b3e-193">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-193">string</span></span>  | <span data-ttu-id="e0b3e-194">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-194">The publish mode for the submission.</span></span> <span data-ttu-id="e0b3e-195">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-195">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="e0b3e-196">Immediate</span><span class="sxs-lookup"><span data-stu-id="e0b3e-196">Immediate</span></span></li><li><span data-ttu-id="e0b3e-197">Manual</span><span class="sxs-lookup"><span data-stu-id="e0b3e-197">Manual</span></span></li><li><span data-ttu-id="e0b3e-198">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="e0b3e-198">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="e0b3e-199">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="e0b3e-199">targetPublishDate</span></span>           | <span data-ttu-id="e0b3e-200">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-200">string</span></span>  | <span data-ttu-id="e0b3e-201">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-201">The publish date for the submission in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |
| <span data-ttu-id="e0b3e-202">tag</span><span class="sxs-lookup"><span data-stu-id="e0b3e-202">tag</span></span>           | <span data-ttu-id="e0b3e-203">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-203">string</span></span>  |  <span data-ttu-id="e0b3e-204">Die [benutzerdefinierten Entwicklerdaten](../publish/enter-add-on-properties.md#custom-developer-data) für das Add-On (diese Informationen wurden zuvor als *tag* bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-204">The [custom developer data](../publish/enter-add-on-properties.md#custom-developer-data) for the add-on (this information was previously called the *tag*).</span></span>   |
| <span data-ttu-id="e0b3e-205">visibility</span><span class="sxs-lookup"><span data-stu-id="e0b3e-205">visibility</span></span>  | <span data-ttu-id="e0b3e-206">string</span><span class="sxs-lookup"><span data-stu-id="e0b3e-206">string</span></span>  |  <span data-ttu-id="e0b3e-207">Die Sichtbarkeit des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-207">The visibility of the add-on.</span></span> <span data-ttu-id="e0b3e-208">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="e0b3e-208">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="e0b3e-209">Hidden</span><span class="sxs-lookup"><span data-stu-id="e0b3e-209">Hidden</span></span></li><li><span data-ttu-id="e0b3e-210">Public</span><span class="sxs-lookup"><span data-stu-id="e0b3e-210">Public</span></span></li><li><span data-ttu-id="e0b3e-211">Private</span><span class="sxs-lookup"><span data-stu-id="e0b3e-211">Private</span></span></li><li><span data-ttu-id="e0b3e-212">NotSet</span><span class="sxs-lookup"><span data-stu-id="e0b3e-212">NotSet</span></span></li></ul>  |


### <a name="request-example"></a><span data-ttu-id="e0b3e-213">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="e0b3e-213">Request example</span></span>

<span data-ttu-id="e0b3e-214">Im folgenden Beispiel wird die Aktualisierung einer Add-On-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-214">The following example demonstrates how to update an add-on submission.</span></span>

```json
PUT https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/9NBLGGH4TNMP/submissions/1152921504621230023 HTTP/1.1
Authorization: Bearer <your access token>
Content-Type: application/json
{
  "contentType": "EMagazine",
  "keywords": [
    "books"
  ],
  "lifetime": "FiveDays",
  "listings": {
    "en": {
      "description": "English add-on description",
      "icon": {
        "fileName": "add-on-en-us-listing2.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (English)"
    },
    "ru": {
      "description": "Russian add-on description",
      "icon": {
        "fileName": "add-on-ru-listing.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (Russian)"
    }
  },
  "pricing": {
    "marketSpecificPricings": {
      "RU": "Tier3",
      "US": "Tier4",
    },
    "sales": [],
    "priceId": "Free"
  },
  "targetPublishDate": "2016-03-15T05:10:58.047Z",
  "targetPublishMode": "Immediate",
  "tag": "SampleTag",
  "visibility": "Public",
}
```

## <a name="response"></a><span data-ttu-id="e0b3e-215">Antwort</span><span class="sxs-lookup"><span data-stu-id="e0b3e-215">Response</span></span>

<span data-ttu-id="e0b3e-216">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-216">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="e0b3e-217">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-217">The response body contains information about the updated submission.</span></span> <span data-ttu-id="e0b3e-218">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-on-submissions.md#add-on-submission-object).</span><span class="sxs-lookup"><span data-stu-id="e0b3e-218">For more details about the values in the response body, see [Add-on submission resource](manage-add-on-submissions.md#add-on-submission-object).</span></span>

```json
{
  "id": "1152921504621243680",
  "contentType": "EMagazine",
  "keywords": [
    "books"
  ],
  "lifetime": "FiveDays",
  "listings": {
    "en": {
      "description": "English add-on description",
      "icon": {
        "fileName": "add-on-en-us-listing2.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (English)"
    },
    "ru": {
      "description": "Russian add-on description",
      "icon": {
        "fileName": "add-on-ru-listing.png",
        "fileStatus": "Uploaded"
      },
      "title": "Add-on Title (Russian)"
    }
  },
  "pricing": {
    "marketSpecificPricings": {
      "RU": "Tier3",
      "US": "Tier4",
    },
    "sales": [],
    "priceId": "Free"
  },
  "targetPublishDate": "2016-03-15T05:10:58.047Z",
  "targetPublishMode": "Immediate",
  "tag": "SampleTag",
  "visibility": "Public",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [
      {
        "code": "None",
        "details": "string"
      }
    ],
    "warnings": [
      {
        "code": "ListingOptOutWarning",
        "details": "You have removed listing language(s): []"
      }
    ],
    "certificationReports": [
      {
      }
    ]
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/26920f66-b592-4439-9a9d-fb0f014902ec?sv=2014-02-14&sr=b&sig=usAN0kNFNnYE2tGQBI%2BARQWejX1Guiz7hdFtRhyK%2Bog%3D&se=2016-06-17T20:45:51Z&sp=rwl",
  "friendlyName": "Submission 2"
}
```

## <a name="error-codes"></a><span data-ttu-id="e0b3e-219">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="e0b3e-219">Error codes</span></span>

<span data-ttu-id="e0b3e-220">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-220">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="e0b3e-221">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="e0b3e-221">Error code</span></span> |  <span data-ttu-id="e0b3e-222">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-222">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="e0b3e-223">400</span><span class="sxs-lookup"><span data-stu-id="e0b3e-223">400</span></span>  | <span data-ttu-id="e0b3e-224">Die Übermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-224">The submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="e0b3e-225">409</span><span class="sxs-lookup"><span data-stu-id="e0b3e-225">409</span></span>  | <span data-ttu-id="e0b3e-226">Die Übermittlung konnte im aktuellen Zustand des Add-Ons nicht aktualisiert werden, oder das Add-on verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="e0b3e-226">The submission could not be updated because of the current state of the add-on, or the add-on uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="e0b3e-227">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e0b3e-227">Related topics</span></span>

* [<span data-ttu-id="e0b3e-228">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="e0b3e-228">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="e0b3e-229">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="e0b3e-229">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="e0b3e-230">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-230">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="e0b3e-231">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-231">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="e0b3e-232">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-232">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="e0b3e-233">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-233">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="e0b3e-234">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="e0b3e-234">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
