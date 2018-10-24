---
author: Xansky
ms.assetid: d305746a-d370-4404-8cde-c85765bf3578
description: Verwenden Sie diese Methode in der Microsoft Store-Werbungs-API, um Zielgruppenprofile für Werbeanzeigenkampagnen zu verwalten.
title: Verwalten von Zielgruppenprofilen
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store Werbungs-API, Anzeigenkampagnen
ms.localizationpriority: medium
ms.openlocfilehash: 8fa142f1df672703d2f14dc185481bb248efe07b
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5471589"
---
# <a name="manage-targeting-profiles"></a><span data-ttu-id="7a353-104">Verwalten von Zielgruppenprofilen</span><span class="sxs-lookup"><span data-stu-id="7a353-104">Manage targeting profiles</span></span>


<span data-ttu-id="7a353-105">Verwenden Sie diese Methoden in der Microsoft Store-Werbungs-API, um Benutzer, Regionen und Bestandstypen als Ziele für jede Lieferpositionen einer Werbeanzeigenkampagne auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="7a353-105">Use these methods in the Microsoft Store promotions API to select the users, geographies and inventory types that you want to target for each delivery line in a promotional ad campaign.</span></span> <span data-ttu-id="7a353-106">Zielgruppenprofile können erstellt und über mehrere Lieferpositionen der Übermittlung hinweg wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7a353-106">Targeting profiles can be created and reused across multiple delivery lines.</span></span>

