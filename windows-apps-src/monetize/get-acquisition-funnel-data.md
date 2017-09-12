---
author: mcleanbyron
description: "Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die Erwerbstrichterdaten für eine Anwendung während eines bestimmten Zeitraums und andere optionale Filter abzurufen."
title: Abrufen von App-Erwerbstrichterdaten
ms.author: mcleans
ms.date: 08/04/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Store-Dienste, Windows Store-Analyse-API, Kauf, Trichter
ms.openlocfilehash: 5e09504eb7ed787fcf330a5cf92027eed5f6bc59
ms.sourcegitcommit: 2b436dc5e5681b8884e0531ee303f851a3e3ccf2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2017
---
# <a name="get-app-acquisition-funnel-data"></a><span data-ttu-id="54ef0-104">Abrufen von App-Erwerbstrichterdaten</span><span class="sxs-lookup"><span data-stu-id="54ef0-104">Get app acquisition funnel data</span></span>

<span data-ttu-id="54ef0-105">Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die Erwerbstrichterdaten für eine Anwendung während eines bestimmten Zeitraums und andere optionale Filter abzurufen.</span><span class="sxs-lookup"><span data-stu-id="54ef0-105">Use this method in the Windows Store analytics API to get acquisition funnel data for an application during a given date range and other optional filters.</span></span> <span data-ttu-id="54ef0-106">Diese Informationen sind auch im [Bericht „Käufe“](../publish/acquisitions-report.md#acquisition-funnel) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="54ef0-106">This information is also available in the [Acquisitions report](../publish/acquisitions-report.md#acquisition-funnel) in the Windows Dev Center dashboard.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54ef0-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="54ef0-107">Prerequisites</span></span>


<span data-ttu-id="54ef0-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="54ef0-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="54ef0-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="54ef0-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Windows Store analytics API.</span></span>
* <span data-ttu-id="54ef0-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="54ef0-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="54ef0-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="54ef0-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="54ef0-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="54ef0-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="54ef0-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="54ef0-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="54ef0-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="54ef0-114">Request syntax</span></span>

| <span data-ttu-id="54ef0-115">Methode</span><span class="sxs-lookup"><span data-stu-id="54ef0-115">Method</span></span> | <span data-ttu-id="54ef0-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="54ef0-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="54ef0-117">GET</span><span class="sxs-lookup"><span data-stu-id="54ef0-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel``` |

<span/>

### <a name="request-header"></a><span data-ttu-id="54ef0-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="54ef0-118">Request header</span></span>

| <span data-ttu-id="54ef0-119">Header</span><span class="sxs-lookup"><span data-stu-id="54ef0-119">Header</span></span>        | <span data-ttu-id="54ef0-120">Typ</span><span class="sxs-lookup"><span data-stu-id="54ef0-120">Type</span></span>   | <span data-ttu-id="54ef0-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54ef0-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="54ef0-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="54ef0-122">Authorization</span></span> | <span data-ttu-id="54ef0-123">String</span><span class="sxs-lookup"><span data-stu-id="54ef0-123">string</span></span> | <span data-ttu-id="54ef0-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54ef0-124">Required.</span></span> <span data-ttu-id="54ef0-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="54ef0-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/> 

### <a name="request-parameters"></a><span data-ttu-id="54ef0-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="54ef0-126">Request parameters</span></span>

| <span data-ttu-id="54ef0-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="54ef0-127">Parameter</span></span>        | <span data-ttu-id="54ef0-128">Typ</span><span class="sxs-lookup"><span data-stu-id="54ef0-128">Type</span></span>   |  <span data-ttu-id="54ef0-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54ef0-129">Description</span></span>      |  <span data-ttu-id="54ef0-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="54ef0-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="54ef0-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="54ef0-131">applicationId</span></span> | <span data-ttu-id="54ef0-132">string</span><span class="sxs-lookup"><span data-stu-id="54ef0-132">string</span></span> | <span data-ttu-id="54ef0-133">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, für die Sie die Erwerbstrichterdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="54ef0-133">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to retrieve acquisition funnel data.</span></span> <span data-ttu-id="54ef0-134">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="54ef0-134">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="54ef0-135">Ja</span><span class="sxs-lookup"><span data-stu-id="54ef0-135">Yes</span></span>  |
| <span data-ttu-id="54ef0-136">startDate</span><span class="sxs-lookup"><span data-stu-id="54ef0-136">startDate</span></span> | <span data-ttu-id="54ef0-137">date</span><span class="sxs-lookup"><span data-stu-id="54ef0-137">date</span></span> | <span data-ttu-id="54ef0-138">Das Startdatum im Datumsbereich der Erwerbstrichterdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="54ef0-138">The start date in the date range of acquisition funnel data to retrieve.</span></span> <span data-ttu-id="54ef0-139">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="54ef0-139">The default is the current date.</span></span> |  <span data-ttu-id="54ef0-140">Nein</span><span class="sxs-lookup"><span data-stu-id="54ef0-140">No</span></span>  |
| <span data-ttu-id="54ef0-141">endDate</span><span class="sxs-lookup"><span data-stu-id="54ef0-141">endDate</span></span> | <span data-ttu-id="54ef0-142">date</span><span class="sxs-lookup"><span data-stu-id="54ef0-142">date</span></span> | <span data-ttu-id="54ef0-143">Das Enddatum im Datumsbereich der Erwerbstrichterdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="54ef0-143">The end date in the date range of acquisition funnel data to retrieve.</span></span> <span data-ttu-id="54ef0-144">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="54ef0-144">The default is the current date.</span></span> |  <span data-ttu-id="54ef0-145">Nein</span><span class="sxs-lookup"><span data-stu-id="54ef0-145">No</span></span>  |
| <span data-ttu-id="54ef0-146">filter</span><span class="sxs-lookup"><span data-stu-id="54ef0-146">filter</span></span> | <span data-ttu-id="54ef0-147">string</span><span class="sxs-lookup"><span data-stu-id="54ef0-147">string</span></span>  | <span data-ttu-id="54ef0-148">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="54ef0-148">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="54ef0-149">Weitere Informationen finden Sie unten im Abschnitt [Filterfelder](#filter-fields).</span><span class="sxs-lookup"><span data-stu-id="54ef0-149">For more information, see the [filter fields](#filter-fields) section below.</span></span> | <span data-ttu-id="54ef0-150">Nein</span><span class="sxs-lookup"><span data-stu-id="54ef0-150">No</span></span>   |

<span/>
 
### <a name="filter-fields"></a><span data-ttu-id="54ef0-151">Filterfelder</span><span class="sxs-lookup"><span data-stu-id="54ef0-151">Filter fields</span></span>

<span data-ttu-id="54ef0-152">Der Parameter *filter* der Anforderung enthält mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="54ef0-152">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="54ef0-153">Jede Anweisung enthält ein Feld und einen Wert, das/der mit den Operatoren **eq** oder **ne** verknüpft ist. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="54ef0-153">Each statement contains a field and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span>

<span data-ttu-id="54ef0-154">Die folgenden Filterfelder werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="54ef0-154">The following filter fields are supported.</span></span> <span data-ttu-id="54ef0-155">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="54ef0-155">String values must be surrounded by single quotes in the *filter* parameter.</span></span>

| <span data-ttu-id="54ef0-156">Felder</span><span class="sxs-lookup"><span data-stu-id="54ef0-156">Fields</span></span>        |  <span data-ttu-id="54ef0-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54ef0-157">Description</span></span>        |
|---------------|-----------------|
| <span data-ttu-id="54ef0-158">campaignId</span><span class="sxs-lookup"><span data-stu-id="54ef0-158">campaignId</span></span> | <span data-ttu-id="54ef0-159">Die ID-Zeichenfolge für einen [Werbekampagne für benutzerdefinierte Apps](../publish/create-a-custom-app-promotion-campaign.md), die dem Kauf zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="54ef0-159">The ID string for a [custom app promotion campaign](../publish/create-a-custom-app-promotion-campaign.md) that is associated with the acquisition.</span></span> |
| <span data-ttu-id="54ef0-160">market</span><span class="sxs-lookup"><span data-stu-id="54ef0-160">market</span></span> | <span data-ttu-id="54ef0-161">Eine Zeichenfolge, die den ISO 3166-Ländercode des Markts enthält, in dem der Kauf erfolgte.</span><span class="sxs-lookup"><span data-stu-id="54ef0-161">A string that contains the ISO 3166 country code of the market where the acquisition occurred.</span></span> |
| <span data-ttu-id="54ef0-162">deviceType</span><span class="sxs-lookup"><span data-stu-id="54ef0-162">deviceType</span></span> | <span data-ttu-id="54ef0-163">Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, auf der Kauf aufgetreten ist:</span><span class="sxs-lookup"><span data-stu-id="54ef0-163">One of the following strings that specifies the device type on which the acquisition occurred:</span></span><ul><li><strong><span data-ttu-id="54ef0-164">PC</span><span class="sxs-lookup"><span data-stu-id="54ef0-164">PC</span></span></strong></li><li><strong><span data-ttu-id="54ef0-165">Phone</span><span class="sxs-lookup"><span data-stu-id="54ef0-165">Phone</span></span></strong></li><li><strong><span data-ttu-id="54ef0-166">Console</span><span class="sxs-lookup"><span data-stu-id="54ef0-166">Console</span></span></strong></li><li><strong><span data-ttu-id="54ef0-167">IoT</span><span class="sxs-lookup"><span data-stu-id="54ef0-167">IoT</span></span></strong></li><li><strong><span data-ttu-id="54ef0-168">Holographic</span><span class="sxs-lookup"><span data-stu-id="54ef0-168">Holographic</span></span></strong></li><li><strong><span data-ttu-id="54ef0-169">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="54ef0-169">Unknown</span></span></strong></li></ul> |
| <span data-ttu-id="54ef0-170">ageGroup</span><span class="sxs-lookup"><span data-stu-id="54ef0-170">ageGroup</span></span> | <span data-ttu-id="54ef0-171">Eine der folgenden Zeichenfolgen, die den Typ der Age-Group des Benutzer angibt, der den Kauf abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="54ef0-171">One of the following strings that specifies the age group of the user who completed the acquisition:</span></span><ul><li><strong><span data-ttu-id="54ef0-172">0 – 17</span><span class="sxs-lookup"><span data-stu-id="54ef0-172">0 – 17</span></span></strong></li><li><strong><span data-ttu-id="54ef0-173">18 – 24</span><span class="sxs-lookup"><span data-stu-id="54ef0-173">18 – 24</span></span></strong></li><li><strong><span data-ttu-id="54ef0-174">25 – 34</span><span class="sxs-lookup"><span data-stu-id="54ef0-174">25 – 34</span></span></strong></li><li><strong><span data-ttu-id="54ef0-175">35 – 49</span><span class="sxs-lookup"><span data-stu-id="54ef0-175">35 – 49</span></span></strong></li><li><strong><span data-ttu-id="54ef0-176">50 oder mehr</span><span class="sxs-lookup"><span data-stu-id="54ef0-176">50 or over</span></span></strong></li><li><strong><span data-ttu-id="54ef0-177">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="54ef0-177">Unknown</span></span></strong></li></ul> |
| <span data-ttu-id="54ef0-178">gender</span><span class="sxs-lookup"><span data-stu-id="54ef0-178">gender</span></span> | <span data-ttu-id="54ef0-179">Eine der folgenden Zeichenfolgen, die das Geschlecht des Benutzer angibt, der den Kauf abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="54ef0-179">One of the following strings that specifies the gender of the user who completed the acquisition:</span></span><ul><li><strong><span data-ttu-id="54ef0-180">M</span><span class="sxs-lookup"><span data-stu-id="54ef0-180">M</span></span></strong></li><li><strong><span data-ttu-id="54ef0-181">F</span><span class="sxs-lookup"><span data-stu-id="54ef0-181">F</span></span></strong></li><li><strong><span data-ttu-id="54ef0-182">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="54ef0-182">Unknown</span></span></strong></li></ul> |


<span data-ttu-id="54ef0-183">Dies sind einige Beispielparameter für *Filter*.</span><span class="sxs-lookup"><span data-stu-id="54ef0-183">Here are some example *filter* parameters.</span></span>

```filter=market eq 'US' and gender eq 'M'```

```filter=(market ne 'US') and (gender ne 'Unknown') and (gender ne 'M') and (market ne 'NO') and (ageGroup ne '50 or over' or ageGroup ne ‘0 - 17’)```

<span/> 

### <a name="request-example"></a><span data-ttu-id="54ef0-184">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="54ef0-184">Request example</span></span>

<span data-ttu-id="54ef0-185">Das folgende Beispiel zeigt verschiedene Anforderungen für den Abruf von Erwerbstrichterdaten für Apps.</span><span class="sxs-lookup"><span data-stu-id="54ef0-185">The following example demonstrates several requests for getting acquisition funnel data for an app.</span></span> <span data-ttu-id="54ef0-186">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="54ef0-186">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel?applicationId=9NBLGGGZ5QDR&startDate=1/1/2017&endDate=2/1/2017  HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel?applicationId=9NBLGGGZ5QDR&startDate=8/1/2016&endDate=8/31/2016&filter=market eq 'US' and gender eq 'm'  HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="54ef0-187">Antwort</span><span class="sxs-lookup"><span data-stu-id="54ef0-187">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="54ef0-188">Antworttext</span><span class="sxs-lookup"><span data-stu-id="54ef0-188">Response body</span></span>

| <span data-ttu-id="54ef0-189">Wert</span><span class="sxs-lookup"><span data-stu-id="54ef0-189">Value</span></span>      | <span data-ttu-id="54ef0-190">Typ</span><span class="sxs-lookup"><span data-stu-id="54ef0-190">Type</span></span>   | <span data-ttu-id="54ef0-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54ef0-191">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="54ef0-192">Wert</span><span class="sxs-lookup"><span data-stu-id="54ef0-192">Value</span></span>      | <span data-ttu-id="54ef0-193">Array</span><span class="sxs-lookup"><span data-stu-id="54ef0-193">array</span></span>  | <span data-ttu-id="54ef0-194">Ein Array von Objekten, die Erwerbstrichterdaten für die App enthalten.</span><span class="sxs-lookup"><span data-stu-id="54ef0-194">An array of objects that contain acquisition funnel data for the app.</span></span> <span data-ttu-id="54ef0-195">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Trichterwerte](#funnel-values).</span><span class="sxs-lookup"><span data-stu-id="54ef0-195">For more information about the data in each object, see the [funnel values](#funnel-values) section below.</span></span>                                                                                                                      |
| <span data-ttu-id="54ef0-196">TotalCount</span><span class="sxs-lookup"><span data-stu-id="54ef0-196">TotalCount</span></span> | <span data-ttu-id="54ef0-197">int</span><span class="sxs-lookup"><span data-stu-id="54ef0-197">int</span></span>    | <span data-ttu-id="54ef0-198">Die Gesamtanzahl der Objekte im *Value* Array.</span><span class="sxs-lookup"><span data-stu-id="54ef0-198">The total number of objects in the *Value* array.</span></span>                         |
<span/>
 
### <a name="funnel-values"></a><span data-ttu-id="54ef0-199">Trichterwerte</span><span class="sxs-lookup"><span data-stu-id="54ef0-199">Funnel values</span></span>

<span data-ttu-id="54ef0-200">Objekte im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="54ef0-200">Objects in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="54ef0-201">Wert</span><span class="sxs-lookup"><span data-stu-id="54ef0-201">Value</span></span>               | <span data-ttu-id="54ef0-202">Typ</span><span class="sxs-lookup"><span data-stu-id="54ef0-202">Type</span></span>   | <span data-ttu-id="54ef0-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="54ef0-203">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="54ef0-204">MetricType</span><span class="sxs-lookup"><span data-stu-id="54ef0-204">MetricType</span></span>                | <span data-ttu-id="54ef0-205">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="54ef0-205">string</span></span> | <span data-ttu-id="54ef0-206">Eine der folgenden Zeichenfolgen, die angibt, die [Trichter Datentyp](../publish/acquisitions-report.md#acquisition-funnel), die in diesem Objekt enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="54ef0-206">One of the following strings that specifies the [type of funnel data](../publish/acquisitions-report.md#acquisition-funnel) that is included in this object:</span></span><ul><li><strong><span data-ttu-id="54ef0-207">PageView</span><span class="sxs-lookup"><span data-stu-id="54ef0-207">PageView</span></span></strong></li><li><strong><span data-ttu-id="54ef0-208">Acquisition</span><span class="sxs-lookup"><span data-stu-id="54ef0-208">Acquisition</span></span></strong></li><li><strong><span data-ttu-id="54ef0-209">Installieren</span><span class="sxs-lookup"><span data-stu-id="54ef0-209">Install</span></span></strong></li><li><strong><span data-ttu-id="54ef0-210">Usage</span><span class="sxs-lookup"><span data-stu-id="54ef0-210">Usage</span></span></strong></li></ul> |
| <span data-ttu-id="54ef0-211">UserCount</span><span class="sxs-lookup"><span data-stu-id="54ef0-211">UserCount</span></span>       | <span data-ttu-id="54ef0-212">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="54ef0-212">string</span></span> | <span data-ttu-id="54ef0-213">Die Anzahl der Benutzer, die vom angegebenen Trichter Schrittausgeführt hat, die *MetricType* Wert.</span><span class="sxs-lookup"><span data-stu-id="54ef0-213">The number of users who performed the funnel step specified by the *MetricType* value.</span></span>             |

<span/> 

### <a name="response-example"></a><span data-ttu-id="54ef0-214">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="54ef0-214">Response example</span></span>

<span data-ttu-id="54ef0-215">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="54ef0-215">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "MetricType": "PageView",
      "UserCount": 100
    },
    {
      "MetricType": "Acquisition",
      "UserCount": 80
    },
    {
      "MetricType": "Install",
      "UserCount": 50
    },
    {
      "MetricType": "Usage",
      "UserCount": 10
    }
  ],
  "TotalCount": 4
}
```

## <a name="related-topics"></a><span data-ttu-id="54ef0-216">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="54ef0-216">Related topics</span></span>

* [<span data-ttu-id="54ef0-217">Bericht „Käufe“</span><span class="sxs-lookup"><span data-stu-id="54ef0-217">Acquisitions report</span></span>](../publish/acquisitions-report.md)
* [<span data-ttu-id="54ef0-218">Zugreifen auf Analysedaten mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="54ef0-218">Access analytics data using Windows Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="54ef0-219">Abrufen von App-Käufen</span><span class="sxs-lookup"><span data-stu-id="54ef0-219">Get app acquisitions</span></span>](get-app-acquisitions.md)
