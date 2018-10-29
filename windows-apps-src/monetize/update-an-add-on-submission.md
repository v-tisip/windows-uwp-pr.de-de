---
author: Xansky
ms.assetid: 8C63D33B-557D-436E-9DDA-11F7A5BFA2D7
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Add-On-Übermittlung.
title: Aktualisieren einer Add-On-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Add-On-Übermittlung, Aktualisieren, In-App-Produkt, IAP
ms.localizationpriority: medium
ms.openlocfilehash: a8c3faf3b3be554e3cbb5bc4891887559ac14ea2
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5740579"
---
# <a name="update-an-add-on-submission"></a><span data-ttu-id="79354-104">Aktualisieren einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-104">Update an add-on submission</span></span>


<span data-ttu-id="79354-105">Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen Add-On-Übermittlung (Add-Ons werden auch als In-App-Produkt bzw. IAP bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="79354-105">Use this method in the Microsoft Store submission API to update an existing add-on (also known as in-app product or IAP) submission.</span></span> <span data-ttu-id="79354-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-an-add-on-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="79354-106">After you successfully update a submission by using this method, you must [commit the submission](commit-an-add-on-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="79354-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer Add-On-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="79354-107">For more information about how this method fits into the process of creating an add-on submission by using the Microsoft Store submission API, see [Manage add-on submissions](manage-add-on-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79354-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="79354-108">Prerequisites</span></span>

<span data-ttu-id="79354-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="79354-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="79354-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="79354-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="79354-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="79354-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="79354-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="79354-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="79354-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="79354-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="79354-114">Erstellen Sie eine Add-On-Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="79354-114">Create an add-on submission for an app in your Dev Center account.</span></span> <span data-ttu-id="79354-115">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="79354-115">You can do this in the Dev Center dashboard, or you can do this by using the [Create an add-on submission](create-an-add-on-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="79354-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="79354-116">Request</span></span>

<span data-ttu-id="79354-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="79354-117">This method has the following syntax.</span></span> <span data-ttu-id="79354-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="79354-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="79354-119">Methode</span><span class="sxs-lookup"><span data-stu-id="79354-119">Method</span></span> | <span data-ttu-id="79354-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="79354-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="79354-121">PUT</span><span class="sxs-lookup"><span data-stu-id="79354-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}/submissions/{submissionId} ``` |


### <a name="request-header"></a><span data-ttu-id="79354-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="79354-122">Request header</span></span>

| <span data-ttu-id="79354-123">Header</span><span class="sxs-lookup"><span data-stu-id="79354-123">Header</span></span>        | <span data-ttu-id="79354-124">Typ</span><span class="sxs-lookup"><span data-stu-id="79354-124">Type</span></span>   | <span data-ttu-id="79354-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="79354-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="79354-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="79354-126">Authorization</span></span> | <span data-ttu-id="79354-127">String</span><span class="sxs-lookup"><span data-stu-id="79354-127">string</span></span> | <span data-ttu-id="79354-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="79354-128">Required.</span></span> <span data-ttu-id="79354-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="79354-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="79354-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="79354-130">Request parameters</span></span>

| <span data-ttu-id="79354-131">Name</span><span class="sxs-lookup"><span data-stu-id="79354-131">Name</span></span>        | <span data-ttu-id="79354-132">Typ</span><span class="sxs-lookup"><span data-stu-id="79354-132">Type</span></span>   | <span data-ttu-id="79354-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="79354-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="79354-134">inAppProductId</span><span class="sxs-lookup"><span data-stu-id="79354-134">inAppProductId</span></span> | <span data-ttu-id="79354-135">String</span><span class="sxs-lookup"><span data-stu-id="79354-135">string</span></span> | <span data-ttu-id="79354-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="79354-136">Required.</span></span> <span data-ttu-id="79354-137">Die Store-ID des Add-Ons, für das Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="79354-137">The Store ID of the add-on for which you want to update a submission.</span></span> <span data-ttu-id="79354-138">Die Store-ID ist im Windows Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen eines Add-Ons](create-an-add-on.md) und zum [Abrufen von Add-On-Details](get-all-add-ons.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="79354-138">The Store ID is available on the Dev Center dashboard, and it is included in the response data for requests to [Create an add-on](create-an-add-on.md) or [get add-on details](get-all-add-ons.md).</span></span>  |
| <span data-ttu-id="79354-139">submissionId</span><span class="sxs-lookup"><span data-stu-id="79354-139">submissionId</span></span> | <span data-ttu-id="79354-140">String</span><span class="sxs-lookup"><span data-stu-id="79354-140">string</span></span> | <span data-ttu-id="79354-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="79354-141">Required.</span></span> <span data-ttu-id="79354-142">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="79354-142">The ID of the submission to update.</span></span> <span data-ttu-id="79354-143">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer Add-On-Übermittlung](create-an-add-on-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="79354-143">This ID is available in the response data for requests to [create an add-on submission](create-an-add-on-submission.md).</span></span> <span data-ttu-id="79354-144">Für eine Übermittlung, die im Dev Center-Dashboard erstellt wurde, ist diese ID auch in der URL für die Übermittlungsseite im Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="79354-144">For a submission that was created in the Dev Center dashboard, this ID is also available in the URL for the submission page in the dashboard.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="79354-145">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="79354-145">Request body</span></span>

<span data-ttu-id="79354-146">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="79354-146">The request body has the following parameters.</span></span>

| <span data-ttu-id="79354-147">Wert</span><span class="sxs-lookup"><span data-stu-id="79354-147">Value</span></span>      | <span data-ttu-id="79354-148">Typ</span><span class="sxs-lookup"><span data-stu-id="79354-148">Type</span></span>   | <span data-ttu-id="79354-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="79354-149">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="79354-150">contentType</span><span class="sxs-lookup"><span data-stu-id="79354-150">contentType</span></span>           | <span data-ttu-id="79354-151">string</span><span class="sxs-lookup"><span data-stu-id="79354-151">string</span></span>  |  <span data-ttu-id="79354-152">Der [Inhaltstyp](../publish/enter-add-on-properties.md#content-type), der im Add-On bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="79354-152">The [type of content](../publish/enter-add-on-properties.md#content-type) that is provided in the add-on.</span></span> <span data-ttu-id="79354-153">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="79354-153">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="79354-154">NotSet</span><span class="sxs-lookup"><span data-stu-id="79354-154">NotSet</span></span></li><li><span data-ttu-id="79354-155">BookDownload</span><span class="sxs-lookup"><span data-stu-id="79354-155">BookDownload</span></span></li><li><span data-ttu-id="79354-156">EMagazine</span><span class="sxs-lookup"><span data-stu-id="79354-156">EMagazine</span></span></li><li><span data-ttu-id="79354-157">ENewspaper</span><span class="sxs-lookup"><span data-stu-id="79354-157">ENewspaper</span></span></li><li><span data-ttu-id="79354-158">MusicDownload</span><span class="sxs-lookup"><span data-stu-id="79354-158">MusicDownload</span></span></li><li><span data-ttu-id="79354-159">MusicStream</span><span class="sxs-lookup"><span data-stu-id="79354-159">MusicStream</span></span></li><li><span data-ttu-id="79354-160">OnlineDataStorage</span><span class="sxs-lookup"><span data-stu-id="79354-160">OnlineDataStorage</span></span></li><li><span data-ttu-id="79354-161">VideoDownload</span><span class="sxs-lookup"><span data-stu-id="79354-161">VideoDownload</span></span></li><li><span data-ttu-id="79354-162">VideoStream</span><span class="sxs-lookup"><span data-stu-id="79354-162">VideoStream</span></span></li><li><span data-ttu-id="79354-163">Asp</span><span class="sxs-lookup"><span data-stu-id="79354-163">Asp</span></span></li><li><span data-ttu-id="79354-164">OnlineDownload</span><span class="sxs-lookup"><span data-stu-id="79354-164">OnlineDownload</span></span></li></ul> |  
| <span data-ttu-id="79354-165">keywords</span><span class="sxs-lookup"><span data-stu-id="79354-165">keywords</span></span>           | <span data-ttu-id="79354-166">array</span><span class="sxs-lookup"><span data-stu-id="79354-166">array</span></span>  | <span data-ttu-id="79354-167">Ein Array von Zeichenfolgen, das bis zu 10 [Schlüsselwörter](../publish/enter-add-on-properties.md#keywords) für das Add-On enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="79354-167">An array of strings that contain up to 10 [keywords](../publish/enter-add-on-properties.md#keywords) for the add-on.</span></span> <span data-ttu-id="79354-168">Die App kann mit diesen Schlüsselwörter Add-Ons abfragen.</span><span class="sxs-lookup"><span data-stu-id="79354-168">Your app can query for add-ons using these keywords.</span></span>   |
| <span data-ttu-id="79354-169">lifetime</span><span class="sxs-lookup"><span data-stu-id="79354-169">lifetime</span></span>           | <span data-ttu-id="79354-170">string</span><span class="sxs-lookup"><span data-stu-id="79354-170">string</span></span>  |  <span data-ttu-id="79354-171">Die Lebensdauer des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="79354-171">The lifetime of the add-on.</span></span> <span data-ttu-id="79354-172">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="79354-172">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="79354-173">Forever</span><span class="sxs-lookup"><span data-stu-id="79354-173">Forever</span></span></li><li><span data-ttu-id="79354-174">OneDay</span><span class="sxs-lookup"><span data-stu-id="79354-174">OneDay</span></span></li><li><span data-ttu-id="79354-175">ThreeDays</span><span class="sxs-lookup"><span data-stu-id="79354-175">ThreeDays</span></span></li><li><span data-ttu-id="79354-176">FiveDays</span><span class="sxs-lookup"><span data-stu-id="79354-176">FiveDays</span></span></li><li><span data-ttu-id="79354-177">OneWeek</span><span class="sxs-lookup"><span data-stu-id="79354-177">OneWeek</span></span></li><li><span data-ttu-id="79354-178">TwoWeeks</span><span class="sxs-lookup"><span data-stu-id="79354-178">TwoWeeks</span></span></li><li><span data-ttu-id="79354-179">OneMonth</span><span class="sxs-lookup"><span data-stu-id="79354-179">OneMonth</span></span></li><li><span data-ttu-id="79354-180">TwoMonths</span><span class="sxs-lookup"><span data-stu-id="79354-180">TwoMonths</span></span></li><li><span data-ttu-id="79354-181">ThreeMonths</span><span class="sxs-lookup"><span data-stu-id="79354-181">ThreeMonths</span></span></li><li><span data-ttu-id="79354-182">SixMonths</span><span class="sxs-lookup"><span data-stu-id="79354-182">SixMonths</span></span></li><li><span data-ttu-id="79354-183">OneYear</span><span class="sxs-lookup"><span data-stu-id="79354-183">OneYear</span></span></li></ul> |
| <span data-ttu-id="79354-184">listings</span><span class="sxs-lookup"><span data-stu-id="79354-184">listings</span></span>           | <span data-ttu-id="79354-185">object</span><span class="sxs-lookup"><span data-stu-id="79354-185">object</span></span>  | <span data-ttu-id="79354-186">Ein Objekt, das Eintragsinfos für das Add-On enthält.</span><span class="sxs-lookup"><span data-stu-id="79354-186">An object that contains listing info for the add-on.</span></span> <span data-ttu-id="79354-187">Weitere Informationen finden Sie unter [Eintragsressource](manage-add-on-submissions.md#listing-object).</span><span class="sxs-lookup"><span data-stu-id="79354-187">For more information, see [Listing resource](manage-add-on-submissions.md#listing-object).</span></span>  |
| <span data-ttu-id="79354-188">pricing</span><span class="sxs-lookup"><span data-stu-id="79354-188">pricing</span></span>           | <span data-ttu-id="79354-189">object</span><span class="sxs-lookup"><span data-stu-id="79354-189">object</span></span>  | <span data-ttu-id="79354-190">Ein Objekt, das Eintragsinfos für das Add-On enthält.</span><span class="sxs-lookup"><span data-stu-id="79354-190">An object that contains pricing info for the add-on.</span></span> <span data-ttu-id="79354-191">Weitere Informationen finden Sie unter [Preisressource](manage-add-on-submissions.md#pricing-object).</span><span class="sxs-lookup"><span data-stu-id="79354-191">For more information, see [Pricing resource](manage-add-on-submissions.md#pricing-object).</span></span>  |
| <span data-ttu-id="79354-192">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="79354-192">targetPublishMode</span></span>           | <span data-ttu-id="79354-193">string</span><span class="sxs-lookup"><span data-stu-id="79354-193">string</span></span>  | <span data-ttu-id="79354-194">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="79354-194">The publish mode for the submission.</span></span> <span data-ttu-id="79354-195">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="79354-195">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="79354-196">Immediate</span><span class="sxs-lookup"><span data-stu-id="79354-196">Immediate</span></span></li><li><span data-ttu-id="79354-197">Manual</span><span class="sxs-lookup"><span data-stu-id="79354-197">Manual</span></span></li><li><span data-ttu-id="79354-198">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="79354-198">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="79354-199">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="79354-199">targetPublishDate</span></span>           | <span data-ttu-id="79354-200">string</span><span class="sxs-lookup"><span data-stu-id="79354-200">string</span></span>  | <span data-ttu-id="79354-201">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="79354-201">The publish date for the submission in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |
| <span data-ttu-id="79354-202">tag</span><span class="sxs-lookup"><span data-stu-id="79354-202">tag</span></span>           | <span data-ttu-id="79354-203">string</span><span class="sxs-lookup"><span data-stu-id="79354-203">string</span></span>  |  <span data-ttu-id="79354-204">Die [benutzerdefinierten Entwicklerdaten](../publish/enter-add-on-properties.md#custom-developer-data) für das Add-On (diese Informationen wurden zuvor als *tag* bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="79354-204">The [custom developer data](../publish/enter-add-on-properties.md#custom-developer-data) for the add-on (this information was previously called the *tag*).</span></span>   |
| <span data-ttu-id="79354-205">visibility</span><span class="sxs-lookup"><span data-stu-id="79354-205">visibility</span></span>  | <span data-ttu-id="79354-206">string</span><span class="sxs-lookup"><span data-stu-id="79354-206">string</span></span>  |  <span data-ttu-id="79354-207">Die Sichtbarkeit des Add-Ons.</span><span class="sxs-lookup"><span data-stu-id="79354-207">The visibility of the add-on.</span></span> <span data-ttu-id="79354-208">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="79354-208">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="79354-209">Hidden</span><span class="sxs-lookup"><span data-stu-id="79354-209">Hidden</span></span></li><li><span data-ttu-id="79354-210">Public</span><span class="sxs-lookup"><span data-stu-id="79354-210">Public</span></span></li><li><span data-ttu-id="79354-211">Private</span><span class="sxs-lookup"><span data-stu-id="79354-211">Private</span></span></li><li><span data-ttu-id="79354-212">NotSet</span><span class="sxs-lookup"><span data-stu-id="79354-212">NotSet</span></span></li></ul>  |


### <a name="request-example"></a><span data-ttu-id="79354-213">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="79354-213">Request example</span></span>

<span data-ttu-id="79354-214">Im folgenden Beispiel wird die Aktualisierung einer Add-On-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="79354-214">The following example demonstrates how to update an add-on submission.</span></span>

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

## <a name="response"></a><span data-ttu-id="79354-215">Antwort</span><span class="sxs-lookup"><span data-stu-id="79354-215">Response</span></span>

<span data-ttu-id="79354-216">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="79354-216">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="79354-217">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="79354-217">The response body contains information about the updated submission.</span></span> <span data-ttu-id="79354-218">Weitere Informationen zu den Werten im Antworttext finden Sie unter [Add-On-Übermittlungsressource](manage-add-on-submissions.md#add-on-submission-object).</span><span class="sxs-lookup"><span data-stu-id="79354-218">For more details about the values in the response body, see [Add-on submission resource](manage-add-on-submissions.md#add-on-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="79354-219">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="79354-219">Error codes</span></span>

<span data-ttu-id="79354-220">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="79354-220">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="79354-221">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="79354-221">Error code</span></span> |  <span data-ttu-id="79354-222">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="79354-222">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="79354-223">400</span><span class="sxs-lookup"><span data-stu-id="79354-223">400</span></span>  | <span data-ttu-id="79354-224">Die Übermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="79354-224">The submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="79354-225">409</span><span class="sxs-lookup"><span data-stu-id="79354-225">409</span></span>  | <span data-ttu-id="79354-226">Die Übermittlung konnte im aktuellen Zustand des Add-Ons nicht aktualisiert werden, oder im Add-On wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="79354-226">The submission could not be updated because of the current state of the add-on, or the add-on uses a Dev Center dashboard feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="79354-227">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="79354-227">Related topics</span></span>

* [<span data-ttu-id="79354-228">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="79354-228">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="79354-229">Verwalten von Add-On-Übermittlungen</span><span class="sxs-lookup"><span data-stu-id="79354-229">Manage add-on submissions</span></span>](manage-add-on-submissions.md)
* [<span data-ttu-id="79354-230">Abrufen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-230">Get an add-on submission</span></span>](get-an-add-on-submission.md)
* [<span data-ttu-id="79354-231">Erstellen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-231">Create an add-on submission</span></span>](create-an-add-on-submission.md)
* [<span data-ttu-id="79354-232">Ausführen eines Commit für eine Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-232">Commit an add-on submission</span></span>](commit-an-add-on-submission.md)
* [<span data-ttu-id="79354-233">Löschen einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-233">Delete an add-on submission</span></span>](delete-an-add-on-submission.md)
* [<span data-ttu-id="79354-234">Abrufen des Status einer Add-On-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="79354-234">Get the status of an add-on submission</span></span>](get-status-for-an-add-on-submission.md)