<span data-ttu-id="7a353-107">Weitere Informationen zu der Beziehung zwischen Zielgruppenprofilen und Anzeigenkampagnen, Lieferpositionen und Werbemitteln finden Sie unter [Anzeigenkampagnen mit Microsoft Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span><span class="sxs-lookup"><span data-stu-id="7a353-107">For more information about the relationship between targeting profiles and ad campaigns, delivery lines, and creatives, see [Run ad campaigns using Microsoft Store services](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a353-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7a353-108">Prerequisites</span></span>

<span data-ttu-id="7a353-109">Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="7a353-109">To use these methods, you need to first do the following:</span></span>

* <span data-ttu-id="7a353-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Microsoft Store-Werbungs-API.</span><span class="sxs-lookup"><span data-stu-id="7a353-110">If you have not done so already, complete all the [prerequisites](run-ad-campaigns-using-windows-store-services.md#prerequisites) for the Microsoft Store promotions API.</span></span>
* <span data-ttu-id="7a353-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token), das in der Anforderungskopfzeile für diese Methoden verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7a353-111">[Obtain an Azure AD access token](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for these methods.</span></span> <span data-ttu-id="7a353-112">Nach Erhalt eines Zugriffstokens können Sie es 60Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="7a353-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="7a353-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-113">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="7a353-114">Anfordern</span><span class="sxs-lookup"><span data-stu-id="7a353-114">Request</span></span>

<span data-ttu-id="7a353-115">Diese Methoden haben die folgenden URIs.</span><span class="sxs-lookup"><span data-stu-id="7a353-115">These methods have the following URIs.</span></span>

| <span data-ttu-id="7a353-116">Methodentyp</span><span class="sxs-lookup"><span data-stu-id="7a353-116">Method type</span></span> | <span data-ttu-id="7a353-117">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="7a353-117">Request URI</span></span>                                                      |  <span data-ttu-id="7a353-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a353-118">Description</span></span>  |
|--------|------------------------------------------------------------------|---------------|
| <span data-ttu-id="7a353-119">POST</span><span class="sxs-lookup"><span data-stu-id="7a353-119">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile``` |  <span data-ttu-id="7a353-120">Erstellt ein neues Zielgruppenprofil.</span><span class="sxs-lookup"><span data-stu-id="7a353-120">Creates a new targeting profile.</span></span>  |
| <span data-ttu-id="7a353-121">PUT</span><span class="sxs-lookup"><span data-stu-id="7a353-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/{targetingProfileId}``` |  <span data-ttu-id="7a353-122">Ändert das durch *TargetingProfileId* angegebene Zielgruppenprofil.</span><span class="sxs-lookup"><span data-stu-id="7a353-122">Edits the targeting profile specified by *targetingProfileId*.</span></span>  |
| <span data-ttu-id="7a353-123">GET</span><span class="sxs-lookup"><span data-stu-id="7a353-123">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/{targetingProfileId}``` |  <span data-ttu-id="7a353-124">Ruft das durch *TargetingProfileId* angegebene Zielgruppenprofil ab.</span><span class="sxs-lookup"><span data-stu-id="7a353-124">Gets the targeting profile specified by *targetingProfileId*.</span></span>  |


### <a name="header"></a><span data-ttu-id="7a353-125">Header</span><span class="sxs-lookup"><span data-stu-id="7a353-125">Header</span></span>

| <span data-ttu-id="7a353-126">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="7a353-126">Header</span></span>        | <span data-ttu-id="7a353-127">Typ</span><span class="sxs-lookup"><span data-stu-id="7a353-127">Type</span></span>   | <span data-ttu-id="7a353-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a353-128">Description</span></span>         |
|---------------|--------|---------------------|
| <span data-ttu-id="7a353-129">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="7a353-129">Authorization</span></span> | <span data-ttu-id="7a353-130">String</span><span class="sxs-lookup"><span data-stu-id="7a353-130">string</span></span> | <span data-ttu-id="7a353-131">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7a353-131">Required.</span></span> <span data-ttu-id="7a353-132">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-132">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
| <span data-ttu-id="7a353-133">Tracking-ID</span><span class="sxs-lookup"><span data-stu-id="7a353-133">Tracking ID</span></span>   | <span data-ttu-id="7a353-134">GUID</span><span class="sxs-lookup"><span data-stu-id="7a353-134">GUID</span></span>   | <span data-ttu-id="7a353-135">Optional.</span><span class="sxs-lookup"><span data-stu-id="7a353-135">Optional.</span></span> <span data-ttu-id="7a353-136">Eine ID, die den Abfrageablauf verfolgt.</span><span class="sxs-lookup"><span data-stu-id="7a353-136">An ID that tracks the call flow.</span></span>                                  |


### <a name="request-body"></a><span data-ttu-id="7a353-137">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="7a353-137">Request body</span></span>

<span data-ttu-id="7a353-138">Die POST- und PUT-Methoden erfordern einen JSON-Anforderungstext mit den erforderlichen Feldern für ein [Zielgruppenprofil](#targeting-profile)-Objekt und alle zusätzlichen Felder, die Sie festlegen oder ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="7a353-138">The POST and PUT methods require a JSON request body with the required fields of a [Targeting profile](#targeting-profile) object and any additional fields you want to set or change.</span></span>


### <a name="request-examples"></a><span data-ttu-id="7a353-139">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="7a353-139">Request examples</span></span>

<span data-ttu-id="7a353-140">Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen eines Profils für aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7a353-140">The following example demonstrates how to call the POST method to create a targeting profile.</span></span>

```json
POST https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile HTTP/1.1
Authorization: Bearer <your access token>

{
    "name": "Contoso App Campaign - Targeting Profile 1",
    "targetingType": "Manual",
    "age": [
      651,
      652],
    "gender": [
      700
    ],
    "country": [
      11,
      12
    ],
    "osVersion": [
      504
    ],
    "deviceType": [
      710
    ],
    "supplyType": [
      11470
    ]
}
```

<span data-ttu-id="7a353-141">Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen eines Profils für aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7a353-141">The following example demonstrates how to call the GET method to retrieve a targeting profile.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/310023951  HTTP/1.1
Authorization: Bearer <your access token>
```

<span/>

## <a name="response"></a><span data-ttu-id="7a353-142">Antwort</span><span class="sxs-lookup"><span data-stu-id="7a353-142">Response</span></span>

<span data-ttu-id="7a353-143">Diese Methoden geben einen JSON-Antworttext mit einem [Zielgruppenprofil](#targeting-profile)-Objekt zurück, das Informationen über das erstellte, aktualisierte bzw. abgerufene Zielgruppenprofil enthält.</span><span class="sxs-lookup"><span data-stu-id="7a353-143">These methods return a JSON response body with a [Targeting profile](#targeting-profile) object that contains information about the targeting profile that was created, updated, or retrieved.</span></span> <span data-ttu-id="7a353-144">Das folgende Beispiel zeigt einen Antworttext für diese Methoden.</span><span class="sxs-lookup"><span data-stu-id="7a353-144">The following example demonstrates a response body for these methods.</span></span>

```json
{
  "Data": {
    "id": 310021746,
    "name": "Contoso App Campaign - Targeting Profile 1",
    "targetingType": "Manual",
    "age": [
      651,
      652
    ],
    "gender": [
      700
    ],
    "country": [
      6,
      13,
      29
    ],
    "osVersion": [
      504,
      505,
      506,
      507,
      508
    ],
    "deviceType": [
      710,
      711
    ],
    "supplyType": [
      11470
    ]
  }
}
```

<span id="targeting-profile"/>

## <a name="targeting-profile-object"></a><span data-ttu-id="7a353-145">Zielgruppenprofil-Objekt</span><span class="sxs-lookup"><span data-stu-id="7a353-145">Targeting profile object</span></span>

<span data-ttu-id="7a353-146">Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder.</span><span class="sxs-lookup"><span data-stu-id="7a353-146">The request and response bodies for these methods contain the following fields.</span></span> <span data-ttu-id="7a353-147">Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d.h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST-Methode erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="7a353-147">This table shows which fields are read-only (meaning that they cannot be changed in the PUT method) and which fields are required in the request body for the POST method.</span></span>

| <span data-ttu-id="7a353-148">Feld</span><span class="sxs-lookup"><span data-stu-id="7a353-148">Field</span></span>        | <span data-ttu-id="7a353-149">Typ</span><span class="sxs-lookup"><span data-stu-id="7a353-149">Type</span></span>   |  <span data-ttu-id="7a353-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a353-150">Description</span></span>      |  <span data-ttu-id="7a353-151">Schreibgeschützt</span><span class="sxs-lookup"><span data-stu-id="7a353-151">Read only</span></span>  | <span data-ttu-id="7a353-152">Standard</span><span class="sxs-lookup"><span data-stu-id="7a353-152">Default</span></span>  | <span data-ttu-id="7a353-153">Erforderlich für POST</span><span class="sxs-lookup"><span data-stu-id="7a353-153">Required for POST</span></span> |  
|--------------|--------|---------------|------|-------------|------------|
|  <span data-ttu-id="7a353-154">ID</span><span class="sxs-lookup"><span data-stu-id="7a353-154">id</span></span>   |  <span data-ttu-id="7a353-155">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="7a353-155">integer</span></span>   |  <span data-ttu-id="7a353-156">Die ID des Zielgruppenprofils.</span><span class="sxs-lookup"><span data-stu-id="7a353-156">The ID of the targeting profile.</span></span>     |   <span data-ttu-id="7a353-157">Ja.</span><span class="sxs-lookup"><span data-stu-id="7a353-157">Yes</span></span>    |       |   <span data-ttu-id="7a353-158">Nein</span><span class="sxs-lookup"><span data-stu-id="7a353-158">No</span></span>      |       
|  <span data-ttu-id="7a353-159">Name</span><span class="sxs-lookup"><span data-stu-id="7a353-159">name</span></span>   |  <span data-ttu-id="7a353-160">String</span><span class="sxs-lookup"><span data-stu-id="7a353-160">string</span></span>   |   <span data-ttu-id="7a353-161">Der Name des Zielgruppenprofils.</span><span class="sxs-lookup"><span data-stu-id="7a353-161">The name of the targeting profile.</span></span>    |    <span data-ttu-id="7a353-162">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-162">No</span></span>   |      |  <span data-ttu-id="7a353-163">Ja.</span><span class="sxs-lookup"><span data-stu-id="7a353-163">Yes</span></span>     |       
|  <span data-ttu-id="7a353-164">targetingType</span><span class="sxs-lookup"><span data-stu-id="7a353-164">targetingType</span></span>   |  <span data-ttu-id="7a353-165">String</span><span class="sxs-lookup"><span data-stu-id="7a353-165">string</span></span>   |  <span data-ttu-id="7a353-166">Einer der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="7a353-166">One of the following values:</span></span> <ul><li><span data-ttu-id="7a353-167">**Automatisch**: Geben Sie diesen Wert an, damit Microsoft das Zielgruppenprofil auf der Grundlage der Einstellungen für Ihre App im Dev Center auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="7a353-167">**Auto**: Specify this value to allow Microsoft to choose the targeting profile based on the settings for your app in Dev Center.</span></span></li><li><span data-ttu-id="7a353-168">**Manuell**: Geben Sie diesen Wert an, um Ihr eigenes Zielgruppenprofil zu definieren.</span><span class="sxs-lookup"><span data-stu-id="7a353-168">**Manual**: Specify this value to define your own targeting profile.</span></span></li></ul>     |  <span data-ttu-id="7a353-169">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-169">No</span></span>     |  <span data-ttu-id="7a353-170">Auto</span><span class="sxs-lookup"><span data-stu-id="7a353-170">Auto</span></span>    |   <span data-ttu-id="7a353-171">Ja.</span><span class="sxs-lookup"><span data-stu-id="7a353-171">Yes</span></span>    |       
|  <span data-ttu-id="7a353-172">Alter</span><span class="sxs-lookup"><span data-stu-id="7a353-172">age</span></span>   |  <span data-ttu-id="7a353-173">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-173">array</span></span>   |   <span data-ttu-id="7a353-174">Eine oder mehrere ganze Zahlen, die den Altersbereich der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-174">One or more integers that identify the age ranges of the users to target.</span></span> <span data-ttu-id="7a353-175">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Alterswerte](#age-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-175">For a complete list of integers, see [Age values](#age-values) in this article.</span></span>    |    <span data-ttu-id="7a353-176">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-176">No</span></span>    |  <span data-ttu-id="7a353-177">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-177">null</span></span>    |     <span data-ttu-id="7a353-178">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-178">No</span></span>    |       
|  <span data-ttu-id="7a353-179">Geschlecht</span><span class="sxs-lookup"><span data-stu-id="7a353-179">gender</span></span>   |  <span data-ttu-id="7a353-180">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-180">array</span></span>   |  <span data-ttu-id="7a353-181">Eine oder mehrere Ganzzahlen, die das Geschlecht der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-181">One or more integers that identify the genders of the users to target.</span></span> <span data-ttu-id="7a353-182">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Geschlechtswerte](#gender-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-182">For a complete list of integers, see [Gender values](#gender-values) in this article.</span></span>       |  <span data-ttu-id="7a353-183">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-183">No</span></span>    |  <span data-ttu-id="7a353-184">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-184">null</span></span>    |     <span data-ttu-id="7a353-185">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-185">No</span></span>    |       
|  <span data-ttu-id="7a353-186">Land</span><span class="sxs-lookup"><span data-stu-id="7a353-186">country</span></span>   |  <span data-ttu-id="7a353-187">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-187">array</span></span>   |  <span data-ttu-id="7a353-188">Eine oder mehrere ganze Zahlen, die die Ländercodes der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-188">One or more integers that identify the country codes of the users to target.</span></span> <span data-ttu-id="7a353-189">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Ländercodewerte](#country-code-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-189">For a complete list of integers, see [Country code values](#country-code-values) in this article.</span></span>    |  <span data-ttu-id="7a353-190">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-190">No</span></span>    |  <span data-ttu-id="7a353-191">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-191">null</span></span>   |      <span data-ttu-id="7a353-192">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-192">No</span></span>   |       
|  <span data-ttu-id="7a353-193">osVersion</span><span class="sxs-lookup"><span data-stu-id="7a353-193">osVersion</span></span>   |  <span data-ttu-id="7a353-194">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-194">array</span></span>   |   <span data-ttu-id="7a353-195">Eine oder mehrere ganze Zahlen, die die Betriebssystemversionen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-195">One or more integers that identify the OS versions of the users to target.</span></span> <span data-ttu-id="7a353-196">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Betriebssystemversionswerte](#osversion-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-196">For a complete list of integers, see [OS version values](#osversion-values) in this article.</span></span>     |   <span data-ttu-id="7a353-197">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-197">No</span></span>    |  <span data-ttu-id="7a353-198">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-198">null</span></span>   |     <span data-ttu-id="7a353-199">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-199">No</span></span>    |       
|  <span data-ttu-id="7a353-200">deviceType</span><span class="sxs-lookup"><span data-stu-id="7a353-200">deviceType</span></span>   | <span data-ttu-id="7a353-201">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-201">array</span></span>    |  <span data-ttu-id="7a353-202">Eine oder mehrere ganze Zahlen, die die Gerätetypen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-202">One or more integers that identify the device types of the users to target.</span></span> <span data-ttu-id="7a353-203">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Gerätetypenwerte](#devicetype-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-203">For a complete list of integers, see [Device type values](#devicetype-values) in this article.</span></span>       |   <span data-ttu-id="7a353-204">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-204">No</span></span>    |  <span data-ttu-id="7a353-205">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-205">null</span></span>    |    <span data-ttu-id="7a353-206">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-206">No</span></span>     |       
|  <span data-ttu-id="7a353-207">supplyType</span><span class="sxs-lookup"><span data-stu-id="7a353-207">supplyType</span></span>   |  <span data-ttu-id="7a353-208">Array</span><span class="sxs-lookup"><span data-stu-id="7a353-208">array</span></span>   |  <span data-ttu-id="7a353-209">Eine oder mehrere ganze Zahlen, die den Bestandstyp angeben, in dem die Anzeigen der Kampagne angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7a353-209">One or more integers that identify the type of inventory where the campaign's ads will be shown.</span></span> <span data-ttu-id="7a353-210">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Bestandstypenwerte](#supplytype-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7a353-210">For a complete list of integers, see [Supply type values](#supplytype-values) in this article.</span></span>      |   <span data-ttu-id="7a353-211">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-211">No</span></span>    |  <span data-ttu-id="7a353-212">Null</span><span class="sxs-lookup"><span data-stu-id="7a353-212">null</span></span>   |     <span data-ttu-id="7a353-213">Nein.</span><span class="sxs-lookup"><span data-stu-id="7a353-213">No</span></span>    |   |  


<span id="age-values"/>

### <a name="age-values"></a><span data-ttu-id="7a353-214">Alterswerte</span><span class="sxs-lookup"><span data-stu-id="7a353-214">Age values</span></span>

<span data-ttu-id="7a353-215">Das Feld *Alter* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die den Altersbereich der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-215">The *age* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the age ranges of the users to target.</span></span>

|  <span data-ttu-id="7a353-216">Ganzzahliger Wert für Feld *Alter*</span><span class="sxs-lookup"><span data-stu-id="7a353-216">Integer value for *age* field</span></span>  |  <span data-ttu-id="7a353-217">Entsprechender Altersbereich</span><span class="sxs-lookup"><span data-stu-id="7a353-217">Corresponding age range</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="7a353-218">651</span><span class="sxs-lookup"><span data-stu-id="7a353-218">651</span></span>     |            <span data-ttu-id="7a353-219">13 bis 17</span><span class="sxs-lookup"><span data-stu-id="7a353-219">13 to 17</span></span>             |
|     <span data-ttu-id="7a353-220">652</span><span class="sxs-lookup"><span data-stu-id="7a353-220">652</span></span>     |           <span data-ttu-id="7a353-221">18 bis 24</span><span class="sxs-lookup"><span data-stu-id="7a353-221">18 to 24</span></span>             |
|     <span data-ttu-id="7a353-222">653</span><span class="sxs-lookup"><span data-stu-id="7a353-222">653</span></span>     |            <span data-ttu-id="7a353-223">25 bis 34</span><span class="sxs-lookup"><span data-stu-id="7a353-223">25 to 34</span></span>             |
|     <span data-ttu-id="7a353-224">654</span><span class="sxs-lookup"><span data-stu-id="7a353-224">654</span></span>     |            <span data-ttu-id="7a353-225">35 bis 49</span><span class="sxs-lookup"><span data-stu-id="7a353-225">35 to 49</span></span>             |
|     <span data-ttu-id="7a353-226">655</span><span class="sxs-lookup"><span data-stu-id="7a353-226">655</span></span>     |            <span data-ttu-id="7a353-227">50 und älter</span><span class="sxs-lookup"><span data-stu-id="7a353-227">50 and above</span></span>             |

<span data-ttu-id="7a353-228">Die unterstützten Werte für das Feld *age* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-228">To get the supported values for the *age* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-229">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-229">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/age
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-230">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-230">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "Age": {
      "651": "Age13To17",
      "652": "Age18To24",
      "653": "Age25To34",
      "654": "Age35To49",
      "655": "Age50AndAbove"
    }
  }
}
```

<span id="gender-values"/>

### <a name="gender-values"></a><span data-ttu-id="7a353-231">Geschlechtswerte</span><span class="sxs-lookup"><span data-stu-id="7a353-231">Gender values</span></span>

<span data-ttu-id="7a353-232">Das Feld *Geschlecht* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die das Geschlecht der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-232">The *gender* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the genders of the users to target.</span></span>

|  <span data-ttu-id="7a353-233">Ganzzahliger Wert für das Feld *gender*</span><span class="sxs-lookup"><span data-stu-id="7a353-233">Integer value for *gender* field</span></span>  |  <span data-ttu-id="7a353-234">Entsprechendes Geschlecht</span><span class="sxs-lookup"><span data-stu-id="7a353-234">Corresponding gender</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="7a353-235">700</span><span class="sxs-lookup"><span data-stu-id="7a353-235">700</span></span>     |            <span data-ttu-id="7a353-236">Männlich</span><span class="sxs-lookup"><span data-stu-id="7a353-236">Male</span></span>             |
|     <span data-ttu-id="7a353-237">701</span><span class="sxs-lookup"><span data-stu-id="7a353-237">701</span></span>     |           <span data-ttu-id="7a353-238">Weiblich</span><span class="sxs-lookup"><span data-stu-id="7a353-238">Female</span></span>             |

<span data-ttu-id="7a353-239">Die unterstützten Werte für das Feld *gender* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-239">To get the supported values for the *gender* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-240">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-240">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/gender
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-241">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-241">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "Gender": {
      "700": "Male",
      "701": "Female"
    }
  }
}
```


<span id="osversion-values"/>

### <a name="os-version-values"></a><span data-ttu-id="7a353-242">Werte für Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="7a353-242">OS version values</span></span>

<span data-ttu-id="7a353-243">Das Feld *Betriebssystemversion* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die Betriebssystemversion der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-243">The *osVersion* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the OS versions of the users to target.</span></span>

|  <span data-ttu-id="7a353-244">Ganzzahliger Wert für das Feld *osVersion*</span><span class="sxs-lookup"><span data-stu-id="7a353-244">Integer value for *osVersion* field</span></span>  |  <span data-ttu-id="7a353-245">Entsprechende Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="7a353-245">Corresponding OS version</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="7a353-246">500</span><span class="sxs-lookup"><span data-stu-id="7a353-246">500</span></span>     |            <span data-ttu-id="7a353-247">Windows Phone7</span><span class="sxs-lookup"><span data-stu-id="7a353-247">Windows Phone 7</span></span>             |
|     <span data-ttu-id="7a353-248">501</span><span class="sxs-lookup"><span data-stu-id="7a353-248">501</span></span>     |           <span data-ttu-id="7a353-249">Windows Phone7.1</span><span class="sxs-lookup"><span data-stu-id="7a353-249">Windows Phone 7.1</span></span>             |
|     <span data-ttu-id="7a353-250">502</span><span class="sxs-lookup"><span data-stu-id="7a353-250">502</span></span>     |           <span data-ttu-id="7a353-251">Windows Phone7.5</span><span class="sxs-lookup"><span data-stu-id="7a353-251">Windows Phone 7.5</span></span>             |
|     <span data-ttu-id="7a353-252">503</span><span class="sxs-lookup"><span data-stu-id="7a353-252">503</span></span>     |           <span data-ttu-id="7a353-253">Windows Phone7.8</span><span class="sxs-lookup"><span data-stu-id="7a353-253">Windows Phone 7.8</span></span>             |
|     <span data-ttu-id="7a353-254">504</span><span class="sxs-lookup"><span data-stu-id="7a353-254">504</span></span>     |           <span data-ttu-id="7a353-255">Windows Phone8.0</span><span class="sxs-lookup"><span data-stu-id="7a353-255">Windows Phone 8.0</span></span>             |
|     <span data-ttu-id="7a353-256">505</span><span class="sxs-lookup"><span data-stu-id="7a353-256">505</span></span>     |           <span data-ttu-id="7a353-257">Windows Phone8.1</span><span class="sxs-lookup"><span data-stu-id="7a353-257">Windows Phone 8.1</span></span>             |
|     <span data-ttu-id="7a353-258">506</span><span class="sxs-lookup"><span data-stu-id="7a353-258">506</span></span>     |           <span data-ttu-id="7a353-259">Windows8.0</span><span class="sxs-lookup"><span data-stu-id="7a353-259">Windows 8.0</span></span>             |
|     <span data-ttu-id="7a353-260">507</span><span class="sxs-lookup"><span data-stu-id="7a353-260">507</span></span>     |           <span data-ttu-id="7a353-261">Windows8.1</span><span class="sxs-lookup"><span data-stu-id="7a353-261">Windows 8.1</span></span>             |
|     <span data-ttu-id="7a353-262">508</span><span class="sxs-lookup"><span data-stu-id="7a353-262">508</span></span>     |           <span data-ttu-id="7a353-263">Windows10</span><span class="sxs-lookup"><span data-stu-id="7a353-263">Windows 10</span></span>             |
|     <span data-ttu-id="7a353-264">509</span><span class="sxs-lookup"><span data-stu-id="7a353-264">509</span></span>     |           <span data-ttu-id="7a353-265">Windows10Mobile</span><span class="sxs-lookup"><span data-stu-id="7a353-265">Windows 10 Mobile</span></span>             |

<span data-ttu-id="7a353-266">Die unterstützten Werte für das Feld *osVersion* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-266">To get the supported values for the *osVersion* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-267">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-267">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/osversion
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-268">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-268">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "OsVersion": {
      "500": "WindowsPhone70",
      "501": "WindowsPhone71",
      "502": "WindowsPhone75",
      "503": "WindowsPhone78",
      "504": "WindowsPhone80",
      "505": "WindowsPhone81",
      "506": "Windows80",
      "507": "Windows81",
      "508": "Windows10",
      "509": "WindowsPhone10"
    }
  }
}
```


<span id="devicetype-values"/>

### <a name="device-type-values"></a><span data-ttu-id="7a353-269">Werte für Gerätetyp</span><span class="sxs-lookup"><span data-stu-id="7a353-269">Device type values</span></span>

<span data-ttu-id="7a353-270">Das Feld *deviceType* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die Gerätetypen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7a353-270">The *deviceType* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the device types of the users to target.</span></span>

|  <span data-ttu-id="7a353-271">Ganzzahliger Wert für das Feld *deviceType*</span><span class="sxs-lookup"><span data-stu-id="7a353-271">Integer value for *deviceType* field</span></span>  |  <span data-ttu-id="7a353-272">Entsprechender Gerätetyp</span><span class="sxs-lookup"><span data-stu-id="7a353-272">Corresponding device type</span></span>  |  <span data-ttu-id="7a353-273">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a353-273">Description</span></span>  |
|---------------------------------|---------------------------|---------------------------|
|     <span data-ttu-id="7a353-274">710</span><span class="sxs-lookup"><span data-stu-id="7a353-274">710</span></span>     |  <span data-ttu-id="7a353-275">Windows</span><span class="sxs-lookup"><span data-stu-id="7a353-275">Windows</span></span>   |  <span data-ttu-id="7a353-276">Hierbei handelt es sich um Geräte mit einer Desktop-Version von Windows10 oder Windows8.x.</span><span class="sxs-lookup"><span data-stu-id="7a353-276">This represents devices running a desktop version of Windows 10 or Windows 8.x.</span></span>  |
|     <span data-ttu-id="7a353-277">711</span><span class="sxs-lookup"><span data-stu-id="7a353-277">711</span></span>     |  <span data-ttu-id="7a353-278">Phone</span><span class="sxs-lookup"><span data-stu-id="7a353-278">Phone</span></span>     |  <span data-ttu-id="7a353-279">Hierbei handelt es sich um Geräte unter Windows10 Mobile, Windows Phone8.x oder Windows Phone7.x.</span><span class="sxs-lookup"><span data-stu-id="7a353-279">This represents devices running Windows 10 Mobile, Windows Phone 8.x, or Windows Phone 7.x.</span></span>

<span data-ttu-id="7a353-280">Die unterstützten Werte für das Feld *deviceType* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-280">To get the supported values for the *deviceType* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-281">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-281">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/devicetype
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-282">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-282">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "DeviceType": {
      "710": "Windows",
      "711": "Phone"
    }
  }
}
```


<span id="supplytype-values"/>

### <a name="supply-type-values"></a><span data-ttu-id="7a353-283">Werte für Bestandstypen</span><span class="sxs-lookup"><span data-stu-id="7a353-283">Supply type values</span></span>

<span data-ttu-id="7a353-284">Das Feld *supplyType* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die den Bestandstyp angeben, in dem die Kampagnenanzeigen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7a353-284">The *supplyType* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the type of inventory where the campaign's ads will be shown.</span></span>

|  <span data-ttu-id="7a353-285">Ganzzahliger Wert für das Feld *SupplyType*</span><span class="sxs-lookup"><span data-stu-id="7a353-285">Integer value for *supplyType* field</span></span>  |  <span data-ttu-id="7a353-286">Entsprechender Bestandstyp</span><span class="sxs-lookup"><span data-stu-id="7a353-286">Corresponding supply type</span></span>  |  <span data-ttu-id="7a353-287">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a353-287">Description</span></span>  |
|---------------------------------|---------------------------|---------------------------|
|     <span data-ttu-id="7a353-288">11470</span><span class="sxs-lookup"><span data-stu-id="7a353-288">11470</span></span>     |  <span data-ttu-id="7a353-289">App</span><span class="sxs-lookup"><span data-stu-id="7a353-289">App</span></span>        |  <span data-ttu-id="7a353-290">Dies bezieht sich auf Anzeigen, die ausschließlich in Apps angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7a353-290">This refers to ads that appear in apps only.</span></span>  |
|     <span data-ttu-id="7a353-291">11471</span><span class="sxs-lookup"><span data-stu-id="7a353-291">11471</span></span>     |  <span data-ttu-id="7a353-292">Universelle</span><span class="sxs-lookup"><span data-stu-id="7a353-292">Universal</span></span>        |  <span data-ttu-id="7a353-293">Dies bezieht sich auf Anzeigen, die in Apps, im Internet und auf anderen Anzeigeflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7a353-293">This refers to ads that appear in apps, on the Web, and on and other display surfaces.</span></span>  |

<span data-ttu-id="7a353-294">Die unterstützten Werte für das Feld *supplyType* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-294">To get the supported values for the *supplyType* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-295">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-295">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/supplytype
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-296">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-296">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "SupplyType": {
      "11470": "App",
      "11471": "Universal"
    }
  }
}
```

<span id="country-code-values"/>

### <a name="country-code-values"></a><span data-ttu-id="7a353-297">Werte für Ländercode</span><span class="sxs-lookup"><span data-stu-id="7a353-297">Country code values</span></span>

<span data-ttu-id="7a353-298">Das Feld *country* in dem Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die [ISO3166-1-Alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Ländercodes der Zielgruppenbenutzer identifizieren.</span><span class="sxs-lookup"><span data-stu-id="7a353-298">The *country* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country codes of the users to target.</span></span>

|  <span data-ttu-id="7a353-299">Ganzzahliger Wert für das Feld *country*</span><span class="sxs-lookup"><span data-stu-id="7a353-299">Integer value for *country* field</span></span>  |  <span data-ttu-id="7a353-300">Entsprechender Ländercode</span><span class="sxs-lookup"><span data-stu-id="7a353-300">Corresponding country code</span></span>  |  
|-------------------------------------|------------------------------|
|     <span data-ttu-id="7a353-301">1</span><span class="sxs-lookup"><span data-stu-id="7a353-301">1</span></span>      |            <span data-ttu-id="7a353-302">USA</span><span class="sxs-lookup"><span data-stu-id="7a353-302">US</span></span>                  |
|     <span data-ttu-id="7a353-303">2</span><span class="sxs-lookup"><span data-stu-id="7a353-303">2</span></span>      |            <span data-ttu-id="7a353-304">AU</span><span class="sxs-lookup"><span data-stu-id="7a353-304">AU</span></span>                  |
|     <span data-ttu-id="7a353-305">3</span><span class="sxs-lookup"><span data-stu-id="7a353-305">3</span></span>      |            <span data-ttu-id="7a353-306">AT</span><span class="sxs-lookup"><span data-stu-id="7a353-306">AT</span></span>                  |
|     <span data-ttu-id="7a353-307">4</span><span class="sxs-lookup"><span data-stu-id="7a353-307">4</span></span>      |            <span data-ttu-id="7a353-308">BE</span><span class="sxs-lookup"><span data-stu-id="7a353-308">BE</span></span>                  |
|     <span data-ttu-id="7a353-309">5</span><span class="sxs-lookup"><span data-stu-id="7a353-309">5</span></span>      |            <span data-ttu-id="7a353-310">BR</span><span class="sxs-lookup"><span data-stu-id="7a353-310">BR</span></span>                  |
|     <span data-ttu-id="7a353-311">6</span><span class="sxs-lookup"><span data-stu-id="7a353-311">6</span></span>      |            <span data-ttu-id="7a353-312">CA</span><span class="sxs-lookup"><span data-stu-id="7a353-312">CA</span></span>                  |
|     <span data-ttu-id="7a353-313">7</span><span class="sxs-lookup"><span data-stu-id="7a353-313">7</span></span>      |            <span data-ttu-id="7a353-314">DK</span><span class="sxs-lookup"><span data-stu-id="7a353-314">DK</span></span>                  |
|     <span data-ttu-id="7a353-315">8</span><span class="sxs-lookup"><span data-stu-id="7a353-315">8</span></span>      |            <span data-ttu-id="7a353-316">FI</span><span class="sxs-lookup"><span data-stu-id="7a353-316">FI</span></span>                  |
|     <span data-ttu-id="7a353-317">9</span><span class="sxs-lookup"><span data-stu-id="7a353-317">9</span></span>      |            <span data-ttu-id="7a353-318">FR</span><span class="sxs-lookup"><span data-stu-id="7a353-318">FR</span></span>                  |
|     <span data-ttu-id="7a353-319">10</span><span class="sxs-lookup"><span data-stu-id="7a353-319">10</span></span>      |            <span data-ttu-id="7a353-320">DE</span><span class="sxs-lookup"><span data-stu-id="7a353-320">DE</span></span>                  |
|     <span data-ttu-id="7a353-321">11</span><span class="sxs-lookup"><span data-stu-id="7a353-321">11</span></span>      |            <span data-ttu-id="7a353-322">GR</span><span class="sxs-lookup"><span data-stu-id="7a353-322">GR</span></span>                  |
|     <span data-ttu-id="7a353-323">12</span><span class="sxs-lookup"><span data-stu-id="7a353-323">12</span></span>      |            <span data-ttu-id="7a353-324">HK</span><span class="sxs-lookup"><span data-stu-id="7a353-324">HK</span></span>                  |
|     <span data-ttu-id="7a353-325">13</span><span class="sxs-lookup"><span data-stu-id="7a353-325">13</span></span>      |            <span data-ttu-id="7a353-326">IN</span><span class="sxs-lookup"><span data-stu-id="7a353-326">IN</span></span>                  |
|     <span data-ttu-id="7a353-327">14</span><span class="sxs-lookup"><span data-stu-id="7a353-327">14</span></span>      |            <span data-ttu-id="7a353-328">IE</span><span class="sxs-lookup"><span data-stu-id="7a353-328">IE</span></span>                  |
|     <span data-ttu-id="7a353-329">15</span><span class="sxs-lookup"><span data-stu-id="7a353-329">15</span></span>      |            <span data-ttu-id="7a353-330">IT</span><span class="sxs-lookup"><span data-stu-id="7a353-330">IT</span></span>                  |
|     <span data-ttu-id="7a353-331">16</span><span class="sxs-lookup"><span data-stu-id="7a353-331">16</span></span>      |            <span data-ttu-id="7a353-332">JP</span><span class="sxs-lookup"><span data-stu-id="7a353-332">JP</span></span>                  |
|     <span data-ttu-id="7a353-333">17</span><span class="sxs-lookup"><span data-stu-id="7a353-333">17</span></span>      |            <span data-ttu-id="7a353-334">LU</span><span class="sxs-lookup"><span data-stu-id="7a353-334">LU</span></span>                  |
|     <span data-ttu-id="7a353-335">18</span><span class="sxs-lookup"><span data-stu-id="7a353-335">18</span></span>      |            <span data-ttu-id="7a353-336">MX</span><span class="sxs-lookup"><span data-stu-id="7a353-336">MX</span></span>                  |
|     <span data-ttu-id="7a353-337">19</span><span class="sxs-lookup"><span data-stu-id="7a353-337">19</span></span>      |            <span data-ttu-id="7a353-338">NL</span><span class="sxs-lookup"><span data-stu-id="7a353-338">NL</span></span>                  |
|     <span data-ttu-id="7a353-339">20</span><span class="sxs-lookup"><span data-stu-id="7a353-339">20</span></span>      |            <span data-ttu-id="7a353-340">NZ</span><span class="sxs-lookup"><span data-stu-id="7a353-340">NZ</span></span>                  |
|     <span data-ttu-id="7a353-341">21</span><span class="sxs-lookup"><span data-stu-id="7a353-341">21</span></span>      |            <span data-ttu-id="7a353-342">NO</span><span class="sxs-lookup"><span data-stu-id="7a353-342">NO</span></span>                  |
|     <span data-ttu-id="7a353-343">22</span><span class="sxs-lookup"><span data-stu-id="7a353-343">22</span></span>      |            <span data-ttu-id="7a353-344">PL</span><span class="sxs-lookup"><span data-stu-id="7a353-344">PL</span></span>                  |
|     <span data-ttu-id="7a353-345">23</span><span class="sxs-lookup"><span data-stu-id="7a353-345">23</span></span>      |            <span data-ttu-id="7a353-346">PT</span><span class="sxs-lookup"><span data-stu-id="7a353-346">PT</span></span>                  |
|     <span data-ttu-id="7a353-347">24</span><span class="sxs-lookup"><span data-stu-id="7a353-347">24</span></span>      |            <span data-ttu-id="7a353-348">SG</span><span class="sxs-lookup"><span data-stu-id="7a353-348">SG</span></span>                  |
|     <span data-ttu-id="7a353-349">25</span><span class="sxs-lookup"><span data-stu-id="7a353-349">25</span></span>      |            <span data-ttu-id="7a353-350">ES</span><span class="sxs-lookup"><span data-stu-id="7a353-350">ES</span></span>                  |
|     <span data-ttu-id="7a353-351">26</span><span class="sxs-lookup"><span data-stu-id="7a353-351">26</span></span>      |            <span data-ttu-id="7a353-352">SE</span><span class="sxs-lookup"><span data-stu-id="7a353-352">SE</span></span>                  |
|     <span data-ttu-id="7a353-353">27</span><span class="sxs-lookup"><span data-stu-id="7a353-353">27</span></span>      |            <span data-ttu-id="7a353-354">CH</span><span class="sxs-lookup"><span data-stu-id="7a353-354">CH</span></span>                  |
|     <span data-ttu-id="7a353-355">28</span><span class="sxs-lookup"><span data-stu-id="7a353-355">28</span></span>      |            <span data-ttu-id="7a353-356">TW</span><span class="sxs-lookup"><span data-stu-id="7a353-356">TW</span></span>                  |
|     <span data-ttu-id="7a353-357">29</span><span class="sxs-lookup"><span data-stu-id="7a353-357">29</span></span>      |            <span data-ttu-id="7a353-358">GB</span><span class="sxs-lookup"><span data-stu-id="7a353-358">GB</span></span>                  |
|     <span data-ttu-id="7a353-359">30</span><span class="sxs-lookup"><span data-stu-id="7a353-359">30</span></span>      |            <span data-ttu-id="7a353-360">RU</span><span class="sxs-lookup"><span data-stu-id="7a353-360">RU</span></span>                  |
|     <span data-ttu-id="7a353-361">31</span><span class="sxs-lookup"><span data-stu-id="7a353-361">31</span></span>      |            <span data-ttu-id="7a353-362">CL</span><span class="sxs-lookup"><span data-stu-id="7a353-362">CL</span></span>                  |
|     <span data-ttu-id="7a353-363">32</span><span class="sxs-lookup"><span data-stu-id="7a353-363">32</span></span>      |            <span data-ttu-id="7a353-364">CO</span><span class="sxs-lookup"><span data-stu-id="7a353-364">CO</span></span>                  |
|     <span data-ttu-id="7a353-365">33</span><span class="sxs-lookup"><span data-stu-id="7a353-365">33</span></span>      |            <span data-ttu-id="7a353-366">CZ</span><span class="sxs-lookup"><span data-stu-id="7a353-366">CZ</span></span>                  |
|     <span data-ttu-id="7a353-367">34</span><span class="sxs-lookup"><span data-stu-id="7a353-367">34</span></span>      |            <span data-ttu-id="7a353-368">HU</span><span class="sxs-lookup"><span data-stu-id="7a353-368">HU</span></span>                  |
|     <span data-ttu-id="7a353-369">35</span><span class="sxs-lookup"><span data-stu-id="7a353-369">35</span></span>      |            <span data-ttu-id="7a353-370">ZA</span><span class="sxs-lookup"><span data-stu-id="7a353-370">ZA</span></span>                  |
|     <span data-ttu-id="7a353-371">36</span><span class="sxs-lookup"><span data-stu-id="7a353-371">36</span></span>      |            <span data-ttu-id="7a353-372">KR</span><span class="sxs-lookup"><span data-stu-id="7a353-372">KR</span></span>                  |
|     <span data-ttu-id="7a353-373">37</span><span class="sxs-lookup"><span data-stu-id="7a353-373">37</span></span>      |            <span data-ttu-id="7a353-374">CN</span><span class="sxs-lookup"><span data-stu-id="7a353-374">CN</span></span>                  |
|     <span data-ttu-id="7a353-375">38</span><span class="sxs-lookup"><span data-stu-id="7a353-375">38</span></span>      |            <span data-ttu-id="7a353-376">RO</span><span class="sxs-lookup"><span data-stu-id="7a353-376">RO</span></span>                  |
|     <span data-ttu-id="7a353-377">39</span><span class="sxs-lookup"><span data-stu-id="7a353-377">39</span></span>      |            <span data-ttu-id="7a353-378">TR</span><span class="sxs-lookup"><span data-stu-id="7a353-378">TR</span></span>                  |
|     <span data-ttu-id="7a353-379">40</span><span class="sxs-lookup"><span data-stu-id="7a353-379">40</span></span>      |            <span data-ttu-id="7a353-380">SK</span><span class="sxs-lookup"><span data-stu-id="7a353-380">SK</span></span>                  |
|     <span data-ttu-id="7a353-381">41</span><span class="sxs-lookup"><span data-stu-id="7a353-381">41</span></span>      |            <span data-ttu-id="7a353-382">IL</span><span class="sxs-lookup"><span data-stu-id="7a353-382">IL</span></span>                  |
|     <span data-ttu-id="7a353-383">42</span><span class="sxs-lookup"><span data-stu-id="7a353-383">42</span></span>      |            <span data-ttu-id="7a353-384">ID</span><span class="sxs-lookup"><span data-stu-id="7a353-384">ID</span></span>                  |
|     <span data-ttu-id="7a353-385">43</span><span class="sxs-lookup"><span data-stu-id="7a353-385">43</span></span>      |            <span data-ttu-id="7a353-386">AR</span><span class="sxs-lookup"><span data-stu-id="7a353-386">AR</span></span>                  |
|     <span data-ttu-id="7a353-387">44</span><span class="sxs-lookup"><span data-stu-id="7a353-387">44</span></span>      |            <span data-ttu-id="7a353-388">MY</span><span class="sxs-lookup"><span data-stu-id="7a353-388">MY</span></span>                  |
|     <span data-ttu-id="7a353-389">45</span><span class="sxs-lookup"><span data-stu-id="7a353-389">45</span></span>      |            <span data-ttu-id="7a353-390">PH</span><span class="sxs-lookup"><span data-stu-id="7a353-390">PH</span></span>                  |
|     <span data-ttu-id="7a353-391">46</span><span class="sxs-lookup"><span data-stu-id="7a353-391">46</span></span>      |            <span data-ttu-id="7a353-392">PE</span><span class="sxs-lookup"><span data-stu-id="7a353-392">PE</span></span>                  |
|     <span data-ttu-id="7a353-393">47</span><span class="sxs-lookup"><span data-stu-id="7a353-393">47</span></span>      |            <span data-ttu-id="7a353-394">UA</span><span class="sxs-lookup"><span data-stu-id="7a353-394">UA</span></span>                  |
|     <span data-ttu-id="7a353-395">48</span><span class="sxs-lookup"><span data-stu-id="7a353-395">48</span></span>      |            <span data-ttu-id="7a353-396">AE</span><span class="sxs-lookup"><span data-stu-id="7a353-396">AE</span></span>                  |
|     <span data-ttu-id="7a353-397">49</span><span class="sxs-lookup"><span data-stu-id="7a353-397">49</span></span>      |            <span data-ttu-id="7a353-398">TH</span><span class="sxs-lookup"><span data-stu-id="7a353-398">TH</span></span>                  |
|     <span data-ttu-id="7a353-399">50</span><span class="sxs-lookup"><span data-stu-id="7a353-399">50</span></span>      |            <span data-ttu-id="7a353-400">IQ</span><span class="sxs-lookup"><span data-stu-id="7a353-400">IQ</span></span>                  |
|     <span data-ttu-id="7a353-401">51</span><span class="sxs-lookup"><span data-stu-id="7a353-401">51</span></span>      |            <span data-ttu-id="7a353-402">VN</span><span class="sxs-lookup"><span data-stu-id="7a353-402">VN</span></span>                  |
|     <span data-ttu-id="7a353-403">52</span><span class="sxs-lookup"><span data-stu-id="7a353-403">52</span></span>      |            <span data-ttu-id="7a353-404">CR</span><span class="sxs-lookup"><span data-stu-id="7a353-404">CR</span></span>                  |
|     <span data-ttu-id="7a353-405">53</span><span class="sxs-lookup"><span data-stu-id="7a353-405">53</span></span>      |            <span data-ttu-id="7a353-406">VE</span><span class="sxs-lookup"><span data-stu-id="7a353-406">VE</span></span>                  |
|     <span data-ttu-id="7a353-407">54</span><span class="sxs-lookup"><span data-stu-id="7a353-407">54</span></span>      |            <span data-ttu-id="7a353-408">QA</span><span class="sxs-lookup"><span data-stu-id="7a353-408">QA</span></span>                  |
|     <span data-ttu-id="7a353-409">55</span><span class="sxs-lookup"><span data-stu-id="7a353-409">55</span></span>      |            <span data-ttu-id="7a353-410">SI</span><span class="sxs-lookup"><span data-stu-id="7a353-410">SI</span></span>                  |
|     <span data-ttu-id="7a353-411">56</span><span class="sxs-lookup"><span data-stu-id="7a353-411">56</span></span>      |            <span data-ttu-id="7a353-412">BG</span><span class="sxs-lookup"><span data-stu-id="7a353-412">BG</span></span>                  |
|     <span data-ttu-id="7a353-413">57</span><span class="sxs-lookup"><span data-stu-id="7a353-413">57</span></span>      |            <span data-ttu-id="7a353-414">LT</span><span class="sxs-lookup"><span data-stu-id="7a353-414">LT</span></span>                  |
|     <span data-ttu-id="7a353-415">58</span><span class="sxs-lookup"><span data-stu-id="7a353-415">58</span></span>      |            <span data-ttu-id="7a353-416">RS</span><span class="sxs-lookup"><span data-stu-id="7a353-416">RS</span></span>                  |
|     <span data-ttu-id="7a353-417">59</span><span class="sxs-lookup"><span data-stu-id="7a353-417">59</span></span>      |            <span data-ttu-id="7a353-418">HR</span><span class="sxs-lookup"><span data-stu-id="7a353-418">HR</span></span>                  |
|     <span data-ttu-id="7a353-419">60</span><span class="sxs-lookup"><span data-stu-id="7a353-419">60</span></span>      |            <span data-ttu-id="7a353-420">HR</span><span class="sxs-lookup"><span data-stu-id="7a353-420">HR</span></span>                  |
|     <span data-ttu-id="7a353-421">61</span><span class="sxs-lookup"><span data-stu-id="7a353-421">61</span></span>      |            <span data-ttu-id="7a353-422">LV</span><span class="sxs-lookup"><span data-stu-id="7a353-422">LV</span></span>                  |
|     <span data-ttu-id="7a353-423">62</span><span class="sxs-lookup"><span data-stu-id="7a353-423">62</span></span>      |            <span data-ttu-id="7a353-424">EE</span><span class="sxs-lookup"><span data-stu-id="7a353-424">EE</span></span>                  |
|     <span data-ttu-id="7a353-425">63</span><span class="sxs-lookup"><span data-stu-id="7a353-425">63</span></span>      |            <span data-ttu-id="7a353-426">IS</span><span class="sxs-lookup"><span data-stu-id="7a353-426">IS</span></span>                  |
|     <span data-ttu-id="7a353-427">64</span><span class="sxs-lookup"><span data-stu-id="7a353-427">64</span></span>      |            <span data-ttu-id="7a353-428">KZ</span><span class="sxs-lookup"><span data-stu-id="7a353-428">KZ</span></span>                  |
|     <span data-ttu-id="7a353-429">65</span><span class="sxs-lookup"><span data-stu-id="7a353-429">65</span></span>      |            <span data-ttu-id="7a353-430">SA</span><span class="sxs-lookup"><span data-stu-id="7a353-430">SA</span></span>                  |
|     <span data-ttu-id="7a353-431">67</span><span class="sxs-lookup"><span data-stu-id="7a353-431">67</span></span>      |            <span data-ttu-id="7a353-432">AL</span><span class="sxs-lookup"><span data-stu-id="7a353-432">AL</span></span>                  |
|     <span data-ttu-id="7a353-433">68</span><span class="sxs-lookup"><span data-stu-id="7a353-433">68</span></span>      |            <span data-ttu-id="7a353-434">DZ</span><span class="sxs-lookup"><span data-stu-id="7a353-434">DZ</span></span>                  |
|     <span data-ttu-id="7a353-435">70</span><span class="sxs-lookup"><span data-stu-id="7a353-435">70</span></span>      |            <span data-ttu-id="7a353-436">AO</span><span class="sxs-lookup"><span data-stu-id="7a353-436">AO</span></span>                  |
|     <span data-ttu-id="7a353-437">72</span><span class="sxs-lookup"><span data-stu-id="7a353-437">72</span></span>      |            <span data-ttu-id="7a353-438">AM</span><span class="sxs-lookup"><span data-stu-id="7a353-438">AM</span></span>                  |
|     <span data-ttu-id="7a353-439">73</span><span class="sxs-lookup"><span data-stu-id="7a353-439">73</span></span>      |            <span data-ttu-id="7a353-440">AZ</span><span class="sxs-lookup"><span data-stu-id="7a353-440">AZ</span></span>                  |
|     <span data-ttu-id="7a353-441">74</span><span class="sxs-lookup"><span data-stu-id="7a353-441">74</span></span>      |            <span data-ttu-id="7a353-442">BS</span><span class="sxs-lookup"><span data-stu-id="7a353-442">BS</span></span>                  |
|     <span data-ttu-id="7a353-443">75</span><span class="sxs-lookup"><span data-stu-id="7a353-443">75</span></span>      |            <span data-ttu-id="7a353-444">BD</span><span class="sxs-lookup"><span data-stu-id="7a353-444">BD</span></span>                  |
|     <span data-ttu-id="7a353-445">76</span><span class="sxs-lookup"><span data-stu-id="7a353-445">76</span></span>      |            <span data-ttu-id="7a353-446">BB</span><span class="sxs-lookup"><span data-stu-id="7a353-446">BB</span></span>                  |
|     <span data-ttu-id="7a353-447">77</span><span class="sxs-lookup"><span data-stu-id="7a353-447">77</span></span>      |            <span data-ttu-id="7a353-448">BY</span><span class="sxs-lookup"><span data-stu-id="7a353-448">BY</span></span>                  |
|     <span data-ttu-id="7a353-449">81</span><span class="sxs-lookup"><span data-stu-id="7a353-449">81</span></span>      |            <span data-ttu-id="7a353-450">BO</span><span class="sxs-lookup"><span data-stu-id="7a353-450">BO</span></span>                  |
|     <span data-ttu-id="7a353-451">82</span><span class="sxs-lookup"><span data-stu-id="7a353-451">82</span></span>      |            <span data-ttu-id="7a353-452">BA</span><span class="sxs-lookup"><span data-stu-id="7a353-452">BA</span></span>                  |
|     <span data-ttu-id="7a353-453">83</span><span class="sxs-lookup"><span data-stu-id="7a353-453">83</span></span>      |            <span data-ttu-id="7a353-454">BW</span><span class="sxs-lookup"><span data-stu-id="7a353-454">BW</span></span>                  |
|     <span data-ttu-id="7a353-455">87</span><span class="sxs-lookup"><span data-stu-id="7a353-455">87</span></span>      |            <span data-ttu-id="7a353-456">KH</span><span class="sxs-lookup"><span data-stu-id="7a353-456">KH</span></span>                  |
|     <span data-ttu-id="7a353-457">88</span><span class="sxs-lookup"><span data-stu-id="7a353-457">88</span></span>      |            <span data-ttu-id="7a353-458">CM</span><span class="sxs-lookup"><span data-stu-id="7a353-458">CM</span></span>                  |
|     <span data-ttu-id="7a353-459">94</span><span class="sxs-lookup"><span data-stu-id="7a353-459">94</span></span>      |            <span data-ttu-id="7a353-460">CD</span><span class="sxs-lookup"><span data-stu-id="7a353-460">CD</span></span>                  |
|     <span data-ttu-id="7a353-461">95</span><span class="sxs-lookup"><span data-stu-id="7a353-461">95</span></span>      |            <span data-ttu-id="7a353-462">CI</span><span class="sxs-lookup"><span data-stu-id="7a353-462">CI</span></span>                  |
|     <span data-ttu-id="7a353-463">96</span><span class="sxs-lookup"><span data-stu-id="7a353-463">96</span></span>      |            <span data-ttu-id="7a353-464">CY</span><span class="sxs-lookup"><span data-stu-id="7a353-464">CY</span></span>                  |
|     <span data-ttu-id="7a353-465">99</span><span class="sxs-lookup"><span data-stu-id="7a353-465">99</span></span>      |            <span data-ttu-id="7a353-466">DO</span><span class="sxs-lookup"><span data-stu-id="7a353-466">DO</span></span>                  |
|     <span data-ttu-id="7a353-467">100</span><span class="sxs-lookup"><span data-stu-id="7a353-467">100</span></span>      |            <span data-ttu-id="7a353-468">EC</span><span class="sxs-lookup"><span data-stu-id="7a353-468">EC</span></span>                  |
|     <span data-ttu-id="7a353-469">101</span><span class="sxs-lookup"><span data-stu-id="7a353-469">101</span></span>      |            <span data-ttu-id="7a353-470">EG</span><span class="sxs-lookup"><span data-stu-id="7a353-470">EG</span></span>                  |
|     <span data-ttu-id="7a353-471">102</span><span class="sxs-lookup"><span data-stu-id="7a353-471">102</span></span>      |            <span data-ttu-id="7a353-472">SV</span><span class="sxs-lookup"><span data-stu-id="7a353-472">SV</span></span>                  |
|     <span data-ttu-id="7a353-473">107</span><span class="sxs-lookup"><span data-stu-id="7a353-473">107</span></span>      |            <span data-ttu-id="7a353-474">FJ</span><span class="sxs-lookup"><span data-stu-id="7a353-474">FJ</span></span>                  |
|     <span data-ttu-id="7a353-475">108</span><span class="sxs-lookup"><span data-stu-id="7a353-475">108</span></span>      |            <span data-ttu-id="7a353-476">GA</span><span class="sxs-lookup"><span data-stu-id="7a353-476">GA</span></span>                  |
|     <span data-ttu-id="7a353-477">110</span><span class="sxs-lookup"><span data-stu-id="7a353-477">110</span></span>      |            <span data-ttu-id="7a353-478">GE</span><span class="sxs-lookup"><span data-stu-id="7a353-478">GE</span></span>                  |
|     <span data-ttu-id="7a353-479">111</span><span class="sxs-lookup"><span data-stu-id="7a353-479">111</span></span>      |            <span data-ttu-id="7a353-480">GH</span><span class="sxs-lookup"><span data-stu-id="7a353-480">GH</span></span>                  |
|     <span data-ttu-id="7a353-481">114</span><span class="sxs-lookup"><span data-stu-id="7a353-481">114</span></span>      |            <span data-ttu-id="7a353-482">GT</span><span class="sxs-lookup"><span data-stu-id="7a353-482">GT</span></span>                  |
|     <span data-ttu-id="7a353-483">118</span><span class="sxs-lookup"><span data-stu-id="7a353-483">118</span></span>      |            <span data-ttu-id="7a353-484">HT</span><span class="sxs-lookup"><span data-stu-id="7a353-484">HT</span></span>                  |
|     <span data-ttu-id="7a353-485">119</span><span class="sxs-lookup"><span data-stu-id="7a353-485">119</span></span>      |            <span data-ttu-id="7a353-486">HN</span><span class="sxs-lookup"><span data-stu-id="7a353-486">HN</span></span>                  |
|     <span data-ttu-id="7a353-487">120</span><span class="sxs-lookup"><span data-stu-id="7a353-487">120</span></span>      |            <span data-ttu-id="7a353-488">JM</span><span class="sxs-lookup"><span data-stu-id="7a353-488">JM</span></span>                  |
|     <span data-ttu-id="7a353-489">121</span><span class="sxs-lookup"><span data-stu-id="7a353-489">121</span></span>      |            <span data-ttu-id="7a353-490">JO</span><span class="sxs-lookup"><span data-stu-id="7a353-490">JO</span></span>                  |
|     <span data-ttu-id="7a353-491">122</span><span class="sxs-lookup"><span data-stu-id="7a353-491">122</span></span>      |            <span data-ttu-id="7a353-492">KE</span><span class="sxs-lookup"><span data-stu-id="7a353-492">KE</span></span>                  |
|     <span data-ttu-id="7a353-493">124</span><span class="sxs-lookup"><span data-stu-id="7a353-493">124</span></span>      |            <span data-ttu-id="7a353-494">KW</span><span class="sxs-lookup"><span data-stu-id="7a353-494">KW</span></span>                  |
|     <span data-ttu-id="7a353-495">125</span><span class="sxs-lookup"><span data-stu-id="7a353-495">125</span></span>      |            <span data-ttu-id="7a353-496">KG</span><span class="sxs-lookup"><span data-stu-id="7a353-496">KG</span></span>                  |
|     <span data-ttu-id="7a353-497">126</span><span class="sxs-lookup"><span data-stu-id="7a353-497">126</span></span>      |            <span data-ttu-id="7a353-498">LA</span><span class="sxs-lookup"><span data-stu-id="7a353-498">LA</span></span>                  |
|     <span data-ttu-id="7a353-499">127 Zeichen lang sein</span><span class="sxs-lookup"><span data-stu-id="7a353-499">127</span></span>      |            <span data-ttu-id="7a353-500">LB</span><span class="sxs-lookup"><span data-stu-id="7a353-500">LB</span></span>                  |
|     <span data-ttu-id="7a353-501">133</span><span class="sxs-lookup"><span data-stu-id="7a353-501">133</span></span>      |            <span data-ttu-id="7a353-502">MK</span><span class="sxs-lookup"><span data-stu-id="7a353-502">MK</span></span>                  |
|     <span data-ttu-id="7a353-503">135</span><span class="sxs-lookup"><span data-stu-id="7a353-503">135</span></span>      |            <span data-ttu-id="7a353-504">MW</span><span class="sxs-lookup"><span data-stu-id="7a353-504">MW</span></span>                  |
|     <span data-ttu-id="7a353-505">138</span><span class="sxs-lookup"><span data-stu-id="7a353-505">138</span></span>      |            <span data-ttu-id="7a353-506">MT</span><span class="sxs-lookup"><span data-stu-id="7a353-506">MT</span></span>                  |
|     <span data-ttu-id="7a353-507">141</span><span class="sxs-lookup"><span data-stu-id="7a353-507">141</span></span>      |            <span data-ttu-id="7a353-508">MU</span><span class="sxs-lookup"><span data-stu-id="7a353-508">MU</span></span>                  |
|     <span data-ttu-id="7a353-509">145</span><span class="sxs-lookup"><span data-stu-id="7a353-509">145</span></span>      |            <span data-ttu-id="7a353-510">ME</span><span class="sxs-lookup"><span data-stu-id="7a353-510">ME</span></span>                  |
|     <span data-ttu-id="7a353-511">146</span><span class="sxs-lookup"><span data-stu-id="7a353-511">146</span></span>      |            <span data-ttu-id="7a353-512">MA</span><span class="sxs-lookup"><span data-stu-id="7a353-512">MA</span></span>                  |
|     <span data-ttu-id="7a353-513">147</span><span class="sxs-lookup"><span data-stu-id="7a353-513">147</span></span>      |            <span data-ttu-id="7a353-514">MZ</span><span class="sxs-lookup"><span data-stu-id="7a353-514">MZ</span></span>                  |
|     <span data-ttu-id="7a353-515">148</span><span class="sxs-lookup"><span data-stu-id="7a353-515">148</span></span>      |            <span data-ttu-id="7a353-516">NA</span><span class="sxs-lookup"><span data-stu-id="7a353-516">NA</span></span>                  |
|     <span data-ttu-id="7a353-517">150</span><span class="sxs-lookup"><span data-stu-id="7a353-517">150</span></span>      |            <span data-ttu-id="7a353-518">NP</span><span class="sxs-lookup"><span data-stu-id="7a353-518">NP</span></span>                  |
|     <span data-ttu-id="7a353-519">151.</span><span class="sxs-lookup"><span data-stu-id="7a353-519">151</span></span>      |            <span data-ttu-id="7a353-520">NI</span><span class="sxs-lookup"><span data-stu-id="7a353-520">NI</span></span>                  |
|     <span data-ttu-id="7a353-521">153</span><span class="sxs-lookup"><span data-stu-id="7a353-521">153</span></span>      |            <span data-ttu-id="7a353-522">NG</span><span class="sxs-lookup"><span data-stu-id="7a353-522">NG</span></span>                  |
|     <span data-ttu-id="7a353-523">154</span><span class="sxs-lookup"><span data-stu-id="7a353-523">154</span></span>      |            <span data-ttu-id="7a353-524">OM</span><span class="sxs-lookup"><span data-stu-id="7a353-524">OM</span></span>                  |
|     <span data-ttu-id="7a353-525">155</span><span class="sxs-lookup"><span data-stu-id="7a353-525">155</span></span>      |            <span data-ttu-id="7a353-526">PK</span><span class="sxs-lookup"><span data-stu-id="7a353-526">PK</span></span>                  |
|     <span data-ttu-id="7a353-527">157</span><span class="sxs-lookup"><span data-stu-id="7a353-527">157</span></span>      |            <span data-ttu-id="7a353-528">PA</span><span class="sxs-lookup"><span data-stu-id="7a353-528">PA</span></span>                  |
|     <span data-ttu-id="7a353-529">159</span><span class="sxs-lookup"><span data-stu-id="7a353-529">159</span></span>      |            <span data-ttu-id="7a353-530">PY</span><span class="sxs-lookup"><span data-stu-id="7a353-530">PY</span></span>                  |
|     <span data-ttu-id="7a353-531">167</span><span class="sxs-lookup"><span data-stu-id="7a353-531">167</span></span>      |            <span data-ttu-id="7a353-532">SN</span><span class="sxs-lookup"><span data-stu-id="7a353-532">SN</span></span>                  |
|     <span data-ttu-id="7a353-533">172</span><span class="sxs-lookup"><span data-stu-id="7a353-533">172</span></span>      |            <span data-ttu-id="7a353-534">LK</span><span class="sxs-lookup"><span data-stu-id="7a353-534">LK</span></span>                  |
|     <span data-ttu-id="7a353-535">176</span><span class="sxs-lookup"><span data-stu-id="7a353-535">176</span></span>      |            <span data-ttu-id="7a353-536">TZ</span><span class="sxs-lookup"><span data-stu-id="7a353-536">TZ</span></span>                  |
|     <span data-ttu-id="7a353-537">180</span><span class="sxs-lookup"><span data-stu-id="7a353-537">180</span></span>      |            <span data-ttu-id="7a353-538">TT</span><span class="sxs-lookup"><span data-stu-id="7a353-538">TT</span></span>                  |
|     <span data-ttu-id="7a353-539">181</span><span class="sxs-lookup"><span data-stu-id="7a353-539">181</span></span>      |            <span data-ttu-id="7a353-540">TN</span><span class="sxs-lookup"><span data-stu-id="7a353-540">TN</span></span>                  |
|     <span data-ttu-id="7a353-541">184</span><span class="sxs-lookup"><span data-stu-id="7a353-541">184</span></span>      |            <span data-ttu-id="7a353-542">UG</span><span class="sxs-lookup"><span data-stu-id="7a353-542">UG</span></span>                  |
|     <span data-ttu-id="7a353-543">185</span><span class="sxs-lookup"><span data-stu-id="7a353-543">185</span></span>      |            <span data-ttu-id="7a353-544">UY</span><span class="sxs-lookup"><span data-stu-id="7a353-544">UY</span></span>                  |
|     <span data-ttu-id="7a353-545">186</span><span class="sxs-lookup"><span data-stu-id="7a353-545">186</span></span>      |            <span data-ttu-id="7a353-546">UZ</span><span class="sxs-lookup"><span data-stu-id="7a353-546">UZ</span></span>                  |
|     <span data-ttu-id="7a353-547">189</span><span class="sxs-lookup"><span data-stu-id="7a353-547">189</span></span>      |            <span data-ttu-id="7a353-548">ZM</span><span class="sxs-lookup"><span data-stu-id="7a353-548">ZM</span></span>                  |
|     <span data-ttu-id="7a353-549">190</span><span class="sxs-lookup"><span data-stu-id="7a353-549">190</span></span>      |            <span data-ttu-id="7a353-550">ZW</span><span class="sxs-lookup"><span data-stu-id="7a353-550">ZW</span></span>                  |
|     <span data-ttu-id="7a353-551">219</span><span class="sxs-lookup"><span data-stu-id="7a353-551">219</span></span>      |            <span data-ttu-id="7a353-552">MD</span><span class="sxs-lookup"><span data-stu-id="7a353-552">MD</span></span>                  |
|     <span data-ttu-id="7a353-553">224</span><span class="sxs-lookup"><span data-stu-id="7a353-553">224</span></span>      |            <span data-ttu-id="7a353-554">PS</span><span class="sxs-lookup"><span data-stu-id="7a353-554">PS</span></span>                  |
|     <span data-ttu-id="7a353-555">225</span><span class="sxs-lookup"><span data-stu-id="7a353-555">225</span></span>      |            <span data-ttu-id="7a353-556">RE</span><span class="sxs-lookup"><span data-stu-id="7a353-556">RE</span></span>                  |
|     <span data-ttu-id="7a353-557">246</span><span class="sxs-lookup"><span data-stu-id="7a353-557">246</span></span>      |            <span data-ttu-id="7a353-558">PR</span><span class="sxs-lookup"><span data-stu-id="7a353-558">PR</span></span>                  |

<span data-ttu-id="7a353-559">Die unterstützten Werte für das Feld *country* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7a353-559">To get the supported values for the *country* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="7a353-560">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="7a353-560">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/country
Authorization: Bearer <your access token>
```

