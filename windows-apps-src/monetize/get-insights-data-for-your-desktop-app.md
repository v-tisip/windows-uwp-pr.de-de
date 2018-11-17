---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von internen Daten für Ihre desktop-Anwendung.
title: Abrufen von internen Daten für die Desktopanwendung
ms.author: mhopkins
ms.date: 07/31/2018
ms.topic: article
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Einblicke
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: bf3407e94270b8c067d6e4ab088d33990ae22abb
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7150788"
---
# <a name="get-insights-data-for-your-desktop-application"></a><span data-ttu-id="be6d6-104">Abrufen von internen Daten für die Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="be6d6-104">Get insights data for your desktop application</span></span>

<span data-ttu-id="be6d6-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von Einblicken, die zugehörige Daten auf Integrität Metrik für eine desktop-Anwendung, die für das [Windows-desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="be6d6-105">Use this method in the Microsoft Store analytics API to get insights data related to health metrics for a desktop application that you have added to the [Windows Desktop Application program](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program).</span></span> <span data-ttu-id="be6d6-106">Diese Daten werden auch im [Bericht "Integrität"](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) für desktopanwendungen im Partner Center.</span><span class="sxs-lookup"><span data-stu-id="be6d6-106">This data is also available in the [Health report](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) for desktop applications in Partner Center.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be6d6-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="be6d6-107">Prerequisites</span></span>

<span data-ttu-id="be6d6-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="be6d6-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="be6d6-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="be6d6-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="be6d6-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="be6d6-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="be6d6-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="be6d6-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="be6d6-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="be6d6-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="be6d6-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="be6d6-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="be6d6-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="be6d6-114">Request syntax</span></span>

| <span data-ttu-id="be6d6-115">Methode</span><span class="sxs-lookup"><span data-stu-id="be6d6-115">Method</span></span> | <span data-ttu-id="be6d6-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="be6d6-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="be6d6-117">GET</span><span class="sxs-lookup"><span data-stu-id="be6d6-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights``` |


### <a name="request-header"></a><span data-ttu-id="be6d6-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="be6d6-118">Request header</span></span>

| <span data-ttu-id="be6d6-119">Header</span><span class="sxs-lookup"><span data-stu-id="be6d6-119">Header</span></span>        | <span data-ttu-id="be6d6-120">Typ</span><span class="sxs-lookup"><span data-stu-id="be6d6-120">Type</span></span>   | <span data-ttu-id="be6d6-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be6d6-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="be6d6-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="be6d6-122">Authorization</span></span> | <span data-ttu-id="be6d6-123">String</span><span class="sxs-lookup"><span data-stu-id="be6d6-123">string</span></span> | <span data-ttu-id="be6d6-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="be6d6-124">Required.</span></span> <span data-ttu-id="be6d6-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="be6d6-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="be6d6-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="be6d6-126">Request parameters</span></span>

