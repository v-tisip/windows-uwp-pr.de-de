---
author: mcleanbyron
ms.assetid: b556a245-6359-4ddc-a4bd-76f9873ab694
description: "Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer App abzurufen."
title: "Abrufen der Stapelüberwachung für einen Fehler in Ihrer App"
ms.author: mcleans
ms.date: 06/16/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Store-Dienste, Windows Store-Analyse-API, Stapelüberwachung, Fehler"
ms.openlocfilehash: bec42609ee9441a872415bc270a97bcb21a858f7
ms.sourcegitcommit: 7aabd2e59d45bbc5512dd4ddd9110ae62b79d552
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2017
---
# <a name="get-the-stack-trace-for-an-error-in-your-app"></a><span data-ttu-id="ca9e0-104">Abrufen der Stapelüberwachung für einen Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ca9e0-104">Get the stack trace for an error in your app</span></span>

<span data-ttu-id="ca9e0-105">Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-105">Use this method in the Windows Store analytics API to get the stack trace for an error in your app.</span></span> <span data-ttu-id="ca9e0-106">Diese Methode kann nur die Stapelüberwachung für einen App-Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-106">This method can only download the stack trace for an app error that occurred in the last 30 days.</span></span> <span data-ttu-id="ca9e0-107">Stapelüberwachungen sind auch im Abschnitt **Fehler** des [Integritätsberichts](../publish/health-report.md) im Windows Dev Center-Dashboard verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-107">Stack traces are also available in the **Failures** section of the [Health report](../publish/health-report.md) in the Windows Dev Center dashboard.</span></span>

<span data-ttu-id="ca9e0-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode für das [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md) aufrufen, um die ID der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-108">Before you can use this method, you must first use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca9e0-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ca9e0-109">Prerequisites</span></span>


<span data-ttu-id="ca9e0-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="ca9e0-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="ca9e0-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Windows Store analytics API.</span></span>
* <span data-ttu-id="ca9e0-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="ca9e0-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="ca9e0-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="ca9e0-115">Rufen Sie die ID der CAB-Datei an, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-115">Get the ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="ca9e0-116">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-116">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="ca9e0-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="ca9e0-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="ca9e0-118">Request syntax</span></span>

| <span data-ttu-id="ca9e0-119">Methode</span><span class="sxs-lookup"><span data-stu-id="ca9e0-119">Method</span></span> | <span data-ttu-id="ca9e0-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="ca9e0-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="ca9e0-121">GET</span><span class="sxs-lookup"><span data-stu-id="ca9e0-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/stacktrace``` |

<span/> 

### <a name="request-header"></a><span data-ttu-id="ca9e0-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="ca9e0-122">Request header</span></span>

| <span data-ttu-id="ca9e0-123">Header</span><span class="sxs-lookup"><span data-stu-id="ca9e0-123">Header</span></span>        | <span data-ttu-id="ca9e0-124">Typ</span><span class="sxs-lookup"><span data-stu-id="ca9e0-124">Type</span></span>   | <span data-ttu-id="ca9e0-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="ca9e0-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-126">Authorization</span></span> | <span data-ttu-id="ca9e0-127">String</span><span class="sxs-lookup"><span data-stu-id="ca9e0-127">string</span></span> | <span data-ttu-id="ca9e0-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-128">Required.</span></span> <span data-ttu-id="ca9e0-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |

<span/> 

### <a name="request-parameters"></a><span data-ttu-id="ca9e0-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ca9e0-130">Request parameters</span></span>

