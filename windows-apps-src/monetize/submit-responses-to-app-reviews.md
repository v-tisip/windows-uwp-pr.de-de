---
ms.assetid: 038903d6-efab-4da6-96b5-046c7431e6e7
description: Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API zum Senden von Antworten auf Rezensionen Ihrer App.
title: Antworten auf Rezensionen übermitteln
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Store-Dienste, Microsoft Store-Rezensions-API, Add-On-Käufe
ms.localizationpriority: medium
ms.openlocfilehash: c08dcda52940f0218b6fdb5be147f058eca7479a
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7973275"
---
# <a name="submit-responses-to-reviews"></a><span data-ttu-id="65708-104">Antworten auf Rezensionen übermitteln</span><span class="sxs-lookup"><span data-stu-id="65708-104">Submit responses to reviews</span></span>


<span data-ttu-id="65708-105">Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API, um Antworten auf Rezensionen Ihrer App zu senden.</span><span class="sxs-lookup"><span data-stu-id="65708-105">Use this method in the Microsoft Store reviews API to programmatically respond to reviews of your app.</span></span> <span data-ttu-id="65708-106">Wenn Sie diese Methode aufrufen, müssen Sie die IDs der Rezensionen angeben, auf die Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-106">When you call this method, you must specify the IDs of the reviews you want to respond to.</span></span> <span data-ttu-id="65708-107">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="65708-107">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

<span data-ttu-id="65708-108">Beim Übermitteln von Rezensionen können Kunden festlegen, dass sie keine Antworten auf ihre Rezension erhalten möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-108">When a customer submits a review, they can choose not to receive responses to their review.</span></span> <span data-ttu-id="65708-109">Wenn Sie versuchen, auf eine Rezension zu antworten, für die der Kunde ausgewählt hat, keine Antworten zu erhalten, wird im Antworttext dieser Methode angegeben, dass der Antwortversuch fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="65708-109">If you try to respond to a review for which the customer chose not to receive responses, the response body of this method will indicate that the response attempt was unsuccessful.</span></span> <span data-ttu-id="65708-110">Vor dem Aufrufen dieser Methode können Sie mit der Methode [Antwortinformationen für App-Rezensionen abrufen](get-response-info-for-app-reviews.md) ermitteln, ob Sie auf eine bestimmte Rezension antworten dürfen.</span><span class="sxs-lookup"><span data-stu-id="65708-110">Before calling this method, you can optionally determine whether you are allowed to respond to a given review by using the [get response info for app reviews](get-response-info-for-app-reviews.md) method.</span></span>

