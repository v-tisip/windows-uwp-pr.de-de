---
ms.assetid: E8751EBF-AE0F-4107-80A1-23C186453B1C
description: Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen App-Übermittlung.
title: Aktualisieren einer App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, App-Übermittlung, Aktualisieren
ms.localizationpriority: medium
ms.openlocfilehash: b61508edf2ebc2ab155110189fe67df63e2bab30
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8736547"
---
# <a name="update-an-app-submission"></a><span data-ttu-id="2fccc-104">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-104">Update an app submission</span></span>

<span data-ttu-id="2fccc-105">Verwenden Sie diese Methode aus der Microsoft Store-Übermittlungs-API zur Aktualisierung einer vorhandenen App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="2fccc-105">Use this method in the Microsoft Store submission API to update an existing app submission.</span></span> <span data-ttu-id="2fccc-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-an-app-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="2fccc-106">After you successfully update a submission by using this method, you must [commit the submission](commit-an-app-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="2fccc-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="2fccc-107">For more information about how this method fits into the process of creating an app submission by using the Microsoft Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fccc-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2fccc-108">Prerequisites</span></span>

<span data-ttu-id="2fccc-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="2fccc-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="2fccc-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="2fccc-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Microsoft Store submission API.</span></span>
* <span data-ttu-id="2fccc-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2fccc-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="2fccc-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="2fccc-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="2fccc-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="2fccc-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="2fccc-114">Erstellen Sie eine Übermittlung für eine Ihrer apps.</span><span class="sxs-lookup"><span data-stu-id="2fccc-114">Create a submission for one of your apps.</span></span> <span data-ttu-id="2fccc-115">Sie können dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .</span><span class="sxs-lookup"><span data-stu-id="2fccc-115">You can do this in Partner Center, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="2fccc-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2fccc-116">Request</span></span>

