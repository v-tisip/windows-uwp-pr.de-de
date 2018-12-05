---
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Erwerbstrichterdaten für eine Anwendung während eines bestimmten Zeitraums und andere optionale Filter abzurufen.
title: Abrufen von App-Erwerbstrichterdaten
ms.date: 08/04/2017
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Kauf, Trichter
ms.localizationpriority: medium
ms.openlocfilehash: d9ccbb081ef6f39ad795105ee2449de4d8442ab3
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8690134"
---
# <a name="get-app-acquisition-funnel-data"></a><span data-ttu-id="ea8a1-104">Abrufen von App-Erwerbstrichterdaten</span><span class="sxs-lookup"><span data-stu-id="ea8a1-104">Get app acquisition funnel data</span></span>

<span data-ttu-id="ea8a1-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Erwerbstrichterdaten für eine Anwendung während eines bestimmten Zeitraums und andere optionale Filter abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-105">Use this method in the Microsoft Store analytics API to get acquisition funnel data for an application during a given date range and other optional filters.</span></span> <span data-ttu-id="ea8a1-106">Diese Informationen sind auch im [Bericht "Käufe"](../publish/acquisitions-report.md#acquisition-funnel) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-106">This information is also available in the [Acquisitions report](../publish/acquisitions-report.md#acquisition-funnel) in Partner Center.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea8a1-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ea8a1-107">Prerequisites</span></span>


<span data-ttu-id="ea8a1-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ea8a1-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ea8a1-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="ea8a1-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ea8a1-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ea8a1-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="ea8a1-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="ea8a1-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="ea8a1-114">Request syntax</span></span>

| <span data-ttu-id="ea8a1-115">Methode</span><span class="sxs-lookup"><span data-stu-id="ea8a1-115">Method</span></span> | <span data-ttu-id="ea8a1-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ea8a1-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="ea8a1-117">GET</span><span class="sxs-lookup"><span data-stu-id="ea8a1-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel``` |


### <a name="request-header"></a><span data-ttu-id="ea8a1-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ea8a1-118">Request header</span></span>

| <span data-ttu-id="ea8a1-119">Header</span><span class="sxs-lookup"><span data-stu-id="ea8a1-119">Header</span></span>        | <span data-ttu-id="ea8a1-120">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8a1-120">Type</span></span>   | <span data-ttu-id="ea8a1-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ea8a1-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-122">Authorization</span></span> | <span data-ttu-id="ea8a1-123">String</span><span class="sxs-lookup"><span data-stu-id="ea8a1-123">string</span></span> | <span data-ttu-id="ea8a1-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-124">Required.</span></span> <span data-ttu-id="ea8a1-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="ea8a1-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ea8a1-126">Request parameters</span></span>

| <span data-ttu-id="ea8a1-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="ea8a1-127">Parameter</span></span>        | <span data-ttu-id="ea8a1-128">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8a1-128">Type</span></span>   |  <span data-ttu-id="ea8a1-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-129">Description</span></span>      |  <span data-ttu-id="ea8a1-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ea8a1-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="ea8a1-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="ea8a1-131">applicationId</span></span> | <span data-ttu-id="ea8a1-132">string</span><span class="sxs-lookup"><span data-stu-id="ea8a1-132">string</span></span> | <span data-ttu-id="ea8a1-133">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der App, für die Sie die Erwerbstrichterdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-133">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to retrieve acquisition funnel data.</span></span> <span data-ttu-id="ea8a1-134">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-134">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="ea8a1-135">Ja</span><span class="sxs-lookup"><span data-stu-id="ea8a1-135">Yes</span></span>  |
| <span data-ttu-id="ea8a1-136">startDate</span><span class="sxs-lookup"><span data-stu-id="ea8a1-136">startDate</span></span> | <span data-ttu-id="ea8a1-137">date</span><span class="sxs-lookup"><span data-stu-id="ea8a1-137">date</span></span> | <span data-ttu-id="ea8a1-138">Das Startdatum im Datumsbereich der Erwerbstrichterdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-138">The start date in the date range of acquisition funnel data to retrieve.</span></span> <span data-ttu-id="ea8a1-139">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-139">The default is the current date.</span></span> |  <span data-ttu-id="ea8a1-140">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8a1-140">No</span></span>  |
| <span data-ttu-id="ea8a1-141">endDate</span><span class="sxs-lookup"><span data-stu-id="ea8a1-141">endDate</span></span> | <span data-ttu-id="ea8a1-142">date</span><span class="sxs-lookup"><span data-stu-id="ea8a1-142">date</span></span> | <span data-ttu-id="ea8a1-143">Das Enddatum im Datumsbereich der Erwerbstrichterdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-143">The end date in the date range of acquisition funnel data to retrieve.</span></span> <span data-ttu-id="ea8a1-144">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-144">The default is the current date.</span></span> |  <span data-ttu-id="ea8a1-145">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8a1-145">No</span></span>  |
| <span data-ttu-id="ea8a1-146">filter</span><span class="sxs-lookup"><span data-stu-id="ea8a1-146">filter</span></span> | <span data-ttu-id="ea8a1-147">string</span><span class="sxs-lookup"><span data-stu-id="ea8a1-147">string</span></span>  | <span data-ttu-id="ea8a1-148">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-148">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="ea8a1-149">Weitere Informationen finden Sie unten im Abschnitt [Filterfelder](#filter-fields).</span><span class="sxs-lookup"><span data-stu-id="ea8a1-149">For more information, see the [filter fields](#filter-fields) section below.</span></span> | <span data-ttu-id="ea8a1-150">Nein</span><span class="sxs-lookup"><span data-stu-id="ea8a1-150">No</span></span>   |

 
### <a name="filter-fields"></a><span data-ttu-id="ea8a1-151">Filterfelder</span><span class="sxs-lookup"><span data-stu-id="ea8a1-151">Filter fields</span></span>

<span data-ttu-id="ea8a1-152">Der Parameter *filter* der Anforderung enthält mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-152">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="ea8a1-153">Jede Anweisung enthält ein Feld und einen Wert, das/der mit den Operatoren **eq** oder **ne** verknüpft ist. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-153">Each statement contains a field and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span>

<span data-ttu-id="ea8a1-154">Die folgenden Filterfelder werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-154">The following filter fields are supported.</span></span> <span data-ttu-id="ea8a1-155">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-155">String values must be surrounded by single quotes in the *filter* parameter.</span></span>

| <span data-ttu-id="ea8a1-156">Felder</span><span class="sxs-lookup"><span data-stu-id="ea8a1-156">Fields</span></span>        |  <span data-ttu-id="ea8a1-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-157">Description</span></span>        |
|---------------|-----------------|
| <span data-ttu-id="ea8a1-158">campaignId</span><span class="sxs-lookup"><span data-stu-id="ea8a1-158">campaignId</span></span> | <span data-ttu-id="ea8a1-159">Die ID-Zeichenfolge für einen [Werbekampagne für benutzerdefinierte Apps](../publish/create-a-custom-app-promotion-campaign.md), die dem Kauf zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-159">The ID string for a [custom app promotion campaign](../publish/create-a-custom-app-promotion-campaign.md) that is associated with the acquisition.</span></span> |
| <span data-ttu-id="ea8a1-160">market</span><span class="sxs-lookup"><span data-stu-id="ea8a1-160">market</span></span> | <span data-ttu-id="ea8a1-161">Eine Zeichenfolge, die den ISO 3166-Ländercode des Markts enthält, in dem der Kauf erfolgte.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-161">A string that contains the ISO 3166 country code of the market where the acquisition occurred.</span></span> |
| <span data-ttu-id="ea8a1-162">deviceType</span><span class="sxs-lookup"><span data-stu-id="ea8a1-162">deviceType</span></span> | <span data-ttu-id="ea8a1-163">Eine der folgenden Zeichenfolgen, die den Typ des Geräts angibt, auf der Kauf aufgetreten ist:</span><span class="sxs-lookup"><span data-stu-id="ea8a1-163">One of the following strings that specifies the device type on which the acquisition occurred:</span></span><ul><li><strong><span data-ttu-id="ea8a1-164">PC</span><span class="sxs-lookup"><span data-stu-id="ea8a1-164">PC</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-165">Phone</span><span class="sxs-lookup"><span data-stu-id="ea8a1-165">Phone</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-166">Console</span><span class="sxs-lookup"><span data-stu-id="ea8a1-166">Console</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-167">IoT</span><span class="sxs-lookup"><span data-stu-id="ea8a1-167">IoT</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-168">Holographic</span><span class="sxs-lookup"><span data-stu-id="ea8a1-168">Holographic</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-169">Unknown</span><span class="sxs-lookup"><span data-stu-id="ea8a1-169">Unknown</span></span></strong></li></ul> |
| <span data-ttu-id="ea8a1-170">ageGroup</span><span class="sxs-lookup"><span data-stu-id="ea8a1-170">ageGroup</span></span> | <span data-ttu-id="ea8a1-171">Eine der folgenden Zeichenfolgen, die den Typ der Age-Group des Benutzer angibt, der den Kauf abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="ea8a1-171">One of the following strings that specifies the age group of the user who completed the acquisition:</span></span><ul><li><strong><span data-ttu-id="ea8a1-172">0 – 17</span><span class="sxs-lookup"><span data-stu-id="ea8a1-172">0 – 17</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-173">18 – 24</span><span class="sxs-lookup"><span data-stu-id="ea8a1-173">18 – 24</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-174">25 – 34</span><span class="sxs-lookup"><span data-stu-id="ea8a1-174">25 – 34</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-175">35 – 49</span><span class="sxs-lookup"><span data-stu-id="ea8a1-175">35 – 49</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-176">50 oder mehr</span><span class="sxs-lookup"><span data-stu-id="ea8a1-176">50 or over</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-177">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="ea8a1-177">Unknown</span></span></strong></li></ul> |
| <span data-ttu-id="ea8a1-178">gender</span><span class="sxs-lookup"><span data-stu-id="ea8a1-178">gender</span></span> | <span data-ttu-id="ea8a1-179">Eine der folgenden Zeichenfolgen, die das Geschlecht des Benutzer angibt, der den Kauf abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="ea8a1-179">One of the following strings that specifies the gender of the user who completed the acquisition:</span></span><ul><li><strong><span data-ttu-id="ea8a1-180">M</span><span class="sxs-lookup"><span data-stu-id="ea8a1-180">M</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-181">F</span><span class="sxs-lookup"><span data-stu-id="ea8a1-181">F</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-182">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="ea8a1-182">Unknown</span></span></strong></li></ul> |


### <a name="request-example"></a><span data-ttu-id="ea8a1-183">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ea8a1-183">Request example</span></span>

<span data-ttu-id="ea8a1-184">Das folgende Beispiel zeigt verschiedene Anforderungen für den Abruf von Erwerbstrichterdaten für Apps.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-184">The following example demonstrates several requests for getting acquisition funnel data for an app.</span></span> <span data-ttu-id="ea8a1-185">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-185">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel?applicationId=9NBLGGGZ5QDR&startDate=1/1/2017&endDate=2/1/2017  HTTP/1.1
Authorization: Bearer <your access token>

GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/funnel?applicationId=9NBLGGGZ5QDR&startDate=8/1/2016&endDate=8/31/2016&filter=market eq 'US' and gender eq 'm'  HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ea8a1-186">Antwort</span><span class="sxs-lookup"><span data-stu-id="ea8a1-186">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="ea8a1-187">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ea8a1-187">Response body</span></span>

| <span data-ttu-id="ea8a1-188">Wert</span><span class="sxs-lookup"><span data-stu-id="ea8a1-188">Value</span></span>      | <span data-ttu-id="ea8a1-189">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8a1-189">Type</span></span>   | <span data-ttu-id="ea8a1-190">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-190">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="ea8a1-191">Wert</span><span class="sxs-lookup"><span data-stu-id="ea8a1-191">Value</span></span>      | <span data-ttu-id="ea8a1-192">Array</span><span class="sxs-lookup"><span data-stu-id="ea8a1-192">array</span></span>  | <span data-ttu-id="ea8a1-193">Ein Array von Objekten, die Erwerbstrichterdaten für die App enthalten.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-193">An array of objects that contain acquisition funnel data for the app.</span></span> <span data-ttu-id="ea8a1-194">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Trichterwerte](#funnel-values).</span><span class="sxs-lookup"><span data-stu-id="ea8a1-194">For more information about the data in each object, see the [funnel values](#funnel-values) section below.</span></span>                  |
| <span data-ttu-id="ea8a1-195">TotalCount</span><span class="sxs-lookup"><span data-stu-id="ea8a1-195">TotalCount</span></span> | <span data-ttu-id="ea8a1-196">int</span><span class="sxs-lookup"><span data-stu-id="ea8a1-196">int</span></span>    | <span data-ttu-id="ea8a1-197">Die Gesamtanzahl der Objekte im *Value* Array.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-197">The total number of objects in the *Value* array.</span></span>        |


### <a name="funnel-values"></a><span data-ttu-id="ea8a1-198">Trichterwerte</span><span class="sxs-lookup"><span data-stu-id="ea8a1-198">Funnel values</span></span>

<span data-ttu-id="ea8a1-199">Objekte im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-199">Objects in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="ea8a1-200">Wert</span><span class="sxs-lookup"><span data-stu-id="ea8a1-200">Value</span></span>               | <span data-ttu-id="ea8a1-201">Typ</span><span class="sxs-lookup"><span data-stu-id="ea8a1-201">Type</span></span>   | <span data-ttu-id="ea8a1-202">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea8a1-202">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="ea8a1-203">MetricType</span><span class="sxs-lookup"><span data-stu-id="ea8a1-203">MetricType</span></span>                | <span data-ttu-id="ea8a1-204">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ea8a1-204">string</span></span> | <span data-ttu-id="ea8a1-205">Eine der folgenden Zeichenfolgen, die angibt, die [Trichter Datentyp](../publish/acquisitions-report.md#acquisition-funnel), die in diesem Objekt enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="ea8a1-205">One of the following strings that specifies the [type of funnel data](../publish/acquisitions-report.md#acquisition-funnel) that is included in this object:</span></span><ul><li><strong><span data-ttu-id="ea8a1-206">PageView</span><span class="sxs-lookup"><span data-stu-id="ea8a1-206">PageView</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-207">Acquisition</span><span class="sxs-lookup"><span data-stu-id="ea8a1-207">Acquisition</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-208">Installieren</span><span class="sxs-lookup"><span data-stu-id="ea8a1-208">Install</span></span></strong></li><li><strong><span data-ttu-id="ea8a1-209">Usage</span><span class="sxs-lookup"><span data-stu-id="ea8a1-209">Usage</span></span></strong></li></ul> |
| <span data-ttu-id="ea8a1-210">UserCount</span><span class="sxs-lookup"><span data-stu-id="ea8a1-210">UserCount</span></span>       | <span data-ttu-id="ea8a1-211">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ea8a1-211">string</span></span> | <span data-ttu-id="ea8a1-212">Die Anzahl der Benutzer, die vom angegebenen Trichter Schrittausgeführt hat, die *MetricType* Wert.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-212">The number of users who performed the funnel step specified by the *MetricType* value.</span></span>             |


### <a name="response-example"></a><span data-ttu-id="ea8a1-213">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="ea8a1-213">Response example</span></span>

<span data-ttu-id="ea8a1-214">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="ea8a1-214">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="ea8a1-215">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ea8a1-215">Related topics</span></span>

* [<span data-ttu-id="ea8a1-216">Bericht „Käufe“</span><span class="sxs-lookup"><span data-stu-id="ea8a1-216">Acquisitions report</span></span>](../publish/acquisitions-report.md)
* [<span data-ttu-id="ea8a1-217">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="ea8a1-217">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="ea8a1-218">Abrufen von App-Käufen</span><span class="sxs-lookup"><span data-stu-id="ea8a1-218">Get app acquisitions</span></span>](get-app-acquisitions.md)
