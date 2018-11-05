---
author: Xansky
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung abzurufen.
title: Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung
ms.author: mhopkins
ms.date: 06/05/2018
ms.topic: article
keywords: Windows10, UWP, Store-Dienste, Microsoft Store-Analyse-API, Stapelüberwachung, Fehler, Desktopanwendung
ms.localizationpriority: medium
ms.openlocfilehash: 024c903ea43d9fabc90b2f6b7891f6de4e92b1d5
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6025276"
---
# <a name="get-the-stack-trace-for-an-error-in-your-desktop-application"></a><span data-ttu-id="a5fee-104">Abrufen der Stapelüberwachung für einen Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="a5fee-104">Get the stack trace for an error in your desktop application</span></span>

<span data-ttu-id="a5fee-105">Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die Stapelüberwachung für einen Fehler in einer Desktopanwendung abzurufen, die Sie zum [Windows-Desktopanwendungsprogramm](https://msdn.microsoft.com/library/windows/desktop/mt826504) hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="a5fee-105">Use this method in the Microsoft Store analytics API to get the stack trace for an error in a desktop application that you have added to the [Windows Desktop Application program](https://msdn.microsoft.com/library/windows/desktop/mt826504).</span></span> <span data-ttu-id="a5fee-106">Diese Methode kann nur die Stapelüberwachung für einen Fehler herunterladen, die in den letzten 30Tagen aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="a5fee-106">This method can only download the stack trace for an error that occurred in the last 30 days.</span></span> <span data-ttu-id="a5fee-107">Stapelüberwachungen sind auch im [Bericht "Integrität"](https://msdn.microsoft.com/library/windows/desktop/mt826504) für desktopanwendungen im Partner Center verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a5fee-107">Stack traces are also available in the [Health report](https://msdn.microsoft.com/library/windows/desktop/mt826504) for desktop applications in Partner Center.</span></span>

<span data-ttu-id="a5fee-108">Bevor Sie diese Methode verwenden können, müssen Sie zuerst die Methode für das [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md) aufrufen, um die ID-Hash der CAB-Datei abzurufen, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a5fee-108">Before you can use this method, you must first use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve the ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5fee-109">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a5fee-109">Prerequisites</span></span>


<span data-ttu-id="a5fee-110">Zur Verwendung dieser Methode sind folgende Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="a5fee-110">To use this method, you need to first do the following:</span></span>

* <span data-ttu-id="a5fee-111">Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.</span><span class="sxs-lookup"><span data-stu-id="a5fee-111">If you have not done so already, complete all the [prerequisites](access-analytics-data-using-windows-store-services.md#prerequisites) for the Microsoft Store analytics API.</span></span>
* <span data-ttu-id="a5fee-112">[Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a5fee-112">[Obtain an Azure AD access token](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token) to use in the request header for this method.</span></span> <span data-ttu-id="a5fee-113">Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft.</span><span class="sxs-lookup"><span data-stu-id="a5fee-113">After you obtain an access token, you have 60 minutes to use it before it expires.</span></span> <span data-ttu-id="a5fee-114">Wenn das Token abgelaufen ist, können Sie ein neues abrufen.</span><span class="sxs-lookup"><span data-stu-id="a5fee-114">After the token expires, you can obtain a new one.</span></span>
* <span data-ttu-id="a5fee-115">Rufen Sie die ID-Hash der CAB-Datei ab, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a5fee-115">Get the ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="a5fee-116">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="a5fee-116">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your app, and use the **cabIdHash** value in the response body of that method.</span></span>

## <a name="request"></a><span data-ttu-id="a5fee-117">Anforderung</span><span class="sxs-lookup"><span data-stu-id="a5fee-117">Request</span></span>


### <a name="request-syntax"></a><span data-ttu-id="a5fee-118">Anforderungssyntax</span><span class="sxs-lookup"><span data-stu-id="a5fee-118">Request syntax</span></span>

| <span data-ttu-id="a5fee-119">Methode</span><span class="sxs-lookup"><span data-stu-id="a5fee-119">Method</span></span> | <span data-ttu-id="a5fee-120">Anforderungs-URI</span><span class="sxs-lookup"><span data-stu-id="a5fee-120">Request URI</span></span>                                                          |
|--------|----------------------------------------------------------------------|
| <span data-ttu-id="a5fee-121">GET</span><span class="sxs-lookup"><span data-stu-id="a5fee-121">GET</span></span>    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/stacktrace``` |


### <a name="request-header"></a><span data-ttu-id="a5fee-122">Anforderungsheader</span><span class="sxs-lookup"><span data-stu-id="a5fee-122">Request header</span></span>

| <span data-ttu-id="a5fee-123">Header</span><span class="sxs-lookup"><span data-stu-id="a5fee-123">Header</span></span>        | <span data-ttu-id="a5fee-124">Typ</span><span class="sxs-lookup"><span data-stu-id="a5fee-124">Type</span></span>   | <span data-ttu-id="a5fee-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5fee-125">Description</span></span>                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| <span data-ttu-id="a5fee-126">Autorisierung</span><span class="sxs-lookup"><span data-stu-id="a5fee-126">Authorization</span></span> | <span data-ttu-id="a5fee-127">String</span><span class="sxs-lookup"><span data-stu-id="a5fee-127">string</span></span> | <span data-ttu-id="a5fee-128">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a5fee-128">Required.</span></span> <span data-ttu-id="a5fee-129">Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;.</span><span class="sxs-lookup"><span data-stu-id="a5fee-129">The Azure AD access token in the form **Bearer** &lt;*token*&gt;.</span></span> |
 

### <a name="request-parameters"></a><span data-ttu-id="a5fee-130">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="a5fee-130">Request parameters</span></span>

| <span data-ttu-id="a5fee-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="a5fee-131">Parameter</span></span>        | <span data-ttu-id="a5fee-132">Typ</span><span class="sxs-lookup"><span data-stu-id="a5fee-132">Type</span></span>   |  <span data-ttu-id="a5fee-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5fee-133">Description</span></span>      |  <span data-ttu-id="a5fee-134">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="a5fee-134">Required</span></span>  |
|---------------|--------|---------------|------|
| <span data-ttu-id="a5fee-135">applicationId</span><span class="sxs-lookup"><span data-stu-id="a5fee-135">applicationId</span></span> | <span data-ttu-id="a5fee-136">string</span><span class="sxs-lookup"><span data-stu-id="a5fee-136">string</span></span> | <span data-ttu-id="a5fee-137">Die Produkt-ID der Desktopanwendung, für die Sie eine Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a5fee-137">The product ID of the desktop application for which you want to get a stack trace.</span></span> <span data-ttu-id="a5fee-138">Um die Produkt-ID einer desktop-Anwendung zu erhalten, öffnen Sie alle [-Analysebericht für Ihre desktop-Anwendung im Partner Center](https://msdn.microsoft.com/library/windows/desktop/mt826504) (z. B. den **Bericht "Integrität"**), und rufen Sie die Produkt-ID aus der URL.</span><span class="sxs-lookup"><span data-stu-id="a5fee-138">To get the product ID of a desktop application, open any [analytics report for your desktop application in Partner Center](https://msdn.microsoft.com/library/windows/desktop/mt826504) (such as the **Health report**) and retrieve the product ID from the URL.</span></span> |  <span data-ttu-id="a5fee-139">Ja</span><span class="sxs-lookup"><span data-stu-id="a5fee-139">Yes</span></span>  |
| <span data-ttu-id="a5fee-140">cabIdHash</span><span class="sxs-lookup"><span data-stu-id="a5fee-140">cabIdHash</span></span> | <span data-ttu-id="a5fee-141">String</span><span class="sxs-lookup"><span data-stu-id="a5fee-141">string</span></span> | <span data-ttu-id="a5fee-142">Die eindeutige ID-Hash der CAB-Datei, die mit dem Fehler verknüpft ist, für den Sie die Stapelüberwachung abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a5fee-142">The unique ID hash of the CAB file that is associated with the error for which you want to retrieve the stack trace.</span></span> <span data-ttu-id="a5fee-143">Verwenden Sie zum Abrufen dieses Wertes die Methode zum [Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung](get-details-for-an-error-in-your-desktop-application.md), um Details zu einem bestimmten Fehler in Ihrer Anwendung abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="a5fee-143">To get this value, use the [get details for an error in your desktop application](get-details-for-an-error-in-your-desktop-application.md) method to retrieve details for a specific error in your application, and use the **cabIdHash** value in the response body of that method.</span></span> |  <span data-ttu-id="a5fee-144">Ja</span><span class="sxs-lookup"><span data-stu-id="a5fee-144">Yes</span></span>  |

 
### <a name="request-example"></a><span data-ttu-id="a5fee-145">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="a5fee-145">Request example</span></span>

<span data-ttu-id="a5fee-146">Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine Stapelüberwachung abrufen.</span><span class="sxs-lookup"><span data-stu-id="a5fee-146">The following example demonstrates how to get a stack trace using this method.</span></span> <span data-ttu-id="a5fee-147">Ersetzen Sie die Parameter *applicationId* und *cabIdHash* durch die entsprechende Werte für Ihre Desktopanwendung.</span><span class="sxs-lookup"><span data-stu-id="a5fee-147">Replace the *applicationId* and *cabIdHash* parameters with the appropriate values for your desktop application.</span></span>

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/desktop/stacktrace?applicationId=10238467886765136388&cabIdHash=54ffb83a-e159-41d2-8158-f36f306cc01e HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a><span data-ttu-id="a5fee-148">Antwort</span><span class="sxs-lookup"><span data-stu-id="a5fee-148">Response</span></span>


### <a name="response-body"></a><span data-ttu-id="a5fee-149">Antworttext</span><span class="sxs-lookup"><span data-stu-id="a5fee-149">Response body</span></span>

| <span data-ttu-id="a5fee-150">Wert</span><span class="sxs-lookup"><span data-stu-id="a5fee-150">Value</span></span>      | <span data-ttu-id="a5fee-151">Typ</span><span class="sxs-lookup"><span data-stu-id="a5fee-151">Type</span></span>    | <span data-ttu-id="a5fee-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5fee-152">Description</span></span>                  |
|------------|---------|--------------------------------|
| <span data-ttu-id="a5fee-153">Wert</span><span class="sxs-lookup"><span data-stu-id="a5fee-153">Value</span></span>      | <span data-ttu-id="a5fee-154">array</span><span class="sxs-lookup"><span data-stu-id="a5fee-154">array</span></span>   | <span data-ttu-id="a5fee-155">Ein Array von Objekten, die jeweils einen einzelnen Frame der Stapelüberwachungsdaten enthalten.</span><span class="sxs-lookup"><span data-stu-id="a5fee-155">An array of objects that each contain one frame of stack trace data.</span></span> <span data-ttu-id="a5fee-156">Weitere Informationen zu den Daten in den einzelnen Objekten finden Sie unten im Abschnitt [Stapelüberwachungswerte](#stack-trace-values).</span><span class="sxs-lookup"><span data-stu-id="a5fee-156">For more information about the data in each object, see the [stack trace values](#stack-trace-values) section below.</span></span> |
| @nextLink  | <span data-ttu-id="a5fee-157">String</span><span class="sxs-lookup"><span data-stu-id="a5fee-157">string</span></span>  | <span data-ttu-id="a5fee-158">Wenn weitere Seiten mit Daten vorhanden sind, enthält diese Zeichenfolge einen URI, mit dem Sie die nächste Seite mit Daten anfordern können.</span><span class="sxs-lookup"><span data-stu-id="a5fee-158">If there are additional pages of data, this string contains a URI that you can use to request the next page of data.</span></span> <span data-ttu-id="a5fee-159">Beispielsweise wird dieser Wert zurückgegeben, wenn der Parameter **top** der Anforderung auf 10 festgelegt ist, es jedoch mehr als 10 Zeilen mit Fehlern für die Abfrage gibt.</span><span class="sxs-lookup"><span data-stu-id="a5fee-159">For example, this value is returned if the **top** parameter of the request is set to 10 but there are more than 10 rows of errors for the query.</span></span> |
| <span data-ttu-id="a5fee-160">TotalCount</span><span class="sxs-lookup"><span data-stu-id="a5fee-160">TotalCount</span></span> | <span data-ttu-id="a5fee-161">Ganzzahl</span><span class="sxs-lookup"><span data-stu-id="a5fee-161">integer</span></span> | <span data-ttu-id="a5fee-162">Die Gesamtzahl der Zeilen im Datenergebnis für die Abfrage.</span><span class="sxs-lookup"><span data-stu-id="a5fee-162">The total number of rows in the data result for the query.</span></span>          |


### <a name="stack-trace-values"></a><span data-ttu-id="a5fee-163">Stapelüberwachungswerte</span><span class="sxs-lookup"><span data-stu-id="a5fee-163">Stack trace values</span></span>

<span data-ttu-id="a5fee-164">Elemente im Array *Value* enthalten die folgenden Werte.</span><span class="sxs-lookup"><span data-stu-id="a5fee-164">Elements in the *Value* array contain the following values.</span></span>

| <span data-ttu-id="a5fee-165">Wert</span><span class="sxs-lookup"><span data-stu-id="a5fee-165">Value</span></span>           | <span data-ttu-id="a5fee-166">Typ</span><span class="sxs-lookup"><span data-stu-id="a5fee-166">Type</span></span>    | <span data-ttu-id="a5fee-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a5fee-167">Description</span></span>      |
|-----------------|---------|----------------|
| <span data-ttu-id="a5fee-168">level</span><span class="sxs-lookup"><span data-stu-id="a5fee-168">level</span></span>            | <span data-ttu-id="a5fee-169">string</span><span class="sxs-lookup"><span data-stu-id="a5fee-169">string</span></span>  |  <span data-ttu-id="a5fee-170">Die Framenummer, die dieses Element im Aufrufstapel darstellt.</span><span class="sxs-lookup"><span data-stu-id="a5fee-170">The frame number that this element represents in the call stack.</span></span>  |
| <span data-ttu-id="a5fee-171">image</span><span class="sxs-lookup"><span data-stu-id="a5fee-171">image</span></span>   | <span data-ttu-id="a5fee-172">string</span><span class="sxs-lookup"><span data-stu-id="a5fee-172">string</span></span>  |   <span data-ttu-id="a5fee-173">Den Namen der ausführbaren Datei oder des Bibliothekbilds, die/das die Funktion enthält, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="a5fee-173">The name of the executable or library image that contains the function that is called in this stack frame.</span></span>           |
| <span data-ttu-id="a5fee-174">function</span><span class="sxs-lookup"><span data-stu-id="a5fee-174">function</span></span> | <span data-ttu-id="a5fee-175">string</span><span class="sxs-lookup"><span data-stu-id="a5fee-175">string</span></span>  |  <span data-ttu-id="a5fee-176">Der Name der Funktion, die in diesem Stapelframe aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="a5fee-176">The name of the function that is called in this stack frame.</span></span> <span data-ttu-id="a5fee-177">Dies ist nur verfügbar, wenn Ihre App Symbole für die ausführbare Datei oder die Bibliothek enthält.</span><span class="sxs-lookup"><span data-stu-id="a5fee-177">This is available only if your app includes symbols for the executable or library.</span></span>              |
| <span data-ttu-id="a5fee-178">offset</span><span class="sxs-lookup"><span data-stu-id="a5fee-178">offset</span></span>     | <span data-ttu-id="a5fee-179">string</span><span class="sxs-lookup"><span data-stu-id="a5fee-179">string</span></span>  |  <span data-ttu-id="a5fee-180">Der Byte-Offset der aktuellen Anweisung relativ zum Start der Funktion.</span><span class="sxs-lookup"><span data-stu-id="a5fee-180">The byte offset of the current instruction relative to the start of the function.</span></span>      |


### <a name="response-example"></a><span data-ttu-id="a5fee-181">Antwortbeispiel</span><span class="sxs-lookup"><span data-stu-id="a5fee-181">Response example</span></span>

<span data-ttu-id="a5fee-182">Das folgende Beispiel zeigt ein Beispiel für einen JSON-Antworttext für diese Anforderung.</span><span class="sxs-lookup"><span data-stu-id="a5fee-182">The following example demonstrates an example JSON response body for this request.</span></span>

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

## <a name="related-topics"></a><span data-ttu-id="a5fee-183">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a5fee-183">Related topics</span></span>

* [<span data-ttu-id="a5fee-184">Integritätsbericht</span><span class="sxs-lookup"><span data-stu-id="a5fee-184">Health report</span></span>](../publish/health-report.md)
* [<span data-ttu-id="a5fee-185">Zugreifen auf Analysedaten mit MicrosoftStore-Diensten</span><span class="sxs-lookup"><span data-stu-id="a5fee-185">Access analytics data using Microsoft Store services</span></span>](access-analytics-data-using-windows-store-services.md)
* [<span data-ttu-id="a5fee-186">Abrufen von Fehlerberichtsdaten für Ihre Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="a5fee-186">Get error reporting data for your desktop application</span></span>](get-desktop-application-error-reporting-data.md)
* [<span data-ttu-id="a5fee-187">Abrufen von Details zu einem Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="a5fee-187">Get details for an error in your desktop application</span></span>](get-details-for-an-error-in-your-desktop-application.md)
* [<span data-ttu-id="a5fee-188">Herunterladen der CAB-Datei bei einem Fehler in Ihrer Desktopanwendung</span><span class="sxs-lookup"><span data-stu-id="a5fee-188">Download the CAB file for an error in your desktop application</span></span>](download-the-cab-file-for-an-error-in-your-desktop-application.md)
