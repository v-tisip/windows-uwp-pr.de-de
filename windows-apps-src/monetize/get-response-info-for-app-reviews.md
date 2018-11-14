---
author: Xansky
ms.assetid: fb6bb856-7a1b-4312-a602-f500646a3119
description: Verwenden Sie diese Methode der Microsoft Store-API für Rezensionen, um zu bestimmen, ob Sie auf eine bestimmte Rezension für eine bestimmte App oder auf alle Rezensionen für diese App antworten können.
title: Antwortinformationen für Rezensionen abrufen
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-API für Rezensionen, Antwortinformationen
ms.localizationpriority: medium
ms.openlocfilehash: 466455a5e8da9364206245f1e0ac10acfed07ee7
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6190136"
---
# <a name="get-response-info-for-reviews"></a><span data-ttu-id="35d3d-104">Antwortinformationen für Rezensionen abrufen</span><span class="sxs-lookup"><span data-stu-id="35d3d-104">Get response info for reviews</span></span>

<span data-ttu-id="35d3d-105">Wenn Sie programmgesteuert auf eine Kundenrezension zu Ihrer App antworten möchten, verwenden Sie diese Methode der Microsoft Store-API für Rezensionen, um zunächst zu ermitteln, ob Sie berechtigt sind, auf die Rezension zu antworten.</span><span class="sxs-lookup"><span data-stu-id="35d3d-105">If you want to programmatically respond to a customer review of your app, you can use this method in the Microsoft Store reviews API to first determine whether you have permission to respond to the review.</span></span> <span data-ttu-id="35d3d-106">Sie können nicht auf Rezensionen von Kunden antworten, die keine Antwort auf ihre Rezension erhalten möchten.</span><span class="sxs-lookup"><span data-stu-id="35d3d-106">You cannot respond to reviews submitted by customers who have chosen not to receive review responses.</span></span> <span data-ttu-id="35d3d-107">Nachdem sichergestellt ist, dass Sie auf eine Rezension antworten können, verwenden Sie die Methode [Antworten auf App-Rezensionen senden](submit-responses-to-app-reviews.md), um programmgesteuert zu antworten.</span><span class="sxs-lookup"><span data-stu-id="35d3d-107">After you confirm that you can respond to the review, you can then use the [submit responses to app reviews](submit-responses-to-app-reviews.md) method to programmatically respond to it.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="35d3d-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="35d3d-108">Prerequisites</span></span>

<span data-ttu-id="35d3d-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="35d3d-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="35d3d-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="35d3d-110">If you have not done so already, complete all the [prerequisites](respond-to-reviews-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="35d3d-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="35d3d-111">[Obtain an Azure AD access token](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="35d3d-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="35d3d-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="35d3d-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="35d3d-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="35d3d-114">Rufen Sie die ID der Rezension ab, für die Sie überprüfen möchten, ob Sie darauf antworten können.</span><span class="sxs-lookup"><span data-stu-id="35d3d-114">Get the ID of the review you want to check to determine whether you can respond to it.</span></span> <span data-ttu-id="35d3d-115">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="35d3d-115">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

## <a name="request"></a><span data-ttu-id="35d3d-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="35d3d-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="35d3d-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="35d3d-117">Request syntax</span></span>

| <span data-ttu-id="35d3d-118">Methode</span><span class="sxs-lookup"><span data-stu-id="35d3d-118">Method</span></span> | <span data-ttu-id="35d3d-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="35d3d-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="35d3d-120">GET</span><span class="sxs-lookup"><span data-stu-id="35d3d-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/{reviewId}/apps/{applicationId}/responses/info``` |


### <a name="request-header"></a><span data-ttu-id="35d3d-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="35d3d-121">Request header</span></span>

| <span data-ttu-id="35d3d-122">Header</span><span class="sxs-lookup"><span data-stu-id="35d3d-122">Header</span></span>        | <span data-ttu-id="35d3d-123">Typ</span><span class="sxs-lookup"><span data-stu-id="35d3d-123">Type</span></span>   | <span data-ttu-id="35d3d-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="35d3d-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="35d3d-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="35d3d-125">Authorization</span></span> | <span data-ttu-id="35d3d-126">String</span><span class="sxs-lookup"><span data-stu-id="35d3d-126">string</span></span> | <span data-ttu-id="35d3d-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="35d3d-127">Required.</span></span> <span data-ttu-id="35d3d-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="35d3d-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="35d3d-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="35d3d-129">Request parameters</span></span>

| <span data-ttu-id="35d3d-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="35d3d-130">Parameter</span></span>        | <span data-ttu-id="35d3d-131">Typ</span><span class="sxs-lookup"><span data-stu-id="35d3d-131">Type</span></span>   | <span data-ttu-id="35d3d-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="35d3d-132">Description</span></span>                                     |  <span data-ttu-id="35d3d-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="35d3d-133">Required</span></span>  |
|---------------|--------|--------------------------------------------------|--------------|
| <span data-ttu-id="35d3d-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="35d3d-134">applicationId</span></span> | <span data-ttu-id="35d3d-135">string</span><span class="sxs-lookup"><span data-stu-id="35d3d-135">string</span></span> | <span data-ttu-id="35d3d-136">Die Store-ID der App, welche die Rezension enthält, für die Sie bestimmen möchten, ob Sie antworten können.</span><span class="sxs-lookup"><span data-stu-id="35d3d-136">The Store ID of the app that contains the review for which you want to determine whether you can respond to.</span></span> <span data-ttu-id="35d3d-137">Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="35d3d-137">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) in Partner Center.</span></span> <span data-ttu-id="35d3d-138">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="35d3d-138">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="35d3d-139">Ja</span><span class="sxs-lookup"><span data-stu-id="35d3d-139">Yes</span></span>  |
| <span data-ttu-id="35d3d-140">reviewId</span><span class="sxs-lookup"><span data-stu-id="35d3d-140">reviewId</span></span> | <span data-ttu-id="35d3d-141">string</span><span class="sxs-lookup"><span data-stu-id="35d3d-141">string</span></span> | <span data-ttu-id="35d3d-142">Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID).</span><span class="sxs-lookup"><span data-stu-id="35d3d-142">The ID of the review you want to respond to (this is a GUID).</span></span> <span data-ttu-id="35d3d-143">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="35d3d-143">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span> <br/><span data-ttu-id="35d3d-144">Wenn Sie diesen Parameter nicht angeben, wird im Antworttext für diese Methode stehen, ob Sie über Berechtigungen zum Beantworten von Rezensionen für die angegebene App verfügen.</span><span class="sxs-lookup"><span data-stu-id="35d3d-144">If you omit this parameter, the response body for this method will indicate whether you have permissions to respond to any reviews for the specified app.</span></span> |  <span data-ttu-id="35d3d-145">Nein</span><span class="sxs-lookup"><span data-stu-id="35d3d-145">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="35d3d-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="35d3d-146">Request example</span></span>

