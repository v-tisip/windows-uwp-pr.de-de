---
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die stapelüberwachung für einen Fehler in Ihrer Xbox One Spiel abzurufen.
title: Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele
ms.date: 11/06/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Stapelüberwachung, Fehler
ms.localizationpriority: medium
ms.openlocfilehash: fd43305c54245c3281a0e840d3df4c5c87ff7ad8
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7834209"
---
# <a name="get-the-stack-trace-for-an-error-in-your-xbox-one-game"></a><span data-ttu-id="ada93-104">Abrufen der stapelüberwachung für einen Fehler in Ihrer Xbox One-Spiele</span><span class="sxs-lookup"><span data-stu-id="ada93-104">Get the stack trace for an error in your Xbox One game</span></span>

<span data-ttu-id="ada93-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API-um die stapelüberwachung für einen Fehler in Ihrer Xbox One Spiel abzurufen, die das über das Xbox-Portal (XDP) und im XDP Analytics Partner Center-Dashboard verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="ada93-105">Use this method in the Microsoft Store analytics API to get the stack trace for an error in your Xbox One game that was ingested through the Xbox Developer Portal (XDP) and available in the XDP Analytics Partner Center dashboard.</span></span> <span data-ttu-id="ada93-106">Diese Methode kann nur die Stapelüberwachung für einen Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="ada93-106">This method can only download the stack trace for an error that occurred in the last 30 days.</span></span>

<span data-ttu-id="ada93-107">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die [Details zu einem Fehler in Ihrer Xbox One Spiel get](get-details-for-an-error-in-your-xbox-one-game.md) -Methode verwenden, um die ID der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für die Sie die stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ada93-107">Before you can use this method, you must first use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ada93-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ada93-108">Prerequisites</span></span>


<span data-ttu-id="ada93-109">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ada93-109">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ada93-110">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="ada93-110">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="ada93-111">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ada93-111">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ada93-112">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ada93-112">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ada93-113">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ada93-113">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="ada93-114">Rufen Sie die ID der CAB-Datei an, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ada93-114">Get the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="ada93-115">Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) -Methode, um Details zu einem bestimmten Fehler in Ihrer app abzurufen, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ada93-115">To get this ID, use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="ada93-116">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ada93-116">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="ada93-117">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="ada93-117">Request syntax</span></span>

| <span data-ttu-id="ada93-118">Methode</span><span class="sxs-lookup"><span data-stu-id="ada93-118">Method</span></span> | <span data-ttu-id="ada93-119">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ada93-119">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="ada93-120">GET</span><span class="sxs-lookup"><span data-stu-id="ada93-120">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/stacktrace``` |


### <a name="request-header"></a><span data-ttu-id="ada93-121">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ada93-121">Request header</span></span>

| <span data-ttu-id="ada93-122">Header</span><span class="sxs-lookup"><span data-stu-id="ada93-122">Header</span></span>        | <span data-ttu-id="ada93-123">Typ</span><span class="sxs-lookup"><span data-stu-id="ada93-123">Type</span></span>   | <span data-ttu-id="ada93-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ada93-124">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ada93-125">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ada93-125">Authorization</span></span> | <span data-ttu-id="ada93-126">String</span><span class="sxs-lookup"><span data-stu-id="ada93-126">string</span></span> | <span data-ttu-id="ada93-127">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ada93-127">Required.</span></span> <span data-ttu-id="ada93-128">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ada93-128">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="ada93-129">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ada93-129">Request parameters</span></span>

