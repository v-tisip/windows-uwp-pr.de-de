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
ms.openlocfilehash: 71497a858060109eaac0f593ce03f2ba3cbf03cc
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5572439"
---
# <a name="get-response-info-for-reviews"></a><span data-ttu-id="57e71-104">Antwortinformationen für Rezensionen abrufen</span><span class="sxs-lookup"><span data-stu-id="57e71-104">Get response info for reviews</span></span>

<span data-ttu-id="57e71-105">Wenn Sie programmgesteuert auf eine Kundenrezension zu Ihrer App antworten möchten, verwenden Sie diese Methode der Microsoft Store-API für Rezensionen, um zunächst zu ermitteln, ob Sie berechtigt sind, auf die Rezension zu antworten.</span><span class="sxs-lookup"><span data-stu-id="57e71-105">If you want to programmatically respond to a customer review of your app, you can use this method in the Microsoft Store reviews API to first determine whether you have permission to respond to the review.</span></span> <span data-ttu-id="57e71-106">Sie können nicht auf Rezensionen von Kunden antworten, die keine Antwort auf ihre Rezension erhalten möchten.</span><span class="sxs-lookup"><span data-stu-id="57e71-106">You cannot respond to reviews submitted by customers who have chosen not to receive review responses.</span></span> <span data-ttu-id="57e71-107">Nachdem sichergestellt ist, dass Sie auf eine Rezension antworten können, verwenden Sie die Methode [Antworten auf App-Rezensionen senden](submit-responses-to-app-reviews.md), um programmgesteuert zu antworten.</span><span class="sxs-lookup"><span data-stu-id="57e71-107">After you confirm that you can respond to the review, you can then use the [submit responses to app reviews](submit-responses-to-app-reviews.md) method to programmatically respond to it.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="57e71-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="57e71-108">Prerequisites</span></span>

