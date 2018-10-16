---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von internen Daten für Ihre desktop-Anwendung.
title: Abrufen von internen Daten für die Desktopanwendung
ms.author: mhopkins
ms.date: 07/31/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Store-Dienste, Microsoft Store-Analyse-API, Einblicke
ms.localizationpriority: medium
ms.openlocfilehash: 0b4390fba26922372a74de76d09844a7243bce73
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "4689595"
---
# <a name="get-insights-data-for-your-desktop-application"></a><span data-ttu-id="e5b91-104">Abrufen von internen Daten für die Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="e5b91-104">Get insights data for your desktop application</span></span>

<span data-ttu-id="e5b91-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen von Einblicke zugehörige Daten auf Health Metrik für eine desktop-Anwendung, die Sie in der [Windows-desktopanwendungsprogramm](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="e5b91-105">Use this method in the Microsoft Store analytics API to get insights data related to health metrics for a desktop application that you have added to the [Windows Desktop Application program](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program).</span></span> <span data-ttu-id="e5b91-106">Diese Daten sind auch im [Bericht "Integrität"](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) für desktopanwendungen im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e5b91-106">This data is also available in the [Health report](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report) for desktop applications in the Windows Dev Center dashboard.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5b91-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e5b91-107">Prerequisites</span></span>

<span data-ttu-id="e5b91-108">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="e5b91-108">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="e5b91-109">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="e5b91-109">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="e5b91-110">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e5b91-110">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="e5b91-111">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="e5b91-111">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="e5b91-112">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="e5b91-112">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="e5b91-113">Anforderung</span><span class="sxs-lookup"><span data-stu-id="e5b91-113">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="e5b91-114">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="e5b91-114">Request syntax</span></span>

