---
author: mcleanbyron
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Analysedaten abzurufen.
title: Abrufen von Xbox Live Analysedaten
ms.author: mcleans
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse
ms.localizationpriority: medium
ms.openlocfilehash: 82c24ee285070d733f3310b4ccec210adeafc27f
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817268"
---
# <a name="get-xbox-live-analytics-data"></a><span data-ttu-id="39171-104">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="39171-104">Get Xbox Live analytics data</span></span>

<span data-ttu-id="39171-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen der letzten 30Tage von allgemeinen Analysedaten für Kunden, die Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) spielen, einschließlich Gerätezubehörnutzung, Internetverbindungstyp, Gamerscore-Verteilung, Spielstatistiken und Freunde- und Follower-Daten.</span><span class="sxs-lookup"><span data-stu-id="39171-105">Use this method in the Microsoft Store analytics API to get the last 30 days of general analytics data for customers playing your [Xbox Live-enabled game](../xbox-live/index.md), including device accessory usage, internet connection type, gamerscore distribution, game statistics, and friends and followers data.</span></span> <span data-ttu-id="39171-106">Diese Informationen sind auch im [Xbox Analyse-Bericht](../publish/xbox-analytics-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="39171-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in the Windows Dev Center dashboard.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39171-107">Diese Methode unterstützt derzeit nur Xbox Live-fähige Spiele, die von [Microsoft Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht werden oder die mithilfe des [ID@Xbox Programms](../xbox-live/developer-program-overview.md#id) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="39171-107">This method currently only supports Xbox Live-enabled games that are published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) or that are submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="39171-108">Es gibt keine Daten für Spiele zurück, die mithilfe des [Xbox Live Creators-Programms](../xbox-live/developer-program-overview.md#xbox-live-creators-program) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="39171-108">It does not return data for games that were submitted via the [Xbox Live Creators Program](../xbox-live/developer-program-overview.md#xbox-live-creators-program).</span></span>

