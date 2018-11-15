---
author: Xansky
ms.assetid: b556a245-6359-4ddc-a4bd-76f9873ab694
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer App abzurufen.
title: Abrufen der Stapelüberwachung für einen Fehler in Ihrer App
ms.author: mhopkins
ms.date: 06/05/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Stapelüberwachung, Fehler
ms.localizationpriority: medium
ms.openlocfilehash: 0befb91175690576b4c0b44fe6e701d4c4efd7df
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6659593"
---
# <a name="get-the-stack-trace-for-an-error-in-your-app"></a><span data-ttu-id="55991-104">Abrufen der Stapelüberwachung für einen Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="55991-104">Get the stack trace for an error in your app</span></span>

<span data-ttu-id="55991-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="55991-105">Use this method in the Microsoft Store analytics API to get the stack trace for an error in your app.</span></span> <span data-ttu-id="55991-106">Diese Methode kann nur die Stapelüberwachung für einen App-Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="55991-106">This method can only download the stack trace for an app error that occurred in the last 30 days.</span></span> <span data-ttu-id="55991-107">Stapelüberwachungen sind auch im Abschnitt **Fehler** im [Bericht "Integrität"](../publish/health-report.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="55991-107">Stack traces are also available in the **Failures** section of the [Health report](../publish/health-report.md) in Partner Center.</span></span>

<span data-ttu-id="55991-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode für das [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md) aufrufen, um die ID der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="55991-108">Before you can use this method, you must first use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55991-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="55991-109">Prerequisites</span></span>


<span data-ttu-id="55991-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="55991-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="55991-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="55991-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="55991-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="55991-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="55991-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="55991-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="55991-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="55991-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="55991-115">Rufen Sie die ID der CAB-Datei an, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="55991-115">Get the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="55991-116">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="55991-116">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="55991-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="55991-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="55991-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="55991-118">Request syntax</span></span>

| <span data-ttu-id="55991-119">Methode</span><span class="sxs-lookup"><span data-stu-id="55991-119">Method</span></span> | <span data-ttu-id="55991-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="55991-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="55991-121">GET</span><span class="sxs-lookup"><span data-stu-id="55991-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/stacktrace``` |


### <a name="request-header"></a><span data-ttu-id="55991-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="55991-122">Request header</span></span>

| <span data-ttu-id="55991-123">Header</span><span class="sxs-lookup"><span data-stu-id="55991-123">Header</span></span>        | <span data-ttu-id="55991-124">Typ</span><span class="sxs-lookup"><span data-stu-id="55991-124">Type</span></span>   | <span data-ttu-id="55991-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55991-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="55991-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="55991-126">Authorization</span></span> | <span data-ttu-id="55991-127">String</span><span class="sxs-lookup"><span data-stu-id="55991-127">string</span></span> | <span data-ttu-id="55991-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="55991-128">Required.</span></span> <span data-ttu-id="55991-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="55991-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |


### <a name="request-parameters"></a><span data-ttu-id="55991-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="55991-130">Request parameters</span></span>

| <span data-ttu-id="55991-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="55991-131">Parameter</span></span>        | <span data-ttu-id="55991-132">Typ</span><span class="sxs-lookup"><span data-stu-id="55991-132">Type</span></span>   |  <span data-ttu-id="55991-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55991-133">Description</span></span>      |  <span data-ttu-id="55991-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55991-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="55991-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="55991-135">applicationId</span></span> | <span data-ttu-id="55991-136">string</span><span class="sxs-lookup"><span data-stu-id="55991-136">string</span></span> | <span data-ttu-id="55991-137">Die Store-ID der App, für die Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="55991-137">The Store ID of the app for which you want to get the stack trace.</span></span> <span data-ttu-id="55991-138">Die Store-ID ist auf der [Seite App-Identität](../publish/view-app-identity-details.md) im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="55991-138">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) in Partner Center.</span></span> <span data-ttu-id="55991-139">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="55991-139">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="55991-140">Ja</span><span class="sxs-lookup"><span data-stu-id="55991-140">Yes</span></span>  |
| <span data-ttu-id="55991-141">cabId</span><span class="sxs-lookup"><span data-stu-id="55991-141">cabId</span></span> | <span data-ttu-id="55991-142">string</span><span class="sxs-lookup"><span data-stu-id="55991-142">string</span></span> | <span data-ttu-id="55991-143">Die eindeutige ID der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="55991-143">The unique ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="55991-144">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="55991-144">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span> |  <span data-ttu-id="55991-145">Ja</span><span class="sxs-lookup"><span data-stu-id="55991-145">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="55991-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="55991-146">Request example</span></span>

<span data-ttu-id="55991-147">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine Stapelüberwachung abrufen.</span><span class="sxs-lookup"><span data-stu-id="55991-147">The following example demonstrates how to get a stack trace using this method.</span></span> <span data-ttu-id="55991-148">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="55991-148">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/stacktrace?applicationId=9NBLGGGZ5QDR&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="55991-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="55991-149">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="55991-150">Antworttext</span><span class="sxs-lookup"><span data-stu-id="55991-150">Response body</span></span>

