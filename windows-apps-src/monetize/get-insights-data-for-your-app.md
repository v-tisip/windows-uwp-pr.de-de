---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store Analytics API zum Abrufen von Daten für Ihre app.
title: Abrufen von Daten
ms.author: mcleans
ms.date: 07/31/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store Services, Microsoft Store Analytics Insights-API
ms.localizationpriority: medium
ms.openlocfilehash: 53fbd91437e5dc702f8672c6cbadeea32a8a96bf
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2884249"
---
# <a name="get-insights-data"></a><span data-ttu-id="2570e-104">Abrufen von Daten</span><span class="sxs-lookup"><span data-stu-id="2570e-104">Get insights data</span></span>

<span data-ttu-id="2570e-105">Verwenden Sie diese Methode in der Microsoft Store Analytics API zum Abrufen von Daten Einblicke in die Übernahmen, Integrität und auslastungskennzahlen für eine app während einen bestimmten Zeitraum hinweg und andere optional Filter im Zusammenhang.</span><span class="sxs-lookup"><span data-stu-id="2570e-105">Use this method in the Microsoft Store analytics API to get insights data related to acquisitions, health, and usage metrics for an app during a given date range and other optional filters.</span></span> <span data-ttu-id="2570e-106">Diese Informationen sind auch im [Insights-Bericht](../publish/insights-report.md) im Dashboard Entwicklungscenter für Windows verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2570e-106">This information is also available in the [Insights report](../publish/insights-report.md) in the Windows Dev Center dashboard.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2570e-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2570e-107">Prerequisites</span></span>


<span data-ttu-id="2570e-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="2570e-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="2570e-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="2570e-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="2570e-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2570e-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="2570e-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="2570e-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="2570e-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="2570e-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="2570e-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="2570e-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="2570e-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="2570e-114">Request syntax</span></span>

| <span data-ttu-id="2570e-115">Methode</span><span class="sxs-lookup"><span data-stu-id="2570e-115">Method</span></span> | <span data-ttu-id="2570e-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="2570e-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="2570e-117">GET</span><span class="sxs-lookup"><span data-stu-id="2570e-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/insights``` |


### <a name="request-header"></a><span data-ttu-id="2570e-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="2570e-118">Request header</span></span>

| <span data-ttu-id="2570e-119">Header</span><span class="sxs-lookup"><span data-stu-id="2570e-119">Header</span></span>        | <span data-ttu-id="2570e-120">Typ</span><span class="sxs-lookup"><span data-stu-id="2570e-120">Type</span></span>   | <span data-ttu-id="2570e-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2570e-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2570e-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="2570e-122">Authorization</span></span> | <span data-ttu-id="2570e-123">String</span><span class="sxs-lookup"><span data-stu-id="2570e-123">string</span></span> | <span data-ttu-id="2570e-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2570e-124">Required.</span></span> <span data-ttu-id="2570e-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="2570e-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="2570e-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="2570e-126">Request parameters</span></span>

