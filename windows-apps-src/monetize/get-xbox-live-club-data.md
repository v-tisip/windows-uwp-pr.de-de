---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Clubdaten abzurufen.
title: Abrufen von Xbox Live Clubdaten
ms.author: mcleans
ms.date: 06/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse, Clubs
ms.localizationpriority: medium
ms.openlocfilehash: b48b3756bb8143f1de6a0698b120658719de09c9
ms.sourcegitcommit: 633dd07c3a9a4d1c2421b43c612774c760b4ee58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "1976558"
---
# <a name="get-xbox-live-club-data"></a><span data-ttu-id="dc760-104">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="dc760-104">Get Xbox Live club data</span></span>

<span data-ttu-id="dc760-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Clubdaten für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="dc760-105">Use this method in the Microsoft Store analytics API to get club data for your [Xbox Live-enabled game](../xbox-live/index.md).</span></span> <span data-ttu-id="dc760-106">Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dc760-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc760-107">Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="dc760-107">This method only supports games for Xbox or games that use Xbox Live services.</span></span> <span data-ttu-id="dc760-108">Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="dc760-108">These games must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="dc760-109">Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="dc760-109">This method does not currently support games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc760-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="dc760-110">Prerequisites</span></span>

<span data-ttu-id="dc760-111">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="dc760-111">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="dc760-112">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="dc760-112">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="dc760-113">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="dc760-113">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="dc760-114">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="dc760-114">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="dc760-115">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="dc760-115">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="dc760-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="dc760-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="dc760-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="dc760-117">Request syntax</span></span>

| <span data-ttu-id="dc760-118">Methode</span><span class="sxs-lookup"><span data-stu-id="dc760-118">Method</span></span> | <span data-ttu-id="dc760-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="dc760-119">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="dc760-120">GET</span><span class="sxs-lookup"><span data-stu-id="dc760-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="dc760-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="dc760-121">Request header</span></span>

| <span data-ttu-id="dc760-122">Header</span><span class="sxs-lookup"><span data-stu-id="dc760-122">Header</span></span>        | <span data-ttu-id="dc760-123">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-123">Type</span></span>   | <span data-ttu-id="dc760-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="dc760-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="dc760-125">Authorization</span></span> | <span data-ttu-id="dc760-126">String</span><span class="sxs-lookup"><span data-stu-id="dc760-126">string</span></span> | <span data-ttu-id="dc760-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="dc760-127">Required.</span></span> <span data-ttu-id="dc760-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="dc760-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="dc760-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="dc760-129">Request parameters</span></span>