| <span data-ttu-id="be6d6-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="be6d6-127">Parameter</span></span>        | <span data-ttu-id="be6d6-128">Typ</span><span class="sxs-lookup"><span data-stu-id="be6d6-128">Type</span></span>   |  <span data-ttu-id="be6d6-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be6d6-129">Description</span></span>      |  <span data-ttu-id="be6d6-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="be6d6-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="be6d6-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="be6d6-131">applicationId</span></span> | <span data-ttu-id="be6d6-132">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-132">string</span></span> | <span data-ttu-id="be6d6-133">Die Produkt-ID der Desktopanwendung, für die Abrufen von internen Daten werden soll.</span><span class="sxs-lookup"><span data-stu-id="be6d6-133">The product ID of the desktop application for which you want to get insights data.</span></span> <span data-ttu-id="be6d6-134">Um die Produkt-ID einer desktop-Anwendung zu erhalten, öffnen Sie alle [-Analysebericht für Ihre desktop-Anwendung im Partner Center](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z. B. den **Bericht "Integrität"**), und rufen Sie die Produkt-ID aus der URL.</span><span class="sxs-lookup"><span data-stu-id="be6d6-134">To get the product ID of a desktop application, open any [analytics report for your desktop application in Partner Center](https://msdn.microsoft.com/library/windows/desktop/mt826504) (such as the **Health report**) and retrieve the product ID from the URL.</span></span> <span data-ttu-id="be6d6-135">Wenn Sie diesen Parameter nicht angeben, enthält der Antworttext internen Daten für alle apps, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="be6d6-135">If you do not specify this parameter, the response body will contain insights data for all apps registered to your account.</span></span>  |  <span data-ttu-id="be6d6-136">Nein</span><span class="sxs-lookup"><span data-stu-id="be6d6-136">No</span></span>  |
| <span data-ttu-id="be6d6-137">startDate</span><span class="sxs-lookup"><span data-stu-id="be6d6-137">startDate</span></span> | <span data-ttu-id="be6d6-138">date</span><span class="sxs-lookup"><span data-stu-id="be6d6-138">date</span></span> | <span data-ttu-id="be6d6-139">Das Startdatum im Datumsbereich der internen Daten abgerufen.</span><span class="sxs-lookup"><span data-stu-id="be6d6-139">The start date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="be6d6-140">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="be6d6-140">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="be6d6-141">Nein</span><span class="sxs-lookup"><span data-stu-id="be6d6-141">No</span></span>  |
| <span data-ttu-id="be6d6-142">endDate</span><span class="sxs-lookup"><span data-stu-id="be6d6-142">endDate</span></span> | <span data-ttu-id="be6d6-143">date</span><span class="sxs-lookup"><span data-stu-id="be6d6-143">date</span></span> | <span data-ttu-id="be6d6-144">Das Enddatum im Datumsbereich der internen Daten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="be6d6-144">The end date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="be6d6-145">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="be6d6-145">The default is the current date.</span></span> |  <span data-ttu-id="be6d6-146">Nein</span><span class="sxs-lookup"><span data-stu-id="be6d6-146">No</span></span>  |
| <span data-ttu-id="be6d6-147">filter</span><span class="sxs-lookup"><span data-stu-id="be6d6-147">filter</span></span> | <span data-ttu-id="be6d6-148">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-148">string</span></span>  | <span data-ttu-id="be6d6-149">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="be6d6-149">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="be6d6-150">Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="be6d6-150">Each statement contains a field name from the response body and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span> <span data-ttu-id="be6d6-151">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="be6d6-151">String values must be surrounded by single quotes in the *filter* parameter.</span></span> <span data-ttu-id="be6d6-152">Beispielsweise *Filter = DataType Eq 'Erwerb'*.</span><span class="sxs-lookup"><span data-stu-id="be6d6-152">For example, *filter=dataType eq 'acquisition'*.</span></span> <p/><p/><span data-ttu-id="be6d6-153">Diese Methode unterstützt derzeit nur der Filter- **Integrität**.</span><span class="sxs-lookup"><span data-stu-id="be6d6-153">Currently this method only supports the filter **health**.</span></span>  | <span data-ttu-id="be6d6-154">Nein</span><span class="sxs-lookup"><span data-stu-id="be6d6-154">No</span></span>   |

### <a name="request-example"></a><span data-ttu-id="be6d6-155">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="be6d6-155">Request example</span></span>

<span data-ttu-id="be6d6-156">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von internen Daten.</span><span class="sxs-lookup"><span data-stu-id="be6d6-156">The following example demonstrates a request for getting insights data.</span></span> <span data-ttu-id="be6d6-157">Ersetzen Sie den Wert *ApplicationId* , mit dem entsprechenden Wert für Ihre desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="be6d6-157">Replace the *applicationId* value with the appropriate value for your desktop application.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights?applicationId=10238467886765136388&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="be6d6-158">Antwort</span><span class="sxs-lookup"><span data-stu-id="be6d6-158">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="be6d6-159">Antworttext</span><span class="sxs-lookup"><span data-stu-id="be6d6-159">Response body</span></span>

| <span data-ttu-id="be6d6-160">Wert</span><span class="sxs-lookup"><span data-stu-id="be6d6-160">Value</span></span>      | <span data-ttu-id="be6d6-161">Typ</span><span class="sxs-lookup"><span data-stu-id="be6d6-161">Type</span></span>   | <span data-ttu-id="be6d6-162">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be6d6-162">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="be6d6-163">Wert</span><span class="sxs-lookup"><span data-stu-id="be6d6-163">Value</span></span>      | <span data-ttu-id="be6d6-164">array</span><span class="sxs-lookup"><span data-stu-id="be6d6-164">array</span></span>  | <span data-ttu-id="be6d6-165">Ein Array von Objekten, die internen Daten für die app enthalten.</span><span class="sxs-lookup"><span data-stu-id="be6d6-165">An array of objects that contain insights data for the app.</span></span> <span data-ttu-id="be6d6-166">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie weiter unten im Abschnitt [Insight Werte](#insight-values) .</span><span class="sxs-lookup"><span data-stu-id="be6d6-166">For more information about the data in each object, see the [Insight values](#insight-values) section below.</span></span>                                                                                                                      |
| <span data-ttu-id="be6d6-167">TotalCount</span><span class="sxs-lookup"><span data-stu-id="be6d6-167">TotalCount</span></span> | <span data-ttu-id="be6d6-168">int</span><span class="sxs-lookup"><span data-stu-id="be6d6-168">int</span></span>    | <span data-ttu-id="be6d6-169">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="be6d6-169">The total number of rows in the data result for the query.</span></span>                 |


