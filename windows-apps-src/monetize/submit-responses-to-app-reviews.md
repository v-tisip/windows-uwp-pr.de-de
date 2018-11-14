---
author: Xansky
ms.assetid: 038903d6-efab-4da6-96b5-046c7431e6e7
description: Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API zum Senden von Antworten auf Rezensionen Ihrer App.
title: Antworten auf Rezensionen übermitteln
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Store-Dienste, Microsoft Store-Rezensions-API, Add-On-Käufe
ms.localizationpriority: medium
ms.openlocfilehash: 8a8a336d477e7d66222632821f0fa0855faae6f7
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6652571"
---
# <a name="submit-responses-to-reviews"></a><span data-ttu-id="8554b-104">Antworten auf Rezensionen übermitteln</span><span class="sxs-lookup"><span data-stu-id="8554b-104">Submit responses to reviews</span></span>


<span data-ttu-id="8554b-105">Verwenden Sie diese Methode in der Microsoft Store-Rezensions-API, um Antworten auf Rezensionen Ihrer App zu senden.</span><span class="sxs-lookup"><span data-stu-id="8554b-105">Use this method in the Microsoft Store reviews API to programmatically respond to reviews of your app.</span></span> <span data-ttu-id="8554b-106">Wenn Sie diese Methode aufrufen, müssen Sie die IDs der Rezensionen angeben, auf die Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-106">When you call this method, you must specify the IDs of the reviews you want to respond to.</span></span> <span data-ttu-id="8554b-107">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="8554b-107">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

<span data-ttu-id="8554b-108">Beim Übermitteln von Rezensionen können Kunden festlegen, dass sie keine Antworten auf ihre Rezension erhalten möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-108">When a customer submits a review, they can choose not to receive responses to their review.</span></span> <span data-ttu-id="8554b-109">Wenn Sie versuchen, auf eine Rezension zu antworten, für die der Kunde ausgewählt hat, keine Antworten zu erhalten, wird im Antworttext dieser Methode angegeben, dass der Antwortversuch fehlgeschlagen ist.</span><span class="sxs-lookup"><span data-stu-id="8554b-109">If you try to respond to a review for which the customer chose not to receive responses, the response body of this method will indicate that the response attempt was unsuccessful.</span></span> <span data-ttu-id="8554b-110">Vor dem Aufrufen dieser Methode können Sie mit der Methode [Antwortinformationen für App-Rezensionen abrufen](get-response-info-for-app-reviews.md) ermitteln, ob Sie auf eine bestimmte Rezension antworten dürfen.</span><span class="sxs-lookup"><span data-stu-id="8554b-110">Before calling this method, you can optionally determine whether you are allowed to respond to a given review by using the [get response info for app reviews](get-response-info-for-app-reviews.md) method.</span></span>

