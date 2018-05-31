---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Erfolgsdaten abzurufen.
title: Abrufen von Xbox Live Erfolgsdaten
ms.author: mcleans
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live-Analyse, Erfolge
ms.localizationpriority: medium
ms.openlocfilehash: 76cbe9abf3b6d668bb157e40f3e61aff885e3cbb
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816015"
---
# <a name="get-xbox-live-achievements-data"></a><span data-ttu-id="b1d4f-104">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-104">Get Xbox Live achievements data</span></span>

<span data-ttu-id="b1d4f-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Anzahl der Kunden zu erhalten, die jeden Erfolg für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) freigeschaltet haben, und zwar während des letzten Tages, für den Erfolgsdaten verfügbar sind, für die vorherigen 30Tage vor diesem Tag und über die gesamte Lebensdauer des Spiels bis zu diesem Tag.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-105">Use this method in the Microsoft Store analytics API to get the number of customers who have unlocked each achievement for your [Xbox Live-enabled game](../xbox-live/index.md) during the most recent day for which achievements data is available, the previous 30 days leading up to that day, and the total lifetime of your game up to that day.</span></span> <span data-ttu-id="b1d4f-106">Diese Informationen sind auch im [Xbox Analysenbericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1d4f-107">Diese Methode unterstützt derzeit nur Xbox Live-fähige Spiele, die von [Microsoft Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht werden oder die mithilfe des [ID@Xbox Programms](../xbox-live/developer-program-overview.md#id) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-107">This method currently only supports Xbox Live-enabled games that are published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) or that are submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="b1d4f-108">Es gibt keine Daten für Spiele zurück, die mithilfe des [Xbox Live Creators-Programms](../xbox-live/developer-program-overview.md#xbox-live-creators-program) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-108">It does not return data for games that were submitted via the [Xbox Live Creators Program](../xbox-live/developer-program-overview.md#xbox-live-creators-program).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1d4f-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b1d4f-109">Prerequisites</span></span>

<span data-ttu-id="b1d4f-110">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="b1d4f-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="b1d4f-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="b1d4f-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="b1d4f-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="b1d4f-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-114">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="b1d4f-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-115">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="b1d4f-116">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="b1d4f-116">Request syntax</span></span>

| <span data-ttu-id="b1d4f-117">Methode</span><span class="sxs-lookup"><span data-stu-id="b1d4f-117">Method</span></span> | <span data-ttu-id="b1d4f-118">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="b1d4f-118">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="b1d4f-119">GET</span><span class="sxs-lookup"><span data-stu-id="b1d4f-119">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="b1d4f-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="b1d4f-120">Request header</span></span>

| <span data-ttu-id="b1d4f-121">Header</span><span class="sxs-lookup"><span data-stu-id="b1d4f-121">Header</span></span>        | <span data-ttu-id="b1d4f-122">Typ</span><span class="sxs-lookup"><span data-stu-id="b1d4f-122">Type</span></span>   | <span data-ttu-id="b1d4f-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-123">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="b1d4f-124">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-124">Authorization</span></span> | <span data-ttu-id="b1d4f-125">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-125">string</span></span> | <span data-ttu-id="b1d4f-126">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-126">Required.</span></span> <span data-ttu-id="b1d4f-127">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-127">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="b1d4f-128">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="b1d4f-128">Request parameters</span></span>


| <span data-ttu-id="b1d4f-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="b1d4f-129">Parameter</span></span>        | <span data-ttu-id="b1d4f-130">Typ</span><span class="sxs-lookup"><span data-stu-id="b1d4f-130">Type</span></span>   |  <span data-ttu-id="b1d4f-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-131">Description</span></span>      |  <span data-ttu-id="b1d4f-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b1d4f-132">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="b1d4f-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="b1d4f-133">applicationId</span></span> | <span data-ttu-id="b1d4f-134">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-134">string</span></span> | <span data-ttu-id="b1d4f-135">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Erfolgsdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-135">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live achievements data.</span></span>  |  <span data-ttu-id="b1d4f-136">Ja</span><span class="sxs-lookup"><span data-stu-id="b1d4f-136">Yes</span></span>  |
| <span data-ttu-id="b1d4f-137">metricType</span><span class="sxs-lookup"><span data-stu-id="b1d4f-137">metricType</span></span> | <span data-ttu-id="b1d4f-138">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-138">string</span></span> | <span data-ttu-id="b1d4f-139">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live-Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-139">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="b1d4f-140">Geben Sie für diese Methode den Wert **achievements** an.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-140">For this method, specify the value **achievements**.</span></span>  |  <span data-ttu-id="b1d4f-141">Ja</span><span class="sxs-lookup"><span data-stu-id="b1d4f-141">Yes</span></span>  |
| <span data-ttu-id="b1d4f-142">top</span><span class="sxs-lookup"><span data-stu-id="b1d4f-142">top</span></span> | <span data-ttu-id="b1d4f-143">int</span><span class="sxs-lookup"><span data-stu-id="b1d4f-143">int</span></span> | <span data-ttu-id="b1d4f-144">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-144">The number of rows of data to return in the request.</span></span> <span data-ttu-id="b1d4f-145">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-145">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="b1d4f-146">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-146">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="b1d4f-147">Nein</span><span class="sxs-lookup"><span data-stu-id="b1d4f-147">No</span></span>  |
| <span data-ttu-id="b1d4f-148">skip</span><span class="sxs-lookup"><span data-stu-id="b1d4f-148">skip</span></span> | <span data-ttu-id="b1d4f-149">int</span><span class="sxs-lookup"><span data-stu-id="b1d4f-149">int</span></span> | <span data-ttu-id="b1d4f-150">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-150">The number of rows to skip in the query.</span></span> <span data-ttu-id="b1d4f-151">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-151">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="b1d4f-152">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-152">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="b1d4f-153">Nein</span><span class="sxs-lookup"><span data-stu-id="b1d4f-153">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="b1d4f-154">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="b1d4f-154">Request example</span></span>

<span data-ttu-id="b1d4f-155">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Erfolgsdaten für Kunden, die die ersten 10 Erfolge für Ihr Xbox Live-fähiges Spiel entsperrt haben.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-155">The following example demonstrates a request for getting achievements data for customers who have unlocked the first 10 achievements for your Xbox Live-enabled game.</span></span> <span data-ttu-id="b1d4f-156">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-156">Replace the *applicationId* value with the Store ID for your game.</span></span>


```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=achievements&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="b1d4f-157">Antwort</span><span class="sxs-lookup"><span data-stu-id="b1d4f-157">Response</span></span>

| <span data-ttu-id="b1d4f-158">Wert</span><span class="sxs-lookup"><span data-stu-id="b1d4f-158">Value</span></span>      | <span data-ttu-id="b1d4f-159">Typ</span><span class="sxs-lookup"><span data-stu-id="b1d4f-159">Type</span></span>   | <span data-ttu-id="b1d4f-160">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-160">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="b1d4f-161">Wert</span><span class="sxs-lookup"><span data-stu-id="b1d4f-161">Value</span></span>      | <span data-ttu-id="b1d4f-162">Array</span><span class="sxs-lookup"><span data-stu-id="b1d4f-162">array</span></span>  | <span data-ttu-id="b1d4f-163">Ein Array von Objekten, die Daten für jeden Erfolg in Ihrem Spiel enthalten.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-163">An array of objects that contain data for each achievement in your game.</span></span> <span data-ttu-id="b1d4f-164">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-164">For more information about the data in each object, see the following table.</span></span>                                                                                                                      |
| @nextLink  | <span data-ttu-id="b1d4f-165">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-165">string</span></span> | <span data-ttu-id="b1d4f-166">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-166">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="b1d4f-167">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 100 festgelegt ist, es jedoch mehr als 100 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-167">For example, this value is returned if the **top** parameter of the request is set to 100 but there are more than 100 rows of data for the query.</span></span> |
| <span data-ttu-id="b1d4f-168">TotalCount</span><span class="sxs-lookup"><span data-stu-id="b1d4f-168">TotalCount</span></span> | <span data-ttu-id="b1d4f-169">int</span><span class="sxs-lookup"><span data-stu-id="b1d4f-169">int</span></span>    | <span data-ttu-id="b1d4f-170">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-170">The total number of rows in the data result for the query.</span></span>  |


<span data-ttu-id="b1d4f-171">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-171">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="b1d4f-172">Wert</span><span class="sxs-lookup"><span data-stu-id="b1d4f-172">Value</span></span>               | <span data-ttu-id="b1d4f-173">Typ</span><span class="sxs-lookup"><span data-stu-id="b1d4f-173">Type</span></span>   | <span data-ttu-id="b1d4f-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b1d4f-174">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="b1d4f-175">applicationId</span><span class="sxs-lookup"><span data-stu-id="b1d4f-175">applicationId</span></span>       | <span data-ttu-id="b1d4f-176">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-176">string</span></span> | <span data-ttu-id="b1d4f-177">Die Store-ID des Spiels, für das Sie Erfolgsdaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-177">The Store ID of the game for which you are retrieving achievements data.</span></span>     |
| <span data-ttu-id="b1d4f-178">reportDateTime</span><span class="sxs-lookup"><span data-stu-id="b1d4f-178">reportDateTime</span></span>     | <span data-ttu-id="b1d4f-179">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-179">string</span></span> |  <span data-ttu-id="b1d4f-180">Das Datum für die Erfolgsdaten.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-180">The date for the achievements data.</span></span>    |
| <span data-ttu-id="b1d4f-181">achievementId</span><span class="sxs-lookup"><span data-stu-id="b1d4f-181">achievementId</span></span>          | <span data-ttu-id="b1d4f-182">number</span><span class="sxs-lookup"><span data-stu-id="b1d4f-182">number</span></span> |  <span data-ttu-id="b1d4f-183">Die ID des Erfolges.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-183">The ID of the achievement.</span></span> |
| <span data-ttu-id="b1d4f-184">achievementName</span><span class="sxs-lookup"><span data-stu-id="b1d4f-184">achievementName</span></span>           | <span data-ttu-id="b1d4f-185">String</span><span class="sxs-lookup"><span data-stu-id="b1d4f-185">string</span></span> | <span data-ttu-id="b1d4f-186">Der Name des Erfolges.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-186">The name of the achievement.</span></span>  |
| <span data-ttu-id="b1d4f-187">gamerscore</span><span class="sxs-lookup"><span data-stu-id="b1d4f-187">gamerscore</span></span>           | <span data-ttu-id="b1d4f-188">number</span><span class="sxs-lookup"><span data-stu-id="b1d4f-188">number</span></span> |  <span data-ttu-id="b1d4f-189">Die Gamerscore-Prämie für den Erfolg.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-189">The gamerscore reward for the achievement.</span></span>  |
| <span data-ttu-id="b1d4f-190">dailyUnlocks</span><span class="sxs-lookup"><span data-stu-id="b1d4f-190">dailyUnlocks</span></span>           | <span data-ttu-id="b1d4f-191">number</span><span class="sxs-lookup"><span data-stu-id="b1d4f-191">number</span></span> |  <span data-ttu-id="b1d4f-192">Die Anzahl der Kunden, die den Erfolg für den Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-192">The number of customers who unlocked the achievement on the day specified by *reportDateTime*.</span></span>  |
| <span data-ttu-id="b1d4f-193">monthlyUnlocks</span><span class="sxs-lookup"><span data-stu-id="b1d4f-193">monthlyUnlocks</span></span>              | <span data-ttu-id="b1d4f-194">number</span><span class="sxs-lookup"><span data-stu-id="b1d4f-194">number</span></span> |  <span data-ttu-id="b1d4f-195">Die Anzahl der Kunden, die den Erfolg in den 30 Tagen vor dem Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-195">The number of customers who unlocked the achievement in the 30 days prior to the day specified by *reportDateTime*.</span></span>   |
| <span data-ttu-id="b1d4f-196">totalUnlocks</span><span class="sxs-lookup"><span data-stu-id="b1d4f-196">totalUnlocks</span></span> | <span data-ttu-id="b1d4f-197">number</span><span class="sxs-lookup"><span data-stu-id="b1d4f-197">number</span></span> |  <span data-ttu-id="b1d4f-198">Die Anzahl der Kunden, die den Erfolg während der Lebensdauer des Spiels bis zu dem Tag entsperrt haben, der durch *reportDateTime* angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-198">The number of customers who have unlocked the achievement during the lifetime of your game, up to the day specified by *reportDateTime*.</span></span>   |


### <a name="response-example"></a><span data-ttu-id="b1d4f-199">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="b1d4f-199">Response example</span></span>

<span data-ttu-id="b1d4f-200">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="b1d4f-200">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="b1d4f-201">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b1d4f-201">Related topics</span></span>

* [<span data-ttu-id="b1d4f-202">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-202">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="b1d4f-203">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-203">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="b1d4f-204">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-204">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="b1d4f-205">Abrufen von Xbox Live Spielehub-Daten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-205">Get Xbox Live Game Hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="b1d4f-206">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-206">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="b1d4f-207">Abrufen von Xbox Live Multiplayer-Daten</span><span class="sxs-lookup"><span data-stu-id="b1d4f-207">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
