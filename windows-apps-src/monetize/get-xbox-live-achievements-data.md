---
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Erfolgsdaten abzurufen.
title: Abrufen von Xbox Live Erfolgsdaten
ms.date: 06/04/2018
ms.topic: article
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live-Analyse, Erfolge
ms.localizationpriority: medium
ms.openlocfilehash: 23a99c637dfd466ba21169626315803dec60e4e8
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8784132"
---
# <a name="get-xbox-live-achievements-data"></a><span data-ttu-id="18038-104">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="18038-104">Get Xbox Live achievements data</span></span>

<span data-ttu-id="18038-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Anzahl der Kunden zu erhalten, die jeden Erfolg für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) freigeschaltet haben, und zwar während des letzten Tages, für den Erfolgsdaten verfügbar sind, für die vorherigen 30Tage vor diesem Tag und über die gesamte Lebensdauer des Spiels bis zu diesem Tag.</span><span class="sxs-lookup"><span data-stu-id="18038-105">Use this method in the Microsoft Store analytics API to get the number of customers who have unlocked each achievement for your [Xbox Live-enabled game](../xbox-live/index.md) during the most recent day for which achievements data is available, the previous 30 days leading up to that day, and the total lifetime of your game up to that day.</span></span> <span data-ttu-id="18038-106">Diese Informationen sind auch in der [Xbox Analysebericht](../publish/xbox-analytics-report.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="18038-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in Partner Center.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18038-107">Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="18038-107">This method only supports games for Xbox or games that use Xbox Live services.</span></span> <span data-ttu-id="18038-108">Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="18038-108">These games must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="18038-109">Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="18038-109">This method does not currently support games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18038-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="18038-110">Prerequisites</span></span>

<span data-ttu-id="18038-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="18038-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="18038-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="18038-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="18038-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="18038-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="18038-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="18038-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="18038-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="18038-115">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="18038-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="18038-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="18038-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="18038-117">Request syntax</span></span>

| <span data-ttu-id="18038-118">Methode</span><span class="sxs-lookup"><span data-stu-id="18038-118">Method</span></span> | <span data-ttu-id="18038-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="18038-119">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="18038-120">GET</span><span class="sxs-lookup"><span data-stu-id="18038-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="18038-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="18038-121">Request header</span></span>

| <span data-ttu-id="18038-122">Header</span><span class="sxs-lookup"><span data-stu-id="18038-122">Header</span></span>        | <span data-ttu-id="18038-123">Typ</span><span class="sxs-lookup"><span data-stu-id="18038-123">Type</span></span>   | <span data-ttu-id="18038-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="18038-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="18038-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="18038-125">Authorization</span></span> | <span data-ttu-id="18038-126">String</span><span class="sxs-lookup"><span data-stu-id="18038-126">string</span></span> | <span data-ttu-id="18038-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="18038-127">Required.</span></span> <span data-ttu-id="18038-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="18038-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="18038-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="18038-129">Request parameters</span></span>


| <span data-ttu-id="18038-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="18038-130">Parameter</span></span>        | <span data-ttu-id="18038-131">Typ</span><span class="sxs-lookup"><span data-stu-id="18038-131">Type</span></span>   |  <span data-ttu-id="18038-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="18038-132">Description</span></span>      |  <span data-ttu-id="18038-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="18038-133">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="18038-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="18038-134">applicationId</span></span> | <span data-ttu-id="18038-135">String</span><span class="sxs-lookup"><span data-stu-id="18038-135">string</span></span> | <span data-ttu-id="18038-136">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Erfolgsdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="18038-136">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live achievements data.</span></span>  |  <span data-ttu-id="18038-137">Ja</span><span class="sxs-lookup"><span data-stu-id="18038-137">Yes</span></span>  |
| <span data-ttu-id="18038-138">metricType</span><span class="sxs-lookup"><span data-stu-id="18038-138">metricType</span></span> | <span data-ttu-id="18038-139">String</span><span class="sxs-lookup"><span data-stu-id="18038-139">string</span></span> | <span data-ttu-id="18038-140">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live-Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="18038-140">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="18038-141">Geben Sie für diese Methode den Wert **achievements** an.</span><span class="sxs-lookup"><span data-stu-id="18038-141">For this method, specify the value **achievements**.</span></span>  |  <span data-ttu-id="18038-142">Ja</span><span class="sxs-lookup"><span data-stu-id="18038-142">Yes</span></span>  |
| <span data-ttu-id="18038-143">top</span><span class="sxs-lookup"><span data-stu-id="18038-143">top</span></span> | <span data-ttu-id="18038-144">int</span><span class="sxs-lookup"><span data-stu-id="18038-144">int</span></span> | <span data-ttu-id="18038-145">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="18038-145">The number of rows of data to return in the request.</span></span> <span data-ttu-id="18038-146">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="18038-146">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="18038-147">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="18038-147">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="18038-148">Nein</span><span class="sxs-lookup"><span data-stu-id="18038-148">No</span></span>  |
| <span data-ttu-id="18038-149">skip</span><span class="sxs-lookup"><span data-stu-id="18038-149">skip</span></span> | <span data-ttu-id="18038-150">int</span><span class="sxs-lookup"><span data-stu-id="18038-150">int</span></span> | <span data-ttu-id="18038-151">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="18038-151">The number of rows to skip in the query.</span></span> <span data-ttu-id="18038-152">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="18038-152">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="18038-153">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="18038-153">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="18038-154">Nein</span><span class="sxs-lookup"><span data-stu-id="18038-154">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="18038-155">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="18038-155">Request example</span></span>

