---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Clubdaten abzurufen.
title: Abrufen von Xbox Live Clubdaten
ms.author: mcleans
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse, Clubs
ms.localizationpriority: medium
ms.openlocfilehash: 09721bf1259c3f44ce2acd5014476aa7e962eaa5
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816685"
---
# <a name="get-xbox-live-club-data"></a><span data-ttu-id="a85a0-104">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-104">Get Xbox Live club data</span></span>

<span data-ttu-id="a85a0-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Clubdaten für Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-105">Use this method in the Microsoft Store analytics API to get club data for your [Xbox Live-enabled game](../xbox-live/index.md).</span></span> <span data-ttu-id="a85a0-106">Diese Informationen sind auch im [Xbox Analysebericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a85a0-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a85a0-107">Diese Methode unterstützt derzeit nur Xbox Live-fähige Spiele, die von [Microsoft Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht werden oder die mithilfe des [ID@Xbox Programms](../xbox-live/developer-program-overview.md#id) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="a85a0-107">This method currently only supports Xbox Live-enabled games that are published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) or that are submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="a85a0-108">Es gibt keine Daten für Spiele zurück, die mithilfe des [Xbox Live Creators-Programms](../xbox-live/developer-program-overview.md#xbox-live-creators-program) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="a85a0-108">It does not return data for games that were submitted via the [Xbox Live Creators Program](../xbox-live/developer-program-overview.md#xbox-live-creators-program).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a85a0-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a85a0-109">Prerequisites</span></span>

<span data-ttu-id="a85a0-110">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="a85a0-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="a85a0-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="a85a0-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="a85a0-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a85a0-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="a85a0-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="a85a0-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="a85a0-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-114">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="a85a0-115">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a85a0-115">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="a85a0-116">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="a85a0-116">Request syntax</span></span>

| <span data-ttu-id="a85a0-117">Methode</span><span class="sxs-lookup"><span data-stu-id="a85a0-117">Method</span></span> | <span data-ttu-id="a85a0-118">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a85a0-118">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="a85a0-119">GET</span><span class="sxs-lookup"><span data-stu-id="a85a0-119">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="a85a0-120">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a85a0-120">Request header</span></span>

| <span data-ttu-id="a85a0-121">Header</span><span class="sxs-lookup"><span data-stu-id="a85a0-121">Header</span></span>        | <span data-ttu-id="a85a0-122">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-122">Type</span></span>   | <span data-ttu-id="a85a0-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-123">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="a85a0-124">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="a85a0-124">Authorization</span></span> | <span data-ttu-id="a85a0-125">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-125">string</span></span> | <span data-ttu-id="a85a0-126">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a85a0-126">Required.</span></span> <span data-ttu-id="a85a0-127">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="a85a0-127">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="a85a0-128">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="a85a0-128">Request parameters</span></span>


| <span data-ttu-id="a85a0-129">Parameter</span><span class="sxs-lookup"><span data-stu-id="a85a0-129">Parameter</span></span>        | <span data-ttu-id="a85a0-130">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-130">Type</span></span>   |  <span data-ttu-id="a85a0-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-131">Description</span></span>      |  <span data-ttu-id="a85a0-132">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="a85a0-132">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="a85a0-133">applicationId</span><span class="sxs-lookup"><span data-stu-id="a85a0-133">applicationId</span></span> | <span data-ttu-id="a85a0-134">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-134">string</span></span> | <span data-ttu-id="a85a0-135">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die Xbox Live Clubdaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a85a0-135">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve Xbox Live club data.</span></span>  |  <span data-ttu-id="a85a0-136">Ja</span><span class="sxs-lookup"><span data-stu-id="a85a0-136">Yes</span></span>  |
| <span data-ttu-id="a85a0-137">metricType</span><span class="sxs-lookup"><span data-stu-id="a85a0-137">metricType</span></span> | <span data-ttu-id="a85a0-138">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-138">string</span></span> | <span data-ttu-id="a85a0-139">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="a85a0-139">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="a85a0-140">Geben Sie für diese Methode den Wert **communitymanagerclub** an.</span><span class="sxs-lookup"><span data-stu-id="a85a0-140">For this method, specify the value **communitymanagerclub**.</span></span>  |  <span data-ttu-id="a85a0-141">Ja</span><span class="sxs-lookup"><span data-stu-id="a85a0-141">Yes</span></span>  |
| <span data-ttu-id="a85a0-142">startDate</span><span class="sxs-lookup"><span data-stu-id="a85a0-142">startDate</span></span> | <span data-ttu-id="a85a0-143">date</span><span class="sxs-lookup"><span data-stu-id="a85a0-143">date</span></span> | <span data-ttu-id="a85a0-144">Das Startdatum im Datumsbereich der Clubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-144">The start date in the date range of club data to retrieve.</span></span> <span data-ttu-id="a85a0-145">Der Standardwert ist 30Tage vor dem aktuellen Datum.</span><span class="sxs-lookup"><span data-stu-id="a85a0-145">The default is 30 days before the current date.</span></span> |  <span data-ttu-id="a85a0-146">Nein</span><span class="sxs-lookup"><span data-stu-id="a85a0-146">No</span></span>  |
| <span data-ttu-id="a85a0-147">endDate</span><span class="sxs-lookup"><span data-stu-id="a85a0-147">endDate</span></span> | <span data-ttu-id="a85a0-148">date</span><span class="sxs-lookup"><span data-stu-id="a85a0-148">date</span></span> | <span data-ttu-id="a85a0-149">Das Enddatum im Datumsbereich der Clubdaten, die abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-149">The end date in the date range of club data to retrieve.</span></span> <span data-ttu-id="a85a0-150">Der Standardwert ist das aktuelle Datum.</span><span class="sxs-lookup"><span data-stu-id="a85a0-150">The default is the current date.</span></span> |  <span data-ttu-id="a85a0-151">Nein</span><span class="sxs-lookup"><span data-stu-id="a85a0-151">No</span></span>  |
| <span data-ttu-id="a85a0-152">top</span><span class="sxs-lookup"><span data-stu-id="a85a0-152">top</span></span> | <span data-ttu-id="a85a0-153">int</span><span class="sxs-lookup"><span data-stu-id="a85a0-153">int</span></span> | <span data-ttu-id="a85a0-154">Die Anzahl der Datenzeilen, die in der Anforderung zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-154">The number of rows of data to return in the request.</span></span> <span data-ttu-id="a85a0-155">Der Maximal- und Standardwert ist 10.000, wenn nicht anders angegeben.</span><span class="sxs-lookup"><span data-stu-id="a85a0-155">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="a85a0-156">Wenn die Abfrage keine weiteren Zeilen enthält, entält der Antworttext den Link „Weiter“, den Sie verwenden können, um die nächste Seite mit Daten anzufordern.</span><span class="sxs-lookup"><span data-stu-id="a85a0-156">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |  <span data-ttu-id="a85a0-157">Nein</span><span class="sxs-lookup"><span data-stu-id="a85a0-157">No</span></span>  |
| <span data-ttu-id="a85a0-158">skip</span><span class="sxs-lookup"><span data-stu-id="a85a0-158">skip</span></span> | <span data-ttu-id="a85a0-159">int</span><span class="sxs-lookup"><span data-stu-id="a85a0-159">int</span></span> | <span data-ttu-id="a85a0-160">Die Anzahl der Zeilen, die in der Abfrage übersprungen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-160">The number of rows to skip in the query.</span></span> <span data-ttu-id="a85a0-161">Verwenden Sie diesen Parameter, um große Datensätze durchzublättern.</span><span class="sxs-lookup"><span data-stu-id="a85a0-161">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="a85a0-162">Beispielsweise rufen „top=10000“ und „skip=0“ die ersten 10.000Datenzeilen ab, „top=10000“ und „skip=10000“ die nächsten 10.000Datenzeilen usw.</span><span class="sxs-lookup"><span data-stu-id="a85a0-162">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> |  <span data-ttu-id="a85a0-163">Nein</span><span class="sxs-lookup"><span data-stu-id="a85a0-163">No</span></span>  |


### <a name="request-example"></a><span data-ttu-id="a85a0-164">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="a85a0-164">Request example</span></span>

<span data-ttu-id="a85a0-165">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von Clubdaten für Ihr Xbox Live-fähiges Spiel an.</span><span class="sxs-lookup"><span data-stu-id="a85a0-165">The following example demonstrates a request for getting club data for your Xbox Live-enabled game.</span></span> <span data-ttu-id="a85a0-166">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="a85a0-166">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=communitymanagerclub&top=10&skip=0 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="a85a0-167">Antwort</span><span class="sxs-lookup"><span data-stu-id="a85a0-167">Response</span></span>

| <span data-ttu-id="a85a0-168">Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-168">Value</span></span>      | <span data-ttu-id="a85a0-169">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-169">Type</span></span>   | <span data-ttu-id="a85a0-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-170">Description</span></span>                  |
|------------|--------|-------------------------------------------------------|
| <span data-ttu-id="a85a0-171">Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-171">Value</span></span>      | <span data-ttu-id="a85a0-172">Array</span><span class="sxs-lookup"><span data-stu-id="a85a0-172">array</span></span>  | <span data-ttu-id="a85a0-173">Ein Array mit einem [ProductData](#productdata)-Objekt, das Daten für Clubs enthält, die sich auf Ihr Spiel sowie auf ein [XboxwideData](#xboxwidedata)-Objekt beziehen, das Clubdaten für alle Xbox Live Kunden enthält.</span><span class="sxs-lookup"><span data-stu-id="a85a0-173">An array that contains one [ProductData](#productdata) object that contains data for clubs related to your game and one [XboxwideData](#xboxwidedata) object that contains club data for all Xbox Live customers.</span></span> <span data-ttu-id="a85a0-174">Diese Daten werden zu Vergleichszwecken mit den Daten für Ihr Spiel beigefügt.</span><span class="sxs-lookup"><span data-stu-id="a85a0-174">This data is included for comparison purposes with the data for your game.</span></span>  |
| @nextLink  | <span data-ttu-id="a85a0-175">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-175">string</span></span> | <span data-ttu-id="a85a0-176">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="a85a0-176">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="a85a0-177">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10000 festgelegt ist, es jedoch mehr als 10000 Zeilen mit Daten für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="a85a0-177">For example, this value is returned if the **top** parameter of the request is set to 10000 but there are more than 10000 rows of data for the query.</span></span> |
| <span data-ttu-id="a85a0-178">TotalCount</span><span class="sxs-lookup"><span data-stu-id="a85a0-178">TotalCount</span></span> | <span data-ttu-id="a85a0-179">int</span><span class="sxs-lookup"><span data-stu-id="a85a0-179">int</span></span>    | <span data-ttu-id="a85a0-180">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="a85a0-180">The total number of rows in the data result for the query.</span></span> |


### <a name="productdata"></a><span data-ttu-id="a85a0-181">ProductData</span><span class="sxs-lookup"><span data-stu-id="a85a0-181">ProductData</span></span>

<span data-ttu-id="a85a0-182">Diese Ressource enthält Clubdaten für Ihr Spiel.</span><span class="sxs-lookup"><span data-stu-id="a85a0-182">This resource contains club data for your game.</span></span>

| <span data-ttu-id="a85a0-183">Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-183">Value</span></span>           | <span data-ttu-id="a85a0-184">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-184">Type</span></span>    | <span data-ttu-id="a85a0-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-185">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="a85a0-186">date</span><span class="sxs-lookup"><span data-stu-id="a85a0-186">date</span></span>            |  <span data-ttu-id="a85a0-187">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-187">string</span></span> |   <span data-ttu-id="a85a0-188">Das Datum für die Clubdaten.</span><span class="sxs-lookup"><span data-stu-id="a85a0-188">The date for the club data.</span></span>   |
|  <span data-ttu-id="a85a0-189">applicationId</span><span class="sxs-lookup"><span data-stu-id="a85a0-189">applicationId</span></span>               |    <span data-ttu-id="a85a0-190">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-190">string</span></span>     |  <span data-ttu-id="a85a0-191">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Clubdaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="a85a0-191">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved club data.</span></span>   |
|  <span data-ttu-id="a85a0-192">clubsWithTitleActivity</span><span class="sxs-lookup"><span data-stu-id="a85a0-192">clubsWithTitleActivity</span></span>               |    <span data-ttu-id="a85a0-193">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-193">int</span></span>     |  <span data-ttu-id="a85a0-194">Die Anzahl der Clubs, die an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="a85a0-194">The number of clubs that are socially engaged with your game.</span></span>   |     
|  <span data-ttu-id="a85a0-195">clubsExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="a85a0-195">clubsExclusiveToGame</span></span>               |   <span data-ttu-id="a85a0-196">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-196">int</span></span>      |  <span data-ttu-id="a85a0-197">Die Anzahl der Clubs, die ausschließlich an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="a85a0-197">The number of clubs that are socially engaged exclusively with your game.</span></span>   |     
|  <span data-ttu-id="a85a0-198">clubFacts</span><span class="sxs-lookup"><span data-stu-id="a85a0-198">clubFacts</span></span>               |   <span data-ttu-id="a85a0-199">Array</span><span class="sxs-lookup"><span data-stu-id="a85a0-199">array</span></span>      |   <span data-ttu-id="a85a0-200">Enthält ein oder mehrere [ClubFacts](#clubfacts)-Objekte zu den einzelnen Clubs, die an Ihrem Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="a85a0-200">Contains one or more [ClubFacts](#clubfacts) objects about each of the clubs that are socially engaged with your game.</span></span>   |


### <a name="xboxwidedata"></a><span data-ttu-id="a85a0-201">XboxwideData</span><span class="sxs-lookup"><span data-stu-id="a85a0-201">XboxwideData</span></span>

<span data-ttu-id="a85a0-202">Diese Ressource enthält die durchschnittlichen Clubdaten über alle Xbox Live-Kunden.</span><span class="sxs-lookup"><span data-stu-id="a85a0-202">This resource contains average club data across all Xbox Live customers.</span></span>

| <span data-ttu-id="a85a0-203">Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-203">Value</span></span>           | <span data-ttu-id="a85a0-204">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-204">Type</span></span>    | <span data-ttu-id="a85a0-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-205">Description</span></span>        |
|-----------------|---------|------|
| <span data-ttu-id="a85a0-206">date</span><span class="sxs-lookup"><span data-stu-id="a85a0-206">date</span></span>            |  <span data-ttu-id="a85a0-207">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-207">string</span></span> |   <span data-ttu-id="a85a0-208">Das Datum für die Clubdaten.</span><span class="sxs-lookup"><span data-stu-id="a85a0-208">The date for the club data.</span></span>   |
|  <span data-ttu-id="a85a0-209">applicationId</span><span class="sxs-lookup"><span data-stu-id="a85a0-209">applicationId</span></span>  |    <span data-ttu-id="a85a0-210">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-210">string</span></span>     |   <span data-ttu-id="a85a0-211">Im **XboxwideData**-Objekt hat diese Zeichenfolge ist immer den Wert **XBOXWIDE**.</span><span class="sxs-lookup"><span data-stu-id="a85a0-211">In the **XboxwideData** object, this string is always the value **XBOXWIDE**.</span></span>  |
|  <span data-ttu-id="a85a0-212">clubsWithTitleActivity</span><span class="sxs-lookup"><span data-stu-id="a85a0-212">clubsWithTitleActivity</span></span>               |   <span data-ttu-id="a85a0-213">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-213">int</span></span>     |  <span data-ttu-id="a85a0-214">Durchschnittlich die Anzahl der Clubs mit Kunden, die an einem Xbox Live-fähigen Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="a85a0-214">On average, the number of clubs with customers that are socially engaged with an Xbox Live-enabled game.</span></span>    |     
|  <span data-ttu-id="a85a0-215">clubsExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="a85a0-215">clubsExclusiveToGame</span></span>               |   <span data-ttu-id="a85a0-216">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-216">int</span></span>      |  <span data-ttu-id="a85a0-217">Durchschnittlich die Anzahl der Clubs mit Kunden, die ausschließlich an einem Xbox Live-fähigen Spiel gemeinschaftlich beteiligt sind.</span><span class="sxs-lookup"><span data-stu-id="a85a0-217">On average, the number of clubs that are socially engaged exclusively with an Xbox Live-enabled game.</span></span>   |     
|  <span data-ttu-id="a85a0-218">clubFacts</span><span class="sxs-lookup"><span data-stu-id="a85a0-218">clubFacts</span></span>               |   <span data-ttu-id="a85a0-219">Objekt</span><span class="sxs-lookup"><span data-stu-id="a85a0-219">object</span></span>      |  <span data-ttu-id="a85a0-220">Enthält ein [ClubFacts](#clubfacts)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="a85a0-220">Contains one [ClubFacts](#clubfacts) object.</span></span> <span data-ttu-id="a85a0-221">Dieses Objekt ist bedeutungslos im Kontext des **XboxwideData**-Objekts und verfügt über Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="a85a0-221">This object is meaningless in the context of the **XboxwideData** object and has default values.</span></span>  |


### <a name="clubfacts"></a><span data-ttu-id="a85a0-222">ClubFacts</span><span class="sxs-lookup"><span data-stu-id="a85a0-222">ClubFacts</span></span>

<span data-ttu-id="a85a0-223">Im **ProductData**-Objekt enthält dieses Objekt enthält Daten für einen bestimmten Club, der Aktivitäten im Bezug auf Ihr Spiel hat.</span><span class="sxs-lookup"><span data-stu-id="a85a0-223">In the **ProductData** object, this object contains data for a specific club that has activity related to your game.</span></span> <span data-ttu-id="a85a0-224">Im **XboxwideData**-Objekt ist dieses Objekt bedeutungslos und verfügt über Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="a85a0-224">In the **XboxwideData** object, this object is meaningless and has default values.</span></span>

| <span data-ttu-id="a85a0-225">Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-225">Value</span></span>           | <span data-ttu-id="a85a0-226">Typ</span><span class="sxs-lookup"><span data-stu-id="a85a0-226">Type</span></span>    | <span data-ttu-id="a85a0-227">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a85a0-227">Description</span></span>        |
|-----------------|---------|--------------------|
|  <span data-ttu-id="a85a0-228">name</span><span class="sxs-lookup"><span data-stu-id="a85a0-228">name</span></span>            |  <span data-ttu-id="a85a0-229">String</span><span class="sxs-lookup"><span data-stu-id="a85a0-229">string</span></span>  |   <span data-ttu-id="a85a0-230">Im **ProductData**-Objekt ist dies der Name des Clubs.</span><span class="sxs-lookup"><span data-stu-id="a85a0-230">In the **ProductData** object, this is the name of the club.</span></span> <span data-ttu-id="a85a0-231">Im **XboxwideData**-Objekt hat dies immer den Wert **XBOXWIDE**.</span><span class="sxs-lookup"><span data-stu-id="a85a0-231">In the **XboxwideData** object, this is always the value **XBOXWIDE**.</span></span>           |
|  <span data-ttu-id="a85a0-232">memberCount</span><span class="sxs-lookup"><span data-stu-id="a85a0-232">memberCount</span></span>               |    <span data-ttu-id="a85a0-233">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-233">int</span></span>     | <span data-ttu-id="a85a0-234">Im **ProductData**-Objekt ist dies die Anzahl der Clubmitglieder, mit Ausnahme der nicht-Mitglieder, die den Club nur besuchen.</span><span class="sxs-lookup"><span data-stu-id="a85a0-234">In the **ProductData** object, this is the number of members in the club, excluding non-members who are just visiting the club.</span></span> <span data-ttu-id="a85a0-235">Im **XboxwideData**-Objekt ist dies immer 0.</span><span class="sxs-lookup"><span data-stu-id="a85a0-235">In the **XboxwideData** object, this is always 0.</span></span>    |
|  <span data-ttu-id="a85a0-236">titleSocialActionsCount</span><span class="sxs-lookup"><span data-stu-id="a85a0-236">titleSocialActionsCount</span></span>               |    <span data-ttu-id="a85a0-237">Int</span><span class="sxs-lookup"><span data-stu-id="a85a0-237">int</span></span>     |  <span data-ttu-id="a85a0-238">Im **ProductData**-Objekt ist dies die Anzahl der gemeinschaftlichen Aktionen, die Mitglieder im Club im Bezug auf Ihr Spiel ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="a85a0-238">In the **ProductData** object, this is the number of social actions that members in the club have performed that are related to your game.</span></span> <span data-ttu-id="a85a0-239">Im **XboxwideData**-Objekt ist dies immer 0</span><span class="sxs-lookup"><span data-stu-id="a85a0-239">In the **XboxwideData** object, this is always 0</span></span>   |
|  <span data-ttu-id="a85a0-240">isExclusiveToGame</span><span class="sxs-lookup"><span data-stu-id="a85a0-240">isExclusiveToGame</span></span>               |    <span data-ttu-id="a85a0-241">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="a85a0-241">Boolean</span></span>     |  <span data-ttu-id="a85a0-242">Im **ProductData**-Objekt gibt dies an, ob der aktuelle Club ausschließlich nur an Ihrem Spiel gemeinschaftlich beteiligt ist.</span><span class="sxs-lookup"><span data-stu-id="a85a0-242">In the **ProductData** object, this indicates whether the current club is socially engaged exclusively with your game.</span></span> <span data-ttu-id="a85a0-243">Im **XboxwideData**-Objekt ist dies immer wahr.</span><span class="sxs-lookup"><span data-stu-id="a85a0-243">In the **XboxwideData** object, this is always true.</span></span>  |


### <a name="response-example"></a><span data-ttu-id="a85a0-244">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="a85a0-244">Response example</span></span>

<span data-ttu-id="a85a0-245">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="a85a0-245">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="a85a0-246">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a85a0-246">Related topics</span></span>

* [<span data-ttu-id="a85a0-247">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="a85a0-247">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="a85a0-248">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-248">Get Xbox Live analytics data</span></span>](get-xbox-live-analytics.md)
* [<span data-ttu-id="a85a0-249">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-249">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="a85a0-250">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-250">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="a85a0-251">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-251">Get Xbox Live game hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="a85a0-252">Abrufen von Xbox Live Multiplayerdaten</span><span class="sxs-lookup"><span data-stu-id="a85a0-252">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
