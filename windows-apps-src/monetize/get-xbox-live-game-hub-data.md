---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Spielehubdaten abzurufen.
title: Abrufen von Xbox Live Spielehubdaten
ms.author: mhopkins
ms.date: 06/04/2018
ms.topic: article
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse, Spielehubs
ms.localizationpriority: medium
ms.openlocfilehash: 0e029e74920f5782e40a0a1737a5a43723ff8835
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5598624"
---
# <a name="get-xbox-live-game-hub-data"></a><span data-ttu-id="f9437-104">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="f9437-104">Get Xbox Live Game Hub data</span></span>


<span data-ttu-id="f9437-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Spielehubdaten für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="f9437-105">Use this method in the Microsoft Store analytics API to get Game Hub data for your [Xbox Live-enabled game](../xbox-live/index.md).</span></span> <span data-ttu-id="f9437-106">Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f9437-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9437-107">Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="f9437-107">This method only supports games for Xbox or games that use Xbox Live services.</span></span> <span data-ttu-id="f9437-108">Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="f9437-108">These games must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="f9437-109">Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="f9437-109">This method does not currently support games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f9437-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="f9437-110">Prerequisites</span></span>

<span data-ttu-id="f9437-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="f9437-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="f9437-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="f9437-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="f9437-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f9437-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="f9437-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="f9437-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="f9437-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="f9437-115">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="f9437-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="f9437-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="f9437-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="f9437-117">Request syntax</span></span>

| <span data-ttu-id="f9437-118">Methode</span><span class="sxs-lookup"><span data-stu-id="f9437-118">Method</span></span> | <span data-ttu-id="f9437-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="f9437-119">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="f9437-120">GET</span><span class="sxs-lookup"><span data-stu-id="f9437-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="f9437-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="f9437-121">Request header</span></span>

| <span data-ttu-id="f9437-122">Header</span><span class="sxs-lookup"><span data-stu-id="f9437-122">Header</span></span>        | <span data-ttu-id="f9437-123">Typ</span><span class="sxs-lookup"><span data-stu-id="f9437-123">Type</span></span>   | <span data-ttu-id="f9437-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9437-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="f9437-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="f9437-125">Authorization</span></span> | <span data-ttu-id="f9437-126">String</span><span class="sxs-lookup"><span data-stu-id="f9437-126">string</span></span> | <span data-ttu-id="f9437-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f9437-127">Required.</span></span> <span data-ttu-id="f9437-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="f9437-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="f9437-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="f9437-129">Request parameters</span></span>

| <span data-ttu-id="f9437-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="f9437-130">Parameter</span></span>        | <span data-ttu-id="f9437-131">Typ</span><span class="sxs-lookup"><span data-stu-id="f9437-131">Type</span></span>   |  <span data-ttu-id="f9437-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9437-132">Description</span></span>      |  <span data-ttu-id="f9437-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="f9437-133">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="f9437-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="f9437-134">applicationId</span></span> | <span data-ttu-id="f9437-135">String</span><span class="sxs-lookup"><span data-stu-id="f9437-135">string</span></span> | <span data-ttu-id="f9437-136">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Spielehubdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="f9437-136">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live Game Hub data.</span></span>  |  <span data-ttu-id="f9437-137">Ja</span><span class="sxs-lookup"><span data-stu-id="f9437-137">Yes</span></span>  |
| <span data-ttu-id="f9437-138">metricType</span><span class="sxs-lookup"><span data-stu-id="f9437-138">metricType</span></span> | <span data-ttu-id="f9437-139">String</span><span class="sxs-lookup"><span data-stu-id="f9437-139">string</span></span> | <span data-ttu-id="f9437-140">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="f9437-140">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="f9437-141">Geben Sie für diese Methode den Wert **communitymanagergamehub** an.</span><span class="sxs-lookup"><span data-stu-id="f9437-141">For this method, specify the value **communitymanagergamehub**.</span></span>  |  <span data-ttu-id="f9437-142">Ja</span><span class="sxs-lookup"><span data-stu-id="f9437-142">Yes</span></span>  |
| <span data-ttu-id="f9437-143">startDate</span><span class="sxs-lookup"><span data-stu-id="f9437-143">startDate</span></span> | <span data-ttu-id="f9437-144">date</span><span class="sxs-lookup"><span data-stu-id="f9437-144">date</span></span> | <span data-ttu-id="f9437-145">Das Startdatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f9437-145">The start date in the date range of Game Hub data to retrieve.</span></span> <span data-ttu-id="f9437-146">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="f9437-146">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="f9437-147">Nein</span><span class="sxs-lookup"><span data-stu-id="f9437-147">No</span></span>  |
| <span data-ttu-id="f9437-148">endDate</span><span class="sxs-lookup"><span data-stu-id="f9437-148">endDate</span></span> | <span data-ttu-id="f9437-149">date</span><span class="sxs-lookup"><span data-stu-id="f9437-149">date</span></span> | <span data-ttu-id="f9437-150">Das Enddatum im Datumsbereich der Spielehubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f9437-150">The end date in the date range of Game Hub data to retrieve.</span></span> <span data-ttu-id="f9437-151">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="f9437-151">The default is the current date.</span></span> |  <span data-ttu-id="f9437-152">Nein</span><span class="sxs-lookup"><span data-stu-id="f9437-152">No</span></span>  |
| <span data-ttu-id="f9437-153">top</span><span class="sxs-lookup"><span data-stu-id="f9437-153">top</span></span> | <span data-ttu-id="f9437-154">int</span><span class="sxs-lookup"><span data-stu-id="f9437-154">int</span></span> | <span data-ttu-id="f9437-155">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f9437-155">The number of rows of data to return in the request.</span></span> <span data-ttu-id="f9437-156">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="f9437-156">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="f9437-157">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="f9437-157">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="f9437-158">Nein</span><span class="sxs-lookup"><span data-stu-id="f9437-158">No</span></span>  |
| <span data-ttu-id="f9437-159">skip</span><span class="sxs-lookup"><span data-stu-id="f9437-159">skip</span></span> | <span data-ttu-id="f9437-160">int</span><span class="sxs-lookup"><span data-stu-id="f9437-160">int</span></span> | <span data-ttu-id="f9437-161">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="f9437-161">The number of rows to skip in the query.</span></span> <span data-ttu-id="f9437-162">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="f9437-162">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="f9437-163">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="f9437-163">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="f9437-164">Nein</span><span class="sxs-lookup"><span data-stu-id="f9437-164">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="f9437-165">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="f9437-165">Request example</span></span>