| <span data-ttu-id="55991-151">Wert</span><span class="sxs-lookup"><span data-stu-id="55991-151">Value</span></span>      | <span data-ttu-id="55991-152">Typ</span><span class="sxs-lookup"><span data-stu-id="55991-152">Type</span></span>    | <span data-ttu-id="55991-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55991-153">Description</span></span>                  |
|------------|---------|--------------------------------|
| <span data-ttu-id="55991-154">Wert</span><span class="sxs-lookup"><span data-stu-id="55991-154">Value</span></span>      | <span data-ttu-id="55991-155">array</span><span class="sxs-lookup"><span data-stu-id="55991-155">array</span></span>   | <span data-ttu-id="55991-156">Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="55991-156">An array of objects that each contain one frame of stack trace data.</span></span> <span data-ttu-id="55991-157">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values).</span><span class="sxs-lookup"><span data-stu-id="55991-157">For more information about the data in each object, see the [stack trace values](#stack-trace-values) section below.</span></span> |
| @nextLink  | <span data-ttu-id="55991-158">String</span><span class="sxs-lookup"><span data-stu-id="55991-158">string</span></span>  | <span data-ttu-id="55991-159">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="55991-159">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="55991-160">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="55991-160">For example, this value is returned if the **top** parameter of the request is set to 10 but there are more than 10 rows of errors for the query.</span></span> |
| <span data-ttu-id="55991-161">TotalCount</span><span class="sxs-lookup"><span data-stu-id="55991-161">TotalCount</span></span> | <span data-ttu-id="55991-162">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="55991-162">integer</span></span> | <span data-ttu-id="55991-163">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="55991-163">The total number of rows in the data result for the query.</span></span>          |


### <a name="stack-trace-values"></a><span data-ttu-id="55991-164">Stapelüberwachungswerte</span><span class="sxs-lookup"><span data-stu-id="55991-164">Stack trace values</span></span>

<span data-ttu-id="55991-165">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="55991-165">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="55991-166">Wert</span><span class="sxs-lookup"><span data-stu-id="55991-166">Value</span></span>           | <span data-ttu-id="55991-167">Typ</span><span class="sxs-lookup"><span data-stu-id="55991-167">Type</span></span>    | <span data-ttu-id="55991-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55991-168">Description</span></span>      |
|-----------------|---------|----------------|
| <span data-ttu-id="55991-169">level</span><span class="sxs-lookup"><span data-stu-id="55991-169">level</span></span>            | <span data-ttu-id="55991-170">string</span><span class="sxs-lookup"><span data-stu-id="55991-170">string</span></span>  |  <span data-ttu-id="55991-171">Die Framenummer, die dieses Element im Aufrufstapel darstellt.</span><span class="sxs-lookup"><span data-stu-id="55991-171">The frame number that this element represents in the call stack.</span></span>  |
| <span data-ttu-id="55991-172">image</span><span class="sxs-lookup"><span data-stu-id="55991-172">image</span></span>   | <span data-ttu-id="55991-173">string</span><span class="sxs-lookup"><span data-stu-id="55991-173">string</span></span>  |   <span data-ttu-id="55991-174">Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="55991-174">The name of the executable or library image that contains the function that is called in this stack frame.</span></span>           |
| <span data-ttu-id="55991-175">function</span><span class="sxs-lookup"><span data-stu-id="55991-175">function</span></span> | <span data-ttu-id="55991-176">string</span><span class="sxs-lookup"><span data-stu-id="55991-176">string</span></span>  |  <span data-ttu-id="55991-177">Der Name der Funktion, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="55991-177">The name of the function that is called in this stack frame.</span></span> <span data-ttu-id="55991-178">Dies ist nur verfügbar, wenn Ihre App Symbole für die ausführbare Datei oder die Bibliothek enthält.</span><span class="sxs-lookup"><span data-stu-id="55991-178">This is available only if your app includes symbols for the executable or library.</span></span>              |
| <span data-ttu-id="55991-179">offset</span><span class="sxs-lookup"><span data-stu-id="55991-179">offset</span></span>     | <span data-ttu-id="55991-180">string</span><span class="sxs-lookup"><span data-stu-id="55991-180">string</span></span>  |  <span data-ttu-id="55991-181">Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.</span><span class="sxs-lookup"><span data-stu-id="55991-181">The byte offset of the current instruction relative to the start of the function.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="55991-182">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="55991-182">Response example</span></span>

<span data-ttu-id="55991-183">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="55991-183">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="55991-184">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="55991-184">Related topics</span></span>

* [<span data-ttu-id="55991-185">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="55991-185">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="55991-186">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="55991-186">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="55991-187">Abrufen von Fehlerberichtsdaten</span><span class="sxs-lookup"><span data-stu-id="55991-187">Get error reporting data</span></span>](get-error-reporting-data.md)
* [<span data-ttu-id="55991-188">Abrufen von Details zu einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="55991-188">Get details for an error in your app</span></span>](get-details-for-an-error-in-your-app.md)
* [<span data-ttu-id="55991-189">Herunterladen der CAB-Datei bei einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="55991-189">Download the CAB file for an error in your app</span></span>](download-the-cab-file-for-an-error-in-your-app.md)