<span data-ttu-id="35d3d-147">Das folgende Beispiel zeigt, wie Sie diese Methode verwenden, um festzustellen, ob auf eine bestimmte Rezension antworten können.</span><span class="sxs-lookup"><span data-stu-id="35d3d-147">The following examples how to use this method to determine whether you can respond to a given review.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/reviews/6be543ff-1c9c-4534-aced-af8b4fbe0316/apps/9WZDNCRFJ3Q8/responses/info HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="35d3d-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="35d3d-148">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="35d3d-149">Antworttext</span><span class="sxs-lookup"><span data-stu-id="35d3d-149">Response body</span></span>

| <span data-ttu-id="35d3d-150">Wert</span><span class="sxs-lookup"><span data-stu-id="35d3d-150">Value</span></span>      | <span data-ttu-id="35d3d-151">Typ</span><span class="sxs-lookup"><span data-stu-id="35d3d-151">Type</span></span>   | <span data-ttu-id="35d3d-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="35d3d-152">Description</span></span>    |  
|------------|--------|-----------------------|
| <span data-ttu-id="35d3d-153">CanRespond</span><span class="sxs-lookup"><span data-stu-id="35d3d-153">CanRespond</span></span>      | <span data-ttu-id="35d3d-154">Boolean</span><span class="sxs-lookup"><span data-stu-id="35d3d-154">Boolean</span></span>  | <span data-ttu-id="35d3d-155">Der Wert **true** gibt an, dass Sie auf die angegebene Rezension antworten können oder dass Sie berechtigt sind, auf eine beliebige Rezensionen für die angegebene App zu antworten.</span><span class="sxs-lookup"><span data-stu-id="35d3d-155">The value **true** indicates that you can respond to the specified review, or that you have permissions to respond to any review for the specified app.</span></span> <span data-ttu-id="35d3d-156">Andernfalls ist dieser Wert **false**.</span><span class="sxs-lookup"><span data-stu-id="35d3d-156">Otherwise, this value is **false**.</span></span>       |
| <span data-ttu-id="35d3d-157">DefaultSupportEmail</span><span class="sxs-lookup"><span data-stu-id="35d3d-157">DefaultSupportEmail</span></span>  | <span data-ttu-id="35d3d-158">string</span><span class="sxs-lookup"><span data-stu-id="35d3d-158">string</span></span> |  <span data-ttu-id="35d3d-159">Die von Ihrer App [unterstütze E-Mail-Adresse](../publish/enter-app-properties.md#support-contact-info) finden Sie im Store-Eintrag Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="35d3d-159">Your app's [support email address](../publish/enter-app-properties.md#support-contact-info) as specified in your app's Store listing.</span></span> <span data-ttu-id="35d3d-160">Wenn Sie keine unterstützte E-Mail-Adresse angegeben haben, ist dieses Feld leer.</span><span class="sxs-lookup"><span data-stu-id="35d3d-160">If you did not specify a support email address, this field is empty.</span></span>    |

 
### <a name="response-example"></a><span data-ttu-id="35d3d-161">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="35d3d-161">Response example</span></span>

<span data-ttu-id="35d3d-162">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="35d3d-162">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "CanRespond": true,
  "DefaultSupportEmail": "support@contoso.com"
}
```

## <a name="related-topics"></a><span data-ttu-id="35d3d-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="35d3d-163">Related topics</span></span>

* [<span data-ttu-id="35d3d-164">Übermitteln von Antworten auf Rezensionen mithilfe der Microsoft Store-Analyse-API</span><span class="sxs-lookup"><span data-stu-id="35d3d-164">Submit responses to reviews using the Microsoft Store analytics API</span></span>](submit-responses-to-app-reviews.md)
* [<span data-ttu-id="35d3d-165">Reagieren Sie auf kundenrezensionen über Partner Center</span><span class="sxs-lookup"><span data-stu-id="35d3d-165">Respond to customer reviews using Partner Center</span></span>](../publish/respond-to-customer-reviews.md)
* [<span data-ttu-id="35d3d-166">Antworten auf Rezensionen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="35d3d-166">Respond to reviews using Microsoft Store services</span></span>](respond-to-reviews-using-windows-store-services.md)
* [<span data-ttu-id="35d3d-167">Abrufen von App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="35d3d-167">Get app reviews</span></span>](get-app-reviews.md)