<span data-ttu-id="f9437-166">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Spielehubdaten für Ihr Xbox Live-fähiges Spiel an.</span><span class="sxs-lookup"><span data-stu-id="f9437-166">The following example demonstrates a request for getting Game Hub data for your Xbox Live-enabled game.</span></span> <span data-ttu-id="f9437-167">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="f9437-167">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=communitymanagergamehub&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="f9437-168">Antwort</span><span class="sxs-lookup"><span data-stu-id="f9437-168">Response</span></span>


| <span data-ttu-id="f9437-169">Wert</span><span class="sxs-lookup"><span data-stu-id="f9437-169">Value</span></span>      | <span data-ttu-id="f9437-170">Typ</span><span class="sxs-lookup"><span data-stu-id="f9437-170">Type</span></span>   | <span data-ttu-id="f9437-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9437-171">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="f9437-172">Wert</span><span class="sxs-lookup"><span data-stu-id="f9437-172">Value</span></span>      | <span data-ttu-id="f9437-173">Array</span><span class="sxs-lookup"><span data-stu-id="f9437-173">array</span></span>  | <span data-ttu-id="f9437-174">Ein Array von Objekten, die für jedes Datum im Datumsbereich der angegebenen Spielehubdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="f9437-174">An array of objects that contain Game Hub data for each date in the specified date range.</span></span> <span data-ttu-id="f9437-175">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie in der folgenden Tabelle.</span><span class="sxs-lookup"><span data-stu-id="f9437-175">For more information about the data in each object, see the following table.</span></span>                                                                                                                      |
| @nextLink  | <span data-ttu-id="f9437-176">String</span><span class="sxs-lookup"><span data-stu-id="f9437-176">string</span></span> | <span data-ttu-id="f9437-177">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="f9437-177">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="f9437-178">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10000 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="f9437-178">For example, this value is returned if the **top** parameter of the request is set to 10000 but there are more than 10000 rows of data for the query.</span></span> |
| <span data-ttu-id="f9437-179">TotalCount</span><span class="sxs-lookup"><span data-stu-id="f9437-179">TotalCount</span></span> | <span data-ttu-id="f9437-180">int</span><span class="sxs-lookup"><span data-stu-id="f9437-180">int</span></span>    | <span data-ttu-id="f9437-181">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="f9437-181">The total number of rows in the data result for the query.</span></span>  |