<span data-ttu-id="7a353-561">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="7a353-561">The following example shows the response body for this method.</span></span>

```json
{
  "Data": {
    "Country": {
      "1": "US",
      "2": "AU",
      "3": "AT",
      "4": "BE",
      "5": "BR",
      "6": "CA",
      "7": "DK",
      "8": "FI",
      "9": "FR",
      "10": "DE",
      "11": "GR",
      "12": "HK",
      "13": "IN",
      "14": "IE",
      "15": "IT",
      "16": "JP",
      "17": "LU",
      "18": "MX",
      "19": "NL",
      "20": "NZ",
      "21": "NO",
      "22": "PL",
      "23": "PT",
      "24": "SG",
      "25": "ES",
      "26": "SE",
      "27": "CH",
      "28": "TW",
      "29": "GB",
      "30": "RU",
      "31": "CL",
      "32": "CO",
      "33": "CZ",
      "34": "HU",
      "35": "ZA",
      "36": "KR",
      "37": "CN",
      "38": "RO",
      "39": "TR",
      "40": "SK",
      "41": "IL",
      "42": "ID",
      "43": "AR",
      "44": "MY",
      "45": "PH",
      "46": "PE",
      "47": "UA",
      "48": "AE",
      "49": "TH",
      "50": "IQ",
      "51": "VN",
      "52": "CR",
      "53": "VE",
      "54": "QA",
      "55": "SI",
      "56": "BG",
      "57": "LT",
      "58": "RS",
      "59": "HR",
      "60": "BH",
      "61": "LV",
      "62": "EE",
      "63": "IS",
      "64": "KZ",
      "65": "SA",
      "67": "AL",
      "68": "DZ",
      "70": "AO",
      "72": "AM",
      "73": "AZ",
      "74": "BS",
      "75": "BD",
      "76": "BB",
      "77": "BY",
      "81": "BO",
      "82": "BA",
      "83": "BW",
      "87": "KH",
      "88": "CM",
      "94": "CD",
      "95": "CI",
      "96": "CY",
      "99": "DO",
      "100": "EC",
      "101": "EG",
      "102": "SV",
      "107": "FJ",
      "108": "GA",
      "110": "GE",
      "111": "GH",
      "114": "GT",
      "118": "HT",
      "119": "HN",
      "120": "JM",
      "121": "JO",
      "122": "KE",
      "124": "KW",
      "125": "KG",
      "126": "LA",
      "127": "LB",
      "133": "MK",
      "135": "MW",
      "138": "MT",
      "141": "MU",
      "145": "ME",
      "146": "MA",
      "147": "MZ",
      "148": "NA",
      "150": "NP",
      "151": "NI",
      "153": "NG",
      "154": "OM",
      "155": "PK",
      "157": "PA",
      "159": "PY",
      "167": "SN",
      "172": "LK",
      "176": "TZ",
      "180": "TT",
      "181": "TN",
      "184": "UG",
      "185": "UY",
      "186": "UZ",
      "189": "ZM",
      "190": "ZW",
      "219": "MD",
      "224": "PS",
      "225": "RE",
      "246": "PR"
    }
  }
}
```

## <a name="related-topics"></a><span data-ttu-id="7a353-562">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7a353-562">Related topics</span></span>

* [<span data-ttu-id="7a353-563">Ausführen von Anzeigenkampagnen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="7a353-563">Run ad campaigns using Microsoft Store Services</span></span>](run-ad-campaigns-using-windows-store-services.md)
* [<span data-ttu-id="7a353-564">Verwalten von Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="7a353-564">Manage ad campaigns</span></span>](manage-ad-campaigns.md)
* [<span data-ttu-id="7a353-565">Verwalten von Lieferpositionen für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="7a353-565">Manage delivery lines for ad campaigns</span></span>](manage-delivery-lines-for-ad-campaigns.md)
* [<span data-ttu-id="7a353-566">Verwalten von Werbemitteln für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="7a353-566">Manage creatives for ad campaigns</span></span>](manage-creatives-for-ad-campaigns.md)
* [<span data-ttu-id="7a353-567">Abrufen der Leistungsdaten einer Anzeigenkampagne</span><span class="sxs-lookup"><span data-stu-id="7a353-567">Get ad campaign performance data</span></span>](get-ad-campaign-performance-data.md)