<span data-ttu-id="18038-156">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Erfolgsdaten für Kunden, die die ersten 10 Erfolge für Ihr Xbox Live-fähiges Spiel entsperrt haben.</span><span class="sxs-lookup"><span data-stu-id="18038-156">The following example demonstrates a request for getting achievements data for customers who have unlocked the first 10 achievements for your Xbox Live-enabled game.</span></span> <span data-ttu-id="18038-157">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="18038-157">Replace the *applicationId* value with the Store ID for your game.</span></span>


```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=achievements&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="18038-158">Antwort</span><span class="sxs-lookup"><span data-stu-id="18038-158">Response</span></span>

| <span data-ttu-id="18038-159">Wert</span><span class="sxs-lookup"><span data-stu-id="18038-159">Value</span></span>      | <span data-ttu-id="18038-160">Typ</span><span class="sxs-lookup"><span data-stu-id="18038-160">Type</span></span>   | <span data-ttu-id="18038-161">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="18038-161">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="18038-162">Wert</span><span class="sxs-lookup"><span data-stu-id="18038-162">Value</span></span>      | <span data-ttu-id="18038-163">Array</span><span class="sxs-lookup"><span data-stu-id="18038-163">array</span></span>  | <span data-ttu-id="18038-164">Ein Array von Objekten, die Daten für jeden Erfolg in Ihrem Spiel enthalten.</span><span class="sxs-lookup"><span data-stu-id="18038-164">An array of objects that contain data for each achievement in your game.</span></span> <span data-ttu-id="18038-165">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="18038-165">For more information about the data in each object, see the following table.</span></span>                                                                                                                      |
| @nextLink  | <span data-ttu-id="18038-166">String</span><span class="sxs-lookup"><span data-stu-id="18038-166">string</span></span> | <span data-ttu-id="18038-167">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="18038-167">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="18038-168">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 100 festgelegt ist, es jedoch mehr als 100 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="18038-168">For example, this value is returned if the **top** parameter of the request is set to 100 but there are more than 100 rows of data for the query.</span></span> |
| <span data-ttu-id="18038-169">TotalCount</span><span class="sxs-lookup"><span data-stu-id="18038-169">TotalCount</span></span> | <span data-ttu-id="18038-170">int</span><span class="sxs-lookup"><span data-stu-id="18038-170">int</span></span>    | <span data-ttu-id="18038-171">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="18038-171">The total number of rows in the data result for the query.</span></span>  |


<span data-ttu-id="18038-172">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="18038-172">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="18038-173">Wert</span><span class="sxs-lookup"><span data-stu-id="18038-173">Value</span></span>               | <span data-ttu-id="18038-174">Typ</span><span class="sxs-lookup"><span data-stu-id="18038-174">Type</span></span>   | <span data-ttu-id="18038-175">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="18038-175">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="18038-176">applicationId</span><span class="sxs-lookup"><span data-stu-id="18038-176">applicationId</span></span>       | <span data-ttu-id="18038-177">String</span><span class="sxs-lookup"><span data-stu-id="18038-177">string</span></span> | <span data-ttu-id="18038-178">Die Store-ID des Spiels, für das Sie Erfolgsdaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="18038-178">The Store ID of the game for which you are retrieving achievements data.</span></span>     |
| <span data-ttu-id="18038-179">reportDateTime</span><span class="sxs-lookup"><span data-stu-id="18038-179">reportDateTime</span></span>     | <span data-ttu-id="18038-180">String</span><span class="sxs-lookup"><span data-stu-id="18038-180">string</span></span> |  <span data-ttu-id="18038-181">Das Datum für die Erfolgsdaten.</span><span class="sxs-lookup"><span data-stu-id="18038-181">The date for the achievements data.</span></span>    |
| <span data-ttu-id="18038-182">achievementId</span><span class="sxs-lookup"><span data-stu-id="18038-182">achievementId</span></span>          | <span data-ttu-id="18038-183">number</span><span class="sxs-lookup"><span data-stu-id="18038-183">number</span></span> |  <span data-ttu-id="18038-184">Die ID des Erfolges.</span><span class="sxs-lookup"><span data-stu-id="18038-184">The ID of the achievement.</span></span> |
| <span data-ttu-id="18038-185">achievementName</span><span class="sxs-lookup"><span data-stu-id="18038-185">achievementName</span></span>           | <span data-ttu-id="18038-186">String</span><span class="sxs-lookup"><span data-stu-id="18038-186">string</span></span> | <span data-ttu-id="18038-187">Der Name des Erfolges.</span><span class="sxs-lookup"><span data-stu-id="18038-187">The name of the achievement.</span></span>  |
| <span data-ttu-id="18038-188">gamerscore</span><span class="sxs-lookup"><span data-stu-id="18038-188">gamerscore</span></span>           | <span data-ttu-id="18038-189">number</span><span class="sxs-lookup"><span data-stu-id="18038-189">number</span></span> |  <span data-ttu-id="18038-190">Die Gamerscore-Prämie für den Erfolg.</span><span class="sxs-lookup"><span data-stu-id="18038-190">The gamerscore reward for the achievement.</span></span>  |
| <span data-ttu-id="18038-191">dailyUnlocks</span><span class="sxs-lookup"><span data-stu-id="18038-191">dailyUnlocks</span></span>           | <span data-ttu-id="18038-192">number</span><span class="sxs-lookup"><span data-stu-id="18038-192">number</span></span> |  <span data-ttu-id="18038-193">Die Anzahl der Kunden, die den Erfolg für den Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="18038-193">The number of customers who unlocked the achievement on the day specified by *reportDateTime*.</span></span>  |
| <span data-ttu-id="18038-194">monthlyUnlocks</span><span class="sxs-lookup"><span data-stu-id="18038-194">monthlyUnlocks</span></span>              | <span data-ttu-id="18038-195">number</span><span class="sxs-lookup"><span data-stu-id="18038-195">number</span></span> |  <span data-ttu-id="18038-196">Die Anzahl der Kunden, die den Erfolg in den 30 Tagen vor dem Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="18038-196">The number of customers who unlocked the achievement in the 30 days prior to the day specified by *reportDateTime*.</span></span>   |
| <span data-ttu-id="18038-197">totalUnlocks</span><span class="sxs-lookup"><span data-stu-id="18038-197">totalUnlocks</span></span> | <span data-ttu-id="18038-198">number</span><span class="sxs-lookup"><span data-stu-id="18038-198">number</span></span> |  <span data-ttu-id="18038-199">Die Anzahl der Kunden, die den Erfolg während der Lebensdauer des Spiels bis zu dem Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="18038-199">The number of customers who have unlocked the achievement during the lifetime of your game, up to the day specified by *reportDateTime*.</span></span>   |


### <a name="response-example"></a><span data-ttu-id="18038-200">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="18038-200">Response example</span></span>

<span data-ttu-id="18038-201">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="18038-201">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "applicationId": "9NBLGGGZ5QDR",
      "reportDateTime": "2018-01-30T00:00:00",
      "achievementId": 6,
      "achievementName": "Yoink!",
      "gamerscore": 10,
      "dailyUnlocks": 0,
      "monthlyUnlocks": 10310,
      "totalUnlocks": 1215360
    },
    {
      "applicationId": "9NBLGGGZ5QDR",
      "reportDateTime": "2018-01-30T00:00:00",
      "achievementId": 7,
      "achievementName": "Ding!",
      "gamerscore": 10,
      "dailyUnlocks": 0,
      "monthlyUnlocks": 10897,
      "totalUnlocks": 1282524
    },
    {
      "applicationId": "9NBLGGGZ5QDR",
      "reportDateTime": "2018-01-30T00:00:00",
      "achievementId": 8,
      "achievementName": "End of the Beginning",
      "gamerscore": 30,
      "dailyUnlocks": 0,
      "monthlyUnlocks": 9848,
      "totalUnlocks": 1105074
    }
  ],
  "@nextLink": null,
  "TotalCount": 3
}
```

## <a name="related-topics"></a><span data-ttu-id="18038-202">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="18038-202">Related topics</span></span>

* [<span data-ttu-id="18038-203">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="18038-203">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="18038-204">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="18038-204">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="18038-205">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="18038-205">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="18038-206">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="18038-206">Get Xbox Live Game Hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="18038-207">Abrufen von Xbox Live-Clubdaten</span><span class="sxs-lookup"><span data-stu-id="18038-207">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="18038-208">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="18038-208">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
