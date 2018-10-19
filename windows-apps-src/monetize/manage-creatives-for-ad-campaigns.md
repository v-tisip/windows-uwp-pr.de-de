---
author: Xansky
ms.assetid: c5246681-82c7-44df-87e1-a84a926e6496
description: Verwenden Sie diese Methode in der Microsoft Store-Werbungs-API, um Werbemittel für Werbeanzeigenkampagnen zu verwalten.
title: Verwalten von Werbemitteln
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store Werbungs-API, Anzeigenkampagnen
ms.localizationpriority: medium
ms.openlocfilehash: 838329101695c21abfb7ac89dd9c83330b7bd26b
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4951083"
---
# <a name="manage-creatives"></a><span data-ttu-id="04436-104">Verwalten von Werbemitteln</span><span class="sxs-lookup"><span data-stu-id="04436-104">Manage creatives</span></span>

<span data-ttu-id="04436-105">Verwenden Sie diese Methoden in der Microsoft Store-Werbungs-API, um Ihre eigenen benutzerdefinierten Werbemittel zu Werbeanzeigenkampagnen hochzuladen oder ein vorhandenes Werbemittel abzurufen.</span><span class="sxs-lookup"><span data-stu-id="04436-105">Use these methods in the Microsoft Store promotions API to upload your own custom creatives to use in promotional ad campaigns or get an existing creative.</span></span> <span data-ttu-id="04436-106">Ein Werbemittel kann einer oder mehreren Lieferpositionen sogar in verschiedenen Anzeigenkampagnen, sofern es sich immer um dieselbe App handelt, zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="04436-106">A creative may be associated with one or more delivery lines, even across ad campaigns, provided it always represents the same app.</span></span>

