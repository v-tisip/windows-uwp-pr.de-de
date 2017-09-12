---
author: mcleanbyron
ms.assetid: E8751EBF-AE0F-4107-80A1-23C186453B1C
description: "Verwenden Sie diese Methode aus der Windows Store-Übermittlungs-Api zur Aktualisierung einer vorhandenen App-Übermittlung."
title: "Aktualisieren einer App-Übermittlung"
ms.author: mcleans
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlung-API, App-Übermittlung, Aktualisieren"
ms.openlocfilehash: b3c071c0d4f070c1a0ac95d6f35c73fcbb4e0455
ms.sourcegitcommit: a7a1b41c7dce6d56250ce3113137391d65d9e401
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2017
---
# <a name="update-an-app-submission"></a><span data-ttu-id="996a0-104">Aktualisieren einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-104">Update an app submission</span></span>

<span data-ttu-id="996a0-105">Verwenden Sie diese Methode aus der Windows Store-Übermittlungs-Api zur Aktualisierung einer vorhandenen App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="996a0-105">Use this method in the Windows Store submission API to update an existing app submission.</span></span> <span data-ttu-id="996a0-106">Nachdem Sie mit dieser Methode eine Übermittlung erfolgreich aktualisiert haben, müssen Sie ein [Commit für die Übermittlung](commit-an-app-submission.md) für Aufnahme und Veröffentlichung durchführen.</span><span class="sxs-lookup"><span data-stu-id="996a0-106">After you successfully update a submission by using this method, you must [commit the submission](commit-an-app-submission.md) for ingestion and publishing.</span></span>

