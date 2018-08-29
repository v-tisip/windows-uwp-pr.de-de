---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Einblicke Daten für Ihre app zu erhalten.
title: Abrufen von Daten Einblicke
ms.author: mcleans
ms.date: 07/31/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Einblicke
ms.localizationpriority: medium
ms.openlocfilehash: 53fbd91437e5dc702f8672c6cbadeea32a8a96bf
ms.sourcegitcommit: 3727445c1d6374401b867c78e4ff8b07d92b7adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "2916638"
---
# <a name="get-insights-data"></a><span data-ttu-id="6d29c-104">Abrufen von Daten Einblicke</span><span class="sxs-lookup"><span data-stu-id="6d29c-104">Get insights data</span></span>

<span data-ttu-id="6d29c-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von Einblicke Daten während eines bestimmten Zeitraums und andere optionale Filter Käufe, Integrität und Nutzung Metrik für eine app im Zusammenhang.</span><span class="sxs-lookup"><span data-stu-id="6d29c-105">Use this method in the Microsoft Store analytics API to get insights data related to acquisitions, health, and usage metrics for an app during a given date range and other optional filters.</span></span> <span data-ttu-id="6d29c-106">Diese Informationen sind auch im [Bericht](../publish/insights-report.md) in Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6d29c-106">This information is also available in the [Insights report](../publish/insights-report.md) in the Windows Dev Center dashboard.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d29c-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6d29c-107">Prerequisites</span></span>


<span data-ttu-id="6d29c-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="6d29c-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="6d29c-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="6d29c-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="6d29c-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6d29c-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="6d29c-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="6d29c-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="6d29c-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="6d29c-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="6d29c-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="6d29c-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="6d29c-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="6d29c-114">Request syntax</span></span>

| <span data-ttu-id="6d29c-115">Methode</span><span class="sxs-lookup"><span data-stu-id="6d29c-115">Method</span></span> | <span data-ttu-id="6d29c-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="6d29c-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="6d29c-117">GET</span><span class="sxs-lookup"><span data-stu-id="6d29c-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/insights``` |


### <a name="request-header"></a><span data-ttu-id="6d29c-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="6d29c-118">Request header</span></span>

| <span data-ttu-id="6d29c-119">Header</span><span class="sxs-lookup"><span data-stu-id="6d29c-119">Header</span></span>        | <span data-ttu-id="6d29c-120">Typ</span><span class="sxs-lookup"><span data-stu-id="6d29c-120">Type</span></span>   | <span data-ttu-id="6d29c-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d29c-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="6d29c-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="6d29c-122">Authorization</span></span> | <span data-ttu-id="6d29c-123">String</span><span class="sxs-lookup"><span data-stu-id="6d29c-123">string</span></span> | <span data-ttu-id="6d29c-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6d29c-124">Required.</span></span> <span data-ttu-id="6d29c-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="6d29c-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="6d29c-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="6d29c-126">Request parameters</span></span>

