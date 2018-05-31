---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Spielehubdaten abzurufen.
title: Abrufen von Xbox Live Spielehubdaten
ms.author: mcleans
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse, Spielehubs
ms.localizationpriority: medium
ms.openlocfilehash: 0d34c95e615a10131b3e7f3ffe9ceb246b652727
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1815785"
---
# <a name="get-xbox-live-game-hub-data"></a><span data-ttu-id="f6401-104">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="f6401-104">Get Xbox Live Game Hub data</span></span>


<span data-ttu-id="f6401-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Spielehubdaten für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f6401-105">Use this method in the Microsoft Store analytics API to get Game Hub data for your [Xbox Live-enabled game](../xbox-live/index.md).</span></span> <span data-ttu-id="f6401-106">Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f6401-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6401-107">Diese Methode unterstützt derzeit nur Xbox Live-fähige Spiele, die von [Microsoft Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht werden oder die mithilfe des [ID@Xbox Programms](../xbox-live/developer-program-overview.md#id) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="f6401-107">This method currently only supports Xbox Live-enabled games that are published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) or that are submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="f6401-108">Es gibt keine Daten für Spiele zurück, die mithilfe des [Xbox Live Creators-Programms](../xbox-live/developer-program-overview.md#xbox-live-creators-program) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="f6401-108">It does not return data for games that were submitted via the [Xbox Live Creators Program](../xbox-live/developer-program-overview.md#xbox-live-creators-program).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6401-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f6401-109">Prerequisites</span></span>

<span data-ttu-id="f6401-110">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="f6401-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="f6401-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="f6401-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="f6401-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6401-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="f6401-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="f6401-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="f6401-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="f6401-114">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="f6401-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="f6401-115">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="f6401-116">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="f6401-116">Request syntax</span></span>

| <span data-ttu-id="f6401-117">Methode</span><span class="sxs-lookup"><span data-stu-id="f6401-117">Method</span></span> | <span data-ttu-id="f6401-118">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="f6401-118">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="f6401-119">GET</span><span class="sxs-lookup"><span data-stu-id="f6401-119">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="f6401-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="f6401-120">Request header</span></span>

| <span data-ttu-id="f6401-121">Header</span><span class="sxs-lookup"><span data-stu-id="f6401-121">Header</span></span>        | <span data-ttu-id="f6401-122">Typ</span><span class="sxs-lookup"><span data-stu-id="f6401-122">Type</span></span>   | <span data-ttu-id="f6401-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6401-123">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f6401-124">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="f6401-124">Authorization</span></span> | <span data-ttu-id="f6401-125">String</span><span class="sxs-lookup"><span data-stu-id="f6401-125">string</span></span> | <span data-ttu-id="f6401-126">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f6401-126">Required.</span></span> <span data-ttu-id="f6401-127">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="f6401-127">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="f6401-128">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="f6401-128">Request parameters</span></span>