<span data-ttu-id="2fccc-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="2fccc-117">This method has the following syntax.</span></span> <span data-ttu-id="2fccc-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="2fccc-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="2fccc-119">Methode</span><span class="sxs-lookup"><span data-stu-id="2fccc-119">Method</span></span> | <span data-ttu-id="2fccc-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2fccc-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="2fccc-121">PUT</span><span class="sxs-lookup"><span data-stu-id="2fccc-121">PUT</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}  ``` |


### <a name="request-header"></a><span data-ttu-id="2fccc-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2fccc-122">Request header</span></span>

| <span data-ttu-id="2fccc-123">Header</span><span class="sxs-lookup"><span data-stu-id="2fccc-123">Header</span></span>        | <span data-ttu-id="2fccc-124">Typ</span><span class="sxs-lookup"><span data-stu-id="2fccc-124">Type</span></span>   | <span data-ttu-id="2fccc-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2fccc-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2fccc-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="2fccc-126">Authorization</span></span> | <span data-ttu-id="2fccc-127">String</span><span class="sxs-lookup"><span data-stu-id="2fccc-127">string</span></span> | <span data-ttu-id="2fccc-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fccc-128">Required.</span></span> <span data-ttu-id="2fccc-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="2fccc-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="2fccc-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="2fccc-130">Request parameters</span></span>

| <span data-ttu-id="2fccc-131">Name</span><span class="sxs-lookup"><span data-stu-id="2fccc-131">Name</span></span>        | <span data-ttu-id="2fccc-132">Typ</span><span class="sxs-lookup"><span data-stu-id="2fccc-132">Type</span></span>   | <span data-ttu-id="2fccc-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2fccc-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2fccc-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="2fccc-134">applicationId</span></span> | <span data-ttu-id="2fccc-135">String</span><span class="sxs-lookup"><span data-stu-id="2fccc-135">string</span></span> | <span data-ttu-id="2fccc-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fccc-136">Required.</span></span> <span data-ttu-id="2fccc-137">Die Store-ID der App, für die Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="2fccc-137">The Store ID of the app for which you want to update a submission.</span></span> <span data-ttu-id="2fccc-138">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="2fccc-138">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="2fccc-139">submissionId</span><span class="sxs-lookup"><span data-stu-id="2fccc-139">submissionId</span></span> | <span data-ttu-id="2fccc-140">String</span><span class="sxs-lookup"><span data-stu-id="2fccc-140">string</span></span> | <span data-ttu-id="2fccc-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fccc-141">Required.</span></span> <span data-ttu-id="2fccc-142">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="2fccc-142">The ID of the submission to update.</span></span> <span data-ttu-id="2fccc-143">Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2fccc-143">This ID is available in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span> <span data-ttu-id="2fccc-144">Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2fccc-144">For a submission that was created in Partner Center, this ID is also available in the URL for the submission page in Partner Center.</span></span>  |


### <a name="request-body"></a><span data-ttu-id="2fccc-145">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="2fccc-145">Request body</span></span>

<span data-ttu-id="2fccc-146">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="2fccc-146">The request body has the following parameters.</span></span>

| <span data-ttu-id="2fccc-147">Wert</span><span class="sxs-lookup"><span data-stu-id="2fccc-147">Value</span></span>      | <span data-ttu-id="2fccc-148">Typ</span><span class="sxs-lookup"><span data-stu-id="2fccc-148">Type</span></span>   | <span data-ttu-id="2fccc-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2fccc-149">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2fccc-150">applicationCategory</span><span class="sxs-lookup"><span data-stu-id="2fccc-150">applicationCategory</span></span>           | <span data-ttu-id="2fccc-151">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-151">string</span></span>  |   <span data-ttu-id="2fccc-152">Eine Zeichenfolge, die [Kategorie und/oder Unterkategorie](https://msdn.microsoft.com/windows/uwp/publish/category-and-subcategory-table) für Ihre App angibt.</span><span class="sxs-lookup"><span data-stu-id="2fccc-152">A string that specifies the [category and/or subcategory](https://msdn.microsoft.com/windows/uwp/publish/category-and-subcategory-table) for your app.</span></span> <span data-ttu-id="2fccc-153">Kategorien und Unterkategorien werden mit einem Unterstrich "_" zu einer einzigen Zeichenfolge zusammengefasst, z.B. **BooksAndReference_EReader**.</span><span class="sxs-lookup"><span data-stu-id="2fccc-153">Categories and subcategories are combined into a single string with the underscore '_' character, such as **BooksAndReference_EReader**.</span></span>      |  
| <span data-ttu-id="2fccc-154">pricing</span><span class="sxs-lookup"><span data-stu-id="2fccc-154">pricing</span></span>           |  <span data-ttu-id="2fccc-155">object</span><span class="sxs-lookup"><span data-stu-id="2fccc-155">object</span></span>  | <span data-ttu-id="2fccc-156">Ein Objekt, das Preisinfos für die App enthält.</span><span class="sxs-lookup"><span data-stu-id="2fccc-156">An object that contains pricing info for the app.</span></span> <span data-ttu-id="2fccc-157">Weitere Informationen finden Sie im Abschnitt [Preisressource](manage-app-submissions.md#pricing-object).</span><span class="sxs-lookup"><span data-stu-id="2fccc-157">For more information, see the [Pricing resource](manage-app-submissions.md#pricing-object) section.</span></span>       |   
| <span data-ttu-id="2fccc-158">visibility</span><span class="sxs-lookup"><span data-stu-id="2fccc-158">visibility</span></span>           |  <span data-ttu-id="2fccc-159">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-159">string</span></span>  |  <span data-ttu-id="2fccc-160">Die Sichtbarkeit der App.</span><span class="sxs-lookup"><span data-stu-id="2fccc-160">The visibility of the app.</span></span> <span data-ttu-id="2fccc-161">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="2fccc-161">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="2fccc-162">Hidden</span><span class="sxs-lookup"><span data-stu-id="2fccc-162">Hidden</span></span></li><li><span data-ttu-id="2fccc-163">Public</span><span class="sxs-lookup"><span data-stu-id="2fccc-163">Public</span></span></li><li><span data-ttu-id="2fccc-164">Private</span><span class="sxs-lookup"><span data-stu-id="2fccc-164">Private</span></span></li><li><span data-ttu-id="2fccc-165">NotSet</span><span class="sxs-lookup"><span data-stu-id="2fccc-165">NotSet</span></span></li></ul>       |   
| <span data-ttu-id="2fccc-166">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="2fccc-166">targetPublishMode</span></span>           | <span data-ttu-id="2fccc-167">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-167">string</span></span>  | <span data-ttu-id="2fccc-168">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="2fccc-168">The publish mode for the submission.</span></span> <span data-ttu-id="2fccc-169">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="2fccc-169">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="2fccc-170">Immediate</span><span class="sxs-lookup"><span data-stu-id="2fccc-170">Immediate</span></span></li><li><span data-ttu-id="2fccc-171">Manual</span><span class="sxs-lookup"><span data-stu-id="2fccc-171">Manual</span></span></li><li><span data-ttu-id="2fccc-172">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="2fccc-172">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="2fccc-173">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="2fccc-173">targetPublishDate</span></span>           | <span data-ttu-id="2fccc-174">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-174">string</span></span>  | <span data-ttu-id="2fccc-175">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="2fccc-175">The publish date for the submission in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |  
| <span data-ttu-id="2fccc-176">listings</span><span class="sxs-lookup"><span data-stu-id="2fccc-176">listings</span></span>           |   <span data-ttu-id="2fccc-177">object</span><span class="sxs-lookup"><span data-stu-id="2fccc-177">object</span></span>  |  <span data-ttu-id="2fccc-178">Ein Wörterbuch von Schlüssel-Wert-Paaren, wobei ein Schlüssel ein Ländercode und ein Wert eine [Eintragsressourcen](manage-app-submissions.md#listing-object)-Objekt ist, das Eintragsinfos für die App enthält.</span><span class="sxs-lookup"><span data-stu-id="2fccc-178">A dictionary of key and value pairs, where each key is a country code and each value is a [Listing resource](manage-app-submissions.md#listing-object) object that contains listing info for the app.</span></span>       |   
| <span data-ttu-id="2fccc-179">hardwarePreferences</span><span class="sxs-lookup"><span data-stu-id="2fccc-179">hardwarePreferences</span></span>           |  <span data-ttu-id="2fccc-180">array</span><span class="sxs-lookup"><span data-stu-id="2fccc-180">array</span></span>  |   <span data-ttu-id="2fccc-181">Ein Array von Zeichenfolgen, die die [Hardwareeinstellungen](https://msdn.microsoft.com/windows/uwp/publish/enter-app-properties#hardware_preferences) für die App definieren.</span><span class="sxs-lookup"><span data-stu-id="2fccc-181">An array of strings that define the [hardware preferences](https://msdn.microsoft.com/windows/uwp/publish/enter-app-properties#hardware_preferences) for your app.</span></span> <span data-ttu-id="2fccc-182">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="2fccc-182">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="2fccc-183">Touch</span><span class="sxs-lookup"><span data-stu-id="2fccc-183">Touch</span></span></li><li><span data-ttu-id="2fccc-184">Keyboard</span><span class="sxs-lookup"><span data-stu-id="2fccc-184">Keyboard</span></span></li><li><span data-ttu-id="2fccc-185">Mouse</span><span class="sxs-lookup"><span data-stu-id="2fccc-185">Mouse</span></span></li><li><span data-ttu-id="2fccc-186">Camera</span><span class="sxs-lookup"><span data-stu-id="2fccc-186">Camera</span></span></li><li><span data-ttu-id="2fccc-187">NfcHce</span><span class="sxs-lookup"><span data-stu-id="2fccc-187">NfcHce</span></span></li><li><span data-ttu-id="2fccc-188">Nfc</span><span class="sxs-lookup"><span data-stu-id="2fccc-188">Nfc</span></span></li><li><span data-ttu-id="2fccc-189">BluetoothLE</span><span class="sxs-lookup"><span data-stu-id="2fccc-189">BluetoothLE</span></span></li><li><span data-ttu-id="2fccc-190">Telephony</span><span class="sxs-lookup"><span data-stu-id="2fccc-190">Telephony</span></span></li></ul>     |   
| <span data-ttu-id="2fccc-191">automaticBackupEnabled</span><span class="sxs-lookup"><span data-stu-id="2fccc-191">automaticBackupEnabled</span></span>           |  <span data-ttu-id="2fccc-192">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-192">boolean</span></span>  |   <span data-ttu-id="2fccc-193">Gibt an, ob Windows die App-Daten in automatische Sicherungen auf OneDrive aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="2fccc-193">Indicates whether Windows can include your app's data in automatic backups to OneDrive.</span></span> <span data-ttu-id="2fccc-194">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="2fccc-194">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>   |   
| <span data-ttu-id="2fccc-195">canInstallOnRemovableMedia</span><span class="sxs-lookup"><span data-stu-id="2fccc-195">canInstallOnRemovableMedia</span></span>           |  <span data-ttu-id="2fccc-196">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-196">boolean</span></span>  |   <span data-ttu-id="2fccc-197">Gibt an, ob Kunden die App auf Wechselmedien installieren können.</span><span class="sxs-lookup"><span data-stu-id="2fccc-197">Indicates whether customers can install your app to removable storage.</span></span> <span data-ttu-id="2fccc-198">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="2fccc-198">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>     |   
| <span data-ttu-id="2fccc-199">isGameDvrEnabled</span><span class="sxs-lookup"><span data-stu-id="2fccc-199">isGameDvrEnabled</span></span>           |  <span data-ttu-id="2fccc-200">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-200">boolean</span></span> |   <span data-ttu-id="2fccc-201">Gibt an, ob game DVR für die App aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2fccc-201">Indicates whether game DVR is enabled for the app.</span></span>    |   
| <span data-ttu-id="2fccc-202">gamingOptions</span><span class="sxs-lookup"><span data-stu-id="2fccc-202">gamingOptions</span></span>           |  <span data-ttu-id="2fccc-203">Objekt</span><span class="sxs-lookup"><span data-stu-id="2fccc-203">object</span></span> |   <span data-ttu-id="2fccc-204">Ein Array mit einer [Spieloptionenressource](manage-app-submissions.md#gaming-options-object), die spielbezogene Einstellungen für die App definiert.</span><span class="sxs-lookup"><span data-stu-id="2fccc-204">An array that contains one [gaming options resource](manage-app-submissions.md#gaming-options-object) that defines game-related settings for the app.</span></span>     |   
| <span data-ttu-id="2fccc-205">hasExternalInAppProducts</span><span class="sxs-lookup"><span data-stu-id="2fccc-205">hasExternalInAppProducts</span></span>           |     <span data-ttu-id="2fccc-206">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="2fccc-206">boolean</span></span>          |   <span data-ttu-id="2fccc-207">Gibt an, ob die App Benutzern Käufe außerhalb des Microsoft Store-e-Commerce-Systems gestattet.</span><span class="sxs-lookup"><span data-stu-id="2fccc-207">Indicates whether your app allows users to make purchase outside the Microsoft Store commerce system.</span></span> <span data-ttu-id="2fccc-208">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="2fccc-208">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>     |   
| <span data-ttu-id="2fccc-209">meetAccessibilityGuidelines</span><span class="sxs-lookup"><span data-stu-id="2fccc-209">meetAccessibilityGuidelines</span></span>           |    <span data-ttu-id="2fccc-210">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-210">boolean</span></span>           |  <span data-ttu-id="2fccc-211">Gibt an, ob getestet wurde, ob die App die Richtlinien zur Barrierefreiheit erfüllt.</span><span class="sxs-lookup"><span data-stu-id="2fccc-211">Indicates whether your app has been tested to meet accessibility guidelines.</span></span> <span data-ttu-id="2fccc-212">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="2fccc-212">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>      |   
| <span data-ttu-id="2fccc-213">notesForCertification</span><span class="sxs-lookup"><span data-stu-id="2fccc-213">notesForCertification</span></span>           |  <span data-ttu-id="2fccc-214">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-214">string</span></span>  |   <span data-ttu-id="2fccc-215">Enthält [Hinweise zur Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification) für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="2fccc-215">Contains [notes for certification](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification) for your app.</span></span>    |    
| <span data-ttu-id="2fccc-216">applicationPackages</span><span class="sxs-lookup"><span data-stu-id="2fccc-216">applicationPackages</span></span>           |   <span data-ttu-id="2fccc-217">array</span><span class="sxs-lookup"><span data-stu-id="2fccc-217">array</span></span>  | <span data-ttu-id="2fccc-218">Enthält Objekte, die Details über die einzelnen Pakete der Übermittlung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2fccc-218">Contains objects that provide details about each package in the submission.</span></span> <span data-ttu-id="2fccc-219">Weitere Informationen finden Sie unten im Abschnitt [Anwendungspaket](manage-app-submissions.md#application-package-object).</span><span class="sxs-lookup"><span data-stu-id="2fccc-219">For more information, see the [Application package](manage-app-submissions.md#application-package-object) section.</span></span> <span data-ttu-id="2fccc-220">Beim Aufruf dieser Methode zur Aktualisierung einer App-Übermittlung sind im Antworttext nur die *fileName*-, *fileStatus*-, *minimumDirectXVersion*- und *minimumSystemRam*-Werte dieser Objekte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fccc-220">When calling this method to update an app submission, only the *fileName*, *fileStatus*, *minimumDirectXVersion*, and *minimumSystemRam* values of these objects are required in the request body.</span></span> <span data-ttu-id="2fccc-221">Die anderen Werte werden von Partner Center aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="2fccc-221">The other values are populated by Partner Center.</span></span>   |    
| <span data-ttu-id="2fccc-222">packageDeliveryOptions</span><span class="sxs-lookup"><span data-stu-id="2fccc-222">packageDeliveryOptions</span></span>    | <span data-ttu-id="2fccc-223">object</span><span class="sxs-lookup"><span data-stu-id="2fccc-223">object</span></span>  | <span data-ttu-id="2fccc-224">Enthält den schrittweisen Paketrollout sowie erforderliche Einstellungen für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="2fccc-224">Contains gradual package rollout and mandatory update settings for the submission.</span></span> <span data-ttu-id="2fccc-225">Weitere Informationen finden Sie unter [options-Objekt für die Paketübermittlung](manage-app-submissions.md#package-delivery-options-object).</span><span class="sxs-lookup"><span data-stu-id="2fccc-225">For more information, see [Package delivery options object](manage-app-submissions.md#package-delivery-options-object).</span></span>  |
| <span data-ttu-id="2fccc-226">enterpriseLicensing</span><span class="sxs-lookup"><span data-stu-id="2fccc-226">enterpriseLicensing</span></span>           |  <span data-ttu-id="2fccc-227">string</span><span class="sxs-lookup"><span data-stu-id="2fccc-227">string</span></span>  |  <span data-ttu-id="2fccc-228">Einer der [Werte für Enterprise-Lizenzierung](manage-app-submissions.md#enterprise-licensing), die das Verhalten der Enterprise-Lizenzierung für die App angeben.</span><span class="sxs-lookup"><span data-stu-id="2fccc-228">One of the [enterprise licensing values](manage-app-submissions.md#enterprise-licensing) values that indicate the enterprise licensing behavior for the app.</span></span>  |    
| <span data-ttu-id="2fccc-229">allowMicrosftDecideAppAvailabilityToFutureDeviceFamilies</span><span class="sxs-lookup"><span data-stu-id="2fccc-229">allowMicrosftDecideAppAvailabilityToFutureDeviceFamilies</span></span>           |  <span data-ttu-id="2fccc-230">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-230">boolean</span></span>   |  <span data-ttu-id="2fccc-231">Gibt an, ob Microsoft [die App für zukünftige Windows10-Gerätefamilien verfügbar machen](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families) darf.</span><span class="sxs-lookup"><span data-stu-id="2fccc-231">Indicates whether Microsoft is allowed to [make the app available to future Windows 10 device families](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families).</span></span>    |    
| <span data-ttu-id="2fccc-232">allowTargetFutureDeviceFamilies</span><span class="sxs-lookup"><span data-stu-id="2fccc-232">allowTargetFutureDeviceFamilies</span></span>           | <span data-ttu-id="2fccc-233">boolean</span><span class="sxs-lookup"><span data-stu-id="2fccc-233">boolean</span></span>   |  <span data-ttu-id="2fccc-234">Gibt an, ob die App [auf zukünftige Windows10-Gerätefamilien abzielen](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families) darf.</span><span class="sxs-lookup"><span data-stu-id="2fccc-234">Indicates whether your app is allowed to [target future Windows 10 device families](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families).</span></span>     |   
| <span data-ttu-id="2fccc-235">trailers</span><span class="sxs-lookup"><span data-stu-id="2fccc-235">trailers</span></span>           |  <span data-ttu-id="2fccc-236">Array</span><span class="sxs-lookup"><span data-stu-id="2fccc-236">array</span></span> |   <span data-ttu-id="2fccc-237">Ein Array mit [Trailerressourcen](manage-app-submissions.md#trailer-object), die Videotrailer für den App-Eintrag darstellen.</span><span class="sxs-lookup"><span data-stu-id="2fccc-237">An array that contains up to [trailer resources](manage-app-submissions.md#trailer-object) that represent video trailers for the app listing.</span></span>   |   


### <a name="request-example"></a><span data-ttu-id="2fccc-238">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="2fccc-238">Request example</span></span>

<span data-ttu-id="2fccc-239">Im folgenden Beispiel wird die Aktualisierung einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="2fccc-239">The following example demonstrates how to update an app submission.</span></span>

```json
PUT https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621230023 HTTP/1.1
Authorization: Bearer <your access token>
Content-Type: application/json
{
  "applicationCategory": "BooksAndReference_EReader",
  "pricing": {
    "trialPeriod": "FifteenDays",
    "marketSpecificPricings": {},
    "sales": [],
    "priceId": "Tier2"
  },
  "visibility": "Public",
  "targetPublishMode": "Manual",
  "targetPublishDate": "1601-01-01T00:00:00Z",
  "listings": {
    "en-us": {
      "baseListing": {
        "copyrightAndTrademarkInfo": "",
        "keywords": [
              "epub"
            ],
        "licenseTerms": "",
        "privacyPolicy": "",
        "supportContact": "",
        "websiteUrl": "",
        "description": "Description",
        "features": [
              "Free ebook reader"
            ],
        "releaseNotes": "",
        "images": [
          {
            "fileName": "contoso.png",
            "fileStatus": "Uploaded",
            "id": "1152921504672272757",
            "imageType": "Screenshot"
          }
        ],
        "recommendedHardware": [],
        "title": "Contoso ebook reader"
      },
      "platformOverrides": {
        "Windows81": {
          "description": "Ebook reader for Windows 8.1"
        }
      }
    }
  },
  "hardwarePreferences": [
    "Touch"
  ],
  "automaticBackupEnabled": false,
  "canInstallOnRemovableMedia": true,
  "isGameDvrEnabled": false,
  "gamingOptions": [],
  "hasExternalInAppProducts": false,
  "meetAccessibilityGuidelines": true,
  "notesForCertification": "",
  "applicationPackages": [
    {
      "fileName": "contoso_app.appx",
      "fileStatus": "PendingUpload",
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None"
    }
  ],
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
  "enterpriseLicensing": "Online",
  "allowMicrosoftDecideAppAvailabilityToFutureDeviceFamilies": true,
  "allowTargetFutureDeviceFamilies": {
    "Desktop": false,
    "Mobile": true,
    "Holographic": true,
    "Xbox": false,
    "Team": true
  },
  "trailers": []
}
```

## <a name="response"></a><span data-ttu-id="2fccc-240">Antwort</span><span class="sxs-lookup"><span data-stu-id="2fccc-240">Response</span></span>

<span data-ttu-id="2fccc-241">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="2fccc-241">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="2fccc-242">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="2fccc-242">The response body contains information about the updated submission.</span></span> <span data-ttu-id="2fccc-243">Weitere Informationen zu den Werten im Antworttext finden Sie unter [App-Übermittlungsressource](manage-app-submissions.md#app-submission-object).</span><span class="sxs-lookup"><span data-stu-id="2fccc-243">For more details about the values in the response body, see [App submission resource](manage-app-submissions.md#app-submission-object).</span></span>

```json
{
  "id": "1152921504621243540",
  "applicationCategory": "BooksAndReference_EReader",
  "pricing": {
    "trialPeriod": "FifteenDays",
    "marketSpecificPricings": {},
    "sales": [],
    "priceId": "Tier2"
  },
  "visibility": "Public",
  "targetPublishMode": "Manual",
  "targetPublishDate": "1601-01-01T00:00:00Z",
  "listings": {
    "en-us": {
      "baseListing": {
        "copyrightAndTrademarkInfo": "",
        "keywords": [
           "epub"
        ],
        "licenseTerms": "",
        "privacyPolicy": "",
        "supportContact": "",
        "websiteUrl": "",
        "description": "Description",
        "features": [
          "Free ebook reader"
        ],
        "releaseNotes": "",
        "images": [
          {
            "fileName": "contoso.png",
            "fileStatus": "Uploaded",
            "id": "1152921504672272757",
            "imageType": "Screenshot"
          }
        ],
        "recommendedHardware": [],
        "title": "Contoso ebook reader"
      },
      "platformOverrides": {
        "Windows81": {
          "description": "Ebook reader for Windows 8.1",
        }
      }
    }
  },
  "hardwarePreferences": [
    "Touch"
  ],
  "automaticBackupEnabled": false,
  "canInstallOnRemovableMedia": true,
  "isGameDvrEnabled": false,
  "gamingOptions": [],
  "hasExternalInAppProducts": false,
  "meetAccessibilityGuidelines": true,
  "notesForCertification": "",
  "status": "PendingCommit",
  "statusDetails": {
    "errors": [],
    "warnings": [],
    "certificationReports": []
  },
  "fileUploadUrl": "https://productingestionbin1.blob.core.windows.net/ingestion/387a9ea8-a412-43a9-8fb3-a38d03eb483d?sv=2014-02-14&sr=b&sig=sdd12JmoaT6BhvC%2BZUrwRweA%2Fkvj%2BEBCY09C2SZZowg%3D&se=2016-06-17T18:32:26Z&sp=rwl",
  "applicationPackages": [
    {
      "fileName": "contoso_app.appx",
      "fileStatus": "PendingUpload",
      "id": "1152921504620138797",
      "version": "1.0.0.0",
      "architecture": "ARM",
      "languages": [
        "en-US"
      ],
      "capabilities": [
        "ID_RESOLUTION_HD720P",
        "ID_RESOLUTION_WVGA",
        "ID_RESOLUTION_WXGA"
      ],
      "minimumDirectXVersion": "None",
      "minimumSystemRam": "None",
      "targetDeviceFamilies": [
        "Windows.Mobile min version 10.0.10240.0"
      ]
    }
  ],
  "packageDeliveryOptions": {
    "packageRollout": {
        "isPackageRollout": false,
        "packageRolloutPercentage": 0.0,
        "packageRolloutStatus": "PackageRolloutNotStarted",
        "fallbackSubmissionId": "0"
    },
    "isMandatoryUpdate": false,
    "mandatoryUpdateEffectiveDate": "1601-01-01T00:00:00.0000000Z"
  },
  "enterpriseLicensing": "Online",
  "allowMicrosoftDecideAppAvailabilityToFutureDeviceFamilies": true,
  "allowTargetFutureDeviceFamilies": {
    "Desktop": false,
    "Mobile": true,
    "Holographic": true,
    "Xbox": false,
    "Team": true
  },
  "friendlyName": "Submission 2",
  "trailers": []
}
```

## <a name="error-codes"></a><span data-ttu-id="2fccc-244">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="2fccc-244">Error codes</span></span>

<span data-ttu-id="2fccc-245">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="2fccc-245">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="2fccc-246">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="2fccc-246">Error code</span></span> |  <span data-ttu-id="2fccc-247">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2fccc-247">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="2fccc-248">400</span><span class="sxs-lookup"><span data-stu-id="2fccc-248">400</span></span>  | <span data-ttu-id="2fccc-249">Die Übermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="2fccc-249">The submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="2fccc-250">409</span><span class="sxs-lookup"><span data-stu-id="2fccc-250">409</span></span>  | <span data-ttu-id="2fccc-251">Die Übermittlung konnte im aktuellen Zustand der app nicht aktualisiert werden, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</span><span class="sxs-lookup"><span data-stu-id="2fccc-251">The submission could not be updated because of the current state of the app, or the app uses a Partner Center feature that is [currently not supported by the Microsoft Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   


## <a name="related-topics"></a><span data-ttu-id="2fccc-252">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2fccc-252">Related topics</span></span>

* [<span data-ttu-id="2fccc-253">Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="2fccc-253">Create and manage submissions using Microsoft Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="2fccc-254">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-254">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="2fccc-255">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-255">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="2fccc-256">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-256">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="2fccc-257">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-257">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="2fccc-258">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="2fccc-258">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