<span data-ttu-id="39171-109">Zusätzliche Analysedaten für Xbox Live-fähige Spiele sind über folgende Methoden verfügbar:</span><span class="sxs-lookup"><span data-stu-id="39171-109">Additional analytics data for Xbox Live-enabled games is available via the following methods:</span></span>
* [<span data-ttu-id="39171-110">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="39171-110">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="39171-111">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="39171-111">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="39171-112">Abrufen von Xbox Live Spielehub-Daten</span><span class="sxs-lookup"><span data-stu-id="39171-112">Get Xbox Live Game Hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="39171-113">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="39171-113">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="39171-114">Abrufen von Xbox Live Multiplayer-Daten</span><span class="sxs-lookup"><span data-stu-id="39171-114">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
* [<span data-ttu-id="39171-115">Abrufen von Xbox Live Daten zur gleichzeitigen Nutzung</span><span class="sxs-lookup"><span data-stu-id="39171-115">Get Xbox Live concurrent usage data</span></span>](get-xbox-live-concurrent-usage-data.md)

## <a name="prerequisites"></a><span data-ttu-id="39171-116">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="39171-116">Prerequisites</span></span>

<span data-ttu-id="39171-117">Um diese Methode zu verwenden, sind die folgenden Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="39171-117">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="39171-118">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="39171-118">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="39171-119">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="39171-119">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="39171-120">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="39171-120">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="39171-121">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="39171-121">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="39171-122">Anforderung</span><span class="sxs-lookup"><span data-stu-id="39171-122">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="39171-123">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="39171-123">Request syntax</span></span>

| <span data-ttu-id="39171-124">Methode</span><span class="sxs-lookup"><span data-stu-id="39171-124">Method</span></span> | <span data-ttu-id="39171-125">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="39171-125">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="39171-126">GET</span><span class="sxs-lookup"><span data-stu-id="39171-126">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="39171-127">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="39171-127">Request header</span></span>

| <span data-ttu-id="39171-128">Header</span><span class="sxs-lookup"><span data-stu-id="39171-128">Header</span></span>        | <span data-ttu-id="39171-129">Typ</span><span class="sxs-lookup"><span data-stu-id="39171-129">Type</span></span>   | <span data-ttu-id="39171-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39171-130">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="39171-131">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="39171-131">Authorization</span></span> | <span data-ttu-id="39171-132">String</span><span class="sxs-lookup"><span data-stu-id="39171-132">string</span></span> | <span data-ttu-id="39171-133">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="39171-133">Required.</span></span> <span data-ttu-id="39171-134">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="39171-134">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="39171-135">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="39171-135">Request parameters</span></span>

| <span data-ttu-id="39171-136">Parameter</span><span class="sxs-lookup"><span data-stu-id="39171-136">Parameter</span></span>        | <span data-ttu-id="39171-137">Typ</span><span class="sxs-lookup"><span data-stu-id="39171-137">Type</span></span>   |  <span data-ttu-id="39171-138">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39171-138">Description</span></span>      |  <span data-ttu-id="39171-139">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="39171-139">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="39171-140">applicationId</span><span class="sxs-lookup"><span data-stu-id="39171-140">applicationId</span></span> | <span data-ttu-id="39171-141">String</span><span class="sxs-lookup"><span data-stu-id="39171-141">string</span></span> | <span data-ttu-id="39171-142">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die allgemeinen Xbox Live Analysedaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="39171-142">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve general Xbox Live analytics data.</span></span>  |  <span data-ttu-id="39171-143">Ja</span><span class="sxs-lookup"><span data-stu-id="39171-143">Yes</span></span>  |
| <span data-ttu-id="39171-144">metricType</span><span class="sxs-lookup"><span data-stu-id="39171-144">metricType</span></span> | <span data-ttu-id="39171-145">String</span><span class="sxs-lookup"><span data-stu-id="39171-145">string</span></span> | <span data-ttu-id="39171-146">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="39171-146">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="39171-147">Geben Sie für diese Methode den Wert **productvalues** an.</span><span class="sxs-lookup"><span data-stu-id="39171-147">For this method, specify the value **productvalues**.</span></span>  |  <span data-ttu-id="39171-148">Ja</span><span class="sxs-lookup"><span data-stu-id="39171-148">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="39171-149">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="39171-149">Request example</span></span>

<span data-ttu-id="39171-150">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von allgemeinen Analysedaten für Kunden, die Ihr Xbox Live-fähiges Spiel spielen.</span><span class="sxs-lookup"><span data-stu-id="39171-150">The following example demonstrates a request for getting general analytics data for customers playing your Xbox Live-enabled game.</span></span> <span data-ttu-id="39171-151">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="39171-151">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=productvalues HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="39171-152">Antwort</span><span class="sxs-lookup"><span data-stu-id="39171-152">Response</span></span>

<span data-ttu-id="39171-153">Diese Methode gibt ein *Value*-Array zurück, das folgende Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="39171-153">This method returns a *Value* array that contains the following objects.</span></span>

| <span data-ttu-id="39171-154">Objekt</span><span class="sxs-lookup"><span data-stu-id="39171-154">Object</span></span>      | <span data-ttu-id="39171-155">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39171-155">Description</span></span>                  |
|-------------|---------------------------------------------------|
| <span data-ttu-id="39171-156">ProductData</span><span class="sxs-lookup"><span data-stu-id="39171-156">ProductData</span></span>   |   <span data-ttu-id="39171-157">Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage an Geräte- und Benutzeranalysedaten für Ihr Spiel enthalten.</span><span class="sxs-lookup"><span data-stu-id="39171-157">Contains one [DeviceProperties](#deviceproperties) object and one [UserProperties](#userproperties) object that contain the last 30 days of device and user analytics data for your game.</span></span>    |  
| <span data-ttu-id="39171-158">XboxwideData</span><span class="sxs-lookup"><span data-stu-id="39171-158">XboxwideData</span></span>   |  <span data-ttu-id="39171-159">Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage der durchschnittlichen Geräte- und Benutzeranalysedaten für alle Xbox Live Kunden in Prozentsätzen enthalten.</span><span class="sxs-lookup"><span data-stu-id="39171-159">Contains one [DeviceProperties](#deviceproperties) object and one [UserProperties](#userproperties) object that contain the last 30 days of average device and user analytics data for all Xbox Live customers, as percentages.</span></span> <span data-ttu-id="39171-160">Diese Daten werden zu Vergleichszwecken mit den Daten für Ihr Spiel beigefügt.</span><span class="sxs-lookup"><span data-stu-id="39171-160">This data is included for comparison purposes with the data for your game.</span></span>   |                                           


### <a name="deviceproperties"></a><span data-ttu-id="39171-161">DeviceProperties</span><span class="sxs-lookup"><span data-stu-id="39171-161">DeviceProperties</span></span>

<span data-ttu-id="39171-162">Diese Ressource enthält Gerätenutzungsdaten für Ihr Spiel oder durchschnittliche Gerätnutzungsdaten für alle Xbox Live-Kunden in den letzten 30Tagen.</span><span class="sxs-lookup"><span data-stu-id="39171-162">This resource contains device usage data for your game or average device usage data for all Xbox Live customers during the last 30 days.</span></span>

| <span data-ttu-id="39171-163">Wert</span><span class="sxs-lookup"><span data-stu-id="39171-163">Value</span></span>           | <span data-ttu-id="39171-164">Typ</span><span class="sxs-lookup"><span data-stu-id="39171-164">Type</span></span>    | <span data-ttu-id="39171-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39171-165">Description</span></span>        |
|-----------------|---------|------|
|  <span data-ttu-id="39171-166">applicationId</span><span class="sxs-lookup"><span data-stu-id="39171-166">applicationId</span></span>               |    <span data-ttu-id="39171-167">String</span><span class="sxs-lookup"><span data-stu-id="39171-167">string</span></span>     |  <span data-ttu-id="39171-168">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="39171-168">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved analytics data.</span></span>   |
|  <span data-ttu-id="39171-169">connectionTypeDistribution</span><span class="sxs-lookup"><span data-stu-id="39171-169">connectionTypeDistribution</span></span>               |    <span data-ttu-id="39171-170">Array</span><span class="sxs-lookup"><span data-stu-id="39171-170">array</span></span>     |   <span data-ttu-id="39171-171">Enthält Objekte, die angeben, wie viele Kunden eine verkabelte Internetverbindung im Vergleich zu einer Wireless-Internetverbindung mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-171">Contains objects that indicate how many customers use a wired internet connection versus a wireless internet connection on Xbox.</span></span> <span data-ttu-id="39171-172">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-172">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-173">**conType**: Gibt den Typ der Verbindung an.</span><span class="sxs-lookup"><span data-stu-id="39171-173">**conType**: Specifies the connection type.</span></span></li><li><span data-ttu-id="39171-174">**deviceCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl Ihrer Spiel-Kunden an, die den Verbindungstyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-174">**deviceCount**: In the **ProductData** object, this field specifies the number of your game's customers that use the connection type.</span></span> <span data-ttu-id="39171-175">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Verbindungstyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-175">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use the connection type.</span></span></li></ul>   |     
|  <span data-ttu-id="39171-176">deviceCount</span><span class="sxs-lookup"><span data-stu-id="39171-176">deviceCount</span></span>               |   <span data-ttu-id="39171-177">String</span><span class="sxs-lookup"><span data-stu-id="39171-177">string</span></span>      |  <span data-ttu-id="39171-178">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kundengeräte an, auf denen Ihr Spiel während der letzten 30Tage gespielt wurde.</span><span class="sxs-lookup"><span data-stu-id="39171-178">In the **ProductData** object, this field specifies the number of customer devices on which your game has been played during the last 30 days.</span></span> <span data-ttu-id="39171-179">Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="39171-179">In the **XboxwideData** object, this field is always 1, indicating a starting percentage of 100% for data for all Xbox Live customers.</span></span>   |     
|  <span data-ttu-id="39171-180">eliteControllerPresentDeviceCount</span><span class="sxs-lookup"><span data-stu-id="39171-180">eliteControllerPresentDeviceCount</span></span>               |   <span data-ttu-id="39171-181">String</span><span class="sxs-lookup"><span data-stu-id="39171-181">string</span></span>      |  <span data-ttu-id="39171-182">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die den Xbox Elite Wireless Controller verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-182">In the **ProductData** object, this field specifies the number of your game's customers that use the Xbox Elite Wireless Controller.</span></span> <span data-ttu-id="39171-183">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Xbox Elite Wireless Controller verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-183">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use the Xbox Elite Wireless Controller.</span></span>  |     
|  <span data-ttu-id="39171-184">externalDrivePresentDeviceCount</span><span class="sxs-lookup"><span data-stu-id="39171-184">externalDrivePresentDeviceCount</span></span>               |   <span data-ttu-id="39171-185">String</span><span class="sxs-lookup"><span data-stu-id="39171-185">string</span></span>      |  <span data-ttu-id="39171-186">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die ein externes Laufwerk mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-186">In the **ProductData** object, this field specifies the number of your game's customers that use an external hard drive on Xbox.</span></span> <span data-ttu-id="39171-187">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die ein externes Laufwerk mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="39171-187">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use an external hard drive on Xbox.</span></span>  |


### <a name="userproperties"></a><span data-ttu-id="39171-188">UserProperties</span><span class="sxs-lookup"><span data-stu-id="39171-188">UserProperties</span></span>

<span data-ttu-id="39171-189">Diese Ressource enthält Benutzerdaten für Ihr Spiel oder durchschnittliche Benutzerdaten für alle Xbox Live-Kunden in den letzten 30Tagen.</span><span class="sxs-lookup"><span data-stu-id="39171-189">This resource contains user data for your game or average user data for all Xbox Live customers during the last 30 days.</span></span>

| <span data-ttu-id="39171-190">Wert</span><span class="sxs-lookup"><span data-stu-id="39171-190">Value</span></span>           | <span data-ttu-id="39171-191">Typ</span><span class="sxs-lookup"><span data-stu-id="39171-191">Type</span></span>    | <span data-ttu-id="39171-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="39171-192">Description</span></span>        |
|-----------------|---------|------|
|  <span data-ttu-id="39171-193">applicationId</span><span class="sxs-lookup"><span data-stu-id="39171-193">applicationId</span></span>               |    <span data-ttu-id="39171-194">String</span><span class="sxs-lookup"><span data-stu-id="39171-194">string</span></span>     |   <span data-ttu-id="39171-195">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="39171-195">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved analytics data.</span></span>  |
|  <span data-ttu-id="39171-196">userCount</span><span class="sxs-lookup"><span data-stu-id="39171-196">userCount</span></span>               |    <span data-ttu-id="39171-197">String</span><span class="sxs-lookup"><span data-stu-id="39171-197">string</span></span>     |   <span data-ttu-id="39171-198">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden an, die Ihr Spiel während der letzten 30Tage gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="39171-198">In the **ProductData** object, this field specifies the number of customers that have played your game during the last 30 days.</span></span> <span data-ttu-id="39171-199">Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="39171-199">In the **XboxwideData** object, this field is always 1, indicating a starting percentage of 100% for data for all Xbox Live customers.</span></span>   |     
|  <span data-ttu-id="39171-200">dvrUsageCounts</span><span class="sxs-lookup"><span data-stu-id="39171-200">dvrUsageCounts</span></span>               |   <span data-ttu-id="39171-201">Array</span><span class="sxs-lookup"><span data-stu-id="39171-201">array</span></span>      |  <span data-ttu-id="39171-202">Enthält Objekte, die angeben, wie viele Kunden einen Spiele-DVR zum Aufzeichnen und Anzeigen des Spiels verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="39171-202">Contains objects that indicate how many customers have used game DVR to record and view gameplay.</span></span> <span data-ttu-id="39171-203">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-203">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-204">**dvrName**: Gibt das verwendete Spiele-DVR-Merkmal an.</span><span class="sxs-lookup"><span data-stu-id="39171-204">**dvrName**: Specifies the game DVR feature used.</span></span> <span data-ttu-id="39171-205">Mögliche Werte sind **gameClipUploads**, **gameClipViews**, **screenshotUploads** und **screenshotViews**.</span><span class="sxs-lookup"><span data-stu-id="39171-205">Possible values are **gameClipUploads**, **gameClipViews**, **screenshotUploads**, and **screenshotViews**.</span></span></li><li><span data-ttu-id="39171-206">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die das angegebene Spiele-DVR-Merkmal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="39171-206">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that used the specified game DVR feature.</span></span> <span data-ttu-id="39171-207">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die das angegebene Spiele-DVR-Merkmal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="39171-207">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that used the specified game DVR feature.</span></span></li></ul>   |     
|  <span data-ttu-id="39171-208">followerCountPercentiles</span><span class="sxs-lookup"><span data-stu-id="39171-208">followerCountPercentiles</span></span>               |   <span data-ttu-id="39171-209">Array</span><span class="sxs-lookup"><span data-stu-id="39171-209">array</span></span>      |  <span data-ttu-id="39171-210">Enthält Objekte, die Details über die Anzahl der Follower für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-210">Contains objects that provide details about the number of followers for customers.</span></span> <span data-ttu-id="39171-211">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-211">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-212">**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Follower-Daten als ein Mittelwert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="39171-212">**percentage**: Currently, this value is always 50, indicating that the follower data is provided as a median value.</span></span></li><li><span data-ttu-id="39171-213">**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für Ihre Spielkunden an.</span><span class="sxs-lookup"><span data-stu-id="39171-213">**value**: In the **ProductData** object, this field specifies the median number of followers for your game's customers.</span></span> <span data-ttu-id="39171-214">Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für alle Xbox Live-Kunden an.</span><span class="sxs-lookup"><span data-stu-id="39171-214">In the **XboxwideData** object, this field specifies the median number of followers for all Xbox Live customers.</span></span></li></ul>  |   
|  <span data-ttu-id="39171-215">friendCountPercentiles</span><span class="sxs-lookup"><span data-stu-id="39171-215">friendCountPercentiles</span></span>               |   <span data-ttu-id="39171-216">Array</span><span class="sxs-lookup"><span data-stu-id="39171-216">array</span></span>      |  <span data-ttu-id="39171-217">Enthält Objekte, die Details über die Anzahl der Freunde für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-217">Contains objects that provide details about the number of friends for customers.</span></span> <span data-ttu-id="39171-218">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-218">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-219">**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Freunde-Daten als ein Mittelwert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="39171-219">**percentage**: Currently, this value is always 50, indicating that the friends data is provided as a median value.</span></span></li><li><span data-ttu-id="39171-220">**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für Ihre Spielkunden an.</span><span class="sxs-lookup"><span data-stu-id="39171-220">**value**: In the **ProductData** object, this field specifies the median number of friends for your game's customers.</span></span> <span data-ttu-id="39171-221">Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für alle Xbox Live-Kunden an.</span><span class="sxs-lookup"><span data-stu-id="39171-221">In the **XboxwideData** object, this field specifies the median number of friends for all Xbox Live customers.</span></span></li></ul>  |     
|  <span data-ttu-id="39171-222">gamerScoreRangeDistribution</span><span class="sxs-lookup"><span data-stu-id="39171-222">gamerScoreRangeDistribution</span></span>               |   <span data-ttu-id="39171-223">Array</span><span class="sxs-lookup"><span data-stu-id="39171-223">array</span></span>      |  <span data-ttu-id="39171-224">Enthält Objekte, die Details über die Gamescore-Verteilung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-224">Contains objects that provide details about the gamerscore distribution for customers.</span></span> <span data-ttu-id="39171-225">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-225">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-226">**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="39171-226">**scoreRange**: The gamerscore range for which the following field provides usage data.</span></span> <span data-ttu-id="39171-227">Beispiel: **10K-25K**.</span><span class="sxs-lookup"><span data-stu-id="39171-227">For example, **10K-25K**.</span></span></li><li><span data-ttu-id="39171-228">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="39171-228">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have a  gamerscore in the specified range for all games they have played.</span></span> <span data-ttu-id="39171-229">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="39171-229">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have a gamerscore in the specified range for all games they have played.</span></span></li></ul>  |
|  <span data-ttu-id="39171-230">titleGamerScoreRangeDistribution</span><span class="sxs-lookup"><span data-stu-id="39171-230">titleGamerScoreRangeDistribution</span></span>               |   <span data-ttu-id="39171-231">Array</span><span class="sxs-lookup"><span data-stu-id="39171-231">array</span></span>      |  <span data-ttu-id="39171-232">Enthält Objekte, die Details über die Gamescore-Verteilung für Ihr Spiel bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-232">Contains objects that provide details about the gamerscore distribution for your game.</span></span> <span data-ttu-id="39171-233">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-233">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-234">**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="39171-234">**scoreRange**: The gamerscore range for which the following field provides usage data.</span></span> <span data-ttu-id="39171-235">Beispiel: **100-200**.</span><span class="sxs-lookup"><span data-stu-id="39171-235">For example, **100-200**.</span></span></li><li><span data-ttu-id="39171-236">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben.</span><span class="sxs-lookup"><span data-stu-id="39171-236">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have a  gamerscore in the specified range for your game.</span></span> <span data-ttu-id="39171-237">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben.</span><span class="sxs-lookup"><span data-stu-id="39171-237">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have a gamerscore in the specified range for your game.</span></span></li></ul>   |
|  <span data-ttu-id="39171-238">socialUsageCounts</span><span class="sxs-lookup"><span data-stu-id="39171-238">socialUsageCounts</span></span>               |   <span data-ttu-id="39171-239">Array</span><span class="sxs-lookup"><span data-stu-id="39171-239">array</span></span>      |  <span data-ttu-id="39171-240">Enthält Objekte, die Details über die gemeinschaftliche Nutzung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-240">Contains objects that provide details about the social usage for customers.</span></span> <span data-ttu-id="39171-241">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-241">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-242">**scName**: Der Typ der gemeinschaftlichen Verwendung.</span><span class="sxs-lookup"><span data-stu-id="39171-242">**scName**: The type of social usage.</span></span> <span data-ttu-id="39171-243">Beispielsweise **gameInvites** und **textMessages**.</span><span class="sxs-lookup"><span data-stu-id="39171-243">For example, **gameInvites** and **textMessages**.</span></span></li><li><span data-ttu-id="39171-244">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="39171-244">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have participated in the specified social usage type.</span></span> <span data-ttu-id="39171-245">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="39171-245">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have participated in the specified social usage type.</span></span></li></ul>   |
|  <span data-ttu-id="39171-246">streamingUsageCounts</span><span class="sxs-lookup"><span data-stu-id="39171-246">streamingUsageCounts</span></span>               |   <span data-ttu-id="39171-247">Array</span><span class="sxs-lookup"><span data-stu-id="39171-247">array</span></span>      |  <span data-ttu-id="39171-248">Enthält Objekte, die Details über die Streaming-Nutzung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="39171-248">Contains objects that provide details about the streaming usage for customers.</span></span> <span data-ttu-id="39171-249">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="39171-249">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="39171-250">**stName**: Der Typ der Streaming-Plattform.</span><span class="sxs-lookup"><span data-stu-id="39171-250">**stName**: The type of streaming platform.</span></span> <span data-ttu-id="39171-251">Beispielsweise **youtubeUsage**, **twitchUsage** und **mixerUsage**.</span><span class="sxs-lookup"><span data-stu-id="39171-251">For example, **youtubeUsage**, **twitchUsage**, and **mixerUsage**.</span></span></li><li><span data-ttu-id="39171-252">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die die angegebene Streaming-Plattform verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="39171-252">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have used the specified streaming platform.</span></span> <span data-ttu-id="39171-253">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die die angegebene Streaming-Plattform verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="39171-253">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have used the specified streaming platform.</span></span></li></ul>  |


### <a name="response-example"></a><span data-ttu-id="39171-254">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="39171-254">Response example</span></span>

<span data-ttu-id="39171-255">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="39171-255">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "ProductData": {
        "DeviceProperties": [
          {
            "applicationId": "9NBLGGGZ5QDR",
            "connectionTypeDistribution": [
              {
                "conType": "WIRED",
                "deviceCount": "43806"
              },
              {
                "conType": "WIRELESS",
                "deviceCount": "104035"
              }
            ],
            "deviceCount": "148063",
            "eliteControllerPresentDeviceCount": "10615",
            "externalDrivePresentDeviceCount": "46388"
          }
        ],
        "UserProperties": [
          {
            "applicationId": "9NBLGGGZ5QDR",
            "userCount": "142345",
            "dvrUsageCounts": [
              {
                "dvrName": "gameClipUploads",
                "userCount": "31264"
              },
              {
                "dvrName": "gameClipViews",
                "userCount": "52236"
              },
              {
                "dvrName": "screenshotUploads",
                "userCount": "27051"
              },
              {
                "dvrName": "screenshotViews",
                "userCount": "45640"
              }
            ],
            "followerCountPercentiles": [
              {
                "percentage": "50",
                "value": "11"
              }
            ],
            "friendCountPercentiles": [
              {
                "percentage": "50",
                "value": "11"
              }
            ],
            "gamerScoreRangeDistribution": [
              {
                "scoreRange": "10K-25K",
                "userCount": "30015"
              },
              {
                "scoreRange": "25K-50K",
                "userCount": "20495"
              },
              {
                "scoreRange": "3K-10K",
                "userCount": "32438"
              },
              {
                "scoreRange": "50K-100K",
                "userCount": "10608"
              },
              {
                "scoreRange": "<3K",
                "userCount": "45726"
              },
              {
                "scoreRange": ">100K",
                "userCount": "3063"
              }
            ],
            "titleGamerScoreRangeDistribution": [
              {
                "scoreRange": "400-600",
                "userCount": "133875"
              },
              {
                "scoreRange": "800-1000",
                "userCount": "45960"
              },
              {
                "scoreRange": "<100",
                "userCount": "269137"
              },
              {
                "scoreRange": "≥1K",
                "userCount": "11634"
              },
              {
                "scoreRange": "100-200",
                "userCount": "334471"
              },
              {
                "scoreRange": "600-800",
                "userCount": "123044"
              },
              {
                "scoreRange": "200-400",
                "userCount": "396725"
              }
            ],
            "socialUsageCounts": [
              {
                "scName": "gameInvites",
                "userCount": "82390"
              },
              {
                "scName": "textMessages",
                "userCount": "91880"
              },
              {
                "scName": "partySessionCount",
                "userCount": "68129"
              }
            ],
            "streamingUsageCounts": [
              {
                "stName": "youtubeUsage",
                "userCount": "74092"
              },
              {
                "stName": "twitchUsage",
                "userCount": "13401"
              }
              {
                "stName": "mixerUsage",
                "userCount": "22907"
              }
            ]
          }
        ]
      },
      "XboxwideData": {
        "DeviceProperties": [
          {
            "applicationId": "XBOXWIDE",
            "connectionTypeDistribution": [
              {
                "conType": "WIRED",
                "deviceCount": "0.213677732584786"
              },
              {
                "conType": "WIRELESS",
                "deviceCount": "0.786322267415214"
              }
            ],
            "deviceCount": "1",
            "eliteControllerPresentDeviceCount": "0.0476609278128012",
            "externalDrivePresentDeviceCount": "0.173747147416134"
          }
        ],
        "UserProperties": [
          {
            "applicationId": "XBOXWIDE",
            "userCount": "1",
            "dvrUsageCounts": [
              {
                "dvrName": "gameClipUploads",
                "userCount": "0.173210623993245"
              },
              {
                "dvrName": "gameClipViews",
                "userCount": "0.202104713778096"
              },
              {
                "dvrName": "screenshotUploads",
                "userCount": "0.136682414274251"
              },
              {
                "dvrName": "screenshotViews",
                "userCount": "0.158057895120314"
              }
            ],
            "followerCountPercentiles": [
              {
                "percentage": "50",
                "value": "5"
              }
            ],
            "friendCountPercentiles": [
              {
                "percentage": "50",
                "value": "5"
              }
            ],
            "gamerScoreRangeDistribution": [
              {
                "scoreRange": "10K-25K",
                "userCount": "0.134709282586519"
              },
              {
                "scoreRange": "25K-50K",
                "userCount": "0.0549468789343825"
              },
              {
                "scoreRange": "50K-100K",
                "userCount": "0.017301313342277"
              },
              {
                "scoreRange": "3K-10K",
                "userCount": "0.216512780268453"
              },
              {
                "scoreRange": "<3K",
                "userCount": "0.573515440094644"
              },
              {
                "scoreRange": ">100K",
                "userCount": "0.00301430477372488"
              }
            ],
            "titleGamerScoreRangeDistribution": [
              {
                "scoreRange": "100-200",
                "userCount": "0.178055695637076"
              },
              {
                "scoreRange": "200-400",
                "userCount": "0.173283639825241"
              },
              {
                "scoreRange": "400-600",
                "userCount": "0.0986865193958259"
              },
              {
                "scoreRange": "600-800",
                "userCount": "0.0506375775462092"
              },
              {
                "scoreRange": "800-1000",
                "userCount": "0.0232398822856435"
              },
              {
                "scoreRange": "<100",
                "userCount": "0.456443551582991"
              },
              {
                "scoreRange": "≥1K",
                "userCount": "0.0196531337270126"
              }
            ],
            "socialUsageCounts": [
              {
                "scName": "gameInvites",
                "userCount": "0.460375855738335"
              },
              {
                "scName": "textMessages",
                "userCount": "0.429256324070832"
              },
              {
                "scName": "partySessionCount",
                "userCount": "0.378446577751268"
              },
              {
                "scName": "gamehubViews",
                "userCount": "0.000197115778147329"
              }
            ],
            "streamingUsageCounts": [
              {
                "stName": "youtubeUsage",
                "userCount": "0.330320919178683"
              },
              {
                "stName": "twitchUsage",
                "userCount": "0.040666241835399"
              }
              {
                "stName": "mixerUsage",
                "userCount": "0.140193816053558"
              }
            ]
          }
        ]
      }
    }
  ],
  "@nextLink": null,
  "TotalCount": 4
}
```

## <a name="related-topics"></a><span data-ttu-id="39171-256">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="39171-256">Related topics</span></span>

* [<span data-ttu-id="39171-257">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="39171-257">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="39171-258">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="39171-258">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="39171-259">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="39171-259">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="39171-260">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="39171-260">Get Xbox Live game hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="39171-261">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="39171-261">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="39171-262">Abrufen von Xbox Live Multiplayer-Daten</span><span class="sxs-lookup"><span data-stu-id="39171-262">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
* [<span data-ttu-id="39171-263">Abrufen von Xbox Live gleichzeitigen Nutzungsdaten</span><span class="sxs-lookup"><span data-stu-id="39171-263">Get Xbox Live concurrent usage data</span></span>](get-xbox-live-concurrent-usage-data.md)