| <span data-ttu-id="f6401-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="f6401-129">Parameter</span></span>        | <span data-ttu-id="f6401-130">Typ</span><span class="sxs-lookup"><span data-stu-id="f6401-130">Type</span></span>   |  <span data-ttu-id="f6401-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6401-131">Description</span></span>      |  <span data-ttu-id="f6401-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="f6401-132">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="f6401-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="f6401-133">applicationId</span></span> | <span data-ttu-id="f6401-134">String</span><span class="sxs-lookup"><span data-stu-id="f6401-134">string</span></span> | <span data-ttu-id="f6401-135">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Spielehubdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="f6401-135">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live Game Hub data.</span></span>  |  <span data-ttu-id="f6401-136">Ja</span><span class="sxs-lookup"><span data-stu-id="f6401-136">Yes</span></span>  |
| <span data-ttu-id="f6401-137">metricType</span><span class="sxs-lookup"><span data-stu-id="f6401-137">metricType</span></span> | <span data-ttu-id="f6401-138">String</span><span class="sxs-lookup"><span data-stu-id="f6401-138">string</span></span> | <span data-ttu-id="f6401-139">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="f6401-139">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="f6401-140">Geben Sie für diese Methode den Wert **communitymanagergamehub** an.</span><span class="sxs-lookup"><span data-stu-id="f6401-140">For this method, specify the value **communitymanagergamehub**.</span></span>  |  <span data-ttu-id="f6401-141">Ja</span><span class="sxs-lookup"><span data-stu-id="f6401-141">Yes</span></span>  |
| <span data-ttu-id="f6401-142">startDate</span><span class="sxs-lookup"><span data-stu-id="f6401-142">startDate</span></span> | <span data-ttu-id="f6401-143">date</span><span class="sxs-lookup"><span data-stu-id="f6401-143">date</span></span> | <span data-ttu-id="f6401-144">Das Startdatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f6401-144">The start date in the date range of Game Hub data to retrieve.</span></span> <span data-ttu-id="f6401-145">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="f6401-145">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="f6401-146">Nein</span><span class="sxs-lookup"><span data-stu-id="f6401-146">No</span></span>  |
| <span data-ttu-id="f6401-147">endDate</span><span class="sxs-lookup"><span data-stu-id="f6401-147">endDate</span></span> | <span data-ttu-id="f6401-148">date</span><span class="sxs-lookup"><span data-stu-id="f6401-148">date</span></span> | <span data-ttu-id="f6401-149">Das Enddatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f6401-149">The end date in the date range of Game Hub data to retrieve.</span></span> <span data-ttu-id="f6401-150">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="f6401-150">The default is the current date.</span></span> |  <span data-ttu-id="f6401-151">Nein</span><span class="sxs-lookup"><span data-stu-id="f6401-151">No</span></span>  |
| <span data-ttu-id="f6401-152">top</span><span class="sxs-lookup"><span data-stu-id="f6401-152">top</span></span> | <span data-ttu-id="f6401-153">int</span><span class="sxs-lookup"><span data-stu-id="f6401-153">int</span></span> | <span data-ttu-id="f6401-154">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f6401-154">The number of rows of data to return in the request.</span></span> <span data-ttu-id="f6401-155">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="f6401-155">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="f6401-156">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="f6401-156">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="f6401-157">Nein</span><span class="sxs-lookup"><span data-stu-id="f6401-157">No</span></span>  |
| <span data-ttu-id="f6401-158">skip</span><span class="sxs-lookup"><span data-stu-id="f6401-158">skip</span></span> | <span data-ttu-id="f6401-159">int</span><span class="sxs-lookup"><span data-stu-id="f6401-159">int</span></span> | <span data-ttu-id="f6401-160">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f6401-160">The number of rows to skip in the query.</span></span> <span data-ttu-id="f6401-161">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="f6401-161">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="f6401-162">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="f6401-162">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="f6401-163">Nein</span><span class="sxs-lookup"><span data-stu-id="f6401-163">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="f6401-164">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="f6401-164">Request example</span></span>

<span data-ttu-id="f6401-165">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Spielehubdaten für Ihr Xbox Live-fähiges Spiel an.</span><span class="sxs-lookup"><span data-stu-id="f6401-165">The following example demonstrates a request for getting Game Hub data for your Xbox Live-enabled game.</span></span> <span data-ttu-id="f6401-166">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="f6401-166">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=communitymanagergamehub&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="f6401-167">Antwort</span><span class="sxs-lookup"><span data-stu-id="f6401-167">Response</span></span>


| <span data-ttu-id="f6401-168">Wert</span><span class="sxs-lookup"><span data-stu-id="f6401-168">Value</span></span>      | <span data-ttu-id="f6401-169">Typ</span><span class="sxs-lookup"><span data-stu-id="f6401-169">Type</span></span>   | <span data-ttu-id="f6401-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6401-170">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="f6401-171">Wert</span><span class="sxs-lookup"><span data-stu-id="f6401-171">Value</span></span>      | <span data-ttu-id="f6401-172">Array</span><span class="sxs-lookup"><span data-stu-id="f6401-172">array</span></span>  | <span data-ttu-id="f6401-173">Ein Array von Objekten, die für jedes Datum im Datumsbereich der angegebenen Spielehubdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="f6401-173">An array of objects that contain Game Hub data for each date in the specified date range.</span></span> <span data-ttu-id="f6401-174">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="f6401-174">For more information about the data in each object, see the following table.</span></span>                                                                                                                      |
| @nextLink  | <span data-ttu-id="f6401-175">String</span><span class="sxs-lookup"><span data-stu-id="f6401-175">string</span></span> | <span data-ttu-id="f6401-176">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="f6401-176">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="f6401-177">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10000 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="f6401-177">For example, this value is returned if the **top** parameter of the request is set to 10000 but there are more than 10000 rows of data for the query.</span></span> |
| <span data-ttu-id="f6401-178">TotalCount</span><span class="sxs-lookup"><span data-stu-id="f6401-178">TotalCount</span></span> | <span data-ttu-id="f6401-179">int</span><span class="sxs-lookup"><span data-stu-id="f6401-179">int</span></span>    | <span data-ttu-id="f6401-180">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="f6401-180">The total number of rows in the data result for the query.</span></span>  |