| <span data-ttu-id="ada93-130">Parameter</span><span class="sxs-lookup"><span data-stu-id="ada93-130">Parameter</span></span>        | <span data-ttu-id="ada93-131">Typ</span><span class="sxs-lookup"><span data-stu-id="ada93-131">Type</span></span>   |  <span data-ttu-id="ada93-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ada93-132">Description</span></span>      |  <span data-ttu-id="ada93-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ada93-133">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="ada93-134">applicationId</span><span class="sxs-lookup"><span data-stu-id="ada93-134">applicationId</span></span> | <span data-ttu-id="ada93-135">string</span><span class="sxs-lookup"><span data-stu-id="ada93-135">string</span></span> | <span data-ttu-id="ada93-136">Die Produkt-ID des Xbox One Spiels, für die Sie eine stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ada93-136">The product ID of the Xbox One game for which you are retrieving a stack trace.</span></span> <span data-ttu-id="ada93-137">Um die Produkt-ID Ihres Spiels zu erhalten, wechseln Sie zu Ihrem Spiel in der Xbox-Entwickler-Portal (XDP) und rufen Sie die Produkt-ID von der URL ab.</span><span class="sxs-lookup"><span data-stu-id="ada93-137">To get the product ID of your game, navigate to your game in the Xbox Developer Portal (XDP) and retrieve the product ID from the URL.</span></span> <span data-ttu-id="ada93-138">Wenn Sie Ihre integritätsdaten aus dem Windows Partner Center Analytics-Bericht herunterladen, ist die Produkt-ID auch in der TSV-Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="ada93-138">Alternatively, if you download your health data from the Windows Partner Center analytics report, the product ID is included in the .tsv file.</span></span> |  <span data-ttu-id="ada93-139">Ja</span><span class="sxs-lookup"><span data-stu-id="ada93-139">Yes</span></span>  |
| <span data-ttu-id="ada93-140">cabId</span><span class="sxs-lookup"><span data-stu-id="ada93-140">cabId</span></span> | <span data-ttu-id="ada93-141">string</span><span class="sxs-lookup"><span data-stu-id="ada93-141">string</span></span> | <span data-ttu-id="ada93-142">Die eindeutige ID der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ada93-142">The unique ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="ada93-143">Um diese ID zu erhalten, verwenden Sie die [Details zu einem Fehler in Ihrer Xbox One Spiel abzurufen](get-details-for-an-error-in-your-xbox-one-game.md) -Methode, um Details zu einem bestimmten Fehler in Ihrer app abzurufen, und verwenden Sie den Wert **CabId** im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ada93-143">To get this ID, use the [get details for an error in your Xbox One game](get-details-for-an-error-in-your-xbox-one-game.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span> |  <span data-ttu-id="ada93-144">Ja</span><span class="sxs-lookup"><span data-stu-id="ada93-144">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="ada93-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ada93-145">Request example</span></span>

<span data-ttu-id="ada93-146">Im folgende Beispiel wird veranschaulicht, wie eine stapelüberwachung für einen Xbox One-Spiele mit dieser Methode abrufen.</span><span class="sxs-lookup"><span data-stu-id="ada93-146">The following example demonstrates how to get a stack trace for an Xbox One game using this method.</span></span> <span data-ttu-id="ada93-147">Ersetzen Sie den *ApplicationId* -Wert durch die Produkt-ID für Ihr Spiel an.</span><span class="sxs-lookup"><span data-stu-id="ada93-147">Replace the *applicationId* value with the product ID for your game.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/xbox/stacktrace?applicationId=BRRT4NJ9B3D1&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ada93-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="ada93-148">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="ada93-149">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ada93-149">Response body</span></span>

| <span data-ttu-id="ada93-150">Wert</span><span class="sxs-lookup"><span data-stu-id="ada93-150">Value</span></span>      | <span data-ttu-id="ada93-151">Typ</span><span class="sxs-lookup"><span data-stu-id="ada93-151">Type</span></span>    | <span data-ttu-id="ada93-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ada93-152">Description</span></span>                  |
|------------|---------|--------------------------------|
| <span data-ttu-id="ada93-153">Wert</span><span class="sxs-lookup"><span data-stu-id="ada93-153">Value</span></span>      | <span data-ttu-id="ada93-154">array</span><span class="sxs-lookup"><span data-stu-id="ada93-154">array</span></span>   | <span data-ttu-id="ada93-155">Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="ada93-155">An array of objects that each contain one frame of stack trace data.</span></span> <span data-ttu-id="ada93-156">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values).</span><span class="sxs-lookup"><span data-stu-id="ada93-156">For more information about the data in each object, see the [stack trace values](#stack-trace-values) section below.</span></span> |
| @nextLink  | <span data-ttu-id="ada93-157">String</span><span class="sxs-lookup"><span data-stu-id="ada93-157">string</span></span>  | <span data-ttu-id="ada93-158">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="ada93-158">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="ada93-159">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="ada93-159">For example, this value is returned if the **top** parameter of the request is set to 10 but there are more than 10 rows of errors for the query.</span></span> |
| <span data-ttu-id="ada93-160">TotalCount</span><span class="sxs-lookup"><span data-stu-id="ada93-160">TotalCount</span></span> | <span data-ttu-id="ada93-161">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="ada93-161">integer</span></span> | <span data-ttu-id="ada93-162">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="ada93-162">The total number of rows in the data result for the query.</span></span>          |


### <a name="stack-trace-values"></a><span data-ttu-id="ada93-163">Stapelüberwachungswerte</span><span class="sxs-lookup"><span data-stu-id="ada93-163">Stack trace values</span></span>

<span data-ttu-id="ada93-164">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="ada93-164">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="ada93-165">Wert</span><span class="sxs-lookup"><span data-stu-id="ada93-165">Value</span></span>           | <span data-ttu-id="ada93-166">Typ</span><span class="sxs-lookup"><span data-stu-id="ada93-166">Type</span></span>    | <span data-ttu-id="ada93-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ada93-167">Description</span></span>      |
|-----------------|---------|----------------|
| <span data-ttu-id="ada93-168">level</span><span class="sxs-lookup"><span data-stu-id="ada93-168">level</span></span>            | <span data-ttu-id="ada93-169">string</span><span class="sxs-lookup"><span data-stu-id="ada93-169">string</span></span>  |  <span data-ttu-id="ada93-170">Die Framenummer, die dieses Element im Aufrufstapel darstellt.</span><span class="sxs-lookup"><span data-stu-id="ada93-170">The frame number that this element represents in the call stack.</span></span>  |
| <span data-ttu-id="ada93-171">image</span><span class="sxs-lookup"><span data-stu-id="ada93-171">image</span></span>   | <span data-ttu-id="ada93-172">string</span><span class="sxs-lookup"><span data-stu-id="ada93-172">string</span></span>  |   <span data-ttu-id="ada93-173">Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ada93-173">The name of the executable or library image that contains the function that is called in this stack frame.</span></span>           |
| <span data-ttu-id="ada93-174">function</span><span class="sxs-lookup"><span data-stu-id="ada93-174">function</span></span> | <span data-ttu-id="ada93-175">string</span><span class="sxs-lookup"><span data-stu-id="ada93-175">string</span></span>  |  <span data-ttu-id="ada93-176">Der Name der Funktion, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ada93-176">The name of the function that is called in this stack frame.</span></span> <span data-ttu-id="ada93-177">Dies ist nur verfügbar, wenn Ihr Spiel Symbole für die ausführbare Datei oder die Bibliothek enthält.</span><span class="sxs-lookup"><span data-stu-id="ada93-177">This is available only if your game includes symbols for the executable or library.</span></span>              |
| <span data-ttu-id="ada93-178">offset</span><span class="sxs-lookup"><span data-stu-id="ada93-178">offset</span></span>     | <span data-ttu-id="ada93-179">string</span><span class="sxs-lookup"><span data-stu-id="ada93-179">string</span></span>  |  <span data-ttu-id="ada93-180">Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.</span><span class="sxs-lookup"><span data-stu-id="ada93-180">The byte offset of the current instruction relative to the start of the function.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="ada93-181">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="ada93-181">Response example</span></span>

<span data-ttu-id="ada93-182">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="ada93-182">The following example demonstrates an example JSON response body for this request.</span></span>

```json
{
  "Value": [
    {
      "level": "0",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.DoWork",
      "offset": "0x25C"
    }
    {
      "level": "1",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.MainPage.Initialize",
      "offset": "0x26"
    }
    {
      "level": "2",
      "image": "Contoso.ContosoApp",
      "function": "Contoso.ContosoApp.Start",
      "offset": "0x66"
    }
  ],
  "@nextLink": null,
  "TotalCount": 3
}

```

## <a name="related-topics"></a><span data-ttu-id="ada93-183">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ada93-183">Related topics</span></span>

* [<span data-ttu-id="ada93-184">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="ada93-184">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="ada93-185">Abrufen von Fehlerberichtsdaten für Ihre Xbox One Spiel</span><span class="sxs-lookup"><span data-stu-id="ada93-185">Get error reporting data for your Xbox One game</span></span>](get-error-reporting-data-for-your-xbox-one-game.md)
* [<span data-ttu-id="ada93-186">Abrufen von Details zu einem Fehler in Ihrer Xbox One-Spiele</span><span class="sxs-lookup"><span data-stu-id="ada93-186">Get details for an error in your Xbox One game</span></span>](get-details-for-an-error-in-your-xbox-one-game.md)
* [<span data-ttu-id="ada93-187">Herunterladen der CAB-Datei für einen Fehler in Ihrer Xbox One Spiel</span><span class="sxs-lookup"><span data-stu-id="ada93-187">Download the CAB file for an error in your Xbox One game</span></span>](download-the-cab-file-for-an-error-in-your-xbox-one-game.md)
