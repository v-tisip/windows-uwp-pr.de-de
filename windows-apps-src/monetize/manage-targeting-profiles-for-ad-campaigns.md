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
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4744287"
---
# <a name="manage-targeting-profiles"></a><span data-ttu-id="1f74e-104">Verwalten von Zielgruppenprofilen</span><span class="sxs-lookup"><span data-stu-id="1f74e-104">Manage targeting profiles</span></span>


<span data-ttu-id="1f74e-105">Verwenden Sie diese Methoden in der Microsoft Store-Werbungs-API, um Benutzer, Regionen und Bestandstypen als Ziele für jede Lieferpositionen einer Werbeanzeigenkampagne auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-105">Use these methods in the Microsoft Store promotions API to select the users, geographies and inventory types that you want to target for each delivery line in a promotional ad campaign.</span></span> <span data-ttu-id="1f74e-106">Zielgruppenprofile können erstellt und über mehrere Lieferpositionen der Übermittlung hinweg wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f74e-106">Targeting profiles can be created and reused across multiple delivery lines.</span></span>

<span data-ttu-id="1f74e-107">Weitere Informationen zu der Beziehung zwischen Zielgruppenprofilen und Anzeigenkampagnen, Lieferpositionen und Werbemitteln finden Sie unter [Anzeigenkampagnen mit Microsoft Store-Diensten ausführen](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span><span class="sxs-lookup"><span data-stu-id="1f74e-107">For more information about the relationship between targeting profiles and ad campaigns, delivery lines, and creatives, see [Run ad campaigns using Microsoft Store services](run-ad-campaigns-using-windows-store-services.md#call-the-windows-store-promotions-api).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f74e-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1f74e-108">Prerequisites</span></span>

<span data-ttu-id="1f74e-109">Zur Verwendung dieser Methoden sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="1f74e-109">To use these methods, you need to first do the following:</span></span>

* <span data-ttu-id="1f74e-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](run-ad-campaigns-using-windows-store-services.md#prerequisites) für die Microsoft Store-Werbungs-API.</span><span class="sxs-lookup"><span data-stu-id="1f74e-110">If you have not done so already, complete all the [prerequisites](run-ad-campaigns-using-windows-store-services.md#prerequisites) for the Microsoft Store promotions API.</span></span>
* <span data-ttu-id="1f74e-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token), das in der Anforderungskopfzeile für diese Methoden verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1f74e-111">[Obtain an Azure AD access token](run-ad-campaigns-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for these methods.</span></span> <span data-ttu-id="1f74e-112">Nach Erhalt eines Zugriffstokens können Sie es 60Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="1f74e-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="1f74e-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-113">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="1f74e-114">Anfordern</span><span class="sxs-lookup"><span data-stu-id="1f74e-114">Request</span></span>

<span data-ttu-id="1f74e-115">Diese Methoden haben die folgenden URIs.</span><span class="sxs-lookup"><span data-stu-id="1f74e-115">These methods have the following URIs.</span></span>

| <span data-ttu-id="1f74e-116">Methodentyp</span><span class="sxs-lookup"><span data-stu-id="1f74e-116">Method type</span></span> | <span data-ttu-id="1f74e-117">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="1f74e-117">Request URI</span></span>                                                      |  <span data-ttu-id="1f74e-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f74e-118">Description</span></span>  |
|--------|------------------------------------------------------------------|---------------|
| <span data-ttu-id="1f74e-119">POST</span><span class="sxs-lookup"><span data-stu-id="1f74e-119">POST</span></span>   | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile``` |  <span data-ttu-id="1f74e-120">Erstellt ein neues Zielgruppenprofil.</span><span class="sxs-lookup"><span data-stu-id="1f74e-120">Creates a new targeting profile.</span></span>  |
| <span data-ttu-id="1f74e-121">PUT</span><span class="sxs-lookup"><span data-stu-id="1f74e-121">PUT</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/{targetingProfileId}``` |  <span data-ttu-id="1f74e-122">Ändert das durch *TargetingProfileId* angegebene Zielgruppenprofil.</span><span class="sxs-lookup"><span data-stu-id="1f74e-122">Edits the targeting profile specified by *targetingProfileId*.</span></span>  |
| <span data-ttu-id="1f74e-123">GET</span><span class="sxs-lookup"><span data-stu-id="1f74e-123">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/{targetingProfileId}``` |  <span data-ttu-id="1f74e-124">Ruft das durch *TargetingProfileId* angegebene Zielgruppenprofil ab.</span><span class="sxs-lookup"><span data-stu-id="1f74e-124">Gets the targeting profile specified by *targetingProfileId*.</span></span>  |


### <a name="header"></a><span data-ttu-id="1f74e-125">Header</span><span class="sxs-lookup"><span data-stu-id="1f74e-125">Header</span></span>

| <span data-ttu-id="1f74e-126">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="1f74e-126">Header</span></span>        | <span data-ttu-id="1f74e-127">Typ</span><span class="sxs-lookup"><span data-stu-id="1f74e-127">Type</span></span>   | <span data-ttu-id="1f74e-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f74e-128">Description</span></span>         |
|---------------|--------|---------------------|
| <span data-ttu-id="1f74e-129">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="1f74e-129">Authorization</span></span> | <span data-ttu-id="1f74e-130">String</span><span class="sxs-lookup"><span data-stu-id="1f74e-130">string</span></span> | <span data-ttu-id="1f74e-131">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1f74e-131">Required.</span></span> <span data-ttu-id="1f74e-132">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-132">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
| <span data-ttu-id="1f74e-133">Tracking-ID</span><span class="sxs-lookup"><span data-stu-id="1f74e-133">Tracking ID</span></span>   | <span data-ttu-id="1f74e-134">GUID</span><span class="sxs-lookup"><span data-stu-id="1f74e-134">GUID</span></span>   | <span data-ttu-id="1f74e-135">Optional.</span><span class="sxs-lookup"><span data-stu-id="1f74e-135">Optional.</span></span> <span data-ttu-id="1f74e-136">Eine ID, die den Abfrageablauf verfolgt.</span><span class="sxs-lookup"><span data-stu-id="1f74e-136">An ID that tracks the call flow.</span></span>                                  |


### <a name="request-body"></a><span data-ttu-id="1f74e-137">Anforderungstext</span><span class="sxs-lookup"><span data-stu-id="1f74e-137">Request body</span></span>

<span data-ttu-id="1f74e-138">Die POST- und PUT-Methoden erfordern einen JSON-Anforderungstext mit den erforderlichen Feldern für ein [Zielgruppenprofil](#targeting-profile)-Objekt und alle zusätzlichen Felder, die Sie festlegen oder ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="1f74e-138">The POST and PUT methods require a JSON request body with the required fields of a [Targeting profile](#targeting-profile) object and any additional fields you want to set or change.</span></span>


### <a name="request-examples"></a><span data-ttu-id="1f74e-139">Anforderungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="1f74e-139">Request examples</span></span>

<span data-ttu-id="1f74e-140">Im folgenden Beispiel wird veranschaulicht, wie die POST-Methode zum Erstellen eines Profils für aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1f74e-140">The following example demonstrates how to call the POST method to create a targeting profile.</span></span>

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

<span data-ttu-id="1f74e-141">Im folgenden Beispiel wird veranschaulicht, wie die GET-Methode zum Abrufen eines Profils für aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1f74e-141">The following example demonstrates how to call the GET method to retrieve a targeting profile.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/targeting-profile/310023951  HTTP/1.1
Authorization: Bearer <your access token>
```

<span/>

## <a name="response"></a><span data-ttu-id="1f74e-142">Antwort</span><span class="sxs-lookup"><span data-stu-id="1f74e-142">Response</span></span>

<span data-ttu-id="1f74e-143">Diese Methoden geben einen JSON-Antworttext mit einem [Zielgruppenprofil](#targeting-profile)-Objekt zurück, das Informationen über das erstellte, aktualisierte bzw. abgerufene Zielgruppenprofil enthält.</span><span class="sxs-lookup"><span data-stu-id="1f74e-143">These methods return a JSON response body with a [Targeting profile](#targeting-profile) object that contains information about the targeting profile that was created, updated, or retrieved.</span></span> <span data-ttu-id="1f74e-144">Das folgende Beispiel zeigt einen Antworttext für diese Methoden.</span><span class="sxs-lookup"><span data-stu-id="1f74e-144">The following example demonstrates a response body for these methods.</span></span>

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

## <a name="targeting-profile-object"></a><span data-ttu-id="1f74e-145">Zielgruppenprofil-Objekt</span><span class="sxs-lookup"><span data-stu-id="1f74e-145">Targeting profile object</span></span>

<span data-ttu-id="1f74e-146">Die Anforderungs- und Antworttexte für diese Methoden enthalten die folgenden Felder.</span><span class="sxs-lookup"><span data-stu-id="1f74e-146">The request and response bodies for these methods contain the following fields.</span></span> <span data-ttu-id="1f74e-147">Die folgende Tabelle zeigt, welche Felder schreibgeschützt sind (d.h. sie können in der PUT-Methode nicht geändert werden) und welche Felder in dem Anforderungstext für die POST-Methode erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="1f74e-147">This table shows which fields are read-only (meaning that they cannot be changed in the PUT method) and which fields are required in the request body for the POST method.</span></span>

| <span data-ttu-id="1f74e-148">Feld</span><span class="sxs-lookup"><span data-stu-id="1f74e-148">Field</span></span>        | <span data-ttu-id="1f74e-149">Typ</span><span class="sxs-lookup"><span data-stu-id="1f74e-149">Type</span></span>   |  <span data-ttu-id="1f74e-150">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f74e-150">Description</span></span>      |  <span data-ttu-id="1f74e-151">Schreibgeschützt</span><span class="sxs-lookup"><span data-stu-id="1f74e-151">Read only</span></span>  | <span data-ttu-id="1f74e-152">Standard</span><span class="sxs-lookup"><span data-stu-id="1f74e-152">Default</span></span>  | <span data-ttu-id="1f74e-153">Erforderlich für POST</span><span class="sxs-lookup"><span data-stu-id="1f74e-153">Required for POST</span></span> |  
|--------------|--------|---------------|------|-------------|------------|
|  <span data-ttu-id="1f74e-154">ID</span><span class="sxs-lookup"><span data-stu-id="1f74e-154">id</span></span>   |  <span data-ttu-id="1f74e-155">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="1f74e-155">integer</span></span>   |  <span data-ttu-id="1f74e-156">Die ID des Zielgruppenprofils.</span><span class="sxs-lookup"><span data-stu-id="1f74e-156">The ID of the targeting profile.</span></span>     |   <span data-ttu-id="1f74e-157">Ja.</span><span class="sxs-lookup"><span data-stu-id="1f74e-157">Yes</span></span>    |       |   <span data-ttu-id="1f74e-158">Nein</span><span class="sxs-lookup"><span data-stu-id="1f74e-158">No</span></span>      |       
|  <span data-ttu-id="1f74e-159">Name</span><span class="sxs-lookup"><span data-stu-id="1f74e-159">name</span></span>   |  <span data-ttu-id="1f74e-160">String</span><span class="sxs-lookup"><span data-stu-id="1f74e-160">string</span></span>   |   <span data-ttu-id="1f74e-161">Der Name des Zielgruppenprofils.</span><span class="sxs-lookup"><span data-stu-id="1f74e-161">The name of the targeting profile.</span></span>    |    <span data-ttu-id="1f74e-162">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-162">No</span></span>   |      |  <span data-ttu-id="1f74e-163">Ja.</span><span class="sxs-lookup"><span data-stu-id="1f74e-163">Yes</span></span>     |       
|  <span data-ttu-id="1f74e-164">targetingType</span><span class="sxs-lookup"><span data-stu-id="1f74e-164">targetingType</span></span>   |  <span data-ttu-id="1f74e-165">String</span><span class="sxs-lookup"><span data-stu-id="1f74e-165">string</span></span>   |  <span data-ttu-id="1f74e-166">Einer der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="1f74e-166">One of the following values:</span></span> <ul><li><span data-ttu-id="1f74e-167">**Automatisch**: Geben Sie diesen Wert an, damit Microsoft das Zielgruppenprofil auf der Grundlage der Einstellungen für Ihre App im Dev Center auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="1f74e-167">**Auto**: Specify this value to allow Microsoft to choose the targeting profile based on the settings for your app in Dev Center.</span></span></li><li><span data-ttu-id="1f74e-168">**Manuell**: Geben Sie diesen Wert an, um Ihr eigenes Zielgruppenprofil zu definieren.</span><span class="sxs-lookup"><span data-stu-id="1f74e-168">**Manual**: Specify this value to define your own targeting profile.</span></span></li></ul>     |  <span data-ttu-id="1f74e-169">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-169">No</span></span>     |  <span data-ttu-id="1f74e-170">Auto</span><span class="sxs-lookup"><span data-stu-id="1f74e-170">Auto</span></span>    |   <span data-ttu-id="1f74e-171">Ja.</span><span class="sxs-lookup"><span data-stu-id="1f74e-171">Yes</span></span>    |       
|  <span data-ttu-id="1f74e-172">Alter</span><span class="sxs-lookup"><span data-stu-id="1f74e-172">age</span></span>   |  <span data-ttu-id="1f74e-173">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-173">array</span></span>   |   <span data-ttu-id="1f74e-174">Eine oder mehrere ganze Zahlen, die den Altersbereich der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-174">One or more integers that identify the age ranges of the users to target.</span></span> <span data-ttu-id="1f74e-175">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Alterswerte](#age-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-175">For a complete list of integers, see [Age values](#age-values) in this article.</span></span>    |    <span data-ttu-id="1f74e-176">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-176">No</span></span>    |  <span data-ttu-id="1f74e-177">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-177">null</span></span>    |     <span data-ttu-id="1f74e-178">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-178">No</span></span>    |       
|  <span data-ttu-id="1f74e-179">Geschlecht</span><span class="sxs-lookup"><span data-stu-id="1f74e-179">gender</span></span>   |  <span data-ttu-id="1f74e-180">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-180">array</span></span>   |  <span data-ttu-id="1f74e-181">Eine oder mehrere Ganzzahlen, die das Geschlecht der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-181">One or more integers that identify the genders of the users to target.</span></span> <span data-ttu-id="1f74e-182">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Geschlechtswerte](#gender-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-182">For a complete list of integers, see [Gender values](#gender-values) in this article.</span></span>       |  <span data-ttu-id="1f74e-183">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-183">No</span></span>    |  <span data-ttu-id="1f74e-184">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-184">null</span></span>    |     <span data-ttu-id="1f74e-185">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-185">No</span></span>    |       
|  <span data-ttu-id="1f74e-186">Land</span><span class="sxs-lookup"><span data-stu-id="1f74e-186">country</span></span>   |  <span data-ttu-id="1f74e-187">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-187">array</span></span>   |  <span data-ttu-id="1f74e-188">Eine oder mehrere ganze Zahlen, die die Ländercodes der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-188">One or more integers that identify the country codes of the users to target.</span></span> <span data-ttu-id="1f74e-189">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Ländercodewerte](#country-code-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-189">For a complete list of integers, see [Country code values](#country-code-values) in this article.</span></span>    |  <span data-ttu-id="1f74e-190">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-190">No</span></span>    |  <span data-ttu-id="1f74e-191">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-191">null</span></span>   |      <span data-ttu-id="1f74e-192">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-192">No</span></span>   |       
|  <span data-ttu-id="1f74e-193">osVersion</span><span class="sxs-lookup"><span data-stu-id="1f74e-193">osVersion</span></span>   |  <span data-ttu-id="1f74e-194">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-194">array</span></span>   |   <span data-ttu-id="1f74e-195">Eine oder mehrere ganze Zahlen, die die Betriebssystemversionen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-195">One or more integers that identify the OS versions of the users to target.</span></span> <span data-ttu-id="1f74e-196">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Betriebssystemversionswerte](#osversion-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-196">For a complete list of integers, see [OS version values](#osversion-values) in this article.</span></span>     |   <span data-ttu-id="1f74e-197">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-197">No</span></span>    |  <span data-ttu-id="1f74e-198">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-198">null</span></span>   |     <span data-ttu-id="1f74e-199">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-199">No</span></span>    |       
|  <span data-ttu-id="1f74e-200">deviceType</span><span class="sxs-lookup"><span data-stu-id="1f74e-200">deviceType</span></span>   | <span data-ttu-id="1f74e-201">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-201">array</span></span>    |  <span data-ttu-id="1f74e-202">Eine oder mehrere ganze Zahlen, die die Gerätetypen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-202">One or more integers that identify the device types of the users to target.</span></span> <span data-ttu-id="1f74e-203">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Gerätetypenwerte](#devicetype-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-203">For a complete list of integers, see [Device type values](#devicetype-values) in this article.</span></span>       |   <span data-ttu-id="1f74e-204">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-204">No</span></span>    |  <span data-ttu-id="1f74e-205">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-205">null</span></span>    |    <span data-ttu-id="1f74e-206">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-206">No</span></span>     |       
|  <span data-ttu-id="1f74e-207">supplyType</span><span class="sxs-lookup"><span data-stu-id="1f74e-207">supplyType</span></span>   |  <span data-ttu-id="1f74e-208">Array</span><span class="sxs-lookup"><span data-stu-id="1f74e-208">array</span></span>   |  <span data-ttu-id="1f74e-209">Eine oder mehrere ganze Zahlen, die den Bestandstyp angeben, in dem die Anzeigen der Kampagne angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-209">One or more integers that identify the type of inventory where the campaign's ads will be shown.</span></span> <span data-ttu-id="1f74e-210">Eine vollständige Liste von ganzen Zahlen finden Sie unter [Bestandstypenwerte](#supplytype-values) in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="1f74e-210">For a complete list of integers, see [Supply type values](#supplytype-values) in this article.</span></span>      |   <span data-ttu-id="1f74e-211">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-211">No</span></span>    |  <span data-ttu-id="1f74e-212">Null</span><span class="sxs-lookup"><span data-stu-id="1f74e-212">null</span></span>   |     <span data-ttu-id="1f74e-213">Nein.</span><span class="sxs-lookup"><span data-stu-id="1f74e-213">No</span></span>    |   |  


<span id="age-values"/>

### <a name="age-values"></a><span data-ttu-id="1f74e-214">Alterswerte</span><span class="sxs-lookup"><span data-stu-id="1f74e-214">Age values</span></span>

<span data-ttu-id="1f74e-215">Das Feld *Alter* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die den Altersbereich der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-215">The *age* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the age ranges of the users to target.</span></span>

|  <span data-ttu-id="1f74e-216">Ganzzahliger Wert für Feld *Alter*</span><span class="sxs-lookup"><span data-stu-id="1f74e-216">Integer value for *age* field</span></span>  |  <span data-ttu-id="1f74e-217">Entsprechender Altersbereich</span><span class="sxs-lookup"><span data-stu-id="1f74e-217">Corresponding age range</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="1f74e-218">651</span><span class="sxs-lookup"><span data-stu-id="1f74e-218">651</span></span>     |            <span data-ttu-id="1f74e-219">13 bis 17</span><span class="sxs-lookup"><span data-stu-id="1f74e-219">13 to 17</span></span>             |
|     <span data-ttu-id="1f74e-220">652</span><span class="sxs-lookup"><span data-stu-id="1f74e-220">652</span></span>     |           <span data-ttu-id="1f74e-221">18 bis 24</span><span class="sxs-lookup"><span data-stu-id="1f74e-221">18 to 24</span></span>             |
|     <span data-ttu-id="1f74e-222">653</span><span class="sxs-lookup"><span data-stu-id="1f74e-222">653</span></span>     |            <span data-ttu-id="1f74e-223">25 bis 34</span><span class="sxs-lookup"><span data-stu-id="1f74e-223">25 to 34</span></span>             |
|     <span data-ttu-id="1f74e-224">654</span><span class="sxs-lookup"><span data-stu-id="1f74e-224">654</span></span>     |            <span data-ttu-id="1f74e-225">35 bis 49</span><span class="sxs-lookup"><span data-stu-id="1f74e-225">35 to 49</span></span>             |
|     <span data-ttu-id="1f74e-226">655</span><span class="sxs-lookup"><span data-stu-id="1f74e-226">655</span></span>     |            <span data-ttu-id="1f74e-227">50 und älter</span><span class="sxs-lookup"><span data-stu-id="1f74e-227">50 and above</span></span>             |

<span data-ttu-id="1f74e-228">Die unterstützten Werte für das Feld *age* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-228">To get the supported values for the *age* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-229">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-229">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/age
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-230">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-230">The following example shows the response body for this method.</span></span>

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

### <a name="gender-values"></a><span data-ttu-id="1f74e-231">Geschlechtswerte</span><span class="sxs-lookup"><span data-stu-id="1f74e-231">Gender values</span></span>

<span data-ttu-id="1f74e-232">Das Feld *Geschlecht* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die das Geschlecht der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-232">The *gender* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the genders of the users to target.</span></span>

|  <span data-ttu-id="1f74e-233">Ganzzahliger Wert für das Feld *gender*</span><span class="sxs-lookup"><span data-stu-id="1f74e-233">Integer value for *gender* field</span></span>  |  <span data-ttu-id="1f74e-234">Entsprechendes Geschlecht</span><span class="sxs-lookup"><span data-stu-id="1f74e-234">Corresponding gender</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="1f74e-235">700</span><span class="sxs-lookup"><span data-stu-id="1f74e-235">700</span></span>     |            <span data-ttu-id="1f74e-236">Männlich</span><span class="sxs-lookup"><span data-stu-id="1f74e-236">Male</span></span>             |
|     <span data-ttu-id="1f74e-237">701</span><span class="sxs-lookup"><span data-stu-id="1f74e-237">701</span></span>     |           <span data-ttu-id="1f74e-238">Weiblich</span><span class="sxs-lookup"><span data-stu-id="1f74e-238">Female</span></span>             |

<span data-ttu-id="1f74e-239">Die unterstützten Werte für das Feld *gender* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-239">To get the supported values for the *gender* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-240">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-240">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/gender
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-241">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-241">The following example shows the response body for this method.</span></span>

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

### <a name="os-version-values"></a><span data-ttu-id="1f74e-242">Werte für Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="1f74e-242">OS version values</span></span>

<span data-ttu-id="1f74e-243">Das Feld *Betriebssystemversion* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die Betriebssystemversion der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-243">The *osVersion* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the OS versions of the users to target.</span></span>

|  <span data-ttu-id="1f74e-244">Ganzzahliger Wert für das Feld *osVersion*</span><span class="sxs-lookup"><span data-stu-id="1f74e-244">Integer value for *osVersion* field</span></span>  |  <span data-ttu-id="1f74e-245">Entsprechende Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="1f74e-245">Corresponding OS version</span></span>  |  
|---------------------------------|---------------------------|
|     <span data-ttu-id="1f74e-246">500</span><span class="sxs-lookup"><span data-stu-id="1f74e-246">500</span></span>     |            <span data-ttu-id="1f74e-247">Windows Phone7</span><span class="sxs-lookup"><span data-stu-id="1f74e-247">Windows Phone 7</span></span>             |
|     <span data-ttu-id="1f74e-248">501</span><span class="sxs-lookup"><span data-stu-id="1f74e-248">501</span></span>     |           <span data-ttu-id="1f74e-249">Windows Phone7.1</span><span class="sxs-lookup"><span data-stu-id="1f74e-249">Windows Phone 7.1</span></span>             |
|     <span data-ttu-id="1f74e-250">502</span><span class="sxs-lookup"><span data-stu-id="1f74e-250">502</span></span>     |           <span data-ttu-id="1f74e-251">Windows Phone7.5</span><span class="sxs-lookup"><span data-stu-id="1f74e-251">Windows Phone 7.5</span></span>             |
|     <span data-ttu-id="1f74e-252">503</span><span class="sxs-lookup"><span data-stu-id="1f74e-252">503</span></span>     |           <span data-ttu-id="1f74e-253">Windows Phone7.8</span><span class="sxs-lookup"><span data-stu-id="1f74e-253">Windows Phone 7.8</span></span>             |
|     <span data-ttu-id="1f74e-254">504</span><span class="sxs-lookup"><span data-stu-id="1f74e-254">504</span></span>     |           <span data-ttu-id="1f74e-255">Windows Phone8.0</span><span class="sxs-lookup"><span data-stu-id="1f74e-255">Windows Phone 8.0</span></span>             |
|     <span data-ttu-id="1f74e-256">505</span><span class="sxs-lookup"><span data-stu-id="1f74e-256">505</span></span>     |           <span data-ttu-id="1f74e-257">Windows Phone8.1</span><span class="sxs-lookup"><span data-stu-id="1f74e-257">Windows Phone 8.1</span></span>             |
|     <span data-ttu-id="1f74e-258">506</span><span class="sxs-lookup"><span data-stu-id="1f74e-258">506</span></span>     |           <span data-ttu-id="1f74e-259">Windows8.0</span><span class="sxs-lookup"><span data-stu-id="1f74e-259">Windows 8.0</span></span>             |
|     <span data-ttu-id="1f74e-260">507</span><span class="sxs-lookup"><span data-stu-id="1f74e-260">507</span></span>     |           <span data-ttu-id="1f74e-261">Windows8.1</span><span class="sxs-lookup"><span data-stu-id="1f74e-261">Windows 8.1</span></span>             |
|     <span data-ttu-id="1f74e-262">508</span><span class="sxs-lookup"><span data-stu-id="1f74e-262">508</span></span>     |           <span data-ttu-id="1f74e-263">Windows10</span><span class="sxs-lookup"><span data-stu-id="1f74e-263">Windows 10</span></span>             |
|     <span data-ttu-id="1f74e-264">509</span><span class="sxs-lookup"><span data-stu-id="1f74e-264">509</span></span>     |           <span data-ttu-id="1f74e-265">Windows10Mobile</span><span class="sxs-lookup"><span data-stu-id="1f74e-265">Windows 10 Mobile</span></span>             |

<span data-ttu-id="1f74e-266">Die unterstützten Werte für das Feld *osVersion* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-266">To get the supported values for the *osVersion* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-267">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-267">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/osversion
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-268">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-268">The following example shows the response body for this method.</span></span>

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

### <a name="device-type-values"></a><span data-ttu-id="1f74e-269">Werte für Gerätetyp</span><span class="sxs-lookup"><span data-stu-id="1f74e-269">Device type values</span></span>

<span data-ttu-id="1f74e-270">Das Feld *deviceType* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die Gerätetypen der Benutzer in der Zielgruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="1f74e-270">The *deviceType* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the device types of the users to target.</span></span>

|  <span data-ttu-id="1f74e-271">Ganzzahliger Wert für das Feld *deviceType*</span><span class="sxs-lookup"><span data-stu-id="1f74e-271">Integer value for *deviceType* field</span></span>  |  <span data-ttu-id="1f74e-272">Entsprechender Gerätetyp</span><span class="sxs-lookup"><span data-stu-id="1f74e-272">Corresponding device type</span></span>  |  <span data-ttu-id="1f74e-273">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f74e-273">Description</span></span>  |
|---------------------------------|---------------------------|---------------------------|
|     <span data-ttu-id="1f74e-274">710</span><span class="sxs-lookup"><span data-stu-id="1f74e-274">710</span></span>     |  <span data-ttu-id="1f74e-275">Windows</span><span class="sxs-lookup"><span data-stu-id="1f74e-275">Windows</span></span>   |  <span data-ttu-id="1f74e-276">Hierbei handelt es sich um Geräte mit einer Desktop-Version von Windows10 oder Windows8.x.</span><span class="sxs-lookup"><span data-stu-id="1f74e-276">This represents devices running a desktop version of Windows 10 or Windows 8.x.</span></span>  |
|     <span data-ttu-id="1f74e-277">711</span><span class="sxs-lookup"><span data-stu-id="1f74e-277">711</span></span>     |  <span data-ttu-id="1f74e-278">Phone</span><span class="sxs-lookup"><span data-stu-id="1f74e-278">Phone</span></span>     |  <span data-ttu-id="1f74e-279">Hierbei handelt es sich um Geräte unter Windows10 Mobile, Windows Phone8.x oder Windows Phone7.x.</span><span class="sxs-lookup"><span data-stu-id="1f74e-279">This represents devices running Windows 10 Mobile, Windows Phone 8.x, or Windows Phone 7.x.</span></span>

<span data-ttu-id="1f74e-280">Die unterstützten Werte für das Feld *deviceType* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-280">To get the supported values for the *deviceType* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-281">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-281">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/devicetype
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-282">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-282">The following example shows the response body for this method.</span></span>

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

### <a name="supply-type-values"></a><span data-ttu-id="1f74e-283">Werte für Bestandstypen</span><span class="sxs-lookup"><span data-stu-id="1f74e-283">Supply type values</span></span>

<span data-ttu-id="1f74e-284">Das Feld *supplyType* im Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die den Bestandstyp angeben, in dem die Kampagnenanzeigen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1f74e-284">The *supplyType* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the type of inventory where the campaign's ads will be shown.</span></span>

|  <span data-ttu-id="1f74e-285">Ganzzahliger Wert für das Feld *SupplyType*</span><span class="sxs-lookup"><span data-stu-id="1f74e-285">Integer value for *supplyType* field</span></span>  |  <span data-ttu-id="1f74e-286">Entsprechender Bestandstyp</span><span class="sxs-lookup"><span data-stu-id="1f74e-286">Corresponding supply type</span></span>  |  <span data-ttu-id="1f74e-287">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1f74e-287">Description</span></span>  |
|---------------------------------|---------------------------|---------------------------|
|     <span data-ttu-id="1f74e-288">11470</span><span class="sxs-lookup"><span data-stu-id="1f74e-288">11470</span></span>     |  <span data-ttu-id="1f74e-289">App</span><span class="sxs-lookup"><span data-stu-id="1f74e-289">App</span></span>        |  <span data-ttu-id="1f74e-290">Dies bezieht sich auf Anzeigen, die ausschließlich in Apps angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1f74e-290">This refers to ads that appear in apps only.</span></span>  |
|     <span data-ttu-id="1f74e-291">11471</span><span class="sxs-lookup"><span data-stu-id="1f74e-291">11471</span></span>     |  <span data-ttu-id="1f74e-292">Universelle</span><span class="sxs-lookup"><span data-stu-id="1f74e-292">Universal</span></span>        |  <span data-ttu-id="1f74e-293">Dies bezieht sich auf Anzeigen, die in Apps, im Internet und auf anderen Anzeigeflächen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1f74e-293">This refers to ads that appear in apps, on the Web, and on and other display surfaces.</span></span>  |

<span data-ttu-id="1f74e-294">Die unterstützten Werte für das Feld *supplyType* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-294">To get the supported values for the *supplyType* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-295">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-295">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/supplytype
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-296">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-296">The following example shows the response body for this method.</span></span>

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

### <a name="country-code-values"></a><span data-ttu-id="1f74e-297">Werte für Ländercode</span><span class="sxs-lookup"><span data-stu-id="1f74e-297">Country code values</span></span>

<span data-ttu-id="1f74e-298">Das Feld *country* in dem Objekt [TargetingProfile](#targeting-profile) enthält eine oder mehrere der folgenden Ganzzahlen, die die [ISO3166-1-Alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Ländercodes der Zielgruppenbenutzer identifizieren.</span><span class="sxs-lookup"><span data-stu-id="1f74e-298">The *country* field in the [TargetingProfile](#targeting-profile) object contains one or more of the following integers that identify the [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country codes of the users to target.</span></span>

|  <span data-ttu-id="1f74e-299">Ganzzahliger Wert für das Feld *country*</span><span class="sxs-lookup"><span data-stu-id="1f74e-299">Integer value for *country* field</span></span>  |  <span data-ttu-id="1f74e-300">Entsprechender Ländercode</span><span class="sxs-lookup"><span data-stu-id="1f74e-300">Corresponding country code</span></span>  |  
|-------------------------------------|------------------------------|
|     <span data-ttu-id="1f74e-301">1</span><span class="sxs-lookup"><span data-stu-id="1f74e-301">1</span></span>      |            <span data-ttu-id="1f74e-302">USA</span><span class="sxs-lookup"><span data-stu-id="1f74e-302">US</span></span>                  |
|     <span data-ttu-id="1f74e-303">2</span><span class="sxs-lookup"><span data-stu-id="1f74e-303">2</span></span>      |            <span data-ttu-id="1f74e-304">AU</span><span class="sxs-lookup"><span data-stu-id="1f74e-304">AU</span></span>                  |
|     <span data-ttu-id="1f74e-305">3</span><span class="sxs-lookup"><span data-stu-id="1f74e-305">3</span></span>      |            <span data-ttu-id="1f74e-306">AT</span><span class="sxs-lookup"><span data-stu-id="1f74e-306">AT</span></span>                  |
|     <span data-ttu-id="1f74e-307">4</span><span class="sxs-lookup"><span data-stu-id="1f74e-307">4</span></span>      |            <span data-ttu-id="1f74e-308">BE</span><span class="sxs-lookup"><span data-stu-id="1f74e-308">BE</span></span>                  |
|     <span data-ttu-id="1f74e-309">5</span><span class="sxs-lookup"><span data-stu-id="1f74e-309">5</span></span>      |            <span data-ttu-id="1f74e-310">BR</span><span class="sxs-lookup"><span data-stu-id="1f74e-310">BR</span></span>                  |
|     <span data-ttu-id="1f74e-311">6</span><span class="sxs-lookup"><span data-stu-id="1f74e-311">6</span></span>      |            <span data-ttu-id="1f74e-312">CA</span><span class="sxs-lookup"><span data-stu-id="1f74e-312">CA</span></span>                  |
|     <span data-ttu-id="1f74e-313">7</span><span class="sxs-lookup"><span data-stu-id="1f74e-313">7</span></span>      |            <span data-ttu-id="1f74e-314">DK</span><span class="sxs-lookup"><span data-stu-id="1f74e-314">DK</span></span>                  |
|     <span data-ttu-id="1f74e-315">8</span><span class="sxs-lookup"><span data-stu-id="1f74e-315">8</span></span>      |            <span data-ttu-id="1f74e-316">FI</span><span class="sxs-lookup"><span data-stu-id="1f74e-316">FI</span></span>                  |
|     <span data-ttu-id="1f74e-317">9</span><span class="sxs-lookup"><span data-stu-id="1f74e-317">9</span></span>      |            <span data-ttu-id="1f74e-318">FR</span><span class="sxs-lookup"><span data-stu-id="1f74e-318">FR</span></span>                  |
|     <span data-ttu-id="1f74e-319">10</span><span class="sxs-lookup"><span data-stu-id="1f74e-319">10</span></span>      |            <span data-ttu-id="1f74e-320">DE</span><span class="sxs-lookup"><span data-stu-id="1f74e-320">DE</span></span>                  |
|     <span data-ttu-id="1f74e-321">11</span><span class="sxs-lookup"><span data-stu-id="1f74e-321">11</span></span>      |            <span data-ttu-id="1f74e-322">GR</span><span class="sxs-lookup"><span data-stu-id="1f74e-322">GR</span></span>                  |
|     <span data-ttu-id="1f74e-323">12</span><span class="sxs-lookup"><span data-stu-id="1f74e-323">12</span></span>      |            <span data-ttu-id="1f74e-324">HK</span><span class="sxs-lookup"><span data-stu-id="1f74e-324">HK</span></span>                  |
|     <span data-ttu-id="1f74e-325">13</span><span class="sxs-lookup"><span data-stu-id="1f74e-325">13</span></span>      |            <span data-ttu-id="1f74e-326">IN</span><span class="sxs-lookup"><span data-stu-id="1f74e-326">IN</span></span>                  |
|     <span data-ttu-id="1f74e-327">14</span><span class="sxs-lookup"><span data-stu-id="1f74e-327">14</span></span>      |            <span data-ttu-id="1f74e-328">IE</span><span class="sxs-lookup"><span data-stu-id="1f74e-328">IE</span></span>                  |
|     <span data-ttu-id="1f74e-329">15</span><span class="sxs-lookup"><span data-stu-id="1f74e-329">15</span></span>      |            <span data-ttu-id="1f74e-330">IT</span><span class="sxs-lookup"><span data-stu-id="1f74e-330">IT</span></span>                  |
|     <span data-ttu-id="1f74e-331">16</span><span class="sxs-lookup"><span data-stu-id="1f74e-331">16</span></span>      |            <span data-ttu-id="1f74e-332">JP</span><span class="sxs-lookup"><span data-stu-id="1f74e-332">JP</span></span>                  |
|     <span data-ttu-id="1f74e-333">17</span><span class="sxs-lookup"><span data-stu-id="1f74e-333">17</span></span>      |            <span data-ttu-id="1f74e-334">LU</span><span class="sxs-lookup"><span data-stu-id="1f74e-334">LU</span></span>                  |
|     <span data-ttu-id="1f74e-335">18</span><span class="sxs-lookup"><span data-stu-id="1f74e-335">18</span></span>      |            <span data-ttu-id="1f74e-336">MX</span><span class="sxs-lookup"><span data-stu-id="1f74e-336">MX</span></span>                  |
|     <span data-ttu-id="1f74e-337">19</span><span class="sxs-lookup"><span data-stu-id="1f74e-337">19</span></span>      |            <span data-ttu-id="1f74e-338">NL</span><span class="sxs-lookup"><span data-stu-id="1f74e-338">NL</span></span>                  |
|     <span data-ttu-id="1f74e-339">20</span><span class="sxs-lookup"><span data-stu-id="1f74e-339">20</span></span>      |            <span data-ttu-id="1f74e-340">NZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-340">NZ</span></span>                  |
|     <span data-ttu-id="1f74e-341">21</span><span class="sxs-lookup"><span data-stu-id="1f74e-341">21</span></span>      |            <span data-ttu-id="1f74e-342">NO</span><span class="sxs-lookup"><span data-stu-id="1f74e-342">NO</span></span>                  |
|     <span data-ttu-id="1f74e-343">22</span><span class="sxs-lookup"><span data-stu-id="1f74e-343">22</span></span>      |            <span data-ttu-id="1f74e-344">PL</span><span class="sxs-lookup"><span data-stu-id="1f74e-344">PL</span></span>                  |
|     <span data-ttu-id="1f74e-345">23</span><span class="sxs-lookup"><span data-stu-id="1f74e-345">23</span></span>      |            <span data-ttu-id="1f74e-346">PT</span><span class="sxs-lookup"><span data-stu-id="1f74e-346">PT</span></span>                  |
|     <span data-ttu-id="1f74e-347">24</span><span class="sxs-lookup"><span data-stu-id="1f74e-347">24</span></span>      |            <span data-ttu-id="1f74e-348">SG</span><span class="sxs-lookup"><span data-stu-id="1f74e-348">SG</span></span>                  |
|     <span data-ttu-id="1f74e-349">25</span><span class="sxs-lookup"><span data-stu-id="1f74e-349">25</span></span>      |            <span data-ttu-id="1f74e-350">ES</span><span class="sxs-lookup"><span data-stu-id="1f74e-350">ES</span></span>                  |
|     <span data-ttu-id="1f74e-351">26</span><span class="sxs-lookup"><span data-stu-id="1f74e-351">26</span></span>      |            <span data-ttu-id="1f74e-352">SE</span><span class="sxs-lookup"><span data-stu-id="1f74e-352">SE</span></span>                  |
|     <span data-ttu-id="1f74e-353">27</span><span class="sxs-lookup"><span data-stu-id="1f74e-353">27</span></span>      |            <span data-ttu-id="1f74e-354">CH</span><span class="sxs-lookup"><span data-stu-id="1f74e-354">CH</span></span>                  |
|     <span data-ttu-id="1f74e-355">28</span><span class="sxs-lookup"><span data-stu-id="1f74e-355">28</span></span>      |            <span data-ttu-id="1f74e-356">TW</span><span class="sxs-lookup"><span data-stu-id="1f74e-356">TW</span></span>                  |
|     <span data-ttu-id="1f74e-357">29</span><span class="sxs-lookup"><span data-stu-id="1f74e-357">29</span></span>      |            <span data-ttu-id="1f74e-358">GB</span><span class="sxs-lookup"><span data-stu-id="1f74e-358">GB</span></span>                  |
|     <span data-ttu-id="1f74e-359">30</span><span class="sxs-lookup"><span data-stu-id="1f74e-359">30</span></span>      |            <span data-ttu-id="1f74e-360">RU</span><span class="sxs-lookup"><span data-stu-id="1f74e-360">RU</span></span>                  |
|     <span data-ttu-id="1f74e-361">31</span><span class="sxs-lookup"><span data-stu-id="1f74e-361">31</span></span>      |            <span data-ttu-id="1f74e-362">CL</span><span class="sxs-lookup"><span data-stu-id="1f74e-362">CL</span></span>                  |
|     <span data-ttu-id="1f74e-363">32</span><span class="sxs-lookup"><span data-stu-id="1f74e-363">32</span></span>      |            <span data-ttu-id="1f74e-364">CO</span><span class="sxs-lookup"><span data-stu-id="1f74e-364">CO</span></span>                  |
|     <span data-ttu-id="1f74e-365">33</span><span class="sxs-lookup"><span data-stu-id="1f74e-365">33</span></span>      |            <span data-ttu-id="1f74e-366">CZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-366">CZ</span></span>                  |
|     <span data-ttu-id="1f74e-367">34</span><span class="sxs-lookup"><span data-stu-id="1f74e-367">34</span></span>      |            <span data-ttu-id="1f74e-368">HU</span><span class="sxs-lookup"><span data-stu-id="1f74e-368">HU</span></span>                  |
|     <span data-ttu-id="1f74e-369">35</span><span class="sxs-lookup"><span data-stu-id="1f74e-369">35</span></span>      |            <span data-ttu-id="1f74e-370">ZA</span><span class="sxs-lookup"><span data-stu-id="1f74e-370">ZA</span></span>                  |
|     <span data-ttu-id="1f74e-371">36</span><span class="sxs-lookup"><span data-stu-id="1f74e-371">36</span></span>      |            <span data-ttu-id="1f74e-372">KR</span><span class="sxs-lookup"><span data-stu-id="1f74e-372">KR</span></span>                  |
|     <span data-ttu-id="1f74e-373">37</span><span class="sxs-lookup"><span data-stu-id="1f74e-373">37</span></span>      |            <span data-ttu-id="1f74e-374">CN</span><span class="sxs-lookup"><span data-stu-id="1f74e-374">CN</span></span>                  |
|     <span data-ttu-id="1f74e-375">38</span><span class="sxs-lookup"><span data-stu-id="1f74e-375">38</span></span>      |            <span data-ttu-id="1f74e-376">RO</span><span class="sxs-lookup"><span data-stu-id="1f74e-376">RO</span></span>                  |
|     <span data-ttu-id="1f74e-377">39</span><span class="sxs-lookup"><span data-stu-id="1f74e-377">39</span></span>      |            <span data-ttu-id="1f74e-378">TR</span><span class="sxs-lookup"><span data-stu-id="1f74e-378">TR</span></span>                  |
|     <span data-ttu-id="1f74e-379">40</span><span class="sxs-lookup"><span data-stu-id="1f74e-379">40</span></span>      |            <span data-ttu-id="1f74e-380">SK</span><span class="sxs-lookup"><span data-stu-id="1f74e-380">SK</span></span>                  |
|     <span data-ttu-id="1f74e-381">41</span><span class="sxs-lookup"><span data-stu-id="1f74e-381">41</span></span>      |            <span data-ttu-id="1f74e-382">IL</span><span class="sxs-lookup"><span data-stu-id="1f74e-382">IL</span></span>                  |
|     <span data-ttu-id="1f74e-383">42</span><span class="sxs-lookup"><span data-stu-id="1f74e-383">42</span></span>      |            <span data-ttu-id="1f74e-384">ID</span><span class="sxs-lookup"><span data-stu-id="1f74e-384">ID</span></span>                  |
|     <span data-ttu-id="1f74e-385">43</span><span class="sxs-lookup"><span data-stu-id="1f74e-385">43</span></span>      |            <span data-ttu-id="1f74e-386">AR</span><span class="sxs-lookup"><span data-stu-id="1f74e-386">AR</span></span>                  |
|     <span data-ttu-id="1f74e-387">44</span><span class="sxs-lookup"><span data-stu-id="1f74e-387">44</span></span>      |            <span data-ttu-id="1f74e-388">MY</span><span class="sxs-lookup"><span data-stu-id="1f74e-388">MY</span></span>                  |
|     <span data-ttu-id="1f74e-389">45</span><span class="sxs-lookup"><span data-stu-id="1f74e-389">45</span></span>      |            <span data-ttu-id="1f74e-390">PH</span><span class="sxs-lookup"><span data-stu-id="1f74e-390">PH</span></span>                  |
|     <span data-ttu-id="1f74e-391">46</span><span class="sxs-lookup"><span data-stu-id="1f74e-391">46</span></span>      |            <span data-ttu-id="1f74e-392">PE</span><span class="sxs-lookup"><span data-stu-id="1f74e-392">PE</span></span>                  |
|     <span data-ttu-id="1f74e-393">47</span><span class="sxs-lookup"><span data-stu-id="1f74e-393">47</span></span>      |            <span data-ttu-id="1f74e-394">UA</span><span class="sxs-lookup"><span data-stu-id="1f74e-394">UA</span></span>                  |
|     <span data-ttu-id="1f74e-395">48</span><span class="sxs-lookup"><span data-stu-id="1f74e-395">48</span></span>      |            <span data-ttu-id="1f74e-396">AE</span><span class="sxs-lookup"><span data-stu-id="1f74e-396">AE</span></span>                  |
|     <span data-ttu-id="1f74e-397">49</span><span class="sxs-lookup"><span data-stu-id="1f74e-397">49</span></span>      |            <span data-ttu-id="1f74e-398">TH</span><span class="sxs-lookup"><span data-stu-id="1f74e-398">TH</span></span>                  |
|     <span data-ttu-id="1f74e-399">50</span><span class="sxs-lookup"><span data-stu-id="1f74e-399">50</span></span>      |            <span data-ttu-id="1f74e-400">IQ</span><span class="sxs-lookup"><span data-stu-id="1f74e-400">IQ</span></span>                  |
|     <span data-ttu-id="1f74e-401">51</span><span class="sxs-lookup"><span data-stu-id="1f74e-401">51</span></span>      |            <span data-ttu-id="1f74e-402">VN</span><span class="sxs-lookup"><span data-stu-id="1f74e-402">VN</span></span>                  |
|     <span data-ttu-id="1f74e-403">52</span><span class="sxs-lookup"><span data-stu-id="1f74e-403">52</span></span>      |            <span data-ttu-id="1f74e-404">CR</span><span class="sxs-lookup"><span data-stu-id="1f74e-404">CR</span></span>                  |
|     <span data-ttu-id="1f74e-405">53</span><span class="sxs-lookup"><span data-stu-id="1f74e-405">53</span></span>      |            <span data-ttu-id="1f74e-406">VE</span><span class="sxs-lookup"><span data-stu-id="1f74e-406">VE</span></span>                  |
|     <span data-ttu-id="1f74e-407">54</span><span class="sxs-lookup"><span data-stu-id="1f74e-407">54</span></span>      |            <span data-ttu-id="1f74e-408">QA</span><span class="sxs-lookup"><span data-stu-id="1f74e-408">QA</span></span>                  |
|     <span data-ttu-id="1f74e-409">55</span><span class="sxs-lookup"><span data-stu-id="1f74e-409">55</span></span>      |            <span data-ttu-id="1f74e-410">SI</span><span class="sxs-lookup"><span data-stu-id="1f74e-410">SI</span></span>                  |
|     <span data-ttu-id="1f74e-411">56</span><span class="sxs-lookup"><span data-stu-id="1f74e-411">56</span></span>      |            <span data-ttu-id="1f74e-412">BG</span><span class="sxs-lookup"><span data-stu-id="1f74e-412">BG</span></span>                  |
|     <span data-ttu-id="1f74e-413">57</span><span class="sxs-lookup"><span data-stu-id="1f74e-413">57</span></span>      |            <span data-ttu-id="1f74e-414">LT</span><span class="sxs-lookup"><span data-stu-id="1f74e-414">LT</span></span>                  |
|     <span data-ttu-id="1f74e-415">58</span><span class="sxs-lookup"><span data-stu-id="1f74e-415">58</span></span>      |            <span data-ttu-id="1f74e-416">RS</span><span class="sxs-lookup"><span data-stu-id="1f74e-416">RS</span></span>                  |
|     <span data-ttu-id="1f74e-417">59</span><span class="sxs-lookup"><span data-stu-id="1f74e-417">59</span></span>      |            <span data-ttu-id="1f74e-418">HR</span><span class="sxs-lookup"><span data-stu-id="1f74e-418">HR</span></span>                  |
|     <span data-ttu-id="1f74e-419">60</span><span class="sxs-lookup"><span data-stu-id="1f74e-419">60</span></span>      |            <span data-ttu-id="1f74e-420">HR</span><span class="sxs-lookup"><span data-stu-id="1f74e-420">HR</span></span>                  |
|     <span data-ttu-id="1f74e-421">61</span><span class="sxs-lookup"><span data-stu-id="1f74e-421">61</span></span>      |            <span data-ttu-id="1f74e-422">LV</span><span class="sxs-lookup"><span data-stu-id="1f74e-422">LV</span></span>                  |
|     <span data-ttu-id="1f74e-423">62</span><span class="sxs-lookup"><span data-stu-id="1f74e-423">62</span></span>      |            <span data-ttu-id="1f74e-424">EE</span><span class="sxs-lookup"><span data-stu-id="1f74e-424">EE</span></span>                  |
|     <span data-ttu-id="1f74e-425">63</span><span class="sxs-lookup"><span data-stu-id="1f74e-425">63</span></span>      |            <span data-ttu-id="1f74e-426">IS</span><span class="sxs-lookup"><span data-stu-id="1f74e-426">IS</span></span>                  |
|     <span data-ttu-id="1f74e-427">64</span><span class="sxs-lookup"><span data-stu-id="1f74e-427">64</span></span>      |            <span data-ttu-id="1f74e-428">KZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-428">KZ</span></span>                  |
|     <span data-ttu-id="1f74e-429">65</span><span class="sxs-lookup"><span data-stu-id="1f74e-429">65</span></span>      |            <span data-ttu-id="1f74e-430">SA</span><span class="sxs-lookup"><span data-stu-id="1f74e-430">SA</span></span>                  |
|     <span data-ttu-id="1f74e-431">67</span><span class="sxs-lookup"><span data-stu-id="1f74e-431">67</span></span>      |            <span data-ttu-id="1f74e-432">AL</span><span class="sxs-lookup"><span data-stu-id="1f74e-432">AL</span></span>                  |
|     <span data-ttu-id="1f74e-433">68</span><span class="sxs-lookup"><span data-stu-id="1f74e-433">68</span></span>      |            <span data-ttu-id="1f74e-434">DZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-434">DZ</span></span>                  |
|     <span data-ttu-id="1f74e-435">70</span><span class="sxs-lookup"><span data-stu-id="1f74e-435">70</span></span>      |            <span data-ttu-id="1f74e-436">AO</span><span class="sxs-lookup"><span data-stu-id="1f74e-436">AO</span></span>                  |
|     <span data-ttu-id="1f74e-437">72</span><span class="sxs-lookup"><span data-stu-id="1f74e-437">72</span></span>      |            <span data-ttu-id="1f74e-438">AM</span><span class="sxs-lookup"><span data-stu-id="1f74e-438">AM</span></span>                  |
|     <span data-ttu-id="1f74e-439">73</span><span class="sxs-lookup"><span data-stu-id="1f74e-439">73</span></span>      |            <span data-ttu-id="1f74e-440">AZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-440">AZ</span></span>                  |
|     <span data-ttu-id="1f74e-441">74</span><span class="sxs-lookup"><span data-stu-id="1f74e-441">74</span></span>      |            <span data-ttu-id="1f74e-442">BS</span><span class="sxs-lookup"><span data-stu-id="1f74e-442">BS</span></span>                  |
|     <span data-ttu-id="1f74e-443">75</span><span class="sxs-lookup"><span data-stu-id="1f74e-443">75</span></span>      |            <span data-ttu-id="1f74e-444">BD</span><span class="sxs-lookup"><span data-stu-id="1f74e-444">BD</span></span>                  |
|     <span data-ttu-id="1f74e-445">76</span><span class="sxs-lookup"><span data-stu-id="1f74e-445">76</span></span>      |            <span data-ttu-id="1f74e-446">BB</span><span class="sxs-lookup"><span data-stu-id="1f74e-446">BB</span></span>                  |
|     <span data-ttu-id="1f74e-447">77</span><span class="sxs-lookup"><span data-stu-id="1f74e-447">77</span></span>      |            <span data-ttu-id="1f74e-448">BY</span><span class="sxs-lookup"><span data-stu-id="1f74e-448">BY</span></span>                  |
|     <span data-ttu-id="1f74e-449">81</span><span class="sxs-lookup"><span data-stu-id="1f74e-449">81</span></span>      |            <span data-ttu-id="1f74e-450">BO</span><span class="sxs-lookup"><span data-stu-id="1f74e-450">BO</span></span>                  |
|     <span data-ttu-id="1f74e-451">82</span><span class="sxs-lookup"><span data-stu-id="1f74e-451">82</span></span>      |            <span data-ttu-id="1f74e-452">BA</span><span class="sxs-lookup"><span data-stu-id="1f74e-452">BA</span></span>                  |
|     <span data-ttu-id="1f74e-453">83</span><span class="sxs-lookup"><span data-stu-id="1f74e-453">83</span></span>      |            <span data-ttu-id="1f74e-454">BW</span><span class="sxs-lookup"><span data-stu-id="1f74e-454">BW</span></span>                  |
|     <span data-ttu-id="1f74e-455">87</span><span class="sxs-lookup"><span data-stu-id="1f74e-455">87</span></span>      |            <span data-ttu-id="1f74e-456">KH</span><span class="sxs-lookup"><span data-stu-id="1f74e-456">KH</span></span>                  |
|     <span data-ttu-id="1f74e-457">88</span><span class="sxs-lookup"><span data-stu-id="1f74e-457">88</span></span>      |            <span data-ttu-id="1f74e-458">CM</span><span class="sxs-lookup"><span data-stu-id="1f74e-458">CM</span></span>                  |
|     <span data-ttu-id="1f74e-459">94</span><span class="sxs-lookup"><span data-stu-id="1f74e-459">94</span></span>      |            <span data-ttu-id="1f74e-460">CD</span><span class="sxs-lookup"><span data-stu-id="1f74e-460">CD</span></span>                  |
|     <span data-ttu-id="1f74e-461">95</span><span class="sxs-lookup"><span data-stu-id="1f74e-461">95</span></span>      |            <span data-ttu-id="1f74e-462">CI</span><span class="sxs-lookup"><span data-stu-id="1f74e-462">CI</span></span>                  |
|     <span data-ttu-id="1f74e-463">96</span><span class="sxs-lookup"><span data-stu-id="1f74e-463">96</span></span>      |            <span data-ttu-id="1f74e-464">CY</span><span class="sxs-lookup"><span data-stu-id="1f74e-464">CY</span></span>                  |
|     <span data-ttu-id="1f74e-465">99</span><span class="sxs-lookup"><span data-stu-id="1f74e-465">99</span></span>      |            <span data-ttu-id="1f74e-466">DO</span><span class="sxs-lookup"><span data-stu-id="1f74e-466">DO</span></span>                  |
|     <span data-ttu-id="1f74e-467">100</span><span class="sxs-lookup"><span data-stu-id="1f74e-467">100</span></span>      |            <span data-ttu-id="1f74e-468">EC</span><span class="sxs-lookup"><span data-stu-id="1f74e-468">EC</span></span>                  |
|     <span data-ttu-id="1f74e-469">101</span><span class="sxs-lookup"><span data-stu-id="1f74e-469">101</span></span>      |            <span data-ttu-id="1f74e-470">EG</span><span class="sxs-lookup"><span data-stu-id="1f74e-470">EG</span></span>                  |
|     <span data-ttu-id="1f74e-471">102</span><span class="sxs-lookup"><span data-stu-id="1f74e-471">102</span></span>      |            <span data-ttu-id="1f74e-472">SV</span><span class="sxs-lookup"><span data-stu-id="1f74e-472">SV</span></span>                  |
|     <span data-ttu-id="1f74e-473">107</span><span class="sxs-lookup"><span data-stu-id="1f74e-473">107</span></span>      |            <span data-ttu-id="1f74e-474">FJ</span><span class="sxs-lookup"><span data-stu-id="1f74e-474">FJ</span></span>                  |
|     <span data-ttu-id="1f74e-475">108</span><span class="sxs-lookup"><span data-stu-id="1f74e-475">108</span></span>      |            <span data-ttu-id="1f74e-476">GA</span><span class="sxs-lookup"><span data-stu-id="1f74e-476">GA</span></span>                  |
|     <span data-ttu-id="1f74e-477">110</span><span class="sxs-lookup"><span data-stu-id="1f74e-477">110</span></span>      |            <span data-ttu-id="1f74e-478">GE</span><span class="sxs-lookup"><span data-stu-id="1f74e-478">GE</span></span>                  |
|     <span data-ttu-id="1f74e-479">111</span><span class="sxs-lookup"><span data-stu-id="1f74e-479">111</span></span>      |            <span data-ttu-id="1f74e-480">GH</span><span class="sxs-lookup"><span data-stu-id="1f74e-480">GH</span></span>                  |
|     <span data-ttu-id="1f74e-481">114</span><span class="sxs-lookup"><span data-stu-id="1f74e-481">114</span></span>      |            <span data-ttu-id="1f74e-482">GT</span><span class="sxs-lookup"><span data-stu-id="1f74e-482">GT</span></span>                  |
|     <span data-ttu-id="1f74e-483">118</span><span class="sxs-lookup"><span data-stu-id="1f74e-483">118</span></span>      |            <span data-ttu-id="1f74e-484">HT</span><span class="sxs-lookup"><span data-stu-id="1f74e-484">HT</span></span>                  |
|     <span data-ttu-id="1f74e-485">119</span><span class="sxs-lookup"><span data-stu-id="1f74e-485">119</span></span>      |            <span data-ttu-id="1f74e-486">HN</span><span class="sxs-lookup"><span data-stu-id="1f74e-486">HN</span></span>                  |
|     <span data-ttu-id="1f74e-487">120</span><span class="sxs-lookup"><span data-stu-id="1f74e-487">120</span></span>      |            <span data-ttu-id="1f74e-488">JM</span><span class="sxs-lookup"><span data-stu-id="1f74e-488">JM</span></span>                  |
|     <span data-ttu-id="1f74e-489">121</span><span class="sxs-lookup"><span data-stu-id="1f74e-489">121</span></span>      |            <span data-ttu-id="1f74e-490">JO</span><span class="sxs-lookup"><span data-stu-id="1f74e-490">JO</span></span>                  |
|     <span data-ttu-id="1f74e-491">122</span><span class="sxs-lookup"><span data-stu-id="1f74e-491">122</span></span>      |            <span data-ttu-id="1f74e-492">KE</span><span class="sxs-lookup"><span data-stu-id="1f74e-492">KE</span></span>                  |
|     <span data-ttu-id="1f74e-493">124</span><span class="sxs-lookup"><span data-stu-id="1f74e-493">124</span></span>      |            <span data-ttu-id="1f74e-494">KW</span><span class="sxs-lookup"><span data-stu-id="1f74e-494">KW</span></span>                  |
|     <span data-ttu-id="1f74e-495">125</span><span class="sxs-lookup"><span data-stu-id="1f74e-495">125</span></span>      |            <span data-ttu-id="1f74e-496">KG</span><span class="sxs-lookup"><span data-stu-id="1f74e-496">KG</span></span>                  |
|     <span data-ttu-id="1f74e-497">126</span><span class="sxs-lookup"><span data-stu-id="1f74e-497">126</span></span>      |            <span data-ttu-id="1f74e-498">LA</span><span class="sxs-lookup"><span data-stu-id="1f74e-498">LA</span></span>                  |
|     <span data-ttu-id="1f74e-499">127 Zeichen lang sein</span><span class="sxs-lookup"><span data-stu-id="1f74e-499">127</span></span>      |            <span data-ttu-id="1f74e-500">LB</span><span class="sxs-lookup"><span data-stu-id="1f74e-500">LB</span></span>                  |
|     <span data-ttu-id="1f74e-501">133</span><span class="sxs-lookup"><span data-stu-id="1f74e-501">133</span></span>      |            <span data-ttu-id="1f74e-502">MK</span><span class="sxs-lookup"><span data-stu-id="1f74e-502">MK</span></span>                  |
|     <span data-ttu-id="1f74e-503">135</span><span class="sxs-lookup"><span data-stu-id="1f74e-503">135</span></span>      |            <span data-ttu-id="1f74e-504">MW</span><span class="sxs-lookup"><span data-stu-id="1f74e-504">MW</span></span>                  |
|     <span data-ttu-id="1f74e-505">138</span><span class="sxs-lookup"><span data-stu-id="1f74e-505">138</span></span>      |            <span data-ttu-id="1f74e-506">MT</span><span class="sxs-lookup"><span data-stu-id="1f74e-506">MT</span></span>                  |
|     <span data-ttu-id="1f74e-507">141</span><span class="sxs-lookup"><span data-stu-id="1f74e-507">141</span></span>      |            <span data-ttu-id="1f74e-508">MU</span><span class="sxs-lookup"><span data-stu-id="1f74e-508">MU</span></span>                  |
|     <span data-ttu-id="1f74e-509">145</span><span class="sxs-lookup"><span data-stu-id="1f74e-509">145</span></span>      |            <span data-ttu-id="1f74e-510">ME</span><span class="sxs-lookup"><span data-stu-id="1f74e-510">ME</span></span>                  |
|     <span data-ttu-id="1f74e-511">146</span><span class="sxs-lookup"><span data-stu-id="1f74e-511">146</span></span>      |            <span data-ttu-id="1f74e-512">MA</span><span class="sxs-lookup"><span data-stu-id="1f74e-512">MA</span></span>                  |
|     <span data-ttu-id="1f74e-513">147</span><span class="sxs-lookup"><span data-stu-id="1f74e-513">147</span></span>      |            <span data-ttu-id="1f74e-514">MZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-514">MZ</span></span>                  |
|     <span data-ttu-id="1f74e-515">148</span><span class="sxs-lookup"><span data-stu-id="1f74e-515">148</span></span>      |            <span data-ttu-id="1f74e-516">NA</span><span class="sxs-lookup"><span data-stu-id="1f74e-516">NA</span></span>                  |
|     <span data-ttu-id="1f74e-517">150</span><span class="sxs-lookup"><span data-stu-id="1f74e-517">150</span></span>      |            <span data-ttu-id="1f74e-518">NP</span><span class="sxs-lookup"><span data-stu-id="1f74e-518">NP</span></span>                  |
|     <span data-ttu-id="1f74e-519">151.</span><span class="sxs-lookup"><span data-stu-id="1f74e-519">151</span></span>      |            <span data-ttu-id="1f74e-520">NI</span><span class="sxs-lookup"><span data-stu-id="1f74e-520">NI</span></span>                  |
|     <span data-ttu-id="1f74e-521">153</span><span class="sxs-lookup"><span data-stu-id="1f74e-521">153</span></span>      |            <span data-ttu-id="1f74e-522">NG</span><span class="sxs-lookup"><span data-stu-id="1f74e-522">NG</span></span>                  |
|     <span data-ttu-id="1f74e-523">154</span><span class="sxs-lookup"><span data-stu-id="1f74e-523">154</span></span>      |            <span data-ttu-id="1f74e-524">OM</span><span class="sxs-lookup"><span data-stu-id="1f74e-524">OM</span></span>                  |
|     <span data-ttu-id="1f74e-525">155</span><span class="sxs-lookup"><span data-stu-id="1f74e-525">155</span></span>      |            <span data-ttu-id="1f74e-526">PK</span><span class="sxs-lookup"><span data-stu-id="1f74e-526">PK</span></span>                  |
|     <span data-ttu-id="1f74e-527">157</span><span class="sxs-lookup"><span data-stu-id="1f74e-527">157</span></span>      |            <span data-ttu-id="1f74e-528">PA</span><span class="sxs-lookup"><span data-stu-id="1f74e-528">PA</span></span>                  |
|     <span data-ttu-id="1f74e-529">159</span><span class="sxs-lookup"><span data-stu-id="1f74e-529">159</span></span>      |            <span data-ttu-id="1f74e-530">PY</span><span class="sxs-lookup"><span data-stu-id="1f74e-530">PY</span></span>                  |
|     <span data-ttu-id="1f74e-531">167</span><span class="sxs-lookup"><span data-stu-id="1f74e-531">167</span></span>      |            <span data-ttu-id="1f74e-532">SN</span><span class="sxs-lookup"><span data-stu-id="1f74e-532">SN</span></span>                  |
|     <span data-ttu-id="1f74e-533">172</span><span class="sxs-lookup"><span data-stu-id="1f74e-533">172</span></span>      |            <span data-ttu-id="1f74e-534">LK</span><span class="sxs-lookup"><span data-stu-id="1f74e-534">LK</span></span>                  |
|     <span data-ttu-id="1f74e-535">176</span><span class="sxs-lookup"><span data-stu-id="1f74e-535">176</span></span>      |            <span data-ttu-id="1f74e-536">TZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-536">TZ</span></span>                  |
|     <span data-ttu-id="1f74e-537">180</span><span class="sxs-lookup"><span data-stu-id="1f74e-537">180</span></span>      |            <span data-ttu-id="1f74e-538">TT</span><span class="sxs-lookup"><span data-stu-id="1f74e-538">TT</span></span>                  |
|     <span data-ttu-id="1f74e-539">181</span><span class="sxs-lookup"><span data-stu-id="1f74e-539">181</span></span>      |            <span data-ttu-id="1f74e-540">TN</span><span class="sxs-lookup"><span data-stu-id="1f74e-540">TN</span></span>                  |
|     <span data-ttu-id="1f74e-541">184</span><span class="sxs-lookup"><span data-stu-id="1f74e-541">184</span></span>      |            <span data-ttu-id="1f74e-542">UG</span><span class="sxs-lookup"><span data-stu-id="1f74e-542">UG</span></span>                  |
|     <span data-ttu-id="1f74e-543">185</span><span class="sxs-lookup"><span data-stu-id="1f74e-543">185</span></span>      |            <span data-ttu-id="1f74e-544">UY</span><span class="sxs-lookup"><span data-stu-id="1f74e-544">UY</span></span>                  |
|     <span data-ttu-id="1f74e-545">186</span><span class="sxs-lookup"><span data-stu-id="1f74e-545">186</span></span>      |            <span data-ttu-id="1f74e-546">UZ</span><span class="sxs-lookup"><span data-stu-id="1f74e-546">UZ</span></span>                  |
|     <span data-ttu-id="1f74e-547">189</span><span class="sxs-lookup"><span data-stu-id="1f74e-547">189</span></span>      |            <span data-ttu-id="1f74e-548">ZM</span><span class="sxs-lookup"><span data-stu-id="1f74e-548">ZM</span></span>                  |
|     <span data-ttu-id="1f74e-549">190</span><span class="sxs-lookup"><span data-stu-id="1f74e-549">190</span></span>      |            <span data-ttu-id="1f74e-550">ZW</span><span class="sxs-lookup"><span data-stu-id="1f74e-550">ZW</span></span>                  |
|     <span data-ttu-id="1f74e-551">219</span><span class="sxs-lookup"><span data-stu-id="1f74e-551">219</span></span>      |            <span data-ttu-id="1f74e-552">MD</span><span class="sxs-lookup"><span data-stu-id="1f74e-552">MD</span></span>                  |
|     <span data-ttu-id="1f74e-553">224</span><span class="sxs-lookup"><span data-stu-id="1f74e-553">224</span></span>      |            <span data-ttu-id="1f74e-554">PS</span><span class="sxs-lookup"><span data-stu-id="1f74e-554">PS</span></span>                  |
|     <span data-ttu-id="1f74e-555">225</span><span class="sxs-lookup"><span data-stu-id="1f74e-555">225</span></span>      |            <span data-ttu-id="1f74e-556">RE</span><span class="sxs-lookup"><span data-stu-id="1f74e-556">RE</span></span>                  |
|     <span data-ttu-id="1f74e-557">246</span><span class="sxs-lookup"><span data-stu-id="1f74e-557">246</span></span>      |            <span data-ttu-id="1f74e-558">PR</span><span class="sxs-lookup"><span data-stu-id="1f74e-558">PR</span></span>                  |

<span data-ttu-id="1f74e-559">Die unterstützten Werte für das Feld *country* können Sie programmgesteuert erhalten, indem Sie die folgende GET-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1f74e-559">To get the supported values for the *country* field programmatically, you can call the following GET method.</span></span>  <span data-ttu-id="1f74e-560">Für die Kopfzeile ```Authorization``` übergeben Sie Ihr Azure AD-Zugriffstoken in Form eines **Bearer** &lt;*-Token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="1f74e-560">For the ```Authorization``` header, pass your Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span>

```json
GET https://manage.devcenter.microsoft.com/v1.0/my/promotion/reference/country
Authorization: Bearer <your access token>
```

<span data-ttu-id="1f74e-561">Mit dem folgenden Codebeispiel wird der Antworttext für diese Methode veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f74e-561">The following example shows the response body for this method.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="1f74e-562">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1f74e-562">Related topics</span></span>

* [<span data-ttu-id="1f74e-563">Ausführen von Anzeigenkampagnen mit Microsoft Store-Diensten</span><span class="sxs-lookup"><span data-stu-id="1f74e-563">Run ad campaigns using Microsoft Store Services</span></span>](run-ad-campaigns-using-windows-store-services.md)
* [<span data-ttu-id="1f74e-564">Verwalten von Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="1f74e-564">Manage ad campaigns</span></span>](manage-ad-campaigns.md)
* [<span data-ttu-id="1f74e-565">Verwalten von Lieferpositionen für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="1f74e-565">Manage delivery lines for ad campaigns</span></span>](manage-delivery-lines-for-ad-campaigns.md)
* [<span data-ttu-id="1f74e-566">Verwalten von Werbemitteln für Anzeigenkampagnen</span><span class="sxs-lookup"><span data-stu-id="1f74e-566">Manage creatives for ad campaigns</span></span>](manage-creatives-for-ad-campaigns.md)
* [<span data-ttu-id="1f74e-567">Abrufen der Leistungsdaten einer Anzeigenkampagne</span><span class="sxs-lookup"><span data-stu-id="1f74e-567">Get ad campaign performance data</span></span>](get-ad-campaign-performance-data.md)