### <a name="insight-values"></a><span data-ttu-id="be6d6-170">Interne Werte</span><span class="sxs-lookup"><span data-stu-id="be6d6-170">Insight values</span></span>

<span data-ttu-id="be6d6-171">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="be6d6-171">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="be6d6-172">Wert</span><span class="sxs-lookup"><span data-stu-id="be6d6-172">Value</span></span>               | <span data-ttu-id="be6d6-173">Typ</span><span class="sxs-lookup"><span data-stu-id="be6d6-173">Type</span></span>   | <span data-ttu-id="be6d6-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be6d6-174">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="be6d6-175">applicationId</span><span class="sxs-lookup"><span data-stu-id="be6d6-175">applicationId</span></span>       | <span data-ttu-id="be6d6-176">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-176">string</span></span> | <span data-ttu-id="be6d6-177">Die Produkt-ID der Desktopanwendung, für die internen Daten abgerufen wurden.</span><span class="sxs-lookup"><span data-stu-id="be6d6-177">The product ID of the desktop application for which you retrieved insights data.</span></span>     |
| <span data-ttu-id="be6d6-178">insightDate</span><span class="sxs-lookup"><span data-stu-id="be6d6-178">insightDate</span></span>                | <span data-ttu-id="be6d6-179">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-179">string</span></span> | <span data-ttu-id="be6d6-180">Das Datum, an dem wir die Änderung in einer bestimmten Metrik identifiziert.</span><span class="sxs-lookup"><span data-stu-id="be6d6-180">The date on which we identified the change in a specific metric.</span></span> <span data-ttu-id="be6d6-181">Dieses Datum stellt das Ende der Woche, in dem wir eine erhebliche Erhöhung erkannt, oder in einer Metrik im Vergleich zur vorherigen Woche, verringern.</span><span class="sxs-lookup"><span data-stu-id="be6d6-181">This date represents the end of the week in which we detected a significant increase or decrease in a metric compared to the week before that.</span></span> |
| <span data-ttu-id="be6d6-182">Datentyp</span><span class="sxs-lookup"><span data-stu-id="be6d6-182">dataType</span></span>     | <span data-ttu-id="be6d6-183">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-183">string</span></span> | <span data-ttu-id="be6d6-184">Eine Zeichenfolge, die allgemeine Analysen Bereich angibt, den diese Insight informiert.</span><span class="sxs-lookup"><span data-stu-id="be6d6-184">A string that specifies the general analytics area that this insight informs.</span></span> <span data-ttu-id="be6d6-185">Diese Methode unterstützt derzeit nur **Integrität**.</span><span class="sxs-lookup"><span data-stu-id="be6d6-185">Currently, this method only supports **health**.</span></span>    |
| <span data-ttu-id="be6d6-186">insightDetail</span><span class="sxs-lookup"><span data-stu-id="be6d6-186">insightDetail</span></span>          | <span data-ttu-id="be6d6-187">array</span><span class="sxs-lookup"><span data-stu-id="be6d6-187">array</span></span> | <span data-ttu-id="be6d6-188">Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die Details für aktuelle Insight darstellen.</span><span class="sxs-lookup"><span data-stu-id="be6d6-188">One or more [InsightDetail values](#insightdetail-values) that represent the details for current insight.</span></span>    |


### <a name="insightdetail-values"></a><span data-ttu-id="be6d6-189">InsightDetail Werte</span><span class="sxs-lookup"><span data-stu-id="be6d6-189">InsightDetail values</span></span>

| <span data-ttu-id="be6d6-190">Wert</span><span class="sxs-lookup"><span data-stu-id="be6d6-190">Value</span></span>               | <span data-ttu-id="be6d6-191">Typ</span><span class="sxs-lookup"><span data-stu-id="be6d6-191">Type</span></span>   | <span data-ttu-id="be6d6-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be6d6-192">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="be6d6-193">FactName</span><span class="sxs-lookup"><span data-stu-id="be6d6-193">FactName</span></span>           | <span data-ttu-id="be6d6-194">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-194">string</span></span> | <span data-ttu-id="be6d6-195">Eine Zeichenfolge, die die Metrik gibt an, die den aktuellen Insight oder die aktuelle Dimension beschreibt.</span><span class="sxs-lookup"><span data-stu-id="be6d6-195">A string that indicates the metric that the current insight or current dimension describes.</span></span> <span data-ttu-id="be6d6-196">Diese Methode unterstützt derzeit nur den Wert **HitCount**.</span><span class="sxs-lookup"><span data-stu-id="be6d6-196">Currently, this method only supports the value **HitCount**.</span></span>  |
| <span data-ttu-id="be6d6-197">SubDimensions</span><span class="sxs-lookup"><span data-stu-id="be6d6-197">SubDimensions</span></span>         | <span data-ttu-id="be6d6-198">array</span><span class="sxs-lookup"><span data-stu-id="be6d6-198">array</span></span> |  <span data-ttu-id="be6d6-199">Ein oder mehrere Objekte, die eine einzelne Metrik für die Einblicke zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="be6d6-199">One or more objects that describe a single metric for the insight.</span></span>   |
| <span data-ttu-id="be6d6-200">Prozent</span><span class="sxs-lookup"><span data-stu-id="be6d6-200">PercentChange</span></span>            | <span data-ttu-id="be6d6-201">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-201">string</span></span> |  <span data-ttu-id="be6d6-202">Der Prozentsatz, den die Metrik über Ihres gesamten Kundenstamms geändert.</span><span class="sxs-lookup"><span data-stu-id="be6d6-202">The percentage that the metric changed across your entire customer base.</span></span>  |
| <span data-ttu-id="be6d6-203">DimensionName</span><span class="sxs-lookup"><span data-stu-id="be6d6-203">DimensionName</span></span>           | <span data-ttu-id="be6d6-204">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-204">string</span></span> |  <span data-ttu-id="be6d6-205">Der Name des die Metrik befindet sich in der aktuellen Dimension beschrieben.</span><span class="sxs-lookup"><span data-stu-id="be6d6-205">The name of the metric described in the current dimension.</span></span> <span data-ttu-id="be6d6-206">Beispiele sind **EventType**, **Markt**, **Gerätetyp**und **PackageVersion**.</span><span class="sxs-lookup"><span data-stu-id="be6d6-206">Examples include **EventType**, **Market**, **DeviceType**, and **PackageVersion**.</span></span>   |
| <span data-ttu-id="be6d6-207">DimensionValue</span><span class="sxs-lookup"><span data-stu-id="be6d6-207">DimensionValue</span></span>              | <span data-ttu-id="be6d6-208">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-208">string</span></span> | <span data-ttu-id="be6d6-209">Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="be6d6-209">The value of the metric that is described in the current dimension.</span></span> <span data-ttu-id="be6d6-210">Beispielsweise ist **DimensionName** **EventType**, **DimensionValue** **Absturz** oder **Blockade**möglicherweise.</span><span class="sxs-lookup"><span data-stu-id="be6d6-210">For example, if **DimensionName** is **EventType**, **DimensionValue** might be **crash** or **hang**.</span></span>   |
| <span data-ttu-id="be6d6-211">FactValue</span><span class="sxs-lookup"><span data-stu-id="be6d6-211">FactValue</span></span>     | <span data-ttu-id="be6d6-212">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-212">string</span></span> | <span data-ttu-id="be6d6-213">Der absoluten Wert der Metrik auf das Datum, an das die Einblicke erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="be6d6-213">The absolute value of the metric on the date the insight was detected.</span></span>  |
| <span data-ttu-id="be6d6-214">Richtung</span><span class="sxs-lookup"><span data-stu-id="be6d6-214">Direction</span></span> | <span data-ttu-id="be6d6-215">string</span><span class="sxs-lookup"><span data-stu-id="be6d6-215">string</span></span> |  <span data-ttu-id="be6d6-216">Die Richtung der Änderung (**positiv** oder **negativ**).</span><span class="sxs-lookup"><span data-stu-id="be6d6-216">The direction of the change (**Positive** or **Negative**).</span></span>   |
| <span data-ttu-id="be6d6-217">Date</span><span class="sxs-lookup"><span data-stu-id="be6d6-217">Date</span></span>              | <span data-ttu-id="be6d6-218">String</span><span class="sxs-lookup"><span data-stu-id="be6d6-218">string</span></span> |  <span data-ttu-id="be6d6-219">Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Insight oder die aktuelle Dimension identifiziert.</span><span class="sxs-lookup"><span data-stu-id="be6d6-219">The date on which we identified the change related to the current insight or the current dimension.</span></span>   |

### <a name="response-example"></a><span data-ttu-id="be6d6-220">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="be6d6-220">Response example</span></span>

<span data-ttu-id="be6d6-221">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="be6d6-221">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="be6d6-222">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="be6d6-222">Related topics</span></span>

* [<span data-ttu-id="be6d6-223">Windows-desktopanwendungsprogramm</span><span class="sxs-lookup"><span data-stu-id="be6d6-223">Windows Desktop Application program</span></span>](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
* [<span data-ttu-id="be6d6-224">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="be6d6-224">Health report</span></span>](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report)
* [<span data-ttu-id="be6d6-225">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="be6d6-225">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