| <span data-ttu-id="dc760-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="dc760-130">Parameter</span></span>        | <span data-ttu-id="dc760-131">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-131">Type</span></span>   |  <span data-ttu-id="dc760-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-132">Description</span></span>      |  <span data-ttu-id="dc760-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dc760-133">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="dc760-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="dc760-134">applicationId</span></span> | <span data-ttu-id="dc760-135">String</span><span class="sxs-lookup"><span data-stu-id="dc760-135">string</span></span> | <span data-ttu-id="dc760-136">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Clubdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="dc760-136">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live club data.</span></span>  |  <span data-ttu-id="dc760-137">Ja</span><span class="sxs-lookup"><span data-stu-id="dc760-137">Yes</span></span>  |
| <span data-ttu-id="dc760-138">metricType</span><span class="sxs-lookup"><span data-stu-id="dc760-138">metricType</span></span> | <span data-ttu-id="dc760-139">String</span><span class="sxs-lookup"><span data-stu-id="dc760-139">string</span></span> | <span data-ttu-id="dc760-140">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="dc760-140">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="dc760-141">Geben Sie für diese Methode den Wert **communitymanagerclub** an.</span><span class="sxs-lookup"><span data-stu-id="dc760-141">For this method, specify the value **communitymanagerclub**.</span></span>  |  <span data-ttu-id="dc760-142">Ja</span><span class="sxs-lookup"><span data-stu-id="dc760-142">Yes</span></span>  |
| <span data-ttu-id="dc760-143">startDate</span><span class="sxs-lookup"><span data-stu-id="dc760-143">startDate</span></span> | <span data-ttu-id="dc760-144">date</span><span class="sxs-lookup"><span data-stu-id="dc760-144">date</span></span> | <span data-ttu-id="dc760-145">Das Startdatum im Datumsbereich der Clubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dc760-145">The start date in the date range of club data to retrieve.</span></span> <span data-ttu-id="dc760-146">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="dc760-146">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="dc760-147">Nein</span><span class="sxs-lookup"><span data-stu-id="dc760-147">No</span></span>  |
| <span data-ttu-id="dc760-148">endDate</span><span class="sxs-lookup"><span data-stu-id="dc760-148">endDate</span></span> | <span data-ttu-id="dc760-149">date</span><span class="sxs-lookup"><span data-stu-id="dc760-149">date</span></span> | <span data-ttu-id="dc760-150">Das Enddatum im Datumsbereich der Clubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dc760-150">The end date in the date range of club data to retrieve.</span></span> <span data-ttu-id="dc760-151">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="dc760-151">The default is the current date.</span></span> |  <span data-ttu-id="dc760-152">Nein</span><span class="sxs-lookup"><span data-stu-id="dc760-152">No</span></span>  |
| <span data-ttu-id="dc760-153">top</span><span class="sxs-lookup"><span data-stu-id="dc760-153">top</span></span> | <span data-ttu-id="dc760-154">int</span><span class="sxs-lookup"><span data-stu-id="dc760-154">int</span></span> | <span data-ttu-id="dc760-155">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dc760-155">The number of rows of data to return in the request.</span></span> <span data-ttu-id="dc760-156">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="dc760-156">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="dc760-157">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="dc760-157">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="dc760-158">Nein</span><span class="sxs-lookup"><span data-stu-id="dc760-158">No</span></span>  |
| <span data-ttu-id="dc760-159">skip</span><span class="sxs-lookup"><span data-stu-id="dc760-159">skip</span></span> | <span data-ttu-id="dc760-160">int</span><span class="sxs-lookup"><span data-stu-id="dc760-160">int</span></span> | <span data-ttu-id="dc760-161">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dc760-161">The number of rows to skip in the query.</span></span> <span data-ttu-id="dc760-162">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="dc760-162">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="dc760-163">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="dc760-163">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="dc760-164">Nein</span><span class="sxs-lookup"><span data-stu-id="dc760-164">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="dc760-165">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="dc760-165">Request example</span></span>

<span data-ttu-id="dc760-166">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Clubdaten für Ihr Xbox Live-fähiges Spiel an.</span><span class="sxs-lookup"><span data-stu-id="dc760-166">The following example demonstrates a request for getting club data for your Xbox Live-enabled game.</span></span> <span data-ttu-id="dc760-167">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="dc760-167">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=communitymanagerclub&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="dc760-168">Antwort</span><span class="sxs-lookup"><span data-stu-id="dc760-168">Response</span></span>

| <span data-ttu-id="dc760-169">Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-169">Value</span></span>      | <span data-ttu-id="dc760-170">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-170">Type</span></span>   | <span data-ttu-id="dc760-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-171">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="dc760-172">Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-172">Value</span></span>      | <span data-ttu-id="dc760-173">Array</span><span class="sxs-lookup"><span data-stu-id="dc760-173">array</span></span>  | <span data-ttu-id="dc760-174">Ein Array mit einem [ProductData](#productdata)-Objekt, das Daten für Clubs enthält, die sich auf Ihr Spiel sowie auf ein [XboxwideData](#xboxwidedata)-Objekt beziehen, das Clubdaten für alle Xbox Live Kunden enthält.</span><span class="sxs-lookup"><span data-stu-id="dc760-174">An array that contains one [ProductData](#productdata) object that contains data for clubs related to your game and one [XboxwideData](#xboxwidedata) object that contains club data for all Xbox Live customers.</span></span> <span data-ttu-id="dc760-175">Diese Daten werden zu Vergleichszwecken mit den Daten für Ihr Spiel beigefügt.</span><span class="sxs-lookup"><span data-stu-id="dc760-175">This data is included for comparison purposes with the data for your game.</span></span>  |
| @nextLink  | <span data-ttu-id="dc760-176">String</span><span class="sxs-lookup"><span data-stu-id="dc760-176">string</span></span> | <span data-ttu-id="dc760-177">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="dc760-177">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="dc760-178">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10000 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="dc760-178">For example, this value is returned if the **top** parameter of the request is set to 10000 but there are more than 10000 rows of data for the query.</span></span> |
| <span data-ttu-id="dc760-179">TotalCount</span><span class="sxs-lookup"><span data-stu-id="dc760-179">TotalCount</span></span> | <span data-ttu-id="dc760-180">int</span><span class="sxs-lookup"><span data-stu-id="dc760-180">int</span></span>    | <span data-ttu-id="dc760-181">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="dc760-181">The total number of rows in the data result for the query.</span></span> |


