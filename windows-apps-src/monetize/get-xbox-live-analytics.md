---
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um Xbox Live Analysedaten abzurufen.
title: Abrufen von Xbox Live Analysedaten
ms.date: 06/04/2018
ms.topic: article
keywords: Windows10, Uwp, Store-Diensten, Microsoft Store-Analyse-API, Xbox Live Analyse
ms.localizationpriority: medium
ms.openlocfilehash: 74c898630641e8b0d53a181d1874c6df62baaa78
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8210081"
---
# <a name="get-xbox-live-analytics-data"></a><span data-ttu-id="94b8c-104">Abrufen von Xbox Live Analysedaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-104">Get Xbox Live analytics data</span></span>

<span data-ttu-id="94b8c-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API zum Abrufen der letzten 30Tage von allgemeinen Analysedaten für Kunden, die Ihr [Xbox Live-fähiges Spiel](../xbox-live/index.md) spielen, einschließlich Gerätezubehörnutzung, Internetverbindungstyp, Gamerscore-Verteilung, Spielstatistiken und Freunde- und Follower-Daten.</span><span class="sxs-lookup"><span data-stu-id="94b8c-105">Use this method in the Microsoft Store analytics API to get the last 30 days of general analytics data for customers playing your [Xbox Live-enabled game](../xbox-live/index.md), including device accessory usage, internet connection type, gamerscore distribution, game statistics, and friends and followers data.</span></span> <span data-ttu-id="94b8c-106">Diese Informationen sind auch in der [Xbox Analysebericht](../publish/xbox-analytics-report.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="94b8c-106">This information is also available in the [Xbox analytics report](../publish/xbox-analytics-report.md) in Partner Center.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94b8c-107">Diese Methode unterstützt nur Spiele für Xbox oder Spiele, die Xbox Live-Dienste verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-107">This method only supports games for Xbox or games that use Xbox Live services.</span></span> <span data-ttu-id="94b8c-108">Diese Spiele müssen den [Konzeptgenehmigungsprozess](../gaming/concept-approval.md) durchlaufen, der Spiele umfasst, die von [Microsoft-Partnern](../xbox-live/developer-program-overview.md#microsoft-partners) veröffentlicht wurden, sowie Spiele, die über das [ID@Xbox-Programm](../xbox-live/developer-program-overview.md#id) übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-108">These games must go through the [concept approval process](../gaming/concept-approval.md), which includes games published by [Microsoft partners](../xbox-live/developer-program-overview.md#microsoft-partners) and games submitted via the [ID@Xbox program](../xbox-live/developer-program-overview.md#id).</span></span> <span data-ttu-id="94b8c-109">Diese Methode unterstützt derzeit keine Spiele, die über das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) eingereicht wurden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-109">This method does not currently support games published via the [Xbox Live Creators Program](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md).</span></span>

<span data-ttu-id="94b8c-110">Zusätzliche Analysedaten für Xbox Live-fähige Spiele sind über folgende Methoden verfügbar:</span><span class="sxs-lookup"><span data-stu-id="94b8c-110">Additional analytics data for Xbox Live-enabled games is available via the following methods:</span></span>
* [<span data-ttu-id="94b8c-111">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-111">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="94b8c-112">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-112">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="94b8c-113">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-113">Get Xbox Live Game Hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="94b8c-114">Abrufen von Xbox Live-Clubdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-114">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="94b8c-115">Abrufen von Xbox Live Multiplayer-Daten</span><span class="sxs-lookup"><span data-stu-id="94b8c-115">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
* [<span data-ttu-id="94b8c-116">Abrufen von Xbox Live Daten zur gleichzeitigen Nutzung</span><span class="sxs-lookup"><span data-stu-id="94b8c-116">Get Xbox Live concurrent usage data</span></span>](get-xbox-live-concurrent-usage-data.md)

## <a name="prerequisites"></a><span data-ttu-id="94b8c-117">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="94b8c-117">Prerequisites</span></span>

<span data-ttu-id="94b8c-118">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="94b8c-118">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="94b8c-119">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="94b8c-119">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="94b8c-120">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="94b8c-120">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="94b8c-121">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="94b8c-121">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="94b8c-122">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-122">After the token expires, you can obtain a new one.</span></span>

## <a name="request"></a><span data-ttu-id="94b8c-123">Anforderung</span><span class="sxs-lookup"><span data-stu-id="94b8c-123">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="94b8c-124">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="94b8c-124">Request syntax</span></span>

| <span data-ttu-id="94b8c-125">Methode</span><span class="sxs-lookup"><span data-stu-id="94b8c-125">Method</span></span> | <span data-ttu-id="94b8c-126">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="94b8c-126">Request URI</span></span>       |
|--------|----------------------|
| <span data-ttu-id="94b8c-127">GET</span><span class="sxs-lookup"><span data-stu-id="94b8c-127">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics``` |


### <a name="request-header"></a><span data-ttu-id="94b8c-128">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="94b8c-128">Request header</span></span>

| <span data-ttu-id="94b8c-129">Header</span><span class="sxs-lookup"><span data-stu-id="94b8c-129">Header</span></span>        | <span data-ttu-id="94b8c-130">Typ</span><span class="sxs-lookup"><span data-stu-id="94b8c-130">Type</span></span>   | <span data-ttu-id="94b8c-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94b8c-131">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="94b8c-132">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="94b8c-132">Authorization</span></span> | <span data-ttu-id="94b8c-133">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-133">string</span></span> | <span data-ttu-id="94b8c-134">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="94b8c-134">Required.</span></span> <span data-ttu-id="94b8c-135">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="94b8c-135">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="94b8c-136">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="94b8c-136">Request parameters</span></span>

| <span data-ttu-id="94b8c-137">Parameter</span><span class="sxs-lookup"><span data-stu-id="94b8c-137">Parameter</span></span>        | <span data-ttu-id="94b8c-138">Typ</span><span class="sxs-lookup"><span data-stu-id="94b8c-138">Type</span></span>   |  <span data-ttu-id="94b8c-139">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94b8c-139">Description</span></span>      |  <span data-ttu-id="94b8c-140">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="94b8c-140">Required</span></span>  
|---------------|--------|---------------|------|
| <span data-ttu-id="94b8c-141">applicationId</span><span class="sxs-lookup"><span data-stu-id="94b8c-141">applicationId</span></span> | <span data-ttu-id="94b8c-142">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-142">string</span></span> | <span data-ttu-id="94b8c-143">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie die allgemeinen Xbox Live Analysedaten abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="94b8c-143">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you want to retrieve general Xbox Live analytics data.</span></span>  |  <span data-ttu-id="94b8c-144">Ja</span><span class="sxs-lookup"><span data-stu-id="94b8c-144">Yes</span></span>  |
| <span data-ttu-id="94b8c-145">metricType</span><span class="sxs-lookup"><span data-stu-id="94b8c-145">metricType</span></span> | <span data-ttu-id="94b8c-146">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-146">string</span></span> | <span data-ttu-id="94b8c-147">Eine Zeichenfolge, die den Typ der abzurufenden Xbox Live Analysedaten angibt.</span><span class="sxs-lookup"><span data-stu-id="94b8c-147">A string that specifies the type of Xbox Live analytics data to retrieve.</span></span> <span data-ttu-id="94b8c-148">Geben Sie für diese Methode den Wert **productvalues** an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-148">For this method, specify the value **productvalues**.</span></span>  |  <span data-ttu-id="94b8c-149">Ja</span><span class="sxs-lookup"><span data-stu-id="94b8c-149">Yes</span></span>  |


### <a name="request-example"></a><span data-ttu-id="94b8c-150">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="94b8c-150">Request example</span></span>

<span data-ttu-id="94b8c-151">Das folgende Beispiel zeigt eine Anforderung zum Abrufen von allgemeinen Analysedaten für Kunden, die Ihr Xbox Live-fähiges Spiel spielen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-151">The following example demonstrates a request for getting general analytics data for customers playing your Xbox Live-enabled game.</span></span> <span data-ttu-id="94b8c-152">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="94b8c-152">Replace the *applicationId* value with the Store ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/gameanalytics?applicationId=9NBLGGGZ5QDR&metrictype=productvalues HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="94b8c-153">Antwort</span><span class="sxs-lookup"><span data-stu-id="94b8c-153">Response</span></span>

<span data-ttu-id="94b8c-154">Diese Methode gibt ein *Value*-Array zurück, das folgende Objekte enthält.</span><span class="sxs-lookup"><span data-stu-id="94b8c-154">This method returns a *Value* array that contains the following objects.</span></span>

| <span data-ttu-id="94b8c-155">Objekt</span><span class="sxs-lookup"><span data-stu-id="94b8c-155">Object</span></span>      | <span data-ttu-id="94b8c-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94b8c-156">Description</span></span>                  |
|-------------|---------------------------------------------------|
| <span data-ttu-id="94b8c-157">ProductData</span><span class="sxs-lookup"><span data-stu-id="94b8c-157">ProductData</span></span>   |   <span data-ttu-id="94b8c-158">Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage an Geräte- und Benutzeranalysedaten für Ihr Spiel enthalten.</span><span class="sxs-lookup"><span data-stu-id="94b8c-158">Contains one [DeviceProperties](#deviceproperties) object and one [UserProperties](#userproperties) object that contain the last 30 days of device and user analytics data for your game.</span></span>    |  
| <span data-ttu-id="94b8c-159">XboxwideData</span><span class="sxs-lookup"><span data-stu-id="94b8c-159">XboxwideData</span></span>   |  <span data-ttu-id="94b8c-160">Enthält ein [DeviceProperties](#deviceproperties)-Objekt und ein [UserProperties](#userproperties)-Objekt, die die letzten 30Tage der durchschnittlichen Geräte- und Benutzeranalysedaten für alle Xbox Live Kunden in Prozentsätzen enthalten.</span><span class="sxs-lookup"><span data-stu-id="94b8c-160">Contains one [DeviceProperties](#deviceproperties) object and one [UserProperties](#userproperties) object that contain the last 30 days of average device and user analytics data for all Xbox Live customers, as percentages.</span></span> <span data-ttu-id="94b8c-161">Diese Daten werden zu Vergleichszwecken mit den Daten für Ihr Spiel beigefügt.</span><span class="sxs-lookup"><span data-stu-id="94b8c-161">This data is included for comparison purposes with the data for your game.</span></span>   |                                           


### <a name="deviceproperties"></a><span data-ttu-id="94b8c-162">DeviceProperties</span><span class="sxs-lookup"><span data-stu-id="94b8c-162">DeviceProperties</span></span>

<span data-ttu-id="94b8c-163">Diese Ressource enthält Gerätenutzungsdaten für Ihr Spiel oder durchschnittliche Gerätnutzungsdaten für alle Xbox Live-Kunden in den letzten 30Tagen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-163">This resource contains device usage data for your game or average device usage data for all Xbox Live customers during the last 30 days.</span></span>

| <span data-ttu-id="94b8c-164">Wert</span><span class="sxs-lookup"><span data-stu-id="94b8c-164">Value</span></span>           | <span data-ttu-id="94b8c-165">Typ</span><span class="sxs-lookup"><span data-stu-id="94b8c-165">Type</span></span>    | <span data-ttu-id="94b8c-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94b8c-166">Description</span></span>        |
|-----------------|---------|------|
|  <span data-ttu-id="94b8c-167">applicationId</span><span class="sxs-lookup"><span data-stu-id="94b8c-167">applicationId</span></span>               |    <span data-ttu-id="94b8c-168">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-168">string</span></span>     |  <span data-ttu-id="94b8c-169">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-169">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved analytics data.</span></span>   |
|  <span data-ttu-id="94b8c-170">connectionTypeDistribution</span><span class="sxs-lookup"><span data-stu-id="94b8c-170">connectionTypeDistribution</span></span>               |    <span data-ttu-id="94b8c-171">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-171">array</span></span>     |   <span data-ttu-id="94b8c-172">Enthält Objekte, die angeben, wie viele Kunden eine verkabelte Internetverbindung im Vergleich zu einer Wireless-Internetverbindung mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-172">Contains objects that indicate how many customers use a wired internet connection versus a wireless internet connection on Xbox.</span></span> <span data-ttu-id="94b8c-173">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-173">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-174">**conType**: Gibt den Typ der Verbindung an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-174">**conType**: Specifies the connection type.</span></span></li><li><span data-ttu-id="94b8c-175">**deviceCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl Ihrer Spiel-Kunden an, die den Verbindungstyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-175">**deviceCount**: In the **ProductData** object, this field specifies the number of your game's customers that use the connection type.</span></span> <span data-ttu-id="94b8c-176">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Verbindungstyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-176">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use the connection type.</span></span></li></ul>   |     
|  <span data-ttu-id="94b8c-177">deviceCount</span><span class="sxs-lookup"><span data-stu-id="94b8c-177">deviceCount</span></span>               |   <span data-ttu-id="94b8c-178">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-178">string</span></span>      |  <span data-ttu-id="94b8c-179">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kundengeräte an, auf denen Ihr Spiel während der letzten 30Tage gespielt wurde.</span><span class="sxs-lookup"><span data-stu-id="94b8c-179">In the **ProductData** object, this field specifies the number of customer devices on which your game has been played during the last 30 days.</span></span> <span data-ttu-id="94b8c-180">Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="94b8c-180">In the **XboxwideData** object, this field is always 1, indicating a starting percentage of 100% for data for all Xbox Live customers.</span></span>   |     
|  <span data-ttu-id="94b8c-181">eliteControllerPresentDeviceCount</span><span class="sxs-lookup"><span data-stu-id="94b8c-181">eliteControllerPresentDeviceCount</span></span>               |   <span data-ttu-id="94b8c-182">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-182">string</span></span>      |  <span data-ttu-id="94b8c-183">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die den Xbox Elite Wireless Controller verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-183">In the **ProductData** object, this field specifies the number of your game's customers that use the Xbox Elite Wireless Controller.</span></span> <span data-ttu-id="94b8c-184">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die den Xbox Elite Wireless Controller verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-184">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use the Xbox Elite Wireless Controller.</span></span>  |     
|  <span data-ttu-id="94b8c-185">externalDrivePresentDeviceCount</span><span class="sxs-lookup"><span data-stu-id="94b8c-185">externalDrivePresentDeviceCount</span></span>               |   <span data-ttu-id="94b8c-186">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-186">string</span></span>      |  <span data-ttu-id="94b8c-187">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die ein externes Laufwerk mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-187">In the **ProductData** object, this field specifies the number of your game's customers that use an external hard drive on Xbox.</span></span> <span data-ttu-id="94b8c-188">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die ein externes Laufwerk mit Xbox verwenden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-188">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that use an external hard drive on Xbox.</span></span>  |


### <a name="userproperties"></a><span data-ttu-id="94b8c-189">UserProperties</span><span class="sxs-lookup"><span data-stu-id="94b8c-189">UserProperties</span></span>

<span data-ttu-id="94b8c-190">Diese Ressource enthält Benutzerdaten für Ihr Spiel oder durchschnittliche Benutzerdaten für alle Xbox Live-Kunden in den letzten 30Tagen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-190">This resource contains user data for your game or average user data for all Xbox Live customers during the last 30 days.</span></span>

| <span data-ttu-id="94b8c-191">Wert</span><span class="sxs-lookup"><span data-stu-id="94b8c-191">Value</span></span>           | <span data-ttu-id="94b8c-192">Typ</span><span class="sxs-lookup"><span data-stu-id="94b8c-192">Type</span></span>    | <span data-ttu-id="94b8c-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="94b8c-193">Description</span></span>        |
|-----------------|---------|------|
|  <span data-ttu-id="94b8c-194">applicationId</span><span class="sxs-lookup"><span data-stu-id="94b8c-194">applicationId</span></span>               |    <span data-ttu-id="94b8c-195">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-195">string</span></span>     |   <span data-ttu-id="94b8c-196">Die [Store-ID](in-app-purchases-and-trials.md#store-ids) des Spiels, für das Sie Analysedaten abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-196">The [Store ID](in-app-purchases-and-trials.md#store-ids) of the game for which you retrieved analytics data.</span></span>  |
|  <span data-ttu-id="94b8c-197">userCount</span><span class="sxs-lookup"><span data-stu-id="94b8c-197">userCount</span></span>               |    <span data-ttu-id="94b8c-198">String</span><span class="sxs-lookup"><span data-stu-id="94b8c-198">string</span></span>     |   <span data-ttu-id="94b8c-199">Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden an, die Ihr Spiel während der letzten 30Tage gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-199">In the **ProductData** object, this field specifies the number of customers that have played your game during the last 30 days.</span></span> <span data-ttu-id="94b8c-200">Im **XboxwideData**-Objekt ist dieses Feld immer 1, womit ein Ausgangsprozentsatz von 100% für Daten für alle Xbox Live-Kunden angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="94b8c-200">In the **XboxwideData** object, this field is always 1, indicating a starting percentage of 100% for data for all Xbox Live customers.</span></span>   |     
|  <span data-ttu-id="94b8c-201">dvrUsageCounts</span><span class="sxs-lookup"><span data-stu-id="94b8c-201">dvrUsageCounts</span></span>               |   <span data-ttu-id="94b8c-202">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-202">array</span></span>      |  <span data-ttu-id="94b8c-203">Enthält Objekte, die angeben, wie viele Kunden einen Spiele-DVR zum Aufzeichnen und Anzeigen des Spiels verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-203">Contains objects that indicate how many customers have used game DVR to record and view gameplay.</span></span> <span data-ttu-id="94b8c-204">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-204">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-205">**dvrName**: Gibt das verwendete Spiele-DVR-Merkmal an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-205">**dvrName**: Specifies the game DVR feature used.</span></span> <span data-ttu-id="94b8c-206">Mögliche Werte sind **gameClipUploads**, **gameClipViews**, **screenshotUploads** und **screenshotViews**.</span><span class="sxs-lookup"><span data-stu-id="94b8c-206">Possible values are **gameClipUploads**, **gameClipViews**, **screenshotUploads**, and **screenshotViews**.</span></span></li><li><span data-ttu-id="94b8c-207">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die das angegebene Spiele-DVR-Merkmal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-207">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that used the specified game DVR feature.</span></span> <span data-ttu-id="94b8c-208">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die das angegebene Spiele-DVR-Merkmal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-208">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that used the specified game DVR feature.</span></span></li></ul>   |     
|  <span data-ttu-id="94b8c-209">followerCountPercentiles</span><span class="sxs-lookup"><span data-stu-id="94b8c-209">followerCountPercentiles</span></span>               |   <span data-ttu-id="94b8c-210">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-210">array</span></span>      |  <span data-ttu-id="94b8c-211">Enthält Objekte, die Details über die Anzahl der Follower für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-211">Contains objects that provide details about the number of followers for customers.</span></span> <span data-ttu-id="94b8c-212">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-212">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-213">**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Follower-Daten als ein Mittelwert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-213">**percentage**: Currently, this value is always 50, indicating that the follower data is provided as a median value.</span></span></li><li><span data-ttu-id="94b8c-214">**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für Ihre Spielkunden an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-214">**value**: In the **ProductData** object, this field specifies the median number of followers for your game's customers.</span></span> <span data-ttu-id="94b8c-215">Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Follower für alle Xbox Live-Kunden an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-215">In the **XboxwideData** object, this field specifies the median number of followers for all Xbox Live customers.</span></span></li></ul>  |   
|  <span data-ttu-id="94b8c-216">friendCountPercentiles</span><span class="sxs-lookup"><span data-stu-id="94b8c-216">friendCountPercentiles</span></span>               |   <span data-ttu-id="94b8c-217">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-217">array</span></span>      |  <span data-ttu-id="94b8c-218">Enthält Objekte, die Details über die Anzahl der Freunde für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-218">Contains objects that provide details about the number of friends for customers.</span></span> <span data-ttu-id="94b8c-219">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-219">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-220">**percentage**: Dieser Wert ist derzeit immer 50, womit angezeigt wird, dass die Freunde-Daten als ein Mittelwert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="94b8c-220">**percentage**: Currently, this value is always 50, indicating that the friends data is provided as a median value.</span></span></li><li><span data-ttu-id="94b8c-221">**value**: Im **ProductData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für Ihre Spielkunden an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-221">**value**: In the **ProductData** object, this field specifies the median number of friends for your game's customers.</span></span> <span data-ttu-id="94b8c-222">Im **XboxwideData**-Objekt gibt dieses Feld die mittlere Anzahl von Freunden für alle Xbox Live-Kunden an.</span><span class="sxs-lookup"><span data-stu-id="94b8c-222">In the **XboxwideData** object, this field specifies the median number of friends for all Xbox Live customers.</span></span></li></ul>  |     
|  <span data-ttu-id="94b8c-223">gamerScoreRangeDistribution</span><span class="sxs-lookup"><span data-stu-id="94b8c-223">gamerScoreRangeDistribution</span></span>               |   <span data-ttu-id="94b8c-224">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-224">array</span></span>      |  <span data-ttu-id="94b8c-225">Enthält Objekte, die Details über die Gamescore-Verteilung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-225">Contains objects that provide details about the gamerscore distribution for customers.</span></span> <span data-ttu-id="94b8c-226">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-226">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-227">**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="94b8c-227">**scoreRange**: The gamerscore range for which the following field provides usage data.</span></span> <span data-ttu-id="94b8c-228">Beispiel: **10K-25K**.</span><span class="sxs-lookup"><span data-stu-id="94b8c-228">For example, **10K-25K**.</span></span></li><li><span data-ttu-id="94b8c-229">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-229">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have a  gamerscore in the specified range for all games they have played.</span></span> <span data-ttu-id="94b8c-230">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für alle Spiele haben, die sie gespielt haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-230">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have a gamerscore in the specified range for all games they have played.</span></span></li></ul>  |
|  <span data-ttu-id="94b8c-231">titleGamerScoreRangeDistribution</span><span class="sxs-lookup"><span data-stu-id="94b8c-231">titleGamerScoreRangeDistribution</span></span>               |   <span data-ttu-id="94b8c-232">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-232">array</span></span>      |  <span data-ttu-id="94b8c-233">Enthält Objekte, die Details über die Gamescore-Verteilung für Ihr Spiel bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-233">Contains objects that provide details about the gamerscore distribution for your game.</span></span> <span data-ttu-id="94b8c-234">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-234">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-235">**scoreRange**: Der Gamerscore-Bereich für den das folgende Feld Nutzungsdaten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="94b8c-235">**scoreRange**: The gamerscore range for which the following field provides usage data.</span></span> <span data-ttu-id="94b8c-236">Beispiel: **100-200**.</span><span class="sxs-lookup"><span data-stu-id="94b8c-236">For example, **100-200**.</span></span></li><li><span data-ttu-id="94b8c-237">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-237">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have a  gamerscore in the specified range for your game.</span></span> <span data-ttu-id="94b8c-238">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die einen Gamerscore im angegebenen Bereich für Ihr Spiel haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-238">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have a gamerscore in the specified range for your game.</span></span></li></ul>   |
|  <span data-ttu-id="94b8c-239">socialUsageCounts</span><span class="sxs-lookup"><span data-stu-id="94b8c-239">socialUsageCounts</span></span>               |   <span data-ttu-id="94b8c-240">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-240">array</span></span>      |  <span data-ttu-id="94b8c-241">Enthält Objekte, die Details über die gemeinschaftliche Nutzung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-241">Contains objects that provide details about the social usage for customers.</span></span> <span data-ttu-id="94b8c-242">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-242">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-243">**scName**: Der Typ der gemeinschaftlichen Verwendung.</span><span class="sxs-lookup"><span data-stu-id="94b8c-243">**scName**: The type of social usage.</span></span> <span data-ttu-id="94b8c-244">Beispielsweise **gameInvites** und **textMessages**.</span><span class="sxs-lookup"><span data-stu-id="94b8c-244">For example, **gameInvites** and **textMessages**.</span></span></li><li><span data-ttu-id="94b8c-245">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-245">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have participated in the specified social usage type.</span></span> <span data-ttu-id="94b8c-246">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz alle Xbox Live-Kunden an, die am angegebenen gemeinschaftlichen Nutzungstyp teilgenommen haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-246">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have participated in the specified social usage type.</span></span></li></ul>   |
|  <span data-ttu-id="94b8c-247">streamingUsageCounts</span><span class="sxs-lookup"><span data-stu-id="94b8c-247">streamingUsageCounts</span></span>               |   <span data-ttu-id="94b8c-248">Array</span><span class="sxs-lookup"><span data-stu-id="94b8c-248">array</span></span>      |  <span data-ttu-id="94b8c-249">Enthält Objekte, die Details über die Streaming-Nutzung für Kunden bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94b8c-249">Contains objects that provide details about the streaming usage for customers.</span></span> <span data-ttu-id="94b8c-250">Jedes Objekt hat zwei Zeichenkettenfelder:</span><span class="sxs-lookup"><span data-stu-id="94b8c-250">Each object has two string fields:</span></span> <ul><li><span data-ttu-id="94b8c-251">**stName**: Der Typ der Streaming-Plattform.</span><span class="sxs-lookup"><span data-stu-id="94b8c-251">**stName**: The type of streaming platform.</span></span> <span data-ttu-id="94b8c-252">Beispielsweise **youtubeUsage**, **twitchUsage** und **mixerUsage**.</span><span class="sxs-lookup"><span data-stu-id="94b8c-252">For example, **youtubeUsage**, **twitchUsage**, and **mixerUsage**.</span></span></li><li><span data-ttu-id="94b8c-253">**userCount**: Im **ProductData**-Objekt gibt dieses Feld die Anzahl der Kunden Ihres Spiels an, die die angegebene Streaming-Plattform verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-253">**userCount**: In the **ProductData** object, this field specifies the number of your game's customers that have used the specified streaming platform.</span></span> <span data-ttu-id="94b8c-254">Im **XboxwideData**-Objekt gibt dieses Feld den Prozentsatz aller Xbox Live-Kunden an, die die angegebene Streaming-Plattform verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="94b8c-254">In the **XboxwideData** object, this field specifies the percentage of all Xbox Live customers that have used the specified streaming platform.</span></span></li></ul>  |


### <a name="response-example"></a><span data-ttu-id="94b8c-255">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="94b8c-255">Response example</span></span>

<span data-ttu-id="94b8c-256">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="94b8c-256">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="94b8c-257">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="94b8c-257">Related topics</span></span>

* [<span data-ttu-id="94b8c-258">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="94b8c-258">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="94b8c-259">Abrufen von Xbox Live Erfolgsdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-259">Get Xbox Live achievements data</span></span>](get-xbox-live-achievements-data.md)
* [<span data-ttu-id="94b8c-260">Abrufen von Xbox Live Integritätsdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-260">Get Xbox Live health data</span></span>](get-xbox-live-health-data.md)
* [<span data-ttu-id="94b8c-261">Abrufen von Xbox Live Spielehubdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-261">Get Xbox Live game hub data</span></span>](get-xbox-live-game-hub-data.md)
* [<span data-ttu-id="94b8c-262">Abrufen von Xbox Live Clubdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-262">Get Xbox Live club data</span></span>](get-xbox-live-club-data.md)
* [<span data-ttu-id="94b8c-263">Abrufen von Xbox Live Multiplayer-Daten</span><span class="sxs-lookup"><span data-stu-id="94b8c-263">Get Xbox Live multiplayer data</span></span>](get-xbox-live-multiplayer-data.md)
* [<span data-ttu-id="94b8c-264">Abrufen von Xbox Live gleichzeitigen Nutzungsdaten</span><span class="sxs-lookup"><span data-stu-id="94b8c-264">Get Xbox Live concurrent usage data</span></span>](get-xbox-live-concurrent-usage-data.md)