<span data-ttu-id="57e71-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="57e71-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="57e71-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](respond-to-reviews-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="57e71-110">If you have not done so already, complete all the [prerequisites](respond-to-reviews-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="57e71-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="57e71-111">[Obtain an Azure AD access token](respond-to-reviews-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="57e71-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="57e71-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="57e71-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="57e71-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="57e71-114">Rufen Sie die ID der Rezension ab, für die Sie überprüfen möchten, ob Sie darauf antworten können.</span><span class="sxs-lookup"><span data-stu-id="57e71-114">Get the ID of the review you want to check to determine whether you can respond to it.</span></span> <span data-ttu-id="57e71-115">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="57e71-115">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span>

## <a name="request"></a><span data-ttu-id="57e71-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="57e71-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="57e71-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="57e71-117">Request syntax</span></span>

| <span data-ttu-id="57e71-118">Methode</span><span class="sxs-lookup"><span data-stu-id="57e71-118">Method</span></span> | <span data-ttu-id="57e71-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="57e71-119">Request URI</span></span>                                                      |
|--------|------------------------------------------------------------------|
| <span data-ttu-id="57e71-120">GET</span><span class="sxs-lookup"><span data-stu-id="57e71-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/reviews/{reviewId}/apps/{applicationId}/responses/info``` |


### <a name="request-header"></a><span data-ttu-id="57e71-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="57e71-121">Request header</span></span>

| <span data-ttu-id="57e71-122">Header</span><span class="sxs-lookup"><span data-stu-id="57e71-122">Header</span></span>        | <span data-ttu-id="57e71-123">Typ</span><span class="sxs-lookup"><span data-stu-id="57e71-123">Type</span></span>   | <span data-ttu-id="57e71-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57e71-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="57e71-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="57e71-125">Authorization</span></span> | <span data-ttu-id="57e71-126">String</span><span class="sxs-lookup"><span data-stu-id="57e71-126">string</span></span> | <span data-ttu-id="57e71-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="57e71-127">Required.</span></span> <span data-ttu-id="57e71-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="57e71-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="57e71-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="57e71-129">Request parameters</span></span>

| <span data-ttu-id="57e71-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="57e71-130">Parameter</span></span>        | <span data-ttu-id="57e71-131">Typ</span><span class="sxs-lookup"><span data-stu-id="57e71-131">Type</span></span>   | <span data-ttu-id="57e71-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57e71-132">Description</span></span>                                     |  <span data-ttu-id="57e71-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="57e71-133">Required</span></span>  |
|---------------|--------|--------------------------------------------------|--------------|
| <span data-ttu-id="57e71-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="57e71-134">applicationId</span></span> | <span data-ttu-id="57e71-135">string</span><span class="sxs-lookup"><span data-stu-id="57e71-135">string</span></span> | <span data-ttu-id="57e71-136">Die Store-ID der App, welche die Rezension enthält, für die Sie bestimmen möchten, ob Sie antworten können.</span><span class="sxs-lookup"><span data-stu-id="57e71-136">The Store ID of the app that contains the review for which you want to determine whether you can respond to.</span></span> <span data-ttu-id="57e71-137">Die Store-ID ist auf der [Seite mit der App-Identität](../publish/view-app-identity-details.md) des DevCenter-Dashboards verfügbar.</span><span class="sxs-lookup"><span data-stu-id="57e71-137">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) of the Dev Center dashboard.</span></span> <span data-ttu-id="57e71-138">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="57e71-138">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="57e71-139">Ja</span><span class="sxs-lookup"><span data-stu-id="57e71-139">Yes</span></span>  |
| <span data-ttu-id="57e71-140">reviewId</span><span class="sxs-lookup"><span data-stu-id="57e71-140">reviewId</span></span> | <span data-ttu-id="57e71-141">string</span><span class="sxs-lookup"><span data-stu-id="57e71-141">string</span></span> | <span data-ttu-id="57e71-142">Die ID der Rezension, auf die Sie antworten möchten (dies ist eine GUID).</span><span class="sxs-lookup"><span data-stu-id="57e71-142">The ID of the review you want to respond to (this is a GUID).</span></span> <span data-ttu-id="57e71-143">Rezensions-IDs finden Sie in den Antwortdaten der Methode [Abrufen von App-Rezensionen](get-app-reviews.md) der Microsoft Store-Analyse-API und unter [Offlinedownload](../publish/download-analytic-reports.md) im Bericht [Rezensionen](../publish/reviews-report.md).</span><span class="sxs-lookup"><span data-stu-id="57e71-143">Review IDs are available in the response data of the [get app reviews](get-app-reviews.md) method in the Microsoft Store analytics API and in the [offline download](../publish/download-analytic-reports.md) of the [Reviews report](../publish/reviews-report.md).</span></span> <br/><span data-ttu-id="57e71-144">Wenn Sie diesen Parameter nicht angeben, wird im Antworttext für diese Methode stehen, ob Sie über Berechtigungen zum Beantworten von Rezensionen für die angegebene App verfügen.</span><span class="sxs-lookup"><span data-stu-id="57e71-144">If you omit this parameter, the response body for this method will indicate whether you have permissions to respond to any reviews for the specified app.</span></span> |  <span data-ttu-id="57e71-145">Nein</span><span class="sxs-lookup"><span data-stu-id="57e71-145">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="57e71-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="57e71-146">Request example</span></span>

<span data-ttu-id="57e71-147">Das folgende Beispiel zeigt, wie Sie diese Methode verwenden, um festzustellen, ob auf eine bestimmte Rezension antworten können.</span><span class="sxs-lookup"><span data-stu-id="57e71-147">The following examples how to use this method to determine whether you can respond to a given review.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/reviews/6be543ff-1c9c-4534-aced-af8b4fbe0316/apps/9WZDNCRFJ3Q8/responses/info HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="57e71-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="57e71-148">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="57e71-149">Antworttext</span><span class="sxs-lookup"><span data-stu-id="57e71-149">Response body</span></span>

| <span data-ttu-id="57e71-150">Wert</span><span class="sxs-lookup"><span data-stu-id="57e71-150">Value</span></span>      | <span data-ttu-id="57e71-151">Typ</span><span class="sxs-lookup"><span data-stu-id="57e71-151">Type</span></span>   | <span data-ttu-id="57e71-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="57e71-152">Description</span></span>    |  
|------------|--------|-----------------------|
| <span data-ttu-id="57e71-153">CanRespond</span><span class="sxs-lookup"><span data-stu-id="57e71-153">CanRespond</span></span>      | <span data-ttu-id="57e71-154">Boolean</span><span class="sxs-lookup"><span data-stu-id="57e71-154">Boolean</span></span>  | <span data-ttu-id="57e71-155">Der Wert **true** gibt an, dass Sie auf die angegebene Rezension antworten können oder dass Sie berechtigt sind, auf eine beliebige Rezensionen für die angegebene App zu antworten.</span><span class="sxs-lookup"><span data-stu-id="57e71-155">The value **true** indicates that you can respond to the specified review, or that you have permissions to respond to any review for the specified app.</span></span> <span data-ttu-id="57e71-156">Andernfalls ist dieser Wert **false**.</span><span class="sxs-lookup"><span data-stu-id="57e71-156">Otherwise, this value is **false**.</span></span>       |
| <span data-ttu-id="57e71-157">DefaultSupportEmail</span><span class="sxs-lookup"><span data-stu-id="57e71-157">DefaultSupportEmail</span></span>  | <span data-ttu-id="57e71-158">string</span><span class="sxs-lookup"><span data-stu-id="57e71-158">string</span></span> |  <span data-ttu-id="57e71-159">Die von Ihrer App [unterstütze E-Mail-Adresse](../publish/enter-app-properties.md#support-contact-info) finden Sie im Store-Eintrag Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="57e71-159">Your app's [support email address](../publish/enter-app-properties.md#support-contact-info) as specified in your app's Store listing.</span></span> <span data-ttu-id="57e71-160">Wenn Sie keine unterstützte E-Mail-Adresse angegeben haben, ist dieses Feld leer.</span><span class="sxs-lookup"><span data-stu-id="57e71-160">If you did not specify a support email address, this field is empty.</span></span>    |

 
### <a name="response-example"></a><span data-ttu-id="57e71-161">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="57e71-161">Response example</span></span>

<span data-ttu-id="57e71-162">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="57e71-162">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "CanRespond": true,
  "DefaultSupportEmail": "support@contoso.com"
}
```

## <a name="related-topics"></a><span data-ttu-id="57e71-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="57e71-163">Related topics</span></span>

* [<span data-ttu-id="57e71-164">Übermitteln von Antworten auf Rezensionen mithilfe der Microsoft Store-Analyse-API</span><span class="sxs-lookup"><span data-stu-id="57e71-164">Submit responses to reviews using the Microsoft Store analytics API</span></span>](submit-responses-to-app-reviews.md)
* [<span data-ttu-id="57e71-165">Reagieren Sie auf Kundenrezensionen über das Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="57e71-165">Respond to customer reviews using the Dev Center dashboard</span></span>](../publish/respond-to-customer-reviews.md)
* [<span data-ttu-id="57e71-166">Antworten auf Rezensionen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="57e71-166">Respond to reviews using Microsoft Store services</span></span>](respond-to-reviews-using-windows-store-services.md)
* [<span data-ttu-id="57e71-167">Abrufen von App-Rezensionen</span><span class="sxs-lookup"><span data-stu-id="57e71-167">Get app reviews</span></span>](get-app-reviews.md)