> [!NOTE]
> <span data-ttu-id="8554b-111">Zusätzlich zur Verwendung dieser Methode zum programmgesteuerten reagieren auf Rezensionen können Sie alternativ auf Rezensionen [mithilfe von Partner Center](../publish/respond-to-customer-reviews.md)reagieren.</span><span class="sxs-lookup"><span data-stu-id="8554b-111">In addition to using this method to programmatically respond to reviews, you can alternatively respond to reviews [using Partner Center](../publish/respond-to-customer-reviews.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8554b-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8554b-112">Prerequisites</span></span>

<span data-ttu-id="8554b-113">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="8554b-113">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="8554b-114">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Rezensions-API.</span><span class="sxs-lookup"><span data-stu-id="8554b-114">If you have not done so already, complete all the [prerequisites](respond-to-reviews-using-windows-store-services.md#prerequisites) for the Microsoft Store reviews API.</span></span>
* <span data-ttu-id="8554b-115">[Rufen Sie ein AzureAD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8554b-115">[Obtain an Azure AD access token](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="8554b-116">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="8554b-116">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="8554b-117">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="8554b-117">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="8554b-118">Rufen Sie die IDs der Rezensionen ab, auf die Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-118">Get the IDs of the reviews you want to respond to.</span></span> <span data-ttu-id="8554b-119">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="8554b-119">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

## <a name="request"></a><span data-ttu-id="8554b-120">Anforderung</span><span class="sxs-lookup"><span data-stu-id="8554b-120">Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8554b-121">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="8554b-121">Request syntax</span></span>

| <span data-ttu-id="8554b-122">Methode</span><span class="sxs-lookup"><span data-stu-id="8554b-122">Method</span></span> | <span data-ttu-id="8554b-123">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="8554b-123">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="8554b-124">POST</span><span class="sxs-lookup"><span data-stu-id="8554b-124">POST</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/responses``` |


### <a name="request-header"></a><span data-ttu-id="8554b-125">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="8554b-125">Request header</span></span>

| <span data-ttu-id="8554b-126">Header</span><span class="sxs-lookup"><span data-stu-id="8554b-126">Header</span></span>        | <span data-ttu-id="8554b-127">Typ</span><span class="sxs-lookup"><span data-stu-id="8554b-127">Type</span></span>   | <span data-ttu-id="8554b-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8554b-128">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="8554b-129">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="8554b-129">Authorization</span></span> | <span data-ttu-id="8554b-130">String</span><span class="sxs-lookup"><span data-stu-id="8554b-130">string</span></span> | <span data-ttu-id="8554b-131">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8554b-131">Required.</span></span> <span data-ttu-id="8554b-132">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="8554b-132">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="8554b-133">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="8554b-133">Request parameters</span></span>

<span data-ttu-id="8554b-134">Diese Methode hat keine Anforderungsparameter.</span><span class="sxs-lookup"><span data-stu-id="8554b-134">This method has no request parameters.</span></span>


### <a name="request-body"></a><span data-ttu-id="8554b-135">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="8554b-135">Request body</span></span>

<span data-ttu-id="8554b-136">Der Anforderungstext hat folgende Werte:</span><span class="sxs-lookup"><span data-stu-id="8554b-136">The request body has the following values.</span></span>

| <span data-ttu-id="8554b-137">Wert</span><span class="sxs-lookup"><span data-stu-id="8554b-137">Value</span></span>        | <span data-ttu-id="8554b-138">Typ</span><span class="sxs-lookup"><span data-stu-id="8554b-138">Type</span></span>   | <span data-ttu-id="8554b-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8554b-139">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------|
| <span data-ttu-id="8554b-140">Responses</span><span class="sxs-lookup"><span data-stu-id="8554b-140">Responses</span></span> | <span data-ttu-id="8554b-141">Array</span><span class="sxs-lookup"><span data-stu-id="8554b-141">array</span></span> | <span data-ttu-id="8554b-142">Ein Array von Objekten, die die Antwortdaten enthalten, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-142">An array of objects that contain the response data you want to submit.</span></span> <span data-ttu-id="8554b-143">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="8554b-143">For more information about the data in each object, see the following table.</span></span> |


<span data-ttu-id="8554b-144">Jedes Objekt im *Responses*-Array enthält die folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="8554b-144">Each object in the *Responses* array contains the following values.</span></span>

| <span data-ttu-id="8554b-145">Wert</span><span class="sxs-lookup"><span data-stu-id="8554b-145">Value</span></span>        | <span data-ttu-id="8554b-146">Typ</span><span class="sxs-lookup"><span data-stu-id="8554b-146">Type</span></span>   | <span data-ttu-id="8554b-147">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8554b-147">Description</span></span>           |  <span data-ttu-id="8554b-148">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8554b-148">Required</span></span>  |
|---------------|--------|-----------------------------|-----|
| <span data-ttu-id="8554b-149">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="8554b-149">ApplicationId</span></span> | <span data-ttu-id="8554b-150">String</span><span class="sxs-lookup"><span data-stu-id="8554b-150">string</span></span> |  <span data-ttu-id="8554b-151">Die Store-ID der App, auf deren Rezension Sie antworten möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-151">The Store ID of the app with the review you want to respond to.</span></span> <span data-ttu-id="8554b-152">Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) des Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8554b-152">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) of Partner Center.</span></span> <span data-ttu-id="8554b-153">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="8554b-153">An example Store ID is 9WZDNCRFJ3Q8.</span></span>   |  <span data-ttu-id="8554b-154">Ja</span><span class="sxs-lookup"><span data-stu-id="8554b-154">Yes</span></span>  |
| <span data-ttu-id="8554b-155">ReviewId</span><span class="sxs-lookup"><span data-stu-id="8554b-155">ReviewId</span></span> | <span data-ttu-id="8554b-156">String</span><span class="sxs-lookup"><span data-stu-id="8554b-156">string</span></span> |  <span data-ttu-id="8554b-157">Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID).</span><span class="sxs-lookup"><span data-stu-id="8554b-157">The ID of the review you want to respond to (this is a GUID).</span></span> <span data-ttu-id="8554b-158">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="8554b-158">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>   |  <span data-ttu-id="8554b-159">Ja</span><span class="sxs-lookup"><span data-stu-id="8554b-159">Yes</span></span>  |
| <span data-ttu-id="8554b-160">ResponseText</span><span class="sxs-lookup"><span data-stu-id="8554b-160">ResponseText</span></span> | <span data-ttu-id="8554b-161">String</span><span class="sxs-lookup"><span data-stu-id="8554b-161">string</span></span> | <span data-ttu-id="8554b-162">Die Antwort, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="8554b-162">The response you want to submit.</span></span> <span data-ttu-id="8554b-163">Ihre Antwort muss [diesen Richtlinien](../publish/respond-to-customer-reviews.md#guidelines-for-responses) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="8554b-163">Your response must follow [these guidelines](../publish/respond-to-customer-reviews.md#guidelines-for-responses).</span></span>   |  <span data-ttu-id="8554b-164">Ja</span><span class="sxs-lookup"><span data-stu-id="8554b-164">Yes</span></span>  |
| <span data-ttu-id="8554b-165">SupportEmail</span><span class="sxs-lookup"><span data-stu-id="8554b-165">SupportEmail</span></span> | <span data-ttu-id="8554b-166">String</span><span class="sxs-lookup"><span data-stu-id="8554b-166">string</span></span> | <span data-ttu-id="8554b-167">Die Support-E-Mail-Adresse Ihrer App, über die der Kunde Sie direkt kontaktieren kann.</span><span class="sxs-lookup"><span data-stu-id="8554b-167">Your app's support email address, which the customer can use to contact you directly.</span></span> <span data-ttu-id="8554b-168">Dies muss eine gültige E-Mail-Adresse sein.</span><span class="sxs-lookup"><span data-stu-id="8554b-168">This must be a valid email address.</span></span>     |  <span data-ttu-id="8554b-169">Ja</span><span class="sxs-lookup"><span data-stu-id="8554b-169">Yes</span></span>  |
| <span data-ttu-id="8554b-170">IsPublic</span><span class="sxs-lookup"><span data-stu-id="8554b-170">IsPublic</span></span> | <span data-ttu-id="8554b-171">Boolean</span><span class="sxs-lookup"><span data-stu-id="8554b-171">Boolean</span></span> |  <span data-ttu-id="8554b-172">Wenn Sie auf **"true"** angeben, wird Ihre Antwort im Store-Eintrag, direkt unter der Rezension des Kunden, Ihre app angezeigt wird und für alle Kunden sichtbar.</span><span class="sxs-lookup"><span data-stu-id="8554b-172">If you specify **true**, your response will be displayed in your app's Store listing, directly below the customer's review, and will be visible to all customers.</span></span> <span data-ttu-id="8554b-173">Bei Angabe von **"false",** und der Benutzer noch nicht den Empfang von e-Mail-Antworten zugelassen wird Ihre Antwort an den Kunden per e-Mail gesendet werden, und es wird nicht für andere Kunden im Store-Eintrag Ihrer app sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="8554b-173">If you specify **false** and the user hasn't opted out of receiving email responses, your response will be sent to the customer via email, and it will not be visible to other customers in your app's Store listing.</span></span> <span data-ttu-id="8554b-174">Wenn Sie angeben, **"false",** und der Benutzer den Empfang von Antworten e-Mail entschieden hat, wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8554b-174">If you specify **false** and the user has opted out of receiving email responses, an error will be returned.</span></span>   |  <span data-ttu-id="8554b-175">Ja</span><span class="sxs-lookup"><span data-stu-id="8554b-175">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="8554b-176">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="8554b-176">Request example</span></span>

<span data-ttu-id="8554b-177">Im folgenden Beispiel wird gezeigt, wie diese Methode verwendet wird, um Antworten auf mehrere Rezensionen zu senden.</span><span class="sxs-lookup"><span data-stu-id="8554b-177">The following example demonstrates how to use this method to submit responses to several reviews.</span></span>

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

## <a name="response"></a><span data-ttu-id="8554b-178">Antwort</span><span class="sxs-lookup"><span data-stu-id="8554b-178">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="8554b-179">Antworttext</span><span class="sxs-lookup"><span data-stu-id="8554b-179">Response body</span></span>

| <span data-ttu-id="8554b-180">Wert</span><span class="sxs-lookup"><span data-stu-id="8554b-180">Value</span></span>        | <span data-ttu-id="8554b-181">Typ</span><span class="sxs-lookup"><span data-stu-id="8554b-181">Type</span></span>   | <span data-ttu-id="8554b-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8554b-182">Description</span></span>            |
|---------------|--------|---------------------|
| <span data-ttu-id="8554b-183">Result</span><span class="sxs-lookup"><span data-stu-id="8554b-183">Result</span></span> | <span data-ttu-id="8554b-184">Array</span><span class="sxs-lookup"><span data-stu-id="8554b-184">array</span></span> | <span data-ttu-id="8554b-185">Ein Array von Objekten, die Daten über jede Antwort enthalten, die Sie gesendet haben.</span><span class="sxs-lookup"><span data-stu-id="8554b-185">An array of objects that contain data about each response you submitted.</span></span> <span data-ttu-id="8554b-186">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="8554b-186">For more information about the data in each object, see the following table.</span></span>  |


<span data-ttu-id="8554b-187">Jedes Objekt im *Result*-Array enthält die folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="8554b-187">Each object in the *Result* array contains the following values.</span></span>

| <span data-ttu-id="8554b-188">Wert</span><span class="sxs-lookup"><span data-stu-id="8554b-188">Value</span></span>        | <span data-ttu-id="8554b-189">Typ</span><span class="sxs-lookup"><span data-stu-id="8554b-189">Type</span></span>   | <span data-ttu-id="8554b-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8554b-190">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------|
| <span data-ttu-id="8554b-191">ApplicationId</span><span class="sxs-lookup"><span data-stu-id="8554b-191">ApplicationId</span></span> | <span data-ttu-id="8554b-192">String</span><span class="sxs-lookup"><span data-stu-id="8554b-192">string</span></span> |  <span data-ttu-id="8554b-193">Die Store-ID der App, auf deren Rezension Sie geantwortet haben.</span><span class="sxs-lookup"><span data-stu-id="8554b-193">The Store ID of the app with the review you responded to.</span></span> <span data-ttu-id="8554b-194">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="8554b-194">An example Store ID is 9WZDNCRFJ3Q8.</span></span>   |
| <span data-ttu-id="8554b-195">ReviewId</span><span class="sxs-lookup"><span data-stu-id="8554b-195">ReviewId</span></span> | <span data-ttu-id="8554b-196">String</span><span class="sxs-lookup"><span data-stu-id="8554b-196">string</span></span> |  <span data-ttu-id="8554b-197">Die ID der Rezension, auf die Sie geantwortet haben.</span><span class="sxs-lookup"><span data-stu-id="8554b-197">The ID of the review you responded to.</span></span> <span data-ttu-id="8554b-198">Dies ist eine GUID.</span><span class="sxs-lookup"><span data-stu-id="8554b-198">This is a GUID.</span></span>   |
| <span data-ttu-id="8554b-199">Successful</span><span class="sxs-lookup"><span data-stu-id="8554b-199">Successful</span></span> | <span data-ttu-id="8554b-200">String</span><span class="sxs-lookup"><span data-stu-id="8554b-200">string</span></span> | <span data-ttu-id="8554b-201">Der Wert **true** gibt an, dass Ihre Antwort erfolgreich gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="8554b-201">The value **true** indicates that your response was sent successfully.</span></span> <span data-ttu-id="8554b-202">Der Wert **false** gibt an, dass Ihre Antwort nicht erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="8554b-202">The value **false** indicates that your response was unsuccessful.</span></span>    |
| <span data-ttu-id="8554b-203">FailureReason</span><span class="sxs-lookup"><span data-stu-id="8554b-203">FailureReason</span></span> | <span data-ttu-id="8554b-204">String</span><span class="sxs-lookup"><span data-stu-id="8554b-204">string</span></span> | <span data-ttu-id="8554b-205">Wenn **Successful** **false** ist, dann enthält dieser Wert einen Grund für den Fehler.</span><span class="sxs-lookup"><span data-stu-id="8554b-205">If **Successful** is **false**, this value contains a reason for the failure.</span></span> <span data-ttu-id="8554b-206">Wenn **Successful** **true** ist, dann ist dieser Wert leer.</span><span class="sxs-lookup"><span data-stu-id="8554b-206">If **Successful** is **true**, this value is empty.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="8554b-207">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="8554b-207">Response example</span></span>

<span data-ttu-id="8554b-208">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="8554b-208">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="8554b-209">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8554b-209">Related topics</span></span>

* [<span data-ttu-id="8554b-210">Reagieren Sie auf kundenrezensionen über Partner Center</span><span class="sxs-lookup"><span data-stu-id="8554b-210">Respond to customer reviews using Partner Center</span></span>](../publish/respond-to-customer-reviews.md)
* [<span data-ttu-id="8554b-211">Antworten auf Rezensionen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="8554b-211">Respond to reviews using Microsoft Store services</span></span>](respond-to-reviews-using-windows-store-services.md)
* [<span data-ttu-id="8554b-212">Abrufen von Antwortinformationen für App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="8554b-212">Get response info for app reviews</span></span>](get-response-info-for-app-reviews.md)
* [<span data-ttu-id="8554b-213">Abrufen von App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="8554b-213">Get app reviews</span></span>](get-app-reviews.md)