| <span data-ttu-id="2570e-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="2570e-127">Parameter</span></span>        | <span data-ttu-id="2570e-128">Typ</span><span class="sxs-lookup"><span data-stu-id="2570e-128">Type</span></span>   |  <span data-ttu-id="2570e-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2570e-129">Description</span></span>      |  <span data-ttu-id="2570e-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="2570e-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="2570e-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="2570e-131">applicationId</span></span> | <span data-ttu-id="2570e-132">string</span><span class="sxs-lookup"><span data-stu-id="2570e-132">string</span></span> | <span data-ttu-id="2570e-133">Die [Nachrichtenspeicher-ID](in-app-purchases-and-trials.md#store-ids) der app Einblicke in die Daten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2570e-133">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the app for which you want to retrieve insights data.</span></span> <span data-ttu-id="2570e-134">Wenn Sie diesen Parameter nicht angeben, wird der Antworttext Einblicke in die Daten für alle apps, die für Ihr Konto registriert enthalten.</span><span class="sxs-lookup"><span data-stu-id="2570e-134">If you do not specify this parameter, the response body will contain insights data for all apps registered to your account.</span></span>  |  <span data-ttu-id="2570e-135">Nein</span><span class="sxs-lookup"><span data-stu-id="2570e-135">No</span></span>  |
| <span data-ttu-id="2570e-136">startDate</span><span class="sxs-lookup"><span data-stu-id="2570e-136">startDate</span></span> | <span data-ttu-id="2570e-137">date</span><span class="sxs-lookup"><span data-stu-id="2570e-137">date</span></span> | <span data-ttu-id="2570e-138">Das Startdatum in der Datumsbereich der Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2570e-138">The start date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="2570e-139">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="2570e-139">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="2570e-140">Nein</span><span class="sxs-lookup"><span data-stu-id="2570e-140">No</span></span>  |
| <span data-ttu-id="2570e-141">endDate</span><span class="sxs-lookup"><span data-stu-id="2570e-141">endDate</span></span> | <span data-ttu-id="2570e-142">date</span><span class="sxs-lookup"><span data-stu-id="2570e-142">date</span></span> | <span data-ttu-id="2570e-143">Das Enddatum im Datumsbereich der Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2570e-143">The end date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="2570e-144">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="2570e-144">The default is the current date.</span></span> |  <span data-ttu-id="2570e-145">Nein</span><span class="sxs-lookup"><span data-stu-id="2570e-145">No</span></span>  |
| <span data-ttu-id="2570e-146">filter</span><span class="sxs-lookup"><span data-stu-id="2570e-146">filter</span></span> | <span data-ttu-id="2570e-147">string</span><span class="sxs-lookup"><span data-stu-id="2570e-147">string</span></span>  | <span data-ttu-id="2570e-148">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="2570e-148">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="2570e-149">Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="2570e-149">Each statement contains a field name from the response body and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span> <span data-ttu-id="2570e-150">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="2570e-150">String values must be surrounded by single quotes in the *filter* parameter.</span></span> <span data-ttu-id="2570e-151">Beispielsweise *Filter = DataType-Eq "Erwerb'*.</span><span class="sxs-lookup"><span data-stu-id="2570e-151">For example, *filter=dataType eq 'acquisition'*.</span></span> <p/><p/><span data-ttu-id="2570e-152">Sie können die folgenden Filterfelder angeben:</span><span class="sxs-lookup"><span data-stu-id="2570e-152">You can specify the following filter fields:</span></span><p/><ul><li><strong><span data-ttu-id="2570e-153">Erwerb</span><span class="sxs-lookup"><span data-stu-id="2570e-153">acquisition</span></span></strong></li><li><strong><span data-ttu-id="2570e-154">Integrität</span><span class="sxs-lookup"><span data-stu-id="2570e-154">health</span></span></strong></li><li><strong><span data-ttu-id="2570e-155">Verwendung</span><span class="sxs-lookup"><span data-stu-id="2570e-155">usage</span></span></strong></li></ul> | <span data-ttu-id="2570e-156">Nein</span><span class="sxs-lookup"><span data-stu-id="2570e-156">No</span></span>   |

### <a name="request-example"></a><span data-ttu-id="2570e-157">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="2570e-157">Request example</span></span>

<span data-ttu-id="2570e-158">Im folgenden Beispiel wird eine Anforderung zum Abrufen von Daten.</span><span class="sxs-lookup"><span data-stu-id="2570e-158">The following example demonstrates a request for getting insights data.</span></span> <span data-ttu-id="2570e-159">Ersetzen Sie den Wert *applicationId* durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="2570e-159">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/insights?applicationId=9NBLGGGZ5QDR&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'acquisition' or dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="2570e-160">Antwort</span><span class="sxs-lookup"><span data-stu-id="2570e-160">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="2570e-161">Antworttext</span><span class="sxs-lookup"><span data-stu-id="2570e-161">Response body</span></span>

| <span data-ttu-id="2570e-162">Wert</span><span class="sxs-lookup"><span data-stu-id="2570e-162">Value</span></span>      | <span data-ttu-id="2570e-163">Typ</span><span class="sxs-lookup"><span data-stu-id="2570e-163">Type</span></span>   | <span data-ttu-id="2570e-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2570e-164">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="2570e-165">Wert</span><span class="sxs-lookup"><span data-stu-id="2570e-165">Value</span></span>      | <span data-ttu-id="2570e-166">array</span><span class="sxs-lookup"><span data-stu-id="2570e-166">array</span></span>  | <span data-ttu-id="2570e-167">Ein Array von Objekten, die Daten für die app enthalten.</span><span class="sxs-lookup"><span data-stu-id="2570e-167">An array of objects that contain insights data for the app.</span></span> <span data-ttu-id="2570e-168">Weitere Informationen zu den Daten in jedem-Objekt finden Sie unter [Einblicke Werte](#insight-values) im Abschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="2570e-168">For more information about the data in each object, see the [Insight values](#insight-values) section below.</span></span>                                                                                                                      |
| <span data-ttu-id="2570e-169">TotalCount</span><span class="sxs-lookup"><span data-stu-id="2570e-169">TotalCount</span></span> | <span data-ttu-id="2570e-170">int</span><span class="sxs-lookup"><span data-stu-id="2570e-170">int</span></span>    | <span data-ttu-id="2570e-171">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="2570e-171">The total number of rows in the data result for the query.</span></span>                 |


### <a name="insight-values"></a><span data-ttu-id="2570e-172">Insight Werte</span><span class="sxs-lookup"><span data-stu-id="2570e-172">Insight values</span></span>

<span data-ttu-id="2570e-173">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="2570e-173">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="2570e-174">Wert</span><span class="sxs-lookup"><span data-stu-id="2570e-174">Value</span></span>               | <span data-ttu-id="2570e-175">Typ</span><span class="sxs-lookup"><span data-stu-id="2570e-175">Type</span></span>   | <span data-ttu-id="2570e-176">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2570e-176">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="2570e-177">applicationId</span><span class="sxs-lookup"><span data-stu-id="2570e-177">applicationId</span></span>       | <span data-ttu-id="2570e-178">string</span><span class="sxs-lookup"><span data-stu-id="2570e-178">string</span></span> | <span data-ttu-id="2570e-179">Die Speicherobjekt-ID der app für die Sie Einblicke in die Daten abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2570e-179">The Store ID of the app for which you are retrieving insights data.</span></span>     |
| <span data-ttu-id="2570e-180">insightDate</span><span class="sxs-lookup"><span data-stu-id="2570e-180">insightDate</span></span>                | <span data-ttu-id="2570e-181">string</span><span class="sxs-lookup"><span data-stu-id="2570e-181">string</span></span> | <span data-ttu-id="2570e-182">Das Datum, an dem wir die Änderung in eine bestimmte Metrik identifiziert.</span><span class="sxs-lookup"><span data-stu-id="2570e-182">The date on which we identified the change in a specific metric.</span></span> <span data-ttu-id="2570e-183">Dieses Datum stellt das Ende der Woche, in dem wir eine erhebliche Steigerung erkannt, oder in eine Metrik in der Woche vor, die im Vergleich zu verringern.</span><span class="sxs-lookup"><span data-stu-id="2570e-183">This date represents the end of the week in which we detected a significant increase or decrease in a metric compared to the week before that.</span></span> |
| <span data-ttu-id="2570e-184">Datentyp</span><span class="sxs-lookup"><span data-stu-id="2570e-184">dataType</span></span>     | <span data-ttu-id="2570e-185">string</span><span class="sxs-lookup"><span data-stu-id="2570e-185">string</span></span> | <span data-ttu-id="2570e-186">Einer der folgenden Zeichenfolgen, die im Bereich mit den allgemeinen Analytics gibt an, dem diese Erkenntnisse beschrieben:</span><span class="sxs-lookup"><span data-stu-id="2570e-186">One of the following strings that specifies the general analytics area that this insight describes:</span></span><p/><ul><li><strong><span data-ttu-id="2570e-187">Erwerb</span><span class="sxs-lookup"><span data-stu-id="2570e-187">acquisition</span></span></strong></li><li><strong><span data-ttu-id="2570e-188">Integrität</span><span class="sxs-lookup"><span data-stu-id="2570e-188">health</span></span></strong></li><li><strong><span data-ttu-id="2570e-189">Verwendung</span><span class="sxs-lookup"><span data-stu-id="2570e-189">usage</span></span></strong></li></ul>   |
| <span data-ttu-id="2570e-190">insightDetail</span><span class="sxs-lookup"><span data-stu-id="2570e-190">insightDetail</span></span>          | <span data-ttu-id="2570e-191">array</span><span class="sxs-lookup"><span data-stu-id="2570e-191">array</span></span> | <span data-ttu-id="2570e-192">Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die die Details zur aktuellen Erkenntnisse darstellen.</span><span class="sxs-lookup"><span data-stu-id="2570e-192">One or more [InsightDetail values](#insightdetail-values) that represent the details for current insight.</span></span>    |


### <a name="insightdetail-values"></a><span data-ttu-id="2570e-193">InsightDetail Werte</span><span class="sxs-lookup"><span data-stu-id="2570e-193">InsightDetail values</span></span>

| <span data-ttu-id="2570e-194">Wert</span><span class="sxs-lookup"><span data-stu-id="2570e-194">Value</span></span>               | <span data-ttu-id="2570e-195">Typ</span><span class="sxs-lookup"><span data-stu-id="2570e-195">Type</span></span>   | <span data-ttu-id="2570e-196">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2570e-196">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="2570e-197">FactName</span><span class="sxs-lookup"><span data-stu-id="2570e-197">FactName</span></span>           | <span data-ttu-id="2570e-198">string</span><span class="sxs-lookup"><span data-stu-id="2570e-198">string</span></span> | <span data-ttu-id="2570e-199">Einer der folgenden Werte, die die Metrik gibt an, der dem aktuellen Erkenntnisse oder der aktuellen Dimension beschreibt, basierend auf der **DataType** -Wert.</span><span class="sxs-lookup"><span data-stu-id="2570e-199">One of the following values that indicates the metric that the current insight or current dimension describes, based on the **dataType** value.</span></span><ul><li><span data-ttu-id="2570e-200">Für die **Integrität**beträgt dieser Wert immer **HitCount**.</span><span class="sxs-lookup"><span data-stu-id="2570e-200">For **health**, this value is always **HitCount**.</span></span></li><li><span data-ttu-id="2570e-201">Für den **Erwerb**beträgt dieser Wert immer **AcquisitionQuantity**.</span><span class="sxs-lookup"><span data-stu-id="2570e-201">For **acquisition**, this value is always **AcquisitionQuantity**.</span></span></li><li><span data-ttu-id="2570e-202">Dieser Wert kann eine der folgenden Zeichenfolgen sein, für die **Verwendung**:</span><span class="sxs-lookup"><span data-stu-id="2570e-202">For **usage**, this value can be one of the following strings:</span></span><ul><li><strong><span data-ttu-id="2570e-203">DailyActiveUsers</span><span class="sxs-lookup"><span data-stu-id="2570e-203">DailyActiveUsers</span></span></strong></li><li><strong><span data-ttu-id="2570e-204">EngagementDurationMinutes</span><span class="sxs-lookup"><span data-stu-id="2570e-204">EngagementDurationMinutes</span></span></strong></li><li><strong><span data-ttu-id="2570e-205">DailyActiveDevices</span><span class="sxs-lookup"><span data-stu-id="2570e-205">DailyActiveDevices</span></span></strong></li><li><strong><span data-ttu-id="2570e-206">DailyNewUsers</span><span class="sxs-lookup"><span data-stu-id="2570e-206">DailyNewUsers</span></span></strong></li><li><strong><span data-ttu-id="2570e-207">DailySessionCount</span><span class="sxs-lookup"><span data-stu-id="2570e-207">DailySessionCount</span></span></strong></li></ul></ul>  |
| <span data-ttu-id="2570e-208">SubDimensions</span><span class="sxs-lookup"><span data-stu-id="2570e-208">SubDimensions</span></span>         | <span data-ttu-id="2570e-209">array</span><span class="sxs-lookup"><span data-stu-id="2570e-209">array</span></span> |  <span data-ttu-id="2570e-210">Ein oder mehrere Objekte, die eine einzelne Metrik für den Einblick beschreiben.</span><span class="sxs-lookup"><span data-stu-id="2570e-210">One or more objects that describe a single metric for the insight.</span></span>   |
| <span data-ttu-id="2570e-211">Änderung</span><span class="sxs-lookup"><span data-stu-id="2570e-211">PercentChange</span></span>            | <span data-ttu-id="2570e-212">string</span><span class="sxs-lookup"><span data-stu-id="2570e-212">string</span></span> |  <span data-ttu-id="2570e-213">Der Prozentsatz, den die Metrik über Ihre gesamte Kunden geändert.</span><span class="sxs-lookup"><span data-stu-id="2570e-213">The percentage that the metric changed across your entire customer base.</span></span>  |
| <span data-ttu-id="2570e-214">DimensionName</span><span class="sxs-lookup"><span data-stu-id="2570e-214">DimensionName</span></span>           | <span data-ttu-id="2570e-215">string</span><span class="sxs-lookup"><span data-stu-id="2570e-215">string</span></span> |  <span data-ttu-id="2570e-216">Der Name der Metrik in der aktuellen Dimension beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2570e-216">The name of the metric described in the current dimension.</span></span> <span data-ttu-id="2570e-217">Beispiele: **EventType**, **Land/Ihrer Region**, **DeviceType**, **PackageVersion**, **AcquisitionType**, **AgeGroup** und **Geschlecht**.</span><span class="sxs-lookup"><span data-stu-id="2570e-217">Examples include **EventType**, **Market**, **DeviceType**, **PackageVersion**, **AcquisitionType**, **AgeGroup** and **Gender**.</span></span>   |
| <span data-ttu-id="2570e-218">DimensionValue</span><span class="sxs-lookup"><span data-stu-id="2570e-218">DimensionValue</span></span>              | <span data-ttu-id="2570e-219">string</span><span class="sxs-lookup"><span data-stu-id="2570e-219">string</span></span> | <span data-ttu-id="2570e-220">Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="2570e-220">The value of the metric that is described in the current dimension.</span></span> <span data-ttu-id="2570e-221">Beispielsweise ist **DimensionName** **EventType**, **DimensionValue** **Absturz** **reagiert**möglicherweise oder.</span><span class="sxs-lookup"><span data-stu-id="2570e-221">For example, if **DimensionName** is **EventType**, **DimensionValue** might be **crash** or **hang**.</span></span>   |
| <span data-ttu-id="2570e-222">FactValue</span><span class="sxs-lookup"><span data-stu-id="2570e-222">FactValue</span></span>     | <span data-ttu-id="2570e-223">string</span><span class="sxs-lookup"><span data-stu-id="2570e-223">string</span></span> | <span data-ttu-id="2570e-224">Der Absolute Wert der Metrik auf das Datum, an das die Einblicke erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="2570e-224">The absolute value of the metric on the date the insight was detected.</span></span>  |
| <span data-ttu-id="2570e-225">Richtung</span><span class="sxs-lookup"><span data-stu-id="2570e-225">Direction</span></span> | <span data-ttu-id="2570e-226">string</span><span class="sxs-lookup"><span data-stu-id="2570e-226">string</span></span> |  <span data-ttu-id="2570e-227">Die Richtung der Änderung (**positiven** oder **negativen**).</span><span class="sxs-lookup"><span data-stu-id="2570e-227">The direction of the change (**Positive** or **Negative**).</span></span>   |
| <span data-ttu-id="2570e-228">Date</span><span class="sxs-lookup"><span data-stu-id="2570e-228">Date</span></span>              | <span data-ttu-id="2570e-229">String</span><span class="sxs-lookup"><span data-stu-id="2570e-229">string</span></span> |  <span data-ttu-id="2570e-230">Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Erkenntnisse oder die aktuelle Dimension identifiziert.</span><span class="sxs-lookup"><span data-stu-id="2570e-230">The date on which we identified the change related to the current insight or the current dimension.</span></span>   |

### <a name="response-example"></a><span data-ttu-id="2570e-231">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="2570e-231">Response example</span></span>

<span data-ttu-id="2570e-232">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="2570e-232">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="2570e-233">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2570e-233">Related topics</span></span>

* [<span data-ttu-id="2570e-234">Insights-Bericht</span><span class="sxs-lookup"><span data-stu-id="2570e-234">Insights report</span></span>](../publish/insights-report.md)
* [<span data-ttu-id="2570e-235">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="2570e-235">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