<span data-ttu-id="996a0-107">Weitere Informationen dazu, wie diese Methode zum Erstellen einer App-Übermittlung mithilfe der Windows Store-Übermittlungs-API passt, finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).</span><span class="sxs-lookup"><span data-stu-id="996a0-107">For more information about how this method fits into the process of creating an app submission by using the Windows Store submission API, see [Manage app submissions](manage-app-submissions.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="996a0-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="996a0-108">Prerequisites</span></span>

<span data-ttu-id="996a0-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="996a0-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="996a0-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API.</span><span class="sxs-lookup"><span data-stu-id="996a0-110">If you have not done so already, complete all the [prerequisites](create-and-manage-submissions-using-windows-store-services.md#prerequisites) for the Windows Store submission API.</span></span>
* <span data-ttu-id="996a0-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="996a0-111">[Obtain an Azure AD access token](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="996a0-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="996a0-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="996a0-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="996a0-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="996a0-114">Erstellen Sie Übermittlung für eine App im Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="996a0-114">Create a submission for an app in your Dev Center account.</span></span> <span data-ttu-id="996a0-115">Sie können dies im Dev Center-Dashboard oder durch Verwenden der Methode [Erstellen einer App-Übermittlung](create-an-app-submission.md) erreichen.</span><span class="sxs-lookup"><span data-stu-id="996a0-115">You can do this in the Dev Center dashboard, or you can do this by using the [create an app submission](create-an-app-submission.md) method.</span></span>

## <a name="request"></a><span data-ttu-id="996a0-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="996a0-116">Request</span></span>

<span data-ttu-id="996a0-117">Diese Methode hat die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="996a0-117">This method has the following syntax.</span></span> <span data-ttu-id="996a0-118">In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Header und Anforderungstexts.</span><span class="sxs-lookup"><span data-stu-id="996a0-118">See the following sections for usage examples and descriptions of the header and request body.</span></span>

| <span data-ttu-id="996a0-119">Methode</span><span class="sxs-lookup"><span data-stu-id="996a0-119">Method</span></span> | <span data-ttu-id="996a0-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="996a0-120">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="996a0-121">PUT</span><span class="sxs-lookup"><span data-stu-id="996a0-121">PUT</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}  ``` |

<span/>
 

### <a name="request-header"></a><span data-ttu-id="996a0-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="996a0-122">Request header</span></span>

| <span data-ttu-id="996a0-123">Header</span><span class="sxs-lookup"><span data-stu-id="996a0-123">Header</span></span>        | <span data-ttu-id="996a0-124">Typ</span><span class="sxs-lookup"><span data-stu-id="996a0-124">Type</span></span>   | <span data-ttu-id="996a0-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="996a0-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="996a0-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="996a0-126">Authorization</span></span> | <span data-ttu-id="996a0-127">String</span><span class="sxs-lookup"><span data-stu-id="996a0-127">string</span></span> | <span data-ttu-id="996a0-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="996a0-128">Required.</span></span> <span data-ttu-id="996a0-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="996a0-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/>

### <a name="request-parameters"></a><span data-ttu-id="996a0-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="996a0-130">Request parameters</span></span>

| <span data-ttu-id="996a0-131">Name</span><span class="sxs-lookup"><span data-stu-id="996a0-131">Name</span></span>        | <span data-ttu-id="996a0-132">Typ</span><span class="sxs-lookup"><span data-stu-id="996a0-132">Type</span></span>   | <span data-ttu-id="996a0-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="996a0-133">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="996a0-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="996a0-134">applicationId</span></span> | <span data-ttu-id="996a0-135">String</span><span class="sxs-lookup"><span data-stu-id="996a0-135">string</span></span> | <span data-ttu-id="996a0-136">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="996a0-136">Required.</span></span> <span data-ttu-id="996a0-137">Die Store-ID der App, für die Sie eine Übermittlung aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="996a0-137">The Store ID of the app for which you want to update a submission.</span></span> <span data-ttu-id="996a0-138">Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span><span class="sxs-lookup"><span data-stu-id="996a0-138">For more information about the Store ID, see [View app identity details](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</span></span>  |
| <span data-ttu-id="996a0-139">submissionId</span><span class="sxs-lookup"><span data-stu-id="996a0-139">submissionId</span></span> | <span data-ttu-id="996a0-140">String</span><span class="sxs-lookup"><span data-stu-id="996a0-140">string</span></span> | <span data-ttu-id="996a0-141">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="996a0-141">Required.</span></span> <span data-ttu-id="996a0-142">Die ID der zu aktualisierenden Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="996a0-142">The ID of the submission to update.</span></span> <span data-ttu-id="996a0-143">Diese ID ist im Dev Center-Dashboard verfügbar und in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) enthalten.</span><span class="sxs-lookup"><span data-stu-id="996a0-143">This ID is available in the Dev Center dashboard, and it is included in the response data for requests to [create an app submission](create-an-app-submission.md).</span></span>  |

<span/>

### <a name="request-body"></a><span data-ttu-id="996a0-144">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="996a0-144">Request body</span></span>

<span data-ttu-id="996a0-145">Der Anforderungstext hat folgende Parameter.</span><span class="sxs-lookup"><span data-stu-id="996a0-145">The request body has the following parameters.</span></span>

| <span data-ttu-id="996a0-146">Wert</span><span class="sxs-lookup"><span data-stu-id="996a0-146">Value</span></span>      | <span data-ttu-id="996a0-147">Typ</span><span class="sxs-lookup"><span data-stu-id="996a0-147">Type</span></span>   | <span data-ttu-id="996a0-148">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="996a0-148">Description</span></span>                                                                                                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="996a0-149">applicationCategory</span><span class="sxs-lookup"><span data-stu-id="996a0-149">applicationCategory</span></span>           | <span data-ttu-id="996a0-150">string</span><span class="sxs-lookup"><span data-stu-id="996a0-150">string</span></span>  |   <span data-ttu-id="996a0-151">Eine Zeichenfolge, die [Kategorie und/oder Unterkategorie](https://msdn.microsoft.com/windows/uwp/publish/category-and-subcategory-table) für Ihre App angibt.</span><span class="sxs-lookup"><span data-stu-id="996a0-151">A string that specifies the [category and/or subcategory](https://msdn.microsoft.com/windows/uwp/publish/category-and-subcategory-table) for your app.</span></span> <span data-ttu-id="996a0-152">Kategorien und Unterkategorien werden mit einem Unterstrich "_" zu einer einzigen Zeichenfolge zusammengefasst, z.B. **BooksAndReference_EReader**.</span><span class="sxs-lookup"><span data-stu-id="996a0-152">Categories and subcategories are combined into a single string with the underscore '_' character, such as **BooksAndReference_EReader**.</span></span>      |  
| <span data-ttu-id="996a0-153">pricing</span><span class="sxs-lookup"><span data-stu-id="996a0-153">pricing</span></span>           |  <span data-ttu-id="996a0-154">object</span><span class="sxs-lookup"><span data-stu-id="996a0-154">object</span></span>  | <span data-ttu-id="996a0-155">Ein Objekt, das Preisinfos für die App enthält.</span><span class="sxs-lookup"><span data-stu-id="996a0-155">An object that contains pricing info for the app.</span></span> <span data-ttu-id="996a0-156">Weitere Informationen finden Sie im Abschnitt [Preisressource](manage-app-submissions.md#pricing-object).</span><span class="sxs-lookup"><span data-stu-id="996a0-156">For more information, see the [Pricing resource](manage-app-submissions.md#pricing-object) section.</span></span>       |   
| <span data-ttu-id="996a0-157">visibility</span><span class="sxs-lookup"><span data-stu-id="996a0-157">visibility</span></span>           |  <span data-ttu-id="996a0-158">string</span><span class="sxs-lookup"><span data-stu-id="996a0-158">string</span></span>  |  <span data-ttu-id="996a0-159">Die Sichtbarkeit der App.</span><span class="sxs-lookup"><span data-stu-id="996a0-159">The visibility of the app.</span></span> <span data-ttu-id="996a0-160">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="996a0-160">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="996a0-161">Hidden</span><span class="sxs-lookup"><span data-stu-id="996a0-161">Hidden</span></span></li><li><span data-ttu-id="996a0-162">Public</span><span class="sxs-lookup"><span data-stu-id="996a0-162">Public</span></span></li><li><span data-ttu-id="996a0-163">Private</span><span class="sxs-lookup"><span data-stu-id="996a0-163">Private</span></span></li><li><span data-ttu-id="996a0-164">NotSet</span><span class="sxs-lookup"><span data-stu-id="996a0-164">NotSet</span></span></li></ul>       |   
| <span data-ttu-id="996a0-165">targetPublishMode</span><span class="sxs-lookup"><span data-stu-id="996a0-165">targetPublishMode</span></span>           | <span data-ttu-id="996a0-166">string</span><span class="sxs-lookup"><span data-stu-id="996a0-166">string</span></span>  | <span data-ttu-id="996a0-167">Der Publish-Modus für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="996a0-167">The publish mode for the submission.</span></span> <span data-ttu-id="996a0-168">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="996a0-168">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="996a0-169">Immediate</span><span class="sxs-lookup"><span data-stu-id="996a0-169">Immediate</span></span></li><li><span data-ttu-id="996a0-170">Manual</span><span class="sxs-lookup"><span data-stu-id="996a0-170">Manual</span></span></li><li><span data-ttu-id="996a0-171">SpecificDate</span><span class="sxs-lookup"><span data-stu-id="996a0-171">SpecificDate</span></span></li></ul> |
| <span data-ttu-id="996a0-172">targetPublishDate</span><span class="sxs-lookup"><span data-stu-id="996a0-172">targetPublishDate</span></span>           | <span data-ttu-id="996a0-173">string</span><span class="sxs-lookup"><span data-stu-id="996a0-173">string</span></span>  | <span data-ttu-id="996a0-174">Das Veröffentlichungsdatum der Übermittlung im ISO 8601-Format, wenn *TargetPublishMode* den Wert SpecificDate hat.</span><span class="sxs-lookup"><span data-stu-id="996a0-174">The publish date for the submission in ISO 8601 format, if the *targetPublishMode* is set to SpecificDate.</span></span>  |  
| <span data-ttu-id="996a0-175">listings</span><span class="sxs-lookup"><span data-stu-id="996a0-175">listings</span></span>           |   <span data-ttu-id="996a0-176">object</span><span class="sxs-lookup"><span data-stu-id="996a0-176">object</span></span>  |  <span data-ttu-id="996a0-177">Ein Wörterbuch von Schlüssel-Wert-Paaren, wobei ein Schlüssel ein Ländercode und ein Wert eine [Eintragsressourcen](manage-app-submissions.md#listing-object)-Objekt ist, das Eintragsinfos für die App enthält.</span><span class="sxs-lookup"><span data-stu-id="996a0-177">A dictionary of key and value pairs, where each key is a country code and each value is a [Listing resource](manage-app-submissions.md#listing-object) object that contains listing info for the app.</span></span>       |   
| <span data-ttu-id="996a0-178">hardwarePreferences</span><span class="sxs-lookup"><span data-stu-id="996a0-178">hardwarePreferences</span></span>           |  <span data-ttu-id="996a0-179">array</span><span class="sxs-lookup"><span data-stu-id="996a0-179">array</span></span>  |   <span data-ttu-id="996a0-180">Ein Array von Zeichenfolgen, die die [Hardwareeinstellungen](https://msdn.microsoft.com/windows/uwp/publish/enter-app-properties#hardware_preferences) für die App definieren.</span><span class="sxs-lookup"><span data-stu-id="996a0-180">An array of strings that define the [hardware preferences](https://msdn.microsoft.com/windows/uwp/publish/enter-app-properties#hardware_preferences) for your app.</span></span> <span data-ttu-id="996a0-181">Folgende Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="996a0-181">This can be one of the following values:</span></span> <ul><li><span data-ttu-id="996a0-182">Touch</span><span class="sxs-lookup"><span data-stu-id="996a0-182">Touch</span></span></li><li><span data-ttu-id="996a0-183">Keyboard</span><span class="sxs-lookup"><span data-stu-id="996a0-183">Keyboard</span></span></li><li><span data-ttu-id="996a0-184">Mouse</span><span class="sxs-lookup"><span data-stu-id="996a0-184">Mouse</span></span></li><li><span data-ttu-id="996a0-185">Camera</span><span class="sxs-lookup"><span data-stu-id="996a0-185">Camera</span></span></li><li><span data-ttu-id="996a0-186">NfcHce</span><span class="sxs-lookup"><span data-stu-id="996a0-186">NfcHce</span></span></li><li><span data-ttu-id="996a0-187">Nfc</span><span class="sxs-lookup"><span data-stu-id="996a0-187">Nfc</span></span></li><li><span data-ttu-id="996a0-188">BluetoothLE</span><span class="sxs-lookup"><span data-stu-id="996a0-188">BluetoothLE</span></span></li><li><span data-ttu-id="996a0-189">Telephony</span><span class="sxs-lookup"><span data-stu-id="996a0-189">Telephony</span></span></li></ul>     |   
| <span data-ttu-id="996a0-190">automaticBackupEnabled</span><span class="sxs-lookup"><span data-stu-id="996a0-190">automaticBackupEnabled</span></span>           |  <span data-ttu-id="996a0-191">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-191">boolean</span></span>  |   <span data-ttu-id="996a0-192">Gibt an, ob Windows die App-Daten in automatische Sicherungen auf OneDrive aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="996a0-192">Indicates whether Windows can include your app's data in automatic backups to OneDrive.</span></span> <span data-ttu-id="996a0-193">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="996a0-193">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>   |   
| <span data-ttu-id="996a0-194">canInstallOnRemovableMedia</span><span class="sxs-lookup"><span data-stu-id="996a0-194">canInstallOnRemovableMedia</span></span>           |  <span data-ttu-id="996a0-195">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-195">boolean</span></span>  |   <span data-ttu-id="996a0-196">Gibt an, ob Kunden die App auf Wechselmedien installieren können.</span><span class="sxs-lookup"><span data-stu-id="996a0-196">Indicates whether customers can install your app to removable storage.</span></span> <span data-ttu-id="996a0-197">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="996a0-197">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>     |   
| <span data-ttu-id="996a0-198">isGameDvrEnabled</span><span class="sxs-lookup"><span data-stu-id="996a0-198">isGameDvrEnabled</span></span>           |  <span data-ttu-id="996a0-199">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-199">boolean</span></span> |   <span data-ttu-id="996a0-200">Gibt an, ob game DVR für die App aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="996a0-200">Indicates whether game DVR is enabled for the app.</span></span>    |   
| <span data-ttu-id="996a0-201">gamingOptions</span><span class="sxs-lookup"><span data-stu-id="996a0-201">gamingOptions</span></span>           |  <span data-ttu-id="996a0-202">Objekt</span><span class="sxs-lookup"><span data-stu-id="996a0-202">object</span></span> |   <span data-ttu-id="996a0-203">Ein Array mit genau einer [Spieloptionenressource](manage-app-submissions.md#gaming-options-object), die spielbezogene Einstellungen für die App definiert.</span><span class="sxs-lookup"><span data-stu-id="996a0-203">An array that contains one [gaming options resource](manage-app-submissions.md#gaming-options-object) that defines game-related settings for the app.</span></span><br/><br/><span data-ttu-id="996a0-204">**Hinweis:**&nbsp;&nbsp;Die Möglichkeit zum Konfigurieren von Gaming-Optionen mit dieser API ist zurzeit nicht für alle Entwicklerkonten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="996a0-204">**Note:**&nbsp;&nbsp;The ability to configure gaming options using this API is currently not available to all developer accounts.</span></span> <span data-ttu-id="996a0-205">Wenn Ihr Konto keinen Zugriff auf diese Ressource hat, ist der *gamingOptions* Wert Null.</span><span class="sxs-lookup"><span data-stu-id="996a0-205">If your account does not have access to this resource, the *gamingOptions* value is null.</span></span>     |   
| <span data-ttu-id="996a0-206">hasExternalInAppProducts</span><span class="sxs-lookup"><span data-stu-id="996a0-206">hasExternalInAppProducts</span></span>           |     <span data-ttu-id="996a0-207">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-207">boolean</span></span>          |   <span data-ttu-id="996a0-208">Gibt an, ob die App Benutzern Käufe außerhalb der Windows Store-e-Commerce-Systems gestattet.</span><span class="sxs-lookup"><span data-stu-id="996a0-208">Indicates whether your app allows users to make purchase outside the Windows Store commerce system.</span></span> <span data-ttu-id="996a0-209">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="996a0-209">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>     |   
| <span data-ttu-id="996a0-210">meetAccessibilityGuidelines</span><span class="sxs-lookup"><span data-stu-id="996a0-210">meetAccessibilityGuidelines</span></span>           |    <span data-ttu-id="996a0-211">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-211">boolean</span></span>           |  <span data-ttu-id="996a0-212">Gibt an, ob getestet wurde, ob die App die Richtlinien zur Barrierefreiheit erfüllt.</span><span class="sxs-lookup"><span data-stu-id="996a0-212">Indicates whether your app has been tested to meet accessibility guidelines.</span></span> <span data-ttu-id="996a0-213">Weitere Informationen finden Sie unter [App-Deklarationen](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span><span class="sxs-lookup"><span data-stu-id="996a0-213">For more information, see [App declarations](https://msdn.microsoft.com/windows/uwp/publish/app-declarations).</span></span>      |   
| <span data-ttu-id="996a0-214">notesForCertification</span><span class="sxs-lookup"><span data-stu-id="996a0-214">notesForCertification</span></span>           |  <span data-ttu-id="996a0-215">string</span><span class="sxs-lookup"><span data-stu-id="996a0-215">string</span></span>  |   <span data-ttu-id="996a0-216">Enthält [Hinweise zur Zertifizierung](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification) für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="996a0-216">Contains [notes for certification](https://msdn.microsoft.com/windows/uwp/publish/notes-for-certification) for your app.</span></span>    |    
| <span data-ttu-id="996a0-217">applicationPackages</span><span class="sxs-lookup"><span data-stu-id="996a0-217">applicationPackages</span></span>           |   <span data-ttu-id="996a0-218">array</span><span class="sxs-lookup"><span data-stu-id="996a0-218">array</span></span>  | <span data-ttu-id="996a0-219">Enthält Objekte, die Details über die einzelnen Pakete der Übermittlung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="996a0-219">Contains objects that provide details about each package in the submission.</span></span> <span data-ttu-id="996a0-220">Weitere Informationen finden Sie unten im Abschnitt [Anwendungspaket](manage-app-submissions.md#application-package-object).</span><span class="sxs-lookup"><span data-stu-id="996a0-220">For more information, see the [Application package](manage-app-submissions.md#application-package-object) section.</span></span> <span data-ttu-id="996a0-221">Beim Aufruf dieser Methode zur Aktualisierung einer App-Übermittlung sind im Antworttext nur die *fileName*-, *fileStatus*-, *minimumDirectXVersion*- und *minimumSystemRam*-Werte dieser Objekte erforderlich.</span><span class="sxs-lookup"><span data-stu-id="996a0-221">When calling this method to update an app submission, only the *fileName*, *fileStatus*, *minimumDirectXVersion*, and *minimumSystemRam* values of these objects are required in the request body.</span></span> <span data-ttu-id="996a0-222">Die übrigen Werte werden von Dev Center aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="996a0-222">The other values are populated by Dev Center.</span></span>   |    
| <span data-ttu-id="996a0-223">packageDeliveryOptions</span><span class="sxs-lookup"><span data-stu-id="996a0-223">packageDeliveryOptions</span></span>    | <span data-ttu-id="996a0-224">object</span><span class="sxs-lookup"><span data-stu-id="996a0-224">object</span></span>  | <span data-ttu-id="996a0-225">Enthält den schrittweisen Paketrollout sowie erforderliche Einstellungen für die Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="996a0-225">Contains gradual package rollout and mandatory update settings for the submission.</span></span> <span data-ttu-id="996a0-226">Weitere Informationen finden Sie unter [options-Objekt für die Paketübermittlung](manage-app-submissions.md#package-delivery-options-object).</span><span class="sxs-lookup"><span data-stu-id="996a0-226">For more information, see [Package delivery options object](manage-app-submissions.md#package-delivery-options-object).</span></span>  |
| <span data-ttu-id="996a0-227">enterpriseLicensing</span><span class="sxs-lookup"><span data-stu-id="996a0-227">enterpriseLicensing</span></span>           |  <span data-ttu-id="996a0-228">string</span><span class="sxs-lookup"><span data-stu-id="996a0-228">string</span></span>  |  <span data-ttu-id="996a0-229">Einer der [Werte für Enterprise-Lizenzierung](manage-app-submissions.md#enterprise-licensing), die das Verhalten der Enterprise-Lizenzierung für die App angeben.</span><span class="sxs-lookup"><span data-stu-id="996a0-229">One of the [enterprise licensing values](manage-app-submissions.md#enterprise-licensing) values that indicate the enterprise licensing behavior for the app.</span></span>  |    
| <span data-ttu-id="996a0-230">allowMicrosftDecideAppAvailabilityToFutureDeviceFamilies</span><span class="sxs-lookup"><span data-stu-id="996a0-230">allowMicrosftDecideAppAvailabilityToFutureDeviceFamilies</span></span>           |  <span data-ttu-id="996a0-231">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-231">boolean</span></span>   |  <span data-ttu-id="996a0-232">Gibt an, ob Microsoft [die App für zukünftige Windows10-Gerätefamilien verfügbar machen](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families) darf.</span><span class="sxs-lookup"><span data-stu-id="996a0-232">Indicates whether Microsoft is allowed to [make the app available to future Windows 10 device families](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families).</span></span>    |    
| <span data-ttu-id="996a0-233">allowTargetFutureDeviceFamilies</span><span class="sxs-lookup"><span data-stu-id="996a0-233">allowTargetFutureDeviceFamilies</span></span>           | <span data-ttu-id="996a0-234">boolean</span><span class="sxs-lookup"><span data-stu-id="996a0-234">boolean</span></span>   |  <span data-ttu-id="996a0-235">Gibt an, ob die App [auf zukünftige Windows10-Gerätefamilien abzielen](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families) darf.</span><span class="sxs-lookup"><span data-stu-id="996a0-235">Indicates whether your app is allowed to [target future Windows 10 device families](https://msdn.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#windows-10-device-families).</span></span>     |   
| <span data-ttu-id="996a0-236">trailers</span><span class="sxs-lookup"><span data-stu-id="996a0-236">trailers</span></span>           |  <span data-ttu-id="996a0-237">Array</span><span class="sxs-lookup"><span data-stu-id="996a0-237">array</span></span> |   <span data-ttu-id="996a0-238">Ein Array mit [Trailerressourcen](manage-app-submissions.md#trailer-object), die Videotrailer für den App-Eintrag darstellen.</span><span class="sxs-lookup"><span data-stu-id="996a0-238">An array that contains up to [trailer resources](manage-app-submissions.md#trailer-object) that represent video trailers for the app listing.</span></span> <br/><br/><span data-ttu-id="996a0-239">**Hinweis:**&nbsp;&nbsp;Die Möglichkeit einen Trailer zu übermitteln mit dieser API ist derzeit nicht für alle Entwicklerkonten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="996a0-239">**Note:**&nbsp;&nbsp;The ability to submit a trailer for your app submission using this API is currently not available to all developer accounts.</span></span> <span data-ttu-id="996a0-240">Wenn Ihr Konto keinen Zugriff auf diese Ressource hat, ist der *trailers* Wert Null.</span><span class="sxs-lookup"><span data-stu-id="996a0-240">If your account does not have access to this resource, the *trailers* value is null.</span></span>  |   

<span/>

### <a name="request-example"></a><span data-ttu-id="996a0-241">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="996a0-241">Request example</span></span>

<span data-ttu-id="996a0-242">Im folgenden Beispiel wird die Aktualisierung einer App-Übermittlung veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="996a0-242">The following example demonstrates how to update an app submission.</span></span>

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

## <a name="response"></a><span data-ttu-id="996a0-243">Antwort</span><span class="sxs-lookup"><span data-stu-id="996a0-243">Response</span></span>

<span data-ttu-id="996a0-244">Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="996a0-244">The following example demonstrates the JSON response body for a successful call to this method.</span></span> <span data-ttu-id="996a0-245">Der Antworttext enthält Informationen zur aktualisierten Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="996a0-245">The response body contains information about the updated submission.</span></span> <span data-ttu-id="996a0-246">Weitere Informationen zu den Werten im Antworttext finden Sie unter [App-Übermittlungsressource](manage-app-submissions.md#app-submission-object).</span><span class="sxs-lookup"><span data-stu-id="996a0-246">For more details about the values in the response body, see [App submission resource](manage-app-submissions.md#app-submission-object).</span></span>

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

## <a name="error-codes"></a><span data-ttu-id="996a0-247">Fehlercodes</span><span class="sxs-lookup"><span data-stu-id="996a0-247">Error codes</span></span>

<span data-ttu-id="996a0-248">Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.</span><span class="sxs-lookup"><span data-stu-id="996a0-248">If the request cannot be successfully completed, the response will contain one of the following HTTP error codes.</span></span>

| <span data-ttu-id="996a0-249">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="996a0-249">Error code</span></span> |  <span data-ttu-id="996a0-250">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="996a0-250">Description</span></span>   |
|--------|------------------|
| <span data-ttu-id="996a0-251">400</span><span class="sxs-lookup"><span data-stu-id="996a0-251">400</span></span>  | <span data-ttu-id="996a0-252">Die Übermittlung konnte nicht aktualisiert werden, da die Anforderung ungültig ist.</span><span class="sxs-lookup"><span data-stu-id="996a0-252">The submission could not be updated because the request is invalid.</span></span> |
| <span data-ttu-id="996a0-253">409</span><span class="sxs-lookup"><span data-stu-id="996a0-253">409</span></span>  | <span data-ttu-id="996a0-254">Die Übermittlung konnte im aktuellen Zustand der App nicht aktualisiert werden, oder in der App wird ein Dev Center-Dashboard-Feature verwendet, das [derzeit nicht von der Windows Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported) wird.</span><span class="sxs-lookup"><span data-stu-id="996a0-254">The submission could not be updated because of the current state of the app, or the app uses a Dev Center dashboard feature that is [currently not supported by the Windows Store submission API](create-and-manage-submissions-using-windows-store-services.md#not_supported).</span></span> |   

<span/>


## <a name="related-topics"></a><span data-ttu-id="996a0-255">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="996a0-255">Related topics</span></span>

* [<span data-ttu-id="996a0-256">Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="996a0-256">Create and manage submissions using Windows Store services</span></span>](create-and-manage-submissions-using-windows-store-services.md)
* [<span data-ttu-id="996a0-257">Abrufen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-257">Get an app submission</span></span>](get-an-app-submission.md)
* [<span data-ttu-id="996a0-258">Erstellen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-258">Create an app submission</span></span>](create-an-app-submission.md)
* [<span data-ttu-id="996a0-259">Ausführen eines Commit für eine App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-259">Commit an app submission</span></span>](commit-an-app-submission.md)
* [<span data-ttu-id="996a0-260">Löschen einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-260">Delete an app submission</span></span>](delete-an-app-submission.md)
* [<span data-ttu-id="996a0-261">Abrufen des Status einer App-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="996a0-261">Get the status of an app submission</span></span>](get-status-for-an-app-submission.md)