> [!NOTE]
> <span data-ttu-id="65708-111">Zusätzlich zur Verwendung dieser Methode zum programmgesteuerten reagieren auf Rezensionen können Sie alternativ auf Rezensionen [mithilfe von Partner Center](../publish/respond-to-customer-reviews.md)reagieren.</span><span class="sxs-lookup"><span data-stu-id="65708-111">In addition to using this method to programmatically respond to reviews, you can alternatively respond to reviews [using Partner Center](../publish/respond-to-customer-reviews.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65708-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="65708-112">Prerequisites</span></span>

<span data-ttu-id="65708-113">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="65708-113">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="65708-114">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Rezensions-API.</span><span class="sxs-lookup"><span data-stu-id="65708-114">If you have not done so already, complete all the [prerequisites](respond-to-reviews-using-windows-store-services.md#prerequisites) for the Microsoft Store reviews API.</span></span>
* <span data-ttu-id="65708-115">[Rufen Sie ein AzureAD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="65708-115">[Obtain an Azure AD access token](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="65708-116">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="65708-116">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="65708-117">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="65708-117">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="65708-118">Rufen Sie die IDs der Rezensionen ab, auf die Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-118">Get the IDs of the reviews you want to respond to.</span></span> <span data-ttu-id="65708-119">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="65708-119">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

## <a name="request"></a><span data-ttu-id="65708-120">Anforderung</span><span class="sxs-lookup"><span data-stu-id="65708-120">Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="65708-121">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="65708-121">Request syntax</span></span>

| <span data-ttu-id="65708-122">Methode</span><span class="sxs-lookup"><span data-stu-id="65708-122">Method</span></span> | <span data-ttu-id="65708-123">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="65708-123">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="65708-124">POST</span><span class="sxs-lookup"><span data-stu-id="65708-124">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/responses``` |


### <a name="request-header"></a><span data-ttu-id="65708-125">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="65708-125">Request header</span></span>

| <span data-ttu-id="65708-126">Header</span><span class="sxs-lookup"><span data-stu-id="65708-126">Header</span></span>        | <span data-ttu-id="65708-127">Typ</span><span class="sxs-lookup"><span data-stu-id="65708-127">Type</span></span>   | <span data-ttu-id="65708-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65708-128">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="65708-129">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="65708-129">Authorization</span></span> | <span data-ttu-id="65708-130">String</span><span class="sxs-lookup"><span data-stu-id="65708-130">string</span></span> | <span data-ttu-id="65708-131">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="65708-131">Required.</span></span> <span data-ttu-id="65708-132">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="65708-132">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="65708-133">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="65708-133">Request parameters</span></span>

<span data-ttu-id="65708-134">Diese Methode hat keine Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="65708-134">This method has no request parameters.</span></span>


### <a name="request-body"></a><span data-ttu-id="65708-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="65708-135">Request body</span></span>

<span data-ttu-id="65708-136">Der Anforderungstext hat folgende Werte:</span><span class="sxs-lookup"><span data-stu-id="65708-136">The request body has the following values.</span></span>

| <span data-ttu-id="65708-137">Wert</span><span class="sxs-lookup"><span data-stu-id="65708-137">Value</span></span>        | <span data-ttu-id="65708-138">Typ</span><span class="sxs-lookup"><span data-stu-id="65708-138">Type</span></span>   | <span data-ttu-id="65708-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65708-139">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------|
| <span data-ttu-id="65708-140">Responses</span><span class="sxs-lookup"><span data-stu-id="65708-140">Responses</span></span> | <span data-ttu-id="65708-141">Array</span><span class="sxs-lookup"><span data-stu-id="65708-141">array</span></span> | <span data-ttu-id="65708-142">Ein Array von Objekten, die die Antwortdaten enthalten, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-142">An array of objects that contain the response data you want to submit.</span></span> <span data-ttu-id="65708-143">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="65708-143">For more information about the data in each object, see the following table.</span></span> |


<span data-ttu-id="65708-144">Jedes Objekt im *Responses*-Array enthält die folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="65708-144">Each object in the *Responses* array contains the following values.</span></span>

| <span data-ttu-id="65708-145">Wert</span><span class="sxs-lookup"><span data-stu-id="65708-145">Value</span></span>        | <span data-ttu-id="65708-146">Typ</span><span class="sxs-lookup"><span data-stu-id="65708-146">Type</span></span>   | <span data-ttu-id="65708-147">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65708-147">Description</span></span>           |  <span data-ttu-id="65708-148">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="65708-148">Required</span></span>  |
|---------------|--------|-----------------------------|-----|
| <span data-ttu-id="65708-149">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="65708-149">ApplicationId</span></span> | <span data-ttu-id="65708-150">String</span><span class="sxs-lookup"><span data-stu-id="65708-150">string</span></span> |  <span data-ttu-id="65708-151">Die Store-ID der App, auf deren Rezension Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-151">The Store ID of the app with the review you want to respond to.</span></span> <span data-ttu-id="65708-152">Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) des Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="65708-152">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) of Partner Center.</span></span> <span data-ttu-id="65708-153">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="65708-153">An example Store ID is 9WZDNCRFJ3Q8.</span></span>   |  <span data-ttu-id="65708-154">Ja</span><span class="sxs-lookup"><span data-stu-id="65708-154">Yes</span></span>  |
| <span data-ttu-id="65708-155">ReviewId</span><span class="sxs-lookup"><span data-stu-id="65708-155">ReviewId</span></span> | <span data-ttu-id="65708-156">String</span><span class="sxs-lookup"><span data-stu-id="65708-156">string</span></span> |  <span data-ttu-id="65708-157">Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID).</span><span class="sxs-lookup"><span data-stu-id="65708-157">The ID of the review you want to respond to (this is a GUID).</span></span> <span data-ttu-id="65708-158">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="65708-158">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>   |  <span data-ttu-id="65708-159">Ja</span><span class="sxs-lookup"><span data-stu-id="65708-159">Yes</span></span>  |
| <span data-ttu-id="65708-160">ResponseText</span><span class="sxs-lookup"><span data-stu-id="65708-160">ResponseText</span></span> | <span data-ttu-id="65708-161">String</span><span class="sxs-lookup"><span data-stu-id="65708-161">string</span></span> | <span data-ttu-id="65708-162">Die Antwort, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="65708-162">The response you want to submit.</span></span> <span data-ttu-id="65708-163">Ihre Antwort muss [diesen Richtlinien](../publish/respond-to-customer-reviews.md#guidelines-for-responses) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="65708-163">Your response must follow [these guidelines](../publish/respond-to-customer-reviews.md#guidelines-for-responses).</span></span>   |  <span data-ttu-id="65708-164">Ja</span><span class="sxs-lookup"><span data-stu-id="65708-164">Yes</span></span>  |
| <span data-ttu-id="65708-165">SupportEmail</span><span class="sxs-lookup"><span data-stu-id="65708-165">SupportEmail</span></span> | <span data-ttu-id="65708-166">String</span><span class="sxs-lookup"><span data-stu-id="65708-166">string</span></span> | <span data-ttu-id="65708-167">Die Support-E-Mail-Adresse Ihrer App, über die der Kunde Sie direkt kontaktieren kann.</span><span class="sxs-lookup"><span data-stu-id="65708-167">Your app's support email address, which the customer can use to contact you directly.</span></span> <span data-ttu-id="65708-168">Dies muss eine gültige E-Mail-Adresse sein.</span><span class="sxs-lookup"><span data-stu-id="65708-168">This must be a valid email address.</span></span>     |  <span data-ttu-id="65708-169">Ja</span><span class="sxs-lookup"><span data-stu-id="65708-169">Yes</span></span>  |
| <span data-ttu-id="65708-170">IsPublic</span><span class="sxs-lookup"><span data-stu-id="65708-170">IsPublic</span></span> | <span data-ttu-id="65708-171">Boolean</span><span class="sxs-lookup"><span data-stu-id="65708-171">Boolean</span></span> |  <span data-ttu-id="65708-172">Wenn Sie **"true"** festlegen, wird Ihre Antwort im Store-Eintrag, direkt unter der Rezension des Kunden, Ihre app angezeigt wird und für alle Kunden sichtbar.</span><span class="sxs-lookup"><span data-stu-id="65708-172">If you specify **true**, your response will be displayed in your app's Store listing, directly below the customer's review, and will be visible to all customers.</span></span> <span data-ttu-id="65708-173">Bei Angabe von **"false",** und der Benutzer noch nicht den Empfang von Antworten e-Mail entschieden wird Ihre Antwort an den Kunden per e-Mail gesendet werden, und es wird nicht für andere Kunden im Store-Eintrag Ihrer app sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="65708-173">If you specify **false** and the user hasn't opted out of receiving email responses, your response will be sent to the customer via email, and it will not be visible to other customers in your app's Store listing.</span></span> <span data-ttu-id="65708-174">Wenn Sie angeben, **"false",** und der Benutzer den Empfang von Antworten e-Mail entschieden hat, wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="65708-174">If you specify **false** and the user has opted out of receiving email responses, an error will be returned.</span></span>   |  <span data-ttu-id="65708-175">Ja</span><span class="sxs-lookup"><span data-stu-id="65708-175">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="65708-176">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="65708-176">Request example</span></span>

<span data-ttu-id="65708-177">Im folgenden Beispiel wird gezeigt, wie diese Methode verwendet wird, um Antworten auf mehrere Rezensionen zu senden.</span><span class="sxs-lookup"><span data-stu-id="65708-177">The following example demonstrates how to use this method to submit responses to several reviews.</span></span>

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/reviews/responses HTTP/1.1
Authorization: Bearer <your access token>
Content-Type: application/json
{
  "Responses": [
    {
      "ApplicationId": "9WZDNCRFJ3Q8",
      "ReviewId": "6be543ff-1c9c-4534-aced-af8b4fbe0316",
      "ResponseText": "Thank you for pointing out this bug. I fixed it and published an update, you should have the fix soon",
      "SupportEmail": "support@contoso.com",
      "IsPublic": "true"
    },
    {
      "ApplicationId": "9NBLGGH1RP08",
      "ReviewId": "80c9671a-96c2-4278-bcbc-be0ce5a32a7c",
      "ResponseText": "Thank you for submitting your review. Can you tell more about what you were doing in the app when it froze? Thanks very much for your help.",
      "SupportEmail": "support@contoso.com",
      "IsPublic": "false"
    }
  ]
}
```

## <a name="response"></a><span data-ttu-id="65708-178">Antwort</span><span class="sxs-lookup"><span data-stu-id="65708-178">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="65708-179">Antworttext</span><span class="sxs-lookup"><span data-stu-id="65708-179">Response body</span></span>

| <span data-ttu-id="65708-180">Wert</span><span class="sxs-lookup"><span data-stu-id="65708-180">Value</span></span>        | <span data-ttu-id="65708-181">Typ</span><span class="sxs-lookup"><span data-stu-id="65708-181">Type</span></span>   | <span data-ttu-id="65708-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65708-182">Description</span></span>            |
|---------------|--------|---------------------|
| <span data-ttu-id="65708-183">Result</span><span class="sxs-lookup"><span data-stu-id="65708-183">Result</span></span> | <span data-ttu-id="65708-184">Array</span><span class="sxs-lookup"><span data-stu-id="65708-184">array</span></span> | <span data-ttu-id="65708-185">Ein Array von Objekten, die Daten über jede Antwort enthalten, die Sie gesendet haben.</span><span class="sxs-lookup"><span data-stu-id="65708-185">An array of objects that contain data about each response you submitted.</span></span> <span data-ttu-id="65708-186">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="65708-186">For more information about the data in each object, see the following table.</span></span>  |


<span data-ttu-id="65708-187">Jedes Objekt im *Result*-Array enthält die folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="65708-187">Each object in the *Result* array contains the following values.</span></span>

| <span data-ttu-id="65708-188">Wert</span><span class="sxs-lookup"><span data-stu-id="65708-188">Value</span></span>        | <span data-ttu-id="65708-189">Typ</span><span class="sxs-lookup"><span data-stu-id="65708-189">Type</span></span>   | <span data-ttu-id="65708-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65708-190">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------|
| <span data-ttu-id="65708-191">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="65708-191">ApplicationId</span></span> | <span data-ttu-id="65708-192">String</span><span class="sxs-lookup"><span data-stu-id="65708-192">string</span></span> |  <span data-ttu-id="65708-193">Die Store-ID der App, auf deren Rezension Sie geantwortet haben.</span><span class="sxs-lookup"><span data-stu-id="65708-193">The Store ID of the app with the review you responded to.</span></span> <span data-ttu-id="65708-194">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="65708-194">An example Store ID is 9WZDNCRFJ3Q8.</span></span>   |
| <span data-ttu-id="65708-195">ReviewId</span><span class="sxs-lookup"><span data-stu-id="65708-195">ReviewId</span></span> | <span data-ttu-id="65708-196">String</span><span class="sxs-lookup"><span data-stu-id="65708-196">string</span></span> |  <span data-ttu-id="65708-197">Die ID der Rezension, auf die Sie geantwortet haben.</span><span class="sxs-lookup"><span data-stu-id="65708-197">The ID of the review you responded to.</span></span> <span data-ttu-id="65708-198">Dies ist eine GUID.</span><span class="sxs-lookup"><span data-stu-id="65708-198">This is a GUID.</span></span>   |
| <span data-ttu-id="65708-199">Successful</span><span class="sxs-lookup"><span data-stu-id="65708-199">Successful</span></span> | <span data-ttu-id="65708-200">String</span><span class="sxs-lookup"><span data-stu-id="65708-200">string</span></span> | <span data-ttu-id="65708-201">Der Wert **true** gibt an, dass Ihre Antwort erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="65708-201">The value **true** indicates that your response was sent successfully.</span></span> <span data-ttu-id="65708-202">Der Wert **false** gibt an, dass Ihre Antwort nicht erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="65708-202">The value **false** indicates that your response was unsuccessful.</span></span>    |
| <span data-ttu-id="65708-203">FailureReason</span><span class="sxs-lookup"><span data-stu-id="65708-203">FailureReason</span></span> | <span data-ttu-id="65708-204">String</span><span class="sxs-lookup"><span data-stu-id="65708-204">string</span></span> | <span data-ttu-id="65708-205">Wenn **Successful** **false** ist, dann enthält dieser Wert einen Grund für den Fehler.</span><span class="sxs-lookup"><span data-stu-id="65708-205">If **Successful** is **false**, this value contains a reason for the failure.</span></span> <span data-ttu-id="65708-206">Wenn **Successful** **true** ist, dann ist dieser Wert leer.</span><span class="sxs-lookup"><span data-stu-id="65708-206">If **Successful** is **true**, this value is empty.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="65708-207">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="65708-207">Response example</span></span>

<span data-ttu-id="65708-208">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="65708-208">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Result": [
    {
      "ApplicationId": "9WZDNCRFJ3Q8",
      "ReviewId": "6be543ff-1c9c-4534-aced-af8b4fbe0316",
      "Successful": "true",
      "FailureReason": ""
    },
    {
      "ApplicationId": "9NBLGGH1RP08",
      "ReviewId": "80c9671a-96c2-4278-bcbc-be0ce5a32a7c",
      "Successful": "false",
      "FailureReason": "No Permission"
    }
  ]
}
```

## <a name="related-topics"></a><span data-ttu-id="65708-209">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="65708-209">Related topics</span></span>

* [<span data-ttu-id="65708-210">Reagieren Sie auf kundenrezensionen über Partner Center</span><span class="sxs-lookup"><span data-stu-id="65708-210">Respond to customer reviews using Partner Center</span></span>](../publish/respond-to-customer-reviews.md)
* [<span data-ttu-id="65708-211">Antworten auf Rezensionen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="65708-211">Respond to reviews using Microsoft Store services</span></span>](respond-to-reviews-using-windows-store-services.md)
* [<span data-ttu-id="65708-212">Abrufen von Antwortinformationen für App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="65708-212">Get response info for app reviews</span></span>](get-response-info-for-app-reviews.md)
* [<span data-ttu-id="65708-213">Abrufen von App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="65708-213">Get app reviews</span></span>](get-app-reviews.md)