| <span data-ttu-id="6d29c-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="6d29c-127">Parameter</span></span>        | <span data-ttu-id="6d29c-128">Typ</span><span class="sxs-lookup"><span data-stu-id="6d29c-128">Type</span></span>   |  <span data-ttu-id="6d29c-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d29c-129">Description</span></span>      |  <span data-ttu-id="6d29c-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6d29c-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="6d29c-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="6d29c-131">applicationId</span></span> | <span data-ttu-id="6d29c-132">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-132">string</span></span> | <span data-ttu-id="6d29c-133">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) der app, für die Sie Einblicke Daten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="6d29c-133">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to retrieve insights data.</span></span> <span data-ttu-id="6d29c-134">Wenn Sie diesen Parameter nicht angeben, enthält der Antworttext Einblicke Daten für alle apps, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="6d29c-134">If you do not specify this parameter, the response body will contain insights data for all apps registered to your account.</span></span>  |  <span data-ttu-id="6d29c-135">Nein</span><span class="sxs-lookup"><span data-stu-id="6d29c-135">No</span></span>  |
| <span data-ttu-id="6d29c-136">startDate</span><span class="sxs-lookup"><span data-stu-id="6d29c-136">startDate</span></span> | <span data-ttu-id="6d29c-137">date</span><span class="sxs-lookup"><span data-stu-id="6d29c-137">date</span></span> | <span data-ttu-id="6d29c-138">Das Startdatum im Datumsbereich der Einblicke Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="6d29c-138">The start date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="6d29c-139">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="6d29c-139">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="6d29c-140">Nein</span><span class="sxs-lookup"><span data-stu-id="6d29c-140">No</span></span>  |
| <span data-ttu-id="6d29c-141">endDate</span><span class="sxs-lookup"><span data-stu-id="6d29c-141">endDate</span></span> | <span data-ttu-id="6d29c-142">date</span><span class="sxs-lookup"><span data-stu-id="6d29c-142">date</span></span> | <span data-ttu-id="6d29c-143">Das Enddatum im Datumsbereich der Einblicke Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="6d29c-143">The end date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="6d29c-144">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="6d29c-144">The default is the current date.</span></span> |  <span data-ttu-id="6d29c-145">Nein</span><span class="sxs-lookup"><span data-stu-id="6d29c-145">No</span></span>  |
| <span data-ttu-id="6d29c-146">filter</span><span class="sxs-lookup"><span data-stu-id="6d29c-146">filter</span></span> | <span data-ttu-id="6d29c-147">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-147">string</span></span>  | <span data-ttu-id="6d29c-148">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="6d29c-148">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="6d29c-149">Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="6d29c-149">Each statement contains a field name from the response body and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span> <span data-ttu-id="6d29c-150">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="6d29c-150">String values must be surrounded by single quotes in the *filter* parameter.</span></span> <span data-ttu-id="6d29c-151">Beispielsweise *Filter = DataType Eq 'Erwerb'*.</span><span class="sxs-lookup"><span data-stu-id="6d29c-151">For example, *filter=dataType eq 'acquisition'*.</span></span> <p/><p/><span data-ttu-id="6d29c-152">Sie können die folgenden Filterfelder angeben:</span><span class="sxs-lookup"><span data-stu-id="6d29c-152">You can specify the following filter fields:</span></span><p/><ul><li><strong><span data-ttu-id="6d29c-153">Erwerb</span><span class="sxs-lookup"><span data-stu-id="6d29c-153">acquisition</span></span></strong></li><li><strong><span data-ttu-id="6d29c-154">Integrität</span><span class="sxs-lookup"><span data-stu-id="6d29c-154">health</span></span></strong></li><li><strong><span data-ttu-id="6d29c-155">Nutzung</span><span class="sxs-lookup"><span data-stu-id="6d29c-155">usage</span></span></strong></li></ul> | <span data-ttu-id="6d29c-156">Nein</span><span class="sxs-lookup"><span data-stu-id="6d29c-156">No</span></span>   |

### <a name="request-example"></a><span data-ttu-id="6d29c-157">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="6d29c-157">Request example</span></span>

<span data-ttu-id="6d29c-158">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Einblicke Daten.</span><span class="sxs-lookup"><span data-stu-id="6d29c-158">The following example demonstrates a request for getting insights data.</span></span> <span data-ttu-id="6d29c-159">Ersetzen Sie den Wert *applicationId* durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="6d29c-159">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/insights?applicationId=9NBLGGGZ5QDR&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'acquisition' or dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="6d29c-160">Antwort</span><span class="sxs-lookup"><span data-stu-id="6d29c-160">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="6d29c-161">Antworttext</span><span class="sxs-lookup"><span data-stu-id="6d29c-161">Response body</span></span>