<span data-ttu-id="04436-107">Weitere Informationen zu der Beziehung zwischen Werbemitteln und Anzeigenkampagnen, Lieferpositionen und Zielgruppenprofilen finden Sie unter [Anzeigenkampagnen mit Microsoft Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span><span class="sxs-lookup"><span data-stu-id="04436-107">For more information about the relationship between creatives and ad campaigns, delivery lines, and targeting profiles, see [Run ad campaigns using Microsoft Store services](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span></span>

> [!NOTE]
> <span data-ttu-id="04436-108">Die maximal zulässige Größe für Ihre Werbemittel ist 40KB, wenn Sie diese API für den Upload Ihrer eigenen Werbemittel verwenden.</span><span class="sxs-lookup"><span data-stu-id="04436-108">When using this API to upload your own creative, the maximum allowed size for your creative is 40 KB.</span></span> <span data-ttu-id="04436-109">Wenn Sie eine größere Werbemitteldatei übermitteln, gibt diese API zwar keinen Fehler zurück, die Kampagne wird jedoch nicht erfolgreich erstellt.</span><span class="sxs-lookup"><span data-stu-id="04436-109">If you submit a creative file larger than this, this API will not return an error, but the campaign will not successfully be created.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04436-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="04436-110">Prerequisites</span></span>

<span data-ttu-id="04436-111">Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="04436-111">To use these methods, you need to first do the following:</span></span>

* <span data-ttu-id="04436-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Microsoft Store-Werbungs-API.</span><span class="sxs-lookup"><span data-stu-id="04436-112">If you have not done so already, complete all the [prerequisites](run-ad-campaigns-using-windows-store-services.md#prerequisites) for the Microsoft Store promotions API.</span></span>
* <span data-ttu-id="04436-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token), das in der Anforderungskopfzeile für diese Methoden verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="04436-113">[Obtain an Azure AD access token](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for these methods.</span></span> <span data-ttu-id="04436-114">Nach Erhalt eines Zugriffstokens können Sie es 60Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="04436-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="04436-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="04436-115">After the token expires, you can obtain a new one.</span></span>


## <a name="request"></a><span data-ttu-id="04436-116">Anfordern</span><span class="sxs-lookup"><span data-stu-id="04436-116">Request</span></span>

<span data-ttu-id="04436-117">Diese Methoden haben die folgenden URIs.</span><span class="sxs-lookup"><span data-stu-id="04436-117">These methods have the following URIs.</span></span>

| <span data-ttu-id="04436-118">Methodentyp</span><span class="sxs-lookup"><span data-stu-id="04436-118">Method type</span></span> | <span data-ttu-id="04436-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="04436-119">Request URI</span></span>     |  <span data-ttu-id="04436-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="04436-120">Description</span></span>  |
|--------|-----------------------------|---------------|
| <span data-ttu-id="04436-121">POST</span><span class="sxs-lookup"><span data-stu-id="04436-121">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative``` |  <span data-ttu-id="04436-122">Erstellt ein neues Werbemittel.</span><span class="sxs-lookup"><span data-stu-id="04436-122">Creates a new creative.</span></span>  |
| <span data-ttu-id="04436-123">GET</span><span class="sxs-lookup"><span data-stu-id="04436-123">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative/{creativeId}``` |  <span data-ttu-id="04436-124">Ruft das durch *CreativeId* angegebene Werbemittel ab.</span><span class="sxs-lookup"><span data-stu-id="04436-124">Gets the creative specified by *creativeId*.</span></span>  |

> [!NOTE]
> <span data-ttu-id="04436-125">Diese API unterstützt derzeit keine PUT-Methode.</span><span class="sxs-lookup"><span data-stu-id="04436-125">This API currently does not support a PUT method.</span></span>


### <a name="header"></a><span data-ttu-id="04436-126">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="04436-126">Header</span></span>

| <span data-ttu-id="04436-127">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="04436-127">Header</span></span>        | <span data-ttu-id="04436-128">Typ</span><span class="sxs-lookup"><span data-stu-id="04436-128">Type</span></span>   | <span data-ttu-id="04436-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="04436-129">Description</span></span>         |
|---------------|--------|---------------------|
| <span data-ttu-id="04436-130">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="04436-130">Authorization</span></span> | <span data-ttu-id="04436-131">String</span><span class="sxs-lookup"><span data-stu-id="04436-131">string</span></span> | <span data-ttu-id="04436-132">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="04436-132">Required.</span></span> <span data-ttu-id="04436-133">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="04436-133">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
| <span data-ttu-id="04436-134">Tracking-ID</span><span class="sxs-lookup"><span data-stu-id="04436-134">Tracking ID</span></span>   | <span data-ttu-id="04436-135">GUID</span><span class="sxs-lookup"><span data-stu-id="04436-135">GUID</span></span>   | <span data-ttu-id="04436-136">Optional.</span><span class="sxs-lookup"><span data-stu-id="04436-136">Optional.</span></span> <span data-ttu-id="04436-137">Eine ID, die den Abfrageablauf verfolgt.</span><span class="sxs-lookup"><span data-stu-id="04436-137">An ID that tracks the call flow.</span></span>                                  |


### <a name="request-body"></a><span data-ttu-id="04436-138">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="04436-138">Request body</span></span>

<span data-ttu-id="04436-139">Die POST-Methode erfordert einen JSON-Anforderungstext mit den erforderlichen Feldern für ein [Werbemittel](#creative)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="04436-139">The POST method requires a JSON request body with the required fields of a [Creative](#creative) object.</span></span>


### <a name="request-examples"></a><span data-ttu-id="04436-140">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="04436-140">Request examples</span></span>

<span data-ttu-id="04436-141">Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen eines Werbemittels aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="04436-141">The following example demonstrates how to call the POST method to create a creative.</span></span> <span data-ttu-id="04436-142">In diesem Beispiel wurde der Wert *content* aus Platzgründen verkürzt.</span><span class="sxs-lookup"><span data-stu-id="04436-142">In this example, the *content* value has been shortened for brevity.</span></span>

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative HTTP/1.1
Authorization: Bearer <your access token>

{
  "name": "Contoso App Campaign - Creative 1",
  "content": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAAQABAAD/2wBDAAgGB...other base64 data shortened for brevity...",
  "height": 80,
  "width": 480,
  "imageAttributes":
  {
    "imageExtension": "PNG"
  }
}
```

<span data-ttu-id="04436-143">Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen eines Werbemittels aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="04436-143">The following example demonstrates how to call the GET method to retrieve a creative.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/creative/106851  HTTP/1.1
Authorization: Bearer <your access token>
```


## <a name="response"></a><span data-ttu-id="04436-144">Antwort</span><span class="sxs-lookup"><span data-stu-id="04436-144">Response</span></span>

<span data-ttu-id="04436-145">Diese Methoden geben ein JSON-Antworttext mit einem [Creative](#creative)-Objekt zurück, das Informationen über das Werbemittel enthält, die erstellt oder abgerufen wurden.</span><span class="sxs-lookup"><span data-stu-id="04436-145">These methods return a JSON response body with a [Creative](#creative) object that contains information about the creative that was created or retrieved.</span></span> <span data-ttu-id="04436-146">Das folgende Beispiel zeigt einen Antworttext für diese Methoden.</span><span class="sxs-lookup"><span data-stu-id="04436-146">The following example demonstrates a response body for these methods.</span></span> <span data-ttu-id="04436-147">In diesem Beispiel wurde der Wert *content* aus Platzgründen verkürzt.</span><span class="sxs-lookup"><span data-stu-id="04436-147">In this example, the *content* value has been shortened for brevity.</span></span>

```json
{
    "Data": {
        "id": 106126,
        "name": "Contoso App Campaign - Creative 2",
        "content": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAAQABAAD/2wBDAAgGB...other base64 data shortened for brevity...",
        "height": 50,
        "width": 300,
        "format": "Banner",
        "imageAttributes":
        {
          "imageExtension": "PNG"
        },
        "storeProductId": "9nblggh42cfd"
    }
}
```


<span id="creative"/>

## <a name="creative-object"></a><span data-ttu-id="04436-148">Kreative-Objekt</span><span class="sxs-lookup"><span data-stu-id="04436-148">Creative object</span></span>

<span data-ttu-id="04436-149">Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder.</span><span class="sxs-lookup"><span data-stu-id="04436-149">The request and response bodies for these methods contain the following fields.</span></span> <span data-ttu-id="04436-150">Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d.h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST-Methode erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="04436-150">This table shows which fields are read-only (meaning that they cannot be changed in the PUT method) and which fields are required in the request body for the POST method.</span></span>

| <span data-ttu-id="04436-151">Feld</span><span class="sxs-lookup"><span data-stu-id="04436-151">Field</span></span>        | <span data-ttu-id="04436-152">Typ</span><span class="sxs-lookup"><span data-stu-id="04436-152">Type</span></span>   |  <span data-ttu-id="04436-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="04436-153">Description</span></span>      |  <span data-ttu-id="04436-154">Schreibgeschützt</span><span class="sxs-lookup"><span data-stu-id="04436-154">Read only</span></span>  | <span data-ttu-id="04436-155">Standard</span><span class="sxs-lookup"><span data-stu-id="04436-155">Default</span></span>  |  <span data-ttu-id="04436-156">Erforderlich für POST</span><span class="sxs-lookup"><span data-stu-id="04436-156">Required for POST</span></span> |  
|--------------|--------|---------------|------|-------------|------------|
|  <span data-ttu-id="04436-157">ID</span><span class="sxs-lookup"><span data-stu-id="04436-157">id</span></span>   |  <span data-ttu-id="04436-158">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="04436-158">integer</span></span>   |  <span data-ttu-id="04436-159">Die ID des Werbemittels.</span><span class="sxs-lookup"><span data-stu-id="04436-159">The ID of the creative.</span></span>     |   <span data-ttu-id="04436-160">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-160">Yes</span></span>    |      |    <span data-ttu-id="04436-161">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-161">No</span></span>   |       
|  <span data-ttu-id="04436-162">Name</span><span class="sxs-lookup"><span data-stu-id="04436-162">name</span></span>   |  <span data-ttu-id="04436-163">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="04436-163">string</span></span>   |   <span data-ttu-id="04436-164">Name des Werbemittels.</span><span class="sxs-lookup"><span data-stu-id="04436-164">The name of the creative.</span></span>    |    <span data-ttu-id="04436-165">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-165">No</span></span>   |      |  <span data-ttu-id="04436-166">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-166">Yes</span></span>     |       
|  <span data-ttu-id="04436-167">content</span><span class="sxs-lookup"><span data-stu-id="04436-167">content</span></span>   |  <span data-ttu-id="04436-168">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="04436-168">string</span></span>   |  <span data-ttu-id="04436-169">Der Inhalt des Werbemittel-Image im Base64-codierten Format.</span><span class="sxs-lookup"><span data-stu-id="04436-169">The content of the creative image, in Base64-encoded format.</span></span><br/><br/><span data-ttu-id="04436-170">**Hinweis:**&nbsp;&nbsp;Die maximal zulässige Größe der Werbemitteldatei beträgt 40KB.</span><span class="sxs-lookup"><span data-stu-id="04436-170">**Note**&nbsp;&nbsp;The maximum allowed size for your creative is 40 KB.</span></span> <span data-ttu-id="04436-171">Wenn Sie eine größere Werbemitteldatei übermitteln, gibt diese API zwar keinen Fehler zurück, die Kampagne wird jedoch nicht erfolgreich erstellt.</span><span class="sxs-lookup"><span data-stu-id="04436-171">If you submit a creative file larger than this, this API will not return an error, but the campaign will not successfully be created.</span></span>     |  <span data-ttu-id="04436-172">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-172">No</span></span>     |      |   <span data-ttu-id="04436-173">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-173">Yes</span></span>    |       
|  <span data-ttu-id="04436-174">height</span><span class="sxs-lookup"><span data-stu-id="04436-174">height</span></span>   |  <span data-ttu-id="04436-175">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="04436-175">integer</span></span>   |   <span data-ttu-id="04436-176">Die Höhe des Werbemittels.</span><span class="sxs-lookup"><span data-stu-id="04436-176">The height of the creative.</span></span>    |    <span data-ttu-id="04436-177">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-177">No</span></span>    |      |   <span data-ttu-id="04436-178">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-178">Yes</span></span>    |       
|  <span data-ttu-id="04436-179">width</span><span class="sxs-lookup"><span data-stu-id="04436-179">width</span></span>   |  <span data-ttu-id="04436-180">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="04436-180">integer</span></span>   |  <span data-ttu-id="04436-181">Die Breite des Werbemittels.</span><span class="sxs-lookup"><span data-stu-id="04436-181">The width of the creative.</span></span>     |  <span data-ttu-id="04436-182">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-182">No</span></span>    |     |    <span data-ttu-id="04436-183">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-183">Yes</span></span>   |       
|  <span data-ttu-id="04436-184">landingUrl</span><span class="sxs-lookup"><span data-stu-id="04436-184">landingUrl</span></span>   |  <span data-ttu-id="04436-185">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="04436-185">string</span></span>   |  <span data-ttu-id="04436-186">Wenn Sie für die Messung von Installationsanalysen für Ihre App einen Kampagnenachverfolgungsdienst wie Kochava, AppsFlyer oder Tune verwenden, weisen Sie die Nachverfolgungs-URL in diesem Feld zu, wenn Sie die POST-Methode aufrufen (wenn angegeben; dieser Wert muss ein gültiger URI sein).</span><span class="sxs-lookup"><span data-stu-id="04436-186">If you are using a campaign tracking service such as Kochava, AppsFlyer or Tune to measure install analytics for your app, assign your tracking URL in this field when you call the POST method (if specified, this value must be a valid URI).</span></span> <span data-ttu-id="04436-187">Wenn Sie keinen Kampagnennachverfolgungsdienst verwenden, lassen Sie diesen Wert beim Aufruf der POST-Methode aus. (In diesem Fall wird diese URL automatisch erstellt.)</span><span class="sxs-lookup"><span data-stu-id="04436-187">If you are not using a campaign tracking service, omit this value when you call the POST method (in this case, this URL will be created automatically).</span></span>   |  <span data-ttu-id="04436-188">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-188">No</span></span>    |     |   <span data-ttu-id="04436-189">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-189">Yes</span></span>    |       
|  <span data-ttu-id="04436-190">format</span><span class="sxs-lookup"><span data-stu-id="04436-190">format</span></span>   |  <span data-ttu-id="04436-191">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="04436-191">string</span></span>   |   <span data-ttu-id="04436-192">Das Anzeigenformat.</span><span class="sxs-lookup"><span data-stu-id="04436-192">The ad format.</span></span> <span data-ttu-id="04436-193">Zurzeit ist **Banner** der einzige Wert, der unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="04436-193">Currently, the only supported value is **Banner**.</span></span>    |   <span data-ttu-id="04436-194">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-194">No</span></span>    |  <span data-ttu-id="04436-195">Banner</span><span class="sxs-lookup"><span data-stu-id="04436-195">Banner</span></span>   |  <span data-ttu-id="04436-196">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-196">No</span></span>     |       
|  <span data-ttu-id="04436-197">imageAttributes</span><span class="sxs-lookup"><span data-stu-id="04436-197">imageAttributes</span></span>   | [<span data-ttu-id="04436-198">ImageAttributes</span><span class="sxs-lookup"><span data-stu-id="04436-198">ImageAttributes</span></span>](#image-attributes)    |   <span data-ttu-id="04436-199">Stellt Attribute für das Werbemittel bereit.</span><span class="sxs-lookup"><span data-stu-id="04436-199">Provides attributes for the creative.</span></span>     |   <span data-ttu-id="04436-200">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-200">No</span></span>    |      |   <span data-ttu-id="04436-201">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-201">Yes</span></span>    |       
|  <span data-ttu-id="04436-202">storeProductId</span><span class="sxs-lookup"><span data-stu-id="04436-202">storeProductId</span></span>   |  <span data-ttu-id="04436-203">String</span><span class="sxs-lookup"><span data-stu-id="04436-203">string</span></span>   |   <span data-ttu-id="04436-204">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, der diese Anzeigenkampagne zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="04436-204">The [Store ID](in-app-purchases-and-trials.md#store-ids) for the app that this ad campaign is associated with.</span></span> <span data-ttu-id="04436-205">Ein Beispiel für eine Store-ID eines Produkts ist 9nblggh42cfd.</span><span class="sxs-lookup"><span data-stu-id="04436-205">An example Store ID for a product is 9nblggh42cfd.</span></span>    |   <span data-ttu-id="04436-206">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-206">No</span></span>    |    |  <span data-ttu-id="04436-207">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-207">No</span></span>     |   |  


<span id="image-attributes"/>

## <a name="imageattributes-object"></a><span data-ttu-id="04436-208">ImageAttributes-Objekt</span><span class="sxs-lookup"><span data-stu-id="04436-208">ImageAttributes object</span></span>

| <span data-ttu-id="04436-209">Feld</span><span class="sxs-lookup"><span data-stu-id="04436-209">Field</span></span>        | <span data-ttu-id="04436-210">Typ</span><span class="sxs-lookup"><span data-stu-id="04436-210">Type</span></span>   |  <span data-ttu-id="04436-211">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="04436-211">Description</span></span>      |  <span data-ttu-id="04436-212">Schreibgeschützt</span><span class="sxs-lookup"><span data-stu-id="04436-212">Read-only</span></span>  | <span data-ttu-id="04436-213">Standardwert</span><span class="sxs-lookup"><span data-stu-id="04436-213">Default value</span></span>  | <span data-ttu-id="04436-214">Erforderlich für POST</span><span class="sxs-lookup"><span data-stu-id="04436-214">Required for POST</span></span> |  
|--------------|--------|---------------|------|-------------|------------|
|  <span data-ttu-id="04436-215">imageExtension</span><span class="sxs-lookup"><span data-stu-id="04436-215">imageExtension</span></span>   |   <span data-ttu-id="04436-216">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="04436-216">string</span></span>  |   <span data-ttu-id="04436-217">Einer der folgenden Werte: **PNG** oder **JPG**.</span><span class="sxs-lookup"><span data-stu-id="04436-217">One of the following values: **PNG** or **JPG**.</span></span>    |    <span data-ttu-id="04436-218">Nein</span><span class="sxs-lookup"><span data-stu-id="04436-218">No</span></span>   |      |   <span data-ttu-id="04436-219">Ja</span><span class="sxs-lookup"><span data-stu-id="04436-219">Yes</span></span>    |       |


## <a name="related-topics"></a><span data-ttu-id="04436-220">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="04436-220">Related topics</span></span>

* [<span data-ttu-id="04436-221">Ausführen von Anzeigenkampagnen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="04436-221">Run ad campaigns using Microsoft Store Services</span></span>](run-ad-campaigns-using-windows-store-services.md)
* [<span data-ttu-id="04436-222">Verwalten von Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="04436-222">Manage ad campaigns</span></span>](manage-ad-campaigns.md)
* [<span data-ttu-id="04436-223">Verwalten von Lieferpositionen für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="04436-223">Manage delivery lines for ad campaigns</span></span>](manage-delivery-lines-for-ad-campaigns.md)
* [<span data-ttu-id="04436-224">Verwalten von Zielgruppenprofilen für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="04436-224">Manage targeting profiles for ad campaigns</span></span>](manage-targeting-profiles-for-ad-campaigns.md)
* [<span data-ttu-id="04436-225">Abrufen der Leistungsdaten einer Anzeigenkampagne</span><span class="sxs-lookup"><span data-stu-id="04436-225">Get ad campaign performance data</span></span>](get-ad-campaign-performance-data.md)