<span data-ttu-id="f6401-181">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="f6401-181">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="f6401-182">Wert</span><span class="sxs-lookup"><span data-stu-id="f6401-182">Value</span></span>               | <span data-ttu-id="f6401-183">Typ</span><span class="sxs-lookup"><span data-stu-id="f6401-183">Type</span></span>   | <span data-ttu-id="f6401-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6401-184">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="f6401-185">date</span><span class="sxs-lookup"><span data-stu-id="f6401-185">date</span></span>                | <span data-ttu-id="f6401-186">String</span><span class="sxs-lookup"><span data-stu-id="f6401-186">string</span></span> | <span data-ttu-id="f6401-187">Das Datum für die Spielehubdaten in diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="f6401-187">The date for the Game Hub data in this object.</span></span> |
| <span data-ttu-id="f6401-188">applicationId</span><span class="sxs-lookup"><span data-stu-id="f6401-188">applicationId</span></span>       | <span data-ttu-id="f6401-189">String</span><span class="sxs-lookup"><span data-stu-id="f6401-189">string</span></span> | <span data-ttu-id="f6401-190">Die Store-ID des Spiels, für das Sie Spielehubdaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="f6401-190">The Store ID of the game for which you are retrieving Game Hub data.</span></span>     |
| <span data-ttu-id="f6401-191">gameHubLikeCount</span><span class="sxs-lookup"><span data-stu-id="f6401-191">gameHubLikeCount</span></span>     | <span data-ttu-id="f6401-192">number</span><span class="sxs-lookup"><span data-stu-id="f6401-192">number</span></span> |   <span data-ttu-id="f6401-193">Die Anzahl der Vorlieben, die zur Spielehubseite an dem angegebenen Datum hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f6401-193">The number of likes added to the Game Hub page on the specified date.</span></span>   |
| <span data-ttu-id="f6401-194">gameHubCommentCount</span><span class="sxs-lookup"><span data-stu-id="f6401-194">gameHubCommentCount</span></span>          | <span data-ttu-id="f6401-195">number</span><span class="sxs-lookup"><span data-stu-id="f6401-195">number</span></span> |  <span data-ttu-id="f6401-196">Die Anzahl der Kommentare, die zur Spielehubseite für Ihre App an dem angegebenen Datum hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f6401-196">The number of comments added to the Game Hub page for your app on the specified date.</span></span>  |
| <span data-ttu-id="f6401-197">gameHubShareCount</span><span class="sxs-lookup"><span data-stu-id="f6401-197">gameHubShareCount</span></span>           | <span data-ttu-id="f6401-198">number</span><span class="sxs-lookup"><span data-stu-id="f6401-198">number</span></span> | <span data-ttu-id="f6401-199">Die Anzahl der Male, die die Spielehubseite für Ihre App von Kunden dem angegebenen Datum geteilt wurden.</span><span class="sxs-lookup"><span data-stu-id="f6401-199">The number of times the Game Hub page for your app was shared by customers on the specified date.</span></span>   |


### <a name="response-example"></a><span data-ttu-id="f6401-200">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="f6401-200">Response example</span></span>

<span data-ttu-id="f6401-201">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="f6401-201">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "date": "2018-01-04",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 10,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0
    },
    {
      "date": "2018-01-05",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 12,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0
    }
  ],
  "@nextLink": null,
  "TotalCount": 26
}
```

## <a name="related-topics"></a><span data-ttu-id="f6401-202">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f6401-202">Related topics</span></span>

* [<span data-ttu-id="f6401-203">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="f6401-203">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="f6401-204">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="f6401-204">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="f6401-205">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="f6401-205">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="f6401-206">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="f6401-206">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="f6401-207">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="f6401-207">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="f6401-208">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="f6401-208">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
