---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live gleichzeitige Nutzungsdaten abzurufen.
title: Abrufen von Xbox Live gleichzeitigen Nutzungsdaten
ms.author: mhopkins
ms.date: 06/04/2018
ms.topic: article
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live-Analyse, gleichzeitige Nutzung
ms.localizationpriority: medium
ms.openlocfilehash: 4506176dcd62a4699c57343c50dfc1b0e7a40b14
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5986152"
---
# <a name="get-xbox-live-concurrent-usage-data"></a><span data-ttu-id="8f69b-104">Abrufen von Xbox Live gleichzeitigen Nutzungsdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-104">Get Xbox Live concurrent usage data</span></span>


<span data-ttu-id="8f69b-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um fast in Echtzeit die Nutzungsdaten (mit 5-15-Minuten-Latenz) über die durchschnittliche Anzahl der Kunden abzurufen, die Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) jede Minute, Stunde oder Tag während eines angegebenen Zeitraums spielen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-105">Use this method in the Microsoft Store analytics API to get near real-time usage data (with 5-15 minutes latency) about the average number of customers playing your [Xbox Live-enabled game](../xbox-live/index.md) every minute, hour, or day during a specified time range.</span></span> <span data-ttu-id="8f69b-106">Diese Informationen sind auch im [Xbox Analysebericht](../publish/xbox-analytics-report.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8f69b-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in Partner Center.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f69b-107">Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="8f69b-107">This method only supports games for Xbox or games that use Xbox Live services.</span></span> <span data-ttu-id="8f69b-108">Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="8f69b-108">These games must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="8f69b-109">Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="8f69b-109">This method does not currently support games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f69b-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8f69b-110">Prerequisites</span></span>

<span data-ttu-id="8f69b-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="8f69b-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="8f69b-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="8f69b-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="8f69b-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8f69b-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="8f69b-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="8f69b-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="8f69b-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-115">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="8f69b-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="8f69b-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="8f69b-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="8f69b-117">Request syntax</span></span>

| <span data-ttu-id="8f69b-118">Methode</span><span class="sxs-lookup"><span data-stu-id="8f69b-118">Method</span></span> | <span data-ttu-id="8f69b-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="8f69b-119">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="8f69b-120">GET</span><span class="sxs-lookup"><span data-stu-id="8f69b-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="8f69b-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="8f69b-121">Request header</span></span>

| <span data-ttu-id="8f69b-122">Header</span><span class="sxs-lookup"><span data-stu-id="8f69b-122">Header</span></span>        | <span data-ttu-id="8f69b-123">Typ</span><span class="sxs-lookup"><span data-stu-id="8f69b-123">Type</span></span>   | <span data-ttu-id="8f69b-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8f69b-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="8f69b-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="8f69b-125">Authorization</span></span> | <span data-ttu-id="8f69b-126">String</span><span class="sxs-lookup"><span data-stu-id="8f69b-126">string</span></span> | <span data-ttu-id="8f69b-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8f69b-127">Required.</span></span> <span data-ttu-id="8f69b-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="8f69b-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="8f69b-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="8f69b-129">Request parameters</span></span>


| <span data-ttu-id="8f69b-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="8f69b-130">Parameter</span></span>        | <span data-ttu-id="8f69b-131">Typ</span><span class="sxs-lookup"><span data-stu-id="8f69b-131">Type</span></span>   |  <span data-ttu-id="8f69b-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8f69b-132">Description</span></span>      |  <span data-ttu-id="8f69b-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8f69b-133">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="8f69b-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="8f69b-134">applicationId</span></span> | <span data-ttu-id="8f69b-135">String</span><span class="sxs-lookup"><span data-stu-id="8f69b-135">string</span></span> | <span data-ttu-id="8f69b-136">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live gleichzeitigen Nutzungsdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-136">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live concurrent usage data.</span></span>  |  <span data-ttu-id="8f69b-137">Ja</span><span class="sxs-lookup"><span data-stu-id="8f69b-137">Yes</span></span>  |
| <span data-ttu-id="8f69b-138">metricType</span><span class="sxs-lookup"><span data-stu-id="8f69b-138">metricType</span></span> | <span data-ttu-id="8f69b-139">String</span><span class="sxs-lookup"><span data-stu-id="8f69b-139">string</span></span> | <span data-ttu-id="8f69b-140">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="8f69b-140">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="8f69b-141">Geben Sie für diese Methode den Wert **concurrency** an.</span><span class="sxs-lookup"><span data-stu-id="8f69b-141">For this method, specify the value **concurrency**.</span></span>  |  <span data-ttu-id="8f69b-142">Ja</span><span class="sxs-lookup"><span data-stu-id="8f69b-142">Yes</span></span>  |
| <span data-ttu-id="8f69b-143">startDate</span><span class="sxs-lookup"><span data-stu-id="8f69b-143">startDate</span></span> | <span data-ttu-id="8f69b-144">date</span><span class="sxs-lookup"><span data-stu-id="8f69b-144">date</span></span> | <span data-ttu-id="8f69b-145">Das Startdatum im Datumsbereich der gleichzeitigen Nutzungsdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-145">The start date in the date range of concurrent usage data to retrieve.</span></span> <span data-ttu-id="8f69b-146">Weitere Informationen finden Sie unter der *aggregationLevel*-Beschreibung für das Standardverhalten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-146">See the *aggregationLevel* description for default behavior.</span></span> |  <span data-ttu-id="8f69b-147">Nein</span><span class="sxs-lookup"><span data-stu-id="8f69b-147">No</span></span>  |
| <span data-ttu-id="8f69b-148">endDate</span><span class="sxs-lookup"><span data-stu-id="8f69b-148">endDate</span></span> | <span data-ttu-id="8f69b-149">date</span><span class="sxs-lookup"><span data-stu-id="8f69b-149">date</span></span> | <span data-ttu-id="8f69b-150">Das Enddatum im Datumsbereich der gleichzeitigen Nutzungsdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-150">The end date in the date range of concurrent usage data to retrieve.</span></span> <span data-ttu-id="8f69b-151">Weitere Informationen finden Sie unter der *aggregationLevel*-Beschreibung für das Standardverhalten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-151">See the *aggregationLevel* description for default behavior.</span></span> |  <span data-ttu-id="8f69b-152">Nein</span><span class="sxs-lookup"><span data-stu-id="8f69b-152">No</span></span>  |
| <span data-ttu-id="8f69b-153">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="8f69b-153">aggregationLevel</span></span> | <span data-ttu-id="8f69b-154">string</span><span class="sxs-lookup"><span data-stu-id="8f69b-154">string</span></span> | <span data-ttu-id="8f69b-155">Gibt den Zeitraum an, für den aggregierte Daten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-155">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="8f69b-156">Dies kann eine der folgenden Zeichenfolgen sein: **minute**, **hour** oder **day**.</span><span class="sxs-lookup"><span data-stu-id="8f69b-156">Can be one of the following strings: **minute**, **hour**, or **day**.</span></span> <span data-ttu-id="8f69b-157">Wenn keine Angabe erfolgt, lautet der Standardwert **day**.</span><span class="sxs-lookup"><span data-stu-id="8f69b-157">If unspecified, the default is **day**.</span></span> <p/><p/><span data-ttu-id="8f69b-158">Wenn Sie kein *startDate* oder *endDate* angeben, ist der Antworttext standardmäßig wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8f69b-158">If you do not specify *startDate* or *endDate*, the response body defaults to the following:</span></span> <ul><li><span data-ttu-id="8f69b-159">**minute**: Die letzten 60 Einträge an verfügbaren Daten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-159">**minute**: The last 60 records of available data.</span></span></li><li><span data-ttu-id="8f69b-160">**hour**: Die letzten 24 Einträge an verfügbaren Daten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-160">**hour**: The last 24 records of available data.</span></span></li><li><span data-ttu-id="8f69b-161">**day**: Die letzten 7 Einträge an verfügbaren Daten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-161">**day**: The last 7 records of available data.</span></span></li></ul><p/><span data-ttu-id="8f69b-162">Die folgenden Aggregationsebenen haben Größenbegrenzungen hinsichtlich der Anzahl von Datensätzen, die zurückgegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="8f69b-162">The following aggregation levels have size limits on the number of records that can be returned.</span></span> <span data-ttu-id="8f69b-163">Die Datensätze werden abgeschnitten, wenn die angeforderte Zeitspanne zu groß ist.</span><span class="sxs-lookup"><span data-stu-id="8f69b-163">The records will be truncated if the requested time span is too large.</span></span> <ul><li><span data-ttu-id="8f69b-164">**minute**: Bis zu 1440 Datensätze (24 Stunden an Daten).</span><span class="sxs-lookup"><span data-stu-id="8f69b-164">**minute**: Up to 1440 records (24 hours of data).</span></span></li><li><span data-ttu-id="8f69b-165">**hour**: Bis zu 720 Datensätze (30 Tage an Daten).</span><span class="sxs-lookup"><span data-stu-id="8f69b-165">**hour**: Up to 720 records (30 days of data).</span></span></li><li><span data-ttu-id="8f69b-166">**day**: Bis zu 60 Datensätze (60 Tage an Daten).</span><span class="sxs-lookup"><span data-stu-id="8f69b-166">**day**: Up to 60 records (60 days of data).</span></span></li></ul>  |  <span data-ttu-id="8f69b-167">Nein</span><span class="sxs-lookup"><span data-stu-id="8f69b-167">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="8f69b-168">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="8f69b-168">Request example</span></span>

<span data-ttu-id="8f69b-169">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von gleichzeitigen Nutzungsdaten für Ihr Xbox Live-fähiges Spiel an.</span><span class="sxs-lookup"><span data-stu-id="8f69b-169">The following example demonstrates a request for getting concurrent usage data for your Xbox Live-enabled game.</span></span> <span data-ttu-id="8f69b-170">Diese Anforderung ruft Daten für jede Minute zwischen dem 1. Februar 2018 und 2. Februar 2018 ab.</span><span class="sxs-lookup"><span data-stu-id="8f69b-170">This request retrieves data for every minute between February 1 2018 and February 2 2018.</span></span> <span data-ttu-id="8f69b-171">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="8f69b-171">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=concurrency&aggregationLevel=hour&startDate=2018-02-01&endData=2018-02-02 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="8f69b-172">Antwort</span><span class="sxs-lookup"><span data-stu-id="8f69b-172">Response</span></span>

<span data-ttu-id="8f69b-173">Der Antworttext enthält ein Array von Objekten, die jeweils einen Satz von gleichzeitigen Nutzungsdaten für eine angegebene Minute, Stunde oder Tag enthalten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-173">The response body contains an array of objects that each contain one set of concurrent usage data for a specified minute, hour, or day.</span></span> <span data-ttu-id="8f69b-174">Jedes Objekt enthält die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="8f69b-174">Each object contains the following values.</span></span>

| <span data-ttu-id="8f69b-175">Wert</span><span class="sxs-lookup"><span data-stu-id="8f69b-175">Value</span></span>      | <span data-ttu-id="8f69b-176">Typ</span><span class="sxs-lookup"><span data-stu-id="8f69b-176">Type</span></span>   | <span data-ttu-id="8f69b-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8f69b-177">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="8f69b-178">Anzahl</span><span class="sxs-lookup"><span data-stu-id="8f69b-178">Count</span></span>      | <span data-ttu-id="8f69b-179">number</span><span class="sxs-lookup"><span data-stu-id="8f69b-179">number</span></span>  | <span data-ttu-id="8f69b-180">Die durchschnittliche Anzahl der Kunden, die Ihr Xbox Live-fähiges Spiel für die angegebene Minute, Stunde oder Tag spielen.</span><span class="sxs-lookup"><span data-stu-id="8f69b-180">The average number of customers playing your Xbox Live-enabled for the specified minute, hour, or day.</span></span> <p/><p/><span data-ttu-id="8f69b-181">**Hinweis:**&nbsp;&nbsp;Ein Wert von 0 gibt an, dass entweder keine gleichzeitigen Benutzer während des angegebenen Intervalls spielten, oder dass beim Sammeln von gleichzeitigen Benutzerdaten für das Spiel während des angegebenen Intervalls ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="8f69b-181">**Note**&nbsp;&nbsp;A value of 0 indicates either that there were no concurrent users during the specified interval, or that there was a failure while collecting concurrent user data for the game during the specified interval.</span></span> |
| <span data-ttu-id="8f69b-182">Date</span><span class="sxs-lookup"><span data-stu-id="8f69b-182">Date</span></span>  | <span data-ttu-id="8f69b-183">String</span><span class="sxs-lookup"><span data-stu-id="8f69b-183">string</span></span> | <span data-ttu-id="8f69b-184">Das Datum und Uhrzeit, die die Minute, Stunde oder Tag angeben, während dessen die gleichzeitigen Nutzungsdaten auftraten.</span><span class="sxs-lookup"><span data-stu-id="8f69b-184">The date and time that specifies the minute, hour or day during which the concurrent usage data occurred.</span></span>  |
| <span data-ttu-id="8f69b-185">SeriesName</span><span class="sxs-lookup"><span data-stu-id="8f69b-185">SeriesName</span></span> | <span data-ttu-id="8f69b-186">String</span><span class="sxs-lookup"><span data-stu-id="8f69b-186">string</span></span>    | <span data-ttu-id="8f69b-187">Dies hat immer den Wert **UserConcurrency**.</span><span class="sxs-lookup"><span data-stu-id="8f69b-187">This always has the value **UserConcurrency**.</span></span> |


### <a name="response-example"></a><span data-ttu-id="8f69b-188">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="8f69b-188">Response example</span></span>

<span data-ttu-id="8f69b-189">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung mit Datenaggregation pro Minute.</span><span class="sxs-lookup"><span data-stu-id="8f69b-189">The following example demonstrates an example JSON response body for this request with data aggregation by minute.</span></span>

```json
[   {
        "Count": 418.0,
        "Date": "2018-02-02T04:42:13.65Z",
        "SeriesName": "UserConcurrency"
    }, {
        "Count": 418.0,
        "Date": "2018-02-02T04:43:13.65Z",
        "SeriesName": "UserConcurrency"
    }, {
        "Count": 415.0,
        "Date": "2018-02-02T04:44:13.65Z",
        "SeriesName": "UserConcurrency"
    }, {
        "Count": 412.0,
        "Date": "2018-02-02T04:45:13.65Z",
        "SeriesName": "UserConcurrency"
    }, {
        "Count": 414.0,
        "Date": "2018-02-02T04:46:13.65Z",
        "SeriesName": "UserConcurrency"
    }
]
```

## <a name="related-topics"></a><span data-ttu-id="8f69b-190">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8f69b-190">Related topics</span></span>

* [<span data-ttu-id="8f69b-191">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="8f69b-191">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="8f69b-192">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-192">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="8f69b-193">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-193">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="8f69b-194">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-194">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="8f69b-195">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-195">Get Xbox Live game hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="8f69b-196">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-196">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="8f69b-197">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="8f69b-197">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