| <span data-ttu-id="e5b91-115">Methode</span><span class="sxs-lookup"><span data-stu-id="e5b91-115">Method</span></span> | <span data-ttu-id="e5b91-116">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="e5b91-116">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="e5b91-117">GET</span><span class="sxs-lookup"><span data-stu-id="e5b91-117">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights``` |


### <a name="request-header"></a><span data-ttu-id="e5b91-118">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="e5b91-118">Request header</span></span>

| <span data-ttu-id="e5b91-119">Header</span><span class="sxs-lookup"><span data-stu-id="e5b91-119">Header</span></span>        | <span data-ttu-id="e5b91-120">Typ</span><span class="sxs-lookup"><span data-stu-id="e5b91-120">Type</span></span>   | <span data-ttu-id="e5b91-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5b91-121">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="e5b91-122">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="e5b91-122">Authorization</span></span> | <span data-ttu-id="e5b91-123">String</span><span class="sxs-lookup"><span data-stu-id="e5b91-123">string</span></span> | <span data-ttu-id="e5b91-124">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e5b91-124">Required.</span></span> <span data-ttu-id="e5b91-125">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="e5b91-125">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="e5b91-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="e5b91-126">Request parameters</span></span>

| <span data-ttu-id="e5b91-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="e5b91-127">Parameter</span></span>        | <span data-ttu-id="e5b91-128">Typ</span><span class="sxs-lookup"><span data-stu-id="e5b91-128">Type</span></span>   |  <span data-ttu-id="e5b91-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5b91-129">Description</span></span>      |  <span data-ttu-id="e5b91-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="e5b91-130">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="e5b91-131">applicationId</span><span class="sxs-lookup"><span data-stu-id="e5b91-131">applicationId</span></span> | <span data-ttu-id="e5b91-132">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-132">string</span></span> | <span data-ttu-id="e5b91-133">Die Produkt-ID der Desktopanwendung, für die Abrufen von internen Daten werden soll.</span><span class="sxs-lookup"><span data-stu-id="e5b91-133">The product ID of the desktop application for which you want to get insights data.</span></span> <span data-ttu-id="e5b91-134">Um die Produkt-ID einer Desktopanwendung zu erhalten, öffnen Sie einen [Dev Center-Analysebericht für Ihre Desktopanwendung](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z.B. den **Integritätsbericht**) und rufen Sie die Produkt-ID aus der URL ab.</span><span class="sxs-lookup"><span data-stu-id="e5b91-134">To get the product ID of a desktop application, open any [Dev Center analytics report for your desktop application](https://msdn.microsoft.com/library/windows/desktop/mt826504) (such as the **Health report**) and retrieve the product ID from the URL.</span></span> <span data-ttu-id="e5b91-135">Wenn Sie diesen Parameter nicht angeben, enthält der Antworttext internen Daten für alle apps, die für Ihr Konto registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="e5b91-135">If you do not specify this parameter, the response body will contain insights data for all apps registered to your account.</span></span>  |  <span data-ttu-id="e5b91-136">Nein</span><span class="sxs-lookup"><span data-stu-id="e5b91-136">No</span></span>  |
| <span data-ttu-id="e5b91-137">startDate</span><span class="sxs-lookup"><span data-stu-id="e5b91-137">startDate</span></span> | <span data-ttu-id="e5b91-138">date</span><span class="sxs-lookup"><span data-stu-id="e5b91-138">date</span></span> | <span data-ttu-id="e5b91-139">Das Startdatum im Datumsbereich der internen Daten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e5b91-139">The start date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="e5b91-140">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="e5b91-140">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="e5b91-141">Nein</span><span class="sxs-lookup"><span data-stu-id="e5b91-141">No</span></span>  |
| <span data-ttu-id="e5b91-142">endDate</span><span class="sxs-lookup"><span data-stu-id="e5b91-142">endDate</span></span> | <span data-ttu-id="e5b91-143">date</span><span class="sxs-lookup"><span data-stu-id="e5b91-143">date</span></span> | <span data-ttu-id="e5b91-144">Das Enddatum im Datumsbereich der internen Daten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e5b91-144">The end date in the date range of insights data to retrieve.</span></span> <span data-ttu-id="e5b91-145">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="e5b91-145">The default is the current date.</span></span> |  <span data-ttu-id="e5b91-146">Nein</span><span class="sxs-lookup"><span data-stu-id="e5b91-146">No</span></span>  |
| <span data-ttu-id="e5b91-147">filter</span><span class="sxs-lookup"><span data-stu-id="e5b91-147">filter</span></span> | <span data-ttu-id="e5b91-148">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-148">string</span></span>  | <span data-ttu-id="e5b91-149">Mindestens eine Anweisung, die die Zeilen in der Antwort filtert.</span><span class="sxs-lookup"><span data-stu-id="e5b91-149">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="e5b91-150">Jede Anweisung enthält einen Feldnamen aus dem Antworttext und einen Wert, die mit den Operatoren **eq** oder **ne** verknüpft sind. Anweisungen können mit **and** oder **or** kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="e5b91-150">Each statement contains a field name from the response body and value that are associated with the **eq** or **ne** operators, and statements can be combined using **and** or **or**.</span></span> <span data-ttu-id="e5b91-151">Zeichenfolgenwerte im Parameter *filter* müssen von einfachen Anführungszeichen eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="e5b91-151">String values must be surrounded by single quotes in the *filter* parameter.</span></span> <span data-ttu-id="e5b91-152">Beispielsweise *Filter = DataType Eq 'Kauf"*.</span><span class="sxs-lookup"><span data-stu-id="e5b91-152">For example, *filter=dataType eq 'acquisition'*.</span></span> <p/><p/><span data-ttu-id="e5b91-153">Diese Methode unterstützt derzeit nur der Filter **Health**.</span><span class="sxs-lookup"><span data-stu-id="e5b91-153">Currently this method only supports the filter **health**.</span></span>  | <span data-ttu-id="e5b91-154">Nein</span><span class="sxs-lookup"><span data-stu-id="e5b91-154">No</span></span>   |

### <a name="request-example"></a><span data-ttu-id="e5b91-155">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="e5b91-155">Request example</span></span>

<span data-ttu-id="e5b91-156">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von internen Daten.</span><span class="sxs-lookup"><span data-stu-id="e5b91-156">The following example demonstrates a request for getting insights data.</span></span> <span data-ttu-id="e5b91-157">Ersetzen Sie den Wert *ApplicationId* , mit dem entsprechenden Wert für Ihre desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e5b91-157">Replace the *applicationId* value with the appropriate value for your desktop application.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/insights?applicationId=10238467886765136388&startDate=6/1/2018&endDate=6/15/2018&filter=dataType eq 'health' HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="e5b91-158">Antwort</span><span class="sxs-lookup"><span data-stu-id="e5b91-158">Response</span></span>

### <a name="response-body"></a><span data-ttu-id="e5b91-159">Antworttext</span><span class="sxs-lookup"><span data-stu-id="e5b91-159">Response body</span></span>

| <span data-ttu-id="e5b91-160">Wert</span><span class="sxs-lookup"><span data-stu-id="e5b91-160">Value</span></span>      | <span data-ttu-id="e5b91-161">Typ</span><span class="sxs-lookup"><span data-stu-id="e5b91-161">Type</span></span>   | <span data-ttu-id="e5b91-162">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5b91-162">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="e5b91-163">Wert</span><span class="sxs-lookup"><span data-stu-id="e5b91-163">Value</span></span>      | <span data-ttu-id="e5b91-164">array</span><span class="sxs-lookup"><span data-stu-id="e5b91-164">array</span></span>  | <span data-ttu-id="e5b91-165">Ein Array von Objekten, die internen Daten für die app enthalten.</span><span class="sxs-lookup"><span data-stu-id="e5b91-165">An array of objects that contain insights data for the app.</span></span> <span data-ttu-id="e5b91-166">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie weiter unten im Abschnitt [Insight Werte](#insight-values) .</span><span class="sxs-lookup"><span data-stu-id="e5b91-166">For more information about the data in each object, see the [Insight values](#insight-values) section below.</span></span>                                                                                                                      |
| <span data-ttu-id="e5b91-167">TotalCount</span><span class="sxs-lookup"><span data-stu-id="e5b91-167">TotalCount</span></span> | <span data-ttu-id="e5b91-168">int</span><span class="sxs-lookup"><span data-stu-id="e5b91-168">int</span></span>    | <span data-ttu-id="e5b91-169">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="e5b91-169">The total number of rows in the data result for the query.</span></span>                 |


### <a name="insight-values"></a><span data-ttu-id="e5b91-170">Insight Werte</span><span class="sxs-lookup"><span data-stu-id="e5b91-170">Insight values</span></span>

<span data-ttu-id="e5b91-171">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="e5b91-171">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="e5b91-172">Wert</span><span class="sxs-lookup"><span data-stu-id="e5b91-172">Value</span></span>               | <span data-ttu-id="e5b91-173">Typ</span><span class="sxs-lookup"><span data-stu-id="e5b91-173">Type</span></span>   | <span data-ttu-id="e5b91-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5b91-174">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="e5b91-175">applicationId</span><span class="sxs-lookup"><span data-stu-id="e5b91-175">applicationId</span></span>       | <span data-ttu-id="e5b91-176">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-176">string</span></span> | <span data-ttu-id="e5b91-177">Die Produkt-ID der Desktopanwendung, für die internen Daten abgerufen wurden.</span><span class="sxs-lookup"><span data-stu-id="e5b91-177">The product ID of the desktop application for which you retrieved insights data.</span></span>     |
| <span data-ttu-id="e5b91-178">insightDate</span><span class="sxs-lookup"><span data-stu-id="e5b91-178">insightDate</span></span>                | <span data-ttu-id="e5b91-179">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-179">string</span></span> | <span data-ttu-id="e5b91-180">Das Datum, an dem wir die Änderung in einer bestimmten Metrik identifiziert.</span><span class="sxs-lookup"><span data-stu-id="e5b91-180">The date on which we identified the change in a specific metric.</span></span> <span data-ttu-id="e5b91-181">Dieses Datum steht für das Ende der Woche, in dem wir eine erhebliche Erhöhung erkannt, oder in einer Metrik im Vergleich zur vorherigen Woche, verringern.</span><span class="sxs-lookup"><span data-stu-id="e5b91-181">This date represents the end of the week in which we detected a significant increase or decrease in a metric compared to the week before that.</span></span> |
| <span data-ttu-id="e5b91-182">Datentyp</span><span class="sxs-lookup"><span data-stu-id="e5b91-182">dataType</span></span>     | <span data-ttu-id="e5b91-183">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-183">string</span></span> | <span data-ttu-id="e5b91-184">Eine Zeichenfolge, die allgemeine Analysen Bereich angibt, den diese Insight informiert.</span><span class="sxs-lookup"><span data-stu-id="e5b91-184">A string that specifies the general analytics area that this insight informs.</span></span> <span data-ttu-id="e5b91-185">Diese Methode unterstützt derzeit nur **Integrität**.</span><span class="sxs-lookup"><span data-stu-id="e5b91-185">Currently, this method only supports **health**.</span></span>    |
| <span data-ttu-id="e5b91-186">insightDetail</span><span class="sxs-lookup"><span data-stu-id="e5b91-186">insightDetail</span></span>          | <span data-ttu-id="e5b91-187">array</span><span class="sxs-lookup"><span data-stu-id="e5b91-187">array</span></span> | <span data-ttu-id="e5b91-188">Eine oder mehrere [InsightDetail Werte](#insightdetail-values) , die Details für die aktuelle Insight darstellen.</span><span class="sxs-lookup"><span data-stu-id="e5b91-188">One or more [InsightDetail values](#insightdetail-values) that represent the details for current insight.</span></span>    |


### <a name="insightdetail-values"></a><span data-ttu-id="e5b91-189">InsightDetail Werte</span><span class="sxs-lookup"><span data-stu-id="e5b91-189">InsightDetail values</span></span>

| <span data-ttu-id="e5b91-190">Wert</span><span class="sxs-lookup"><span data-stu-id="e5b91-190">Value</span></span>               | <span data-ttu-id="e5b91-191">Typ</span><span class="sxs-lookup"><span data-stu-id="e5b91-191">Type</span></span>   | <span data-ttu-id="e5b91-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5b91-192">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="e5b91-193">FactName</span><span class="sxs-lookup"><span data-stu-id="e5b91-193">FactName</span></span>           | <span data-ttu-id="e5b91-194">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-194">string</span></span> | <span data-ttu-id="e5b91-195">Eine Zeichenfolge, die die Metrik gibt an, die den aktuellen Insight oder die aktuelle Dimension beschreibt.</span><span class="sxs-lookup"><span data-stu-id="e5b91-195">A string that indicates the metric that the current insight or current dimension describes.</span></span> <span data-ttu-id="e5b91-196">Diese Methode unterstützt derzeit nur den Wert **HitCount**.</span><span class="sxs-lookup"><span data-stu-id="e5b91-196">Currently, this method only supports the value **HitCount**.</span></span>  |
| <span data-ttu-id="e5b91-197">SubDimensions</span><span class="sxs-lookup"><span data-stu-id="e5b91-197">SubDimensions</span></span>         | <span data-ttu-id="e5b91-198">array</span><span class="sxs-lookup"><span data-stu-id="e5b91-198">array</span></span> |  <span data-ttu-id="e5b91-199">Ein oder mehrere Objekte, die eine einzelne Metrik für die Einblicke zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="e5b91-199">One or more objects that describe a single metric for the insight.</span></span>   |
| <span data-ttu-id="e5b91-200">Prozent</span><span class="sxs-lookup"><span data-stu-id="e5b91-200">PercentChange</span></span>            | <span data-ttu-id="e5b91-201">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-201">string</span></span> |  <span data-ttu-id="e5b91-202">Der Prozentsatz, den die Metrik über Ihres gesamten Kundenstamms geändert.</span><span class="sxs-lookup"><span data-stu-id="e5b91-202">The percentage that the metric changed across your entire customer base.</span></span>  |
| <span data-ttu-id="e5b91-203">DimensionName</span><span class="sxs-lookup"><span data-stu-id="e5b91-203">DimensionName</span></span>           | <span data-ttu-id="e5b91-204">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-204">string</span></span> |  <span data-ttu-id="e5b91-205">Der Name des die Metrik befindet sich in der aktuellen Dimension beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e5b91-205">The name of the metric described in the current dimension.</span></span> <span data-ttu-id="e5b91-206">Beispiele: **EventType**, **Markt**, **Gerätetyp**und **PackageVersion**.</span><span class="sxs-lookup"><span data-stu-id="e5b91-206">Examples include **EventType**, **Market**, **DeviceType**, and **PackageVersion**.</span></span>   |
| <span data-ttu-id="e5b91-207">DimensionValue</span><span class="sxs-lookup"><span data-stu-id="e5b91-207">DimensionValue</span></span>              | <span data-ttu-id="e5b91-208">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-208">string</span></span> | <span data-ttu-id="e5b91-209">Der Wert der Metrik, die in der aktuellen Dimension beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="e5b91-209">The value of the metric that is described in the current dimension.</span></span> <span data-ttu-id="e5b91-210">Kann z. B., wenn **DimensionName** **EventType**ist, **DimensionValue** **Absturz** oder **Blockade**.</span><span class="sxs-lookup"><span data-stu-id="e5b91-210">For example, if **DimensionName** is **EventType**, **DimensionValue** might be **crash** or **hang**.</span></span>   |
| <span data-ttu-id="e5b91-211">FactValue</span><span class="sxs-lookup"><span data-stu-id="e5b91-211">FactValue</span></span>     | <span data-ttu-id="e5b91-212">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-212">string</span></span> | <span data-ttu-id="e5b91-213">Der absoluten Wert des die Metrik befindet sich auf das Datum, an das die Einblicke erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="e5b91-213">The absolute value of the metric on the date the insight was detected.</span></span>  |
| <span data-ttu-id="e5b91-214">Richtung</span><span class="sxs-lookup"><span data-stu-id="e5b91-214">Direction</span></span> | <span data-ttu-id="e5b91-215">string</span><span class="sxs-lookup"><span data-stu-id="e5b91-215">string</span></span> |  <span data-ttu-id="e5b91-216">Die Richtung der Änderung (**positiv** oder **negativ**).</span><span class="sxs-lookup"><span data-stu-id="e5b91-216">The direction of the change (**Positive** or **Negative**).</span></span>   |
| <span data-ttu-id="e5b91-217">Date</span><span class="sxs-lookup"><span data-stu-id="e5b91-217">Date</span></span>              | <span data-ttu-id="e5b91-218">String</span><span class="sxs-lookup"><span data-stu-id="e5b91-218">string</span></span> |  <span data-ttu-id="e5b91-219">Das Datum, an dem wir die Änderung im Zusammenhang mit der aktuellen Insight oder die aktuelle Dimension identifiziert.</span><span class="sxs-lookup"><span data-stu-id="e5b91-219">The date on which we identified the change related to the current insight or the current dimension.</span></span>   |

### <a name="response-example"></a><span data-ttu-id="e5b91-220">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="e5b91-220">Response example</span></span>

<span data-ttu-id="e5b91-221">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="e5b91-221">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="e5b91-222">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e5b91-222">Related topics</span></span>

* [<span data-ttu-id="e5b91-223">Windows-desktopanwendungsprogramm</span><span class="sxs-lookup"><span data-stu-id="e5b91-223">Windows Desktop Application program</span></span>](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program)
* [<span data-ttu-id="e5b91-224">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="e5b91-224">Health report</span></span>](https://docs.microsoft.com/windows/desktop/appxpkg/windows-desktop-application-program#health-report)
* [<span data-ttu-id="e5b91-225">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="e5b91-225">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