### <a name="productdata"></a><span data-ttu-id="dc760-182">ProductData</span><span class="sxs-lookup"><span data-stu-id="dc760-182">ProductData</span></span>

<span data-ttu-id="dc760-183">Diese Ressource enthält Clubdaten für Ihr Spiel.</span><span class="sxs-lookup"><span data-stu-id="dc760-183">This resource contains club data for your game.</span></span>

| <span data-ttu-id="dc760-184">Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-184">Value</span></span>           | <span data-ttu-id="dc760-185">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-185">Type</span></span>    | <span data-ttu-id="dc760-186">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-186">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="dc760-187">date</span><span class="sxs-lookup"><span data-stu-id="dc760-187">date</span></span>            |  <span data-ttu-id="dc760-188">String</span><span class="sxs-lookup"><span data-stu-id="dc760-188">string</span></span> |   <span data-ttu-id="dc760-189">Das Datum für die Clubdaten.</span><span class="sxs-lookup"><span data-stu-id="dc760-189">The date for the club data.</span></span>   |
|  <span data-ttu-id="dc760-190">applicationId</span><span class="sxs-lookup"><span data-stu-id="dc760-190">applicationId</span></span>               |    <span data-ttu-id="dc760-191">String</span><span class="sxs-lookup"><span data-stu-id="dc760-191">string</span></span>     |  <span data-ttu-id="dc760-192">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Clubdaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="dc760-192">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved club data.</span></span>   |
|  <span data-ttu-id="dc760-193">clubsWithTitleActivity</span><span class="sxs-lookup"><span data-stu-id="dc760-193">clubsWithTitleActivity</span></span>               |    <span data-ttu-id="dc760-194">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-194">int</span></span>     |  <span data-ttu-id="dc760-195">Die Anzahl der Clubs, die an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="dc760-195">The number of clubs that are socially engaged with your game.</span></span>   |     
|  <span data-ttu-id="dc760-196">clubsExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="dc760-196">clubsExclusiveToGame</span></span>               |   <span data-ttu-id="dc760-197">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-197">int</span></span>      |  <span data-ttu-id="dc760-198">Die Anzahl der Clubs, die ausschließlich an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="dc760-198">The number of clubs that are socially engaged exclusively with your game.</span></span>   |     
|  <span data-ttu-id="dc760-199">clubFacts</span><span class="sxs-lookup"><span data-stu-id="dc760-199">clubFacts</span></span>               |   <span data-ttu-id="dc760-200">Array</span><span class="sxs-lookup"><span data-stu-id="dc760-200">array</span></span>      |   <span data-ttu-id="dc760-201">Enthält ein oder mehrere [ClubFacts](#clubfacts)-Objekte zu den einzelnen Clubs, die an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="dc760-201">Contains one or more [ClubFacts](#clubfacts) objects about each of the clubs that are socially engaged with your game.</span></span>   |


### <a name="xboxwidedata"></a><span data-ttu-id="dc760-202">XboxwideData</span><span class="sxs-lookup"><span data-stu-id="dc760-202">XboxwideData</span></span>

<span data-ttu-id="dc760-203">Diese Ressource enthält die durchschnittlichen Clubdaten über alle Xbox Live-Kunden.</span><span class="sxs-lookup"><span data-stu-id="dc760-203">This resource contains average club data across all Xbox Live customers.</span></span>

| <span data-ttu-id="dc760-204">Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-204">Value</span></span>           | <span data-ttu-id="dc760-205">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-205">Type</span></span>    | <span data-ttu-id="dc760-206">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-206">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="dc760-207">date</span><span class="sxs-lookup"><span data-stu-id="dc760-207">date</span></span>            |  <span data-ttu-id="dc760-208">String</span><span class="sxs-lookup"><span data-stu-id="dc760-208">string</span></span> |   <span data-ttu-id="dc760-209">Das Datum für die Clubdaten.</span><span class="sxs-lookup"><span data-stu-id="dc760-209">The date for the club data.</span></span>   |
|  <span data-ttu-id="dc760-210">applicationId</span><span class="sxs-lookup"><span data-stu-id="dc760-210">applicationId</span></span>  |    <span data-ttu-id="dc760-211">String</span><span class="sxs-lookup"><span data-stu-id="dc760-211">string</span></span>     |   <span data-ttu-id="dc760-212">Im **XboxwideData**-Objekt hat diese Zeichenfolge ist immer den Wert **XBOXWIDE**.</span><span class="sxs-lookup"><span data-stu-id="dc760-212">In the **XboxwideData** object, this string is always the value **XBOXWIDE**.</span></span>  |
|  <span data-ttu-id="dc760-213">clubsWithTitleActivity</span><span class="sxs-lookup"><span data-stu-id="dc760-213">clubsWithTitleActivity</span></span>               |   <span data-ttu-id="dc760-214">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-214">int</span></span>     |  <span data-ttu-id="dc760-215">Durchschnittlich die Anzahl der Clubs mit Kunden, die an einem Xbox Live-fähigen Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="dc760-215">On average, the number of clubs with customers that are socially engaged with an Xbox Live-enabled game.</span></span>    |     
|  <span data-ttu-id="dc760-216">clubsExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="dc760-216">clubsExclusiveToGame</span></span>               |   <span data-ttu-id="dc760-217">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-217">int</span></span>      |  <span data-ttu-id="dc760-218">Durchschnittlich die Anzahl der Clubs mit Kunden, die ausschließlich an einem Xbox Live-fähigen Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="dc760-218">On average, the number of clubs that are socially engaged exclusively with an Xbox Live-enabled game.</span></span>   |     
|  <span data-ttu-id="dc760-219">clubFacts</span><span class="sxs-lookup"><span data-stu-id="dc760-219">clubFacts</span></span>               |   <span data-ttu-id="dc760-220">Objekt</span><span class="sxs-lookup"><span data-stu-id="dc760-220">object</span></span>      |  <span data-ttu-id="dc760-221">Enthält ein [ClubFacts](#clubfacts)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="dc760-221">Contains one [ClubFacts](#clubfacts) object.</span></span> <span data-ttu-id="dc760-222">Dieses Objekt ist bedeutungslos im Kontext des **XboxwideData**-Objekts und verfügt über Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="dc760-222">This object is meaningless in the context of the **XboxwideData** object and has default values.</span></span>  |


### <a name="clubfacts"></a><span data-ttu-id="dc760-223">ClubFacts</span><span class="sxs-lookup"><span data-stu-id="dc760-223">ClubFacts</span></span>

<span data-ttu-id="dc760-224">Im **ProductData**-Objekt enthält dieses Objekt enthält Daten für einen bestimmten Club, der Aktivitäten im Bezug auf Ihr Spiel hat.</span><span class="sxs-lookup"><span data-stu-id="dc760-224">In the **ProductData** object, this object contains data for a specific club that has activity related to your game.</span></span> <span data-ttu-id="dc760-225">Im **XboxwideData**-Objekt ist dieses Objekt bedeutungslos und verfügt über Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="dc760-225">In the **XboxwideData** object, this object is meaningless and has default values.</span></span>

| <span data-ttu-id="dc760-226">Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-226">Value</span></span>           | <span data-ttu-id="dc760-227">Typ</span><span class="sxs-lookup"><span data-stu-id="dc760-227">Type</span></span>    | <span data-ttu-id="dc760-228">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dc760-228">Description</span></span>        |
|-----------------|---------|--------------------|
|  <span data-ttu-id="dc760-229">name</span><span class="sxs-lookup"><span data-stu-id="dc760-229">name</span></span>            |  <span data-ttu-id="dc760-230">String</span><span class="sxs-lookup"><span data-stu-id="dc760-230">string</span></span>  |   <span data-ttu-id="dc760-231">Im **ProductData**-Objekt ist dies der Name des Clubs.</span><span class="sxs-lookup"><span data-stu-id="dc760-231">In the **ProductData** object, this is the name of the club.</span></span> <span data-ttu-id="dc760-232">Im **XboxwideData**-Objekt hat dies immer den Wert **XBOXWIDE**.</span><span class="sxs-lookup"><span data-stu-id="dc760-232">In the **XboxwideData** object, this is always the value **XBOXWIDE**.</span></span>           |
|  <span data-ttu-id="dc760-233">memberCount</span><span class="sxs-lookup"><span data-stu-id="dc760-233">memberCount</span></span>               |    <span data-ttu-id="dc760-234">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-234">int</span></span>     | <span data-ttu-id="dc760-235">Im **ProductData**-Objekt ist dies die Anzahl der Clubmitglieder, mit Ausnahme der nicht-Mitglieder, die den Club nur besuchen.</span><span class="sxs-lookup"><span data-stu-id="dc760-235">In the **ProductData** object, this is the number of members in the club, excluding non-members who are just visiting the club.</span></span> <span data-ttu-id="dc760-236">Im **XboxwideData**-Objekt ist dies immer 0.</span><span class="sxs-lookup"><span data-stu-id="dc760-236">In the **XboxwideData** object, this is always 0.</span></span>    |
|  <span data-ttu-id="dc760-237">titleSocialActionsCount</span><span class="sxs-lookup"><span data-stu-id="dc760-237">titleSocialActionsCount</span></span>               |    <span data-ttu-id="dc760-238">Int</span><span class="sxs-lookup"><span data-stu-id="dc760-238">int</span></span>     |  <span data-ttu-id="dc760-239">Im **ProductData**-Objekt ist dies die Anzahl der gemeinschaftlichen Aktionen, die Mitglieder im Club im Bezug auf Ihr Spiel ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="dc760-239">In the **ProductData** object, this is the number of social actions that members in the club have performed that are related to your game.</span></span> <span data-ttu-id="dc760-240">Im **XboxwideData**-Objekt ist dies immer 0</span><span class="sxs-lookup"><span data-stu-id="dc760-240">In the **XboxwideData** object, this is always 0</span></span>   |
|  <span data-ttu-id="dc760-241">isExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="dc760-241">isExclusiveToGame</span></span>               |    <span data-ttu-id="dc760-242">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="dc760-242">Boolean</span></span>     |  <span data-ttu-id="dc760-243">Im **ProductData**-Objekt gibt dies an, ob der aktuelle Club ausschließlich nur an Ihrem Spiel gemeinschaftlich beteiligt ist.</span><span class="sxs-lookup"><span data-stu-id="dc760-243">In the **ProductData** object, this indicates whether the current club is socially engaged exclusively with your game.</span></span> <span data-ttu-id="dc760-244">Im **XboxwideData**-Objekt ist dies immer wahr.</span><span class="sxs-lookup"><span data-stu-id="dc760-244">In the **XboxwideData** object, this is always true.</span></span>  |


### <a name="response-example"></a><span data-ttu-id="dc760-245">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="dc760-245">Response example</span></span>

<span data-ttu-id="dc760-246">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="dc760-246">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "ProductData": [
        {
          "date": "2018-01-30",
          "applicationId": "9NBLGGGZ5QDR",
          "clubsWithTitleActivity": 3,
          "clubsExclusiveToGame": 1,
          "clubFacts": [
            {
              "name": "Club Contoso Racing",
              "memberCount": 1,
              "titleSocialActionsCount": 1,
              "isExclusiveToGame": false
            },
            {
              "name": "Club Contoso Sports",
              "memberCount": 12,
              "titleSocialActionsCount": 9,
              "isExclusiveToGame": false
            },
            {
              "name": "Club Contoso Maze",
              "memberCount": 4,
              "titleSocialActionsCount": 2,
              "isExclusiveToGame": false
            }
          ]
        }
      ],
      "XboxwideData": [
        {
          "date": "2018-01-30",
          "applicationId": "XBOXWIDE",
          "clubsWithTitleActivity": 25,
          "clubsExclusiveToGame": 3,
          "clubFacts": [
            {
              "name": "XBOXWIDE",
              "memberCount": 0,
              "titleSocialActionsCount": 0,
              "isExclusiveToGame": true
            }
          ]
        }
      ]
    }
  ],
  "@nextLink": "gameanalytics?applicationId=9NBLGGGZ5QDR&metricType=communitymanagerclub&top=1&skip=1&startDate=2018/01/04&endDate=2018/02/02&orderby=date desc",
  "TotalCount": 27
}
```

## <a name="related-topics"></a><span data-ttu-id="dc760-247">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="dc760-247">Related topics</span></span>

* [<span data-ttu-id="dc760-248">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="dc760-248">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="dc760-249">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="dc760-249">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="dc760-250">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="dc760-250">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="dc760-251">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="dc760-251">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="dc760-252">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="dc760-252">Get Xbox Live game hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="dc760-253">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="dc760-253">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