| <span data-ttu-id="ca9e0-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="ca9e0-131">Parameter</span></span>        | <span data-ttu-id="ca9e0-132">Typ</span><span class="sxs-lookup"><span data-stu-id="ca9e0-132">Type</span></span>   |  <span data-ttu-id="ca9e0-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-133">Description</span></span>      |  <span data-ttu-id="ca9e0-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ca9e0-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="ca9e0-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="ca9e0-135">applicationId</span></span> | <span data-ttu-id="ca9e0-136">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-136">string</span></span> | <span data-ttu-id="ca9e0-137">Die Store-ID der App, für die Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-137">The Store ID of the app for which you want to get the stack trace.</span></span> <span data-ttu-id="ca9e0-138">Die Store-ID ist auf der [Seite mit der App-Identität](../publish/view-app-identity-details.md) des DevCenter-Dashboards verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-138">The Store ID is available on the [App identity page](../publish/view-app-identity-details.md) of the Dev Center dashboard.</span></span> <span data-ttu-id="ca9e0-139">Beispiel für eine Store-ID: 9WZDNCRFJ3Q8.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-139">An example Store ID is 9WZDNCRFJ3Q8.</span></span> |  <span data-ttu-id="ca9e0-140">Ja</span><span class="sxs-lookup"><span data-stu-id="ca9e0-140">Yes</span></span>  |
| <span data-ttu-id="ca9e0-141">cabId</span><span class="sxs-lookup"><span data-stu-id="ca9e0-141">cabId</span></span> | <span data-ttu-id="ca9e0-142">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-142">string</span></span> | <span data-ttu-id="ca9e0-143">Die eindeutige ID der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-143">The unique ID of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="ca9e0-144">Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Details zu einem Fehler in Ihrer App](get-details-for-an-error-in-your-app.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabId**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-144">To get this ID, use the [get details for an error in your app](get-details-for-an-error-in-your-app.md) method to retrieve details for a specific error in your app, and use the **cabId** value in the response body of that method.</span></span> |  <span data-ttu-id="ca9e0-145">Ja</span><span class="sxs-lookup"><span data-stu-id="ca9e0-145">Yes</span></span>  |

<span/>
 
### <a name="request-example"></a><span data-ttu-id="ca9e0-146">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ca9e0-146">Request example</span></span>

<span data-ttu-id="ca9e0-147">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine Stapelüberwachung abrufen.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-147">The following example demonstrates how to get a stack trace using this method.</span></span> <span data-ttu-id="ca9e0-148">Ersetzen Sie den *applicationId*-Wert durch die Store-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-148">Replace the *applicationId* value with the Store ID for your app.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/stacktrace?applicationId=9NBLGGGZ5QDR&cabId=1336373323853 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="ca9e0-149">Antwort</span><span class="sxs-lookup"><span data-stu-id="ca9e0-149">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="ca9e0-150">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ca9e0-150">Response body</span></span>

| <span data-ttu-id="ca9e0-151">Wert</span><span class="sxs-lookup"><span data-stu-id="ca9e0-151">Value</span></span>      | <span data-ttu-id="ca9e0-152">Typ</span><span class="sxs-lookup"><span data-stu-id="ca9e0-152">Type</span></span>    | <span data-ttu-id="ca9e0-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-153">Description</span></span>                  |
|------------|---------|--------------------------------|
| <span data-ttu-id="ca9e0-154">Wert</span><span class="sxs-lookup"><span data-stu-id="ca9e0-154">Value</span></span>      | <span data-ttu-id="ca9e0-155">array</span><span class="sxs-lookup"><span data-stu-id="ca9e0-155">array</span></span>   | <span data-ttu-id="ca9e0-156">Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-156">An array of objects that each contain one frame of stack trace data.</span></span> <span data-ttu-id="ca9e0-157">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values).</span><span class="sxs-lookup"><span data-stu-id="ca9e0-157">For more information about the data in each object, see the [stack trace values](#stack-trace-values) section below.</span></span> |
| @nextLink  | <span data-ttu-id="ca9e0-158">String</span><span class="sxs-lookup"><span data-stu-id="ca9e0-158">string</span></span>  | <span data-ttu-id="ca9e0-159">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-159">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="ca9e0-160">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-160">For example, this value is returned if the **top** parameter of the request is set to 10 but there are more than 10 rows of errors for the query.</span></span> |
| <span data-ttu-id="ca9e0-161">TotalCount</span><span class="sxs-lookup"><span data-stu-id="ca9e0-161">TotalCount</span></span> | <span data-ttu-id="ca9e0-162">inumber</span><span class="sxs-lookup"><span data-stu-id="ca9e0-162">inumber</span></span> | <span data-ttu-id="ca9e0-163">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-163">The total number of rows in the data result for the query.</span></span>          |

<span/>

### <a name="stack-trace-values"></a><span data-ttu-id="ca9e0-164">Stapelüberwachungswerte</span><span class="sxs-lookup"><span data-stu-id="ca9e0-164">Stack trace values</span></span>

<span data-ttu-id="ca9e0-165">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-165">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="ca9e0-166">Wert</span><span class="sxs-lookup"><span data-stu-id="ca9e0-166">Value</span></span>           | <span data-ttu-id="ca9e0-167">Typ</span><span class="sxs-lookup"><span data-stu-id="ca9e0-167">Type</span></span>    | <span data-ttu-id="ca9e0-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ca9e0-168">Description</span></span>      |
|-----------------|---------|----------------|
| <span data-ttu-id="ca9e0-169">level</span><span class="sxs-lookup"><span data-stu-id="ca9e0-169">level</span></span>            | <span data-ttu-id="ca9e0-170">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-170">string</span></span>  |  <span data-ttu-id="ca9e0-171">Die Framenummer, die dieses Element im Aufrufstapel darstellt.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-171">The frame number that this element represents in the call stack.</span></span>  |
| <span data-ttu-id="ca9e0-172">image</span><span class="sxs-lookup"><span data-stu-id="ca9e0-172">image</span></span>   | <span data-ttu-id="ca9e0-173">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-173">string</span></span>  |   <span data-ttu-id="ca9e0-174">Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-174">The name of the executable or library image that contains the function that is called in this stack frame.</span></span>           |
| <span data-ttu-id="ca9e0-175">function</span><span class="sxs-lookup"><span data-stu-id="ca9e0-175">function</span></span> | <span data-ttu-id="ca9e0-176">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-176">string</span></span>  |  <span data-ttu-id="ca9e0-177">Der Name der Funktion, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-177">The name of the function that is called in this stack frame.</span></span> <span data-ttu-id="ca9e0-178">Dies ist nur verfügbar, wenn Ihre App Symbole für die ausführbare Datei oder die Bibliothek enthält.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-178">This is available only if your app includes symbols for the executable or library.</span></span>              |
| <span data-ttu-id="ca9e0-179">offset</span><span class="sxs-lookup"><span data-stu-id="ca9e0-179">offset</span></span>     | <span data-ttu-id="ca9e0-180">string</span><span class="sxs-lookup"><span data-stu-id="ca9e0-180">string</span></span>  |  <span data-ttu-id="ca9e0-181">Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-181">The byte offset of the current instruction relative to the start of the function.</span></span>      |

<span/> 

### <a name="response-example"></a><span data-ttu-id="ca9e0-182">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="ca9e0-182">Response example</span></span>

<span data-ttu-id="ca9e0-183">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="ca9e0-183">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="ca9e0-184">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ca9e0-184">Related topics</span></span>

* [<span data-ttu-id="ca9e0-185">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="ca9e0-185">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="ca9e0-186">Zugreifen auf Analysedaten mit WindowsStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="ca9e0-186">Access analytics data using Windows Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="ca9e0-187">Abrufen von Fehlerberichtsdaten</span><span class="sxs-lookup"><span data-stu-id="ca9e0-187">Get error reporting data</span></span>](get-error-reporting-data.md)
* [<span data-ttu-id="ca9e0-188">Abrufen von Details zu einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ca9e0-188">Get details for an error in your app</span></span>](get-details-for-an-error-in-your-app.md)
* [<span data-ttu-id="ca9e0-189">Herunterladen der CAB-Datei bei einem Fehler in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ca9e0-189">Download the CAB file for an error in your app</span></span>](download-the-cab-file-for-an-error-in-your-app.md)