| <span data-ttu-id="6d29c-162">Wert</span><span class="sxs-lookup"><span data-stu-id="6d29c-162">Value</span></span>      | <span data-ttu-id="6d29c-163">Typ</span><span class="sxs-lookup"><span data-stu-id="6d29c-163">Type</span></span>   | <span data-ttu-id="6d29c-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d29c-164">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="6d29c-165">Wert</span><span class="sxs-lookup"><span data-stu-id="6d29c-165">Value</span></span>      | <span data-ttu-id="6d29c-166">array</span><span class="sxs-lookup"><span data-stu-id="6d29c-166">array</span></span>  | <span data-ttu-id="6d29c-167">Ein Array von Objekten, die Einblicke Daten für die app enthalten.</span><span class="sxs-lookup"><span data-stu-id="6d29c-167">An array of objects that contain insights data for the app.</span></span> <span data-ttu-id="6d29c-168">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie weiter unten im Abschnitt [Insight Werte](#insight-values) .</span><span class="sxs-lookup"><span data-stu-id="6d29c-168">For more information about the data in each object, see the [Insight values](#insight-values) section below.</span></span>                                                                                                                      |
| <span data-ttu-id="6d29c-169">TotalCount</span><span class="sxs-lookup"><span data-stu-id="6d29c-169">TotalCount</span></span> | <span data-ttu-id="6d29c-170">int</span><span class="sxs-lookup"><span data-stu-id="6d29c-170">int</span></span>    | <span data-ttu-id="6d29c-171">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="6d29c-171">The total number of rows in the data result for the query.</span></span>                 |


### <a name="insight-values"></a><span data-ttu-id="6d29c-172">Insight-Werte</span><span class="sxs-lookup"><span data-stu-id="6d29c-172">Insight values</span></span>

<span data-ttu-id="6d29c-173">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="6d29c-173">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="6d29c-174">Wert</span><span class="sxs-lookup"><span data-stu-id="6d29c-174">Value</span></span>               | <span data-ttu-id="6d29c-175">Typ</span><span class="sxs-lookup"><span data-stu-id="6d29c-175">Type</span></span>   | <span data-ttu-id="6d29c-176">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d29c-176">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="6d29c-177">applicationId</span><span class="sxs-lookup"><span data-stu-id="6d29c-177">applicationId</span></span>       | <span data-ttu-id="6d29c-178">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-178">string</span></span> | <span data-ttu-id="6d29c-179">Die Store-ID der app, für die Sie Einblicke Daten abrufen.</span><span class="sxs-lookup"><span data-stu-id="6d29c-179">The Store ID of the app for which you are retrieving insights data.</span></span>     |
| <span data-ttu-id="6d29c-180">insightDate</span><span class="sxs-lookup"><span data-stu-id="6d29c-180">insightDate</span></span>                | <span data-ttu-id="6d29c-181">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-181">string</span></span> | <span data-ttu-id="6d29c-182">Das Datum, an dem wir die Änderung in einer bestimmten Metrik identifiziert.</span><span class="sxs-lookup"><span data-stu-id="6d29c-182">The date on which we identified the change in a specific metric.</span></span> <span data-ttu-id="6d29c-183">Dieses Datum steht das Ende der Woche, in dem wir eine erhebliche Erhöhung erkannt, oder in einer Metrik im Vergleich zur vorherigen Woche, verringern.</span><span class="sxs-lookup"><span data-stu-id="6d29c-183">This date represents the end of the week in which we detected a significant increase or decrease in a metric compared to the week before that.</span></span> |
| <span data-ttu-id="6d29c-184">Datentyp</span><span class="sxs-lookup"><span data-stu-id="6d29c-184">dataType</span></span>     | <span data-ttu-id="6d29c-185">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-185">string</span></span> | <span data-ttu-id="6d29c-186">Eine der folgenden Zeichenfolgen, die die allgemeine Analysen Bereich angibt, den diese Insight beschreibt:</span><span class="sxs-lookup"><span data-stu-id="6d29c-186">One of the following strings that specifies the general analytics area that this insight describes:</span></span><p/><ul><li><strong><span data-ttu-id="6d29c-187">Erwerb</span><span class="sxs-lookup"><span data-stu-id="6d29c-187">acquisition</span></span></strong></li><li><strong><span data-ttu-id="6d29c-188">Integrität</span><span class="sxs-lookup"><span data-stu-id="6d29c-188">health</span></span></strong></li><li><strong><span data-ttu-id="6d29c-189">Nutzung</span><span class="sxs-lookup"><span data-stu-id="6d29c-189">usage</span></span></strong></li></ul>   |
| <span data-ttu-id="6d29c-190">insightDetail</span><span class="sxs-lookup"><span data-stu-id="6d29c-190">insightDetail</span></span>          | <span data-ttu-id="6d29c-191">array</span><span class="sxs-lookup"><span data-stu-id="6d29c-191">array</span></span> | <span data-ttu-id="6d29c-192">Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die Details für aktuelle Insight darstellen.</span><span class="sxs-lookup"><span data-stu-id="6d29c-192">One or more [InsightDetail values](#insightdetail-values) that represent the details for current insight.</span></span>    |


### <a name="insightdetail-values"></a><span data-ttu-id="6d29c-193">InsightDetail Werte</span><span class="sxs-lookup"><span data-stu-id="6d29c-193">InsightDetail values</span></span>

| <span data-ttu-id="6d29c-194">Wert</span><span class="sxs-lookup"><span data-stu-id="6d29c-194">Value</span></span>               | <span data-ttu-id="6d29c-195">Typ</span><span class="sxs-lookup"><span data-stu-id="6d29c-195">Type</span></span>   | <span data-ttu-id="6d29c-196">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d29c-196">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="6d29c-197">FactName</span><span class="sxs-lookup"><span data-stu-id="6d29c-197">FactName</span></span>           | <span data-ttu-id="6d29c-198">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-198">string</span></span> | <span data-ttu-id="6d29c-199">Die folgenden Werte, der die Metrik angibt, die das aktuelle Insight oder die aktuelle Dimension zu beschreiben, basierend auf dem **DataType** -Wert.</span><span class="sxs-lookup"><span data-stu-id="6d29c-199">One of the following values that indicates the metric that the current insight or current dimension describes, based on the **dataType** value.</span></span><ul><li><span data-ttu-id="6d29c-200">**Integrität**ist dieser Wert immer **HitCount**.</span><span class="sxs-lookup"><span data-stu-id="6d29c-200">For **health**, this value is always **HitCount**.</span></span></li><li><span data-ttu-id="6d29c-201">Für den **Kauf**ist dieser Wert immer **AcquisitionQuantity**.</span><span class="sxs-lookup"><span data-stu-id="6d29c-201">For **acquisition**, this value is always **AcquisitionQuantity**.</span></span></li><li><span data-ttu-id="6d29c-202">Für die **Nutzung**kann der Wert eine der folgenden Zeichenfolgen sein:</span><span class="sxs-lookup"><span data-stu-id="6d29c-202">For **usage**, this value can be one of the following strings:</span></span><ul><li><strong><span data-ttu-id="6d29c-203">DailyActiveUsers</span><span class="sxs-lookup"><span data-stu-id="6d29c-203">DailyActiveUsers</span></span></strong></li><li><strong><span data-ttu-id="6d29c-204">EngagementDurationMinutes</span><span class="sxs-lookup"><span data-stu-id="6d29c-204">EngagementDurationMinutes</span></span></strong></li><li><strong><span data-ttu-id="6d29c-205">DailyActiveDevices</span><span class="sxs-lookup"><span data-stu-id="6d29c-205">DailyActiveDevices</span></span></strong></li><li><strong><span data-ttu-id="6d29c-206">DailyNewUsers</span><span class="sxs-lookup"><span data-stu-id="6d29c-206">DailyNewUsers</span></span></strong></li><li><strong><span data-ttu-id="6d29c-207">DailySessionCount</span><span class="sxs-lookup"><span data-stu-id="6d29c-207">DailySessionCount</span></span></strong></li></ul></ul>  |
| <span data-ttu-id="6d29c-208">SubDimensions</span><span class="sxs-lookup"><span data-stu-id="6d29c-208">SubDimensions</span></span>         | <span data-ttu-id="6d29c-209">array</span><span class="sxs-lookup"><span data-stu-id="6d29c-209">array</span></span> |  <span data-ttu-id="6d29c-210">Ein oder mehrere Objekte, die eine einzelne Metrik für die Einblicke zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="6d29c-210">One or more objects that describe a single metric for the insight.</span></span>   |
| <span data-ttu-id="6d29c-211">Prozent</span><span class="sxs-lookup"><span data-stu-id="6d29c-211">PercentChange</span></span>            | <span data-ttu-id="6d29c-212">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-212">string</span></span> |  <span data-ttu-id="6d29c-213">Der Prozentsatz, den die Metrik über Ihres gesamten Kundenstamms geändert.</span><span class="sxs-lookup"><span data-stu-id="6d29c-213">The percentage that the metric changed across your entire customer base.</span></span>  |
| <span data-ttu-id="6d29c-214">DimensionName</span><span class="sxs-lookup"><span data-stu-id="6d29c-214">DimensionName</span></span>           | <span data-ttu-id="6d29c-215">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-215">string</span></span> |  <span data-ttu-id="6d29c-216">Der Name des die Metrik befindet sich in der aktuellen Dimension beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6d29c-216">The name of the metric described in the current dimension.</span></span> <span data-ttu-id="6d29c-217">Beispiele sind **EventType**"," **Markt**"," **DeviceType**"," **PackageVersion**"," **AcquisitionType**"," **AgeGroup** "und" **Geschlecht**.</span><span class="sxs-lookup"><span data-stu-id="6d29c-217">Examples include **EventType**, **Market**, **DeviceType**, **PackageVersion**, **AcquisitionType**, **AgeGroup** and **Gender**.</span></span>   |
| <span data-ttu-id="6d29c-218">DimensionValue</span><span class="sxs-lookup"><span data-stu-id="6d29c-218">DimensionValue</span></span>              | <span data-ttu-id="6d29c-219">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-219">string</span></span> | <span data-ttu-id="6d29c-220">Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="6d29c-220">The value of the metric that is described in the current dimension.</span></span> <span data-ttu-id="6d29c-221">Beispielsweise ist **DimensionName** **EventType**, **DimensionValue** **Absturz** oder **Blockade**möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="6d29c-221">For example, if **DimensionName** is **EventType**, **DimensionValue** might be **crash** or **hang**.</span></span>   |
| <span data-ttu-id="6d29c-222">FactValue</span><span class="sxs-lookup"><span data-stu-id="6d29c-222">FactValue</span></span>     | <span data-ttu-id="6d29c-223">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-223">string</span></span> | <span data-ttu-id="6d29c-224">Der absoluten Wert der Metrik auf das Datum, an das die Einblicke erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="6d29c-224">The absolute value of the metric on the date the insight was detected.</span></span>  |
| <span data-ttu-id="6d29c-225">Richtung</span><span class="sxs-lookup"><span data-stu-id="6d29c-225">Direction</span></span> | <span data-ttu-id="6d29c-226">string</span><span class="sxs-lookup"><span data-stu-id="6d29c-226">string</span></span> |  <span data-ttu-id="6d29c-227">Die Richtung der Änderung (**positiv** oder **negativ**).</span><span class="sxs-lookup"><span data-stu-id="6d29c-227">The direction of the change (**Positive** or **Negative**).</span></span>   |
| <span data-ttu-id="6d29c-228">Date</span><span class="sxs-lookup"><span data-stu-id="6d29c-228">Date</span></span>              | <span data-ttu-id="6d29c-229">String</span><span class="sxs-lookup"><span data-stu-id="6d29c-229">string</span></span> |  <span data-ttu-id="6d29c-230">Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Insight oder die aktuelle Dimension identifiziert.</span><span class="sxs-lookup"><span data-stu-id="6d29c-230">The date on which we identified the change related to the current insight or the current dimension.</span></span>   |

### <a name="response-example"></a><span data-ttu-id="6d29c-231">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="6d29c-231">Response example</span></span>

<span data-ttu-id="6d29c-232">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="6d29c-232">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "applicationId": "9NBLGGGZ5QDR",
      "insightDate": "2018-06-03T00:00:00",
      "dataType": "health",
      "insightDetail": [
        {
          "FactName": "HitCount",
          "SubDimensions": [
            {
              "FactName:": "HitCount",
              "PercentChange": "21",
              "DimensionValue:": "DE",
              "FactValue": "109",
              "Direction": "Positive",
              "Date": "6/3/2018 12:00:00 AM",
              "DimensionName": "Market"
            }
          ],
          "DimensionValue": "crash",
          "Date": "6/3/2018 12:00:00 AM",
          "DimensionName": "EventType"
        },
        {
          "FactName": "HitCount",
          "SubDimensions": [
            {
              "FactName:": "HitCount",
              "PercentChange": "71",
              "DimensionValue:": "JP",
              "FactValue": "112",
              "Direction": "Positive",
              "Date": "6/3/2018 12:00:00 AM",
              "DimensionName": "Market"
            }
          ],
          "DimensionValue": "hang",
          "Date": "6/3/2018 12:00:00 AM",
          "DimensionName": "EventType"
        },
      ],
      "insightId": "9CY0F3VBT1AS942AFQaeyO0k2zUKfyOhrOHc0036Iwc="
    }
  ],
  "@nextLink": null,
  "TotalCount": 2
}
```

## <a name="related-topics"></a><span data-ttu-id="6d29c-233">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6d29c-233">Related topics</span></span>

* [<span data-ttu-id="6d29c-234">Geschäftsinformationen-Bericht</span><span class="sxs-lookup"><span data-stu-id="6d29c-234">Insights report</span></span>](../publish/insights-report.md)
* [<span data-ttu-id="6d29c-235">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="6d29c-235">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