<span data-ttu-id="f9437-182">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="f9437-182">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="f9437-183">Wert</span><span class="sxs-lookup"><span data-stu-id="f9437-183">Value</span></span>               | <span data-ttu-id="f9437-184">Typ</span><span class="sxs-lookup"><span data-stu-id="f9437-184">Type</span></span>   | <span data-ttu-id="f9437-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f9437-185">Description</span></span>                           |
|---------------------|--------|-------------------------------------------|
| <span data-ttu-id="f9437-186">date</span><span class="sxs-lookup"><span data-stu-id="f9437-186">date</span></span>                | <span data-ttu-id="f9437-187">String</span><span class="sxs-lookup"><span data-stu-id="f9437-187">string</span></span> | <span data-ttu-id="f9437-188">Das Datum für die Spielehubdaten in diesem Objekt.</span><span class="sxs-lookup"><span data-stu-id="f9437-188">The date for the Game Hub data in this object.</span></span> |
| <span data-ttu-id="f9437-189">applicationId</span><span class="sxs-lookup"><span data-stu-id="f9437-189">applicationId</span></span>       | <span data-ttu-id="f9437-190">String</span><span class="sxs-lookup"><span data-stu-id="f9437-190">string</span></span> | <span data-ttu-id="f9437-191">Die Store-ID des Spiels, für das Sie Spielehubdaten abrufen.</span><span class="sxs-lookup"><span data-stu-id="f9437-191">The Store ID of the game for which you are retrieving Game Hub data.</span></span>     |
| <span data-ttu-id="f9437-192">gameHubLikeCount</span><span class="sxs-lookup"><span data-stu-id="f9437-192">gameHubLikeCount</span></span>     | <span data-ttu-id="f9437-193">number</span><span class="sxs-lookup"><span data-stu-id="f9437-193">number</span></span> |   <span data-ttu-id="f9437-194">Die Anzahl der Vorlieben, die zur Spielehubseite an dem angegebenen Datum hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f9437-194">The number of likes added to the Game Hub page on the specified date.</span></span>   |
| <span data-ttu-id="f9437-195">gameHubCommentCount</span><span class="sxs-lookup"><span data-stu-id="f9437-195">gameHubCommentCount</span></span>          | <span data-ttu-id="f9437-196">number</span><span class="sxs-lookup"><span data-stu-id="f9437-196">number</span></span> |  <span data-ttu-id="f9437-197">Die Anzahl der Kommentare, die zur Spielehubseite für Ihre App an dem angegebenen Datum hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="f9437-197">The number of comments added to the Game Hub page for your app on the specified date.</span></span>  |
| <span data-ttu-id="f9437-198">gameHubShareCount</span><span class="sxs-lookup"><span data-stu-id="f9437-198">gameHubShareCount</span></span>           | <span data-ttu-id="f9437-199">number</span><span class="sxs-lookup"><span data-stu-id="f9437-199">number</span></span> | <span data-ttu-id="f9437-200">Die Anzahl der Male, die die Spielehubseite für Ihre App von Kunden am angegebenen Datum geteilt wurden.</span><span class="sxs-lookup"><span data-stu-id="f9437-200">The number of times the Game Hub page for your app was shared by customers on the specified date.</span></span>   |
| <span data-ttu-id="f9437-201">gameHubFollowerCount</span><span class="sxs-lookup"><span data-stu-id="f9437-201">gameHubFollowerCount</span></span>          | <span data-ttu-id="f9437-202">number</span><span class="sxs-lookup"><span data-stu-id="f9437-202">number</span></span> | <span data-ttu-id="f9437-203">Die Anzahl der Follower der ganzen Zeit für die Spielehubseite für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="f9437-203">The number of all-time followers for the Game Hub page for your app.</span></span>   |


### <a name="response-example"></a><span data-ttu-id="f9437-204">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="f9437-204">Response example</span></span>

<span data-ttu-id="f9437-205">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="f9437-205">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "date": "2018-01-04",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 10,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0,
      "gameHubFollowerCount": 15924
    },
    {
      "date": "2018-01-05",
      "applicationId": "9NBLGGGZ5QDR",
      "gameHubLikeCount": 12,
      "gameHubCommentCount": 1,
      "gameHubShareCount": 0,
      "gameHubFollowerCount": 15931
    }
  ],
  "@nextLink": null,
  "TotalCount": 26
}
```

## <a name="related-topics"></a><span data-ttu-id="f9437-206">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f9437-206">Related topics</span></span>

* [<span data-ttu-id="f9437-207">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="f9437-207">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="f9437-208">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="f9437-208">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="f9437-209">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="f9437-209">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="f9437-210">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="f9437-210">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="f9437-211">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="f9437-211">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="f9437-212">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="f9437-212">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
